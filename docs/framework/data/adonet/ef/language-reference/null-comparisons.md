---
title: Null Karşılaştırmalar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
ms.openlocfilehash: 71b7c4d86debe8cf267b1b65e3d176cbc4704e6d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185112"
---
# <a name="null-comparisons"></a>Null Karşılaştırmalar

`null`Veri kaynağındaki bir değer, değerin bilinmediğini gösterir. LINQ to Entities sorgularda, belirli hesaplamalar veya karşılaştırmalar yalnızca geçerli veya null olmayan verileri olan satırlarda gerçekleştirilmeleri için null değerleri kontrol edebilirsiniz. Ancak CLR null semantiği, veri kaynağının null semantiklerinden farklı olabilir. Çoğu veritabanı, null karşılaştırmaları işlemek için üç değerli mantığın bir sürümünü kullanır. Diğer bir deyişle, null değere karşı bir karşılaştırma, olarak değerlendirmez `true` veya olarak `false` değerlendirilir `unknown` . Genellikle bu, ANSI null değerleri uygulamasıdır, ancak bu her zaman durum değildir.  
  
 Varsayılan olarak SQL Server, null-eşittir-null karşılaştırması null değer döndürür. Aşağıdaki örnekte, `ShipDate` null olduğu satırlar sonuç kümesinden çıkarılır ve Transact-SQL ifadesinde 0 satır döndürülür.  
  
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

 *Anahtar Seçici* , bir öğeden anahtar ayıklamak için standart sorgu işleçleri içinde kullanılan bir işlevdir. Anahtar Seçicisi işlevinde bir ifade bir sabit ile karşılaştırılabilir. Bir ifade null sabitle karşılaştırıldığı veya iki null sabit değer karşılaştırılmadığında CLR null semantiğinin anlamı vardır. Veri kaynağında null değeri olan iki sütun karşılaştırılabilince depo null semantiğinin anlamı vardır. Anahtar seçicileri, ve gibi gruplandırma ve sıralama standart sorgu işleçleri içinde bulunur <xref:System.Linq.Queryable.GroupBy%2A> ve sorgu sonuçlarının sırasını veya gruplandırılmasına göre anahtarlar seçmek için kullanılır.  
  
## <a name="null-property-on-a-null-object"></a>Null nesne üzerinde null özelliği  

 Entity Framework, null bir nesnenin özellikleri null. CLR 'de null nesnenin bir özelliğine başvurmasına çalıştığınızda, bir alırsınız <xref:System.NullReferenceException> . Bir LINQ sorgusu bir null nesnenin özelliğini içeriyorsa, bu durum tutarsız davranışa neden olabilir.  
  
 Örneğin, aşağıdaki sorguda, öğesine dönüştürme `NewProduct` işlemi komut ağacı katmanında yapılır, bu da `Introduced` özelliğin NULL olmasını sağlayabilir. Veritabanı, <xref:System.DateTime> karşılaştırma değeri true olarak değerlendirilip null karşılaştırmaları tanımlıysa, satır dahil edilir.  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a>Toplama Işlevlerine null koleksiyonlar geçirme  

 LINQ to Entities, bir toplama işlevine destekleyen bir koleksiyon geçirdiğinizde `IQueryable` , toplu işlemler veritabanında gerçekleştirilir. Bellek içinde gerçekleştirilmiş bir sorgunun sonuçlarında ve veritabanında gerçekleştirilen bir sorgu sonucunda farklılıklar olabilir. Bellek içi sorgu ile eşleşme yoksa sorgu sıfır döndürür. Veritabanında aynı sorgu döndürülür `null` . Bir `null` LINQ toplama işlevine bir değer geçirilirse, bir özel durum oluşturulur. Olası değerleri kabul etmek için `null` , sorgu sonuçlarını alan türlerin türlerini ve özelliklerini null yapılabilir değer türlerine atayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorgu İfadeleri](expressions-in-linq-to-entities-queries.md)
