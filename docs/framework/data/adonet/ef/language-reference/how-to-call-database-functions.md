---
title: 'Nasıl yapılır: Veritabanı İşlevleri Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
ms.openlocfilehash: 5990e9f4c08eafeae6bed18d3d8af0617b84ff54
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147933"
---
# <a name="how-to-call-database-functions"></a><span data-ttu-id="21e76-102">Nasıl yapılır: Veritabanı İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="21e76-102">How to: Call Database Functions</span></span>
<span data-ttu-id="21e76-103"><xref:System.Data.Objects.SqlClient.SqlFunctions> Sınıfı LINQ to Entities sorgularında kullanmak için SQL Server işlevleri yöntemlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="21e76-103">The <xref:System.Data.Objects.SqlClient.SqlFunctions> class contains methods that expose SQL Server functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="21e76-104">Kullanırken <xref:System.Data.Objects.SqlClient.SqlFunctions> yöntemleri LINQ to Entities sorgularında, karşılık gelen veritabanı işlevleri veritabanında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="21e76-104">When you use <xref:System.Data.Objects.SqlClient.SqlFunctions> methods in LINQ to Entities queries, the corresponding database functions are executed in the database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21e76-105">Bir değerler kümesi üzerinde bir hesaplama gerçekleştirmek ve (toplam veritabanı işlevleri olarak da bilinir) tek bir değer döndürmesi veritabanı işlevleri doğrudan çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="21e76-105">Database functions that perform a calculation on a set of values and return a single value (also known as aggregate database functions) can be directly invoked.</span></span> <span data-ttu-id="21e76-106">Diğer kurallı işlevler yalnızca bir LINQ to Entities sorgusunda bir parçası olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="21e76-106">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="21e76-107">Bir toplama işlevi doğrudan çağırmak için geçmelidir bir <xref:System.Data.Objects.ObjectQuery%601> işlevi.</span><span class="sxs-lookup"><span data-stu-id="21e76-107">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="21e76-108">Daha fazla bilgi için aşağıdaki ikinci örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="21e76-108">For more information, see the second example below.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21e76-109">Yöntemlere <xref:System.Data.Objects.SqlClient.SqlFunctions> sınıfı SQL Server işleve özeldir.</span><span class="sxs-lookup"><span data-stu-id="21e76-109">The methods in the <xref:System.Data.Objects.SqlClient.SqlFunctions> class are specific to SQL Server functions.</span></span> <span data-ttu-id="21e76-110">Veritabanı işlevler sunan benzer sınıflar diğer sağlayıcılar bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="21e76-110">Similar classes that expose database functions may be available through other providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21e76-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="21e76-111">Example</span></span>  
 <span data-ttu-id="21e76-112">Aşağıdaki örnekte [AdventureWorks satışları modeli](https://archive.codeplex.com/?p=msftdbprodsamples).</span><span class="sxs-lookup"><span data-stu-id="21e76-112">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="21e76-113">Örnek bir LINQ to Entities sorgusunda, kullanır yürütür <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> Soyadı tüm kişileri döndürülecek yöntemi "B" ile başlar:</span><span class="sxs-lookup"><span data-stu-id="21e76-113">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> method to return all contacts whose last name starts with "Si":</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="21e76-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="21e76-114">Example</span></span>  
 <span data-ttu-id="21e76-115">Aşağıdaki örnekte [AdventureWorks satışları modeli](https://archive.codeplex.com/?p=msftdbprodsamples).</span><span class="sxs-lookup"><span data-stu-id="21e76-115">The following example uses the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples).</span></span> <span data-ttu-id="21e76-116">Örnek toplama çağırır <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> doğrudan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="21e76-116">The example calls the aggregate <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> method directly.</span></span> <span data-ttu-id="21e76-117">Unutmayın bir <xref:System.Data.Objects.ObjectQuery%601> bir LINQ to Entities sorgusunda parçası olmadan çağrılmasına izin veren işleve geçirilir.</span><span class="sxs-lookup"><span data-stu-id="21e76-117">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="21e76-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21e76-118">See also</span></span>

- [<span data-ttu-id="21e76-119">LINQ to Entities Sorgularında Çağırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="21e76-119">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="21e76-120">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="21e76-120">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
