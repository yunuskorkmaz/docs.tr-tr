---
title: Varlık SQL Başvurusu
ms.date: 03/30/2017
ms.assetid: 61ce7ee1-ffe2-477d-8a9f-835b0a11d900
ms.openlocfilehash: 79cdf35128ac35920797060b09ff2fc5999708a7
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37028025"
---
# <a name="entity-sql-reference"></a>Varlık SQL Başvurusu

Bu bölüm, varlık SQL başvuru makaleleri içerir. Bu makalede özetler ve varlık SQL işleçleri kategoriye göre gruplandırır.

## <a name="arithmetic-operators"></a>Aritmetik işleçler

Aritmetik işleçler bir veya daha fazla sayısal veri türleri iki ifadeye matematik işlemleri gerçekleştirir. Aşağıdaki tabloda, varlık SQL aritmetik işleçler listelenmektedir:

|İşleç|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|
|--------------|---------|
|[+ (Ekle)](add.md)|Ayrıca.|
|[/ (Böl)](divide-entity-sql.md)|Bölme.|
|[% (Modül)](modulo-entity-sql.md)|Bölme kalanı döndürür.|
|[* (Çarp)](multiply-entity-sql.md)|Çarpma.|
|[- (Negatif)](negative-entity-sql.md)|Değilleme.|
|[- (Çıkar)](subtract-entity-sql.md)|Çıkarma.|

## <a name="canonical-functions"></a>Kurallı işlevleri

Kurallı işlevleri tüm veri sağlayıcıları tarafından desteklenir ve tüm sorgulanırken teknolojileri ile kullanılabilir. Aşağıdaki tabloda kurallı işlevleri listelenmektedir:

|İşlev|Tür|
|--------------|----------|
|[Birleşik varlık SQL kurallı işlevleri](aggregate-canonical-functions.md)|Toplama varlık SQL kurallı işlevleri açıklanır.|
|[Kurallı Matematik İşlevleri](math-canonical-functions.md)|Matematik varlık SQL kurallı işlevleri açıklanır.|
|[Kurallı Dize İşlevleri](string-canonical-functions.md)|Dize varlığı SQL kurallı işlevleri açıklanır.|
|[Kurallı Tarih ve Saat İşlevleri](date-and-time-canonical-functions.md)|Tarih ve saat varlık SQL kurallı işlevleri açıklanır.|
|[Bit Düzeyinde Kurallı İşlevler](bitwise-canonical-functions.md)|Bit düzeyinde varlık SQL kurallı işlevleri açıklanır.|
|[Diğer Kurallı İşlevler](other-canonical-functions.md)|Bit düzeyinde, tarih, dize, matematik veya toplu olarak sınıflandırılan değil işlevleri açıklanır.|

## <a name="comparison-operators"></a>Karşılaştırma işleçleri

Karşılaştırma işleçleri şu türler için tanımlanır: `Byte`, `Int16`, `Int32`, `Int64`, `Double`, `Single`, `Decimal`, `String`, `DateTime`, `Date`, `Time` , `DateTimeOffset`. Karşılaştırma işleci uygulanmadan önce örtük tür yükseltme işlenenler için oluşur. Karşılaştırma işleçleri her zaman Boole değerleri verim. İşlenen en az biri olduğunda `null`, sonuç `null`.

Eşitlik ve eşitsizlik gibi kimliğine sahip nesne türü için tanımlanmış `Boolean` türü. Kimliğine sahip olmayan ilkel nesneleri aynı kimliğe paylaşıyorsanız eşit olarak kabul edilir. Aşağıdaki tabloda, varlık SQL Karşılaştırma işleçleri listelenmektedir:

|İşleç|Açıklama|
|--------------|-----------------|
|[= (Eşittir)](equals-entity-sql.md)|İki ifadeye eşitliğini karşılaştırır.|
|[> (Büyüktür)](greater-than-entity-sql.md)|Sol ifade sağ ifade büyük bir değere sahip olup olmadığını belirlemek için iki ifadeye karşılaştırır.|
|[>= (Büyüktür veya Eşittir)](greater-than-or-equal-to-entity-sql.md)|Sol ifade sağ ifade eşit veya daha büyük bir değere sahip olup olmadığını belirlemek için iki ifadeye karşılaştırır.|
|[OLAN &AMP;#91;DEĞİL&AMP;#93; NULL](isnull-entity-sql.md)|Bir sorgu ifadesi null olup olmadığını belirler.|
|[< (Küçüktür)](less-than-entity-sql.md)|Sol ifade sağ ifade'den küçük bir değer olup olmadığını belirlemek için iki ifadeye karşılaştırır.|
|[<= (Küçüktür veya Eşittir)](less-than-or-equal-to-entity-sql.md)|Sol ifade bir değere eşit veya sağ ifade için olup olmadığını belirlemek için iki ifadeye karşılaştırır.|
|[&AMP;#91;DEĞİL&AMP;#93; BETWEEN](between-entity-sql.md)|Belirtilen aralıktaki bir değere bir ifade sonucu olup olmadığını belirler.|
|[!= (Eşit Değildir)](not-equal-to-entity-sql.md)|Sol ifade sağ ifade eşit değil olup olmadığını belirlemek için iki ifadeye karşılaştırır.|
|[&AMP;#91;DEĞİL&AMP;#93; GİBİ](like-entity-sql.md)|Bir özel karakter dizesi belirtilen desenle eşleşip eşleşmediğini belirler.|

## <a name="logical-and-case-expression-operators"></a>Mantıksal ve büyük/küçük harfe ifade işleçleri

Mantıksal işleçler bir koşul gerçekte için test edin. Servis talebi ifade sonucu belirlemek için Boole ifadeleri kümesi olur. Aşağıdaki tabloda, mantıksal ve büyük/küçük HARFE ifadesi işleçleri listeler:

|İşleç|Açıklama|
|--------------|-----------------|
|[& & (Mantıksal ve)](and-entity-sql.md)|Mantıksal and|
|[! (Mantıksal değil)](not-entity-sql.md)|Mantıksal değil.|
|[&#124;&#124;(Mantıksal OR)](or-entity-sql.md)|Mantıksal OR.|
|[CASE](case-entity-sql.md)|Boole ifadeleri sonucu belirlemek için bir dizi değerlendirir.|
|[THEN](then-entity-sql.md)|Sonucunu bir [zaman](http://msdn.microsoft.com/library/6233fe9f-00b0-460e-8372-64e138a5f998) doğru olarak değerlendirildiğinde yan tümcesi.|

## <a name="query-operators"></a>Sorgu işleçleri

Sorgu işleçleri, varlık veri döndüren sorgu ifadeleri tanımlamak için kullanılır. Aşağıdaki tabloda, sorgu işleçleri listelenmektedir:

|İşleç|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|
|--------------|---------|
|[FROM](from-entity-sql.md)|Kullanılan koleksiyon belirtir [seçin](select-entity-sql.md) deyimleri.|
|[GROUP BY](group-by-entity-sql.md)|Hangi nesneleri, bir sorgu tarafından döndürülür grupları belirtir ([seçin](select-entity-sql.md)) ifade olan yerleştirilecek.|
|[Grouppartıtıon](grouppartition-entity-sql.md)|Bağımsız değişken değerleri toplama ilgili olduğu Grup bölümünün öngörülen koleksiyonunu döndürür.|
|[HAVING](having-entity-sql.md)|Bir grup veya bir toplama için bir arama koşulu belirtir.|
|[LIMIT](limit-entity-sql.md)|İle kullanılan [ORDER BY](order-by-entity-sql.md) gerçekleştirilen fiziksel disk belleği yan tümcesini.|
|[ORDER BY](order-by-entity-sql.md)|Döndürülen nesneler üzerinde kullanılan sıralama düzenini belirleyen bir [seçin](select-entity-sql.md) deyimi.|
|[SELECT](select-entity-sql.md)|Öğeleri bir sorgu tarafından döndürülen projeksiyon belirtir.|
|[SKIP](skip-entity-sql.md)|İle kullanılan [ORDER BY](order-by-entity-sql.md) gerçekleştirilen fiziksel disk belleği yan tümcesini.|
|[TOP](top-entity-sql.md)|Yalnızca ilk satır kümesini sorgu sonuç döndürülür belirtir.|
|[WHERE](where-entity-sql.md)|Koşullu bir sorgu tarafından döndürülen veri filtreler.|

## <a name="reference-operators"></a>Başvuru işleçleri

Belirli bir varlık kümesinde belirli bir varlık için bir mantıksal işaretçisi (yabancı anahtar) başvurudur. Varlık SQL oluşturmak, deconstruct ve başvurular arasında gezinmek için aşağıdaki işleçleri destekler:

|İşleç|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|
|--------------|---------|
|[CREATEREF](createref-entity-sql.md)|Bir varlık başvuruları bir varlık kümesi oluşturur.|
|[DEREF](deref-entity-sql.md)|Bir başvuru değer ve başvuru sonucu, üretir dereferences.|
|[KEY](key-entity-sql.md)|Bir başvuru veya varlık ifade anahtarını ayıklar.|
|[NAVIGATE](navigate-entity-sql.md)|Bir varlık türü arasında ilişki üzerinden giderek sağlar|
|[REF](ref-entity-sql.md)|Bir varlık örneği için bir başvuru döndürür.|

## <a name="set-operators"></a>Küme işleci

Varlık SQL çeşitli güçlü işlemler sağlar. Bu küme işleci UNION, INTERSECT, EXCEPT, Transact-SQL işleçleriyle benzer içerir ve EXISTS. Varlık SQL işleçleri yinelenen eleme (SET) (gelen) sınama üyelik ve birleşimler (birleştirme) için de destekler. Aşağıdaki tabloda, varlık SQL kümesi işleçleri listeler:

|İşleç|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|
|--------------|---------|
|[ANYELEMENT](anyelement-entity-sql.md)|Bir öğenin birden çok değerli bir koleksiyondan ayıklar.|
|[EXCEPT](except-entity-sql.md)|Tüm farklı değerler koleksiyonu sorgu ifadesinden sorgu ifadesinden EXCEPT işleneni sağındaki ayrıca döndürülen olmayan EXCEPT işleneni sola döndürür.|
|[&AMP;#91;DEĞİL&AMP;#93; EXISTS](exists-entity-sql.md)|Bir koleksiyonu boş olup olmadığını belirler.|
|[FLATTEN](flatten-entity-sql.md)|Değişkeninin bir koleksiyonlar koleksiyonu düzleştirilmiş bir koleksiyonuna dönüştürür.|
|[&AMP;#91;DEĞİL&AMP;#93; IN](in-entity-sql.md)|Bir değer bir koleksiyondaki herhangi bir değer eşleşip eşleşmediğini belirler.|
|[INTERSECT](intersect-entity-sql.md)|Her iki sorgu ifadeleri sol tarafından döndürülen tüm farklı değerler koleksiyonu ve INTERSECT işleneni sağ tarafında döndürür.|
|[OVERLAPS](overlaps-entity-sql.md)|İki koleksiyon ortak öğeler sahip olup olmadığını belirler.|
|[SET](set-entity-sql.md)|Kaldırılan tüm yinelenen öğeler ile yeni bir koleksiyon sağlayan tarafından bir kümesine nesneler koleksiyonunu dönüştürmek için kullanılır.|
|[UNION](union-entity-sql.md)|İki veya daha fazla sorguların sonuçlarını tek bir koleksiyona birleştirir.|

## <a name="type-operators"></a>Türü işleçleri

Varlık SQL oluşturulan, sorgulanabilir ve yönetilebilir bir ifade (değer) türüne izin işlemler sağlar. Aşağıdaki tablo türleri ile çalışmak için kullanılan işleçleri listeler:

|İşleç|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|
|--------------|---------|
|[CAST](cast-entity-sql.md)|Bir veri türünde bir ifadenin diğerine dönüştürür.|
|[COLLECTION](collection-entity-sql.md)|Kullanılan bir [işlevi](function-entity-sql.md) varlık türleri veya karmaşık türler koleksiyonu bildirmek için işlemi.|
|[OLAN &AMP;#91;DEĞİL&AMP;#93; SONU](isof-entity-sql.md)|İfade türü belirtilen türe veya onun alt türlerinden birini olup olmadığını belirler.|
|[OFTYPE](oftype-entity-sql.md)|Belirli bir türde bir sorgu ifadesinden nesneler koleksiyonunu döndürür.|
|[Adlandırılmış Tür Oluşturucu](named-type-constructor-entity-sql.md)|Varlık türleri veya karmaşık türler örneklerini oluşturmak için kullanılır.|
|[MULTISET](multiset-entity-sql.md)|Değerler listesinden bir çoklu küme örneği oluşturur.|
|[ROW](row-entity-sql.md)|Bir veya daha fazla değer anonim, yapısal olarak yazılan kayıtları oluşturur.|
|[TREAT](treat-entity-sql.md)|Belirli bir temel türdeki bir nesneyi belirtilen türetilen türde bir nesne olarak değerlendirir.|

## <a name="other-operators"></a>Diğer işleçleri

Aşağıdaki tablo diğer varlık SQL işleçleri listeler:

|İşleç|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|
|--------------|---------|
|[+ (Dize Birleştirme)](string-concatenation-entity-sql.md)|Varlık SQL dizeyi birleştirmek için kullanılır.|
|[. (Üye Erişimi)](member-access-entity-sql.md)|Bir özellik veya yapısal kavramsal model türünün bir örneği alanının değerini erişmek için kullanılır.|
|[-- (Yorum)](comment-entity-sql.md)|Varlık SQL açıklamaları içerir.|
|[FUNCTION](function-entity-sql.md)|Bir varlık SQL sorgusunda yürütülebilir bir satır içi işlev tanımlar.|

## <a name="see-also"></a>Ayrıca bkz.

[Entity SQL Dili](entity-sql-language.md)
