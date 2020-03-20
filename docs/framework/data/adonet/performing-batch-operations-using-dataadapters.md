---
title: DataAdapters Kullanarak Toplu İşlemleri Gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.openlocfilehash: 62a61051e5b9d896f8a89ed3d2745859fc07a7ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149264"
---
# <a name="performing-batch-operations-using-dataadapters"></a><span data-ttu-id="6b53d-102">DataAdapters Kullanarak Toplu İşlemleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="6b53d-102">Performing Batch Operations Using DataAdapters</span></span>
<span data-ttu-id="6b53d-103">ADO.NET toplu iş <xref:System.Data.Common.DataAdapter> desteği, bir seferde bir işlem göndermek <xref:System.Data.DataSet> <xref:System.Data.DataTable> yerine insert, UPDATE ve DELETE işlemlerini sunucudan veya sunucudan gruplandırmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6b53d-103">Batch support in ADO.NET allows a <xref:System.Data.Common.DataAdapter> to group INSERT, UPDATE, and DELETE operations from a <xref:System.Data.DataSet> or <xref:System.Data.DataTable> to the server, instead of sending one operation at a time.</span></span> <span data-ttu-id="6b53d-104">Sunucuya gidiş dönüş seyahatlerinin sayısındaki azalma genellikle önemli performans kazançlarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="6b53d-104">The reduction in the number of round trips to the server typically results in significant performance gains.</span></span> <span data-ttu-id="6b53d-105">Toplu güncellemeler SQL Server ( ) ve<xref:System.Data.SqlClient>Oracle (<xref:System.Data.OracleClient>için .NET veri sağlayıcıları için desteklenir).</span><span class="sxs-lookup"><span data-stu-id="6b53d-105">Batch updates are supported for the .NET data providers for SQL Server (<xref:System.Data.SqlClient>) and Oracle (<xref:System.Data.OracleClient>).</span></span>  
  
 <span data-ttu-id="6b53d-106">ADO.NET önceki sürümlerinde yapılan <xref:System.Data.DataSet> değişikliklerle veritabanını güncelleştirirken, gerçekleştirilen veritabanının `Update` `DataAdapter` güncelleştirme yöntemi her seferinde bir satırdır.</span><span class="sxs-lookup"><span data-stu-id="6b53d-106">When updating a database with changes from a <xref:System.Data.DataSet> in previous versions of ADO.NET, the `Update` method of a `DataAdapter` performed updates to the database one row at a time.</span></span> <span data-ttu-id="6b53d-107">Belirtilen <xref:System.Data.DataTable>satırlar arasında yinelenirken, değiştirilip değiştirilmediğini görmek için her biri <xref:System.Data.DataRow> incelendi.</span><span class="sxs-lookup"><span data-stu-id="6b53d-107">As it iterated through the rows in the specified <xref:System.Data.DataTable>, it examined each <xref:System.Data.DataRow> to see if it had been modified.</span></span> <span data-ttu-id="6b53d-108">Satır değiştirilmişse, bu satır `UpdateCommand`için `InsertCommand` `DeleteCommand` <xref:System.Data.DataRow.RowState%2A> özelliğin değerine bağlı olarak uygun , veya , olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="6b53d-108">If the row had been modified, it called the appropriate `UpdateCommand`, `InsertCommand`, or `DeleteCommand`, depending on the value of the <xref:System.Data.DataRow.RowState%2A> property for that row.</span></span> <span data-ttu-id="6b53d-109">Her satır güncelleştirmesi veritabanına bir ağ gidiş-dönüş içeriyordu.</span><span class="sxs-lookup"><span data-stu-id="6b53d-109">Every row update involved a network round-trip to the database.</span></span>  
  
 <span data-ttu-id="6b53d-110">2.0ADO.NET ile başlayarak, <xref:System.Data.Common.DbDataAdapter> <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> bir özelliği ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="6b53d-110">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbDataAdapter> exposes an <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> property.</span></span> <span data-ttu-id="6b53d-111">Pozitif `UpdateBatchSize` bir tamsayı değerine ayarlanması, veritabanındaki güncelleştirmelerin belirtilen boyutta toplu olarak gönderilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="6b53d-111">Setting the `UpdateBatchSize` to a positive integer value causes updates to the database to be sent as batches of the specified size.</span></span> <span data-ttu-id="6b53d-112">Örneğin, `UpdateBatchSize` 10'a ayar 10 ayrı deyimleri gruplatır ve bunları tek bir toplu iş olarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="6b53d-112">For example, setting the `UpdateBatchSize` to 10 will group 10 separate statements and submit them as single batch.</span></span> <span data-ttu-id="6b53d-113">`UpdateBatchSize` 0'a ayar, <xref:System.Data.Common.DataAdapter> sunucunun işleyebilir en büyük toplu iş boyutunu kullanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="6b53d-113">Setting the `UpdateBatchSize` to 0 will cause the <xref:System.Data.Common.DataAdapter> to use the largest batch size that the server can handle.</span></span> <span data-ttu-id="6b53d-114">Satırlar teker teker gönderildiğinden, toplu iş güncelleştirmelerini 1 olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6b53d-114">Setting it to 1 disables batch updates, as rows are sent one at a time.</span></span>  
  
 <span data-ttu-id="6b53d-115">Son derece büyük bir toplu iş yürütme performansı azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="6b53d-115">Executing an extremely large batch could decrease performance.</span></span> <span data-ttu-id="6b53d-116">Bu nedenle, uygulamanızı uygulamadan önce en uygun toplu iş boyutu ayarı için test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b53d-116">Therefore, you should test for the optimum batch size setting before implementing your application.</span></span>  
  
## <a name="using-the-updatebatchsize-property"></a><span data-ttu-id="6b53d-117">UpdateBatchSize Özelliğini Kullanma</span><span class="sxs-lookup"><span data-stu-id="6b53d-117">Using the UpdateBatchSize Property</span></span>  
 <span data-ttu-id="6b53d-118">Toplu iş güncelleştirmeleri <xref:System.Data.IDbCommand.UpdatedRowSource%2A> etkinleştirildiğinde, DataAdapter'ın `UpdateCommand` `InsertCommand`özellik `DeleteCommand` değeri , <xref:System.Data.UpdateRowSource.None> ve <xref:System.Data.UpdateRowSource.OutputParameters>ayarlanmalıdır veya .</span><span class="sxs-lookup"><span data-stu-id="6b53d-118">When batch updates are enabled, the <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of the DataAdapter's `UpdateCommand`, `InsertCommand`, and `DeleteCommand` should be set to <xref:System.Data.UpdateRowSource.None> or <xref:System.Data.UpdateRowSource.OutputParameters>.</span></span> <span data-ttu-id="6b53d-119">Toplu iş güncelleştirmesi gerçekleştirirken, <xref:System.Data.IDbCommand.UpdatedRowSource%2A> komutun <xref:System.Data.UpdateRowSource.Both> <xref:System.Data.UpdateRowSource.FirstReturnedRecord> özellik değeri veya geçersizdir.</span><span class="sxs-lookup"><span data-stu-id="6b53d-119">When performing a batch update, the command's <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of <xref:System.Data.UpdateRowSource.FirstReturnedRecord> or <xref:System.Data.UpdateRowSource.Both> is invalid.</span></span>  
  
 <span data-ttu-id="6b53d-120">Aşağıdaki yordam `UpdateBatchSize` özelliğin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b53d-120">The following procedure demonstrates the use of the `UpdateBatchSize` property.</span></span> <span data-ttu-id="6b53d-121"><xref:System.Data.DataSet> Yordam, **Production.ProductCategory** tablosunda **ProductCategoryID** ve **Name** alanlarını temsil eden sütunları olan bir nesne ve toplu iş boyutunu (toplu işteki satır sayısı) temsil eden bir tamsayı olan iki bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="6b53d-121">The procedure takes two arguments, a <xref:System.Data.DataSet> object that has columns representing the **ProductCategoryID** and **Name** fields in the **Production.ProductCategory** table, and an integer representing the batch size (the number of rows in the batch).</span></span> <span data-ttu-id="6b53d-122"><xref:System.Data.SqlClient.SqlDataAdapter> Kod, yeni bir nesne oluşturur <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>ve <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> onun , ve özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6b53d-122">The code creates a new <xref:System.Data.SqlClient.SqlDataAdapter> object, setting its <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties.</span></span> <span data-ttu-id="6b53d-123">Kod, nesnenin <xref:System.Data.DataSet> satırları değiştirdiğini varsayar.</span><span class="sxs-lookup"><span data-stu-id="6b53d-123">The code assumes that the <xref:System.Data.DataSet> object has modified rows.</span></span> <span data-ttu-id="6b53d-124">`UpdateBatchSize` Özelliği ayarlar ve güncelleştirmeyi yürütür.</span><span class="sxs-lookup"><span data-stu-id="6b53d-124">It sets the `UpdateBatchSize` property and executes the update.</span></span>  
  
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
  
## <a name="handling-batch-update-related-events-and-errors"></a><span data-ttu-id="6b53d-125">Toplu Güncellemeyle İlgili Olaylar ve Hatalar</span><span class="sxs-lookup"><span data-stu-id="6b53d-125">Handling Batch Update-Related Events and Errors</span></span>  
 <span data-ttu-id="6b53d-126">**DataAdapter'ın** güncelleştirmeyle ilgili iki olayı vardır: **RowUpdating** ve **RowUpdate**.</span><span class="sxs-lookup"><span data-stu-id="6b53d-126">The **DataAdapter** has two update-related events: **RowUpdating** and **RowUpdated**.</span></span> <span data-ttu-id="6b53d-127">ADO.NET önceki sürümlerinde, toplu işleme devre dışı bırakıldığında, bu olayların her biri işlenen her satır için bir kez oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6b53d-127">In previous versions of ADO.NET, when batch processing is disabled, each of these events is generated once for each row processed.</span></span> <span data-ttu-id="6b53d-128">**Güncelleştirme** gerçekleşmeden önce Satır Güncelleştirmesi oluşturulur ve veritabanı güncelleştirmesi tamamlandıktan sonra **RowUpdate** oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6b53d-128">**RowUpdating** is generated before the update occurs, and **RowUpdated** is generated after the database update has been completed.</span></span>  
  
### <a name="event-behavior-changes-with-batch-updates"></a><span data-ttu-id="6b53d-129">Toplu İşlemlerle Olay Davranışı Değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="6b53d-129">Event Behavior Changes with Batch Updates</span></span>  
 <span data-ttu-id="6b53d-130">Toplu işişleme etkinleştirildiğinde, tek bir veritabanı işleminde birden çok satır güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6b53d-130">When batch processing is enabled, multiple rows are updated in a single database operation.</span></span> <span data-ttu-id="6b53d-131">Bu nedenle, `RowUpdated` her toplu iş için yalnızca `RowUpdating` bir olay oluşurken, olay işlenen her satır için oluşur.</span><span class="sxs-lookup"><span data-stu-id="6b53d-131">Therefore, only one `RowUpdated` event occurs for each batch, whereas the `RowUpdating` event occurs for each row processed.</span></span> <span data-ttu-id="6b53d-132">Toplu işlem devre dışı bırakıldığında, iki olay bire bir ayrılmayla ateşlenir, burada `RowUpdating` bir olay ve bir `RowUpdated` olay bir satır için ateş lenir ve sonra bir `RowUpdating` ve bir `RowUpdated` olay tüm satırlar işlenene kadar bir sonraki satır için ateşlenir.</span><span class="sxs-lookup"><span data-stu-id="6b53d-132">When batch processing is disabled, the two events are fired with one-to-one interleaving, where one `RowUpdating` event and one `RowUpdated` event fire for a row, and then one `RowUpdating` and one `RowUpdated` event fire for the next row, until all of the rows are processed.</span></span>  
  
### <a name="accessing-updated-rows"></a><span data-ttu-id="6b53d-133">Güncelleştirilmiş Satırlara Erişim</span><span class="sxs-lookup"><span data-stu-id="6b53d-133">Accessing Updated Rows</span></span>  
 <span data-ttu-id="6b53d-134">Toplu işişleme devre dışı bırakıldığında, güncelleştirilen <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> satıra <xref:System.Data.Common.RowUpdatedEventArgs> sınıfın özelliği kullanılarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="6b53d-134">When batch processing is disabled, the row being updated can be accessed using the <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> property of the <xref:System.Data.Common.RowUpdatedEventArgs> class.</span></span>  
  
 <span data-ttu-id="6b53d-135">Toplu işişleme etkinleştirildiğinde, `RowUpdated` birden çok satır için tek bir olay oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6b53d-135">When batch processing is enabled, a single `RowUpdated` event is generated for multiple rows.</span></span> <span data-ttu-id="6b53d-136">Bu nedenle, her `Row` satır için özelliğin değeri null.</span><span class="sxs-lookup"><span data-stu-id="6b53d-136">Therefore, the value of the `Row` property for each row is null.</span></span> <span data-ttu-id="6b53d-137">`RowUpdating`olaylar hala her satır için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6b53d-137">`RowUpdating` events are still generated for each row.</span></span> <span data-ttu-id="6b53d-138"><xref:System.Data.Common.RowUpdatedEventArgs> Sınıfın yöntemi, <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> satırların başvurularını bir diziye kopyalayarak işlenen satırlara erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b53d-138">The <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method of the <xref:System.Data.Common.RowUpdatedEventArgs> class allows you to access the processed rows by copying references to the rows into an array.</span></span> <span data-ttu-id="6b53d-139">Satır işlenmezse, `CopyToRows` bir <xref:System.ArgumentNullException>.</span><span class="sxs-lookup"><span data-stu-id="6b53d-139">If no rows are being processed, `CopyToRows` throws an <xref:System.ArgumentNullException>.</span></span> <span data-ttu-id="6b53d-140">Yöntemi <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> aramadan önce işlenen satır sayısını döndürmek için özelliği kullanın. <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A></span><span class="sxs-lookup"><span data-stu-id="6b53d-140">Use the <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> property to return the number of rows processed before calling the <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method.</span></span>  
  
### <a name="handling-data-errors"></a><span data-ttu-id="6b53d-141">Veri Hatalarını Işleme</span><span class="sxs-lookup"><span data-stu-id="6b53d-141">Handling Data Errors</span></span>  
 <span data-ttu-id="6b53d-142">Toplu yürütme, her bir deyimin yürütülmesiyle aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6b53d-142">Batch execution has the same effect as the execution of each individual statement.</span></span> <span data-ttu-id="6b53d-143">İfadeler toplu iş eklenme sırasına göre yürütülür.</span><span class="sxs-lookup"><span data-stu-id="6b53d-143">Statements are executed in the order that the statements were added to the batch.</span></span> <span data-ttu-id="6b53d-144">Hatalar, toplu iş modu devre dışı bırakıldığında olduğu gibi toplu iş modunda da işlenir.</span><span class="sxs-lookup"><span data-stu-id="6b53d-144">Errors are handled the same way in batch mode as they are when batch mode is disabled.</span></span> <span data-ttu-id="6b53d-145">Her satır ayrı ayrı işlenir.</span><span class="sxs-lookup"><span data-stu-id="6b53d-145">Each row is processed separately.</span></span> <span data-ttu-id="6b53d-146">Yalnızca veritabanında başarıyla işlenmiş satırlar ilgili <xref:System.Data.DataRow> içinde <xref:System.Data.DataTable>güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6b53d-146">Only rows that have been successfully processed in the database will be updated in the corresponding <xref:System.Data.DataRow> within the <xref:System.Data.DataTable>.</span></span>  
  
 <span data-ttu-id="6b53d-147">Veri sağlayıcısı ve arka uç veritabanı sunucusu, toplu yürütme için hangi SQL yapılarının destekleniyi belirler.</span><span class="sxs-lookup"><span data-stu-id="6b53d-147">The data provider and the back-end database server determine which SQL constructs are supported for batch execution.</span></span> <span data-ttu-id="6b53d-148">Yürütme için desteklenmeyen bir bildirim gönderilirse bir özel durum atılabilir.</span><span class="sxs-lookup"><span data-stu-id="6b53d-148">An exception may be thrown if a non-supported statement is submitted for execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b53d-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b53d-149">See also</span></span>

- [<span data-ttu-id="6b53d-150">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="6b53d-150">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="6b53d-151">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="6b53d-151">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="6b53d-152">DataAdapter Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="6b53d-152">Handling DataAdapter Events</span></span>](handling-dataadapter-events.md)
- [<span data-ttu-id="6b53d-153">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6b53d-153">ADO.NET Overview</span></span>](ado-net-overview.md)
