---
title: Kimlik Önbelleğinden Nesne Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: 702d88f844f00b86e64404bd100fd6b3d34971c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211237"
---
# <a name="retrieving-objects-from-the-identity-cache"></a><span data-ttu-id="58eed-102">Kimlik Önbelleğinden Nesne Alma</span><span class="sxs-lookup"><span data-stu-id="58eed-102">Retrieving Objects from the Identity Cache</span></span>
<span data-ttu-id="58eed-103">Bu konu LINQ türleri tarafından yönetilen kimlik önbelleğinden nesne döndüren SQL sorgularını açıklar <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="58eed-103">This topic describes the types of LINQ to SQL queries that return an object from the identity cache that is managed by the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="58eed-104">LINQ to SQL'de, yöntemler birini <xref:System.Data.Linq.DataContext> nesnelerini yönetir sorgular yürütülürken, nesne kimliklerini bir kimlik önbellekte oturum açarak olduğu.</span><span class="sxs-lookup"><span data-stu-id="58eed-104">In LINQ to SQL, one of the ways in which the <xref:System.Data.Linq.DataContext> manages objects is by logging object identities in an identity cache as queries are executed.</span></span> <span data-ttu-id="58eed-105">Bazı durumlarda, LINQ to SQL veritabanında bir sorgu çalıştırmadan önce kimlik önbelleğinden nesne alma dener.</span><span class="sxs-lookup"><span data-stu-id="58eed-105">In some cases, LINQ to SQL will attempt to retrieve an object from the identity cache before executing a query in the database.</span></span>  
  
 <span data-ttu-id="58eed-106">Genel olarak, kimlik önbelleğinden nesne döndürmek bir LINQ to SQL sorgusunda sorgu birincil anahtara bir nesnenin temel alması gerekir ve tek bir nesne döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="58eed-106">In general, for a LINQ to SQL query to return an object from the identity cache, the query must be based on the primary key of an object and must return a single object.</span></span> <span data-ttu-id="58eed-107">Özellikle, sorgu, aşağıda gösterilen genel formlar birinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="58eed-107">In particular, the query must be in one of the general forms shown below.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58eed-108">Önceden derlenmiş sorgular kimlik önbelleğinden nesne döndürmez.</span><span class="sxs-lookup"><span data-stu-id="58eed-108">Pre-compiled queries will not return objects from the identity cache.</span></span> <span data-ttu-id="58eed-109">Önceden derlenmiş sorgular hakkında daha fazla bilgi için bkz. <xref:System.Data.Linq.CompiledQuery> ve [nasıl yapılır: Store ve sorguları yeniden](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).</span><span class="sxs-lookup"><span data-stu-id="58eed-109">For more information about pre-compiled queries, see <xref:System.Data.Linq.CompiledQuery> and [How to: Store and Reuse Queries](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).</span></span>  
  
 <span data-ttu-id="58eed-110">Bir sorgu kimlik önbelleğinden nesne almak için aşağıdaki genel biçimlerden birinde olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="58eed-110">A query must be in one of the following general forms to retrieve an object from the identity cache:</span></span>  
  
-   <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`  
  
-   <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`  
  
 <span data-ttu-id="58eed-111">Bu genel Forms'ta `Function1`, `Function2`, ve `predicate` şu şekilde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="58eed-111">In these general forms, `Function1`, `Function2`, and `predicate` are defined as follows.</span></span>  
  
 `Function1` <span data-ttu-id="58eed-112">aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="58eed-112">can be any of the following:</span></span>  
  
-   <xref:System.Linq.Queryable.Where%2A>  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `Function2` <span data-ttu-id="58eed-113">aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="58eed-113">can be any of the following:</span></span>  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `predicate` <span data-ttu-id="58eed-114">nesnenin birincil anahtar özelliği bir sabit değer için ayarlanmış bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="58eed-114">must be an expression in which the object's primary key property is set to a constant value.</span></span> <span data-ttu-id="58eed-115">Bir nesnenin birden fazla özelliği tarafından tanımlanan bir birincil anahtar varsa, her bir birincil anahtar özelliği bir sabit değere ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="58eed-115">If an object has a primary key defined by more than one property, each primary key property must be set to a constant value.</span></span> <span data-ttu-id="58eed-116">Form örnekleri verilmiştir `predicate` gerçekleştirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="58eed-116">The following are examples of the form `predicate` must take:</span></span>  
  
-   `c => c.PK == constant_value`  
  
-   `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a><span data-ttu-id="58eed-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="58eed-117">Example</span></span>  
 <span data-ttu-id="58eed-118">Aşağıdaki kod, kimlik önbelleğinden nesne alma SQL sorgularını LINQ türlerinin örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="58eed-118">The following code provides examples of the types of LINQ to SQL queries that retrieve an object from the identity cache.</span></span>  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="58eed-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58eed-119">See also</span></span>

- [<span data-ttu-id="58eed-120">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="58eed-120">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="58eed-121">Nesne Kimliği</span><span class="sxs-lookup"><span data-stu-id="58eed-121">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
- [<span data-ttu-id="58eed-122">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="58eed-122">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="58eed-123">Nesne Kimliği</span><span class="sxs-lookup"><span data-stu-id="58eed-123">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
