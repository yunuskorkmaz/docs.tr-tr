---
title: DataSet Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: d496167b7bce31491402414c43ae0bcdee423b89
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786500"
---
# <a name="creating-a-dataset"></a><span data-ttu-id="74ac7-102">DataSet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="74ac7-102">Creating a DataSet</span></span>
<span data-ttu-id="74ac7-103">Oluşturucuyu çağırarak bir <xref:System.Data.DataSet> örneğini oluşturabilirsiniz. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="74ac7-103">You create an instance of a <xref:System.Data.DataSet> by calling the <xref:System.Data.DataSet> constructor.</span></span> <span data-ttu-id="74ac7-104">İsteğe bağlı olarak bir ad bağımsız değişkeni belirtin.</span><span class="sxs-lookup"><span data-stu-id="74ac7-104">Optionally specify a name argument.</span></span> <span data-ttu-id="74ac7-105">İçin <xref:System.Data.DataSet>bir ad belirtmezseniz, ad "NewDataSet" olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="74ac7-105">If you do not specify a name for the <xref:System.Data.DataSet>, the name is set to "NewDataSet".</span></span>  
  
 <span data-ttu-id="74ac7-106">Ayrıca, varolan <xref:System.Data.DataSet>bir temelinde yeni <xref:System.Data.DataSet> bir oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74ac7-106">You can also create a new <xref:System.Data.DataSet> based on an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="74ac7-107">Yeni <xref:System.Data.DataSet> , var olan <xref:System.Data.DataSet>öğesinin tam bir kopyası olabilir. bunun bir kopyası, ilişkisel <xref:System.Data.DataSet> yapıyı veya şemayı kopyalayan ancak var <xref:System.Data.DataSet>olan veya öğesinin <xref:System.Data.DataSet>bir alt kümesindeki verilerin hiçbirini içermeyen bir kopyasıdır. yalnızca, <xref:System.Data.DataSet> <xref:System.Data.DataSet.GetChanges%2A> yöntemi kullanılarak var olan değiştirilen satırları içerir.</span><span class="sxs-lookup"><span data-stu-id="74ac7-107">The new <xref:System.Data.DataSet> can be an exact copy of the existing <xref:System.Data.DataSet>; a clone of the <xref:System.Data.DataSet> that copies the relational structure or schema but that does not contain any of the data from the existing <xref:System.Data.DataSet>; or a subset of the <xref:System.Data.DataSet>, containing only the modified rows from the existing <xref:System.Data.DataSet> using the <xref:System.Data.DataSet.GetChanges%2A> method.</span></span> <span data-ttu-id="74ac7-108">Daha fazla bilgi için bkz. [DataSet Içeriğini kopyalama](copying-dataset-contents.md).</span><span class="sxs-lookup"><span data-stu-id="74ac7-108">For more information, see [Copying DataSet Contents](copying-dataset-contents.md).</span></span>  
  
 <span data-ttu-id="74ac7-109">Aşağıdaki kod örneği, bir <xref:System.Data.DataSet>örneğinin nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="74ac7-109">The following code example demonstrates how to construct an instance of a <xref:System.Data.DataSet>.</span></span>  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="74ac7-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74ac7-110">See also</span></span>

- [<span data-ttu-id="74ac7-111">DataAdapter’dan bir DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="74ac7-111">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="74ac7-112">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="74ac7-112">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="74ac7-113">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="74ac7-113">ADO.NET Overview</span></span>](../ado-net-overview.md)
