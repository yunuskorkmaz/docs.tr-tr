---
title: DataSet’e Veri Yükleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 53f0f5a589a0033c9612f0465dff090ab04e3fc4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794950"
---
# <a name="loading-data-into-a-dataset"></a><span data-ttu-id="9fb7b-102">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="9fb7b-102">Loading Data Into a DataSet</span></span>
<span data-ttu-id="9fb7b-103">Bir <xref:System.Data.DataSet> nesne, LINQ to DataSet üzerinde sorgu yapabilmeniz için önce doldurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9fb7b-103">A <xref:System.Data.DataSet> object must first be populated before you can query over it with LINQ to DataSet.</span></span> <span data-ttu-id="9fb7b-104">' Yi doldurmanız <xref:System.Data.DataSet>için birkaç farklı yol vardır.</span><span class="sxs-lookup"><span data-stu-id="9fb7b-104">There are several different ways to populate the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9fb7b-105">Örneğin, veritabanını sorgulamak ve sonuçları [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.DataSet>öğesine yüklemek için ' yi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fb7b-105">For example, you can use [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] to query the database and load the results into the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9fb7b-106">Daha fazla bilgi için bkz. [LINQ to SQL](./sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="9fb7b-106">For more information, see [LINQ to SQL](./sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="9fb7b-107">Veri <xref:System.Data.DataSet> yüklemeye yönelik başka bir yaygın yol, veritabanından veri almak için <xref:System.Data.Common.DataAdapter> sınıfını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="9fb7b-107">Another common way to load data into a <xref:System.Data.DataSet> is to use the <xref:System.Data.Common.DataAdapter> class to retrieve data from the database.</span></span> <span data-ttu-id="9fb7b-108">Bu, aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9fb7b-108">This is illustrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fb7b-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="9fb7b-109">Example</span></span>  
 <span data-ttu-id="9fb7b-110">Bu örnek, 2002 <xref:System.Data.Common.DataAdapter> yılında satış bilgileri için AdventureWorks veritabanını sorgulamak için bir kullanır ve sonuçları bir <xref:System.Data.DataSet>öğesine yükler.</span><span class="sxs-lookup"><span data-stu-id="9fb7b-110">This example uses a <xref:System.Data.Common.DataAdapter> to query the AdventureWorks database for sales information from the year 2002, and loads the results into a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="9fb7b-111"><xref:System.Data.DataSet> Doldurulduktan sonra, LINQ to DataSet kullanarak sorgu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fb7b-111">After the <xref:System.Data.DataSet> has been populated, you can write queries against it by using LINQ to DataSet.</span></span> <span data-ttu-id="9fb7b-112">Bu örnekteki yöntem LINQ to DataSet örneklerde örnek sorgularda kullanılır. [](linq-to-dataset-examples.md) `FillDataSet`</span><span class="sxs-lookup"><span data-stu-id="9fb7b-112">The `FillDataSet` method in this example is used in the example queries in [LINQ to DataSet Examples](linq-to-dataset-examples.md).</span></span> <span data-ttu-id="9fb7b-113">Daha fazla bilgi için bkz. [veri kümelerini sorgulama](querying-datasets-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="9fb7b-113">For more information, see [Querying DataSets](querying-datasets-linq-to-dataset.md).</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a><span data-ttu-id="9fb7b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9fb7b-114">See also</span></span>

- [<span data-ttu-id="9fb7b-115">LINQ to DataSet Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9fb7b-115">LINQ to DataSet Overview</span></span>](linq-to-dataset-overview.md)
- [<span data-ttu-id="9fb7b-116">DataSet’leri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="9fb7b-116">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="9fb7b-117">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="9fb7b-117">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
