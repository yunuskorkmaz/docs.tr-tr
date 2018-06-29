---
title: Değişiklik SQL oluşturma
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: 1d24775a7a50da1008a5097e1a2caf4e72c946e2
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37071958"
---
# <a name="modification-sql-generation"></a>Değişiklik SQL oluşturma
Bu bölüm için değiştirme SQL oluşturma modülü geliştirmek nasıl anlatır, (SQL:1999-uyumlu bir veritabanına) sağlayıcısı. Bu modül, uygun SQL INSERT, UPDATE veya DELETE deyimleri değişikliği komut ağacı çevirmek için sorumludur.  
  
 Select deyimi için SQL oluşturma hakkında daha fazla bilgi için bkz: [SQL üretimi](../../../../../docs/framework/data/adonet/ef/sql-generation.md).  
  
## <a name="overview-of-modification-command-trees"></a>Değişiklik komut ağaçlarını genel bakış  
 Değişiklik SQL oluşturma modülü üzerinde belirli bir giriş DbModificationCommandTree temel veritabanı özgü değişikliği SQL deyimlerini oluşturur.  
  
 Bir değişiklik DML işlemi (bir ekleme, güncelleştirme veya silme işlemi) nesne modeli gösterimini bir DbModificationCommandTree olan DbCommandTree devralan. DbModificationCommandTree üç uygulamaları şunlardır:  
  
-   DbInsertCommandTree  
  
-   DbUpdateCommandTree  
  
-   DbDeleteCommandTree  
  
 DbModificationCommandTree ve tarafından üretilen bunun uygulamalarını [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] her zaman tek bir satır işlemi temsil eder. Bu bölümde, bu tür, .NET Framework sürüm 3.5 kısıtlamalar ile açıklanmaktadır.  
  
 ![Diyagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")  
  
 DbModificationCommandTree değiştirme işlemi için ayarlanmış hedef temsil eden bir hedef özelliğine sahiptir. Giriş kümesi tanımlar hedefin ifade özelliği her zaman DbScanExpression olur.  Bir DbScanExpression ya da bir tablo veya Görünüm gösterebilir veya meta veri özelliği, hedef "sorgu tanımlama" ise, bir veri kümesi null olmayan bir sorgu ile tanımlanan.  
  
 Bir sorgu temsil eden bir DbScanExpression yalnızca bir sağlayıcı değiştirme hedefi olarak belirlenen modelde tanımlayan bir sorgu kullanarak tanımlandı, ancak hiçbir işlev karşılık gelen değiştirme işlemi için sağlanan ulaşabilir. Sağlayıcıları (SqlClient, örneğin, desteklemez) senaryosunu destekleyecek mümkün olmayabilir.  
  
 DbInsertCommandTree bir komut ağacındaki ifade edilen bir tek satır ekleme işlemi temsil eder.  
  
```  
public sealed class DbInsertCommandTree : DbModificationCommandTree {  
   public IList<DbModificationClause> SetClauses { get }  
   public DbExpression Returning { get }  
}  
```  
  
 DbUpdateCommandTree bir komut ağacındaki ifade edilen bir tek satır güncelleştirme işlemini temsil eder.  
  
 DbDeleteCommandTree bir komut ağacındaki ifade edilen tek satır silme işlemini temsil eder.  
  
### <a name="restrictions-on-modification-command-tree-properties"></a>Değişiklik komut ağacı özellikleri kısıtlamalar  
 Aşağıdaki bilgiler ve kısıtlamaları değişiklik komut ağacı özellikleri için geçerlidir.  
  
#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>DbInsertCommandTree ve DbUpdateCommandTree döndürme  
 Null olmayan döndürme komutu bir okuyucu döndürdüğünü gösterir. Aksi takdirde komut etkilenen satırların sayısını (eklenir veya güncelleştirilir) gösteren bir skaler değer döndürmelidir.  
  
 Bir yansıtma eklenen veya güncelleştirilen satır tabanlı döndürülecek sonuç döndürme değeri belirtir. Tür bağımsız değişkenleri karşılık gelen DbModificationCommandTree hedef başvuru temsil eden bir DbVariableReferenceExpression üzerinden bir DbPropertyExpression olan her bir satır temsil eden Dbnewınstanceexpression yalnızca olabilir. Döndürme her zaman oluşturulan veya değerleri hesaplanmış sütun deposu özelliğinde kullanılan DbPropertyExpressions tarafından temsil edilen özellikleri. En az bir satır eklenmekte tablonun oluşturulan veya (StoreGeneratedPattern.Identity veya StoreGeneratedPattern.Computed olarak ssdl işaretli) hesaplanmış deposu olarak belirtildiğinde DbInsertCommandTree içinde döndürme null değil. DbUpdateCommandTrees içinde döndürme null olmayan, satır güncelleştiriliyor tablosunun en az bir özellik deposu olarak belirtildiğinde hesaplanan (olarak işaretlenmişse StoreGeneratedPattern.Computed ssdl içinde).  
  
#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>DbInsertCommandTree ve DbUpdateCommandTree SetClauses  
 INSERT listesini SetClauses belirtir veya güncelleştirme ekleme veya güncelleştirme işlemi tanımlamak yan tümceleri ayarlayın.  
  
```  
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.   
```  
  
 Özellik güncelleştirilmelidir özelliği belirtir. Her zaman bir başvuru karşılık gelen DbModificationCommandTree hedefi temsil eden bir DbVariableReferenceExpression üzerinden bir DbPropertyExpression olur.  
  
 Değer yeni değer özelliği güncelleştirileceği ile belirtir. Türü ya da DbConstantExpression veya DbNullExpression.  
  
#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a>DbUpdateCommandTree ve DbDeleteCommandTree karşılaştırma  
 Koşulu, hangi hedef koleksiyonun üyeleri güncelleştirilemez veya belirlemek için kullanılan koşulu belirtir. DbExpressions aşağıdaki alt kümesini yerleşik bir ifade ağacına şöyledir:  
  
-   DbComparisonExpression tür aşağıda kısıtlı olarak DbPropertyExression olan sağ alt ve sol alt bir DbConstantExpression ile eşittir.  
  
-   DbConstantExpression  
  
-   Bir DbPropertyExpresison kısıtlı olarak üzerinden DbIsNullExpression  
  
-   Karşılık gelen DbModificationCommandTree hedef başvuru temsil eden bir DbVariableReferenceExpression üzerinden DbPropertyExpression.  
  
-   DbAndExpression  
  
-   DbNotExpression  
  
-   DbOrExpression  
  
## <a name="modification-sql-generation-in-the-sample-provider"></a>Örnek sağlayıcısında değişiklik SQL oluşturma  
 [Entity Framework örnek sağlayıcısı](http://go.microsoft.com/fwlink/?LinkId=180616) destekleyen bir ADO.NET veri sağlayıcıları bileşenlerinin gösterir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. SQL Server 2005 veritabanlarını hedefler ve System.Data.SqlClient ADO.NET 2.0 veri sağlayıcısı en üstünde bir sarmalayıcı olarak uygulanmıştır.  
  
 (SQL Generation\DmlSqlGenerator.cs dosyasında bulunur) örnek sağlayıcısı'nın değişikliği SQL oluşturma modülü giriş DbModificationCommandTree alır ve tek bir değişiklik büyük olasılıkla döndürmek için bir select deyimi tarafından izlenen SQL deyimini üreten bir DbModificationCommandTree tarafından belirtilen okuyucu. Hedef SQL Server veritabanı tarafından oluşturulan komutları şeklini etkileyeceğini unutmayın.  
  
### <a name="helper-classes-expressiontranslator"></a>Yardımcı sınıfları: ExpressionTranslator  
 Tüm değişiklik komut ağacı özelliklerinin DbExpression türünde bir ortak basit Çeviricisi ExpressionTranslator görür. Yalnızca değişikliği komut ağacı özelliklerini kısıtlı ifade türleri çevrilmesi destekler ve aklınızda belirli kısıtlamalar ile yapılandırılır.  
  
 Aşağıdaki bilgiler, belirli ifade türleri (Önemsiz çevirileri düğümleriyle göz ardı edilir) ziyaret açıklanır.  
  
### <a name="dbcomparisonexpression"></a>DbComparisonExpression  
 Ne zaman ExpressionTranslator yapılandırılmıştır ile preserveMemberValues = true ve sağa sabiti (yerine DbNullExpression) bir DbConstantExpression olduğunda, bunu sol işleneni (DbPropertyExpressions) ile ilişkilendirir DbConstantExpression. Dönüş bir Select deyimi etkilenen satır tanımlamak üzere oluşturulan gerekiyorsa, kullanılır.  
  
### <a name="dbconstantexpression"></a>DbConstantExpression  
 Her ziyaret edilen sabit bir parametre oluşturulur.  
  
### <a name="dbpropertyexpression"></a>DbPropertyExpression  
 O oluşturma (tablo değişkeni kullanıldığında, yalnızca güncelleştirme senaryolarda gerçekleşir) bir diğer ad oluşturduğu sürece her zaman temsil eden giriş tablosu DbPropertyExpression örneği, diğer ad için giriş belirtilmesi gerekiyor; Çeviri varsayılan özellik adı olarak.  
  
## <a name="generating-an-insert-sql-command"></a>Bir INSERT SQL komutu oluşturuluyor  
 Örnek Sağlayıcısı'nda belirtilen DbInsertCommandTree için oluşturulan INSERT komutu aşağıdaki iki Ekle şablonlarından birini izler.  
  
 İlk şablon SetClauses listesinde değerlerine göre Ekle gerçekleştirmek için bir komut var ve döndürme özelliği null olmayan, eklenen satır için döndürme özelliğinde belirtilen özellikleri döndürmek için bir SELECT deyimi. Koşul öğesi "\@ @ROWCOUNT > 0" değeri bir satır eklediyseniz true. Koşul öğesi "keyMemberI keyValueI = &#124; SCOPE_IDENTITY()" şeklini alır "keyMemberI SCOPE_IDENTITY() =" yalnızca SCOPE_IDENTITY() bir kimlik (eklenen son kimlik değer döndürdüğünden keyMemeberI depoda üretilmiş bir anahtarı ise depoda üretilmiş) sütun.  
  
```  
-- first insert Template  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES   
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 İkinci Şablon Ekle burada birincil anahtarı depoda üretilmiş ancak bir tamsayı türünde değil ve bu nedenle scope_identity()) ile kullanılamaz satır ekleme belirtiyorsa gereklidir. Depoda üretilmiş bir bileşik anahtarı ise de kullanılır.  
  
```  
-- second insert template  
DECLARE @generated_keys TABLE [(keyMember0, … keyMemberN)  
  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
 OUTPUT inserted.KeyMember0, …, inserted.KeyMemberN INTO @generated_keys  
 VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES  
  
[SELECT <returning_over_t>   
 FROM @generated_keys  AS g  
JOIN <target> AS t ON g.KeyMember0 = t.KeyMember0 AND … g.KeyMemberN = t.KeyMemberN  
 WHERE @@ROWCOUNT > 0  
```  
  
 Örnek sağlayıcısıyla içerdiği modelini kullanan bir örnek verilmiştir. Bu bir INSERT komutu DbInsertCommandTree oluşturur.  
  
 Aşağıdaki kod bir kategori ekler:  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = new Category();  
   c.CategoryName = "Test Category";  
   c.Description = "A new category for testing";  
   northwindContext.AddObject("Categories", c);  
   northwindContext.SaveChanges();  
}  
```  
  
 Bu kod sağlayıcısına geçirilen aşağıdaki komut ağacı üretir:  
  
```  
DbInsertCommandTree  
|_Parameters  
|_Target : 'target'  
| |_Scan : dbo.Categories  
|_SetClauses  
| |_DbSetClause  
| | |_Property  
| | | |_Var(target).CategoryName  
| | |_Value  
| |   |_'Test Category'  
| |_DbSetClause  
| | |_Property  
| | | |_Var(target).Description  
| | |_Value  
| |   |_'A new category for testing'  
| |_DbSetClause  
|   |_Property  
|   | |_Var(target).Picture  
|   |_Value  
|     |_null  
|_Returning  
  |_NewInstance : Record['CategoryID'=Edm.Int32]  
    |_Column : 'CategoryID'  
      |_Var(target).CategoryID  
```  
  
 Örnek sağlayıcısı üreten depolama komutu aşağıdaki SQL ifadesi şöyledir:  
  
```  
insert [dbo].[Categories]([CategoryName], [Description], [Picture])  
values (@p0, @p1, null)  
select [CategoryID]  
from [dbo].[Categories]  
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()  
```  
  
## <a name="generating-an-update-sql-command"></a>Bir güncelleştirme SQL komutu oluşturuluyor  
 Belirli bir DbUpdateCommandTree için oluşturulan güncelleştirme komutu aşağıdaki şablona göre:  
  
```  
-- UPDATE Template   
UPDATE <target>   
SET setClauseProprerty0 = setClauseValue0,  .. setClauseProprertyN = setClauseValueN  | @i = 0  
WHERE <predicate>  
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 Set yan tümcesinin sahte set yan tümcesine sahip ("@i = 0") hiçbir set yan tümceleri yalnızca belirtilen. Bu herhangi deposu-sütunları yeniden hesaplanan olduğundan emin olmaktır.  
  
 Yalnızca döndürme özelliği null değilse, bir select deyimi döndürme özelliğinde belirtilen özellikleri döndürmek için oluşturulur.  
  
 Aşağıdaki örnek, bir güncelleştirme komutu oluşturmak için örnek sağlayıcısı ile model kullanır.  
  
 Aşağıdaki kullanıcı kodu bir kategori güncelleştirir:  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();  
   c.CategoryName = "New test name";  
   northwindContext.SaveChanges();  
}  
```  
  
 Bu kullanıcı kodu sağlayıcısına geçirilen aşağıdaki komut ağacı üretir:  
  
```  
DbUpdateCommandTree  
|_Parameters  
|_Target : 'target'  
| |_Scan : dbo.Categories  
|_SetClauses  
| |_DbSetClause  
|   |_Property  
|   | |_Var(target).CategoryName  
|   |_Value  
|     |_'New test name'  
|_Predicate  
| |_  
|   |_Var(target).CategoryID  
|   |_=  
|   |_10  
|_Returning   
```  
  
 Örnek sağlayıcısı aşağıdaki depolama komutu üretir:  
  
```  
update [dbo].[Categories]  
set [CategoryName] = @p0  
where ([CategoryID] = @p1)   
```  
  
### <a name="generating-a-delete-sql-command"></a>Silme SQL komutu oluşturuluyor  
 Belirli bir DbDeleteCommandTree için oluşturulan DELETE komutu aşağıdaki şablona göre:  
  
```  
-- DELETE Template   
DELETE <target>   
WHERE <predicate>  
```  
  
 Aşağıdaki örnek, silme komutu oluşturmak için örnek sağlayıcısı ile model kullanır.  
  
 Aşağıdaki kullanıcı kodu bir kategori siler:  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();  
   northwindContext.DeleteObject(c);  
   northwindContext.SaveChanges();  
}  
```  
  
 Bu kullanıcı kodu sağlayıcısına geçirilen aşağıdaki komut ağacı üretir.  
  
```  
DbDeleteCommandTree  
|_Parameters  
|_Target : 'target'  
| |_Scan : dbo.Categories  
|_Predicate  
  |_  
    |_Var(target).CategoryID  
    |_=  
    |_10  
```  
  
 Aşağıdaki depolama komutu örnek sağlayıcısı tarafından oluşturulur:  
  
```  
delete [dbo].[Categories]  
where ([CategoryID] = @p0)  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity Framework Veri Sağlayıcısı Yazma](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
