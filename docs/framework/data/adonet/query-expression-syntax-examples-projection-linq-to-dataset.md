---
title: "Sorgu ifade sözdizimi örnekleri: Projeksiyon (LINQ-DataSet)"
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
ms.assetid: 48c9f5ed-76bf-4228-ab10-5217bbb295a3
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9aab649eebdccc480f4681da5e3d9499cb62eab6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="query-expression-syntax-examples-projection--linq-to-dataset"></a><span data-ttu-id="7c998-102">Sorgu ifade sözdizimi örnekleri: Projeksiyon (LINQ-DataSet)</span><span class="sxs-lookup"><span data-stu-id="7c998-102">Query Expression Syntax Examples: Projection  (LINQ to DataSet)</span></span>
<span data-ttu-id="7c998-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Select%2A> ve <xref:System.Linq.Enumerable.SelectMany%2A> sorgulamak için yöntemleri bir <xref:System.Data.DataSet> sorgu ifade sözdizimi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="7c998-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="7c998-104">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [yüklenirken veri içine bir veri kümesi](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="7c998-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="7c998-105">Bu konudaki örnekler kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını AdventureWorks örnek veritabanını kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c998-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="7c998-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` deyimleri:</span><span class="sxs-lookup"><span data-stu-id="7c998-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="7c998-107">Daha fazla bilgi için bkz: [nasıl yapılır: bir LINQ to Visual Studio'da DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="7c998-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="7c998-108">Seçim</span><span class="sxs-lookup"><span data-stu-id="7c998-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="7c998-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="7c998-109">Example</span></span>  
 <span data-ttu-id="7c998-110">Bu örnekte <xref:System.Linq.Enumerable.Select%2A> bulunan tüm satırlar döndürülecek yöntemi `Product` tablo ve ürün adlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7c998-110">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="7c998-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="7c998-111">Example</span></span>  
 <span data-ttu-id="7c998-112">Bu örnekte <xref:System.Linq.Enumerable.Select%2A> yalnızca ürün adlarını bir dizi dönün.</span><span class="sxs-lookup"><span data-stu-id="7c998-112">This example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple2)]  
  
## <a name="selectmany"></a><span data-ttu-id="7c998-113">SelectMany</span><span class="sxs-lookup"><span data-stu-id="7c998-113">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="7c998-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="7c998-114">Example</span></span>  
 <span data-ttu-id="7c998-115">Bu örnek kullanır `From …, …` (denk <xref:System.Linq.Enumerable.SelectMany%2A> yöntemi) tümünü seçmek için nereye siparişleri `TotalDue` değerinden 500,00 değil.</span><span class="sxs-lookup"><span data-stu-id="7c998-115">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="7c998-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="7c998-116">Example</span></span>  
 <span data-ttu-id="7c998-117">Bu örnekte `From …, …` (denk <xref:System.Linq.Enumerable.SelectMany%2A> yöntemi) burada sırasını yapıldı 1 Ekim 2002 veya sonraki sürümlerde tüm siparişleri seçmek için.</span><span class="sxs-lookup"><span data-stu-id="7c998-117">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="7c998-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="7c998-118">Example</span></span>  
 <span data-ttu-id="7c998-119">Bu örnekte bir `From …, …` (denk <xref:System.Linq.Enumerable.SelectMany%2A> yöntemi) sipariş toplam olduğu 10000.00 kullandığı'dan büyük ve tüm siparişleri seçmek için `From` toplam iki kez isteyen önlemek için atama.</span><span class="sxs-lookup"><span data-stu-id="7c998-119">This example uses a `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="7c998-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7c998-120">See Also</span></span>  
 [<span data-ttu-id="7c998-121">Bir veri kümesine veri yükleme</span><span class="sxs-lookup"><span data-stu-id="7c998-121">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="7c998-122">LINQ-DataSet örnekleri</span><span class="sxs-lookup"><span data-stu-id="7c998-122">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="7c998-123">Standart sorgu işleçlerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="7c998-123">Standard Query Operators Overview</span></span>](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
