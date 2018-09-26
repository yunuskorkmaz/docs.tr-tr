---
title: DataAdapter olaylarını işleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: 3c2158e94f936dd2b28fe46310fd96df8dbc50fb
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47108214"
---
# <a name="handling-dataadapter-events"></a>DataAdapter olaylarını işleme
ADO.NET <xref:System.Data.Common.DataAdapter> veri kaynağındaki verilere yapılan değişikliklere yanıt vermek için kullanabileceğiniz üç olayları gösterir. Aşağıdaki tabloda `DataAdapter` olayları.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|`RowUpdating`|Bir UPDATE, INSERT veya DELETE işlemi bir satıra (birine yapılan bir çağrıyla `Update` yöntemleri) hakkında başlamaktır.|  
|`RowUpdated`|Bir UPDATE, INSERT veya DELETE işlemi bir satıra (birine yapılan bir çağrıyla `Update` yöntemleri) tamamlandı.|  
|`FillError`|Sırasında bir hata oluştu bir `Fill` işlemi.|  
  
## <a name="rowupdating-and-rowupdated"></a>RowUpdating ve RowUpdated  
 `RowUpdating` bir satırdan için önce herhangi bir güncelleştirme tetiklenir <xref:System.Data.DataSet> veri kaynağında işlendi. `RowUpdated` herhangi bir satırı güncelleştirme sonra tetiklenen `DataSet` veri kaynağında işlendi. Sonuç olarak, kullanabileceğiniz `RowUpdating` , gerçekleşmeden önce bir güncelleştirme meydana gelir, ek işleme sağlamak için geçerli güncelleştirme ve zamanlama için bir toplu işleme daha sonra işlenmek üzere iptal etmek için güncelleştirilmiş bir satır için başvuru korumak için güncelleştirme davranışını değiştirmek için , ve benzeri. `RowUpdated` hatalar ve güncelleştirme sırasında oluşan özel durumlar için yanıt için kullanışlıdır. Hata bilgilerini ekleyebilirsiniz `DataSet`, yanı sıra yeniden deneme mantığı ve benzeri.  
  
 <xref:System.Data.Common.RowUpdatingEventArgs> Ve <xref:System.Data.Common.RowUpdatedEventArgs> geçirilen bağımsız değişkenler `RowUpdating` ve `RowUpdated` olayları aşağıdakileri içerir: bir `Command` başvuran özelliği `Command` ; güncelleştirme gerçekleştirmek için kullanılan nesne bir `Row` başvuran özelliği `DataRow` güncelleştirilmiş bilgileri içeren bir nesne bir `StatementType` ne tür bir güncelleştirme gerçekleştirilmekte olan için; özellik `TableMapping`, varsa; ve `Status` işlem.  
  
 Kullanabileceğiniz `Status` istenen işlemi sırasında bir hata oluştuğunda ve belirlemek için özellik geçerli ve sonuçta elde edilen satırları karşı eylemleri denetlemek için. Olay gerçekleştiğinde `Status` özellik ya da eşittir `Continue` veya `ErrorsOccurred`. Aşağıdaki tabloda, ayarlayabileceği değerleri gösterir `Status` özelliği güncelleştirme sırasında sonraki eylemler denetlemek için.  
  
|Durum|Açıklama|  
|------------|-----------------|  
|`Continue`|Güncelleştirme işlemi devam edin.|  
|`ErrorsOccurred`|Güncelleştirme işlemi iptal ve özel durum.|  
|`SkipCurrentRow`|Geçerli satırın yoksay ve güncelleştirme işlemi devam edin.|  
|`SkipAllRemainingRows`|Güncelleştirme işlemi iptal etmek, ancak bir özel durum oluşturması beklenmiyor.|  
  
 Ayarı `Status` özelliğini `ErrorsOccurred` bir özel durum oluşturulmasına neden olur. Hangi ayarlayarak özel durum denetleyebilirsiniz `Errors` özelliği istenen özel duruma bakın. Diğer değerleri kullanarak `Status` öğesinden oluşturulan bir özel durum engeller.  
  
 Ayrıca `ContinueUpdateOnError` hatalarını işlemek için özellik satır güncelleştirildi. Varsa `DataAdapter.ContinueUpdateOnError` olduğu `true`, oluşturulan bir özel durum satır sonuçlarında güncelleştirmeye, özel durum metni içine yerleştirildiğinde `RowError` belirli bir satır ve işleme bilgileri, bir özel durum oluşturmadan devam eder. Bu sayede hatalar için yanıt vermede olduğunda `Update` aksine tamamlandıktan `RowUpdated` hata ile karşılaşıldığında hatalar için yanıt sağlayan bir olay.  
  
 Aşağıdaki kod örneği, hem ekleyip olay işleyicileri gösterilmektedir. `RowUpdating` Olay işleyicisi zaman damgası ile silinen tüm kayıtları günlüğe yazar. `RowUpdated` Olay işleyicisi ekler hata bilgilerini `RowError` özelliği içindeki satırın `DataSet`özel durumu gizler ve işleme devam eder (yansıtma davranışını `ContinueUpdateOnError`  =  `true`).  
  
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
  
## <a name="fillerror"></a>FillError  
 `DataAdapter` Sorunları `FillError` sırasında bir hata oluştuğunda olay bir `Fill` işlemi. Bu tür, yaygın olarak eklenen bir satırdaki verileri bazı kesinlik kaybı olmadan bir .NET Framework türüne dönüştürülemedi oluşur.  
  
 Sırasında bir hata oluşursa bir `Fill` işlemi, geçerli satır eklenmez `DataTable`. `FillError` Olay sağlar, hatayı giderin ve satır eklemek için veya dışlanmış bir satır yoksayıp devam etmek `Fill` işlemi.  
  
 `FillErrorEventArgs` Geçirilen `FillError` olay yanıtlama ve hataları çözün olanak tanıyan çeşitli özellikler içerir. Aşağıdaki tablo özelliklerini gösterir `FillErrorEventArgs` nesne.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|`Errors`|`Exception` Oluştu.|  
|`DataTable`|`DataTable` Hata oluştuğunda doldurulan nesnesi.|  
|`Values`|Hata oluştuğunda eklenen satır değerlerini içeren bir dizi nesne. Sıra başvuruyor `Values` dizi eklenen satırın sütun sıralı başvuruları karşılık gelir. Örneğin, `Values[0]` satırın ilk sütunu olarak eklenen değerdir.|  
|`Continue`|Özel durum gerekip gerekmediğini seçmenize olanak sağlar. Ayarı `Continue` özelliğini `false` geçerli durdurulur `Fill` işlemi ve bir özel durum oluşturulur. Ayarı `Continue` için `true` devam `Fill` hata rağmen işlemi.|  
  
 Aşağıdaki kod örneği için bir olay işleyicisi ekler `FillError` olayı `DataAdapter`. İçinde `FillError` örnek olay kodu belirler duyarlık kaybı, özel durum yanıt olanağı sağlayan olası olup olmadığını.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [DataSet Olaylarını İşleme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 [DataTable Olaylarını İşleme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [Olaylar](../../../../docs/standard/events/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
