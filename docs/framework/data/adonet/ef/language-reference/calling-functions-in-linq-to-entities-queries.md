---
title: LINQ to Entities Sorgularında Çağırma İşlevleri
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 6fa1a7204a91a62c30e8683c449cc2be44132b4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61605788"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="ce558-102">LINQ to Entities Sorgularında Çağırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="ce558-102">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="ce558-103">Bu bölümdeki konular, LINQ to Entities sorgularında işlevlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ce558-103">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="ce558-104"><xref:System.Data.Objects.EntityFunctions> Ve <xref:System.Data.Objects.SqlClient.SqlFunctions> sınıflar, Entity Framework bir parçası olarak kurallı erişimi ve veritabanı işlevleri sunar.</span><span class="sxs-lookup"><span data-stu-id="ce558-104">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="ce558-105">Daha fazla bilgi için [nasıl yapılır: Kurallı işlevler çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) ve [nasıl yapılır: Veritabanı işlevleri çağırma](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span><span class="sxs-lookup"><span data-stu-id="ce558-105">For more information, see [How to: Call Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md) and [How to: Call Database Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="ce558-106">Özel bir işlev çağırma işlemi üç temel adımları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="ce558-106">The process for calling a custom function requires three basic steps:</span></span>  
  
1. <span data-ttu-id="ce558-107">Kavramsal modelinizde bir fonksiyon tanımlayın veya depolama modelinizdeki bir işlev bildirir.</span><span class="sxs-lookup"><span data-stu-id="ce558-107">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2. <span data-ttu-id="ce558-108">Uygulamanız için bir yöntem ekleyin ve işlevine modeliyle eşlemek bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ce558-108">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3. <span data-ttu-id="ce558-109">Bir LINQ to Entities sorgusunda işlevi çağırın.</span><span class="sxs-lookup"><span data-stu-id="ce558-109">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="ce558-110">Daha fazla bilgi için bu bölümdeki konular, bkz.</span><span class="sxs-lookup"><span data-stu-id="ce558-110">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ce558-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ce558-111">In This Section</span></span>  
 [<span data-ttu-id="ce558-112">Nasıl yapılır: Kurallı işlevler çağırma</span><span class="sxs-lookup"><span data-stu-id="ce558-112">How to: Call Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="ce558-113">Nasıl yapılır: Veritabanı işlevleri çağırma</span><span class="sxs-lookup"><span data-stu-id="ce558-113">How to: Call Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-database-functions.md)  
  
 [<span data-ttu-id="ce558-114">Nasıl yapılır: Özel veritabanı işlevleri çağırma</span><span class="sxs-lookup"><span data-stu-id="ce558-114">How to: Call Custom Database Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="ce558-115">Nasıl yapılır: Sorgularda model tanımlı işlevler çağırma</span><span class="sxs-lookup"><span data-stu-id="ce558-115">How to: Call Model-Defined Functions in Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="ce558-116">Nasıl yapılır: Model tanımlı işlevleri nesne yöntemleri çağırma</span><span class="sxs-lookup"><span data-stu-id="ce558-116">How to: Call Model-Defined Functions as Object Methods</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="ce558-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce558-117">See also</span></span>

- [<span data-ttu-id="ce558-118">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="ce558-118">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
- [<span data-ttu-id="ce558-119">Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="ce558-119">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
- <span data-ttu-id="ce558-120">[.edmx dosyasını genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ce558-120">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- <span data-ttu-id="ce558-121">[Nasıl yapılır: Kavramsal modelde özel işlevleri tanımlayın](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ce558-121">[How to: Define Custom Functions in the Conceptual Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span></span>
