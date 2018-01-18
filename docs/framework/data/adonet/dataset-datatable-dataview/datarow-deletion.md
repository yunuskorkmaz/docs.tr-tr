---
title: DataRow silme
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
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5102e1e2d95bd6adc29d5f2a2317bc15f8386cdc
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="datarow-deletion"></a><span data-ttu-id="55701-102">DataRow silme</span><span class="sxs-lookup"><span data-stu-id="55701-102">DataRow Deletion</span></span>
<span data-ttu-id="55701-103">Silmek için kullanabileceğiniz iki yöntem vardır bir <xref:System.Data.DataRow> nesnesinin bir <xref:System.Data.DataTable> nesne: **kaldırmak** yöntemi <xref:System.Data.DataRowCollection> nesnesi ve <xref:System.Data.DataRow.Delete%2A> yöntemi **DataRow**nesnesi.</span><span class="sxs-lookup"><span data-stu-id="55701-103">There are two methods you can use to delete a <xref:System.Data.DataRow> object from a <xref:System.Data.DataTable> object: the **Remove** method of the <xref:System.Data.DataRowCollection> object, and the <xref:System.Data.DataRow.Delete%2A> method of the **DataRow** object.</span></span> <span data-ttu-id="55701-104">Oysa <xref:System.Data.DataRowCollection.Remove%2A> yöntemi siler bir **DataRow** gelen **DataRowCollection**, <xref:System.Data.DataRow.Delete%2A> yöntemi yalnızca satır silme işlemi için işaretler.</span><span class="sxs-lookup"><span data-stu-id="55701-104">Whereas the <xref:System.Data.DataRowCollection.Remove%2A> method deletes a **DataRow** from the **DataRowCollection**, the <xref:System.Data.DataRow.Delete%2A> method only marks the row for deletion.</span></span> <span data-ttu-id="55701-105">Uygulama çağırdığında gerçek kaldırma oluşur **AcceptChanges** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="55701-105">The actual removal occurs when the application calls the **AcceptChanges** method.</span></span> <span data-ttu-id="55701-106">Kullanarak <xref:System.Data.DataRow.Delete%2A>, hangi satırların gerçekten kaldırmadan önce silinmek üzere işaretlenmiş program aracılığıyla kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55701-106">By using <xref:System.Data.DataRow.Delete%2A>, you can programmatically check which rows are marked for deletion before actually removing them.</span></span> <span data-ttu-id="55701-107">Bir satır silinmek üzere işaretli olduğunda, <xref:System.Data.DataRow.RowState%2A> özelliği ayarlanmış <xref:System.Data.DataRow.Delete%2A>.</span><span class="sxs-lookup"><span data-stu-id="55701-107">When a row is marked for deletion, its <xref:System.Data.DataRow.RowState%2A> property is set to <xref:System.Data.DataRow.Delete%2A>.</span></span>  
  
 <span data-ttu-id="55701-108">Ne <xref:System.Data.DataRow.Delete%2A> ya da <xref:System.Data.DataRowCollection.Remove%2A> üzerinden yineleme sırasında bir foreach döngüsü çağrılmalıdır bir <xref:System.Data.DataRowCollection> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="55701-108">Neither <xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> should be called in a foreach loop while iterating through a <xref:System.Data.DataRowCollection> object.</span></span> <span data-ttu-id="55701-109"><xref:System.Data.DataRow.Delete%2A>ya da <xref:System.Data.DataRowCollection.Remove%2A> koleksiyon durumunu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="55701-109"><xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> modify the state of the collection.</span></span>  
  
 <span data-ttu-id="55701-110">Kullanırken bir <xref:System.Data.DataSet> veya **DataTable** ile birlikte bir **DataAdapter** ve kullanmak, bir ilişkisel veri kaynağı **silmek** yöntemi  **DataRow** satır kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="55701-110">When using a <xref:System.Data.DataSet> or **DataTable** in conjunction with a **DataAdapter** and a relational data source, use the **Delete** method of the **DataRow** to remove the row.</span></span> <span data-ttu-id="55701-111">**Silmek** yöntemi satır olarak işaretler **silinmiş** içinde **DataSet** veya **DataTable** ancak onu kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="55701-111">The **Delete** method marks the row as **Deleted** in the **DataSet** or **DataTable** but does not remove it.</span></span> <span data-ttu-id="55701-112">Bunun yerine, **DataAdapter** olarak işaretlenmiş bir satır karşılaştığında **silinmiş**, yürütülmeden kendi **DeleteCommand** veri kaynağında satır silme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="55701-112">Instead, when the **DataAdapter** encounters a row marked as **Deleted**, it executes its **DeleteCommand** method to delete the row at the data source.</span></span> <span data-ttu-id="55701-113">Satır sonra kalıcı olarak kullanılarak kaldırılabilir **AcceptChanges** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="55701-113">The row can then be permanently removed using the **AcceptChanges** method.</span></span> <span data-ttu-id="55701-114">Kullanırsanız **kaldırmak** satırı silmek için Satırı tablosundan tamamen kaldırılır ancak **DataAdapter** veri kaynağında satır silmez.</span><span class="sxs-lookup"><span data-stu-id="55701-114">If you use **Remove** to delete the row, the row is removed entirely from the table, but the **DataAdapter** will not delete the row at the data source.</span></span>  
  
 <span data-ttu-id="55701-115">**Kaldırmak** yöntemi **DataRowCollection** geçen bir **DataRow** bağımsız değişken olarak ve aşağıdaki örnekte gösterildiği gibi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="55701-115">The **Remove** method of the **DataRowCollection** takes a **DataRow** as an argument and removes it from the collection, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 <span data-ttu-id="55701-116">Buna karşılık, aşağıdaki örnekte nasıl çağırılacağını **silmek** yöntemi bir **DataRow** değiştirmek için kendi **RowState** için **silinmiş** .</span><span class="sxs-lookup"><span data-stu-id="55701-116">In contrast, the following example demonstrates how to call the **Delete** method on a **DataRow** to change its **RowState** to **Deleted**.</span></span>  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 <span data-ttu-id="55701-117">Bir satır silinmek üzere işaretlenmiş ve çağırmanız **AcceptChanges** yöntemi **DataTable** nesne satır kaldırılır **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="55701-117">If a row is marked for deletion and you call the **AcceptChanges** method of the **DataTable** object, the row is removed from the **DataTable**.</span></span> <span data-ttu-id="55701-118">Buna karşılık, çağırırsanız **RejectChanges**, **RowState** satırının ne olarak işaretlenen önce haline döner **silinmiş**.</span><span class="sxs-lookup"><span data-stu-id="55701-118">In contrast, if you call **RejectChanges**, the **RowState** of the row reverts to what it was before being marked as **Deleted**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55701-119">Varsa **RowState** , bir **DataRow** olan **eklenen**, yani yalnızca eklendi tabloya ve ardından olarak işaretlenmiş **silinmiş**, bu tablosundan kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="55701-119">If the **RowState** of a **DataRow** is **Added**, meaning it has just been added to the table, and it is then marked as **Deleted**, it is removed from the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55701-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55701-120">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="55701-121">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="55701-121">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="55701-122">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="55701-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
