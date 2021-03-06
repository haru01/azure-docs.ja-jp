---
title: OMS ポータルの Azure への移行 | Microsoft Docs
description: OMS ポータルは、すべての機能が Azure portal に移行されるのに伴い、非推奨となります。 この記事では、今回の切り替えの詳細について説明します。
services: log-analytics
documentationcenter: ''
author: bwren
manager: carmonm
editor: ''
ms.service: log-analytics
ms.workload: na
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: conceptual
ms.date: 06/11/2018
ms.author: bwren
ms.component: na
ms.openlocfilehash: e47e8cbd209ea34317ca9b176a2c4b0fef10a2b2
ms.sourcegitcommit: 5892c4e1fe65282929230abadf617c0be8953fd9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37133601"
---
# <a name="oms-portal-moving-to-azure"></a>OMS ポータルの Azure への移行
OMS ポータルをご利用いただきありがとうございます。 お客様からのご支援を励みに、今後も監視と管理のサービスへの重点的な投資を継続いたします。 お客様から繰り返し寄せられたフィードバックの 1 つに、オンプレミスと Azure の両方のワークロードを同じ方法で監視、管理できるようにしてほしいというものがありました。 ご存知のことと思われますが、Azure portal はすべての Azure サービスのハブであり、リソースをピン留めできるダッシュボード、リソースを見つけるためのインテリジェント検索、リソース管理のためのタグ付けなど、豊富な機能を備えた管理エクスペリエンスを提供しています。 監視と管理のワークフローを統合、合理化するために、Microsoft では OMS ポータルの機能を Azure portal に追加する作業を進めていました。 今回、ほぼすべての OMS ポータルの機能が Azure portal に組み込まれたことをご報告します。 実際に、Traffic Manager などの一部の新機能は、Azure portal でのみ使用可能となっています。 機能のギャップがほんのいくつか残っており、影響の大きい 5 つのソリューションについては、現在も Azure portal への移行が進められています。 これらの機能を使用していない場合は、OMS ポータルで実行していた作業をすべて Azure portal で実行でき、さらに新しい機能も使用できます。 まだ Azure portal を使用されていない場合は、すぐに使い始めることをお勧めします。 

これら 2 つのポータル間に残っているギャップについては、2018 年 8 月までに解消する予定です。 OMS ポータルが非推奨となるまでのタイムラインについては、お客様からのフィードバックに基づき、Microsoft からご連絡します。 Azure portal への移行は喜ばしいイベントであり、切り替えは簡単に済むと見込んでいます。 しかし、変化には困難が付きものであり、中断を伴う可能性も考えられます。 ご質問やフィードバック、懸念事項については LAUpgradeFeedback@microsoft.com までお問い合わせください。 この記事の残りの部分では、主なシナリオ、現在のギャップ、この切り替えのロードマップについて説明します。 


## <a name="what-will-change"></a>変更内容 
OMS ポータルが非推奨となるのに伴い、次の変更が発表されています。 これらの各変更については、以降のセクションで詳しく説明します。

- Alert Management ソリューションが、新しいアラート管理のエクスペリエンスに置き換えられます。
- ユーザー アクセス管理が、Azure のロールベースのアクセス制御を使用して、Azure portal 内で行われるようになります。
- Application Insights Connector が不要になります。これは、クロスワークスペース クエリを通じて同じ機能を実現できるためです。
- OMS モバイル アプリが非推奨となります。 
- NSG ソリューションは、Traffic Analytics ソリューションを通じて入手できる拡張機能に置き換えられます。



## <a name="current-known-gaps"></a>現時点での既知のギャップ 
現在、いくつかの機能のギャップがあり、これらについては OMS ポータルを使用し続ける必要があります。 これらのギャップは解消が進められており、このドキュメントは適宜更新されます。 拡張機能と変更について次々発表されるお知らせについては、「[Azure の更新情報](https://azure.microsoft.com/updates/?product=log-analytics)」も参照してください。

- 次のソリューションは、Azure portal でまだ完全には機能しません。 これらのソリューションは、更新されるまで、引き続きクラシック ポータルで使用する必要があります。

    - Windows Analytics ソリューション ([Upgrade Readiness](https://technet.microsoft.com/itpro/windows/deploy/upgrade-readiness-get-started)、[デバイスの正常性](https://docs.microsoft.com/windows/deployment/update/device-health-monitor)、[Update Compliance](https://technet.microsoft.com/itpro/windows/manage/update-compliance-get-started))
    - [DNS 分析](log-analytics-dns.md) 
    - [Surface Hub](log-analytics-surface-hubs.md)

-  Azure 内の Log Analytics リソースにアクセスできるようにするには、[Azure のロールベースのアクセス](#user-access-and-role-migration)を利用して、ユーザーにアクセス許可を付与する必要があります。
- OMS ポータルで作成された更新スケジュールは、Azure portal の [更新管理] ダッシュボード上にある、スケジュールされた更新プログラムのデプロイまたは更新ジョブの履歴に反映されない可能性があります。 このギャップは、2018 年 6 月末までに対処される予定です。
- カスタム ログのプレビュー機能は、OMS ポータルからのみ有効にできます。 これについては、2018 年 6 月末までにすべてのワークスペースで自動的に有効になります。
 
## <a name="what-should-i-do-now"></a>現時点で何をすべきか  
Azure portal への切り替え方法については、「[Common questions for transition from OMS portal to Azure portal for Log Analytics users (OMS ポータルから Azure portal への切り替えに関する Log Analytics ユーザーの一般的な質問)](../log-analytics/log-analytics-oms-portal-faq.md)」を参照してください。 [上記で説明したギャップ](#current-known-gaps)がお使いの環境で当てはまらない場合は、メインのエクスペリエンスとして Azure portal の使用を開始することを検討してください。 フィードバックやご質問、懸念事項については LAUpgradeFeedback@microsoft.com までお問い合わせください。

## <a name="changes-to-alerts"></a>アラートの変更内容 

### <a name="alert-extension"></a>アラートの拡張機能  
アラートは [Azure portal に拡張機能として移行](../monitoring-and-diagnostics/monitoring-alerts-extend.md)中です。 これが完了したら、アラートに対する管理アクションは Azure portal でのみ使用可能になります。 既存のアラートは引き続き OMS ポータルに表示されます。 Log Analytics Alert REST API または Log Analytics のアラート リソース テンプレートを使用してプログラムでアラートにアクセスする場合は、API 呼び出し、Azure Resource Manager テンプレート、PowerShell コマンドではアクションではなくアクション グループを使用する必要があります。

### <a name="alert-management-solution"></a>アラート管理ソリューション
[Alert Management ソリューション](log-analytics-solution-alert-management.md)の代わりに、[Azure Monitor の統合アラート インターフェイス](../monitoring-and-diagnostics/monitoring-overview-unified-alerts.md)を使用して、アラートの視覚化と管理を行うことができます。 この新しいエクスペリエンスでは、Log Analytics からのログ アラートをはじめ、Azure 内の複数のソースからのアラートが集約されます。 アラートの分布の表示、関連するアラートをスマート グループで自動的にグループ化する機能の活用、複数のサブスクリプションにわたるアラートの表示が可能なほか、さまざまなフィルターを適用することもできます。 これらの機能はすべて、2018 年 6 月 4 日からプレビューで使用できます。 Alert Management ソリューションは、Azure portal では使用できなくなります。 

Alert Management ソリューションで収集されたデータ (アラートの種類を含むレコード) は、このソリューションがワークスペースにインストールされているかぎり、引き続き Log Analytics に保存されます。 2018 年 8 月から、統合アラートからワークスペースへのアラートのストリーミングが有効になり、この機能の代わりに使用されます。 一部のスキーマの変更が予定されており、今後発表される予定です。

## <a name="user-access-and-role-migration"></a>ユーザー アクセスとロールの移行
Azure portal のアクセス管理は、OMS ポータルのアクセス管理よりも機能豊富で強力ですが、一部で変換が必要になります。 Log Analytics でのアクセス管理の詳細については、「[ワークスペースを管理する](log-analytics-manage-access.md#manage-accounts-and-users)」を参照してください。

6 月 25 日から 7 月までの間に、OMS ポータルのアクセス制御のアクセス許可が、Azure portal のアクセス許可へと自動変換され始めます。 変換が完了すると、ユーザーは、OMS ポータルのユーザー管理セクションから Azure 内のアクセス制御 (IAM) にルーティングされるようになります。 

変換中は、OMS ポータルでのアクセス許可を持つ各ユーザーまたはセキュリティ グループがチェックされ、Azure に同等のレベルまたはアクセス許可があるかどうかが確認されます。 アクセス許可がない場合は、関連するワークスペースとソリューション用に次のロールが割り当てられます。

| OMS ポータルのアクセス許可 | Azure のロール |
|:---|:---|
| ReadOnly | Log Analytics 閲覧者 |
| Contributor | Log Analytics 共同作成者 |
| 管理者 | Owner |

ユーザーに過剰なアクセス許可が割り当てられないようにするため、システムではこれらのアクセス許可をリソース グループ レベルで自動的に割り当てることはありません。 そのため、ワークスペース管理者は、次のアクションを行うために、自分自身に対し、リソース グループ レベルまたはサブスクリプション レベルで手動で "_所有者_" または "_共同作成者_" のロールを割り当てる必要があります。

- ソリューションの追加または削除
- 新しいカスタム ビューの定義
- Manage alerts 

場合によっては、自動変換でアクセス許可を適用できないことがあり、その場合は管理者に対し、アクセス許可を手動で割り当てることが求められます。

## <a name="oms-mobile-app"></a>OMS モバイル アプリ
OMS モバイル アプリは、OMS ポータルと共に非推奨となります。 OMS モバイル アプリの代わりに、モバイル デバイスのブラウザーから直接 Azure portal にアクセスすることで、IT インフラストラクチャ、ダッシュ ボード、保存されたクエリに関する情報にアクセスできます。 アラートを取得するには、[Azure のアクション グループ](../monitoring-and-diagnostics/monitoring-action-groups.md)を構成して、SMS または音声通話の形式で通知が届くようにする必要があります。

## <a name="application-insights-connector-and-solution"></a>Application Insights Connector と Application Insights ソリューション
[Application Insights Connector](log-analytics-app-insights-connector.md) では、Application Insights のデータを Log Analytics のワークスペースに移動させることができます。 このデータの重複は、インフラストラクチャとアプリケーションのデータ全体を視覚化するために必要でした。

[クロスリソース クエリ](log-analytics-cross-workspace-search.md)のサポートにより、データの重複は不要になります。 そのため、既存の Application Insights ソリューションは非推奨となります。 7 月以降は、新しい Application Insights リソースを Log Analytics ワークスペースにリンクさせることができなくなります。 既存のリンクとダッシュボードは引き続き 2018 年 11 月まで使用可能です。


## <a name="azure-network-security-group-analytics"></a>Azure ネットワーク セキュリティ グループ分析
[Azure Network Security Group Analytics ソリューション](log-analytics-azure-networking-analytics.md#azure-network-security-group-analytics-solution-in-log-analytics)は、最近発表された [Traffic Analytics](https://azure.microsoft.com/en-in/blog/traffic-analytics-in-preview/) に置き換えられます。Traffic Analytics では、クラウド ネットワークにおけるユーザーとアプリケーションのアクティビティを視覚化できます。 Traffic Analytics は、組織のネットワーク アクティビティの監査、アプリケーションとデータのセキュリティ保護、ワークロードのパフォーマンスの最適化、コンプライアンスの維持に役立ちます。 

このソリューションでは、NSG フロー ログを分析し、次の分析情報を提供します。

- Azure とインターネット、パブリック クラウド リージョン、VNET、およびサブネットの間のネットワークのトラフィック フロー。
- ネットワーク上のアプリケーションとプロトコル。スニファーや専用のフロー収集アプライアンスは不要です。
- トップ トーカー、チャット数が多いアプリケーション、クラウド内の VM の会話、トラフィックのホット スポット。
- VNET 間のトラフィックの送信元と送信先、重要なビジネス サービスとアプリケーションの間の内部関係。
- 悪意のあるトラフィック、インターネットに対して開かれているポート、インターネットにアクセスしようとしているアプリケーションや VM などに対するセキュリティ。
- 容量使用率。過剰なプロビジョニングまたは過小使用の問題を回避するのに役立ちます。

診断の設定を引き続き使用して、NSG ログを Log Analytics に送信できるので、保存された既存の検索、アラート、ダッシュボードを引き続き使用できます。 このソリューションを既にインストール済みのお客様は、別途通知があるまで、引き続きお使いいただけます。 6 月 20 日から、Network Security Group Analytics ソリューションはマーケットプレースから削除され、[Azure クイック スタート テンプレート](https://azure.microsoft.com/resources/templates/?resourceType=Microsoft.Operationalinsights)としてコミュニティを通じて入手できるようになります。

## <a name="next-steps"></a>次の手順
- OMS ポータルから Azure portal への移行に関するガイダンスについては、「[Common questions for transition from OMS portal to Azure portal for Log Analytics users (OMS ポータルから Azure portal への切り替えに関する Log Analytics ユーザーの一般的な質問)](log-analytics-oms-portal-faq.md)」を参照してください。