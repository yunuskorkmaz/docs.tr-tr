---
title: DataAdapters kullanarak toplu işlemleri gerçekleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
ms.openlocfilehash: e585d8a3c21f4a256a2e706389fc9f8adc7900da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361991"
---
# <a name="performing-batch-operations-using-dataadapters"></a>DataAdapters kullanarak toplu işlemleri gerçekleştirme
ADO.NET toplu desteği sağlayan bir <xref:System.Data.Common.DataAdapter> INSERT, UPDATE ve DELETE işlemlerinden gruplandırmak için bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable> bir defada bir işlem göndermek yerine bu sunucuya. Sunucuya gidiş dönüş sayısı azalma genellikle önemli performans artışları sonuçlanır. Toplu güncelleştirmeler, SQL Server için .NET veri sağlayıcıları için desteklenir (<xref:System.Data.SqlClient>) ve Oracle (<xref:System.Data.OracleClient>).  
  
 Bir veritabanı ile güncelleştirilirken değiştiğinde alanından bir <xref:System.Data.DataSet> ADO.NET, önceki sürümlerinde `Update` yöntemi bir `DataAdapter` veritabanı bir satır için güncelleştirmeleri aynı anda gerçekleştirilen. Belirtilen satırları aracılığıyla yinelendiğinde gibi <xref:System.Data.DataTable>, her incelenmesi <xref:System.Data.DataRow> değişiklik yapıldığını olmadığını görmek için. Satır modifiye, uygun adlı `UpdateCommand`, `InsertCommand`, veya `DeleteCommand`değerine bağlı olarak <xref:System.Data.DataRow.RowState%2A> ilgili satır özelliği. Her bir satır güncelleştirme ağ gidiş veritabanına dahil.  
  
 ADO.NET 2.0 ile başlayan <xref:System.Data.Common.DbDataAdapter> kullanıma sunan bir <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> özelliği. Ayarı `UpdateBatchSize` pozitif bir tamsayı değeri belirtilen boyut toplu gönderilmesi gereken veritabanı güncelleştirmelerini neden olur. Örneğin, ayarlama `UpdateBatchSize` 10 10 ayrı deyim grup ve tek bir toplu gönderin. Ayarı `UpdateBatchSize` 0 olarak neden olacak <xref:System.Data.Common.DataAdapter> sunucunun işleyebileceği en büyük toplu iş boyutunu kullanması için. Satırları birer birer gönderildiğinde 1 devre dışı bırakır toplu güncelleştirmeler için ayarlama.  
  
 Son derece büyük bir toplu iş yürütülürken performansı düşürür. Bu nedenle, uygulamanızın uygulamadan önce optimum toplu iş boyutu ayarı için test etmeniz gerekir.  
  
## <a name="using-the-updatebatchsize-property"></a>UpdateBatchSize özelliğini kullanma  
 Toplu güncelleştirmeler etkinleştirildiğinde, <xref:System.Data.IDbCommand.UpdatedRowSource%2A> DataAdapter özellik değerinin `UpdateCommand`, `InsertCommand`, ve `DeleteCommand` ayarlanmalı <xref:System.Data.UpdateRowSource.None> veya <xref:System.Data.UpdateRowSource.OutputParameters>. Ne zaman bir toplu işlem gerçekleştirme güncelleştirme komutunun <xref:System.Data.IDbCommand.UpdatedRowSource%2A> özellik değerinin <xref:System.Data.UpdateRowSource.FirstReturnedRecord> veya <xref:System.Data.UpdateRowSource.Both> geçersiz.  
  
 Aşağıdaki yordam kullanımını gösteren `UpdateBatchSize` özelliği. İki bağımsız değişken, yordamın kullandığı bir <xref:System.Data.DataSet> temsil eden sütun olan nesneyi **ProductCategoryID** ve **adı** alanlarını **Production.ProductCategory**tablo ve toplu iş boyutu (toplu satır sayısı) temsil eden bir tamsayı. Yeni bir kod oluşturur <xref:System.Data.SqlClient.SqlDataAdapter> ayarı nesne, kendi <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, ve <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> özellikleri. Kod varsayar <xref:System.Data.DataSet> nesne satır değiştirdi. Bu ayarlar `UpdateBatchSize` özelliği ve güncelleştirme yürütür.  
  
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
 **DataAdapter** iki güncelleştirme ile ilgili olayları vardır: **RowUpdating** ve **RowUpdated**. Toplu işleme devre dışı bırakıldığında, ADO.NET önceki sürümlerinde, bu olayların her biri bir kez işlenen her satır için oluşturulur. **RowUpdating** güncelleştirme oluşmadan önce oluşturulan ve **RowUpdated** Veritabanı Güncelleştirme tamamlandıktan sonra oluşturulur.  
  
### <a name="event-behavior-changes-with-batch-updates"></a>Toplu Güncelleştirmeler ile olay davranışı değişiklikleri  
 Toplu işleme etkinleştirildiğinde, birden çok satır bir tek veritabanı işleminde güncelleştirilir. Bu nedenle, yalnızca bir `RowUpdated` olayı, ancak her toplu işlem için oluşur `RowUpdating` olayı işlenen her satır için oluşur. Toplu işleme devre dışı bırakıldığında, iki birebir Interleaving bir yerlerde olaylar `RowUpdating` olay ve tek `RowUpdated` bir satır ve sonra bir olay yangın `RowUpdating` ve bir `RowUpdated` olay yangın sonraki satıra kadar tüm satırlar için işlenir.  
  
### <a name="accessing-updated-rows"></a>Güncelleştirilmiş satırları erişme  
 Toplu işleme devre dışı bırakıldığında, güncelleştirilen satır kullanılarak erişilebilir <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> özelliği <xref:System.Data.Common.RowUpdatedEventArgs> sınıfı.  
  
 Toplu işleme etkin olduğunda, tek bir `RowUpdated` olay birden çok satır için oluşturulur. Bu nedenle, değeri `Row` her satır için özellik NULL'dur. `RowUpdating` olayları yine her satır için oluşturulur. <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> Yöntemi <xref:System.Data.Common.RowUpdatedEventArgs> sınıfı bir diziye satırlara yapılan başvurular kopyalayarak işlenen satır erişmenize olanak verir. Hiçbir satır işlenmekte olan, `CopyToRows` oluşturur bir <xref:System.ArgumentNullException>. Kullanım <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> çağırmadan önce işlenen satır sayısını döndürmek için özellik <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> yöntemi.  
  
### <a name="handling-data-errors"></a>Veri hataları işleme  
 Toplu iş yürütme her tek tek bir deyimi yürütme aynı etkiye sahiptir. Deyimleri deyimleri toplu eklenen sırada yürütülür. Toplu iş modunda devre dışı bırakıldığında oldukları gibi hatalar toplu iş modunda aynı şekilde ele alınır. Her satır ayrı ayrı işlenir. Veritabanında başarıyla işlenen satır ilgili güncelleştirilmeyecek <xref:System.Data.DataRow> içinde <xref:System.Data.DataTable>.  
  
 Veri sağlayıcı ve arka uç veritabanı sunucusunun hangi SQL yapıları toplu iş yürütme için desteklenen belirler. Desteklenmeyen bir deyimi yürütme için gönderdiyseniz bir özel durum oluşturulabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Veri Kaynaklarını DataAdapters ile Güncelleştirme](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [DataAdapter Olaylarını İşleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
