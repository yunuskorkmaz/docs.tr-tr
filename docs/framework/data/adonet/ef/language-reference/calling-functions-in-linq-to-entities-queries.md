---
title: "LINQ to Entities sorgularında işlevleri çağırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6e50147d356ad9e389a87868205bb9b8b6b3e7b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="3b1e1-102">LINQ to Entities sorgularında işlevleri çağırma</span><span class="sxs-lookup"><span data-stu-id="3b1e1-102">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="3b1e1-103">Bu bölümdeki konular, LINQ to Entities sorgularında işlevlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="3b1e1-103">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="3b1e1-104"><xref:System.Data.Objects.EntityFunctions> Ve <xref:System.Data.Objects.SqlClient.SqlFunctions> sınıfları, Entity Framework'ün bir parçası olarak erişim kurallı ve veritabanı işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b1e1-104">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="3b1e1-105">Daha fazla bilgi için bkz [nasıl yapılır: çağrı kurallı işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) ve [nasıl yapılır: çağrı veritabanı işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span><span class="sxs-lookup"><span data-stu-id="3b1e1-105">For more information, see [How to: Call Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) and [How to: Call Database Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="3b1e1-106">Özel bir işlev çağırma işlemi üç temel adımlar gerektirir:</span><span class="sxs-lookup"><span data-stu-id="3b1e1-106">The process for calling a custom function requires three basic steps:</span></span>  
  
1.  <span data-ttu-id="3b1e1-107">Kavramsal modelde bir işlev tanımlayın veya depolama modelinizi işlevinde bildirin.</span><span class="sxs-lookup"><span data-stu-id="3b1e1-107">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2.  <span data-ttu-id="3b1e1-108">Uygulamanız için bir yöntem ekleyin ve modelle işlevinde Eşle bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3b1e1-108">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3.  <span data-ttu-id="3b1e1-109">Bir LINQ to Entities sorgusunda işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="3b1e1-109">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="3b1e1-110">Bu bölümdeki konular, daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="3b1e1-110">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3b1e1-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3b1e1-111">In This Section</span></span>  
 [<span data-ttu-id="3b1e1-112">Nasıl yapılır: çağrı kurallı işlevleri</span><span class="sxs-lookup"><span data-stu-id="3b1e1-112">How to: Call Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="3b1e1-113">Nasıl yapılır: çağrı veritabanı işlevleri</span><span class="sxs-lookup"><span data-stu-id="3b1e1-113">How to: Call Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [<span data-ttu-id="3b1e1-114">Nasıl yapılır: özel veritabanı işlevleri çağırma</span><span class="sxs-lookup"><span data-stu-id="3b1e1-114">How to: Call Custom Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="3b1e1-115">Nasıl yapılır: Model tarafından tanımlanan işlevler sorgularda çağırın</span><span class="sxs-lookup"><span data-stu-id="3b1e1-115">How to: Call Model-Defined Functions in Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="3b1e1-116">Nasıl yapılır: çağrı nesne yöntemleri olarak modeli tarafından tanımlanan İşlevler</span><span class="sxs-lookup"><span data-stu-id="3b1e1-116">How to: Call Model-Defined Functions as Object Methods</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="3b1e1-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3b1e1-117">See Also</span></span>  
 [<span data-ttu-id="3b1e1-118">LINQ to Entities sorguları</span><span class="sxs-lookup"><span data-stu-id="3b1e1-118">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [<span data-ttu-id="3b1e1-119">Kurallı işlevleri</span><span class="sxs-lookup"><span data-stu-id="3b1e1-119">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)  
 [<span data-ttu-id="3b1e1-120">.edmx dosyasının genel bakış</span><span class="sxs-lookup"><span data-stu-id="3b1e1-120">.edmx File Overview</span></span>](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="3b1e1-121">Nasıl yapılır: özel işlevler kavramsal modelde tanımlayın</span><span class="sxs-lookup"><span data-stu-id="3b1e1-121">How to: Define Custom Functions in the Conceptual Model</span></span>](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f)
