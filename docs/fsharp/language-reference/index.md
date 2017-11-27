---
title: "F# Dili Başvurusu"
description: "F # dili özelliği dili belirteçleri, kavramlar, türleri, ifadeler ve derleyici desteklenen yapı konuları için bu başvurusundan bilgi."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b1707be1-7b7c-4fdd-a717-d9c190bc5fb5
ms.openlocfilehash: 0d26d5a6f47ce8a92aefe338ea8c39295d042794
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="f-language-reference"></a>F# Dili Başvurusu

Bu bölüm, F # dili, .NET hedefleyen bir çok kip programlama dili için bir başvuru değildir. F # dili işlevsel, nesne yönelimli ve kesinlik temelli programlama modelleri destekler.


## <a name="f-tokens"></a>F # belirteçleri
Aşağıdaki tabloda, anahtar sözcükler, simgeler ve F # belirteçleri olarak kullanılan değişmez değerleri tabloları sağlayan başvuru konuları gösterir.



|Başlık|Açıklama|
|-----|-----------|
|[Klavye başvurusu](keyword-reference.md)|Tüm F # dili anahtar sözcükler hakkında bilgilere bağlantılar içerir.|
|[Simge ve işleç başvurusu](symbol-and-operator-reference/index.md)|Simgeler ve F # dilinde kullanılan işleçleri bir tablo içeriyor.|
|[Değişmez değerler](literals.md)|F # ve F # değişmez değerleri türü bilgilerini belirtmek nasıl değişmez değerler için söz dizimi açıklanmıştır.|

## <a name="f-language-concepts"></a>F # dil kavramları
Aşağıdaki tabloda başvuru konuları dil kavramları açıklamak kullanılabilir gösterir.



|Başlık|Açıklama|
|-----|-----------|
|[İşlevler](functions/index.md)|Temel birim herhangi bir programlama dili program yürütme işlevlerdir. Diğer diller olduğu gibi bir F # işlevi bir ada sahip, parametreler ve bağımsız değişkenler Al olabilir ve gövde sahiptir. F # ayrıca değerleri olarak işlevler değerlendirmesini gibi işlevsel programlama yapıları adlandırılmamış işlevler ifadelerde, yeni işlevler, curried işlevleri ve kısmi yapmamanız işlevlerin örtük tanımı oluşturmak için işlevlerin oluşturulması kullanılmasını destekler işlev bağımsız değişkenleri uygulama.|
|[F # türleri](fsharp-types.md)|F # ve F # türleri nasıl adlı ve açıklanan kullanılan türleri açıklanmaktadır.|
|[Tür çıkarımı](type-inference.md)|F # derleyici değerleri, değişkenleri, parametreler ve dönüş değerleri türlerini nasıl oluşturur açıklar.|
|[Otomatik Genelleştirme](generics/automatic-generalization.md)|F # genel yapılar açıklar.|
|[Devralma](inheritance.md)|Veya, nesne odaklı programlama subtyping "olduğunu-a" ilişki model oluşturmak için kullanılan devralma açıklanır.|
|[Üyeleri](members/index.md)|F # nesne türleri üyeleri açıklar.|
|[Parametreler ve bağımsız değişkenler](Parameters-and-Arguments.md)|Parametreleri tanımlama ve bağımsız değişkenleri işlevleri, yöntemlere ve özelliklere geçirme için dil desteğini açıklar. Başvuruya göre geçirme hakkında bilgi içerir.|
|[İşleç aşırı yüklemesi](operator-overloading.md)|Aritmetik işleçler bir sınıf ya da kayıt türü ve genel düzeyde aşırı yüklemeyi açıklar.|
|[Atama ve dönüştürmeler](casting-and-conversions.md)|F # tür dönüştürmeleri için destek açıklanır.|
|[Erişim denetimi](access-control.md)|Erişim denetimi F # açıklar. Erişim denetimi, hangi istemcilerin türleri, yöntemleri, işlevleri gibi bazı program öğeleri vb. kullanabilmek için bildirme anlamına gelir.|
|[Desen eşleştirme](pattern-matching.md)|F # dili bir desen ile Karşılaştır verileri ayıklamak, veri bağlı parçalarına veya çeşitli şekillerde verilerden bilgi ayıklamak için kullanılan giriş veri dönüştürme için kurallar desenleri açıklar.|
|[Etkin desenler](active-patterns.md)|Etkin desenler açıklar. Etkin desenler giriş verisi ayırabilir adlandırılmış bölümleri tanımlamak etkinleştirin. Etkin desenler her bölüm için özelleştirilmiş bir şekilde veri parçalayın için kullanabilirsiniz.|
|[Onaylar](assertions.md)|Açıklar `assert` hata ayıklama özelliğini, bir ifade test etmek için kullanabileceğiniz ifade. Hata ayıklama modunda başarısızlık durumunda, bir onaylama sistem hata iletişim kutusu oluşturur.|
|[Özel durum işleme](exception-handling/index.md)|Özel durum işleme F # dili desteği hakkında bilgiler içerir.|
|[öznitelikleri](attributes.md)|Bir programlama yapısı uygulanacak meta verilerini etkinleştir öznitelikleri açıklanmaktadır.|
|[Kaynak Yönetimi: `use` anahtar sözcüğü](resource-management-the-use-keyword.md)|Anahtar sözcükler açıklar `use` ve `using`, hangi denetleyebilir başlatma ve kaynak sürümü|
|[ad alanları](namespaces.md)|F # ad alanı desteğini açıklar. Bir ad alanı, kod ilgili işlevselliği alanlarına program öğeleri gruplandırması için bir ad eklemek sağlayarak düzenlemenizi sağlar.|
|[Modülleri](modules.md)|Modülleri açıklar. Bir F # modülün değerler, türleri ve F # programında işlevi değerleri gibi F # kodu, bir gruplandırmasıdır. Modüllerinde kodu gruplandırma ilgili kod birlikte tutmaya yardımcı olur ve ad çakışmalarını programınızdaki önlemeye yardımcı olur.|
|[İçeri aktarma bildirimleri: `open` anahtar sözcüğü](import-declarations-the-open-keyword.md)|Açıklar nasıl `open` çalışır. Bir alma bildirimi bir modüle ya da öğeleri bir tam ad kullanmadan başvuru isim belirtir.|
|[İmzaları](signatures.md)|İmzalar ve imza dosyalarını açıklar. Bir imza dosyası türleri, ad alanları ve modülleri gibi F # program öğeleri, bir dizi ortak imzalar hakkında bilgiler içerir. Bu program öğeleri erişilebilirliğini belirtmek için kullanılabilir.|
|[XML belgeleri](xml-documentation.md)|XML belge açıklamaları olarak da bilinen üç eğik çizgi açıklamaları belge dosyalarını oluşturmak için destek açıklanır. Yalnızca diğer .NET dilleri olduğu gibi F # kod açıklamaları belgelerinden üretebilir.|
|[Ayrıntılı sözdizimi](verbose-syntax.md)|Basit sözdizimi etkinleştirilmediğinde F # yapıları için söz dizimi açıklanmıştır. Ayrıntılı sözdizimi tarafından belirtilir `#light "off"` kod dosyasının üst yönergesi.|

## <a name="f-types"></a>F# Türleri
Aşağıdaki tabloda, F # dili tarafından desteklenen türlerini tanımlamak başvuru konuları kullanılabilir gösterir.



|Başlık|Açıklama|
|-----|-----------|
|[değerleri](values/index.md)|Belirli bir türe sahip değişmez miktarlarının değerleri açıklar; değerleri tamsayı veya kayan nokta sayıları, karakter veya metin, listeler, dizileri, dizileri, diziler, ayrılmış birleşimler, kayıtları, sınıf türleri veya işlevi değerleri olabilir.|
|[İlkel türler](primitive-types.md)|F # dilinde kullanılan temel ilkel türler açıklanmaktadır. Ayrıca karşılık gelen .NET türleri ve minimum ve maksimum değerleri her tür için sağlar.|
|[Birim türü](unit-type.md)|Açıklar `unit` belirli bir değere; olmadığını gösteren bir tür türü `unit` türüne sahip başka bir değer yok veya gerekli olduğunda bir yer tutucu olarak davranan yalnızca tek bir değer.|
|[Dizeleri](strings.md)|F # dizeleri açıklar. `string` Türü değişmez metin, Unicode karakter dizisi temsil eder. `string`bir diğer adı için `System.String` .NET Framework'teki.|
|[Diziler](tuples.md)|Muhtemelen farklı türlerde adlandırılmamış ancak sıralı değerler gruplandırmaları olan başlıkları açıklar.|
|[F # koleksiyon türleri](fsharp-collection-types.md)|Diziler, listeler, sıraları (seq), maps ve ayarlar için türleri dahil olmak üzere F # işlevsel koleksiyon türleri, genel bakış.|
|[Listeler](lists.md)|Listeleri açıklar. F # öğeleri sıralı, sabit bir dizi listesidir tüm aynı türde.|
|[Seçenekler](options.md)|Seçenek türü açıklanmaktadır. Bir değer olabilir veya olmayabilir F # bir seçenek kullanılır. Temel alınan tür seçeneği vardır ve ya da bu türde bir değer tutabilir veya bir değere sahip olmayabilir.|
|[Dizileri](sequences.md)|Dizileri açıklar. Öğeleri mantıksal bir dizi bir dizidir tüm bir tür. Temsili bir değişmez değer öğe sayısını belirten küçük olabilir tek tek sıralı öğeleri yalnızca gerekli olursa hesaplanır.|
|[Diziler](arrays.md)|Diziler açıklar. Sabit boyutlu, sıfır tabanlı, değişken dizileri ardışık veri öğelerinin, tümü aynı türde dizidir.|
|[Kayıtları](records.md)|Kayıtları açıklar. Kayıtları üyeleri isteğe bağlı olarak adlandırılmış değerler basit toplamalar temsil eder.|
|[Ayrılmış birleşimler](discriminated-unions.md)|Ayrılmış birleşimler, çeşitli adlandırılmış durumlarda, her biri farklı olması olası değerler ve türleri birini olabilecek değerleri için destek sağlayan açıklar.|
|[Numaralandırmalar](enumerations.md)|Numaralandırmalar açıklar tanımlanan bir dizi türleri değerleri adlandırılır. Kodunu daha okunabilir ve sürdürülebilir hale değişmez değerler yerine bunları kullanabilirsiniz.|
|[Başvuru hücreleri](reference-cells.md)|Başvuru semantiği ile değişebilir değişkenleri oluşturmak üzere etkinleştirmeniz depolama konumlarının başvuru hücreleri açıklar.|
|[Tür kısaltmaları](type-abbreviations.md)|Türleri için diğer adlardır tür kısaltmaları açıklar.|
|[Sınıfları](classes.md)|Özellikleri, yöntemleri ve olayları sahip nesneleri temsil eden türler sınıflar açıklanmaktadır.|
|[Yapıları](structures.md)|Küçük miktarda veri ve basit davranışı türleri için bir sınıf daha etkili olabilir compact nesne türleri yapıları açıklar.|
|[Arabirimleri](interfaces.md)|Diğer sınıflar uygulayan ilgili üyeleri kümeleri belirtmek arabirimler açıklanmaktadır.|
|[Soyut sınıflar](abstract-classes.md)|Gerçeklenmemiş, bazı veya tüm üyeleri bırakın ve böylece uygulamaları türetilmiş sınıfları tarafından sağlanabilir sınıflarının soyut sınıflar açıklanmaktadır.|
|[Tür uzantıları](type-extensions.md)|Önceden tanımlanmış nesne türü için yeni üyeler eklemenize izin türü uzantılarını açıklar.|
|[Esnek türler](flexible-types.md)|Esnek türler açıklanmaktadır. Esnek türü ek açıklama bir parametre, değişken veya değer türü ile uyumlu bir türü olduğunun bir göstergesi, uyumluluk sınıfların veya arabirimleri nesne yönelimli bir hiyerarşinin konuma göre belirlendiği belirtilmiştir.|
|[Temsilciler](delegates.md)|Bir nesne olarak bir işlev çağrısını temsil eden temsilciler açıklar.|
|[Ölçü birimleri](units-of-measure.md)|Ölçü birimleri açıklar. F #'ta kayan nokta genellikle uzunluğu, birim, yığın ve benzeri belirtmek için kullanılan ölçü ilişkili sahip.|
|[Tür sağlayıcıları](../tutorials/type-providers/index.md)|Açıklar türü ve veritabanlarına erişim ve web hizmetleri için yerleşik tür sağlayıcılarını kullanarak talimatlara bağlantılar sağlar.|

## <a name="f-expressions"></a>F # ifadeleri
Aşağıdaki tabloda, F # ifadeleri açıklayan konuları listeler.

|Başlık|Açıklama|
|-----|-----------|
|[Koşullu ifadeler:`if...then...else`](conditional-expressions-if-then-else.md)|Açıklar `if...then...else` kodunun farklı dalları çalıştırır ve verilen Boole ifadesi bağlı olarak farklı bir değer de veren ifade.|
|[Eşleşme ifadeleri](match-expressions.md)|Açıklar `match` ifadesi karşılaştırmaya ifade desenleri dayalı dallanma denetim sağlar.|
|[Döngüler: `for...to` ifade](loops-for-to-expression.md)|Açıklar `for...to` Döngü değişkeninin değerini aralığında bir döngüde yinelemek için kullanılan ifade.|
|[Döngüler: `for...in` ifade](loops-for-in-expression.md)|Açıklar `for...in` ifadesi, bir aralık ifade, dizi, liste, dizi gibi numaralandırılabilir bir koleksiyon içindeki bir desenle eşleşen üzerinden yinelemek için kullanılan bir döngü yapısı veya numaralandırma destekleyen diğer yapı.|
|[Döngüler: `while...do` ifade](loops-while-do-expression.md)|Açıklar `while...do` belirtilen test koşul doğru iken yinelemeli yürütme (döngü) gerçekleştirmek için kullanılan ifade.|
|[Nesne ifadeleri](object-expressions.md)|Yeni bir var olan temel türü, arabirim veya arabirimleri göre dinamik olarak oluşturulan, anonim nesne türü örneklerini oluşturmak ifadelerini nesne ifadeleri açıklar.|
|[Geç hesaplamalar](lazy-computations.md)|Hemen değerlendirilmez, ancak sonuç gerçekten gerekli olduğunda bunun yerine değerlendirilir hesaplamalar olan geç hesaplamalar açıklar.|
|[Hesaplama ifadeleri](computation-expressions.md)|Sıralı ve denetim akışı yapıları ve bağlamaları kullanılarak birleştirilen hesaplamalar yazmak için uygun bir söz dizimi sağlayan hesaplama ifadeleri F #'ta, açıklar. İçin kullanışlı bir söz dizimi sağlamak için kullanılabilir *monads*, verileri, Denetim ve işlevsel programlarda yan etkileri yönetmek için kullanılan bir işlev programlama özelliği. Hesaplama ifadesi, zaman uyumsuz iş akışı bir tür zaman uyumsuz ve paralel hesaplamaları için destek sağlar. Daha fazla bilgi için bkz: [zaman uyumsuz iş akışları](asynchronous-workflows.md).|
|[Zaman uyumsuz iş akışları](asynchronous-workflows.md)|Zaman uyumsuz iş akışları, zaman uyumsuz kod çok yakın, yoludur şekilde doğal olarak zaman uyumlu bir kod yazmak istediğiniz yazmanıza olanak veren bir dil özelliğini açıklar.|
|[Kod tırnak işaretleri](code-quotations.md)|Kod tırnak işaretleri oluşturmak ve F # kodu ifadelerle programlı olarak çalışmanıza olanak sağlayan bir dil özelliğini açıklar.|
|[Sorgu ifadeleri](query-expressions.md)|Sorgu ifadeleri LINQ F # için uygulayan ve bir veri kaynağı veya numaralandırılabilir koleksiyonu sorguları yazmanızı sağlar bir dil özelliğini açıklar.|

## <a name="compiler-supported-constructs"></a>Derleyici tarafından desteklenen yapıları
Aşağıdaki tabloda özel derleyici desteklenen yapıları açıklayan konuları listeler.

|Konu|Açıklama|
|-----|-----------|
|[Derleyici Seçenekleri](compiler-options.md)|F # derleyici komut satırı seçeneklerini açıklar.|
|[Derleyici yönergeleri](compiler-directives.md)|İşlemci yönergeleri ve derleyici yönergeleri açıklar.|
|[Kaynak satırı, dosya ve yol tanımlayıcıları](source-line-file-path-identifiers.md)|Tanımlayıcılar açıklanmaktadır `__LINE__`, `__SOURCE_DIRECTORY__` ve `__SOURCE_FILE__`, kaynak satır numarası, dizin ve dosya adı kodunuzdaki erişim sağlayan yerleşik değerleri şunlardır.|

## <a name="see-also"></a>Ayrıca Bkz.
[Visual F #](../index.md)
