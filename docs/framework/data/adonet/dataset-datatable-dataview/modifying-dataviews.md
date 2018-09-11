---
title: DataView değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 3b1e0cbfc6118ad9ca670f5d91183b78b2c99d89
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268542"
---
# <a name="modifying-dataviews"></a><span data-ttu-id="6dccc-102">DataView değiştirme</span><span class="sxs-lookup"><span data-stu-id="6dccc-102">Modifying DataViews</span></span>
<span data-ttu-id="6dccc-103">Kullanabileceğiniz <xref:System.Data.DataView> eklemek, silmek veya temel tablodaki veri satırlarının değiştirin.</span><span class="sxs-lookup"><span data-stu-id="6dccc-103">You can use the <xref:System.Data.DataView> to add, delete, or modify rows of data in the underlying table.</span></span> <span data-ttu-id="6dccc-104">Kullanabilme **DataView** temel tablodaki verileri değiştirmek için üç Boole özelliklerinden birini ayarlayarak denetlenir **DataView**.</span><span class="sxs-lookup"><span data-stu-id="6dccc-104">The ability to use the **DataView** to modify data in the underlying table is controlled by setting one of three Boolean properties of the **DataView**.</span></span> <span data-ttu-id="6dccc-105">Bu özellikleri <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, ve <xref:System.Data.DataView.AllowDelete%2A>.</span><span class="sxs-lookup"><span data-stu-id="6dccc-105">These properties are <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, and <xref:System.Data.DataView.AllowDelete%2A>.</span></span> <span data-ttu-id="6dccc-106">Bunlar ayarlandığından **true** varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="6dccc-106">They are set to **true** by default.</span></span>  
  
 <span data-ttu-id="6dccc-107">Varsa **AllowNew** olduğu **true**, kullanabileceğiniz <xref:System.Data.DataView.AddNew%2A> yöntemi **DataView** yeni bir <xref:System.Data.DataRowView>.</span><span class="sxs-lookup"><span data-stu-id="6dccc-107">If **AllowNew** is **true**, you can use the <xref:System.Data.DataView.AddNew%2A> method of the **DataView** to create a new <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="6dccc-108">Yeni bir satır olmadığına dikkat edin, aslında eklenen temel alınan <xref:System.Data.DataTable> kadar <xref:System.Data.DataRowView.EndEdit%2A> yöntemi **DataRowView** çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6dccc-108">Note that a new row is not actually added to the underlying <xref:System.Data.DataTable> until the <xref:System.Data.DataRowView.EndEdit%2A> method of the **DataRowView** is called.</span></span> <span data-ttu-id="6dccc-109">Varsa <xref:System.Data.DataRowView.CancelEdit%2A> yöntemi **DataRowView** olan çağrılır, yeni satır atılır.</span><span class="sxs-lookup"><span data-stu-id="6dccc-109">If the <xref:System.Data.DataRowView.CancelEdit%2A> method of the **DataRowView** is called, the new row is discarded.</span></span> <span data-ttu-id="6dccc-110">Ayrıca tek düzen unutmayın **DataRowView** birer güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="6dccc-110">Note also that you can edit only one **DataRowView** at a time.</span></span> <span data-ttu-id="6dccc-111">Eğer **AddNew** veya **BeginEdit** yöntemi **DataRowView** bekleyen satır bulunduğu sürece **EndEdit** üzerinde örtük olarak çağırılamaz Bekleyen satır.</span><span class="sxs-lookup"><span data-stu-id="6dccc-111">If you call the **AddNew** or **BeginEdit** method of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="6dccc-112">Zaman **EndEdit** olan çağrılır, değişiklikler temel alınan uygulanır **DataTable** ve daha sonra olabilir kaydedilmiş veya kullanarak **AcceptChanges** veya  **RejectChanges** yöntemlerinin **DataTable**, **veri kümesi**, veya **DataRow** nesne.</span><span class="sxs-lookup"><span data-stu-id="6dccc-112">When **EndEdit** is called, the changes are applied to the underlying **DataTable** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="6dccc-113">Varsa **AllowNew** olduğu **false**, eğer bir özel durum **AddNew** yöntemi **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="6dccc-113">If **AllowNew** is **false**, an exception is thrown if you call the **AddNew** method of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="6dccc-114">Varsa **AllowEdit** olduğu **true**, içeriğini değiştirebileceğiniz bir **DataRow** aracılığıyla **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="6dccc-114">If **AllowEdit** is **true**, you can modify the contents of a **DataRow** via the **DataRowView**.</span></span> <span data-ttu-id="6dccc-115">Kullanarak temel alınan satır için değişiklikleri doğrulayabilirsiniz **DataRowView.EndEdit** kullanarak değişiklikleri veya reddetme **DataRowView.CancelEdit**.</span><span class="sxs-lookup"><span data-stu-id="6dccc-115">You can confirm changes to the underlying row using **DataRowView.EndEdit** or reject the changes using **DataRowView.CancelEdit**.</span></span> <span data-ttu-id="6dccc-116">Bir kerede yalnızca bir satır düzenlenebilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6dccc-116">Note that only one row can be edited at a time.</span></span> <span data-ttu-id="6dccc-117">Çağırırsanız **AddNew** veya **BeginEdit** yöntemlerinin **DataRowView** bekleyen satır bulunduğu sürece **EndEdit** üzerinde örtük olarak çağırılamaz Bekleyen satır.</span><span class="sxs-lookup"><span data-stu-id="6dccc-117">If you call the **AddNew** or **BeginEdit** methods of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="6dccc-118">Zaman **EndEdit** çağrılır, önerilen değişikliklerin yerleştirildiğinde **geçerli** arka plandaki satır sürümü **DataRow** ve daha sonra olabilir kaydedilmiş veya kullanarakreddetti **AcceptChanges** veya **RejectChanges** yöntemlerinin **DataTable**, **veri kümesi**, veya **DataRow** nesne.</span><span class="sxs-lookup"><span data-stu-id="6dccc-118">When **EndEdit** is called, proposed changes are placed in the **Current** row version of the underlying **DataRow** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="6dccc-119">Varsa **AllowEdit** olduğu **false**, bir değer değiştirmeyi denerseniz bir özel durum **DataView**.</span><span class="sxs-lookup"><span data-stu-id="6dccc-119">If **AllowEdit** is **false**, an exception is thrown if you attempt to modify a value in the **DataView**.</span></span>  
  
 <span data-ttu-id="6dccc-120">Var olan bir zaman **DataRowView** düzenlenirse, temel alınan olayları **DataTable** yine de önerilen değişiklikleri gerçekleştirilecektir.</span><span class="sxs-lookup"><span data-stu-id="6dccc-120">When an existing **DataRowView** is being edited, events of the underlying **DataTable** will still be raised with the proposed changes.</span></span> <span data-ttu-id="6dccc-121">Eğer unutmayın **EndEdit** veya **CancelEdit** temel üzerinde **DataRow**, bekleyen değişiklikleri uygulanan veya olup olmamasına bakılmaksızın iptal  **EndEdit** veya **CancelEdit** üzerinde çağrılır **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="6dccc-121">Note that if you call **EndEdit** or **CancelEdit** on the underlying **DataRow**, pending changes will be applied or canceled regardless of whether **EndEdit** or **CancelEdit** is called on the **DataRowView**.</span></span>  
  
 <span data-ttu-id="6dccc-122">Varsa **AllowDelete** olduğu **true**, satırlardan silebilirsiniz **DataView** kullanarak **Sil** yöntemi **DataView**  veya **DataRowView** nesne ve satırları silindi temel **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="6dccc-122">If **AllowDelete** is **true**, you can delete rows from the **DataView** by using the **Delete** method of the **DataView** or **DataRowView** object, and the rows are deleted from the underlying **DataTable**.</span></span> <span data-ttu-id="6dccc-123">Daha sonra tamamlama veya reddetme kullanarak siler **AcceptChanges** veya **RejectChanges** sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="6dccc-123">You can later commit or reject the deletes using **AcceptChanges** or **RejectChanges** respectively.</span></span> <span data-ttu-id="6dccc-124">Varsa **AllowDelete** olduğu **false**, çağırırsanız bir özel durum **Sil** yöntemi **DataView** veya  **DataRowView**.</span><span class="sxs-lookup"><span data-stu-id="6dccc-124">If **AllowDelete** is **false**, an exception is thrown if you call the **Delete** method of the **DataView** or **DataRowView**.</span></span>  
  
 <span data-ttu-id="6dccc-125">Aşağıdaki kod örneği kullanarak devre dışı bırakır. **DataView** için delete satırları ve temel alınan kullanarak tablo için yeni bir satır ekler **DataView**.</span><span class="sxs-lookup"><span data-stu-id="6dccc-125">The following code example disables using the **DataView** to delete rows  and adds a new row to the underlying table using the **DataView**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6dccc-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6dccc-126">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 <xref:System.Data.DataRowView>  
 [<span data-ttu-id="6dccc-127">DataViews</span><span class="sxs-lookup"><span data-stu-id="6dccc-127">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="6dccc-128">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="6dccc-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
