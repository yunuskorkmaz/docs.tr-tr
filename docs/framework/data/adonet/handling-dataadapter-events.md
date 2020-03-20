---
title: DataAdapter Olaylarını İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: d01198d158c4e1c64f12e8a0756c3d4e599fce74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149550"
---
# <a name="handling-dataadapter-events"></a>DataAdapter Olaylarını İşleme
ADO.NET, <xref:System.Data.Common.DataAdapter> veri kaynağındaki verilerde yapılan değişikliklere yanıt vermek için kullanabileceğiniz üç olayı ortaya çıkarır. Aşağıdaki tabloolayları `DataAdapter` gösterir.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|`RowUpdating`|Bir satırda `Update` (yöntemlerden birine yapılan bir çağrıyla) bir UPDATE, INSERT veya DELETE işlemi başlamak üzeredir.|  
|`RowUpdated`|Bir satırdaki `Update` (yöntemlerden birine yapılan bir çağrıyla) BIR UPDATE, INSERT veya DELETE işlemi tamamlandı.|  
|`FillError`|Bir işlem sırasında bir `Fill` hata oluştu.|  
  
## <a name="rowupdating-and-rowupdated"></a>Satır Güncelleme ve Satır Güncelleme  
 `RowUpdating`veri kaynağında işlenen bir satıra <xref:System.Data.DataSet> herhangi bir güncelleştirme önce yükseltilir. `RowUpdated`veri kaynağında işlenen bir satıra `DataSet` herhangi bir güncelleştirme sonra yükseltilir. Sonuç olarak, güncelleştirme `RowUpdating` davranışını gerçekleşmeden önce değiştirmek, güncelleştirme ne zaman gerçekleşeceğini ek işleme sağlamak, güncelleştirilmiş bir satıra başvuruyu tutmak, geçerli güncelleştirmeyi iptal etmek ve daha sonra işlenecek bir toplu iş işlemi için zamanlamak için kullanabilirsiniz. `RowUpdated`güncelleştirme sırasında oluşan hataları ve özel durumları yanıtlamak için yararlıdır. Hata bilgilerini `DataSet`, yeniden deneme mantığına ve benzeri bilgilere ekleyebilirsiniz.  
  
 Ve <xref:System.Data.Common.RowUpdatingEventArgs> <xref:System.Data.Common.RowUpdatedEventArgs> bağımsız değişkenlere `RowUpdating` `RowUpdated` geçirilen ve olaylar `Command` şunlardır: `Command` güncelleştirmeyi gerçekleştirmek için kullanılan nesneye başvuran bir özellik; güncelleştirilmiş bilgileri `DataRow` içeren nesneye başvuran bir `Row` özellik; ne `StatementType` tür bir güncelleştirme nin gerçekleştirildiği ne tür bir özellik; `TableMapping`, varsa; `Status` ve operasyonun.  
  
 `Status` İşlem sırasında bir hata oluşup oluşmadiğini belirlemek ve istenirse, eylemleri geçerli ve ortaya çıkan satırlara karşı denetlemek için özelliği kullanabilirsiniz. Olay oluştuğunda, `Status` özellik eşittir ya `Continue` `ErrorsOccurred`da . Aşağıdaki tablo, güncelleştirme sırasında sonraki eylemleri `Status` denetlemek için özelliği ayarlayabileceğiniz değerleri gösterir.  
  
|Durum|Açıklama|  
|------------|-----------------|  
|`Continue`|Güncelleştirme işlemine devam edin.|  
|`ErrorsOccurred`|Güncelleştirme işlemini iptal edin ve bir özel durum atın.|  
|`SkipCurrentRow`|Geçerli satırı yoksayın ve güncelleştirme işlemine devam edin.|  
|`SkipAllRemainingRows`|Güncelleştirme işlemini iptal edin, ancak bir özel durum atmayın.|  
  
 `Status` Özelliği, `ErrorsOccurred` özel bir özel durum atacak şekilde ayarlamak. `Errors` Özelliği istenilen özel durum için ayarlayarak hangi özel durum atılacağını denetleyebilirsiniz. Diğer değerlerden birini `Status` kullanmak, bir özel durum atılmasını önler.  
  
 Güncelleştirilmiş satırlar `ContinueUpdateOnError` için hataları işlemek için özelliği de kullanabilirsiniz. Eğer `DataAdapter.ContinueUpdateOnError` `true`ise, bir satıra güncelleştirme bir özel durum atılması ile sonuçlanırsa, özel durum metni belirli satırın `RowError` bilgilerine yerleştirilir ve işleme özel durum atmadan devam edilir. Bu, hatayla karşılaşıldığında `Update` hatalara yanıt vermenizi `RowUpdated` sağlayan olayın aksine, tamamlandığında hatalara yanıt vermenizi sağlar.  
  
 Aşağıdaki kod örneği, olay işleyicilerinin hem ekleyeceğini hem de kaldırılmasını gösterir. Olay `RowUpdating` işleyicisi, silinen tüm kayıtların bir günlüğünü bir zaman damgası ile yazar. `RowUpdated` Olay işleyicisi satırın `RowError` özelliğine hata `DataSet`bilgileri ekler, özel durumu bastırır ve işleme `ContinueUpdateOnError`  =  `true`devam eder (davranışı yansıtma).  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim custAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
' Add handlers.  
AddHandler custAdapter.RowUpdating, New SqlRowUpdatingEventHandler( _  
  AddressOf OnRowUpdating)  
AddHandler custAdapter.RowUpdated, New SqlRowUpdatedEventHandler(  
  AddressOf OnRowUpdated)  
  
' Set DataAdapter command properties, fill DataSet, and modify DataSet.  
  
custAdapter.Update(custDS, "Customers")  
  
' Remove handlers.  
RemoveHandler custAdapter.RowUpdating, _  
  New SqlRowUpdatingEventHandler(AddressOf OnRowUpdating)  
RemoveHandler custAdapter.RowUpdated, _  
  New SqlRowUpdatedEventHandler(AddressOf OnRowUpdated)  
  
Private Shared Sub OnRowUpdating(sender As Object, _  
  args As SqlRowUpdatingEventArgs)  
  If args.StatementType = StatementType.Delete Then  
    Dim tw As System.IO.TextWriter = _  
  System.IO.File.AppendText("Deletes.log")  
    tw.WriteLine( _  
      "{0}: Customer {1} Deleted.", DateTime.Now, args.Row(_  
      "CustomerID", DataRowVersion.Original))  
    tw.Close()  
  End If  
End Sub  
  
Private Shared Sub OnRowUpdated( _  
  sender As Object, args As SqlRowUpdatedEventArgs)  
  If args.Status = UpdateStatus.ErrorsOccurred  
    args.Status = UpdateStatus.SkipCurrentRow  
    args.Row.RowError = args.Errors.Message  
  End If  
End Sub  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter custAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
// Add handlers.  
custAdapter.RowUpdating += new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
// Set DataAdapter command properties, fill DataSet, modify DataSet.  
  
custAdapter.Update(custDS, "Customers");  
  
// Remove handlers.  
custAdapter.RowUpdating -= new SqlRowUpdatingEventHandler(OnRowUpdating);  
custAdapter.RowUpdated -= new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
protected static void OnRowUpdating(  
  object sender, SqlRowUpdatingEventArgs args)  
{  
  if (args.StatementType == StatementType.Delete)  
  {  
    System.IO.TextWriter tw = System.IO.File.AppendText("Deletes.log");  
    tw.WriteLine(  
      "{0}: Customer {1} Deleted.", DateTime.Now,
       args.Row["CustomerID", DataRowVersion.Original]);  
    tw.Close();  
  }  
}  
  
protected static void OnRowUpdated(  
  object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.Status == UpdateStatus.ErrorsOccurred)  
  {  
    args.Row.RowError = args.Errors.Message;  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="fillerror"></a>Fillerror  
 Bir `DataAdapter` `Fill` işlem `FillError` sırasında bir hata oluştuğunda sorunları. Bu tür hatalar genellikle, eklenen satırdaki verilerin bazı kesinlik kaybı olmadan bir .NET Framework türüne dönüştürülemediğinde oluşur.  
  
 Bir işlem sırasında bir `Fill` hata oluşursa, geçerli `DataTable`satır . Olay, `FillError` hatayı çözmenizi ve satırı eklemenizi veya dışlanan satırı yok `Fill` saymanızı ve işlemi devam etmenizi sağlar.  
  
 `FillError` Olaya geçirilen, `FillErrorEventArgs` yanıt vermenizi ve hataları çözmenizi sağlayan birkaç özellik içerebilir. Aşağıdaki tablo nesnenin `FillErrorEventArgs` özelliklerini gösterir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|`Errors`|Olan `Exception` bu.|  
|`DataTable`|Hata `DataTable` oluştuğunda doldurulan nesne.|  
|`Values`|Hata oluştuğunda eklenen satırın değerlerini içeren bir nesne dizisi. `Values` Dizinin ordinal referansları, eklenen satır sütunlarının ordinal başvurularına karşılık gelir. Örneğin, `Values[0]` satırın ilk sütunu olarak eklenen değerdir.|  
|`Continue`|Bir özel durum atıp atmayacağını seçmenizi sağlar. `Continue` Özelliğin geçerli `false` `Fill` işlemi durduracak şekilde ayarlanması ve bir özel durum atılır. Ayarı, `Continue` `Fill` hataya `true` rağmen işlemi devam ettir.|  
  
 Aşağıdaki kod örneği olay için `FillError` bir olay `DataAdapter`işleyicisi ekler . `FillError` Olay kodunda, örnek, özel durum yanıtlama olanağı sağlayarak hassas kayıp potansiyeli olup olmadığını belirler.  
  
```vb  
AddHandler adapter.FillError, New FillErrorEventHandler( _  
  AddressOf FillError)  
  
Dim dataSet As DataSet = New DataSet  
adapter.Fill(dataSet, "ThisTable")  
  
Private Shared Sub FillError(sender As Object, _  
  args As FillErrorEventArgs)  
  If args.Errors.GetType() Is Type.GetType("System.OverflowException") Then  
    ' Code to handle precision loss.  
    ' Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(New Object() _  
      {args.Values(0), args.Values(1), DBNull.Value})  
    ' Set the RowError containing the value for the third column.  
    myRow.RowError = _  
      "OverflowException encountered. Value from data source: " & _  
      args.Values(2)  
    args.Continue = True  
  End If  
End Sub  
```  
  
```csharp  
adapter.FillError += new FillErrorEventHandler(FillError);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "ThisTable");  
  
protected static void FillError(object sender, FillErrorEventArgs args)  
{  
  if (args.Errors.GetType() == typeof(System.OverflowException))  
  {  
    // Code to handle precision loss.  
    //Add a row to table using the values from the first two columns.  
    DataRow myRow = args.DataTable.Rows.Add(new object[]  
       {args.Values[0], args.Values[1], DBNull.Value});  
    //Set the RowError containing the value for the third column.  
    myRow.RowError =
       "OverflowException Encountered. Value from data source: " +  
       args.Values[2];  
    args.Continue = true;  
  }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [DataSet Olaylarını İşleme](./dataset-datatable-dataview/handling-dataset-events.md)
- [DataTable Olaylarını İşleme](./dataset-datatable-dataview/handling-datatable-events.md)
- [Olaylar](../../../standard/events/index.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
