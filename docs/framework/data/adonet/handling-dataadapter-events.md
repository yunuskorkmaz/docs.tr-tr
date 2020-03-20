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
# <a name="handling-dataadapter-events"></a><span data-ttu-id="64ac7-102">DataAdapter Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="64ac7-102">Handling DataAdapter Events</span></span>
<span data-ttu-id="64ac7-103">ADO.NET, <xref:System.Data.Common.DataAdapter> veri kaynağındaki verilerde yapılan değişikliklere yanıt vermek için kullanabileceğiniz üç olayı ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="64ac7-103">The ADO.NET <xref:System.Data.Common.DataAdapter> exposes three events that you can use to respond to changes made to data at the data source.</span></span> <span data-ttu-id="64ac7-104">Aşağıdaki tabloolayları `DataAdapter` gösterir.</span><span class="sxs-lookup"><span data-stu-id="64ac7-104">The following table shows the `DataAdapter` events.</span></span>  
  
|<span data-ttu-id="64ac7-105">Olay</span><span class="sxs-lookup"><span data-stu-id="64ac7-105">Event</span></span>|<span data-ttu-id="64ac7-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64ac7-106">Description</span></span>|  
|-----------|-----------------|  
|`RowUpdating`|<span data-ttu-id="64ac7-107">Bir satırda `Update` (yöntemlerden birine yapılan bir çağrıyla) bir UPDATE, INSERT veya DELETE işlemi başlamak üzeredir.</span><span class="sxs-lookup"><span data-stu-id="64ac7-107">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is about to begin.</span></span>|  
|`RowUpdated`|<span data-ttu-id="64ac7-108">Bir satırdaki `Update` (yöntemlerden birine yapılan bir çağrıyla) BIR UPDATE, INSERT veya DELETE işlemi tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="64ac7-108">An UPDATE, INSERT, or DELETE operation on a row (by a call to one of the `Update` methods) is complete.</span></span>|  
|`FillError`|<span data-ttu-id="64ac7-109">Bir işlem sırasında bir `Fill` hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="64ac7-109">An error has occurred during a `Fill` operation.</span></span>|  
  
## <a name="rowupdating-and-rowupdated"></a><span data-ttu-id="64ac7-110">Satır Güncelleme ve Satır Güncelleme</span><span class="sxs-lookup"><span data-stu-id="64ac7-110">RowUpdating and RowUpdated</span></span>  
 <span data-ttu-id="64ac7-111">`RowUpdating`veri kaynağında işlenen bir satıra <xref:System.Data.DataSet> herhangi bir güncelleştirme önce yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="64ac7-111">`RowUpdating` is raised before any update to a row from the <xref:System.Data.DataSet> has been processed at the data source.</span></span> <span data-ttu-id="64ac7-112">`RowUpdated`veri kaynağında işlenen bir satıra `DataSet` herhangi bir güncelleştirme sonra yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="64ac7-112">`RowUpdated` is raised after any update to a row from the `DataSet` has been processed at the data source.</span></span> <span data-ttu-id="64ac7-113">Sonuç olarak, güncelleştirme `RowUpdating` davranışını gerçekleşmeden önce değiştirmek, güncelleştirme ne zaman gerçekleşeceğini ek işleme sağlamak, güncelleştirilmiş bir satıra başvuruyu tutmak, geçerli güncelleştirmeyi iptal etmek ve daha sonra işlenecek bir toplu iş işlemi için zamanlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64ac7-113">As a result, you can use `RowUpdating` to modify update behavior before it happens, to provide additional handling when an update will occur, to retain a reference to an updated row, to cancel the current update and schedule it for a batch process to be processed later, and so on.</span></span> <span data-ttu-id="64ac7-114">`RowUpdated`güncelleştirme sırasında oluşan hataları ve özel durumları yanıtlamak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="64ac7-114">`RowUpdated` is useful for responding to errors and exceptions that occur during the update.</span></span> <span data-ttu-id="64ac7-115">Hata bilgilerini `DataSet`, yeniden deneme mantığına ve benzeri bilgilere ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64ac7-115">You can add error information to the `DataSet`, as well as retry logic, and so on.</span></span>  
  
 <span data-ttu-id="64ac7-116">Ve <xref:System.Data.Common.RowUpdatingEventArgs> <xref:System.Data.Common.RowUpdatedEventArgs> bağımsız değişkenlere `RowUpdating` `RowUpdated` geçirilen ve olaylar `Command` şunlardır: `Command` güncelleştirmeyi gerçekleştirmek için kullanılan nesneye başvuran bir özellik; güncelleştirilmiş bilgileri `DataRow` içeren nesneye başvuran bir `Row` özellik; ne `StatementType` tür bir güncelleştirme nin gerçekleştirildiği ne tür bir özellik; `TableMapping`, varsa; `Status` ve operasyonun.</span><span class="sxs-lookup"><span data-stu-id="64ac7-116">The <xref:System.Data.Common.RowUpdatingEventArgs> and <xref:System.Data.Common.RowUpdatedEventArgs> arguments passed to the `RowUpdating` and `RowUpdated` events include the following: a `Command` property that references the `Command` object being used to perform the update; a `Row` property that references the `DataRow` object containing the updated information; a `StatementType` property for what type of update is being performed; the `TableMapping`, if applicable; and the `Status` of the operation.</span></span>  
  
 <span data-ttu-id="64ac7-117">`Status` İşlem sırasında bir hata oluşup oluşmadiğini belirlemek ve istenirse, eylemleri geçerli ve ortaya çıkan satırlara karşı denetlemek için özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64ac7-117">You can use the `Status` property to determine if an error has occurred during the operation and, if desired, to control the actions against the current and resulting rows.</span></span> <span data-ttu-id="64ac7-118">Olay oluştuğunda, `Status` özellik eşittir ya `Continue` `ErrorsOccurred`da .</span><span class="sxs-lookup"><span data-stu-id="64ac7-118">When the event occurs, the `Status` property equals either `Continue` or `ErrorsOccurred`.</span></span> <span data-ttu-id="64ac7-119">Aşağıdaki tablo, güncelleştirme sırasında sonraki eylemleri `Status` denetlemek için özelliği ayarlayabileceğiniz değerleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="64ac7-119">The following table shows the values to which you can set the `Status` property in order to control later actions during the update.</span></span>  
  
|<span data-ttu-id="64ac7-120">Durum</span><span class="sxs-lookup"><span data-stu-id="64ac7-120">Status</span></span>|<span data-ttu-id="64ac7-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64ac7-121">Description</span></span>|  
|------------|-----------------|  
|`Continue`|<span data-ttu-id="64ac7-122">Güncelleştirme işlemine devam edin.</span><span class="sxs-lookup"><span data-stu-id="64ac7-122">Continue the update operation.</span></span>|  
|`ErrorsOccurred`|<span data-ttu-id="64ac7-123">Güncelleştirme işlemini iptal edin ve bir özel durum atın.</span><span class="sxs-lookup"><span data-stu-id="64ac7-123">Abort the update operation and throw an exception.</span></span>|  
|`SkipCurrentRow`|<span data-ttu-id="64ac7-124">Geçerli satırı yoksayın ve güncelleştirme işlemine devam edin.</span><span class="sxs-lookup"><span data-stu-id="64ac7-124">Ignore the current row and continue the update operation.</span></span>|  
|`SkipAllRemainingRows`|<span data-ttu-id="64ac7-125">Güncelleştirme işlemini iptal edin, ancak bir özel durum atmayın.</span><span class="sxs-lookup"><span data-stu-id="64ac7-125">Abort the update operation but do not throw an exception.</span></span>|  
  
 <span data-ttu-id="64ac7-126">`Status` Özelliği, `ErrorsOccurred` özel bir özel durum atacak şekilde ayarlamak.</span><span class="sxs-lookup"><span data-stu-id="64ac7-126">Setting the `Status` property to `ErrorsOccurred` causes an exception to be thrown.</span></span> <span data-ttu-id="64ac7-127">`Errors` Özelliği istenilen özel durum için ayarlayarak hangi özel durum atılacağını denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64ac7-127">You can control which exception is thrown by setting the `Errors` property to the desired exception.</span></span> <span data-ttu-id="64ac7-128">Diğer değerlerden birini `Status` kullanmak, bir özel durum atılmasını önler.</span><span class="sxs-lookup"><span data-stu-id="64ac7-128">Using one of the other values for `Status` prevents an exception from being thrown.</span></span>  
  
 <span data-ttu-id="64ac7-129">Güncelleştirilmiş satırlar `ContinueUpdateOnError` için hataları işlemek için özelliği de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="64ac7-129">You can also use the `ContinueUpdateOnError` property to handle errors for updated rows.</span></span> <span data-ttu-id="64ac7-130">Eğer `DataAdapter.ContinueUpdateOnError` `true`ise, bir satıra güncelleştirme bir özel durum atılması ile sonuçlanırsa, özel durum metni belirli satırın `RowError` bilgilerine yerleştirilir ve işleme özel durum atmadan devam edilir.</span><span class="sxs-lookup"><span data-stu-id="64ac7-130">If `DataAdapter.ContinueUpdateOnError` is `true`, when an update to a row results in an exception being thrown, the text of the exception is placed into the `RowError` information of the particular row, and processing continues without throwing an exception.</span></span> <span data-ttu-id="64ac7-131">Bu, hatayla karşılaşıldığında `Update` hatalara yanıt vermenizi `RowUpdated` sağlayan olayın aksine, tamamlandığında hatalara yanıt vermenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="64ac7-131">This enables you to respond to errors when the `Update` is complete, in contrast to the `RowUpdated` event, which enables you to respond to errors when the error is encountered.</span></span>  
  
 <span data-ttu-id="64ac7-132">Aşağıdaki kod örneği, olay işleyicilerinin hem ekleyeceğini hem de kaldırılmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="64ac7-132">The following code sample shows how to both add and remove event handlers.</span></span> <span data-ttu-id="64ac7-133">Olay `RowUpdating` işleyicisi, silinen tüm kayıtların bir günlüğünü bir zaman damgası ile yazar.</span><span class="sxs-lookup"><span data-stu-id="64ac7-133">The `RowUpdating` event handler writes a log of all deleted records with a time stamp.</span></span> <span data-ttu-id="64ac7-134">`RowUpdated` Olay işleyicisi satırın `RowError` özelliğine hata `DataSet`bilgileri ekler, özel durumu bastırır ve işleme `ContinueUpdateOnError`  =  `true`devam eder (davranışı yansıtma).</span><span class="sxs-lookup"><span data-stu-id="64ac7-134">The `RowUpdated` event handler adds error information to the `RowError` property of the row in the `DataSet`, suppresses the exception, and continues processing (mirroring the behavior of `ContinueUpdateOnError` = `true`).</span></span>  
  
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
  
## <a name="fillerror"></a><span data-ttu-id="64ac7-135">Fillerror</span><span class="sxs-lookup"><span data-stu-id="64ac7-135">FillError</span></span>  
 <span data-ttu-id="64ac7-136">Bir `DataAdapter` `Fill` işlem `FillError` sırasında bir hata oluştuğunda sorunları.</span><span class="sxs-lookup"><span data-stu-id="64ac7-136">The `DataAdapter` issues the `FillError` event when an error occurs during a `Fill` operation.</span></span> <span data-ttu-id="64ac7-137">Bu tür hatalar genellikle, eklenen satırdaki verilerin bazı kesinlik kaybı olmadan bir .NET Framework türüne dönüştürülemediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="64ac7-137">This type of error commonly occurs when the data in the row being added could not be converted to a .NET Framework type without some loss of precision.</span></span>  
  
 <span data-ttu-id="64ac7-138">Bir işlem sırasında bir `Fill` hata oluşursa, geçerli `DataTable`satır .</span><span class="sxs-lookup"><span data-stu-id="64ac7-138">If an error occurs during a `Fill` operation, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="64ac7-139">Olay, `FillError` hatayı çözmenizi ve satırı eklemenizi veya dışlanan satırı yok `Fill` saymanızı ve işlemi devam etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="64ac7-139">The `FillError` event enables you to resolve the error and add the row, or to ignore the excluded row and continue the `Fill` operation.</span></span>  
  
 <span data-ttu-id="64ac7-140">`FillError` Olaya geçirilen, `FillErrorEventArgs` yanıt vermenizi ve hataları çözmenizi sağlayan birkaç özellik içerebilir.</span><span class="sxs-lookup"><span data-stu-id="64ac7-140">The `FillErrorEventArgs` passed to the `FillError` event can contain several properties that enable you to respond to and resolve errors.</span></span> <span data-ttu-id="64ac7-141">Aşağıdaki tablo nesnenin `FillErrorEventArgs` özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="64ac7-141">The following table shows the properties of the `FillErrorEventArgs` object.</span></span>  
  
|<span data-ttu-id="64ac7-142">Özellik</span><span class="sxs-lookup"><span data-stu-id="64ac7-142">Property</span></span>|<span data-ttu-id="64ac7-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64ac7-143">Description</span></span>|  
|--------------|-----------------|  
|`Errors`|<span data-ttu-id="64ac7-144">Olan `Exception` bu.</span><span class="sxs-lookup"><span data-stu-id="64ac7-144">The `Exception` that occurred.</span></span>|  
|`DataTable`|<span data-ttu-id="64ac7-145">Hata `DataTable` oluştuğunda doldurulan nesne.</span><span class="sxs-lookup"><span data-stu-id="64ac7-145">The `DataTable` object being filled when the error occurred.</span></span>|  
|`Values`|<span data-ttu-id="64ac7-146">Hata oluştuğunda eklenen satırın değerlerini içeren bir nesne dizisi.</span><span class="sxs-lookup"><span data-stu-id="64ac7-146">An array of objects that contains the values of the row being added when the error occurred.</span></span> <span data-ttu-id="64ac7-147">`Values` Dizinin ordinal referansları, eklenen satır sütunlarının ordinal başvurularına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="64ac7-147">The ordinal references of the `Values` array correspond to the ordinal references of the columns of the row being added.</span></span> <span data-ttu-id="64ac7-148">Örneğin, `Values[0]` satırın ilk sütunu olarak eklenen değerdir.</span><span class="sxs-lookup"><span data-stu-id="64ac7-148">For example, `Values[0]` is the value that was being added as the first column of the row.</span></span>|  
|`Continue`|<span data-ttu-id="64ac7-149">Bir özel durum atıp atmayacağını seçmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="64ac7-149">Allows you to choose whether or not to throw an exception.</span></span> <span data-ttu-id="64ac7-150">`Continue` Özelliğin geçerli `false` `Fill` işlemi durduracak şekilde ayarlanması ve bir özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="64ac7-150">Setting the `Continue` property to `false` will halt the current `Fill` operation, and an exception will be thrown.</span></span> <span data-ttu-id="64ac7-151">Ayarı, `Continue` `Fill` hataya `true` rağmen işlemi devam ettir.</span><span class="sxs-lookup"><span data-stu-id="64ac7-151">Setting `Continue` to `true` continues the `Fill` operation despite the error.</span></span>|  
  
 <span data-ttu-id="64ac7-152">Aşağıdaki kod örneği olay için `FillError` bir olay `DataAdapter`işleyicisi ekler .</span><span class="sxs-lookup"><span data-stu-id="64ac7-152">The following code example adds an event handler for the `FillError` event of the `DataAdapter`.</span></span> <span data-ttu-id="64ac7-153">`FillError` Olay kodunda, örnek, özel durum yanıtlama olanağı sağlayarak hassas kayıp potansiyeli olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="64ac7-153">In the `FillError` event code, the example determines if there is the potential for precision loss, providing the opportunity to respond to the exception.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="64ac7-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64ac7-154">See also</span></span>

- [<span data-ttu-id="64ac7-155">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="64ac7-155">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="64ac7-156">DataSet Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="64ac7-156">Handling DataSet Events</span></span>](./dataset-datatable-dataview/handling-dataset-events.md)
- [<span data-ttu-id="64ac7-157">DataTable Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="64ac7-157">Handling DataTable Events</span></span>](./dataset-datatable-dataview/handling-datatable-events.md)
- [<span data-ttu-id="64ac7-158">Olaylar</span><span class="sxs-lookup"><span data-stu-id="64ac7-158">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="64ac7-159">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="64ac7-159">ADO.NET Overview</span></span>](ado-net-overview.md)
