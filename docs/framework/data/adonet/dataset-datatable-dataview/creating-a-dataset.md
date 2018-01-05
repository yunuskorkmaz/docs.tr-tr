---
title: "Bir veri kümesi oluşturma"
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
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8ae997822d71a0a0a4276b8b32b963149a8ed67a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-dataset"></a><span data-ttu-id="3d712-102">Bir veri kümesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="3d712-102">Creating a DataSet</span></span>
<span data-ttu-id="3d712-103">Bir örneğini oluşturmak bir <xref:System.Data.DataSet> çağırarak <xref:System.Data.DataSet> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="3d712-103">You create an instance of a <xref:System.Data.DataSet> by calling the <xref:System.Data.DataSet> constructor.</span></span> <span data-ttu-id="3d712-104">İsteğe bağlı olarak bir adı bağımsız değişkenini belirtin.</span><span class="sxs-lookup"><span data-stu-id="3d712-104">Optionally specify a name argument.</span></span> <span data-ttu-id="3d712-105">İçin bir ad belirtmezseniz, <xref:System.Data.DataSet>, adı "NewDataSet" ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3d712-105">If you do not specify a name for the <xref:System.Data.DataSet>, the name is set to "NewDataSet".</span></span>  
  
 <span data-ttu-id="3d712-106">Ayrıca, yeni bir oluşturabilirsiniz <xref:System.Data.DataSet> var olan temel <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="3d712-106">You can also create a new <xref:System.Data.DataSet> based on an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="3d712-107">Yeni <xref:System.Data.DataSet> var olan tam bir kopyasını olabilir <xref:System.Data.DataSet>; bir kopyasını <xref:System.Data.DataSet> ilişkisel yapısı veya şema kopyalar ancak, varolan verilerin içermediğinden <xref:System.Data.DataSet>; veya bir alt kümesini <xref:System.Data.DataSet>, Mevcut kümeden yalnızca değiştirilen satırları içeren <xref:System.Data.DataSet> kullanarak <xref:System.Data.DataSet.GetChanges%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3d712-107">The new <xref:System.Data.DataSet> can be an exact copy of the existing <xref:System.Data.DataSet>; a clone of the <xref:System.Data.DataSet> that copies the relational structure or schema but that does not contain any of the data from the existing <xref:System.Data.DataSet>; or a subset of the <xref:System.Data.DataSet>, containing only the modified rows from the existing <xref:System.Data.DataSet> using the <xref:System.Data.DataSet.GetChanges%2A> method.</span></span> <span data-ttu-id="3d712-108">Daha fazla bilgi için bkz: [kopyalama DataSet içeriği](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md).</span><span class="sxs-lookup"><span data-stu-id="3d712-108">For more information, see [Copying DataSet Contents](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md).</span></span>  
  
 <span data-ttu-id="3d712-109">Aşağıdaki kod örneğinde olgusu yapmayı gösteren bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="3d712-109">The following code example demonstrates how to construct an instance of a <xref:System.Data.DataSet>.</span></span>  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d712-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d712-110">See Also</span></span>  
 [<span data-ttu-id="3d712-111">DataAdapter’dan bir DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="3d712-111">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [<span data-ttu-id="3d712-112">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="3d712-112">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="3d712-113">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="3d712-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
