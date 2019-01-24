---
title: İşleç önceliği (varlık SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: c68ac6d89426896b708ac74de1268f8ea8f193c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506845"
---
# <a name="operator-precedence-entity-sql"></a>İşleç önceliği (varlık SQL)
Olduğunda bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu sahip birden çok işleç, İşleç önceliği işlemleri gerçekleştirilir sırasını belirler. Yürütme sırası, sorgu sonucu olarak önemli ölçüde etkileyebilir.  
  
 İşleçler, öncelik düzeyleri aşağıdaki tabloda gösterilen sahip. Daha yüksek bir düzeye sahip bir işleç, daha düşük bir düzeye sahip bir işleç önce değerlendirilir.  
  
|Düzey|İşlem türü|İşleç|  
|-----------|--------------------|--------------|  
|1.|Birincil|`. , [] ()`|  
|2|Birli|`! not`|  
|3|Çarpma|`* / %`|  
|4|Eklenebilir|`+ -`|  
|5|Sıralama|`< > <= >=`|  
|6|Eşitlik|`= != <>`|  
|7|Koşullu VE|`and &&`|  
|8|Koşullu VEYA|`or &#124;&#124;`|  
  
 İki işleç bir ifadede aynı işleci öncelik düzeyine sahip olduğunuzda, bunlar, sağdan sola değerlendirilir sorgu konumlarına göre. Örneğin, `x+y-z` değerlendirmesinde `(x+y)-z`.  
  
 Parantez tanımlı sorgu işleçleri önceliği geçersiz kılmak için kullanabilirsiniz. Parantez içindeki her şeyi ilk sonuç parantezler dışında herhangi bir işleç tarafından kullanılabilir önce tek bir sonuç elde etmek üzere değerlendirilir. Örneğin, `x+y*z` çarpar `y` tarafından `z` ve ekler `x`, ancak `(x+y)*z` ekler `x` için `y` ve sonucu çarpan `z`.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Entity SQL’e Genel Bakış](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
