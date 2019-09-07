---
title: 'Nasıl yapılır: Kurallı İşlevleri Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: a1c550b35142cffceeaf08f7d9ff049c766307e0
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397563"
---
# <a name="how-to-call-canonical-functions"></a><span data-ttu-id="02658-102">Nasıl yapılır: Kurallı İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="02658-102">How to: Call Canonical Functions</span></span>
<span data-ttu-id="02658-103">Sınıfı <xref:System.Data.Objects.EntityFunctions> , LINQ to Entities sorgularda kullanılacak kurallı işlevleri kullanıma sunan yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="02658-103">The <xref:System.Data.Objects.EntityFunctions> class contains methods that expose canonical functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="02658-104">Kurallı işlevler hakkında daha fazla bilgi için bkz. [kurallı işlevler](canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="02658-104">For information about canonical functions, see [Canonical Functions](canonical-functions.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02658-105">Sınıfındaki ve <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> yöntemlerinin Kurallı işlev eşdeğerleri yoktur. <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> <xref:System.Data.Objects.EntityFunctions></span><span class="sxs-lookup"><span data-stu-id="02658-105">The <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> and <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> methods in the <xref:System.Data.Objects.EntityFunctions> class do not have canonical function equivalents.</span></span>  
  
 <span data-ttu-id="02658-106">Bir değer kümesi üzerinde hesaplama gerçekleştiren ve tek bir değer döndüren (Toplama kurallı işlevler olarak da bilinir) kurallı işlevler doğrudan çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="02658-106">Canonical functions that perform a calculation on a set of values and return a single value (also known as aggregate canonical functions) can be directly invoked.</span></span> <span data-ttu-id="02658-107">Diğer kurallı işlevler, yalnızca bir LINQ to Entities sorgusunun parçası olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="02658-107">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="02658-108">Bir toplama işlevini doğrudan çağırmak için, işlevine bir <xref:System.Data.Objects.ObjectQuery%601> öğesine geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="02658-108">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="02658-109">Daha fazla bilgi için aşağıdaki ikinci örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="02658-109">For more information, see the second example below.</span></span>  
  
 <span data-ttu-id="02658-110">LINQ to Entities sorgularda ortak dil çalışma zamanı (CLR) yöntemlerini kullanarak, bazı kurallı işlevleri çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02658-110">You can call some canonical functions by using common language runtime (CLR) methods in LINQ to Entities queries.</span></span> <span data-ttu-id="02658-111">Kurallı işlevlerle eşlenen CLR yöntemlerinin listesi için bkz. [CLR yöntemi Ile kurallı Işlev eşleme](clr-method-to-canonical-function-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="02658-111">For a list of CLR methods that map to canonical functions, see [CLR Method to Canonical Function Mapping](clr-method-to-canonical-function-mapping.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="02658-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="02658-112">Example</span></span>  
 <span data-ttu-id="02658-113">Aşağıdaki örnek, [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)kullanır.</span><span class="sxs-lookup"><span data-stu-id="02658-113">The following example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="02658-114">Örnek, ve <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> `SellEndDate` arasındaki`SellStartDate` farkın 365 günden daha az olduğu tüm ürünleri döndürmek için yöntemini kullanan LINQ to Entities bir sorgu yürütür:</span><span class="sxs-lookup"><span data-stu-id="02658-114">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> method to return all products for which the difference between `SellEndDate` and `SellStartDate` is less than 365 days:</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="02658-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="02658-115">Example</span></span>  
 <span data-ttu-id="02658-116">Aşağıdaki örnek, [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)kullanır.</span><span class="sxs-lookup"><span data-stu-id="02658-116">The following example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="02658-117">Örnek, `SalesOrderHeader` alt toplamların standart <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> sapmasını döndürmek için doğrudan toplama yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="02658-117">The example calls the aggregate <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> method directly to return the standard deviation of `SalesOrderHeader` subtotals.</span></span> <span data-ttu-id="02658-118">Öğesinin bir <xref:System.Data.Objects.ObjectQuery%601> LINQ to Entities sorgusunun parçası olmadan çağrılmasına izin veren işleve geçtiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="02658-118">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="02658-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02658-119">See also</span></span>

- [<span data-ttu-id="02658-120">LINQ to Entities Sorgularında Çağırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="02658-120">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="02658-121">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="02658-121">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
