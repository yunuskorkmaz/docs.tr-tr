---
title: Veri kaynaklarını DataAdapter ile güncelleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: 4a6e22352a309f9d624c6922abc531cb31a5baf1
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736695"
---
# <a name="updating-data-sources-with-dataadapters"></a>Veri kaynaklarını DataAdapter ile güncelleştirme

@No__t-1 ' in `Update` yöntemi <xref:System.Data.DataSet> ' den veri kaynağına geri yapılan değişiklikleri çözümlemek için çağrılır. @No__t-1 yöntemi gibi `Update` yöntemi, bir `DataSet` örneği ve isteğe bağlı bir <xref:System.Data.DataTable> nesnesi veya `DataTable` adı olarak, bağımsız değişken alır. @No__t-0 örneği, yapılan değişiklikleri içeren `DataSet` ' dir ve `DataTable` ' den değişikliklerin alınacağı tabloyu tanımlar. @No__t-0 belirtilmemişse, `DataSet` ' deki ilk `DataTable` kullanılır.

@No__t-0 yöntemini çağırdığınızda, `DataAdapter` yapılan değişiklikleri analiz eder ve uygun komutu yürütür (INSERT, UPDATE veya DELETE). @No__t-0, bir <xref:System.Data.DataRow> değişikliği karşılaştığında, değişikliği işlemek için <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> veya <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> kullanır. Bu, tasarım zamanında komut sözdizimini belirterek ve mümkün olduğunda saklı yordamların kullanımı aracılığıyla ADO.NET uygulamanızın performansını en üst düzeye çıkarmanıza olanak sağlar. @No__t-0 çağrılmadan önce komutları açıkça ayarlamanız gerekir. @No__t-0 çağrılırsa ve belirli bir güncelleştirme için uygun komut yoksa (örneğin, silinen satırlar için `DeleteCommand`), bir özel durum oluşturulur.

> [!NOTE]
> @No__t-0 kullanarak verileri düzenlemek veya silmek için SQL Server saklı yordamlar kullanıyorsanız, saklı yordam tanımında SET NOCOUNT kullanmayın. Bu, etkilenen satırların sayısının sıfır olmasına neden olur. Bu, `DataAdapter` ' ı eşzamanlılık çakışması olarak yorumlar. Bu olayda <xref:System.Data.DBConcurrencyException> oluşturulur.

Komut parametreleri, bir SQL deyimin giriş ve çıkış değerlerini veya `DataSet` ' daki her değiştirilmiş satır için saklı yordamı belirtmek üzere kullanılabilir. Daha fazla bilgi için bkz. [DataAdapter Parameters](dataadapter-parameters.md).

> [!NOTE]
> @No__t-0 içindeki bir satırı silme ve satırı kaldırma arasındaki farkı anlamak önemlidir. @No__t-0 veya `RemoveAt` yöntemini çağırdığınızda, satır hemen kaldırılır. Daha sonra `DataTable` veya `DataSet` ' i @no__t 2 ' ye geçirirseniz ve `Update` ' i çağırdığınızda, arka uç veri kaynağındaki karşılık gelen tüm satırlar etkilenmeyecektir. @No__t-0 yöntemini kullandığınızda, satır `DataTable` ' de kalır ve silinmek üzere işaretlenir. Daha sonra `DataTable` veya `DataSet` ' i `DataAdapter` ' ye geçirirseniz ve `Update` ' i çağırırsanız, arka uç veri kaynağındaki karşılık gelen satır silinir.

@No__t-0 ' ı tek bir veritabanı tablosundan eşlenir veya oluşturulursa, `DataAdapter` ' i `DeleteCommand`, `InsertCommand` ve `UpdateCommand` nesnelerini otomatik olarak oluşturmak için <xref:System.Data.Common.DbCommandBuilder> nesnesinden faydalanabilirsiniz. Daha fazla bilgi için bkz. [CommandBuilder 'lar Ile komut oluşturma](generating-commands-with-commandbuilders.md).

## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a>Değerleri bir veri kümesiyle eşlemek için UpdatedRowSource kullanma

Bir <xref:System.Data.Common.DbCommand> nesnesinin <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> özelliğini kullanarak, veri kaynağından döndürülen değerlerin bir `DataAdapter` ' in Update yöntemine yapılan çağrıdan @no__t nasıl geri eşlendiğini denetleyebilirsiniz. @No__t-0 özelliğini <xref:System.Data.UpdateRowSource> sabit listesi değerlerinden birine ayarlayarak, `DataAdapter` komutlarıyla döndürülen çıkış parametrelerinin yok sayılıp `DataSet` ' teki değiştirilen satıra uygulanıp uygulanmadığını kontrol edebilirsiniz. Ayrıca, ilk döndürülen satırın (varsa) `DataTable` ' daki değiştirilen satıra uygulanıp uygulanmadığını belirtebilirsiniz.

Aşağıdaki tabloda `UpdateRowSource` numaralandırmanın farklı değerleri ve `DataAdapter` ile kullanılan bir komutun davranışını nasıl etkilediği açıklanmaktadır.

|UpdatedRowSource numaralandırması|Açıklama|
|----------------------------------|-----------------|
|<xref:System.Data.UpdateRowSource.Both>|Döndürülen sonuç kümesinin hem çıkış parametreleri hem de ilk satırı `DataSet` ' daki değiştirilen satırla eşleştirilebilir.|
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Yalnızca döndürülen sonuç kümesinin ilk satırındaki veriler `DataSet` ' daki değiştirilen satıra eşlenebilir.|
|<xref:System.Data.UpdateRowSource.None>|Döndürülen sonuç kümesinin herhangi bir çıkış parametresi veya satırı yok sayılır.|
|<xref:System.Data.UpdateRowSource.OutputParameters>|Yalnızca çıkış parametreleri `DataSet` ' daki değiştirilen satıra eşlenebilir.|

@No__t-0 yöntemi, değişikliklerinizi veri kaynağına geri çözümler; Ancak, `DataSet` ' i en son doldurduktan sonra diğer istemciler veri kaynağındaki verileri değiştirmiş olabilir. @No__t-0 ' ı geçerli verilerle yenilemek için `DataAdapter` ve `Fill` metodunu kullanın. Tabloya yeni satırlar eklenecek ve güncel bilgiler mevcut satırlara dahil edilecek. @No__t-0 yöntemi, yeni bir satırın eklenip eklenmeyeceğini veya var olan bir satırın, `DataSet` ' deki satırların birincil anahtar değerleri ve `SelectCommand` tarafından döndürülen satırlarda incelenip güncelleştirileceğini belirler. @No__t-0 yöntemi, `SelectCommand` tarafından döndürülen sonuçlardaki bir satırdaki birincil anahtar değeriyle eşleşen bir @no__t satır için birincil anahtar değeriyle karşılaştığında, `SelectCommand` tarafından döndürülen satırdaki bilgilerle mevcut satırı güncelleştirir ve <xref:System.Data.DataRow.RowState%2A> o değerini ayarlar. mevcut satırı `Unchanged` ' e kadar yapın. @No__t-0 tarafından döndürülen bir satır, `DataSet` ' deki satırların birincil anahtar değerleriyle eşleşmeyen bir birincil anahtar değerine sahipse, `Fill` yöntemi `RowState` ' ü `Unchanged` ile yeni bir satır ekler.

> [!NOTE]
> @No__t-0 bir dış BIRLEŞTIRMENIN sonuçlarını döndürürse, `DataAdapter`, elde edilen `DataTable` için bir `PrimaryKey` değeri ayarlayamaz. Yinelenen satırların doğru bir şekilde çözümlendiğinden emin olmak için `PrimaryKey` tanımlamanız gerekir. Daha fazla bilgi için bkz. [birincil anahtarları tanımlama](./dataset-datatable-dataview/defining-primary-keys.md).

@No__t-0 yöntemini çağırırken oluşabilecek özel durumları işlemek için, `RowUpdated` olayını kullanarak, ortaya çıkan satır güncelleştirme hatalarına yanıt verebilir (bkz. [DataAdapter olaylarını işleme](handling-dataadapter-events.md)) veya `Update` ' i çağırmadan önce `DataAdapter.ContinueUpdateOnError` ' ü `true` ' e ayarlayabilirsiniz ve Güncelleştirme tamamlandığında belirli bir satırın `RowError` özelliğinde saklanan hata bilgileri (bkz. [satır hatası bilgileri](./dataset-datatable-dataview/row-error-information.md)).

> [!NOTE]
> @No__t-1, `DataTable` veya `DataRow` `AcceptChanges` ' ı çağırmak, `DataRow` ' i y-5 değerlerinin üzerine yazılmasına neden olur `DataRow` için `Current` değerleri. Satırı benzersiz olarak tanımlayan alan değerleri değiştirilmişse, @no__t çağrıldıktan sonra, `Original` değerleri artık veri kaynağındaki değerlerle eşleşmeyecektir. `AcceptChanges`, `DataAdapter` ' in Update metoduna yapılan çağrı sırasında her satır için otomatik olarak çağrılır. Önce `DataAdapter` ' in `AcceptChangesDuringUpdate` özelliğini false ' a ayarlayarak veya `RowUpdated` olayı için bir olay işleyicisi oluşturarak ve <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> ' i <xref:System.Data.UpdateStatus.SkipCurrentRow> ' e ayarlayarak Update yöntemine yapılan çağrı sırasında özgün değerleri koruyabilirsiniz. Daha fazla bilgi için bkz. [DataSet Içeriğini birleştirme](./dataset-datatable-dataview/merging-dataset-contents.md) ve [DataAdapter olaylarını işleme](handling-dataadapter-events.md).

## <a name="example"></a>Örnek

Aşağıdaki örneklerde, bir `DataAdapter` ' in `UpdateCommand` ' ını açıkça ayarlayıp `Update` metodunu çağırarak, değiştirilen satırlara yapılan güncelleştirmelerin nasıl gerçekleştirileceği gösterilmektedir. UPDATE ifadesinin WHERE yan tümcesinde belirtilen parametrenin, `SourceColumn` ' in `Original` değerini kullanacak şekilde ayarlandığını unutmayın. Bu önemlidir çünkü `Current` değeri değiştirilmiş olabilir ve veri kaynağındaki değerle eşleşmeyebilir. @No__t-0 değeri, veri kaynağından `DataTable` doldurmak için kullanılan değerdir.

[!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]

## <a name="autoincrement-columns"></a>AutoIncrement sütunları

Veri kaynağınızdaki tabloların sütunları otomatik olarak artırdığında, bir saklı yordamın çıkış parametresi olarak otomatik artım değerini döndürerek ve bunu bir tablodaki sütunla eşleştirerek, ' ı @no__t sütunları doldurabilirsiniz. bir saklı yordam veya SQL ifadesiyle döndürülen sonuç kümesinin ilk satırındaki veya ek bir SELECT ifadesini yürütmek için `DataAdapter` ' nin `RowUpdated` olayı kullanılarak otomatik artış değeri. Daha fazla bilgi ve örnek için bkz. [kimlik veya OtomatikSayı değerlerini alma](retrieving-identity-or-autonumber-values.md).

## <a name="ordering-of-inserts-updates-and-deletes"></a>Ekleme, güncelleştirme ve silme sıralaması

Birçok durumda, `DataSet` üzerinden yapılan değişikliklerin veri kaynağına gönderildiği sıra önemlidir. Örneğin, var olan bir satır için birincil anahtar değeri güncellenir ve yeni birincil anahtar değeriyle yabancı anahtar olarak yeni bir satır eklendiyse, bu güncelleştirmeyi INSERT öncesinde işlemek önemlidir.

Yalnızca belirli bir `RowState` içeren satırlara başvuran bir `DataRow` dizisi döndürmek için `DataTable` ' in `Select` yöntemini kullanabilirsiniz. Ardından değiştirilen satırları işlemek için döndürülen `DataRow` dizisini `DataAdapter` `Update` yöntemine geçirebilirsiniz. Görüntülenecek satırların bir alt kümesini belirterek, ekleme, güncelleştirme ve silme işleme sırasını kontrol edebilirsiniz.

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
adapter.Update(table.Select(Nothing, Nothing, _
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

- [DataAdapter ve DataReaders](dataadapters-and-datareaders.md)
- [Satır durumları ve satır sürümleri](./dataset-datatable-dataview/row-states-and-row-versions.md)
- [AcceptChanges ve RejectChanges](./dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- [Veri kümesi Içeriğini birleştirme](./dataset-datatable-dataview/merging-dataset-contents.md)
- [Kimlik veya OtomatikSayı değerlerini alma](retrieving-identity-or-autonumber-values.md)
- [ADO.NET genel bakış](ado-net-overview.md)
