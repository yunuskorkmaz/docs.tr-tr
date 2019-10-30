---
title: Değişiklik SQL Oluşturma
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: b6c1b71effba17d33c035d0f1df386bf56d405b5
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039893"
---
# <a name="modification-sql-generation"></a>Değişiklik SQL Oluşturma

Bu bölümde, (SQL: 1999 uyumlu veritabanı) sağlayıcınız için bir değiştirme SQL oluşturma modülünün nasıl geliştirilmesi anlatılmaktadır. Bu modül, bir değiştirme komut ağacını uygun SQL INSERT, UPDATE veya DELETE ifadelerine çevirmekten sorumludur.

Select deyimleri için SQL üretimi hakkında daha fazla bilgi için bkz. [SQL üretimi](sql-generation.md).

## <a name="overview-of-modification-command-trees"></a>Değiştirme komut ağaçlarına genel bakış

Değişiklik SQL oluşturma modülü, belirli bir giriş DbModificationCommandTree temelinde veritabanına özel değişiklik SQL deyimleri oluşturur.

DbModificationCommandTree bir değiştirme DML işleminin (bir INSERT, Update veya delete işlemi), DbCommandTree 'den devralan bir nesne modeli gösterimidir. DbModificationCommandTree ' nin üç uygulaması vardır:

- DbInsertCommandTree

- DbUpdateCommandTree

- DbDeleteCommandTree

DbModificationCommandTree ve Entity Framework tarafından üretilen uygulamaları her zaman tek bir satır işlemini temsil eder. Bu bölümde, .NET Framework sürüm 3,5 ' de kısıtlamaları olan bu türler açıklanmaktadır.

![Çizimindeki](./media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")

DbModificationCommandTree, değişiklik işlemi için hedef kümesini temsil eden bir Target özelliğine sahiptir. Giriş kümesini tanımlayan hedefin Expression özelliği her zaman DbScanExpression ' dır.  Bir DbScanExpression bir tabloyu veya görünümü temsil edebilir ya da hedefin "sorgu tanımlaması" meta veri özelliği null değilse bir sorgu ile tanımlanmış bir veri kümesini temsil edebilir.

Bir sorguyu temsil eden bir DbScanExpression, küme, modelde bir tanımlama sorgusu kullanılarak tanımlanmışsa ancak ilgili değişiklik işlemi için hiçbir işlev sağlanmadıysa yalnızca bir değişikliğin hedefi olarak bir sağlayıcıya ulaşabilir. Sağlayıcılar böyle bir senaryoyu destekleyemeyebilir (örneğin, SqlClient).

DbInsertCommandTree, komut ağacı olarak ifade edilen tek satırlık ekleme işlemini temsil eder.

```csharp
public sealed class DbInsertCommandTree : DbModificationCommandTree {
   public IList<DbModificationClause> SetClauses { get }
   public DbExpression Returning { get }
}
```

DbUpdateCommandTree, komut ağacı olarak ifade edilen tek satırlık bir güncelleştirme işlemini temsil eder.

DbDeleteCommandTree, komut ağacı olarak ifade edilen tek satırlık silme işlemini temsil eder.

### <a name="restrictions-on-modification-command-tree-properties"></a>Değiştirme komut ağacı özelliklerindeki kısıtlamalar

Aşağıdaki bilgiler ve kısıtlamalar değiştirme komut ağacı özellikleri için geçerlidir.

#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>DbInsertCommandTree ve DbUpdateCommandTree içine dönme

Null olmayan, döndürme komutun bir okuyucu döndürdüğünü gösterir. Aksi takdirde, komut etkilenen satır sayısını belirten bir skaler değer döndürmelidir (ekli veya güncelleştirilmiş).

Döndürülen değer, girilen veya güncellenen satıra göre döndürülecek sonuçların projeksiyonunu belirtir. Yalnızca bir satırı temsil eden DbNewInstanceExpression oluşturamıyor türünde olabilir ve bağımsız değişkenlerinin her biri, karşılık gelen DbModificationCommandTree hedefine bir başvuruyu temsil eden bir DbVariableReferenceExpression üzerinde bir DbPropertyExpression olur. Döndürülen özellikte kullanılan Dbpropertydeyimleriyle temsil edilen özellikler, her zaman üretilen veya hesaplanan değerleri depolar. DbInsertCommandTree içinde, satır eklenmekte olan tablonun en az bir özelliği depo oluşturuldu veya hesaplandı (StoreGeneratedPattern. Identity veya StoreGeneratedPattern. ssdl içinde hesaplanan) olarak belirtildiğinde, döndüren döndürme null değildir. DbUpdateCommandTrees içinde, satırın güncelleştirilmekte olduğu tablonun en az bir özelliği (StoreGeneratedPattern. ssdl içinde hesaplanan) olarak belirtildiğinde, döndüren döndürme null değildir.

#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>DbInsertCommandTree ve DbUpdateCommandTree içindeki Settümceleri

Settümceleri ekleme veya güncelleştirme işlemini tanımlayan INSERT veya Update set yan tümceleri listesini belirtir.

Liste öğeleri, ekleme veya güncelleştirme değiştirme işleminde tek bir yan tümce belirten DbModificationClause türü olarak belirtilir. DbSetClause, DbModificationClause öğesinden devralır ve bir özelliğin değerini ayarlayan bir değiştirme işleminde yan tümceyi belirtir. .NET Framework sürüm 3,5 ' den başlayarak, SetClause 'daki tüm öğeler SetClause türündedir.

Özelliği, güncellenmesi gereken özelliği belirtir. Bir DbVariableReferenceExpression üzerinde her zaman bir DbPropertyExpression, buna karşılık gelen DbModificationCommandTree hedefine yönelik bir başvuruyu temsil eder.

Değer, özelliği güncelleştirilecek yeni değeri belirtir. Bu, DbConstantExpression veya Dbsnullexpression türünde olabilir.

#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a>DbUpdateCommandTree ve DbDeleteCommandTree içindeki koşul

Koşul, hedef koleksiyonun hangi üyelerinin güncelleştirileceğini veya silineceğini belirlemekte kullanılan koşulu belirtir. Bu, Dbdeyimlerden oluşan aşağıdaki alt kümesini oluşturulmuş bir ifade ağacıdır:

- Sağ alt öğesi, aşağıda kısıtlanmış bir DbPropertyExpression ve bir DbConstantExpression sol alt öğesi olacak şekilde, türü eşittir DbComparisonExpression.

- DbConstantExpression

- Aşağıda kısıtlanmış bir DbPropertyExpression üzerinde Dbissnullexpression

- Karşılık gelen DbModificationCommandTree hedefine yönelik bir başvuruyu temsil eden bir DbVariableReferenceExpression üzerinde DbPropertyExpression.

- DbAndExpression

- DbNotExpression

- DbOrExpression

## <a name="modification-sql-generation-in-the-sample-provider"></a>Örnek sağlayıcıda değişiklik SQL üretimi

[Entity Framework örnek sağlayıcı](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) , Entity Framework destekleyen ADO.NET veri sağlayıcılarının bileşenlerini gösterir. SQL Server 2005 veritabanını hedefler ve System. Data. SqlClient ADO.NET 2,0 Veri Sağlayıcısı üzerine bir sarmalayıcı olarak uygulanır.

Örnek sağlayıcının (SQL Generation\DmlSqlGenerator.cs dosyasında bulunur) değişiklik SQL oluşturma modülü, bir giriş DbModificationCommandTree alır ve tek bir değişiklik SQL deyiminden sonra bir SELECT deyiminden sonra gelen bir DbModificationCommandTree tarafından belirtilmişse okuyucu. Oluşturulan komutların şeklinin hedef SQL Server veritabanından etkileneceğini unutmayın.

### <a name="helper-classes-expressiontranslator"></a>Yardımcı sınıflar: ExpressionTranslator

ExpressionTranslator, DbExpression türünde tüm değiştirme komut ağacı özellikleri için ortak bir basit çevirici işlevi görür. Yalnızca değiştirme komutu ağacının özelliklerinin kısıtlandığı ve belirli kısıtlamalarla birlikte oluşturulduğu ifade türlerinin çevirisini destekler.

Aşağıdaki bilgiler belirli ifade türlerini ziyaret etmenizi açıklar (önemsiz çevirileri olan düğümler atlanır).

### <a name="dbcomparisonexpression"></a>DbComparisonExpression

ExpressionTranslator, preserveMemberValues = true ile oluşturulduğunda ve sağdaki sabit değeri bir DbConstantExpression (Dbsnullexpression yerine) olduğunda, sol işleneni (DbPropertyExpression) bununla ilişkilendirir DbConstantExpression. Bu, etkilenen satırı tanımlamak için bir return SELECT ifadesinin oluşturulması gerekiyorsa kullanılır.

### <a name="dbconstantexpression"></a>DbConstantExpression

Her ziyaret edilen sabit için bir parametre oluşturulur.

### <a name="dbpropertyexpression"></a>DbPropertyExpression

Oluşturma işlemi her zaman giriş tablosunu temsil ettiğinden, kuşak bir diğer ad oluşturmadıysa (yalnızca bir tablo değişkeni kullanıldığında güncelleştirme senaryolarında olur), giriş için diğer ad belirtilmesi gerekmez; Çeviri varsayılan olarak özellik adını alır.

## <a name="generating-an-insert-sql-command"></a>INSERT SQL komutu oluşturma

Örnek sağlayıcıda verilen bir DbInsertCommandTree için, oluşturulan INSERT komutu aşağıdaki iki ekleme şablonundan birini izler.

İlk şablonda, Setyan tümceleri listesindeki değerleri verilen ekleme işlemini gerçekleştirmeye yönelik bir komut ve döndürülen özellik null değilse, ekli satır için döndürülen özellikte belirtilen özellikleri döndürecek bir SELECT deyimidir. Bir satır eklenirse, "\@@ROWCOUNT > 0" koşul öğesi doğru. "KeyMemberI = keyValueI &#124; scope_identity ()" koşul öğesi, "keyMemberI = scope_identity ()" şeklini, ancak keyMemberI 'nin bir kimliğe ekli en son kimlik değerini döndürdüğü "keymemberi = ()" şeklini alır ( Depo oluşturuldu) sütunu.

```sql
-- first insert Template
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

INSERT, birincil anahtarın depoda oluşturulduğu, ancak bir tamsayı türü olmadığı ancak bu nedenle scope_identity () ile birlikte kullanılamayan bir satır eklemeyi belirtiyorsa ikinci şablon gereklidir. Bu, Birleşik bir depoda oluşturulan anahtar varsa da kullanılır.

```sql
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

Örnek sağlayıcıda bulunan modeli kullanan bir örnek aşağıda verilmiştir. DbInsertCommandTree öğesinden bir INSERT komutu oluşturur.

Aşağıdaki kod bir kategori ekler:

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = new Category();
   c.CategoryName = "Test Category";
   c.Description = "A new category for testing";
   northwindContext.AddObject("Categories", c);
   northwindContext.SaveChanges();
}
```

Bu kod, sağlayıcıya geçirilen aşağıdaki komut ağacını üretir:

```output
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

Örnek sağlayıcının ürettiği mağaza komutu aşağıdaki SQL deyimidir:

```sql
insert [dbo].[Categories]([CategoryName], [Description], [Picture])
values (@p0, @p1, null)
select [CategoryID]
from [dbo].[Categories]
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()
```

## <a name="generating-an-update-sql-command"></a>Bir Update SQL komutu oluşturuluyor

Belirli bir DbUpdateCommandTree için, oluşturulan güncelleştirme komutu aşağıdaki şablona dayalıdır:

```sql
-- UPDATE Template
UPDATE <target>
SET setClauseProperty0 = setClauseValue0, .. setClausePropertyN = setClauseValueN  | @i = 0
WHERE <predicate>

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

Set yan tümcesi, yalnızca set yan tümceleri belirtilmemişse, sahte set yan tümcesine ("@i = 0") sahiptir. Bu, tüm mağaza hesaplanmış sütunlarının yeniden hesaplanmasını sağlamaktır.

Yalnızca döndüren özelliği null değilse, return özelliğinde belirtilen özellikleri döndürmek için bir SELECT ifadesinin oluşturulması gerekir.

Aşağıdaki örnek, bir Update komutu oluşturmak için örnek sağlayıcıda bulunan modeli kullanır.

Aşağıdaki Kullanıcı kodu bir kategoriyi güncelleştirir:

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();
   c.CategoryName = "New test name";
   northwindContext.SaveChanges();
}
```

Bu Kullanıcı kodu, sağlayıcıya geçirilen aşağıdaki komut ağacını üretir:

```output
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

Örnek sağlayıcı aşağıdaki Store komutunu üretir:

```sql
update [dbo].[Categories]
set [CategoryName] = @p0
where ([CategoryID] = @p1)
```

### <a name="generating-a-delete-sql-command"></a>Bir DELETE SQL komutu oluşturuluyor

Belirli bir DbDeleteCommandTree için, oluşturulan DELETE komutu aşağıdaki şablona dayalıdır:

```sql
-- DELETE Template
DELETE <target>
WHERE <predicate>
```

Aşağıdaki örnek, bir Delete komutu oluşturmak için örnek sağlayıcıda bulunan modeli kullanır.

Aşağıdaki Kullanıcı kodu bir kategoriyi siler:

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();
   northwindContext.DeleteObject(c);
   northwindContext.SaveChanges();
}
```

Bu Kullanıcı kodu, sağlayıcıya geçirilen aşağıdaki komut ağacını üretir.

```output
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

Aşağıdaki mağaza komutu örnek sağlayıcı tarafından üretilir:

```sql
delete [dbo].[Categories]
where ([CategoryID] = @p0)
```

## <a name="see-also"></a>Ayrıca bkz.

- [Entity Framework Veri Sağlayıcısı Yazma](writing-an-ef-data-provider.md)
