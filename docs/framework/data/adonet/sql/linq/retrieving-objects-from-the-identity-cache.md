---
title: Kimlik Önbelleğinden Nesne Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: ef771d924d9b508c29061f75a45808b5f81abb53
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963831"
---
# <a name="retrieving-objects-from-the-identity-cache"></a><span data-ttu-id="0bb80-102">Kimlik Önbelleğinden Nesne Alma</span><span class="sxs-lookup"><span data-stu-id="0bb80-102">Retrieving Objects from the Identity Cache</span></span>
<span data-ttu-id="0bb80-103">Bu konu, <xref:System.Data.Linq.DataContext>tarafından yönetilen kimlik önbelleğinden bir nesne döndüren LINQ to SQL sorgularının türlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="0bb80-103">This topic describes the types of LINQ to SQL queries that return an object from the identity cache that is managed by the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="0bb80-104">LINQ to SQL, nesneleri <xref:System.Data.Linq.DataContext> yönetme yöntemlerinden biri, sorgular yürütüldüğü zaman bir kimlik önbelleğindeki nesne kimliklerini günlüğe kaydetmeye göre yapılır.</span><span class="sxs-lookup"><span data-stu-id="0bb80-104">In LINQ to SQL, one of the ways in which the <xref:System.Data.Linq.DataContext> manages objects is by logging object identities in an identity cache as queries are executed.</span></span> <span data-ttu-id="0bb80-105">Bazı durumlarda LINQ to SQL veritabanında bir sorgu yürütmeden önce kimlik önbelleğinden bir nesne almaya çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="0bb80-105">In some cases, LINQ to SQL will attempt to retrieve an object from the identity cache before executing a query in the database.</span></span>  
  
 <span data-ttu-id="0bb80-106">Genellikle, bir LINQ to SQL sorgusunun kimlik önbelleğinden bir nesne döndürmesi için, sorgunun bir nesnenin birincil anahtarını temel almalıdır ve tek bir nesne döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0bb80-106">In general, for a LINQ to SQL query to return an object from the identity cache, the query must be based on the primary key of an object and must return a single object.</span></span> <span data-ttu-id="0bb80-107">Özellikle, sorgu aşağıda gösterilen genel formlardan birinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0bb80-107">In particular, the query must be in one of the general forms shown below.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0bb80-108">Önceden derlenen sorgular, kimlik önbelleğinden nesne döndürmez.</span><span class="sxs-lookup"><span data-stu-id="0bb80-108">Pre-compiled queries will not return objects from the identity cache.</span></span> <span data-ttu-id="0bb80-109">Önceden derlenen sorgular hakkında daha fazla bilgi için bkz <xref:System.Data.Linq.CompiledQuery> . ve [nasıl yapılır: Sorguları](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md)depolayın ve yeniden kullanın.</span><span class="sxs-lookup"><span data-stu-id="0bb80-109">For more information about pre-compiled queries, see <xref:System.Data.Linq.CompiledQuery> and [How to: Store and Reuse Queries](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).</span></span>  
  
 <span data-ttu-id="0bb80-110">Bir sorgu, kimlik önbelleğinden bir nesne almak için aşağıdaki genel formlardan birinde olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="0bb80-110">A query must be in one of the following general forms to retrieve an object from the identity cache:</span></span>  
  
- <span data-ttu-id="0bb80-111"><xref:System.Data.Linq.Table%601>`.Function1(` `predicate``)`</span><span class="sxs-lookup"><span data-stu-id="0bb80-111"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span></span>  
  
- <span data-ttu-id="0bb80-112"><xref:System.Data.Linq.Table%601>`.Function1(` `predicate``).Function2()`</span><span class="sxs-lookup"><span data-stu-id="0bb80-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span></span>  
  
 <span data-ttu-id="0bb80-113">Bu genel formlarda `Function1` `Function2`,, ve `predicate` aşağıdaki gibi tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0bb80-113">In these general forms, `Function1`, `Function2`, and `predicate` are defined as follows.</span></span>  
  
 <span data-ttu-id="0bb80-114">`Function1`aşağıdakilerden herhangi biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="0bb80-114">`Function1` can be any of the following:</span></span>  
  
- <xref:System.Linq.Queryable.Where%2A>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="0bb80-115">`Function2`aşağıdakilerden herhangi biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="0bb80-115">`Function2` can be any of the following:</span></span>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="0bb80-116">`predicate`nesnenin birincil anahtar özelliğinin sabit bir değere ayarlandığı bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0bb80-116">`predicate` must be an expression in which the object's primary key property is set to a constant value.</span></span> <span data-ttu-id="0bb80-117">Bir nesnenin birden fazla özellik tarafından tanımlanmış bir birincil anahtarı varsa, her birincil anahtar özelliği sabit bir değere ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0bb80-117">If an object has a primary key defined by more than one property, each primary key property must be set to a constant value.</span></span> <span data-ttu-id="0bb80-118">Aşağıda, form `predicate` örnekleri gelmelidir:</span><span class="sxs-lookup"><span data-stu-id="0bb80-118">The following are examples of the form `predicate` must take:</span></span>  
  
- `c => c.PK == constant_value`  
  
- `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a><span data-ttu-id="0bb80-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="0bb80-119">Example</span></span>  
 <span data-ttu-id="0bb80-120">Aşağıdaki kod, kimlik önbelleğinden bir nesne alan LINQ to SQL sorgularının türlerine örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0bb80-120">The following code provides examples of the types of LINQ to SQL queries that retrieve an object from the identity cache.</span></span>  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0bb80-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bb80-121">See also</span></span>

- [<span data-ttu-id="0bb80-122">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="0bb80-122">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="0bb80-123">Nesne Kimliği</span><span class="sxs-lookup"><span data-stu-id="0bb80-123">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
- [<span data-ttu-id="0bb80-124">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="0bb80-124">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="0bb80-125">Nesne Kimliği</span><span class="sxs-lookup"><span data-stu-id="0bb80-125">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
