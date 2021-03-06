---
title: 'チュートリアル: Azure Active Directory と UserVoice の統合 | Microsoft Docs'
description: Azure Active Directory と UserVoice の間でシングル サインオンを構成する方法について説明します。
services: active-directory
documentationCenter: na
author: jeevansd
manager: mtillman
ms.reviewer: joflore
ms.assetid: 684a405b-8932-46f6-b43a-4d97a42b6b87
ms.service: active-directory
ms.component: saas-app-tutorial
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/21/2017
ms.author: jeedes
ms.openlocfilehash: 8ead383ef0967fcaf67f3157f0a51104126ad618
ms.sourcegitcommit: 7208bfe8878f83d5ec92e54e2f1222ffd41bf931
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2018
ms.locfileid: "39045412"
---
# <a name="tutorial-azure-active-directory-integration-with-uservoice"></a>チュートリアル: Azure Active Directory と UserVoice の統合

このチュートリアルでは、UserVoice と Azure Active Directory (Azure AD) を統合する方法について説明します。

UserVoice と Azure AD の統合には、次の利点があります。

- UserVoice にアクセスする Azure AD ユーザーを制御できます。
- ユーザーが自分の Azure AD アカウントで UserVoice に自動サインオン (シングル サインオン) できるようになります。
- 1 つの中央サイト (Azure Portal) でアカウントを管理できます。

SaaS アプリと Azure AD の統合の詳細については、「[Azure Active Directory のアプリケーション アクセスとシングル サインオンとは](../manage-apps/what-is-single-sign-on.md)」をご覧ください。

## <a name="prerequisites"></a>前提条件

UserVoice と Azure AD の統合を構成するには、次のものが必要です。

- Azure AD サブスクリプション
- UserVoice でのシングル サインオンが有効なサブスクリプション

> [!NOTE]
> このチュートリアルの手順をテストする場合、運用環境を使用しないことをお勧めします。

このチュートリアルの手順をテストするには、次の推奨事項に従ってください。

- 必要な場合を除き、運用環境は使用しないでください。
- Azure AD の評価環境がない場合は、[1 か月の評価版を入手できます](https://azure.microsoft.com/pricing/free-trial/)。

## <a name="scenario-description"></a>シナリオの説明
このチュートリアルでは、テスト環境で Azure AD のシングル サインオンをテストします。 このチュートリアルで説明するシナリオは、主に次の 2 つの要素で構成されています。

1. ギャラリーからの UserVoice の追加
2. Azure AD シングル サインオンの構成とテスト

## <a name="adding-uservoice-from-the-gallery"></a>ギャラリーからの UserVoice の追加
Azure AD への UserVoice の統合を構成するには、ギャラリーから管理対象 SaaS アプリの一覧に UserVoice を追加する必要があります。

**ギャラリーから UserVoice を追加するには、次の手順を実行します。**

1. **[Azure Portal](https://portal.azure.com)** の左側のナビゲーション ウィンドウで、**[Azure Active Directory]** アイコンをクリックします。 

    ![Azure Active Directory のボタン][1]

2. **[エンタープライズ アプリケーション]** に移動します。 次に、**[すべてのアプリケーション]** に移動します。

    ![[エンタープライズ アプリケーション] ブレード][2]
    
3. 新しいアプリケーションを追加するには、ダイアログの上部にある **[新しいアプリケーション]** をクリックします。

    ![[新しいアプリケーション] ボタン][3]

4. 検索ボックスに「**UserVoice**」と入力し、結果ウィンドウで **[UserVoice]** を選び、**[追加]** をクリックして、アプリケーションを追加します。

    ![結果一覧の UserVoice](./media/uservoice-tutorial/tutorial_uservoice_addfromgallery.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>Azure AD シングル サインオンの構成とテスト

このセクションでは、"Britta Simon" というテスト ユーザーに基づいて、UserVoice で Azure AD のシングル サインオンを構成し、テストします。

シングル サインオンを機能させるには、Azure AD ユーザーに対応する UserVoice ユーザーが Azure AD で認識されている必要があります。 言い換えると、Azure AD ユーザーと UserVoice の関連ユーザーの間で、リンク関係が確立されている必要があります。

UserVoice で、Azure AD の **[ユーザー名]** の値を **[Username]** の値として割り当ててリンク関係を確立します。

UserVoice で Azure AD のシングル サインオンを構成してテストするには、次の手順を完了する必要があります。

1. **[Azure AD シングル サインオンの構成](#configure-azure-ad-single-sign-on)** - ユーザーがこの機能を使用できるようにします。
2. **[Azure AD のテスト ユーザーの作成](#create-an-azure-ad-test-user)** - Britta Simon で Azure AD のシングル サインオンをテストします。
3. **[UserVoice テスト ユーザーの作成](#create-a-uservoice-test-user)** - UserVoice で Britta Simon に対応するユーザーを作成し、Azure AD の Britta Simon にリンクさせます。
4. **[Azure AD テスト ユーザーの割り当て](#assign-the-azure-ad-test-user)** - Britta Simon が Azure AD シングル サインオンを使用できるようにします。
5. **[シングル サインオンのテスト](#test-single-sign-on)** - 構成が機能するかどうかを確認します。

### <a name="configure-azure-ad-single-sign-on"></a>Azure AD シングル サインオンの構成

このセクションでは、Azure Portal で Azure AD のシングル サインオンを有効にして、UserVoice アプリケーションでシングル サインオンを構成します。

**UserVoice で Azure AD シングル サインオンを構成するには、次の手順を実行します。**

1. Azure Portal の **UserVoice** アプリケーション統合ページで、**[シングル サインオン]** をクリックします。

    ![シングル サインオン構成のリンク][4]

2. **[シングル サインオン]** ダイアログで、**[モード]** として **[SAML ベースのサインオン]** を選択し、シングル サインオンを有効にします。
 
    ![[シングル サインオン] ダイアログ ボックス](./media/uservoice-tutorial/tutorial_uservoice_samlbase.png)

3. **[UserVoice のドメインと URL]** セクションで、次の手順を実行します。

    ![[UserVoice のドメインと URL] のシングル サインオン情報](./media/uservoice-tutorial/tutorial_uservoice_url.png)

    a. **[サインオン URL]** ボックスに、`https://<tenantname>.UserVoice.com` のパターンを使用して URL を入力します。

    b. **[識別子]** ボックスに、`https://<tenantname>.UserVoice.com` の形式で URL を入力します。

    > [!NOTE] 
    > これらは実際の値ではありません。 実際のサインオン URL と識別子でこれらの値を更新してください。 これらの値を取得するには、[UserVoice クライアント サポート チーム](https://www.uservoice.com/)に問い合わせてください。

4. **[SAML 署名証明書]** セクションで、証明書の **[拇印]** の値をコピーします。

    ![証明書のダウンロードのリンク](./media/uservoice-tutorial/tutorial_uservoice_certificate.png) 

5. **[保存]** ボタンをクリックします。

    ![[シングル サインオンの構成] の [保存] ボタン](./media/uservoice-tutorial/tutorial_general_400.png)

6. **[UserVoice 構成]** セクションで、**[UserVoice の構成]** をクリックして、**[サインオンの構成]** ウィンドウを開きます。 **クイック リファレンス セクション**から、**サインアウト URL と SAML シングル サインオン サービス URL** をコピーします。

    ![UserVoice 構成](./media/uservoice-tutorial/tutorial_uservoice_configure.png) 

7. 別の Web ブラウザーのウィンドウで、UserVoice 企業サイトに管理者としてログインします。

8. 上部のツール バーの **[設定]** をクリックし、メニューから **[Web ポータル]** を選択します。
   
    ![アプリ側の [設定] セクション](./media/uservoice-tutorial/ic777519.png "設定")

9. **[Web ポータル]** タブの **[ユーザー認証]** セクションで、**[編集]** をクリックして **[ユーザー認証の編集]** ダイアログ ページを開きます。
   
    ![[Web ポータル] タブ](./media/uservoice-tutorial/ic777520.png "Web ポータル")

10. **[ユーザー認証の編集]** ダイアログ ページで、次の手順に従います。
   
    ![ユーザー認証の編集](./media/uservoice-tutorial/ic777521.png "Edit user authentication")
   
    a. **[シングル サインオン]** をクリックします。
 
    b. Azure Portal からコピーした **[SAML シングル サインオン サービスの URL]** の値を **[SSO Remote Sign-In]\(SSO リモート サインイン\)** ボックスに貼り付けます。

    c. Azure Portal からコピーした **[サインアウト URL]** の値を **[SSO Remote Sign-Out]\(SSO リモート サインアウト\)** ボックスに貼り付けます。
 
    d. Azure Portal からコピーした **[拇印]** の値を **[Current certificate SHA1 fingerprint]\(現在の証明書 SHA1 のフィンガープリント\)** ボックスに貼り付けます。
    
    e. **[認証設定の保存]** をクリックします。

> [!TIP]
> アプリのセットアップ中、[Azure Portal](https://portal.azure.com) 内で上記の手順の簡易版を確認できるようになりました。  **[Active Directory] の [エンタープライズ アプリケーション]** セクションからこのアプリを追加した後、**[シングル サインオン]** タブをクリックし、一番下の **[構成]** セクションから組み込みドキュメントにアクセスするだけです。 組み込みドキュメント機能の詳細については、[Azure AD の組み込みドキュメント]( https://go.microsoft.com/fwlink/?linkid=845985)に関するページを参照してください。
> 

### <a name="create-an-azure-ad-test-user"></a>Azure AD のテスト ユーザーの作成

このセクションの目的は、Azure Portal で Britta Simon というテスト ユーザーを作成することです。

   ![Azure AD のテスト ユーザーの作成][100]

**Azure AD でテスト ユーザーを作成するには、次の手順に従います。**

1. Azure Portal の左側のウィンドウで、**Azure Active Directory** のボタンをクリックします。

    ![Azure Active Directory のボタン](./media/uservoice-tutorial/create_aaduser_01.png)

2. ユーザーの一覧を表示するには、**[ユーザーとグループ]** に移動し、**[すべてのユーザー]** をクリックします。

    ![[ユーザーとグループ] と [すべてのユーザー] リンク](./media/uservoice-tutorial/create_aaduser_02.png)

3. **[ユーザー]** ダイアログ ボックスを開くには、**[すべてのユーザー]** ダイアログ ボックスの上部にある **[追加]** をクリックしてきます。

    ![[追加] ボタン](./media/uservoice-tutorial/create_aaduser_03.png)

4. **[ユーザー]** ダイアログ ボックスで、次の手順に従います。

    ![[ユーザー] ダイアログ ボックス](./media/uservoice-tutorial/create_aaduser_04.png)

    a. **[名前]** ボックスに「**BrittaSimon**」と入力します。

    b. **[ユーザー名]** ボックスに、ユーザーである Britta Simon の電子メール アドレスを入力します。

    c. **[パスワードを表示]** チェック ボックスをオンにし、**[パスワード]** ボックスに表示された値を書き留めます。

    d. **Create** をクリックしてください。
 
### <a name="create-a-uservoice-test-user"></a>UserVoice テスト ユーザーの作成

Azure AD ユーザーが UserVoice にログインできるようにするには、そのユーザーを UserVoice にプロビジョニングする必要があります。 UserVoice の場合、プロビジョニングは手動で行います。

### <a name="to-provision-a-user-account-perform-the-following-steps"></a>ユーザー アカウントをプロビジョニングするには、次の手順を実行します。
1. **UserVoice** テナントにログインします。

2. **[設定]** に移動します。
   
    ![設定](./media/uservoice-tutorial/ic777811.png "Settings")

3. **[全般]** をクリックします。

4. **[エージェントとアクセス許可]** をクリックします。
   
    ![エージェントとアクセス許可](./media/uservoice-tutorial/ic777812.png "Agents and permissions")

5. **[管理者の追加]** をクリックします。
   
    ![管理者の追加](./media/uservoice-tutorial/ic777813.png "Add admins")

6. **[管理者の招待]** ダイアログで、次の手順を実行します。
   
    ![管理者の招待](./media/uservoice-tutorial/ic777814.png "Invite admins")
   
    a. [電子メール] ボックスに、プロビジョニングするアカウントの電子メール アドレスを入力し、**[追加]** をクリックします。
   
    b. **[招待]** をクリックします。

> [!NOTE]
> UserVoice から提供されている他の UserVoice ユーザー アカウント作成ツールまたは API を使用して、AAD ユーザー アカウントをプロビジョニングできます。

### <a name="assign-the-azure-ad-test-user"></a>Azure AD テスト ユーザーの割り当て

このセクションでは、Britta Simon に UserVoice へのアクセスを許可することで、このユーザーが Azure シングル サインオンを使用できるようにします。

![ユーザー ロールを割り当てる][200] 

**UserVoice に Britta Simon を割り当てるには、次の手順に従います。**

1. Azure Portal でアプリケーション ビューを開き、ディレクトリ ビューに移動します。次に、**[エンタープライズ アプリケーション]** に移動し、**[すべてのアプリケーション]** をクリックします。

    ![ユーザーの割り当て][201] 

2. アプリケーションの一覧で **[UserVoice]** を選択します。

    ![アプリケーションの一覧の UserVoice リンク](./media/uservoice-tutorial/tutorial_uservoice_app.png)  

3. 左側のメニューで **[ユーザーとグループ]** をクリックします。

    ![[ユーザーとグループ] リンク][202]

4. **[追加]** ボタンをクリックします。 次に、**[割り当ての追加]** ダイアログで **[ユーザーとグループ]** を選択します。

    ![[割り当ての追加] ウィンドウ][203]

5. **[ユーザーとグループ]** ダイアログで、ユーザーの一覧から **[Britta Simon]** を選択します。

6. **[ユーザーとグループ]** ダイアログで **[選択]** をクリックします。

7. **[割り当ての追加]** ダイアログで **[割り当て]** ボタンをクリックします。
    
### <a name="test-single-sign-on"></a>シングル サインオンのテスト

このセクションでは、アクセス パネルを使用して Azure AD のシングル サインオン構成をテストします。

アクセス パネルで [UserVoice] タイルをクリックすると、UserVoice アプリケーションに自動的にサインオンします。
アクセス パネルの詳細については、[アクセス パネルの概要](../user-help/active-directory-saas-access-panel-introduction.md)に関する記事を参照してください。 

## <a name="additional-resources"></a>その他のリソース

* [SaaS アプリと Azure Active Directory を統合する方法に関するチュートリアルの一覧](tutorial-list.md)
* [Azure Active Directory のアプリケーション アクセスとシングル サインオンとは](../manage-apps/what-is-single-sign-on.md)



<!--Image references-->

[1]: ./media/uservoice-tutorial/tutorial_general_01.png
[2]: ./media/uservoice-tutorial/tutorial_general_02.png
[3]: ./media/uservoice-tutorial/tutorial_general_03.png
[4]: ./media/uservoice-tutorial/tutorial_general_04.png

[100]: ./media/uservoice-tutorial/tutorial_general_100.png

[200]: ./media/uservoice-tutorial/tutorial_general_200.png
[201]: ./media/uservoice-tutorial/tutorial_general_201.png
[202]: ./media/uservoice-tutorial/tutorial_general_202.png
[203]: ./media/uservoice-tutorial/tutorial_general_203.png

