---
title: Azure Service Fabric コンテナー サービスに対して gMSA を設定する | Microsoft Docs
description: Azure Service Fabric で実行されているコンテナーに対して gMSA を設定する方法について説明します。
services: service-fabric
documentationcenter: .net
author: mani-ramaswamy
manager: timlt
editor: ''
ms.assetid: ab49c4b9-74a8-4907-b75b-8d2ee84c6d90
ms.service: service-fabric
ms.devlang: dotNet
ms.topic: conceptual
ms.tgt_pltfrm: NA
ms.workload: NA
ms.date: 03/23/2018
ms.author: subramar
ms.openlocfilehash: e4cd0b42e21609f88edc28c8fd7b5c433d56b3c1
ms.sourcegitcommit: eb75f177fc59d90b1b667afcfe64ac51936e2638
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2018
ms.locfileid: "34209095"
---
# <a name="set-up-gmsa-for-windows-containers-running-on-service-fabric"></a>Service Fabric で実行されている Windows コンテナーに対して gMSA を設定する

gMSA (グループの管理されたサービス アカウント) を設定するには、資格情報の指定ファイル (`credspec`) をクラスター内のすべてのノードに配置します。 VM 拡張機能を使用して、すべてのノードにファイルをコピーできます。  `credspec` ファイルには、gMSA アカウント情報を含める必要があります。 `credspec` ファイルの詳細については、「[Service Accounts](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/live/windows-server-container-tools/ServiceAccounts)」(サービス アカウント) を参照してください。 資格情報の指定と `Hostname` タグは、アプリケーション マニフェストに指定されています。 `Hostname` タグは、コンテナーが実行されている gMSA アカウント名と一致する必要があります。  `Hostname` タグを使用すると、Kerberos 認証を使用して、コンテナーが自身をドメイン内の他のサービスに対して認証することができます。  アプリケーション マニフェストで `Hostname` と `credspec` を指定するサンプルを次のスニペットに示します。

```xml
<Policies>
  <ContainerHostPolicies CodePackageRef="NodeService.Code" Isolation="process" Hostname="gMSAAccountName">
    <SecurityOption Value="credentialspec=file://WebApplication1.json"/>
  </ContainerHostPolicies>
</Policies>
```
次の手順については、次の記事を参照してください。

* [Windows Server 2016 上での Service Fabric への Windows コンテナーのデプロイ](service-fabric-get-started-containers.md)
* [Linux 上での Service Fabric への Docker コンテナーのデプロイ](service-fabric-get-started-containers-linux.md)
