---
title: Kimliği veya Otomatik Sayı Değerlerini Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6b7f9cb-81be-44e1-bb94-56137954876d
ms.openlocfilehash: 1387dad1f588770384422bf579ed547271b30c0a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794554"
---
# <a name="retrieving-identity-or-autonumber-values"></a>Kimliği veya Otomatik Sayı Değerlerini Alma

İlişkisel veritabanındaki birincil anahtar, her zaman benzersiz değerler içeren bir sütun veya sütun birleşimidir. Birincil anahtar değerini bilmek, onu içeren satırı bulmanıza olanak sağlar. SQL Server, Oracle ve Microsoft Access/Jet gibi ilişkisel veritabanı motorları, birincil anahtarlar olarak belirlenebilir sütunları otomatik olarak arttırın oluşturulmasını destekler. Bu değerler, bir tabloya satırlar eklendikçe sunucu tarafından oluşturulur. SQL Server bir sütunun Identity özelliğini ayarlarsınız, Oracle 'da bir sıra oluşturur ve Microsoft Access 'te bir OtomatikSayı sütunu oluşturursunuz.

<xref:System.Data.DataColumn> Ayrıca ,<xref:System.Data.DataColumn.AutoIncrement%2A> özelliği true olarak ayarlayarak değerleri otomatik olarak arttırarak oluşturmak için de kullanılabilir. Bununla birlikte, birden fazla istemci uygulaması bağımsız olarak değerleri otomatik olarak arttırdığınızda <xref:System.Data.DataTable>, tek bir ' ın ayrı örneklerinde yinelenen değerlerle karşılaşabilirsiniz. Sunucunun otomatik olarak artırılmaları, her bir kullanıcının her ekli satır için oluşturulan değeri almasına izin vererek olası çakışmaları ortadan kaldırır.

`Update` Bir`DataAdapter`yöntemi çağrısı sırasında, veritabanı, ADO.net uygulamanıza çıkış parametreleri olarak veya INSERT ifadesiyle aynı toplu işte yürütülen bir SELECT ifadesinin sonuç kümesinin ilk döndürülen kaydı olarak geri veri gönderebilir. ADO.NET bu değerleri alabilir ve güncelleştirilecek ilgili sütunları <xref:System.Data.DataRow> güncelleştirebilir.

Microsoft Access Jet veritabanı altyapısı gibi bazı veritabanı motorları, çıkış parametrelerini desteklemez ve tek bir toplu işte birden çok deyimi işleyemez. Jet veritabanı altyapısı ile çalışırken, bir olay işleyicisinde `RowUpdated` `DataAdapter`otomatik olarak bir SELECT komutu yürüterek ekli bir satır için oluşturulan yeni OtomatikSayı değerini elde edebilirsiniz.

> [!NOTE]
> Otomatik artan değer kullanmanın bir alternatifi, her yeni satır eklendiği sırada <xref:System.Guid.NewGuid%2A> sunucuya kopyalanabilen <xref:System.Guid> istemci bilgisayarda bir GUID veya genel benzersiz tanımlayıcı oluşturmak için bir nesnenin yöntemini kullanmaktır. Yöntemi `NewGuid` , hiçbir değer yinelenmeyecek yüksek bir olasılık sağlayan bir algoritma kullanılarak oluşturulan bir 16 baytlık ikili değer oluşturur. Bir SQL Server veritabanında GUID, SQL Server Transact-SQL `uniqueidentifier` `NEWID()` işlevi kullanılarak otomatik olarak oluşturabileceğiniz bir sütunda depolanır. GUID 'in birincil anahtar olarak kullanılması performansı olumsuz etkileyebilir. SQL Server, genel olarak benzersiz `NEWSEQUENTIALID()` olan ancak dizine daha verimli bir şekilde dizinlenebilir bir ardışık GUID üreten, işlevi için destek sağlar.

## <a name="retrieving-sql-server-identity-column-values"></a>SQL Server Identity sütunu değerlerini alma

Microsoft SQL Server ile çalışırken, ekli bir satır için kimlik değerini döndürmek üzere çıkış parametresiyle bir saklı yordam oluşturabilirsiniz. Aşağıdaki tabloda, kimlik sütunu değerlerini almak için kullanılabilecek SQL Server ' deki üç Transact-SQL işlevleri açıklanmaktadır.

|İşlev|Açıklama|
|--------------|-----------------|
|SCOPE_IDENTITY|Geçerli yürütme kapsamındaki son kimlik değerini döndürür. SCOPE_IDENTITY çoğu senaryo için önerilir.|
|@@IDENTITY|Geçerli oturumdaki herhangi bir tabloda oluşturulan son kimlik değerini içerir. @@IDENTITY tetikleyicilerden etkilenebilir ve bekleeceğiniz kimlik değerini döndüremeyebilir.|
|IDENT_CURRENT|Herhangi bir oturumdaki ve herhangi bir kapsamdaki belirli bir tablo için oluşturulan son kimlik değerini döndürür.|

 Aşağıdaki saklı yordamda, **Kategoriler** tablosuna bir satır ekleme ve Transact-SQL SCOPE_IDENTITY () işlevi tarafından oluşturulan yeni kimlik değerini döndürmek için bir çıkış parametresi kullanma gösterilmektedir.

```sql
CREATE PROCEDURE dbo.InsertCategory
  @CategoryName nvarchar(15),
  @Identity int OUT
AS
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)
SET @Identity = SCOPE_IDENTITY()
```

Saklı yordam daha sonra bir <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter> nesnenin kaynağı olarak belirtilebilir. <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> Öğesinin özelliği olarak ayarlanmalıdır<xref:System.Data.CommandType.StoredProcedure>. <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> Kimlik çıktısı, ' <xref:System.Data.SqlClient.SqlParameter> <xref:System.Data.ParameterDirection> a sahip olan bir oluşturarak alınır. <xref:System.Data.ParameterDirection.Output> `UpdateRowSource.Both` <xref:System.Data.SqlClient.SqlCommand.UpdatedRowSource%2A> `UpdateRowSource.OutputParameters` İşlendiğinde, otomatik olarak artan kimlik değeri döndürülür ve INSERT komutunun özelliğini veya olarak ayarlarsanız geçerli satırın CategoryID sütununa konur. `InsertCommand`

INSERT komutunuz hem bir INSERT ifadesini hem de yeni kimlik değerini döndüren bir SELECT ifadesini içeren bir Batch çalıştırırsa, INSERT komutunun `UpdatedRowSource` özelliğini olarak `UpdateRowSource.FirstReturnedRecord`ayarlayarak yeni değeri alabilirsiniz.

[!code-csharp[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/VB/source.vb#1)]

## <a name="merging-new-identity-values"></a>Yeni kimlik değerleri birleştiriliyor

Yaygın bir senaryo, yalnızca değiştirilen satırları `GetChanges` içeren bir kopya `DataTable` oluşturmak ve a `Update` `DataAdapter`yöntemini çağırırken yeni kopyayı kullanmak için bir ' ın yöntemini çağırmaktan oluşur. Bu özellikle, değiştirilen satırları güncelleştirmeyi gerçekleştiren ayrı bir bileşene sıralama yapmanız gerektiğinde faydalıdır. Güncelleştirme sonrasında, kopya daha sonra orijinalde `DataTable`birleştirilmek zorunda olan yeni kimlik değerleri içerebilir. Yeni kimlik değerlerinin, `DataTable`içindeki özgün değerlerden farklı olması olasıdır. Birleştirme işlemini gerçekleştirmek için, yeni kimlik değerlerini içeren yeni satırları eklemek yerine, özgün `DataTable`tablodaki AutoIncrement sütunlarının özgün değerleri korunacak ve bu verileri güncelleştirmek gerekir . Bununla birlikte, `Update` varsayılan olarak, bir `DataAdapter`öğesinin yöntemine yapılan çağrıdan sonra bu özgün değerler kaybolur, çünkü `AcceptChanges` her biri `DataRow`için örtülü olarak çağırılır.

Bir `DataRow` `DataColumn` güncelleştirme`DataAdapter` sırasında içindeki içindeki özgün değerlerini korumanın iki yolu vardır:

- Özgün değerleri korumak için ilk yöntem, `AcceptChangesDuringUpdate` `DataAdapter` öğesinin özelliğini olarak `false`ayarlandır. Bu, `DataRow` `DataTable` güncelleştirilmekte olan her durumda etkiler. Daha fazla bilgi ve bir kod örneği için bkz <xref:System.Data.Common.DataAdapter.AcceptChangesDuringUpdate%2A>.

- İkinci yöntem `RowUpdated` , öğesini <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> olarak `DataAdapter` ayarlamakiçinöğesininolayişleyicisinekodyazmaktır.<xref:System.Data.UpdateStatus.SkipCurrentRow> Güncellenir `DataRow` , ancak her `DataColumn` birinin özgün değeri korunur. Bu yöntem, bazı satırlar için özgün değerleri koruyabilmenizi sağlar ve diğerleri için değildir. Örneğin, kodunuz ilk olarak, eklenen satırlar için özgün değerleri koruyabilir ve önce öğesini denetleyerek ve yalnızca <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A> içeren `Insert` `StatementType` satırları için olarak <xref:System.Data.UpdateStatus.SkipCurrentRow> ayarlayarak <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> , düzenlenebilir veya silinmiş satırlar için değil.

Bir `DataRow` güncelleştirme`DataAdapter` sırasında özgün değerleri korumak için bu yöntemlerden herhangi biri kullanıldığında ADO.net, geçerli değerlerini çıkış parametrelerine veya ilk tarafından döndürülen yeni değerlere ayarlamak için bir dizi eylem gerçekleştirir `DataRow` . sonuç kümesinin döndürülen satırı, hala her `DataColumn`birinde özgün değeri korurken. İlk olarak `AcceptChanges` , `DataRow` öğesinin yöntemi geçerli değerleri özgün değerler olarak korumak için çağrılır ve sonra yeni değerler atanır. <xref:System.Data.DataRow.RowState%2A> Özelliği olarak `DataRows` ayarlanmış<xref:System.Data.DataRowState.Added>olan bu eylemlerin, <xref:System.Data.DataRowState.Modified>özelliği olarak ayarlanmış olacak şekilde, beklenmeyen bir durum olabilir. `RowState`

Komut sonuçlarının her <xref:System.Data.DataRow> güncelleştirilme için nasıl uygulandığı, her <xref:System.Data.Common.DbCommand>birinin <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> özelliği tarafından belirlenir. Bu özellik, `UpdateRowSource` Numaralandırmadaki bir değere ayarlanır.

Aşağıdaki tabloda, `UpdateRowSource` numaralandırma değerlerinin güncelleştirilmiş satırların <xref:System.Data.DataRow.RowState%2A> özelliğini nasıl etkilediği açıklanmaktadır.

|Üye adı|Açıklama|
|-----------------|-----------------|
|<xref:System.Data.UpdateRowSource.Both>|`AcceptChanges`çağrılır ve her iki çıkış parametresi değeri ve/veya döndürülen sonuç kümesinin ilk satırındaki değerler `DataRow` güncellenmek üzere yerleştirilir. Uygulanacak `RowState` değer yoksa, <xref:System.Data.DataRowState.Unchanged>olacaktır.|
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|`AcceptChanges` Bir satır döndürülürse, çağırılır ve satır `DataTable`öğesinde değiştirilen satırla eşleştirilir, olarak ayarlanıyor `RowState` `Modified`. Hiçbir satır döndürülmezse, `AcceptChanges` çağrılmaz `RowState` ve kalır `Added`.|
|<xref:System.Data.UpdateRowSource.None>|Döndürülen tüm parametreler veya satırlar yok sayılır. ' A yönelik `AcceptChanges` bir çağrı yoktur ve `Added`kalır. `RowState`|
|<xref:System.Data.UpdateRowSource.OutputParameters>|`AcceptChanges`çağrılır ve tüm çıktı parametreleri öğesinde `DataTable`değiştirilen satırla eşlenir ve ' ı ' olarak `RowState` ayarlar `Modified`. Çıkış parametresi `RowState` yoksa, `Unchanged`olacaktır.|

### <a name="example"></a>Örnek

Bu örnek, bir `DataTable` öğesinden değiştirilen satırların ayıklanışını ve bir veri kaynağını güncelleştirmek ve yeni bir kimlik sütun değeri almak için bir <xref:System.Data.SqlClient.SqlDataAdapter> kullanarak öğesini gösterir. İki Transact-SQL deyimini yürütür;ilkiINSERTdeyimidirveikincisikimlikdeğerinialmakiçinSCOPE_IDENTITYişlevinikullananbirSELECTdeyimidir.<xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>

```sql
INSERT INTO dbo.Shippers (CompanyName)
VALUES (@CompanyName);
SELECT ShipperID, CompanyName FROM dbo.Shippers
WHERE ShipperID = SCOPE_IDENTITY();
```

`UpdateRowSource.FirstReturnedRow` <xref:System.Data.MissingSchemaAction> INSERT komutunun `MissingSchemaAction.AddWithKey`özelliği olarak ayarlanır`DataAdapter` ve öğesinin özelliği olarak ayarlanır. `UpdatedRowSource` , `DataTable` Doldurulur ve kod `DataTable`öğesine yeni bir satır ekler. Değiştirilen satırlar daha sonra ' a geçirilen `DataTable` `DataAdapter`yeni bir ' a ayıklanır ve ardından sunucuyu günceller.

[!code-csharp[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#1)]

Olay işleyicisi, satırın bir <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A> INSERT olup olmadığını belirlemede öğesini denetler <xref:System.Data.SqlClient.SqlRowUpdatedEventArgs>. `OnRowUpdated` Eğer ise, <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> özelliği olarak <xref:System.Data.UpdateStatus.SkipCurrentRow>ayarlanır. Satır güncellenir, ancak satırdaki özgün değerler korunur. Yordamın ana gövdesinde, <xref:System.Data.DataSet.Merge%2A> yöntemi yeni kimlik değerini orijinalde `DataTable`birleştirmek için çağrılır ve son `AcceptChanges` olarak çağırılır.

[!code-csharp[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#2)]
[!code-vb[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#2)]

## <a name="retrieving-microsoft-access-autonumber-values"></a>Microsoft Access otomatik sayı değerleri alınıyor

Bu bölüm, Jet 4,0 veritabanından değerlerin nasıl alınacağını `Autonumber` gösteren bir örnek içerir. Jet veritabanı altyapısı, bir toplu işte birden çok deyimin yürütülmesini veya çıkış parametrelerinin kullanımını desteklemez, bu nedenle, ekli satıra atanan yeni `Autonumber` değeri döndürmek için bu tekniklerden birini kullanmak mümkün değildir. Ancak, yeni `RowUpdated` @IDENTITY değerialmakiçinayrıbirSELECT@ifadesiniyürütenolay`Autonumber` işleyicisine kod ekleyebilirsiniz.

### <a name="example"></a>Örnek

Kullanılarak `MissingSchemaAction.AddWithKey`şema bilgileri eklemek yerine, bu örnek, öğesini doldurmanız `DataTable` <xref:System.Data.OleDb.OleDbDataAdapter> için `DataTable`çağrılmadan önce doğru şemayla bir yapılandırır. Bu durumda, **CategoryID** sütunu her bir yerleştirilen satıra atanan değeri sıfıra, 0 <xref:System.Data.DataColumn.AutoIncrement%2A> ' a ve <xref:System.Data.DataColumn.AutoIncrementStep%2A> -1 ' e ayarlayarak `true` <xref:System.Data.DataColumn.AutoIncrementSeed%2A> , sıfıra başlayarak azaltmak üzere yapılandırılır. Kod daha sonra iki yeni satır ekler ve değiştirilen `GetChanges` satırları `Update` yöntemine geçirilen yeni `DataTable` bir satıra eklemek için kullanır.

[!code-csharp[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#1)]
[!code-vb[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#1)]

Olay işleyicisi `Update` , öğesinin`OleDbDataAdapter`ifadesiyle aynı açık <xref:System.Data.OleDb.OleDbConnection>öğesinikullanır. `RowUpdated` Ekli satırların öğesini `StatementType` denetler <xref:System.Data.OleDb.OleDbRowUpdatedEventArgs> . Her ekli satır için, bağlantı <xref:System.Data.OleDb.OleDbCommand> üzerinde select @@IDENTITY ifadesini yürütmek üzere yeni bir oluşturulur `DataRow`. Bu, öğesinin **CategoryID** sütununa `Autonumber` yerleştirilen yeni değeri döndürür. Özelliği daha sonra gizli çağrısını `AcceptChanges`bastırmak `UpdateStatus.SkipCurrentRow` için olarak ayarlanır. `Status` Yordamın ana gövdesinde, `Merge` yöntemi iki `DataTable` nesneyi birleştirmek için çağrılır ve son olarak `AcceptChanges` çağırılır.

[!code-csharp[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#2)]
[!code-vb[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#2)]

### <a name="retrieving-identity-values"></a>Kimlik değerlerini alma

Sütunda değerlerin benzersiz olması gerektiğinde genellikle sütunu kimlik olarak ayarlayacağız. Ve bazen de yeni verilerin kimlik değerine ihtiyacımız var. Bu örnek, kimlik değerlerinin nasıl alınacağını gösterir:

- Veri eklemek ve bir kimlik değeri döndürmek için bir saklı yordam oluşturur.

- Yeni verileri eklemek ve sonucu göstermek için bir komut yürütür.

- Yeni <xref:System.Data.SqlClient.SqlDataAdapter> verileri eklemek ve sonucu göstermek için kullanır.

Örneği derleyip çalıştırmadan önce, örnek veritabanını aşağıdaki betiği kullanarak oluşturmanız gerekir:

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
CREATE procedure [dbo].[CourseExtInfo] @CourseId int
as
select c.CourseID,c.Title,c.Credits,d.Name as DepartmentName
from Course as c left outer join Department as d on c.DepartmentID=d.DepartmentID
where c.CourseID=@CourseId

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
create procedure [dbo].[DepartmentInfo] @DepartmentId int,@CourseCount int output
as
select @CourseCount=Count(c.CourseID)
from course as c
where c.DepartmentID=@DepartmentId

select d.DepartmentID,d.Name,d.Budget,d.StartDate,d.Administrator
from Department as d
where d.DepartmentID=@DepartmentId

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
Create PROCEDURE [dbo].[GetDepartmentsOfSpecifiedYear]
@Year int,@BudgetSum money output
AS
BEGIN
        SELECT @BudgetSum=SUM([Budget])
  FROM [MySchool].[dbo].[Department]
  Where YEAR([StartDate])=@Year

SELECT [DepartmentID]
      ,[Name]
      ,[Budget]
      ,[StartDate]
      ,[Administrator]
  FROM [MySchool].[dbo].[Department]
  Where YEAR([StartDate])=@Year

END
GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE PROCEDURE [dbo].[GradeOfStudent]
-- Add the parameters for the stored procedure here
@CourseTitle nvarchar(100),@FirstName nvarchar(50),
@LastName nvarchar(50),@Grade decimal(3,2) output
AS
BEGIN
select @Grade=Max(Grade)
from [dbo].[StudentGrade] as s join [dbo].[Course] as c on
s.CourseID=c.CourseID join [dbo].[Person] as p on s.StudentID=p.PersonID
where c.Title=@CourseTitle and p.FirstName=@FirstName
and p.LastName= @LastName
END
GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE PROCEDURE [dbo].[InsertPerson]
-- Add the parameters for the stored procedure here
@FirstName nvarchar(50),@LastName nvarchar(50),
@PersonID int output
AS
BEGIN
    insert [dbo].[Person](LastName,FirstName) Values(@LastName,@FirstName)

    set @PersonID=SCOPE_IDENTITY()
END
Go

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

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
SET ANSI_PADDING ON
GO
CREATE TABLE [dbo].[Person]([PersonID] [int] IDENTITY(1,1) NOT NULL,
[LastName] [nvarchar](50) NOT NULL,
[FirstName] [nvarchar](50) NOT NULL,
[HireDate] [datetime] NULL,
[EnrollmentDate] [datetime] NULL,
[Picture] [varbinary](max) NULL,
 CONSTRAINT [PK_School.Student] PRIMARY KEY CLUSTERED
(
[PersonID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[StudentGrade]([EnrollmentID] [int] IDENTITY(1,1) NOT NULL,
[CourseID] [nvarchar](10) NOT NULL,
[StudentID] [int] NOT NULL,
[Grade] [decimal](3, 2) NOT NULL,
 CONSTRAINT [PK_StudentGrade] PRIMARY KEY CLUSTERED
(
[EnrollmentID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
create view [dbo].[EnglishCourse]
as
select c.CourseID,c.Title,c.Credits,c.DepartmentID
from Course as c join Department as d on c.DepartmentID=d.DepartmentID
where d.Name=N'English'

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
SET IDENTITY_INSERT [dbo].[Person] ON

INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (1, N'Hu', N'Nan', NULL, CAST(0x0000A0BF00000000 AS DateTime))
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (2, N'Norman', N'Laura', NULL, CAST(0x0000A0BF00000000 AS DateTime))
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (3, N'Olivotto', N'Nino', NULL, CAST(0x0000A0BF00000000 AS DateTime))
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (4, N'Anand', N'Arturo', NULL, CAST(0x0000A0BF00000000 AS DateTime))
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (5, N'Jai', N'Damien', NULL, CAST(0x0000A0BF00000000 AS DateTime))
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (6, N'Holt', N'Roger', CAST(0x000097F100000000 AS DateTime), NULL)
INSERT [dbo].[Person] ([PersonID], [LastName], [FirstName], [HireDate], [EnrollmentDate]) VALUES (7, N'Martin', N'Randall', CAST(0x00008B1A00000000 AS DateTime), NULL)
SET IDENTITY_INSERT [dbo].[Person] OFF
SET IDENTITY_INSERT [dbo].[StudentGrade] ON

INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (1, N'C1045', 1, CAST(3.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (2, N'C1045', 2, CAST(3.00 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (3, N'C1045', 3, CAST(2.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (4, N'C1045', 4, CAST(4.00 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (5, N'C1045', 5, CAST(3.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (6, N'C1061', 1, CAST(4.00 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (7, N'C1061', 3, CAST(3.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (8, N'C1061', 4, CAST(2.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (9, N'C1061', 5, CAST(1.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (10, N'C2021', 1, CAST(2.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (11, N'C2021', 2, CAST(3.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (12, N'C2021', 4, CAST(3.00 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (13, N'C2021', 5, CAST(3.00 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (14, N'C2042', 1, CAST(2.00 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (15, N'C2042', 2, CAST(3.50 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (16, N'C2042', 3, CAST(4.00 AS Decimal(3, 2)))
INSERT [dbo].[StudentGrade] ([EnrollmentID], [CourseID], [StudentID], [Grade]) VALUES (17, N'C2042', 5, CAST(3.00 AS Decimal(3, 2)))
SET IDENTITY_INSERT [dbo].[StudentGrade] OFF
ALTER TABLE [dbo].[Course]  WITH CHECK ADD  CONSTRAINT [FK_Course_Department] FOREIGN KEY([DepartmentID])
REFERENCES [dbo].[Department] ([DepartmentID])
GO
ALTER TABLE [dbo].[Course] CHECK CONSTRAINT [FK_Course_Department]
GO
ALTER TABLE [dbo].[StudentGrade]  WITH CHECK ADD  CONSTRAINT [FK_StudentGrade_Student] FOREIGN KEY([StudentID])
REFERENCES [dbo].[Person] ([PersonID])
GO
ALTER TABLE [dbo].[StudentGrade] CHECK CONSTRAINT [FK_StudentGrade_Student]
GO
```

Kod listesi aşağıda verilmiştir:

> [!TIP]
> Kod listesi, Kapsamım adlı bir Access veritabanı dosyasına başvurur. C# [Code.msdn.Microsoft.com](https://code.msdn.microsoft.com/How-to-Retrieve-the-511acece)adresinden hayal chool. mdb 'yi (tam veya Visual Basic örnek projenin parçası olarak) indirebilirsiniz.

```csharp
using System;
using System.Data;
using System.Data.OleDb;
using System.Data.SqlClient;

class Program {
   static void Main(string[] args) {
      String SqlDbConnectionString = "Data Source=(local);Initial Catalog=MySchool;Integrated Security=True;Asynchronous Processing=true;";

      InsertPerson(SqlDbConnectionString, "Janice", "Galvin");
      Console.WriteLine();

      InsertPersonInAdapter(SqlDbConnectionString, "Peter", "Krebs");
      Console.WriteLine();

      String oledbConnectionString = "Provider=Microsoft.Jet.OLEDB.4.0; Data Source=Database\\MySchool.mdb";
      InsertPersonInJet4Database(oledbConnectionString, "Janice", "Galvin");
      Console.WriteLine();

      Console.WriteLine("Please press any key to exit.....");
      Console.ReadKey();
   }

   // Using stored procedure to insert a new row and retrieve the identity value
   static void InsertPerson(String connectionString, String firstName, String lastName) {
      String commandText = "dbo.InsertPerson";

      using (SqlConnection conn = new SqlConnection(connectionString)) {
         using (SqlCommand cmd = new SqlCommand(commandText, conn)) {
            cmd.CommandType = CommandType.StoredProcedure;

            cmd.Parameters.Add(new SqlParameter("@FirstName", firstName));
            cmd.Parameters.Add(new SqlParameter("@LastName", lastName));
            SqlParameter personId = new SqlParameter("@PersonID", SqlDbType.Int);
            personId.Direction = ParameterDirection.Output;
            cmd.Parameters.Add(personId);

            conn.Open();
            cmd.ExecuteNonQuery();

            Console.WriteLine("Person Id of new person:{0}", personId.Value);
         }
      }
   }

   // Using stored procedure in adapter to insert new rows and update the identity value.
   static void InsertPersonInAdapter(String connectionString, String firstName, String lastName) {
      String commandText = "dbo.InsertPerson";
      using (SqlConnection conn = new SqlConnection(connectionString)) {
         SqlDataAdapter mySchool = new SqlDataAdapter("Select PersonID,FirstName,LastName from [dbo].[Person]", conn);

         mySchool.InsertCommand = new SqlCommand(commandText, conn);
         mySchool.InsertCommand.CommandType = CommandType.StoredProcedure;

         mySchool.InsertCommand.Parameters.Add(
             new SqlParameter("@FirstName", SqlDbType.NVarChar, 50, "FirstName"));
         mySchool.InsertCommand.Parameters.Add(
             new SqlParameter("@LastName", SqlDbType.NVarChar, 50, "LastName"));

         SqlParameter personId = mySchool.InsertCommand.Parameters.Add(new SqlParameter("@PersonID", SqlDbType.Int, 0, "PersonID"));
         personId.Direction = ParameterDirection.Output;

         DataTable persons = new DataTable();
         mySchool.Fill(persons);

         DataRow newPerson = persons.NewRow();
         newPerson["FirstName"] = firstName;
         newPerson["LastName"] = lastName;
         persons.Rows.Add(newPerson);

         mySchool.Update(persons);
         Console.WriteLine("Show all persons:");
         ShowDataTable(persons, 14);
      }
   }

   /// For a Jet 4.0 database, we need use the single statement and event handler to insert new rows and retrieve the identity value.
   static void InsertPersonInJet4Database(String connectionString, String firstName, String lastName) {
      String commandText = "Insert into Person(FirstName,LastName) Values(?,?)";
      using (OleDbConnection conn = new OleDbConnection(connectionString)) {
         OleDbDataAdapter mySchool = new OleDbDataAdapter("Select PersonID,FirstName,LastName from Person", conn);

         // Create Insert Command
         mySchool.InsertCommand = new OleDbCommand(commandText, conn);
         mySchool.InsertCommand.CommandType = CommandType.Text;

         mySchool.InsertCommand.Parameters.Add(new OleDbParameter("@FirstName", OleDbType.VarChar, 50, "FirstName"));
         mySchool.InsertCommand.Parameters.Add(new OleDbParameter("@LastName", OleDbType.VarChar, 50, "LastName"));
         mySchool.InsertCommand.UpdatedRowSource = UpdateRowSource.Both;

         DataTable persons = CreatePersonsTable();

         mySchool.Fill(persons);

         DataRow newPerson = persons.NewRow();
         newPerson["FirstName"] = firstName;
         newPerson["LastName"] = lastName;
         persons.Rows.Add(newPerson);

         DataTable dataChanges = persons.GetChanges();

         mySchool.RowUpdated += OnRowUpdated;

         mySchool.Update(dataChanges);

         Console.WriteLine("Data before merging:");
         ShowDataTable(persons, 14);
         Console.WriteLine();

         persons.Merge(dataChanges);
         persons.AcceptChanges();

         Console.WriteLine("Data after merging");
         ShowDataTable(persons, 14);
      }
   }

   static void OnRowUpdated(object sender, OleDbRowUpdatedEventArgs e) {
      if (e.StatementType == StatementType.Insert) {
         // Retrieve the identity value
         OleDbCommand cmdNewId = new OleDbCommand("Select @@IDENTITY", e.Command.Connection);
         e.Row["PersonID"] = (Int32)cmdNewId.ExecuteScalar();

         // After the status is changed, the original values in the row are preserved. And the
         // Merge method will be called to merge the new identity value into the original DataTable.
         e.Status = UpdateStatus.SkipCurrentRow;
      }
   }

   // Create the Persons table before filling.
   private static DataTable CreatePersonsTable() {
      DataTable persons = new DataTable();

      DataColumn personId = new DataColumn();
      personId.DataType = Type.GetType("System.Int32");
      personId.ColumnName = "PersonID";
      personId.AutoIncrement = true;
      personId.AutoIncrementSeed = 0;
      personId.AutoIncrementStep = -1;
      persons.Columns.Add(personId);

      DataColumn firstName = new DataColumn();
      firstName.DataType = Type.GetType("System.String");
      firstName.ColumnName = "FirstName";
      persons.Columns.Add(firstName);

      DataColumn lastName = new DataColumn();
      lastName.DataType = Type.GetType("System.String");
      lastName.ColumnName = "LastName";
      persons.Columns.Add(lastName);

      DataColumn[] pkey = { personId };
      persons.PrimaryKey = pkey;

      return persons;
   }

   private static void ShowDataTable(DataTable table, Int32 length) {
      foreach (DataColumn col in table.Columns) {
         Console.Write("{0,-" + length + "}", col.ColumnName);
      }
      Console.WriteLine();

      foreach (DataRow row in table.Rows) {
         foreach (DataColumn col in table.Columns) {
            if (col.DataType.Equals(typeof(DateTime)))
               Console.Write("{0,-" + length + ":d}", row[col]);
            else if (col.DataType.Equals(typeof(Decimal)))
               Console.Write("{0,-" + length + ":C}", row[col]);
            else
               Console.Write("{0,-" + length + "}", row[col]);
         }

         Console.WriteLine();
      }
   }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’te Veri Alma ve Değiştirme](retrieving-and-modifying-data.md)
- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [Satır Durumları ve Satır Sürümleri](./dataset-datatable-dataview/row-states-and-row-versions.md)
- [AcceptChanges ve RejectChanges](./dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- [DataSet İçeriklerini Birleştirme](./dataset-datatable-dataview/merging-dataset-contents.md)
- [Veri Kaynaklarını DataAdapters ile Güncelleştirme](updating-data-sources-with-dataadapters.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
