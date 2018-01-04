---
title: "DataView değiştirme"
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
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 921707b07f1e8c8a9208df7de74512325f3027d2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-dataviews"></a><span data-ttu-id="10ae4-102">DataView değiştirme</span><span class="sxs-lookup"><span data-stu-id="10ae4-102">Modifying DataViews</span></span>
<span data-ttu-id="10ae4-103">Kullanabileceğiniz <xref:System.Data.DataView> eklemek, silmek veya temel tablodaki veri satırlarının değiştirin.</span><span class="sxs-lookup"><span data-stu-id="10ae4-103">You can use the <xref:System.Data.DataView> to add, delete, or modify rows of data in the underlying table.</span></span> <span data-ttu-id="10ae4-104">Kullanma yeteneğini **DataView** temel tablodaki verileri değiştirmek için üç Boolean özelliklerinden birini ayarlanmasıyla denetlenir **DataView**.</span><span class="sxs-lookup"><span data-stu-id="10ae4-104">The ability to use the **DataView** to modify data in the underlying table is controlled by setting one of three Boolean properties of the **DataView**.</span></span> <span data-ttu-id="10ae4-105">Bu özellikleri <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, ve <xref:System.Data.DataView.AllowDelete%2A>.</span><span class="sxs-lookup"><span data-stu-id="10ae4-105">These properties are <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, and <xref:System.Data.DataView.AllowDelete%2A>.</span></span> <span data-ttu-id="10ae4-106">Bunlar ayarlamak **true** varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="10ae4-106">They are set to **true** by default.</span></span>  
  
 <span data-ttu-id="10ae4-107">Varsa **AllowNew** olan **true**, kullanabileceğiniz <xref:System.Data.DataView.AddNew%2A> yöntemi **DataView** yeni <xref:System.Data.DataRowView>.</span><span class="sxs-lookup"><span data-stu-id="10ae4-107">If **AllowNew** is **true**, you can use the <xref:System.Data.DataView.AddNew%2A> method of the **DataView** to create a new <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="10ae4-108">Yeni bir satır olmadığına dikkat edin gerçekte eklenen temel <xref:System.Data.DataTable> kadar <xref:System.Data.DataRowView.EndEdit%2A> yöntemi **DataRowView** olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="10ae4-108">Note that a new row is not actually added to the underlying <xref:System.Data.DataTable> until the <xref:System.Data.DataRowView.EndEdit%2A> method of the **DataRowView** is called.</span></span> <span data-ttu-id="10ae4-109">Varsa <xref:System.Data.DataRowView.CancelEdit%2A> yöntemi **DataRowView** olan adı verilen yeni satır atılır.</span><span class="sxs-lookup"><span data-stu-id="10ae4-109">If the <xref:System.Data.DataRowView.CancelEdit%2A> method of the **DataRowView** is called, the new row is discarded.</span></span> <span data-ttu-id="10ae4-110">Ayrıca tek düzen unutmayın **DataRowView** birer birer.</span><span class="sxs-lookup"><span data-stu-id="10ae4-110">Note also that you can edit only one **DataRowView** at a time.</span></span> <span data-ttu-id="10ae4-111">Çağırırsanız **AddNew** veya **BeginEdit** yöntemi **DataRowView** bekleyen bir satır var, ancak **EndEdit** üzerinde örtük olarak adlandırılır Bekleyen satır.</span><span class="sxs-lookup"><span data-stu-id="10ae4-111">If you call the **AddNew** or **BeginEdit** method of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="10ae4-112">Zaman **EndEdit** olduğu olarak adlandırılan, değişiklikler temel uygulanır **DataTable** ve daha sonra olabilir kabul edildiğini veya kullanarak **AcceptChanges** veya  **RejectChanges** yöntemlerinin **DataTable**, **DataSet**, veya **DataRow** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="10ae4-112">When **EndEdit** is called, the changes are applied to the underlying **DataTable** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="10ae4-113">Varsa **AllowNew** olan **false**, çağırırsanız bir özel durum **AddNew** yöntemi **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="10ae4-113">If **AllowNew** is **false**, an exception is thrown if you call the **AddNew** method of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="10ae4-114">Varsa **AllowEdit** olan **true**, içeriğini değiştirebileceğiniz bir **DataRow** aracılığıyla **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="10ae4-114">If **AllowEdit** is **true**, you can modify the contents of a **DataRow** via the **DataRowView**.</span></span> <span data-ttu-id="10ae4-115">Temel alınan satır kullanarak değişiklikleri onaylayabilirsiniz **DataRowView.EndEdit** kullanarak değişiklikleri veya reddetme **DataRowView.CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="10ae4-115">You can confirm changes to the underlying row using **DataRowView.EndEdit** or reject the changes using **DataRowView.CancelEdit**.</span></span> <span data-ttu-id="10ae4-116">Aynı anda yalnızca bir satır düzenlenebilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="10ae4-116">Note that only one row can be edited at a time.</span></span> <span data-ttu-id="10ae4-117">Çağırırsanız **AddNew** veya **BeginEdit** yöntemlerinin **DataRowView** bekleyen bir satır var, ancak **EndEdit** üzerinde örtük olarak adlandırılır Bekleyen satır.</span><span class="sxs-lookup"><span data-stu-id="10ae4-117">If you call the **AddNew** or **BeginEdit** methods of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="10ae4-118">Zaman **EndEdit** olarak adlandırılır, önerilen değişiklikleri yerleştirilir **geçerli** temel satır sürümü **DataRow** ve daha sonra olabilir kabul edildiğini veya kullanarakreddetti **AcceptChanges** veya **RejectChanges** yöntemlerinin **DataTable**, **DataSet**, veya **DataRow** nesne.</span><span class="sxs-lookup"><span data-stu-id="10ae4-118">When **EndEdit** is called, proposed changes are placed in the **Current** row version of the underlying **DataRow** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="10ae4-119">Varsa **AllowEdit** olan **false**, bir değer değiştirmeyi denerseniz bir özel durum **DataView**.</span><span class="sxs-lookup"><span data-stu-id="10ae4-119">If **AllowEdit** is **false**, an exception is thrown if you attempt to modify a value in the **DataView**.</span></span>  
  
 <span data-ttu-id="10ae4-120">Var olan **DataRowView** düzenlenirse, arka plandaki olayları **DataTable** önerilen değişikliklerle hala gerçekleştirilecektir.</span><span class="sxs-lookup"><span data-stu-id="10ae4-120">When an existing **DataRowView** is being edited, events of the underlying **DataTable** will still be raised with the proposed changes.</span></span> <span data-ttu-id="10ae4-121">Çağırırsanız unutmayın **EndEdit** veya **CancelEdit** arka plandaki üzerinde **DataRow**, bekleyen değişiklikler uygulanan veya olup olmamasına bakılmaksızın iptal  **EndEdit** veya **CancelEdit** üzerinde adlı **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="10ae4-121">Note that if you call **EndEdit** or **CancelEdit** on the underlying **DataRow**, pending changes will be applied or canceled regardless of whether **EndEdit** or **CancelEdit** is called on the **DataRowView**.</span></span>  
  
 <span data-ttu-id="10ae4-122">Varsa **AllowDelete** olan **true**, satırları silebilirsiniz **DataView** kullanarak **silmek** yöntemi **DataView**  veya **DataRowView** nesne ve satırları silinir arka plandaki gelen **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="10ae4-122">If **AllowDelete** is **true**, you can delete rows from the **DataView** by using the **Delete** method of the **DataView** or **DataRowView** object, and the rows are deleted from the underlying **DataTable**.</span></span> <span data-ttu-id="10ae4-123">Daha sonra yürütün veya kullanarak siler Reddet **AcceptChanges** veya **RejectChanges** sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="10ae4-123">You can later commit or reject the deletes using **AcceptChanges** or **RejectChanges** respectively.</span></span> <span data-ttu-id="10ae4-124">Varsa **AllowDelete** olan **false**, çağırırsanız bir özel durum **silmek** yöntemi **DataView** veya  **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="10ae4-124">If **AllowDelete** is **false**, an exception is thrown if you call the **Delete** method of the **DataView** or **DataRowView**.</span></span>  
  
 <span data-ttu-id="10ae4-125">Aşağıdaki kod örneğinde devre dışı bırakır **DataView** için delete satırlar ve temel alınan tabloda kullanmaya yeni bir satır ekler **DataView**.</span><span class="sxs-lookup"><span data-stu-id="10ae4-125">The following code example disables using the **DataView** to delete rows  and adds a new row to the underlying table using the **DataView**.</span></span>  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## <a name="see-also"></a><span data-ttu-id="10ae4-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="10ae4-126">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [<span data-ttu-id="10ae4-127">DataViews</span><span class="sxs-lookup"><span data-stu-id="10ae4-127">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="10ae4-128">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="10ae4-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
