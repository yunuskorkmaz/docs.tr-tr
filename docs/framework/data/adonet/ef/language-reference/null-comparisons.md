---
title: Null Karşılaştırmalar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
ms.openlocfilehash: f3bbb55ec65df1af776779682d307a67034e34b3
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489905"
---
# <a name="null-comparisons"></a>Null Karşılaştırmalar
A `null` değerindeki veri kaynağı değeri bilinmeyen olduğunu gösterir. İçinde [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgular, denetleyebilirsiniz null değerler, bu nedenle, bazı hesaplamalar veya karşılaştırmalar yalnızca geçerli veya null olmayan, içeren satırları üzerinde gerçekleştirilen veri. CLR null semantikler, ancak veri kaynağı bir null semantiğe farklı olabilir. Çoğu veritabanı, null karşılaştırmalar işlemek için mantığı üç değerli bir sürümünü kullanın. Diğer bir deyişle, bir null değeri karşılaştırmak için değerlendirilmiyor `true` veya `false`, olarak değerlendirilen `unknown`. ANSI null değerlere uygulaması genellikle budur ancak bu her zaman böyle değildir.  
  
 SQL Server'da varsayılan olarak null eşittir null karşılaştırma null değeri döndürür. Aşağıdaki örnekte, satırları burada `ShipDate` olan null sonuç kümesinden dışlanan ve Transact-SQL deyimini 0 satırları döndürür.  
  
```  
-- Find order details and orders with no ship date.  
SELECT h.SalesOrderID  
FROM Sales.SalesOrderHeader h  
JOIN Sales.SalesOrderDetail o ON o.SalesOrderID = h.SalesOrderID  
WHERE h.ShipDate IS Null  
```  
  
 Bu null eşittir null karşılaştırma doğru döndüğü CLR null semantiğe çok farklıdır.  
  
 Aşağıdaki LINQ sorgusu CLR'de gösterilir, ancak veri kaynağında yürütülür. CLR semantik veri kaynağında uyulacaktır garanti olduğundan, Beklenen davranış belirsiz.  
  
 [!code-csharp[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#joinonnull)]
 [!code-vb[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#joinonnull)]  
  
## <a name="key-selectors"></a>Anahtar Seçici  
 A *anahtar Seçici* standart sorgu işleçleri öğeden bir anahtarı ayıklamak için kullanılan bir işlevdir. Anahtar Seçici işlevinde bir ifade bir sabit ile karşılaştırılabilir. CLR null semantikler, bir ifade için bir null sabit karşılaştırılır veya iki boş sabitlerini karşılaştırıldığında sergilenen. İki sütun veri kaynağında null değerler ile karşılaştırıldığında, Store null semantikler izleyen gösteriyordu. Anahtar Seçici çok gruplandırma ve standart sorgu işleçleri gibi sıralama bulunan <xref:System.Linq.Queryable.GroupBy%2A>ve siparişine ait anahtarları seçin veya sorgu sonuçları gruplandırmak için kullanılır.  
  
## <a name="null-property-on-a-null-object"></a>Bir Null nesne null özelliği  
 İçinde [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)], bir null Nesne Özellikleri null. CLR içinde null bir nesnenin bir özelliğini başvuru girişiminde bulunduğunuzda alacak bir <xref:System.NullReferenceException>. LINQ sorgusu null bir nesnenin bir özelliğini içerdiğinde, bu tutarsız davranışlara neden olabilir.  
  
 Örneğin, sorguda aşağıdaki dönüştürme `NewProduct` sonuçlanabilir komut ağacı katmanda yapılır `Introduced` null olan özelliği. Veritabanı null karşılaştırmalar tanımlanmışsa şekilde <xref:System.DateTime> karşılaştırma true olarak değerlendirilir, satır dahil edilir.  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a>Toplama işlevleri için boş koleksiyonları geçirme  
 İçinde [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], destekleyen bir koleksiyonu geçirdiğinizde `IQueryable` bir toplama işlevi toplama işlemleri veritabanına gerçekleştirilir. Bellek içinde gerçekleştirilen bir sorgu ve veritabanına gerçekleştirilen sorgu sonuçlarını farklılıklar olabilir. Herhangi bir eşleşme varsa bir bellek içi sorgusu ile sorgu sıfır döndürür. Veritabanını, aynı sorgu döndürür `null`. Varsa bir `null` LINQ Toplama işlevi için geçirilen değer, bir özel durum oluşturulur. Olası kabul edecek şekilde `null` değerleri, cast türleri ve türlerin boş değer atanabilir türler için sorgu sonuçlarını alma özellikleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
