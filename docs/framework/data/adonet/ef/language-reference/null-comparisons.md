---
title: Null Karşılaştırmalar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
ms.openlocfilehash: 697c933daeb3c68fb4ea89a957b639a79a9407f8
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249662"
---
# <a name="null-comparisons"></a>Null Karşılaştırmalar
Veri `null` kaynağındaki bir değer, değerin bilinmediğini gösterir. LINQ'dan Varlıklara sorgularda, belirli hesaplamaların veya karşılaştırmaların yalnızca geçerli veya geçersiz olmayan verilere sahip satırlarda gerçekleştirilmelerini sağlamak için null değerlerini denetleyebilirsiniz. Ancak CLR null semantik, veri kaynağının null semantiklerinden farklı olabilir. Çoğu veritabanları null karşılaştırmaları işlemek için üç değerli mantık bir sürümünü kullanır. Diğer bir şey, null değerine karşı `true` `false`bir karşılaştırma değerlendirmez veya , `unknown`o için değerlendirir . Genellikle bu ANSI nulls bir uygulamadır, ancak bu her zaman böyle değildir.  
  
 SQL Server'da varsayılan olarak, null-equals-null karşılaştırması null değeri döndürür. Aşağıdaki örnekte, null olan `ShipDate` satırlar sonuç kümesinin dışında tutulur ve Transact-SQL deyimi 0 satır döndürüler.  
  
```sql  
-- Find order details and orders with no ship date.  
SELECT h.SalesOrderID  
FROM Sales.SalesOrderHeader h  
JOIN Sales.SalesOrderDetail o ON o.SalesOrderID = h.SalesOrderID  
WHERE h.ShipDate IS Null  
```  
  
 Bu, null-equals-null karşılaştırmasının doğru döndüğü CLR null semantikinden çok farklıdır.  
  
 Aşağıdaki LINQ sorgusu CLR'de ifade edilir, ancak veri kaynağında yürütülür. CLR semantikinin veri kaynağında onurlandırılacağına dair bir garanti olmadığından, beklenen davranış belirsizdir.  
  
 [!code-csharp[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#joinonnull)]
 [!code-vb[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#joinonnull)]  
  
## <a name="key-selectors"></a>Anahtar Seçiciler  
 *Anahtar seçici,* standart sorgu işleçlerinde bir öğeden bir anahtar ayıklamak için kullanılan bir işlevdir. Anahtar seçici işlevinde, bir ifade bir sabitle karşılaştırılabilir. Bir ifade null constant ile karşılaştırıldığında veya iki null sabit karşılaştırıldığında CLR null semantik sergilenir. Veri kaynağında null değerleri olan iki sütun karşılaştırılırsa depo null semantik leri sergilenir. Anahtar seçiciler, <xref:System.Linq.Queryable.GroupBy%2A>standart sorgu işleçlerini gruplandırma ve sıralama gibi birçok sayıda bulunur ve sorgu sonuçlarını sipariş etmek veya gruplamak için anahtarları seçmek için kullanılır.  
  
## <a name="null-property-on-a-null-object"></a>Null Nesneüzerinde Null Özellik  
 Varlık Çerçevesi'nde, null nesnenin özellikleri null'dur. CLR'de null bir nesnenin özelliğine başvurmayı denediğinizde, bir <xref:System.NullReferenceException>. BIR LINQ sorgusu null nesnenin bir özelliği ni içeriyorsa, bu tutarsız davranışlara neden olabilir.  
  
 Örneğin, aşağıdaki sorguda, döküm `NewProduct` komut ağacı katmanında yapılır ve bu `Introduced` da özelliğin null olmasına neden olabilir. Veritabanı, karşılaştırmanın <xref:System.DateTime> doğru olarak değerlendireceği null karşılaştırmaları tanımlamışsa, satır dahil edilir.  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a>Null Koleksiyonlarının Toplu Fonksiyonlara Geçirilmesi  
 LINQ'dan Varlıklara, bir toplama işlevini `IQueryable` destekleyen bir koleksiyon geçtiğinde, veritabanında toplu işlemler gerçekleştirilir. Bellekte gerçekleştirilen bir sorgunun ve veritabanında gerçekleştirilen bir sorgunun sonuçlarında farklılıklar olabilir. Bellek içi sorguda, eşleşme yoksa sorgu sıfır döndürür. Veritabanında, aynı sorgu `null`döndürür. Bir `null` değer LINQ toplam işlevine aktarılırsa, bir özel durum atılır. Olası `null` değerleri kabul etmek için, sorgu sonuçlarını alan türlerin türlerini ve özelliklerini geçersiz değer türlerine döküm.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorgu İfadeleri](expressions-in-linq-to-entities-queries.md)
