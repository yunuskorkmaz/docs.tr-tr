---
title: F# Dili Başvurusu
description: Bu F# başvurudan dil belirteçleri, kavramlar, türler, ifadeler ve derleyicinin desteklediği yapı konularına yönelik dil özelliği bilgilerini bulun.
ms.date: 05/16/2016
ms.openlocfilehash: ac7e268b28d6bb654e4443d04695cb15fe756e9f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424998"
---
# <a name="f-language-reference"></a>F# Dili Başvurusu

Bu bölüm, .NET hedefleyen çok faktörlü F# programlama dili olan dile bir başvurudur. F# Dil işlev, nesne yönelimli ve kesinlik temelli programlama modellerini destekler.

## <a name="f-tokens"></a>F#Simgelerini

Aşağıdaki tabloda, içinde F#belirteç olarak kullanılan anahtar sözcükler, semboller ve sabit değerler tabloları sağlayan başvuru konuları gösterilmektedir.

|Başlık|Açıklama|
|-----|-----------|
|[Klavye Başvurusu](keyword-reference.md)|Tüm F# dil anahtar kelimeleri hakkındaki bilgilerin bağlantılarını içerir.|
|[Simge ve İşleç Başvurusu](./symbol-and-operator-reference/index.md)|F# Dilde kullanılan bir sembol ve işleç tablosu içerir.|
|[Değişmez Değerler](literals.md)|İçindeki F# değişmez değerler için söz dizimini ve değişmez değer için F# tür bilgilerinin nasıl belirtileceğini açıklar.|

## <a name="f-language-concepts"></a>F#Dil kavramları

Aşağıdaki tabloda, dil kavramlarını tanımlayan kullanılabilir başvuru konuları gösterilmektedir.

|Başlık|Açıklama|
|-----|-----------|
|[İşlevler](./functions/index.md)|İşlevler, herhangi bir programlama dilinde program yürütmenin temel birimidir. Diğer dillerde olduğu gibi, bir F# işlevin adı vardır, parametreleri olabilir ve bağımsız değişkenler alabilir ve bir gövdeye sahip olabilir. F#Ayrıca, işlevleri değer olarak davranma, ifadelerde adlandırılmamış işlevleri kullanma, yeni işlevler, curried işlevleri ve kısmi olarak işlevlerin örtük tanımına göre işlev oluşturma gibi işlev programlama yapılarını destekler. işlev bağımsız değişkenlerinin uygulaması.|
|[F# Türleri](fsharp-types.md)|İçinde F# kullanılan türleri ve türlerin adlandırılması ve açıklanme F# biçimini açıklar.|
|[Tür Çıkarımı](type-inference.md)|F# Derleyicinin değer, değişken, parametre ve dönüş değeri türlerini nasıl kullandığını açıklar.|
|[Otomatik Genelleştirme](./generics/automatic-generalization.md)|' De F#genel yapıları açıklar.|
|[Devralma](inheritance.md)|Nesne odaklı programlamada "a-a" ilişkisini veya alt yazmayı modellemek için kullanılan devralmayı açıklar.|
|[Üyeler](./members/index.md)|F# Nesne türlerinin üyelerini açıklar.|
|[Parametreler ve Bağımsız Değişkenler](Parameters-and-Arguments.md)|Parametreleri tanımlama ve işlevlere, yöntemlere ve özelliklere bağımsız değişkenleri geçirme için dil desteğini açıklar. Başvuruya göre geçme hakkında bilgi içerir.|
|[İşleç Aşırı Yüklemesi](operator-overloading.md)|Bir sınıf veya kayıt türünde ve genel düzeyde aritmetik işleçlerin nasıl aşırı yükleneceğini açıklar.|
|[Tür Değiştirme ve Dönüştürmeler](casting-and-conversions.md)|İçindeki F#tür dönüştürmeleri için desteği açıklar.|
|[Erişim Denetimi](access-control.md)|İçindeki F#erişim denetimini açıklar. Erişim denetimi, istemcilerin türler, Yöntemler, işlevler vb. gibi belirli program öğelerini kullanabildiklerini bildiren anlamına gelir.|
|[Desen Eşleştirme](pattern-matching.md)|Verileri bir desenle karşılaştırmak, verileri yapısal parçalar halinde çıkarmak veya verileri çeşitli yollarla ayıklamak F# için dil genelinde kullanılan giriş verilerini dönüştürme kuralları olan desenleri açıklar.|
|[Etkin Desenler](active-patterns.md)|Etkin desenleri açıklar. Etkin desenler, giriş verilerini bölümlendirilen adlandırılmış bölümler tanımlamanızı sağlar. Her bölüm için özelleştirilmiş bir şekilde verileri ayırmak için etkin desenleri kullanabilirsiniz.|
|[Onaylamalar](assertions.md)|Bir ifadeyi test etmek için kullanabileceğiniz bir hata ayıklama özelliği olan `assert` ifadesini açıklar. Hata ayıklama modunda hata oluştuğunda bir onaylama işlemi bir sistem hatası iletişim kutusu oluşturur.|
|[Özel Durum İşleme](./exception-handling/index.md)|F# Dilde özel durum işleme desteği hakkında bilgi içerir.|
|[özelliklerine](attributes.md)|Meta verilerin bir programlama yapısına uygulanmasını sağlayan öznitelikleri açıklar.|
|[Kaynak yönetimi: `use` anahtar sözcüğü](resource-management-the-use-keyword.md)|Kaynak başlatma ve serbest bırakma işlemini denetleyebilen `use` ve `using`anahtar sözcüklerini açıklar|
|[öznitelikleri](namespaces.md)|İçinde F#ad alanı desteğini açıklar. Bir ad alanı, program öğeleri gruplandırmasına bir ad iliştirmenizi sağlayarak kodu ilgili işlevlerin alanlarıyla düzenlemenizi sağlar.|
|[Modüller](modules.md)|Modüller açıklanmaktadır. F# Modül, bir F# programdaki değerler, türler ve işlev değerleri gibi bir F# kod gruplandırmasıdır. Modüllerde kod gruplandırma, ilgili kodu birlikte tutmaya yardımcı olur ve programınızda ad çakışmalarını önlemeye yardımcı olur.|
|[İçeri aktarma bildirimleri: `open` anahtar sözcüğü](import-declarations-the-open-keyword.md)|`open` nasıl çalıştığını açıklar. İçeri aktarma bildirimi, öğelerini tam nitelikli bir ad kullanmadan başvuralabileceğiniz bir modül veya ad alanını belirtir.|
|[İmzalar](signature-files.md)|İmzaları ve imza dosyalarını açıklar. İmza dosyası türler, ad alanları ve modüller gibi bir F# program öğeleri kümesinin genel imzaları hakkında bilgiler içerir. Bu program öğelerinin erişilebilirliğini belirtmek için kullanılabilir.|
|[XML Belgeleri](xml-documentation.md)|Üçlü eğik çizgi açıklamaları olarak da bilinen XML belgesi açıklamaları için belge dosyası oluşturma desteğini açıklar. Kod açıklamalarından F# daha fazla .net dilinde olduğu gibi belgeler üretebilirsiniz.|
|[Ayrıntılı Söz Dizimi](verbose-syntax.md)|Hafif sözdizimi etkin olmadığında F# yapıların sözdizimini açıklar. Ayrıntılı sözdizimi, kod dosyasının en üstündeki `#light "off"` yönergesi tarafından gösterilir.|

## <a name="f-types"></a>F# Türleri

Aşağıdaki tabloda, F# dil tarafından desteklenen türleri tanımlayan kullanılabilir başvuru konuları gösterilmektedir.

|Başlık|Açıklama|
|-----|-----------|
|[deðerler](./values/index.md)|Belirli bir türe sahip sabit miktarlar olan değerleri açıklar; değerler tamsayı veya kayan nokta sayıları, karakterler veya metin, listeler, sıralar, diziler, tanımlama grupları, ayırt edici birleşimler, kayıtlar, sınıf türleri veya işlev değerleri olabilir.|
|[Temel Türler](basic-types.md)|F# Dilde kullanılan temel temel türleri açıklar. Ayrıca, her tür için karşılık gelen .NET türlerini ve en düşük ve en yüksek değerleri sağlar.|
|[Birim Türü](unit-type.md)|Belirli bir değerin yokluğunu gösteren bir tür olan `unit` türünü açıklar; `unit` türü, başka bir değer yoksa veya gerekli olmadığında yer tutucu olarak davranan yalnızca tek bir değere sahiptir.|
|[Dizeler](strings.md)|İçindeki F#dizeleri açıklar. `string` türü, Unicode karakter dizisi olarak sabit metni temsil eder. `string`, .NET Framework `System.String` için bir diğer addır.|
|[Demetler](tuples.md)|Adlandırılmamış, ancak muhtemelen farklı türlerin sıralı değerlerinin gruplamaları olan tanımlama gruplarını açıklar.|
|[F# Koleksiyon Türleri](fsharp-collection-types.md)|Diziler, listeler, F# diziler (seq), haritalar ve kümeler için türler de dahil olmak üzere işlevsel koleksiyon türlerine genel bakış.|
|[Listeler](lists.md)|Listeleri açıklar. İçindeki F# bir liste, aynı türden tümü sıralanmış, sabit bir öğe dizisidir.|
|[Seçenekler](options.md)|Seçenek türünü açıklar. ' De F# bir seçenek, bir değer varsa veya mevcut olmadığında kullanılır. Bir seçenek temel bir türe sahiptir ve bu tür bir değeri tutabilir ya da bir değere sahip olmayabilir.|
|[Diziler](sequences.md)|Dizileri açıklar. Dizi, tek bir türdeki öğelerin mantıksal bir dizisidir. Tek tek dizi öğeleri yalnızca gerekliyse hesaplanır, bu nedenle gösterim bir sabit öğe sayısı değerinden daha küçük olabilir.|
|[Diziler](arrays.md)|Dizileri açıklar. Diziler, hepsi aynı türde olan sabit boyutlu, sıfır tabanlı ve değiştirilebilir dizilerdir.|
|[Kayıtlar](records.md)|Kayıtları açıklar. Kayıtlar, isteğe bağlı olarak Üyeler ile adlandırılmış değerlerin basit toplamlarını temsil eder.|
|[Ayrılmış Birleşimler](discriminated-unions.md)|Her biri büyük olasılıkla farklı değerler ve türler içeren çeşitli adlandırılmış durumlardan biri olabilecek değerler için destek sağlayan ayırt edici birleşimleri açıklar.|
|[Sabit Listeleri](enumerations.md)|Numaralandırmaların tanımlanmış bir adlandırılmış değerler kümesine sahip türleri olduğunu açıklar. Kodu daha okunaklı ve bakım yapılabilir hale getirmek için bunları değişmez değerler yerine kullanabilirsiniz.|
|[Başvuru Hücreleri](reference-cells.md)|Başvuru semantiğinin değişebilir değişkenler oluşturmanızı sağlayan depolama konumları olan başvuru hücrelerini açıklar.|
|[Tür Kısaltmaları](type-abbreviations.md)|Türler için alternatif adlar olan tür kısaltmalarını açıklar.|
|[Sınıflar](classes.md)|Özelliklere, yöntemlere ve olaylara sahip olabilecek nesneleri temsil eden türler olan sınıfları açıklar.|
|[Yapılar](structures.md)|Az miktarda veri ve basit davranışa sahip olan türler için bir sınıftan daha verimli olabilecek, Compact nesne türleri olan yapıları açıklar.|
|[Arabirimler](interfaces.md)|Diğer sınıfların uygulayan ilgili üye kümelerini belirten arabirimlerini açıklar.|
|[Soyut Sınıflar](abstract-classes.md)|Uygulamaların türetilmiş sınıflar tarafından sağlanabilmesi için bazı veya tüm üyeleri uygulanmayan sınıflar olan soyut sınıfları açıklar.|
|[Tür Uzantıları](type-extensions.md)|Daha önce tanımlanmış bir nesne türüne yeni üyeler eklemenize olanak sağlayan tür uzantılarını açıklar.|
|[Esnek Türler](flexible-types.md)|Esnek türleri açıklar. Esnek tür ek açıklaması, bir parametre, değişken veya değerin belirtilen tür ile uyumlu bir tür olduğunu belirtir; burada uyumluluk, nesne odaklı sınıfların veya arabirimlerin bulunduğu konuma göre belirlenir.|
|[Temsilciler](delegates.md)|Bir işlev çağrısını nesne olarak temsil eden temsilcileri açıklar.|
|[Ölçü Birimleri](units-of-measure.md)|Ölçü birimlerini açıklar. İçindeki F# kayan nokta değerleri, genellikle uzunluğu, hacmi, kütle, vb. belirtmek için kullanılan, ilişkili ölçü birimlerine sahip olabilir.|
|[Tür Sağlayıcıları](../tutorials/type-providers/index.md)|Türü açıklar ve, veritabanlarına ve Web hizmetlerine erişmek için yerleşik tür sağlayıcılarını kullanma hakkındaki izlenecek yollara bağlantılar sağlar.|

## <a name="f-expressions"></a>F#İfadelerde

Aşağıdaki tabloda, ifadeleri betimleyen F# konular listelenmektedir.

|Başlık|Açıklama|
|-----|-----------|
|[Koşullu Ifadeler: `if...then...else`](conditional-expressions-if-then-else.md)|Kodun farklı dallarını çalıştıran ve ayrıca verilen Boolean ifadeye bağlı olarak farklı bir değere değerlendirilen `if...then...else` ifadesini açıklar.|
|[Eşleşme İfadeleri](match-expressions.md)|Desen kümesine sahip bir ifadenin karşılaştırmasına dayalı olarak dallanma denetimi sağlayan `match` ifadesini açıklar.|
|[Döngüler: `for...to` Ifade](loops-for-to-expression.md)|Bir döngü değişkeninin değer aralığı üzerinde bir döngüde yinelemek için kullanılan `for...to` ifadesini açıklar.|
|[Döngüler: `for...in` Ifade](loops-for-in-expression.md)|Bir Aralık ifadesi, sırası, liste, dizi ya da numaralandırmayı destekleyen diğer yapı gibi sıralanabilir bir koleksiyondaki bir düzenin eşleşmelerini yinelemek için kullanılan bir döngü yapısı olan `for...in` ifadesini açıklar.|
|[Döngüler: `while...do` Ifade](loops-while-do-expression.md)|Belirtilen test koşulu doğru olduğunda yinelemeli yürütmeyi (döngü) gerçekleştirmek için kullanılan `while...do` ifadesini açıklar.|
|[Nesne İfadeleri](object-expressions.md)|Mevcut bir temel türü, arabirimi veya arabirim kümesini temel alan dinamik olarak oluşturulan, anonim nesne türünün yeni örneklerini oluşturan ifadeler olan nesne ifadelerini açıklar.|
|[Gecikmeli İfadeler](lazy-expressions.md)|Hemen değerlendirilmediği hesaplamalar olan yavaş ifadeleri açıklar, ancak bunun yerine sonuç gerçekten gerektiğinde değerlendirilir.|
|[Hesaplama İfadeleri](computation-expressions.md)|İçindeki F#hesaplama ifadelerini açıklar ve bu, denetim akışı yapıları ve bağlamaları kullanılarak sıralanmakta ve birleştirilebilir hesaplamalar yazmak için kullanışlı bir sözdizimi sağlar. Bunlar, işlevsel programlardaki verileri, denetimi ve yan etkileri yönetmek için kullanılabilen bir işlevsel programlama özelliği olan *monadları*için uygun bir sözdizimi sağlamak üzere kullanılabilir. Bir tür hesaplama ifadesi, zaman uyumsuz iş akışı, zaman uyumsuz ve paralel hesaplamalar için destek sağlar. Daha fazla bilgi için bkz. [zaman uyumsuz Iş akışları](asynchronous-workflows.md).|
|[Zaman Uyumsuz İş Akışları](asynchronous-workflows.md)|Zaman uyumsuz kodu, doğal olarak zaman uyumlu olarak yazacağınız bir şekilde yazmanıza imkan tanıyan bir dil özelliği olan zaman uyumsuz iş akışlarını açıklar.|
|[Kod Alıntıları](code-quotations.md)|Kod ifadelerini programlama yoluyla oluşturmanıza ve bunlarla F# çalışmanıza olanak tanıyan bir dil özelliği olan kod tekliflerini açıklar.|
|[Sorgu İfadeleri](query-expressions.md)|İçin F# LINQ uygulayan ve bir veri kaynağına veya sıralanabilir koleksiyona karşı sorgular yazmanızı sağlayan bir dil özelliği olan sorgu ifadelerini açıklar.|

## <a name="compiler-supported-constructs"></a>Derleyici tarafından desteklenen yapılar

Aşağıdaki tabloda, derleyicinin desteklediği özel yapıları anlatan konular listelenmektedir.

|Konu|Açıklama|
|-----|-----------|
|[Derleyici Seçenekleri](compiler-options.md)|F# Derleyici için komut satırı seçeneklerini açıklar.|
|[Derleyici Yönergeleri](compiler-directives.md)|İşlemci yönergelerini ve derleyici yönergelerini açıklar.|
|[Kaynak Satırı, Dosya ve Yol Tanımlayıcıları](source-line-file-path-identifiers.md)|Kodunuzda kaynak satır numarası, dizin ve dosya adına erişmenizi sağlayan yerleşik değerler olan `__LINE__`, `__SOURCE_DIRECTORY__` ve `__SOURCE_FILE__`tanımlayıcılarını açıklar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual F#](../index.md)
