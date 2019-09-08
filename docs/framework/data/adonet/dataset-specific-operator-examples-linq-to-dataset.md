---
title: DataSet 'e özgü Işleç örnekleri (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fdd64af-6ad0-46cd-91c8-dbe26620eeb1
ms.openlocfilehash: 6a9dc82e0bb065b455c0208daaf2d28a74cd7e34
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784206"
---
# <a name="dataset-specific-operator-examples-linq-to-dataset"></a><span data-ttu-id="5e961-102">DataSet 'e özgü Işleç örnekleri (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="5e961-102">DataSet-Specific Operator Examples (LINQ to DataSet)</span></span>
<span data-ttu-id="5e961-103">Bu konudaki örneklerde, <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yönteminin <xref:System.Data.DataRowComparer> ve sınıfının nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5e961-103">The examples in this topic demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
 <span data-ttu-id="5e961-104">Bu örneklerde kullanılan [](loading-data-into-a-dataset.md) yöntemiverileribirverikümesineyüklerken`FillDataSet` belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5e961-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="5e961-105">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5e961-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="5e961-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="5e961-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="5e961-107">Daha fazla bilgi için [nasıl yapılır: Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md)'Da bir LINQ to DataSet projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5e961-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="copytodatatable"></a><span data-ttu-id="5e961-108">CopyToDataTable</span><span class="sxs-lookup"><span data-stu-id="5e961-108">CopyToDataTable</span></span>  
  
### <a name="example"></a><span data-ttu-id="5e961-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e961-109">Example</span></span>  
 <span data-ttu-id="5e961-110">Bu örnek, <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> yöntemini <xref:System.Data.DataTable> kullanarak bir sorgu sonuçlarıyla bir yükler.</span><span class="sxs-lookup"><span data-stu-id="5e961-110">This example loads a <xref:System.Data.DataTable> with query results by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#loaddatatablewithqueryresults)]
 [!code-vb[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#loaddatatablewithqueryresults)]  
  
## <a name="datarowcomparer"></a><span data-ttu-id="5e961-111">DataRowComparer</span><span class="sxs-lookup"><span data-stu-id="5e961-111">DataRowComparer</span></span>  
  
### <a name="example"></a><span data-ttu-id="5e961-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e961-112">Example</span></span>  
 <span data-ttu-id="5e961-113">Bu örnek, kullanarak <xref:System.Data.DataRowComparer>iki farklı veri satırını karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="5e961-113">This example compares two different data rows by using <xref:System.Data.DataRowComparer>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CompareDifferentDataRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#comparedifferentdatarows)]  
  
## <a name="see-also"></a><span data-ttu-id="5e961-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e961-114">See also</span></span>

- [<span data-ttu-id="5e961-115">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="5e961-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="5e961-116">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="5e961-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
