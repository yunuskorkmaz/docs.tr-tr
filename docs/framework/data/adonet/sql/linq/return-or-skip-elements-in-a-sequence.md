---
title: Dizideki Öğeleri Döndürme veya Atlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: a5c32afc913443787ad8371f31f1fe330b126398
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792760"
---
# <a name="return-or-skip-elements-in-a-sequence"></a>Dizideki Öğeleri Döndürme veya Atlama
<xref:System.Linq.Queryable.Take%2A> İşleci kullanarak bir dizide verilen sayıda öğeyi döndürün ve sonra kalanı atlayın.  
  
 Bir dizide verilen sayıda öğeyi atlamak için işlecinikullanınveardındankalanıgeridöndürün.<xref:System.Linq.Queryable.Skip%2A>  
  
> [!NOTE]
> <xref:System.Linq.Enumerable.Take%2A>ve <xref:System.Linq.Enumerable.Skip%2A> SQL Server 2000 ' de sorgularda kullanıldıkları bazı sınırlamalar vardır. Daha fazla bilgi için bkz. [sorun giderme](troubleshooting.md)içindeki "SQL Server 2000 'de özel durumları atla ve al" girişi.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Linq.Queryable.Skip%2A> SQL`NOT EXISTS` yan tümcesiyle bir alt sorgu kullanarak çevirir. Bu çeviri aşağıdaki sınırlamalara sahiptir:  
  
- Bağımsız değişken bir küme olmalıdır. Sıralı olsa bile çoklu kümeler desteklenmez.  
  
- Oluşturulan sorgu, üzerinde <xref:System.Linq.Queryable.Skip%2A> uygulanan temel sorgu için oluşturulan sorgudan çok daha karmaşık olabilir. Bu karmaşıklık, performans düşüşüyle ve hatta zaman aşımına neden olabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, işe `Take` alınan ilk beş `Employees` ' u seçmek için kullanır. Koleksiyonun öncelikle tarafından `HireDate`sıralandığı unutulmamalıdır.  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, en <xref:System.Linq.Queryable.Skip%2A> pahalı `Products`10 dışında tümünü seçmek için kullanır.  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Linq.Queryable.Skip%2A> ve <xref:System.Linq.Queryable.Take%2A> yöntemlerini ilk 50 kaydı atlamak için birleştirir ve sonra sonraki 10 ' u döndürür.  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <xref:System.Linq.Queryable.Take%2A>ve <xref:System.Linq.Queryable.Skip%2A> işlemler yalnızca sıralı kümelere karşı iyi tanımlanmış. Sıralanmamış kümeler veya birden çok küme semantiği tanımsızdır.  
  
 SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 'de sıralama sınırlamaları nedeniyle, <xref:System.Linq.Queryable.Take%2A> veya <xref:System.Linq.Queryable.Skip%2A> işlecinin bağımsız değişkeninin sıralamasını işlecin sonucuna taşımaya çalışır.  
  
> [!NOTE]
> Çeviri SQL Server 2000 ve SQL Server 2005 için farklıdır. Herhangi bir karmaşıklık sorgusu ile <xref:System.Linq.Queryable.Skip%2A> kullanmayı planlıyorsanız SQL Server 2005 kullanın.  
  
 SQL Server 2000 için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aşağıdaki sorguyu göz önünde bulundurun:  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]sıralamayı SQL kodundaki sonuna aşağıdaki gibi gider:  
  
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
  
 <xref:System.Linq.Queryable.Take%2A> Ve<xref:System.Linq.Queryable.Skip%2A> birlikte zincirlendiği zaman, belirtilen tüm sıralama tutarlı olmalıdır. Aksi takdirde, sonuçlar tanımsızdır.  
  
 SQL belirtimine dayalı negatif olmayan, sabit integral bağımsız değişkenleri için her ikisi <xref:System.Linq.Queryable.Take%2A> <xref:System.Linq.Queryable.Skip%2A> de iyi tanımlanmıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Örnekleri](query-examples.md)
- [Standart Sorgu İşleci Çevirisi](standard-query-operator-translation.md)
