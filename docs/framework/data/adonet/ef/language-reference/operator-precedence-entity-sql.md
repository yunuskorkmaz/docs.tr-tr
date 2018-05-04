---
title: İşleç önceliği (varlık SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: ab5158a2af18a422cb82f0d44412bcd85a04dc2a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="operator-precedence-entity-sql"></a>İşleç önceliği (varlık SQL)
Zaman bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu sahip birden çok işleç, İşleç önceliği işlemler gerçekleştirilir sırasını belirler. Yürütme sırasını, sorgu sonucu olarak önemli ölçüde etkileyebilir.  
  
 İşleçler aşağıdaki tabloda gösterilen öncelik düzeyine sahip. Daha yüksek bir düzeye sahip bir işleç daha düşük bir düzeye sahip bir işleç önce değerlendirilir.  
  
|Düzey|İşlem türü|İşleç|  
|-----------|--------------------|--------------|  
|1.|birincil|`. , [] ()`|  
|2|Birli|`! not`|  
|3|Çarpma|`* / %`|  
|4|ADDITIVE|`+ -`|  
|5|Sıralama|`< > <= >=`|  
|6|Eşitlik|`= != <>`|  
|7|Koşullu VE|`and &&`|  
|8|Koşullu VEYA|`or &#124;&#124;`|  
  
 İşleç önceliği düzeyde bir ifadede iki işleç sahip olduğunuzda, soldan sağa değerlendirilme sorgu konumlarına göre. Örneğin, `x+y-z` olarak değerlendirilir `(x+y)-z`.  
  
 Sorgu işleçlerinin tanımlı önceliği geçersiz kılmak için ayraç kullanın. Parantez içindeki her şeyi sonuç parantez dışında herhangi bir işleç tarafından kullanılabilir önce tek bir sonuç elde etmek üzere önce değerlendirilir. Örneğin, `x+y*z` çarpar `y` tarafından `z` ve ardından ekler `x`, ancak `(x+y)*z` ekler `x` için `y` ve sonuç olarak çoğaltır `z`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
