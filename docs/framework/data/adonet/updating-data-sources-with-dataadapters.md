---
title: Veri Kaynaklarını DataAdapters ile Güncelleştirme
description: DataAdapter 'ın Update yönteminin bir veri kümesinden gelen değişiklikleri ADO.NET uygulamalarında veri kaynağına nasıl çözümleyebileceğinizi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: e2348a3a89aa1c28856bfc21aaa25f2c8327aac7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286190"
---
# <a name="updating-data-sources-with-dataadapters"></a>Veri Kaynaklarını DataAdapters ile Güncelleştirme

' `Update` Nin yöntemi, <xref:System.Data.Common.DataAdapter> <xref:System.Data.DataSet> geri dönerek veri kaynağına yapılan değişiklikleri çözümlemek için çağırılır. Yöntemi gibi `Update` Yöntem, `Fill` bir örneği `DataSet` ve isteğe bağlı bir <xref:System.Data.DataTable> nesne ya da ad bağımsız değişken olarak alır `DataTable` . `DataSet`Örnek, `DataSet` yapılan değişiklikleri içeren, ve `DataTable` değişikliklerin alınacağı tabloyu tanımlar. Hayır `DataTable` belirtilirse, içindeki ilk, `DataTable` `DataSet` kullanılır.

Yöntemini çağırdığınızda, `Update` `DataAdapter` yapılan değişiklikleri analiz eder ve uygun komutu YÜRÜTÜR (INSERT, Update veya delete). `DataAdapter`Bir değişikliğe karşılaştığında, <xref:System.Data.DataRow> <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> değişikliği işlemek için, veya kullanır. Bu, tasarım zamanında komut sözdizimini belirterek ve mümkün olduğunda saklı yordamların kullanımı aracılığıyla ADO.NET uygulamanızın performansını en üst düzeye çıkarmanıza olanak sağlar. Çağrılmadan önce komutları açıkça ayarlamanız gerekir `Update` . `Update`Çağrılırsa ve belirli bir güncelleştirme için uygun komut yoksa (örneğin, `DeleteCommand` silinen satırlar için Hayır), bir özel durum oluşturulur.

> [!NOTE]
> Kullanarak veri düzenlemek veya silmek için SQL Server saklı yordamlar kullanıyorsanız `DataAdapter` , saklı yordam TANıMıNDA SET NOCOUNT kullanmayın. Bu, etkilenen satırların sayısının sıfır olmasına neden olur ve bu da `DataAdapter` eşzamanlılık çakışması olarak yorumladığı anlamına gelir. Bu olayda, bir <xref:System.Data.DBConcurrencyException> oluşturulur.

Komut parametreleri, bir SQL deyimin giriş ve çıkış değerlerini veya içindeki her bir değiştirilen satır için saklı yordamı belirtmek için kullanılabilir `DataSet` . Daha fazla bilgi için bkz. [DataAdapter Parameters](dataadapter-parameters.md).

> [!NOTE]
> İçindeki bir satırı silme ve satırı kaldırma arasındaki farkı anlamak önemlidir <xref:System.Data.DataTable> . `Remove`Veya `RemoveAt` yöntemini çağırdığınızda, satır hemen kaldırılır. Daha sonra `DataTable` veya ' a geçiş yaparsanız, arka uç veri kaynağındaki karşılık gelen satırlar etkilenmez `DataSet` `DataAdapter` `Update` . Yöntemini kullandığınızda, `Delete` satır içinde kalır `DataTable` ve silinmek üzere işaretlenir. Daha sonra `DataTable` veya ' e geçirirseniz `DataSet` `DataAdapter` `Update` , arka uç veri kaynağındaki karşılık gelen satır silinir.

`DataTable`Tek bir veritabanı tablosundan eşlemleriniz veya oluşturulursa,,, <xref:System.Data.Common.DbCommandBuilder> ve nesnelerini otomatik olarak oluşturmak için nesnesinden faydalanabilir `DeleteCommand` `InsertCommand` `UpdateCommand` `DataAdapter` . Daha fazla bilgi için bkz. [CommandBuilder 'lar Ile komut oluşturma](generating-commands-with-commandbuilders.md).

## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a>Değerleri bir veri kümesiyle eşlemek için UpdatedRowSource kullanma

Bir `DataTable` `DataAdapter` nesnenin özelliğini kullanarak, veri kaynağından döndürülen değerlerin bir ' ın update yöntemine yapılan çağrıya nasıl geri eşlendiğini denetleyebilirsiniz <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> <xref:System.Data.Common.DbCommand> . `UpdatedRowSource`Özelliğini <xref:System.Data.UpdateRowSource> sabit listesi değerlerinden birine ayarlayarak, komutlar tarafından döndürülen çıkış parametrelerinin `DataAdapter` yok sayıldığını veya içindeki değiştirilen satıra uygulanıp uygulanmadığını kontrol edebilirsiniz `DataSet` . Ayrıca, ilk döndürülen satırın (varsa) içindeki değiştirilen satıra uygulanıp uygulanmayacağını belirtebilirsiniz `DataTable` .

Aşağıdaki tabloda, numaralandırmanın farklı değerleri `UpdateRowSource` ve ile kullanılan bir komutun davranışlarını nasıl etkilediği açıklanmaktadır `DataAdapter` .

|UpdatedRowSource numaralandırması|Description|
|----------------------------------|-----------------|
|<xref:System.Data.UpdateRowSource.Both>|Döndürülen sonuç kümesinin çıkış parametreleri ve ilk satırı, içindeki değiştirilen satırla eşleştirilebilir `DataSet` .|
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Yalnızca döndürülen sonuç kümesinin ilk satırındaki veriler, içindeki değiştirilen satırla eşleştirilebilir `DataSet` .|
|<xref:System.Data.UpdateRowSource.None>|Döndürülen sonuç kümesinin herhangi bir çıkış parametresi veya satırı yok sayılır.|
|<xref:System.Data.UpdateRowSource.OutputParameters>|Yalnızca çıkış parametreleri içindeki değiştirilen satırla eşleştirilebilir `DataSet` .|

`Update`Yöntemi, değişikliklerinizi veri kaynağına geri çözümler; ancak diğer istemciler, son doldurduğunuz zamandan bu yana veri kaynağındaki verileri değiştirmiş olabilir `DataSet` . Güncel verilerle uygulamanızı yenilemek için `DataSet` `DataAdapter` ve `Fill` yöntemini kullanın. Tabloya yeni satırlar eklenecek ve güncel bilgiler mevcut satırlara dahil edilecek. `Fill`Yöntemi, yeni bir satırın eklenip eklenmeyeceğini veya içindeki satırların birincil anahtar değerleri `DataSet` ve tarafından döndürülen satırlarda incelenerek güncelleştirilip güncelleştirilmediğini belirler `SelectCommand` . Yöntemi, `Fill` `DataSet` tarafından döndürülen sonuçlardaki bir satırdaki birincil anahtar değeriyle eşleşen bir satır için birincil anahtar değeriyle karşılaştığında, var olan satırı `SelectCommand` tarafından döndürülen satırdaki bilgilerle güncelleştirir `SelectCommand` ve <xref:System.Data.DataRow.RowState%2A> var olan satırın değerini olarak ayarlar `Unchanged` . Tarafından döndürülen bir satır `SelectCommand` , içindeki satırların birincil anahtar değerleriyle eşleşmeyen bir birincil anahtar değerine sahipse `DataSet` , `Fill` yöntemi ' a sahip yeni bir satır ekler `RowState` `Unchanged` .

> [!NOTE]
> Eğer, `SelectCommand` BIR Dış birleştirmenin sonuçlarını döndürürse, `DataAdapter` `PrimaryKey` sonuç için bir değer ayarlayamaz `DataTable` . `PrimaryKey`Yinelenen satırların doğru bir şekilde çözümlendiğinden emin olmak için kendiniz tanımlamanız gerekir. Daha fazla bilgi için bkz. [birincil anahtarları tanımlama](./dataset-datatable-dataview/defining-primary-keys.md).

Yöntemi çağırırken oluşabilecek özel durumları işlemek için olayı, `Update` `RowUpdated` meydana gelen satır güncelleştirme hatalarına yanıt vermek için kullanabilirsiniz (bkz. [DataAdapter olaylarını işleme](handling-dataadapter-events.md)) veya `DataAdapter.ContinueUpdateOnError` `true` çağrılmadan önce olarak ayarlayabilir ve bu `Update` `RowError` güncelleştirme tamamlandığında belirli bir satırın özelliğinde depolanan hata bilgilerine yanıt verebilirsiniz (bkz. [satır hata bilgileri](./dataset-datatable-dataview/row-error-information.md)).

> [!NOTE]
> `AcceptChanges`,, Veya üzerinde çağırma, için `DataSet` `DataTable` `DataRow` tüm `Original` değerlerin `DataRow` üzerine yazılmasına neden olur `Current` `DataRow` . Satırı benzersiz olarak tanımlayan alan değerleri değiştirilmişse, değerler çağrıldıktan sonra, `AcceptChanges` `Original` veri kaynağındaki değerlerle artık eşleşmeyecektir. `AcceptChanges`, bir öğesinin Update metoduna yapılan çağrı sırasında her satır için otomatik olarak çağrılır `DataAdapter` . İlk değeri Update yöntemine yapılan bir çağrı sırasında `AcceptChangesDuringUpdate` , önce özelliğinin özelliğini false olarak ayarlayarak `DataAdapter` ya da olay için bir olay işleyicisi oluşturarak `RowUpdated` ve öğesini olarak ayarlayarak koruyabilirsiniz <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> <xref:System.Data.UpdateStatus.SkipCurrentRow> . Daha fazla bilgi için bkz. [DataSet Içeriğini birleştirme](./dataset-datatable-dataview/merging-dataset-contents.md) ve [DataAdapter olaylarını işleme](handling-dataadapter-events.md).

## <a name="example"></a>Örnek

Aşağıdaki örneklerde, `UpdateCommand` `DataAdapter` ' nin ve metodunu çağırarak, değiştirilmiş satırlara yapılan güncelleştirmelerin nasıl gerçekleştirileceği gösterilmektedir `Update` . UPDATE ifadesinin WHERE yan tümcesinde belirtilen parametrenin değerini kullanacak şekilde ayarlandığından emin olun `Original` `SourceColumn` . Bu önemlidir çünkü `Current` değer değiştirilmiş olabilir ve veri kaynağındaki değerle eşleşmeyebilir. `Original`Değer, veri kaynağından doldurmak için kullanılan değerdir `DataTable` .

[!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]

## <a name="autoincrement-columns"></a>AutoIncrement sütunları

Veri kaynağınızdaki tabloların sütunları otomatik olarak artırdıysanız, otomatik artış değerini, saklı bir yordamın `DataSet` çıkış parametresi olarak döndürerek ve bir tablodaki sütunla eşleyerek, bir saklı yordam veya SQL ifadesiyle döndürülen sonuç kümesinin ilk satırına otomatik artış değeri döndürerek ya da `RowUpdated` `DataAdapter` ek bir SELECT ifadesini yürütmek için öğesinin olayını kullanarak, içindeki sütunları doldurabilirsiniz. Daha fazla bilgi ve örnek için bkz. [kimlik veya OtomatikSayı değerlerini alma](retrieving-identity-or-autonumber-values.md).

## <a name="ordering-of-inserts-updates-and-deletes"></a>Ekleme, güncelleştirme ve silme sıralaması

Birçok durumda, üzerinde yapılan değişikliklerin `DataSet` veri kaynağına gönderildiği sıra önemlidir. Örneğin, var olan bir satır için birincil anahtar değeri güncellenir ve yeni birincil anahtar değeriyle yabancı anahtar olarak yeni bir satır eklendiyse, bu güncelleştirmeyi INSERT öncesinde işlemek önemlidir.

`Select` `DataTable` `DataRow` Yalnızca belirli bir ile satırlara başvuran bir dizi döndürmek için ' ın metodunu kullanabilirsiniz `RowState` . Daha sonra `DataRow` `Update` , `DataAdapter` değiştirilen satırları işlemek için döndürülen diziyi öğesinin yöntemine geçirebilirsiniz. Görüntülenecek satırların bir alt kümesini belirterek, ekleme, güncelleştirme ve silme işleme sırasını kontrol edebilirsiniz.

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

C# ve bu kod örneğiyle Visual Basic projeler, [Geliştirici kod örneklerinde](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D)bulunabilir.

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

- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [Satır Durumları ve Satır Sürümleri](./dataset-datatable-dataview/row-states-and-row-versions.md)
- [AcceptChanges ve RejectChanges](./dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- [DataSet İçeriklerini Birleştirme](./dataset-datatable-dataview/merging-dataset-contents.md)
- [Kimliği veya Otomatik Sayı Değerlerini Alma](retrieving-identity-or-autonumber-values.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
