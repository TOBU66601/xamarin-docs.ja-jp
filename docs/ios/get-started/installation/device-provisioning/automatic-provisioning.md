---
title: 自動プロビジョニング
description: Xamarin.iOS が正常にインストールされたら、iOS 開発の次の手順は、iOS デバイスをプロビジョニングすることです。 このガイドでは、Visual Studio for Mac の自動署名を使用して、開発証明書とプロファイルを要求する方法について説明します。
ms.prod: xamarin
ms.assetid: 81FCB2ED-687C-40BC-ABF1-FB4303034D01
ms.technology: xamarin-ios
author: asb3993
ms.author: amburns
ms.date: 11/17/2017
ms.openlocfilehash: 01818d2870c7cf59a0f15385dbb3565f07400ff0
ms.sourcegitcommit: 945df041e2180cb20af08b83cc703ecd1aedc6b0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2018
---
# <a name="automatic-provisioning"></a>自動プロビジョニング

_Xamarin.iOS が正常にインストールされたら、iOS 開発の次の手順は、iOS デバイスをプロビジョニングすることです。このガイドでは、Visual Studio for Mac の自動署名を使用して、開発証明書とプロファイルを要求する方法について説明します。_

## <a name="requirements"></a>必要条件

- Visual Studio for Mac 7.3 以降
- Xcode 9 以降

> [!IMPORTANT]
> このガイドでは、Visual Studio for Mac を使用して Apple デバイスの展開を設定する方法と、アプリケーションを展開する方法について説明します。 この処理と、Windows 上の Visual Studio で同じ処理を実行する方法の手動の手順については、「[Manual Povisioning](~/ios/get-started/installation/device-provisioning/manual-provisioning.md)」(手動プロビジョニング) ガイドの詳細な手順に従うことをお勧めします。

## <a name="enabling-automatic-signing"></a>自動署名を有効にする

自動署名プロセスを開始する前に、Visual Studio for Mac で Apple ID を追加しておく必要があります。手順については、「[Apple Account Management](~/cross-platform/macios/apple-account-management.md)」(Apple アカウントの管理) ガイドを参照してください。 Apple ID を追加すると、関連する_チーム_を使用できます。 こうすることで、チームに対して証明書、プロファイル、およびその他の ID を作成できます。 プロビジョニング プロファイルに含まれるアプリ ID のプレフィックスを作成するためにもチーム ID が使用されます。 チーム ID を使用することで、Apple は開発者の身元を検証できます。

iOS デバイスで開発のためにアプリに自動的に署名するには、次の手順を実行します。

1. Visual Studio for Mac で iOS プロジェクトを開きます。

2. **Info.plist** ファイルを開きます。

3. **[署名]** セクションで、**[自動プロビジョニング]** を選択します。

    ![チーム セレクターのドロップダウン](automatic-provisioning-images/image2.png)

4. **[チーム]** ドロップダウンからチームを選択します。

6. 数秒後に、署名証明書とプロビジョニング プロファイルが作成されます。

    ![証明書とプロファイルが正常に作成されました](automatic-provisioning-images/image5.png)

    自動署名に失敗すると、**自動署名パッド**にエラーの理由が表示されます。

## <a name="triggering-automatic-provisioning"></a>自動プロビジョニングのトリガー

自動署名を有効にすると、次のいずれかの状況になったときに、Visual Studio for Mac で必要に応じてこれらのアーティファクトが更新されます。

* iOS デバイスを Mac に接続した
    - これで、デバイスが Apple Developer Portal に登録されているかどうかが自動的に確認されます。 登録されていない場合は追加され、それを含む新しいプロビジョニング プロファイルが生成されます。
* アプリのバンドル ID が変更された
    - これでアプリ ID が更新されます。 このアプリ ID が含まれる新しいプロビジョニング プロファイルが作成されます。
* Entitlements.plist ファイルで、サポートされる機能が有効になります。
    - この機能がアプリ ID に追加され、アプリ ID が更新された新しいプロビジョニング プロファイルが生成されます。
    - 現在はサポートされていない機能もあります。 サポートされる機能の詳細については、「[Working with Capabilities](~/ios/deploy-test/provisioning/capabilities/index.md)」(機能の使用) ガイドを参照してください。


## <a name="related-links"></a>関連リンク

- [無料プロビジョニング](~/ios/get-started/installation/device-provisioning/free-provisioning.md)
- [アプリの配布](~/ios/deploy-test/app-distribution/index.md)
- [トラブルシューティング](~/ios/deploy-test/troubleshooting.md)
- [Apple - アプリ配布ガイド](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/Introduction/Introduction.html)
