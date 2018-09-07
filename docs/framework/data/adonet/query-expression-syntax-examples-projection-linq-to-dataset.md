---
title: 'Sorgu ifadesi söz dizimi örnekleri: Projeksiyon (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48c9f5ed-76bf-4228-ab10-5217bbb295a3
ms.openlocfilehash: 92e013647b4f4b6ba14d46add24d5d71a6875bb0
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44075741"
---
# <a name="query-expression-syntax-examples-projection--linq-to-dataset"></a><span data-ttu-id="0a219-102">Sorgu ifadesi söz dizimi örnekleri: Projeksiyon (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="0a219-102">Query Expression Syntax Examples: Projection  (LINQ to DataSet)</span></span>
<span data-ttu-id="0a219-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.Select%2A> ve <xref:System.Linq.Enumerable.SelectMany%2A> sorgulamak için yöntemleri bir <xref:System.Data.DataSet> sorgu ifadesi söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="0a219-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="0a219-104">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [verileri bir DataSet içine Yükleniyor](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="0a219-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="0a219-105">Bu konudaki örnekler AdventureWorks örnek veritabanındaki kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0a219-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0a219-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="0a219-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="0a219-107">Daha fazla bilgi için [nasıl yapılır: bir LINQ to DataSet proje Visual Studio'da oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="0a219-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="0a219-108">Seçim</span><span class="sxs-lookup"><span data-stu-id="0a219-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="0a219-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a219-109">Example</span></span>  
 <span data-ttu-id="0a219-110">Bu örnekte <xref:System.Linq.Enumerable.Select%2A> bulunan tüm satırlar döndürülecek yöntemi `Product` tablo ve ürün adlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0a219-110">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="0a219-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a219-111">Example</span></span>  
 <span data-ttu-id="0a219-112">Bu örnekte <xref:System.Linq.Enumerable.Select%2A> yalnızca ürün adlarını bir dizisini döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="0a219-112">This example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple2)]  
  
## <a name="selectmany"></a><span data-ttu-id="0a219-113">SelectMany</span><span class="sxs-lookup"><span data-stu-id="0a219-113">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="0a219-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a219-114">Example</span></span>  
 <span data-ttu-id="0a219-115">Bu örnekte `From …, …` (denk <xref:System.Linq.Enumerable.SelectMany%2A> yöntemi) tümünü seçmek için nereye siparişleri `TotalDue` kısa da 500,00 olduğu.</span><span class="sxs-lookup"><span data-stu-id="0a219-115">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="0a219-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a219-116">Example</span></span>  
 <span data-ttu-id="0a219-117">Bu örnekte `From …, …` (denk <xref:System.Linq.Enumerable.SelectMany%2A> yöntemi) burada sırasını yapıldı 1 Ekim 2002 veya daha sonra tüm siparişleri seçin.</span><span class="sxs-lookup"><span data-stu-id="0a219-117">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="0a219-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a219-118">Example</span></span>  
 <span data-ttu-id="0a219-119">Bu örnekte bir `From …, …` (denk <xref:System.Linq.Enumerable.SelectMany%2A> yöntemi) tüm siparişleri sipariş toplam olduğu 10000.00 kullanan'dan büyük ve seçmek için `From` toplam iki kez isteyen önlemek için atama.</span><span class="sxs-lookup"><span data-stu-id="0a219-119">This example uses a `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="0a219-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0a219-120">See Also</span></span>  
 [<span data-ttu-id="0a219-121">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="0a219-121">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="0a219-122">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="0a219-122">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [<span data-ttu-id="0a219-123">Standart Sorgu İşleçlerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0a219-123">Standard Query Operators Overview</span></span>](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
