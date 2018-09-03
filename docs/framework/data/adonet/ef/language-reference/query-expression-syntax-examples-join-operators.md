---
title: 'Sorgu ifadesi söz dizimi örnekleri: Birleşim işleçleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 343e8dda-70b2-409d-9334-ce9a880c3cea
ms.openlocfilehash: 4db511d74c4cce82bfd010f77cb1580dbb704b41
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43476030"
---
# <a name="query-expression-syntax-examples-join-operators"></a><span data-ttu-id="b3ed8-102">Sorgu ifadesi söz dizimi örnekleri: Birleşim işleçleri</span><span class="sxs-lookup"><span data-stu-id="b3ed8-102">Query Expression Syntax Examples: Join Operators</span></span>
<span data-ttu-id="b3ed8-103">Birleştirme, birbiriyle gezilebilir hiçbir ilişki ilişkisel veritabanı tabloları gibi veri kaynakları hedef sorgularda önemli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="b3ed8-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="b3ed8-104">İki veri kaynaklarının bir birleştirme nesnelerin bir veri kaynağı ile bir veri kaynağındaki ortak bir özniteliği paylaşan nesnelerin ilişkidir.</span><span class="sxs-lookup"><span data-stu-id="b3ed8-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="b3ed8-105">Daha fazla bilgi için [standart sorgu işleçlerine genel bakış](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="b3ed8-105">For more information, see [Standard Query Operators Overview](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
 <span data-ttu-id="b3ed8-106">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.GroupJoin%2A> ve <xref:System.Linq.Enumerable.Join%2A> sorgulamak için yöntemleri [AdventureWorks satışları modeli](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) sorgu ifadesi söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="b3ed8-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="b3ed8-107">Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b3ed8-107">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="b3ed8-108">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="b3ed8-108">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="b3ed8-109">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="b3ed8-109">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="b3ed8-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3ed8-110">Example</span></span>  
 <span data-ttu-id="b3ed8-111">Aşağıdaki örnek gerçekleştiren bir <xref:System.Linq.Enumerable.GroupJoin%2A> her müşteri siparişleri sayısını bulmak için SalesOrderHeader ve satış siparişi ayrıntısını tablolar üzerinden.</span><span class="sxs-lookup"><span data-stu-id="b3ed8-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="b3ed8-112">Grup birleştirme her öğe ilk (soldaki) veri kaynağının diğer veri kaynağında ilişkili hiçbir öğe olsa bile, döndüren bir sol dış birleşim eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="b3ed8-112">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="b3ed8-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3ed8-113">Example</span></span>  
 <span data-ttu-id="b3ed8-114">Aşağıdaki örnek gerçekleştiren bir <xref:System.Linq.Enumerable.GroupJoin%2A> kişi başına siparişlerin sayısını bulmak için iletişim ve SalesOrderHeader tablolar üzerinden.</span><span class="sxs-lookup"><span data-stu-id="b3ed8-114">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="b3ed8-115">Her kişi için kimlikleri ve sipariş sayısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b3ed8-115">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
### <a name="example"></a><span data-ttu-id="b3ed8-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3ed8-116">Example</span></span>  
 <span data-ttu-id="b3ed8-117">Aşağıdaki örnek gerçekleştiren bir <xref:System.Linq.Enumerable.GroupJoin%2A> başvurun ve SalesOrderHeader tablolar üzerinden.</span><span class="sxs-lookup"><span data-stu-id="b3ed8-117">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables.</span></span> <span data-ttu-id="b3ed8-118">Grup birleştirme her öğe ilk (soldaki) veri kaynağının diğer veri kaynağında ilişkili hiçbir öğe olsa bile, döndüren bir sol dış birleşim eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="b3ed8-118">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="b3ed8-119">Birleştirme</span><span class="sxs-lookup"><span data-stu-id="b3ed8-119">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="b3ed8-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3ed8-120">Example</span></span>  
 <span data-ttu-id="b3ed8-121">Aşağıdaki örnek, çevrimiçi siparişler Ağustos ay almak için SalesOrderHeader ve satış siparişi ayrıntısını tablolar üzerinde birleştirme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="b3ed8-121">The following example performs a join over the SalesOrderHeader and SalesOrderDetail tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP L2E Examples#Join](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#join)]
 [!code-vb[DP L2E Examples#Join](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="b3ed8-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3ed8-122">See Also</span></span>  
 [<span data-ttu-id="b3ed8-123">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="b3ed8-123">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
