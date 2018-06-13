---
title: Dönüş veya bir dizi Atla öğeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: 228de9f3b92d45866c98976be08b84988a2db8d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359884"
---
# <a name="return-or-skip-elements-in-a-sequence"></a>Dönüş veya bir dizi Atla öğeleri
Kullanım <xref:System.Linq.Queryable.Take%2A> işleci bir dizisinde öğeleri, verilen sayıda dönün ve kalanını atlayın.  
  
 Kullanım <xref:System.Linq.Queryable.Skip%2A> dizisindeki öğelerin verilen bir sayının atlamayı ve geri kalan dönmek için işleci.  
  
> [!NOTE]
>  <xref:System.Linq.Enumerable.Take%2A> ve <xref:System.Linq.Enumerable.Skip%2A> SQL Server 2000 karşı sorgularda kullanıldığında belirli sınırlamaları vardır. Daha fazla bilgi için "Atlayın ve SQL Server 2000'de özel durumlar alın" girdisinde bkz [sorun giderme](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çevirir <xref:System.Linq.Queryable.Skip%2A> SQL ile bir alt sorgu kullanarak `NOT EXISTS` yan tümcesi. Bu çeviri aşağıdaki sınırlamalara sahiptir:  
  
-   Bağımsız değişkeni bir küme olmalıdır. Multisets, sipariş olsa bile desteklenmez.  
  
-   Oluşturulan sorgu üretileceği temel sorgu için oluşturulan sorgu çok daha karmaşık olabilir <xref:System.Linq.Queryable.Skip%2A> uygulanır. Bu karmaşıklık performans düşüklüğü veya hatta bir zaman aşımı neden olabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Take` ilk beş seçmek için `Employees` işe. Koleksiyon önce tarafından sıralanan Not `HireDate`.  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır <xref:System.Linq.Queryable.Skip%2A> en pahalı 10 dışında tüm seçmek için `Products`.  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek birleştirir <xref:System.Linq.Queryable.Skip%2A> ve <xref:System.Linq.Queryable.Take%2A> ilk 50 kaydı atlayın ve sonraki 10 dönmek için yöntemleri.  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <xref:System.Linq.Queryable.Take%2A> ve <xref:System.Linq.Queryable.Skip%2A> işlemleri yalnızca sıralı kümelerine göre iyi tanımlanmış. Sırasız kümeleri veya multisets anlamları tanımlanmamıştır.  
  
 SQL'de sıralama sınırlamalar nedeniyle [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bağımsız değişkeni sıralama taşımayı dener <xref:System.Linq.Queryable.Take%2A> veya <xref:System.Linq.Queryable.Skip%2A> işlecinin sonucu işleci.  
  
> [!NOTE]
>  Çeviri için farklı [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] ve [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)]. Kullanmayı planlıyorsanız, <xref:System.Linq.Queryable.Skip%2A> herhangi karmaşıklık query ile birlikte kullanma [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].  
  
 Aşağıdakileri göz önünde bulundurun [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] için sorgu [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]:  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL kodda sonuna şu şekilde sıralama taşır:  
  
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
  
 Zaman <xref:System.Linq.Queryable.Take%2A> ve <xref:System.Linq.Queryable.Skip%2A> olan birbirine zincirlenmiş, tüm belirtilen sıralama tutarlı olmalıdır. Aksi takdirde, sonuçları tanımlanmamış.  
  
 Negatif olmayan için tam sayı sabit bağımsız değişkenler tabanlı SQL belirtimi her ikisi de <xref:System.Linq.Queryable.Take%2A> ve <xref:System.Linq.Queryable.Skip%2A> iyi tanımlanmış olması.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu Örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Standart Sorgu İşleci Çevirisi](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
