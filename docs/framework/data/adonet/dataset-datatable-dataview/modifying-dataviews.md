---
title: DataView Değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 0b2bfd1b0490572e78c8ce365491a8d48db87684
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204576"
---
# <a name="modifying-dataviews"></a><span data-ttu-id="3beea-102">DataView Değiştirme</span><span class="sxs-lookup"><span data-stu-id="3beea-102">Modifying DataViews</span></span>
<span data-ttu-id="3beea-103">Temel tablodaki veri satırlarını <xref:System.Data.DataView> eklemek, silmek veya değiştirmek için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3beea-103">You can use the <xref:System.Data.DataView> to add, delete, or modify rows of data in the underlying table.</span></span> <span data-ttu-id="3beea-104">Temel tablodaki verileri değiştirmek için **DataView** kullanma özelliği, **DataView**'ın üç Boole özelliğinden biri ayarlanarak denetlenir.</span><span class="sxs-lookup"><span data-stu-id="3beea-104">The ability to use the **DataView** to modify data in the underlying table is controlled by setting one of three Boolean properties of the **DataView**.</span></span> <span data-ttu-id="3beea-105">Bu özellikler, <xref:System.Data.DataView.AllowNew%2A> <xref:System.Data.DataView.AllowEdit%2A> ve<xref:System.Data.DataView.AllowDelete%2A>' dir.</span><span class="sxs-lookup"><span data-stu-id="3beea-105">These properties are <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, and <xref:System.Data.DataView.AllowDelete%2A>.</span></span> <span data-ttu-id="3beea-106">Varsayılan olarak **true** olarak ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3beea-106">They are set to **true** by default.</span></span>  
  
 <span data-ttu-id="3beea-107">**AllowNew** **true**ise, yeni <xref:System.Data.DataView.AddNew%2A> <xref:System.Data.DataRowView>bir oluşturmak için **DataView** yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3beea-107">If **AllowNew** is **true**, you can use the <xref:System.Data.DataView.AddNew%2A> method of the **DataView** to create a new <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="3beea-108">Yeni bir satırın, <xref:System.Data.DataTable> **DataRowView** 'ın <xref:System.Data.DataRowView.EndEdit%2A> yöntemi çağrılana kadar temeldeki temel içine eklenmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3beea-108">Note that a new row is not actually added to the underlying <xref:System.Data.DataTable> until the <xref:System.Data.DataRowView.EndEdit%2A> method of the **DataRowView** is called.</span></span> <span data-ttu-id="3beea-109"><xref:System.Data.DataRowView.CancelEdit%2A> **DataRowView** 'ın yöntemi çağrılırsa, yeni satır atılır.</span><span class="sxs-lookup"><span data-stu-id="3beea-109">If the <xref:System.Data.DataRowView.CancelEdit%2A> method of the **DataRowView** is called, the new row is discarded.</span></span> <span data-ttu-id="3beea-110">Aynı anda yalnızca bir **DataRowView** öğesini düzenleyebileceğinizi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3beea-110">Note also that you can edit only one **DataRowView** at a time.</span></span> <span data-ttu-id="3beea-111">Bekleyen bir satır varken **DataRowView** 'ın **AddNew** veya **BeginEdit** metodunu çağırırsanız, **EndEdit** , bekleyen satırda örtük olarak çağırılır.</span><span class="sxs-lookup"><span data-stu-id="3beea-111">If you call the **AddNew** or **BeginEdit** method of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="3beea-112">**EndEdit** çağrıldığında, değişiklikler temel alınan **DataTable** 'a uygulanır ve daha sonra **DataTable**, **DataSet veya** **veri kümesinin AcceptChanges veya RejectChanges yöntemleri kullanılarak uygulanabilir veya reddedilebilir. DataRow** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="3beea-112">When **EndEdit** is called, the changes are applied to the underlying **DataTable** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="3beea-113">**AllowNew** **yanlış**Ise, **DataRowView**'ın **AddNew** metodunu çağırdığınızda bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3beea-113">If **AllowNew** is **false**, an exception is thrown if you call the **AddNew** method of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="3beea-114">**AllowEdit** **true**ise, bir **DataRow** 'ın içeriğini **DataRowView**aracılığıyla değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3beea-114">If **AllowEdit** is **true**, you can modify the contents of a **DataRow** via the **DataRowView**.</span></span> <span data-ttu-id="3beea-115">**DataRowView. EndEdit** kullanarak temel alınan satırdaki değişiklikleri doğrulayabilirsiniz veya **DataRowView. CancelEdit**kullanarak değişiklikleri reddedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3beea-115">You can confirm changes to the underlying row using **DataRowView.EndEdit** or reject the changes using **DataRowView.CancelEdit**.</span></span> <span data-ttu-id="3beea-116">Tek seferde yalnızca bir satırın düzenlenebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3beea-116">Note that only one row can be edited at a time.</span></span> <span data-ttu-id="3beea-117">Bekleyen bir satır varken **DataRowView** 'ın **AddNew** veya **BeginEdit** yöntemlerini çağırırsanız, **EndEdit** , bekleyen satırda örtük olarak çağırılır.</span><span class="sxs-lookup"><span data-stu-id="3beea-117">If you call the **AddNew** or **BeginEdit** methods of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="3beea-118">**EndEdit** çağrıldığında, önerilen değişiklikler temel alınan **DataRow** 'ın **geçerli** satır sürümüne yerleştirilir ve daha sonra, **' nin AcceptChanges veya RejectChanges yöntemleri kullanılarak gerçekleştirilebilir DataTable**, **DataSet**veya **DataRow** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="3beea-118">When **EndEdit** is called, proposed changes are placed in the **Current** row version of the underlying **DataRow** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="3beea-119">**AllowEdit** **false**ise, **DataView**içindeki bir değeri değiştirmeye çalışırsanız bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3beea-119">If **AllowEdit** is **false**, an exception is thrown if you attempt to modify a value in the **DataView**.</span></span>  
  
 <span data-ttu-id="3beea-120">Varolan bir **DataRowView** düzenlenirken, temel alınan **DataTable** olayları, önerilen değişikliklerle yine de oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3beea-120">When an existing **DataRowView** is being edited, events of the underlying **DataTable** will still be raised with the proposed changes.</span></span> <span data-ttu-id="3beea-121">Temel alınan **DataRow**üzerinde **EndEdit** veya **CancelEdit** çağırırsanız, bekleyen değişikliklerin, **DataRowView**üzerinde **EndEdit** veya **CancelEdit** çağrılıp çağrılmadığına bakılmaksızın uygulanacağını veya iptal edildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3beea-121">Note that if you call **EndEdit** or **CancelEdit** on the underlying **DataRow**, pending changes will be applied or canceled regardless of whether **EndEdit** or **CancelEdit** is called on the **DataRowView**.</span></span>  
  
 <span data-ttu-id="3beea-122">**AllowDelete** **true**ise DataView veya **DataRowView** nesnesinin **Delete** yöntemini kullanarak **DataView** nesnesinden satırları silebilirsiniz ve satırlar temeldeki **DataTable**'dan silinir.</span><span class="sxs-lookup"><span data-stu-id="3beea-122">If **AllowDelete** is **true**, you can delete rows from the **DataView** by using the **Delete** method of the **DataView** or **DataRowView** object, and the rows are deleted from the underlying **DataTable**.</span></span> <span data-ttu-id="3beea-123">Daha sonra, sırasıyla **AcceptChanges** veya **RejectChanges** kullanarak silmeleri kaydedebilir veya reddedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3beea-123">You can later commit or reject the deletes using **AcceptChanges** or **RejectChanges** respectively.</span></span> <span data-ttu-id="3beea-124">**AllowDelete** **false**Ise, **DataView** veya **DataRowView**'ın **Delete** yöntemini çağırdığınızda bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3beea-124">If **AllowDelete** is **false**, an exception is thrown if you call the **Delete** method of the **DataView** or **DataRowView**.</span></span>  
  
 <span data-ttu-id="3beea-125">Aşağıdaki kod örneği, satırları silmek için **DataView** kullanımını devre dışı bırakır ve **DataView**kullanarak temel tabloya yeni bir satır ekler.</span><span class="sxs-lookup"><span data-stu-id="3beea-125">The following code example disables using the **DataView** to delete rows  and adds a new row to the underlying table using the **DataView**.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3beea-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3beea-126">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="3beea-127">DataViews</span><span class="sxs-lookup"><span data-stu-id="3beea-127">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="3beea-128">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="3beea-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
