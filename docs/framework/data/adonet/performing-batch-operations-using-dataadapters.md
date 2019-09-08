---
title: DataAdapters Kullanarak Toplu İşlemleri Gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.openlocfilehash: 8667cffb032daf0043915d3bee7127ef9b70756b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794513"
---
# <a name="performing-batch-operations-using-dataadapters"></a><span data-ttu-id="3b0d5-102">DataAdapters Kullanarak Toplu İşlemleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="3b0d5-102">Performing Batch Operations Using DataAdapters</span></span>
<span data-ttu-id="3b0d5-103">ADO.net ' de Batch desteği, <xref:System.Data.Common.DataAdapter> bir kerede bir işlem göndermek yerine bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable> sunucuya ekleme, güncelleştirme ve silme işlemlerini gruplandıra sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-103">Batch support in ADO.NET allows a <xref:System.Data.Common.DataAdapter> to group INSERT, UPDATE, and DELETE operations from a <xref:System.Data.DataSet> or <xref:System.Data.DataTable> to the server, instead of sending one operation at a time.</span></span> <span data-ttu-id="3b0d5-104">Sunucuya gidiş dönüş sayısı azalmasıyla genellikle önemli performans kazançları elde olur.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-104">The reduction in the number of round trips to the server typically results in significant performance gains.</span></span> <span data-ttu-id="3b0d5-105">Toplu güncelleştirmeler, SQL Server (<xref:System.Data.SqlClient>) ve Oracle (<xref:System.Data.OracleClient>) için .NET veri sağlayıcıları için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-105">Batch updates are supported for the .NET data providers for SQL Server (<xref:System.Data.SqlClient>) and Oracle (<xref:System.Data.OracleClient>).</span></span>  
  
 <span data-ttu-id="3b0d5-106">Önceki ADO.net sürümlerindeki değişikliklerle <xref:System.Data.DataSet> bir veritabanını güncelleştirirken `Update` , `DataAdapter` gerçekleştirilen bir güncelleştirme yöntemi tek seferde veritabanında bir satır olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-106">When updating a database with changes from a <xref:System.Data.DataSet> in previous versions of ADO.NET, the `Update` method of a `DataAdapter` performed updates to the database one row at a time.</span></span> <span data-ttu-id="3b0d5-107">Belirtilen <xref:System.Data.DataTable>satırlarda yinelendiğinde, değiştirilip değiştirilmediğini görmek için her biri <xref:System.Data.DataRow> incelenir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-107">As it iterated through the rows in the specified <xref:System.Data.DataTable>, it examined each <xref:System.Data.DataRow> to see if it had been modified.</span></span> <span data-ttu-id="3b0d5-108">Satır değiştirilmişse, `UpdateCommand`bu satırın <xref:System.Data.DataRow.RowState%2A> özelliğinin değerine bağlı olarak, veya, `InsertCommand`uygun, `DeleteCommand`veya olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-108">If the row had been modified, it called the appropriate `UpdateCommand`, `InsertCommand`, or `DeleteCommand`, depending on the value of the <xref:System.Data.DataRow.RowState%2A> property for that row.</span></span> <span data-ttu-id="3b0d5-109">Her satır güncelleştirmesi, veritabanına gidiş dönüş ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-109">Every row update involved a network round-trip to the database.</span></span>  
  
 <span data-ttu-id="3b0d5-110">ADO.NET 2,0 ile başlayarak, <xref:System.Data.Common.DbDataAdapter> bir <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> özelliği kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-110">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbDataAdapter> exposes an <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> property.</span></span> <span data-ttu-id="3b0d5-111">' In `UpdateBatchSize` pozitif bir tamsayı değerine ayarlanması, veritabanında yapılan güncelleştirmelerin belirtilen boyuttaki toplu işler olarak gönderilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-111">Setting the `UpdateBatchSize` to a positive integer value causes updates to the database to be sent as batches of the specified size.</span></span> <span data-ttu-id="3b0d5-112">Örneğin, 10 `UpdateBatchSize` olarak ayarlandığında 10 ayrı deyim gruplandıralınacaktır ve bunları tek toplu iş olarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-112">For example, setting the `UpdateBatchSize` to 10 will group 10 separate statements and submit them as single batch.</span></span> <span data-ttu-id="3b0d5-113">0 olarak ayarlamak, <xref:System.Data.Common.DataAdapter> sunucusunun işleyebileceği en büyük toplu iş boyutunu kullanmasına neden olur. `UpdateBatchSize`</span><span class="sxs-lookup"><span data-stu-id="3b0d5-113">Setting the `UpdateBatchSize` to 0 will cause the <xref:System.Data.Common.DataAdapter> to use the largest batch size that the server can handle.</span></span> <span data-ttu-id="3b0d5-114">1 olarak ayarlandığında toplu güncelleştirmeler devre dışı bırakılır ve satırlar birer birer gönderilir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-114">Setting it to 1 disables batch updates, as rows are sent one at a time.</span></span>  
  
 <span data-ttu-id="3b0d5-115">Son derece büyük bir toplu iş yürütülmesi performansı düşürebilir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-115">Executing an extremely large batch could decrease performance.</span></span> <span data-ttu-id="3b0d5-116">Bu nedenle, uygulamanızı uygulamadan önce en iyi toplu iş boyutu ayarını test etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-116">Therefore, you should test for the optimum batch size setting before implementing your application.</span></span>  
  
## <a name="using-the-updatebatchsize-property"></a><span data-ttu-id="3b0d5-117">UpdateBatchSize özelliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="3b0d5-117">Using the UpdateBatchSize Property</span></span>  
 <span data-ttu-id="3b0d5-118"><xref:System.Data.IDbCommand.UpdatedRowSource%2A> Batch güncelleştirmeleri etkinleştirildiğinde, `UpdateCommand`DataAdapter `InsertCommand`'ın, ve `DeleteCommand` özelliğinin özellik değeri veya <xref:System.Data.UpdateRowSource.OutputParameters>olarak <xref:System.Data.UpdateRowSource.None> ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-118">When batch updates are enabled, the <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of the DataAdapter's `UpdateCommand`, `InsertCommand`, and `DeleteCommand` should be set to <xref:System.Data.UpdateRowSource.None> or <xref:System.Data.UpdateRowSource.OutputParameters>.</span></span> <span data-ttu-id="3b0d5-119">Toplu güncelleştirme gerçekleştirirken komutun <xref:System.Data.IDbCommand.UpdatedRowSource%2A> özellik <xref:System.Data.UpdateRowSource.FirstReturnedRecord> değeri <xref:System.Data.UpdateRowSource.Both> geçersiz.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-119">When performing a batch update, the command's <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of <xref:System.Data.UpdateRowSource.FirstReturnedRecord> or <xref:System.Data.UpdateRowSource.Both> is invalid.</span></span>  
  
 <span data-ttu-id="3b0d5-120">Aşağıdaki yordam `UpdateBatchSize` özelliğinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-120">The following procedure demonstrates the use of the `UpdateBatchSize` property.</span></span> <span data-ttu-id="3b0d5-121">Yordam iki bağımsız değişken <xref:System.Data.DataSet> alır, **üretim. ProductCategory** tablosundaki **ProductCategoryID** ve **Name** alanlarını temsil eden sütunlara sahip bir nesne ve toplu iş boyutunu temsil eden bir tamsayı (sayısı toplu işlemdeki satırlar).</span><span class="sxs-lookup"><span data-stu-id="3b0d5-121">The procedure takes two arguments, a <xref:System.Data.DataSet> object that has columns representing the **ProductCategoryID** and **Name** fields in the **Production.ProductCategory** table, and an integer representing the batch size (the number of rows in the batch).</span></span> <span data-ttu-id="3b0d5-122">Kod yeni <xref:System.Data.SqlClient.SqlDataAdapter> bir nesne oluşturur,, ve <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> özelliklerini <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>ayarlar <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-122">The code creates a new <xref:System.Data.SqlClient.SqlDataAdapter> object, setting its <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties.</span></span> <span data-ttu-id="3b0d5-123">Kod, <xref:System.Data.DataSet> nesnenin satırları değiştirdiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-123">The code assumes that the <xref:System.Data.DataSet> object has modified rows.</span></span> <span data-ttu-id="3b0d5-124">`UpdateBatchSize` Özelliği ayarlar ve güncelleştirmeyi yürütür.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-124">It sets the `UpdateBatchSize` property and executes the update.</span></span>  
  
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
  
## <a name="handling-batch-update-related-events-and-errors"></a><span data-ttu-id="3b0d5-125">Batch güncelleştirmesiyle Ilgili olayları ve hataları işleme</span><span class="sxs-lookup"><span data-stu-id="3b0d5-125">Handling Batch Update-Related Events and Errors</span></span>  
 <span data-ttu-id="3b0d5-126">**DataAdapter** 'ta güncelleştirmeyle ilgili iki olay vardır: **RowUpdating** ve **RowUpdated**.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-126">The **DataAdapter** has two update-related events: **RowUpdating** and **RowUpdated**.</span></span> <span data-ttu-id="3b0d5-127">Önceki ADO.NET sürümlerinde, toplu işlem devre dışı bırakıldığında, işlenen her satır için bu olayların her biri bir kez oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-127">In previous versions of ADO.NET, when batch processing is disabled, each of these events is generated once for each row processed.</span></span> <span data-ttu-id="3b0d5-128">**RowUpdating** güncelleştirme gerçekleşmeden önce oluşturulur ve veritabanı güncelleştirmesi tamamlandıktan sonra **RowUpdated** oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-128">**RowUpdating** is generated before the update occurs, and **RowUpdated** is generated after the database update has been completed.</span></span>  
  
### <a name="event-behavior-changes-with-batch-updates"></a><span data-ttu-id="3b0d5-129">Toplu güncelleştirmeler ile olay davranışı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="3b0d5-129">Event Behavior Changes with Batch Updates</span></span>  
 <span data-ttu-id="3b0d5-130">Toplu işlem etkinleştirildiğinde, tek bir veritabanı işleminde birden çok satır güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-130">When batch processing is enabled, multiple rows are updated in a single database operation.</span></span> <span data-ttu-id="3b0d5-131">Bu nedenle, her `RowUpdated` bir yığın için yalnızca bir olay oluşur, `RowUpdating` ancak olay işlenen her satır için gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-131">Therefore, only one `RowUpdated` event occurs for each batch, whereas the `RowUpdating` event occurs for each row processed.</span></span> <span data-ttu-id="3b0d5-132">Toplu işlem devre dışı bırakıldığında `RowUpdating` , iki olay, bir `RowUpdating` satır için bir olay `RowUpdated` ve bir olay tetiklendiğinde bir ve sonra bir sonraki satır için bir ve `RowUpdated` bir olay tetiklendiğinde, tüm satırlar işlenir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-132">When batch processing is disabled, the two events are fired with one-to-one interleaving, where one `RowUpdating` event and one `RowUpdated` event fire for a row, and then one `RowUpdating` and one `RowUpdated` event fire for the next row, until all of the rows are processed.</span></span>  
  
### <a name="accessing-updated-rows"></a><span data-ttu-id="3b0d5-133">Güncelleştirilmiş satırlara erişme</span><span class="sxs-lookup"><span data-stu-id="3b0d5-133">Accessing Updated Rows</span></span>  
 <span data-ttu-id="3b0d5-134">Toplu işlem devre dışı bırakıldığında, güncellenen satıra <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> <xref:System.Data.Common.RowUpdatedEventArgs> sınıfının özelliği kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-134">When batch processing is disabled, the row being updated can be accessed using the <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> property of the <xref:System.Data.Common.RowUpdatedEventArgs> class.</span></span>  
  
 <span data-ttu-id="3b0d5-135">Batch işleme etkinleştirildiğinde, birden çok satır için `RowUpdated` tek bir olay oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-135">When batch processing is enabled, a single `RowUpdated` event is generated for multiple rows.</span></span> <span data-ttu-id="3b0d5-136">Bu nedenle, her satır için `Row` özelliğin değeri null olur.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-136">Therefore, the value of the `Row` property for each row is null.</span></span> <span data-ttu-id="3b0d5-137">`RowUpdating`her satır için olaylar yine de oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-137">`RowUpdating` events are still generated for each row.</span></span> <span data-ttu-id="3b0d5-138">Sınıfının<xref:System.Data.Common.RowUpdatedEventArgs> yöntemi, <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> satırları satırlara başvuruları bir diziye kopyalayarak, işlenen satırlara erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-138">The <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method of the <xref:System.Data.Common.RowUpdatedEventArgs> class allows you to access the processed rows by copying references to the rows into an array.</span></span> <span data-ttu-id="3b0d5-139">Hiçbir satır işlenmiyorsa, `CopyToRows` bir <xref:System.ArgumentNullException>oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-139">If no rows are being processed, `CopyToRows` throws an <xref:System.ArgumentNullException>.</span></span> <span data-ttu-id="3b0d5-140">Yöntemi çağrılmadan önce işlenen satır sayısını döndürmek için özelliğinikullanın.<xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A></span><span class="sxs-lookup"><span data-stu-id="3b0d5-140">Use the <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> property to return the number of rows processed before calling the <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method.</span></span>  
  
### <a name="handling-data-errors"></a><span data-ttu-id="3b0d5-141">Veri hatalarını işleme</span><span class="sxs-lookup"><span data-stu-id="3b0d5-141">Handling Data Errors</span></span>  
 <span data-ttu-id="3b0d5-142">Toplu yürütme, her ayrı deyimin yürütülmesiyle aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-142">Batch execution has the same effect as the execution of each individual statement.</span></span> <span data-ttu-id="3b0d5-143">Deyimler, deyimlerin toplu işe eklendiği sırada yürütülür.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-143">Statements are executed in the order that the statements were added to the batch.</span></span> <span data-ttu-id="3b0d5-144">Hatalar, Batch modu devre dışı bırakıldığında olduğu gibi Batch modunda aynı şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-144">Errors are handled the same way in batch mode as they are when batch mode is disabled.</span></span> <span data-ttu-id="3b0d5-145">Her satır ayrı işlenir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-145">Each row is processed separately.</span></span> <span data-ttu-id="3b0d5-146">Yalnızca veritabanında başarıyla işlenen satırlar, <xref:System.Data.DataRow> <xref:System.Data.DataTable>içinde karşılık gelen ' de güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-146">Only rows that have been successfully processed in the database will be updated in the corresponding <xref:System.Data.DataRow> within the <xref:System.Data.DataTable>.</span></span>  
  
 <span data-ttu-id="3b0d5-147">Veri sağlayıcısı ve arka uç veritabanı sunucusu, toplu yürütme için desteklenen SQL yapılarını tespit edilir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-147">The data provider and the back-end database server determine which SQL constructs are supported for batch execution.</span></span> <span data-ttu-id="3b0d5-148">Yürütülmek üzere desteklenmeyen bir ifade gönderildiğinde bir özel durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-148">An exception may be thrown if a non-supported statement is submitted for execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b0d5-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-149">See also</span></span>

- [<span data-ttu-id="3b0d5-150">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="3b0d5-150">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="3b0d5-151">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="3b0d5-151">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="3b0d5-152">DataAdapter Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="3b0d5-152">Handling DataAdapter Events</span></span>](handling-dataadapter-events.md)
- [<span data-ttu-id="3b0d5-153">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3b0d5-153">ADO.NET Overview</span></span>](ado-net-overview.md)
