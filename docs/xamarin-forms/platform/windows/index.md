---
title: Windows プラットフォームの機能
ms.prod: xamarin
ms.assetid: F6EA9E49-FB3E-442F-AF13-B7AD0C80D11F
ms.technology: xamarin-forms
author: davidbritch
ms.author: dabritch
ms.date: 03/20/2017
ms.openlocfilehash: ab6b12738028b4f3439629f334ed5429244f4d5a
ms.sourcegitcommit: 945df041e2180cb20af08b83cc703ecd1aedc6b0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2018
---
# <a name="windows-platform-features"></a>Windows プラットフォームの機能

Windows プラットフォーム用の Xamarin.Forms アプリケーションを開発すると、Visual Studio が必要です。 [要件 ページ](~/xamarin-forms/get-started/installation.md)の詳細についてには、の前提条件が含まれています。

![](images/allhanselman.png "Windows で実行されている Xamarin.Forms アプリケーション")

## <a name="platform-support"></a>プラットフォームのサポート

Visual Studio で使用可能な Xamarin.Forms テンプレートには、既定で 1 つの Windows プロジェクトが含まれます。

* **ユニバーサル Windows プラットフォーム アプリ**-Windows 10 用 Xamarin.Forms アプリを最適化することもできます。 ユニバーサル (UWP) アプリは、電話、タブレット、およびデスクトップ デバイスで実行できます。

Visual Studio に正しい開発オプションをインストールしている場合は、することはも[追加](installation/index.md)これらのプロジェクトを Windows の旧バージョンをサポートするタイプ。

* **Windows 8.1** - タブレットに Xamarin.Forms アプリを展開することができ、Windows 8.1 アプリとしてのフォーム ファクター デスクトップ プロジェクトの WinRT コントロールを使用します。
* **Windows Phone 8.1** -Xamarin.Forms が WinRT を使用して Windows Phone 8.1 プラットフォームを完全にサポートします。 Windows Phone 8.1 のサポートを使用してアプリの外観は、Silverlight をベースとする、以前の Xamarin.Forms Windows Phone アプリに異なる場合があります。


> [!NOTE]
> Xamarin.Forms 1.x、2.x サポート_Windows Phone 8 Silverlight_アプリケーションの開発、ただしこのプロジェクトの種類は廃止されました。


## <a name="getting-started"></a>作業の開始

移動して**ファイル > 新規 > プロジェクト**Visual Studio での 1 つを選択し、**クロスプラット フォーム > Blank App (Xamarin.Forms)**作業を開始するテンプレートです。

以前の Xamarin.Forms ソリューションまたは macOS などで作成したものは必要ありません上に示したすべての Windows プロジェクト (手動で追加する必要があります)。
Windows プラットフォームを対象とする中にない場合、ソリューションでは、アクセス、[セットアップ手順](installation/index.md)に必要な Windows プロジェクトの種類/秒を追加します。


## <a name="samples"></a>サンプル

[すべてのサンプル](https://github.com/xamarin/xamarin-forms-book-preview-2)Charles Petzold 帳簿の[ *Xamarin.Forms を使用したモバイル アプリを作成する*](~/xamarin-forms/creating-mobile-apps-xamarin-forms/index.md) Windows Phone 8.1、Windows 8.1、および (Windows 10) 用のユニバーサル Windows プラットフォームのプロジェクトが含まれます。

["Scott Hanselman"デモ アプリ](https://github.com/jamesmontemagno/Hanselman.Forms)は個別に使用し、Apple Watch、Android を着用プロジェクトも含まれます (それぞれ、Xamarin.iOS および Xamarin.Android を使用して、Xamarin.Forms で稼働していないこれらのプラットフォーム)。


## <a name="related-links"></a>関連リンク

- [セットアップの Windows プロジェクト](~/xamarin-forms/platform/windows/installation/index.md)
