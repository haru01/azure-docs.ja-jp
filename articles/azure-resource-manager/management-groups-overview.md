---
title: Azure 管理グループでリソースを整理する | Microsoft Docs
description: 管理グループとその使用方法について説明します。
author: rthorn17
manager: rithorn
editor: ''
ms.assetid: 482191ac-147e-4eb6-9655-c40c13846672
ms.service: azure-resource-manager
ms.devlang: na
ms.topic: conceptual
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 7/09/2018
ms.author: rithorn
ms.openlocfilehash: c8152a6c12c776806d9a17c5e434d825d6c91165
ms.sourcegitcommit: 0a84b090d4c2fb57af3876c26a1f97aac12015c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38466645"
---
# <a name="organize-your-resources-with-azure-management-groups"></a>Azure 管理グループでリソースを整理する

組織に多数のサブスクリプションがある場合は、これらのサブスクリプションのアクセス、ポリシー、およびコンプライアンスを効率的に管理する方法が必要になることがあります。 Azure 管理グループの範囲は、サブスクリプションを上回ります。 "管理グループ" と呼ばれるコンテナーにサブスクリプションを整理して、管理グループに管理条件を適用できます。 管理グループ内のすべてのサブスクリプションは、管理グループに適用された条件を自動的に継承します。 管理グループを使うと、サブスクリプションの種類に関係なく、大きな規模でエンタープライズ レベルの管理を行うことができます。

管理グループ機能は、パブリック プレビューで使用できます。 管理グループを使い始めるには、[Azure Portal](https://portal.azure.com) にサインインし、**[すべてのサービス]** セクションで **[管理グループ]** を探します。

たとえば、仮想マシン (VM) の作成に使えるリージョンを制限するポリシーを管理グループに適用できます。 そのリージョンでの VM の作成を許可するだけで、その管理グループの下にあるすべての管理グループ、サブスクリプション、リソースに、このポリシーが適用されます。

## <a name="hierarchy-of-management-groups-and-subscriptions"></a>管理グループとサブスクリプションの階層

管理グループとサブスクリプションの柔軟な構造を作成し、リソースを階層に整理して、統一されたポリシーとアクセス管理を適用できます。
次の図では、部門別に整理された管理グループとサブスクリプションで構成される階層の例を示します。

![ツリー](media/management-groups/MG_overview.png)

部門別にグループ化された階層を作成することで、その管理グループに属する部門に "*継承*" される [Azure のロールベースのアクセス制御 (RBAC)](../role-based-access-control/overview.md) のロールを割り当てることができます。 管理グループを使うと、ロールの割り当てが 1 回しか必要ないので、ワークロードが減り、エラーのリスクが軽減されます。

### <a name="important-facts-about-management-groups"></a>管理グループに関する重要な事実

- 1 つのディレクトリでは、10,000 個の管理グループをサポートできます。
- 管理グループのツリーは、最大 6 レベルの深さをサポートできます。
  - この制限には、ルート レベルまたはサブスクリプション レベルは含まれません。
- 各管理グループとサブスクリプションは、1 つの親のみをサポートできます。
- 各管理グループは、複数の子を持つことができます。
- すべてのサブスクリプションと管理グループは、各ディレクトリの 1 つの階層内に格納されます。 プレビュー中の例外については、[ルート管理グループに関する重要な情報](#important-facts-about-the-root-management-group)を参照してください。

### <a name="preview-subscription-visibility-limitation"></a>プレビュー サブスクリプションの可視性の制限

現在、プレビューにはアクセス権を継承したサブスクリプションを表示できないという制限があります。 サブスクリプションへのアクセス権は継承されましたが、その継承は Azure Resource Manager によってまだ受け入れられていません。  

アクセス権を持っている場合、サブスクリプションに関する情報を取得するために REST API を使用すると詳細情報が返されます。しかし、Azure Portal および Azure PowerShell では、サブスクリプションは表示されません。

この項目については現在処理中であり、管理グループの "一般提供" を発表するまでには解決する予定です。  

### <a name="cloud-solution-provider-csp-limitation-during-preview"></a>プレビュー期間中のクラウド ソリューション プロバイダー (CSP) の制限

現在、クラウド ソリューション プロバイダー (CSP) パートナーに、その顧客のディレクトリ内の顧客の管理グループを作成または管理することができないという制限があります。  
この項目については現在処理中であり、管理グループの "一般提供" を発表するまでには解決する予定です。

## <a name="root-management-group-for-each-directory"></a>各ディレクトリのルート管理グループ

各ディレクトリには、"ルート" 管理グループと呼ばれる 1 つの最上位管理グループがあります。 このルート管理グループは階層に組み込まれており、すべての管理グループとサブスクリプションはルート管理グループにまとめられます。 ルート管理グループにより、グローバル ポリシーと RBAC の割り当てをディレクトリ レベルで適用できます。 [ディレクトリ管理者は自分自身を昇格させて](../role-based-access-control/elevate-access-global-admin.md)、最初にこのルート グループの所有者にする必要があります。 グループの所有者になった管理者は、任意の RBAC ロールを他のディレクトリ ユーザーまたはグループに割り当てて、階層を管理することができます。  

### <a name="important-facts-about-the-root-management-group"></a>ルート管理グループに関する重要な事実

- ルート管理グループの名前と ID は、既定で設定されています。 表示名はいつでも更新でき、Azure Portal 内での表示を変えることができます。
  - 名前は "Tenant root group" になります。
  - ID は Azure Active Directory ID になります。
- 他の管理グループと異なり、ルート管理グループを移動または削除することはできません。  
- すべてのサブスクリプションと管理グループは、ディレクトリ内の 1 つのルート管理グループにまとめられます。
  - ディレクトリ内のすべてのリソースは、グローバル管理用のルート管理グループにまとめられます。
  - 既定では、新しいサブスクリプションは作成時に自動的にルート管理グループに設定されます。
- すべての Azure ユーザーはルート管理グループを表示できますが、すべてのユーザーがルート管理グループを管理するアクセス権を持つわけではありません。
  - サブスクリプションへのアクセス権を持つすべてのユーザーは、階層内にそのサブスクリプションが存在するコンテキストを参照できます。  
  - 既定では、ルート管理グループには誰もアクセスできません。 ディレクトリグローバル管理者は、自分自身を昇格させてアクセス権を取得できる唯一のユーザーです。  アクセス権を取得したディレクトリ管理者は、他のユーザーが管理できるように任意の RBAC ロールを割り当てることができます。  

>[!NOTE]
>2018 年 6 月 25 日以前に管理グループ サービスの使用を開始したディレクトリは、階層内のすべてのサブスクリプションが設定されていない可能性があります。 管理グループ チームは、その日付以前にパブリック プレビューで管理グループの使用を開始した各ディレクトリを過去にさかのぼって更新しています。この作業は、2018 年 7 月中に完了します。 ディレクトリ内のすべてのサブスクリプションは、以前のルート管理グループの子になります。  
>
>この遡及的プロセスについて質問等がございましたら、managementgroups@microsoft.com にお問い合わせください。  
  
## <a name="initial-setup-of-management-groups"></a>管理グループの初期セットアップ

ユーザーが管理グループの使用を開始する際には、初期セットアップ プロセスが発生します。 最初の手順として、ディレクトリでルート管理グループが作成されます。 このグループが作成されると、ディレクトリ内に存在するすべての既存のサブスクリプションがルート管理グループの子になります。  このプロセスが実行される理由は、ディレクトリ内に管理グループ階層が 1 つだけ存在するようにするためです。  ディレクトリ内に 1 つの階層が存在することにより、ディレクトリ内の他のユーザーがバイパスできないグローバル アクセス権とポリシーを管理ユーザーが適用できるようになります。 ディレクトリ内に 1 つの階層が存在することにより、ルートに割り当てられている内容は、ディレクトリ内のすべての管理グループ、サブスクリプション、リソース グループ、およびリソースに適用されます。  

> [!IMPORTANT]
> ルート管理グループでのユーザーのアクセス権またはポリシーの割り当ては、**ディレクトリ内のすべてのリソースに適用されます**。 そのため、すべてのユーザーは、このスコープで定義されている項目を所有する必要性を評価する必要があります。  ユーザーアクセスやポリシーの割り当ては、このスコープでのみ「必須」である必要があります。  
  
## <a name="management-group-access"></a>管理グループ アクセス

Azure 管理グループは、すべてのリソース アクセスとロール定義について、[Azure のロールベースのアクセス制御 (RBAC)](../role-based-access-control/overview.md) をサポートします。 これらのアクセス許可は、階層内に存在する子リソースに継承されます。 管理グループには任意の組み込み RBAC ロールを割り当てることができます。ロールは階層を継承し、各リソースに割り当てられます。  たとえば、VM 共同作成者の RBAC ロールは、管理グループに割り当てることができます。 このロールには、管理グループに対するアクションはありませんが、その管理グループに属するすべての VM に継承されます。  

次の図に、管理グループのロールとサポートされているアクションの一覧を示します。

| RBAC ロール名             | Create | 名前の変更 | Move | Delete | アクセス権の割り当て | ポリシーの割り当て | 読み取り  |
|:-------------------------- |:------:|:------:|:----:|:------:|:-------------:| :------------:|:-----:|
|Owner                       | ○      | ○      | ○    | ○      | ○             |               | ○     |
|Contributor                 | ○      | ○      | ○    | ○      |               |               | ○     |
|Reader                      |        |        |      |        |               |               | ○     |
|リソース ポリシー共同作成者 |        |        |      |        |               | ○             |       |
|User Access Administrator   |        |        |      |        | ○             |               |       |

### <a name="custom-rbac-role-definition-and-assignment"></a>カスタム RBAC ロールの定義と割り当て

現時点では、管理グループのカスタム RBAC ロールはサポートされていません。  この項目の状態については、[管理グループ フィードバック フォーラム](https://aka.ms/mgfeedback)を参照してください。

## <a name="next-steps"></a>次の手順

管理グループについて詳しくは、以下をご覧ください。

- [管理グループを作成して Azure リソースを整理する](management-groups-create.md)
- [管理グループを変更、削除、または管理する方法](management-groups-manage.md)
- [Azure PowerShell モジュールのインストール](https://www.powershellgallery.com/packages/AzureRM.ManagementGroups/0.0.1-preview)
- [REST API 仕様の確認](https://github.com/Azure/azure-rest-api-specs/tree/master/specification/managementgroups/resource-manager/Microsoft.Management/preview)
- [Azure CLI 拡張機能のインストール](https://docs.microsoft.com/cli/azure/extension?view=azure-cli-latest#az_extension_list_available)
