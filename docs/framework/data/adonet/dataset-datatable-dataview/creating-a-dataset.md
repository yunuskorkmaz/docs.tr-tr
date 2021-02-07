---
description: 'Hakkında daha fazla bilgi edinin: veri kümesi oluşturma'
title: DataSet Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: 7a52c6e73b5ab3ba4bf384d6bab3640b85929fcc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739657"
---
# <a name="creating-a-dataset"></a><span data-ttu-id="d6ebf-103">DataSet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d6ebf-103">Creating a DataSet</span></span>

<span data-ttu-id="d6ebf-104">Oluşturucuyu çağırarak bir örneğini oluşturabilirsiniz <xref:System.Data.DataSet> <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="d6ebf-104">You create an instance of a <xref:System.Data.DataSet> by calling the <xref:System.Data.DataSet> constructor.</span></span> <span data-ttu-id="d6ebf-105">İsteğe bağlı olarak bir ad bağımsız değişkeni belirtin.</span><span class="sxs-lookup"><span data-stu-id="d6ebf-105">Optionally specify a name argument.</span></span> <span data-ttu-id="d6ebf-106">İçin bir ad belirtmezseniz, <xref:System.Data.DataSet> ad "NewDataSet" olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d6ebf-106">If you do not specify a name for the <xref:System.Data.DataSet>, the name is set to "NewDataSet".</span></span>  
  
 <span data-ttu-id="d6ebf-107">Ayrıca, <xref:System.Data.DataSet> varolan bir temelinde yeni bir oluşturabilirsiniz <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="d6ebf-107">You can also create a new <xref:System.Data.DataSet> based on an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="d6ebf-108">Yeni, <xref:System.Data.DataSet> var olan öğesinin tam bir kopyası olabilir <xref:System.Data.DataSet> <xref:System.Data.DataSet> . Bu, ilişkisel yapıyı veya şemayı kopyalayan, ancak var olan bir veri kümesini ya da bir alt kümesini içeren, ancak, <xref:System.Data.DataSet> <xref:System.Data.DataSet> yalnızca var olan bir ' ın <xref:System.Data.DataSet> <xref:System.Data.DataSet.GetChanges%2A> .</span><span class="sxs-lookup"><span data-stu-id="d6ebf-108">The new <xref:System.Data.DataSet> can be an exact copy of the existing <xref:System.Data.DataSet>; a clone of the <xref:System.Data.DataSet> that copies the relational structure or schema but that does not contain any of the data from the existing <xref:System.Data.DataSet>; or a subset of the <xref:System.Data.DataSet>, containing only the modified rows from the existing <xref:System.Data.DataSet> using the <xref:System.Data.DataSet.GetChanges%2A> method.</span></span> <span data-ttu-id="d6ebf-109">Daha fazla bilgi için bkz. [DataSet Içeriğini kopyalama](copying-dataset-contents.md).</span><span class="sxs-lookup"><span data-stu-id="d6ebf-109">For more information, see [Copying DataSet Contents](copying-dataset-contents.md).</span></span>  
  
 <span data-ttu-id="d6ebf-110">Aşağıdaki kod örneği, bir örneğinin nasıl oluşturulacağını göstermektedir <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="d6ebf-110">The following code example demonstrates how to construct an instance of a <xref:System.Data.DataSet>.</span></span>  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="d6ebf-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6ebf-111">See also</span></span>

- [<span data-ttu-id="d6ebf-112">DataAdapter’dan bir DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="d6ebf-112">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="d6ebf-113">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="d6ebf-113">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="d6ebf-114">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d6ebf-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
