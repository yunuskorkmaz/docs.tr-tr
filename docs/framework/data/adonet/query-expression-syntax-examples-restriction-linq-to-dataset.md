---
title: 'Sorgu İfadesi Sözdizimi Örnekleri: Kısıtlama (DATASet için LINQ)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1daf42c2-c9f4-4cda-b291-7641b9c6d3fe
ms.openlocfilehash: 6ec4eac6c0fb2d044e429e88d50c619aa38de4b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149199"
---
# <a name="query-expression-syntax-examples-restriction-linq-to-dataset"></a><span data-ttu-id="a4ea3-102">Sorgu İfadesi Sözdizimi Örnekleri: Kısıtlama (DATASet için LINQ)</span><span class="sxs-lookup"><span data-stu-id="a4ea3-102">Query Expression Syntax Examples: Restriction (LINQ to DataSet)</span></span>
<span data-ttu-id="a4ea3-103">Bu konudaki örnekler, sorgu <xref:System.Linq.Enumerable.Where%2A> ifadesi sözdizimini kullanarak bir <xref:System.Data.DataSet> sorgu yöntemini nasıl kullanacağımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="a4ea3-104">Bu `FillDataSet` örneklerde kullanılan yöntem, [Veri Kümesine Veri Yükleme'de](loading-data-into-a-dataset.md)belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="a4ea3-105">Bu konudaki örnekler AdventureWorks örnek veritabanındaki İletişim, Adres, Ürün, SalesOrderHeader ve SalesOrderDetail tablolarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="a4ea3-106">Bu konudaki örneklerde `using` / `Imports` aşağıdaki ifadeler kullanılır:</span><span class="sxs-lookup"><span data-stu-id="a4ea3-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
[!code-csharp[DP LINQ to DataSetExamples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
  
 <span data-ttu-id="a4ea3-107">Daha fazla bilgi için [bkz: Visual Studio'da DataSet Project'e LINQ oluşturun.](how-to-create-a-linq-to-dataset-project-in-vs.md)</span><span class="sxs-lookup"><span data-stu-id="a4ea3-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="where"></a><span data-ttu-id="a4ea3-108">Konum</span><span class="sxs-lookup"><span data-stu-id="a4ea3-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="a4ea3-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4ea3-109">Example</span></span>  
 <span data-ttu-id="a4ea3-110">Bu örnek tüm çevrimiçi siparişleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-110">This example returns all online orders.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)]
  
### <a name="example"></a><span data-ttu-id="a4ea3-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4ea3-111">Example</span></span>  
 <span data-ttu-id="a4ea3-112">Bu örnek, sipariş miktarının 2'den büyük ve 6'dan küçük olduğu siparişleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-112">This example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where2)]  
 [!code-vb[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where2)]
  
### <a name="example"></a><span data-ttu-id="a4ea3-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4ea3-113">Example</span></span>  
 <span data-ttu-id="a4ea3-114">Bu örnek, tüm kırmızı renkli ürünleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-114">This example returns all red colored products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]  
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]
  
### <a name="example"></a><span data-ttu-id="a4ea3-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="a4ea3-115">Example</span></span>  
 <span data-ttu-id="a4ea3-116">Bu örnek, <xref:System.Linq.Enumerable.Where%2A> 1 Aralık 2002'den sonra yapılan siparişleri <xref:System.Data.DataRow.GetChildRows%2A> bulmak için yöntemi kullanır ve sonra her siparişiçin ayrıntıları almak için yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-116">This example uses the <xref:System.Linq.Enumerable.Where%2A> method to find orders that were made after December 1, 2002 and then uses the <xref:System.Data.DataRow.GetChildRows%2A> method to get the details for each order.</span></span>  
  
 [!code-csharp[DP LINQ to DataSetExamples#WhereDrillDown](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#wheredrilldown)]
 [!code-vb[DP LINQ to DataSet Examples#WhereDrillDown](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#wheredrilldown)]  
  
## <a name="see-also"></a><span data-ttu-id="a4ea3-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4ea3-117">See also</span></span>

- [<span data-ttu-id="a4ea3-118">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="a4ea3-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="a4ea3-119">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="a4ea3-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="a4ea3-120">Standart Sorgu Operatörlerine Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="a4ea3-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="a4ea3-121">Standart Sorgu Operatörlerine Genel Bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4ea3-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
