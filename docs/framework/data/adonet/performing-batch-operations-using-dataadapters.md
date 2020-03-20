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
# <a name="performing-batch-operations-using-dataadapters"></a>DataAdapters Kullanarak Toplu İşlemleri Gerçekleştirme
ADO.NET toplu iş <xref:System.Data.Common.DataAdapter> desteği, bir seferde bir işlem göndermek <xref:System.Data.DataSet> <xref:System.Data.DataTable> yerine insert, UPDATE ve DELETE işlemlerini sunucudan veya sunucudan gruplandırmasına olanak tanır. Sunucuya gidiş dönüş seyahatlerinin sayısındaki azalma genellikle önemli performans kazançlarına neden olabilir. Toplu güncellemeler SQL Server ( ) ve<xref:System.Data.SqlClient>Oracle (<xref:System.Data.OracleClient>için .NET veri sağlayıcıları için desteklenir).  
  
 ADO.NET önceki sürümlerinde yapılan <xref:System.Data.DataSet> değişikliklerle veritabanını güncelleştirirken, gerçekleştirilen veritabanının `Update` `DataAdapter` güncelleştirme yöntemi her seferinde bir satırdır. Belirtilen <xref:System.Data.DataTable>satırlar arasında yinelenirken, değiştirilip değiştirilmediğini görmek için her biri <xref:System.Data.DataRow> incelendi. Satır değiştirilmişse, bu satır `UpdateCommand`için `InsertCommand` `DeleteCommand` <xref:System.Data.DataRow.RowState%2A> özelliğin değerine bağlı olarak uygun , veya , olarak adlandırılır. Her satır güncelleştirmesi veritabanına bir ağ gidiş-dönüş içeriyordu.  
  
 2.0ADO.NET ile başlayarak, <xref:System.Data.Common.DbDataAdapter> <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> bir özelliği ortaya çıkarır. Pozitif `UpdateBatchSize` bir tamsayı değerine ayarlanması, veritabanındaki güncelleştirmelerin belirtilen boyutta toplu olarak gönderilmesine neden olur. Örneğin, `UpdateBatchSize` 10'a ayar 10 ayrı deyimleri gruplatır ve bunları tek bir toplu iş olarak gönderir. `UpdateBatchSize` 0'a ayar, <xref:System.Data.Common.DataAdapter> sunucunun işleyebilir en büyük toplu iş boyutunu kullanmasına neden olur. Satırlar teker teker gönderildiğinden, toplu iş güncelleştirmelerini 1 olarak ayarlar.  
  
 Son derece büyük bir toplu iş yürütme performansı azaltabilir. Bu nedenle, uygulamanızı uygulamadan önce en uygun toplu iş boyutu ayarı için test etmeniz gerekir.  
  
## <a name="using-the-updatebatchsize-property"></a>UpdateBatchSize Özelliğini Kullanma  
 Toplu iş güncelleştirmeleri <xref:System.Data.IDbCommand.UpdatedRowSource%2A> etkinleştirildiğinde, DataAdapter'ın `UpdateCommand` `InsertCommand`özellik `DeleteCommand` değeri , <xref:System.Data.UpdateRowSource.None> ve <xref:System.Data.UpdateRowSource.OutputParameters>ayarlanmalıdır veya . Toplu iş güncelleştirmesi gerçekleştirirken, <xref:System.Data.IDbCommand.UpdatedRowSource%2A> komutun <xref:System.Data.UpdateRowSource.Both> <xref:System.Data.UpdateRowSource.FirstReturnedRecord> özellik değeri veya geçersizdir.  
  
 Aşağıdaki yordam `UpdateBatchSize` özelliğin kullanımını gösterir. <xref:System.Data.DataSet> Yordam, **Production.ProductCategory** tablosunda **ProductCategoryID** ve **Name** alanlarını temsil eden sütunları olan bir nesne ve toplu iş boyutunu (toplu işteki satır sayısı) temsil eden bir tamsayı olan iki bağımsız değişken alır. <xref:System.Data.SqlClient.SqlDataAdapter> Kod, yeni bir nesne oluşturur <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>ve <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> onun , ve özelliklerini ayarlar. Kod, nesnenin <xref:System.Data.DataSet> satırları değiştirdiğini varsayar. `UpdateBatchSize` Özelliği ayarlar ve güncelleştirmeyi yürütür.  
  
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
  
## <a name="handling-batch-update-related-events-and-errors"></a>Toplu Güncellemeyle İlgili Olaylar ve Hatalar  
 **DataAdapter'ın** güncelleştirmeyle ilgili iki olayı vardır: **RowUpdating** ve **RowUpdate**. ADO.NET önceki sürümlerinde, toplu işleme devre dışı bırakıldığında, bu olayların her biri işlenen her satır için bir kez oluşturulur. **Güncelleştirme** gerçekleşmeden önce Satır Güncelleştirmesi oluşturulur ve veritabanı güncelleştirmesi tamamlandıktan sonra **RowUpdate** oluşturulur.  
  
### <a name="event-behavior-changes-with-batch-updates"></a>Toplu İşlemlerle Olay Davranışı Değişiklikleri  
 Toplu işişleme etkinleştirildiğinde, tek bir veritabanı işleminde birden çok satır güncelleştirilir. Bu nedenle, `RowUpdated` her toplu iş için yalnızca `RowUpdating` bir olay oluşurken, olay işlenen her satır için oluşur. Toplu işlem devre dışı bırakıldığında, iki olay bire bir ayrılmayla ateşlenir, burada `RowUpdating` bir olay ve bir `RowUpdated` olay bir satır için ateş lenir ve sonra bir `RowUpdating` ve bir `RowUpdated` olay tüm satırlar işlenene kadar bir sonraki satır için ateşlenir.  
  
### <a name="accessing-updated-rows"></a>Güncelleştirilmiş Satırlara Erişim  
 Toplu işişleme devre dışı bırakıldığında, güncelleştirilen <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> satıra <xref:System.Data.Common.RowUpdatedEventArgs> sınıfın özelliği kullanılarak erişilebilir.  
  
 Toplu işişleme etkinleştirildiğinde, `RowUpdated` birden çok satır için tek bir olay oluşturulur. Bu nedenle, her `Row` satır için özelliğin değeri null. `RowUpdating`olaylar hala her satır için oluşturulur. <xref:System.Data.Common.RowUpdatedEventArgs> Sınıfın yöntemi, <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> satırların başvurularını bir diziye kopyalayarak işlenen satırlara erişmenizi sağlar. Satır işlenmezse, `CopyToRows` bir <xref:System.ArgumentNullException>. Yöntemi <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> aramadan önce işlenen satır sayısını döndürmek için özelliği kullanın. <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A>  
  
### <a name="handling-data-errors"></a>Veri Hatalarını Işleme  
 Toplu yürütme, her bir deyimin yürütülmesiyle aynı etkiye sahiptir. İfadeler toplu iş eklenme sırasına göre yürütülür. Hatalar, toplu iş modu devre dışı bırakıldığında olduğu gibi toplu iş modunda da işlenir. Her satır ayrı ayrı işlenir. Yalnızca veritabanında başarıyla işlenmiş satırlar ilgili <xref:System.Data.DataRow> içinde <xref:System.Data.DataTable>güncelleştirilir.  
  
 Veri sağlayıcısı ve arka uç veritabanı sunucusu, toplu yürütme için hangi SQL yapılarının destekleniyi belirler. Yürütme için desteklenmeyen bir bildirim gönderilirse bir özel durum atılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [Veri Kaynaklarını DataAdapters ile Güncelleştirme](updating-data-sources-with-dataadapters.md)
- [DataAdapter Olaylarını İşleme](handling-dataadapter-events.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
