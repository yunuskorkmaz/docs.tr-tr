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
# <a name="datatable-edits"></a>DataTable Düzenlemeleri
Bir <xref:System.Data.DataRow>sütun değerlerinde değişiklik yaptığınızda, değişiklikler hemen satırın geçerli durumuna yerleştirilir. Daha <xref:System.Data.DataRowState> sonra **Değiştirilmiştir**ve değişiklikler **DataRow'un**veya <xref:System.Data.DataRow.AcceptChanges%2A> <xref:System.Data.DataRow.RejectChanges%2A> yöntemlerkullanılarak kabul edilir veya reddedilir. **DataRow** ayrıca, düzenleme sırasında satırın durumunu askıya almak için kullanabileceğiniz üç yöntem de sağlar. Bu yöntemler <xref:System.Data.DataRow.BeginEdit%2A> <xref:System.Data.DataRow.EndEdit%2A>, <xref:System.Data.DataRow.CancelEdit%2A>, ve .  
  
 **DataRow'daki** sütun değerlerini doğrudan değiştirdiğinizde, **DataRow** **Geçerli**, **Varsayılan**ve **Özgün** satır sürümlerini kullanarak sütun değerlerini yönetir. Bu satır sürümlerine ek olarak, **BeginEdit**, **EndEdit**ve **CancelEdit** yöntemleri dördüncü satır sürümünü kullanın: **Önerilen**. Satır sürümleri hakkında daha fazla bilgi için [Bkz. Satır Durumları ve Satır Sürümleri.](row-states-and-row-versions.md)  
  
 **Önerilen** satır sürümü **BeginEdit'i** arayarak başlayan ve **EndEdit veya CancelEdit'i** kullanarak veya AcceptChanges veya **CancelEdit,** **RejectChanges'ı** arayarak sona eren bir düzenleme işlemi sırasında bulunur. **RejectChanges**  
  
 Düzenleme işlemi sırasında, **DataTable'ın** **Sütun Değiştirilen** olayında **Önerilen Değer'i** değerlendirerek tek tek sütunlara doğrulama mantığı uygulayabilirsiniz. **Sütun Değiştirilen** olay, değişen sütuna ve **Önerilen Değere**başvuruda bulunan **DataColumnChangeEventArgs** tutar. Önerilen değeri değerlendirdikten sonra, değiştirebilir veya yapılantı iptal edebilirsiniz. Edinme sona erdiğinde, satır **Önerilen** durumdan dışarı taşınır.  
  
 **EndEdit'i**arayarak düzenlemeyi onaylayabilir veya **CancelEdit'i**arayarak iptal edebilirsiniz. **EndEdit'in** değişikliklerinizi onaylamasına gerek yoksa da, **AcceptChanges** çağrılana kadar **DataSet'in** değişiklikleri gerçekte kabul etmediğini unutmayın. Ayrıca, Son Edit veya **CancelEdit**ile **EndEdit** yapılan düzeltmeyi sona erdirmeden önce **AcceptChanges'ı** ararsanız, düzeltmenin sona erdiğini ve **Önerilen** satır değerlerinin hem **Geçerli** hem de **Özgün** satır sürümleri için kabul edildiğini unutmayın. Aynı şekilde, **Reddet Değişiklikleri'ni** aramak da ediyi sona erdirir ve **Geçerli** ve **Önerilen** satır sürümlerini atar. AcceptChanges veya **RejectChanges'ı** aradıktan **RejectChanges** sonra EndEdit veya **CancelEdit'i** aramanın hiçbir etkisi yoktur, çünkü düzeltme zaten sona ermiştir. **EndEdit**  
  
 Aşağıdaki örnek, **EndEdit ve CancelEdit** ile **CancelEdit** **BeginEdit'in** nasıl kullanılacağını gösterir. Örnek ayrıca **ColumnChanged** etkinliğinde **önerilen değeri** denetler ve düzenleneni iptal edip etmeyeceğine karar verir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [DataTable Verilerini Düzenleme](manipulating-data-in-a-datatable.md)
- [DataTable Olaylarını İşleme](handling-datatable-events.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
