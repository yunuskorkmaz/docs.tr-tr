---
title: İşleç önceliği (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: f8aa0f213a24d6431d8910af849571a67fbd9f57
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175648"
---
# <a name="operator-precedence-entity-sql"></a>İşleç önceliği (Entity SQL)

Bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorguda birden çok işleç olduğunda, işleç önceliği işlemlerin gerçekleştirileceği diziyi belirler. Yürütmenin sırası, sorgu sonucunu önemli ölçüde etkileyebilir.  
  
 İşleçler aşağıdaki tabloda gösterilen öncelik düzeylerine sahiptir. Daha yüksek düzeyi olan bir işleç, daha düşük düzeydeki bir işleçten önce değerlendirilir.  
  
|Düzey|İşlem türü|İşleç|  
|-----------|--------------------|--------------|  
|1|Birincil|`. , [] ()`|  
|2|Birli|`! not`|  
|3|Çarpımsal|`* / %`|  
|4|Toplamsal|`+ -`|  
|5|Sıralama|`< > <= >=`|  
|6|Eşitlik|`= != <>`|  
|7|Koşullu VE|`and &&`|  
|8|Koşullu VEYA|`or &#124;&#124;`|  
  
 Bir ifadedeki iki operatör aynı operatör öncelik düzeyine sahip olduğunda, sorgudaki konumlarına göre soldan sağa değerlendirilir. Örneğin, `x+y-z` olarak değerlendirilir `(x+y)-z` .  
  
 Bir sorgudaki operatörlerin tanımlanmış önceliğini geçersiz kılmak için parantezleri kullanabilirsiniz. Parantez içindeki her şey, sonucun parantez dışında herhangi bir operatör tarafından kullanılabilmesi için önce tek bir sonuç verecek şekilde değerlendirilir. Örneğin, ile `x+y*z` çarpar `y` `z` ve sonra ekler `x` , ancak `(x+y)*z` `x` sonucunu öğesine ekler `y` ve sonra sonucu ile çarpar `z` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL’e Genel Bakış](entity-sql-overview.md)
