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
# <a name="spatial-functions"></a>Uzamsal İşlevler

Uzamsal türler için değişmez değer biçimi yoktur. Ancak, Iyi bilinen metin biçiminde dizeler kullanarak çağırdığınız kurallı Entity Framework işlevleri kullanabilirsiniz. Örneğin, aşağıdaki işlev çağrısı bir geometri noktası oluşturur:  
  
```sql  
GeometryFromText('POINT (43 -73)')  
```  
  
 <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions>Yöntemlerin tüm uzamsal kurallı Entity Framework yöntemleri vardır. Bir işleve hangi parametrelerin geçirilmesi gerektiğini görmek için bir ilgilendiğiniz yönteme tıklayın.
