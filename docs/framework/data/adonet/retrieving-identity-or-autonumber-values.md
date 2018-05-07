---
title: Kimliği veya sayı değerlerini alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6b7f9cb-81be-44e1-bb94-56137954876d
ms.openlocfilehash: ce3c888ce9e96d1f5768ce9cf3f3eef8cf8624e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="retrieving-identity-or-autonumber-values"></a>Kimliği veya sayı değerlerini alma
İlişkisel bir veritabanındaki bir birincil anahtar sütunlarının her zaman benzersiz değerler içeren bir sütun veya ' dir. Birincil anahtar değerine bilerek içerdiği satırı bulun olanak tanır. SQL Server, Oracle ve Microsoft Access/Jet gibi ilişkisel veritabanı motoru birincil anahtarlar olarak belirlenebilir sütunları otomatik olarak artırma oluşturulmasını destekler. Tabloya satır eklendikçe bu değerleri sunucu tarafından üretilir. SQL Server'daki bir sütunun kimliğini özelliğini ayarlayın, Oracle bir dizisi oluşturma ve Microsoft Access içinde bir sayı sütun oluşturun.  
  
 A <xref:System.Data.DataColumn> ayarlayarak otomatik olarak artacak değerlerini oluşturmak için de kullanılabilir <xref:System.Data.DataColumn.AutoIncrement%2A> özelliğinin true. Ancak, ayrı ayrı örnekleri yinelenen değerler şunun bir <xref:System.Data.DataTable>, birden çok istemci uygulamaları bağımsız olarak otomatik olarak artacak değerleri oluşturuluyor. Eklenen her satır için oluşturulan değerini almak her bir kullanıcı izin vererek sunucu otomatik olarak artacak değerleri oluştur olması olası çakışmaları ortadan kaldırır.  
  
 Çağrı sırasında `Update` yöntemi bir `DataAdapter`, veritabanını geri uygulamanıza ADO.NET çıkış parametreleri veya aynı toplu iş INSERT deyiminin olarak yürütülen bir SELECT deyimi sonuç kümesi ilk döndürülen kaydının olarak veri gönderebilir. ADO.NET bu değerleri almak ve karşılık gelen sütunları güncelleştirme <xref:System.Data.DataRow> güncelleştiriliyor.  
  
 Microsoft Access Jet veritabanı altyapısı gibi bazı veritabanı motoru çıkış parametreleri desteklemez ve tek bir toplu iş birden fazla deyime işleyemiyor. Jet veritabanı altyapısı ile çalışırken, bir olay işleyicisi için ayrı bir SELECT komutu yürüterek eklenmiş bir satır için oluşturulan yeni sayı değeri alabilir `RowUpdated` olayı `DataAdapter`.  
  
> [!NOTE]
>  Bir otomatik artan değeri kullanmaya alternatif kullanmaktır <xref:System.Guid.NewGuid%2A> yöntemi bir <xref:System.Guid> bir GUID veya eklenen her yeni satırın sunucuya kopyalanabilmesi için istemci bilgisayar üzerinde genel benzersiz tanımlayıcısını oluşturulacak nesne. `NewGuid` Yöntemi, hiçbir değer çoğaltılır yüksek olasılık sağlayan bir algoritma kullanarak oluşturduğunuz 16 bayt ikili bir değer oluşturur. Bir SQL Server veritabanında bir GUID depolanan bir `uniqueidentifier` SQL Server Transact-SQL kullanarak otomatik olarak oluşturabilir sütun `NEWID()` işlevi. Birincil anahtarı olarak bir GUID kullanarak performansı olumsuz etkileyebilir. SQL Server için destek sağlar `NEWSEQUENTIALID()` , garanti edilmez genel olarak benzersiz olmalıdır, ancak, dizini daha verimli bir şekilde sıralı bir GUID oluşturur işlevi.  
  
## <a name="retrieving-sql-server-identity-column-values"></a>SQL Server kimlik sütunu değerlerini alma  
 Microsoft SQL Server ile çalışırken, eklenen satır kimlik değeri döndürmek için çıktı parametresi ile bir saklı yordam oluşturabilirsiniz. Aşağıdaki tabloda, üç kimlik sütun değerleri almak için kullanılan SQL Server Transact-SQL işlevleri açıklanmaktadır.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|SCOPE_IDENTITY|Geçerli yürütme kapsam içinde son kimlik değeri döndürür. SCOPE_IDENTITY çoğu senaryolar için önerilir.|  
|@@IDENTITY|Herhangi bir tabloda geçerli oturumda oluşturulan son kimlik değeri içerir. @@IDENTITY tetikleyiciler tarafından etkilenebilir ve beklediğiniz kimlik değeri döndürmeyebilir.|  
|IDENT_CURRENT|Belirli bir tablo için herhangi bir oturumunda ve herhangi bir kapsamdaki oluşturulan son kimlik değeri döndürür.|  
  
 Aşağıdaki saklı yordamı bir satıra eklemek gösterilmiştir **kategorileri** tablo ve Transact-SQL SCOPE_IDENTITY() işlevi tarafından oluşturulan yeni kimlik değeri döndürmek için bir çıktı parametresi kullanın.  
  
```  
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
```  
  
 Saklı yordam sonra kaynağı olarak belirtilebilir <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> , bir <xref:System.Data.SqlClient.SqlDataAdapter> nesnesi. <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> Özelliği <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> ayarlanmalıdır <xref:System.Data.CommandType.StoredProcedure>. Kimlik çıkış oluşturarak alınır bir <xref:System.Data.SqlClient.SqlParameter> olan bir <xref:System.Data.ParameterDirection> , <xref:System.Data.ParameterDirection.Output>. Zaman `InsertCommand` olan işlenen, otomatik artan kimlik değeri döndürdü ve bulundukları **adlı kullanıcı, Categoryıd'si** ayarlarsanız geçerli satır sütunu <xref:System.Data.SqlClient.SqlCommand.UpdatedRowSource%2A> INSERT komutu özelliğinin `UpdateRowSource.OutputParameters` veya `UpdateRowSource.Both`.  
  
 INSERT komutu, INSERT deyimi ve yeni kimlik değeri döndüren bir SELECT deyimi içeren batch'in sonra ayarlayarak, yeni değer alabilirsiniz `UpdatedRowSource` INSERT komutu özelliğinin `UpdateRowSource.FirstReturnedRecord`.  
  
 [!code-csharp[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/VB/source.vb#1)]  
  
## <a name="merging-new-identity-values"></a>Yeni kimlik değerleri birleştirme  
 Yaygın bir senaryo çağırmaktır `GetChanges` yöntemi bir `DataTable` yalnızca değiştirilen satırları içeren bir kopyasını oluşturun ve yeni bir kopyasını çağrılırken kullanmak için `Update` yöntemi bir `DataAdapter`. Değiştirilen satırları güncelleştirme gerçekleştirir ayrı bir bileşen için sıralama gerektiğinde bu seçenek özellikle yararlıdır. Güncelleştirmenin ardından kopya özgün kopyayla birleştirilmelidir yeni kimlik değerleri içerebilir `DataTable`. Yeni kimlik değerleri özgün değerlerinden farklı olması olası `DataTable`. Birleştirme, özgün değerlerini gerçekleştirmek için **AutoIncrement** kopya sütunlarında gerekir korunur, bulun ve orijinal varolan satırları güncelleştirmek için `DataTable`, yerine içeren yeni satırlar ekleme Yeni kimlik değerleri. Ancak, varsayılan olarak bu özgün değerler için bir çağrı sonra kaybolur `Update` yöntemi bir `DataAdapter`, çünkü `AcceptChanges` her biri için güncelleştirilmiş örtük olarak adlandırılır `DataRow`.  
  
 Özgün değerlerini korumak için iki yolla bir `DataColumn` içinde bir `DataRow` sırasında bir `DataAdapter` güncelleştirin:  
  
-   Özgün değerler koruma ilk yöntemi ayarlamaktır `AcceptChangesDuringUpdate` özelliği `DataAdapter` için `false`. Bu etkiler her `DataRow` içinde `DataTable` güncelleştiriliyor. Daha fazla bilgi ve bir kod örneği için bkz: <xref:System.Data.Common.DataAdapter.AcceptChangesDuringUpdate%2A>.  
  
-   Kod yazmak için ikinci yöntemdir `RowUpdated` olay işleyicisi `DataAdapter` ayarlamak için <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> için <xref:System.Data.UpdateStatus.SkipCurrentRow>. `DataRow` Özgün değeri her güncelleştirilmiş `DataColumn` korunur. Bu yöntem, özgün değerleri bazı satırlar için ve başkaları için değil korumak sağlar. İlk denetleyerek kodunuzu eklenen satırların ve düzenlenen veya silinen satır için özgün değerler gibi koruyabilirsiniz <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A> ve ardından ayarlar <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> için <xref:System.Data.UpdateStatus.SkipCurrentRow> satırlar için yalnızca bir `StatementType` , `Insert`.  
  
 Bu yöntemlerin her ikisi kullanıldığında özgün değerleri korumak için bir `DataRow` sırasında bir `DataAdapter` güncelleştirme, ADO.NET geçerli değerlerini ayarlamak için Eylemler dizisi gerçekleştirir `DataRow` çıkış parametreleri veya ilk tarafından döndürülen yeni değerleri hala özgün değeri her korurken bir sonuç kümesi satır döndürülen `DataColumn`. İlk olarak, `AcceptChanges` yöntemi `DataRow` geçerli değerleri özgün değerler olarak korumak için çağrılır ve ardından yeni değerler atanır. Bu Eylemler, aşağıdaki `DataRows` , vardı kendi <xref:System.Data.DataRow.RowState%2A> özelliğini <xref:System.Data.DataRowState.Added> olacaktır kendi `RowState` özelliğini <xref:System.Data.DataRowState.Modified>, hangi olabilir beklenmeyen.  
  
 Komut sonuçları her birine nasıl uygulandığını <xref:System.Data.DataRow> güncelleştirilmekte tarafından belirlenir <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> her özellik <xref:System.Data.Common.DbCommand>. Bu özellik değere ayarlandığında `UpdateRowSource` numaralandırması.  
  
 Aşağıdaki tabloda açıklanmaktadır nasıl `UpdateRowSource` numaralandırma değerlerinin etkileyen <xref:System.Data.DataRow.RowState%2A> güncelleştirilmiş satır özelliği.  
  
|Üye adı|Açıklama|  
|-----------------|-----------------|  
|<xref:System.Data.UpdateRowSource.Both>|`AcceptChanges` denir ve her ikisi de parametre değerlerini çıkış ve/veya herhangi bir döndürülen sonuç kümesi ilk satır değerleri yerleştirilir `DataRow` güncelleştiriliyor. Uygulamak için hiçbir değer `RowState` olacaktır <xref:System.Data.DataRowState.Unchanged>.|  
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Bir satır döndürülürse `AcceptChanges` olarak adlandırılır ve satır değiştirilen satıra eşlendi `DataTable`, ayar `RowState` için `Modified`. Satır, ardından döndürülürse `AcceptChanges` çağrılmaz ve `RowState` kalır `Added`.|  
|<xref:System.Data.UpdateRowSource.None>|Herhangi bir döndürülen parametreleri veya satırlar yok sayılır. Hiçbir çağrısı yok `AcceptChanges` ve `RowState` kalır `Added`.|  
|<xref:System.Data.UpdateRowSource.OutputParameters>|`AcceptChanges` olarak adlandırılır ve çıktı parametreleri değiştirilen satıra eşlendi `DataTable`, ayar `RowState` için `Modified`. Hiçbir çıktı parametresi varsa `RowState` olacaktır `Unchanged`.|  
  
### <a name="example"></a>Örnek  
 Bu örnek, değiştirilen satırları ayıklanıyor gösterir bir `DataTable` ve kullanarak bir <xref:System.Data.SqlClient.SqlDataAdapter> veri kaynağını güncelleştirmek ve yeni bir kimlik sütunu değer almak için. <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> İki Transact-SQL deyimi yürütür; ilk INSERT deyiminin ve ikinci bir kimlik değeri almak için SCOPE_IDENTITY işlevi kullanan bir SELECT deyimi.  
  
```  
INSERT INTO dbo.Shippers (CompanyName)   
VALUES (@CompanyName);  
SELECT ShipperID, CompanyName FROM dbo.Shippers   
WHERE ShipperID = SCOPE_IDENTITY();  
```  
  
 `UpdatedRowSource` INSERT komutu özelliği ayarlanmış `UpdateRowSource.FirstReturnedRow` ve <xref:System.Data.MissingSchemaAction> özelliği `DataAdapter` ayarlanır `MissingSchemaAction.AddWithKey`. `DataTable` Girilir ve kod için yeni bir satır ekler `DataTable`. Değiştirilen satırları sonra yeni bir ayıklanır `DataTable`, için geçirilen `DataAdapter`, sunucu, daha sonra güncelleştirir.  
  
 [!code-csharp[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#1)]  
  
 `OnRowUpdated` Olay işleyicisi denetimleri <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A> , <xref:System.Data.SqlClient.SqlRowUpdatedEventArgs> satır INSERT olup olmadığını belirlemek için. İse, sonra <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> özelliği ayarlanmış <xref:System.Data.UpdateStatus.SkipCurrentRow>. Satır güncelleştirildi, ancak sıradaki özgün değerleri korunur. Yordamı, ana gövdesinde <xref:System.Data.DataSet.Merge%2A> yöntemi yeni kimlik değeri birleştirmek için çağrılır `DataTable`ve son olarak `AcceptChanges` olarak adlandırılır.  
  
 [!code-csharp[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#2)]
 [!code-vb[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#2)]  
  
## <a name="retrieving-microsoft-access-autonumber-values"></a>Microsoft Access sayı değerlerini alma  
 Bu bölüm nasıl alınacağını gösteren bir örnek içerir `Autonumber` Jet 4.0 veritabanı değerleri. Yeni döndürmek için aşağıdaki yöntemlerden birini kullanmak mümkün değildir Jet veritabanı altyapısı birden çok deyime yürütülmesini bir toplu işlem veya çıkış parametreleri kullanımını desteklemez `Autonumber` eklenen bir satıra atanan değer. Bununla birlikte, kod ekleyebilirsiniz `RowUpdated` @ ayrı bir SELECT yürütür olay işleyicisi@IDENTITY yeni almak için deyimi `Autonumber` değeri.  
  
### <a name="example"></a>Örnek  
 Şema bilgileri kullanarak eklemek yerine `MissingSchemaAction.AddWithKey`, bu örnek yapılandırır bir `DataTable` çağrılmadan önce doğru şema <xref:System.Data.OleDb.OleDbDataAdapter> doldurmak için `DataTable`. Bu durumda, **adlı kullanıcı, Categoryıd'si** sütun sıfır olarak ayarlayarak başlayarak eklenen her satıra atanan değer düşürmek için yapılandırılmış <xref:System.Data.DataColumn.AutoIncrement%2A> için `true`, <xref:System.Data.DataColumn.AutoIncrementSeed%2A> 0 olarak ve <xref:System.Data.DataColumn.AutoIncrementStep%2A> -1. Kod, ardından iki yeni satır ekler ve kullandığı `GetChanges` değiştirilen satırları yeni bir eklemek için `DataTable` için geçirilen `Update` yöntemi.  
  
 [!code-csharp[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#1)]
 [!code-vb[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#1)]  
  
 `RowUpdated` Olay işleyicisi kullandığı aynı açık <xref:System.Data.OleDb.OleDbConnection> olarak `Update` deyiminin `OleDbDataAdapter`. Denetlediği `StatementType` , <xref:System.Data.OleDb.OleDbRowUpdatedEventArgs> için eklenen satır. Eklenen her için yeni bir satır <xref:System.Data.OleDb.OleDbCommand> @ Seç yürütmek için oluşturulan@IDENTITY yeni döndürme bağlantıda deyimi `Autonumber` yerleştirilir değeri **adlı kullanıcı, Categoryıd'si** sütunu `DataRow`. `Status` Özelliği ayarlanmış sonra `UpdateStatus.SkipCurrentRow` gizli çağrısı gizlemek için `AcceptChanges`. Yordamı, ana gövdesinde `Merge` yöntemi iki birleştirmek için çağrılır `DataTable` nesneleri ve son olarak `AcceptChanges` olarak adlandırılır.  
  
 [!code-csharp[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#2)]
 [!code-vb[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#2)]  
  
### <a name="retrieving-identity-values"></a>Kimlik değerlerini alma  
 Genellikle, sütundaki değerlerin benzersiz olması gerektiğinde sütun kimliği olarak ayarlayın. Ve bazen kimliğinizi yeni veri kimlik değeri gerekiyor. Bu örnek, kimlik değerleri almak gösterilmiştir:  
  
-   Veri eklemek ve bir kimlik değeri döndürmek için bir saklı yordam oluşturur.  
  
-   Yeni veri eklemek ve sonucu görüntülemek için bir komut yürütür.  
  
-   Kullanan <xref:System.Data.SqlClient.SqlDataAdapter> yeni veri eklemek ve sonucu görüntülemek için.  
  
 Derleme ve örneği çalıştırmadan önce aşağıdaki komut dosyası kullanarak örnek veritabanı oluşturmanız gerekir:  
  
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
  
 Kod listesi aşağıdadır:  
  
> [!IMPORTANT]
>  Kod listesi MySchool.mdb adlı bir Access veritabanı dosyasına başvuruyor. MySchool.mdb (tam C# veya Visual Basic örnek proje parçası) herhangi birinden indirebilirsiniz [Visual Studio 2012 örnek](http://code.msdn.microsoft.com/How-to-retrieve-the-95b4ee43) veya [Visual Studio 2013 örnek](http://code.msdn.microsoft.com/How-to-Retrieve-the-511acece).  
  
```  
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
  
   /// For a Jet 4.0 database, we need use the sigle statement and event handler to insert new rows and retrieve the identity value.  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Satır Durumları ve Satır Sürümleri](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [AcceptChanges ve RejectChanges](../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)  
 [DataSet İçeriklerini Birleştirme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 [Veri Kaynaklarını DataAdapters ile Güncelleştirme](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
