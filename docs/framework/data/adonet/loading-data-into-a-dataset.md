---
description: 'Hakkında daha fazla bilgi edinin: veri kümesine veri yükleme'
title: DataSet’e Veri Yükleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
ms.openlocfilehash: 167a399d17257008e884fbcccc96de17398b8f88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681688"
---
# <a name="loading-data-into-a-dataset"></a><span data-ttu-id="8d485-103">DataSet’e Veri Yükleme</span><span class="sxs-lookup"><span data-stu-id="8d485-103">Loading Data Into a DataSet</span></span>

<span data-ttu-id="8d485-104">Bir <xref:System.Data.DataSet> nesne, LINQ to DataSet üzerinde sorgu yapabilmeniz için önce doldurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d485-104">A <xref:System.Data.DataSet> object must first be populated before you can query over it with LINQ to DataSet.</span></span> <span data-ttu-id="8d485-105">' Yi doldurmanız için birkaç farklı yol vardır <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="8d485-105">There are several different ways to populate the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="8d485-106">Örneğin, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] veritabanını sorgulamak ve sonuçları öğesine yüklemek için ' yi kullanabilirsiniz <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="8d485-106">For example, you can use [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] to query the database and load the results into the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="8d485-107">Daha fazla bilgi için bkz. [LINQ to SQL](./sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="8d485-107">For more information, see [LINQ to SQL](./sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="8d485-108">Veri yüklemeye yönelik başka bir yaygın yol <xref:System.Data.DataSet> , <xref:System.Data.Common.DataAdapter> veritabanından veri almak için sınıfını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="8d485-108">Another common way to load data into a <xref:System.Data.DataSet> is to use the <xref:System.Data.Common.DataAdapter> class to retrieve data from the database.</span></span> <span data-ttu-id="8d485-109">Bu, aşağıdaki örnekte gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8d485-109">This is illustrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d485-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d485-110">Example</span></span>  

 <span data-ttu-id="8d485-111">Bu örnek, <xref:System.Data.Common.DataAdapter> 2002 yılında satış bilgileri Için AdventureWorks veritabanını sorgulamak için bir kullanır ve sonuçları bir öğesine yükler <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="8d485-111">This example uses a <xref:System.Data.Common.DataAdapter> to query the AdventureWorks database for sales information from the year 2002, and loads the results into a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="8d485-112"><xref:System.Data.DataSet>Doldurulduktan sonra, LINQ to DataSet kullanarak sorgu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d485-112">After the <xref:System.Data.DataSet> has been populated, you can write queries against it by using LINQ to DataSet.</span></span> <span data-ttu-id="8d485-113">`FillDataSet`Bu örnekteki yöntem [LINQ to DataSet örneklerde](linq-to-dataset-examples.md)örnek sorgularda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8d485-113">The `FillDataSet` method in this example is used in the example queries in [LINQ to DataSet Examples](linq-to-dataset-examples.md).</span></span> <span data-ttu-id="8d485-114">Daha fazla bilgi için bkz. [veri kümelerini sorgulama](querying-datasets-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="8d485-114">For more information, see [Querying DataSets](querying-datasets-linq-to-dataset.md).</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a><span data-ttu-id="8d485-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d485-115">See also</span></span>

- [<span data-ttu-id="8d485-116">LINQ to DataSet Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8d485-116">LINQ to DataSet Overview</span></span>](linq-to-dataset-overview.md)
- [<span data-ttu-id="8d485-117">DataSet’leri Sorgulama</span><span class="sxs-lookup"><span data-stu-id="8d485-117">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="8d485-118">LINQ to DataSet Örnekleri</span><span class="sxs-lookup"><span data-stu-id="8d485-118">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
