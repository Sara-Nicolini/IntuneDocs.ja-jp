---
# required metadata

title: Microsoft Intune コンソールでモバイル アプリケーション管理ポリシーを構成して展開する | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: b4fb33a8-a2fa-4353-bd89-5bda48b68e83

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: joglocke
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune コンソールでモバイル アプリケーション管理ポリシーを構成して展開する
Microsoft Intune のモバイル アプリケーション管理ポリシーでは、会社のコンプライアンスとセキュリティ ポリシーに合わせて展開するアプリの機能を変更できます。 たとえば、管理対象アプリでの切り取り、コピー、および貼り付け操作を制限することや、管理対象ブラウザー内ですべての Web リンクを開くようにアプリを構成することができます。

モバイル アプリケーション管理ポリシーのサポート:

-   Android 4 以降を実行するデバイス。

-   iOS 7 以降を実行するデバイス。

> [!TIP] モバイル アプリケーション管理ポリシーでは、Intune に登録されているデバイスがサポートされます。
>
> Intune で管理されていないデバイスのアプリ管理ポリシーを作成する方法については、「[Protect app data using mobile app management policies with Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)」 (Microsoft Intune でモバイル アプリケーション管理ポリシーを使用してデータを保護する) を参照してください。

他の Intune ポリシーとは異なり、モバイル アプリケーション管理ポリシーは直接展開しません。 代わりに、制限するアプリにポリシーを関連付けます。 アプリがデバイスにデプロイされ、インストールされると、指定した設定が有効になります。

アプリに制限を適用するには、アプリに Microsoft Intune アプリ SDK を組み込む必要があります。 この種類のアプリを取得するには、次の 3 つの方法があります。

-   **ポリシー管理型アプリを使用する** - アプリ SDK が組み込まれています。 この種類のアプリを追加するには、iTunes ストアや Google Play などのアプリ ストアからアプリへのリンクを指定します。 それ以上の処理は、この種類のアプリには必要ありません。 「[Microsoft Intune のモバイル アプリケーション管理ポリシーと共に使用できるアプリ](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)」の一覧を参照してください。

-   **"ラップされた" アプリを使用する** - **Microsoft Intune アプリ ラッピング ツール**を使用して、アプリ SDK を含むように再パッケージされたアプリ。 通常、このツールは、社内で作成された企業アプリの処理に使用されます。 このツールを使用して、アプリ ストアからダウンロードされたアプリを処理することはできません。 「[Microsoft Intune アプリ ラッピング ツールでモバイル アプリケーション管理のために iOS アプリを準備する](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)」および「[Microsoft Intune アプリ ラッピング ツールでモバイル アプリケーション管理のために Android アプリを準備する](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)」を参照してください。

- **Intune アプリ SDK を組み込む独自のアプリを作成する** - Intune アプリ SDK を使用すると、作成中のアプリにアプリ管理機能を組み込むことができます。 詳細については、「[Intune アプリ SDK の概要](/develop/intune-app-sdk)」を参照してください。

アプリ ラッピング ツールと Intune アプリ SDK のどちらを選ぶかについては、「[Microsoft Intune によるモバイル アプリケーション管理のためにアプリを準備する方法を決める](/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)」を参照してください。

iOS や Android 用の Outlook アプリなど、管理対象アプリの一部は**複数の ID** をサポートします。 つまり、Intune により、アプリでは管理設定が会社のアカウントまたはデータのみに適用されます。

Outlook アプリの使用例を次に示します。

-   ユーザーが会社と個人の電子メール アカウントを構成した場合、Intune は、会社のアカウントのみに管理設定を適用し、個人のアカウントは管理しません。

-   デバイスが廃止された場合や登録解除された場合は、会社の Outlook データだけがデバイスから削除されます。

-   使用する会社のアカウントは、デバイスを Intune に登録するときに使用したものと同じアカウントにする必要があります。

> [!TIP] Intune を Configuration Manager とともに使用している場合は、「[Configuration Manager のモバイル アプリケーション管理ポリシーを使用してアプリを制御する方法](https://technet.microsoft.com/library/mt131414.aspx)」を参照してください。

## モバイル アプリケーション管理ポリシーを使用したアプリの作成と展開

-   **手順 1:** ポリシー管理型アプリへのリンクを取得して、ラップされたアプリを作成するか、Intune アプリ SDK を使用して MAM 対応アプリを作成する。

-   **手順 2:** クラウド ストレージにアプリを公開する。

-   **手順 3:** モバイル アプリケーション管理ポリシーを作成する。

-   **手順 4:** アプリを展開し、アプリをモバイル アプリケーション管理ポリシーに関連付けるオプションを選択する。

-   **手順 5:** アプリの展開を監視する。

## **手順 1:** ポリシー管理型アプリへのリンクを取得して、ラップされたアプリを作成するか、Intune アプリ SDK を使用して MAM 対応アプリを作成する。

-   **アプリ ストアでポリシー管理型アプリへのリンクを取得するには** - アプリ ストアから、デプロイするポリシー管理型アプリの URL を見つけてメモします。

    たとえば、Microsoft Word for iPad アプリの URL は、**https://itunes.apple.com/jp/app/microsoft-word-for-ipad/id586447913?mt=8** です。


## **手順 2:** クラウド ストレージにアプリを公開する
管理対象アプリを公開する手順は、公開するのがポリシー管理型アプリであるか、Microsoft Intune App Wrapping Tool for iOS を使用して処理されたアプリであるかによって異なります。

#### ポリシー管理型アプリを公開するには

1.  アプリをクラウド ストレージにアップロードする準備ができたら、「[Microsoft Intune でモバイル デバイスのアプリを追加する](add-apps-for-mobile-devices-in-microsoft-intune.md)」の手順に従います。

2.  iOS アプリの場合は、[ **このソフトウェアをデバイスで使用可能にする方法を選択します**] の [ **App Store からの管理された iOS アプリ**] を選択します。

    Android アプリの場合は、[ **外部リンク**] を選択します。

3.  [ **URL を指定する**] で、前にメモしたポリシー管理型アプリの URL を入力します。

アップロードが完了すると、アップロードされたアプリの [ **ソフトウェア プロパティ** ] ページの [ **アプリ管理ポリシー** ] に [ **はい** ] と表示されます。

アプリが正常にアップロードされたことを確認したら、手順 3. に進みます。

#### Microsoft Intune アプリ ラッピング ツールを使用して処理されたアプリを発行するには

1.  アプリをクラウド ストレージにアップロードする準備ができたら、「[Microsoft Intune でモバイル デバイスのアプリを追加する](add-apps-for-mobile-devices-in-microsoft-intune.md)」の手順に従います。

2.  [ **このソフトウェアをデバイスで使用可能にする方法を選択します**] の [ **ソフトウェア インストーラー**] を選択します。

3.  **[ソフトウェア インストーラーのファイルの種類]** の **[iOS アプリケーション パッケージ (&#42;.ipa ファイル)]** を選択します。

アップロードが完了すると、アップロードされたアプリの [ **ソフトウェア プロパティ** ] ページの [ **アプリ管理ポリシー** ] に [ **はい** ] と表示されます。

アプリが正常にアップロードされたことを確認したら、手順 3. に進みます。

## **手順 3:** モバイル アプリケーション管理ポリシーを作成する

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[ポリシー]** &gt; **[概要]** &gt; **[ポリシーの追加]** の順に選択します。

2.  アプリを構成するデバイスの種類に応じて、次のいずれかの [ **ソフトウェア** ] ポリシーを構成およびデプロイします。

    -   **モバイル アプリケーション管理ポリシー (Android 4 以降)**

    -   **モバイル アプリケーション管理ポリシー (iOS 7 以降)**

    推奨される設定を使用することも、設定をカスタマイズすることもできます。 詳細については、「[Microsoft Intune ポリシーを使用してデバイスの設定と機能を管理する](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)」を参照してください。

3.  必要に応じて、次の設定を構成します。 オプションは、ポリシーを構成するデバイスの種類によって異なる場合があります。

|設定の名前|説明|
    |---------|--------------------|
    |**名前**|このポリシーの名前を指定します。|
    |**説明**|必要に応じて、このポリシーの説明を指定します。|
    |**[Web コンテンツを会社の管理対象ブラウザーで表示するように制限する]**|この設定が有効の場合、アプリ内のすべてのリンクは、管理対象ブラウザーで開きます。 このオプションを有効にするには、デバイスにこのアプリをデプロイしている必要があります。|
    |[**Android のバックアップを禁止** ] または [ **Prevent iTunes および iCloud のバックアップを禁止**]|アプリからのすべての情報のバックアップを無効にします。|
    |**[アプリで他のアプリへのデータ転送を許可する]**|このアプリがデータを送信できる、送信先のアプリを指定します。 いずれのアプリへのデータ転送も許可しない、他の管理対象アプリへの転送のみを許可する、または任意のアプリへの転送を許可する選択ができます。 この設定でモバイル デバイスの "**開く**" 機能の使用を制御することはできません。<br /><br />たとえば、データ転送を許可しない場合は、SMS メッセージング、連絡先への画像の割り当て、Facebook や Twitter への投稿などのサービスへのデータ転送を制限します。<br /><br />iOS デバイスの場合、管理されたアプリと管理されていないアプリ間のドキュメント転送を防ぐには、**[管理されていないその他のアプリで管理されたドキュメントを許可する]** 設定を無効にするモバイル デバイスのセキュリティ ポリシーを構成し、デプロイする必要もあります。他の管理対象アプリへの転送のみを許可するように選択した場合、それぞれの種類のコンテンツを開くために、Intune PDF Viewer および Image Viewer (デプロイされている場合) が使用されます。<br /><br />さらに、このオプションを **[ポリシーで管理されているアプリ]** または **[なし]** に設定すると、Spotlight 検索を使用してアプリ内のデータを検索できる iOS 9 の機能がブロックされます。|
    |**[アプリで他のアプリからのデータの受信を許可する]**|このアプリがデータを受信できる、受信元のアプリを指定します。 いずれのアプリからのデータ転送も許可しない、他の管理対象アプリからの転送のみを許可する、または任意のアプリからの転送を許可する選択ができます。<br /><br />複数の ID をサポートする iOS アプリの場合 (Intune は管理設定を会社アカウントまたはアプリ内のデータにのみ適用します)、モバイル アプリケーション管理ポリシーが適用された登録済みのデバイスでは、ユーザーがモバイル アプリケーション管理ポリシーによって管理されていないアプリからデータにアクセスしたときに、そのデータは会社のデータとして扱われ、ポリシーによって保護されます。|
    |**[[名前を付けて保存] を禁止]**|このポリシーを使用するすべてのアプリで個人のクラウド ストレージの場所 (個人用の OneDrive や Dropbox など) にデータを保存する **[名前を付けて保存]** オプションの使用を無効にします。|
    |**[切り取り、コピー、および他のアプリでの貼り付けを制限する]**|切り取り、コピー、および貼り付け操作を、アプリで使用する方法を指定します。 次の中から選択します。<br /><br />**[ブロック]** - このアプリと他のアプリの間で、切り取り、コピー、および貼り付け操作を許可しません。<br /><br />**[ポリシー管理型アプリ]** - このアプリと他の管理対象アプリ間のみで、切り取り、コピー、および貼り付け操作を許可します。<br /><br />**[ポリシー管理型アプリと貼り付け]** - このアプリからのデータの切り取りまたはコピーと、他の管理対象アプリへの貼り付けのみを許可します。 任意のアプリからのデータの切り取りまたはコピーと、このアプリへの貼り付けを許可します。<br /><br />**[すべてのアプリ]** - このアプリとの切り取り、コピー、および貼り付けの操作に制限はありません。<br /><br />管理対象アプリ間でデータをコピーして貼り付けるには、両方のアプリで **[ポリシー管理型アプリ]** または **[ポリシー管理型アプリと貼り付け]** 設定が構成されている必要があります。|
    |**[アクセスには簡易暗証番号が必要]**|このアプリを使用するための暗証番号の入力をユーザーに要求します。 ユーザーは、アプリを初めて実行するときに、この暗証番号の設定が求められます。|
    |**[暗証番号をリセットするまでの試行数]**|暗証番号のリセットが必要になるまでにユーザーが行うことができる、暗証番号の入力回数を指定します。|
    |**[アクセスには会社の資格情報が必要]**|アプリにアクセスする前に会社のログイン情報の入力をユーザーに要求します。|
    |**[アクセスには会社のポリシーに準拠したデバイスが必要]**|デバイスが脱獄または root 化されていない場合にのみ、アプリを使用できるようにします。|
    |**[(分数) 後に、アクセス要件を再確認する]**|[ **タイムアウト** ] フィールドに、アプリの起動後にアプリのアクセス要件を再確認するまでの時間を指定します。|
    |**[オフラインの猶予期間]**|デバイスがオフラインの場合は、アプリのアクセス要件を再確認するまでの時間を指定します。|
    |**[アプリ データの暗号化]**|SD カードなど、外部に格納されているデータを含む、このアプリに関連するすべてのデータを暗号化することを指定します。<br /><br />**iOS 用の暗号化**<br /><br />Intune モバイル アプリケーション管理ポリシーに関連付けられているアプリでは、データは OS によって提供されるデバイス レベルの暗号化を使用して、格納中に暗号化されます。 これは、IT 管理者によって設定される必要があるデバイスの暗証番号ポリシーを介して有効になります。 暗証番号が必要な場合、モバイル アプリケーション管理ポリシーの設定に従ってデータが暗号化されます。 Apple のドキュメントで説明されているように、 [iOS 7 で使用されるモジュールは、FIPS 140-2 で認定されています](http://support.apple.com/en-us/HT202739)。<br /><br />**Android 用の暗号化**<br /><br />Intune モバイル アプリケーション管理ポリシーに関連付けられているアプリでは、暗号化は Microsoft によって提供されます。 データは、ファイル I/O 操作中に同期的に暗号化されます。  デバイス ストレージ上のコンテンツは常に暗号化されます。 この暗号化方法は FIPS 140-2 で認定されていません。|
    |[**画面キャプチャをブロック** ] (Android デバイスのみ)|このアプリを使用するときに、デバイスの画面キャプチャ機能をブロックするように指定します。|

4.  終了したら、**[ポリシーの保存]** を選びます。

 **[ポリシー]** ワークスペースの **[構成ポリシー]** ノードに新しいポリシーが表示されます。

## **手順 4:** アプリをモバイル アプリケーション管理ポリシーに関連付け、アプリを展開する
アプリをデプロイし、必ず [ **モバイル アプリの管理** ] ページでモバイル アプリケーション管理ポリシーを選択して、ポリシーをアプリに関連付けます。

詳細については、「[Deploy apps in Microsoft Intune](deploy-apps.md)」 (Microsoft Intune でアプリを展開する) を参照してください。

> [!IMPORTANT] iOS 7.1 以前のオペレーティング システムを実行しているデバイスの場合、関連付けられているポリシーはアプリのアンインストール時に削除されません。
>
> Intune からデバイスの登録を解除すると、ポリシーはアプリからは削除されません。ポリシーが適用されているアプリは、アプリのアンインストールおよび再インストール後もポリシー設定を保持します。

### アプリが既にデバイスに展開されている場合の対処方法
アプリを展開する際に、対象とするユーザーやデバイスのいずれかにアプリの管理対象外バージョンが既にインストールされている (例: ユーザーがアプリ ストアから Microsoft Word をインストールしている) 状況が発生する場合があります。

この場合は、構成した管理対象バージョンをインストールできるように、管理対象外バージョンを手動でアンインストールするようにユーザーに依頼する必要があります。

ただし、iOS 9 以降を実行するデバイスの場合は、Intune が自動的に、既存アプリの管理を引き継ぐための権限を与えるようユーザーに要求します。 ユーザーが同意すると、アプリは Intune による管理の対象になり、アプリに関連付けられたすべてのモバイル アプリケーション管理ポリシーも適用されます。

> [!TIP] デバイスが監視モードの場合は、Intune はユーザーに権限を要求せずに、既存アプリの管理を引き継ぎます。

## **手順 5:** アプリの展開を監視する。
モバイル アプリケーション管理ポリシーに関連付けられたアプリを作成し、デプロイしたら、次の手順を使用してアプリを監視し、ポリシーの競合を解決します。

#### デプロイの状態を表示するには

1.  [Microsoft Intune 管理コンソール](https://manage.microsoft.com)で、**[グループ]** &gt; **[概要]** の順に選択します。

2.  次の手順のいずれかを実行します。

    -   **[すべてのユーザー]** を選択し、デバイスを確認するユーザーをダブルクリックします。 **[ユーザーのプロパティ]** ページで、**[デバイス]** を選択し、確認するデバイスをダブルクリックします。

    -   **[すべてのデバイス]** &gt; **[すべてのモバイル デバイス]** の順に選択します。 **[デバイス グループのプロパティ]** ページで、**[デバイス]** を選択し、確認するデバイスをダブルクリックします。

3.  **[モバイル デバイスのプロパティ]** ページで、**[ポリシー]** を選択して、デバイスにデプロイされているモバイル アプリケーション管理ポリシーの一覧を表示します。

4.  状態を表示するモバイル アプリケーション管理ポリシーを選択します。 下のペインで、ポリシーの詳細を表示し、ノードを展開してその設定を表示します。

5.  各モバイル アプリケーション管理ポリシーの [ **状態** ] 列に、[ **準拠**]、[ **準拠 (保留中)**]、または [ **エラー** ] が表示されます。 選択したポリシーに 1 つまたは複数の設定の競合がある場合、このフィールドに [ **エラー** ] が表示されます。

6.  競合を識別したら、競合するポリシー設定を変更して同じ設定を使用するようにしたり、アプリとユーザーにポリシーを 1 つだけデプロイしたりできます。

### ポリシー競合の解決方法
ユーザーまたはデバイスへの最初のデプロイで、モバイル アプリケーション管理ポリシーの競合がある場合、競合している特定の設定値が、アプリにデプロイされたポリシーから削除され、アプリは組み込みの競合値を使用します。

アプリまたはユーザーへの以降のデプロイでモバイル アプリ管理ポリシーの競合がある場合、競合している特定の設定値は、アプリにデプロイされたモバイル アプリ管理ポリシーで更新されず、アプリはその設定の既存の値を使用します。

デバイスまたはユーザーが 2 つの競合するポリシーを受け取った場合は、次の動作が適用されます。

-   ポリシーがデバイスに既にデプロイされている場合、既存のポリシー設定は上書きされません。

-   ポリシーが既にデバイスにデプロイされておらず、2 つの競合する設定がデプロイされている場合、デバイスに組み込まれている既定の設定が使用されます。


<!--HONumber=Jun16_HO2-->


