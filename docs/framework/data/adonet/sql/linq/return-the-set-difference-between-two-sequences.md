---
title: İki Dizi Arasındaki Küme Farkını Döndürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 49a8d22377ef1f7d0fde16880a82002754e1bbc4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200335"
---
# <a name="return-the-set-difference-between-two-sequences"></a>İki Dizi Arasındaki Küme Farkını Döndürme

<xref:System.Linq.Queryable.Except%2A>İki sıra arasındaki küme farkını döndürmek için işlecini kullanın.  
  
## <a name="example"></a>Örnek  

 Bu örnek, <xref:System.Linq.Queryable.Except%2A> `Customers` canlı ancak canlı olmayan tüm ülkelerin/bölgelerin bir dizisini döndürmek için kullanır `Employees` .  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' De, <xref:System.Linq.Queryable.Except%2A> işlem yalnızca kümeler üzerinde tanımlıdır. Multisets semantiği tanımsızdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu örnekleri](query-examples.md)
- [Standart Sorgu İşleci Çevirisi](standard-query-operator-translation.md)
