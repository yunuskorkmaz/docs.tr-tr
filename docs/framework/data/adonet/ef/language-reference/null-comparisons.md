---
title: Null Karşılaştırmalar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
ms.openlocfilehash: 0996b7d864c5892e383cb98d4065e99b096206d1
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854325"
---
# <a name="null-comparisons"></a>Null Karşılaştırmalar
Veri `null` kaynağındaki bir değer, değerin bilinmediğini gösterir. LINQ to Entities sorgularda, belirli hesaplamalar veya karşılaştırmalar yalnızca geçerli veya null olmayan verileri olan satırlarda gerçekleştirilmeleri için null değerleri kontrol edebilirsiniz. Ancak CLR null semantiği, veri kaynağının null semantiklerinden farklı olabilir. Çoğu veritabanı, null karşılaştırmaları işlemek için üç değerli mantığın bir sürümünü kullanır. Diğer bir deyişle, null değere karşı bir karşılaştırma, olarak değerlendirmez `true` veya `false`olarak değerlendirilir `unknown`. Genellikle bu, ANSI null değerleri uygulamasıdır, ancak bu her zaman durum değildir.  
  
 Varsayılan olarak SQL Server, null-eşittir-null karşılaştırması null değer döndürür. Aşağıdaki örnekte, null `ShipDate` olduğu satırlar sonuç kümesinden çıkarılır ve Transact-SQL ifadesinde 0 satır döndürülür.  
  
```  
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
 *Anahtar Seçici* , bir öğeden anahtar ayıklamak için standart sorgu işleçleri içinde kullanılan bir işlevdir. Anahtar Seçicisi işlevinde bir ifade bir sabit ile karşılaştırılabilir. Bir ifade null sabitle karşılaştırıldığı veya iki null sabit değer karşılaştırılmadığında CLR null semantiğinin anlamı vardır. Veri kaynağında null değeri olan iki sütun karşılaştırılabilince depo null semantiğinin anlamı vardır. Anahtar seçicileri, ve gibi gruplandırma ve sıralama standart sorgu işleçleri <xref:System.Linq.Queryable.GroupBy%2A>içinde bulunur ve sorgu sonuçlarının sırasını veya gruplandırılmasına göre anahtarlar seçmek için kullanılır.  
  
## <a name="null-property-on-a-null-object"></a>Null nesne üzerinde null özelliği  
 Entity Framework, null bir nesnenin özellikleri null. CLR 'de null nesnenin bir özelliğine başvurmasına çalıştığınızda, bir <xref:System.NullReferenceException>alırsınız. Bir LINQ sorgusu bir null nesnenin özelliğini içeriyorsa, bu durum tutarsız davranışa neden olabilir.  
  
 Örneğin, aşağıdaki sorguda, öğesine `NewProduct` dönüştürme işlemi komut ağacı katmanında yapılır, bu da `Introduced` özelliğin NULL olmasını sağlayabilir. Veritabanı, <xref:System.DateTime> karşılaştırma değeri true olarak değerlendirilip null karşılaştırmaları tanımlıysa, satır dahil edilir.  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a>Toplama Işlevlerine null koleksiyonlar geçirme  
 LINQ to Entities, bir toplama işlevine destekleyen `IQueryable` bir koleksiyon geçirdiğinizde, toplu işlemler veritabanında gerçekleştirilir. Bellek içinde gerçekleştirilmiş bir sorgunun sonuçlarında ve veritabanında gerçekleştirilen bir sorgu sonucunda farklılıklar olabilir. Bellek içi sorgu ile eşleşme yoksa sorgu sıfır döndürür. Veritabanında aynı sorgu döndürülür `null`. Bir LINQ `null` toplama işlevine bir değer geçirilirse, bir özel durum oluşturulur. Olası `null` değerleri kabul etmek için, sorgu sonuçlarını alan türlerin türlerini ve özelliklerini null yapılabilir türlere atayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorgu İfadeleri](expressions-in-linq-to-entities-queries.md)
