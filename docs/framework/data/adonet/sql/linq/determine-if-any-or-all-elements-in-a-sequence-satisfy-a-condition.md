---
title: Dizideki Öğelerin Herhangi Birinin veya Tümünün Bir Koşulu Karşılayıp Karşılamadığını Belirleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: c1bc8e18f2e3b0c67b98713e67fc261649a6a0e2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128342"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a>Dizideki Öğelerin Herhangi Birinin veya Tümünün Bir Koşulu Karşılayıp Karşılamadığını Belirleme
<xref:System.Linq.Enumerable.All%2A> İşleci döndürür `true` bir dizideki tüm öğeler koşulu karşılaması durumunda.  
  
 <xref:System.Linq.Queryable.Any%2A> İşleci döndürür `true` bir dizideki herhangi bir öğenin bir koşulu karşılıyorsa.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, en az bir sipariş olan müşteriler bir dizisini döndürür. `Where` / `where` Yan tümcesi değerlendirilen `true` , verilen `Customer` içeren `Order`.  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki Visual Basic kod, sipariş vermiş değil Müşteri listesini belirler ve bu listedeki her müşteri için bir ilgili kişi adı sağlanır sağlar.  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki C# örnek müşteri siparişleri olan bir dizi döndürür bir `ShipCity` "C" ile başlayan. Ayrıca dönüş sipariş olan müşteriler bunlara dahildir. (Tasarıma göre <xref:System.Linq.Queryable.All%2A> işleci döndürür `true` boş bir dizi için.) Sipariş müşterilerle ortadan konsol çıkışında kullanarak `Count` işleci.  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
