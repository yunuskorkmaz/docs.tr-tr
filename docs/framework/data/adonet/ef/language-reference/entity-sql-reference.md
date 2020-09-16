---
title: Entity SQL başvurusu
ms.date: 03/30/2017
ms.assetid: 61ce7ee1-ffe2-477d-8a9f-835b0a11d900
ms.openlocfilehash: 987aa5c05b88d684e050721077d704b29e546aab
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90542130"
---
# <a name="entity-sql-reference"></a>Entity SQL başvurusu

Bu bölüm Entity SQL başvuru makaleleri içerir. Bu makale, Entity SQL işleçlerini kategoriye göre özetler ve gruplandırır.

## <a name="arithmetic-operators"></a>Aritmetik İşleçler

Aritmetik işleçler bir veya daha fazla sayısal veri türünün iki ifadesi üzerinde matematik işlemleri gerçekleştirir. Aşağıdaki tabloda Entity SQL aritmetik işleçler listelenmektedir:

|Operatör|Kullanın|
|--------------|---------|
|[+ (Ekle)](add.md)|Ek olarak.|
|[(Böl)](divide-entity-sql.md)|Bölmenin.|
|[% (Mod)](modulo-entity-sql.md)|Bir bölme işleminden kalanı döndürür.|
|[* (Çarp)](multiply-entity-sql.md)|Anda.|
|[- (Negatif)](negative-entity-sql.md)|Anlaşma.|
|[- (Çıkar)](subtract-entity-sql.md)|StrA.|

## <a name="canonical-functions"></a>Kurallı işlevler

Kurallı işlevler tüm veri sağlayıcıları tarafından desteklenir ve tüm sorgulama teknolojileri tarafından kullanılabilir. Aşağıdaki tabloda kurallı işlevler listelenmektedir:

|İşlev|Tür|
|--------------|----------|
|[Entity SQL kurallı Işlevleri toplama](aggregate-canonical-functions.md)|Kurallı Entity SQL işlevlerini açıklar.|
|[Kurallı Matematik İşlevleri](math-canonical-functions.md)|Matematik Entity SQL kurallı işlevleri ele alır.|
|[Kurallı Dize İşlevleri](string-canonical-functions.md)|Kurallı Entity SQL dize ve kurallı işlevleri açıklar.|
|[Kurallı Tarih ve Saat İşlevleri](date-and-time-canonical-functions.md)|Kurallı işlevleri Entity SQL tarih ve saat açıklanmaktadır.|
|[Bit Düzeyinde Kurallı İşlevler](bitwise-canonical-functions.md)|Bit düzeyinde Entity SQL kurallı işlevleri açıklar.|
|[Diğer Kurallı İşlevler](other-canonical-functions.md)|Bit düzeyinde, tarih/saat, dize, matematik veya toplama olarak sınıflandırılmayan işlevleri açıklar.|

## <a name="comparison-operators"></a>Karşılaştırma işleçleri

Karşılaştırma işleçleri aşağıdaki türler için tanımlanmıştır: `Byte` ,,, `Int16` , `Int32` `Int64` `Double` , `Single` , `Decimal` , `String` , `DateTime` , `Date` , `Time` , `DateTimeOffset` . Karşılaştırma işleci uygulanmadan önce işlenenler için örtük tür yükseltme oluşur. Karşılaştırma işleçleri her zaman Boole değerleri verir. İşlenenlerinden en az biri olduğunda `null` , sonuç olur `null` .

Eşitlik ve eşitsizlik, türü gibi kimliği olan herhangi bir nesne türü için tanımlanır `Boolean` . Kimliği olan temel olmayan nesneler aynı kimliği paylaşıyorsa eşit kabul edilir. Aşağıdaki tabloda Entity SQL karşılaştırma işleçleri listelenmektedir:

|İşleç|Açıklama|
|--------------|-----------------|
|[= (Eşittir)](equals-entity-sql.md)|İki ifadenin eşitliğini karşılaştırır.|
|[> (Büyüktür)](greater-than-entity-sql.md)|Sol ifadenin sağ ifadeden daha büyük bir değere sahip olup olmadığını anlamak için iki ifadeyi karşılaştırır.|
|[>= (büyüktür veya eşittir)](greater-than-or-equal-to-entity-sql.md)|Sol ifadenin sağ ifadeden büyük veya ona eşit bir değere sahip olup olmadığını anlamak için iki ifadeyi karşılaştırır.|
|[\[null değil \]](isnull-entity-sql.md)|Sorgu ifadesinin null olup olmadığını belirler.|
|[< (Küçüktür)](less-than-entity-sql.md)|Sol ifadenin doğru ifadeden daha küçük bir değere sahip olup olmadığını anlamak için iki ifadeyi karşılaştırır.|
|[<= (Küçüktür veya Eşittir)](less-than-or-equal-to-entity-sql.md)|Sol ifadenin doğru ifadeye eşit veya ondan küçük bir değere sahip olup olmadığını anlamak için iki ifadeyi karşılaştırır.|
|[\[\]ARALARıNDA değil](between-entity-sql.md)|Bir ifadenin belirtilen aralıktaki bir değer ile sonuçlanıp sonuçlanmadığını belirler.|
|[\!= (Eşit değildir)](not-equal-to-entity-sql.md)|Sol ifadenin sağ ifadeye eşit olup olmadığını anlamak için iki ifadeyi karşılaştırır.|
|[\[\]BEĞENMIYOR](like-entity-sql.md)|Belirli bir karakter dizesinin belirtilen bir Düzenle eşleşip eşleşmediğini belirler.|

## <a name="logical-and-case-expression-operators"></a>Mantıksal ve Case ifade işleçleri

Mantıksal işleçler bir koşulun gerçeği için test. CASE ifadesi sonucu belirleyecek bir dizi Boole ifadesi değerlendirir. Aşağıdaki tabloda mantıksal ve CASE ifade işleçleri listelenmektedir:

|İşleç|Açıklama|
|--------------|-----------------|
|[&&  (mantıksal AND)](and-entity-sql.md)|Mantıksal AND.|
|[\! (Mantıksal DEĞIL)](not-entity-sql.md)|Mantıksal DEĞIL.|
|[&#124;&#124;  (mantıksal veya)](or-entity-sql.md)|Mantıksal OR.|
|[HARFLERINI](case-entity-sql.md)|Sonucu tespit etmek için bir dizi Boole ifadesi değerlendirir.|
|[NI](then-entity-sql.md)|True olarak [değerlendirildiğinde bir WHERE](/previous-versions/dotnet/netframework-4.0/bb387119(v=vs.100)) yan tümcesinin sonucu.|

## <a name="query-operators"></a>Sorgu işleçleri

Sorgu işleçleri, varlık verileri döndüren sorgu ifadelerini tanımlamak için kullanılır. Aşağıdaki tabloda sorgu işleçleri listelenmektedir:

|Operatör|Kullanın|
|--------------|---------|
|[FROM](from-entity-sql.md)|[Select](select-entity-sql.md) deyimlerinde kullanılan koleksiyonu belirtir.|
|[GROUP BY](group-by-entity-sql.md)|Bir sorgu ([Select](select-entity-sql.md)) ifadesi tarafından döndürülen nesnelerin yerleştirileceği grupları belirtir.|
|[GROUPPARTITION](grouppartition-entity-sql.md)|Toplamanın ilişkili olduğu grup bölümünü tahmin eden bağımsız değişken değerlerinin bir koleksiyonunu döndürür.|
|[HAVING](having-entity-sql.md)|Grup veya toplama için bir arama koşulu belirtir.|
|[SıNıRLı](limit-entity-sql.md)|Fiziksel disk belleği gerçekleştirmeyen [order by](order-by-entity-sql.md) yan tümcesi ile kullanılır.|
|[SİPARİŞ VEREN](order-by-entity-sql.md)|Bir [Select](select-entity-sql.md) ifadesinde döndürülen nesnelerde kullanılan sıralama düzenini belirtir.|
|[SEÇIN](select-entity-sql.md)|Bir sorgu tarafından döndürülen projeksiyondaki öğeleri belirtir.|
|[ŞIMDILIK](skip-entity-sql.md)|Fiziksel disk belleği gerçekleştirmeyen [order by](order-by-entity-sql.md) yan tümcesi ile kullanılır.|
|[Sayfanın Üstü](top-entity-sql.md)|Sorgu sonucundan yalnızca ilk satır kümesinin döndürüleceğini belirtir.|
|[WHERE](where-entity-sql.md)|Bir sorgu tarafından döndürülen verileri koşullu olarak filtreler.|

## <a name="reference-operators"></a>Başvuru işleçleri

Başvuru, belirli bir varlık kümesindeki belirli bir varlığa yönelik mantıksal bir işaretçisidir (yabancı anahtardır). Entity SQL, başvuruları oluşturmak, oluşturmak ve bunlar arasında gezinmek için aşağıdaki işleçleri destekler:

|Operatör|Kullanın|
|--------------|---------|
|[CREATEREF](createref-entity-sql.md)|Bir varlık kümesindeki bir varlığa başvurular oluşturur.|
|[DEREF](deref-entity-sql.md)|Başvuru değerine başvurur ve başvurunun sonucunu üretir.|
|[ANAHTAR](key-entity-sql.md)|Başvurunun veya bir varlık ifadesinin anahtarını ayıklar.|
|[GEÇMEK](navigate-entity-sql.md)|Bir varlık türünden diğerine ilişki üzerinde gezinmeniz sağlar|
|[REF](ref-entity-sql.md)|Bir varlık örneğine bir başvuru döndürür.|

## <a name="set-operators"></a>İşleç ayarla

Entity SQL, çeşitli güçlü ayarlama işlemleri sağlar. Bu, UNıON, ıNTERSECT, EXCEPT ve var gibi Transact-SQL işleçleriyle benzerlik olarak ayarlanan işleçleri içerir. Entity SQL Ayrıca, yinelenen eleme (SET), üyelik testi (IÇINDE) ve birleşimler (JOIN) için işleçleri de destekler. Aşağıdaki tablo Entity SQL set işleçlerini listeler:

|Operatör|Kullanın|
|--------------|---------|
|[ANYELEMENT](anyelement-entity-sql.md)|Çok değerli bir koleksiyondan bir öğe ayıklar.|
|[EXCEPT](except-entity-sql.md)|Sorgu ifadesinden, EXCEPT işlecinin sağına doğru bir şekilde döndürülmeyen EXCEPT işlecinin soluna ait farklı değerlerin bir koleksiyonunu döndürür.|
|[\[YOK \]](exists-entity-sql.md)|Bir koleksiyonun boş olup olmadığını belirler.|
|[LEŞTIREBILIR](flatten-entity-sql.md)|Bir koleksiyon koleksiyonunu düzleştirilmiş bir koleksiyona dönüştürür.|
|[\[NOT \] ın](in-entity-sql.md)|Bir değerin bir koleksiyondaki herhangi bir değerle eşleşip eşleşmediğini belirler.|
|[INTERSECT](intersect-entity-sql.md)|INTERSECT işleneninin sol ve sağ taraflarındaki sorgu ifadeleri tarafından döndürülen ayrı değerlerin bir koleksiyonunu döndürür.|
|[OVERLAPS](overlaps-entity-sql.md)|İki koleksiyonun ortak öğelere sahip olup olmadığını belirler.|
|[KURMAK](set-entity-sql.md)|Yinelenen öğeleri kaldırılmış şekilde yeni bir koleksiyon oluşturarak bir nesne koleksiyonunu bir kümesine dönüştürmek için kullanılır.|
|[BIRLEŞIM](union-entity-sql.md)|İki veya daha fazla sorgunun sonuçlarını tek bir koleksiyonda birleştirir.|

## <a name="type-operators"></a>Tür işleçleri

Entity SQL, bir ifade türünün (değer) oluşturulmasını, sorgulanmasını ve yerine işleneceğini sağlayan işlemler sağlar. Aşağıdaki tabloda, türleriyle çalışmak için kullanılan işleçler listelenmektedir:

|Operatör|Kullanın|
|--------------|---------|
|[CAST](cast-entity-sql.md)|Bir veri türündeki bir ifadeyi bir diğerine dönüştürür.|
|[KOLEKSIYON](collection-entity-sql.md)|Bir [işlev](function-entity-sql.md) işleminde varlık türleri veya karmaşık türler koleksiyonunu bildirmek için kullanılır.|
|[Şu \[ değil \]](isof-entity-sql.md)|Bir ifadenin türünün belirtilen türde mi yoksa alt türlerinden biri mi olduğunu belirler.|
|[OFTYPE](oftype-entity-sql.md)|Belirli türde olan bir sorgu ifadesinden bir nesne koleksiyonu döndürür.|
|[Adlandırılmış Tür Oluşturucu](named-type-constructor-entity-sql.md)|Varlık türlerinin veya karmaşık türlerin örneklerini oluşturmak için kullanılır.|
|[MULTISET](multiset-entity-sql.md)|Bir değer listesinden bir çoklu küme örneği oluşturur.|
|[ROW](row-entity-sql.md)|Bir veya daha fazla değerden anonim, yapısal olarak yazılmış kayıtlar oluşturur.|
|[TREAT](treat-entity-sql.md)|Belirli bir temel türdeki bir nesneyi belirtilen türetilmiş türün bir nesnesi olarak değerlendirir.|

## <a name="other-operators"></a>Diğer işleçler

Aşağıdaki tablo diğer Entity SQL işleçlerini listeler:

|Operatör|Kullanın|
|--------------|---------|
|[+ (Dize Birleştirme)](string-concatenation-entity-sql.md)|Entity SQL dizeleri birleştirmek için kullanılır.|
|[. (Üye erişimi)](member-access-entity-sql.md)|Yapısal kavramsal model türü örneğinin bir özelliğinin veya alanının değerine erişmek için kullanılır.|
|[-- (Yorum)](comment-entity-sql.md)|Entity SQL açıklamalarını dahil edin.|
|[ÇALıŞMAYACAKTıR](function-entity-sql.md)|Bir Entity SQL sorgusunda yürütülebilecek bir satır içi işlevi tanımlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Dili](entity-sql-language.md)
