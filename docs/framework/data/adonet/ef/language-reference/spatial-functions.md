---
title: Uzamsal İşlevler
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: ad6b722e84aae40354e30434b107752d02352645
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43776959"
---
# <a name="spatial-functions"></a><span data-ttu-id="e65fb-102">Uzamsal İşlevler</span><span class="sxs-lookup"><span data-stu-id="e65fb-102">Spatial Functions</span></span>
<span data-ttu-id="e65fb-103">Uzamsal türler için sabit biçim yoktur.</span><span class="sxs-lookup"><span data-stu-id="e65fb-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="e65fb-104">Ancak, iyi bilinen metin biçiminde dizeleriyle çağrı kurallı Entity Framework işlevleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e65fb-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="e65fb-105">Örneğin, aşağıdaki işlev çağrısı geometri noktası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e65fb-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="e65fb-106">[SpatialEdmFunctions yöntemleri](https://msdn.microsoft.com/library/hh749531.aspx) sayfası uzamsal kurallı Entity Framework yöntemlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="e65fb-106">The [SpatialEdmFunctions Methods](https://msdn.microsoft.com/library/hh749531.aspx) page lists all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="e65fb-107">Hangi parametreler bir işleve geçilmesi gerekir görmek için ilgilendiğiniz bir yöntemi tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e65fb-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
