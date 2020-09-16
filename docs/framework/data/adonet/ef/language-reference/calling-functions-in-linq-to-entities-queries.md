---
title: LINQ to Entities Sorgularında Çağırma İşlevleri
description: EntityFunctions ve SqlFunctions sınıflarının Entity Framework bir parçası olarak kurallı ve veritabanı işlevlerine nasıl erişim sağlayakullandığını görmek için bu makaleleri kullanın.
ms.date: 03/30/2017
ms.assetid: 12a525a9-727c-4464-a0c7-71a0ef541792
ms.openlocfilehash: eb206e9b331da1ae442c1f310e78fec5c6b57e82
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546054"
---
# <a name="calling-functions-in-linq-to-entities-queries"></a><span data-ttu-id="3f265-103">LINQ to Entities Sorgularında Çağırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="3f265-103">Calling Functions in LINQ to Entities Queries</span></span>
<span data-ttu-id="3f265-104">Bu bölümdeki konular, LINQ to Entities sorgularda işlevlerin nasıl çağrılacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="3f265-104">The topics in this section describe how to call functions in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="3f265-105"><xref:System.Data.Objects.EntityFunctions>Ve <xref:System.Data.Objects.SqlClient.SqlFunctions> sınıfları, Entity Framework bir parçası olarak kurallı ve veritabanı işlevlerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f265-105">The <xref:System.Data.Objects.EntityFunctions> and <xref:System.Data.Objects.SqlClient.SqlFunctions> classes provide access to canonical and database functions as part of the Entity Framework.</span></span> <span data-ttu-id="3f265-106">Daha fazla bilgi için bkz. [nasıl yapılır: kurallı Işlevleri çağırma](how-to-call-canonical-functions.md) ve [nasıl yapılır: veritabanı işlevlerini çağırma](how-to-call-database-functions.md).</span><span class="sxs-lookup"><span data-stu-id="3f265-106">For more information, see [How to: Call Canonical Functions](how-to-call-canonical-functions.md) and [How to: Call Database Functions](how-to-call-database-functions.md).</span></span>  
  
 <span data-ttu-id="3f265-107">Özel bir işlevi çağırma işlemi üç temel adım gerektirir:</span><span class="sxs-lookup"><span data-stu-id="3f265-107">The process for calling a custom function requires three basic steps:</span></span>  
  
1. <span data-ttu-id="3f265-108">Kavramsal modelinizde bir işlev tanımlayın veya depolama modelinizde bir işlev bildirin.</span><span class="sxs-lookup"><span data-stu-id="3f265-108">Define a function in your conceptual model or declare a function in your storage model.</span></span>  
  
2. <span data-ttu-id="3f265-109">Uygulamanıza bir yöntem ekleyin ve bunu ile modeldeki işlevle eşleyin <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> .</span><span class="sxs-lookup"><span data-stu-id="3f265-109">Add a method to your application and map it to the function in the model with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span>  
  
3. <span data-ttu-id="3f265-110">İşlevi bir LINQ to Entities sorgusunda çağırın.</span><span class="sxs-lookup"><span data-stu-id="3f265-110">Call the function in a LINQ to Entities query.</span></span>  
  
 <span data-ttu-id="3f265-111">Daha fazla bilgi için bu bölümdeki konulara bakın.</span><span class="sxs-lookup"><span data-stu-id="3f265-111">For more information, see the topics in this section.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3f265-112">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3f265-112">In This Section</span></span>  
 [<span data-ttu-id="3f265-113">Nasıl yapılır: Kurallı İşlevler Çağırma</span><span class="sxs-lookup"><span data-stu-id="3f265-113">How to: Call Canonical Functions</span></span>](how-to-call-canonical-functions.md)  
  
 [<span data-ttu-id="3f265-114">Nasıl yapılır: Veritabanı İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="3f265-114">How to: Call Database Functions</span></span>](how-to-call-database-functions.md)  
  
 [<span data-ttu-id="3f265-115">Nasıl yapılır: Özel Veritabanı İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="3f265-115">How to: Call Custom Database Functions</span></span>](how-to-call-custom-database-functions.md)  
  
 [<span data-ttu-id="3f265-116">Nasıl Yapılır: Sorgularda Model Tanımlı İşlevler Çağırma</span><span class="sxs-lookup"><span data-stu-id="3f265-116">How to: Call Model-Defined Functions in Queries</span></span>](how-to-call-model-defined-functions-in-queries.md)  
  
 [<span data-ttu-id="3f265-117">Nasıl Yapılır: Model Tanımlı İşlevleri Nesne Yöntemleri Olarak Çağırma</span><span class="sxs-lookup"><span data-stu-id="3f265-117">How to: Call Model-Defined Functions as Object Methods</span></span>](how-to-call-model-defined-functions-as-object-methods.md)  
  
## <a name="see-also"></a><span data-ttu-id="3f265-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f265-118">See also</span></span>

- [<span data-ttu-id="3f265-119">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="3f265-119">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- [<span data-ttu-id="3f265-120">Kurallı İşlevler</span><span class="sxs-lookup"><span data-stu-id="3f265-120">Canonical Functions</span></span>](canonical-functions.md)
- <span data-ttu-id="3f265-121">[. edmx dosyasına genel bakış](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3f265-121">[.edmx File Overview](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- <span data-ttu-id="3f265-122">[Nasıl yapılır: kavramsal modelde özel Işlevleri tanımlama](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3f265-122">[How to: Define Custom Functions in the Conceptual Model](/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))</span></span>
