---
title: "SQL CLR türüyle eşleşmiyor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6a027bd898409708dd6800908a6736f5853058df
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="sql-clr-type-mismatches"></a>SQL CLR türüyle eşleşmiyor
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nesne modeli ve SQL Server arasında çeviri çoğunu otomatikleştirir. Bununla birlikte, bazı durumlarda tam çeviri engeller. Bu anahtar uyuşmazlıkları ortak dil çalışma zamanı (CLR) türleri ve SQL Server veritabanı türleri arasında aşağıdaki bölümlerde özetlenmiştir. Belirli tür eşlemeleri ve adresindeki işlevi çevirisi hakkında daha fazla ayrıntı bulabilirsiniz [SQL CLR türü eşleme](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) ve [veri türler ve işlevler](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md).  
  
## <a name="data-types"></a>Veri Türleri  
 Çeviri CLR SQL sunucusu arasındaki bir sorgu veritabanına gönderildiğinde ve sonuçları, nesne modelinde gönderildiğinde oluşur. Örneğin, aşağıdaki Transact-SQL sorgusu iki değer dönüşümler gerektirir:  
  
```  
Select DateOfBirth From Customer Where CustomerId = @id     
```  
  
 SQL Server'da sorgu yürütülebilmesi Transact-SQL parametresi için değer belirtilmelidir. Bu örnekte, `id` parametre değeri gereken ilk dönüştürülür bir CLR <xref:System.Int32?displayProperty=nameWithType> türü SQL Server `INT` veritabanı değeri nedir anlamanız yazın. SQL Server sonuçları almak için `DateOfBirth` SQL Server'dan sütun çevrilen `DATETIME` bir CLR türüne <xref:System.DateTime?displayProperty=nameWithType> nesne modelinde kullanılmak tür. Bu örnekte, CLR nesne modeli ve SQL Server veritabanı türleri doğal eşlemeleri vardır. Ancak, bu her zaman geçerli değildir.  
  
### <a name="missing-counterparts"></a>Ortaklarınıza eksik  
 Aşağıdaki türlerden makul ortaklarınıza gerekmez.  
  
-   CLR eşleşmiyor <xref:System> ad alanı:  
  
    -   **İmzasız tamsayılar**. Bu tür taşması önlemek için imzalanmış dekiler daha büyük boyutta için genellikle eşlenir. Değişmez değerler, imzalı bir sayısal değere göre aynı veya daha küçük boyutu dönüştürülebilir.  
  
    -   **Boolean**. Bu tür bir bit veya daha büyük sayısal veya dize için eşlenebilir. Bir hazır değer aynı değer veren bir ifade eşlenebilir (örneğin, `1=1` için SQL'de `True` CLS içinde).  
  
    -   **TimeSpan**. Bu tür iki arasındaki farkı temsil eder `DateTime` değerleri ve karşılık gelmiyor `timestamp` SQL Server'ın. CLR <xref:System.TimeSpan?displayProperty=nameWithType> SQL Server'a da eşleyebilir `TIME` bazı durumlarda türü. SQL Server `TIME` türü pozitif değer 24 saatten az temsil etmek için yalnızca tasarlanmıştır. CLR <xref:System.TimeSpan> kadar büyük aralığı yok.  
  
    > [!NOTE]
    >  SQL Server'a özgü [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] türlerini <xref:System.Data.SqlTypes> bu karşılaştırma dahil edilmez.  
  
-   SQL Server uyuşmazlıkları:  
  
    -   **Karakter türleri uzunluğu sabit**. Transact-SQL arasında Unicode ve Unicode olmayan kategorilere ayırır ve her kategoride birbirinden farklı üç sahiptir: uzunluğu sabit `nchar` / `char`, değişken uzunlukta `nvarchar` / `varchar`, ve büyük ölçekli `ntext` / `text`. Sabit uzunlukta karakter türleri için CLR eşleştirilebilir <xref:System.Char?displayProperty=nameWithType> alma türü karakterleri, ancak bunlar gerçekten dönüşümler ve davranış aynı türden karşılık değil.  
  
    -   **Bit**. Ancak `bit` etki alanına sahip değerleri olarak aynı sayıda `Nullable<Boolean>`, iki farklı türleridir. `Bit`değerleri alır `1` ve `0` yerine `true` / `false`ve bir Boole ifadeleri eşdeğer olarak kullanılamaz.  
  
    -   **Zaman damgası**. CLR aksine <xref:System.TimeSpan?displayProperty=nameWithType> türü, SQL Server `TIMESTAMP` türünü temsil eder, her güncelleştirme için benzersiz olan ve arasındaki farkı dayanmıyor veritabanı tarafından oluşturulan bir 8 bayt <xref:System.DateTime> değerleri.  
  
    -   **Para** ve **küçük para**. Bu tür eşlenebilir <xref:System.Decimal> ancak temel olarak farklı türleri ve bu nedenle sunucu tabanlı işlevleri ve dönüşümleri tarafından kabul edilir.  
  
### <a name="multiple-mappings"></a>Birden çok eşleme  
 Bir veya daha fazla CLR veri türlerini eşleyebilirsiniz çok SQL Server veri türü vardır. Bir veya daha fazla SQL Server türlerine eşlenir birçok CLR türü vardır. Bir eşleme LINQ-SQL tarafından desteklenebilir rağmen CLR ve SQL Server arasında eşlenen iki tür duyarlık, aralık ve semantiği mükemmel bir eşleşme olduğunu gelmez. Bazı eşlemeler, bu boyutlar bir bölümünü veya tamamını farklılıkları içerebilir. Çeşitli eşleme olasılıklara bu olası farklılıklar ayrıntılarını bulabilirsiniz [SQL CLR türü eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
### <a name="user-defined-types"></a>Kullanıcı tanımlı türler  
 Kullanıcı tanımlı CLR Türleri türü sistem boşluğunu yardımcı olmak için tasarlanmıştır. Yine de ilginç sorunları türü sürüm oluşturma hakkında yüzey. İstemci sürümünde değişikliğe veritabanı sunucusunda depolanan türü değişikliği matched. Bu tür bir değişiklik burada türü anlamları eşleşmeyebilir ve sürüm boşluk görünür hale gelmiştir büyük olasılıkla başka bir tür uyuşmazlığı neden olur. Devralma hiyerarşileri birbirini izleyen sürümlerde bulunanad gibi başka zorluklar oluşur.  
  
## <a name="expression-semantics"></a>İfade semantiği  
 CLR ve veritabanı türleri arasında ikili uyuşmazlığı yanı sıra ifadeleri karmaşıklık uyuşmazlığı ekleyin. İşleç semantiği, işlevi semantiği, örtük tür dönüştürmeleri ve öncelik kuralları uyuşmazlıkları dikkate alınmalıdır.  
  
 Aşağıdaki alt bölümleri görünüşe göre benzer ifadeleri arasındaki uyumsuzluk gösterilmektedir. Verilen bir CLR ifade anlam olarak eşdeğer SQL deyimlerini oluşturmak mümkün olabilir. Ancak, bunu görünüşe göre benzer ifadeleri anlamsal farklarını CLR kullanıcıya korumalı olup olmadığı ve dolayısıyla anlamsal eşdeğer için gerekli olan değişiklikleri amacını taşımaktadır değil NET değil. Bir ifade için değer kümesini değerlendirildiğinde bu özellikle kritik bir sorundur. Fark görünürlüğünü verileri - üzerinde bağlı ve kodlama ve hata ayıklama sırasında belirlemek sabit.  
  
### <a name="null-semantics"></a>Null semantiği  
 SQL deyimleri Boole ifadeleri için üç değerli mantığı sağlar. Sonucu true, false ve null olabilir. Bunun aksine, CLR iki değerli Boole sonucu null değerler içeren karşılaştırmaları için belirtir. Aşağıdaki kod göz önünde bulundurun:  
  
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
  
 İki değerli sonuçlarıyla ilgili varsayımına ile benzer bir sorun oluşur.  
  
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
  
 Önceki örnekte SQL oluşturma, eşdeğer davranışını elde edebilirsiniz, ancak çeviri doğru şekilde amacınız gösterebilir değil.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]C# getirmez `null` veya [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] `nothing` karşılaştırma semantiği SQL'de. Karşılaştırma işleçleri sözdizimsel olarak SQL eşdeğerlerine çevrilir. Sunucu veya bağlantı ayarları tarafından tanımlanan semantiğini SQL semantiği yansıtır. (Semantiğini değiştirmek için ayarları değiştirebilirsiniz, ancak) iki null değerler varsayılan SQL Server Ayarları altında eşit olarak kabul edilir. Ne olursa olsun, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgusu çevirisi sunucu ayarlarını dikkate almaz.  
  
 Değişmez değeri ile bir karşılaştırma `null` (`nothing`) uygun SQL sürümü çevrilir (`is null` veya `is not null`).  
  
 Değeri `null` (`nothing`) harmanlamasında SQL Server tarafından; tanımlanır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] harmanlama değiştirmez.  
  
### <a name="type-conversion-and-promotion"></a>Tür dönüştürmeleri ve yükseltme  
 SQL deyimlerinde örtük dönüşümler zengin bir kümesini destekler. C# benzer ifadeleri açık atama gerektirir. Örneğin:  
  
-   `Nvarchar`ve `DateTime` türleri karşılaştırılabilir SQL'de tüm açık atamaları; C# açık dönüşüm gerektirir.  
  
-   `Decimal`örtük olarak dönüştürülür `DateTime` SQL. C# için örtük bir dönüştürme izin vermiyor.  
  
 Benzer şekilde, temel türleri kümesi farklı olduğundan türü öncelik Transact-SQL C# türü öncelik farklıdır. Aslında, öncelik listeleri arasındaki Temizle alt/üst ilişkisi yoktur. Örneğin, karşılaştırma bir `nvarchar` ile bir `varchar` örtük dönüştürme neden `varchar` ifade `nvarchar`. CLR eşdeğer bir yükseltme sağlar.  
  
 Basit durumda, bu farklılıklar CLR ifadeleri yayınları için karşılık gelen bir SQL ifadesi gereksiz olmasına neden. Daha da önemlisi, bir SQL ifadesi Ara sonuçlarını örtük olarak hiçbir doğru karşılık gelen C# ' ta sahip bir türü yükseltilmesi ve bunun tam tersi. Genel olarak, test, hata ayıklama ve bu tür bir ifade doğrulama ekler önemli yük kullanıcı.  
  
### <a name="collation"></a>Harmanlama  
 Transact-SQL açık harmanlamaları karakter dizesi türleri için ek açıklamaları olarak destekler. Bu harmanlamaları belirli karşılaştırmaları geçerliliğini belirler. Örneğin, iki sütun farklı açık harmanlamaları ile karşılaştıran bir hatadır. Çok Basitleştirilmiş CTS dize türünün kullanımı gibi hataları neden olmaz. Aşağıdaki örnek göz önünde bulundurun:  
  
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
  
 Sonuç harmanlama alt yan tümcesi oluşturur bir *kısıtlanmış türü* değiştirilebilir değil.  
  
 Benzer şekilde, sıralama düzeni türü sistemlerden önemli ölçüde farklı olabilir. Bu farkı sonuçlarını sıralama etkiler. <xref:System.Guid>tüm 16 bayt lexicographic sıraya göre sıralanır (`IComparable()`), T-SQL GUID'lerini aşağıdaki sırayla karşılaştırır ise: node(10-15), clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3). NT tarafından üretilen GUID böyle bir sekizli sipariş varken bu sıralama SQL 7. 0 ' gerçekleştirilir. Yaklaşım aynı düğüm kümesine oluşturulan GUID'ler zaman damgası göre sıralı gelen güvence altına. Yaklaşım da (hale eklemeleri ekler yerine rastgele IOs) dizin oluşturma için yararlıdır. Daha sonra Windows sırasını Gizlilik sorunları nedeniyle karıştırılmış, ancak SQL uyumluluğu korumak gerekir. Geçici bir çözüm kullanmaktır <xref:System.Data.SqlTypes.SqlGuid> yerine <xref:System.Guid>.  
  
### <a name="operator-and-function-differences"></a>İşleç ve işlev farklılıkları  
 İşleçler ve temelde karşılaştırılabilir işlevleri farklý semantiklerine sahip. Örneğin:  
  
-   C# için mantıksal işleçler işlenenler sözcük sırasını dayalı kısa devre semantiği belirtir `&&` ve `||`. SQL kümesini temel alan sorgular için diğer yandan hedeflenen ve bu nedenle yürütme sırasını karar vermek en iyi hale getirme için özgürlüğü sağlar. Etkileri bazıları şunlardır:  
  
    -   Anlam olarak eşdeğer çeviri duyar "`CASE` ... `WHEN` … `THEN`"işlenen yürütülmesi yeniden sıralama önlemek için SQL oluşturun.  
  
    -   Gevşek bir çeviri `AND` / `OR` C# ifade ilk işlenen değerlendirme sonuca bağlı ikinci işlenen değerlendirmeye dayalıysa, işleçler beklenmeyen hatalara neden olabilir.  
  
-   `Round()`işlevi farklı semantiklerine sahip [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] ve T-SQL.  
  
-   Dizeler için başlangıç dizini CLR 0 ancak SQL 1 ' dir. Bu nedenle, dizini içeren herhangi bir işlev dizin çeviri gerekir.  
  
-   CLR ('%') modulus işleci kayan nokta numaraları destekler, ancak SQL desteklemez.  
  
-   `Like` İşleci etkili bir şekilde otomatik aşırı örtük dönüşümler üzerinde temel alır. Rağmen `Like` işleci karakter dizesi türleri, sayısal türler arasında örtük dönüşüm üzerinde çalışılacak tanımlanır veya `DateTime` türlerine izin verir ile kullanılmak üzere bu dize olmayan türlerde için `Like` da. CTS, karşılaştırılabilir örtük dönüşümler yok. Bu nedenle, ek aşırı gereklidir.  
  
    > [!NOTE]
    >  Bu `Like` işleci davranış uygulanır C# Yalnızca; Visual Basic `Like` sözcüktür değişmez.  
  
-   Taşma SQL'de her zaman işaretli ancak C# ' ta açıkça belirtilmesi gerekir (değil, [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) wraparound önlemek için. C1 + C2 C3 içinde depolanıyorsa tamsayı sütunları C1, C2 ve C3, verilen (güncelleştirme T ayarlamak C3 = C1 + C2).  
  
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
  
-   SQL gerçekleştirir simetrik aritmetik sırasında yuvarlama [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] kullandığı banker yuvarlaması. Bilgi Bankası makalesi 196652 ek ayrıntılar için bkz.  
  
-   Ortak yerel ayarlar için varsayılan olarak SQL'de karakter dizesi karşılaştırmaları duyarsızdır. Visual Basic ve C# büyük küçük harfe duyarlıdır. Örneğin, `s == "Food"` (`s = "Food"` içinde [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) ve `s == "Food"` farklı sonuçlar varsa sağlayabilen `s` olan `food`.  
  
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
  
-   İşleçler / sabit uzunlukta karakter türü SQL değişkenlerinde uygulanan işlevleri sahip aynı işleçleri / CLR uygulanan işlevleri daha önemli ölçüde farklı semantiği <xref:System.String?displayProperty=nameWithType>. Bu ayrıca türleri hakkında bölümde açıklanan eksik karşılık gelen sorun uzantısı olarak görüntülenmesine.  
  
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
  
 Özet olarak, karışık bir çeviri CLR ifadeler için gerekli olabilir ve ek işleçleri/işlevler SQL işlevselliği kullanıma sunmak gerekli olabilir.  
  
### <a name="type-casting"></a>Tür atama  
 C# ve SQL, kullanıcılar ifade varsayılan semantikleri açık tür atamaları kullanarak değiştirebilirsiniz (`Cast` ve `Convert`). Ancak, bu özellik türü sistem sınırından gösterme bir ikilemini doğurur. İstenen semantiği sağlar SQL cast kolayca bir karşılık gelen C cast # çevrilemiyor. Öte yandan, bir C# cast doğrudan Tür uyuşmazlıkları, eksik ortaklarınıza ve farklı türe öncelik hiyerarşileri nedeniyle cast bir eşdeğer SQL çevrilemez. Tür sistemi uyuşmazlığı gösterme ve ifadesinin önemli güç kaybı arasında bir denge yoktur.  
  
 Diğer durumlarda, tür atama ya da etki alanında bir ifade doğrulanması için gerekli değil ancak varsayılan olmayan eşleme ifade doğru uygulandığından emin olmak için gerekli olabilir.  
  
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
 Bazı SQL Server CLR için hesap türü farkları performans düşüklüğü resut türü sistemleri CLR ve SQL Server arasında çapraz zaman olabilir. Performansı etkileyen senaryoları örnekleri şunlardır:  
  
-   İçin değerlendirme sırası zorlandı mantıksal ve/veya işleçleri  
  
-   Koşul değerlendirme sırası zorlamak için SQL oluşturma SQL iyileştirici'nin yeteneğini kısıtlar.  
  
-   Tür dönüştürmeleri bir CLR derleyici veya nesne ilişkisel bir sorgu uygulaması tarafından sunulan olup olmadığını dizin kullanım curtail.  
  
     Örneğin,  
  
    ```  
    -- Table DDL  
    create table T5 (  
        Col1      varchar(100)  
    )  
    ```  
  
     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]  
  
     İfade çevirisi göz önünde bulundurun `(s = SOME_STRING_CONSTANT)`.  
  
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
  
 Anlam farklar ek olarak, performans etkileri CLR türü sistemleri ve SQL Server arasında çapraz yaparken göz önünde bulundurmanız önemlidir. Büyük veri kümeleri için bu tür performans sorunlarını uygulama dağıtılabilir olup olmadığını belirleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
