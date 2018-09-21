---
title: DataAdapter olaylarını işleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 11515b25-ee49-4b1d-9294-a142147c1ec5
ms.openlocfilehash: 3c2158e94f936dd2b28fe46310fd96df8dbc50fb
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46525558"
---
# <a name="handling-dataadapter-events"></a><span data-ttu-id="9e8b4-102">DataAdapter olaylarını işleme</span><span class="sxs-lookup"><span data-stu-id="9e8b4-102">Handling DataAdapter Events</span></span>
<span data-ttu-id="9e8b4-103">ADO.NET <xref:System.Data.Common.DataAdapter> veri kaynağındaki verilere yapılan değişikliklere yanıt vermek için kullanabileceğiniz üç olayları gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-103">The ADO.NET <xref:System.Data.Common.DataAdapter> exposes three events that you can use to respond to changes made to data at the data source.</span></span> <span data-ttu-id="9e8b4-104">Aşağıdaki tabloda `DataAdapter` olayları.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-104">The following table shows the `DataAdapter` events.</span></span>  
  
|<span data-ttu-id="9e8b4-105">Olay</span><span class="sxs-lookup"><span data-stu-id="9e8b4-105">Event</span></span>|<span data-ttu-id="9e8b4-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e8b4-106">Description</span></span>|  
|-----------|-----------------|  
|`RowUpdating`|<span data-ttu-id="9e8b4-107">Bir UPDATE, INSERT veya DELETE işlemi bir satıra (birine yapılan bir çağrıyla `Update` yöntemleri) hakkında başlamaktır.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-107">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is about to begin.</span></span>|  
|`RowUpdated`|<span data-ttu-id="9e8b4-108">Bir UPDATE, INSERT veya DELETE işlemi bir satıra (birine yapılan bir çağrıyla `Update` yöntemleri) tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-108">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is complete.</span></span>|  
|`FillError`|<span data-ttu-id="9e8b4-109">Sırasında bir hata oluştu bir `Fill` işlemi.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-109">An error has occurred during a `Fill` operation.</span></span>|  
  
## <a name="rowupdating-and-rowupdated"></a><span data-ttu-id="9e8b4-110">RowUpdating ve RowUpdated</span><span class="sxs-lookup"><span data-stu-id="9e8b4-110">RowUpdating and RowUpdated</span></span>  
 <span data-ttu-id="9e8b4-111">`RowUpdating` bir satırdan için önce herhangi bir güncelleştirme tetiklenir <xref:System.Data.DataSet> veri kaynağında işlendi.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-111">`RowUpdating` is raised before any update to a row from the <xref:System.Data.DataSet> has been processed at the data source.</span></span> <span data-ttu-id="9e8b4-112">`RowUpdated` herhangi bir satırı güncelleştirme sonra tetiklenen `DataSet` veri kaynağında işlendi.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-112">`RowUpdated` is raised after any update to a row from the `DataSet` has been processed at the data source.</span></span> <span data-ttu-id="9e8b4-113">Sonuç olarak, kullanabileceğiniz `RowUpdating` , gerçekleşmeden önce bir güncelleştirme meydana gelir, ek işleme sağlamak için geçerli güncelleştirme ve zamanlama için bir toplu işleme daha sonra işlenmek üzere iptal etmek için güncelleştirilmiş bir satır için başvuru korumak için güncelleştirme davranışını değiştirmek için , ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-113">As a result, you can use `RowUpdating` to modify update behavior before it happens, to provide additional handling when an update will occur, to retain a reference to an updated row, to cancel the current update and schedule it for a batch process to be processed later, and so on.</span></span> <span data-ttu-id="9e8b4-114">`RowUpdated` hatalar ve güncelleştirme sırasında oluşan özel durumlar için yanıt için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-114">`RowUpdated` is useful for responding to errors and exceptions that occur during the update.</span></span> <span data-ttu-id="9e8b4-115">Hata bilgilerini ekleyebilirsiniz `DataSet`, yanı sıra yeniden deneme mantığı ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-115">You can add error information to the `DataSet`, as well as retry logic, and so on.</span></span>  
  
 <span data-ttu-id="9e8b4-116"><xref:System.Data.Common.RowUpdatingEventArgs> Ve <xref:System.Data.Common.RowUpdatedEventArgs> geçirilen bağımsız değişkenler `RowUpdating` ve `RowUpdated` olayları aşağıdakileri içerir: bir `Command` başvuran özelliği `Command` ; güncelleştirme gerçekleştirmek için kullanılan nesne bir `Row` başvuran özelliği `DataRow` güncelleştirilmiş bilgileri içeren bir nesne bir `StatementType` ne tür bir güncelleştirme gerçekleştirilmekte olan için; özellik `TableMapping`, varsa; ve `Status` işlem.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-116">The <xref:System.Data.Common.RowUpdatingEventArgs> and <xref:System.Data.Common.RowUpdatedEventArgs> arguments passed to the `RowUpdating` and `RowUpdated` events include the following: a `Command` property that references the `Command` object being used to perform the update; a `Row` property that references the `DataRow` object containing the updated information; a `StatementType` property for what type of update is being performed; the `TableMapping`, if applicable; and the `Status` of the operation.</span></span>  
  
 <span data-ttu-id="9e8b4-117">Kullanabileceğiniz `Status` istenen işlemi sırasında bir hata oluştuğunda ve belirlemek için özellik geçerli ve sonuçta elde edilen satırları karşı eylemleri denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-117">You can use the `Status` property to determine if an error has occurred during the operation and, if desired, to control the actions against the current and resulting rows.</span></span> <span data-ttu-id="9e8b4-118">Olay gerçekleştiğinde `Status` özellik ya da eşittir `Continue` veya `ErrorsOccurred`.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-118">When the event occurs, the `Status` property equals either `Continue` or `ErrorsOccurred`.</span></span> <span data-ttu-id="9e8b4-119">Aşağıdaki tabloda, ayarlayabileceği değerleri gösterir `Status` özelliği güncelleştirme sırasında sonraki eylemler denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-119">The following table shows the values to which you can set the `Status` property in order to control later actions during the update.</span></span>  
  
|<span data-ttu-id="9e8b4-120">Durum</span><span class="sxs-lookup"><span data-stu-id="9e8b4-120">Status</span></span>|<span data-ttu-id="9e8b4-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e8b4-121">Description</span></span>|  
|------------|-----------------|  
|`Continue`|<span data-ttu-id="9e8b4-122">Güncelleştirme işlemi devam edin.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-122">Continue the update operation.</span></span>|  
|`ErrorsOccurred`|<span data-ttu-id="9e8b4-123">Güncelleştirme işlemi iptal ve özel durum.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-123">Abort the update operation and throw an exception.</span></span>|  
|`SkipCurrentRow`|<span data-ttu-id="9e8b4-124">Geçerli satırın yoksay ve güncelleştirme işlemi devam edin.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-124">Ignore the current row and continue the update operation.</span></span>|  
|`SkipAllRemainingRows`|<span data-ttu-id="9e8b4-125">Güncelleştirme işlemi iptal etmek, ancak bir özel durum oluşturması beklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-125">Abort the update operation but do not throw an exception.</span></span>|  
  
 <span data-ttu-id="9e8b4-126">Ayarı `Status` özelliğini `ErrorsOccurred` bir özel durum oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-126">Setting the `Status` property to `ErrorsOccurred` causes an exception to be thrown.</span></span> <span data-ttu-id="9e8b4-127">Hangi ayarlayarak özel durum denetleyebilirsiniz `Errors` özelliği istenen özel duruma bakın.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-127">You can control which exception is thrown by setting the `Errors` property to the desired exception.</span></span> <span data-ttu-id="9e8b4-128">Diğer değerleri kullanarak `Status` öğesinden oluşturulan bir özel durum engeller.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-128">Using one of the other values for `Status` prevents an exception from being thrown.</span></span>  
  
 <span data-ttu-id="9e8b4-129">Ayrıca `ContinueUpdateOnError` hatalarını işlemek için özellik satır güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-129">You can also use the `ContinueUpdateOnError` property to handle errors for updated rows.</span></span> <span data-ttu-id="9e8b4-130">Varsa `DataAdapter.ContinueUpdateOnError` olduğu `true`, oluşturulan bir özel durum satır sonuçlarında güncelleştirmeye, özel durum metni içine yerleştirildiğinde `RowError` belirli bir satır ve işleme bilgileri, bir özel durum oluşturmadan devam eder.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-130">If `DataAdapter.ContinueUpdateOnError` is `true`, when an update to a row results in an exception being thrown, the text of the exception is placed into the `RowError` information of the particular row, and processing continues without throwing an exception.</span></span> <span data-ttu-id="9e8b4-131">Bu sayede hatalar için yanıt vermede olduğunda `Update` aksine tamamlandıktan `RowUpdated` hata ile karşılaşıldığında hatalar için yanıt sağlayan bir olay.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-131">This enables you to respond to errors when the `Update` is complete, in contrast to the `RowUpdated` event, which enables you to respond to errors when the error is encountered.</span></span>  
  
 <span data-ttu-id="9e8b4-132">Aşağıdaki kod örneği, hem ekleyip olay işleyicileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-132">The following code sample shows how to both add and remove event handlers.</span></span> <span data-ttu-id="9e8b4-133">`RowUpdating` Olay işleyicisi zaman damgası ile silinen tüm kayıtları günlüğe yazar.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-133">The `RowUpdating` event handler writes a log of all deleted records with a time stamp.</span></span> <span data-ttu-id="9e8b4-134">`RowUpdated` Olay işleyicisi ekler hata bilgilerini `RowError` özelliği içindeki satırın `DataSet`özel durumu gizler ve işleme devam eder (yansıtma davranışını `ContinueUpdateOnError`  =  `true`).</span><span class="sxs-lookup"><span data-stu-id="9e8b4-134">The `RowUpdated` event handler adds error information to the `RowError` property of the row in the `DataSet`, suppresses the exception, and continues processing (mirroring the behavior of `ContinueUpdateOnError` = `true`).</span></span>  
  
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
  
## <a name="fillerror"></a><span data-ttu-id="9e8b4-135">FillError</span><span class="sxs-lookup"><span data-stu-id="9e8b4-135">FillError</span></span>  
 <span data-ttu-id="9e8b4-136">`DataAdapter` Sorunları `FillError` sırasında bir hata oluştuğunda olay bir `Fill` işlemi.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-136">The `DataAdapter` issues the `FillError` event when an error occurs during a `Fill` operation.</span></span> <span data-ttu-id="9e8b4-137">Bu tür, yaygın olarak eklenen bir satırdaki verileri bazı kesinlik kaybı olmadan bir .NET Framework türüne dönüştürülemedi oluşur.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-137">This type of error commonly occurs when the data in the row being added could not be converted to a .NET Framework type without some loss of precision.</span></span>  
  
 <span data-ttu-id="9e8b4-138">Sırasında bir hata oluşursa bir `Fill` işlemi, geçerli satır eklenmez `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-138">If an error occurs during a `Fill` operation, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="9e8b4-139">`FillError` Olay sağlar, hatayı giderin ve satır eklemek için veya dışlanmış bir satır yoksayıp devam etmek `Fill` işlemi.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-139">The `FillError` event enables you to resolve the error and add the row, or to ignore the excluded row and continue the `Fill` operation.</span></span>  
  
 <span data-ttu-id="9e8b4-140">`FillErrorEventArgs` Geçirilen `FillError` olay yanıtlama ve hataları çözün olanak tanıyan çeşitli özellikler içerir.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-140">The `FillErrorEventArgs` passed to the `FillError` event can contain several properties that enable you to respond to and resolve errors.</span></span> <span data-ttu-id="9e8b4-141">Aşağıdaki tablo özelliklerini gösterir `FillErrorEventArgs` nesne.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-141">The following table shows the properties of the `FillErrorEventArgs` object.</span></span>  
  
|<span data-ttu-id="9e8b4-142">Özellik</span><span class="sxs-lookup"><span data-stu-id="9e8b4-142">Property</span></span>|<span data-ttu-id="9e8b4-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e8b4-143">Description</span></span>|  
|--------------|-----------------|  
|`Errors`|<span data-ttu-id="9e8b4-144">`Exception` Oluştu.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-144">The `Exception` that occurred.</span></span>|  
|`DataTable`|<span data-ttu-id="9e8b4-145">`DataTable` Hata oluştuğunda doldurulan nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-145">The `DataTable` object being filled when the error occurred.</span></span>|  
|`Values`|<span data-ttu-id="9e8b4-146">Hata oluştuğunda eklenen satır değerlerini içeren bir dizi nesne.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-146">An array of objects that contains the values of the row being added when the error occurred.</span></span> <span data-ttu-id="9e8b4-147">Sıra başvuruyor `Values` dizi eklenen satırın sütun sıralı başvuruları karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-147">The ordinal references of the `Values` array correspond to the ordinal references of the columns of the row being added.</span></span> <span data-ttu-id="9e8b4-148">Örneğin, `Values[0]` satırın ilk sütunu olarak eklenen değerdir.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-148">For example, `Values[0]` is the value that was being added as the first column of the row.</span></span>|  
|`Continue`|<span data-ttu-id="9e8b4-149">Özel durum gerekip gerekmediğini seçmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-149">Allows you to choose whether or not to throw an exception.</span></span> <span data-ttu-id="9e8b4-150">Ayarı `Continue` özelliğini `false` geçerli durdurulur `Fill` işlemi ve bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-150">Setting the `Continue` property to `false` will halt the current `Fill` operation, and an exception will be thrown.</span></span> <span data-ttu-id="9e8b4-151">Ayarı `Continue` için `true` devam `Fill` hata rağmen işlemi.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-151">Setting `Continue` to `true` continues the `Fill` operation despite the error.</span></span>|  
  
 <span data-ttu-id="9e8b4-152">Aşağıdaki kod örneği için bir olay işleyicisi ekler `FillError` olayı `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-152">The following code example adds an event handler for the `FillError` event of the `DataAdapter`.</span></span> <span data-ttu-id="9e8b4-153">İçinde `FillError` örnek olay kodu belirler duyarlık kaybı, özel durum yanıt olanağı sağlayan olası olup olmadığını.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-153">In the `FillError` event code, the example determines if there is the potential for precision loss, providing the opportunity to respond to the exception.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9e8b4-154">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e8b4-154">See Also</span></span>  
 [<span data-ttu-id="9e8b4-155">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="9e8b4-155">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="9e8b4-156">DataSet Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="9e8b4-156">Handling DataSet Events</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 [<span data-ttu-id="9e8b4-157">DataTable Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="9e8b4-157">Handling DataTable Events</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [<span data-ttu-id="9e8b4-158">Olaylar</span><span class="sxs-lookup"><span data-stu-id="9e8b4-158">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="9e8b4-159">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="9e8b4-159">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
