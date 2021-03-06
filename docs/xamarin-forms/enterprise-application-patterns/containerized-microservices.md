---
title: コンテナー化 Microservices
ms.prod: xamarin
ms.assetid: 5872ad92-04e0-4f1a-9691-79d5602f5683
ms.technology: xamarin-forms
author: davidbritch
ms.author: dabritch
ms.date: 08/07/2017
ms.openlocfilehash: 461a1310ff430c16e49fa0ed6037a77b1302f769
ms.sourcegitcommit: 945df041e2180cb20af08b83cc703ecd1aedc6b0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2018
---
# <a name="containerized-microservices"></a>コンテナー化 Microservices

クライアントとサーバー アプリケーションを開発すると、各層に、特定のテクノロジを使用する階層化されたアプリケーションの構築に焦点を合わせてが生まれました。 このようなアプリケーションは多くの場合と呼ばれるを*モノリシック*アプリケーション、およびはハードウェアのピーク時の負荷をあらかじめスケール上にパッケージ化します。 この開発方法の主な欠点は、テスト コストや、個々 のコンポーネントを簡単にスケールできません、各階層内のコンポーネント間の密結合です。 単純な更新プログラムが持つことができます、この層の他の予期しない現象アプリケーション コンポーネントを変更する必要がその全体の層を再評価して、再展開するためです。

特にに関する、クラウドの時代にはスケーリング個々 のコンポーネントが簡単にすることはできません。 モノリシックのアプリケーションでは、ドメイン固有の機能が含まれてし、通常フロント エンド、ビジネス ロジック、およびデータ ストレージなどの機能のレイヤーで除算します。 図 8-1 に示すように、単体のアプリケーションは、複数のコンピューターにアプリケーション全体を複製してスケーリングされます。

![](containerized-microservices-images/monolithicapp.png "モノリシックなアプリケーションのスケーリング方法")

**図 8-1**: モノリシックなアプリケーションのスケーリングの手法

## <a name="microservices"></a>Microservices

Microservices には、アプリケーションの開発と展開を別のアプローチ、機敏性、スケール、および先進的なクラウド アプリケーションの信頼性の要件には、最適なアプローチが用意されています。 Microservices アプリケーションは、アプリケーションの全体的な機能を提供する連携する独立したコンポーネントに分解されます。 用語マイクロ サービスは、各マイクロ サービスを 1 つの関数を実装するように、アプリケーションがサービス上の独立した問題を反映するために十分な小規模から構成することを強調します。 さらに、各マイクロ サービスは、他の microservices が通信してそのデータを共有できるように、適切に定義されたコントラクトを持ちます。 Microservices の一般的な例は、ショッピング カートが含まれて、処理を在庫、サブシステム、および支払い処理を購入します。

Microservices スケール アウトできるとは独立して、同時に拡張されるジャイアントのモノリシック アプリケーションと比較しています。 これは、特定の機能領域を必要な処理電源やネットワーク帯域幅需要をサポートするためが不必要にスケール アウト アプリケーションの他の領域ではなく拡大/縮小することを意味します。 図 8-2 は、場所 microservices が導入され、個別に拡張、この方法を示しています。 マシン間でサービスのインスタンスを作成します。

![](containerized-microservices-images/microservicesapp.png "Microservices アプリケーションのスケーリング方法")

**図 8-2**: Microservices アプリケーション スケーリングの手法

マイクロ サービスのスケール アウトは、アプリケーションの負荷の変化に対応することにより、ほぼ瞬時にできます。 たとえば、アプリケーションの web に接続する機能に単一のマイクロ サービスでは、追加の受信トラフィックを処理するスケール アウトする必要があるアプリケーションでのみマイクロ サービス可能性があります。

アプリケーションのスケーラビリティの従来のモデルでは、永続的なデータを格納する共有の外部データ ストアでの負荷分散、ステートレスな層のあります。 ステートフルな microservices 通常が配置されているサーバー上にローカルに保存、独自の永続的なデータの管理、ネットワークのオーバーヘッドを回避するアクセスと複雑なクロス サービス操作。 これにより、データの最も高速な処理を有効にされ、キャッシュ システムの必要性を排除することができます。 さらに、拡張性の高いステートフル microservices には通常を超えると 1 台のサーバーがサポートできる、データのサイズおよび転送のスループットを管理する、インスタンス間でデータがパーティション分割します。

Microservices では、独立した更新プログラムもサポートします。 この疎 microservices では、高速で信頼性の高いアプリケーションの進化を提供します。 独立した、分散性質には、ローリング更新プログラム、単一のマイクロ サービスのインスタンスのサブセットのみが特定の時点で更新されますがサポートしています。 そのため、問題が検出された場合、バグのある更新ロールバックできます、欠陥のあるコードまたは構成ですべてのインスタンスを更新する前にします。 同様に、microservices では通常、スキーマのバージョン管理を使用して、どのマイクロ サービスに関係なくインスタンスが通信で、更新を適用しているときに、クライアントが、一貫したバージョンを表示できるようにします。

したがって、マイクロ サービス アプリケーションでは、モノリシック アプリケーション経由で多くのメリットがあります。

-   各マイクロ サービスは、比較的小さい、簡単に管理の進化です。
-   各マイクロ サービスを開発して他のサービスとは別に展開できます。
-   各マイクロ サービスできるスケール アウト個別にします。 たとえば、カタログ サービスまたはショッピング バスケット サービスは、スケール アウトされた順序付けのサービスよりも多くする必要があります。 そのため、スケール アウトする際、結果として得られるインフラストラクチャはリソースを消費より効率的にします。
-   各マイクロ サービスは、すべての問題を分離します。 たとえば、サービスで問題がある場合にだけ影響するサービスです。 他のサービスは、要求の処理を続行できます。
-   各マイクロ サービスは、最新のテクノロジを使用できます。 Microservices は独立して実行するサイド バイ サイドであるため、最新のテクノロジとフレームワーク使用できます、強制的にモノリシック アプリケーションによって使用される古いフレームワークを使用するのではなく。

ただし、マイクロ サービス ベースのソリューションでは、潜在的な欠点もあります。

-   Microservices にアプリケーションをパーティション分割する方法を選択するには、完全に独立した、エンド ツー エンド、そのデータ ソースに対する責任を含む各マイクロ サービスがある困難ことができます。
-   開発者は、複雑さと待機時間をアプリケーションに追加のサービス間の通信を実装する必要があります。
-   複数 microservices 通常の間でアトミックのトランザクションは、行うことができません。 そのため、ビジネス要件では、microservices 間最終的整合性を採用する必要があります。
-   実稼働環境では、多数の独立したサービスのセキュリティが侵害されたシステムの管理の展開および運用の複雑さがあります。
-   マイクロ サービスでのクライアントへの直接通信できるようになります microservices のコントラクトをリファクターするが困難です。 たとえば、時間の経過と共に、システムがサービスにパーティション分割方法必要がありますを変更します。 2 つ以上のサービスに分割することが 1 つのサービスと、2 つのサービスがマージ可能性があります。 クライアントを microservices と直接通信時に、このリファクタリング操作はクライアント アプリとの互換性を分割できます。

## <a name="containerization"></a>コンテナー詰め

コンテナリゼーションはなアプローチをアプリケーションとその依存関係、および配置マニフェストのファイルとして抽象化されて、環境の構成のバージョン管理されたセットは、パッケージにまとめ、ユニットとしてテスト、コンテナーのイメージとしてソフトウェア開発をし、ホスト オペレーティング システムを展開します。

コンテナーとは、分離性、リソース制御、およびポータブル オペレーティング環境、アプリケーションが他のコンテナーまたはホストのリソースに触れることがなく実行できます。 そのため、コンテナーと外観や動作、新しくインストールした物理コンピューターまたは仮想マシン。

コンテナーとバーチャル マシンの場合は、多くの類似点がある図 8-3 に示すようにします。

![](containerized-microservices-images/containersvsvirtualmachines.png "Microservices アプリケーションのスケーリング方法")

**図 8-3**: 仮想マシンとコンテナーの比較

コンテナーは、オペレーティング システムを実行するには、ファイル システムが、および場合と同様に、物理または仮想マシン、ネットワーク経由でアクセスできます。 ただし、テクノロジ、およびコンテナーによって使用される概念は、仮想マシンからかなり異なります。 仮想マシンには、アプリケーション、必要な依存関係、および完全ゲスト オペレーティング システムが含まれます。 コンテナーは、アプリケーションとその依存関係が含まれますが、(コンテナーごとに特別な仮想マシン内で実行される HYPER-V コンテナー) とは別のホスト オペレーティング システム上の独立したプロセスとして実行されている他のコンテナーと、オペレーティング システムを共有します。 そのため、コンテナーは、リソースを共有し、通常のバーチャル マシンよりも少ないリソースを必要とします。

コンテナー指向の開発と展開方法の利点は、一貫性のない環境のセットアップとそれらに付属している問題に起因する問題のほとんどがなくなることです。 さらに、コンテナーは、必要に応じて新しいコンテナーをインスタンス化を高速のアプリケーションのスケール アップ機能を許可します。

主要な概念、コンテナーの作成と操作時に次のとおりです。

-   コンテナー ホスト: 物理またはバーチャル マシン ホストのコンテナーを構成します。 コンテナー ホストでは、1 つまたは複数のコンテナーを実行します。
-   コンテナー イメージ: イメージは、相互に積み重ねられた階層ファイル システムの和集合で構成され、コンテナーの基礎となります。 状態が、イメージにないとは別の環境に展開された決して変化します。
-   コンテナー: コンテナーは、イメージのランタイム インスタンスです。
-   コンテナーの OS イメージ: コンテナーは、イメージから展開されます。 コンテナーのオペレーティング システム イメージは、場合によっては多数のイメージ レイヤーのコンテナーを構成する最初のレイヤーです。 コンテナーのオペレーティング システムは、変更不可にして、変更できません。
-   コンテナー リポジトリ: コンテナーのイメージが作成されるたびに、イメージとその依存関係がリポジトリに格納、ローカルです。 コンテナー ホストでは、これらのイメージを何度も再利用できます。 コンテナー イメージも格納できます、パブリックまたはプライベート レジストリになど[Docker Hub](https://hub.docker.com/)、別のコンテナー ホスト間で使用できるようにします。

企業はマイクロ サービスを実装するベースのアプリケーション、され、Docker には、ほとんどのソフトウェア プラットフォームとクラウドのベンダーで採用されてきましたが標準的なコンテナーの実装になると、ますますコンテナー採用することです。

EShopOnContainers 参照アプリケーションでは、図 8-4 に示すように、次の 4 つのコンテナー化バックエンド microservices をホストするのに Docker を使用します。

![](containerized-microservices-images/microservicesarchitecture.png "eShopOnContainers は、アプリケーション バックエンド microservices を参照します。")

**図 8-4**: eShopOnContainers アプリケーション バックエンド microservices の参照

参照アプリケーションのバックエンド サービスのアーキテクチャは、共同作業 microservices とコンテナーの形式で複数の自律的なサブシステムに分解されます。 各マイクロ サービス機能の 1 つの領域を提供します。 id サービス、カタログ サービス、順序付けのサービス、およびバスケット サービス。

各マイクロ サービスには、独自のデータベースは、他の microservices から完全に分離させるを許可することがあります。 必要に応じて、異なる microservices からのデータベース間の一貫性はアプリケーション レベルのイベントを使用して実現されます。 詳細については、次を参照してください。 [Microservices 間の通信](#communication_between_microservices)です。

参照アプリケーションの詳細については、次を参照してください。 [.NET Microservices: .NET アプリケーションのコンテナーをアーキテクチャ](https://aka.ms/microservicesebook)です。

<a name="communication_between_client_and_microservices" />

## <a name="communication-between-client-and-microservices"></a>クライアントと Microservices 間の通信

使用して、コンテナー化バックエンド microservices と eShopOnContainers モバイル アプリが通信する*マイクロ サービスでのクライアントへの直接*図 8-5 で表示されている通信します。

![](containerized-microservices-images/directclienttomicroservicecommunication.png "Microservices アプリケーションのスケーリング方法")

**図 8-5**: 直接クライアント-マイクロ-サービスの通信

マイクロ サービスでのクライアントへの直接通信では、モバイル アプリは、マイクロ サービスごとに異なる TCP ポートでのパブリック エンドポイントを通じて直接各マイクロ サービスに要求を行います。 、実稼働環境で、エンドポイントは通常マップ マイクロ サービスのロード バランサーは、要求を使用可能なインスタンスに配分します。

> [!TIP]
> ゲートウェイ通信の API を使用することを検討してください。 マイクロ サービスでのクライアントへの直接的な通信、大規模で複雑なマイクロ サービスを構築ベースのアプリケーションが、小規模なアプリケーションの複数の適切な場合の欠点ことができます。 ベースのアプリケーションで microservices 数万を大きなマイクロ サービスを設計時に、API ゲートウェイ通信の使用を検討します。 詳細については、次を参照してください。 [.NET Microservices: .NET アプリケーションのコンテナーをアーキテクチャ](https://aka.ms/microservicesebook)です。

<a name="communication_between_microservices" />

## <a name="communication-between-microservices"></a>Microservices 間の通信

Microservices ベースのアプリケーションは、複数のコンピューターで実行されている可能性、分散システムです。 通常、各サービス インスタンスはプロセスです。 そのため、サービスは、HTTP、TCP、Advanced Message Queuing Protocol (AMQP)、各サービスの性質によって、バイナリ プロトコルなど、プロセス間通信プロトコルを使用してをやり取りする必要があります。

マイクロ サービス-マイクロ-サービスの通信用の 2 つの一般的な方法は、データ、および軽量な非同期メッセージングの更新プログラムを複数 microservices 間で通信するときにに対してクエリを実行するときに HTTP ベースで通信の残りの部分です。

非同期メッセージングに基づいてイベント ドリブン通信は、複数の microservices 間での変更を反映するときに重要です。 この方法では、マイクロ サービスは、何か重要なときの動作、たとえば、ビジネス エンティティを更新するときにイベントを公開します。 その他の microservices は、これらのイベントをサブスクライブします。 次に、マイクロ サービス イベントを受信すると、パブリッシュされている複数のイベントになる可能性がありますさらに、独自のビジネス エンティティを更新します。 これは、公開/定期受信機能、イベント バスで通常得られます。

イベント バスにより、図 8-6 に示すように、互いを明示的に認識するコンポーネントを必要とせず、microservices 間の通信の公開/定期受信します。

![](containerized-microservices-images/eventbus.png "イベント バスで公開/定期受信します。")

**図 8-6:**イベント バスで公開/定期受信

アプリケーションの観点から、イベント バスは、発行するだけのインターフェイスを介して公開されるチャネルをサブスクライブします。 ただし、イベント バスを実装する方法が異なることができます。 たとえば、イベント バス実装でした RabbitMQ、Azure Service Bus または使用 NServiceBus MassTransit など他のサービス バス。 図 8-7 では、イベント バスを eShopOnContainers の参照をアプリケーションで使用する方法を示します。

![](containerized-microservices-images/microservicesarchitecturewitheventbus.png "参照をアプリケーションで、イベント ドリブンの非同期通信")

**図 8-7:**の参照をアプリケーションで、イベント ドリブンの非同期通信

EShopOnContainers イベント バス、RabbitMQ を使用して実装では、1 対多非同期パブリッシュ/サブスクライブ機能を提供します。 これは、イベントを発行した後があること、同じイベントをリッスンしている複数のサブスクライバーを意味します。 図 8-9 では、この関係を示します。

![](containerized-microservices-images/eventdrivencommunication.png "一対多の通信")

**図 8-9**: 一対多の通信

この一対多の通信方法は、サービス間で最終的整合性を確保する、複数のサービスにまたがるビジネス トランザクションを実装するのにイベントを使用します。 最終的な一貫したトランザクションは、一連の分散の手順で構成されます。 そのため、ユーザー プロファイル マイクロ サービス UpdateUser コマンドを受信すると、そのデータベース内のユーザーの詳細を更新し、イベント バスに UserUpdated イベントを公開します。 このイベントを受信し、応答で、それぞれのデータベースで、購入者情報を更新するバスケット マイクロ サービスと順序付けのマイクロ サービスの両方がサブスクライブしています。

> [!NOTE]
> EShopOnContainers イベント バス、RabbitMQ を使用して実装は概念実証としてのみ使用するためのものです。 実稼働システムでは、代替イベント バス実装を検討してください。

イベント バス実装については、次を参照してください。 [.NET Microservices: .NET アプリケーションのコンテナーをアーキテクチャ](https://aka.ms/microservicesebook)です。

## <a name="summary"></a>まとめ

Microservices は、アプリケーションの開発とは、先進的なクラウド アプリケーションのアジリティ、スケール、および信頼性の要件に適しています展開する方法を提供します。 することができましていないスケール アウト、独立している特定の機能領域スケールできます必要な処理電源やネットワーク帯域幅の領域を不必要にスケーリングがない、要求をサポートするためにすることを意味するは microservices の主な利点の 1 つ要求の増加が発生していないアプリケーションです。

コンテナーとは、分離性、リソース制御、およびポータブル オペレーティング環境、アプリケーションが他のコンテナーまたはホストのリソースに触れることがなく実行できます。 企業はマイクロ サービスを実装するベースのアプリケーション、され、Docker には、ほとんどのソフトウェア プラットフォームとクラウドのベンダーで採用されてきましたが標準的なコンテナーの実装になると、ますますコンテナー採用することです。


## <a name="related-links"></a>関連リンク

- [電子 (2 Mb PDF) のダウンロードします。](https://aka.ms/xamarinpatternsebook)
- [eShopOnContainers (GitHub) (サンプル)](https://github.com/dotnet-architecture/eShopOnContainers)
