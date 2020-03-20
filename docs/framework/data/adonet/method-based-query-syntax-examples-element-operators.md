---
title: 'Yöntem Tabanlı Sorgu Sözdizimi Örnekleri: Eleman Operatörleri (LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eedf2fbd-f407-4f62-bb1a-c00eb001b1dd
ms.openlocfilehash: e43208d6ae524a1370b936d42508e9c7a7d196e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149513"
---
# <a name="method-based-query-syntax-examples-element-operators-linq-to-dataset"></a><span data-ttu-id="96b2e-102">Yöntem Tabanlı Sorgu Sözdizimi Örnekleri: Eleman Operatörleri (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="96b2e-102">Method-Based Query Syntax Examples: Element Operators (LINQ to DataSet)</span></span>
<span data-ttu-id="96b2e-103">Bu konudaki örnekler, sorgu <xref:System.Linq.Enumerable.First%2A> ifadesi <xref:System.Linq.Enumerable.ElementAt%2A> sözdizimini <xref:System.Data.DataRow> <xref:System.Data.DataSet> kullanarak öğeleri almak için nasıl kullanılacağını ve yöntemleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="96b2e-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="96b2e-104">Bu `FillDataSet` örneklerde kullanılan yöntem, [Veri Kümesine Veri Yükleme'de](loading-data-into-a-dataset.md)belirtilir.</span><span class="sxs-lookup"><span data-stu-id="96b2e-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="96b2e-105">Bu konudaki örnekler AdventureWorks örnek veritabanındaki İletişim, Adres, Ürün, SalesOrderHeader ve SalesOrderDetail tablolarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="96b2e-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="96b2e-106">Bu konudaki örneklerde `using` / `Imports` aşağıdaki ifadeler kullanılır:</span><span class="sxs-lookup"><span data-stu-id="96b2e-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
[!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]

 <span data-ttu-id="96b2e-107">Daha fazla bilgi için [bkz: Visual Studio'da DataSet Project'e LINQ oluşturun.](how-to-create-a-linq-to-dataset-project-in-vs.md)</span><span class="sxs-lookup"><span data-stu-id="96b2e-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="elementat"></a><span data-ttu-id="96b2e-108">Elementat</span><span class="sxs-lookup"><span data-stu-id="96b2e-108">ElementAt</span></span>  
  
### <a name="example"></a><span data-ttu-id="96b2e-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="96b2e-109">Example</span></span>  
 <span data-ttu-id="96b2e-110">Bu örnekte <xref:System.Linq.Enumerable.ElementAt%2A> beşinci adresi almak `PostalCode` için yöntem kullanır == "M4B 1V7".</span><span class="sxs-lookup"><span data-stu-id="96b2e-110">This example uses the <xref:System.Linq.Enumerable.ElementAt%2A> method to retrieve the fifth address where `PostalCode` == "M4B 1V7".</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]
[!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]
  
## <a name="first"></a><span data-ttu-id="96b2e-111">İlk</span><span class="sxs-lookup"><span data-stu-id="96b2e-111">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="96b2e-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="96b2e-112">Example</span></span>  
 <span data-ttu-id="96b2e-113">Bu örnek, <xref:System.Linq.Enumerable.First%2A> ilk adı 'Brooke' olan ilk ilgili kişi dönmek için yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="96b2e-113">This example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is 'Brooke'.</span></span>  
  
[!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]
[!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)]
  
## <a name="see-also"></a><span data-ttu-id="96b2e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96b2e-114">See also</span></span>

- [<span data-ttu-id="96b2e-115">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="96b2e-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="96b2e-116">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="96b2e-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="96b2e-117">Standart Sorgu Operatörlerine Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="96b2e-117">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="96b2e-118">Standart Sorgu Operatörlerine Genel Bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96b2e-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
