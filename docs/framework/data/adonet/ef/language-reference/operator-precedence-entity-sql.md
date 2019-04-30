---
title: İşleç önceliği (varlık SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: 722ebe5f0ec530f8c7f86e9f9901451b060903f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760356"
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
