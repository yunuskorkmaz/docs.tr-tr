---
title: Dizideki Öğeleri Döndürme veya Atlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: 885e6bc011041320a3dc7b17d84b2541bf030adf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033468"
---
# <a name="return-or-skip-elements-in-a-sequence"></a>Dizideki Öğeleri Döndürme veya Atlama
Kullanım <xref:System.Linq.Queryable.Take%2A> işleci bir dizideki öğeler, verilen sayıda dönün ve sonra kalanını atlayın.  
  
 Kullanım <xref:System.Linq.Queryable.Skip%2A> işleci bir dizideki öğelerin verilen bir sayının atlamayı ve sonra kalanı döndürür.  
  
> [!NOTE]
>  <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> SQL Server 2000 sorguları içinde kullanıldığında belirli sınırlamaları vardır. "Atla ve SQL Server 2000'de özel durumlar'ı Al" girdisinde daha fazla bilgi için bkz. [sorun giderme](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çevirir <xref:System.Linq.Queryable.Skip%2A> SQL ile bir alt sorgu kullanarak `NOT EXISTS` yan tümcesi. Bu çeviri aşağıdaki sınırlamalara sahiptir:  
  
- Bağımsız değişken bir küme olmalıdır. Multisets, sipariş bile desteklenmez.  
  
- Oluşturulan sorgu, üzerinde temel sorgu için oluşturulan sorgu çok daha karmaşık <xref:System.Linq.Queryable.Skip%2A> uygulanır. Bu karmaşıklığı, performans veya hatta bir zaman aşımı neden olabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Take` ilk beş seçilecek `Employees` işe. Koleksiyonun varsayılan olarak sıralanır Not `HireDate`.  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Linq.Queryable.Skip%2A> en pahalı 10 tüm seçilecek `Products`.  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek birleştirir <xref:System.Linq.Queryable.Skip%2A> ve <xref:System.Linq.Queryable.Take%2A> ilk 50 kaydı atlayabilir ve ardından sonraki 10 döndürmek için yöntemleri.  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <xref:System.Linq.Queryable.Take%2A> ve <xref:System.Linq.Queryable.Skip%2A> işlemlerdir sıralı kümelerine göre yalnızca iyi tanımlanmış. Sırasız kümeleri veya multisets semantiği tanımsızdır.  
  
 SQL'de sıralama sınırlamaları nedeniyle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bağımsız değişkeni sıralama taşımaya <xref:System.Linq.Queryable.Take%2A> veya <xref:System.Linq.Queryable.Skip%2A> işlecinin sonucunu işleci.  
  
> [!NOTE]
>  Çeviri için farklı [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] ve [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)]. Kullanmayı planlıyorsanız <xref:System.Linq.Queryable.Skip%2A> ile bir sorgu tüm karmaşıklığı [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].  
  
 Aşağıdakileri göz önünde bulundurun [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgu [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]:  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL kodunda sonuna aşağıdaki şekilde sıralama taşır:  
  
```  
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],  
FROM [Customers] AS [t0]  
WHERE (NOT (EXISTS(  
    SELECT NULL AS [EMPTY]  
    FROM (  
        SELECT TOP 1 [t1].[CustomerID]  
        FROM [Customers] AS [t1]  
        WHERE [t1].[City] = @p0  
        ORDER BY [t1].[CustomerID]  
        ) AS [t2]  
    WHERE [t0].[CustomerID] = [t2].[CustomerID]  
    ))) AND ([t0].[City] = @p1)  
ORDER BY [t0].[CustomerID]  
```  
  
 Zaman <xref:System.Linq.Queryable.Take%2A> ve <xref:System.Linq.Queryable.Skip%2A> olan birbirine zincirlenmiş, tüm belirtilen sıralama tutarlı olması gerekir. Aksi takdirde, sonuçlar tanımsızdır.  
  
 Negatif olmayan için sabit tamsayı bağımsız değişkenleri temel SQL belirtimine her ikisi de <xref:System.Linq.Queryable.Take%2A> ve <xref:System.Linq.Queryable.Skip%2A> iyi tanımlanmış olması.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Standart Sorgu İşleci Çevirisi](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
