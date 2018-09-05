---
title: Kimlik veya otomatik sayı değerlerini alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d6b7f9cb-81be-44e1-bb94-56137954876d
ms.openlocfilehash: ca739f703267f27932ec7450a59d7f4afaffd64b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43670983"
---
# <a name="retrieving-identity-or-autonumber-values"></a>Kimlik veya otomatik sayı değerlerini alma
İlişkisel bir veritabanındaki bir birincil anahtar bir sütun veya her zaman benzersiz değerler içeren sütunlar bileşimidir. Birincil anahtar değeri bilerek, onu içeren satırın bulundurmanıza olanak tanır. SQL Server, Oracle ve Microsoft Access/Jet gibi ilişkisel veritabanı altyapılarından birincil anahtar olarak belirlenebilir sütunları otomatik olarak artırma oluşturmayı destekler. Tabloya satır eklendikçe bu değerler sunucu tarafından oluşturulur. SQL Server, bir sütunun kimlik özelliği ayarlamak, Oracle bir dizi oluşturun ve Microsoft Access içinde oluşturduğunuz bir sayı sütunu.  
  
 A <xref:System.Data.DataColumn> ayarlayarak otomatik olarak artan değerleri oluşturmak için de kullanılabilir <xref:System.Data.DataColumn.AutoIncrement%2A> özelliği true. Ancak, ayrı örneklerinde yinelenen değerlere sahip çıkabilir bir <xref:System.Data.DataTable>, birden çok istemci uygulamaları birbirinden bağımsız olarak otomatik artan değerleri oluşturuluyor. Sunucunun otomatik olarak artan değerleri oluşturmak zorunda eklenen her satır için oluşturulan değeri almak her bir kullanıcı sağlayarak olası çakışmaları ortadan kaldırır.  
  
 Çağrı sırasında `Update` yöntemi bir `DataAdapter`, veritabanı, ADO.NET uygulamaya çıkış parametreleri olarak veya bir SELECT deyimi INSERT deyimi aynı toplu yürütüldü, sonuç kümesinin döndürülen ilk kaydı olarak veri gönderebilir. ADO.NET, bu değerleri almak ve karşılık gelen sütunlarda güncelleştirme <xref:System.Data.DataRow> güncelleştiriliyor.  
  
 Microsoft Access Jet veritabanı altyapısı gibi bazı veritabanı altyapıları, çıktı parametreleri desteklemez ve tek bir toplu işlemde birden çok deyime işleyemiyor. Jet veritabanı altyapısı ile çalışırken, bir olay işleyicisi için ayrı bir SELECT komutu yürüterek eklenmiş bir satır için oluşturulan yeni sayı değeri alabilir `RowUpdated` olayı `DataAdapter`.  
  
> [!NOTE]
>  Artan değerini otomatik kullanmaya alternatif kullanmaktır <xref:System.Guid.NewGuid%2A> yöntemi bir <xref:System.Guid> GUID ya da her yeni satırda eklenmiş gibi sunucuya kopyaladığınız istemci bilgisayarda genel benzersiz tanımlayıcısını oluşturmak için nesne. `NewGuid` Yöntemi hiçbir değer çoğaltılır yüksek olasılık sağlayan bir algoritma kullanarak oluşturulan 16 bayt ikili değer oluşturur. Bir SQL Server veritabanında bir GUID olarak depolanan bir `uniqueidentifier` SQL Server Transact-SQL kullanarak otomatik olarak oluşturmak bir sütun `NEWID()` işlevi. Bir GUID birincil bir anahtar kullanarak performansı olumsuz etkileyebilir. SQL Server için destek sağlar `NEWSEQUENTIALID()` işlevin, garanti edilmez genel olarak benzersiz olmalıdır, ancak bu dizinlenebilir daha verimli bir şekilde sıralı bir GUID oluşturur.  
  
## <a name="retrieving-sql-server-identity-column-values"></a>SQL Server kimlik sütunu değerlerini alma  
 Microsoft SQL Server ile çalışırken, eklenen bir satır için kimlik değeri döndürmek için bir output parametresi ile bir saklı yordam oluşturabilirsiniz. Aşağıdaki tabloda, üç kimlik sütunu değerlerini almak için kullanılan SQL Server Transact-SQL işlevleri açıklanmaktadır.  
  
|İşlev|Açıklama|  
|--------------|-----------------|  
|SCOPE_IDENTITY|Geçerli yürütme kapsamı içinde son kimlik değeri döndürür. SCOPE_IDENTITY çoğu senaryo için önerilir.|  
|@@IDENTITY|Herhangi bir tabloda geçerli oturumda oluşturulan son kimlik değeri içerir. @@IDENTITY tetikleyiciler tarafından etkilenebilir ve beklediğiniz kimlik değerini döndürmeyebilir.|  
|IDENT_CURRENT|Belirli bir tablo için tüm oturumları ve herhangi bir kapsamı içinde oluşturulan son kimlik değeri döndürür.|  
  
 Aşağıdaki saklı yordamı bir satır içine ekleme işlemini gösterir **kategorileri** tablo ve Transact-SQL SCOPE_IDENTITY() işlevi tarafından oluşturulan yeni kimlik değeri döndürmek için bir çıktı parametresi kullanın.  
  
```  
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
```  
  
 Saklı yordam ardından kaynağı olarak belirtilebilir <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> , bir <xref:System.Data.SqlClient.SqlDataAdapter> nesne. <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> Özelliği <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> ayarlanmalıdır <xref:System.Data.CommandType.StoredProcedure>. Kimlik çıkışı oluşturarak alınan bir <xref:System.Data.SqlClient.SqlParameter> olan bir <xref:System.Data.ParameterDirection> , <xref:System.Data.ParameterDirection.Output>. Zaman `InsertCommand` olduğu işlenen, otomatik olarak artan kimlik değeri döndürdü ve bulundukları **CategoryID** ayarlarsanız geçerli satırdaki sütun <xref:System.Data.SqlClient.SqlCommand.UpdatedRowSource%2A> Ekle komutu özelliği `UpdateRowSource.OutputParameters` veya `UpdateRowSource.Both`.  
  
 INSERT deyimi hem yeni kimlik değeri döndüren bir SELECT deyimi içeren bir toplu iş, INSERT komutu yürütür, ardından ayarlayarak yeni değer alabilir, `UpdatedRowSource` Ekle komutu özelliği `UpdateRowSource.FirstReturnedRecord`.  
  
 [!code-csharp[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.RetrieveIdentityStoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.RetrieveIdentityStoredProcedure/VB/source.vb#1)]  
  
## <a name="merging-new-identity-values"></a>Yeni kimlik değerleri birleştirme  
 Sık karşılaşılan bir senaryodur çağırmaktır `GetChanges` yöntemi bir `DataTable` yalnızca değiştirilen satırları içeren bir kopyasını oluşturun ve yeni bir kopyasını çağrılırken kullanılacak `Update` yöntemi bir `DataAdapter`. Değiştirilen satırları güncelleştirme gerçekleştirir ayrı bir bileşen için hazırlamak, ihtiyacınız olduğunda bu kullanışlıdır. Güncelleştirmenin ardından özgün tekrar birleştirilmelidir yeni kimlik değerleri kopya içerebilir `DataTable`. Yeni kimlik değerleri özgün değerden farklı olması olası `DataTable`. Öğesinin özgün değerleri birleştirme işlemini gerçekleştirmek için **AutoIncrement** kopyalama sütunlarında gerekir muhafaza edilir, bulun ve orijinal mevcut satırlarını güncelleştirin aktarabilmek için `DataTable`, yerine içeren yeni satır ekleme Yeni kimlik değerleri. Bununla birlikte, varsayılan olarak bu özgün değerleri çağrısı yapıldıktan sonra kaybolur `Update` yöntemi bir `DataAdapter`, çünkü `AcceptChanges` güncelleştirilen her biri için örtük olarak çağırılamaz `DataRow`.  
  
 Öğesinin özgün değerleri korumak için iki yolla bir `DataColumn` içinde bir `DataRow` sırasında bir `DataAdapter` güncelleştirin:  
  
-   Orijinal değerleri koruma, ilk yöntem ayarlamaktır `AcceptChangesDuringUpdate` özelliği `DataAdapter` için `false`. Bu etkiler her `DataRow` içinde `DataTable` güncelleştiriliyor. Daha fazla bilgi ve bir kod örneği için bkz: <xref:System.Data.Common.DataAdapter.AcceptChangesDuringUpdate%2A>.  
  
-   İkinci yöntem, kod yazmaya olan `RowUpdated` olay işleyicisine `DataAdapter` ayarlanacak <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> için <xref:System.Data.UpdateStatus.SkipCurrentRow>. `DataRow` Her öğenin özgün değerinde güncelleştirilmiş `DataColumn` korunur. Bu yöntem, özgün değerlerine bazı satırlar için ve başkaları için koruma sağlar. İlk kontrol ederek kodunuz düzenlenen ya da silinen satır için değil ve eklenmiş satırlar için orijinal değerleri gibi koruyabilirsiniz <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A> ve ardından ayarlar <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> için <xref:System.Data.UpdateStatus.SkipCurrentRow> bulunan satırlar için yalnızca bir `StatementType` , `Insert`.  
  
 Bu yöntemlerin her ikisi kullanıldığında özgün değerlerini korumak için bir `DataRow` sırasında bir `DataAdapter` güncelleştirme, ADO.NET, geçerli değerlerini ayarlamak için Eylemler dizisi gerçekleştirir `DataRow` çıkış parametreleri veya ilk tarafından döndürülen yeni değerlere bir sonuç kümesi satırının hala özgün değeri her korurken döndürülen `DataColumn`. İlk olarak, `AcceptChanges` yöntemi `DataRow` geçerli değerleri özgün değerleri olarak korumak için çağrılır ve ardından yeni değerler atanır. Bu Eylemler, aşağıdaki `DataRows` vardı, kendi <xref:System.Data.DataRow.RowState%2A> özelliğini <xref:System.Data.DataRowState.Added> olacaktır kendi `RowState` özelliğini <xref:System.Data.DataRowState.Modified>, beklenmeyen gösterebilir.  
  
 Komutu sonuçları her birine nasıl uygulandığını <xref:System.Data.DataRow> güncelleştirilmesini göre belirlenir <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> her özellik <xref:System.Data.Common.DbCommand>. Bu özellik için bir değer ayarlanır `UpdateRowSource` sabit listesi.  
  
 Aşağıdaki tabloda açıklanmıştır nasıl `UpdateRowSource` numaralandırma değerlerinin etkileyen <xref:System.Data.DataRow.RowState%2A> güncelleştirilen satırların bulunduğu özelliği.  
  
|Üye adı|Açıklama|  
|-----------------|-----------------|  
|<xref:System.Data.UpdateRowSource.Both>|`AcceptChanges` olarak adlandırılır ve hem de çıkış parametresi değerleri ve/veya herhangi bir sonuç kümesi ilk satırındaki değerleri yerleştirilir `DataRow` güncelleştiriliyor. Uygulamak için hiçbir değer `RowState` olacaktır <xref:System.Data.DataRowState.Unchanged>.|  
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|Bir satır döndürülürse `AcceptChanges` çağrılır ve değiştirilmiş satır satır eşlendiği `DataTable`ayarını `RowState` için `Modified`. Hiçbir satır, sonra döndürülürse `AcceptChanges` değil olarak adlandırılır ve `RowState` kalır `Added`.|  
|<xref:System.Data.UpdateRowSource.None>|Herhangi bir satır veya döndürülen parametreleri göz ardı edilir. Hiçbir çağrı yoktur `AcceptChanges` ve `RowState` kalır `Added`.|  
|<xref:System.Data.UpdateRowSource.OutputParameters>|`AcceptChanges` denir ve herhangi bir çıktı parametreleri değiştirilen satıra eşlendiğini `DataTable`ayarını `RowState` için `Modified`. Hiçbir çıktı parametresi varsa `RowState` olacaktır `Unchanged`.|  
  
### <a name="example"></a>Örnek  
 Bu örnek, ayıklama değiştirilen satırları gösterir. bir `DataTable` ve kullanarak bir <xref:System.Data.SqlClient.SqlDataAdapter> veri kaynağını güncelleştirebilir ve yeni bir kimlik sütunu değerini almak için. <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> İki Transact-SQL deyimleri yürütür; ilk INSERT deyiminin ve ikinci bir kimlik değeri alınacak SCOPE_IDENTITY işlevini kullanan bir SELECT deyimi.  
  
```  
INSERT INTO dbo.Shippers (CompanyName)   
VALUES (@CompanyName);  
SELECT ShipperID, CompanyName FROM dbo.Shippers   
WHERE ShipperID = SCOPE_IDENTITY();  
```  
  
 `UpdatedRowSource` Özelliği Ekle komutunun `UpdateRowSource.FirstReturnedRow` ve <xref:System.Data.MissingSchemaAction> özelliği `DataAdapter` ayarlanır `MissingSchemaAction.AddWithKey`. `DataTable` Doldurulur ve yeni bir satır için kod ekler `DataTable`. Değiştirilen satırların sonra yeni bir ayıklandıktan `DataTable`, için geçirilen `DataAdapter`, daha sonra sunucu güncelleştirir.  
  
 [!code-csharp[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.MergeIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#1)]  
  
 `OnRowUpdated` Olay işleyicisine denetimleri <xref:System.Data.Common.RowUpdatedEventArgs.StatementType%2A> , <xref:System.Data.SqlClient.SqlRowUpdatedEventArgs> satır ekleme olup olmadığını belirlemek için. İse, ardından <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> özelliği <xref:System.Data.UpdateStatus.SkipCurrentRow>. Satır güncelleştirildi, ancak satır özgün değerleri korunur. Yordamı, ana gövdesinde <xref:System.Data.DataSet.Merge%2A> yeni kimlik değeri birleştirmek için yöntemi çağrıldığında `DataTable`ve son olarak `AcceptChanges` çağrılır.  
  
 [!code-csharp[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/CS/source.cs#2)]
 [!code-vb[DataWorks SqlClient.MergeIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.MergeIdentity/VB/source.vb#2)]  
  
## <a name="retrieving-microsoft-access-autonumber-values"></a>Microsoft Access sayı değerlerini alma  
 Bu bölüm nasıl alınacağını gösteren bir örnek içerir `Autonumber` Jet 4.0 veritabanı değerleri. Bu nedenle yeni döndürmek için aşağıdaki yöntemlerden birini kullanmak mümkün değildir Jet veritabanı altyapısı birden çok deyim yürütülemedi toplu veya çıkış parametreleri kullanımını desteklemiyor `Autonumber` eklenen bir satır için atanan değer. Ancak, kod ekleyebilirsiniz `RowUpdated` @ ayrı bir SELECT yürüten bir olay işleyicisi@IDENTITY yeni almak için deyimi `Autonumber` değeri.  
  
### <a name="example"></a>Örnek  
 Şema bilgileri kullanarak eklemek yerine `MissingSchemaAction.AddWithKey`, bu örneği yapılandırır bir `DataTable` çağrılmadan önce doğru şema ile <xref:System.Data.OleDb.OleDbDataAdapter> doldurmak için `DataTable`. Bu durumda, **CategoryID** ayarlayarak sıfırdan başlayarak eklenen her satırın atanan değer düşürmek için yapılandırılmış sütun <xref:System.Data.DataColumn.AutoIncrement%2A> için `true`, <xref:System.Data.DataColumn.AutoIncrementSeed%2A> 0 ve <xref:System.Data.DataColumn.AutoIncrementStep%2A> -1. Kod, ardından iki yeni satır ekler ve kullandığı `GetChanges` değiştirilen satırların yeni bir eklemek için `DataTable` yapan `Update` yöntemi.  
  
 [!code-csharp[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#1)]
 [!code-vb[DataWorks OleDb.JetAutonumberMerge#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#1)]  
  
 `RowUpdated` Kullandığı aynı açık olay işleyicisi <xref:System.Data.OleDb.OleDbConnection> olarak `Update` deyiminin `OleDbDataAdapter`. Denetlediği `StatementType` , <xref:System.Data.OleDb.OleDbRowUpdatedEventArgs> için eklenen satır. Eklenen her biri için yeni bir satır <xref:System.Data.OleDb.OleDbCommand> @ Seç yürütmek için oluşturulan@IDENTITY deyimi yeni döndüren bağlantıda `Autonumber` yerleştirilen değeri **CategoryID** sütununun `DataRow`. `Status` Özelliği ayarlanmış ardından `UpdateStatus.SkipCurrentRow` gizli çağrısı bastırmak için `AcceptChanges`. Yordamı, ana gövdesinde `Merge` iki birleştirilecek yöntemi çağrıldığında `DataTable` nesneleri ve son olarak `AcceptChanges` çağrılır.  
  
 [!code-csharp[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/CS/source.cs#2)]
 [!code-vb[DataWorks OleDb.JetAutonumberMerge#2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks OleDb.JetAutonumberMerge/VB/source.vb#2)]  
  
### <a name="retrieving-identity-values"></a>Kimlik değerlerini alma  
 Genellikle, sütundaki değerleri benzersiz olmalıdır, sütun kimliği olarak ayarlayın. Ve bazen yeni veri kimlik değeri gerekiyor. Bu örnek, kimlik değerlerin nasıl alınacağını gösterir:  
  
-   Veri eklemek ve bir kimlik değeri döndürmek için bir saklı yordam oluşturur.  
  
-   Yeni verileri ekleyin ve sonucu görüntülemek için bir komutu yürütür.  
  
-   Kullanan <xref:System.Data.SqlClient.SqlDataAdapter> yeni verileri ekleyin ve sonucu görüntülemek için.  
  
 Derleme ve örneği çalıştırmak için önce aşağıdaki betiği kullanarak örnek veritabanı oluşturmanız gerekir:  
  
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
  
 Kodu listesi aşağıdadır:  
  
> [!IMPORTANT]
>  Kod listesi MySchool.mdb adlı bir Access veritabanı dosyasına başvuruyor. MySchool.mdb (tam C# veya Visual Basic örnek proje kapsamında)'nden ya da indirebilirsiniz [Visual Studio 2012 örnek](https://code.msdn.microsoft.com/How-to-retrieve-the-95b4ee43) veya [Visual Studio 2013 örnek](https://code.msdn.microsoft.com/How-to-Retrieve-the-511acece).  
  
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
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
