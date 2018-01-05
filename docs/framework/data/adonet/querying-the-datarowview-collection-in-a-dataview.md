---
title: DataView DataRowView koleksiyonunda sorgulama
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
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 02b32157fe88bddfd9a777042f6da87aa48ca551
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a><span data-ttu-id="3b52b-102">DataView DataRowView koleksiyonunda sorgulama</span><span class="sxs-lookup"><span data-stu-id="3b52b-102">Querying the DataRowView Collection in a DataView</span></span>
<span data-ttu-id="3b52b-103"><xref:System.Data.DataView> Numaralandırılabilir bir topluluğu gösterir <xref:System.Data.DataRowView> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="3b52b-103">The <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="3b52b-104"><xref:System.Data.DataRowView>özelleştirilmiş bir görünümünü temsil eden bir <xref:System.Data.DataRow> ve, belirli bir sürümünü görüntüler <xref:System.Data.DataRow> denetiminde.</span><span class="sxs-lookup"><span data-stu-id="3b52b-104"><xref:System.Data.DataRowView> represents a customized view of a <xref:System.Data.DataRow> and displays a specific version of that <xref:System.Data.DataRow> in a control.</span></span> <span data-ttu-id="3b52b-105">Yalnızca bir sürümü bir <xref:System.Data.DataRow> bir denetim aracılığıyla gibi görüntülenebilen bir <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="3b52b-105">Only one version of a <xref:System.Data.DataRow> can be displayed through a control, such as a <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="3b52b-106">Erişebileceğiniz <xref:System.Data.DataRow> tarafından sunulan <xref:System.Data.DataRowView> aracılığıyla <xref:System.Data.DataRowView.Row%2A> özelliği <xref:System.Data.DataRowView>.</span><span class="sxs-lookup"><span data-stu-id="3b52b-106">You can access the <xref:System.Data.DataRow> that is exposed by the <xref:System.Data.DataRowView> through the <xref:System.Data.DataRowView.Row%2A> property of the <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="3b52b-107">Kullanarak değerleri görüntülerken bir <xref:System.Data.DataRowView>, <xref:System.Data.DataView.RowStateFilter%2A> özelliği, arka plandaki hangi satır sürümü belirler <xref:System.Data.DataRow> sunulur.</span><span class="sxs-lookup"><span data-stu-id="3b52b-107">When you view values by using a <xref:System.Data.DataRowView>, the <xref:System.Data.DataView.RowStateFilter%2A> property determines which row version of the underlying <xref:System.Data.DataRow> is exposed.</span></span> <span data-ttu-id="3b52b-108">Kullanarak farklı satır sürümler erişme hakkında bilgi için bir <xref:System.Data.DataRow>, bkz: [satır durumları ve satır sürümleri](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="3b52b-108">For information about accessing different row versions using a <xref:System.Data.DataRow>, see [Row States and Row Versions](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span> <span data-ttu-id="3b52b-109">Çünkü koleksiyonunu <xref:System.Data.DataRowView> tarafından sunulan nesneleri <xref:System.Data.DataView> olan numaralandırılabilir, kullanabilirsiniz [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] ele sorgulanamıyor.</span><span class="sxs-lookup"><span data-stu-id="3b52b-109">Because the collection of <xref:System.Data.DataRowView> objects exposed by the <xref:System.Data.DataView> is enumerable, you can use [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] to query over it.</span></span>  
  
 <span data-ttu-id="3b52b-110">Aşağıdaki örnek sorgularda `Product` tablo için kırmızı renkli ürünler ve bu sorgudan bir tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3b52b-110">The following example queries the `Product` table for red-colored products and creates a table from that query.</span></span> <span data-ttu-id="3b52b-111">A <xref:System.Data.DataView> tablosundan oluşturulur ve <xref:System.Data.DataView.RowStateFilter%2A> özelliği, silinen ve değiştirilen satırlarda filtrelemek için ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3b52b-111">A <xref:System.Data.DataView> is created from the table and the <xref:System.Data.DataView.RowStateFilter%2A> property is set to filter on deleted and modified rows.</span></span> <span data-ttu-id="3b52b-112"><xref:System.Data.DataView> Daha sonra bir LINQ Sorgu kaynağı olarak kullanılır ve <xref:System.Data.DataRowView> , değiştirilen ve silinen nesneleri bağlı bir <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="3b52b-112">The <xref:System.Data.DataView> is then used as a source in a LINQ query, and the <xref:System.Data.DataRowView> objects that have been modified and deleted are bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 <span data-ttu-id="3b52b-113">Aşağıdaki örnek, bağlı bir görünümden ürünlerin bir tablo oluşturur. bir <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="3b52b-113">The following example creates a table of products from a view that is bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="3b52b-114"><xref:System.Data.DataView> Kırmızı renkli ürünleri ve sıralı için sorgulanır sonuçları bağlı bir <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="3b52b-114">The <xref:System.Data.DataView> is queried for red-colored products and the ordered results are bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a><span data-ttu-id="3b52b-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3b52b-115">See Also</span></span>  
 [<span data-ttu-id="3b52b-116">Veri Bağlama ve LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="3b52b-116">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
