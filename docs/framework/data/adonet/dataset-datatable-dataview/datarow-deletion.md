---
title: DataRow Silme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 57f51ada00bf24617ca3e295a010aae64f0aa849
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196144"
---
# <a name="datarow-deletion"></a><span data-ttu-id="a7be8-102">DataRow Silme</span><span class="sxs-lookup"><span data-stu-id="a7be8-102">DataRow Deletion</span></span>
<span data-ttu-id="a7be8-103">Silmek için kullanabileceğiniz iki yöntem vardır bir <xref:System.Data.DataRow> nesnesinden bir <xref:System.Data.DataTable> nesne: **Kaldır** yöntemi <xref:System.Data.DataRowCollection> nesnesi ve <xref:System.Data.DataRow.Delete%2A> yöntemi **DataRow**nesne.</span><span class="sxs-lookup"><span data-stu-id="a7be8-103">There are two methods you can use to delete a <xref:System.Data.DataRow> object from a <xref:System.Data.DataTable> object: the **Remove** method of the <xref:System.Data.DataRowCollection> object, and the <xref:System.Data.DataRow.Delete%2A> method of the **DataRow** object.</span></span> <span data-ttu-id="a7be8-104">Oysa <xref:System.Data.DataRowCollection.Remove%2A> yöntemi siler bir **DataRow** gelen **DataRowCollection**, <xref:System.Data.DataRow.Delete%2A> yöntemi yalnızca satır silme işlemi için işaretler.</span><span class="sxs-lookup"><span data-stu-id="a7be8-104">Whereas the <xref:System.Data.DataRowCollection.Remove%2A> method deletes a **DataRow** from the **DataRowCollection**, the <xref:System.Data.DataRow.Delete%2A> method only marks the row for deletion.</span></span> <span data-ttu-id="a7be8-105">Uygulama çağırdığında gerçek kaldırma gerçekleşir **AcceptChanges** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a7be8-105">The actual removal occurs when the application calls the **AcceptChanges** method.</span></span> <span data-ttu-id="a7be8-106">Kullanarak <xref:System.Data.DataRow.Delete%2A>, hangi satırların gerçekten kaldırmadan önce silinmek üzere işaretlenmiş programlı olarak denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7be8-106">By using <xref:System.Data.DataRow.Delete%2A>, you can programmatically check which rows are marked for deletion before actually removing them.</span></span> <span data-ttu-id="a7be8-107">Satır silme için işaretlendiğinden kendi <xref:System.Data.DataRow.RowState%2A> özelliği <xref:System.Data.DataRow.Delete%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7be8-107">When a row is marked for deletion, its <xref:System.Data.DataRow.RowState%2A> property is set to <xref:System.Data.DataRow.Delete%2A>.</span></span>  
  
 <span data-ttu-id="a7be8-108">Ne <xref:System.Data.DataRow.Delete%2A> ya da <xref:System.Data.DataRowCollection.Remove%2A> bir foreach döngüsü içinde yineleme sırasında çağrılması gereken bir <xref:System.Data.DataRowCollection> nesne.</span><span class="sxs-lookup"><span data-stu-id="a7be8-108">Neither <xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> should be called in a foreach loop while iterating through a <xref:System.Data.DataRowCollection> object.</span></span> <span data-ttu-id="a7be8-109"><xref:System.Data.DataRow.Delete%2A> ya da <xref:System.Data.DataRowCollection.Remove%2A> koleksiyon durumunu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a7be8-109"><xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> modify the state of the collection.</span></span>  
  
 <span data-ttu-id="a7be8-110">Kullanırken bir <xref:System.Data.DataSet> veya **DataTable** ile birlikte bir **DataAdapter** ve kullanmak, bir ilişkisel veri kaynağı **Sil** yöntemi  **DataRow** satırı Kaldır.</span><span class="sxs-lookup"><span data-stu-id="a7be8-110">When using a <xref:System.Data.DataSet> or **DataTable** in conjunction with a **DataAdapter** and a relational data source, use the **Delete** method of the **DataRow** to remove the row.</span></span> <span data-ttu-id="a7be8-111">**Sil** yöntemi satır olarak işaretler **silinmiş** içinde **veri kümesi** veya **DataTable** ancak bunu kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="a7be8-111">The **Delete** method marks the row as **Deleted** in the **DataSet** or **DataTable** but does not remove it.</span></span> <span data-ttu-id="a7be8-112">Bunun yerine, **DataAdapter** olarak işaretlenmiş bir satır karşılaştığında **silinmiş**, yürütür, **DeleteCommand** veri kaynağındaki satırı silmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a7be8-112">Instead, when the **DataAdapter** encounters a row marked as **Deleted**, it executes its **DeleteCommand** method to delete the row at the data source.</span></span> <span data-ttu-id="a7be8-113">Satır sonra kalıcı olarak kullanılarak kaldırılabilir **AcceptChanges** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a7be8-113">The row can then be permanently removed using the **AcceptChanges** method.</span></span> <span data-ttu-id="a7be8-114">Kullanırsanız **Kaldır** satırı silmek için satırın tablosundan tamamen kaldırılır ancak **DataAdapter** veri kaynağında satırın silinmesine neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="a7be8-114">If you use **Remove** to delete the row, the row is removed entirely from the table, but the **DataAdapter** will not delete the row at the data source.</span></span>  
  
 <span data-ttu-id="a7be8-115">**Kaldır** yöntemi **DataRowCollection** götüren bir **DataRow** bağımsız değişken olarak ve aşağıdaki örnekte gösterildiği gibi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a7be8-115">The **Remove** method of the **DataRowCollection** takes a **DataRow** as an argument and removes it from the collection, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 <span data-ttu-id="a7be8-116">Buna karşılık, aşağıdaki örnekte nasıl çağrılacağını gösterir **Sil** metodunda bir **DataRow** değiştirmek için kendi **RowState** için **silinen** .</span><span class="sxs-lookup"><span data-stu-id="a7be8-116">In contrast, the following example demonstrates how to call the **Delete** method on a **DataRow** to change its **RowState** to **Deleted**.</span></span>  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 <span data-ttu-id="a7be8-117">Bir satırı silinmek üzere işaretlendiğinden ve çağırmanızı **AcceptChanges** yöntemi **DataTable** nesnesi, satır kaldırılır **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="a7be8-117">If a row is marked for deletion and you call the **AcceptChanges** method of the **DataTable** object, the row is removed from the **DataTable**.</span></span> <span data-ttu-id="a7be8-118">Buna karşılık, çağırırsanız **RejectChanges**, **RowState** satırının ne olarak işaretlenmesi önce haline döner **silinmiş**.</span><span class="sxs-lookup"><span data-stu-id="a7be8-118">In contrast, if you call **RejectChanges**, the **RowState** of the row reverts to what it was before being marked as **Deleted**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7be8-119">Varsa **RowState** , bir **DataRow** olduğu **eklenen**, yani yalnızca eklendiğini tablosuna ve ardından olarak işaretlenmiş **silinmiş**, bu tablosundan kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="a7be8-119">If the **RowState** of a **DataRow** is **Added**, meaning it has just been added to the table, and it is then marked as **Deleted**, it is removed from the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7be8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7be8-120">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="a7be8-121">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="a7be8-121">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="a7be8-122">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="a7be8-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
