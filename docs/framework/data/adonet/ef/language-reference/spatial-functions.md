---
title: Uzamsal İşlevler
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: 09402633c5e7f591a534992fc92655e6a2d1d88d
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904483"
---
# <a name="spatial-functions"></a><span data-ttu-id="e084b-102">Uzamsal İşlevler</span><span class="sxs-lookup"><span data-stu-id="e084b-102">Spatial Functions</span></span>
<span data-ttu-id="e084b-103">Uzamsal türler için sabit biçim yoktur.</span><span class="sxs-lookup"><span data-stu-id="e084b-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="e084b-104">Ancak, iyi bilinen metin biçiminde dizeleriyle çağrı kurallı Entity Framework işlevleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e084b-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="e084b-105">Örneğin, aşağıdaki işlev çağrısı geometri noktası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e084b-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="e084b-106"><xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> Yöntemi uzamsal kurallı Entity Framework yöntemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="e084b-106">The <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> methods have all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="e084b-107">Hangi parametreler bir işleve geçilmesi gerekir görmek için ilgilendiğiniz bir yöntemi tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e084b-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
