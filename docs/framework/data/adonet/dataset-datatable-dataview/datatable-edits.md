---
title: DataTable Düzenlemeleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: a970ebda76f5bb6bdea704dabef2ee305436c613
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205020"
---
# <a name="datatable-edits"></a>DataTable Düzenlemeleri
İçindeki sütun değerlerinde değişiklik yaptığınızda <xref:System.Data.DataRow>, değişiklikler satırın geçerli durumuna hemen yerleştirilir. <xref:System.Data.DataRow.AcceptChanges%2A> <xref:System.Data.DataRow.RejectChanges%2A>Daha sonra değiştirildi olarak ayarlanır ve değişiklikler DataRow 'ın veya yöntemleri kullanılarak kabul edilir veya reddedilir. <xref:System.Data.DataRowState> **DataRow** , siz de satırı düzenlediğinizde satırın durumunu askıya almak için kullanabileceğiniz üç yöntem sağlar. Bu yöntemler, <xref:System.Data.DataRow.BeginEdit%2A> <xref:System.Data.DataRow.EndEdit%2A> ve<xref:System.Data.DataRow.CancelEdit%2A>' dir.  
  
 **DataRow** içindeki sütun değerlerini doğrudan değiştirdiğinizde, **DataRow** **geçerli**, **varsayılan**ve **orijinal** satır sürümlerini kullanarak sütun değerlerini yönetir. Bu satır sürümlerine ek olarak, **BeginEdit**, **EndEdit**ve **CancelEdit** yöntemleri Dördüncü satır sürümünü kullanır: **Önerilir**. Satır sürümleri hakkında daha fazla bilgi için bkz. [Satır durumları ve satır sürümleri](row-states-and-row-versions.md).  
  
 **Önerilen** satır sürümü, **BeginEdit** çağırarak başlayan ve, **EndEdit** veya **CancelEdit** kullanarak ya da **AcceptChanges** ya da **RejectChanges**çağırarak biten bir düzenleme işlemi sırasında bulunur.  
  
 Düzenleme işlemi sırasında, **DataTable**'ın **ColumnChanged** olayında **ProposedValue** değerlendirerek ayrı sütunlara doğrulama mantığı uygulayabilirsiniz. **ColumnChanged** olayı, **ProposedValue**ve ile değişen sütuna bir başvuru tutan **DataColumnChangeEventArgs** barındırır. Önerilen değeri değerlendirdikten sonra, bunu değiştirebilir veya düzenlemeyi iptal edebilirsiniz. Düzenleme sona erdikten sonra satır **Önerilen** durumdan çıkar.  
  
 **Sorguları**çağırarak veya **CancelEdit**çağırarak bu düzenlemeleri iptal edebilirsiniz. **EndEdit** , düzenlemelerinizi Doğrulamalarken, **veri kümesinin** , **AcceptChanges** çağrısı yapılıncaya kadar değişiklikleri gerçekten kabul etmediğinden emin olun. Ayrıca, Edit öğesini **EndEdit** veya **CancelEdit**Ile sonlandırmadan önce **AcceptChanges** 'ı çağırdığınızda, düzenleme sonlandırılır ve **Önerilen** satır değerleri hem **geçerli** hem de **orijinal** satır sürümleri için kabul edilir. Aynı şekilde, **RejectChanges** öğesini çağırmak düzenlemeyi sonlandırır ve **geçerli** ve **Önerilen** satır sürümlerini atar. **AcceptChanges** veya **RejectChanges** çağrıldıktan sonra **EndEdit** veya **CancelEdit** çağırmak, düzenleme zaten sona erdiğinden hiçbir etkiye sahip değildir.  
  
 Aşağıdaki örnek, BeginEdit ve **CancelEdit**ile **BeginEdit** 'in nasıl kullanılacağını gösterir. Örnek ayrıca **ColumnChanged** olaydaki **ProposedValue** denetimini denetler ve düzenlemeyi iptal edip etmeyeceğine karar verir.  
  
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
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
