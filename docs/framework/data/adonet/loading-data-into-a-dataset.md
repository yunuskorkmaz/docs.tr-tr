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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4be4c1aa449c3bd78774c6aafe1ec2b55b27b663
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="loading-data-into-a-dataset"></a><span data-ttu-id="49b79-102">Bir veri kümesine veri yükleme</span><span class="sxs-lookup"><span data-stu-id="49b79-102">Loading Data Into a DataSet</span></span>
<span data-ttu-id="49b79-103">A <xref:System.Data.DataSet> nesnesi, ilk ile üzerinden sorgulayabilirsiniz önce doldurulmalıdır [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="49b79-103">A <xref:System.Data.DataSet> object must first be populated before you can query over it with [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="49b79-104">Doldurmak için birkaç farklı yolu vardır <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="49b79-104">There are several different ways to populate the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="49b79-105">Örneğin, kullanabileceğiniz [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] veritabanını sorgulamak ve sonuçları içine yüklemek için <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="49b79-105">For example, you can use [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] to query the database and load the results into the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="49b79-106">Daha fazla bilgi için bkz: [LINQ-SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="49b79-106">For more information, see [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="49b79-107">Verileri yüklemek için başka bir yaygın yolu bir <xref:System.Data.DataSet> kullanmaktır <xref:System.Data.Common.DataAdapter> veritabanından veri almak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="49b79-107">Another common way to load data into a <xref:System.Data.DataSet> is to use the <xref:System.Data.Common.DataAdapter> class to retrieve data from the database.</span></span> <span data-ttu-id="49b79-108">Bu, aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="49b79-108">This is illustrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49b79-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="49b79-109">Example</span></span>  
 <span data-ttu-id="49b79-110">Bu örnekte bir <xref:System.Data.Common.DataAdapter> 2002, yıldan satış bilgileri AdventureWorks veritabanını sorgulamak için ve sonuçları içine yükler bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="49b79-110">This example uses a <xref:System.Data.Common.DataAdapter> to query the AdventureWorks database for sales information from the year 2002, and loads the results into a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="49b79-111">Sonra <xref:System.Data.DataSet> , bu sorguları kullanarak yazabilirsiniz doldurulmuş olan [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="49b79-111">After the <xref:System.Data.DataSet> has been populated, you can write queries against it by using [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="49b79-112">`FillDataSet` Yöntemi bu örnekte, örnek sorguların kullanılıyor [LINQ-DataSet örnekler](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md).</span><span class="sxs-lookup"><span data-stu-id="49b79-112">The `FillDataSet` method in this example is used in the example queries in [LINQ to DataSet Examples](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md).</span></span> <span data-ttu-id="49b79-113">Daha fazla bilgi için bkz: [sorgulama veri kümeleri](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="49b79-113">For more information, see [Querying DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md).</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a><span data-ttu-id="49b79-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="49b79-114">See Also</span></span>  
 [<span data-ttu-id="49b79-115">LINQ to DataSet Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="49b79-115">LINQ to DataSet Overview</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)  
 [<span data-ttu-id="49b79-116">DataSet’leri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="49b79-116">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [<span data-ttu-id="49b79-117">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="49b79-117">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
