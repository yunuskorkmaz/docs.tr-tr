---
title: Uzamsal İşlevler
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: 09402633c5e7f591a534992fc92655e6a2d1d88d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797702"
---
# <a name="spatial-functions"></a><span data-ttu-id="21337-102">Uzamsal İşlevler</span><span class="sxs-lookup"><span data-stu-id="21337-102">Spatial Functions</span></span>
<span data-ttu-id="21337-103">Uzamsal türler için sabit biçim yoktur.</span><span class="sxs-lookup"><span data-stu-id="21337-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="21337-104">Ancak, iyi bilinen metin biçiminde dizeleriyle çağrı kurallı Entity Framework işlevleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="21337-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="21337-105">Örneğin, aşağıdaki işlev çağrısı geometri noktası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="21337-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="21337-106"><xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> Yöntemi uzamsal kurallı Entity Framework yöntemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="21337-106">The <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> methods have all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="21337-107">Hangi parametreler bir işleve geçilmesi gerekir görmek için ilgilendiğiniz bir yöntemi tıklayın.</span><span class="sxs-lookup"><span data-stu-id="21337-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
