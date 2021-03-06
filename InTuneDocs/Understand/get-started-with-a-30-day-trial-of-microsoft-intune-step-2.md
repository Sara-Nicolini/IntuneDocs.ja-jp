---
# required metadata

title: Microsoft Intune の 30 日間評価版にユーザーを追加する | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 9e40999b-46f7-447b-8974-72af82bec7ef

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Microsoft Intune の 30 日間評価版にユーザーを追加する
アカウントを設定したので、**新しいユーザー** ウィザードを使用して個別のユーザー アカウントを Intune に追加します。または**ユーザーの一括追加**ウィザードを使用して、一括でユーザーを追加します (このセクションの手順を参照してください)。  操作を開始する前に、Intune が管理者アカウントを処理する方法について理解することが重要です。

テナント管理者は、Office 365 管理センターを使用して、Microsoft Intune **ユーザー グループ**にユーザーを追加します。 **ユーザー グループ** にユーザーを追加すると、Intune サブスクリプション ライセンスをユーザーに割り当てることができます。また、この操作を終えると、ライセンスを割り当てたユーザーが Microsoft Intune 管理コンソールに表示されます。

Intune の管理者アカウントは、通常のユーザー アカウントとは違い、Office 365 管理センターで作成されません。 代わりに、管理コンソールを使用して、**[管理]** ワークスペースの **[管理者の管理]** で読み取り専用アクセスまたはフル アクセスの管理者権限を割り当てます。 読み取り専用アクセスが割り当てられているサービス管理者は、Intune の設定を変更できませんが、データを表示し、レポートを実行することができます。 フル アクセス権を持つサービス管理者には、使用可能なすべての管理者権限が与えられます。

Intune 管理コンソールではテナント管理者の情報を確認できますが、テナント管理者を作成することはできません。 既定では、サブスクリプション所有者が Microsoft Intune サービスのテナント管理者になり、Office 365 管理センターと Intune 管理コンソールの両方に対するフル アクセス権を持ちます。 タスクを委任しやすくするために、またパスワードを忘れた場合に Intune サービスの管理者アカウントがロックアウトされないように、Office 365 管理センターを使用して、少なくとも 1 つの追加のテナント管理者アカウントを作成することをお勧めします。

## 個々のユーザー アカウントを追加する
次の手順を使用すると、評価版のテナントに追加のユーザー アカウントを作成できます。 追加する各ユーザー アカウントは、Intune 無料評価版で使用できる 100 ライセンスの 1 つとしてカウントされます。

1.  [Office 365 管理センター](http://go.microsoft.com/fwlink/?LinkID=787455)で、**[ユーザーの追加]** &gt; **[新規]** &gt; **[ユーザー]** を選択し、**新しいユーザー** ウィザードを開始します。

2.  **[詳細]** ページで、必要なフィールドを入力します。

3.  **[設定]** ページで、ユーザーの **[場所]** を設定します。

4.  **[グループ]** ページで、**[次へ]** をクリックして、既定の設定を確認し、Intune のライセンスをユーザー アカウントに割り当てます。

5.  **[電子メール]** ページで、アカウントのユーザー名と一時パスワードの通知を受け取る電子メール アドレスを、最大 5 つ指定します。 複数の電子メール アドレスは、セミコロン (;) で区切ります。 完了したら、**[作成]** を選択して、サブスクリプションにユーザーを追加します。

6.  **[結果]** ページで、新しいアカウント名と一時パスワードを確認できます。 一時パスワードは Intune によって自動的に作成されます。

7.  Office 365 管理センターに新しいユーザーが表示されたら、次のように新しいユーザーが正常に作成されたことを確認します。

    1.  [Intune 管理コンソール](https://manage.microsoft.com/)で、**[管理者]** &gt; **[ポータル サイト]** の順に選択し、画面の一番下までスクロールします。 **[Intune ポータル サイト]** の下に表示されている URL をコピーします。

    2.  "プライベート モード" で新しいブラウザー ウィンドウを開くか (Internet Explorer で **[ツール]** &gt; **[InPrivate ブラウズ]** をクリックします)、別のデバイスで新しいブラウザー ウィンドウを開いて、前の手順でコピーした URL にアクセスします。 ユーザーは、最初にサインインするときに、アカウントの新しいパスワードを指定する必要があります。

## 一括でユーザーを追加する
一括で Intune にユーザーを追加するには、**ユーザーの一括追加**ウィザードを使用して、ユーザー データが含まれるコンマ区切り値 (CSV) ファイルをアップロードします。 ウィザード内のリンクを使用すると、空のテンプレートとサンプル CSV ファイルをダウンロードできます。 CSV ファイルの最初の行には、ユーザー データ列の各ラベルが正しい順序で記載されている必要があります。 CSV ファイルに指定するユーザーごとに、 **ユーザー名** ( **bob@contoso.com**など) と、 **表示名** ( **Bob Kelly**など) を入力する必要があります。

1.  [Office 365 管理センター](http://go.microsoft.com/fwlink/?LinkID=787455)で、**[ユーザー]** &gt; **[新規]** を選択します。

2.  **[一括追加]** を選択して、一括追加ウィザードを起動します。

3.  **[ファイルの選択]** ページで、**[参照]** を選択して、コンピューターの既存の CSV ファイルを指定して読み込みます。 ウィザード内のリンクを使用して、サンプル CSV ファイルまたは空のテンプレート ファイルをダウンロードすることもできます。

4.  **[確認]** ページで結果を確認します。詳細を表示するには、**[表示]** を選択します。

5.  **[設定]** ページで、サインインの状態が "**許可済み**" であることを確認して、**[場所]** を設定します。 これらの設定は、CSV ファイルで追加されるすべてのユーザー アカウントに適用されます。

6.  **[グループ]** ページで、**[次へ]** を選択して、既定の設定を確認し、CSV ファイルで追加されたすべてのユーザー アカウントに Intune のライセンスを割り当てます。 チェック ボックスの既定はオンで、Intune のライセンスが各アカウントに割り当てられます。

7.  **[電子メール]** ページで、ユーザー名と、Intune が各アカウント用に作成する一時パスワードの通知を受け取る電子メール アドレスを、最大 5 つ指定します。 複数の電子メール アドレスは、セミコロン (;) で区切ります。 準備ができたら、**[作成]** を選択して、サブスクリプションにユーザーを追加します。

8.  **[結果]** ページで、各ユーザー アカウントのアカウント名と一時パスワードを表示できます。

インポートして追加した各ユーザー アカウントは、Office 365 管理センターの **[ユーザー]** ノードに表示されるようになります。 新しいユーザーは、最初にサインインするときに、ユーザー アカウントの新しいパスワードを指定する必要があります。

### 次のステップ
これで終了です。 *Microsoft Intune の評価*チュートリアルの手順 2 が完了しました。

>[!div class="step-by-step"]

>[&larr;**評価版にサインアップ**](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-1.md)     [**グループの作成**&rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)  


<!--HONumber=May16_HO3-->


