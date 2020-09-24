---
title: DataTable Düzenlemeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 4fdb19e7fa014bf4a7c924b1fbae53fa44de6e3c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153267"
---
# <a name="datatable-edits"></a><span data-ttu-id="ab97a-102">DataTable Düzenlemeleri</span><span class="sxs-lookup"><span data-stu-id="ab97a-102">DataTable Edits</span></span>

<span data-ttu-id="ab97a-103">İçindeki sütun değerlerinde değişiklik yaptığınızda <xref:System.Data.DataRow> , değişiklikler satırın geçerli durumuna hemen yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ab97a-103">When you make changes to column values in a <xref:System.Data.DataRow>, the changes are immediately placed in the current state of the row.</span></span> <span data-ttu-id="ab97a-104"><xref:System.Data.DataRowState>Daha sonra **değiştirildi**olarak ayarlanır ve değişiklikler <xref:System.Data.DataRow.AcceptChanges%2A> <xref:System.Data.DataRow.RejectChanges%2A> **DataRow**'ın veya yöntemleri kullanılarak kabul edilir veya reddedilir.</span><span class="sxs-lookup"><span data-stu-id="ab97a-104">The <xref:System.Data.DataRowState> is then set to **Modified**, and the changes are accepted or rejected using the <xref:System.Data.DataRow.AcceptChanges%2A> or <xref:System.Data.DataRow.RejectChanges%2A> methods of the **DataRow**.</span></span> <span data-ttu-id="ab97a-105">**DataRow** , siz de satırı düzenlediğinizde satırın durumunu askıya almak için kullanabileceğiniz üç yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="ab97a-105">The **DataRow** also provides three methods that you can use to suspend the state of the row while you are editing it.</span></span> <span data-ttu-id="ab97a-106">Bu yöntemler <xref:System.Data.DataRow.BeginEdit%2A> , <xref:System.Data.DataRow.EndEdit%2A> ve ' dir <xref:System.Data.DataRow.CancelEdit%2A> .</span><span class="sxs-lookup"><span data-stu-id="ab97a-106">These methods are <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, and <xref:System.Data.DataRow.CancelEdit%2A>.</span></span>  
  
 <span data-ttu-id="ab97a-107">**DataRow** içindeki sütun değerlerini doğrudan değiştirdiğinizde, **DataRow** **geçerli**, **varsayılan**ve **orijinal** satır sürümlerini kullanarak sütun değerlerini yönetir.</span><span class="sxs-lookup"><span data-stu-id="ab97a-107">When you modify column values in a **DataRow** directly, the **DataRow** manages the column values using the **Current**, **Default**, and **Original** row versions.</span></span> <span data-ttu-id="ab97a-108">Bu satır sürümlerinin yanı sıra, **BeginEdit**, **EndEdit**ve **CancelEdit** yöntemleri Dördüncü satır sürümünü kullanır: **önerilir**.</span><span class="sxs-lookup"><span data-stu-id="ab97a-108">In addition to these row versions, the **BeginEdit**, **EndEdit**, and **CancelEdit** methods use a fourth row version: **Proposed**.</span></span> <span data-ttu-id="ab97a-109">Satır sürümleri hakkında daha fazla bilgi için bkz. [Satır durumları ve satır sürümleri](row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="ab97a-109">For more information about row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="ab97a-110">**Önerilen** satır sürümü, **BeginEdit** çağırarak başlayan ve, **EndEdit** veya **CancelEdit** kullanarak ya da **AcceptChanges** ya da **RejectChanges**çağırarak biten bir düzenleme işlemi sırasında bulunur.</span><span class="sxs-lookup"><span data-stu-id="ab97a-110">The **Proposed** row version exists during an edit operation that begins by calling **BeginEdit** and that ends either by using **EndEdit** or **CancelEdit,** or by calling **AcceptChanges** or **RejectChanges**.</span></span>  
  
 <span data-ttu-id="ab97a-111">Düzenleme işlemi sırasında, **DataTable**'ın **ColumnChanged** olayında **ProposedValue** değerlendirerek ayrı sütunlara doğrulama mantığı uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab97a-111">During the edit operation, you can apply validation logic to individual columns by evaluating the **ProposedValue** in the **ColumnChanged** event of the **DataTable**.</span></span> <span data-ttu-id="ab97a-112">**ColumnChanged** olayı, **ProposedValue**ve ile değişen sütuna bir başvuru tutan **DataColumnChangeEventArgs** barındırır.</span><span class="sxs-lookup"><span data-stu-id="ab97a-112">The **ColumnChanged** event holds **DataColumnChangeEventArgs** that keep a reference to the column that is changing and to the **ProposedValue**.</span></span> <span data-ttu-id="ab97a-113">Önerilen değeri değerlendirdikten sonra, bunu değiştirebilir veya düzenlemeyi iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab97a-113">After you evaluate the proposed value, you can either modify it or cancel the edit.</span></span> <span data-ttu-id="ab97a-114">Düzenleme sona erdikten sonra satır **Önerilen** durumdan çıkar.</span><span class="sxs-lookup"><span data-stu-id="ab97a-114">When the edit is ended, the row moves out of the **Proposed** state.</span></span>  
  
 <span data-ttu-id="ab97a-115">**Sorguları**çağırarak veya **CancelEdit**çağırarak bu düzenlemeleri iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab97a-115">You can confirm edits by calling **EndEdit**, or you can cancel them by calling **CancelEdit**.</span></span> <span data-ttu-id="ab97a-116">**EndEdit** , düzenlemelerinizi Doğrulamalarken, **veri kümesinin** , **AcceptChanges** çağrısı yapılıncaya kadar değişiklikleri gerçekten kabul etmediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ab97a-116">Note that while **EndEdit** does confirm your edits, the **DataSet** does not actually accept the changes until **AcceptChanges** is called.</span></span> <span data-ttu-id="ab97a-117">Ayrıca, Edit öğesini **EndEdit** veya **CancelEdit**Ile sonlandırmadan önce **AcceptChanges** 'ı çağırdığınızda, düzenleme sonlandırılır ve **Önerilen** satır değerleri hem **geçerli** hem de **orijinal** satır sürümleri için kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="ab97a-117">Note also that if you call **AcceptChanges** before you have ended the edit with **EndEdit** or **CancelEdit**, the edit is ended and the **Proposed** row values are accepted for both the **Current** and **Original** row versions.</span></span> <span data-ttu-id="ab97a-118">Aynı şekilde, **RejectChanges** öğesini çağırmak düzenlemeyi sonlandırır ve **geçerli** ve **Önerilen** satır sürümlerini atar.</span><span class="sxs-lookup"><span data-stu-id="ab97a-118">In the same manner, calling **RejectChanges** ends the edit and discards the **Current** and **Proposed** row versions.</span></span> <span data-ttu-id="ab97a-119">**AcceptChanges** veya **RejectChanges** çağrıldıktan sonra **EndEdit** veya **CancelEdit** çağırmak, düzenleme zaten sona erdiğinden hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="ab97a-119">Calling **EndEdit** or **CancelEdit** after calling **AcceptChanges** or **RejectChanges** has no effect because the edit has already ended.</span></span>  
  
 <span data-ttu-id="ab97a-120">Aşağıdaki örnek, BeginEdit ve **CancelEdit**ile **BeginEdit** 'in **EndEdit** nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab97a-120">The following example demonstrates how to use **BeginEdit** with **EndEdit** and **CancelEdit**.</span></span> <span data-ttu-id="ab97a-121">Örnek ayrıca **ColumnChanged** olaydaki **ProposedValue** denetimini denetler ve düzenlemeyi iptal edip etmeyeceğine karar verir.</span><span class="sxs-lookup"><span data-stu-id="ab97a-121">The example also checks the **ProposedValue** in the **ColumnChanged** event and decides whether to cancel the edit.</span></span>  
  
```vb  
Dim workTable As DataTable = New DataTable  
workTable.Columns.Add("LastName", Type.GetType("System.String"))  
  
AddHandler workTable.ColumnChanged, _  
  New DataColumnChangeEventHandler(AddressOf OnColumnChanged)  
  
Dim workRow As DataRow = workTable.NewRow()  
workRow(0) = "Smith"  
workTable.Rows.Add(workRow)  
  
workRow.BeginEdit()  
' Causes the ColumnChanged event to write a message and cancel the edit.  
workRow(0) = ""
workRow.EndEdit()  
  
' Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow(0), workRow.RowState)  
  
Private Shared Sub OnColumnChanged( _  
  sender As Object, args As DataColumnChangeEventArgs)  
  If args.Column.ColumnName = "LastName" Then  
    If args.ProposedValue.ToString() = "" Then  
      Console.WriteLine("Last Name cannot be blank.  Edit canceled.")  
      args.Row.CancelEdit()  
    End If  
  End If  
End Sub  
```  
  
```csharp  
DataTable workTable  = new DataTable();  
workTable.Columns.Add("LastName", typeof(String));  
  
workTable.ColumnChanged +=
  new DataColumnChangeEventHandler(OnColumnChanged);  
  
DataRow workRow = workTable.NewRow();  
workRow[0] = "Smith";  
workTable.Rows.Add(workRow);  
  
workRow.BeginEdit();  
// Causes the ColumnChanged event to write a message and cancel the edit.  
workRow[0] = "";
workRow.EndEdit();  
  
// Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow[0], workRow.RowState);
  
protected static void OnColumnChanged(  
  Object sender, DataColumnChangeEventArgs args)  
{  
  if (args.Column.ColumnName == "LastName")  
    if (args.ProposedValue.ToString() == "")  
    {  
      Console.WriteLine("Last Name cannot be blank. Edit canceled.");  
      args.Row.CancelEdit();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab97a-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab97a-122">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [<span data-ttu-id="ab97a-123">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="ab97a-123">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="ab97a-124">DataTable Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="ab97a-124">Handling DataTable Events</span></span>](handling-datatable-events.md)
- [<span data-ttu-id="ab97a-125">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ab97a-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
