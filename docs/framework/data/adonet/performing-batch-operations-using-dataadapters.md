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
# <a name="performing-batch-operations-using-dataadapters"></a>DataAdapters Kullanarak Toplu İşlemleri Gerçekleştirme
ADO.net ' de Batch desteği, <xref:System.Data.Common.DataAdapter> bir kerede bir işlem göndermek yerine bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable> sunucuya ekleme, güncelleştirme ve silme işlemlerini gruplandıra sağlar. Sunucuya gidiş dönüş sayısı azalmasıyla genellikle önemli performans kazançları elde olur. Toplu güncelleştirmeler, SQL Server (<xref:System.Data.SqlClient>) ve Oracle (<xref:System.Data.OracleClient>) için .NET veri sağlayıcıları için desteklenir.  
  
 Önceki ADO.net sürümlerindeki değişikliklerle <xref:System.Data.DataSet> bir veritabanını güncelleştirirken `Update` , `DataAdapter` gerçekleştirilen bir güncelleştirme yöntemi tek seferde veritabanında bir satır olarak gerçekleştirilir. Belirtilen <xref:System.Data.DataTable>satırlarda yinelendiğinde, değiştirilip değiştirilmediğini görmek için her biri <xref:System.Data.DataRow> incelenir. Satır değiştirilmişse, `UpdateCommand`bu satırın <xref:System.Data.DataRow.RowState%2A> özelliğinin değerine bağlı olarak, veya, `InsertCommand`uygun, `DeleteCommand`veya olarak adlandırılır. Her satır güncelleştirmesi, veritabanına gidiş dönüş ile ilgilidir.  
  
 ADO.NET 2,0 ile başlayarak, <xref:System.Data.Common.DbDataAdapter> bir <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> özelliği kullanıma sunar. ' In `UpdateBatchSize` pozitif bir tamsayı değerine ayarlanması, veritabanında yapılan güncelleştirmelerin belirtilen boyuttaki toplu işler olarak gönderilmesine neden olur. Örneğin, 10 `UpdateBatchSize` olarak ayarlandığında 10 ayrı deyim gruplandıralınacaktır ve bunları tek toplu iş olarak gönderilir. 0 olarak ayarlamak, <xref:System.Data.Common.DataAdapter> sunucusunun işleyebileceği en büyük toplu iş boyutunu kullanmasına neden olur. `UpdateBatchSize` 1 olarak ayarlandığında toplu güncelleştirmeler devre dışı bırakılır ve satırlar birer birer gönderilir.  
  
 Son derece büyük bir toplu iş yürütülmesi performansı düşürebilir. Bu nedenle, uygulamanızı uygulamadan önce en iyi toplu iş boyutu ayarını test etmelisiniz.  
  
## <a name="using-the-updatebatchsize-property"></a>UpdateBatchSize özelliğini kullanma  
 <xref:System.Data.IDbCommand.UpdatedRowSource%2A> Batch güncelleştirmeleri etkinleştirildiğinde, `UpdateCommand`DataAdapter `InsertCommand`'ın, ve `DeleteCommand` özelliğinin özellik değeri veya <xref:System.Data.UpdateRowSource.OutputParameters>olarak <xref:System.Data.UpdateRowSource.None> ayarlanmalıdır. Toplu güncelleştirme gerçekleştirirken komutun <xref:System.Data.IDbCommand.UpdatedRowSource%2A> özellik <xref:System.Data.UpdateRowSource.FirstReturnedRecord> değeri <xref:System.Data.UpdateRowSource.Both> geçersiz.  
  
 Aşağıdaki yordam `UpdateBatchSize` özelliğinin kullanımını gösterir. Yordam iki bağımsız değişken <xref:System.Data.DataSet> alır, **üretim. ProductCategory** tablosundaki **ProductCategoryID** ve **Name** alanlarını temsil eden sütunlara sahip bir nesne ve toplu iş boyutunu temsil eden bir tamsayı (sayısı toplu işlemdeki satırlar). Kod yeni <xref:System.Data.SqlClient.SqlDataAdapter> bir nesne oluşturur,, ve <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> özelliklerini <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>ayarlar <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>. Kod, <xref:System.Data.DataSet> nesnenin satırları değiştirdiği varsayılır. `UpdateBatchSize` Özelliği ayarlar ve güncelleştirmeyi yürütür.  
  
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
  
## <a name="handling-batch-update-related-events-and-errors"></a>Batch güncelleştirmesiyle Ilgili olayları ve hataları işleme  
 **DataAdapter** 'ta güncelleştirmeyle ilgili iki olay vardır: **RowUpdating** ve **RowUpdated**. Önceki ADO.NET sürümlerinde, toplu işlem devre dışı bırakıldığında, işlenen her satır için bu olayların her biri bir kez oluşturulur. **RowUpdating** güncelleştirme gerçekleşmeden önce oluşturulur ve veritabanı güncelleştirmesi tamamlandıktan sonra **RowUpdated** oluşturulur.  
  
### <a name="event-behavior-changes-with-batch-updates"></a>Toplu güncelleştirmeler ile olay davranışı değişiklikleri  
 Toplu işlem etkinleştirildiğinde, tek bir veritabanı işleminde birden çok satır güncelleştirilir. Bu nedenle, her `RowUpdated` bir yığın için yalnızca bir olay oluşur, `RowUpdating` ancak olay işlenen her satır için gerçekleşir. Toplu işlem devre dışı bırakıldığında `RowUpdating` , iki olay, bir `RowUpdating` satır için bir olay `RowUpdated` ve bir olay tetiklendiğinde bir ve sonra bir sonraki satır için bir ve `RowUpdated` bir olay tetiklendiğinde, tüm satırlar işlenir.  
  
### <a name="accessing-updated-rows"></a>Güncelleştirilmiş satırlara erişme  
 Toplu işlem devre dışı bırakıldığında, güncellenen satıra <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> <xref:System.Data.Common.RowUpdatedEventArgs> sınıfının özelliği kullanılarak erişilebilir.  
  
 Batch işleme etkinleştirildiğinde, birden çok satır için `RowUpdated` tek bir olay oluşturulur. Bu nedenle, her satır için `Row` özelliğin değeri null olur. `RowUpdating`her satır için olaylar yine de oluşturulur. Sınıfının<xref:System.Data.Common.RowUpdatedEventArgs> yöntemi, <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> satırları satırlara başvuruları bir diziye kopyalayarak, işlenen satırlara erişmenizi sağlar. Hiçbir satır işlenmiyorsa, `CopyToRows` bir <xref:System.ArgumentNullException>oluşturur. Yöntemi çağrılmadan önce işlenen satır sayısını döndürmek için özelliğinikullanın.<xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A>  
  
### <a name="handling-data-errors"></a>Veri hatalarını işleme  
 Toplu yürütme, her ayrı deyimin yürütülmesiyle aynı etkiye sahiptir. Deyimler, deyimlerin toplu işe eklendiği sırada yürütülür. Hatalar, Batch modu devre dışı bırakıldığında olduğu gibi Batch modunda aynı şekilde işlenir. Her satır ayrı işlenir. Yalnızca veritabanında başarıyla işlenen satırlar, <xref:System.Data.DataRow> <xref:System.Data.DataTable>içinde karşılık gelen ' de güncelleştirilir.  
  
 Veri sağlayıcısı ve arka uç veritabanı sunucusu, toplu yürütme için desteklenen SQL yapılarını tespit edilir. Yürütülmek üzere desteklenmeyen bir ifade gönderildiğinde bir özel durum oluşabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [Veri Kaynaklarını DataAdapters ile Güncelleştirme](updating-data-sources-with-dataadapters.md)
- [DataAdapter Olaylarını İşleme](handling-dataadapter-events.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
