---
title: "Kimlik önbellekten nesneleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d078476e881c3823d7772a9db4cdbdb23dac8bb4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-objects-from-the-identity-cache"></a><span data-ttu-id="1cac9-102">Kimlik önbellekten nesneleri</span><span class="sxs-lookup"><span data-stu-id="1cac9-102">Retrieving Objects from the Identity Cache</span></span>
<span data-ttu-id="1cac9-103">LINQ türleri tarafından yönetilen bir nesne kimliği önbellekten döndüren SQL sorguları için bu konuda açıklanmaktadır <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="1cac9-103">This topic describes the types of LINQ to SQL queries that return an object from the identity cache that is managed by the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="1cac9-104">LINQ-SQL, hangi yollarla birini <xref:System.Data.Linq.DataContext> nesneleri yönetir sorguları gerçekleştirilirken nesne kimliklerinin bir kimlik önbelleğinde günlüğe kaydetme tarafından.</span><span class="sxs-lookup"><span data-stu-id="1cac9-104">In LINQ to SQL, one of the ways in which the <xref:System.Data.Linq.DataContext> manages objects is by logging object identities in an identity cache as queries are executed.</span></span> <span data-ttu-id="1cac9-105">Bazı durumlarda, LINQ to SQL nesne kimliği veritabanında bir sorgu çalıştırmadan önce önbellekten dener.</span><span class="sxs-lookup"><span data-stu-id="1cac9-105">In some cases, LINQ to SQL will attempt to retrieve an object from the identity cache before executing a query in the database.</span></span>  
  
 <span data-ttu-id="1cac9-106">Genel olarak, bir nesne kimliği önbellekten döndürmek bir LINQ to SQL sorgusunda sorgu nesnenin birincil anahtarı temel gerekir ve tek bir nesne döndürmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1cac9-106">In general, for a LINQ to SQL query to return an object from the identity cache, the query must be based on the primary key of an object and must return a single object.</span></span> <span data-ttu-id="1cac9-107">Özellikle, sorgu, aşağıda gösterilen genel formlar birinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1cac9-107">In particular, the query must be in one of the general forms shown below.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1cac9-108">Önceden derlenmiş sorgular nesneleri kimlik önbellekten döndürmez.</span><span class="sxs-lookup"><span data-stu-id="1cac9-108">Pre-compiled queries will not return objects from the identity cache.</span></span> <span data-ttu-id="1cac9-109">Önceden derlenmiş sorguları hakkında daha fazla bilgi için bkz: <xref:System.Data.Linq.CompiledQuery> ve [nasıl yapılır: depola ve yeniden sorgular](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).</span><span class="sxs-lookup"><span data-stu-id="1cac9-109">For more information about pre-compiled queries, see <xref:System.Data.Linq.CompiledQuery> and [How to: Store and Reuse Queries](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md).</span></span>  
  
 <span data-ttu-id="1cac9-110">Bir sorgu, bir nesne kimliği önbelleğinden almak için aşağıdaki genel formlar birinde olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="1cac9-110">A query must be in one of the following general forms to retrieve an object from the identity cache:</span></span>  
  
-   <span data-ttu-id="1cac9-111"><xref:System.Data.Linq.Table%601>`.Function1(``predicate``)`</span><span class="sxs-lookup"><span data-stu-id="1cac9-111"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span></span>  
  
-   <span data-ttu-id="1cac9-112"><xref:System.Data.Linq.Table%601>`.Function1(``predicate``).Function2()`</span><span class="sxs-lookup"><span data-stu-id="1cac9-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span></span>  
  
 <span data-ttu-id="1cac9-113">Bu genel formlardaki `Function1`, `Function2`, ve `predicate` şu şekilde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="1cac9-113">In these general forms, `Function1`, `Function2`, and `predicate` are defined as follows.</span></span>  
  
 <span data-ttu-id="1cac9-114">`Function1`aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="1cac9-114">`Function1` can be any of the following:</span></span>  
  
-   <xref:System.Linq.Queryable.Where%2A>  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="1cac9-115">`Function2`aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="1cac9-115">`Function2` can be any of the following:</span></span>  
  
-   <xref:System.Linq.Queryable.First%2A>  
  
-   <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
-   <xref:System.Linq.Queryable.Single%2A>  
  
-   <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="1cac9-116">`predicate`nesnenin birincil anahtar özelliği bir sabit değer için ayarlanmış bir ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1cac9-116">`predicate` must be an expression in which the object's primary key property is set to a constant value.</span></span> <span data-ttu-id="1cac9-117">Bir nesnenin birden fazla özelliği tarafından tanımlanan bir birincil anahtar varsa, her birincil anahtar özelliği bir sabit değere ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1cac9-117">If an object has a primary key defined by more than one property, each primary key property must be set to a constant value.</span></span> <span data-ttu-id="1cac9-118">Form örnekleri aşağıda verilmiştir `predicate` gerçekleştirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="1cac9-118">The following are examples of the form `predicate` must take:</span></span>  
  
-   `c => c.PK == constant_value`  
  
-   `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a><span data-ttu-id="1cac9-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="1cac9-119">Example</span></span>  
 <span data-ttu-id="1cac9-120">Aşağıdaki kod, bir nesne kimliği önbellekten SQL sorgularını LINQ türlerinin örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1cac9-120">The following code provides examples of the types of LINQ to SQL queries that retrieve an object from the identity cache.</span></span>  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1cac9-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1cac9-121">See Also</span></span>  
 [<span data-ttu-id="1cac9-122">Sorgu kavramları</span><span class="sxs-lookup"><span data-stu-id="1cac9-122">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="1cac9-123">Nesne Kimliği</span><span class="sxs-lookup"><span data-stu-id="1cac9-123">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)  
 [<span data-ttu-id="1cac9-124">Arka plan bilgileri</span><span class="sxs-lookup"><span data-stu-id="1cac9-124">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="1cac9-125">Nesne Kimliği</span><span class="sxs-lookup"><span data-stu-id="1cac9-125">Object Identity</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
