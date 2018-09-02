---
title: 'Sorgu ifadesi söz dizimi örnekleri: Birleşim işleçleri (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f4d86667-3392-470d-a076-5ca6cbb660f6
ms.openlocfilehash: 462d857c231c0222517cbdedfbe3ae148e66e693
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43392929"
---
# <a name="query-expression-syntax-examples-join-operators-linq-to-dataset"></a><span data-ttu-id="2e670-102">Sorgu ifadesi söz dizimi örnekleri: Birleşim işleçleri (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="2e670-102">Query Expression Syntax Examples: Join Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="2e670-103">Birleştirme, birbiriyle gezilebilir hiçbir ilişki ilişkisel veritabanı tabloları gibi veri kaynakları hedef sorgularda önemli bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="2e670-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="2e670-104">İki veri kaynaklarının bir birleştirme nesnelerin bir veri kaynağı ile bir veri kaynağındaki ortak bir özniteliği paylaşan nesnelerin ilişkidir.</span><span class="sxs-lookup"><span data-stu-id="2e670-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="2e670-105">Daha fazla bilgi için [standart sorgu işleçlerine genel bakış](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="2e670-105">For more information, see [Standard Query Operators Overview](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
 <span data-ttu-id="2e670-106">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.GroupJoin%2A> ve <xref:System.Linq.Enumerable.Join%2A> sorgulamak için yöntemleri bir <xref:System.Data.DataSet> sorgu ifadesi söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="2e670-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="2e670-107">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [verileri bir DataSet içine Yükleniyor](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="2e670-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="2e670-108">Bu konudaki örnekler AdventureWorks örnek veritabanındaki kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="2e670-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="2e670-109">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="2e670-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="2e670-110">Daha fazla bilgi için [nasıl yapılır: bir LINQ to DataSet proje Visual Studio'da oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="2e670-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="groupjoin"></a><span data-ttu-id="2e670-111">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="2e670-111">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="2e670-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e670-112">Example</span></span>  
 <span data-ttu-id="2e670-113">Bu örnek gerçekleştiren bir <xref:System.Linq.Enumerable.GroupJoin%2A> üzerinden `SalesOrderHeader` ve `SalesOrderDetail` tabloların her müşteri siparişleri sayısını bulur.</span><span class="sxs-lookup"><span data-stu-id="2e670-113">This example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the `SalesOrderHeader` and `SalesOrderDetail` tables to find the number of orders per customer.</span></span> <span data-ttu-id="2e670-114">Grup birleştirme her öğe ilk (soldaki) veri kaynağının diğer veri kaynağında ilişkili hiçbir öğe olsa bile, döndüren bir sol dış birleşim eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="2e670-114">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="2e670-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e670-115">Example</span></span>  
 <span data-ttu-id="2e670-116">Bu örnekte gerçekleştiren bir <xref:System.Linq.Enumerable.GroupJoin%2A> üzerinden `Contact` ve `SalesOrderHeader` tablolar.</span><span class="sxs-lookup"><span data-stu-id="2e670-116">This example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the `Contact` and `SalesOrderHeader` tables.</span></span> <span data-ttu-id="2e670-117">Grup birleştirme her öğe ilk (soldaki) veri kaynağının diğer veri kaynağında ilişkili hiçbir öğe olsa bile, döndüren bir sol dış birleşim eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="2e670-117">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="2e670-118">Birleştirme</span><span class="sxs-lookup"><span data-stu-id="2e670-118">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="2e670-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e670-119">Example</span></span>  
 <span data-ttu-id="2e670-120">Bu örnek üzerinde birleştirme gerçekleştirir `SalesOrderHeader` ve `SalesOrderDetail` çevrimiçi siparişler Ağustos ay almak için tablolar.</span><span class="sxs-lookup"><span data-stu-id="2e670-120">This example performs a join over the `SalesOrderHeader` and `SalesOrderDetail` tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="2e670-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2e670-121">See Also</span></span>  
 [<span data-ttu-id="2e670-122">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="2e670-122">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="2e670-123">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="2e670-123">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="2e670-124">Standart Sorgu İşleçlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2e670-124">Standard Query Operators Overview</span></span>](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
