---
# required metadata

title: Microsoft Intune でデバイスのコンプライアンス ポリシーを作成する |Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 5336dac0-a2cc-4cd4-8511-67e4f95bd700

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: chrisgre
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune でデバイスのコンプライアンス ポリシーを作成する
このトピックでは、デバイスが準拠しているとみなされるために従う必要があるコンプライアンス ポリシーを作成するために使用できる手順について説明します。

##  手順 1: 新しいポリシーを追加する
  [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[ポリシー]** &gt; **[コンプライアンス ポリシー]** &gt; **[追加]** の順に選択します。

  ![上部の [追加] メニューを示している Intune 管理コンソールのコンプライアンス ポリシー ページ](./media/intune-sa-3a-add-compliance-policy.png)

##  手順 2: 設定を構成する
**[ポリシーの作成]** ページで、必要に応じて以下の設定を有効にします。
  -   パスワードや暗号化などのシステムのセキュリティ設定
  -   デバイスが改造されているかどうか、Windows デバイス正常性構成証明書サービスによって正常と報告されているかどうかなどのデバイスのヘルスの設定
  -   必要な最小 OS バージョンや許可される最大 OS バージョンなどのデイバイスのプロパティの設定
![[ポリシーの作成] ページの [全般] タブのスクリーン ショット ](./media/intune-sa-3b-create-policy.png)

##  手順 3: ポリシーを保存する
終了したら、**[ポリシーの保存]** を選びます。

ポリシーは、保存した後、すぐ展開できますが、後で展開することもできます。 **[ポリシー]** ワークスペースの **[コンプライアンス ポリシー]** ノードに新しいポリシーが表示されます。

## サポートされるポリシー設定
次の表は、コンプライアンス ポリシー設定と、それらがサポートされるプラットフォームの一覧を示しています。

-------------
|Setting|iOS|Android|Windows|
|-----|----|-----|-----|
|モバイル デバイスのロックを解除するパスワードを要求する|iOS 6 以降|Android 4.0 以降 <br>Samsung KNOX Standard 4.0 以降|Windows Phone 8 以降|
|単純なパスワードを許可する|iOS 6 以降|サポートされていません|Windows Phone 8 以降|
|パスワードの最小文字数|iOS 6 以降| Android 4.0 以降<br>Samsung KNOX Standard 4.0 以降| Windows Phone 8 以降<br>Windows 8.1|
|必要なパスワードの種類|iOS 6 以降|利用不可|Windows Phone 8 以降 <br>Windows RT<br> Windows RT 8.1 <br>Windows 8.1|
|文字セットの最小数|iOS 6 以降|利用不可|Windows Phone 8 以降 <br>Windows RT<br> Windows RT 8.1 <br>Windows 8.1|
|パスワードの品質|利用不可|Android 4.0 以降 <br>Samsung KNOX Standard 4.0 以降|利用不可|
|パスワードが必要になるまでの非アクティブ状態の時間 (分)|iOS 6 以降|Android 4.0 以降<br>Samsung KNOX Standard 4.0 以降|Windows Phone 8 以降<br>Windows RT および Windows RT 8.1<br>Windows 8.1|
|パスワードの有効期限 (日数)|iOS 6 以降|Android 4.0 以降<br>Samsung KNOX Standard 4.0 以降|Windows Phone 8 以降<br>Windows RT および Windows RT 8.1<br>Windows 8.1|
|パスワードの履歴を記憶する|iOS 6 以降|Android 4.0 以降<br>Samsung KNOX Standard 4.0 以降|Windows Phone 8 以降<br>Windows RT および Windows RT 8.1<br>Windows 8.1|
|前のパスワードの再利用を防止|iOS 6 以降|Android 4.0 以降<br>Samsung KNOX Standard 4.0 以降|Windows Phone 8 以降<br>Windows RT および Windows RT 8.1<br>Windows 8.1|
|デバイスがアイドル状態から戻るときにパスワードを必須とする| 利用不可| 利用不可|[Windows] 10 Mobile|
|モバイル デバイスの暗号化を要求する|該当なし|Android 4.0 以降<br>Samsung KNOX Standard 4.0 以降|Windows Phone 8 以降<br> Windows 8.1|
|デバイスが正常と報告されることを要求する| 利用不可| 利用不可|Windows <br>[Windows] 10 Mobile|
|デバイスは改造もルート化も行われていなければならない|iOS 6 以降|Android 4.0 以降<br>Samsung KNOX Standard 4.0 以降|利用不可|
|電子メール アカウントは Intune によって管理される必要がある|iOS 6 以降|利用不可| 利用不可|
|Intune によって管理される必要のある電子メール プロファイルを選択する|iOS 6 以降|利用不可| 利用不可|
|必要な最小 OS バージョン|iOS 6 以降|Android 4.0 以降<br>Samsung KNOX Standard 4.0 以降| Windows Phone 8 以降<br>Windows 8.1|
|許可される最大 OS バージョン|iOS 6 以降|Android 4.0 以降<br>Samsung KNOX Standard 4.0 以降|Windows Phone 8 以降<br>Windows 8.1|

各プラットフォームでサポートされるコンプライアンス設定の詳細については、次のいずれかを選択してください。
> [!div class="op_single_selector"]
- [iOS デバイス向けのコンプライアンス ポリシー設定](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Android デバイス向けのコンプライアンス ポリシー設定](android-compliance-policy-settings-in-microsoft-intune.md)
- [Windows と Windows Phones 向けのコンプライアンス ポリシー設定 ](windows-compliance-policy-settings-in-microsoft-intune.md)


## 次のステップ
[コンプライアンス ポリシーを展開して監視する](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### 関連項目
[デバイス コンプライアンス ポリシーの概要](introduction-to-device-compliance-policies-in-microsoft-intune.md)


<!--HONumber=Jun16_HO2-->


