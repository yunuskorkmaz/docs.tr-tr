---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Projeksiyon (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48c9f5ed-76bf-4228-ab10-5217bbb295a3
ms.openlocfilehash: 9b8e898ce666b8b443521391eda67318bdf23915
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783009"
---
# <a name="query-expression-syntax-examples-projection--linq-to-dataset"></a><span data-ttu-id="6f661-102">Sorgu İfadesi Söz Dizimi Örnekleri: Projeksiyon (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="6f661-102">Query Expression Syntax Examples: Projection  (LINQ to DataSet)</span></span>
<span data-ttu-id="6f661-103">Bu konudaki örneklerde, sorgu ifadesi söz dizimini kullanarak bir <xref:System.Linq.Enumerable.Select%2A> <xref:System.Data.DataSet> sorgusu <xref:System.Linq.Enumerable.SelectMany%2A> sorgulamak için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6f661-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="6f661-104">Bu örneklerde kullanılan [](loading-data-into-a-dataset.md) yöntemiverileribirverikümesineyüklerken`FillDataSet` belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6f661-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="6f661-105">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6f661-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="6f661-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="6f661-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="6f661-107">Daha fazla bilgi için [nasıl yapılır: Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md)'Da bir LINQ to DataSet projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6f661-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="6f661-108">Seçim</span><span class="sxs-lookup"><span data-stu-id="6f661-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="6f661-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f661-109">Example</span></span>  
 <span data-ttu-id="6f661-110">Bu örnek, <xref:System.Linq.Enumerable.Select%2A> `Product` tablodaki tüm satırları döndürmek ve ürün adlarını göstermek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6f661-110">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="6f661-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f661-111">Example</span></span>  
 <span data-ttu-id="6f661-112">Bu örnekte, <xref:System.Linq.Enumerable.Select%2A> yalnızca ürün adları sırası döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6f661-112">This example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple2)]  
  
## <a name="selectmany"></a><span data-ttu-id="6f661-113">SelectMany</span><span class="sxs-lookup"><span data-stu-id="6f661-113">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="6f661-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f661-114">Example</span></span>  
 <span data-ttu-id="6f661-115">Bu örnek, `From …, …` 500,00 ' den küçük `TotalDue` olan <xref:System.Linq.Enumerable.SelectMany%2A> tüm siparişleri seçmek için (yönteminin eşdeğeri) kullanır.</span><span class="sxs-lookup"><span data-stu-id="6f661-115">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="6f661-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f661-116">Example</span></span>  
 <span data-ttu-id="6f661-117">Bu örnek, `From …, …` 1 Ekim 2002 veya sonraki <xref:System.Linq.Enumerable.SelectMany%2A> bir sürümde siparişin yapıldığı tüm siparişleri seçmek için (yönteminin eşdeğeri) kullanır.</span><span class="sxs-lookup"><span data-stu-id="6f661-117">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="6f661-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f661-118">Example</span></span>  
 <span data-ttu-id="6f661-119">Bu örnek, sipariş `From …, …` toplamı 10000,00 ' den büyük <xref:System.Linq.Enumerable.SelectMany%2A> olan tüm siparişleri seçmek için bir (yönteminin eşdeğeri) kullanır ve toplamın iki kez istenmesine `From` engel olmak için atamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="6f661-119">This example uses a `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="6f661-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f661-120">See also</span></span>

- [<span data-ttu-id="6f661-121">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="6f661-121">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="6f661-122">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="6f661-122">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="6f661-123">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="6f661-123">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="6f661-124">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f661-124">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
