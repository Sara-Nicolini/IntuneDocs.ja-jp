---
# required metadata

title: モバイル デバイス セキュリティ ポリシー設定 | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: e5ab3b76-08af-4893-b294-fb6627fdc4c6

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune のモバイル デバイス セキュリティ ポリシー設定
> [!IMPORTANT]
> Microsoft Intune では、デバイス プラットフォームごとに構成ポリシーが分割されました。それらのポリシーには、使用可能な最新の設定が含まれています。 引き続きモバイル デバイスのセキュリティ ポリシーを使用でき、既存の展開も機能します。 ただし、モバイル デバイスのセキュリティ ポリシーは将来的に削除されるため、できるだけ早く新しい構成ポリシーに移行することを計画してください。

Intune のモバイル デバイスのセキュリティ ポリシーを使用すると、組織内の管理対象デバイスに展開できるさまざまな設定を構成できます。 これらの設定を使用して、デバイスの機能とセキュリティを制御できます。

モバイル デバイス セキュリティ ポリシーは、次のデバイスの種類に対して作成および展開できます。

-   Windows RT 8.1 および登録されている Windows 8.1 デバイス

-   Windows RT

-   Windows Phone 8 および Windows Phone 8.1

-   iOS

-   Android および Samsung KNOX

> [!NOTE]
> 一部のデバイスに適用されない設定もあります。 構成できるすべての設定については、次の表を参照してください。

## セキュリティ設定

|設定の名前|Windows 8.1 および Windows RT 8.1|Windows RT|Windows Phone 8 および Windows Phone 8.1|iOS|Android および Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**モバイル デバイスのロックを解除するパスワードを要求する**|×|×|○|○|○|
|**必要なパスワードの種類**<br /><br />(数値のみや英数字など、必要なパスワードの種類を指定します)|○|○|○|○|×|
|**必要なパスワードの種類 - 文字セットの最小数**<br /><br />文字セットには、小文字、大文字、数字、および記号の 4 種類があります。 この設定では、パスワードに含める必要がある文字セットの数を指定します。 ただし、iOS デバイスの場合は、パスワードに含める必要がある記号の数を指定します。|○|○|○|○|×|
|**最小のパスワードの長さ**|○|○|○|○|○|
|**単純なパスワードを許可する**<br /><br />単純なパスワードには、"0000" や "1234" があります|×|×|○|○|×|
|**デバイスをワイプするまでの連続サインイン エラーの数**|○|○|○|○|○|
|**画面がオフになるまでの非アクティブな時間 (分)**<sup>1</sup>|○|○|○|○|○|
|**パスワードの有効期限 (日)**|○|○|○|○|○|
|**パスワードの履歴を記憶する**|○|○|○|○|○|
|**パスワードの履歴を保存する** - **前のパスワードを再利用できないようにする**|○|○|○|○|○|
|**パスワードの品質**|×|×|×|×|○|
|**ピクチャ パスワードと PIN を許可する**|○|○|×|×|×|
|**パスワードが必要になるまでの非アクティブ状態の時間 (分)**|×|×|×|○|×|
|**指紋によるロック解除を使用する**|×|×|×|iOS 7 以降|×|
iOS デバイスの場合、**[画面がオフになるまでの非アクティブな時間 (分)]** と **[ デバイスの画面がロックされるまでの非アクティブな時間 (分)]** の設定を構成する場合、順番に適用されます。 たとえば、両方の設定値を「 **5** 」分に設定すると、5 分後に画面が自動的にオフになり、さらに 5 分後にデバイスがロックされます。 ただし、ユーザーが手動で画面をオフにした場合、2 つ目の設定は即時に適用されます。 同じ例で、ユーザーが画面をオフにした後、デバイスは 5 分後にロックされます。

Windows RT を実行するデバイスにパスワードの長さポリシーを展開すると、ユーザーは、現在のパスワードがポリシー要件に準拠している場合でもパスワードを再設定するように求められます。

## 暗号化の設定

|設定の名前|Windows 8.1 および Windows RT 8.1|Windows RT|Windows Phone 8 および Windows Phone 8.1|iOS|Android および Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**モバイル デバイスの暗号化を要求する**<sup>1</sup><br /><br />Windows Phone 8 デバイスの場合、これを **[はい]**に設定する必要があります。<br /><br />iOS デバイスでの暗号化を有効にするには、 **[モバイル デバイスのロック解除にパスワードを必要とする]**設定を有効にします。|○|×|○|×|○|
|**メモリ カードの暗号化を必要とする**<br /><br />Exchange ActiveSync によって管理されるデバイスにも当てはまります。|該当なし|該当なし|n/a (アプリおよび関連付けられたデータは自動的に暗号化される)|該当なし|○|
Windows 8.1 が実行されているデバイスの追加情報

-   Windows 8.1 が実行されているデバイスで暗号化を適用するには、 [Windows の 2014 年 12 月付け MDM クライアント更新プログラム](http://support.microsoft.com/kb/3013816) を各デバイスにインストールする必要があります。

-   Windows 8.1 デバイスに対してこの設定を有効にすると、デバイスのすべてのユーザーに Microsoft アカウントが必要になります。

-   暗号化を機能させるには、デバイスが Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) ハードウェア認定要件を満たしている必要があります。

-   デバイスで暗号化を適用すると、回復キーは、ユーザーの Microsoft アカウントからしかアクセスできなくなります。また、OneDrive アカウントからアクセスする必要があります。 ユーザーの代わりにこのキーを回復することはできません。

## マルウェアの設定

|設定の名前|Windows 8.1 および Windows RT 8.1|Windows RT|Windows Phone 8 および Windows Phone 8.1|iOS|Android および Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**ネットワーク ファイアウォールを必須にする**|○|×|×|×|×|
|**SmartScreen を有効にする**|○|×|×|×|×|

## システムの設定

|設定の名前|Windows 8.1 および Windows RT 8.1|Windows RT|Windows Phone 8 および Windows Phone 8.1|iOS|Android および Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**自動更新を必須にする**|○|×|×|×|×|
|**自動更新を必須にする – 自動的にインストールする更新プログラムの最低限の分類。**<br /><br />自動的にインストールする更新プログラムの分類を選択します。<br /><br />**[重要]** - 重要として分類されたすべての更新プログラムをインストールします。<br /><br />**[推奨]** - 重要または推奨として分類されたすべての更新プログラムをインストールします。|○|×|×|×|×|
|**画面のキャプチャを許可する**|×|×|Windows Phone 8.1 のみ|○|はい (Samsung KNOX のみ)|
|**ロック画面でコントロール センターを使用する**|×|×|×|iOS 7 以降|×|
|**ロック画面で通知ビューを使用する**|×|×|×|iOS 7 以降|×|
|**ロック画面で今日ビューを使用する**|×|×|×|iOS 7 以降|×|
|**ユーザー アカウント コントロール**|○|×|×|×|×|
|**診断データの送信を使用する**|○|×|Windows Phone 8.1 のみ|○|はい (Samsung KNOX のみ)|
|**信頼されていない TLS 証明書を許可する**|×|×|×|○|×|
|**ロック中に個人用ウォレット ソフトウェアを使用する**|×|×|×|○|×|
|**工場出荷時のリセットを許可する**|×|×|×|×|はい (Samsung KNOX のみ)|


## クラウドの設定 – ドキュメントおよびデータ

|設定の名前|Windows 8.1 および Windows RT 8.1|Windows RT|Windows Phone 8 および Windows Phone 8.1|iOS|Android および Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**iCloud へのバックアップの許可**|×|×|×|○|×|
|**ドキュメントと iCloud の同期の許可**|×|×|×|○|×|
|**フォトストリームと iCloud の同期の許可**|×|×|×|○|×|
|**暗号化されたバックアップを必須にする**|×|×|×|○|×|
|**作業フォルダーの URL**<br /><br />(作業フォルダーの URL を設定して、デバイス間でドキュメントを同期できるようにします)|○|×|×|×|×|
|**Google へのバックアップの許可**|×|×|×|×|はい (Samsung KNOX のみ)|

## クラウドの設定 – アカウントおよび同期

|設定の名前|Windows 8.1 および Windows RT 8.1|Windows RT|Windows Phone 8 および Windows Phone 8.1|iOS|Android および Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Microsoft アカウントを許可する**|×|×|Windows Phone 8.1 のみ|×|×|
|**Google アカウントの自動同期を許可する**|×|×|×|×|はい (Samsung KNOX のみ)|

## 電子メールの設定

|設定の名前|Windows 8.1 および Windows RT 8.1|Windows RT|Windows Phone 8 および Windows Phone 8.1|iOS|Android および Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**ユーザーが電子メールの添付ファイルをダウンロードできるようにする**<sup>1</sup>|該当なし|該当なし|該当なし|該当なし|該当なし|
|**[電子メールを同期する期間]** は、Exchange ActiveSync によって管理されるデバイスにも当てはまります。|該当なし|該当なし|該当なし|該当なし|該当なし|
|**[選択した設定を完全にサポートしないモバイル デバイスを Exchange と同期させる (Exchange ActiveSync)]** は、Exchange ActiveSync によって管理されるデバイスにも当てはまります。|該当なし|該当なし|該当なし|該当なし|該当なし|
|**Windows メール アプリケーションで Microsoft アカウントをオプションにする**|○|×|×|×|×|
|**カスタム電子メール アカウントを許可する**|×|×|Windows Phone 8.1 のみ|×|×|

## アプリケーションの設定 - ブラウザー

|設定の名前|Windows 8.1 および Windows RT 8.1|Windows RT|Windows Phone 8 および Windows Phone 8.1|iOS|Android および Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Web ブラウザーを許可する**|×|×|Windows Phone 8.1 のみ|○|はい (Samsung KNOX のみ)|
|**オートコンプリートを使用する**|○|×|×|○|はい (Samsung KNOX のみ)|
|**ポップアップ ブロックを使用する**|○|×|×|○|はい (Samsung KNOX のみ)|
|**Cookie を使用する**|×|×|×|○|はい (Samsung KNOX のみ)|
|**プラグインを使用する**|○|×|×|×|×|
|**アクティブ スクリプティングを使用する**|○|×|×|○|はい (Samsung KNOX のみ)|
|**不正行為の警告を使用する**|○|×|×|○|×|
|**1 単語の入力でイントラネット サイトにアクセスできるようにする**<br /><br />("Bing" など、1 つの単語を使用して Internet Explorer に移動先の Web サイトを指示できるようにします)|○|×|×|×|×|
|**イントラネット ネットワークの自動検出を使用する**|○|×|×|×|×|
|**インターネットのセキュリティ レベル**|○|×|×|×|×|
|**イントラネットのセキュリティ レベル**|○|×|×|×|×|
|**信頼済みサイトのセキュリティ レベル**|○|×|×|×|×|
|**制限付きサイトのセキュリティ レベル**|○|×|×|×|×|
|**Do Not Track ヘッダーを送信する**|○|×|×|×|×|
|**エンタープライズ モード メニューへのアクセスを許可する**|○|×|×|×|×|
|**エンタープライズ モード サイト リストの場所**|○|×|×|×|×|

## アプリケーションの設定 - アプリケーション

|設定の名前|Windows 8.1 および Windows RT 8.1|Windows RT|Windows Phone 8 および Windows Phone 8.1|iOS|Android および Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**アプリケーション ストアを許可する**|×|×|Windows Phone 8.1 のみ|○|はい (Samsung KNOX のみ)|
|**アプリケーション ストアへのアクセスにパスワードを必要とする**|×|×|×|○|×|
|**アプリ内購入を使用する**|×|×|×|○|×|
|**他の管理対象ではないアプリで管理対象ドキュメントを使用する**|×|×|×|iOS 7 以降|×|
|**他の管理対象アプリで管理対象ではないドキュメントを使用する**|×|×|×|iOS 7 以降|×|
|**ビデオ会議を使用する**|×|×|×|○|×|
|**メディア ストアでアダルト コンテンツを許可する**|×|×|×|○|×|
|**アプリのインストールを許可する**|×|×|×|iOS 6 以降|×|

## アプリケーションの設定 - ゲーム

|設定の名前|Windows 8.1 および Windows RT 8.1|Windows RT|Windows Phone 8 および Windows Phone 8.1|iOS|Android および Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**ゲーム センターの友だちを使用する**|×|×|×|○|×|
|**マルチプレイヤー ゲームを使用する**|×|×|×|○|×|

## デバイス機能の設定 - ハードウェア

|設定の名前|Windows 8.1 および Windows RT 8.1|Windows RT|Windows Phone 8 および Windows Phone 8.1|iOS|Android および Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**カメラを許可する**|×|×|Windows Phone 8.1 のみ|○|○|
|**リムーバブル記憶域を許可する**|×|×|○|×|はい (Samsung KNOX のみ)|
|**Wi-Fi を許可する**|×|×|Windows Phone 8.1 のみ|×|はい (Samsung KNOX のみ)|
|**Wi-Fi テザリングを許可する**|×|×|Windows Phone 8.1 のみ|×|はい (Samsung KNOX のみ)|
|**無料 Wi-Fi スポットへの自動接続を許可する**|×|×|Windows Phone 8.1 のみ|×|×|
|**Wi-Fi スポットの報告を許可する**<br /><br />(近くにある接続を検出するために、Wi-Fi 接続に関する情報を送信する)|×|×|Windows Phone 8.1 のみ|×|×|
|**位置情報を許可する**<br /><br />(デバイスによる場所の情報の使用を許可する)|×|×|Windows Phone 8.1 のみ|×|はい (Samsung KNOX のみ)|
|**NFC を許可する**<br /><br />(近距離無線通信を使用する操作を許可する)|×|×|Windows Phone 8.1 のみ|×|はい (Samsung KNOX のみ)|
|**Bluetooth を許可する**|×|×|Windows Phone 8.1 のみ|×|はい (Samsung KNOX のみ)|
|**電源の切断を許可する**<br>この設定が無効の場合、Samsung KNOX デバイスの **[デバイスをワイプするまで許可するサインインの失敗回数]** 設定は機能しません。|×|×|×|×|はい (Samsung KNOX のみ)|

## デバイス機能の設定 - 移動体通信

|設定の名前|Windows 8.1 および Windows RT 8.1|Windows RT|Windows Phone 8 および Windows Phone 8.1|iOS|Android および Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**音声通話ローミングを許可する**|×|×|×|○|はい (Samsung KNOX のみ)|
|**データ ローミングを許可する**|○|×|×|○|はい (Samsung KNOX のみ)|
|**ローミング中の自動同期を許可する**|×|×|×|○|×|
|**SMS/MMS メッセージングを許可する**|×|×|×|×|はい (Samsung KNOX のみ)|

## デバイス機能の設定 - 機能

|設定の名前|Windows 8.1 および Windows RT 8.1|Windows RT|Windows Phone 8 および Windows Phone 8.1|iOS|Android および Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**音声アシスタントを使用する**|×|×|×|○|はい (Samsung KNOX のみ)|
|**デバイスのロック中に音声アシスタントを使用する**|×|×|×|○|×|
|**音声による発信を使用する**|×|×|×|○|はい (Samsung KNOX のみ)|
|**コピーと貼り付けを許可する**|×|×|Windows Phone 8.1 のみ|×|はい (Samsung KNOX のみ)|
|**アプリケーション間でのクリップボードの共有を許可する**|×|×|×|×|はい (Samsung KNOX のみ)|
|**YouTube を許可する**|×|×|×|×|はい (Samsung KNOX のみ)|

### 関連項目
[Microsoft Intune policies.md を使用してデバイスの設定と機能を管理する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO2-->


