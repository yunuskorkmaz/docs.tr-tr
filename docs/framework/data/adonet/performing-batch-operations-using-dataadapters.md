---
title: DataAdapters kullanarak toplu işlemleri gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.openlocfilehash: cfc77ff3b030ffebf52feab0190f81fc4e581cf9
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47231144"
---
# <a name="performing-batch-operations-using-dataadapters"></a>DataAdapters kullanarak toplu işlemleri gerçekleştirme
ADO.NET'te batch desteği sağlayan bir <xref:System.Data.Common.DataAdapter> INSERT, UPDATE ve DELETE işlemlerini gruplamak için bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable> yerine, aynı anda tek bir işlem sunucusuna. Sunucuya gidiş dönüş sayısı azalma, genellikle önemli performans artışları sonuçlanır. Toplu güncelleştirmeler, SQL Server için .NET veri sağlayıcıları desteklenir (<xref:System.Data.SqlClient>) ve Oracle (<xref:System.Data.OracleClient>).  
  
 Bir veritabanı ile güncelleştirme ne zaman değişir bir <xref:System.Data.DataSet> ADO.NET, önceki sürümlerinde `Update` yöntemi bir `DataAdapter` veritabanı bir satır için güncelleştirmeleri aynı anda gerçekleştirilen. Belirtilen satırları aracılığıyla yinelenir gibi <xref:System.Data.DataTable>, her incelenirken <xref:System.Data.DataRow> değişiklik yapıldığını olmadığını görmek için. Satır değiştiren, uygun adlı `UpdateCommand`, `InsertCommand`, veya `DeleteCommand`değerine bağlı olarak <xref:System.Data.DataRow.RowState%2A> ilgili satır için özellik. Her satır güncelleştirme veritabanını bir ağ gidiş dönüş dahil.  
  
 ADO.NET 2.0 ile başlayarak <xref:System.Data.Common.DbDataAdapter> sunan bir <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> özelliği. Ayar `UpdateBatchSize` pozitif bir tamsayı değeri, güncelleştirmeleri belirtilen boyutta toplu gönderilmesi için veritabanına neden olur. Örneğin, ayarlamak `UpdateBatchSize` 10 10 ayrı deyim grup ve bunları tek bir toplu gönderin. Ayarlama `UpdateBatchSize` 0 olarak açacak <xref:System.Data.Common.DataAdapter> sunucu işleyebileceği en büyük toplu iş boyutu kullanılacak. Satırları teker teker gönderilir gibi 1 devre dışı bırakır toplu güncelleştirmeler için ayarlar.  
  
 Son derece büyük bir toplu iş yürütme performansı düşürür. Bu nedenle, uygulamanızı uygulamadan önce en yüksek toplu iş boyutu ayarı için test etmeniz gerekir.  
  
## <a name="using-the-updatebatchsize-property"></a>UpdateBatchSize özelliğini kullanma  
 Toplu güncelleştirmeler etkinleştirildiğinde <xref:System.Data.IDbCommand.UpdatedRowSource%2A> DataAdapter özelliği değerinin `UpdateCommand`, `InsertCommand`, ve `DeleteCommand` ayarlanmalıdır <xref:System.Data.UpdateRowSource.None> veya <xref:System.Data.UpdateRowSource.OutputParameters>. Ne zaman bir toplu güncelleştirme gerçekleştirme, komutun <xref:System.Data.IDbCommand.UpdatedRowSource%2A> özelliği değerinin <xref:System.Data.UpdateRowSource.FirstReturnedRecord> veya <xref:System.Data.UpdateRowSource.Both> geçersiz.  
  
 Aşağıdaki yordam kullanımını göstermektedir `UpdateBatchSize` özelliği. Yordamın kullandığı iki bağımsız değişkeni bir <xref:System.Data.DataSet> temsil eden bir sütuna sahip nesne **ProductCategoryID** ve **adı** alanlarını **Production.ProductCategory**tablo ve toplu iş boyutu (toplu satır sayısı) temsil eden bir tamsayı. Yeni bir kod oluşturur <xref:System.Data.SqlClient.SqlDataAdapter> ayarlama nesne, kendi <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, ve <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> özellikleri. Kod olduğunu varsayar <xref:System.Data.DataSet> nesne satır değiştirdi. Bu ayarlar `UpdateBatchSize` özellik ve güncelleştirme yürütür.  
  
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
  
## <a name="handling-batch-update-related-events-and-errors"></a>Toplu güncelleştirme ile ilgili olayları ve hataları işleme  
 **DataAdapter** iki güncelleştirme ile ilgili olayları vardır: **RowUpdating** ve **RowUpdated**. Toplu işlem devre dışı bırakıldığında, ADO.NET önceki sürümlerinde, bu olayların her biri çok kez işlenen her satır için oluşturulur. **RowUpdating** güncelleştirme gerçekleşmeden önce oluşturulan ve **RowUpdated** veritabanı güncelleştirmesi tamamlandıktan sonra oluşturulur.  
  
### <a name="event-behavior-changes-with-batch-updates"></a>Toplu Güncelleştirmeler ile olay davranış değişiklikleri  
 Toplu işleme etkin olduğunda, bir tek veritabanı işlemi birden çok satır güncelleştirilir. Bu nedenle, yalnızca bir `RowUpdated` ise her toplu iş için bir olay oluşursa `RowUpdating` olay işlenen her satır için gerçekleşir. Toplu işlem devre dışı bırakıldığında, iki bire Interleaving bir yerlerde olaylar `RowUpdating` olay ve tek `RowUpdated` ve ardından tek bir satır için olay yangın `RowUpdating` ve bir `RowUpdated` sonraki satıra kadar tüm satırlar için olay tetikleme işlenir.  
  
### <a name="accessing-updated-rows"></a>Güncelleştirilen satırların erişme  
 Toplu işlem devre dışı bırakıldığında, güncelleştirilen satır kullanılarak erişilebilir <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> özelliği <xref:System.Data.Common.RowUpdatedEventArgs> sınıfı.  
  
 Toplu işleme etkin olduğunda, tek bir `RowUpdated` olay birden çok satır için oluşturulur. Bu nedenle, değerini `Row` her satır için özellik NULL'dur. `RowUpdating` olayları yine de her satır için oluşturulur. <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> Yöntemi <xref:System.Data.Common.RowUpdatedEventArgs> sınıfı satırları için başvurular bir dizi içine kopyalayarak işlenen satırları erişmenizi sağlar. Hiçbir satır işlenmekte olan, `CopyToRows` oluşturur bir <xref:System.ArgumentNullException>. Kullanım <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> çağırmadan önce işlenen satır sayısını döndürmek için özellik <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> yöntemi.  
  
### <a name="handling-data-errors"></a>Veri hataları işleme  
 Toplu işlem yürütmesi tek tek her deyimin yürütme ile aynı etkiye sahiptir. Deyimleri deyimleri toplu eklenen sırayla yürütülür. Hataları, toplu iş modu devre dışı bırakıldığında, oldukları gibi aynı şekilde toplu iş modunda işlenir. Her satır ayrı ayrı işlenir. İlgili veritabanında başarıyla işlenen satır güncelleştirilir <xref:System.Data.DataRow> içinde <xref:System.Data.DataTable>.  
  
 Veri sağlayıcısı ve arka uç veritabanı sunucusunun hangi SQL yapıları toplu iş yürütme için desteklenen belirleyin. Desteklenmeyen bir deyimi yürütme için gönderdiyseniz, bir özel durum.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Veri Kaynaklarını DataAdapters ile Güncelleştirme](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [DataAdapter Olaylarını İşleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
