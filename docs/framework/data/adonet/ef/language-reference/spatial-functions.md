---
title: Uzamsal İşlevler
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: eba384e77389f82006479f165178e80fcac244b1
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319296"
---
# <a name="spatial-functions"></a><span data-ttu-id="defde-102">Uzamsal İşlevler</span><span class="sxs-lookup"><span data-stu-id="defde-102">Spatial Functions</span></span>
<span data-ttu-id="defde-103">Uzamsal türler için değişmez değer biçimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="defde-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="defde-104">Ancak, Iyi bilinen metin biçiminde dizeler kullanarak çağırdığınız kurallı Entity Framework işlevleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="defde-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="defde-105">Örneğin, aşağıdaki işlev çağrısı bir geometri noktası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="defde-105">For example, the following function call creates a geometry point:</span></span>  
  
```sql  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="defde-106">@No__t-0 yöntemlerinde tüm uzamsal kurallı Entity Framework yöntemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="defde-106">The <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> methods have all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="defde-107">Bir işleve hangi parametrelerin geçirilmesi gerektiğini görmek için bir ilgilendiğiniz yönteme tıklayın.</span><span class="sxs-lookup"><span data-stu-id="defde-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
