---
title: DataAdapters Kullanarak Toplu İşlemleri Gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.openlocfilehash: 9dd6abb91b3549e3bc8b4ae84cbb227171512ecb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177429"
---
# <a name="performing-batch-operations-using-dataadapters"></a><span data-ttu-id="7347e-102">DataAdapters Kullanarak Toplu İşlemleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="7347e-102">Performing Batch Operations Using DataAdapters</span></span>

<span data-ttu-id="7347e-103">ADO.NET ' de Batch desteği <xref:System.Data.Common.DataAdapter> <xref:System.Data.DataSet> , bir kerede bir işlem göndermek yerine bir veya sunucuya ekleme, GÜNCELLEŞTIRME ve silme işlemlerini gruplandıra sağlar <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="7347e-103">Batch support in ADO.NET allows a <xref:System.Data.Common.DataAdapter> to group INSERT, UPDATE, and DELETE operations from a <xref:System.Data.DataSet> or <xref:System.Data.DataTable> to the server, instead of sending one operation at a time.</span></span> <span data-ttu-id="7347e-104">Sunucuya gidiş dönüş sayısı azalmasıyla genellikle önemli performans kazançları elde olur.</span><span class="sxs-lookup"><span data-stu-id="7347e-104">The reduction in the number of round trips to the server typically results in significant performance gains.</span></span> <span data-ttu-id="7347e-105">Toplu güncelleştirmeler, SQL Server ( <xref:System.Data.SqlClient> ) ve Oracle () için .NET veri sağlayıcıları için desteklenir <xref:System.Data.OracleClient> .</span><span class="sxs-lookup"><span data-stu-id="7347e-105">Batch updates are supported for the .NET data providers for SQL Server (<xref:System.Data.SqlClient>) and Oracle (<xref:System.Data.OracleClient>).</span></span>  
  
 <span data-ttu-id="7347e-106">Önceki ADO.NET sürümlerindeki değişikliklerle bir veritabanını güncelleştirirken <xref:System.Data.DataSet> , `Update` gerçekleştirilen bir `DataAdapter` güncelleştirme yöntemi tek seferde veritabanında bir satır olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7347e-106">When updating a database with changes from a <xref:System.Data.DataSet> in previous versions of ADO.NET, the `Update` method of a `DataAdapter` performed updates to the database one row at a time.</span></span> <span data-ttu-id="7347e-107">Belirtilen satırlarda yinelendiğinde <xref:System.Data.DataTable> , <xref:System.Data.DataRow> değiştirilip değiştirilmediğini görmek için her biri incelenir.</span><span class="sxs-lookup"><span data-stu-id="7347e-107">As it iterated through the rows in the specified <xref:System.Data.DataTable>, it examined each <xref:System.Data.DataRow> to see if it had been modified.</span></span> <span data-ttu-id="7347e-108">Satır değiştirilmişse, `UpdateCommand` `InsertCommand` `DeleteCommand` Bu satırın özelliğinin değerine bağlı olarak, veya, uygun, veya olarak adlandırılır <xref:System.Data.DataRow.RowState%2A> .</span><span class="sxs-lookup"><span data-stu-id="7347e-108">If the row had been modified, it called the appropriate `UpdateCommand`, `InsertCommand`, or `DeleteCommand`, depending on the value of the <xref:System.Data.DataRow.RowState%2A> property for that row.</span></span> <span data-ttu-id="7347e-109">Her satır güncelleştirmesi, veritabanına gidiş dönüş ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="7347e-109">Every row update involved a network round-trip to the database.</span></span>  
  
 <span data-ttu-id="7347e-110">ADO.NET 2,0 ile başlayarak, <xref:System.Data.Common.DbDataAdapter> bir özelliği kullanıma sunar <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> .</span><span class="sxs-lookup"><span data-stu-id="7347e-110">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbDataAdapter> exposes an <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> property.</span></span> <span data-ttu-id="7347e-111">' In `UpdateBatchSize` pozitif bir tamsayı değerine ayarlanması, veritabanında yapılan güncelleştirmelerin belirtilen boyuttaki toplu işler olarak gönderilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="7347e-111">Setting the `UpdateBatchSize` to a positive integer value causes updates to the database to be sent as batches of the specified size.</span></span> <span data-ttu-id="7347e-112">Örneğin, `UpdateBatchSize` 10 olarak ayarlandığında 10 ayrı deyim gruplandıralınacaktır ve bunları tek toplu iş olarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="7347e-112">For example, setting the `UpdateBatchSize` to 10 will group 10 separate statements and submit them as single batch.</span></span> <span data-ttu-id="7347e-113">`UpdateBatchSize`0 olarak ayarlamak, <xref:System.Data.Common.DataAdapter> sunucusunun işleyebileceği en büyük toplu iş boyutunu kullanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="7347e-113">Setting the `UpdateBatchSize` to 0 will cause the <xref:System.Data.Common.DataAdapter> to use the largest batch size that the server can handle.</span></span> <span data-ttu-id="7347e-114">1 olarak ayarlandığında toplu güncelleştirmeler devre dışı bırakılır ve satırlar birer birer gönderilir.</span><span class="sxs-lookup"><span data-stu-id="7347e-114">Setting it to 1 disables batch updates, as rows are sent one at a time.</span></span>  
  
 <span data-ttu-id="7347e-115">Son derece büyük bir toplu iş yürütülmesi performansı düşürebilir.</span><span class="sxs-lookup"><span data-stu-id="7347e-115">Executing an extremely large batch could decrease performance.</span></span> <span data-ttu-id="7347e-116">Bu nedenle, uygulamanızı uygulamadan önce en iyi toplu iş boyutu ayarını test etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="7347e-116">Therefore, you should test for the optimum batch size setting before implementing your application.</span></span>  
  
## <a name="using-the-updatebatchsize-property"></a><span data-ttu-id="7347e-117">UpdateBatchSize özelliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="7347e-117">Using the UpdateBatchSize Property</span></span>  

 <span data-ttu-id="7347e-118">Batch güncelleştirmeleri etkinleştirildiğinde, <xref:System.Data.IDbCommand.UpdatedRowSource%2A> DataAdapter 'ın, ve özelliğinin özellik değeri `UpdateCommand` `InsertCommand` `DeleteCommand` veya olarak ayarlanmalıdır <xref:System.Data.UpdateRowSource.None> <xref:System.Data.UpdateRowSource.OutputParameters> .</span><span class="sxs-lookup"><span data-stu-id="7347e-118">When batch updates are enabled, the <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of the DataAdapter's `UpdateCommand`, `InsertCommand`, and `DeleteCommand` should be set to <xref:System.Data.UpdateRowSource.None> or <xref:System.Data.UpdateRowSource.OutputParameters>.</span></span> <span data-ttu-id="7347e-119">Toplu güncelleştirme gerçekleştirirken komutun <xref:System.Data.IDbCommand.UpdatedRowSource%2A> özellik değeri <xref:System.Data.UpdateRowSource.FirstReturnedRecord> <xref:System.Data.UpdateRowSource.Both> geçersiz.</span><span class="sxs-lookup"><span data-stu-id="7347e-119">When performing a batch update, the command's <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of <xref:System.Data.UpdateRowSource.FirstReturnedRecord> or <xref:System.Data.UpdateRowSource.Both> is invalid.</span></span>  
  
 <span data-ttu-id="7347e-120">Aşağıdaki yordam özelliğinin kullanımını gösterir `UpdateBatchSize` .</span><span class="sxs-lookup"><span data-stu-id="7347e-120">The following procedure demonstrates the use of the `UpdateBatchSize` property.</span></span> <span data-ttu-id="7347e-121">Yordam iki bağımsız değişken alır, <xref:System.Data.DataSet> **üretim. ProductCategory** tablosundaki **ProductCategoryID** ve **Name** alanlarını temsil eden sütunları ve toplu iş boyutunu temsil eden bir tamsayı (toplu işteki satır sayısı).</span><span class="sxs-lookup"><span data-stu-id="7347e-121">The procedure takes two arguments, a <xref:System.Data.DataSet> object that has columns representing the **ProductCategoryID** and **Name** fields in the **Production.ProductCategory** table, and an integer representing the batch size (the number of rows in the batch).</span></span> <span data-ttu-id="7347e-122">Kod yeni bir nesne oluşturur <xref:System.Data.SqlClient.SqlDataAdapter> ,, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> ve <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7347e-122">The code creates a new <xref:System.Data.SqlClient.SqlDataAdapter> object, setting its <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties.</span></span> <span data-ttu-id="7347e-123">Kod, <xref:System.Data.DataSet> nesnenin satırları değiştirdiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="7347e-123">The code assumes that the <xref:System.Data.DataSet> object has modified rows.</span></span> <span data-ttu-id="7347e-124">`UpdateBatchSize`Özelliği ayarlar ve güncelleştirmeyi yürütür.</span><span class="sxs-lookup"><span data-stu-id="7347e-124">It sets the `UpdateBatchSize` property and executes the update.</span></span>  
  
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
  
## <a name="handling-batch-update-related-events-and-errors"></a><span data-ttu-id="7347e-125">Batch güncelleştirmesiyle Ilgili olayları ve hataları işleme</span><span class="sxs-lookup"><span data-stu-id="7347e-125">Handling Batch Update-Related Events and Errors</span></span>  

 <span data-ttu-id="7347e-126">**DataAdapter** 'ta güncelleştirmeyle ilgili iki olay vardır: **RowUpdating** ve **RowUpdated**.</span><span class="sxs-lookup"><span data-stu-id="7347e-126">The **DataAdapter** has two update-related events: **RowUpdating** and **RowUpdated**.</span></span> <span data-ttu-id="7347e-127">Önceki ADO.NET sürümlerinde, toplu işlem devre dışı bırakıldığında, işlenen her satır için bu olayların her biri bir kez oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7347e-127">In previous versions of ADO.NET, when batch processing is disabled, each of these events is generated once for each row processed.</span></span> <span data-ttu-id="7347e-128">**RowUpdating** güncelleştirme gerçekleşmeden önce oluşturulur ve veritabanı güncelleştirmesi tamamlandıktan sonra **RowUpdated** oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7347e-128">**RowUpdating** is generated before the update occurs, and **RowUpdated** is generated after the database update has been completed.</span></span>  
  
### <a name="event-behavior-changes-with-batch-updates"></a><span data-ttu-id="7347e-129">Toplu güncelleştirmeler ile olay davranışı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="7347e-129">Event Behavior Changes with Batch Updates</span></span>  

 <span data-ttu-id="7347e-130">Toplu işlem etkinleştirildiğinde, tek bir veritabanı işleminde birden çok satır güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7347e-130">When batch processing is enabled, multiple rows are updated in a single database operation.</span></span> <span data-ttu-id="7347e-131">Bu nedenle, `RowUpdated` her bir yığın için yalnızca bir olay oluşur, ancak `RowUpdating` olay işlenen her satır için gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="7347e-131">Therefore, only one `RowUpdated` event occurs for each batch, whereas the `RowUpdating` event occurs for each row processed.</span></span> <span data-ttu-id="7347e-132">Toplu işlem devre dışı bırakıldığında, iki olay bir `RowUpdating` olay için bir olay ve bir `RowUpdated` olay tetiklendiğinde bir ve daha sonra bir `RowUpdating` `RowUpdated` sonraki satır için bir ve bir olay tetiklendiğinde, tüm satırlar işlenene kadar bir-tek araya ekleme ile tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="7347e-132">When batch processing is disabled, the two events are fired with one-to-one interleaving, where one `RowUpdating` event and one `RowUpdated` event fire for a row, and then one `RowUpdating` and one `RowUpdated` event fire for the next row, until all of the rows are processed.</span></span>  
  
### <a name="accessing-updated-rows"></a><span data-ttu-id="7347e-133">Güncelleştirilmiş satırlara erişme</span><span class="sxs-lookup"><span data-stu-id="7347e-133">Accessing Updated Rows</span></span>  

 <span data-ttu-id="7347e-134">Toplu işlem devre dışı bırakıldığında, güncellenen satıra <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> sınıfının özelliği kullanılarak erişilebilir <xref:System.Data.Common.RowUpdatedEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="7347e-134">When batch processing is disabled, the row being updated can be accessed using the <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> property of the <xref:System.Data.Common.RowUpdatedEventArgs> class.</span></span>  
  
 <span data-ttu-id="7347e-135">Batch işleme etkinleştirildiğinde, `RowUpdated` birden çok satır için tek bir olay oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7347e-135">When batch processing is enabled, a single `RowUpdated` event is generated for multiple rows.</span></span> <span data-ttu-id="7347e-136">Bu nedenle, `Row` her satır için özelliğin değeri null olur.</span><span class="sxs-lookup"><span data-stu-id="7347e-136">Therefore, the value of the `Row` property for each row is null.</span></span> <span data-ttu-id="7347e-137">`RowUpdating` her satır için olaylar yine de oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7347e-137">`RowUpdating` events are still generated for each row.</span></span> <span data-ttu-id="7347e-138"><xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A>Sınıfının yöntemi, <xref:System.Data.Common.RowUpdatedEventArgs> satırları satırlara başvuruları bir diziye kopyalayarak, işlenen satırlara erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7347e-138">The <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method of the <xref:System.Data.Common.RowUpdatedEventArgs> class allows you to access the processed rows by copying references to the rows into an array.</span></span> <span data-ttu-id="7347e-139">Hiçbir satır işlenmiyorsa, `CopyToRows` bir oluşturur <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="7347e-139">If no rows are being processed, `CopyToRows` throws an <xref:System.ArgumentNullException>.</span></span> <span data-ttu-id="7347e-140"><xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A>Yöntemi çağrılmadan önce işlenen satır sayısını döndürmek için özelliğini kullanın <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> .</span><span class="sxs-lookup"><span data-stu-id="7347e-140">Use the <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> property to return the number of rows processed before calling the <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method.</span></span>  
  
### <a name="handling-data-errors"></a><span data-ttu-id="7347e-141">Veri hatalarını işleme</span><span class="sxs-lookup"><span data-stu-id="7347e-141">Handling Data Errors</span></span>  

 <span data-ttu-id="7347e-142">Toplu yürütme, her ayrı deyimin yürütülmesiyle aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7347e-142">Batch execution has the same effect as the execution of each individual statement.</span></span> <span data-ttu-id="7347e-143">Deyimler, deyimlerin toplu işe eklendiği sırada yürütülür.</span><span class="sxs-lookup"><span data-stu-id="7347e-143">Statements are executed in the order that the statements were added to the batch.</span></span> <span data-ttu-id="7347e-144">Hatalar, Batch modu devre dışı bırakıldığında olduğu gibi Batch modunda aynı şekilde işlenir.</span><span class="sxs-lookup"><span data-stu-id="7347e-144">Errors are handled the same way in batch mode as they are when batch mode is disabled.</span></span> <span data-ttu-id="7347e-145">Her satır ayrı işlenir.</span><span class="sxs-lookup"><span data-stu-id="7347e-145">Each row is processed separately.</span></span> <span data-ttu-id="7347e-146">Yalnızca veritabanında başarıyla işlenen satırlar, içinde karşılık gelen ' de güncelleştirilir <xref:System.Data.DataRow> <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="7347e-146">Only rows that have been successfully processed in the database will be updated in the corresponding <xref:System.Data.DataRow> within the <xref:System.Data.DataTable>.</span></span>  
  
 <span data-ttu-id="7347e-147">Veri sağlayıcısı ve arka uç veritabanı sunucusu, toplu yürütme için desteklenen SQL yapılarını tespit edilir.</span><span class="sxs-lookup"><span data-stu-id="7347e-147">The data provider and the back-end database server determine which SQL constructs are supported for batch execution.</span></span> <span data-ttu-id="7347e-148">Yürütülmek üzere desteklenmeyen bir ifade gönderildiğinde bir özel durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="7347e-148">An exception may be thrown if a non-supported statement is submitted for execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7347e-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7347e-149">See also</span></span>

- [<span data-ttu-id="7347e-150">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="7347e-150">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="7347e-151">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="7347e-151">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="7347e-152">DataAdapter Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="7347e-152">Handling DataAdapter Events</span></span>](handling-dataadapter-events.md)
- [<span data-ttu-id="7347e-153">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7347e-153">ADO.NET Overview</span></span>](ado-net-overview.md)
