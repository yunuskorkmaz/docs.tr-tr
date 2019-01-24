---
title: Bir veri kümesine veri yükleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 0f50638beb50220d06daef7bbd6002b319a92476
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622968"
---
# <a name="loading-data-into-a-dataset"></a><span data-ttu-id="b8da4-102">Bir veri kümesine veri yükleme</span><span class="sxs-lookup"><span data-stu-id="b8da4-102">Loading Data Into a DataSet</span></span>
<span data-ttu-id="b8da4-103">A <xref:System.Data.DataSet> nesne, ilk ile ele sorgulayabilirsiniz önce doldurulmalıdır [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b8da4-103">A <xref:System.Data.DataSet> object must first be populated before you can query over it with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="b8da4-104">Doldurmak için birkaç farklı şekilde <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b8da4-104">There are several different ways to populate the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b8da4-105">Örneğin, kullanabileceğiniz [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] sonuçları içine yükleyin ve veritabanını sorgulamak için <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b8da4-105">For example, you can use [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] to query the database and load the results into the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b8da4-106">Daha fazla bilgi için [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="b8da4-106">For more information, see [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="b8da4-107">Verileri yüklemek için başka bir yaygın yolu bir <xref:System.Data.DataSet> kullanmaktır <xref:System.Data.Common.DataAdapter> veritabanından veri almak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="b8da4-107">Another common way to load data into a <xref:System.Data.DataSet> is to use the <xref:System.Data.Common.DataAdapter> class to retrieve data from the database.</span></span> <span data-ttu-id="b8da4-108">Bu, aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b8da4-108">This is illustrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8da4-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8da4-109">Example</span></span>  
 <span data-ttu-id="b8da4-110">Bu örnekte bir <xref:System.Data.Common.DataAdapter> 2002, yılın satış bilgi AdventureWorks veritabanını sorgulamak için ve sonuçlara yükleyen bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="b8da4-110">This example uses a <xref:System.Data.Common.DataAdapter> to query the AdventureWorks database for sales information from the year 2002, and loads the results into a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b8da4-111">Sonra <xref:System.Data.DataSet> kullanarak sorgular yazabilirsiniz doldurulmadı [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b8da4-111">After the <xref:System.Data.DataSet> has been populated, you can write queries against it by using [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="b8da4-112">`FillDataSet` Yöntemi bu örnekte örnek sorgular, kullanılan [LINQ to DataSet örnekleri](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md).</span><span class="sxs-lookup"><span data-stu-id="b8da4-112">The `FillDataSet` method in this example is used in the example queries in [LINQ to DataSet Examples](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md).</span></span> <span data-ttu-id="b8da4-113">Daha fazla bilgi için [veri kümelerini sorgulama](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="b8da4-113">For more information, see [Querying DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a><span data-ttu-id="b8da4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8da4-114">See also</span></span>
- [<span data-ttu-id="b8da4-115">LINQ to DataSet Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b8da4-115">LINQ to DataSet Overview</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)
- [<span data-ttu-id="b8da4-116">DataSet’leri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="b8da4-116">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="b8da4-117">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="b8da4-117">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
