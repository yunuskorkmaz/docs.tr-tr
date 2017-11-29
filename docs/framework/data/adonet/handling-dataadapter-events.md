---
title: "Olaylarını işleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b6ca32ac1b0af1f290a9c2b2e33c51efa7a3b149
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="handling-dataadapter-events"></a>Olaylarını işleme
ADO.NET <xref:System.Data.Common.DataAdapter> veri kaynağında verilere yapılan değişiklikleri yanıt vermek için kullanabileceğiniz üç olayları gösterir. Aşağıdaki tabloda `DataAdapter` olaylar.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|`RowUpdating`|Bir satır üzerinde bir güncelleştirme, ekleme veya silme işlemi (biri için bir çağrı tarafından `Update` yöntemleri) hakkında başlamaktır.|  
|`RowUpdated`|Bir satır üzerinde bir güncelleştirme, ekleme veya silme işlemi (biri için bir çağrı tarafından `Update` yöntemleri) tamamlandı.|  
|`FillError`|Sırasında bir hata oluştu bir `Fill` işlemi.|  
  
## <a name="rowupdating-and-rowupdated"></a>RowUpdating ve RowUpdated  
 `RowUpdating`önce herhangi bir güncelleştirme satırdan tetiklenir <xref:System.Data.DataSet> veri kaynağında işlenir. `RowUpdated`herhangi bir satırı güncelleştirdikten sonra tetiklenir `DataSet` veri kaynağında işlenir. Sonuç olarak, kullanabileceğiniz `RowUpdating` , gerçekleşmeden önce bir güncelleştirme ortaya çıktığında ek işleme sağlamak üzere, geçerli güncelleştirme ve zamanlama için bir toplu işlem daha sonra işlenmek üzere iptal etmek için güncelleştirilmiş bir satıra bir başvuru korumak için güncelleştirme davranışını değiştirmek için , ve benzeri. `RowUpdated`hatalar ve güncelleştirme sırasında oluşan özel durumlar için yanıt için yararlıdır. Hata bilgilerini ekleyebilirsiniz `DataSet`, yanı sıra mantığı yeniden deneyin ve benzeri.  
  
 <xref:System.Data.Common.RowUpdatingEventArgs> Ve <xref:System.Data.Common.RowUpdatedEventArgs> bağımsız değişkenleri geçirilen `RowUpdating` ve `RowUpdated` olaylar aşağıdakileri içerir: bir `Command` başvuruyor özelliği `Command` ; güncelleştirme gerçekleştirmek için kullanılan nesne bir `Row` başvuran özelliği `DataRow` güncelleştirilmiş bilgileri içeren bir nesne bir `StatementType` hangi güncelleştirme türünü gerçekleştirildiği; özelliği `TableMapping`, varsa; ve `Status` işlem.  
  
 Kullanabileceğiniz `Status` istenen işlemi sırasında bir hata oluştuğunda ve belirlemek için özellik geçerli ve sonuçta elde edilen satırları karşı eylemler denetlemek için. Olay ortaya çıktığında `Status` özelliği ya da eşittir `Continue` veya `ErrorsOccurred`. Aşağıdaki tablo, belirleyebileceğiniz ayarlar değerleri gösterir `Status` özelliği güncelleştirme sırasında sonraki eylemler denetlemek için.  
  
|Durum|Açıklama|  
|------------|-----------------|  
|`Continue`|Güncelleştirme işlemi devam edin.|  
|`ErrorsOccurred`|Güncelleştirme işlemi iptal etmek ve bir özel durum.|  
|`SkipCurrentRow`|Geçerli satırda yoksay ve güncelleştirme işlemi devam edin.|  
|`SkipAllRemainingRows`|Güncelleştirme işlemi iptal etmek, ancak bir özel durum değil.|  
  
 Ayarı `Status` özelliğine `ErrorsOccurred` bir özel durum oluşturulmasına neden olur. Ayarlayarak hangi özel durum denetleyebilirsiniz `Errors` için istenen özel özellik. Diğer değerler için birini kullanarak `Status` oluşturulan gelen bir özel durum engeller.  
  
 Aynı zamanda `ContinueUpdateOnError` için hataları işlemek için özellik satır güncelleştirildi. Varsa `DataAdapter.ContinueUpdateOnError` olan `true`, oluşturulan bir özel durum satır sonuçlarında için bir güncelleştirme, özel durum metni içine yerleştirildiğinde `RowError` belirli bir satır ve işleme bilgileri, bir özel durum oluşturmadan devam eder. Bu, hataları yanıtlamasını sağlar, `Update` tersine için tamamlandıktan `RowUpdated` hatayla karşılaştığında hataları yanıtlamasını sağlar olay.  
  
 Aşağıdaki kod örneği, hem ekleyip olay işleyicileri gösterilmektedir. `RowUpdating` Olay işleyicisi zaman damgası ile silinen tüm kayıtları günlüğe yazar. `RowUpdated` Olay işleyicisi ekler hata bilgileri için `RowError` satırda özelliğinin `DataSet`, özel durum bastırır ve işleme devam eder (davranışını yansıtma `ContinueUpdateOnError`  =  `true`).  
  
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
 `DataAdapter` Sorunları `FillError` sırasında bir hata oluştuğunda olay bir `Fill` işlemi. Bu tür hatalara, yaygın olarak eklenen satır verileri duyarlık kaybı olmadan bir .NET Framework türüne dönüştürülemedi oluşur.  
  
 Sırasında bir hata oluşursa, bir `Fill` işlemi, geçerli satır eklenmez `DataTable`. `FillError` Olay sağlar, hatayı giderin ve satır eklemek için veya dışlanan satır yoksayıp devam etmek `Fill` işlemi.  
  
 `FillErrorEventArgs` Geçirilen `FillError` olay yanıt ve hataları çözümleyin olanak tanıyan çeşitli özellikler içerebilir. Aşağıdaki tabloda özelliklerini gösterir `FillErrorEventArgs` nesnesi.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|`Errors`|`Exception` Oluştu.|  
|`DataTable`|`DataTable` Hata oluştuğu sırada doldurulan nesne.|  
|`Values`|Hata oluştuğunda eklenmekte olan satır değerleri içeren bir nesneler dizisi. Sıra başvuruyor `Values` dizi eklenen satırın sütunların sırası başvuruları karşılık gelir. Örneğin, `Values[0]` satırının ilk sütununu eklendi değerdir.|  
|`Continue`|Özel bir durum oluşturulup oluşturulmayacağını seçmenize olanak sağlar. Ayarı `Continue` özelliğine `false` geçerli durdurulur `Fill` işlemi ve bir özel durum oluşturulur. Ayarı `Continue` için `true` devam `Fill` hata rağmen işlemi.|  
  
 Aşağıdaki kod örneği için bir olay işleyicisi ekler `FillError` olayı `DataAdapter`. İçinde `FillError` olay kodu örnek belirler duyarlık kaybı, özel durumu yanıt olanağı sağlayarak olası olup olmadığını.  
  
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
    args.RowError = _  
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
    args.RowError =   
       "OverflowException Encountered. Value from data source: " +  
       args.Values[2];  
    args.Continue = true;  
  }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataAdapters ve DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Veri kümesi olayları işleme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 [DataTable olayları işleme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [Olayları](../../../../docs/standard/events/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
