---
title: Dizideki Öğelerin Herhangi Birinin veya Tümünün Bir Koşulu Karşılayıp Karşılamadığını Belirleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: 65a9a7cf289c2006bab14cb384efb07eaea7f7a0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194433"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a>Dizideki Öğelerin Herhangi Birinin veya Tümünün Bir Koşulu Karşılayıp Karşılamadığını Belirleme

<xref:System.Linq.Enumerable.All%2A>İşleci bir `true` dizideki tüm öğelerin bir koşulu karşılayıp karşılamadığını döndürür.  
  
 <xref:System.Linq.Queryable.Any%2A>İşleci, `true` bir dizideki herhangi bir öğe bir koşulu karşılıyorsa döndürür.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, en az bir siparişi olan müşteriler dizisini döndürür. `Where` / `where` Yan tümcesi, verilen varsa öğesini değerlendirir `true` `Customer` `Order` .  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki Visual Basic kod, sipariş yerleştirmediğiniz müşterilerin listesini belirler ve bu listedeki her müşteri için bir kişi adı sağlanır.  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki C# örneği, siparişlerinin `ShipCity` "C" ile başlayan bir dizi müşteriyi döndürür. Ayrıca, iadeye dahil olan müşteriler siparişi olmayan müşterilerdir. (Tasarıma göre, <xref:System.Linq.Queryable.All%2A> işleç `true` boş bir sıra için döndürülür.) Siparişi olmayan müşteriler, işletmen kullanılarak konsol çıkışında ortadan kalkar `Count` .  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu örnekleri](query-examples.md)
