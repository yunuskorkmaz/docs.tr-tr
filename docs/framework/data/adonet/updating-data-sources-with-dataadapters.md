---
title: Veri kaynaklarını DataAdapters ile güncelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: b8e082b98870a59e8fb6f42fa7bedb86c2832d33
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245632"
---
# <a name="updating-data-sources-with-dataadapters"></a>Veri kaynaklarını DataAdapters ile güncelleştirme
`Update` Yöntemi <xref:System.Data.Common.DataAdapter> değişikliklerden çözümlemek için çağrılan bir <xref:System.Data.DataSet> veri kaynağına geri dönün. `Update` Yöntemi gibi `Fill` yöntemi örneği bağımsız değişken olarak alan bir `DataSet`ve isteğe bağlı <xref:System.Data.DataTable> nesne veya `DataTable` adı. `DataSet` Örneği `DataSet` yapılmış, değişiklikleri içeren ve `DataTable` değişiklikleri alınacak tabloyu tanımlar. Hayır ise `DataTable` belirtilirse, ilk `DataTable` içinde `DataSet` kullanılır.  
  
 Çağırdığınızda `Update` yöntemi `DataAdapter` yapmış olduğunuz değişiklikleri analiz eder ve (INSERT, UPDATE veya DELETE) uygun komutu yürütür. Zaman `DataAdapter` değişiklik karşılaştığında bir <xref:System.Data.DataRow>, kullandığı <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, veya <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> değişiklik işlemek için. Bu sayede tasarım zamanında komut sözdizimi belirtilerek ADO.NET uygulamanızın performansını en üst düzeye çıkarmak ve mümkün olduğunda, saklı yordamları kullanarak. Açıkça çağırmadan önce komutları ayarlanmalıdır `Update`. Varsa `Update` çağrılır ve uygun komutu için belirli bir güncelleştirmenin mevcut değil (örneğin, Hayır `DeleteCommand` silinen satırları), bir özel durum oluşturulur.  
  
> [!NOTE]
>  Düzenleme veya silme verileri kullanarak SQL Server saklı yordamları kullanıyorsanız bir `DataAdapter`, saklı yordam tanımında SET NOCOUNT ON kullanmadığınızdan emin olun. Bu, etkilenen satır sayısı sıfır olarak döndürülen neden olur, `DataAdapter` bir eşzamanlılık çakışması yorumlar. Bu olay bir <xref:System.Data.DBConcurrencyException> oluşturulur.  
  
 Komut parametreleri, giriş ve çıkış değerleri için bir SQL deyimi veya saklı yordam değiştirilen her satır için belirtmek için kullanılabilir bir `DataSet`. Daha fazla bilgi için [DataAdapter parametreleri](../../../../docs/framework/data/adonet/dataadapter-parameters.md).  
  
> [!NOTE]
>  İçinde bir satırın silinmesi arasındaki farkı anlamak önemlidir bir <xref:System.Data.DataTable> ve satır kaldırılıyor. Çağırdığınızda `Remove` veya `RemoveAt` yöntemi, satır hemen kaldırıldı. Arka uç veri kaynağına karşılık gelen tüm satırlarda, ardından geçirirseniz etkilenmez `DataTable` veya `DataSet` için bir `DataAdapter` ve çağrı `Update`. Kullanırken `Delete` yöntemi, satır içinde kalır `DataTable` ve silinmek üzere işaretlenmiş. Ardından geçirirseniz `DataTable` veya `DataSet` için bir `DataAdapter` ve çağrı `Update`, arka uç veri kaynağına karşılık gelen satır silindi.  
  
 Varsa, `DataTable` eşler veya oluşturulan bir tek veritabanı tablosundan avantajlarından yararlanabilirsiniz <xref:System.Data.Common.DbCommandBuilder> otomatik olarak oluşturmak için nesne `DeleteCommand`, `InsertCommand`, ve `UpdateCommand` için nesneleri `DataAdapter`. Daha fazla bilgi için [CommandBuilders ile komut oluşturma](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).  
  
## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a>Değerlerini bir veri kümesine eşlenecek UpdatedRowSource kullanma  
 Veri kaynağından döndürülen değerlerin geri nasıl eşleneceğini denetleyebilirsiniz `DataTable` güncelleştirme yöntemi çağrıyı izleyen bir `DataAdapter`, kullanarak <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> özelliği bir <xref:System.Data.Common.DbCommand> nesne. Ayarlayarak `UpdatedRowSource` özelliğini birine <xref:System.Data.UpdateRowSource> numaralandırma değerlerinin çıkış parametreleri tarafından döndürülen olup olmadığını denetleyebilir `DataAdapter` komutları göz ardı veya değiştirilen satır içinde uygulanan `DataSet`. İlk değiştirilen satıra uygulanan (varsa) satır döndürülüp döndürülmediğini belirtebilirsiniz `DataTable`.  
  
 Farklı değerleri aşağıdaki tabloda açıklanmıştır `UpdateRowSource` numaralandırma ve ile kullanılan bir komut davranışını nasıl etkilediklerini bir `DataAdapter`.  
  
|UpdatedRowSource numaralandırması|Açıklama|  
|----------------------------------|-----------------|  
|<xref:System.Data.UpdateRowSource.Both>|Değiştirilen satır içinde hem çıkış parametreleri hem de döndürülen sonuç kümesi ilk satır eşlenebilir `DataSet`.|  
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Döndürülen sonuç kümesi ilk satır verileri yalnızca değiştirilen satıra eşlenebilir `DataSet`.|  
|<xref:System.Data.UpdateRowSource.None>|Tüm çıkış parametreleri veya döndürülen sonuç kümesinin satırlar yoksayılır.|  
|<xref:System.Data.UpdateRowSource.OutputParameters>|Çıktı parametreleri yalnızca End'i eşlenebilir değiştirilen satıra `DataSet`.|  
  
 `Update` Yöntemi çözümler yaptığınız değişiklikleri veri kaynağına geri; ancak diğer istemciler değiştirilen veri kaynağını veri doldurduğunuz son daraltılmasından `DataSet`. Yenilemek için `DataSet` geçerli verilerle kullanmanız `DataAdapter` ve `Fill` yöntemi. Yeni satır tabloya eklenecek ve güncelleştirilmiş bilgileri var olan satır birleştirilir. `Fill` Yöntemi yeni bir satır eklenir ya da mevcut bir satırı birincil anahtar değerlerini satırlarda inceleyerek güncelleştirilecek belirler `DataSet` ve tarafından döndürülen satırlar `SelectCommand`. Varsa `Fill` yöntemi ile karşılaşırsa, bir satır için birincil bir anahtar değeri `DataSet` tarafından döndürülen sonuçları bir satırdaki birincil bir anahtar değeri ile eşleşen `SelectCommand`, var olan satır tarafındandöndürülensatırbilgilerlegüncelleştirir`SelectCommand`ve ayarlar <xref:System.Data.DataRow.RowState%2A> için mevcut satırın `Unchanged`. Tarafından döndürülen bir satır varsa `SelectCommand` birincil anahtar değerlerini satırlarda eşleşmeyen birincil bir anahtar değere sahip `DataSet`, `Fill` yöntemi ile yeni bir satır ekler bir `RowState` , `Unchanged`.  
  
> [!NOTE]
>  Varsa `SelectCommand` bir dış birleştirme, sonuçlarını döndürür `DataAdapter` değil ayarlayacak bir `PrimaryKey` elde edilen değer `DataTable`. Tanımlamanız gerekir `PrimaryKey` kendinize yinelenen satırları düzgün şekilde çözümlendiğinden emin olun. Daha fazla bilgi için [birincil anahtarlar tanımlama](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 Çağrılırken oluşabilecek özel durumları işlemek için `Update` kullanabileceğiniz yöntemi `RowUpdated` oluşunca, satır güncelleştirme hatalar için yanıt vermede olay (bkz [DataAdapter olaylarını işleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)), veya ayarlayabilirsiniz `DataAdapter.ContinueUpdateOnError` için`true` çağırmadan önce `Update`ve depolanan hata bilgilerini yanıtlar `RowError` güncelleştirme tamamlandığında belirli bir satır özelliği (bkz [satır hatası bilgileri](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)).  
  
 **Not** çağırma `AcceptChanges` üzerinde `DataSet`, `DataTable`, veya `DataRow` tüm neden olacak `Original` değerleri bir `DataRow` üzerine için `Current` değerleri `DataRow`. Çağırdıktan sonra satırı benzersiz olarak tanımlayan alan değerlerini değiştirilmişse, `AcceptChanges` `Original` değerleri veri kaynağı değerleri artık eşleşir. `AcceptChanges` Güncelleştirme yöntemine bir çağrı sırasında her satır için otomatik olarak adlandırılan bir `DataAdapter`. İlk ayarlayarak güncelleştirme yöntemine bir çağrı sırasında orijinal değerleri koruyabilir `AcceptChangesDuringUpdate` özelliği `DataAdapter` false veya bir olay işleyicisi için oluşturarak `RowUpdated` olay ve ayarı <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> için <xref:System.Data.UpdateStatus.SkipCurrentRow>. Daha fazla bilgi için [DataSet içeriklerini birleştirme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md) ve [DataAdapter olaylarını işleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekler açıkça ayarlayarak değiştirilmiş satırları güncelleştirmeleri gerçekleştirmek nasıl göstermektedir `UpdateCommand` , bir `DataAdapter` ve çağırma kendi `Update` yöntemi. Bildirim parametresi güncelleştirme WHERE yan tümcesinde deyimi kullanmak üzere ayarlanmış belirtilen `Original` değerini `SourceColumn`. Bu önemlidir çünkü `Current` değeri değiştirilmiş olabilir ve veri kaynağı değeri eşleşmeyebilir. `Original` Değerdir doldurmak için kullanılan değer `DataTable` veri kaynağından.  
  
 [!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]  
  
## <a name="autoincrement-columns"></a>AutoIncrement sütunları  
 Veri kaynağınızdaki tabloları otomatik artan sütununuz varsa, sütunları doldurabilirsiniz, `DataSet` göre ya da otomatik artış değeri döndüren bir saklı yordam bir output parametresi olarak ve bu tablodaki bir sütun eşleme, döndürme otomatik artış değeri bir sonuç kümesi saklı yordam ya da SQL deyimi veya kullanarak döndürülen ilk satırında `RowUpdated` olayı `DataAdapter` ek bir SELECT deyimi yürütmek için. Daha fazla bilgi ve örnek için bkz. [alınırken kimlik veya otomatik sayı değerlerini](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).  
  
## <a name="ordering-of-inserts-updates-and-deletes"></a>Ekleme, güncelleştirme ve silme sıralama  
 Birçok durumda aracılığıyla hangi değişiklikleri sırayla `DataSet` gönderilen veri kaynağı önemlidir. Örneğin, mevcut bir satırı için birincil bir anahtar değer güncelleştirilir ve yabancı anahtar yeni birincil anahtar değerine sahip yeni bir satır eklendi, güncelleştirmeden önce INSERT işlemek önemlidir.  
  
 Kullanabileceğiniz `Select` yöntemi `DataTable` döndürülecek bir `DataRow` yalnızca belirli bir satırla başvuran bir dizi `RowState`. Ardından döndürülen geçirebilirsiniz `DataRow` için dizi `Update` yöntemi `DataAdapter` değiştirilen satırları işlenecek. Güncelleştirilecek satır kümesini belirterek, ekleme, güncelleştirme ve silme işlenme sırasını denetleyebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Örneğin, aşağıdaki kod, tablonun silinen satırları işlenen ilk sonra güncelleştirilen satırların ve eklenen satırları olmasını sağlar.  
  
```vb  
Dim table As DataTable = dataSet.Tables("Customers")  
  
' First process deletes.  
dataSet.Update(table.Select(Nothing, Nothing, _  
  DataViewRowState.Deleted))  
  
' Next process updates.  
adapter.Update(table.Select(Nothing, Nothing, _  
  DataViewRowState.ModifiedCurrent))  
  
' Finally, process inserts.  
dataAdapater.Update(table.Select(Nothing, Nothing, _  
  DataViewRowState.Added))  
```  
  
```csharp  
DataTable table = dataSet.Tables["Customers"];  
  
// First process deletes.  
adapter.Update(table.Select(null, null, DataViewRowState.Deleted));  
  
// Next process updates.  
adapter.Update(table.Select(null, null,   
  DataViewRowState.ModifiedCurrent));  
  
// Finally, process inserts.  
adapter.Update(table.Select(null, null, DataViewRowState.Added));  
```  
  
## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a>DataAdapter almak ve verileri güncelleştirmek için kullanın  
 DataAdapter almak ve verileri güncelleştirmek için kullanabilirsiniz.  
  
-   Örnek DataAdapter.AcceptChangesDuringFill veritabanındaki verileri kopyalamak için kullanır. Özelliği false ayarlarsanız, tablonun doldururken AcceptChanges çağrılmaz ve yeni eklenen satırlar eklenen satırlar olarak kabul edilir. Bu nedenle, örnek veritabanına yeni satır eklemek için bu satırlara kullanır.  
  
-   Örnekleri DataAdapter.TableMappings DataTable ve kaynak tablosu arasındaki eşlemeyi tanımlamak için kullanır.  
  
-   Örnek DataAdapter.FillLoadOption bağdaştırıcısı DataTable nesnesinden dbdatareader öğesine dönüştürülemedi nasıl doldurduğunu belirlemek için kullanır. Bir DataTable oluşturduğunuzda, yalnızca veri veritabanından geçerli sürümü veya özgün sürümle LoadOption.Upsert veya LoadOption.PreserveChanges olarak ayarlayarak yazabilirsiniz.  
  
-   Toplu işlemleri gerçekleştirmek için DbDataAdapter.UpdateBatchSize kullanarak örnek ayrıca tablo güncelleştirin.  
  
 Derleme ve örneği çalıştırmadan önce örnek veritabanını oluşturmanız gerekir:  
  
```sql
USE [master]  
GO  
  
CREATE DATABASE [MySchool]   
  
GO  
  
USE [MySchool]  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
CREATE TABLE [dbo].[Course]([CourseID] [nvarchar](10) NOT NULL,  
[Year] [smallint] NOT NULL,  
[Title] [nvarchar](100) NOT NULL,  
[Credits] [int] NOT NULL,  
[DepartmentID] [int] NOT NULL,  
 CONSTRAINT [PK_Course] PRIMARY KEY CLUSTERED  
(  
[CourseID] ASC,  
[Year] ASC  
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]  
  
GO  
  
SET ANSI_NULLS ON  
GO  
SET QUOTED_IDENTIFIER ON  
GO  
CREATE TABLE [dbo].[Department]([DepartmentID] [int] IDENTITY(1,1) NOT NULL,  
[Name] [nvarchar](50) NOT NULL,  
[Budget] [money] NOT NULL,  
[StartDate] [datetime] NOT NULL,  
[Administrator] [int] NULL,  
 CONSTRAINT [PK_Department] PRIMARY KEY CLUSTERED  
(  
[DepartmentID] ASC  
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]  
  
GO  
  
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1045', 2012, N'Calculus', 4, 7)  
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1061', 2012, N'Physics', 4, 1)  
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2021', 2012, N'Composition', 3, 2)  
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2042', 2012, N'Literature', 4, 2)  
  
SET IDENTITY_INSERT [dbo].[Department] ON   
  
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (1, N'Engineering', 350000.0000, CAST(0x0000999C00000000 AS DateTime), 2)  
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (2, N'English', 120000.0000, CAST(0x0000999C00000000 AS DateTime), 6)  
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (4, N'Economics', 200000.0000, CAST(0x0000999C00000000 AS DateTime), 4)  
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (7, N'Mathematics', 250024.0000, CAST(0x0000999C00000000 AS DateTime), 3)  
SET IDENTITY_INSERT [dbo].[Department] OFF  
  
ALTER TABLE [dbo].[Course]  WITH CHECK ADD  CONSTRAINT [FK_Course_Department] FOREIGN KEY([DepartmentID])  
REFERENCES [dbo].[Department] ([DepartmentID])  
GO  
ALTER TABLE [dbo].[Course] CHECK CONSTRAINT [FK_Course_Department]  
GO  
```  
  
 Bu kod örneği ile C# ve Visual Basic projeleri bulunabilir [geliştirici kodu örnekleri](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).  
  
```csharp
using System;  
using System.Data;  
using System.Data.Common;  
using System.Data.SqlClient;  
using System.Linq;  
using CSDataAdapterOperations.Properties;  
  
namespace CSDataAdapterOperations.Properties {  
   internal sealed partial class Settings : global::System.Configuration.ApplicationSettingsBase {  
  
      private static Settings defaultInstance = ((Settings)(global::System.Configuration.ApplicationSettingsBase.Synchronized(new Settings())));  
  
      public static Settings Default {  
         get {  
            return defaultInstance;  
         }  
      }  
  
      [global::System.Configuration.ApplicationScopedSettingAttribute()]  
      [global::System.Configuration.DefaultSettingValueAttribute("Data Source=(local);Initial Catalog=MySchool;Integrated Security=True")]  
      public string MySchoolConnectionString {  
         get {  
            return ((string)(this["MySchoolConnectionString"]));  
         }  
      }  
   }  
}  
  
class Program {  
   static void Main(string[] args) {  
      Settings settings = new Settings();  
  
      // Copy the data from the database.  Get the table Department and Course from the database.  
      String selectString = @"SELECT [DepartmentID],[Name],[Budget],[StartDate],[Administrator]  
                                     FROM [MySchool].[dbo].[Department];  
  
                                   SELECT [CourseID],@Year as [Year],Max([Title]) as [Title],  
                                   Max([Credits]) as [Credits],Max([DepartmentID]) as [DepartmentID]  
                                   FROM [MySchool].[dbo].[Course]  
                                   Group by [CourseID]";  
  
      DataSet mySchool = new DataSet();  
  
      SqlCommand selectCommand = new SqlCommand(selectString);  
      SqlParameter parameter = selectCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2);  
      parameter.Value = new Random(DateTime.Now.Millisecond).Next(9999);  
  
      // Use DataTableMapping to map the source tables and the destination tables.  
      DataTableMapping[] tableMappings = {new DataTableMapping("Table", "Department"), new DataTableMapping("Table1", "Course")};  
      CopyData(mySchool, settings.MySchoolConnectionString, selectCommand, tableMappings);  
  
      Console.WriteLine("The following tables are from the database.");  
      foreach (DataTable table in mySchool.Tables) {  
         Console.WriteLine(table.TableName);  
         ShowDataTable(table);  
      }  
  
      // Roll back the changes  
      DataTable department = mySchool.Tables["Department"];  
      DataTable course = mySchool.Tables["Course"];  
  
      department.Rows[0]["Name"] = "New" + department.Rows[0][1];  
      course.Rows[0]["Title"] = "New" + course.Rows[0]["Title"];  
      course.Rows[0]["Credits"] = 10;  
  
      Console.WriteLine("After we changed the tables:");  
      foreach (DataTable table in mySchool.Tables) {  
         Console.WriteLine(table.TableName);  
         ShowDataTable(table);  
      }  
  
      department.RejectChanges();  
      Console.WriteLine("After use the RejectChanges method in Department table to roll back the changes:");  
      ShowDataTable(department);  
  
      DataColumn[] primaryColumns = { course.Columns["CourseID"] };  
      DataColumn[] resetColumns = { course.Columns["Title"] };  
      ResetCourse(course, settings.MySchoolConnectionString, primaryColumns, resetColumns);  
      Console.WriteLine("After use the ResetCourse method in Course table to roll back the changes:");  
      ShowDataTable(course);  
  
      // Batch update the table.  
      String insertString = @"Insert into [MySchool].[dbo].[Course]([CourseID],[Year],[Title],   
                                   [Credits],[DepartmentID])   
             values (@CourseID,@Year,@Title,@Credits,@DepartmentID)";  
      SqlCommand insertCommand = new SqlCommand(insertString);  
      insertCommand.Parameters.Add("@CourseID", SqlDbType.NVarChar, 10, "CourseID");  
      insertCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2, "Year");  
      insertCommand.Parameters.Add("@Title", SqlDbType.NVarChar, 100, "Title");  
      insertCommand.Parameters.Add("@Credits", SqlDbType.Int, 4, "Credits");  
      insertCommand.Parameters.Add("@DepartmentID", SqlDbType.Int, 4, "DepartmentID");  
  
      const Int32 batchSize = 10;  
      BatchInsertUpdate(course, settings.MySchoolConnectionString, insertCommand, batchSize);  
   }  
  
   private static void CopyData(DataSet dataSet, String connectionString, SqlCommand selectCommand, DataTableMapping[] tableMappings) {  
      using (SqlConnection connection = new SqlConnection(connectionString)) {  
         selectCommand.Connection = connection;  
  
         connection.Open();  
  
         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {adapter.TableMappings.AddRange(tableMappings);  
            // If set the AcceptChangesDuringFill as the false, AcceptChanges will not be called on a   
            // DataRow after it is added to the DataTable during any of the Fill operations.  
            adapter.AcceptChangesDuringFill = false;  
  
            adapter.Fill(dataSet);  
         }  
      }  
   }  
  
   // Roll back only one column or several columns data of the Course table by call ResetDataTable method.  
   private static void ResetCourse(DataTable table, String connectionString,  
       DataColumn[] primaryColumns, DataColumn[] resetColumns) {  
      table.PrimaryKey = primaryColumns;  
  
      // Build the query string  
      String primaryCols = String.Join(",", primaryColumns.Select(col => col.ColumnName));  
      String resetCols = String.Join(",", resetColumns.Select(col => $"Max({col.ColumnName}) as {col.ColumnName}"));
  
      String selectString = $"Select {primaryCols},{resetCols} from Course Group by {primaryCols}");
  
      SqlCommand selectCommand = new SqlCommand(selectString);  
  
      ResetDataTable(table, connectionString, selectCommand);  
   }  
  
   // RejectChanges will roll back all changes made to the table since it was loaded, or the last time AcceptChanges   
   // was called. When you copy from the database, you can lose all the data after calling RejectChanges  
   // The ResetDataTable method rolls back one or more columns of data.  
   private static void ResetDataTable(DataTable table, String connectionString,  
       SqlCommand selectCommand) {  
      using (SqlConnection connection = new SqlConnection(connectionString)) {  
         selectCommand.Connection = connection;  
  
         connection.Open();  
  
         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {  
            // The incoming values for this row will be written to the current version of each   
            // column. The original version of each column's data will not be changed.  
            adapter.FillLoadOption = LoadOption.Upsert;  
  
            adapter.Fill(table);  
         }  
      }  
   }  
  
   private static void BatchInsertUpdate(DataTable table, String connectionString,  
       SqlCommand insertCommand, Int32 batchSize) {  
      using (SqlConnection connection = new SqlConnection(connectionString)) {  
         insertCommand.Connection = connection;  
         // When setting UpdateBatchSize to a value other than 1, all the commands   
         // associated with the SqlDataAdapter have to have their UpdatedRowSource   
         // property set to None or OutputParameters. An exception is thrown otherwise.  
         insertCommand.UpdatedRowSource = UpdateRowSource.None;  
  
         connection.Open();  
  
         using (SqlDataAdapter adapter = new SqlDataAdapter()) {  
            adapter.InsertCommand = insertCommand;  
            // Gets or sets the number of rows that are processed in each round-trip to the server.  
            // Setting it to 1 disables batch updates, as rows are sent one at a time.  
            adapter.UpdateBatchSize = batchSize;  
  
            adapter.Update(table);  
  
            Console.WriteLine("Successfully to update the table.");  
         }  
      }  
   }  
  
   private static void ShowDataTable(DataTable table) {  
      foreach (DataColumn col in table.Columns) {  
         Console.Write("{0,-14}", col.ColumnName);  
      }  
      Console.WriteLine("{0,-14}", "RowState");  
  
      foreach (DataRow row in table.Rows) {  
         foreach (DataColumn col in table.Columns) {  
            if (col.DataType.Equals(typeof(DateTime)))  
               Console.Write("{0,-14:d}", row[col]);  
            else if (col.DataType.Equals(typeof(Decimal)))  
               Console.Write("{0,-14:C}", row[col]);  
            else  
               Console.Write("{0,-14}", row[col]);  
         }  
         Console.WriteLine("{0,-14}", row.RowState);  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Satır Durumları ve Satır Sürümleri](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [AcceptChanges ve RejectChanges](../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)  
 [DataSet İçeriklerini Birleştirme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 [Kimliği veya Otomatik Sayı Değerlerini Alma](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
