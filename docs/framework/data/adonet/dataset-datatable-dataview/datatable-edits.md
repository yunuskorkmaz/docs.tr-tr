---
title: DataTable düzenlemeler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: b806e642a5cce6a55ff0dcecc9b018f3ee78bad8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758626"
---
# <a name="datatable-edits"></a>DataTable düzenlemeler
Değişiklikler yaptığınızda sütun değerleri için bir <xref:System.Data.DataRow>, değişiklikleri hemen satır geçerli durumunda yerleştirilir. <xref:System.Data.DataRowState> Sonra ayarlanır **değiştirilen**, değişiklikleri kabul veya kullanarak <xref:System.Data.DataRow.AcceptChanges%2A> veya <xref:System.Data.DataRow.RejectChanges%2A> yöntemlerinin **DataRow**. **DataRow** da Siz düzenlerken satır durumunu askıya almak için kullanabileceğiniz üç yöntem sunar. Bu yöntemler <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, ve <xref:System.Data.DataRow.CancelEdit%2A>.  
  
 Sütun değerleri değiştirdiğinizde bir **DataRow** doğrudan **DataRow** kullanarak sütun değerlerini yönetir **geçerli**, **varsayılan**, ve **Özgün** satır sürümleri. Bu satır sürümleri yanı sıra **BeginEdit**, **EndEdit**, ve **CancelEdit** dördüncü bir satır sürümü yöntemleri kullanın: **önerilen**. Satır sürümleri hakkında daha fazla bilgi için bkz: [satır durumları ve satır sürümleri](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
 **Önerilen** satır sürümü var. çağırarak başlayan bir düzenleme işlemi sırasında **BeginEdit** ve kullanarak ya da sona **EndEdit** veya **CancelEdit,**  veya çağırarak **AcceptChanges** veya **RejectChanges**.  
  
 Düzenleme işlemi sırasında doğrulama mantığını tek tek sütun değerlendirerek uygulayabilirsiniz **ProposedValue** içinde **ColumnChanged** olayı **DataTable**. **ColumnChanged** olay tutan **DataColumnChangeEventArgs** değiştiriyor. sütun ve için bir başvuru tutun **ProposedValue**. Önerilen değer değerlendirdikten sonra değiştirmek veya düzenlemeyi iptal etmek. Düzen sona erdikten sonra satır dışı taşır **önerilen** durumu.  
  
 Çağırarak düzenlemeleri onaylayabilirsiniz **EndEdit**, veya bunları çağırarak iptal **CancelEdit**. Unutmayın, while **EndEdit** yaptığınız düzenlemeleri onaylamak **DataSet** gerçekten değişinceye kadar kabul etmiyorum **AcceptChanges** olarak adlandırılır. Çağırırsanız ayrıca **AcceptChanges** düzenleme sona ermeden önce **EndEdit** veya **CancelEdit**, Düzen sona erdi ve **önerilen** satır değerleri için her ikisini de kabul edilir **geçerli** ve **özgün** satır sürümleri. Aynı şekilde çağırma **RejectChanges** düzenleme sona erer ve atar **geçerli** ve **önerilen** satır sürümleri. Çağırma **EndEdit** veya **CancelEdit** çağırdıktan sonra **AcceptChanges** veya **RejectChanges** düzenleme zaten sahip olduğu herhangi bir etkisi olmaz. sona erdi.  
  
 Aşağıdaki örnekte nasıl kullanılacağı ortaya **BeginEdit** ile **EndEdit** ve **CancelEdit**. Bu örnek ayrıca denetler **ProposedValue** içinde **ColumnChanged** olay ve düzenlemeyi iptal etmek mi karar verir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataRowVersion>  
 [DataTable Verilerini Düzenleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [DataTable Olaylarını İşleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
