---
description: 'Daha fazla bilgi edinin: uzamsal Işlevler'
title: Uzamsal İşlevler
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: cde8f1b0fcf5904eb33fe061de69e566da2804dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767888"
---
# <a name="spatial-functions"></a><span data-ttu-id="07da0-103">Uzamsal İşlevler</span><span class="sxs-lookup"><span data-stu-id="07da0-103">Spatial Functions</span></span>

<span data-ttu-id="07da0-104">Uzamsal türler için değişmez değer biçimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="07da0-104">There is no literal format for spatial types.</span></span> <span data-ttu-id="07da0-105">Ancak, Well-Known metin biçiminde dizeler kullanarak çağırdığınız kurallı Entity Framework işlevleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="07da0-105">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="07da0-106">Örneğin, aşağıdaki işlev çağrısı bir geometri noktası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="07da0-106">For example, the following function call creates a geometry point:</span></span>  
  
```sql  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="07da0-107"><xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions>Yöntemlerin tüm uzamsal kurallı Entity Framework yöntemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="07da0-107">The <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> methods have all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="07da0-108">Bir işleve hangi parametrelerin geçirilmesi gerektiğini görmek için bir ilgilendiğiniz yönteme tıklayın.</span><span class="sxs-lookup"><span data-stu-id="07da0-108">Click on a method of interest to see what parameters should be passed to a function.</span></span>
