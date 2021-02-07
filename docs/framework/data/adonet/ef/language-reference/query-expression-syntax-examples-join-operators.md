---
description: 'Hakkında daha fazla bilgi: sorgu Ifadesi söz dizimi örnekleri: JOIN Işleçleri'
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Birleşim İşleçleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 343e8dda-70b2-409d-9334-ce9a880c3cea
ms.openlocfilehash: 01ca3157ef13097c5c89ac1e6bafd03873c05977
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696210"
---
# <a name="query-expression-syntax-examples-join-operators"></a><span data-ttu-id="08120-103">Sorgu İfadesi Söz Dizimi Örnekleri: Birleşim İşleçleri</span><span class="sxs-lookup"><span data-stu-id="08120-103">Query Expression Syntax Examples: Join Operators</span></span>

<span data-ttu-id="08120-104">Birleştirme, ilişkisel veritabanı tabloları gibi birbirleriyle gezinebilir ilişki bulunmayan veri kaynaklarını hedefleyen sorgularda önemli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="08120-104">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="08120-105">İki veri kaynağının birleşimi, bir veri kaynağındaki nesnelerin diğer veri kaynağında ortak bir özniteliği paylaşan nesneler ile ilişkilendirilmesi olur.</span><span class="sxs-lookup"><span data-stu-id="08120-105">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="08120-106">Daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış](/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="08120-106">For more information, see [Standard Query Operators Overview](/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).</span></span>  
  
 <span data-ttu-id="08120-107">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.GroupJoin%2A> <xref:System.Linq.Enumerable.Join%2A> sorgu ifadesi sözdizimini kullanarak [AdventureWorks Sales modelini](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) sorgulamak için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="08120-107">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="08120-108">Bu örneklerde kullanılan AdventureWorks Sales modeli, AdventureWorks örnek veritabanındaki Contact, Address, Product, SalesOrderHeader ve SalesOrderDetail tablolarından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="08120-108">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="08120-109">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="08120-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="08120-110">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="08120-110">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="08120-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="08120-111">Example</span></span>  

 <span data-ttu-id="08120-112">Aşağıdaki örnek, <xref:System.Linq.Enumerable.GroupJoin%2A> müşteri başına sipariş sayısını bulmak Için SalesOrderHeader ve SalesOrderDetail tabloları üzerinde bir yapar.</span><span class="sxs-lookup"><span data-stu-id="08120-112">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="08120-113">Bir grup birleşimi, diğer veri kaynağında hiçbir bağıntılı öğe olmasa bile, ilk (soldaki) veri kaynağının her bir öğesini döndüren sol dış birleştirmenin eşdeğeridir.</span><span class="sxs-lookup"><span data-stu-id="08120-113">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="08120-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="08120-114">Example</span></span>  

 <span data-ttu-id="08120-115">Aşağıdaki örnek, iletişim <xref:System.Linq.Enumerable.GroupJoin%2A> başına düşen sipariş sayısını bulmak Için Contact ve SalesOrderHeader tabloları üzerinde bir yapar.</span><span class="sxs-lookup"><span data-stu-id="08120-115">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="08120-116">Her bir kişinin sıra sayısı ve kimlikleri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="08120-116">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="08120-117">Birleştir</span><span class="sxs-lookup"><span data-stu-id="08120-117">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="08120-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="08120-118">Example</span></span>  

 <span data-ttu-id="08120-119">Aşağıdaki örnek, Ağustos 'un ayına ait çevrimiçi siparişleri almak için SalesOrderHeader ve SalesOrderDetail tablolarında bir JOIN uygular.</span><span class="sxs-lookup"><span data-stu-id="08120-119">The following example performs a join over the SalesOrderHeader and SalesOrderDetail tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP L2E Examples#Join](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#join)]
 [!code-vb[DP L2E Examples#Join](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="08120-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08120-120">See also</span></span>

- [<span data-ttu-id="08120-121">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="08120-121">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
