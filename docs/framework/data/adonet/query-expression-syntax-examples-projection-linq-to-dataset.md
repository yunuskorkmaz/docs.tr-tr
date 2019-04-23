---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Yansıtma (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48c9f5ed-76bf-4228-ab10-5217bbb295a3
ms.openlocfilehash: 3bd7934cef03df391c1871b8499f911a023d7d3b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097596"
---
# <a name="query-expression-syntax-examples-projection--linq-to-dataset"></a><span data-ttu-id="5e077-102">Sorgu İfadesi Söz Dizimi Örnekleri: Yansıtma (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="5e077-102">Query Expression Syntax Examples: Projection  (LINQ to DataSet)</span></span>
<span data-ttu-id="5e077-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Select%2A> ve <xref:System.Linq.Enumerable.SelectMany%2A> sorgulamak için yöntemleri bir <xref:System.Data.DataSet> sorgu ifadesi söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="5e077-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="5e077-104">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [verileri bir DataSet içine Yükleniyor](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="5e077-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="5e077-105">Bu konudaki örnekler AdventureWorks örnek veritabanındaki kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="5e077-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="5e077-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="5e077-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="5e077-107">Daha fazla bilgi için [nasıl yapılır: Visual Studio'da bir LINQ to DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="5e077-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="5e077-108">Seçim</span><span class="sxs-lookup"><span data-stu-id="5e077-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="5e077-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e077-109">Example</span></span>  
 <span data-ttu-id="5e077-110">Bu örnekte <xref:System.Linq.Enumerable.Select%2A> bulunan tüm satırlar döndürülecek yöntemi `Product` tablo ve ürün adlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5e077-110">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="5e077-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e077-111">Example</span></span>  
 <span data-ttu-id="5e077-112">Bu örnekte <xref:System.Linq.Enumerable.Select%2A> yalnızca ürün adlarını bir dizisini döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="5e077-112">This example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple2)]  
  
## <a name="selectmany"></a><span data-ttu-id="5e077-113">SelectMany</span><span class="sxs-lookup"><span data-stu-id="5e077-113">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="5e077-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e077-114">Example</span></span>  
 <span data-ttu-id="5e077-115">Bu örnekte `From …, …` (denk <xref:System.Linq.Enumerable.SelectMany%2A> yöntemi) tümünü seçmek için nereye siparişleri `TotalDue` kısa da 500,00 olduğu.</span><span class="sxs-lookup"><span data-stu-id="5e077-115">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="5e077-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e077-116">Example</span></span>  
 <span data-ttu-id="5e077-117">Bu örnekte `From …, …` (denk <xref:System.Linq.Enumerable.SelectMany%2A> yöntemi) burada sırasını yapıldı 1 Ekim 2002 veya daha sonra tüm siparişleri seçin.</span><span class="sxs-lookup"><span data-stu-id="5e077-117">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="5e077-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e077-118">Example</span></span>  
 <span data-ttu-id="5e077-119">Bu örnekte bir `From …, …` (denk <xref:System.Linq.Enumerable.SelectMany%2A> yöntemi) tüm siparişleri sipariş toplam olduğu 10000.00 kullanan'dan büyük ve seçmek için `From` toplam iki kez isteyen önlemek için atama.</span><span class="sxs-lookup"><span data-stu-id="5e077-119">This example uses a `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="5e077-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e077-120">See also</span></span>

- [<span data-ttu-id="5e077-121">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="5e077-121">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="5e077-122">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="5e077-122">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
- [<span data-ttu-id="5e077-123">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="5e077-123">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="5e077-124">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e077-124">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
