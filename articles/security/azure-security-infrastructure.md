---
title: Azure インフラストラクチャのセキュリティ | Microsoft Docs
description: この記事では、Microsoft が Azure データセンターのセキュリティを確保する方法について説明します。
services: security
documentationcenter: na
author: TerryLanfear
manager: MBaldwin
editor: TomSh
ms.assetid: 61e95a87-39c5-48f5-aee6-6f90ddcd336e
ms.service: security
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 07/06/2018
ms.author: terrylan
ms.openlocfilehash: 397bd1f904b676a6ba020ec78fb1cad05c460be1
ms.sourcegitcommit: d551ddf8d6c0fd3a884c9852bc4443c1a1485899
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/07/2018
ms.locfileid: "37903858"
---
# <a name="azure-infrastructure-security"></a>Azure インフラストラクチャのセキュリティ
Microsoft Azure は、Microsoft によって管理および運用されているデータセンター内で実行されます。 これらの地理的に分散したデータセンターは、セキュリティおよび信頼性のための、ISO/IEC 27001:2013 や NIST SP 800-53 などの主要な業界標準に準拠しています。 これらのデータセンターは、Microsoft の運用担当者によって管理および監視されます。 これらの運用担当者には、世界最大のオンライン サービスを週 7 日 24 時間体制の継続性で提供することについての数年にわたる経験があります。

この一連の記事では、Microsoft が Azure インフラストラクチャをセキュリティ保護するために行っていることに関する情報を提供します。 これらの記事では、次のことについて説明します。

- [物理的なセキュリティ](azure-physical-security.md)
- [可用性](azure-infrastructure-availability.md)
- [コンポーネントと境界](azure-infrastructure-components.md)
- [ネットワーク アーキテクチャ](azure-infrastructure-network.md)
- [運用ネットワーク](azure-production-network.md)
- [SQL Database](azure-infrastructure-sql.md)
- [操作](azure-infrastructure-operations.md)
- [監視](azure-infrastructure-monitoring.md)
- [整合性](azure-infrastructure-integrity.md)
- [データ保護](azure-protection-of-customer-data.md)

## <a name="shared-responsibility-model"></a>共同責任モデル
お客様と Microsoft との責任の分担を理解することが重要です。 オンプレミスでは、お客様はスタック全体を所有しますが、クラウドに移行すると、責任の一部は Microsoft に移譲されます。 次の責任マトリックスは、お客様と Microsoft がそれぞれ責任を負う、サービスとしてのソフトウェア (SaaS)、サービスとしてのプラットフォーム (PaaS)、およびサービスとしてのインフラストラクチャ (IaaS) のデプロイにおけるスタックの領域を示しています。

![Shared responsibility][1]

デプロイの種類に関係なく、常にお客様が責任を持つ項目は次のとおりです。

- データ
- エンドポイント
- アカウント
- アクセス管理

SaaS、PaaS、および IaaS のデプロイにおけるお客様と Microsoft の間の責任の分配を理解するようにしてください。 詳細については、[クラウド コンピューティングの共同責任](https://gallery.technet.microsoft.com/Shared-Responsibilities-81d0ff91/file/153019/1/Shared%20responsibilities%20for%20cloud%20computing.pdf)に関するページを参照してください。

## <a name="next-steps"></a>次の手順
Microsoft が Azure インフラストラクチャをセキュリティ保護するために行っていることの詳細については、次を参照してください。

- [Azure ファシリティ、プレミス、および物理的なセキュリティ](azure-physical-security.md)
- [Azure インフラストラクチャの可用性](azure-infrastructure-availability.md)
- [Azure 情報システムのコンポーネントと境界](azure-infrastructure-components.md)
- [Azure ネットワーク アーキテクチャ](azure-infrastructure-network.md)
- [Azure 運用ネットワーク](azure-production-network.md)
- [Microsoft Azure SQL Database のセキュリティ機能](azure-infrastructure-sql.md)
- [Azure の運用操作と管理](azure-infrastructure-operations.md)
- [Azure インフラストラクチャの監視](azure-infrastructure-monitoring.md)
- [Azure インフラストラクチャの整合性](azure-infrastructure-integrity.md)
- [Azure での顧客データの保護](azure-protection-of-customer-data.md)

<!--Image references-->
[1]: ./media/azure-security-infrastructure/responsibility-zones.png
