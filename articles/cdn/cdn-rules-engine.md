---
title: Azure CDN ルール エンジンを使用した HTTP 動作のオーバーライド | Microsoft Docs
description: 規則エンジンでは、Azure CDN における HTTP 要求の処理方法 (特定種類のコンテンツの配信のブロックなど) のカスタマイズのほか、キャッシュ ポリシーの定義、HTTP ヘッダーの変更などを行えます。
services: cdn
documentationcenter: ''
author: dksimpson
manager: cfowler
editor: ''
ms.assetid: 625a912b-91f2-485d-8991-128cc194ee71
ms.service: cdn
ms.workload: tbd
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 06/11/2018
ms.author: v-deasim
ms.openlocfilehash: df8114aaf5b4672ea51482978abde6f0ce724528
ms.sourcegitcommit: 1b8665f1fff36a13af0cbc4c399c16f62e9884f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35261051"
---
# <a name="override-http-behavior-using-the-azure-cdn-rules-engine"></a>Azure CDN ルール エンジンを使用した HTTP 動作のオーバーライド
[!INCLUDE [cdn-premium-feature](../../includes/cdn-premium-feature.md)]

## <a name="overview"></a>概要
Azure CDN ルール エンジンを使用すると、HTTP 要求を処理する方法をカスタマイズできます。 たとえば、特定の種類のコンテンツの配信のブロック、キャッシュ ポリシーの定義、HTTP ヘッダーの変更などを行うことができます。 このチュートリアルでは、CDN 資産のキャッシュ動作を変更するルールを作成する方法について説明します。 ルール エンジンの構文の詳細については、「[Azure CDN ルール エンジンのリファレンス](cdn-rules-engine-reference.md)」をご覧ください。

## <a name="access"></a>Access
ルール エンジンにアクセスするには、まず、**[CDN プロファイル]** ページの上部の **[管理]** を選択して、Azure CDN 管理ページにアクセスする必要があります。 エンドポイントが動的サイトの高速化 (DSA) に最適化されているかどうかに応じて、エンドポイントの種類に適したルール セットを使用してルール エンジンにアクセスします。

- 一般的な Web 配信または DSA 以外に最適化されたエンドポイント: 
    
    **[HTTP Large]\(HTTP ラージ\)** タブを選択し、**[ルール エンジン]** を選択します。

    ![HTTP のルール エンジン](./media/cdn-rules-engine/cdn-http-rules-engine.png)

- DSA に最適化されたエンドポイント: 
    
    **[ADN]** タブを選択し、**[ルール エンジン]** を選択します。 
    
    ADN は、DSA コンテンツを指定する際に Verizon で使用される用語です。 ここで作成したルールは、プロファイル内の DSA に最適化されていないエンドポイントでは無視されます。 

    ![DSA のルール エンジン](./media/cdn-rules-engine/cdn-dsa-rules-engine.png)

## <a name="tutorial"></a>チュートリアル
1. **[CDN プロファイル]** ページで、**[管理]** を選択します。
   
    ![[CDN プロファイル] の [管理] ボタン](./media/cdn-rules-engine/cdn-manage-btn.png)
   
    CDN 管理ポータルが開きます。

2. **[HTTP Large]\(HTTP ラージ\)** タブを選択し、**[ルール エンジン]** を選択します。
   
    新しいルールのオプションが表示されます。
   
    ![CDN の新しい規則オプション](./media/cdn-rules-engine/cdn-new-rule.png)
   
   > [!IMPORTANT]
   > 複数の規則が表示される順序は、これらの規則の処理方法に影響します。 前の規則で指定したアクションは、後続の規則でオーバーライドされます。
   > 

3. **[名前 / 説明]** テキストボックスに名前を入力します。

4. ルールを適用する要求の種類を指定します。 既定の一致条件の **[常に]** を使用します。 
   
   ![CDN ルールの一致条件](./media/cdn-rules-engine/cdn-request-type.png)
   
   > [!NOTE]
   > ドロップダウン リストには複数の一致条件が用意されています。 現在選択されている一致条件については、左側の青い情報アイコンをクリックしてください。
   > 
   >  条件式の詳細な一覧については、[ルール エンジンの条件式](cdn-rules-engine-reference-match-conditions.md)に関する記事をご覧ください。
   >  
   > 一致条件の詳細な一覧については、[ルール エンジンの一致条件](cdn-rules-engine-reference-match-conditions.md)に関する記事をご覧ください。
   > 
   > 

5. 新しい機能を追加するには、**[機能]** の横にある **+** をクリックします。  左側のドロップダウンで、 **[内部の最長期間を強制する]** を選択します。  表示されるテキスト ボックスに、「 **300**」と入力します。 その他の既定値は変更しないでください。
   
   ![CDN ルールの機能](./media/cdn-rules-engine/cdn-new-feature.png)
   
   > [!NOTE]
   > ドロップダウン リストには複数の機能が用意されています。 現在選択されている機能については、左側の青い情報アイコンをクリックしてください。 
   >
   > **[Force Internal Max-Age]\(内部の最長期間を強制する\)** では、資産の `Cache-Control` ヘッダーと `Expires` ヘッダーをオーバーライドして、CDN エッジ ノードが配信元の資産を更新するタイミングを制御します。 この例では、CDN エッジ ノードは、資産を 300 秒間 (5 分間) キャッシュしてから、配信元の資産を更新します。
   > 
   > 機能の詳細な一覧については、[ルール エンジンの機能](cdn-rules-engine-reference-features.md)に関する記事をご覧ください。
   > 
   > 

6. **[追加]** を選択して新しいルールを保存します。  次に、新しい規則は承認を待機します。 承認されると、状態が **[保留中の XML]** から **[アクティブな XML]** に変わります。
   
   > [!IMPORTANT]
   > ルールの変更が Azure CDN に反映されるまでに、最大 10 分かかる場合があります。
   > 
   > 

## <a name="see-also"></a>関連項目
* [Azure CDN の概要](cdn-overview.md)
* [ルール エンジンのリファレンス](cdn-rules-engine-reference.md)
* [ルール エンジンの一致条件](cdn-rules-engine-reference-match-conditions.md)
* [ルール エンジンの条件式](cdn-rules-engine-reference-conditional-expressions.md)
* [ルール エンジンの機能](cdn-rules-engine-reference-features.md)
* [Azure Friday: Azure CDN に新しく追加された強力な Premium 機能](https://azure.microsoft.com/documentation/videos/azure-cdns-powerful-new-premium-features/) (ビデオ)