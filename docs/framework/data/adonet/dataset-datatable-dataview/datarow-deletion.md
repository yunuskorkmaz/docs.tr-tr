---
description: 'Daha fazla bilgi: DataRow silme'
title: DataRow Silme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: fff3117256629c2fa0262e2aa163da09174390dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739579"
---
# <a name="datarow-deletion"></a><span data-ttu-id="d3001-103">DataRow Silme</span><span class="sxs-lookup"><span data-stu-id="d3001-103">DataRow Deletion</span></span>

<span data-ttu-id="d3001-104">Nesnesinden bir nesneyi silmek için kullanabileceğiniz iki yöntem vardır <xref:System.Data.DataRow> <xref:System.Data.DataTable> : nesnenin **Remove** yöntemi <xref:System.Data.DataRowCollection> ve <xref:System.Data.DataRow.Delete%2A> **DataRow** nesnesinin yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d3001-104">There are two methods you can use to delete a <xref:System.Data.DataRow> object from a <xref:System.Data.DataTable> object: the **Remove** method of the <xref:System.Data.DataRowCollection> object, and the <xref:System.Data.DataRow.Delete%2A> method of the **DataRow** object.</span></span> <span data-ttu-id="d3001-105">Yöntemi, <xref:System.Data.DataRowCollection.Remove%2A> **DataRowCollection** öğesinden bir **DataRow** siler, <xref:System.Data.DataRow.Delete%2A> Yöntem yalnızca silme satırını işaretler.</span><span class="sxs-lookup"><span data-stu-id="d3001-105">Whereas the <xref:System.Data.DataRowCollection.Remove%2A> method deletes a **DataRow** from the **DataRowCollection**, the <xref:System.Data.DataRow.Delete%2A> method only marks the row for deletion.</span></span> <span data-ttu-id="d3001-106">Gerçek kaldırma, uygulama **AcceptChanges** yöntemini çağırdığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="d3001-106">The actual removal occurs when the application calls the **AcceptChanges** method.</span></span> <span data-ttu-id="d3001-107">Kullanarak <xref:System.Data.DataRow.Delete%2A> , kaldırma işleminin gerçekten kaldırılmadan önce hangi satırların silinmek üzere işaretlendiğini programlı bir şekilde denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3001-107">By using <xref:System.Data.DataRow.Delete%2A>, you can programmatically check which rows are marked for deletion before actually removing them.</span></span> <span data-ttu-id="d3001-108">Bir satır silinmek üzere işaretlendiğinde, <xref:System.Data.DataRow.RowState%2A> özelliği olarak ayarlanır <xref:System.Data.DataRow.Delete%2A> .</span><span class="sxs-lookup"><span data-stu-id="d3001-108">When a row is marked for deletion, its <xref:System.Data.DataRow.RowState%2A> property is set to <xref:System.Data.DataRow.Delete%2A>.</span></span>  
  
 <span data-ttu-id="d3001-109"><xref:System.Data.DataRow.Delete%2A> <xref:System.Data.DataRowCollection.Remove%2A> Bir nesne üzerinden yineleme sırasında ForEach döngüsünde ne de çağrılmalıdır <xref:System.Data.DataRowCollection> .</span><span class="sxs-lookup"><span data-stu-id="d3001-109">Neither <xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> should be called in a foreach loop while iterating through a <xref:System.Data.DataRowCollection> object.</span></span> <span data-ttu-id="d3001-110"><xref:System.Data.DataRow.Delete%2A><xref:System.Data.DataRowCollection.Remove%2A>koleksiyonun durumunu da değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3001-110"><xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> modify the state of the collection.</span></span>  
  
 <span data-ttu-id="d3001-111">Bir <xref:System.Data.DataSet> **DataAdapter** ve ilişkisel veri kaynağıyla birlikte bir veya **DataTable** kullanırken, satırı kaldırmak için **DataRow** 'ın **Delete** yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d3001-111">When using a <xref:System.Data.DataSet> or **DataTable** in conjunction with a **DataAdapter** and a relational data source, use the **Delete** method of the **DataRow** to remove the row.</span></span> <span data-ttu-id="d3001-112">**Delete** yöntemi, satırı **DataSet** veya **DataTable** öğesinde **Deleted** olarak işaretler, ancak kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d3001-112">The **Delete** method marks the row as **Deleted** in the **DataSet** or **DataTable** but does not remove it.</span></span> <span data-ttu-id="d3001-113">Bunun yerine, **DataAdapter** **Silinmiş** olarak işaretlenen bir satırla karşılaştığında, veri kaynağındaki satırı silmek için **DeleteCommand** yöntemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="d3001-113">Instead, when the **DataAdapter** encounters a row marked as **Deleted**, it executes its **DeleteCommand** method to delete the row at the data source.</span></span> <span data-ttu-id="d3001-114">Daha sonra satır, **AcceptChanges** yöntemi kullanılarak kalıcı olarak kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3001-114">The row can then be permanently removed using the **AcceptChanges** method.</span></span> <span data-ttu-id="d3001-115">Satırı silmek için **Kaldır** ' ı kullanırsanız, satır tamamen tablodan kaldırılır, ancak **DataAdapter** veri kaynağındaki satırı silmez.</span><span class="sxs-lookup"><span data-stu-id="d3001-115">If you use **Remove** to delete the row, the row is removed entirely from the table, but the **DataAdapter** will not delete the row at the data source.</span></span>  
  
 <span data-ttu-id="d3001-116">**DataRowCollection** 'ın **Remove** yöntemi bir **DataRow** öğesini bağımsız değişken olarak alır ve aşağıdaki örnekte gösterildiği gibi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d3001-116">The **Remove** method of the **DataRowCollection** takes a **DataRow** as an argument and removes it from the collection, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 <span data-ttu-id="d3001-117">Buna karşılık aşağıdaki örnek, **RowState** değerini **Deleted** olarak değiştirmek Için bir **DataRow** üzerinde **Delete** yönteminin nasıl çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d3001-117">In contrast, the following example demonstrates how to call the **Delete** method on a **DataRow** to change its **RowState** to **Deleted**.</span></span>  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 <span data-ttu-id="d3001-118">Bir satır silinmek üzere işaretlenmişse ve **DataTable** nesnesinin **AcceptChanges** metodunu çağırırsanız, satır **DataTable**'dan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="d3001-118">If a row is marked for deletion and you call the **AcceptChanges** method of the **DataTable** object, the row is removed from the **DataTable**.</span></span> <span data-ttu-id="d3001-119">Buna karşılık, **RejectChanges** öğesini çağırırsanız, satırın **RowState** 'ı **silindi** olarak işaretlenmeden önce ne olduğuna geri döner.</span><span class="sxs-lookup"><span data-stu-id="d3001-119">In contrast, if you call **RejectChanges**, the **RowState** of the row reverts to what it was before being marked as **Deleted**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3001-120">Bir **DataRow** 'ın **RowState** değerini **eklendiyse**, bu, tabloya yalnızca eklenmiş olduğunu belirtir ve sonra **silindi** olarak işaretlenir, tablodan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="d3001-120">If the **RowState** of a **DataRow** is **Added**, meaning it has just been added to the table, and it is then marked as **Deleted**, it is removed from the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3001-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3001-121">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="d3001-122">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="d3001-122">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="d3001-123">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d3001-123">ADO.NET Overview</span></span>](../ado-net-overview.md)
