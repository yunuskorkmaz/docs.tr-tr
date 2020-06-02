---
title: Kimliği veya Otomatik Sayı Değerlerini Alma
description: İlişkisel veritabanlarındaki birincil anahtarların kimlik ve otomatik sayı değerlerini almayı ve ADO.NET içinde yeni kimlik değerlerini birleştirmeyi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6b7f9cb-81be-44e1-bb94-56137954876d
ms.openlocfilehash: dbbc013a5b6c83391a29109beca44120c68d827f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286578"
---
# <a name="retrieving-identity-or-autonumber-values"></a>Kimliği veya Otomatik Sayı Değerlerini Alma

İlişkisel veritabanındaki birincil anahtar, her zaman benzersiz değerler içeren bir sütun veya sütun birleşimidir. Birincil anahtar değerini bilmek, onu içeren satırı bulmanıza olanak sağlar. SQL Server, Oracle ve Microsoft Access/Jet gibi ilişkisel veritabanı motorları, birincil anahtarlar olarak belirlenebilir sütunları otomatik olarak arttırın oluşturulmasını destekler. Bu değerler, bir tabloya satırlar eklendikçe sunucu tarafından oluşturulur. SQL Server bir sütunun Identity özelliğini ayarlarsınız, Oracle 'da bir sıra oluşturur ve Microsoft Access 'te bir OtomatikSayı sütunu oluşturursunuz.

<xref:System.Data.DataColumn>Ayrıca, özelliği true olarak ayarlayarak değerleri otomatik olarak arttırarak oluşturmak için de kullanılabilir <xref:System.Data.DataColumn.AutoIncrement%2A> . Bununla birlikte, <xref:System.Data.DataTable> birden fazla istemci uygulaması bağımsız olarak değerleri otomatik olarak arttırdığınızda, tek bir ' ın ayrı örneklerinde yinelenen değerlerle karşılaşabilirsiniz. Sunucunun otomatik olarak artırılmaları, her bir kullanıcının her ekli satır için oluşturulan değeri almasına izin vererek olası çakışmaları ortadan kaldırır.

`Update`Bir yöntemi çağrısı sırasında `DataAdapter` , veritabanı, ADO.net uygulamanıza çıkış parametreleri olarak veya INSERT ifadesiyle aynı toplu işte yürütülen bir SELECT ifadesinin sonuç kümesinin ilk döndürülen kaydı olarak geri veri gönderebilir. ADO.NET bu değerleri alabilir ve güncelleştirilecek ilgili sütunları güncelleştirebilir <xref:System.Data.DataRow> .

Microsoft Access Jet veritabanı altyapısı gibi bazı veritabanı motorları, çıkış parametrelerini desteklemez ve tek bir toplu işte birden çok deyimi işleyemez. Jet veritabanı altyapısı ile çalışırken, bir olay işleyicisinde otomatik olarak bir SELECT komutu yürüterek ekli bir satır için oluşturulan yeni OtomatikSayı değerini elde edebilirsiniz `RowUpdated` `DataAdapter` .

> [!NOTE]
> Otomatik artan değer kullanmanın bir alternatifi, <xref:System.Guid.NewGuid%2A> <xref:System.Guid> her yeni satır eklendiği sırada sunucuya kopyalanabilen istemci bılgısayarda bir GUID veya genel benzersiz tanımlayıcı oluşturmak için bir nesnenin yöntemini kullanmaktır. `NewGuid`Yöntemi, hiçbir değer yinelenmeyecek yüksek bir olasılık sağlayan bir algoritma kullanılarak oluşturulan bir 16 baytlık ikili değer oluşturur. Bir SQL Server veritabanında GUID, `uniqueidentifier` SQL Server Transact-SQL işlevi kullanılarak otomatik olarak oluşturabileceğiniz bir sütunda depolanır `NEWID()` . GUID 'in birincil anahtar olarak kullanılması performansı olumsuz etkileyebilir. SQL Server `NEWSEQUENTIALID()` , genel olarak benzersiz olan ancak dizine daha verimli bir şekilde dizinlenebilir bir ARDıŞıK GUID üreten, işlevi için destek sağlar.

## <a name="retrieving-sql-server-identity-column-values"></a>SQL Server Identity sütunu değerlerini alma

Microsoft SQL Server ile çalışırken, ekli bir satır için kimlik değerini döndürmek üzere çıkış parametresiyle bir saklı yordam oluşturabilirsiniz. Aşağıdaki tabloda, kimlik sütunu değerlerini almak için kullanılabilecek SQL Server ' deki üç Transact-SQL işlevleri açıklanmaktadır.

|İşlev|Açıklama|
|--------------|-----------------|
|SCOPE_IDENTITY|Geçerli yürütme kapsamındaki son kimlik değerini döndürür. SCOPE_IDENTITY çoğu senaryo için önerilir.|
|@@IDENTITY|Geçerli oturumdaki herhangi bir tabloda oluşturulan son kimlik değerini içerir. @ @IDENTITY tetikleyicilerden etkilenebilir ve bekleeceğiniz kimlik değerini döndüremeyebilir.|
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

Saklı yordam daha sonra bir nesnenin kaynağı olarak belirtilebilir <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter> . <xref:System.Data.SqlClient.SqlCommand.CommandType%2A>Öğesinin özelliği <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> olarak ayarlanmalıdır <xref:System.Data.CommandType.StoredProcedure> . Kimlik çıktısı, ' <xref:System.Data.SqlClient.SqlParameter> a sahip olan bir oluşturarak alınır <xref:System.Data.ParameterDirection> <xref:System.Data.ParameterDirection.Output> . `InsertCommand`İşlendiğinde, otomatik olarak artan kimlik değeri döndürülür **CategoryID** ve <xref:System.Data.SqlClient.SqlCommand.UpdatedRowSource%2A> Insert komutunun özelliğini `UpdateRowSource.OutputParameters` veya olarak ayarlarsanız geçerli satırın CategoryID sütununa konur `UpdateRowSource.Both` .

INSERT komutunuz hem bir INSERT ifadesini hem de yeni kimlik değerini döndüren bir SELECT ifadesini içeren bir Batch çalıştırırsa, `UpdatedRowSource` Insert komutunun özelliğini olarak ayarlayarak yeni değeri alabilirsiniz `UpdateRowSource.FirstReturnedRecord` .

[!code-csharp[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/VB/source.vb#1)]

## <a name="merging-new-identity-values"></a>Yeni kimlik değerleri birleştiriliyor

Yaygın bir senaryo, `GetChanges` `DataTable` yalnızca değiştirilen satırları içeren bir kopya oluşturmak ve a yöntemini çağırırken yeni kopyayı kullanmak için bir ' ın yöntemini çağırmaktan oluşur `Update` `DataAdapter` . Bu özellikle, değiştirilen satırları güncelleştirmeyi gerçekleştiren ayrı bir bileşene sıralama yapmanız gerektiğinde faydalıdır. Güncelleştirme sonrasında, kopya daha sonra orijinalde birleştirilmek zorunda olan yeni kimlik değerleri içerebilir `DataTable` . Yeni kimlik değerlerinin, içindeki özgün değerlerden farklı olması olasıdır `DataTable` . Birleştirme işlemini gerçekleştirmek için, **AutoIncrement** `DataTable` yeni kimlik değerlerini içeren yeni satırları eklemek yerine, kopyada bulunan AutoIncrement sütunlarının orijinal değerlerinin, orijinal içinde mevcut satırları bulabilmesi ve güncelleştirebilmesi için korunması gerekir. Bununla birlikte, varsayılan olarak, bir öğesinin yöntemine yapılan çağrıdan sonra bu özgün değerler kaybolur `Update` `DataAdapter` , çünkü `AcceptChanges` her biri için örtülü olarak çağırılır `DataRow` .

Bir `DataColumn` güncelleştirme sırasında içindeki içindeki özgün değerlerini korumanın iki yolu vardır `DataRow` `DataAdapter` :

- Özgün değerleri korumak için ilk yöntem `AcceptChangesDuringUpdate` , öğesinin özelliğini olarak ayarlandır `DataAdapter` `false` . Bu `DataRow` , güncelleştirilmekte olan her durumda etkiler `DataTable` . Daha fazla bilgi ve bir kod örneği için bkz <xref:System.Data.Common.DataAdapter.AcceptChangesDuringUpdate%2A> ..

- İkinci yöntem, öğesini `RowUpdated` olarak ayarlamak için öğesinin olay işleyicisine kod yazmaktır `DataAdapter` <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> <xref:System.Data.UpdateStatus.SkipCurrentRow> . `DataRow`Güncellenir, ancak her birinin özgün değeri `DataColumn` korunur. Bu yöntem, bazı satırlar için özgün değerleri koruyabilmenizi sağlar ve diğerleri için değildir. Örneğin, kodunuz ilk olarak, eklenen satırlar için özgün değerleri koruyabilir ve önce <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A> öğesini denetleyerek ve <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> <xref:System.Data.UpdateStatus.SkipCurrentRow> yalnızca içeren satırları için olarak ayarlayarak, düzenlenebilir veya silinmiş satırlar için değil `StatementType` `Insert` .

Bu yöntemlerin herhangi biri, bir güncelleştirme sırasında özgün değerleri korumak için kullanıldığında `DataRow` `DataAdapter` , ADO.NET geçerli değerlerini `DataRow` çıkış parametreleri tarafından döndürülen yeni değerlere veya bir sonuç kümesinin ilk döndürülen satırına ayarlamak için bir dizi eylem gerçekleştirir, ancak yine de her birindeki özgün değeri korur `DataColumn` . İlk olarak, `AcceptChanges` öğesinin yöntemi `DataRow` geçerli değerleri özgün değerler olarak korumak için çağrılır ve sonra yeni değerler atanır. `DataRows`Özelliği olarak ayarlanmış olan bu eylemlerin, <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Added> özelliği olarak ayarlanmış olacak şekilde, `RowState` beklenmeyen bir <xref:System.Data.DataRowState.Modified> durum olabilir.

Komut sonuçlarının her güncelleştirilme için nasıl uygulandığı, <xref:System.Data.DataRow> her birinin özelliği tarafından belirlenir <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> <xref:System.Data.Common.DbCommand> . Bu özellik, Numaralandırmadaki bir değere ayarlanır `UpdateRowSource` .

Aşağıdaki tabloda, `UpdateRowSource` numaralandırma değerlerinin <xref:System.Data.DataRow.RowState%2A> güncelleştirilmiş satırların özelliğini nasıl etkilediği açıklanmaktadır.

|Üye adı|Description|
|-----------------|-----------------|
|<xref:System.Data.UpdateRowSource.Both>|`AcceptChanges`çağrılır ve her iki çıkış parametresi değeri ve/veya döndürülen sonuç kümesinin ilk satırındaki değerler `DataRow` güncellenmek üzere yerleştirilir. Uygulanacak değer yoksa, `RowState` olacaktır <xref:System.Data.DataRowState.Unchanged> .|
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Bir satır döndürülürse, `AcceptChanges` çağırılır ve satır öğesinde değiştirilen satırla eşleştirilir, olarak `DataTable` ayarlanıyor `RowState` `Modified` . Hiçbir satır döndürülmezse, `AcceptChanges` çağrılmaz ve `RowState` kalır `Added` .|
|<xref:System.Data.UpdateRowSource.None>|Döndürülen tüm parametreler veya satırlar yok sayılır. ' A yönelik bir çağrı yoktur `AcceptChanges` ve `RowState` kalır `Added` .|
|<xref:System.Data.UpdateRowSource.OutputParameters>|`AcceptChanges`çağrılır ve tüm çıktı parametreleri öğesinde değiştirilen satırla eşlenir ve `DataTable` ' ı ' olarak ayarlar `RowState` `Modified` . Çıkış parametresi yoksa, `RowState` olacaktır `Unchanged` .|

### <a name="example"></a>Örnek

Bu örnek, bir öğesinden değiştirilen satırların ayıklanışını `DataTable` ve bir <xref:System.Data.SqlClient.SqlDataAdapter> veri kaynağını güncelleştirmek ve yeni bir kimlik sütun değeri almak için bir kullanarak öğesini gösterir. <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>Iki Transact-SQL deyimini yürütür; ılkı INSERT deyimidir ve ikincisi kimlik değerini almak için SCOPE_IDENTITY işlevini kullanan BIR SELECT deyimidir.

```sql
INSERT INTO dbo.Shippers (CompanyName)
VALUES (@CompanyName);
SELECT ShipperID, CompanyName FROM dbo.Shippers
WHERE ShipperID = SCOPE_IDENTITY();
```

`UpdatedRowSource`Insert komutunun özelliği olarak ayarlanır `UpdateRowSource.FirstReturnedRow` ve <xref:System.Data.MissingSchemaAction> öğesinin özelliği `DataAdapter` olarak ayarlanır `MissingSchemaAction.AddWithKey` . , `DataTable` Doldurulur ve kod öğesine yeni bir satır ekler `DataTable` . Değiştirilen satırlar daha sonra ' a geçirilen yeni bir ' a ayıklanır ve `DataTable` `DataAdapter` ardından sunucuyu günceller.

[!code-csharp[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#1)]

`OnRowUpdated`Olay işleyicisi, <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A> <xref:System.Data.SqlClient.SqlRowUpdatedEventArgs> satırın bir INSERT olup olmadığını belirlemede öğesini denetler. Eğer ise, <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> özelliği olarak ayarlanır <xref:System.Data.UpdateStatus.SkipCurrentRow> . Satır güncellenir, ancak satırdaki özgün değerler korunur. Yordamın ana gövdesinde, <xref:System.Data.DataSet.Merge%2A> yöntemi yeni kimlik değerini orijinalde birleştirmek için çağrılır `DataTable` ve son olarak `AcceptChanges` çağırılır.

[!code-csharp[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#2)]
[!code-vb[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#2)]

## <a name="retrieving-microsoft-access-autonumber-values"></a>Microsoft Access otomatik sayı değerleri alınıyor

Bu bölüm, `Autonumber` Jet 4,0 veritabanından değerlerin nasıl alınacağını gösteren bir örnek içerir. Jet veritabanı altyapısı, bir toplu işte birden çok deyimin yürütülmesini veya çıkış parametrelerinin kullanımını desteklemez, bu nedenle, ekli satıra atanan yeni değeri döndürmek için bu tekniklerden birini kullanmak mümkün değildir `Autonumber` . Ancak, `RowUpdated` @IDENTITY yeni değeri almak için ayrı bir SELECT @ ifadesini yürüten olay işleyicisine kod ekleyebilirsiniz `Autonumber` .

### <a name="example"></a>Örnek

Kullanılarak şema bilgileri eklemek yerine, `MissingSchemaAction.AddWithKey` Bu örnek, öğesini `DataTable` doldurmanız için çağrılmadan önce doğru şemayla bir yapılandırır <xref:System.Data.OleDb.OleDbDataAdapter> `DataTable` . Bu durumda, **CategoryID** sütunu her bir yerleştirilen satıra atanan değeri sıfıra, <xref:System.Data.DataColumn.AutoIncrement%2A> `true` <xref:System.Data.DataColumn.AutoIncrementSeed%2A> 0 ' a ve <xref:System.Data.DataColumn.AutoIncrementStep%2A> -1 ' e ayarlayarak, sıfıra başlayarak azaltmak üzere yapılandırılır. Kod daha sonra iki yeni satır ekler ve `GetChanges` değiştirilen satırları yöntemine geçirilen yeni bir satıra eklemek için kullanır `DataTable` `Update` .

[!code-csharp[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#1)]
[!code-vb[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#1)]

`RowUpdated`Olay işleyicisi <xref:System.Data.OleDb.OleDbConnection> `Update` , öğesinin ifadesiyle aynı Açık öğesini kullanır `OleDbDataAdapter` . `StatementType` <xref:System.Data.OleDb.OleDbRowUpdatedEventArgs> Ekli satırların öğesini denetler. Her ekli satır için, <xref:System.Data.OleDb.OleDbCommand> bağlantı ÜZERINDE SELECT @ ifadesini yürütmek üzere yeni bir oluşturulur @IDENTITY `Autonumber` . Bu, öğesinin **CategoryID** sütununa yerleştirilen yeni değeri döndürür `DataRow` . `Status`Özelliği daha sonra `UpdateStatus.SkipCurrentRow` gizli çağrısını bastırmak için olarak ayarlanır `AcceptChanges` . Yordamın ana gövdesinde, `Merge` yöntemi iki nesneyi birleştirmek için çağrılır `DataTable` ve son olarak `AcceptChanges` çağırılır.

[!code-csharp[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#2)]
[!code-vb[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#2)]

### <a name="retrieving-identity-values"></a>Kimlik değerlerini alma

Sütunda değerlerin benzersiz olması gerektiğinde genellikle sütunu kimlik olarak ayarlayacağız. Ve bazen de yeni verilerin kimlik değerine ihtiyacımız var. Bu örnek, kimlik değerlerinin nasıl alınacağını gösterir:

- Veri eklemek ve bir kimlik değeri döndürmek için bir saklı yordam oluşturur.

- Yeni verileri eklemek ve sonucu göstermek için bir komut yürütür.

- <xref:System.Data.SqlClient.SqlDataAdapter>Yeni verileri eklemek ve sonucu göstermek için kullanır.

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
> Kod listesi, Kapsamım adlı bir Access veritabanı dosyasına başvurur. [Code.msdn.Microsoft.com](https://code.msdn.microsoft.com/How-to-Retrieve-the-511acece)adresinden hayal chool. mdb 'yi (tam C# veya Visual Basic örnek projenin bir parçası olarak) indirebilirsiniz.

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
