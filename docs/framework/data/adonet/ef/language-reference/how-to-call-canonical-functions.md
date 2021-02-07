---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: kurallı Işlevleri çağırma'
title: 'Nasıl yapılır: Kurallı İşlevler Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: d1e2310bccd6cc60177dba9a2e4c3a104702ba0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696847"
---
# <a name="how-to-call-canonical-functions"></a><span data-ttu-id="a27e9-103">Nasıl yapılır: Kurallı İşlevler Çağırma</span><span class="sxs-lookup"><span data-stu-id="a27e9-103">How to: Call Canonical Functions</span></span>

<span data-ttu-id="a27e9-104"><xref:System.Data.Objects.EntityFunctions>Sınıfı, LINQ to Entities sorgularda kullanılacak kurallı işlevleri kullanıma sunan yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="a27e9-104">The <xref:System.Data.Objects.EntityFunctions> class contains methods that expose canonical functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="a27e9-105">Kurallı işlevler hakkında daha fazla bilgi için bkz. [kurallı işlevler](canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="a27e9-105">For information about canonical functions, see [Canonical Functions](canonical-functions.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a27e9-106"><xref:System.Data.Objects.EntityFunctions.AsUnicode%2A>Sınıfındaki ve <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> yöntemlerinin <xref:System.Data.Objects.EntityFunctions> Kurallı işlev eşdeğerleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="a27e9-106">The <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> and <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> methods in the <xref:System.Data.Objects.EntityFunctions> class do not have canonical function equivalents.</span></span>  
  
 <span data-ttu-id="a27e9-107">Bir değer kümesi üzerinde hesaplama gerçekleştiren ve tek bir değer döndüren (Toplama kurallı işlevler olarak da bilinir) kurallı işlevler doğrudan çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a27e9-107">Canonical functions that perform a calculation on a set of values and return a single value (also known as aggregate canonical functions) can be directly invoked.</span></span> <span data-ttu-id="a27e9-108">Diğer kurallı işlevler, yalnızca bir LINQ to Entities sorgusunun parçası olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a27e9-108">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="a27e9-109">Bir toplama işlevini doğrudan çağırmak için, işlevine bir öğesine geçirmeniz gerekir <xref:System.Data.Objects.ObjectQuery%601> .</span><span class="sxs-lookup"><span data-stu-id="a27e9-109">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="a27e9-110">Daha fazla bilgi için aşağıdaki ikinci örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="a27e9-110">For more information, see the second example below.</span></span>  
  
 <span data-ttu-id="a27e9-111">LINQ to Entities sorgularda ortak dil çalışma zamanı (CLR) yöntemlerini kullanarak, bazı kurallı işlevleri çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a27e9-111">You can call some canonical functions by using common language runtime (CLR) methods in LINQ to Entities queries.</span></span> <span data-ttu-id="a27e9-112">Kurallı işlevlerle eşlenen CLR yöntemlerinin listesi için bkz. [CLR yöntemi Ile kurallı Işlev eşleme](clr-method-to-canonical-function-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="a27e9-112">For a list of CLR methods that map to canonical functions, see [CLR Method to Canonical Function Mapping](clr-method-to-canonical-function-mapping.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a27e9-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="a27e9-113">Example</span></span>  

 <span data-ttu-id="a27e9-114">Aşağıdaki örnek, [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)kullanır.</span><span class="sxs-lookup"><span data-stu-id="a27e9-114">The following example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="a27e9-115">Örnek, <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> ve arasındaki farkın `SellEndDate` `SellStartDate` 365 günden daha az olduğu tüm ürünleri döndürmek için yöntemini kullanan LINQ to Entities bir sorgu yürütür:</span><span class="sxs-lookup"><span data-stu-id="a27e9-115">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> method to return all products for which the difference between `SellEndDate` and `SellStartDate` is less than 365 days:</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="a27e9-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="a27e9-116">Example</span></span>  

 <span data-ttu-id="a27e9-117">Aşağıdaki örnek, [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)kullanır.</span><span class="sxs-lookup"><span data-stu-id="a27e9-117">The following example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="a27e9-118">Örnek, <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> alt toplamların standart sapmasını döndürmek için doğrudan toplama yöntemini çağırır `SalesOrderHeader` .</span><span class="sxs-lookup"><span data-stu-id="a27e9-118">The example calls the aggregate <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> method directly to return the standard deviation of `SalesOrderHeader` subtotals.</span></span> <span data-ttu-id="a27e9-119">Öğesinin bir <xref:System.Data.Objects.ObjectQuery%601> LINQ to Entities sorgusunun parçası olmadan çağrılmasına izin veren işleve geçtiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a27e9-119">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a27e9-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a27e9-120">See also</span></span>

- [<span data-ttu-id="a27e9-121">LINQ to Entities Sorgularında Çağırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a27e9-121">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="a27e9-122">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="a27e9-122">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
