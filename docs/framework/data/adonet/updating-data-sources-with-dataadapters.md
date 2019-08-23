---
title: Veri Kaynaklarını DataAdapters ile Güncelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: 2b7d6ac6022da793b90b5447062ceac82cc7290c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965198"
---
# <a name="updating-data-sources-with-dataadapters"></a>Veri Kaynaklarını DataAdapters ile Güncelleştirme
' `Update` <xref:System.Data.DataSet> Nin yöntemi,geridönerekverikaynağınayapılandeğişiklikleri<xref:System.Data.Common.DataAdapter> çözümlemek için çağırılır. `DataSet` `DataTable` <xref:System.Data.DataTable> Yöntemi gibi `Fill` Yöntem, bir örneği ve isteğe bağlı bir nesne ya da ad bağımsız değişken olarak alır. `Update` Örnek, yapılan değişiklikleri içeren, ve `DataTable` değişikliklerin alınacağı tabloyu tanımlar. `DataSet` `DataSet` Hayır `DataTable` belirtilirse, `DataTable` içindeki`DataSet` ilk, kullanılır.  
  
 `Update` Yöntemini`DataAdapter` çağırdığınızda, yapılan değişiklikleri analiz eder ve uygun komutu yürütür (INSERT, Update veya delete). <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> Bir `DataAdapter` değişikliğekarşılaştığında,değişikliğiişlemekiçin<xref:System.Data.DataRow>, veya kullanır. Bu, tasarım zamanında komut sözdizimini belirterek ve mümkün olduğunda saklı yordamların kullanımı aracılığıyla ADO.NET uygulamanızın performansını en üst düzeye çıkarmanıza olanak sağlar. Çağrılmadan `Update`önce komutları açıkça ayarlamanız gerekir. Çağrılırsa ve belirli bir güncelleştirme için uygun komut yoksa (örneğin, silinen satırlar için Hayır `DeleteCommand` ), bir özel durum oluşturulur. `Update`  
  
> [!NOTE]
> Kullanarak veri düzenlemek veya silmek için SQL Server saklı yordamlar kullanıyorsanız `DataAdapter`, saklı yordam tanımında set nocount kullanmayın. Bu, etkilenen satırların sayısının sıfır olmasına neden olur ve bu da `DataAdapter` eşzamanlılık çakışması olarak yorumladığı anlamına gelir. Bu olayda, bir <xref:System.Data.DBConcurrencyException> oluşturulur.  
  
 Komut parametreleri, bir SQL deyimin giriş ve çıkış değerlerini veya içindeki her bir `DataSet`değiştirilen satır için saklı yordamı belirtmek için kullanılabilir. Daha fazla bilgi için bkz. [DataAdapter Parameters](../../../../docs/framework/data/adonet/dataadapter-parameters.md).  
  
> [!NOTE]
> İçindeki bir <xref:System.Data.DataTable> satırı silme ve satırı kaldırma arasındaki farkı anlamak önemlidir. `Remove` Veya`RemoveAt` yöntemini çağırdığınızda, satır hemen kaldırılır. Daha `DataTable` sonra veya `DataSet` `DataAdapter` '`Update`a geçiş yaparsanız, arka uç veri kaynağındaki karşılık gelen satırlar etkilenmez. `Delete` Yöntemini kullandığınızda, satır `DataTable` içinde kalır ve silinmek üzere işaretlenir. Daha sonra `DataTable` veya `DataSet` ' `DataAdapter` e`Update`geçirirseniz, arka uç veri kaynağındaki karşılık gelen satır silinir.  
  
 Tek bir `DataTable` veritabanı tablosundan eşlemleriniz veya oluşturulursa,,, ve `UpdateCommand` nesnelerini `DataAdapter`otomatik olarak oluşturmak `DeleteCommand` `InsertCommand`için <xref:System.Data.Common.DbCommandBuilder> nesnesinden faydalanabilir. Daha fazla bilgi için bkz. [CommandBuilder 'lar Ile komut oluşturma](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).  
  
## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a>Değerleri bir veri kümesiyle eşlemek için UpdatedRowSource kullanma  
 `DataTable` `DataAdapter`Bir nesnenin<xref:System.Data.Common.DbCommand> özelliğini kullanarak, veri kaynağından döndürülen değerlerin bir ' ın update yöntemine yapılan çağrıya nasıl geri eşlendiğini denetleyebilirsiniz. <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> `UpdatedRowSource` Özelliğini <xref:System.Data.UpdateRowSource> sabit listesi değerlerinden birine ayarlayarak, `DataAdapter` komutlar tarafından döndürülen çıkış parametrelerinin yok sayıldığını `DataSet`veya içindeki değiştirilen satıra uygulanıp uygulanmadığını kontrol edebilirsiniz. Ayrıca, `DataTable`ilk döndürülen satırın (varsa) içindeki değiştirilen satıra uygulanıp uygulanmayacağını belirtebilirsiniz.  
  
 Aşağıdaki tabloda, `UpdateRowSource` numaralandırmanın farklı değerleri ve `DataAdapter`ile kullanılan bir komutun davranışlarını nasıl etkilediği açıklanmaktadır.  
  
|UpdatedRowSource numaralandırması|Açıklama|  
|----------------------------------|-----------------|  
|<xref:System.Data.UpdateRowSource.Both>|Döndürülen sonuç kümesinin çıkış parametreleri ve ilk satırı, `DataSet`içindeki değiştirilen satırla eşleştirilebilir.|  
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Yalnızca döndürülen sonuç kümesinin ilk satırındaki veriler, `DataSet`içindeki değiştirilen satırla eşleştirilebilir.|  
|<xref:System.Data.UpdateRowSource.None>|Döndürülen sonuç kümesinin herhangi bir çıkış parametresi veya satırı yok sayılır.|  
|<xref:System.Data.UpdateRowSource.OutputParameters>|Yalnızca çıkış parametreleri içindeki `DataSet`değiştirilen satırla eşleştirilebilir.|  
  
 Yöntemi, değişikliklerinizi veri kaynağına geri çözümler; ancak diğer istemciler, `DataSet`son doldurduğunuz zamandan bu yana veri kaynağındaki verileri değiştirmiş olabilir. `Update` Güncel verilerle uygulamanızı `DataSet` yenilemek için `DataAdapter` ve `Fill` yöntemini kullanın. Tabloya yeni satırlar eklenecek ve güncel bilgiler mevcut satırlara dahil edilecek. Yöntemi, yeni bir satırın eklenip eklenmeyeceğini veya `DataSet` içindeki satırların birincil anahtar değerleri ve tarafından `SelectCommand`döndürülen satırlarda incelenerek güncelleştirilip güncelleştirilmediğini belirler. `Fill` `Fill` Yöntemi `DataSet` , tarafından`SelectCommand`döndürülen sonuçlarda yer alan bir satırdaki birincil anahtar değeriyle eşleşen bir satır için birincil anahtar değeriyle karşılaşırsa, var olan satırı `SelectCommand`,ve var olan <xref:System.Data.DataRow.RowState%2A> satırın öğesini olarak `Unchanged`ayarlar. Tarafından `SelectCommand` döndürülen bir satır, `DataSet`içindeki satırların birincil anahtar değerleriyle eşleşmeyen bir birincil anahtar değerine sahipse, `Fill` `Unchanged`yöntemi ' a `RowState` sahip yeni bir satır ekler.  
  
> [!NOTE]
> Eğer, `SelectCommand` bir dış birleştirmenin `DataAdapter` sonuçlarını döndürürse, sonuç `DataTable`için bir `PrimaryKey` değer ayarlayamaz. Yinelenen satırların doğru bir `PrimaryKey` şekilde çözümlendiğinden emin olmak için kendiniz tanımlamanız gerekir. Daha fazla bilgi için bkz. [birincil anahtarları tanımlama](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 `Update` Yöntemi çağırırken oluşabilecek özel durumları işlemek için `RowUpdated` olayı, meydana gelen satır güncelleştirme hatalarına yanıt vermek için kullanabilirsiniz (bkz. [DataAdapter olaylarını işleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)) veya daha önce olarak ayarlayabilirsiniz `DataAdapter.ContinueUpdateOnError` `true` Güncelleştirme `Update`tamamlandığında belirli bir satırın `RowError` özelliğinde depolanan hata bilgilerini çağırma ve bunlara yanıt verme (bkz. [satır hatası bilgileri](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)).  
  
 **Göz önünde** `DataSet`, `AcceptChanges` ,Veya`DataRow` üzerinde çağırma, için tüm `Original` değerlerin üzerineyazılmasına`Current` neden olur`DataRow`. `DataRow` `DataTable` Satırı benzersiz olarak tanımlayan alan değerleri değiştirilmişse, `AcceptChanges` `Original` değerler çağrıldıktan sonra, veri kaynağındaki değerlerle artık eşleşmeyecektir. `AcceptChanges`, bir `DataAdapter`öğesinin Update metoduna yapılan çağrı sırasında her satır için otomatik olarak çağrılır. İlk değeri Update yöntemine yapılan bir çağrı `AcceptChangesDuringUpdate` sırasında, `DataAdapter` önce özelliğinin özelliğini false olarak ayarlayarak ya da `RowUpdated` olay için bir olay işleyicisi oluşturarak ve öğesini <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> olarak <xref:System.Data.UpdateStatus.SkipCurrentRow>ayarlayarak koruyabilirsiniz. Daha fazla bilgi için bkz. [DataSet Içeriğini birleştirme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md) ve [DataAdapter olaylarını işleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde, `UpdateCommand` `DataAdapter` ' nin ve `Update` metodunu çağırarak, değiştirilmiş satırlara yapılan güncelleştirmelerin nasıl gerçekleştirileceği gösterilmektedir. Update ifadesinin WHERE yan tümcesinde belirtilen parametrenin `Original` değerini `SourceColumn`kullanacak şekilde ayarlandığından emin olun. Bu önemlidir çünkü `Current` değer değiştirilmiş olabilir ve veri kaynağındaki değerle eşleşmeyebilir. Değer, veri kaynağından `DataTable` doldurmak için kullanılan değerdir. `Original`  
  
 [!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]  
  
## <a name="autoincrement-columns"></a>AutoIncrement sütunları  
 Veri kaynağınızdaki tabloların sütunları otomatik olarak artırırsa, otomatik artış değerini bir saklı yordamın çıkış parametresi olarak döndürerek ve `DataSet` bunu bir tablodaki sütunla eşleştirerek, içindeki sütunları doldurabilirsiniz. bir saklı yordam veya SQL ifadesiyle döndürülen sonuç kümesinin ilk satırındaki otomatik artış değeri veya ek bir SELECT ifadesini yürütmek `RowUpdated` `DataAdapter` için öğesinin olayı kullanılarak. Daha fazla bilgi ve örnek için bkz. [kimlik veya OtomatikSayı değerlerini alma](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).  
  
## <a name="ordering-of-inserts-updates-and-deletes"></a>Ekleme, güncelleştirme ve silme sıralaması  
 Birçok durumda, üzerinde yapılan `DataSet` değişikliklerin veri kaynağına gönderildiği sıra önemlidir. Örneğin, var olan bir satır için birincil anahtar değeri güncellenir ve yeni birincil anahtar değeriyle yabancı anahtar olarak yeni bir satır eklendiyse, bu güncelleştirmeyi INSERT öncesinde işlemek önemlidir.  
  
 `Select` Yalnızca belirli `DataTable` `DataRow` bir ile satırlara başvuran bir dizi döndürmek için ' ın metodunu kullanabilirsiniz. `RowState` Daha sonra, `DataRow` `Update` değiştirilensatırlarıişlemekiçindöndürülendiziyi`DataAdapter` öğesinin yöntemine geçirebilirsiniz. Görüntülenecek satırların bir alt kümesini belirterek, ekleme, güncelleştirme ve silme işleme sırasını kontrol edebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Örneğin, aşağıdaki kod, tablonun silinen satırlarının önce işlenmesini, ardından güncelleştirilmiş satırları ve eklenen satırları sağlar.  
  
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
  
## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a>Verileri almak ve güncelleştirmek için bir DataAdapter kullanın  
 Verileri almak ve güncelleştirmek için bir DataAdapter kullanabilirsiniz.  
  
- Örnek, veritabanındaki verileri kopyalamak için DataAdapter. AcceptChangesDuringFill ' i kullanır. Özellik false olarak ayarlandıysa, tablo doldurulurken AcceptChanges çağrılmaz ve yeni eklenen satırlar eklenen satırlar olarak değerlendirilir. Bu nedenle örnek, yeni satırları veritabanına eklemek için bu satırları kullanır.  
  
- Örnekler, kaynak tablo ve DataTable arasındaki eşlemeyi tanımlamak için DataAdapter. TableMappings kullanır.  
  
- Örnek, bağdaştırıcının DataTable nesnesini DbDataReader 'dan nasıl doldurduğunu anlamak için DataAdapter. FillLoadOption kullanır. Bir DataTable oluşturduğunuzda, özelliği LoadOption. upsert veya LoadOption. PreserveChanges olarak ayarlayarak veritabanını yalnızca geçerli sürüme veya özgün sürüme yazabilirsiniz.  
  
- Örnek, toplu işlemleri gerçekleştirmek için DbDataAdapter. UpdateBatchSize kullanarak tabloyu da güncelleştirir.  
  
 Örneği derleyip çalıştırmadan önce örnek veritabanını oluşturmanız gerekir:  
  
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
  
 C#ve bu kod örneğine sahip Visual Basic projeler [Geliştirici kodu örnekleri](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D)üzerinde bulunabilir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Satır Durumları ve Satır Sürümleri](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)
- [AcceptChanges ve RejectChanges](../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- [DataSet İçeriklerini Birleştirme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)
- [Kimliği veya Otomatik Sayı Değerlerini Alma](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
