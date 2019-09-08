---
title: Dizideki Öğelerin Herhangi Birinin veya Tümünün Bir Koşulu Karşılayıp Karşılamadığını Belirleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: 7de65579cb41641aded0b9a320fac59804959ff5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782221"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a>Dizideki Öğelerin Herhangi Birinin veya Tümünün Bir Koşulu Karşılayıp Karşılamadığını Belirleme
İşleci bir dizideki tüm öğelerin bir koşulu karşılayıp karşılamadığını döndürür `true`. <xref:System.Linq.Enumerable.All%2A>  
  
 İşleci <xref:System.Linq.Queryable.Any%2A> , bir `true` dizideki herhangi bir öğe bir koşulu karşılıyorsa döndürür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, en az bir siparişi olan müşteriler dizisini döndürür. `Where` Yantümcesi`Customer` , verilen `true` varsa öğesini değerlendirir .`Order` / `where`  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Visual Basic kod, sipariş yerleştirmediğiniz müşterilerin listesini belirler ve bu listedeki her müşteri için bir kişi adı sağlanır.  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki C# örnek, siparişlerinin `ShipCity` "C" ile başlayan bir müşteri dizisini döndürür. Ayrıca, iadeye dahil olan müşteriler siparişi olmayan müşterilerdir. (Tasarıma göre, <xref:System.Linq.Queryable.All%2A> işleç boş bir sıra için döndürülür `true` .) Siparişi olmayan müşteriler, `Count` işletmen kullanılarak konsol çıkışında ortadan kalkar.  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Örnekleri](query-examples.md)
