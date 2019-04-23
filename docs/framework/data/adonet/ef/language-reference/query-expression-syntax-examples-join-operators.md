---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Birleşim İşleçleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 343e8dda-70b2-409d-9334-ce9a880c3cea
ms.openlocfilehash: da583ed207a8c4fc9e061d517895ca0f2fea2f5e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168824"
---
# <a name="query-expression-syntax-examples-join-operators"></a><span data-ttu-id="93d49-102">Sorgu İfadesi Söz Dizimi Örnekleri: Birleşim İşleçleri</span><span class="sxs-lookup"><span data-stu-id="93d49-102">Query Expression Syntax Examples: Join Operators</span></span>
<span data-ttu-id="93d49-103">Birleştirme, birbiriyle gezilebilir hiçbir ilişki ilişkisel veritabanı tabloları gibi veri kaynakları hedef sorgularda önemli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="93d49-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="93d49-104">İki veri kaynaklarının bir birleştirme nesnelerin bir veri kaynağı ile bir veri kaynağındaki ortak bir özniteliği paylaşan nesnelerin ilişkidir.</span><span class="sxs-lookup"><span data-stu-id="93d49-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="93d49-105">Daha fazla bilgi için [standart sorgu işleçlerine genel bakış](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="93d49-105">For more information, see [Standard Query Operators Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).</span></span>  
  
 <span data-ttu-id="93d49-106">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.GroupJoin%2A> ve <xref:System.Linq.Enumerable.Join%2A> sorgulamak için yöntemleri [AdventureWorks satışları modeli](https://archive.codeplex.com/?p=msftdbprodsamples) sorgu ifadesi söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="93d49-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="93d49-107">Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="93d49-107">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="93d49-108">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="93d49-108">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="93d49-109">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="93d49-109">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="93d49-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="93d49-110">Example</span></span>  
 <span data-ttu-id="93d49-111">Aşağıdaki örnek gerçekleştiren bir <xref:System.Linq.Enumerable.GroupJoin%2A> her müşteri siparişleri sayısını bulmak için SalesOrderHeader ve satış siparişi ayrıntısını tablolar üzerinden.</span><span class="sxs-lookup"><span data-stu-id="93d49-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="93d49-112">Grup birleştirme her öğe ilk (soldaki) veri kaynağının diğer veri kaynağında ilişkili hiçbir öğe olsa bile, döndüren bir sol dış birleşim eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="93d49-112">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="93d49-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="93d49-113">Example</span></span>  
 <span data-ttu-id="93d49-114">Aşağıdaki örnek gerçekleştiren bir <xref:System.Linq.Enumerable.GroupJoin%2A> kişi başına siparişlerin sayısını bulmak için iletişim ve SalesOrderHeader tablolar üzerinden.</span><span class="sxs-lookup"><span data-stu-id="93d49-114">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="93d49-115">Her kişi için kimlikleri ve sipariş sayısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="93d49-115">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="93d49-116">Birleştirme</span><span class="sxs-lookup"><span data-stu-id="93d49-116">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="93d49-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="93d49-117">Example</span></span>  
 <span data-ttu-id="93d49-118">Aşağıdaki örnek, çevrimiçi siparişler Ağustos ay almak için SalesOrderHeader ve satış siparişi ayrıntısını tablolar üzerinde birleştirme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="93d49-118">The following example performs a join over the SalesOrderHeader and SalesOrderDetail tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP L2E Examples#Join](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#join)]
 [!code-vb[DP L2E Examples#Join](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="93d49-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93d49-119">See also</span></span>

- [<span data-ttu-id="93d49-120">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="93d49-120">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
