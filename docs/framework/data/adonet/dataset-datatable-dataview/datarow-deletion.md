---
title: DataRow Silme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 46109ee1781b8b509df87b4203c51a55b9f596ae
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205110"
---
# <a name="datarow-deletion"></a><span data-ttu-id="6436c-102">DataRow Silme</span><span class="sxs-lookup"><span data-stu-id="6436c-102">DataRow Deletion</span></span>
<span data-ttu-id="6436c-103">Nesnesinden <xref:System.Data.DataRow> bir nesneyi <xref:System.Data.DataTable> silmek için kullanabileceğiniz iki yöntem vardır: <xref:System.Data.DataRowCollection> nesnenin **Remove** <xref:System.Data.DataRow.Delete%2A> yöntemi ve **DataRow** nesnesinin yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6436c-103">There are two methods you can use to delete a <xref:System.Data.DataRow> object from a <xref:System.Data.DataTable> object: the **Remove** method of the <xref:System.Data.DataRowCollection> object, and the <xref:System.Data.DataRow.Delete%2A> method of the **DataRow** object.</span></span> <span data-ttu-id="6436c-104">Yöntemi, **DataRowCollection**öğesinden bir <xref:System.Data.DataRow.Delete%2A> **DataRow** siler, yöntem yalnızca silme satırını işaretler. <xref:System.Data.DataRowCollection.Remove%2A></span><span class="sxs-lookup"><span data-stu-id="6436c-104">Whereas the <xref:System.Data.DataRowCollection.Remove%2A> method deletes a **DataRow** from the **DataRowCollection**, the <xref:System.Data.DataRow.Delete%2A> method only marks the row for deletion.</span></span> <span data-ttu-id="6436c-105">Gerçek kaldırma, uygulama **AcceptChanges** yöntemini çağırdığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="6436c-105">The actual removal occurs when the application calls the **AcceptChanges** method.</span></span> <span data-ttu-id="6436c-106">Kullanarak <xref:System.Data.DataRow.Delete%2A>, kaldırma işleminin gerçekten kaldırılmadan önce hangi satırların silinmek üzere işaretlendiğini programlı bir şekilde denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6436c-106">By using <xref:System.Data.DataRow.Delete%2A>, you can programmatically check which rows are marked for deletion before actually removing them.</span></span> <span data-ttu-id="6436c-107">Bir satır silinmek üzere işaretlendiğinde, <xref:System.Data.DataRow.RowState%2A> özelliği olarak <xref:System.Data.DataRow.Delete%2A>ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="6436c-107">When a row is marked for deletion, its <xref:System.Data.DataRow.RowState%2A> property is set to <xref:System.Data.DataRow.Delete%2A>.</span></span>  
  
 <span data-ttu-id="6436c-108"><xref:System.Data.DataRowCollection.Remove%2A> Bir <xref:System.Data.DataRow.Delete%2A> nesneüzerindenyinelemesırasındaForEachdöngüsünde<xref:System.Data.DataRowCollection> ne de çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6436c-108">Neither <xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> should be called in a foreach loop while iterating through a <xref:System.Data.DataRowCollection> object.</span></span> <span data-ttu-id="6436c-109"><xref:System.Data.DataRow.Delete%2A>Koleksiyonun <xref:System.Data.DataRowCollection.Remove%2A> durumunu da değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6436c-109"><xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> modify the state of the collection.</span></span>  
  
 <span data-ttu-id="6436c-110">Bir DataAdapter ve <xref:System.Data.DataSet> ilişkisel veri kaynağıyla birlikte bir veya **DataTable** kullanırken, satırı kaldırmak için **DataRow** 'ın **Delete** yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6436c-110">When using a <xref:System.Data.DataSet> or **DataTable** in conjunction with a **DataAdapter** and a relational data source, use the **Delete** method of the **DataRow** to remove the row.</span></span> <span data-ttu-id="6436c-111">**Delete** yöntemi, satırı **DataSet** veya **DataTable** öğesinde **Deleted** olarak işaretler, ancak kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6436c-111">The **Delete** method marks the row as **Deleted** in the **DataSet** or **DataTable** but does not remove it.</span></span> <span data-ttu-id="6436c-112">Bunun yerine, **DataAdapter** **Silinmiş**olarak işaretlenen bir satırla karşılaştığında, veri kaynağındaki satırı silmek için **DeleteCommand** yöntemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="6436c-112">Instead, when the **DataAdapter** encounters a row marked as **Deleted**, it executes its **DeleteCommand** method to delete the row at the data source.</span></span> <span data-ttu-id="6436c-113">Daha sonra satır, **AcceptChanges** yöntemi kullanılarak kalıcı olarak kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="6436c-113">The row can then be permanently removed using the **AcceptChanges** method.</span></span> <span data-ttu-id="6436c-114">Satırı silmek için **Kaldır** ' ı kullanırsanız, satır tamamen tablodan kaldırılır, ancak **DataAdapter** veri kaynağındaki satırı silmez.</span><span class="sxs-lookup"><span data-stu-id="6436c-114">If you use **Remove** to delete the row, the row is removed entirely from the table, but the **DataAdapter** will not delete the row at the data source.</span></span>  
  
 <span data-ttu-id="6436c-115">**DataRowCollection** 'ın **Remove** yöntemi bir **DataRow** öğesini bağımsız değişken olarak alır ve aşağıdaki örnekte gösterildiği gibi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6436c-115">The **Remove** method of the **DataRowCollection** takes a **DataRow** as an argument and removes it from the collection, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 <span data-ttu-id="6436c-116">Buna karşılık aşağıdaki örnek, **RowState** değerini **Deleted**olarak değiştirmek Için bir **DataRow** üzerinde **Delete** yönteminin nasıl çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6436c-116">In contrast, the following example demonstrates how to call the **Delete** method on a **DataRow** to change its **RowState** to **Deleted**.</span></span>  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 <span data-ttu-id="6436c-117">Bir satır silinmek üzere işaretlenmişse ve **DataTable** nesnesinin **AcceptChanges** metodunu çağırırsanız, satır **DataTable**'dan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="6436c-117">If a row is marked for deletion and you call the **AcceptChanges** method of the **DataTable** object, the row is removed from the **DataTable**.</span></span> <span data-ttu-id="6436c-118">Buna karşılık, **RejectChanges**öğesini çağırırsanız, satırın **RowState** 'ı **silindi**olarak işaretlenmeden önce ne olduğuna geri döner.</span><span class="sxs-lookup"><span data-stu-id="6436c-118">In contrast, if you call **RejectChanges**, the **RowState** of the row reverts to what it was before being marked as **Deleted**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6436c-119">Bir **DataRow** 'ın **RowState** değerini **eklendiyse**, bu, tabloya yalnızca eklenmiş olduğunu belirtir ve sonra **silindi**olarak işaretlenir, tablodan kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="6436c-119">If the **RowState** of a **DataRow** is **Added**, meaning it has just been added to the table, and it is then marked as **Deleted**, it is removed from the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6436c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6436c-120">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="6436c-121">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="6436c-121">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="6436c-122">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="6436c-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
