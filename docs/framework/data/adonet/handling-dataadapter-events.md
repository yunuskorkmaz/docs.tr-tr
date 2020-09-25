---
title: DataAdapter Olaylarını İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: a2c2dc71cc9e5c445fd05534dad5ad47fd66f436
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194732"
---
# <a name="handling-dataadapter-events"></a>DataAdapter Olaylarını İşleme

ADO.NET, <xref:System.Data.Common.DataAdapter> veri kaynağındaki verilerde yapılan değişikliklere yanıt vermek için kullanabileceğiniz üç olay sunar. Aşağıdaki tabloda `DataAdapter` Olaylar gösterilmektedir.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|`RowUpdating`|Bir satırdaki GÜNCELLEŞTIRME, ekleme veya SILME işlemi (metotlardan birine yapılan bir çağrı ile `Update` ) başlamak üzere.|  
|`RowUpdated`|Bir satırdaki GÜNCELLEŞTIRME, ekleme veya SILME işlemi (metotlardan birine yapılan bir çağrı ile `Update` ) tamamlanmıştır.|  
|`FillError`|İşlem sırasında bir hata oluştu `Fill` .|  
  
## <a name="rowupdating-and-rowupdated"></a>RowUpdating ve RowUpdated  

 `RowUpdating` , öğesinden bir satırdaki herhangi bir güncelleştirme <xref:System.Data.DataSet> veri kaynağında işlenmeden önce tetiklenir. `RowUpdated` , öğesinden bir satırdaki herhangi bir güncelleştirme `DataSet` veri kaynağında işlendikten sonra oluşturulur. Sonuç olarak, güncelleştirme `RowUpdating` davranışını yapmadan önce değiştirmek, bir güncelleştirme gerçekleştiğinde, güncelleştirilmiş bir satıra yönelik bir başvuruyu sürdürmek, geçerli güncelleştirmeyi iptal etmek ve ardından bir toplu işlemin daha sonra işlenecek şekilde zamanlamak için kullanabilirsiniz. `RowUpdated` , güncelleştirme sırasında oluşan hatalara ve özel durumlara yanıt vermek için yararlıdır. Öğesine hata bilgilerini `DataSet` ve yeniden deneme mantığını ve benzerlerini de ekleyebilirsiniz.  
  
 Ve <xref:System.Data.Common.RowUpdatingEventArgs> <xref:System.Data.Common.RowUpdatedEventArgs> olaylarına geçirilen bağımsız değişkenler `RowUpdating` `RowUpdated` şunlardır: `Command` `Command` güncelleştirmeyi gerçekleştirmek için kullanılan nesneye başvuran bir özellik; `Row` `DataRow` güncelleştirilmiş bilgileri içeren nesneye başvuran bir özellik; `StatementType` ne tür bir güncelleştirme gerçekleştirilmekte olan bir özellik; `TableMapping` varsa, ve `Status` işlem işlemi.  
  
 `Status`Özelliği, işlem sırasında bir hata oluşup olmadığını ve isterseniz geçerli ve sonuç satırlarıyla eylemleri denetlemek için kullanabilirsiniz. Olay gerçekleştiğinde, `Status` özelliği ya da değerine eşittir `Continue` `ErrorsOccurred` . Aşağıdaki tabloda, `Status` güncelleştirme sırasında sonraki işlemleri denetlemek için özelliği ayarlayabileceğiniz değerler gösterilmektedir.  
  
|Durum|Açıklama|  
|------------|-----------------|  
|`Continue`|Güncelleştirme işlemine devam edin.|  
|`ErrorsOccurred`|Güncelleştirme işlemini iptal edin ve bir özel durum oluşturun.|  
|`SkipCurrentRow`|Geçerli satırı yoksayın ve güncelleştirme işlemine devam edin.|  
|`SkipAllRemainingRows`|Güncelleştirme işlemini iptal edin, ancak özel durum oluşturmaz.|  
  
 `Status`Özelliği olarak ayarlamak `ErrorsOccurred` bir özel durumun oluşturulmasına neden olur. Özelliği istenen özel duruma ayarlayarak hangi özel durumun oluşturulmuş olduğunu denetleyebilirsiniz `Errors` . İçin diğer değerlerden birini kullanmak, `Status` bir özel durumun oluşturulmasını engeller.  
  
 Ayrıca, `ContinueUpdateOnError` güncelleştirilmiş satırlar için hataları işlemek üzere özelliğini de kullanabilirsiniz. `DataAdapter.ContinueUpdateOnError`İse `true` , bir satırdaki bir güncelleştirme bir özel durumla sonuçlanmışsa, özel durumun metni `RowError` belirli bir satırın bilgilerine konur ve işleme özel durum oluşturmadan devam eder. Bu, bir `Update` `RowUpdated` hata ile karşılaşıldığında hatalara yanıt vermenize olanak sağlayan olaya karşılık olarak hatalara yanıt vermenize olanak sağlar.  
  
 Aşağıdaki kod örneği, olay işleyicilerinin nasıl ekleneceğini ve kaldırılacağını gösterir. `RowUpdating`Olay işleyicisi, bir zaman damgasıyla silinen tüm kayıtların günlüğünü yazar. `RowUpdated`Olay işleyicisi `RowError` , içindeki satırın özelliğine hata bilgilerini ekler `DataSet` , özel durumu bastırır ve işleme devam eder (davranışını yansıtma `ContinueUpdateOnError`  =  `true` ).  
  
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

 `DataAdapter` `FillError` İşlem sırasında bir hata oluştuğunda olayı yayınlar `Fill` . Bu tür bir hata genellikle, eklenmekte olan satırdaki veriler bir duyarlık kaybı olmadan bir .NET Framework türüne dönüştürülemiyorsa oluşur.  
  
 İşlem sırasında bir hata oluşursa `Fill` , geçerli satır öğesine eklenmez `DataTable` . `FillError`Olay, hatayı çözmenize ve satırı eklemenize, ya da dışlanan satırı yoksaymanızı ve işleme devam etmenizi sağlar `Fill` .  
  
 `FillErrorEventArgs`Olaya geçilen, `FillError` hatalara yanıt vermenize ve bunları çözmenize olanak sağlayan çeşitli özellikler içerebilir. Aşağıdaki tabloda nesnesinin özellikleri gösterilmektedir `FillErrorEventArgs` .  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|`Errors`|`Exception`Bu oluştu.|  
|`DataTable`|`DataTable`Hata oluştuğunda Doldurulmakta olan nesne.|  
|`Values`|Hata oluştuğunda eklenmekte olan satırın değerlerini içeren bir nesne dizisi. Dizinin sıralı başvuruları, `Values` eklenmekte olan satır sütunlarının sıralı başvurularına karşılık gelir. Örneğin, `Values[0]` satırın ilk sütunu olarak eklenmekte olan değerdir.|  
|`Continue`|Bir özel durum oluşturulup oluşturulmayacağını seçmenize olanak sağlar. `Continue`Özelliği olarak ayarlamak `false` geçerli `Fill` işlemi durdurur ve bir özel durum oluşturulur. `Continue` `true` Hataya rağmen işleme devam etmek için ayarlama `Fill` .|  
  
 Aşağıdaki kod örneği, olayı için bir olay işleyicisi ekler `FillError` `DataAdapter` . `FillError`Olay kodunda örnek, özel duruma yanıt verme fırsatı sağlayarak duyarlık kaybı için olası olup olmadığını belirler.  
  
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
