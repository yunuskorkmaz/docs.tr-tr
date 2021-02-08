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
# <a name="spatial-functions"></a>Uzamsal İşlevler

Uzamsal türler için değişmez değer biçimi yoktur. Ancak, Well-Known metin biçiminde dizeler kullanarak çağırdığınız kurallı Entity Framework işlevleri kullanabilirsiniz. Örneğin, aşağıdaki işlev çağrısı bir geometri noktası oluşturur:  
  
```sql  
GeometryFromText('POINT (43 -73)')  
```  
  
 <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions>Yöntemlerin tüm uzamsal kurallı Entity Framework yöntemleri vardır. Bir işleve hangi parametrelerin geçirilmesi gerektiğini görmek için bir ilgilendiğiniz yönteme tıklayın.
