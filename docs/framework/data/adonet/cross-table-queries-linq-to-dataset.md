---
title: "Geçici Tablo Sorgu (LINQ-DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0ede3cef32fc752239dfbed6a05adbdb1cc5bfbe
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="cross-table-queries-linq-to-dataset"></a><span data-ttu-id="42967-102">Geçici Tablo Sorgu (LINQ-DataSet)</span><span class="sxs-lookup"><span data-stu-id="42967-102">Cross-Table Queries (LINQ to DataSet)</span></span>
<span data-ttu-id="42967-103">Tek bir tablo sorgulama yanı sıra, geçici tablo sorguları da gerçekleştirebilirsiniz [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="42967-103">In addition to querying a single table, you can also perform cross-table queries in [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="42967-104">Bu kullanılarak yapılır bir *birleştirme*.</span><span class="sxs-lookup"><span data-stu-id="42967-104">This is done by using a *join*.</span></span> <span data-ttu-id="42967-105">Bir birleştirme nesnelerin bir veri kaynağı bir ürün gibi başka bir veri kaynağındaki ortak bir özniteliği paylaşan veya kimliği başvurun nesnelerle ilişkidir</span><span class="sxs-lookup"><span data-stu-id="42967-105">A join is the association of objects in one data source with objects that share a common attribute in another data source, such as a product or contact ID.</span></span> <span data-ttu-id="42967-106">Nesne odaklı programlama içindeki nesneleri arasındaki ilişkiler her nesneyi başka bir nesneye başvuruda bulunan bir üye içerdiğinden gitmek görece kolaydır.</span><span class="sxs-lookup"><span data-stu-id="42967-106">In object-oriented programming, relationships between objects are relatively easy to navigate because each object has a member that references another object.</span></span> <span data-ttu-id="42967-107">Dış veritabanı tablolarında ancak ilişkilerinde gezinme kadar basit değildir.</span><span class="sxs-lookup"><span data-stu-id="42967-107">In external database tables, however, navigating relationships is not as straightforward.</span></span> <span data-ttu-id="42967-108">Veritabanı tabloları yerleşik ilişkileri içermez.</span><span class="sxs-lookup"><span data-stu-id="42967-108">Database tables do not contain built-in relationships.</span></span> <span data-ttu-id="42967-109">Bu durumlarda, birleştirme işlemi her kaynak öğelerinden eşleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="42967-109">In these cases, the join operation can be used to match elements from each source.</span></span> <span data-ttu-id="42967-110">Örneğin, ürün bilgilerini ve satış bilgilerini içeren iki tablo verildiğinde, satış bilgilerini ve ürünleri aynı sipariş için eşleştirilecek bir birleştirme işlemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42967-110">For example, given two tables that contain product information and sales information, you could use a join operation to match sales information and products for the same sales order.</span></span>  
  
 <span data-ttu-id="42967-111">[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] Framework sağlayan iki birleştirme işleçleri <xref:System.Linq.Enumerable.Join%2A> ve <xref:System.Linq.Enumerable.GroupJoin%2A>.</span><span class="sxs-lookup"><span data-stu-id="42967-111">The [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] framework provides two join operators, <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="42967-112">Bu işleçlere gerçekleştirmek *benzer birleşimler*: başka bir deyişle, iki veri eşleşen birleştirmeler kaynakları yalnızca kendi anahtarları eşit olduğunda.</span><span class="sxs-lookup"><span data-stu-id="42967-112">These operators perform *equi-joins*: that is, joins that match two data sources only when their keys are equal.</span></span> <span data-ttu-id="42967-113">(Buna karşın [!INCLUDE[tsql](../../../../includes/tsql-md.md)] destekler birleştirme işleçleri dışında `equals`, gibi `less than` işleci.)</span><span class="sxs-lookup"><span data-stu-id="42967-113">(By contrast, [!INCLUDE[tsql](../../../../includes/tsql-md.md)] supports join operators other than `equals`, such as the `less than` operator.)</span></span>  
  
 <span data-ttu-id="42967-114">İlişkisel veritabanı terimleriyle <xref:System.Linq.Enumerable.Join%2A> bir iç birleştirme uygular.</span><span class="sxs-lookup"><span data-stu-id="42967-114">In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join.</span></span> <span data-ttu-id="42967-115">Bir iç birleştirme birleşim türünde içinde hangi ters veri kümesindeki bir eşleşme olan nesneler döndürülür.</span><span class="sxs-lookup"><span data-stu-id="42967-115">An inner join is a type of join in which only those objects that have a match in the opposite data set are returned.</span></span>  
  
 <span data-ttu-id="42967-116"><xref:System.Linq.Enumerable.GroupJoin%2A> Operatörleri ilişkisel veritabanı bağlamında doğrudan bir eşdeğer sahiptir; İç birleşimler sol dış birleştirmeler ve bir alt kümesi uygulayan.</span><span class="sxs-lookup"><span data-stu-id="42967-116">The <xref:System.Linq.Enumerable.GroupJoin%2A> operators have no direct equivalent in relational database terms; they implement a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="42967-117">Bu ikinci koleksiyonda ilişkili öğe olsa bile bir sol dış birleşim her öğesinin ilk (soldaki) koleksiyonu döndüren bir birleşim ' dir.</span><span class="sxs-lookup"><span data-stu-id="42967-117">A left outer join is a join that returns each element of the first (left) collection, even if it has no correlated elements in the second collection.</span></span>  
  
 <span data-ttu-id="42967-118">Birleşimler hakkında daha fazla bilgi için bkz: [birleştirme işlemleri](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107).</span><span class="sxs-lookup"><span data-stu-id="42967-118">For more information about joins, see [Join Operations](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107).</span></span>  
  
## <a name="example"></a><span data-ttu-id="42967-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="42967-119">Example</span></span>  
 <span data-ttu-id="42967-120">Aşağıdaki örnek, geleneksel bir birleştirme gerçekleştirir `SalesOrderHeader` ve `SalesOrderDetail` Ağustos, month çevrimiçi olarak sipariş edinme AdventureWorks örnek veritabanı tablolarından.</span><span class="sxs-lookup"><span data-stu-id="42967-120">The following example performs a traditional join of the `SalesOrderHeader` and `SalesOrderDetail` tables from the AdventureWorks sample database to obtain online orders from the month of August.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="42967-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="42967-121">See Also</span></span>  
 [<span data-ttu-id="42967-122">DataSet’leri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="42967-122">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [<span data-ttu-id="42967-123">Tek Tablolu Sorgular</span><span class="sxs-lookup"><span data-stu-id="42967-123">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 [<span data-ttu-id="42967-124">Türü Belirtilmiş DataSet’leri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="42967-124">Querying Typed DataSets</span></span>](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 [<span data-ttu-id="42967-125">Birleştirme İşlemleri</span><span class="sxs-lookup"><span data-stu-id="42967-125">Join Operations</span></span>](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107)  
 [<span data-ttu-id="42967-126">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="42967-126">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
