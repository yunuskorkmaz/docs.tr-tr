---
title: 'Nasıl yapılır: Kurallı İşlevleri Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: 6e555b3d896862db491b34e11564e70bbe2d15eb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213161"
---
# <a name="how-to-call-canonical-functions"></a><span data-ttu-id="caa32-102">Nasıl yapılır: Kurallı İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="caa32-102">How to: Call Canonical Functions</span></span>
<span data-ttu-id="caa32-103"><xref:System.Data.Objects.EntityFunctions> Sınıfı LINQ to Entities sorgularında kullanmak için kurallı işlevler sunan yöntemlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="caa32-103">The <xref:System.Data.Objects.EntityFunctions> class contains methods that expose canonical functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="caa32-104">Kurallı işlevler hakkında daha fazla bilgi için bkz: [kurallı işlevler](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="caa32-104">For information about canonical functions, see [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="caa32-105"><xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> Ve <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> yöntemleri <xref:System.Data.Objects.EntityFunctions> sınıfı kurallı işlev eşdeğerleri sahip değil.</span><span class="sxs-lookup"><span data-stu-id="caa32-105">The <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> and <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> methods in the <xref:System.Data.Objects.EntityFunctions> class do not have canonical function equivalents.</span></span>  
  
 <span data-ttu-id="caa32-106">Bir değerler kümesi üzerinde bir hesaplama gerçekleştirmek ve (diğer adıyla toplu kurallı işlevler) tek bir değer döndürmesi kurallı işlevler doğrudan çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="caa32-106">Canonical functions that perform a calculation on a set of values and return a single value (also known as aggregate canonical functions) can be directly invoked.</span></span> <span data-ttu-id="caa32-107">Diğer kurallı işlevler yalnızca bir LINQ to Entities sorgusunda bir parçası olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="caa32-107">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="caa32-108">Bir toplama işlevi doğrudan çağırmak için geçmelidir bir <xref:System.Data.Objects.ObjectQuery%601> işlevi.</span><span class="sxs-lookup"><span data-stu-id="caa32-108">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="caa32-109">Daha fazla bilgi için aşağıdaki ikinci örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="caa32-109">For more information, see the second example below.</span></span>  
  
 <span data-ttu-id="caa32-110">Ortak dil çalışma zamanı (CLR) yöntemleri LINQ to Entities sorgularında kullanarak bazı kurallı işlevler çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="caa32-110">You can call some canonical functions by using common language runtime (CLR) methods in LINQ to Entities queries.</span></span> <span data-ttu-id="caa32-111">Kurallı işlevler için harita CLR yöntemlerinde listesi için bkz. [CLR yöntemini kurallı işlev eşleme Mapping](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="caa32-111">For a list of CLR methods that map to canonical functions, see [CLR Method to Canonical Function Mapping](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="caa32-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="caa32-112">Example</span></span>  
 <span data-ttu-id="caa32-113">Aşağıdaki örnekte [AdventureWorks satışları modeli](https://archive.codeplex.com/?p=msftdbprodsamples).</span><span class="sxs-lookup"><span data-stu-id="caa32-113">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="caa32-114">Örnek bir LINQ to Entities sorgusunda, kullanır yürütür <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> tüm ürünler için döndürülecek yöntemi arasındaki farkı `SellEndDate` ve `SellStartDate` küçüktür 365 gün:</span><span class="sxs-lookup"><span data-stu-id="caa32-114">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> method to return all products for which the difference between `SellEndDate` and `SellStartDate` is less than 365 days:</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="caa32-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="caa32-115">Example</span></span>  
 <span data-ttu-id="caa32-116">Aşağıdaki örnekte [AdventureWorks satışları modeli](https://archive.codeplex.com/?p=msftdbprodsamples).</span><span class="sxs-lookup"><span data-stu-id="caa32-116">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="caa32-117">Örnek toplama çağırır <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> standart sapmasını doğrudan döndürülecek yöntemi `SalesOrderHeader` alt toplamları.</span><span class="sxs-lookup"><span data-stu-id="caa32-117">The example calls the aggregate <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> method directly to return the standard deviation of `SalesOrderHeader` subtotals.</span></span> <span data-ttu-id="caa32-118">Unutmayın bir <xref:System.Data.Objects.ObjectQuery%601> bir LINQ to Entities sorgusunda parçası olmadan çağrılmasına izin veren işleve geçirilir.</span><span class="sxs-lookup"><span data-stu-id="caa32-118">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="caa32-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="caa32-119">See also</span></span>

- [<span data-ttu-id="caa32-120">LINQ to Entities Sorgularında Çağırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="caa32-120">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="caa32-121">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="caa32-121">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
