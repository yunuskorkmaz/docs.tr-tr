---
title: 'Sorgu Ifadesi söz dizimi örnekleri: öğe Işleçleri (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ca392dda-16e3-45c7-8d87-12d8d4ee0578
ms.openlocfilehash: 1d722f642941c9ec37cd6304dfb428fd621a314a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189116"
---
# <a name="query-expression-syntax-examples-element-operators-linq-to-dataset"></a><span data-ttu-id="9ccf7-102">Sorgu Ifadesi söz dizimi örnekleri: öğe Işleçleri (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="9ccf7-102">Query Expression Syntax Examples: Element Operators (LINQ to DataSet)</span></span>

<span data-ttu-id="9ccf7-103">Bu konudaki örneklerde, <xref:System.Linq.Enumerable.First%2A> <xref:System.Linq.Enumerable.ElementAt%2A> <xref:System.Data.DataRow> <xref:System.Data.DataSet> sorgu ifadesi söz dizimini kullanarak bir öğesinden öğeleri almak için ve yöntemlerinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9ccf7-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="9ccf7-104">`FillDataSet`Bu örneklerde kullanılan yöntemi [verileri bir veri kümesine yüklerken](loading-data-into-a-dataset.md)belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9ccf7-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="9ccf7-105">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9ccf7-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="9ccf7-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="9ccf7-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="9ccf7-107">Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9ccf7-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="elementat"></a><span data-ttu-id="9ccf7-108">ElementAt</span><span class="sxs-lookup"><span data-stu-id="9ccf7-108">ElementAt</span></span>  
  
### <a name="example"></a><span data-ttu-id="9ccf7-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="9ccf7-109">Example</span></span>  

 <span data-ttu-id="9ccf7-110">Bu örnek, <xref:System.Linq.Enumerable.ElementAt%2A> `PostalCode` = = "M4B 1V7" Where beşinci adresini almak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9ccf7-110">This example uses the <xref:System.Linq.Enumerable.ElementAt%2A> method to retrieve the fifth address where `PostalCode` == "M4B 1V7".</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]
 [!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]  
  
## <a name="first"></a><span data-ttu-id="9ccf7-111">Birinci</span><span class="sxs-lookup"><span data-stu-id="9ccf7-111">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="9ccf7-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="9ccf7-112">Example</span></span>  

 <span data-ttu-id="9ccf7-113">Bu örnek, <xref:System.Linq.Enumerable.First%2A> ilk adı ' Brooke ' olan ilk kişiyi döndürmek için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9ccf7-113">This example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is 'Brooke'.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="9ccf7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ccf7-114">See also</span></span>

- [<span data-ttu-id="9ccf7-115">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="9ccf7-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="9ccf7-116">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="9ccf7-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="9ccf7-117">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="9ccf7-117">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="9ccf7-118">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ccf7-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
