---
description: 'Hakkında daha fazla bilgi edinin: DataView değiştirme'
title: DataView Değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: e0f62c0b8553cd4b83c28da99b8bdec316c8a91d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651840"
---
# <a name="modifying-dataviews"></a><span data-ttu-id="3bf56-103">DataView Değiştirme</span><span class="sxs-lookup"><span data-stu-id="3bf56-103">Modifying DataViews</span></span>

<span data-ttu-id="3bf56-104"><xref:System.Data.DataView>Temel tablodaki veri satırlarını eklemek, silmek veya değiştirmek için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bf56-104">You can use the <xref:System.Data.DataView> to add, delete, or modify rows of data in the underlying table.</span></span> <span data-ttu-id="3bf56-105">Temel tablodaki verileri değiştirmek için **DataView** kullanma özelliği, **DataView**'ın üç Boole özelliğinden biri ayarlanarak denetlenir.</span><span class="sxs-lookup"><span data-stu-id="3bf56-105">The ability to use the **DataView** to modify data in the underlying table is controlled by setting one of three Boolean properties of the **DataView**.</span></span> <span data-ttu-id="3bf56-106">Bu özellikler <xref:System.Data.DataView.AllowNew%2A> , <xref:System.Data.DataView.AllowEdit%2A> ve ' dir <xref:System.Data.DataView.AllowDelete%2A> .</span><span class="sxs-lookup"><span data-stu-id="3bf56-106">These properties are <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, and <xref:System.Data.DataView.AllowDelete%2A>.</span></span> <span data-ttu-id="3bf56-107">Varsayılan olarak **true** olarak ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3bf56-107">They are set to **true** by default.</span></span>  
  
 <span data-ttu-id="3bf56-108">**AllowNew** **true** ise, <xref:System.Data.DataView.AddNew%2A> Yeni bir oluşturmak için **DataView** yöntemini kullanabilirsiniz <xref:System.Data.DataRowView> .</span><span class="sxs-lookup"><span data-stu-id="3bf56-108">If **AllowNew** is **true**, you can use the <xref:System.Data.DataView.AddNew%2A> method of the **DataView** to create a new <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="3bf56-109">Yeni bir satırın, <xref:System.Data.DataTable> <xref:System.Data.DataRowView.EndEdit%2A> **DataRowView** 'ın yöntemi çağrılana kadar temeldeki temel içine eklenmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3bf56-109">Note that a new row is not actually added to the underlying <xref:System.Data.DataTable> until the <xref:System.Data.DataRowView.EndEdit%2A> method of the **DataRowView** is called.</span></span> <span data-ttu-id="3bf56-110"><xref:System.Data.DataRowView.CancelEdit%2A> **DataRowView** 'ın yöntemi çağrılırsa, yeni satır atılır.</span><span class="sxs-lookup"><span data-stu-id="3bf56-110">If the <xref:System.Data.DataRowView.CancelEdit%2A> method of the **DataRowView** is called, the new row is discarded.</span></span> <span data-ttu-id="3bf56-111">Aynı anda yalnızca bir **DataRowView** öğesini düzenleyebileceğinizi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3bf56-111">Note also that you can edit only one **DataRowView** at a time.</span></span> <span data-ttu-id="3bf56-112">Bekleyen bir satır varken **DataRowView** 'ın **AddNew** veya **BeginEdit** metodunu çağırırsanız, **EndEdit** , bekleyen satırda örtük olarak çağırılır.</span><span class="sxs-lookup"><span data-stu-id="3bf56-112">If you call the **AddNew** or **BeginEdit** method of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="3bf56-113">**EndEdit** çağrıldığında, değişiklikler temel alınan **DataTable** 'a uygulanır ve daha sonra **DataTable**, **DataSet** veya **DataRow** nesnesinin **AcceptChanges** veya **RejectChanges** yöntemleri kullanılarak gerçekleştirilebilir veya reddedilebilir.</span><span class="sxs-lookup"><span data-stu-id="3bf56-113">When **EndEdit** is called, the changes are applied to the underlying **DataTable** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="3bf56-114">**AllowNew** **yanlış** Ise, **DataRowView**'ın **AddNew** metodunu çağırdığınızda bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3bf56-114">If **AllowNew** is **false**, an exception is thrown if you call the **AddNew** method of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="3bf56-115">**AllowEdit** **true** ise, bir **DataRow** 'ın içeriğini **DataRowView** aracılığıyla değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bf56-115">If **AllowEdit** is **true**, you can modify the contents of a **DataRow** via the **DataRowView**.</span></span> <span data-ttu-id="3bf56-116">**DataRowView. EndEdit** kullanarak temel alınan satırdaki değişiklikleri doğrulayabilirsiniz veya **DataRowView. CancelEdit** kullanarak değişiklikleri reddedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bf56-116">You can confirm changes to the underlying row using **DataRowView.EndEdit** or reject the changes using **DataRowView.CancelEdit**.</span></span> <span data-ttu-id="3bf56-117">Tek seferde yalnızca bir satırın düzenlenebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3bf56-117">Note that only one row can be edited at a time.</span></span> <span data-ttu-id="3bf56-118">Bekleyen bir satır varken **DataRowView** 'ın **AddNew** veya **BeginEdit** yöntemlerini çağırırsanız, **EndEdit** , bekleyen satırda örtük olarak çağırılır.</span><span class="sxs-lookup"><span data-stu-id="3bf56-118">If you call the **AddNew** or **BeginEdit** methods of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="3bf56-119">**EndEdit** çağrıldığında, önerilen değişiklikler temel alınan **DataRow** 'ın **geçerli** satır sürümüne yerleştirilir ve daha sonra **DataTable**, **DataSet** veya **DataRow** nesnesinin **AcceptChanges** veya **RejectChanges** yöntemleri kullanılarak uygulanabilir veya reddedilebilir.</span><span class="sxs-lookup"><span data-stu-id="3bf56-119">When **EndEdit** is called, proposed changes are placed in the **Current** row version of the underlying **DataRow** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="3bf56-120">**AllowEdit** **false** ise, **DataView** içindeki bir değeri değiştirmeye çalışırsanız bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3bf56-120">If **AllowEdit** is **false**, an exception is thrown if you attempt to modify a value in the **DataView**.</span></span>  
  
 <span data-ttu-id="3bf56-121">Varolan bir **DataRowView** düzenlenirken, temel alınan **DataTable** olayları, önerilen değişikliklerle yine de oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3bf56-121">When an existing **DataRowView** is being edited, events of the underlying **DataTable** will still be raised with the proposed changes.</span></span> <span data-ttu-id="3bf56-122">Temel alınan **DataRow** üzerinde **EndEdit** veya **CancelEdit** çağırırsanız, bekleyen değişikliklerin, **DataRowView** üzerinde **EndEdit** veya **CancelEdit** çağrılıp çağrılmadığına bakılmaksızın uygulanacağını veya iptal edildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3bf56-122">Note that if you call **EndEdit** or **CancelEdit** on the underlying **DataRow**, pending changes will be applied or canceled regardless of whether **EndEdit** or **CancelEdit** is called on the **DataRowView**.</span></span>  
  
 <span data-ttu-id="3bf56-123">**AllowDelete** **true** ise **DataView veya** **DataRowView** nesnesinin **Delete** yöntemini kullanarak **DataView** nesnesinden satırları silebilirsiniz ve satırlar temeldeki **DataTable**'dan silinir.</span><span class="sxs-lookup"><span data-stu-id="3bf56-123">If **AllowDelete** is **true**, you can delete rows from the **DataView** by using the **Delete** method of the **DataView** or **DataRowView** object, and the rows are deleted from the underlying **DataTable**.</span></span> <span data-ttu-id="3bf56-124">Daha sonra, sırasıyla **AcceptChanges** veya **RejectChanges** kullanarak silmeleri kaydedebilir veya reddedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bf56-124">You can later commit or reject the deletes using **AcceptChanges** or **RejectChanges** respectively.</span></span> <span data-ttu-id="3bf56-125">**AllowDelete** **false** Ise, **DataView** veya **DataRowView**'ın **Delete** yöntemini çağırdığınızda bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3bf56-125">If **AllowDelete** is **false**, an exception is thrown if you call the **Delete** method of the **DataView** or **DataRowView**.</span></span>  
  
 <span data-ttu-id="3bf56-126">Aşağıdaki kod örneği, satırları silmek için **DataView** kullanımını devre dışı bırakır ve **DataView** kullanarak temel tabloya yeni bir satır ekler.</span><span class="sxs-lookup"><span data-stu-id="3bf56-126">The following code example disables using the **DataView** to delete rows  and adds a new row to the underlying table using the **DataView**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3bf56-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bf56-127">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="3bf56-128">DataViews</span><span class="sxs-lookup"><span data-stu-id="3bf56-128">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="3bf56-129">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3bf56-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
