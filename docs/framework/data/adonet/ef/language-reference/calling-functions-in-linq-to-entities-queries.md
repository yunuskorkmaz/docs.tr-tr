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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d7199c41f8bcf81340956b17f616bec76e534dcc
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="2129a-102">LINQ to Entities sorgularında işlevleri çağırma</span><span class="sxs-lookup"><span data-stu-id="2129a-102">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="2129a-103">Bu bölümdeki konular, LINQ to Entities sorgularında işlevlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="2129a-103">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="2129a-104"><xref:System.Data.Objects.EntityFunctions> Ve <xref:System.Data.Objects.SqlClient.SqlFunctions> sınıfları, Entity Framework'ün bir parçası olarak erişim kurallı ve veritabanı işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2129a-104">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="2129a-105">Daha fazla bilgi için bkz [nasıl yapılır: çağrı kurallı işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) ve [nasıl yapılır: çağrı veritabanı işlevleri](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span><span class="sxs-lookup"><span data-stu-id="2129a-105">For more information, see [How to: Call Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) and [How to: Call Database Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="2129a-106">Özel bir işlev çağırma işlemi üç temel adımlar gerektirir:</span><span class="sxs-lookup"><span data-stu-id="2129a-106">The process for calling a custom function requires three basic steps:</span></span>  
  
1.  <span data-ttu-id="2129a-107">Kavramsal modelde bir işlev tanımlayın veya depolama modelinizi işlevinde bildirin.</span><span class="sxs-lookup"><span data-stu-id="2129a-107">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2.  <span data-ttu-id="2129a-108">Uygulamanız için bir yöntem ekleyin ve modelle işlevinde Eşle bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2129a-108">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3.  <span data-ttu-id="2129a-109">Bir LINQ to Entities sorgusunda işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="2129a-109">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="2129a-110">Bu bölümdeki konular, daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="2129a-110">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2129a-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2129a-111">In This Section</span></span>  
 [<span data-ttu-id="2129a-112">Nasıl yapılır: Kurallı İşlevler Çağırma</span><span class="sxs-lookup"><span data-stu-id="2129a-112">How to: Call Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="2129a-113">Nasıl yapılır: Veritabanı İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="2129a-113">How to: Call Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [<span data-ttu-id="2129a-114">Nasıl yapılır: Özel Veritabanı İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="2129a-114">How to: Call Custom Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="2129a-115">Nasıl Yapılır: Sorgularda Model Tanımlı İşlevler Çağırma</span><span class="sxs-lookup"><span data-stu-id="2129a-115">How to: Call Model-Defined Functions in Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="2129a-116">Nasıl Yapılır: Model Tanımlı İşlevleri Nesne Yöntemleri Olarak Çağırma</span><span class="sxs-lookup"><span data-stu-id="2129a-116">How to: Call Model-Defined Functions as Object Methods</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="2129a-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2129a-117">See Also</span></span>  
 [<span data-ttu-id="2129a-118">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="2129a-118">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [<span data-ttu-id="2129a-119">Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="2129a-119">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)  
 [<span data-ttu-id="2129a-120">.edmx dosyasının genel bakış</span><span class="sxs-lookup"><span data-stu-id="2129a-120">.edmx File Overview</span></span>](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="2129a-121">Nasıl yapılır: özel işlevler kavramsal modelde tanımlayın</span><span class="sxs-lookup"><span data-stu-id="2129a-121">How to: Define Custom Functions in the Conceptual Model</span></span>](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)
