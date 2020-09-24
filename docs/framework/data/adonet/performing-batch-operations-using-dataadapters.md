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
# <a name="performing-batch-operations-using-dataadapters"></a>DataAdapters Kullanarak Toplu İşlemleri Gerçekleştirme

ADO.NET ' de Batch desteği <xref:System.Data.Common.DataAdapter> <xref:System.Data.DataSet> , bir kerede bir işlem göndermek yerine bir veya sunucuya ekleme, GÜNCELLEŞTIRME ve silme işlemlerini gruplandıra sağlar <xref:System.Data.DataTable> . Sunucuya gidiş dönüş sayısı azalmasıyla genellikle önemli performans kazançları elde olur. Toplu güncelleştirmeler, SQL Server ( <xref:System.Data.SqlClient> ) ve Oracle () için .NET veri sağlayıcıları için desteklenir <xref:System.Data.OracleClient> .  
  
 Önceki ADO.NET sürümlerindeki değişikliklerle bir veritabanını güncelleştirirken <xref:System.Data.DataSet> , `Update` gerçekleştirilen bir `DataAdapter` güncelleştirme yöntemi tek seferde veritabanında bir satır olarak gerçekleştirilir. Belirtilen satırlarda yinelendiğinde <xref:System.Data.DataTable> , <xref:System.Data.DataRow> değiştirilip değiştirilmediğini görmek için her biri incelenir. Satır değiştirilmişse, `UpdateCommand` `InsertCommand` `DeleteCommand` Bu satırın özelliğinin değerine bağlı olarak, veya, uygun, veya olarak adlandırılır <xref:System.Data.DataRow.RowState%2A> . Her satır güncelleştirmesi, veritabanına gidiş dönüş ile ilgilidir.  
  
 ADO.NET 2,0 ile başlayarak, <xref:System.Data.Common.DbDataAdapter> bir özelliği kullanıma sunar <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> . ' In `UpdateBatchSize` pozitif bir tamsayı değerine ayarlanması, veritabanında yapılan güncelleştirmelerin belirtilen boyuttaki toplu işler olarak gönderilmesine neden olur. Örneğin, `UpdateBatchSize` 10 olarak ayarlandığında 10 ayrı deyim gruplandıralınacaktır ve bunları tek toplu iş olarak gönderilir. `UpdateBatchSize`0 olarak ayarlamak, <xref:System.Data.Common.DataAdapter> sunucusunun işleyebileceği en büyük toplu iş boyutunu kullanmasına neden olur. 1 olarak ayarlandığında toplu güncelleştirmeler devre dışı bırakılır ve satırlar birer birer gönderilir.  
  
 Son derece büyük bir toplu iş yürütülmesi performansı düşürebilir. Bu nedenle, uygulamanızı uygulamadan önce en iyi toplu iş boyutu ayarını test etmelisiniz.  
  
## <a name="using-the-updatebatchsize-property"></a>UpdateBatchSize özelliğini kullanma  

 Batch güncelleştirmeleri etkinleştirildiğinde, <xref:System.Data.IDbCommand.UpdatedRowSource%2A> DataAdapter 'ın, ve özelliğinin özellik değeri `UpdateCommand` `InsertCommand` `DeleteCommand` veya olarak ayarlanmalıdır <xref:System.Data.UpdateRowSource.None> <xref:System.Data.UpdateRowSource.OutputParameters> . Toplu güncelleştirme gerçekleştirirken komutun <xref:System.Data.IDbCommand.UpdatedRowSource%2A> özellik değeri <xref:System.Data.UpdateRowSource.FirstReturnedRecord> <xref:System.Data.UpdateRowSource.Both> geçersiz.  
  
 Aşağıdaki yordam özelliğinin kullanımını gösterir `UpdateBatchSize` . Yordam iki bağımsız değişken alır, <xref:System.Data.DataSet> **üretim. ProductCategory** tablosundaki **ProductCategoryID** ve **Name** alanlarını temsil eden sütunları ve toplu iş boyutunu temsil eden bir tamsayı (toplu işteki satır sayısı). Kod yeni bir nesne oluşturur <xref:System.Data.SqlClient.SqlDataAdapter> ,, <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> ve <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> özelliklerini ayarlar. Kod, <xref:System.Data.DataSet> nesnenin satırları değiştirdiği varsayılır. `UpdateBatchSize`Özelliği ayarlar ve güncelleştirmeyi yürütür.  
  
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

 Toplu işlem etkinleştirildiğinde, tek bir veritabanı işleminde birden çok satır güncelleştirilir. Bu nedenle, `RowUpdated` her bir yığın için yalnızca bir olay oluşur, ancak `RowUpdating` olay işlenen her satır için gerçekleşir. Toplu işlem devre dışı bırakıldığında, iki olay bir `RowUpdating` olay için bir olay ve bir `RowUpdated` olay tetiklendiğinde bir ve daha sonra bir `RowUpdating` `RowUpdated` sonraki satır için bir ve bir olay tetiklendiğinde, tüm satırlar işlenene kadar bir-tek araya ekleme ile tetiklenir.  
  
### <a name="accessing-updated-rows"></a>Güncelleştirilmiş satırlara erişme  

 Toplu işlem devre dışı bırakıldığında, güncellenen satıra <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> sınıfının özelliği kullanılarak erişilebilir <xref:System.Data.Common.RowUpdatedEventArgs> .  
  
 Batch işleme etkinleştirildiğinde, `RowUpdated` birden çok satır için tek bir olay oluşturulur. Bu nedenle, `Row` her satır için özelliğin değeri null olur. `RowUpdating` her satır için olaylar yine de oluşturulur. <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A>Sınıfının yöntemi, <xref:System.Data.Common.RowUpdatedEventArgs> satırları satırlara başvuruları bir diziye kopyalayarak, işlenen satırlara erişmenizi sağlar. Hiçbir satır işlenmiyorsa, `CopyToRows` bir oluşturur <xref:System.ArgumentNullException> . <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A>Yöntemi çağrılmadan önce işlenen satır sayısını döndürmek için özelliğini kullanın <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> .  
  
### <a name="handling-data-errors"></a>Veri hatalarını işleme  

 Toplu yürütme, her ayrı deyimin yürütülmesiyle aynı etkiye sahiptir. Deyimler, deyimlerin toplu işe eklendiği sırada yürütülür. Hatalar, Batch modu devre dışı bırakıldığında olduğu gibi Batch modunda aynı şekilde işlenir. Her satır ayrı işlenir. Yalnızca veritabanında başarıyla işlenen satırlar, içinde karşılık gelen ' de güncelleştirilir <xref:System.Data.DataRow> <xref:System.Data.DataTable> .  
  
 Veri sağlayıcısı ve arka uç veritabanı sunucusu, toplu yürütme için desteklenen SQL yapılarını tespit edilir. Yürütülmek üzere desteklenmeyen bir ifade gönderildiğinde bir özel durum oluşabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [Veri Kaynaklarını DataAdapters ile Güncelleştirme](updating-data-sources-with-dataadapters.md)
- [DataAdapter Olaylarını İşleme](handling-dataadapter-events.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
