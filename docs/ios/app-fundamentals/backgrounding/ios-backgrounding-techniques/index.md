---
title: iOS Backgrounding 手法
ms.prod: xamarin
ms.assetid: 011A8D48-1CDC-486A-A2B0-C4946118E7A9
ms.technology: xamarin-ios
author: bradumbaugh
ms.author: brumbaug
ms.openlocfilehash: 261507e8cbca8e94f5cabbb010dcd444c432d96c
ms.sourcegitcommit: 945df041e2180cb20af08b83cc703ecd1aedc6b0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2018
---
# <a name="ios-backgrounding-techniques"></a>iOS Backgrounding 手法

次のセクションでは、既存の backgrounding オプションと共に、次の iOS 機能について説明します。

-  [日和見的なバック グラウンド タスク](~/ios/app-fundamentals/backgrounding/ios-backgrounding-techniques/ios-backgrounding-with-tasks.md#background_tasks_in_iOS_7)-日和見的なチャンクでバック グラウンド タスクを実行して、デバイスが他の処理の起動状態にすることによってバッテリの寿命を保持します。
-  [バック グラウンド転送サービス](~/ios/app-fundamentals/backgrounding/ios-backgrounding-techniques/ios-backgrounding-with-tasks.md#background-transfers)- 確実にアップロードし、ネットワークの状態やファイルのサイズに関係なくファイルをダウンロードします。
-  [フェッチをバック グラウンド](~/ios/app-fundamentals/backgrounding/ios-backgrounding-techniques/updating-an-application-in-the-background.md#background_fetch)-システムにより決定された間隔でバック グラウンドからアプリケーションを更新します。
-  [リモート通知](~/ios/app-fundamentals/backgrounding/ios-backgrounding-techniques/updating-an-application-in-the-background.md#remote_notifications)-ユーザーがユーザーに通知するか、自動的に更新するオプションが、アプリケーションを開く前に、バック グラウンドでのコンテンツの更新をトリガーするプッシュ通知を使用します。
-  **UI の更新をバック グラウンド**- ユーザーのアプリケーションの UI を準備して、バック グラウンドからすべてのアプリケーションのスナップショットを更新します。
