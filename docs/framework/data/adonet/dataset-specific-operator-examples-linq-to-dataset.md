---
title: DataSet 'e özgü Işleç örnekleri (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fdd64af-6ad0-46cd-91c8-dbe26620eeb1
ms.openlocfilehash: 4cd99a103fabee3c87036a9933077a3a967f5a13
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173698"
---
# <a name="dataset-specific-operator-examples-linq-to-dataset"></a><span data-ttu-id="c1cda-102">DataSet 'e özgü Işleç örnekleri (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="c1cda-102">DataSet-Specific Operator Examples (LINQ to DataSet)</span></span>

<span data-ttu-id="c1cda-103">Bu konudaki örneklerde, yönteminin ve sınıfının nasıl kullanılacağı gösterilmektedir <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> <xref:System.Data.DataRowComparer> .</span><span class="sxs-lookup"><span data-stu-id="c1cda-103">The examples in this topic demonstrate how to use the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method and the <xref:System.Data.DataRowComparer> class.</span></span>  
  
 <span data-ttu-id="c1cda-104">`FillDataSet`Bu örneklerde kullanılan yöntemi [verileri bir veri kümesine yüklerken](loading-data-into-a-dataset.md)belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c1cda-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="c1cda-105">Bu konudaki örneklerde, AdventureWorks örnek veritabanındaki Ilgili kişi, adres, ürün, SalesOrderHeader ve SalesOrderDetail tabloları kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c1cda-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="c1cda-106">Bu konudaki örnekler aşağıdaki `using` / `Imports` deyimleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="c1cda-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="c1cda-107">Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma](how-to-create-a-linq-to-dataset-project-in-vs.md).</span><span class="sxs-lookup"><span data-stu-id="c1cda-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="copytodatatable"></a><span data-ttu-id="c1cda-108">CopyToDataTable</span><span class="sxs-lookup"><span data-stu-id="c1cda-108">CopyToDataTable</span></span>  
  
### <a name="example"></a><span data-ttu-id="c1cda-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1cda-109">Example</span></span>  

 <span data-ttu-id="c1cda-110">Bu örnek <xref:System.Data.DataTable> , yöntemini kullanarak bir sorgu sonuçlarıyla bir yükler <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> .</span><span class="sxs-lookup"><span data-stu-id="c1cda-110">This example loads a <xref:System.Data.DataTable> with query results by using the <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#loaddatatablewithqueryresults)]
 [!code-vb[DP LINQ to DataSet Examples#LoadDataTableWithQueryResults](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#loaddatatablewithqueryresults)]  
  
## <a name="datarowcomparer"></a><span data-ttu-id="c1cda-111">DataRowComparer</span><span class="sxs-lookup"><span data-stu-id="c1cda-111">DataRowComparer</span></span>  
  
### <a name="example"></a><span data-ttu-id="c1cda-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1cda-112">Example</span></span>  

 <span data-ttu-id="c1cda-113">Bu örnek, kullanarak iki farklı veri satırını karşılaştırır <xref:System.Data.DataRowComparer> .</span><span class="sxs-lookup"><span data-stu-id="c1cda-113">This example compares two different data rows by using <xref:System.Data.DataRowComparer>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CompareDifferentDataRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#comparedifferentdatarows)]  
  
## <a name="see-also"></a><span data-ttu-id="c1cda-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1cda-114">See also</span></span>

- [<span data-ttu-id="c1cda-115">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="c1cda-115">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="c1cda-116">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="c1cda-116">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
