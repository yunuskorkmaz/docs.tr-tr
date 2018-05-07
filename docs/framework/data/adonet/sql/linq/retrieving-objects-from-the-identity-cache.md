---
title: Kimlik önbellekten nesneleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: fe22dbdff0e5e9ea6bfe55fc24c492414e01cd6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="retrieving-objects-from-the-identity-cache"></a>Kimlik önbellekten nesneleri
LINQ türleri tarafından yönetilen bir nesne kimliği önbellekten döndüren SQL sorguları için bu konuda açıklanmaktadır <xref:System.Data.Linq.DataContext>.  
  
 LINQ-SQL, hangi yollarla birini <xref:System.Data.Linq.DataContext> nesneleri yönetir sorguları gerçekleştirilirken nesne kimliklerinin bir kimlik önbelleğinde günlüğe kaydetme tarafından. Bazı durumlarda, LINQ to SQL nesne kimliği veritabanında bir sorgu çalıştırmadan önce önbellekten dener.  
  
 Genel olarak, bir nesne kimliği önbellekten döndürmek bir LINQ to SQL sorgusunda sorgu nesnenin birincil anahtarı temel gerekir ve tek bir nesne döndürmesi gerekir. Özellikle, sorgu, aşağıda gösterilen genel formlar birinde olmalıdır.  
  
> [!NOTE]
>  Önceden derlenmiş sorgular nesneleri kimlik önbellekten döndürmez. Önceden derlenmiş sorguları hakkında daha fazla bilgi için bkz: <xref:System.Data.Linq.CompiledQuery> ve [nasıl yapılır: depola ve yeniden sorgular](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).  
  
 Bir sorgu, bir nesne kimliği önbelleğinden almak için aşağıdaki genel formlar birinde olmalıdır:  
  
-   <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`  
  
-   <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`  
  
 Bu genel formlardaki `Function1`, `Function2`, ve `predicate` şu şekilde tanımlanır.  
  
 `Function1` aşağıdakilerden biri olabilir:  
  
-   <xref:System.Linq.Queryable.Where%2A>  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `Function2` aşağıdakilerden biri olabilir:  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `predicate` nesnenin birincil anahtar özelliği bir sabit değer için ayarlanmış bir ifade olmalıdır. Bir nesnenin birden fazla özelliği tarafından tanımlanan bir birincil anahtar varsa, her birincil anahtar özelliği bir sabit değere ayarlamanız gerekir. Form örnekleri aşağıda verilmiştir `predicate` gerçekleştirmeniz gerekir:  
  
-   `c => c.PK == constant_value`  
  
-   `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir nesne kimliği önbellekten SQL sorgularını LINQ türlerinin örnekleri sağlar.  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Nesne Kimliği](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)  
 [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Nesne Kimliği](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
