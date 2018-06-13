---
title: 'Sorgu ifade sözdizimi örnekleri: Birleştirme işleçleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 343e8dda-70b2-409d-9334-ce9a880c3cea
ms.openlocfilehash: af7bea7c9fda7a3c1eb1e419c50dcd61df8c63d1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765925"
---
# <a name="query-expression-syntax-examples-join-operators"></a><span data-ttu-id="f6b1b-102">Sorgu ifade sözdizimi örnekleri: Birleştirme işleçleri</span><span class="sxs-lookup"><span data-stu-id="f6b1b-102">Query Expression Syntax Examples: Join Operators</span></span>
<span data-ttu-id="f6b1b-103">Birleştirme, birbirlerine, gezinebilir hiçbir ilişki ilişkisel veritabanı tabloları gibi sahip veri kaynaklarına hedef sorgularda önemli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="f6b1b-104">İki veri kaynaklarının bir birleştirme nesnelerin bir veri kaynağının diğer veri kaynağındaki ortak bir özniteliği paylaşan nesnelerle ilişkidir.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="f6b1b-105">Daha fazla bilgi için bkz: [standart sorgu işleçlerine genel bakış](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="f6b1b-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
 <span data-ttu-id="f6b1b-106">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.GroupJoin%2A> ve <xref:System.Linq.Enumerable.Join%2A> sorgulamak için yöntemleri [AdventureWorks satış modeli](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) sorgu ifade sözdizimi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="f6b1b-107">Bu örneklerde kullanılan AdventureWorks satış modeli AdventureWorks örnek veritabanını kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-107">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f6b1b-108">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="f6b1b-108">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="f6b1b-109">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="f6b1b-109">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="f6b1b-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6b1b-110">Example</span></span>  
 <span data-ttu-id="f6b1b-111">Aşağıdaki örnek gerçekleştiren bir <xref:System.Linq.Enumerable.GroupJoin%2A> müşteri başına sipariş sayısını bulmak için SalesOrderHeader ve satış siparişi ayrıntısını tablolar üzerinde.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="f6b1b-112">Bir grup birleştirme her öğe ilk (soldaki) veri kaynağının diğer veri kaynağında ilişkili öğe olsa bile, döndüren bir sol dış birleşim eşdeğeridir.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-112">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="f6b1b-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6b1b-113">Example</span></span>  
 <span data-ttu-id="f6b1b-114">Aşağıdaki örnek gerçekleştiren bir <xref:System.Linq.Enumerable.GroupJoin%2A> kişi başına siparişleri sayısını bulmak için iletişim ve SalesOrderHeader tablolar üzerinde.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-114">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="f6b1b-115">Sıra sayısı ve her kişi için kimlikleri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-115">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
### <a name="example"></a><span data-ttu-id="f6b1b-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6b1b-116">Example</span></span>  
 <span data-ttu-id="f6b1b-117">Aşağıdaki örnek gerçekleştiren bir <xref:System.Linq.Enumerable.GroupJoin%2A> başvurun ve SalesOrderHeader tablolar üzerinde.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-117">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables.</span></span> <span data-ttu-id="f6b1b-118">Bir grup birleştirme her öğe ilk (soldaki) veri kaynağının diğer veri kaynağında ilişkili öğe olsa bile, döndüren bir sol dış birleşim eşdeğeridir.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-118">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="f6b1b-119">Birleştirme</span><span class="sxs-lookup"><span data-stu-id="f6b1b-119">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="f6b1b-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6b1b-120">Example</span></span>  
 <span data-ttu-id="f6b1b-121">Aşağıdaki örnek, çevrimiçi olarak sipariş Ağustos, month almak için SalesOrderHeader ve satış siparişi ayrıntısını tablolar üzerinde birleştirme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-121">The following example performs a join over the SalesOrderHeader and SalesOrderDetail tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP L2E Examples#Join](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#join)]
 [!code-vb[DP L2E Examples#Join](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="f6b1b-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6b1b-122">See Also</span></span>  
 [<span data-ttu-id="f6b1b-123">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="f6b1b-123">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
