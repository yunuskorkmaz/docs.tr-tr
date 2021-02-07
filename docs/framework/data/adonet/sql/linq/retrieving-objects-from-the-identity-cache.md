---
description: 'Hakkında daha fazla bilgi edinin: kimlik önbelleğinden nesneleri alma'
title: Kimlik Önbelleğinden Nesne Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: 1f3d5f839a6fff33d62d4e0cb2281bd087f2d320
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695092"
---
# <a name="retrieving-objects-from-the-identity-cache"></a>Kimlik Önbelleğinden Nesne Alma

Bu konu, tarafından yönetilen kimlik önbelleğinden bir nesne döndüren LINQ to SQL sorgularının türlerini açıklar <xref:System.Data.Linq.DataContext> .  
  
 LINQ to SQL, nesneleri yönetme yöntemlerinden biri, <xref:System.Data.Linq.DataContext> sorgular yürütüldüğü zaman bir kimlik önbelleğindeki nesne kimliklerini günlüğe kaydetmeye göre yapılır. Bazı durumlarda LINQ to SQL veritabanında bir sorgu yürütmeden önce kimlik önbelleğinden bir nesne almaya çalışacaktır.  
  
 Genellikle, bir LINQ to SQL sorgusunun kimlik önbelleğinden bir nesne döndürmesi için, sorgunun bir nesnenin birincil anahtarını temel almalıdır ve tek bir nesne döndürmesi gerekir. Özellikle, sorgu aşağıda gösterilen genel formlardan birinde olmalıdır.  
  
> [!NOTE]
> Önceden derlenen sorgular, kimlik önbelleğinden nesne döndürmez. Önceden derlenen sorgular hakkında daha fazla bilgi için bkz <xref:System.Data.Linq.CompiledQuery> . ve [nasıl yapılır: sorguları depolama ve yeniden kullanma](how-to-store-and-reuse-queries.md).  
  
 Bir sorgu, kimlik önbelleğinden bir nesne almak için aşağıdaki genel formlardan birinde olmalıdır:  
  
- <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`  
  
- <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`  
  
 Bu genel formlarda,, `Function1` `Function2` ve `predicate` aşağıdaki gibi tanımlanmıştır.  
  
 `Function1` aşağıdakilerden herhangi biri olabilir:  
  
- <xref:System.Linq.Queryable.Where%2A>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `Function2` aşağıdakilerden herhangi biri olabilir:  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `predicate` nesnenin birincil anahtar özelliğinin sabit bir değere ayarlandığı bir ifade olmalıdır. Bir nesnenin birden fazla özellik tarafından tanımlanmış bir birincil anahtarı varsa, her birincil anahtar özelliği sabit bir değere ayarlanmalıdır. Aşağıda, form örnekleri `predicate` gelmelidir:  
  
- `c => c.PK == constant_value`  
  
- `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, kimlik önbelleğinden bir nesne alan LINQ to SQL sorgularının türlerine örnekler sağlar.  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](query-concepts.md)
- [Nesne Kimliği](object-identity.md)
- [Arka Plan Bilgileri](background-information.md)
- [Nesne Kimliği](object-identity.md)
