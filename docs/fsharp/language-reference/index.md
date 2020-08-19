---
title: Dil Başvurusu
description: 'Bu başvurudan dil belirteçleri, kavramlar, türler, ifadeler ve derleyicinin desteklediği yapı konularına F # dil özelliği bilgilerini bulun.'
ms.date: 08/13/2020
ms.openlocfilehash: 02711489c214c1fcdb2da80f30bff63d67769c17
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558159"
---
# <a name="f-language-reference"></a>F# Dili Başvurusu

Bu bölüm, .NET 'i hedefleyen bir multi-kip programlama dili olan F # diline yönelik bir başvurudur. F # dili işlevsel, nesne yönelimli ve kesinlik temelli programlama modellerini destekler.

## <a name="f-core-library-api-reference"></a>F # Çekirdek Kitaplığı API başvurusu

[F # Core Library (FSharp. Core) API başvurusu](https://fsharp.github.io/fsharp-core-docs/) , tüm F # Çekirdek Kitaplığı ad alanları, modüller, türler ve işlevler için başvurudur.

## <a name="f-tokens"></a>F # belirteçleri

Aşağıdaki tabloda, F # içinde belirteç olarak kullanılan anahtar sözcükler, semboller ve sabit değerler tabloları sağlayan başvuru makaleleri gösterilmektedir.

|Başlık|Açıklama|
|-----|-----------|
|[Klavye Başvurusu](keyword-reference.md)|Tüm F # dil anahtar kelimeleri hakkındaki bilgilerin bağlantılarını içerir.|
|[Simge ve İşleç Başvurusu](./symbol-and-operator-reference/index.md)|F # dilinde kullanılan bir sembol ve işleç tablosu içerir.|
|[Değişmez Değerler](literals.md)|F # içindeki sabit değerler için söz dizimini ve F # değişmez değerleri için tür bilgilerinin nasıl belirtileceğini açıklar.|

## <a name="f-language-concepts"></a>F # dil kavramları

Aşağıdaki tabloda, dil kavramlarını tanımlayan kullanılabilir başvuru konuları gösterilmektedir.

|Başlık|Açıklama|
|-----|-----------|
|[İşlevler](./functions/index.md)|İşlevler, herhangi bir programlama dilinde program yürütmenin temel birimidir. Diğer dillerde olduğu gibi, bir F # işlevinin adı vardır, parametreleri olabilir ve bağımsız değişkenler alabilir ve bir gövdeye sahip olabilir. F #, işlevleri değer olarak kabul etmek, ifadelerde adlandırılmamış işlevleri kullanmak, yeni işlevler, curried işlevleri ve işlev bağımsız değişkenlerinin kısmi uygulaması aracılığıyla işlev tanımları oluşturmak için işlevlerin oluşturulması gibi işlevsel programlama yapılarını da destekler.|
|[F# Türleri](fsharp-types.md)|F # içinde kullanılan türleri ve F # türlerinin nasıl adlandırıldığını ve açıklandığını açıklar.|
|[Tür Çıkarma](type-inference.md)|F # derleyicisinin değer türlerini, değişkenleri, parametreleri ve dönüş değerlerini nasıl kullandığını açıklar.|
|[Otomatik Genelleştirme](./generics/automatic-generalization.md)|F # içinde genel yapıları açıklar.|
|[Devralma](inheritance.md)|Nesne odaklı programlamada "a-a" ilişkisini veya alt yazmayı modellemek için kullanılan devralmayı açıklar.|
|[Üyeler](./members/index.md)|F # nesne türlerinin üyelerini açıklar.|
|[Parametreler ve Bağımsız Değişkenler](Parameters-and-Arguments.md)|Parametreleri tanımlama ve işlevlere, yöntemlere ve özelliklere bağımsız değişkenleri geçirme için dil desteğini açıklar. Başvuruya göre geçme hakkında bilgi içerir.|
|[İşleç aşırı yüklemesi](operator-overloading.md)|Bir sınıf veya kayıt türünde ve genel düzeyde aritmetik işleçlerin nasıl aşırı yükleneceğini açıklar.|
|[Atama ve Dönüştürmeler](casting-and-conversions.md)|F # içinde tür dönüştürmeleri için desteği açıklar.|
|[Access Control](access-control.md)|F # ' da erişim denetimini açıklar. Erişim denetimi, istemcilerin türler, Yöntemler, işlevler vb. gibi belirli program öğelerini kullanabildiklerini bildiren anlamına gelir.|
|[Model eşleştirme](pattern-matching.md)|Giriş verilerini dönüştürme kuralları olan ve F # dili boyunca kullanılan desenleri açıklar. Verileri bir düzeniyle karşılaştırabilir, verileri yapısal parçalar halinde çıkarabilir veya verileri çeşitli yollarla ayıklayabilirsiniz.|
|[Etkin Desenler](active-patterns.md)|Etkin desenleri açıklar. Etkin desenler, giriş verilerini bölümlendirilen adlandırılmış bölümler tanımlamanızı sağlar. Her bölüm için özelleştirilmiş bir şekilde verileri ayırmak için etkin desenleri kullanabilirsiniz.|
|[Onaylamalar](assertions.md)|`assert`Bir ifadeyi test etmek için kullanabileceğiniz bir hata ayıklama özelliği olan ifadeyi açıklar. Hata ayıklama modunda hata oluştuğunda bir onaylama işlemi bir sistem hatası iletişim kutusu oluşturur.|
|[Özel Durum İşleme](./exception-handling/index.md)|F # dilinde özel durum işleme desteği hakkında bilgi içerir.|
|[özelliklerine](attributes.md)|Meta verilerin bir programlama yapısına uygulanmasını sağlayan öznitelikleri açıklar.|
|[Kaynak yönetimi: `use` anahtar sözcüğü](resource-management-the-use-keyword.md)|`use` `using` , Kaynakların başlatılmasını ve serbest bırakılması için kullanabileceğiniz anahtar kelimeleri açıklar|
|[öznitelikleri](namespaces.md)|F # içinde ad alanı desteğini açıklar. Bir ad alanı, program öğeleri gruplandırmasına bir ad iliştirmenizi sağlayarak kodu ilgili işlevlerin alanlarıyla düzenlemenizi sağlar.|
|[Modül](modules.md)|Modüller açıklanmaktadır. F # modülü, f # programında değerler, türler ve işlev değerleri gibi bir F # kodu gruplandırmasıdır. Modüllerde kod gruplandırma, ilgili kodu birlikte tutmaya yardımcı olur ve programınızda ad çakışmalarını önlemeye yardımcı olur.|
|[İçeri aktarma bildirimleri: `open` anahtar sözcüğü](import-declarations-the-open-keyword.md)|Nasıl `open` çalıştığını açıklar. İçeri aktarma bildirimi, öğelerini tam nitelikli bir ad kullanmadan başvuralabileceğiniz bir modül veya ad alanını belirtir.|
|[İmzalar](signature-files.md)|İmzaları ve imza dosyalarını açıklar. İmza dosyası türler, ad alanları ve modüller gibi bir F # program öğesi kümesinin genel imzaları hakkında bilgiler içerir. Bu program öğelerinin erişilebilirliğini belirtmek için kullanılabilir.|
|[XML Belgeleri](xml-documentation.md)|Üçlü eğik çizgi açıklamaları olarak da bilinen XML belgesi açıklamaları için belge dosyası oluşturma desteğini açıklar. F # içindeki kod açıklamalarından farklı .NET dillerinde belgeler oluşturabilirsiniz.|
|[Ayrıntılı Sözdizimi](verbose-syntax.md)|Hafif sözdizimi etkin olmadığında F # yapıları için sözdizimi açıklar. Ayrıntılı sözdizimi, `#light "off"` kod dosyasının en üstündeki yönergeyle belirtilir.|
|[Düz Metin Biçimlendirmesi](plaintext-formatting.md)|F # uygulamalarında sprintf ve diğer düz metin biçimlendirmelerini nasıl kullanacağınızı öğrenin.|

## <a name="f-types"></a>F# Türleri

Aşağıdaki tabloda, F # dili tarafından desteklenen türleri tanımlayan kullanılabilir başvuru konuları gösterilmektedir.

|Başlık|Açıklama|
|-----|-----------|
|[deðerler](./values/index.md)|Belirli bir türe sahip sabit miktarlar olan değerleri açıklar; değerler tamsayı veya kayan nokta sayıları, karakterler veya metin, listeler, sıralar, diziler, tanımlama grupları, ayırt edici birleşimler, kayıtlar, sınıf türleri veya işlev değerleri olabilir.|
|[Temel Türler](basic-types.md)|F # dilinde kullanılan temel temel türleri açıklar. Ayrıca, her tür için karşılık gelen .NET türlerini ve en düşük ve en yüksek değerleri sağlar.|
|[Birim Türü](unit-type.md)|Belirli bir `unit` değerin yokluğunu gösteren bir tür olan türü açıklar; `unit` tür, başka bir değer yoksa veya gerektiğinde yer tutucu görevi gören tek bir değer içerir.|
|[Dizeler](strings.md)|F # içindeki dizeleri açıklar. `string`Tür, Unicode karakter dizisi olarak sabit metni temsil eder. `string` , .NET Framework için bir diğer addır `System.String` .|
|[Demetler](tuples.md)|Adlandırılmamış, ancak muhtemelen farklı türlerin sıralı değerlerinin gruplamaları olan tanımlama gruplarını açıklar.|
|[F# Koleksiyon Türleri](fsharp-collection-types.md)|Diziler, listeler, sıralar (sıra), haritalar ve kümeler için türler de dahil olmak üzere F # işlevsel koleksiyon türlerine genel bakış.|
|[Listeler](lists.md)|Listeleri açıklar. F # ' daki bir liste, aynı türden tümü sıralanmış, sabit bir öğe dizisidir.|
|[Seçenekler](options.md)|Seçenek türünü açıklar. F # ' daki bir seçenek, bir değer varsa veya mevcut olmadığında kullanılır. Bir seçenek temel bir türe sahiptir ve bu tür bir değeri tutabilir ya da bir değere sahip olmayabilir.|
|[Diziler](sequences.md)|Dizileri açıklar. Dizi, tek bir türdeki öğelerin mantıksal bir dizisidir. Tek tek dizi öğeleri yalnızca gerekliyse hesaplanır, bu nedenle gösterim bir sabit öğe sayısı değerinden daha küçük olabilir.|
|[Diziler](arrays.md)|Dizileri açıklar. Diziler, hepsi aynı türde olan sabit boyutlu, sıfır tabanlı ve değiştirilebilir dizilerdir.|
|[Kayıtlar](records.md)|Kayıtları açıklar. Kayıtlar, isteğe bağlı olarak Üyeler ile adlandırılmış değerlerin basit toplamlarını temsil eder.|
|[Ayrılmış Birleşimler](discriminated-unions.md)|Her biri büyük olasılıkla farklı değerler ve türler içeren çeşitli adlandırılmış durumlardan biri olabilecek değerler için destek sağlayan ayırt edici birleşimleri açıklar.|
|[Numaralandırmalar](enumerations.md)|Numaralandırmaların tanımlanmış bir adlandırılmış değerler kümesine sahip türleri olduğunu açıklar. Kodu daha okunaklı ve bakım yapılabilir hale getirmek için bunları değişmez değerler yerine kullanabilirsiniz.|
|[Başvuru Hücreleri](reference-cells.md)|Başvuru semantiğinin değişebilir değişkenler oluşturmanızı sağlayan depolama konumları olan başvuru hücrelerini açıklar.|
|[Tür Kısaltmaları](type-abbreviations.md)|Türler için alternatif adlar olan tür kısaltmalarını açıklar.|
|[Sınıflar](classes.md)|Özelliklere, yöntemlere ve olaylara sahip olabilecek nesneleri temsil eden türler olan sınıfları açıklar.|
|[Yapılar](structures.md)|Az miktarda veri ve basit davranışa sahip olan türler için bir sınıftan daha verimli olabilecek, Compact nesne türleri olan yapıları açıklar.|
|[Arabirimler](interfaces.md)|Diğer sınıfların uygulayan ilgili üye kümelerini belirten arabirimlerini açıklar.|
|[Soyut sınıflar](abstract-classes.md)|Uygulamaların türetilmiş sınıflar tarafından sağlanabilmesi için bazı veya tüm üyeleri uygulanmayan sınıflar olan soyut sınıfları açıklar.|
|[Tür Genişletmeleri](type-extensions.md)|Daha önce tanımlanmış bir nesne türüne yeni üyeler eklemenize olanak sağlayan tür uzantılarını açıklar.|
|[Esnek Türler](flexible-types.md)|Esnek türleri açıklar. Esnek tür ek açıklaması, bir parametre, değişken veya değerin belirtilen tür ile uyumlu bir tür olduğunu belirtir ve uyumluluk, nesne odaklı sınıfların veya arabirimlerin bulunduğu konuma göre belirlenir.|
|[Temsilciler](delegates.md)|Bir işlev çağrısını nesne olarak temsil eden temsilcileri açıklar.|
|[Ölçü Birimleri](units-of-measure.md)|Ölçü birimlerini açıklar. F # içindeki kayan nokta değerleri, genellikle uzunluğu, hacmi, kütle, vb. belirtmek için kullanılan ilişkili ölçü birimlerine sahip olabilir.|
|[Tür Sağlayıcıları](../tutorials/type-providers/index.md)|Türü açıklar ve, veritabanlarına ve Web hizmetlerine erişmek için yerleşik tür sağlayıcılarını kullanma hakkındaki izlenecek yollara bağlantılar sağlar.|

## <a name="f-expressions"></a>F # Ifadeleri

Aşağıdaki tabloda, F # ifadelerini tanımlayan konular listelenmektedir.

|Başlık|Açıklama|
|-----|-----------|
|[Koşullu Ifadeler: `if...then...else`](conditional-expressions-if-then-else.md)|`if...then...else`Farklı kod dalları çalıştıran ve ayrıca verilen Boole ifadesine bağlı olarak farklı bir değer olarak değerlendirilen ifadeyi açıklar.|
|[Eşleşme İfadeleri](match-expressions.md)|`match`Desen kümesine sahip bir ifadenin karşılaştırmasına dayalı olarak dallanma denetimi sağlayan ifadeyi açıklar.|
|[Döngüler: `for...to` ifade](loops-for-to-expression.md)|Bir döngü `for...to` değişkeninin değer aralığı üzerinde bir döngüde yinelemek için kullanılan ifadeyi açıklar.|
|[Döngüler: `for...in` ifade](loops-for-in-expression.md)|Bir `for...in` Aralık ifadesi, sıra, liste, dizi ya da numaralandırmayı destekleyen diğer yapı gibi sıralanabilir bir koleksiyondaki bir düzenin eşleşmelerini yinelemek için kullanılan bir döngü yapısı olan ifadeyi açıklar.|
|[Döngüler: `while...do` ifade](loops-while-do-expression.md)|`while...do`Belirtilen test koşulu doğru olduğunda yinelemeli yürütmeyi (döngü) gerçekleştirmek için kullanılan ifadeyi açıklar.|
|[Nesne İfadeleri](object-expressions.md)|Mevcut bir temel türü, arabirimi veya arabirim kümesini temel alan dinamik olarak oluşturulan, anonim nesne türünün yeni örneklerini oluşturan ifadeler olan nesne ifadelerini açıklar.|
|[Gecikmeli İfadeler](lazy-expressions.md)|Hemen değerlendirilmediği hesaplamalar olan yavaş ifadeleri açıklar, ancak bunun yerine sonuç gerçekten gerektiğinde değerlendirilir.|
|[Hesaplama İfadeleri](computation-expressions.md)|Denetim akışı yapıları ve bağlamaları kullanılarak sıralanmakta ve birleştirilebilir hesaplamalar yazmak için kullanışlı bir sözdizimi sağlayan F # içindeki hesaplama ifadelerini açıklar. Bunlar, işlevsel programlardaki verileri, denetimi ve yan etkileri yönetmek için kullanılabilecek bir işlevsel programlama özelliği olan *monadları*için uygun bir sözdizimi sağlamak üzere kullanılabilir. Bir tür hesaplama ifadesi, zaman uyumsuz iş akışı, zaman uyumsuz ve paralel hesaplamalar için destek sağlar. Daha fazla bilgi için bkz. [zaman uyumsuz Iş akışları](asynchronous-workflows.md).|
|[Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)|Zaman uyumsuz kodu, doğal olarak zaman uyumlu olarak yazacağınız bir şekilde yazmanıza imkan tanıyan bir dil özelliği olan zaman uyumsuz iş akışlarını açıklar.|
|[Kod Tırnak İşaretleri](code-quotations.md)|Programlama yoluyla F # kod ifadelerini oluşturup çalışmanıza olanak tanıyan bir dil özelliği olan kod tekliflerini açıklar.|
|[Sorgu İfadeleri](query-expressions.md)|F # için LINQ uygulayan ve bir veri kaynağına veya sıralanabilir koleksiyona karşı sorgular yazmanıza olanak tanıyan bir dil özelliği olan sorgu ifadelerini açıklar.|

## <a name="compiler-supported-constructs"></a>Derleyici tarafından desteklenen yapılar

Aşağıdaki tabloda, derleyicinin desteklediği özel yapıları anlatan konular listelenmektedir.

|Konu|Açıklama|
|-----|-----------|
|[Derleyici seçenekleri](compiler-options.md)|F # derleyicisi için komut satırı seçeneklerini açıklar.|
|[Derleyici Yönergeleri](compiler-directives.md)|İşlemci yönergelerini ve derleyici yönergelerini açıklar.|
|[Kaynak Satırı, Dosya ve Yol Tanımlayıcıları](source-line-file-path-identifiers.md)|`__LINE__` `__SOURCE_DIRECTORY__` `__SOURCE_FILE__` Kodunuzda kaynak satır numarası, dizin ve dosya adına erişmenizi sağlayan yerleşik değerler olan tanımlayıcıları açıklar.|
