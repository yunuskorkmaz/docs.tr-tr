---
title: SQL-CLR Tür Uyumsuzlukları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
ms.openlocfilehash: 77090a9f22dcf3d55739aa03535bee863793d858
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172893"
---
# <a name="sql-clr-type-mismatches"></a>SQL-CLR Tür Uyumsuzlukları
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modeli ve SQL Server arasındaki çeviriyi çoğunu otomatikleştirir. Bununla birlikte, bazı durumlarda, tam çeviri engelleyin. Aşağıdaki bölümlerde bu anahtar uyuşmazlıklarını ortak dil çalışma zamanı (CLR) türleri ve SQL Server veritabanı türleri özetlenir. Özel tür eşlemeleri ve işlev çeviri sırasında hakkında daha fazla ayrıntı bulabilirsiniz [SQL-CLR tür eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) ve [veri türleri ve işlevleri](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md).  
  
## <a name="data-types"></a>Veri Türleri  
 Çeviri CLR ve SQL Server arasındaki bir sorgu için veritabanı gönderildiğinde ve sonuçları, nesne modeline geri gönderildiğinde gerçekleşir. Örneğin, aşağıdaki Transact-SQL sorgusunu iki değer dönüştürmeleri gerektirir:  
  
```  
Select DateOfBirth From Customer Where CustomerId = @id     
```  
  
 SQL Server'da sorgu yürütülmeden önce Transact-SQL parametresi için değer belirtilmelidir. Bu örnekte, `id` parametre değeri bir CLR önce çevrilmelidir <xref:System.Int32?displayProperty=nameWithType> türü bir SQL Server'a `INT` veritabanı değeri ne olduğunu anlayabilmeniz yazın. Sonuçları, SQL Server'ı almak için `DateOfBirth` SQL Server'dan sütunun çevrilmiş `DATETIME` bir CLR türüne <xref:System.DateTime?displayProperty=nameWithType> türü için nesne modeli kullanın. Bu örnekte, SQL Server veritabanı ve CLR nesne modeli türlerinde doğal eşlemelere sahip. Ancak bu her zaman böyle değildir.  
  
### <a name="missing-counterparts"></a>Ortaklarınıza eksik  
 Aşağıdaki türleri makul ortaklarınıza yok.  
  
-   CLR içinde eşleşmiyor <xref:System> ad alanı:  
  
    -   **İşaretsiz tamsayılar**. Bu türler, genellikle taşması önlemek için imzalı karşılıkları daha büyük boyutta için eşlenir. Değişmez değerler, imzalı bir sayısal değere göre aynı veya daha küçük boyutta dönüştürülebilir.  
  
    -   **Boole**. Bu tür bir bit veya daha büyük sayısal ya da dize olarak eşlenebilir. Aynı değer için değerlendirilen bir ifade bir sabit değer eşlenebilir (örneğin, `1=1` için SQL'de `True` CLS içinde).  
  
    -   **TimeSpan**. Bu tür iki arasındaki farkı temsil eder `DateTime` değerleri ve gelmiyor `timestamp` SQL Server. CLR <xref:System.TimeSpan?displayProperty=nameWithType> SQL Server'a da eşleyebilir `TIME` bazı durumlarda türü. SQL Server `TIME` türü 24 saatten az pozitif değerleri temsil etmek için yalnızca tasarlanmıştır. CLR <xref:System.TimeSpan> kadar büyük aralığı yok.  
  
    > [!NOTE]
    >  SQL Server'a özgü [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] türlerini <xref:System.Data.SqlTypes> bu Karşılaştırmada dahil edilmez.  
  
-   SQL Server'da uyuşmazlığı:  
  
    -   **Karakter türleri uzunluğu sabit**. Transact-SQL Unicode ve Unicode olmayan kategorilere ayırır ve her kategoride üç ayrı türü vardır: uzunluğu sabit `nchar` / `char`, değişken uzunluğu `nvarchar` / `varchar`, ve daha büyük boyutlu `ntext` / `text`. Sabit uzunluk karakter türleri için CLR eşleştirilebilir <xref:System.Char?displayProperty=nameWithType> almak için tür karakter, ancak bunlar gerçekten aynı türe dönüştürme ve davranışı karşılık gelmez.  
  
    -   **Bit**. Ancak `bit` etki alanına sahip değer olarak aynı sayıda `Nullable<Boolean>`, iki farklı tür aşağıda verilmiştir. `Bit` değerleri alır `1` ve `0` yerine `true` / `false`, Boolean ifadeler için eşdeğer olarak kullanılamaz.  
  
    -   **Zaman damgası**. CLR aksine <xref:System.TimeSpan?displayProperty=nameWithType> türü, SQL Server `TIMESTAMP` türünü temsil eden arasındaki fark temel almaz ve her güncelleştirme için benzersiz olan veritabanı tarafından oluşturulan bir 8-bayt sayısı <xref:System.DateTime> değerleri.  
  
    -   **Para** ve **küçük para**. Bu tür eşlenebilir <xref:System.Decimal> ancak temelde farklı türleri ve bu nedenle, sunucu tabanlı işlevleri ve dönüştürmeler tarafından kabul edilir.  
  
### <a name="multiple-mappings"></a>Birden çok eşlemeleri  
 Bir veya daha fazla CLR veri türleri eşleyebilirsiniz birçok SQL Server veri türleri vardır. Bir veya daha fazla SQL Server türlerini eşleyebilirsiniz birçok CLR türü vardır. LINQ to SQL ile bir eşleme desteklenmiyor olabilir ancak CLR ve SQL Server arasında eşlenen iki tür kusursuz kesinliği, aralık ve semantiği olduğunu gelmez. Bazı eşlemeleri, tüm bu boyutlara farklılıkları içerebilir. Çeşitli eşleme olasılıklara olası farklar hakkındaki ayrıntıları bulabilirsiniz [SQL-CLR tür eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
### <a name="user-defined-types"></a>Kullanıcı tanımlı türler  
 Kullanıcı tanımlı CLR türleri, tür sistem boşluğu yardımcı olmak için tasarlanmıştır. Yine de bunlar türü sürüm oluşturma hakkında ilginç sorunları ortaya çıkarır. İstemci sürümünde değişikliğe veritabanı sunucusunda depolanan tür değişikliği eşlenmesi değil. Herhangi bir değişiklik burada türü anlamları eşleşmeyebilir ve sürüm aralığı görünür hale gelmiş büyük olasılıkla başka bir tür uyuşmazlığı neden olur. Devralma hiyerarşilerini birbirini izleyen sürümlerde yeniden düzenlenen gibi diğer zorluklar oluşur.  
  
## <a name="expression-semantics"></a>İfade semantiği  
 CLR ve veritabanı türler arasında ikili uyuşmazlığı yanı sıra ifadeler için uyuşmazlık karmaşıklık ekleyin. İşleci semantik, işlev semantiği, örtük tür dönüştürme ve öncelik kuralları uyuşmazlıkları dikkate alınmalıdır.  
  
 Aşağıdaki alt bölümleri görünüşe göre benzer ifadeler arasındaki uyumsuzluk göstermektedir. Verilen bir CLR ifade için anlamsal olarak eşdeğer SQL deyimlerini oluşturmak mümkün olabilir. Ancak, bu görünüşe göre benzer ifadeler anlam farklarını CLR kullanıcı için yetkisiz değiştirmeye karşı korumalı olup ve bu nedenle anlam denklik için gerekli olan değişiklikleri veya yöneliktir açık değil. Bir dizi için bir ifade değerlendirildiğinde bu özellikle önemli bir sorundur. Fark görünürlüğünü bağımlı veri - ve kodlama ve hata ayıklama sırasında belirlemek zor olabilir.  
  
### <a name="null-semantics"></a>Null Semantikler  
 SQL deyimleri, Boolean ifadeler için üç değerli mantığı sağlar. Sonucu true, false veya null olabilir. Bunun aksine, CLR iki değerli Boolean sonucu null değerler içeren karşılaştırmaları için belirtir. Aşağıdaki kodu göz önünde bulundurun:  
  
 [!code-csharp[DLinqMismatch#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#2)]
 [!code-vb[DLinqMismatch#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#2)]  
  
```  
-- Assume col1 and col2 are integer columns with null values.   
-- Assume that ANSI null behavior has not been explicitly  
--    turned off.  
Select …  
From …  
Where col1 = col2  
-- Evaluates to null, not true and the corresponding row is not  
--     selected.  
-- To obtain matching behavior (i -> col1, j -> col2) change  
--     the query to the following:  
Select …  
From …  
Where  
    col1 = col2   
or (col1 is null and col2 is null)  
-- (Visual Basic 'Nothing'.)  
```  
  
 İki değerli sonuçlarıyla ilgili varsayım benzer bir sorun oluşur.  
  
 [!code-csharp[DLinqMismatch#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#3)]
 [!code-vb[DLinqMismatch#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#3)]  
  
```  
-- Assume col1 and col2 are nullable columns.  
-- Assume that ANSI null behavior has not been explicitly  
--     turned off.  
Select …  
From …  
Where  
    col1 = col2        
or col1 != col2  
-- Visual Basic: col1 <> col2.  
  
-- Excludes the case where the boolean expression evaluates  
--     to null. Therefore the where clause does not always  
--     evaluate to true.  
```  
  
 Önceki örnekte SQL oluşturma, eşdeğer bir davranış elde edebilirsiniz, ancak çevirisi amacınız doğru yansıtmayabilir.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] değil uygulamaktadır C# `null` veya Visual Basic `nothing` SQL karşılaştırma semantiği. Karşılaştırma işleçleri sözdizimsel olarak SQL eşdeğerlerine dönüştürülür. Sunucu veya bağlantı ayarları tarafından tanımlandığı şekilde, semantiği SQL semantiği yansıtır. (Semantiği değiştirmek için ayarları değiştirebilirsiniz ancak) iki null değerler varsayılan SQL Server Ayarları altında eşit olarak kabul edilir. Ne olursa olsun, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgu çevirisi sunucu ayarlarını dikkate almaz.  
  
 Değişmez değer ile bir karşılaştırması `null` (`nothing`) en uygun SQL sürümüne çevrilir (`is null` veya `is not null`).  
  
 Değerini `null` (`nothing`) harmanlamasında SQL Server tarafından tanımlanır. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] harmanlama değiştirmez.  
  
### <a name="type-conversion-and-promotion"></a>Tür dönüştürme ve yükseltme  
 SQL ifadelerinde zengin örtülü dönüştürmeleri destekler. Benzer ifadelerinde C# açık bir tür dönüştürme gerektirir. Örneğin:  
  
-   `Nvarchar` ve `DateTime` türleri karşılaştırılabilir SQL'de açık tüm atamaları; C# açık dönüştürme gerektirir.  
  
-   `Decimal` örtük olarak dönüştürülür `DateTime` SQL. C#bir örtük dönüştürmelerine izin vermiyor.  
  
 Benzer şekilde, Transact-SQL türü önceliği türü önceliği farklıdır C# temel türleri kümesini farklı olduğu için. Aslında, öncelik listeler arasında NET alt/üst ilişkisi yoktur. Örneğin, karşılaştırma bir `nvarchar` ile bir `varchar` örtük dönüştürülmesi neden `varchar` ifadesine `nvarchar`. CLR hiçbir eşdeğer yükseltme sağlar.  
  
 Basit durumda, bu farklılıkları CLR ifadeler için karşılık gelen bir SQL ifadesi yedekli olacak şekilde yayınları neden. Daha da önemlisi, Ara sonuçlar bir SQL ifadesi örtük olarak hiçbir doğru karşılığı yoktur, bir tür yükseltilmesi C#ve bunun tersi de geçerlidir. Genel olarak, test etme, hata ayıklama ve doğrulama gibi ifadelerin ekler önemli yük kullanıcı.  
  
### <a name="collation"></a>Harmanlama  
 Transact-SQL açık harmanlamaları karakter dize türleri için ek açıklamaları olarak destekler. Bu harmanlamaları belirli karşılaştırmalar geçerliliğini belirler. Örneğin, iki sütun farklı açık harmanlamaları ile karşılaştıran bir hatadır. Basitleştirilmiş çok CTS dize türü kullanımı gibi hataları neden olmaz. Aşağıdaki örnek göz önünde bulundurun:  
  
```  
create table T2 (  
    Col1 nvarchar(10),  
    Col2      nvarchar(10) collate Latin_general_ci_as  
)  
```  
  
 [!code-csharp[DLinqMismatch#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#4)]
 [!code-vb[DLinqMismatch#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#4)]  
  
```  
Select …  
From …  
Where Col1 = Col2  
-- Error, collation conflict.  
```  
  
 Aslında, harmanlama tümce oluşturur bir *kısıtlı türü* değiştirilebilir değildir.  
  
 Benzer şekilde, sıralama türü sistem arasında önemli ölçüde farklı olabilir. Bu farkın, sonuçlarını sıralama etkiler. <xref:System.Guid> tüm 16 bayt sözlük sırasına göre sıralanabilir (`IComparable()`) T-SQL GUID'leri şu sırayla karşılaştırır bilgileriyse: node(10-15) clock-seq(8-9), time-high(6-7) time-mid(4-5), time-low(0-3). Bu sıralama, NT tarafından oluşturulan GUID sekizli böyle bir siparişin başlattıklarında SQL 7. 0'yapıldı. Yaklaşım GUID'leri aynı düğüm kümesi oluşturulan sıralı zaman damgasına göre gelen olmasını sağladı. Yaklaşım (haline ekler yerine rastgele IOs ekler) dizin oluşturma için kullanışlıdır. Daha sonra Windows içinde sırasını Gizlilik sorunları nedeniyle karıştırılmış, ancak SQL uyumluluğu sürdürmeniz gerekir. Geçici bir çözüm kullanmaktır <xref:System.Data.SqlTypes.SqlGuid> yerine <xref:System.Guid>.  
  
### <a name="operator-and-function-differences"></a>İşleç ve işlev farklılıkları  
 İşleçler ve temelde benzer işlevler farenizin farklı semantiklere sahip. Örneğin:  
  
-   C#kısa devre semantiği için mantıksal işleçler işlenenlerin sözcük düzenine dayanan belirtir `&&` ve `||`. SQL, diğer taraftan kümesi tabanlı sorgular için hedeflenen ve bu nedenle iyileştirici yürütme sırası karar özgürlüğü sağlar. Bazı uygulamaları şunlardır:  
  
    -   Anlamsal olarak eşdeğer çeviri gerektirir "`CASE` ... `WHEN` … `THEN`"yeniden sıralama işlenen yürütülmesini önlemek için SQL'de oluşturun.  
  
    -   Gevşek bir çeviri `AND` / `OR` işleçleri, beklenmeyen hatalar neden C# ifade değerlendirme birinci işlenenin sonucuna göre ikinci işlenenin değerlendirmeye kullanır.  
  
-   `Round()` işlev farklı semantiğe sahip [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] ve T-SQL.  
  
-   Dizeler için başlangıç dizini 1'de SQL CLR içinde 0 nesnesidir. Bu nedenle, dizin olan herhangi bir işlev dizin çeviri gerekir.  
  
-   CLR, kayan noktalı sayıları ('%') modulus işleci destekler, ancak SQL yoktur.  
  
-   `Like` İşleci etkili bir şekilde otomatik aşırı örtük dönüştürmeleri temel alır. Ancak `Like` işleci karakter dize türleri, sayısal türleri arasında örtük dönüşüm üzerinde çalışılacak tanımlanır veya `DateTime` türleri ile kullanılmak üzere bu dize olmayan türlerde sağlar `Like` ekleyebiliyorsa. CTS içinde karşılaştırılabilir örtük dönüştürmelerin yok. Bu nedenle, aşırı ek gereklidir.  
  
    > [!NOTE]
    >  Bu `Like` işleci davranışı uygular C# yalnızca; Visual Basic `Like` anahtar sözcüğü, değişmez.  
  
-   Taşma her zaman SQL ile işaretli, ancak açıkça belirtilmesi gerekir C# (içinde olmayan adresle önlemek için VisualBasic). Tamsayı sütunlarını C1, C2 ve C3, C1 + C2 C3 içinde depolanıyorsa, verilen (güncelleştirme T ayarlamak C3 = C1 + C2).  
  
    ```  
    create table T3 (  
        Col1      integer,  
        Col2      integer  
    )  
    insert into T3 (col1, col2) values (2147483647, 5)  
    -- Valid values: max integer value and 5.  
    select * from T3 where col1 + col2 < 0  
    -- Produces arithmetic overflow error.  
    ```  
  
 [!code-csharp[DLinqMismatch#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#5)]
 [!code-vb[DLinqMismatch#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#5)]  
  
-   SQL simetrik aritmetiği gerçekleştirir çalışırken yuvarlama [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] kullandığı banker yuvarlama. Bilgi Bankası makalesi 196652 ek ayrıntılar için bkz.  
  
-   Ortak yerel ayarlar için varsayılan SQL karakter dize karşılaştırmaları duyarsızdır. Visual Basic hem de C#, bunlar büyük küçük harfe duyarlıdır. Örneğin, `s == "Food"` (`s = "Food"` Visual Basic'te) ve `s == "Food"` ise farklı sonuçlar verecek `s` olduğu `food`.  
  
    ```  
    -- Assume default US-English locale (case insensitive).  
    create table T4 (  
        Col1      nvarchar (256)  
    )  
    insert into T4 values (‘Food’)   
    insert into T4 values (‘FOOD’)  
    select * from T4 where Col1 = ‘food’  
    -- Both the rows are returned because of case-insensitive matching.  
    ```  
  
 [!code-csharp[DLinqMismatch#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#6)]
 [!code-vb[DLinqMismatch#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#6)]  
  
-   İşleçler / SQL sabit uzunluk karakter tür bağımsız değişkenleri için uygulanan işlevleri aynı işleçler/CLR ile uygulanan işlevleri daha önemli ölçüde farklı semantiğe sahip <xref:System.String?displayProperty=nameWithType>. Bu da bir uzantısı türleri hakkında bölümünde ele alınan eksik karşılığı sorunu olarak görüntülenmesine.  
  
    ```  
    create table T4 (  
        Col1      nchar(4)  
    )  
    Insert into T5(Col1) values ('21');  
    Insert into T5(Col1) values ('1021');  
    Select * from T5 where Col1 like '%1'  
    -- Only the second row with Col1 = '1021' is returned.  
    -- Not the first row!  
    ```  
  
     [!code-csharp[DLinqMismatch#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#7)]
     [!code-vb[DLinqMismatch#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#7)]  
  
     Dize birleştirme ile benzer bir sorun oluşur.  
  
    ```  
    create table T6 (  
        Col1      nchar(4)  
        Col2       nchar(4)  
    )  
    Insert into T6 values ('a', 'b');  
    Select Col1+Col2 from T6  
    -- Returns concatenation of padded strings "a   b   " and not "ab".  
    ```  
  
 Özet olarak, bir karışık çeviri CLR ifadeler için gerekli olabilir ve ek işleçler/işlevler SQL işlevselliği göstermek gerekli olabilir.  
  
### <a name="type-casting"></a>Tür atama  
 İçinde C# ve SQL'de kullanıcılar ifade varsayılan semantikleri açık tür atamaları kullanarak değiştirebilirsiniz (`Cast` ve `Convert`). Ancak, bu özellik türü sistem sınırından ifşa eden bir ikilemle doğurur. İstenen semantiği sağlar bir SQL atama ilgili bir kolayca çevrilemez C# cast. Öte yandan, bir C# atama doğrudan çevrilemez dönüştürme türü uyuşmazlığı, eksik ortaklarınıza ve farklı tür öncelik hiyerarşileri nedeniyle eşdeğer olan bir SQL oturum. Tür sistemi uyuşmazlığı gösterme ve ifadenin önemli güç kaybı arasında bir ilişki yoktur.  
  
 Diğer durumlarda, tür atama ya da etki alanındaki bir ifadenin doğrulama için gerekli olmayan ancak varsayılan olmayan eşleme ifade doğru uygulandığından emin olmak için gerekli olabilir.  
  
```  
-- Example from "Non-default Mapping" section extended  
create table T5 (  
    Col1      nvarchar(10),  
    Col2      nvarchar(10)  
)  
Insert into T5(col1, col2) values (‘3’, ‘2’);  
```  
  
 [!code-csharp[DLinqMismatch#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#8)]
 [!code-vb[DLinqMismatch#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#8)]  
  
```  
Select *  
From T5  
Where Col1 + Col2 > 4     
-- "Col1 + Col2" expr evaluates to '32'   
```  
  
## <a name="performance-issues"></a>Performans sorunları  
 Bazı SQL Server CLR için hesap türü farkları performans türü sistemleri CLR ve SQL Server arasında geçen zaman neden olabilir. Performansı etkileyen senaryolarına örnekler şunlardır:  
  
-   İçin değerlendirme sırası zorlandı mantıksal ve/veya işleçler  
  
-   Koşul değerlendirme sırası zorlamak için SQL oluşturma, SQL iyileştirici'nin yeteneğini kısıtlar.  
  
-   Tür dönüştürmeleri, nesne ilişkisel sorgu uygulamaya veya bir CLR derleyici tarafından sunulan olmadığını dizin kullanım curtail.  
  
     Örneğin,  
  
    ```  
    -- Table DDL  
    create table T5 (  
        Col1      varchar(100)  
    )  
    ```  
  
     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]  
  
     İfade çevirisini göz önünde bulundurun `(s = SOME_STRING_CONSTANT)`.  
  
    ```  
    -- Corresponding part of SQL where clause  
    Where …  
    Col1 = SOME_STRING_CONSTANT  
    -- This expression is of the form <varchar> = <nvarchar>.  
    -- Hence SQL introduces a conversion from varchar to nvarchar,  
    --     resulting in  
    Where …  
    Convert(nvarchar(100), Col1) = SOME_STRING_CONSTANT  
    -- Cannot use the index for column Col1 for some implementations.  
    ```  
  
 Anlam farklılıklara ek olarak, CLR türü sistemleri ve SQL Server arasında geçen zaman performans etkilerini dikkate almak önemlidir. Büyük veri kümeleri için bu tür performans sorunlarını, uygulama dağıtılabilir olup olmadığını belirleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
