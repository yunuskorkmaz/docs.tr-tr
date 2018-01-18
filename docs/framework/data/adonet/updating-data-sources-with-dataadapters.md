---
title: "Veri kaynakları ile DataAdapters güncelleştiriliyor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
caps.latest.revision: "8"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e99ff801894149a2324638bfacbc1d32ee937e0a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="updating-data-sources-with-dataadapters"></a>Veri kaynakları ile DataAdapters güncelleştiriliyor
`Update` Yöntemi <xref:System.Data.Common.DataAdapter> değişikliklerden çözümlemek için çağrılan bir <xref:System.Data.DataSet> veri kaynağına geri. `Update` Yöntemi gibi `Fill` yöntemi örneği bağımsız değişken olarak alan bir `DataSet`ve isteğe bağlı bir <xref:System.Data.DataTable> nesne veya `DataTable` adı. `DataSet` Örneği `DataSet` yapıldı, değişiklikler içeriyor ve `DataTable` değişiklikleri alınacağı tabloyu tanımlar. Öyle değilse `DataTable` belirtilirse, ilk `DataTable` içinde `DataSet` kullanılır.  
  
 Çağırdığınızda `Update` yöntemi, `DataAdapter` yapmış olduğunuz değişiklikleri analiz eder ve uygun komutu (INSERT, UPDATE veya DELETE) yürütür. Zaman `DataAdapter` bir değişiklik karşılaştığı bir <xref:System.Data.DataRow>, kullanır <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, veya <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> değişiklik işleyemedi. Bu tasarım zamanında komut sözdizimi belirterek ADO.NET uygulamanızın performansını en üst düzeye çıkarmanıza olanak tanır ve mümkün olduğunda, saklı yordamlar yalıtılacaktır. Komutları çağırmadan önce açık olarak ayarlamalısınız `Update`. Varsa `Update` olarak adlandırılır ve uygun komutu için belirli bir güncelleştirme yok (örneğin, Hayır `DeleteCommand` silinen satır), bir özel durum.  
  
> [!NOTE]
>  Düzenlemek veya kullanarak verileri silmek için SQL Server saklı yordamları kullanıyorsanız, bir `DataAdapter`, saklı yordam tanımı'nda SET NOCOUNT ON kullanmadığınızdan emin olun. Bu sıfır olarak döndürülen etkilenen satırların sayısı neden olur, `DataAdapter` bir eşzamanlılık çakışması yorumlar. Bu olay bir <xref:System.Data.DBConcurrencyException> oluşturulur.  
  
 Komut parametreleri, bir SQL deyimi için girdi ve çıktı değerler veya değiştirilen her satır için saklı yordam belirtmek için kullanılabilir bir `DataSet`. Daha fazla bilgi için bkz: [DataAdapter parametreleri](../../../../docs/framework/data/adonet/dataadapter-parameters.md).  
  
> [!NOTE]
>  Bir satırın silinmesi arasındaki farkı anlamak önemlidir bir <xref:System.Data.DataTable> ve satır kaldırma. Çağırdığınızda `Remove` veya `RemoveAt` yöntemi, satır hemen kaldırılır. Ardından başarılı olursa arka uç veri kaynağına karşılık gelen satırları etkilenmez `DataTable` veya `DataSet` için bir `DataAdapter` ve arama `Update`. Kullandığınızda `Delete` yöntemi, satır içinde kalır `DataTable` ve silinmek üzere işaretlenmiş. Ardından geçirirseniz `DataTable` veya `DataSet` için bir `DataAdapter` ve arama `Update`, arka uç veri kaynağına karşılık gelen satır silindi.  
  
 Varsa, `DataTable` eşlendiği veya oluşturulan tek veritabanı tablosundan özelliklerden yararlanabilirsiniz <xref:System.Data.Common.DbCommandBuilder> otomatik olarak oluşturmak için nesne `DeleteCommand`, `InsertCommand`, ve `UpdateCommand` için nesneleri `DataAdapter`. Daha fazla bilgi için bkz: [CommandBuilders oluşturma komutlarıyla](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).  
  
## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a>Bir veri kümesine değerlerini eşlemek için UpdatedRowSource kullanma  
 Veri kaynağından döndürülen değerler geri nasıl eşlendiğini denetleyebilir `DataTable` güncelleştirme yöntemini çağrısından bir `DataAdapter`, kullanarak <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> özelliği bir <xref:System.Data.Common.DbCommand> nesnesi. Ayarlayarak `UpdatedRowSource` özelliğini birine <xref:System.Data.UpdateRowSource> numaralandırma değerlerinin çıkış parametreleri tarafından döndürülen olup olmadığını denetleyebilir `DataAdapter` komutlar göz ardı veya değiştirilen satırda uygulanan `DataSet`. İlk (varsa) satır değiştirilen satırda uygulanan döndürülen olup olmadığını belirtebilirsiniz `DataTable`.  
  
 Farklı değerleri aşağıdaki tabloda açıklanmaktadır `UpdateRowSource` numaralandırma ve ile kullanılan bir komut davranışını nasıl etkilediklerini bir `DataAdapter`.  
  
|UpdatedRowSource numaralandırması|Açıklama|  
|----------------------------------|-----------------|  
|<xref:System.Data.UpdateRowSource.Both>|Değiştirilen satır çıkış parametreleri ve döndürülen sonuç kümesi ilk satır eşlenebilir `DataSet`.|  
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Döndürülen sonuç kümesi ilk satır verileri yalnızca değiştirilen satıra eşlenebilir `DataSet`.|  
|<xref:System.Data.UpdateRowSource.None>|Herhangi bir çıktı parametreleri veya döndürülen sonuç kümesinin satırlar yok sayılır.|  
|<xref:System.Data.UpdateRowSource.OutputParameters>|Çıkış parametreleri yalnızca değiştirilen satıra eşlenebilir `DataSet`.|  
  
 `Update` Metodu çözümler değişikliklerinizi geri veri kaynağına; ancak diğer istemciler değiştirilen verileri veri kaynağında doldurduğunuz son zaman `DataSet`. Yenilemek için `DataSet` geçerli verilerle kullanmak `DataAdapter` ve `Fill` yöntemi. Yeni satırlar tabloya eklenir ve güncelleştirilmiş bilgileri varolan satırlara birleştirilir. `Fill` Yöntemi yeni bir satır eklenir ya da var olan bir satır satır birincil anahtar değerlerinin inceleyerek güncelleştirileceği belirler `DataSet` ve tarafından döndürülen satır `SelectCommand`. Varsa `Fill` yöntemi karşılaştığı bir satır için bir birincil anahtar değeri `DataSet` tarafından döndürülen sonuçlar numaralı satırdaki bir birincil anahtar değeri ile eşleşen `SelectCommand`, varolan bir satır tarafındandöndürülensatırbilgileriylegüncelleştirir`SelectCommand`ve ayarlar <xref:System.Data.DataRow.RowState%2A> mevcut satırın `Unchanged`. Tarafından döndürülen bir satır varsa `SelectCommand` satırları birincil anahtar değerleriyle eşleşmeyen birincil anahtar değerine sahip `DataSet`, `Fill` yöntemi ile yeni bir satır ekler bir `RowState` , `Unchanged`.  
  
> [!NOTE]
>  Varsa `SelectCommand` bir dış birleşim, sonuçlarını döndürür `DataAdapter` ayarlanmamış bir `PrimaryKey` elde edilen değer `DataTable`. Tanımlamanız gerekir `PrimaryKey` kendinize yinelenen satırları düzgün olarak çözülen emin olun. Daha fazla bilgi için bkz: [tanımlama birincil anahtarlar](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 Çağırma sırasında meydana gelebilecek özel durumları işleme `Update` yöntemini kullanabilirsiniz `RowUpdated` göründüklerinde satır güncelleştirme hataları yanıtlamasını olay (bkz [olaylarını işleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)), veya ayarlayabilirsiniz `DataAdapter.ContinueUpdateOnError` için`true` çağırmadan önce `Update`ve depolanan hata bilgilerini yanıtlar `RowError` güncelleştirme tamamlandığında, belirli bir satır özelliği (bkz [satır hata bilgilerini](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)).  
  
 **Not** çağırma `AcceptChanges` üzerinde `DataSet`, `DataTable`, veya `DataRow` tüm neden olacak `Original` değerleri bir `DataRow` ile üzerine yazılmasını `Current` değerleri `DataRow`. Çağrıldıktan sonra satırı benzersiz olarak tanımlayan alan değerlerini değiştirilmişse, `AcceptChanges` `Original` değerleri artık değerleri veri kaynağında eşleşmeyen. `AcceptChanges`Her satır için güncelleştirme yöntemine bir çağrı sırasında otomatik olarak çağrılır bir `DataAdapter`. İlk ayarlayarak güncelleştirme yöntemine bir çağrı sırasında orijinal değerleri koruyabilir `AcceptChangesDuringUpdate` özelliği `DataAdapter` false ya da bir olay işleyicisi oluşturarak `RowUpdated` olay ve ayarı <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> için <xref:System.Data.UpdateStatus.SkipCurrentRow>. Daha fazla bilgi için bkz: [birleştirme DataSet içeriği](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md) ve [olaylarını işleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekler açıkça ayarlayarak değiştirilmiş satırlara güncelleştirmeleri gerçekleştirmek nasıl göstermektedir `UpdateCommand` , bir `DataAdapter` ve çağırma kendi `Update` yöntemi. Parametre güncelleştirme WHERE yan tümcesinde deyimi kullanmak üzere ayarlanmış belirtilen bildirimi `Original` değerini `SourceColumn`. Bu önemlidir çünkü `Current` değeri değiştirilmiş olabilir ve veri kaynağındaki değer eşleşmeyebilir. `Original` Değerdir doldurmak için kullanılan değer `DataTable` veri kaynağından.  
  
 [!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]  
  
## <a name="autoincrement-columns"></a>AutoIncrement sütunları  
 Veri kaynağınızı tablolardan otomatik artırma sütunları varsa, sütunları doldurabilirsiniz, `DataSet` da otomatik artım değeri döndüren bir saklı yordam bir output parametresi olarak ve, bir tablodaki bir sütun eşlemesi, göre döndürme bir sonuç kümesi bir saklı yordam veya SQL deyimi veya kullanarak döndürülen ilk satırında otomatik artım değeri `RowUpdated` olayı `DataAdapter` ek bir SELECT deyimi yürütmek için. Daha fazla bilgi ve bir örnek için bkz: [alma kimliği veya sayı değerlerini](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).  
  
## <a name="ordering-of-inserts-updates-and-deletes"></a>Ekler, güncelleştirmeleri ve silme sıralama  
 Birçok durumlarda aracılığıyla hangi değişikliklerinin sırayla `DataSet` gönderilen veri kaynağı önemlidir. Örneğin, bir birincil anahtar değeri olan bir satır için güncelleştirilir ve yabancı anahtar olarak yeni birincil anahtar değerine sahip yeni bir satır eklenir, güncelleştirmeden önce Ekle işlemek önemlidir.  
  
 Kullanabileceğiniz `Select` yöntemi `DataTable` döndürmek için bir `DataRow` yalnızca belirli bir satırlarla başvuran dizi `RowState`. Ardından döndürülen geçirebilirsiniz `DataRow` için dizi `Update` yöntemi `DataAdapter` değiştirilen satırları işleyemedi. Güncelleştirilecek satırların alt kümesini belirterek ekler, güncelleştirmeleri ve silme işlenen siparişi kontrol edebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Örneğin, aşağıdaki kodu tablonun silinen satırları işlenen ilk sonra güncelleştirilen satırları ve eklenen satırlar olmasını sağlar.  
  
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
 DataAdapter alabilir ve verileri güncelleştirmek için kullanabilirsiniz.  
  
-   Örnek DataAdapter.AcceptChangesDuringFill veritabanındaki verileri kopyalamak için kullanır. Özelliği false olarak ayarlarsanız, AcceptChanges tablo doldururken çağrılmaz ve yeni eklenen satır ekli satırlar olarak kabul edilir. Bu nedenle, örnek veritabanına yeni satır eklemek için bu satırı kullanır.  
  
-   Örnekler DataAdapter.TableMappings kaynak tablosu ile DataTable arasında eşleme tanımlamak için kullanır.  
  
-   Örnek DataAdapter.FillLoadOption nasıl bağdaştırıcısı DataTable DbDataReader nesnesinden doldurur belirlemek için kullanır. DataTable oluşturduğunuzda, yalnızca verileri veritabanından geçerli sürümü veya özgün sürümü LoadOption.Upsert veya LoadOption.PreserveChanges olarak özelliği ayarlanarak yazabilirsiniz.  
  
-   Toplu işlemleri gerçekleştirmek için DbDataAdapter.UpdateBatchSize kullanarak örnek da tabloyu güncelleştir.  
  
 Derleme ve örneği çalıştırmadan önce örnek veritabanı oluşturmanız gerekir:  
  
```  
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
  
 Bu kod örneği ile C# ve Visual Basic projeleri bulunabilir [Geliştirici kod örnekleri](http://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).  
  
```  
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
      String resetCols = String.Join(",", resetColumns.Select(col => "Max(" + col.ColumnName + ") as " + col.ColumnName));  
  
      String selectString = String.Format("Select {0},{1} from Course Group by {0}", primaryCols, resetCols);  
  
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
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
