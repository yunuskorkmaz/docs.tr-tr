---
title: 'Nasıl yapılır: çağrı veritabanı işlevleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79038efa-15bf-464a-83e2-35fe145252ce
ms.openlocfilehash: b885cedbb324ee0a076990bceb28bf256814bb26
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-call-database-functions"></a><span data-ttu-id="45194-102">Nasıl yapılır: çağrı veritabanı işlevleri</span><span class="sxs-lookup"><span data-stu-id="45194-102">How to: Call Database Functions</span></span>
<span data-ttu-id="45194-103"><xref:System.Data.Objects.SqlClient.SqlFunctions> Sınıfı LINQ to Entities sorgularında kullanmak için SQL Server işlevleri yöntemlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="45194-103">The <xref:System.Data.Objects.SqlClient.SqlFunctions> class contains methods that expose SQL Server functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="45194-104">Kullandığınızda <xref:System.Data.Objects.SqlClient.SqlFunctions> varlıklar sorguları, karşılık gelen veritabanı işlevleri LINQ yöntemlere veritabanında çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="45194-104">When you use <xref:System.Data.Objects.SqlClient.SqlFunctions> methods in LINQ to Entities queries, the corresponding database functions are executed in the database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45194-105">Tek bir değer (Birleşik veritabanı işlevleri olarak da bilinir) bir değerler kümesi üzerinde bir hesaplama gerçekleştirmek ve veritabanı işlevleri doğrudan çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="45194-105">Database functions that perform a calculation on a set of values and return a single value (also known as aggregate database functions) can be directly invoked.</span></span> <span data-ttu-id="45194-106">Kurallı diğer işlevleri yalnızca bir LINQ to Entities sorgusunun bir parçası olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="45194-106">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="45194-107">Bir toplama işlevi doğrudan çağırmak için geçmesi gereken bir <xref:System.Data.Objects.ObjectQuery%601> işlevi.</span><span class="sxs-lookup"><span data-stu-id="45194-107">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="45194-108">Daha fazla bilgi için aşağıdaki ikinci örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="45194-108">For more information, see the second example below.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45194-109">Yöntemlere <xref:System.Data.Objects.SqlClient.SqlFunctions> sınıfı için SQL Server işlevleri özeldir.</span><span class="sxs-lookup"><span data-stu-id="45194-109">The methods in the <xref:System.Data.Objects.SqlClient.SqlFunctions> class are specific to SQL Server functions.</span></span> <span data-ttu-id="45194-110">Veritabanı işlevleri kullanıma benzer sınıflar diğer sağlayıcıları üzerinden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="45194-110">Similar classes that expose database functions may be available through other providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45194-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="45194-111">Example</span></span>  
 <span data-ttu-id="45194-112">Aşağıdaki örnek kullanır [AdventureWorks satış modeli](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="45194-112">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="45194-113">Örnek bir LINQ to kullanan varlıklar sorgu yürütür <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> Soyadı tüm kişileri döndürülecek yöntemi "Si" ile başlar:</span><span class="sxs-lookup"><span data-stu-id="45194-113">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.SqlClient.SqlFunctions.CharIndex%2A> method to return all contacts whose last name starts with "Si":</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#3)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="45194-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="45194-114">Example</span></span>  
 <span data-ttu-id="45194-115">Aşağıdaki örnek kullanır [AdventureWorks satış modeli](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="45194-115">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="45194-116">Örnek toplama çağırır <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> doğrudan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="45194-116">The example calls the aggregate <xref:System.Data.Objects.SqlClient.SqlFunctions.ChecksumAggregate%2A> method directly.</span></span> <span data-ttu-id="45194-117">Unutmayın bir <xref:System.Data.Objects.ObjectQuery%601> bir LINQ to Entities sorgusunun parçası olmadan çağrılmasına izin veren işlevi geçirilir.</span><span class="sxs-lookup"><span data-stu-id="45194-117">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#4)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="45194-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45194-118">See Also</span></span>  
 [<span data-ttu-id="45194-119">LINQ to Entities Sorgularında Çağırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="45194-119">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [<span data-ttu-id="45194-120">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="45194-120">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
