---
title: 'Sorgu Ifadesi söz dizimi örnekleri: projeksiyon (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48c9f5ed-76bf-4228-ab10-5217bbb295a3
ms.openlocfilehash: e003c4356c2ab32814ac7a76ce008e21fb34192e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183175"
---
# <a name="query-expression-syntax-examples-projection--linq-to-dataset"></a><span data-ttu-id="eb04a-102">Sorgu Ifadesi söz dizimi örnekleri: projeksiyon (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="eb04a-102">Query Expression Syntax Examples: Projection  (LINQ to DataSet)</span></span>

<span data-ttu-id="eb04a-103">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.Select%2A> <xref:System.Linq.Enumerable.SelectMany%2A> <xref:System.Data.DataSet> sorgu ifadesi söz dizimini kullanarak bir sorgusu sorgulamak için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="eb04a-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="eb04a-104">`FillDataSet`Bu örneklerde kullanılan yöntemi [verileri bir veri kümesine yüklerken](loading-data-into-a-dataset.md)belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="eb04a-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="eb04a-105">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eb04a-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="eb04a-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="eb04a-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="eb04a-107">Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="eb04a-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="eb04a-108">Şunu seçin:</span><span class="sxs-lookup"><span data-stu-id="eb04a-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="eb04a-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb04a-109">Example</span></span>  

 <span data-ttu-id="eb04a-110">Bu örnek, <xref:System.Linq.Enumerable.Select%2A> tablodaki tüm satırları döndürmek `Product` ve ürün adlarını göstermek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="eb04a-110">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="eb04a-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb04a-111">Example</span></span>  

 <span data-ttu-id="eb04a-112">Bu örnekte <xref:System.Linq.Enumerable.Select%2A> , yalnızca ürün adları sırası döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb04a-112">This example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple2)]  
  
## <a name="selectmany"></a><span data-ttu-id="eb04a-113">SelectMany</span><span class="sxs-lookup"><span data-stu-id="eb04a-113">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="eb04a-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb04a-114">Example</span></span>  

 <span data-ttu-id="eb04a-115">Bu örnek, `From …, …` <xref:System.Linq.Enumerable.SelectMany%2A> 500,00 ' den küçük olan tüm siparişleri seçmek için (yönteminin eşdeğeri) kullanır `TotalDue` .</span><span class="sxs-lookup"><span data-stu-id="eb04a-115">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="eb04a-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb04a-116">Example</span></span>  

 <span data-ttu-id="eb04a-117">Bu örnek, `From …, …` <xref:System.Linq.Enumerable.SelectMany%2A> 1 Ekim 2002 veya sonraki bir sürümde siparişin yapıldığı tüm siparişleri seçmek için (yönteminin eşdeğeri) kullanır.</span><span class="sxs-lookup"><span data-stu-id="eb04a-117">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="eb04a-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb04a-118">Example</span></span>  

 <span data-ttu-id="eb04a-119">Bu örnek, `From …, …` <xref:System.Linq.Enumerable.SelectMany%2A> sipariş toplamı 10000,00 ' den büyük olan tüm siparişleri seçmek için bir (yönteminin eşdeğeri) kullanır ve `From` toplamın iki kez istenmesine engel olmak için atamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="eb04a-119">This example uses a `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="eb04a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb04a-120">See also</span></span>

- [<span data-ttu-id="eb04a-121">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="eb04a-121">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="eb04a-122">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="eb04a-122">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="eb04a-123">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="eb04a-123">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="eb04a-124">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb04a-124">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
