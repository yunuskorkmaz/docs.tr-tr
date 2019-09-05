---
title: LINQ to Entities Sorgularında Çağırma İşlevleri
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: 267bb393d9e75c66eb18139e8897da34bd86e159
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251260"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="721db-102">LINQ to Entities Sorgularında Çağırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="721db-102">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="721db-103">Bu bölümdeki konular, LINQ to Entities sorgularda işlevlerin nasıl çağrılacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="721db-103">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="721db-104"><xref:System.Data.Objects.EntityFunctions> Ve<xref:System.Data.Objects.SqlClient.SqlFunctions> sınıfları, Entity Framework bir parçası olarak kurallı ve veritabanı işlevlerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="721db-104">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="721db-105">Daha fazla bilgi için [nasıl yapılır: Kurallı işlevleri](how-to-call-canonical-functions.md) çağırın ve [şunları yapın: Veritabanı Işlevlerini](how-to-call-database-functions.md)çağırın.</span><span class="sxs-lookup"><span data-stu-id="721db-105">For more information, see [How to: Call Canonical Functions](how-to-call-canonical-functions.md) and [How to: Call Database Functions](how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="721db-106">Özel bir işlevi çağırma işlemi üç temel adım gerektirir:</span><span class="sxs-lookup"><span data-stu-id="721db-106">The process for calling a custom function requires three basic steps:</span></span>  
  
1. <span data-ttu-id="721db-107">Kavramsal modelinizde bir işlev tanımlayın veya depolama modelinizde bir işlev bildirin.</span><span class="sxs-lookup"><span data-stu-id="721db-107">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2. <span data-ttu-id="721db-108">Uygulamanıza bir yöntem ekleyin ve bunu ile <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>modeldeki işlevle eşleyin.</span><span class="sxs-lookup"><span data-stu-id="721db-108">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3. <span data-ttu-id="721db-109">İşlevi bir LINQ to Entities sorgusunda çağırın.</span><span class="sxs-lookup"><span data-stu-id="721db-109">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="721db-110">Daha fazla bilgi için bu bölümdeki konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="721db-110">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="721db-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="721db-111">In This Section</span></span>  
 [<span data-ttu-id="721db-112">Nasıl yapılır: Kurallı Işlevleri çağırın</span><span class="sxs-lookup"><span data-stu-id="721db-112">How to: Call Canonical Functions</span></span>](how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="721db-113">Nasıl yapılır: Arama veritabanı Işlevleri</span><span class="sxs-lookup"><span data-stu-id="721db-113">How to: Call Database Functions</span></span>](how-to-call-database-functions.md)  
  
 [<span data-ttu-id="721db-114">Nasıl yapılır: Özel veritabanı Işlevlerini çağırma</span><span class="sxs-lookup"><span data-stu-id="721db-114">How to: Call Custom Database Functions</span></span>](how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="721db-115">Nasıl yapılır: Sorgularda model tanımlı Işlevleri çağırma</span><span class="sxs-lookup"><span data-stu-id="721db-115">How to: Call Model-Defined Functions in Queries</span></span>](how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="721db-116">Nasıl yapılır: Model tanımlı Işlevleri nesne yöntemleri olarak çağırma</span><span class="sxs-lookup"><span data-stu-id="721db-116">How to: Call Model-Defined Functions as Object Methods</span></span>](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="721db-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="721db-117">See also</span></span>

- [<span data-ttu-id="721db-118">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="721db-118">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- [<span data-ttu-id="721db-119">Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="721db-119">Canonical Functions</span></span>](canonical-functions.md)
- <span data-ttu-id="721db-120">[. edmx dosyasına genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="721db-120">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- <span data-ttu-id="721db-121">[Nasıl yapılır: Kavramsal modelde özel Işlevleri tanımlama](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="721db-121">[How to: Define Custom Functions in the Conceptual Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span></span>
