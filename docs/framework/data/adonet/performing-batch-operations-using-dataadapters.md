---
title: DataAdapters kullanarak toplu işlemleri gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.openlocfilehash: cfc77ff3b030ffebf52feab0190f81fc4e581cf9
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847886"
---
# <a name="performing-batch-operations-using-dataadapters"></a><span data-ttu-id="4d2f3-102">DataAdapters kullanarak toplu işlemleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="4d2f3-102">Performing Batch Operations Using DataAdapters</span></span>
<span data-ttu-id="4d2f3-103">ADO.NET'te batch desteği sağlayan bir <xref:System.Data.Common.DataAdapter> INSERT, UPDATE ve DELETE işlemlerini gruplamak için bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable> yerine, aynı anda tek bir işlem sunucusuna.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-103">Batch support in ADO.NET allows a <xref:System.Data.Common.DataAdapter> to group INSERT, UPDATE, and DELETE operations from a <xref:System.Data.DataSet> or <xref:System.Data.DataTable> to the server, instead of sending one operation at a time.</span></span> <span data-ttu-id="4d2f3-104">Sunucuya gidiş dönüş sayısı azalma, genellikle önemli performans artışları sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-104">The reduction in the number of round trips to the server typically results in significant performance gains.</span></span> <span data-ttu-id="4d2f3-105">Toplu güncelleştirmeler, SQL Server için .NET veri sağlayıcıları desteklenir (<xref:System.Data.SqlClient>) ve Oracle (<xref:System.Data.OracleClient>).</span><span class="sxs-lookup"><span data-stu-id="4d2f3-105">Batch updates are supported for the .NET data providers for SQL Server (<xref:System.Data.SqlClient>) and Oracle (<xref:System.Data.OracleClient>).</span></span>  
  
 <span data-ttu-id="4d2f3-106">Bir veritabanı ile güncelleştirme ne zaman değişir bir <xref:System.Data.DataSet> ADO.NET, önceki sürümlerinde `Update` yöntemi bir `DataAdapter` veritabanı bir satır için güncelleştirmeleri aynı anda gerçekleştirilen.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-106">When updating a database with changes from a <xref:System.Data.DataSet> in previous versions of ADO.NET, the `Update` method of a `DataAdapter` performed updates to the database one row at a time.</span></span> <span data-ttu-id="4d2f3-107">Belirtilen satırları aracılığıyla yinelenir gibi <xref:System.Data.DataTable>, her incelenirken <xref:System.Data.DataRow> değişiklik yapıldığını olmadığını görmek için.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-107">As it iterated through the rows in the specified <xref:System.Data.DataTable>, it examined each <xref:System.Data.DataRow> to see if it had been modified.</span></span> <span data-ttu-id="4d2f3-108">Satır değiştiren, uygun adlı `UpdateCommand`, `InsertCommand`, veya `DeleteCommand`değerine bağlı olarak <xref:System.Data.DataRow.RowState%2A> ilgili satır için özellik.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-108">If the row had been modified, it called the appropriate `UpdateCommand`, `InsertCommand`, or `DeleteCommand`, depending on the value of the <xref:System.Data.DataRow.RowState%2A> property for that row.</span></span> <span data-ttu-id="4d2f3-109">Her satır güncelleştirme veritabanını bir ağ gidiş dönüş dahil.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-109">Every row update involved a network round-trip to the database.</span></span>  
  
 <span data-ttu-id="4d2f3-110">ADO.NET 2.0 ile başlayarak <xref:System.Data.Common.DbDataAdapter> sunan bir <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-110">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbDataAdapter> exposes an <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> property.</span></span> <span data-ttu-id="4d2f3-111">Ayar `UpdateBatchSize` pozitif bir tamsayı değeri, güncelleştirmeleri belirtilen boyutta toplu gönderilmesi için veritabanına neden olur.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-111">Setting the `UpdateBatchSize` to a positive integer value causes updates to the database to be sent as batches of the specified size.</span></span> <span data-ttu-id="4d2f3-112">Örneğin, ayarlamak `UpdateBatchSize` 10 10 ayrı deyim grup ve bunları tek bir toplu gönderin.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-112">For example, setting the `UpdateBatchSize` to 10 will group 10 separate statements and submit them as single batch.</span></span> <span data-ttu-id="4d2f3-113">Ayarlama `UpdateBatchSize` 0 olarak açacak <xref:System.Data.Common.DataAdapter> sunucu işleyebileceği en büyük toplu iş boyutu kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-113">Setting the `UpdateBatchSize` to 0 will cause the <xref:System.Data.Common.DataAdapter> to use the largest batch size that the server can handle.</span></span> <span data-ttu-id="4d2f3-114">Satırları teker teker gönderilir gibi 1 devre dışı bırakır toplu güncelleştirmeler için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-114">Setting it to 1 disables batch updates, as rows are sent one at a time.</span></span>  
  
 <span data-ttu-id="4d2f3-115">Son derece büyük bir toplu iş yürütme performansı düşürür.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-115">Executing an extremely large batch could decrease performance.</span></span> <span data-ttu-id="4d2f3-116">Bu nedenle, uygulamanızı uygulamadan önce en yüksek toplu iş boyutu ayarı için test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-116">Therefore, you should test for the optimum batch size setting before implementing your application.</span></span>  
  
## <a name="using-the-updatebatchsize-property"></a><span data-ttu-id="4d2f3-117">UpdateBatchSize özelliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="4d2f3-117">Using the UpdateBatchSize Property</span></span>  
 <span data-ttu-id="4d2f3-118">Toplu güncelleştirmeler etkinleştirildiğinde <xref:System.Data.IDbCommand.UpdatedRowSource%2A> DataAdapter özelliği değerinin `UpdateCommand`, `InsertCommand`, ve `DeleteCommand` ayarlanmalıdır <xref:System.Data.UpdateRowSource.None> veya <xref:System.Data.UpdateRowSource.OutputParameters>.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-118">When batch updates are enabled, the <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of the DataAdapter's `UpdateCommand`, `InsertCommand`, and `DeleteCommand` should be set to <xref:System.Data.UpdateRowSource.None> or <xref:System.Data.UpdateRowSource.OutputParameters>.</span></span> <span data-ttu-id="4d2f3-119">Ne zaman bir toplu güncelleştirme gerçekleştirme, komutun <xref:System.Data.IDbCommand.UpdatedRowSource%2A> özelliği değerinin <xref:System.Data.UpdateRowSource.FirstReturnedRecord> veya <xref:System.Data.UpdateRowSource.Both> geçersiz.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-119">When performing a batch update, the command's <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of <xref:System.Data.UpdateRowSource.FirstReturnedRecord> or <xref:System.Data.UpdateRowSource.Both> is invalid.</span></span>  
  
 <span data-ttu-id="4d2f3-120">Aşağıdaki yordam kullanımını göstermektedir `UpdateBatchSize` özelliği.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-120">The following procedure demonstrates the use of the `UpdateBatchSize` property.</span></span> <span data-ttu-id="4d2f3-121">Yordamın kullandığı iki bağımsız değişkeni bir <xref:System.Data.DataSet> temsil eden bir sütuna sahip nesne **ProductCategoryID** ve **adı** alanlarını **Production.ProductCategory**tablo ve toplu iş boyutu (toplu satır sayısı) temsil eden bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-121">The procedure takes two arguments, a <xref:System.Data.DataSet> object that has columns representing the **ProductCategoryID** and **Name** fields in the **Production.ProductCategory** table, and an integer representing the batch size (the number of rows in the batch).</span></span> <span data-ttu-id="4d2f3-122">Yeni bir kod oluşturur <xref:System.Data.SqlClient.SqlDataAdapter> ayarlama nesne, kendi <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, ve <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-122">The code creates a new <xref:System.Data.SqlClient.SqlDataAdapter> object, setting its <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties.</span></span> <span data-ttu-id="4d2f3-123">Kod olduğunu varsayar <xref:System.Data.DataSet> nesne satır değiştirdi.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-123">The code assumes that the <xref:System.Data.DataSet> object has modified rows.</span></span> <span data-ttu-id="4d2f3-124">Bu ayarlar `UpdateBatchSize` özellik ve güncelleştirme yürütür.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-124">It sets the `UpdateBatchSize` property and executes the update.</span></span>  
  
```vb  
Public Sub BatchUpdate( _  
  ByVal dataTable As DataTable, ByVal batchSize As Int32)  
    ' Assumes GetConnectionString() returns a valid connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    ' Connect to the AdventureWorks database.  
    Using connection As New SqlConnection(connectionString)  
        ' Create a SqlDataAdapter.  
        Dim adapter As New SqlDataAdapter()  
  
        'Set the UPDATE command and parameters.  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Production.ProductCategory SET " _  
          & "Name=@Name WHERE ProductCategoryID=@ProdCatID;", _  
          connection)  
        adapter.UpdateCommand.Parameters.Add("@Name", _  
          SqlDbType.NVarChar, 50, "Name")  
        adapter.UpdateCommand.Parameters.Add("@ProdCatID",  _  
          SqlDbType.Int, 4, " ProductCategoryID ")  
        adapter.UpdateCommand.UpdatedRowSource = _  
          UpdateRowSource.None  
  
        'Set the INSERT command and parameter.  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Production.ProductCategory (Name) VALUES (@Name);", _  
  connection)  
        adapter.InsertCommand.Parameters.Add("@Name", _  
          SqlDbType.NVarChar, 50, "Name")  
        adapter.InsertCommand.UpdatedRowSource = _  
          UpdateRowSource.None  
  
        'Set the DELETE command and parameter.  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Production.ProductCategory " _  
          & "WHERE ProductCategoryID=@ProdCatID;", connection)  
        adapter.DeleteCommand.Parameters.Add("@ProdCatID", _  
           SqlDbType.Int, 4, " ProductCategoryID ")  
        adapter.DeleteCommand.UpdatedRowSource = UpdateRowSource.None  
  
        ' Set the batch size.  
        adapter.UpdateBatchSize = batchSize  
  
        ' Execute the update.  
        adapter.Update(dataTable)  
    End Using  
End Sub  
```  
  
```csharp  
public static void BatchUpdate(DataTable dataTable,Int32 batchSize)  
{  
    // Assumes GetConnectionString() returns a valid connection string.  
    string connectionString = GetConnectionString();  
  
    // Connect to the AdventureWorks database.  
    using (SqlConnection connection = new   
      SqlConnection(connectionString))  
    {  
  
        // Create a SqlDataAdapter.  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        // Set the UPDATE command and parameters.  
        adapter.UpdateCommand = new SqlCommand(  
            "UPDATE Production.ProductCategory SET "  
            + "Name=@Name WHERE ProductCategoryID=@ProdCatID;",   
            connection);  
        adapter.UpdateCommand.Parameters.Add("@Name",   
           SqlDbType.NVarChar, 50, "Name");  
        adapter.UpdateCommand.Parameters.Add("@ProdCatID",   
           SqlDbType.Int, 4, "ProductCategoryID");  
         adapter.UpdateCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the INSERT command and parameter.  
        adapter.InsertCommand = new SqlCommand(  
            "INSERT INTO Production.ProductCategory (Name) VALUES (@Name);",   
            connection);  
        adapter.InsertCommand.Parameters.Add("@Name",   
          SqlDbType.NVarChar, 50, "Name");  
        adapter.InsertCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the DELETE command and parameter.  
        adapter.DeleteCommand = new SqlCommand(  
            "DELETE FROM Production.ProductCategory "  
            + "WHERE ProductCategoryID=@ProdCatID;", connection);  
        adapter.DeleteCommand.Parameters.Add("@ProdCatID",   
          SqlDbType.Int, 4, "ProductCategoryID");  
        adapter.DeleteCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the batch size.  
        adapter.UpdateBatchSize = batchSize;  
  
        // Execute the update.  
        adapter.Update(dataTable);  
    }  
}  
```  
  
## <a name="handling-batch-update-related-events-and-errors"></a><span data-ttu-id="4d2f3-125">Toplu güncelleştirme ile ilgili olayları ve hataları işleme</span><span class="sxs-lookup"><span data-stu-id="4d2f3-125">Handling Batch Update-Related Events and Errors</span></span>  
 <span data-ttu-id="4d2f3-126">**DataAdapter** iki güncelleştirme ile ilgili olayları vardır: **RowUpdating** ve **RowUpdated**.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-126">The **DataAdapter** has two update-related events: **RowUpdating** and **RowUpdated**.</span></span> <span data-ttu-id="4d2f3-127">Toplu işlem devre dışı bırakıldığında, ADO.NET önceki sürümlerinde, bu olayların her biri çok kez işlenen her satır için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-127">In previous versions of ADO.NET, when batch processing is disabled, each of these events is generated once for each row processed.</span></span> <span data-ttu-id="4d2f3-128">**RowUpdating** güncelleştirme gerçekleşmeden önce oluşturulan ve **RowUpdated** veritabanı güncelleştirmesi tamamlandıktan sonra oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-128">**RowUpdating** is generated before the update occurs, and **RowUpdated** is generated after the database update has been completed.</span></span>  
  
### <a name="event-behavior-changes-with-batch-updates"></a><span data-ttu-id="4d2f3-129">Toplu Güncelleştirmeler ile olay davranış değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="4d2f3-129">Event Behavior Changes with Batch Updates</span></span>  
 <span data-ttu-id="4d2f3-130">Toplu işleme etkin olduğunda, bir tek veritabanı işlemi birden çok satır güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-130">When batch processing is enabled, multiple rows are updated in a single database operation.</span></span> <span data-ttu-id="4d2f3-131">Bu nedenle, yalnızca bir `RowUpdated` ise her toplu iş için bir olay oluşursa `RowUpdating` olay işlenen her satır için gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-131">Therefore, only one `RowUpdated` event occurs for each batch, whereas the `RowUpdating` event occurs for each row processed.</span></span> <span data-ttu-id="4d2f3-132">Toplu işlem devre dışı bırakıldığında, iki bire Interleaving bir yerlerde olaylar `RowUpdating` olay ve tek `RowUpdated` ve ardından tek bir satır için olay yangın `RowUpdating` ve bir `RowUpdated` sonraki satıra kadar tüm satırlar için olay tetikleme işlenir.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-132">When batch processing is disabled, the two events are fired with one-to-one interleaving, where one `RowUpdating` event and one `RowUpdated` event fire for a row, and then one `RowUpdating` and one `RowUpdated` event fire for the next row, until all of the rows are processed.</span></span>  
  
### <a name="accessing-updated-rows"></a><span data-ttu-id="4d2f3-133">Güncelleştirilen satırların erişme</span><span class="sxs-lookup"><span data-stu-id="4d2f3-133">Accessing Updated Rows</span></span>  
 <span data-ttu-id="4d2f3-134">Toplu işlem devre dışı bırakıldığında, güncelleştirilen satır kullanılarak erişilebilir <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> özelliği <xref:System.Data.Common.RowUpdatedEventArgs> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-134">When batch processing is disabled, the row being updated can be accessed using the <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> property of the <xref:System.Data.Common.RowUpdatedEventArgs> class.</span></span>  
  
 <span data-ttu-id="4d2f3-135">Toplu işleme etkin olduğunda, tek bir `RowUpdated` olay birden çok satır için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-135">When batch processing is enabled, a single `RowUpdated` event is generated for multiple rows.</span></span> <span data-ttu-id="4d2f3-136">Bu nedenle, değerini `Row` her satır için özellik NULL'dur.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-136">Therefore, the value of the `Row` property for each row is null.</span></span> <span data-ttu-id="4d2f3-137">`RowUpdating` olayları yine de her satır için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-137">`RowUpdating` events are still generated for each row.</span></span> <span data-ttu-id="4d2f3-138"><xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> Yöntemi <xref:System.Data.Common.RowUpdatedEventArgs> sınıfı satırları için başvurular bir dizi içine kopyalayarak işlenen satırları erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-138">The <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method of the <xref:System.Data.Common.RowUpdatedEventArgs> class allows you to access the processed rows by copying references to the rows into an array.</span></span> <span data-ttu-id="4d2f3-139">Hiçbir satır işlenmekte olan, `CopyToRows` oluşturur bir <xref:System.ArgumentNullException>.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-139">If no rows are being processed, `CopyToRows` throws an <xref:System.ArgumentNullException>.</span></span> <span data-ttu-id="4d2f3-140">Kullanım <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> çağırmadan önce işlenen satır sayısını döndürmek için özellik <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-140">Use the <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> property to return the number of rows processed before calling the <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method.</span></span>  
  
### <a name="handling-data-errors"></a><span data-ttu-id="4d2f3-141">Veri hataları işleme</span><span class="sxs-lookup"><span data-stu-id="4d2f3-141">Handling Data Errors</span></span>  
 <span data-ttu-id="4d2f3-142">Toplu işlem yürütmesi tek tek her deyimin yürütme ile aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-142">Batch execution has the same effect as the execution of each individual statement.</span></span> <span data-ttu-id="4d2f3-143">Deyimleri deyimleri toplu eklenen sırayla yürütülür.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-143">Statements are executed in the order that the statements were added to the batch.</span></span> <span data-ttu-id="4d2f3-144">Hataları, toplu iş modu devre dışı bırakıldığında, oldukları gibi aynı şekilde toplu iş modunda işlenir.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-144">Errors are handled the same way in batch mode as they are when batch mode is disabled.</span></span> <span data-ttu-id="4d2f3-145">Her satır ayrı ayrı işlenir.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-145">Each row is processed separately.</span></span> <span data-ttu-id="4d2f3-146">İlgili veritabanında başarıyla işlenen satır güncelleştirilir <xref:System.Data.DataRow> içinde <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-146">Only rows that have been successfully processed in the database will be updated in the corresponding <xref:System.Data.DataRow> within the <xref:System.Data.DataTable>.</span></span>  
  
 <span data-ttu-id="4d2f3-147">Veri sağlayıcısı ve arka uç veritabanı sunucusunun hangi SQL yapıları toplu iş yürütme için desteklenen belirleyin.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-147">The data provider and the back-end database server determine which SQL constructs are supported for batch execution.</span></span> <span data-ttu-id="4d2f3-148">Desteklenmeyen bir deyimi yürütme için gönderdiyseniz, bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-148">An exception may be thrown if a non-supported statement is submitted for execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d2f3-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d2f3-149">See Also</span></span>  
 [<span data-ttu-id="4d2f3-150">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="4d2f3-150">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="4d2f3-151">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="4d2f3-151">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="4d2f3-152">DataAdapter Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="4d2f3-152">Handling DataAdapter Events</span></span>](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 [<span data-ttu-id="4d2f3-153">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="4d2f3-153">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
