---
title: Dizideki Öğeleri Döndürme veya Atlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: 1a36d3c8457374183148599bf8160d14847cbf3e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200426"
---
# <a name="return-or-skip-elements-in-a-sequence"></a>Dizideki Öğeleri Döndürme veya Atlama

İşleci kullanarak <xref:System.Linq.Queryable.Take%2A> bir dizide verilen sayıda öğeyi döndürün ve sonra kalanı atlayın.  
  
 <xref:System.Linq.Queryable.Skip%2A>Bir dizide verilen sayıda öğeyi atlamak için işlecini kullanın ve ardından kalanı geri döndürün.  
  
> [!NOTE]
> <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> SQL Server 2000 ' de sorgularda kullanıldıkları bazı sınırlamalar vardır. Daha fazla bilgi için bkz. [sorun giderme](troubleshooting.md)içindeki "SQL Server 2000 'de özel durumları atla ve al" girişi.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Linq.Queryable.Skip%2A>SQL yan tümcesiyle bir alt sorgu kullanarak çevirir `NOT EXISTS` . Bu çeviri aşağıdaki sınırlamalara sahiptir:  
  
- Bağımsız değişken bir küme olmalıdır. Sıralı olsa bile çoklu kümeler desteklenmez.  
  
- Oluşturulan sorgu, üzerinde uygulanan temel sorgu için oluşturulan sorgudan çok daha karmaşık olabilir <xref:System.Linq.Queryable.Skip%2A> . Bu karmaşıklık, performans düşüşüyle ve hatta zaman aşımına neden olabilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `Take` işe alınan ilk beş ' u seçmek için kullanır `Employees` . Koleksiyonun öncelikle tarafından sıralandığı unutulmamalıdır `HireDate` .  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Linq.Queryable.Skip%2A> en pahalı 10 dışında tümünü seçmek için kullanır `Products` .  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Linq.Queryable.Skip%2A> ve <xref:System.Linq.Queryable.Take%2A> yöntemlerini ilk 50 kaydı atlamak için birleştirir ve sonra sonraki 10 ' u döndürür.  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <xref:System.Linq.Queryable.Take%2A> ve <xref:System.Linq.Queryable.Skip%2A> işlemler yalnızca sıralı kümelere karşı iyi tanımlanmış. Sıralanmamış kümeler veya birden çok küme semantiği tanımsızdır.  
  
 SQL 'de sıralama sınırlamaları nedeniyle, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veya işlecinin bağımsız değişkeninin sıralamasını <xref:System.Linq.Queryable.Take%2A> <xref:System.Linq.Queryable.Skip%2A> işlecin sonucuna taşımaya çalışır.  
  
> [!NOTE]
> Çeviri SQL Server 2000 ve SQL Server 2005 için farklıdır. <xref:System.Linq.Queryable.Skip%2A>Herhangi bir karmaşıklık sorgusu ile kullanmayı planlıyorsanız SQL Server 2005 kullanın.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]SQL Server 2000 için aşağıdaki sorguyu göz önünde bulundurun:  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sıralamayı SQL kodundaki sonuna aşağıdaki gibi gider:  
  
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
  
 <xref:System.Linq.Queryable.Take%2A>Ve <xref:System.Linq.Queryable.Skip%2A> birlikte zincirlendiği zaman, belirtilen tüm sıralama tutarlı olmalıdır. Aksi takdirde, sonuçlar tanımsızdır.  
  
 SQL belirtimine dayalı negatif olmayan, sabit integral bağımsız değişkenleri için her ikisi de <xref:System.Linq.Queryable.Take%2A> <xref:System.Linq.Queryable.Skip%2A> iyi tanımlanmıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu örnekleri](query-examples.md)
- [Standart Sorgu İşleci Çevirisi](standard-query-operator-translation.md)
