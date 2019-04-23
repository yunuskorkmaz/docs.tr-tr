---
title: Kimlik Önbelleğinden Nesne Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: 702d88f844f00b86e64404bd100fd6b3d34971c6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211237"
---
# <a name="retrieving-objects-from-the-identity-cache"></a>Kimlik Önbelleğinden Nesne Alma
Bu konu LINQ türleri tarafından yönetilen kimlik önbelleğinden nesne döndüren SQL sorgularını açıklar <xref:System.Data.Linq.DataContext>.  
  
 LINQ to SQL'de, yöntemler birini <xref:System.Data.Linq.DataContext> nesnelerini yönetir sorgular yürütülürken, nesne kimliklerini bir kimlik önbellekte oturum açarak olduğu. Bazı durumlarda, LINQ to SQL veritabanında bir sorgu çalıştırmadan önce kimlik önbelleğinden nesne alma dener.  
  
 Genel olarak, kimlik önbelleğinden nesne döndürmek bir LINQ to SQL sorgusunda sorgu birincil anahtara bir nesnenin temel alması gerekir ve tek bir nesne döndürmelidir. Özellikle, sorgu, aşağıda gösterilen genel formlar birinde olmalıdır.  
  
> [!NOTE]
>  Önceden derlenmiş sorgular kimlik önbelleğinden nesne döndürmez. Önceden derlenmiş sorgular hakkında daha fazla bilgi için bkz. <xref:System.Data.Linq.CompiledQuery> ve [nasıl yapılır: Store ve sorguları yeniden](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).  
  
 Bir sorgu kimlik önbelleğinden nesne almak için aşağıdaki genel biçimlerden birinde olmalıdır:  
  
-   <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`  
  
-   <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`  
  
 Bu genel Forms'ta `Function1`, `Function2`, ve `predicate` şu şekilde tanımlanır.  
  
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
  
 `predicate` nesnenin birincil anahtar özelliği bir sabit değer için ayarlanmış bir ifade olmalıdır. Bir nesnenin birden fazla özelliği tarafından tanımlanan bir birincil anahtar varsa, her bir birincil anahtar özelliği bir sabit değere ayarlamanız gerekir. Form örnekleri verilmiştir `predicate` gerçekleştirmeniz gerekir:  
  
-   `c => c.PK == constant_value`  
  
-   `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, kimlik önbelleğinden nesne alma SQL sorgularını LINQ türlerinin örnekleri sağlar.  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Nesne Kimliği](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Nesne Kimliği](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
