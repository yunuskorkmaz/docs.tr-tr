---
title: DataAdapter Olaylarını İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: 8438a7b54ca19625687ab96386384cf62ae62d11
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783805"
---
# <a name="handling-dataadapter-events"></a><span data-ttu-id="3a6c4-102">DataAdapter Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="3a6c4-102">Handling DataAdapter Events</span></span>
<span data-ttu-id="3a6c4-103">ADO.net <xref:System.Data.Common.DataAdapter> , veri kaynağındaki verilerde yapılan değişikliklere yanıt vermek için kullanabileceğiniz üç olay sunar.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-103">The ADO.NET <xref:System.Data.Common.DataAdapter> exposes three events that you can use to respond to changes made to data at the data source.</span></span> <span data-ttu-id="3a6c4-104">Aşağıdaki tabloda `DataAdapter` olaylar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-104">The following table shows the `DataAdapter` events.</span></span>  
  
|<span data-ttu-id="3a6c4-105">Olay</span><span class="sxs-lookup"><span data-stu-id="3a6c4-105">Event</span></span>|<span data-ttu-id="3a6c4-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a6c4-106">Description</span></span>|  
|-----------|-----------------|  
|`RowUpdating`|<span data-ttu-id="3a6c4-107">Bir satırdaki güncelleştirme, ekleme veya silme işlemi ( `Update` metotlardan birine yapılan bir çağrı ile) başlamak üzere.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-107">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is about to begin.</span></span>|  
|`RowUpdated`|<span data-ttu-id="3a6c4-108">Bir satırdaki güncelleştirme, ekleme veya silme işlemi ( `Update` metotlardan birine yapılan bir çağrı ile) tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-108">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is complete.</span></span>|  
|`FillError`|<span data-ttu-id="3a6c4-109">`Fill` İşlem sırasında bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-109">An error has occurred during a `Fill` operation.</span></span>|  
  
## <a name="rowupdating-and-rowupdated"></a><span data-ttu-id="3a6c4-110">RowUpdating ve RowUpdated</span><span class="sxs-lookup"><span data-stu-id="3a6c4-110">RowUpdating and RowUpdated</span></span>  
 <span data-ttu-id="3a6c4-111">`RowUpdating`, <xref:System.Data.DataSet> öğesinden bir satırdaki herhangi bir güncelleştirme veri kaynağında işlenmeden önce tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-111">`RowUpdating` is raised before any update to a row from the <xref:System.Data.DataSet> has been processed at the data source.</span></span> <span data-ttu-id="3a6c4-112">`RowUpdated`, `DataSet` öğesinden bir satırdaki herhangi bir güncelleştirme veri kaynağında işlendikten sonra oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-112">`RowUpdated` is raised after any update to a row from the `DataSet` has been processed at the data source.</span></span> <span data-ttu-id="3a6c4-113">Sonuç olarak, güncelleştirme davranışını yapmadan önce `RowUpdating` değiştirmek için, bir güncelleştirme gerçekleştiğinde, güncelleştirilmiş bir satıra yönelik bir başvuruyu sürdürmek için, geçerli güncelleştirmeyi iptal etmek ve daha sonra işlenecek bir toplu işlem için zamanlamak üzere, bir güncelleştirme gerçekleştiğinde ek işleme sağlamak için kullanabilirsiniz vb.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-113">As a result, you can use `RowUpdating` to modify update behavior before it happens, to provide additional handling when an update will occur, to retain a reference to an updated row, to cancel the current update and schedule it for a batch process to be processed later, and so on.</span></span> <span data-ttu-id="3a6c4-114">`RowUpdated`, güncelleştirme sırasında oluşan hatalara ve özel durumlara yanıt vermek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-114">`RowUpdated` is useful for responding to errors and exceptions that occur during the update.</span></span> <span data-ttu-id="3a6c4-115">Öğesine `DataSet`hata bilgilerini ve yeniden deneme mantığını ve benzerlerini de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-115">You can add error information to the `DataSet`, as well as retry logic, and so on.</span></span>  
  
 <span data-ttu-id="3a6c4-116"><xref:System.Data.Common.RowUpdatingEventArgs> `Command` `Row` Ve olaylarına geçirilen`RowUpdating`bağımsızdeğişkenler şunlardır :`Command` güncelleştirmeyi gerçekleştirmek için kullanılan nesneye başvuran bir özellik; a <xref:System.Data.Common.RowUpdatedEventArgs> `RowUpdated` Güncelleştirilmiş `DataRow` bilgileri içeren nesneye başvuran özellik; ne tür bir güncelleştirme `StatementType` gerçekleştirilmekte `TableMapping`olan bir özellik; varsa,, varsa, ve `Status` işlemi.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-116">The <xref:System.Data.Common.RowUpdatingEventArgs> and <xref:System.Data.Common.RowUpdatedEventArgs> arguments passed to the `RowUpdating` and `RowUpdated` events include the following: a `Command` property that references the `Command` object being used to perform the update; a `Row` property that references the `DataRow` object containing the updated information; a `StatementType` property for what type of update is being performed; the `TableMapping`, if applicable; and the `Status` of the operation.</span></span>  
  
 <span data-ttu-id="3a6c4-117">`Status` Özelliği, işlem sırasında bir hata oluşup olmadığını ve isterseniz geçerli ve sonuç satırlarıyla eylemleri denetlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-117">You can use the `Status` property to determine if an error has occurred during the operation and, if desired, to control the actions against the current and resulting rows.</span></span> <span data-ttu-id="3a6c4-118">Olay gerçekleştiğinde, `Status` özelliği ya `ErrorsOccurred`da `Continue` değerine eşittir.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-118">When the event occurs, the `Status` property equals either `Continue` or `ErrorsOccurred`.</span></span> <span data-ttu-id="3a6c4-119">Aşağıdaki tabloda, güncelleştirme sırasında sonraki işlemleri denetlemek için `Status` özelliği ayarlayabileceğiniz değerler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-119">The following table shows the values to which you can set the `Status` property in order to control later actions during the update.</span></span>  
  
|<span data-ttu-id="3a6c4-120">Durum</span><span class="sxs-lookup"><span data-stu-id="3a6c4-120">Status</span></span>|<span data-ttu-id="3a6c4-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a6c4-121">Description</span></span>|  
|------------|-----------------|  
|`Continue`|<span data-ttu-id="3a6c4-122">Güncelleştirme işlemine devam edin.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-122">Continue the update operation.</span></span>|  
|`ErrorsOccurred`|<span data-ttu-id="3a6c4-123">Güncelleştirme işlemini iptal edin ve bir özel durum oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-123">Abort the update operation and throw an exception.</span></span>|  
|`SkipCurrentRow`|<span data-ttu-id="3a6c4-124">Geçerli satırı yoksayın ve güncelleştirme işlemine devam edin.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-124">Ignore the current row and continue the update operation.</span></span>|  
|`SkipAllRemainingRows`|<span data-ttu-id="3a6c4-125">Güncelleştirme işlemini iptal edin, ancak özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-125">Abort the update operation but do not throw an exception.</span></span>|  
  
 <span data-ttu-id="3a6c4-126">`Status` Özelliği olarak`ErrorsOccurred` ayarlamak bir özel durumun oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-126">Setting the `Status` property to `ErrorsOccurred` causes an exception to be thrown.</span></span> <span data-ttu-id="3a6c4-127">`Errors` Özelliği istenen özel duruma ayarlayarak hangi özel durumun oluşturulmuş olduğunu denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-127">You can control which exception is thrown by setting the `Errors` property to the desired exception.</span></span> <span data-ttu-id="3a6c4-128">İçin `Status` diğer değerlerden birini kullanmak, bir özel durumun oluşturulmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-128">Using one of the other values for `Status` prevents an exception from being thrown.</span></span>  
  
 <span data-ttu-id="3a6c4-129">Ayrıca, `ContinueUpdateOnError` güncelleştirilmiş satırlar için hataları işlemek üzere özelliğini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-129">You can also use the `ContinueUpdateOnError` property to handle errors for updated rows.</span></span> <span data-ttu-id="3a6c4-130">İse `DataAdapter.ContinueUpdateOnError` `RowError` , bir satırdaki bir güncelleştirme bir özel durumla sonuçlanmışsa, özel durumun metni belirli bir satırın bilgilerine konur ve işleme özel durum oluşturmadan devam eder. `true`</span><span class="sxs-lookup"><span data-stu-id="3a6c4-130">If `DataAdapter.ContinueUpdateOnError` is `true`, when an update to a row results in an exception being thrown, the text of the exception is placed into the `RowError` information of the particular row, and processing continues without throwing an exception.</span></span> <span data-ttu-id="3a6c4-131">Bu, bir hata ile karşılaşıldığında hatalara yanıt vermenize `Update` olanak sağlayan `RowUpdated` olaya karşılık olarak hatalara yanıt vermenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-131">This enables you to respond to errors when the `Update` is complete, in contrast to the `RowUpdated` event, which enables you to respond to errors when the error is encountered.</span></span>  
  
 <span data-ttu-id="3a6c4-132">Aşağıdaki kod örneği, olay işleyicilerinin nasıl ekleneceğini ve kaldırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-132">The following code sample shows how to both add and remove event handlers.</span></span> <span data-ttu-id="3a6c4-133">Olay `RowUpdating` işleyicisi, bir zaman damgasıyla silinen tüm kayıtların günlüğünü yazar.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-133">The `RowUpdating` event handler writes a log of all deleted records with a time stamp.</span></span> <span data-ttu-id="3a6c4-134">`RowError`  =  `ContinueUpdateOnError`Olay işleyicisi `true`, içindekisatırınözelliğinehatabilgileriniekler,özeldurumubastırırveişlemedevameder(davranışınıyansıtma).`DataSet` `RowUpdated`</span><span class="sxs-lookup"><span data-stu-id="3a6c4-134">The `RowUpdated` event handler adds error information to the `RowError` property of the row in the `DataSet`, suppresses the exception, and continues processing (mirroring the behavior of `ContinueUpdateOnError` = `true`).</span></span>  
  
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
  
## <a name="fillerror"></a><span data-ttu-id="3a6c4-135">FillError</span><span class="sxs-lookup"><span data-stu-id="3a6c4-135">FillError</span></span>  
 <span data-ttu-id="3a6c4-136">İşlemsırasında`Fill` bir `FillError` hata oluştuğunda olayı yayınlar.`DataAdapter`</span><span class="sxs-lookup"><span data-stu-id="3a6c4-136">The `DataAdapter` issues the `FillError` event when an error occurs during a `Fill` operation.</span></span> <span data-ttu-id="3a6c4-137">Bu tür bir hata genellikle, eklenmekte olan satırdaki veriler bir duyarlık kaybı olmadan bir .NET Framework türüne dönüştürülemiyorsa oluşur.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-137">This type of error commonly occurs when the data in the row being added could not be converted to a .NET Framework type without some loss of precision.</span></span>  
  
 <span data-ttu-id="3a6c4-138">`Fill` İşlem sırasında bir hata oluşursa, geçerli satır `DataTable`öğesine eklenmez.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-138">If an error occurs during a `Fill` operation, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="3a6c4-139">Olay, hatayı çözmenize ve satırı eklemenize, ya da dışlanan satırı yoksaymanızı ve `Fill` işleme devam etmenizi sağlar. `FillError`</span><span class="sxs-lookup"><span data-stu-id="3a6c4-139">The `FillError` event enables you to resolve the error and add the row, or to ignore the excluded row and continue the `Fill` operation.</span></span>  
  
 <span data-ttu-id="3a6c4-140">Olaya`FillError` geçilen, `FillErrorEventArgs` hatalara yanıt vermenize ve bunları çözmenize olanak sağlayan çeşitli özellikler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-140">The `FillErrorEventArgs` passed to the `FillError` event can contain several properties that enable you to respond to and resolve errors.</span></span> <span data-ttu-id="3a6c4-141">Aşağıdaki tabloda `FillErrorEventArgs` nesnesinin özellikleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-141">The following table shows the properties of the `FillErrorEventArgs` object.</span></span>  
  
|<span data-ttu-id="3a6c4-142">Özellik</span><span class="sxs-lookup"><span data-stu-id="3a6c4-142">Property</span></span>|<span data-ttu-id="3a6c4-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a6c4-143">Description</span></span>|  
|--------------|-----------------|  
|`Errors`|<span data-ttu-id="3a6c4-144">`Exception` Bu oluştu.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-144">The `Exception` that occurred.</span></span>|  
|`DataTable`|<span data-ttu-id="3a6c4-145">Hata oluştuğunda Doldurulmakta olan nesne.`DataTable`</span><span class="sxs-lookup"><span data-stu-id="3a6c4-145">The `DataTable` object being filled when the error occurred.</span></span>|  
|`Values`|<span data-ttu-id="3a6c4-146">Hata oluştuğunda eklenmekte olan satırın değerlerini içeren bir nesne dizisi.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-146">An array of objects that contains the values of the row being added when the error occurred.</span></span> <span data-ttu-id="3a6c4-147">`Values` Dizinin sıralı başvuruları, eklenmekte olan satır sütunlarının sıralı başvurularına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-147">The ordinal references of the `Values` array correspond to the ordinal references of the columns of the row being added.</span></span> <span data-ttu-id="3a6c4-148">Örneğin, `Values[0]` satırın ilk sütunu olarak eklenmekte olan değerdir.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-148">For example, `Values[0]` is the value that was being added as the first column of the row.</span></span>|  
|`Continue`|<span data-ttu-id="3a6c4-149">Bir özel durum oluşturulup oluşturulmayacağını seçmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-149">Allows you to choose whether or not to throw an exception.</span></span> <span data-ttu-id="3a6c4-150">Özelliği olarak `false` ayarlamak geçerli`Fill` işlemi durdurur ve bir özel durum oluşturulur. `Continue`</span><span class="sxs-lookup"><span data-stu-id="3a6c4-150">Setting the `Continue` property to `false` will halt the current `Fill` operation, and an exception will be thrown.</span></span> <span data-ttu-id="3a6c4-151">Hataya rağmen `true` `Continue` işleme`Fill` devam etmek için ayarlama.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-151">Setting `Continue` to `true` continues the `Fill` operation despite the error.</span></span>|  
  
 <span data-ttu-id="3a6c4-152">Aşağıdaki kod örneği, `FillError` `DataAdapter`olayı için bir olay işleyicisi ekler.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-152">The following code example adds an event handler for the `FillError` event of the `DataAdapter`.</span></span> <span data-ttu-id="3a6c4-153">`FillError` Olay kodunda örnek, özel duruma yanıt verme fırsatı sağlayarak duyarlık kaybı için olası olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-153">In the `FillError` event code, the example determines if there is the potential for precision loss, providing the opportunity to respond to the exception.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a6c4-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a6c4-154">See also</span></span>

- [<span data-ttu-id="3a6c4-155">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="3a6c4-155">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="3a6c4-156">DataSet Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="3a6c4-156">Handling DataSet Events</span></span>](./dataset-datatable-dataview/handling-dataset-events.md)
- [<span data-ttu-id="3a6c4-157">DataTable Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="3a6c4-157">Handling DataTable Events</span></span>](./dataset-datatable-dataview/handling-datatable-events.md)
- [<span data-ttu-id="3a6c4-158">Olaylar</span><span class="sxs-lookup"><span data-stu-id="3a6c4-158">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="3a6c4-159">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3a6c4-159">ADO.NET Overview</span></span>](ado-net-overview.md)
