---
title: Uzamsal işlevleri
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: 7b78cbf4dc53ba1bc4148fa0077615e43cc8f9f9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="spatial-functions"></a><span data-ttu-id="de8ac-102">Uzamsal işlevleri</span><span class="sxs-lookup"><span data-stu-id="de8ac-102">Spatial Functions</span></span>
<span data-ttu-id="de8ac-103">Uzamsal türler için hiçbir değişmez değer biçimi yok.</span><span class="sxs-lookup"><span data-stu-id="de8ac-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="de8ac-104">Ancak, iyi bilinen metin biçiminde dizeleriyle çağrı kurallı Entity Framework işlevlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de8ac-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="de8ac-105">Örneğin, aşağıdaki işlev çağrısı geometri noktası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="de8ac-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="de8ac-106">[SpatialEdmFunctions yöntemleri](http://msdn.microsoft.com/library/hh749531.aspx) sayfası tüm uzamsal kurallı Entity Framework yöntemlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="de8ac-106">The [SpatialEdmFunctions Methods](http://msdn.microsoft.com/library/hh749531.aspx) page lists all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="de8ac-107">Hangi parametreler bir işleve iletilmesi gereken görmek için ilgilendiğiniz bir yöntem tıklayın.</span><span class="sxs-lookup"><span data-stu-id="de8ac-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
