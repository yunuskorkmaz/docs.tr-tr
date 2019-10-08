---
title: Dizideki Öğeleri Döndürme veya Atlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: 7c98681493738b4e94ed14417fa1437efb6c12ac
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003314"
---
# <a name="return-or-skip-elements-in-a-sequence"></a>Dizideki Öğeleri Döndürme veya Atlama
Bir dizide verilen sayıda öğe döndürmek için <xref:System.Linq.Queryable.Take%2A> işlecini kullanın ve ardından kalanı atlayın.  
  
 Bir dizide verilen sayıda öğeyi atlamak için <xref:System.Linq.Queryable.Skip%2A> işlecini kullanın ve ardından kalanı geri döndürün.  
  
> [!NOTE]
> <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> SQL Server 2000 ' de sorgularda kullanıldıkları zaman belirli sınırlamalara sahiptir. Daha fazla bilgi için bkz. [sorun giderme](troubleshooting.md)içindeki "SQL Server 2000 'de özel durumları atla ve al" girişi.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], SQL `NOT EXISTS` yan tümcesiyle bir alt sorgu kullanarak <xref:System.Linq.Queryable.Skip%2A> çevirir. Bu çeviri aşağıdaki sınırlamalara sahiptir:  
  
- Bağımsız değişken bir küme olmalıdır. Sıralı olsa bile çoklu kümeler desteklenmez.  
  
- Oluşturulan sorgu <xref:System.Linq.Queryable.Skip%2A> ' ın uygulandığı temel sorgu için oluşturulan sorgudan çok daha karmaşık olabilir. Bu karmaşıklık, performans düşüşüyle ve hatta zaman aşımına neden olabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek ilk beş `Employees` ' i seçmek için `Take` kullanır. Koleksiyonun öncelikle `HireDate` ile sıralanacağını unutmayın.  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, en pahalı 10 `Products` dışında tümünü seçmek için <xref:System.Linq.Queryable.Skip%2A> kullanır.  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ilk 50 kayıtları atlamak için <xref:System.Linq.Queryable.Skip%2A> ve <xref:System.Linq.Queryable.Take%2A> yöntemlerini birleştirir ve ardından sonraki 10 ' u döndürür.  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <xref:System.Linq.Queryable.Take%2A> ve <xref:System.Linq.Queryable.Skip%2A> işlemleri yalnızca sıralı kümelere karşı iyi tanımlanmış. Sıralanmamış kümeler veya birden çok küme semantiği tanımsızdır.  
  
 SQL 'de sıralama sınırlamaları nedeniyle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Linq.Queryable.Take%2A> veya <xref:System.Linq.Queryable.Skip%2A> işlecinin bağımsız değişkeninin sıralamasını işlecin sonucuna taşımaya çalışır.  
  
> [!NOTE]
> Çeviri SQL Server 2000 ve SQL Server 2005 için farklıdır. @No__t-0 ' ı herhangi bir karmaşıklık sorgusu ile kullanmayı planlıyorsanız, SQL Server 2005 ' i kullanın.  
  
 SQL Server 2000 için aşağıdaki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgusunu göz önünde bulundurun:  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], sıralamayı SQL kodundaki sonuna aşağıdaki gibi taşıdır:  
  
```sql
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
  
 @No__t-0 ve <xref:System.Linq.Queryable.Skip%2A> birlikte zincirlendiği zaman, belirtilen tüm sıralama tutarlı olmalıdır. Aksi takdirde, sonuçlar tanımsızdır.  
  
 SQL belirtimine dayalı negatif olmayan, sabit tamsayı bağımsız değişkenleri için hem <xref:System.Linq.Queryable.Take%2A> hem de <xref:System.Linq.Queryable.Skip%2A> iyi tanımlanmıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Örnekleri](query-examples.md)
- [Standart Sorgu İşleci Çevirisi](standard-query-operator-translation.md)
