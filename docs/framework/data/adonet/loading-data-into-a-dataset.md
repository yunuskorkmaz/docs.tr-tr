---
title: "Bir veri kümesine veri yükleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: afb05055d67a4430909a657fc0ee90c97d3ebfb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="loading-data-into-a-dataset"></a><span data-ttu-id="5cfcc-102">Bir veri kümesine veri yükleme</span><span class="sxs-lookup"><span data-stu-id="5cfcc-102">Loading Data Into a DataSet</span></span>
<span data-ttu-id="5cfcc-103">A <xref:System.Data.DataSet> nesnesi, ilk ile üzerinden sorgulayabilirsiniz önce doldurulmalıdır [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5cfcc-103">A <xref:System.Data.DataSet> object must first be populated before you can query over it with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="5cfcc-104">Doldurmak için birkaç farklı yolu vardır <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="5cfcc-104">There are several different ways to populate the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="5cfcc-105">Örneğin, kullanabileceğiniz [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] veritabanını sorgulamak ve sonuçları içine yüklemek için <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="5cfcc-105">For example, you can use [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] to query the database and load the results into the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="5cfcc-106">Daha fazla bilgi için bkz: [LINQ-SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="5cfcc-106">For more information, see [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="5cfcc-107">Verileri yüklemek için başka bir yaygın yolu bir <xref:System.Data.DataSet> kullanmaktır <xref:System.Data.Common.DataAdapter> veritabanından veri almak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="5cfcc-107">Another common way to load data into a <xref:System.Data.DataSet> is to use the <xref:System.Data.Common.DataAdapter> class to retrieve data from the database.</span></span> <span data-ttu-id="5cfcc-108">Bu, aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5cfcc-108">This is illustrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cfcc-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="5cfcc-109">Example</span></span>  
 <span data-ttu-id="5cfcc-110">Bu örnekte bir <xref:System.Data.Common.DataAdapter> 2002, yıldan satış bilgileri AdventureWorks veritabanını sorgulamak için ve sonuçları içine yükler bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="5cfcc-110">This example uses a <xref:System.Data.Common.DataAdapter> to query the AdventureWorks database for sales information from the year 2002, and loads the results into a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="5cfcc-111">Sonra <xref:System.Data.DataSet> , bu sorguları kullanarak yazabilirsiniz doldurulmuş olan [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5cfcc-111">After the <xref:System.Data.DataSet> has been populated, you can write queries against it by using [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="5cfcc-112">`FillDataSet` Yöntemi bu örnekte, örnek sorguların kullanılıyor [LINQ-DataSet örnekler](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md).</span><span class="sxs-lookup"><span data-stu-id="5cfcc-112">The `FillDataSet` method in this example is used in the example queries in [LINQ to DataSet Examples](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md).</span></span> <span data-ttu-id="5cfcc-113">Daha fazla bilgi için bkz: [sorgulama veri kümeleri](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="5cfcc-113">For more information, see [Querying DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a><span data-ttu-id="5cfcc-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5cfcc-114">See Also</span></span>  
 [<span data-ttu-id="5cfcc-115">LINQ-DataSet genel bakış</span><span class="sxs-lookup"><span data-stu-id="5cfcc-115">LINQ to DataSet Overview</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)  
 [<span data-ttu-id="5cfcc-116">Veri kümeleri sorgulama</span><span class="sxs-lookup"><span data-stu-id="5cfcc-116">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [<span data-ttu-id="5cfcc-117">LINQ-DataSet örnekleri</span><span class="sxs-lookup"><span data-stu-id="5cfcc-117">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
