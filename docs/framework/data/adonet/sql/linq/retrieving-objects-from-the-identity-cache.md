---
title: Kimlik Önbelleğinden Nesne Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: 457e11ddad16ca3be55f53f03c480b0e464ab38f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200400"
---
# <a name="retrieving-objects-from-the-identity-cache"></a><span data-ttu-id="cf188-102">Kimlik Önbelleğinden Nesne Alma</span><span class="sxs-lookup"><span data-stu-id="cf188-102">Retrieving Objects from the Identity Cache</span></span>

<span data-ttu-id="cf188-103">Bu konu, tarafından yönetilen kimlik önbelleğinden bir nesne döndüren LINQ to SQL sorgularının türlerini açıklar <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="cf188-103">This topic describes the types of LINQ to SQL queries that return an object from the identity cache that is managed by the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="cf188-104">LINQ to SQL, nesneleri yönetme yöntemlerinden biri, <xref:System.Data.Linq.DataContext> sorgular yürütüldüğü zaman bir kimlik önbelleğindeki nesne kimliklerini günlüğe kaydetmeye göre yapılır.</span><span class="sxs-lookup"><span data-stu-id="cf188-104">In LINQ to SQL, one of the ways in which the <xref:System.Data.Linq.DataContext> manages objects is by logging object identities in an identity cache as queries are executed.</span></span> <span data-ttu-id="cf188-105">Bazı durumlarda LINQ to SQL veritabanında bir sorgu yürütmeden önce kimlik önbelleğinden bir nesne almaya çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="cf188-105">In some cases, LINQ to SQL will attempt to retrieve an object from the identity cache before executing a query in the database.</span></span>  
  
 <span data-ttu-id="cf188-106">Genellikle, bir LINQ to SQL sorgusunun kimlik önbelleğinden bir nesne döndürmesi için, sorgunun bir nesnenin birincil anahtarını temel almalıdır ve tek bir nesne döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf188-106">In general, for a LINQ to SQL query to return an object from the identity cache, the query must be based on the primary key of an object and must return a single object.</span></span> <span data-ttu-id="cf188-107">Özellikle, sorgu aşağıda gösterilen genel formlardan birinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf188-107">In particular, the query must be in one of the general forms shown below.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf188-108">Önceden derlenen sorgular, kimlik önbelleğinden nesne döndürmez.</span><span class="sxs-lookup"><span data-stu-id="cf188-108">Pre-compiled queries will not return objects from the identity cache.</span></span> <span data-ttu-id="cf188-109">Önceden derlenen sorgular hakkında daha fazla bilgi için bkz <xref:System.Data.Linq.CompiledQuery> . ve [nasıl yapılır: sorguları depolama ve yeniden kullanma](how-to-store-and-reuse-queries.md).</span><span class="sxs-lookup"><span data-stu-id="cf188-109">For more information about pre-compiled queries, see <xref:System.Data.Linq.CompiledQuery> and [How to: Store and Reuse Queries](how-to-store-and-reuse-queries.md).</span></span>  
  
 <span data-ttu-id="cf188-110">Bir sorgu, kimlik önbelleğinden bir nesne almak için aşağıdaki genel formlardan birinde olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="cf188-110">A query must be in one of the following general forms to retrieve an object from the identity cache:</span></span>  
  
- <span data-ttu-id="cf188-111"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span><span class="sxs-lookup"><span data-stu-id="cf188-111"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span></span>  
  
- <span data-ttu-id="cf188-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span><span class="sxs-lookup"><span data-stu-id="cf188-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span></span>  
  
 <span data-ttu-id="cf188-113">Bu genel formlarda,, `Function1` `Function2` ve `predicate` aşağıdaki gibi tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cf188-113">In these general forms, `Function1`, `Function2`, and `predicate` are defined as follows.</span></span>  
  
 <span data-ttu-id="cf188-114">`Function1` aşağıdakilerden herhangi biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="cf188-114">`Function1` can be any of the following:</span></span>  
  
- <xref:System.Linq.Queryable.Where%2A>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="cf188-115">`Function2` aşağıdakilerden herhangi biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="cf188-115">`Function2` can be any of the following:</span></span>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="cf188-116">`predicate` nesnenin birincil anahtar özelliğinin sabit bir değere ayarlandığı bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf188-116">`predicate` must be an expression in which the object's primary key property is set to a constant value.</span></span> <span data-ttu-id="cf188-117">Bir nesnenin birden fazla özellik tarafından tanımlanmış bir birincil anahtarı varsa, her birincil anahtar özelliği sabit bir değere ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf188-117">If an object has a primary key defined by more than one property, each primary key property must be set to a constant value.</span></span> <span data-ttu-id="cf188-118">Aşağıda, form örnekleri `predicate` gelmelidir:</span><span class="sxs-lookup"><span data-stu-id="cf188-118">The following are examples of the form `predicate` must take:</span></span>  
  
- `c => c.PK == constant_value`  
  
- `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a><span data-ttu-id="cf188-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf188-119">Example</span></span>  

 <span data-ttu-id="cf188-120">Aşağıdaki kod, kimlik önbelleğinden bir nesne alan LINQ to SQL sorgularının türlerine örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf188-120">The following code provides examples of the types of LINQ to SQL queries that retrieve an object from the identity cache.</span></span>  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cf188-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf188-121">See also</span></span>

- [<span data-ttu-id="cf188-122">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="cf188-122">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="cf188-123">Nesne Kimliği</span><span class="sxs-lookup"><span data-stu-id="cf188-123">Object Identity</span></span>](object-identity.md)
- [<span data-ttu-id="cf188-124">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="cf188-124">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="cf188-125">Nesne Kimliği</span><span class="sxs-lookup"><span data-stu-id="cf188-125">Object Identity</span></span>](object-identity.md)
