---
title: Azure Portal で Windows VM の FQDN を作成する | Microsoft Docs
description: Azure Portal で仮想マシンに基づいて、Resource Manager の完全修飾ドメイン名 (FQDN) を作成する方法を説明します。
services: virtual-machines-windows
documentationcenter: ''
author: cynthn
manager: jeconnoc
editor: tysonn
tags: azure-resource-manager
ms.assetid: a2ae5887-76df-485e-ae19-0efd96df8600
ms.service: virtual-machines-windows
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: vm-windows
ms.workload: infrastructure-services
ms.date: 12/13/2017
ms.author: cynthn
ms.custom: H1Hack27Feb2017
ms.openlocfilehash: 79b3e3ba01076dcfe5820fb832fa1839398c6c04
ms.sourcegitcommit: 0a84b090d4c2fb57af3876c26a1f97aac12015c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38597388"
---
# <a name="create-a-fully-qualified-domain-name-in-the-azure-portal-for-a-windows-vm"></a>Windows VM 用の Azure Portal での完全修飾ドメイン名の作成

[Azure ポータル](https://portal.azure.com)で仮想マシン (VM) を作成すると、仮想マシン用のパブリック IP リソースが自動的に作成されます。 この IP アドレスを使用して、VM にリモートでアクセスします。 ポータルでは[完全修飾ドメイン名](https://en.wikipedia.org/wiki/Fully_qualified_domain_name) (FQDN) は作成されませんが、VM の作成後に作成できます。 この記事では、DNS 名または FQDN を作成する手順を示します。

## <a name="create-a-fqdn"></a>FQDN の作成
この記事では、既に VM が作成されていることを前提としています。 必要であれば、[ポータルで VM を作成する](quick-create-portal.md)か、[ Azure PowerShell を使用して VM を作成する](quick-create-powershell.md)ことができます。 VM が起動したら、次の手順を実行します。

[!INCLUDE [virtual-machines-common-portal-create-fqdn](../../../includes/virtual-machines-common-portal-create-fqdn.md)]

リモート デスクトップ プロトコル (RDP) 用など、この DNS 名を使用して、VM にリモートで接続できるようになります。

## <a name="next-steps"></a>次の手順
これで、VM にパブリック IP と DNS 名が設定されたため、IIS、SQL、SharePoint などの一般的なアプリケーション フレームワークやサービスをデプロイできるようになりました。

Azure デプロイの構築に関するヒントについては、[Resource Manager の使用](../../azure-resource-manager/resource-group-overview.md)に関する記事から確認することもできます。

