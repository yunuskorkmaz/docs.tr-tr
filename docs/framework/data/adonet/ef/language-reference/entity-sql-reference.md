---
title: Entity SQL Başvurusu
ms.date: 03/30/2017
ms.assetid: 61ce7ee1-ffe2-477d-8a9f-835b0a11d900
ms.openlocfilehash: 75f9c61a24ffdcba890ae04ccc5c656460c13088
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522160"
---
# <a name="entity-sql-reference"></a>Entity SQL Başvurusu

Bu bölüm, Entity SQL Başvurusu makaleler içerir. Bu makalede özetler ve varlık SQL işleçleri kategorilere göre gruplandırır.

## <a name="arithmetic-operators"></a>Aritmetik işleçler

Aritmetik işleçler iki deyim bir veya daha fazla sayısal veri türleri üzerinde matematik işlemleri gerçekleştirir. Entity SQL aritmetik işleçleri aşağıdaki tabloda listelenmektedir:

|İşleç|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|
|--------------|---------|
|[+ (Ekle)](add.md)|Ayrıca.|
|[/ (Böl)](divide-entity-sql.md)|Bölme.|
|[% (Mod)](modulo-entity-sql.md)|Bir bölme işleminden kalanı döndürür.|
|[* (Çarp)](multiply-entity-sql.md)|Çarpma.|
|[- (Negatif)](negative-entity-sql.md)|Değilleme.|
|[- (Çıkar)](subtract-entity-sql.md)|Çıkarma.|

## <a name="canonical-functions"></a>Kurallı İşlevler

Kurallı işlevler ve tüm sorgulanırken teknolojiler tarafından kullanılan tüm veri sağlayıcıları tarafından desteklenir. Aşağıdaki tablo kurallı işlevler listeler:

|İşlev|Tür|
|--------------|----------|
|[Toplam varlık SQL kurallı İşlevler](aggregate-canonical-functions.md)|Entity SQL toplu kurallı işlevler açıklanmaktadır.|
|[Kurallı Matematik İşlevleri](math-canonical-functions.md)|Kurallı matematik varlık SQL işlevleri açıklanır.|
|[Kurallı Dize İşlevleri](string-canonical-functions.md)|Kurallı dize varlık SQL işlevleri açıklanır.|
|[Kurallı Tarih ve Saat İşlevleri](date-and-time-canonical-functions.md)|Tarih ve saat varlık SQL kurallı işlevler açıklanmaktadır.|
|[Bit Düzeyinde Kurallı İşlevler](bitwise-canonical-functions.md)|Entity SQL bit düzeyinde kurallı işlevler açıklanmaktadır.|
|[Diğer Kurallı İşlevler](other-canonical-functions.md)|Bit düzeyinde, tarih, dize, matematik veya toplama sınıflandırılan değil işlevleri açıklanır.|

## <a name="comparison-operators"></a>Karşılaştırma işleçleri

Karşılaştırma işleçleri aşağıdaki türleri için tanımlanır: `Byte`, `Int16`, `Int32`, `Int64`, `Double`, `Single`, `Decimal`, `String`, `DateTime`, `Date`, `Time` , `DateTimeOffset`. Karşılaştırma işleci uygulanmadan önce örtük tür promosyonu işlenenler için gerçekleşir. Karşılaştırma işleçleri, her zaman Boolean değerleri yield. En az bir işlenen olduğunda `null`, sonuç `null`.

Eşitlik ve eşitsizlik kimliği gibi sahip herhangi bir nesne türü için tanımlanmış `Boolean` türü. Kimlik basit olmayan nesnelerle aynı kimliğini paylaştıkları, eşit olarak kabul edilir. Aşağıdaki tabloda, varlık SQL Karşılaştırma işleçleri listelenir:

|İşleç|Açıklama|
|--------------|-----------------|
|[= (Eşittir)](equals-entity-sql.md)|İki ifadenin eşitlik karşılaştırır.|
|[> (Büyüktür)](greater-than-entity-sql.md)|Sol ifade sağ ifade daha büyük bir değere sahip olup olmadığını belirlemek için iki deyim karşılaştırır.|
|[>= (Büyüktür veya Eşittir)](greater-than-or-equal-to-entity-sql.md)|Sol ifade sağ ifade eşit veya büyük bir değer olup olmadığını belirlemek için iki deyim karşılaştırır.|
|[OLAN \[DEĞİL\] NULL](isnull-entity-sql.md)|Sorgu ifadesi null olup olmadığını belirler.|
|[< (Küçüktür)](less-than-entity-sql.md)|Sol ifade sağ ifade'den küçük bir değere sahip olup olmadığını belirlemek için iki deyim karşılaştırır.|
|[<= (Küçüktür veya Eşittir)](less-than-or-equal-to-entity-sql.md)|Sol ifade düşük bir değere eşit veya ondan sağ ifade olup olmadığını belirlemek için iki deyim karşılaştırır.|
|[\[DEĞİL\] BETWEEN](between-entity-sql.md)|Bir ifadenin belirtilen bir aralıktaki bir değer sonuçlanıp sonuçlanmayacağını belirler.|
|[\!= (Eşit değildir)](not-equal-to-entity-sql.md)|Sol ifade doğru ifade eşit değilse olup olmadığını belirlemek için iki deyim karşılaştırır.|
|[\[DEĞİL\] GİBİ](like-entity-sql.md)|Belirli bir karakter dizesi belirtilen desenle eşleşip eşleşmediğini belirler.|

## <a name="logical-and-case-expression-operators"></a>Mantıksal ve büyük/küçük harf ifade işleçleri

Mantıksal işleçler, basit bir koşul için test edin. CASE ifadesi sonucu belirlemek için Boolean ifadeler bir dizi olarak değerlendirilir. Aşağıdaki tabloda, mantıksal ve büyük/küçük harf ifade işleçleri listelenmektedir:

|İşleç|Açıklama|
|--------------|-----------------|
|[& & (Mantıksal ve)](and-entity-sql.md)|Mantıksal and|
|[\! (Mantıksal değil)](not-entity-sql.md)|Mantıksal değil.|
|[&#124;&#124;(Mantıksal veya)](or-entity-sql.md)|Mantıksal OR.|
|[CASE](case-entity-sql.md)|Boolean ifadeleri sonucu belirlemek için bir dizi olarak değerlendirilir.|
|[THEN](then-entity-sql.md)|Sonucu bir [OLDUĞUNDA](https://msdn.microsoft.com/library/6233fe9f-00b0-460e-8372-64e138a5f998) doğru olarak değerlendirildiğinde yan tümcesi.|

## <a name="query-operators"></a>Sorgu işleçleri

Sorgu işleçleri, varlık veri döndüren sorgu ifadeleri tanımlamak için kullanılır. Aşağıdaki tabloda, sorgu işleçleri listelenir:

|İşleç|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|
|--------------|---------|
|[FROM](from-entity-sql.md)|Kullanılan toplama belirtir [seçin](select-entity-sql.md) deyimleri.|
|[GROUP BY](group-by-entity-sql.md)|Hangi nesnelerin, bir sorgu tarafından döndürülür grupları belirtir ([seçin](select-entity-sql.md)) ifade olan yerleştirilecek.|
|[Grouppartıtıon](grouppartition-entity-sql.md)|Bağımsız değişken değerleri toplama ilgili olduğu grubu bölümü öngörülen koleksiyonunu döndürür.|
|[HAVING](having-entity-sql.md)|Bir toplama veya bir grup için bir arama koşulu belirtir.|
|[LIMIT](limit-entity-sql.md)|İle kullanılan [ORDER BY](order-by-entity-sql.md) gerçekleştirilen fiziksel disk belleği yan tümcesi.|
|[ORDER BY](order-by-entity-sql.md)|Döndürülen nesneler üzerinde kullanılan sıralama düzeni belirtir. bir [seçin](select-entity-sql.md) deyimi.|
|[SELECT](select-entity-sql.md)|Bir sorgu tarafından döndürülen projeksiyon öğeleri belirtir.|
|[SKIP](skip-entity-sql.md)|İle kullanılan [ORDER BY](order-by-entity-sql.md) gerçekleştirilen fiziksel disk belleği yan tümcesi.|
|[TOP](top-entity-sql.md)|Yalnızca ilk satır kümesini sorgu sonuç döndüren belirtir.|
|[WHERE](where-entity-sql.md)|Koşullu olarak bir sorgu tarafından döndürülen veri filtreler.|

## <a name="reference-operators"></a>Başvuru işleçleri

Bir mantıksal bir işaretçi (yabancı anahtar) özel varlık kümesinde belirli bir varlığa başvurudur. Entity SQL oluşturmak, ayrıştırma ve başvuruları arasında gezinmek için aşağıdaki işleçleri destekler:

|İşleç|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|
|--------------|---------|
|[CREATEREF](createref-entity-sql.md)|Bir varlık başvuruları içinde bir varlık kümesini oluşturur.|
|[DEREF](deref-entity-sql.md)|Bir başvuru değeri ve bu sonucu başvuru oluşturur başvurusunu kaldırır.|
|[KEY](key-entity-sql.md)|Bir başvuru veya varlık ifade anahtarını ayıklar.|
|[NAVIGATE](navigate-entity-sql.md)|Bir varlık türü arasında ilişki üzerinden gitmenizi sağlar|
|[REF](ref-entity-sql.md)|Bir varlık örneği için bir başvuru döndürür.|

## <a name="set-operators"></a>Küme işleci

Entity SQL çeşitli güçlü işlemler sağlar. Bu küme işleci Transact-SQL işleçleri UNION, INTERSECT veya EXCEPT, gibi benzer içerir ve mevcut. Entity SQL yinelenen eleme (SET), üyelik (gelen) test etme ve birleşimler (birleştirme) işleçleri de destekler. Entity SQL kümesi işleçleri aşağıdaki tabloda listelenmektedir:

|İşleç|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|
|--------------|---------|
|[ANYELEMENT](anyelement-entity-sql.md)|Birden çok değerli bir koleksiyondan bir öğe ayıklar.|
|[EXCEPT](except-entity-sql.md)|Ayrıca sorgu ifadesinden EXCEPT işlecinin sağ için döndürülen olmayan EXCEPT işlecinin sol sorgu ifadesinden farklı değerleri koleksiyonunu döndürür.|
|[\[DEĞİL\] EXISTS](exists-entity-sql.md)|Bir koleksiyonu boş olup olmadığını belirler.|
|[FLATTEN](flatten-entity-sql.md)|Değişkeninin bir koleksiyonlar koleksiyonu düzleştirilmiş bir koleksiyonuna dönüştürür.|
|[\[DEĞİL\] GİRİŞ](in-entity-sql.md)|Değer bir koleksiyondaki herhangi bir değer ile eşleşip eşleşmediğini belirler.|
|[INTERSECT](intersect-entity-sql.md)|INTERSECT işlecinin sol tarafında soldaki iki sorgu ifadeleri tarafından döndürülen herhangi ayrı değerlerin bir koleksiyonunu döndürür.|
|[OVERLAPS](overlaps-entity-sql.md)|İki koleksiyon ortak öğeler sahip olup olmadığını belirler.|
|[SET](set-entity-sql.md)|Kaldırılan tüm yinelenen öğeleri ile yeni bir koleksiyon sonuçlanmıyor tarafından bir küme içine nesneler koleksiyonunu dönüştürmek için kullanılır.|
|[UNION](union-entity-sql.md)|İki veya daha fazla sorguların sonuçlarını tek bir koleksiyon birleştirir.|

## <a name="type-operators"></a>Tür işleçleri

Varlık SQL türü oluşturulan, sorgulanan ve yönetilebilir ifadesinin (değer) izin işlemleri sağlar. Aşağıdaki tabloda türleriyle çalışmak için kullanılan işleçleri listelenir:

|İşleç|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|
|--------------|---------|
|[CAST](cast-entity-sql.md)|Bir veri türündeki bir ifade diğerine dönüştürür.|
|[COLLECTION](collection-entity-sql.md)|Kullanılan bir [işlevi](function-entity-sql.md) varlık türleri veya karmaşık türler koleksiyonu bildirmek için işlemi.|
|[OLAN \[DEĞİL\] SONU](isof-entity-sql.md)|Belirtilen tür veya onun alt türlerinden birini bir ifadenin türü olup olmadığını belirler.|
|[OFTYPE](oftype-entity-sql.md)|Belirli bir tür bir sorgu ifadesinden nesnelerinin bir koleksiyonunu döndürür.|
|[Adlandırılmış Tür Oluşturucu](named-type-constructor-entity-sql.md)|Varlık türleri veya karmaşık türler örneklerini oluşturmak için kullanılır.|
|[MULTISET](multiset-entity-sql.md)|Değerler listesinden bir çoklu küme örneği oluşturur.|
|[ROW](row-entity-sql.md)|Bir veya daha fazla değer anonim, yapısal olarak belirlenmiş kayıtları oluşturur.|
|[TREAT](treat-entity-sql.md)|Belirli bir temel türü bir nesneyi belirtilen türetilmiş bir türde bir nesne olarak değerlendirir.|

## <a name="other-operators"></a>Diğer işleçler

Aşağıdaki tabloda diğer varlık SQL işleçleri listelenir:

|İşleç|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|
|--------------|---------|
|[+ (Dize Birleştirme)](string-concatenation-entity-sql.md)|Entity SQL dizeyi birleştirmek için kullanılır.|
|[. (Üye Erişimi)](member-access-entity-sql.md)|Bir özellik veya alan yapısal kavramsal model türünün bir örneği, değere erişmek için kullanılır.|
|[-- (Yorum)](comment-entity-sql.md)|Entity SQL açıklamaları içerir.|
|[FUNCTION](function-entity-sql.md)|Bir varlık SQL sorgusu yürütülebilecek bir satır içi işlevi tanımlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Entity SQL Dili](entity-sql-language.md)
