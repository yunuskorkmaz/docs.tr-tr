---
title: Uzamsal İşlevler
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: 7d0979b5166c847244cbeec97acf4fa4f745a259
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169589"
---
# <a name="spatial-functions"></a><span data-ttu-id="eefdc-102">Uzamsal İşlevler</span><span class="sxs-lookup"><span data-stu-id="eefdc-102">Spatial Functions</span></span>

<span data-ttu-id="eefdc-103">Uzamsal türler için değişmez değer biçimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="eefdc-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="eefdc-104">Ancak, Iyi bilinen metin biçiminde dizeler kullanarak çağırdığınız kurallı Entity Framework işlevleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eefdc-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="eefdc-105">Örneğin, aşağıdaki işlev çağrısı bir geometri noktası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="eefdc-105">For example, the following function call creates a geometry point:</span></span>  
  
```sql  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="eefdc-106"><xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions>Yöntemlerin tüm uzamsal kurallı Entity Framework yöntemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="eefdc-106">The <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> methods have all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="eefdc-107">Bir işleve hangi parametrelerin geçirilmesi gerektiğini görmek için bir ilgilendiğiniz yönteme tıklayın.</span><span class="sxs-lookup"><span data-stu-id="eefdc-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
