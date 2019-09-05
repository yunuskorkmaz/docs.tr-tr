---
title: 'Nasıl yapılır: Veritabanı İşlevleri Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
ms.openlocfilehash: c9cb8d32227447d3808dc250a39fef0867257a77
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250776"
---
# <a name="how-to-call-database-functions"></a><span data-ttu-id="823e5-102">Nasıl yapılır: Veritabanı İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="823e5-102">How to: Call Database Functions</span></span>
<span data-ttu-id="823e5-103">Sınıfı <xref:System.Data.Objects.SqlClient.SqlFunctions> , LINQ to Entities sorgularda kullanmak üzere SQL Server işlevleri sunan yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="823e5-103">The <xref:System.Data.Objects.SqlClient.SqlFunctions> class contains methods that expose SQL Server functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="823e5-104">LINQ to Entities sorgularda Yöntemler <xref:System.Data.Objects.SqlClient.SqlFunctions> kullandığınızda, karşılık gelen veritabanı işlevleri veritabanında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="823e5-104">When you use <xref:System.Data.Objects.SqlClient.SqlFunctions> methods in LINQ to Entities queries, the corresponding database functions are executed in the database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="823e5-105">Bir değer kümesi üzerinde hesaplama yapan ve tek bir değer döndüren (toplu veritabanı işlevleri olarak da bilinir) veritabanı işlevleri doğrudan çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="823e5-105">Database functions that perform a calculation on a set of values and return a single value (also known as aggregate database functions) can be directly invoked.</span></span> <span data-ttu-id="823e5-106">Diğer kurallı işlevler, yalnızca bir LINQ to Entities sorgusunun parçası olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="823e5-106">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="823e5-107">Bir toplama işlevini doğrudan çağırmak için, işlevine bir <xref:System.Data.Objects.ObjectQuery%601> öğesine geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="823e5-107">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="823e5-108">Daha fazla bilgi için aşağıdaki ikinci örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="823e5-108">For more information, see the second example below.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="823e5-109"><xref:System.Data.Objects.SqlClient.SqlFunctions> Sınıfındaki Yöntemler SQL Server işlevlere özgüdür.</span><span class="sxs-lookup"><span data-stu-id="823e5-109">The methods in the <xref:System.Data.Objects.SqlClient.SqlFunctions> class are specific to SQL Server functions.</span></span> <span data-ttu-id="823e5-110">Veritabanı işlevlerini kullanıma sunan benzer sınıflar, diğer sağlayıcılar aracılığıyla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="823e5-110">Similar classes that expose database functions may be available through other providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="823e5-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="823e5-111">Example</span></span>  
 <span data-ttu-id="823e5-112">Aşağıdaki örnek, [AdventureWorks Sales modelini](https://archive.codeplex.com/?p=msftdbprodsamples)kullanır.</span><span class="sxs-lookup"><span data-stu-id="823e5-112">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="823e5-113">Örnek, son adı "si" ile başlayan <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> tüm kişileri döndürmek için yöntemini kullanan LINQ to Entities bir sorgu yürütür:</span><span class="sxs-lookup"><span data-stu-id="823e5-113">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> method to return all contacts whose last name starts with "Si":</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="823e5-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="823e5-114">Example</span></span>  
 <span data-ttu-id="823e5-115">Aşağıdaki örnek, [AdventureWorks Sales modelini](https://archive.codeplex.com/?p=msftdbprodsamples)kullanır.</span><span class="sxs-lookup"><span data-stu-id="823e5-115">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="823e5-116">Örnek, doğrudan toplama <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="823e5-116">The example calls the aggregate <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> method directly.</span></span> <span data-ttu-id="823e5-117">Öğesinin bir <xref:System.Data.Objects.ObjectQuery%601> LINQ to Entities sorgusunun parçası olmadan çağrılmasına izin veren işleve geçtiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="823e5-117">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="823e5-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="823e5-118">See also</span></span>

- [<span data-ttu-id="823e5-119">LINQ to Entities Sorgularında Çağırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="823e5-119">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="823e5-120">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="823e5-120">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
