---
title: Null Karşılaştırmalar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
ms.openlocfilehash: 8eca2ee1afec5662e40d4f43347c469bd538c066
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319495"
---
# <a name="null-comparisons"></a>Null Karşılaştırmalar
Veri kaynağındaki bir `null` değeri, değerin bilinmediğini gösterir. LINQ to Entities sorgularda, belirli hesaplamalar veya karşılaştırmalar yalnızca geçerli veya null olmayan verileri olan satırlarda gerçekleştirilmeleri için null değerleri kontrol edebilirsiniz. Ancak CLR null semantiği, veri kaynağının null semantiklerinden farklı olabilir. Çoğu veritabanı, null karşılaştırmaları işlemek için üç değerli mantığın bir sürümünü kullanır. Diğer bir deyişle, null değere karşı bir karşılaştırma `true` veya `false` olarak değerlendirilmez; `unknown` olarak değerlendirilir. Genellikle bu, ANSI null değerleri uygulamasıdır, ancak bu her zaman durum değildir.  
  
 Varsayılan olarak SQL Server, null-eşittir-null karşılaştırması null değer döndürür. Aşağıdaki örnekte, `ShipDate` ' ın null olduğu satırlar sonuç kümesinden çıkarılır ve Transact-SQL ifadesinde 0 satır döndürülür.  
  
```sql  
-- Find order details and orders with no ship date.  
SELECT h.SalesOrderID  
FROM Sales.SalesOrderHeader h  
JOIN Sales.SalesOrderDetail o ON o.SalesOrderID = h.SalesOrderID  
WHERE h.ShipDate IS Null  
```  
  
 Bu, null-Equals-null karşılaştırmasının true döndüğü CLR null semantiğinin çok farklıdır.  
  
 Aşağıdaki LINQ sorgusu CLR 'de ifade edilir, ancak veri kaynağında yürütülür. CLR semantiğinin veri kaynağında kabul edildiği garantisi olmadığından, beklenen davranışın belirsiz olması gerekir.  
  
 [!code-csharp[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#joinonnull)]
 [!code-vb[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#joinonnull)]  
  
## <a name="key-selectors"></a>Anahtar seçicileri  
 *Anahtar Seçici* , bir öğeden anahtar ayıklamak için standart sorgu işleçleri içinde kullanılan bir işlevdir. Anahtar Seçicisi işlevinde bir ifade bir sabit ile karşılaştırılabilir. Bir ifade null sabitle karşılaştırıldığı veya iki null sabit değer karşılaştırılmadığında CLR null semantiğinin anlamı vardır. Veri kaynağında null değeri olan iki sütun karşılaştırılabilince depo null semantiğinin anlamı vardır. Anahtar seçicileri, <xref:System.Linq.Queryable.GroupBy%2A> gibi gruplandırma ve sıralama standart sorgu işleçleri içinde bulunur ve sorgu sonuçlarının sırasını veya gruplandırılmasına göre anahtar seçmek için kullanılır.  
  
## <a name="null-property-on-a-null-object"></a>Null nesne üzerinde null özelliği  
 Entity Framework, null bir nesnenin özellikleri null. CLR 'de null nesnenin bir özelliğine başvurmasına çalıştığınızda, bir <xref:System.NullReferenceException> alırsınız. Bir LINQ sorgusu bir null nesnenin özelliğini içeriyorsa, bu durum tutarsız davranışa neden olabilir.  
  
 Örneğin, aşağıdaki sorguda, `NewProduct` ' a dönüştürme işlemi komut ağacı katmanında yapılır, bu da `Introduced` özelliğinin null olmasını sağlayabilir. Veritabanı, <xref:System.DateTime> karşılaştırması doğru olarak değerlendirilip null karşılaştırmaları tanımlıysa, satır dahil edilir.  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a>Toplama Işlevlerine null koleksiyonlar geçirme  
 LINQ to Entities ' de, bir toplama işlevine `IQueryable` ' ı destekleyen bir koleksiyon geçirdiğinizde, toplu işlemler veritabanında gerçekleştirilir. Bellek içinde gerçekleştirilmiş bir sorgunun sonuçlarında ve veritabanında gerçekleştirilen bir sorgu sonucunda farklılıklar olabilir. Bellek içi sorgu ile eşleşme yoksa sorgu sıfır döndürür. Veritabanında, aynı sorgu `null` ' ı döndürür. Bir `null` değeri bir LINQ toplama işlevine geçirilirse, bir özel durum oluşturulur. Olası `null` değerlerini kabul etmek için, sorgu sonuçlarını alan türlerin türlerini ve özelliklerini null yapılabilir türlere atayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorgu İfadeleri](expressions-in-linq-to-entities-queries.md)
