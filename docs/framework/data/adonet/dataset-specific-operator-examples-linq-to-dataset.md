---
title: DataSet'e özgü işleç örnekleri (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fdd64af-6ad0-46cd-91c8-dbe26620eeb1
ms.openlocfilehash: 27a48b7ffe5466c52f19f15cf3c1a6cb558028b2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097349"
---
# <a name="dataset-specific-operator-examples-linq-to-dataset"></a><span data-ttu-id="c0646-102">DataSet'e özgü işleç örnekleri (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="c0646-102">DataSet-Specific Operator Examples (LINQ to DataSet)</span></span>
<span data-ttu-id="c0646-103">Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yöntemi ve <xref:System.Data.DataRowComparer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c0646-103">The examples in this topic demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
 <span data-ttu-id="c0646-104">`FillDataSet` Bu örneklerde kullanılan yöntemi belirtilen [verileri bir DataSet içine Yükleniyor](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="c0646-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="c0646-105">Bu konudaki örnekler AdventureWorks örnek veritabanındaki kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="c0646-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="c0646-106">Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="c0646-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="c0646-107">Daha fazla bilgi için [nasıl yapılır: Visual Studio'da bir LINQ to DataSet projesi oluşturma](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="c0646-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="copytodatatable"></a><span data-ttu-id="c0646-108">CopyToDataTable</span><span class="sxs-lookup"><span data-stu-id="c0646-108">CopyToDataTable</span></span>  
  
### <a name="example"></a><span data-ttu-id="c0646-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0646-109">Example</span></span>  
 <span data-ttu-id="c0646-110">Bu örnekte yükleyen bir <xref:System.Data.DataTable> kullanarak sorgu sonuçları ile <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c0646-110">This example loads a <xref:System.Data.DataTable> with query results by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#loaddatatablewithqueryresults)]
 [!code-vb[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#loaddatatablewithqueryresults)]  
  
## <a name="datarowcomparer"></a><span data-ttu-id="c0646-111">DataRowComparer</span><span class="sxs-lookup"><span data-stu-id="c0646-111">DataRowComparer</span></span>  
  
### <a name="example"></a><span data-ttu-id="c0646-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0646-112">Example</span></span>  
 <span data-ttu-id="c0646-113">Bu örnek iki farklı veri satırları kullanarak karşılaştırır <xref:System.Data.DataRowComparer>.</span><span class="sxs-lookup"><span data-stu-id="c0646-113">This example compares two different data rows by using <xref:System.Data.DataRowComparer>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CompareDifferentDataRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#comparedifferentdatarows)]  
  
## <a name="see-also"></a><span data-ttu-id="c0646-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0646-114">See also</span></span>

- [<span data-ttu-id="c0646-115">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="c0646-115">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="c0646-116">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="c0646-116">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
