---
title: DataAdapter Olaylarını İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: a63e65289a51a7647270a978cec11ef6bc201e45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962752"
---
# <a name="handling-dataadapter-events"></a>DataAdapter Olaylarını İşleme
ADO.net <xref:System.Data.Common.DataAdapter> , veri kaynağındaki verilerde yapılan değişikliklere yanıt vermek için kullanabileceğiniz üç olay sunar. Aşağıdaki tabloda `DataAdapter` olaylar gösterilmektedir.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|`RowUpdating`|Bir satırdaki güncelleştirme, ekleme veya silme işlemi ( `Update` metotlardan birine yapılan bir çağrı ile) başlamak üzere.|  
|`RowUpdated`|Bir satırdaki güncelleştirme, ekleme veya silme işlemi ( `Update` metotlardan birine yapılan bir çağrı ile) tamamlanmıştır.|  
|`FillError`|`Fill` İşlem sırasında bir hata oluştu.|  
  
## <a name="rowupdating-and-rowupdated"></a>RowUpdating ve RowUpdated  
 `RowUpdating`, <xref:System.Data.DataSet> öğesinden bir satırdaki herhangi bir güncelleştirme veri kaynağında işlenmeden önce tetiklenir. `RowUpdated`, `DataSet` öğesinden bir satırdaki herhangi bir güncelleştirme veri kaynağında işlendikten sonra oluşturulur. Sonuç olarak, güncelleştirme davranışını yapmadan önce `RowUpdating` değiştirmek için, bir güncelleştirme gerçekleştiğinde, güncelleştirilmiş bir satıra yönelik bir başvuruyu sürdürmek için, geçerli güncelleştirmeyi iptal etmek ve daha sonra işlenecek bir toplu işlem için zamanlamak üzere, bir güncelleştirme gerçekleştiğinde ek işleme sağlamak için kullanabilirsiniz vb. `RowUpdated`, güncelleştirme sırasında oluşan hatalara ve özel durumlara yanıt vermek için yararlıdır. Öğesine `DataSet`hata bilgilerini ve yeniden deneme mantığını ve benzerlerini de ekleyebilirsiniz.  
  
 <xref:System.Data.Common.RowUpdatingEventArgs> `Command` `Row` Ve olaylarına geçirilen`RowUpdating`bağımsızdeğişkenler şunlardır :`Command` güncelleştirmeyi gerçekleştirmek için kullanılan nesneye başvuran bir özellik; a <xref:System.Data.Common.RowUpdatedEventArgs> `RowUpdated` Güncelleştirilmiş `DataRow` bilgileri içeren nesneye başvuran özellik; ne tür bir güncelleştirme `StatementType` gerçekleştirilmekte `TableMapping`olan bir özellik; varsa,, varsa, ve `Status` işlemi.  
  
 `Status` Özelliği, işlem sırasında bir hata oluşup olmadığını ve isterseniz geçerli ve sonuç satırlarıyla eylemleri denetlemek için kullanabilirsiniz. Olay gerçekleştiğinde, `Status` özelliği ya `ErrorsOccurred`da `Continue` değerine eşittir. Aşağıdaki tabloda, güncelleştirme sırasında sonraki işlemleri denetlemek için `Status` özelliği ayarlayabileceğiniz değerler gösterilmektedir.  
  
|Durum|Açıklama|  
|------------|-----------------|  
|`Continue`|Güncelleştirme işlemine devam edin.|  
|`ErrorsOccurred`|Güncelleştirme işlemini iptal edin ve bir özel durum oluşturun.|  
|`SkipCurrentRow`|Geçerli satırı yoksayın ve güncelleştirme işlemine devam edin.|  
|`SkipAllRemainingRows`|Güncelleştirme işlemini iptal edin, ancak özel durum oluşturmaz.|  
  
 `Status` Özelliği olarak`ErrorsOccurred` ayarlamak bir özel durumun oluşturulmasına neden olur. `Errors` Özelliği istenen özel duruma ayarlayarak hangi özel durumun oluşturulmuş olduğunu denetleyebilirsiniz. İçin `Status` diğer değerlerden birini kullanmak, bir özel durumun oluşturulmasını engeller.  
  
 Ayrıca, `ContinueUpdateOnError` güncelleştirilmiş satırlar için hataları işlemek üzere özelliğini de kullanabilirsiniz. İse `DataAdapter.ContinueUpdateOnError` `RowError` , bir satırdaki bir güncelleştirme bir özel durumla sonuçlanmışsa, özel durumun metni belirli bir satırın bilgilerine konur ve işleme özel durum oluşturmadan devam eder. `true` Bu, bir hata ile karşılaşıldığında hatalara yanıt vermenize `Update` olanak sağlayan `RowUpdated` olaya karşılık olarak hatalara yanıt vermenize olanak sağlar.  
  
 Aşağıdaki kod örneği, olay işleyicilerinin nasıl ekleneceğini ve kaldırılacağını gösterir. Olay `RowUpdating` işleyicisi, bir zaman damgasıyla silinen tüm kayıtların günlüğünü yazar. `RowError`  =  `ContinueUpdateOnError`Olay işleyicisi `true`, içindekisatırınözelliğinehatabilgileriniekler,özeldurumubastırırveişlemedevameder(davranışınıyansıtma).`DataSet` `RowUpdated`  
  
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
 İşlemsırasında`Fill` bir `FillError` hata oluştuğunda olayı yayınlar.`DataAdapter` Bu tür bir hata genellikle, eklenmekte olan satırdaki veriler bir duyarlık kaybı olmadan bir .NET Framework türüne dönüştürülemiyorsa oluşur.  
  
 `Fill` İşlem sırasında bir hata oluşursa, geçerli satır `DataTable`öğesine eklenmez. Olay, hatayı çözmenize ve satırı eklemenize, ya da dışlanan satırı yoksaymanızı ve `Fill` işleme devam etmenizi sağlar. `FillError`  
  
 Olaya`FillError` geçilen, `FillErrorEventArgs` hatalara yanıt vermenize ve bunları çözmenize olanak sağlayan çeşitli özellikler içerebilir. Aşağıdaki tabloda `FillErrorEventArgs` nesnesinin özellikleri gösterilmektedir.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|`Errors`|`Exception` Bu oluştu.|  
|`DataTable`|Hata oluştuğunda Doldurulmakta olan nesne.`DataTable`|  
|`Values`|Hata oluştuğunda eklenmekte olan satırın değerlerini içeren bir nesne dizisi. `Values` Dizinin sıralı başvuruları, eklenmekte olan satır sütunlarının sıralı başvurularına karşılık gelir. Örneğin, `Values[0]` satırın ilk sütunu olarak eklenmekte olan değerdir.|  
|`Continue`|Bir özel durum oluşturulup oluşturulmayacağını seçmenize olanak sağlar. Özelliği olarak `false` ayarlamak geçerli`Fill` işlemi durdurur ve bir özel durum oluşturulur. `Continue` Hataya rağmen `true` `Continue` işleme`Fill` devam etmek için ayarlama.|  
  
 Aşağıdaki kod örneği, `FillError` `DataAdapter`olayı için bir olay işleyicisi ekler. `FillError` Olay kodunda örnek, özel duruma yanıt verme fırsatı sağlayarak duyarlık kaybı için olası olup olmadığını belirler.  
  
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

- [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [DataSet Olaylarını İşleme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)
- [DataTable Olaylarını İşleme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)
- [Olaylar](../../../standard/events/index.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
