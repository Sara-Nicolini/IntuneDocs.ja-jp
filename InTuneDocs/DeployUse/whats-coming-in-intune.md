---
# required metadata

title: 今後予定されている機能 | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 05/17/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d

# optional metadata

ROBOTS: noindex,nofollow
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune に今後予定されている機能
ここに記載されている情報は、秘密保持契約書のもとごく限られた範囲について開示されたものであり、また今後変更される可能性があります。 ここに挙げられている機能は、発売日に間に合わない可能性があり、その場合は将来のリリースを待たなければなりません。 正式なリリースに向けてパイロット (フライト) テスト中の機能もあります。 ご不明な点や懸念される事項がある場合は、Intune の開発チームまたは PM にお問い合わせください。

このページは定期的に更新されます。 定期的にこちらのページをご覧のうえ最新の機能をチェックしてください。

Intune に関して以下の機能が現在開発されています。 そのすべての機能は、ハイブリッド環境 (Configuration Manager と Intune の共存環境) でもサポートされます。 最新のハイブリッド機能の詳細については、[ハイブリッド環境の新機能に関するページ](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx)を参照してください。

## Intune の通信
- **Intune サービス正常性に関する情報。** Intune のこの情報は、他の Microsoft サービスと共に中央の場所に移動されました。 そのため、この情報は [Office 365 管理ポータル](https://portal.office.com/Admin/Default.aspx)の [サービス正常性] で参照できるようになりました。 詳細については、[このブログ投稿](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)を参照してください。

- **メッセージ センターの UI オンボード。** [Office 365 管理ポータル](https://portal.office.com/)に Intune を移行する取り組みの一環として、新機能をはじめとする告知にメッセージ センターを活用することとなりました。 また Office 365 Admin モバイル コンパニオン アプリをインストールすることによって通知を携帯電話で受け取り、ユーザーや配布リストに宛てて簡単にメッセージを転送することもできます。
メッセージ センターの運用は、5 月リリースからとなります。更新プログラムが完成した時点で通知します。Intune に追加された機能や強化された機能についての情報を盛り込む予定です。 メッセージ センターの情報をチェックするには、[Office 365 管理ポータル](https://portal.office.com/)にログインし、左側のナビゲーション ウィンドウで**メッセージ センター**のオプションを選択してください。

## アプリ管理
- **MAM ポリシーで管理できるようになった新しいアプリ。** Android 用の Microsoft Word、Excel、および PowerPoint の各アプリを、Intune に登録されていないデバイス上の MAM ポリシーに関連付けられるようになりました。 サポートされているアプリの完全なリストについては、[Microsoft Intune アプリケーション パートナー ページ](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)の Microsoft Intune モバイル アプリケーション ギャラリーを参照してください。


- **ブラウザーの条件付きアクセス。** Exchange Online と SharePoint Online 用の条件付きアクセス ポリシーを設定すると、管理下にあって、かつ条件を満たした iOS デバイスと Android デバイスに、Exchange Online と SharePoint Online へのアクセスを限定することができます。 Outlook Web Access (OWA) や SharePoint サイトにエンド ユーザーが iOS または Android デバイスでサインインしようとすると、そのデバイスを Intune に登録するよう求めるメッセージが表示されます。また条件を満たしていないことが問題になっている場合は、その問題を解消してから、サインインを試行するように求められます。
<!---TFS 1175844--->

- **MAM SDK: PIN の長さの構成に対応。** デバイス PIN と同様、MAM アプリに使用する PIN の長さを指定できるようになります。 この場合エンド ユーザーは、管理者が設定した新しい制限に従う必要があります。 入力文字数が増える分、PIN 画面の外観が若干調整されます。
<!--- TFS 1104753--->

- **Android 用 Skype for Business。** Skype for Business を MAM の対象にできるようになりました (登録ポリシー不要)。  ユーザーがログインすると、MAM ポリシーが適用されます。
<!--- TFS item 1248444 --->

- **iOS 用 Skype for Business。** Skype for Business を MAM の対象にできるようになりました (登録ポリシー不要)。  ユーザーがログインすると、MAM ポリシーが適用されます。
<!--- TFS item 1248443 --->

### Xamarin のサポート
以下のシナリオで、Microsoft Intune アプリ SDK のサポート対象に Xamarin アプリが追加されます。

- Intune SDK を使用して既存の基幹業務アプリのコードを変更する、または新しいアプリを作成する。 プラグインは、[Microsoft Intune Github](https://github.com/msintuneappsdk) ページから入手できます。
- Intune アプリ ラッピング ツールを使用して既存の基幹業務アプリを MAM に対応させる。

どの方法を使用するかについては、「[Microsoft Intune によるモバイル アプリケーション管理のためにアプリを準備する方法を決める](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)」を参照してください。
<!--- TFS 1061478 & TFS 1152340--->


## デバイス管理
- **Windows PC のリモート アシスタンス セッション。** Windows デスクトップ エージェントによって管理された PC では、TeamViewer との連携によって、管理対象コンピューターとのリモート アシスタンス セッションを確立することができます。エンド ユーザーのヘルプデスク部門でこの機能を活かすことができます。 Windows 7、8、8.1、10 が対象となります。
<!--- TFS 1284856--->



## [ポータル サイト]

- **エンド ユーザーへのトースト通知。** エンド ユーザーがポータル サイトからデバイスの登録または削除を行う際に、Android ポータル サイト アプリからのトースト通知が表示されるようになりました。
- **デバイス ID バナーによってエンド ユーザーへの情報提供を拡充。** エンド ユーザーがポータル サイトを使用する際に選択したデバイスの視認性が向上しています。 間違ったデバイスを選択した場合は、ホーム ページ バナー上のリンクをタップして正しいデバイスを選択できます。
<!--- TFS 1231157--->

- **Android ポータル サイト アプリでのデバイス登録マネージャー アカウントへの変更。** パフォーマンスと拡張性を高めるために、Intune の Android ポータル サイト アプリの **[デバイス]** ペインにはすべてのデバイス登録マネージャー (DEM) デバイスが表示されなくなります。 アプリを実行しているローカル デバイスのみが、ポータル サイト アプリ経由で登録されている場合にだけ表示されます。 ローカル デバイスに対する操作は DEM で実行できますが、他の登録デバイスのリモート管理を実行できるのは、Intune 管理コンソールからのみとなります。

- **iOS ポータル サイト アプリのデバイス登録マネージャー アカウントへの変更。** パフォーマンスと拡張性を高めるために、Intune の iOS ポータル サイト アプリの [デバイス] ペインには、すべてのデバイス登録マネージャー (DEM) デバイスが表示されなくなります。 アプリを実行しているローカル デバイスのみ、ポータル サイト アプリ経由で登録されている場合にだけ表示されます。 ローカル デバイスに対する操作は DEM で実行できますが、他の登録デバイスのリモート管理は、Intune 管理コンソールから実行する必要があります。  また、Apple Device Enrollment Program または Apple Configurator ツールでの DEM アカウントの使用は廃止されます。 共有 iOS デバイスに関しては、どちらの登録手段も既にユーザーレスの登録がサポートされています。  共有デバイスのユーザーレスの登録が利用できない場合のみ DEM アカウントを使用してください。



## 廃止予定のサービス
**カスタム グループを対象とした通知規則の廃止。**
Intune の通知規則では、Intune からの電子メール アラートの送信先が定義されます。 現時点では、作成した Intune デバイス グループ内のデバイスのすべてのユーザーに電子メールを送信するように通知規則を構成することができます。 2016 年 6 月 1 日頃以降、ユーザーが作成したグループを対象とすることはできなくなります。

現在、Microsoft Intune 管理コンソールから作成したグループを通知規則の対象とするには、以下の手順を実行します。

**[管理者]** ワークスペースで、**[通知規則]** > **[新しい規則の作成]** の順にクリックします。

通知規則の作成ウィザードの手順 2. で、規則の対象とするデバイス グループを選択します。 この "デバイス グループの選択" の手順は Intune コンソールから削除されます。

この変更に向けた準備は次のように予定されています。
- 2016 年 6 月に、新しいテナントでは通知規則の作成ウィザードの手順 2. が表示されなくなります。 既存のテナントは影響を受けません。
- 2016 年 8 月頃に、既存の一部のテナントではウィザードの "デバイス グループの選択" が表示されなくなります。
- 2016 年 10 月頃には、すべてのテナントでウィザードの "デバイス グループの選択" が表示されなくなる予定です。

<!---   TFS 1278864--->
**iOS ポータル サイト アプリのサポートの変更。**
今後数か月で、iOS 用 Microsoft Intune ポータル サイト アプリが更新され、iOS 8.0 以降を実行しているデバイスのみがサポートされるようになります。 したがって、ユーザーは iOS 8.0 より前のバージョンを実行する新しいデバイスを登録できなくなります。 iOS 8.0 より前のバージョンを実行している登録済みのデバイスは引き続き管理されます。また、期間限定で、ポータル サイト アプリも引き続き使用できます。 ただし、最新バージョンのポータル サイト アプリにアクセスする場合、デバイスは iOS 8.0 以降にある必要があります。 新しい Intune の機能を最大限に活用するには、iOS 8.0 以降に更新するようユーザーに通知することをお勧めします。  

- **Intune Viewer アプリ。** 新しい RMS 共有アプリのリリースに伴い、2016 年 8 月以降、次の Intune Viewer アプリを削除する予定です。
    - Intune AV Viewer
    - Intune PDF Viewer
    - Google Play の Android 用 Intune Image Viewer

  Intune Viewer アプリを使用する代わりに、Android 用の新しい Rights Management アプリ (RMS 共有) を使用することをお勧めします。そうすることで、3 つのアプリを個別にではなく、1 つのアプリを展開して、Android デバイス上の企業ファイルを安全に表示することができます。 RMS 共有アプリ (ドキュメントへのリンクを含む) の詳細を確認してください。






### 関連項目
最近の開発状況について詳しくは、「[Microsoft Intune の新機能](whats-new-in-microsoft-intune.md)」をご覧ください。


<!--HONumber=May16_HO5-->


