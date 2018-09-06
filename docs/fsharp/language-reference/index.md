---
title: F# Dili Başvurusu
description: 'F # dil özelliği bilgilerinden bu başvuruyu dili belirteçleri, kavramları, türleri, ifadeler ve derleyici tarafından desteklenen yapı konuları bulun.'
ms.date: 05/16/2016
ms.openlocfilehash: adce37ee393673b7611ad24f385c8b8106f6ce86
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43873256"
---
# <a name="f-language-reference"></a>F# Dili Başvurusu

Bu bölüm, F # dili, bir çoklu paradigma programlama dili .NET desteği için bir başvurudur. F # dili, işlev, nesne yönelimli ve buyurgan programlama modelini destekler.

## <a name="f-tokens"></a>F # belirteçleri

Tablolarda anahtar sözcükler, simgeler ve F # belirteçleri olarak kullanılan sabit değerleri sağlayan başvuru konuları aşağıdaki tabloda gösterilmektedir.

|Başlık|Açıklama|
|-----|-----------|
|[Klavye Başvurusu](keyword-reference.md)|Tüm F # dil anahtar sözcükleri hakkında daha fazla bilgi için bağlantılar içerir.|
|[Simge ve İşleç Başvurusu](symbol-and-operator-reference/index.md)|Simgeler ve işleçler F # dilinde kullanılan bir tablo içeriyor.|
|[Değişmez Değerler](literals.md)|F # ve F # değişmez değerleri için tür bilgilerini belirleme konusunda değişmez değerler sözdizimi açıklar.|

## <a name="f-language-concepts"></a>F # dil kavramları

Dil kavramları açıklayan kullanılabilir başvuru konuları aşağıdaki tabloda gösterilmektedir.

|Başlık|Açıklama|
|-----|-----------|
|[İşlevler](functions/index.md)|Tüm programlama dillerinde program yürütmenin temel birimi işlevlerdir. F # işlevi bir ada sahip diğer dillerde olduğu gibi parametreleri ve sınav zamanı bağımsız değişkenleri olabilir ve bir gövdeye sahip. F # ayrıca değerlere işlevler değerlendirmesini gibi fonksiyonel programlama yapıları adlandırılmamış işlevler ifadelerde örtülü bir tanım kısmi yoluyla işlevlerin yeni işlevleri ve curried işlevleri oluşturmak üzere işlevlerin oluşturulması kullanılmasını destekler işlev bağımsız değişkenleri uygulama.|
|[F# Türleri](fsharp-types.md)|F # ve F # türleri nasıl adlı ve açıklanan kullanılan türleri açıklanmaktadır.|
|[Tür Çıkarımı](type-inference.md)|F # derleyicisi değerleri, değişkenleri, parametreler ve dönüş değerlerinin türleri nasıl çıkarsar açıklar.|
|[Otomatik Genelleştirme](generics/automatic-generalization.md)|F # genel yapıları açıklar.|
|[Devralma](inheritance.md)|Nesne yönelimli programlama subtyping ya da "olan bir" ilişkileri modellemek için kullanılan bir devralma açıklar.|
|[Üyeler](members/index.md)|F # nesne türlerinin üyelerini açıklar.|
|[Parametreler ve Bağımsız Değişkenler](Parameters-and-Arguments.md)|Parametreleri tanımlama ve bağımsız değişkenleri işlevleri, yöntemlere ve özelliklere geçirme için dil desteğini açıklar. Bu başvuruya göre geçirme hakkında bilgi içerir.|
|[İşleç Aşırı Yüklemesi](operator-overloading.md)|Aritmetik işleçler bir sınıf ya da kayıt türü ve genel düzeyde aşırı açıklar.|
|[Tür Değiştirme ve Dönüştürmeler](casting-and-conversions.md)|F # tür dönüştürmeleri desteğini açıklar.|
|[Erişim Denetimi](access-control.md)|F #'deki erişim denetimi açıklanmaktadır. Erişim denetimi, hangi istemcilerin vb. türleri, yöntemleri, İşlevler gibi belirli program öğelerini kullanabilir bildirme anlamına gelir.|
|[Desen Eşleştirme](pattern-matching.md)|F # dilinde bir desen ile karşılaştırma verileri ayıklamak, verileri bileşenlerine ayırmak veya çeşitli şekillerde verilerden bilgi ayıklamak için kullanılan giriş verileri dönüştürmeye ilişkin kurallardır desenleri açıklar.|
|[Etkin Desenler](active-patterns.md)|Etkin desenler açıklanmaktadır. Etkin desenler, giriş verileri alt bölümlere adlandırılmış bölümler tanımlamanıza olanak sağlar. Etkin desenler, her bölüm için özelleştirilmiş bir şekilde veri ayırmak için kullanabilirsiniz.|
|[Onaylamalar](assertions.md)|Açıklar `assert` bir ifade test etmek için kullanabileceğiniz bir hata ayıklama özelliği olan ifade. Hata ayıklama modunda başarısızlık durumunda, bir sistem hatası iletişim kutusu bir onay oluşturur.|
|[Özel Durum İşleme](exception-handling/index.md)|Özel durum işleme F # dil desteği hakkında bilgi içerir.|
|[Öznitelikleri](attributes.md)|Bir programlama yapısı için uygulanacak meta verilerini etkinleştir öznitelikleri açıklanmaktadır.|
|[Kaynak Yönetimi: `use` anahtar sözcüğü](resource-management-the-use-keyword.md)|Anahtar sözcükler açıklar `use` ve `using`, hangi denetleyebilir başlatma ve kaynakların sürüm|
|[Ad alanları](namespaces.md)|F #'de ad alanı desteğini açıklar. Bir ad alanı program öğeleri gruplandırması için bir ad eklemek sağlayarak, ilgili işlevleri alanlarına kod düzenlemenize olanak tanır.|
|[Modüller](modules.md)|Modüller açıklar. Bir F # modülü, değer türleri ve işlev değerleri olarak F # programında gibi F # kodu, gruplandırmasıdır. Kod modüllerinde gruplandırma ilgili kod bir arada tutmaya yardımcı olur ve programınızdaki ad çakışmalarını önlemek yardımcı olur.|
|[İçeri aktarma bildirimleri: `open` anahtar sözcüğü](import-declarations-the-open-keyword.md)|Açıklayan nasıl `open` çalışır. İçeri aktarma bildirimi, modül veya öğeleri bir tam adı kullanmadan başvuru ad alanı belirtir.|
|[İmzalar](signatures.md)|İmzalar ve imza dosyalarını açıklar. Bir imza dosyası türleri, ad alanları ve modüller gibi F # program öğelerini, bir dizi ortak imzalarını hakkında bilgiler içerir. Bu program öğelerini erişilebilirliğini belirtmek için kullanılabilir.|
|[XML Belgeleri](xml-documentation.md)|Belge dosyaları için XML belge açıklamaları, olarak da bilinen üç eğik çizgi açıklamalarını oluşturma desteğini açıklar. Kod açıklamaları F # diğer .NET dilleri olduğu gibi belgelerden üretebilir.|
|[Ayrıntılı Söz Dizimi](verbose-syntax.md)|Basit sözdizimi etkinleştirilmediğinde F # yapılarını sözdizimi açıklar. Ayrıntılı sözdizimi tarafından belirtilen `#light "off"` kod dosyasının üst yönergesi.|

## <a name="f-types"></a>F# Türleri

Aşağıdaki tabloda F # dili tarafından desteklenen türleri açıklayan başvuru konuları kullanılabilir gösterilmektedir.

|Başlık|Açıklama|
|-----|-----------|
|[Değerleri](values/index.md)|Belirli bir türüne sahip sabit miktarlarının değerleri açıklar; değerleri tamsayı veya kayan nokta numaralarını, karakter veya metin, listeler, dizileri, diziler, diziler, ayrılmış birleşimler, kayıtları, sınıf türleri veya işlev değerleri olabilir.|
|[Temel Türler](basic-types.md)|F # dilinde kullanılan temel temel türler açıklanmaktadır. Ayrıca karşılık gelen .NET türleri ve minimum ve maksimum değerler her türü için sağlar.|
|[Birim Türü](unit-type.md)|Açıklar `unit` belirli bir değer; devamsızlık gösteren bir tür olan türü `unit` türüne sahip başka bir değer yok veya gerekli olduğunda, bir yer tutucu olarak görev yapar yalnızca tek bir değer.|
|[Dizeler](strings.md)|F # dizelerini açıklar. `string` Türü sabit metin, Unicode karakter dizisi olarak temsil eder. `string` için bir diğer addır `System.String` .NET Framework'teki.|
|[Demetler](tuples.md)|Gruplandırmaları adlandırılmamış ancak sıralı değerleri muhtemelen farklı türde diziler açıklar.|
|[F# Koleksiyon Türleri](fsharp-collection-types.md)|Diziler, listeler, dizileri (seq), haritalar ve kümeler için türleri dahil olmak üzere F # işlevsel koleksiyon türleri, genel bakış.|
|[Listeler](lists.md)|Listelerini açıklar. Öğeleri sıralanmış, sabit bir dizi listedir F # tümü aynı türde.|
|[Seçenekler](options.md)|Seçenek türü açıklar. Bir değer olabilir veya olmayabilir F # içinde bir seçenek kullanılır. Bir temel türü seçeneği vardır ve bu türde bir değer ya da tutabilir veya bir değer olmayabilir.|
|[Diziler](sequences.md)|Dizileri açıklar. Mantıksal bir dizi öğelerinin bir dizisidir tümü tek. Gösterim literal öğesi sayısını gösteren daha küçük olabilir bireysel sırası öğeleri yalnızca gerekli olursa, hesaplanır.|
|[Diziler](arrays.md)|Dizileri açıklar. Sabit boyutlu, sıfır tabanlı, kesilebilir dizileri ardışık veri öğelerinin tümü aynı türde dizilerdir.|
|[Kayıtlar](records.md)|Kayıtları açıklar. Kayıtları basit toplamalarla üyeleri ile isteğe bağlı olarak adlandırılan değerleri temsil eder.|
|[Ayrılmış Birleşimler](discriminated-unions.md)|Ayrılmış birleşimler, çeşitli adlandırılmış durumlarda, farklı olması olası değerlerini ve türlerini her biri olabilen değerleri için destek sağlayan açıklar.|
|[Sabit Listeleri](enumerations.md)|Numaralandırmaları açıklar tanımlı bir dizi türleri değerleri olarak adlandırılır. Kod daha okunabilir ve sürdürülebilir hale getirmek için değişmez değerler yerine bunları kullanabilirsiniz.|
|[Başvuru Hücreleri](reference-cells.md)|Başvuru semantiğiyle değişebilir değişkenleri oluşturmanıza olanak sağlayan depolama yerleridir başvuru hücreleri açıklar.|
|[Tür Kısaltmaları](type-abbreviations.md)|Türleri için alternatif adlar olan tür kısaltmaları açıklar.|
|[Sınıflar](classes.md)|Özellikleri, yöntemleri ve olayları olabilir nesneleri temsil eden türler sınıflarını açıklar.|
|[Yapılar](structures.md)|Az miktarda veri ve basit davranışı sahip türleri bir sınıf daha verimli olabilir compact nesne türleri yapıları açıklar.|
|[Arabirimler](interfaces.md)|Diğer sınıfları uygulayan ilgili üyeleri kümesini belirten ve arabirimler açıklanmaktadır.|
|[Soyut Sınıflar](abstract-classes.md)|Uygulanmayanları, bazı veya tüm üyeleri bırakın ve böylece uygulamaları türetilmiş sınıflar tarafından sağlanması sınıflarının soyut sınıfları açıklar.|
|[Tür Uzantıları](type-extensions.md)|Bir önceden tanımlanmış nesne türü için yeni üyeler eklemenize olanak sağlayan tür uzantıları açıklar.|
|[Esnek Türler](flexible-types.md)|Esnek türler açıklanmaktadır. Bir esnek tür ek açıklamasına parametre, değişken veya değer türü ile uyumlu bir türe sahip bir göstergesi, uyumluluk sınıfları arabirimler ve nesne yönelimli bir hiyerarşideki konuma göre belirlendiği belirtilmiştir.|
|[Temsilciler](delegates.md)|Bir nesne olarak bir işlev çağrısını temsil eden temsilciler açıklar.|
|[Ölçü Birimleri](units-of-measure.md)|Ölçü birimleri açıklar. F #'ta kayan nokta değerleri genellikle uzunluğu, toplu, yığın ve benzeri belirtmek için kullanılan ölçü birimlerini ilişkili.|
|[Tür Sağlayıcıları](../tutorials/type-providers/index.md)|Açıklayan tür sağlar ve yerleşik tür sağlayıcılarını kullanarak veritabanları ve web hizmetleri için izlenecek yollar için bağlantılar sağlar.|

## <a name="f-expressions"></a>F # ifadeleri

Aşağıdaki tabloda, F # ifadelerini açıklayan konuları listeler.

|Başlık|Açıklama|
|-----|-----------|
|[Koşullu ifadeler: `if...then...else`](conditional-expressions-if-then-else.md)|Açıklar `if...then...else` kodunun farklı dallara çalışan ve ayrıca verilen Boole ifadesi bağlı olarak farklı bir değer olarak değerlendirilen ifade.|
|[Eşleşme İfadeleri](match-expressions.md)|Açıklar `match` karşılaştırma ifade desenleri temel alan dallanma denetim sağlayan bir ifade.|
|[Döngüler: `for...to` ifadesi](loops-for-to-expression.md)|Açıklar `for...to` bir döngüde bir dizi bir döngü değişkeninin değerleri üzerinden yineleme yapmak için kullanılan ifade.|
|[Döngüler: `for...in` ifadesi](loops-for-in-expression.md)|Açıklar `for...in` ifadesi, bir aralık ifadesi, sıra, list, dizi gibi bir sıralanabilir koleksiyonun içindeki bir desenle eşleşmeleri üzerinden yineleme yapmak için kullanılan uvozuje konstruktor veya numaralandırma destekleyen diğer yapı.|
|[Döngüler: `while...do` ifadesi](loops-while-do-expression.md)|Açıklar `while...do` belirtilen test koşulu true olduğu sürece, yinelemeli yürütme (döngü) gerçekleştirmek için kullanılan ifade.|
|[Nesne İfadeleri](object-expressions.md)|Bir mevcut temel tür, arabirimi veya arabirim kümesine göre bir dinamik olarak oluşturulmuş, anonim bir nesne türünün yeni örneğini oluşturma ifadeler nesne ifadeleri açıklar.|
|[Geç Hesaplamalar](lazy-computations.md)|Geç hesaplamalar hemen değerlendirilmeyen, ancak bunun yerine sonucu gerçekten gerekli olduğunda değerlendirilir hesaplamalar olan açıklar.|
|[Hesaplama İfadeleri](computation-expressions.md)|F #'ta, sıralı ve denetim akışı yapılarını ve bağlamalar kullanılarak birleştirilen hesaplamalar yazmak için kullanışlı bir söz dizimi sağlayan hesaplama ifadeleri açıklar. İçin kullanışlı bir söz dizimi sağlamak için kullanılabilir *monadları*, veri, Denetim ve yan etkileri işlevsel programlarda yönetmek için kullanılan bir işlevsel programlama özelliği. Hesaplama ifadesi, zaman uyumsuz iş akışı bir tür, zaman uyumsuz ve paralel hesaplamaları için destek sağlar. Daha fazla bilgi için [zaman uyumsuz iş akışları](asynchronous-workflows.md).|
|[Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)|Zaman uyumsuz iş akışları, zaman uyumsuz kod çok yakın şekilde, bir şekilde doğal olarak zaman uyumlu bir kod yazmak istediğiniz yazmanızı sağlayan bir dil özelliğini açıklar.|
|[Kod Alıntıları](code-quotations.md)|Kod tırnak işaretleri, oluşturmak ve F # kodu ifadeleri ile programlı bir şekilde çalışmanıza olanak sağlayan bir dil özelliğini açıklar.|
|[Sorgu İfadeleri](query-expressions.md)|Sorgu ifadeleri LINQ F # için uygular ve bir veri kaynağı veya bir sıralanabilir koleksiyonun karşı sorgular yazmanızı sağlar bir dil özelliği açıklar.|

## <a name="compiler-supported-constructs"></a>Derleyici tarafından desteklenen yapılar

Aşağıdaki tabloda, derleyici tarafından desteklenen özel yapıları açıklayan konulara listeler.

|Konu|Açıklama|
|-----|-----------|
|[Derleyici Seçenekleri](compiler-options.md)|F # derleyicisi için komut satırı seçeneklerini açıklar.|
|[Derleyici Yönergeleri](compiler-directives.md)|İşlemci yönergeleri ve derleyici yönergeleri açıklar.|
|[Kaynak Satırı, Dosya ve Yol Tanımlayıcıları](source-line-file-path-identifiers.md)|Tanımlayıcılar açıklanmaktadır `__LINE__`, `__SOURCE_DIRECTORY__` ve `__SOURCE_FILE__`, kodunuzda kaynak satırı numarasını, dizin ve dosya adına erişmenize olanak tanıyan yerleşik değerleri şunlardır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual F#](../index.md)
