---
title: "Null karşılaştırmaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0b29caeed4bf60a5a7ad723ffd46520a89a5bd87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="null-comparisons"></a>Null karşılaştırmaları
A `null` veri kaynağındaki değer, değer bilinmeyen olduğunu gösterir. İçinde [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] sorgular, kontrol edebilirsiniz null değerleri bu nedenle, bazı hesaplamalar veya karşılaştırmaları yalnızca geçerli veya boş olan satırlar üzerinde gerçekleştirilen veri. CLR null semantiği, ancak veri kaynağı null semantiği farklı olabilir. Çoğu veritabanları, null karşılaştırma işlemek için üç değerli mantığı sürümünü kullanın. Diğer bir deyişle, bir null değer karşılaştırmak için değerlendirmez `true` veya `false`, için değerlendirir `unknown`. Genellikle bu ANSI null değerlere uygulamasıdır, ancak bu her zaman geçerli değildir.  
  
 SQL Server'da varsayılan olarak, null eşittir null karşılaştırma null değeri döndürür. Aşağıdaki örnekte, satırları nerede `ShipDate` null sonuç kümesinden hariç tutulur ve [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] deyimi 0 satır döndürebildiği.  
  
```  
-- Find order details and orders with no ship date.  
SELECT h.SalesOrderID  
FROM Sales.SalesOrderHeader h  
JOIN Sales.SalesOrderDetail o ON o.SalesOrderID = h.SalesOrderID  
WHERE h.ShipDate IS Null  
```  
  
 Null eşittir null karşılaştırma doğru döndüğü bu CLR null semantiğini çok farklı değildir.  
  
 Aşağıdaki LINQ sorgusu CLR ifade edilir, ancak veri kaynağında yürütülür. CLR semantiği veri kaynağında uyulacaktır garanti olduğundan, beklenen bir davranış belirsiz.  
  
 [!code-csharp[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#joinonnull)]
 [!code-vb[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#joinonnull)]  
  
## <a name="key-selectors"></a>Anahtar Seçici  
 A *anahtar Seçici* standart sorgu işleçleri bir anahtarı bir öğeden çıkarmak için kullanılan bir işlev. Anahtar Seçici işlevinde bir ifadenin bir sabit ile karşılaştırılabilir. CLR boş semantiği bir ifade null bir sabite karşılaştırılır veya iki null sabit karşılaştırılır sergilenen. İki sütun veri kaynağındaki null değerler ile karşılaştırıldığında, mağaza null semantiği sergilenen. Anahtar Seçici gruplandırma ve standart sorgu işleçleri gibi sıralama çoğunda bulunan <xref:System.Linq.Queryable.GroupBy%2A>ve anahtarları olarak siparişe seçin veya sorgu sonuçları gruplandırmak için kullanılır.  
  
## <a name="null-property-on-a-null-object"></a>Null özellik Null bir nesne üzerinde  
 İçinde [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)], null bir nesne özelliklerini null. CLR içinde null bir nesnenin bir özelliğini başvuru girişiminde bulunduğunuzda alacak bir <xref:System.NullReferenceException>. LINQ Sorgu null bir nesnenin bir özelliğini içerir, bu tutarsız davranışlara neden olabilir.  
  
 Örneğin, sorguda aşağıdaki dönüştürme `NewProduct` sonuçlanabilir komut ağacı katmanda yapılır `Introduced` özelliği null olması. Veritabanı boş karşılaştırmalar tanımladıysanız şekilde <xref:System.DateTime> karşılaştırma doğru olarak değerlendirir, satır dahil edilir.  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## <a name="passing-null-collections-to-aggregate-functions"></a>Toplama işlevlerinin Null koleksiyonlarını geçirme  
 İçinde [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], destekleyen bir koleksiyonu geçirdiğinizde `IQueryable` bir toplama işlevi için veritabanına toplama işlemleri gerçekleştirilir. Bellek içinde gerçekleştirilen bir sorgu ve veritabanına gerçekleştirilen sorgu sonuçları farklılıklar olabilir. Herhangi bir eşleşme varsa bir bellek içi sorgusu ile sorgu sıfır döndürür. Adlı veritabanı, aynı sorgu döndürür `null`. Varsa bir `null` LINQ Toplama işlevi için geçirilen değer, bir özel durum. Olası kabul etmek için `null` değerleri, cast türleri ve türlerin boş değer atanabilir türler için sorgu sonuçlarını almak özellikleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to Entities Sorgu İfadeleri](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
