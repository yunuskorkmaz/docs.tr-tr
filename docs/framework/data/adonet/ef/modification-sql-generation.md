---
title: Değişiklik SQL oluşturma
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: 8e0568e32094b6cc27137409f3d908928d82cebb
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45989962"
---
# <a name="modification-sql-generation"></a>Değişiklik SQL oluşturma
Bu bölümde bir değişiklik SQL oluşturma modülü için geliştirme anlatılmaktadır, (SQL:1999-uyumlu veritabanı) sağlayıcısı. Bu modül, uygun SQL INSERT, UPDATE veya DELETE deyimlerine bir değişikliği komut ağacı çevirmek için sorumludur.  
  
 Select deyimleri için SQL oluşturma hakkında daha fazla bilgi için bkz. [SQL oluşturma](../../../../../docs/framework/data/adonet/ef/sql-generation.md).  
  
## <a name="overview-of-modification-command-trees"></a>Değişiklik komut ağaçlarını genel bakış  
 Değişiklik SQL oluşturma modülü, belirli bir giriş DbModificationCommandTree üzerinde temel veritabanı özgü değişiklik SQL deyimleri oluşturur.  
  
 Bir DbModificationCommandTree nesne modeli, bir DML işlemi (bir ekleme, güncelleştirme veya silme işlemi) değişiklik temsilidir DbCommandTree devralıyor. Üç uygulamaları DbModificationCommandTree vardır:  
  
-   DbInsertCommandTree  
  
-   DbUpdateCommandTree  
  
-   DbDeleteCommandTree  
  
 DbModificationCommandTree ve tarafından üretilen kendi uygulamalarını [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] her zaman tek bir satır işlemi temsil eder. Bu bölümde, .NET Framework sürüm 3.5, kısıtlama olmadan bu türleri açıklanmaktadır.  
  
 ![Diyagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")  
  
 DbModificationCommandTree ayarlama değiştirme işlemi için hedef temsil eden bir hedef özelliği vardır. Giriş kümesinde tanımlayan hedefin ifade her zaman DbScanExpression özelliğidir.  Bir DbScanExpression ya da bir tablo veya Görünüm temsil edebilir veya bir veri kümesi meta verileri özelliği, hedef "sorgu tanımlama" ise null olmayan bir sorgu ile tanımlanan.  
  
 Bir sorgu temsil eder bir DbScanExpression yalnızca bir sağlayıcı değiştirme hedefi belirlenen modelde tanımlayan bir sorgu kullanarak tanımlandı, ancak hiçbir işlev karşılık gelen bir değiştirme işlemi için sağlanan ulaşabilir. Sağlayıcıları (SqlClient, örneğin, daha önceden) senaryosunu desteklemek mümkün olmayabilir.  
  
 DbInsertCommandTree komut ağaç olarak ifade edilen bir tek satır ekleme işlemi temsil eder.  
  
```  
public sealed class DbInsertCommandTree : DbModificationCommandTree {  
   public IList<DbModificationClause> SetClauses { get }  
   public DbExpression Returning { get }  
}  
```  
  
 DbUpdateCommandTree komut ağaç olarak ifade edilen bir tek satır güncelleştirme işlemi temsil eder.  
  
 DbDeleteCommandTree komut ağaç olarak ifade edilen bir tek satır silme işlemini temsil eder.  
  
### <a name="restrictions-on-modification-command-tree-properties"></a>Değişiklik komut ağacı özellikleri kısıtlamaları  
 Aşağıdaki bilgileri ve kısıtlamaları değişikliği komut ağacı özellikleri için geçerlidir.  
  
#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>DbInsertCommandTree ve DbUpdateCommandTree döndürme  
 Null olmadığında, döndürme komutu bir okuyucu döndürdüğünü gösterir. Aksi takdirde, komut, etkilenen satır sayısı (eklendiğinde veya güncelleştirildiğinde) belirten bir skaler değer döndürmelidir.  
  
 Döndürme değeri, eklenen veya güncelleştirilen satırı tabanlı döndürülmesi gereken sonuçlar bir projeksiyon belirtir. Yalnızca Dbnewınstanceexpression her biriyle ilgili DbModificationCommandTree hedefi için bir başvuruyu temsil eden bir DbVariableReferenceExpression üzerinden bir DbPropertyExpression olan bağımsız bir satırı temsil eden türünde olabilir. Özellikleri döndürme her zaman depolama üretilen veya hesaplanan değerleri özelliğinde kullanılan DbPropertyExpressions tarafından temsil edilir. Satır eklenmekte tablonun en az bir özellik olarak oluşturulan ya da (StoreGeneratedPattern.Identity veya StoreGeneratedPattern.Computed olarak ssdl işaretli) hesaplanan deposu belirtildiğinde DbInsertCommandTree içinde döndürme null değil. Döndürme DbUpdateCommandTrees içinde null değil, satır güncelleştiriliyor tablonun en az bir özellik deposu olarak belirtildiğinde (olarak işaretlenmişse StoreGeneratedPattern.Computed ssdl içinde) hesaplanan.  
  
#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>SetClauses DbInsertCommandTree ve DbUpdateCommandTree  
 INSERT listesini SetClauses belirtir veya güncelleştirme ekleme veya güncelleştirme işlemi tanımlayan bir yan tümceleri ayarlayın.  
  
```  
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.   
```  
  
 Özellik güncelleştirilmesi gereken özelliği belirtir. Her zaman ilgili DbModificationCommandTree hedefinin bir başvuruyu temsil eder bir DbVariableReferenceExpression üzerinden bir DbPropertyExpression olur.  
  
 Değer özelliğini güncelleştirmek yeni değeri belirtir. Tür ya da DbConstantExpression veya DbNullExpression.  
  
#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a>Koşul DbUpdateCommandTree ve DbDeleteCommandTree  
 Hedef koleksiyonun üyeleri güncelleştirildiğinde veya silindiğinde belirlemek için kullanılan karşılaştırma koşulu belirtir. Bu yerleşik DbExpressions aşağıdaki alt kümesini bir ifade ağacı şöyledir:  
  
-   DbComparisonExpression türde bir DbPropertyExression aşağıda kısıtlı olarak olan sağ alt ve sol alt bir DbConstantExpression ile eşittir.  
  
-   DbConstantExpression  
  
-   Üzerinden bir DbPropertyExpresison kısıtlı olarak DbIsNullExpression  
  
-   Karşılık gelen DbModificationCommandTree hedefi için bir başvuruyu temsil eden bir DbVariableReferenceExpression üzerinden DbPropertyExpression.  
  
-   DbAndExpression  
  
-   DbNotExpression  
  
-   DbOrExpression  
  
## <a name="modification-sql-generation-in-the-sample-provider"></a>Örnek sağlayıcısında değişiklik SQL oluşturma  
 [Entity Framework örnek sağlayıcısı](https://go.microsoft.com/fwlink/?LinkId=180616) destekleyen bir ADO.NET veri sağlayıcıları bileşenlerini gösterir [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Bu, bir SQL Server 2005 veritabanını hedefler ve System.Data.SqlClient ADO.NET 2.0 veri sağlayıcısı üzerine bir sarmalayıcı olarak uygulanır.  
  
 Değişiklik SQL oluşturma Modülü (SQL Generation\DmlSqlGenerator.cs dosyasında bulunur) örnek sağlayıcısı bir giriş DbModificationCommandTree alır ve tek bir değişiklik büyük olasılıkla döndürmek için bir select deyimi tarafından izlenen SQL deyimini oluşturan bir okuyucu tarafından DbModificationCommandTree belirtildi. Hedef SQL Server veritabanı tarafından oluşturulan komutları şeklini etkileyeceğini unutmayın.  
  
### <a name="helper-classes-expressiontranslator"></a>Yardımcı sınıfları: ExpressionTranslator  
 ExpressionTranslator DbExpression türünde tüm değişiklik komut ağacı özellikleri için ortak bir basit translator işlevi görür. Bu değişikliği komut ağacı özelliklerini sınırlı olan ifade türleri çeviri destekler ve göz önünde belirli kısıtlamalar ile oluşturulmuş.  
  
 Aşağıdaki bilgiler, belirli ifade türleri (Önemsiz çevirileri düğümleri atlanır) ziyaret açıklanır.  
  
### <a name="dbcomparisonexpression"></a>DbComparisonExpression  
 ExpressionTranslator preserveMemberValues ile oluşturulan zaman = true ve sağa sabiti (DbNullExpression) yerine bir DbConstantExpression, sol işleneni (DbPropertyExpressions) ile ilişkilendirir DbConstantExpression. Dönüş bir Select deyimi etkilenen satır tanımlamak üzere oluşturulan gerekiyorsa, kullanılır.  
  
### <a name="dbconstantexpression"></a>DbConstantExpression  
 Ziyaret edilen her sabit bir parametre oluşturulur.  
  
### <a name="dbpropertyexpression"></a>DbPropertyExpression  
 Oluşturma (tablo değişkeni kullanıldığında, yalnızca güncelleştirme senaryolarda gerçekleşir) bir diğer ad oluşturduğu sürece her zaman temsil eden girdi tablosu DbPropertyExpression örneğini düşünüldüğünde, takma ad için girişi belirtilmesi gerekiyor; Çeviri varsayılan olarak özellik adıdır.  
  
## <a name="generating-an-insert-sql-command"></a>Bir INSERT SQL komutu oluşturma  
 Oluşturulan INSERT komutu için belirli bir DbInsertCommandTree örnek sağlayıcısında aşağıdaki iki INSERT şablonlardan birini izler.  
  
 İlk şablon SetClauses listesinde değerlerine INSERT gerçekleştirmek için bir komut vardır ve döndürme özelliği null değildi, eklenen satır için döndürme özelliğinde belirtilen dönüş özellikleri için bir SELECT deyimi. Koşul öğe "\@ @ROWCOUNT > 0" değeri bir satır eklenmişse true. Koşul öğe "keyMemberI keyValueI = &#124; SCOPE_IDENTITY()" şeklini alır "keyMemberI SCOPE_IDENTITY() =" SCOPE_IDENTITY() bir kimlik (eklenen son kimlik değeri döndürdüğünden keyMemeberI depoda üretilmiş bir anahtar ise yalnızca depoda üretilmiş) sütunu.  
  
```  
-- first insert Template  
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]    
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES   
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 INSERT burada birincil anahtarı depoda üretilmiş ancak bir tamsayı türü değil ve bu nedenle scope_identity()) ile kullanılamaz, bir satır eklemeyi belirtiyorsa, ikinci şablon gereklidir. Depoda üretilmiş bir bileşik anahtarı varsa de kullanılır.  
  
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
  
 Örnek sağlayıcısı ile birlikte modeli kullanan bir örnek verilmiştir. Bu, bir DbInsertCommandTree INSERT komutu oluşturur.  
  
 Aşağıdaki kod, bir kategori ekler:  
  
```  
using (NorthwindEntities northwindContext = new NorthwindEntities()) {  
   Category c = new Category();  
   c.CategoryName = "Test Category";  
   c.Description = "A new category for testing";  
   northwindContext.AddObject("Categories", c);  
   northwindContext.SaveChanges();  
}  
```  
  
 Bu kod, sağlayıcıya geçirilir aşağıdaki komut ağacı üretir:  
  
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
  
 Aşağıdaki SQL deyimini örnek sağlayıcısında üreten mağazası komut şöyledir:  
  
```  
insert [dbo].[Categories]([CategoryName], [Description], [Picture])  
values (@p0, @p1, null)  
select [CategoryID]  
from [dbo].[Categories]  
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()  
```  
  
## <a name="generating-an-update-sql-command"></a>Bir güncelleştirme SQL komutu oluşturma  
 Bir verilen DbUpdateCommandTree için oluşturulan güncelleştirme komutunu aşağıdaki şablonu temel alan:  
  
```  
-- UPDATE Template   
UPDATE <target>   
SET setClauseProprerty0 = setClauseValue0,  .. setClauseProprertyN = setClauseValueN  | @i = 0  
WHERE <predicate>  
  
[SELECT <returning>   
 FROM <target>  
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]  
```  
  
 Sahte set yan tümcesi set yan tümcesi olan ("@i = 0") hiçbir set yan tümceleri yalnızca belirtilen. Tüm depolama sütunları yeniden hesaplanan emin olmak için budur.  
  
 Yalnızca döndürme özelliği null değilse, döndürme özelliğinde belirtilen özellikleri döndürmek için bir select deyimi oluşturuldu.  
  
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
  
 Örnek sağlayıcısında aşağıdaki depolama komutu üretir:  
  
```  
update [dbo].[Categories]  
set [CategoryName] = @p0  
where ([CategoryID] = @p1)   
```  
  
### <a name="generating-a-delete-sql-command"></a>Silme SQL komutu oluşturma  
 Bir verilen DbDeleteCommandTree için oluşturulan DELETE komutu aşağıdaki şablonu temel alan:  
  
```  
-- DELETE Template   
DELETE <target>   
WHERE <predicate>  
```  
  
 Aşağıdaki örnek, bir silme komutu oluşturmak için örnek sağlayıcısı ile model kullanır.  
  
 Aşağıdaki kullanıcı kodu bir kategoriyi siler:  
  
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
  
 Aşağıdaki depolama komutu örnek sağlayıcısı tarafından üretilir:  
  
```  
delete [dbo].[Categories]  
where ([CategoryID] = @p0)  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Entity Framework Veri Sağlayıcısı Yazma](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
