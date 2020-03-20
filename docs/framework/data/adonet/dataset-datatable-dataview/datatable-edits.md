---
title: DataTable Düzenlemeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 9e8c4204b51121b147fc7614066d9b849a687574
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151266"
---
# <a name="datatable-edits"></a><span data-ttu-id="bad97-102">DataTable Düzenlemeleri</span><span class="sxs-lookup"><span data-stu-id="bad97-102">DataTable Edits</span></span>
<span data-ttu-id="bad97-103">Bir <xref:System.Data.DataRow>sütun değerlerinde değişiklik yaptığınızda, değişiklikler hemen satırın geçerli durumuna yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bad97-103">When you make changes to column values in a <xref:System.Data.DataRow>, the changes are immediately placed in the current state of the row.</span></span> <span data-ttu-id="bad97-104">Daha <xref:System.Data.DataRowState> sonra **Değiştirilmiştir**ve değişiklikler **DataRow'un**veya <xref:System.Data.DataRow.AcceptChanges%2A> <xref:System.Data.DataRow.RejectChanges%2A> yöntemlerkullanılarak kabul edilir veya reddedilir.</span><span class="sxs-lookup"><span data-stu-id="bad97-104">The <xref:System.Data.DataRowState> is then set to **Modified**, and the changes are accepted or rejected using the <xref:System.Data.DataRow.AcceptChanges%2A> or <xref:System.Data.DataRow.RejectChanges%2A> methods of the **DataRow**.</span></span> <span data-ttu-id="bad97-105">**DataRow** ayrıca, düzenleme sırasında satırın durumunu askıya almak için kullanabileceğiniz üç yöntem de sağlar.</span><span class="sxs-lookup"><span data-stu-id="bad97-105">The **DataRow** also provides three methods that you can use to suspend the state of the row while you are editing it.</span></span> <span data-ttu-id="bad97-106">Bu yöntemler <xref:System.Data.DataRow.BeginEdit%2A> <xref:System.Data.DataRow.EndEdit%2A>, <xref:System.Data.DataRow.CancelEdit%2A>, ve .</span><span class="sxs-lookup"><span data-stu-id="bad97-106">These methods are <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, and <xref:System.Data.DataRow.CancelEdit%2A>.</span></span>  
  
 <span data-ttu-id="bad97-107">**DataRow'daki** sütun değerlerini doğrudan değiştirdiğinizde, **DataRow** **Geçerli**, **Varsayılan**ve **Özgün** satır sürümlerini kullanarak sütun değerlerini yönetir.</span><span class="sxs-lookup"><span data-stu-id="bad97-107">When you modify column values in a **DataRow** directly, the **DataRow** manages the column values using the **Current**, **Default**, and **Original** row versions.</span></span> <span data-ttu-id="bad97-108">Bu satır sürümlerine ek olarak, **BeginEdit**, **EndEdit**ve **CancelEdit** yöntemleri dördüncü satır sürümünü kullanın: **Önerilen**.</span><span class="sxs-lookup"><span data-stu-id="bad97-108">In addition to these row versions, the **BeginEdit**, **EndEdit**, and **CancelEdit** methods use a fourth row version: **Proposed**.</span></span> <span data-ttu-id="bad97-109">Satır sürümleri hakkında daha fazla bilgi için [Bkz. Satır Durumları ve Satır Sürümleri.](row-states-and-row-versions.md)</span><span class="sxs-lookup"><span data-stu-id="bad97-109">For more information about row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="bad97-110">**Önerilen** satır sürümü **BeginEdit'i** arayarak başlayan ve **EndEdit veya CancelEdit'i** kullanarak veya AcceptChanges veya **CancelEdit,** **RejectChanges'ı** arayarak sona eren bir düzenleme işlemi sırasında bulunur. **RejectChanges**</span><span class="sxs-lookup"><span data-stu-id="bad97-110">The **Proposed** row version exists during an edit operation that begins by calling **BeginEdit** and that ends either by using **EndEdit** or **CancelEdit,** or by calling **AcceptChanges** or **RejectChanges**.</span></span>  
  
 <span data-ttu-id="bad97-111">Düzenleme işlemi sırasında, **DataTable'ın** **Sütun Değiştirilen** olayında **Önerilen Değer'i** değerlendirerek tek tek sütunlara doğrulama mantığı uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bad97-111">During the edit operation, you can apply validation logic to individual columns by evaluating the **ProposedValue** in the **ColumnChanged** event of the **DataTable**.</span></span> <span data-ttu-id="bad97-112">**Sütun Değiştirilen** olay, değişen sütuna ve **Önerilen Değere**başvuruda bulunan **DataColumnChangeEventArgs** tutar.</span><span class="sxs-lookup"><span data-stu-id="bad97-112">The **ColumnChanged** event holds **DataColumnChangeEventArgs** that keep a reference to the column that is changing and to the **ProposedValue**.</span></span> <span data-ttu-id="bad97-113">Önerilen değeri değerlendirdikten sonra, değiştirebilir veya yapılantı iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bad97-113">After you evaluate the proposed value, you can either modify it or cancel the edit.</span></span> <span data-ttu-id="bad97-114">Edinme sona erdiğinde, satır **Önerilen** durumdan dışarı taşınır.</span><span class="sxs-lookup"><span data-stu-id="bad97-114">When the edit is ended, the row moves out of the **Proposed** state.</span></span>  
  
 <span data-ttu-id="bad97-115">**EndEdit'i**arayarak düzenlemeyi onaylayabilir veya **CancelEdit'i**arayarak iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bad97-115">You can confirm edits by calling **EndEdit**, or you can cancel them by calling **CancelEdit**.</span></span> <span data-ttu-id="bad97-116">**EndEdit'in** değişikliklerinizi onaylamasına gerek yoksa da, **AcceptChanges** çağrılana kadar **DataSet'in** değişiklikleri gerçekte kabul etmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bad97-116">Note that while **EndEdit** does confirm your edits, the **DataSet** does not actually accept the changes until **AcceptChanges** is called.</span></span> <span data-ttu-id="bad97-117">Ayrıca, Son Edit veya **CancelEdit**ile **EndEdit** yapılan düzeltmeyi sona erdirmeden önce **AcceptChanges'ı** ararsanız, düzeltmenin sona erdiğini ve **Önerilen** satır değerlerinin hem **Geçerli** hem de **Özgün** satır sürümleri için kabul edildiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bad97-117">Note also that if you call **AcceptChanges** before you have ended the edit with **EndEdit** or **CancelEdit**, the edit is ended and the **Proposed** row values are accepted for both the **Current** and **Original** row versions.</span></span> <span data-ttu-id="bad97-118">Aynı şekilde, **Reddet Değişiklikleri'ni** aramak da ediyi sona erdirir ve **Geçerli** ve **Önerilen** satır sürümlerini atar.</span><span class="sxs-lookup"><span data-stu-id="bad97-118">In the same manner, calling **RejectChanges** ends the edit and discards the **Current** and **Proposed** row versions.</span></span> <span data-ttu-id="bad97-119">AcceptChanges veya **RejectChanges'ı** aradıktan **RejectChanges** sonra EndEdit veya **CancelEdit'i** aramanın hiçbir etkisi yoktur, çünkü düzeltme zaten sona ermiştir. **EndEdit**</span><span class="sxs-lookup"><span data-stu-id="bad97-119">Calling **EndEdit** or **CancelEdit** after calling **AcceptChanges** or **RejectChanges** has no effect because the edit has already ended.</span></span>  
  
 <span data-ttu-id="bad97-120">Aşağıdaki örnek, **EndEdit ve CancelEdit** ile **CancelEdit** **BeginEdit'in** nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bad97-120">The following example demonstrates how to use **BeginEdit** with **EndEdit** and **CancelEdit**.</span></span> <span data-ttu-id="bad97-121">Örnek ayrıca **ColumnChanged** etkinliğinde **önerilen değeri** denetler ve düzenleneni iptal edip etmeyeceğine karar verir.</span><span class="sxs-lookup"><span data-stu-id="bad97-121">The example also checks the **ProposedValue** in the **ColumnChanged** event and decides whether to cancel the edit.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bad97-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bad97-122">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [<span data-ttu-id="bad97-123">DataTable Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="bad97-123">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="bad97-124">DataTable Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="bad97-124">Handling DataTable Events</span></span>](handling-datatable-events.md)
- [<span data-ttu-id="bad97-125">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bad97-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
