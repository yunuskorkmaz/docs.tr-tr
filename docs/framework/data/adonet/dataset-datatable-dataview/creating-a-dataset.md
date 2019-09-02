---
title: DataSet Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 57629d8f-393e-4677-8b83-29ffde27f5fc
ms.openlocfilehash: 19badb009ebe95c52ab1dbbaef96f280c769553b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205162"
---
# <a name="creating-a-dataset"></a><span data-ttu-id="538b3-102">DataSet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="538b3-102">Creating a DataSet</span></span>
<span data-ttu-id="538b3-103">Oluşturucuyu çağırarak bir <xref:System.Data.DataSet> örneğini oluşturabilirsiniz. <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="538b3-103">You create an instance of a <xref:System.Data.DataSet> by calling the <xref:System.Data.DataSet> constructor.</span></span> <span data-ttu-id="538b3-104">İsteğe bağlı olarak bir ad bağımsız değişkeni belirtin.</span><span class="sxs-lookup"><span data-stu-id="538b3-104">Optionally specify a name argument.</span></span> <span data-ttu-id="538b3-105">İçin <xref:System.Data.DataSet>bir ad belirtmezseniz, ad "NewDataSet" olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="538b3-105">If you do not specify a name for the <xref:System.Data.DataSet>, the name is set to "NewDataSet".</span></span>  
  
 <span data-ttu-id="538b3-106">Ayrıca, varolan <xref:System.Data.DataSet>bir temelinde yeni <xref:System.Data.DataSet> bir oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="538b3-106">You can also create a new <xref:System.Data.DataSet> based on an existing <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="538b3-107">Yeni <xref:System.Data.DataSet> , var olan <xref:System.Data.DataSet>öğesinin tam bir kopyası olabilir. bunun bir kopyası, ilişkisel <xref:System.Data.DataSet> yapıyı veya şemayı kopyalayan ancak var <xref:System.Data.DataSet>olan veya öğesinin <xref:System.Data.DataSet>bir alt kümesindeki verilerin hiçbirini içermeyen bir kopyasıdır. yalnızca, <xref:System.Data.DataSet> <xref:System.Data.DataSet.GetChanges%2A> yöntemi kullanılarak var olan değiştirilen satırları içerir.</span><span class="sxs-lookup"><span data-stu-id="538b3-107">The new <xref:System.Data.DataSet> can be an exact copy of the existing <xref:System.Data.DataSet>; a clone of the <xref:System.Data.DataSet> that copies the relational structure or schema but that does not contain any of the data from the existing <xref:System.Data.DataSet>; or a subset of the <xref:System.Data.DataSet>, containing only the modified rows from the existing <xref:System.Data.DataSet> using the <xref:System.Data.DataSet.GetChanges%2A> method.</span></span> <span data-ttu-id="538b3-108">Daha fazla bilgi için bkz. [DataSet Içeriğini kopyalama](copying-dataset-contents.md).</span><span class="sxs-lookup"><span data-stu-id="538b3-108">For more information, see [Copying DataSet Contents](copying-dataset-contents.md).</span></span>  
  
 <span data-ttu-id="538b3-109">Aşağıdaki kod örneği, bir <xref:System.Data.DataSet>örneğinin nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="538b3-109">The following code example demonstrates how to construct an instance of a <xref:System.Data.DataSet>.</span></span>  
  
```vb  
Dim customerOrders As DataSet = New DataSet("CustomerOrders")  
```  
  
```csharp  
DataSet customerOrders = new DataSet("CustomerOrders");  
```  
  
## <a name="see-also"></a><span data-ttu-id="538b3-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="538b3-110">See also</span></span>

- [<span data-ttu-id="538b3-111">DataAdapter’dan bir DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="538b3-111">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)
- [<span data-ttu-id="538b3-112">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="538b3-112">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="538b3-113">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="538b3-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
