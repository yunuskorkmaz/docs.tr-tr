---
title: F# turu
description: Bazı F# programlama dilinde kod örnekleriyle birlikte bu turda anahtar özelliklerini inceleyin.
ms.date: 02/28/2018
ms.openlocfilehash: d129e2312ae3da64f04b3bbb0bbd0b4d77aad36e
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2018
ms.locfileid: "42924527"
---
# <a name="tour-of-f"></a>F# turu #

F# hakkında bilgi edinmek için en iyi yolu, okuma ve F# kodu yazacak sağlamaktır.  Bu makalede tura F# dilinin temel özelliklerinden bazıları aracılığıyla görür ve makinenizde yürütebilir bazı kod parçacıklarına verin.  Bir geliştirme ortamını ayarlama bilgi edinmek için kullanıma [Başlarken](tutorials/getting-started/index.md).

İki birincil kavram vardır F#: işlevleri ve türleri.  Bu Turun, bu iki kavrama kalan dil özelliklerini vurgulamak.

## <a name="functions-and-modules"></a>İşlevler ve modüller

En temel herhangi bir F# programı parçalarıdır ***işlevleri*** düzenlenir ***modülleri***.  [İşlevleri](language-reference/functions/index.md) çıktı üretmek için girişler çalışma gerçekleştirme ve altında düzenlenmiş [modülleri](language-reference/modules.md), F# içinde öğeleri gruplandırma birincil yolu olduğu.  Kullanılarak tanımlanır [ `let` bağlama](language-reference/functions/let-bindings.md), işlevin bir ad verin ve bağımsız değişkenleri tanımlayın.

[!code-fsharp[BasicFunctions](../../samples/snippets/fsharp/tour.fs#L101-L133)]

`let` bir değeri bir değişkene diğer dillerdeki benzer bir adla bağlama nasıl bağlamaları de olur.  `let` bağlamaları ***değişmez*** yerinde bir değer veya işlevi için bir ad bağlandıktan sonra değiştirilemez, yani varsayılan olarak,.  Bu değişkenler olan diğer dillerdeki aksine, ***değişebilir***, değerlerine anlamı değiştirilebilir herhangi bir noktada süre.  Değişebilir bir bağlama gerektiriyorsa, kullanabileceğiniz `let mutable ...` söz dizimi.

[!code-fsharp[Immutability](../../samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a>Sayılar ve Boole değerlerini dizeleri

F# aynı temel bir .NET dili olarak destekler [ilkel türler](language-reference/primitive-types.md) .NET içinde mevcut.

Çeşitli sayısal türleri F# dilinde gösterilir aşağıda verilmiştir:

[!code-fsharp[Numbers](../../samples/snippets/fsharp/tour.fs#L49-L68)]

Boole değerlerin işte ve temel koşullu mantık gerçekleştirme şu şekilde görünür:

[!code-fsharp[Bools](../../samples/snippets/fsharp/tour.fs#L142-L152)]

Ve hangi temel işte [dize](language-reference/strings.md) işleme şöyle:

[!code-fsharp[Strings](../../samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a>Demetler

[Diziler](language-reference/tuples.md) F# gerçekten önemli olan.  Bunlar, kendilerini değeri olarak davranılıp adlandırılmamış ancak sıralı değerleri gruplandırmasıdır.  Bunları, diğer değerlerinden toplanmış değerleri olarak düşünün.  Rahatça birden çok değer döndüren bir işlevden veya bazı geçici kolaylık sağlamak için değerleri gruplandırma gibi pek çok kullanımı, sahiptirler.

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L186-L203)]

F# 4.1 itibariyle, ayrıca oluşturabilirsiniz `struct` tanımlama grubu.  Bu ayrıca tam da C# 7/Visual Basic 15 demetleri ile birlikte çalışmak `struct` diziler:

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L205-L218)]

Çünkü dikkat etmeniz önemlidir `struct` diziler değer türleri, diziler, başvuru için örtük olarak dönüştürülemez ya da tam tersi.  Başvuru ve yapı tanımlama grubu arasında açıkça dönüştürmeniz gerekir.

## <a name="pipelines-and-composition"></a>İşlem hatları ve oluşturma

İşleçler gibi kanal `|>` F# içinde veri işleme sırasında yaygın olarak kullanılır. Bu işleçler "işlem" hatları işlevlerin esnek bir şekilde kurmanızı sağlayan işlevlerdir. Aşağıdaki örnek, basit bir işlev işlem hattını oluşturmak üzere bu işleçler avantajlarından nasıl yararlanabilirsiniz aracılığıyla anlatılmaktadır:

[!code-fsharp[Pipelines](../../samples/snippets/fsharp/tour.fs#L227-L282)]

Yapılan önceki örnekte F# bu kadar listesini işleme işlevleri, birinci sınıf işlevler dahil olmak üzere, birçok özelliklerinin kullanımını ve [kısmi uygulama](language-reference/functions/index.md#partial-application-of-arguments). Her birinin söz konusu kavramlar derin bir anlayış biraz Gelişmiş hale olsa da, bu işlevler işlem hatları oluştururken verileri işlemek için nasıl bir kolayca kullanılabilir açık olmalıdır.

## <a name="lists-arrays-and-sequences"></a>Listeler, diziler ve dizileri

F# çekirdek kitaplığının üç birincil koleksiyon türlerini listeler, diziler ve dizileri var.

[Listeler](language-reference/lists.md) sıralı, değişmez koleksiyonları öğeleri aynı türde olan.  Bunlar tek bağlantılı listeler, yani büyük iseler, numaralandırma, ancak rastgele erişim ve birleştirme için kötü bir seçim için yöneliktir.  Bu listeler genelde bir listedir bağlantılı liste listeleri temsil etmek için kullanmayın diğer popüler dilde aksine.

[!code-fsharp[Lists](../../samples/snippets/fsharp/tour.fs#L309-L359)]

[Diziler](language-reference/arrays.md) sabit boyutu, *değişebilir* aynı türdeki öğelerin koleksiyonu.  Öğelerin hızlı rastgele erişim desteği ve yalnızca bitişik bellek bloklarını oldukları için F# listeleri işlevinden daha hızlıdır.

[!code-fsharp[Arrays](../../samples/snippets/fsharp/tour.fs#L368-L407)]

[Dizileri](language-reference/sequences.md) aynı türdeki tüm öğeleri mantıksal bir dizi.  Bunlar daha genel bir tür listeler ve dizi, öğeleri mantıksal bir dizi, "Görünüm" yeterli olur.  Bunlar olabilir çünkü bunlar da göze ***yavaş***, yani yalnızca gerektiğinde öğeleri hesaplanabilir.

[!code-fsharp[Sequences](../../samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a>Özyinelemeli İşlevler

Koleksiyonları veya öğelerin sıralarının işleme genellikle yapılır [özyineleme](language-reference/functions/index.md#recursive-functions) F#.  F# döngüler ve kesin programlama desteği sahip olsa da, doğruluğu garanti etmek daha kolay olduğundan, özyineleme tercih edilir.

>[!NOTE]
Aşağıdaki örnek deseni ile eşleşen birini kullanır `match` ifade.  Bu temel yapı, bu makalenin sonraki bölümlerinde ele alınmıştır.

[!code-fsharp[RecursiveFunctions](../../samples/snippets/fsharp/tour.fs#L461-L500)]

F# de Tail çağrısı iyileştirmesi için tam destek, böylece bunlar yalnızca bir döngü yapısı kadar hızlı ilerleyebilirler özyinelemeli çağrılar iyileştirmeye yönelik bir yol yoktur.

## <a name="record-and-discriminated-union-types"></a>Kayıt ve ayrılmış birleşim türleri

Kayıt ve birleşim türlerini F# kodunda kullanılan iki temel veri türleri ve genellikle bir F# programında verileri temsil etmek için en iyi yoludur.  Bu sınıflar benzer diğer dillerde sağlar ancak kendi birincil farklardan biri yapısal eşitlik semantiğine sahip olduğunu belirtir.  Bunun anlamı, "yerel" benzerdir ve eşitlik oldukça basittir; yalnızca biri diğerine eşit olup olmadığını denetleyin.

[Kayıtları](language-reference/records.md) olan toplama (örneğin, yöntemler) isteğe bağlı üyeleriyle adlandırılmış değerler.  C# veya Java ile ilgili bilgi sahibi değilseniz, ardından bu yapısal eşitlik olduğu ve seremoni daha az POCOs veya pojo'ları - benzer gelecektir.

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L507-L559)]

F# 4.1 itibariyle, kayıt olarak da gösterebilir `struct`s.  Bunun `[<Struct>]` özniteliği:

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L561-L568)]

[Ayrılmış birleşimler (DUs)](language-reference/discriminated-unions.md) birkaç adlandırılmış forms veya durumları olabilecek değerler.  Tür içinde depolanan verileri ayrı değerlerden biri olabilir.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L575-L631)]

DUs olarak da kullanabilirsiniz *tek örneği ayırt edici birleşimler*, ilkel türler üzerinde modelleme etki alanıyla yardımcı olmak için.  Çoğu zaman, dizeler ve diğer ilkel türler bir şeyi temsil etmek için kullanılır ve bu nedenle belirli bir anlamı verilir.  Ancak, veriler yalnızca ilkel gösterimini kullanarak yanlışlıkla yanlış bir değer atama içinde sebep olabilir!  Her ayrı tek örneği UNION olarak bilgi türünü temsil eden Bu senaryoda doğruluk zorunlu kılabilir.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L633-L654)]

Temeldeki değeri bir tek örneği ayırt edici birleşim içinde almak için yukarıdaki örnekte gösterildiği gibi açıkça unwrap gerekir.

Ayrıca, DUs da yinelenen tanımları kolayca ağaçları ve kendiliğinden özyinelemeli verileri temsil eden olanak tanıyan destekler.  Örneğin, işte bir ikili arama ağacını ile nasıl temsil `exists` ve `insert` işlevleri.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L656-L683)]

Bu özyinelemeli yapısına işletim DUs ağacında bir veri türü özyinelemeli yapısını temsil etmek izin olduğundan, oldukça basittir ve doğruluğu garanti eder.  Ayrıca desen eşleştirme aşağıda gösterildiği gibi desteklenir.

Ayrıca, DUs olarak gösterebilir `struct`s ile `[<Struct>]` özniteliği:

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L685-L696)]

Ancak, bu işlem yapıldığında akılda tutulması gereken iki önemli nokta vardır:

1. Yinelemeli olarak tanımlanmış bir yapı DU olamaz.
2. Bir yapı DU her biri kendi çalışmaları için benzersiz adlara sahip olmalıdır.

Yukarıdaki takip edilmemesi bir derleme hatasına neden olur.

## <a name="pattern-matching"></a>Desen Eşleştirme

[Eşleşen desen](language-reference/pattern-matching.md) sağlayan doğruluk F# türleri üzerinde çalışması için F# dil özelliğidir.  Yukarıdaki örneklerde, büyük olasılıkla oldukça fark etmiş `match x with ...` söz dizimi.  Bu yapı ne bilinen aracılığıyla bir veri türü kapsamlı desen eşleştirme kullanılırken tüm olası durumları dikkate almak için zorlamak için veri türleri "şekline" anlayabilmeniz derleyici sağlar.  Bu doğruluğu inanılmaz güçlü ve zekice "ne bir çalışma zamanı sorunu derleme zamanı içine normalde olacağını kaldırmak için" kullanılabilir.

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L705-L742)]

Toplu kullanabilirsiniz `function` yapan işlevleri kullanın yazarken, kullanışlı olan desen eşleştirme için yapı [kısmi uygulama](language-reference/functions/index.md#partial-application-of-arguments):

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L744-L762)]

Bir sorun fark kullanımıdır `_` deseni.  Bu olarak bilinir [joker karakter deseni](language-reference/pattern-matching.md#wildcard-pattern), "Miyim yoksa dikkatli bir şey nedir" ifadesini içeren bir yolu olan.  Kullanışlı olsa da, kapsamlı desen eşleştirme yanlışlıkla atlamak ve artık fayda derleme zamanı enforcements kullanırken dikkatli olmazsanız `_`.  Ayrılmış bir tür hakkında belirli bilgilere İlgilenmiyor, en iyi şekilde kullanılır anlamlı bir desen eşleme ifadesinde durumlarda tüm numaralandırılan olduğunda ne zaman eşleştirme veya son yan desen.

[Etkin desenler](language-reference/active-patterns.md) desen eşleştirme ile kullanmak için güçlü bir başka yapının olan.  Özel formlar, bunları desen eşleştirme çağrısı sitesinde parçalama uygulamasına giriş veri bölümü olanak sağlar.  Bunlar ayrıca, böylece bölümü bir işlev olarak tanımlamak için izin verme parametreli olabilir.  Etkin desenler desteklemek için önceki örneği genişleterek şuna benzer:

[!code-fsharp[ActivePatterns](../../samples/snippets/fsharp/tour.fs#L764-L786)]

## <a name="optional-types"></a>İsteğe bağlı türler

Ayırt edici birleşim türlerinin bir özel durum seçeneği, F# çekirdek kitaplığının bir parçası olduğunu oldukça kullanışlı olduğu türüdür.

[Seçenek türü](language-reference/options.md) iki durumlarından biri temsil eden bir türdür: bir değer ya da hiç bir şey.  Burada bir değer olabilir veya belirli bir işlemden oluşturmayabilir hiçbir senaryoda kullanılır.  Bunun ardından bir çalışma zamanı sorunu yerine derleme zamanı endişe yaparak her iki durumda, hesap için zorlar.  Bunlar genellikle API'leri kullanılır nerede `null` böylece hakkında endişelenme gereksinimini ortadan kullanılan bunun yerine, "şey" temsil etmek için `NullReferenceException` birçok durumda.

[!code-fsharp[Options](../../samples/snippets/fsharp/tour.fs#L789-L814)]

## <a name="units-of-measure"></a>Ölçü Birimleri

F# tür sistemi benzersiz bir özellik ölçü birimleri ile sayısal değişmez değerleri için bağlam sağlamak için olanağıdır.

[Ölçü birimleri](language-reference/units-of-measure.md) gibi ölçümleri, bir birim için bir sayısal tür ilişkilendirmek izin ve sahip işlevleri gerçekleştiren iş birimleri sayısal değişmez değerler yerine.  Bu, geçirilen sayısal değişmez değerlerinin türleri mantıklı bir bağlamında, bu nedenle çalışma zamanı hatalarını ortadan kaldırarak, bu tür iş ile ilişkili doğrulamak derleyiciyi etkinleştirir.

[!code-fsharp[UnitsOfMeasure](../../samples/snippets/fsharp/tour.fs#L817-L842)]

F# çekirdek kitaplığının birçok sı birim türleri ve birim dönüştürmeleri tanımlar.  Daha fazla bilgi için kullanıma [Microsoft.FSharp.Data.unitsystems.sı Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d).

## <a name="classes-and-interfaces"></a>Sınıfları ve arabirimleri

F# ayrıca sahip .NET sınıfları için tam destek [arabirimleri](language-reference/interfaces.md), [soyut sınıflar](language-reference/abstract-classes.md), [devralma](language-reference/inheritance.md)ve benzeri.

[Sınıflar](language-reference/classes.md) .NET nesnelerini temsil eden türleri, özellikleri, yöntemleri ve olayları olarak sahip olabilir, [üyeleri](language-reference/members/index.md).

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L845-L880)]

Genel sınıfları tanımlama da çok kolaydır.

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L883-L908)]

Bir arabirim uygulamak için kullanabilirsiniz `interface ... with` sözdizimi veya [nesne ifadesi](language-reference/object-expressions.md).

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L911-L934)]

## <a name="which-types-to-use"></a>Hangi türlerin kullanımı

Sınıflar, kayıtları, ayırt edici birleşimler ve diziler varlığını müşteri adayları için önemli bir soru: hangi kullanmalısınız?  Çoğu her şeyi gibi hayatta yanıt koşullarınıza üzerinde bağlıdır.

Diziler, birden çok değer döndüren bir işlevden ve geçici toplamını değerleri içeren bir değer mükemmel özellikler.

Bir "adımı yukarı" etiketleri ve isteğe bağlı üyeleri için destek adlı bir tanımlama grubu kayıtlardır.  Bunlar, veri aktarım sırasında program aracılığıyla düşük seremoni gösterimi için mükemmeldir.  Sahip oldukları yapısal eşitlik için karşılaştırma kullanımı kolaydır.

Ayrılmış birleşimler pek çok kullanımı vardır, ancak temel avantajı, bunları "veri sahip olabileceği tüm olası şekiller için" hesap için desen eşleştirme ile birlikte kullanabilirler sağlamaktır.  

Sınıflar gibi bilgileri temsil eder ve işlevselliği için bu bilgileri ayrıca tie gerektiğinde nedeni, çok sayıda için mükemmeldir.  Bazı verileri, kavramsal olarak bağlı işlevselliği olduğunda bir, sınıflar ve Object-Oriented programlama ilkeleri kullanarak büyük bir avantaj udur.  Bu diller sınıfları için neredeyse her şey kullandıkça da tercih edilen veri türü C# ve Visual Basic ile birlikte çalışırken sınıflardır.

## <a name="next-steps"></a>Sonraki Adımlar

Birincil dili özelliklerinin bazılarını gördüğünüze göre ilk, F# programları yazmak için hazır!  Kullanıma [Başlarken](tutorials/getting-started/index.md) geliştirme ortamınızı ayarlama ve bazı kodlar yazma hakkında bilgi edinmek için.

Daha fazla bilgi için sonraki adımlar dilediğiniz olabilir, ancak öneririz [ilk sınıf değerleri işlevler](introduction-to-functional-programming/functions-as-first-class-values.md) <!--[Introduction to Functional Programming in F#](introduction-to-functional-programming/index.md)--> işlevsel programlama kavramları ile daha rahat kullanmak için.  Bunlar, F# içinde sağlam programları derleme gerekli olacaktır.

Ayrıca, kullanıma [F# dili başvurusu](language-reference/index.md) kavramsal içeriğe kapsamlı koleksiyonu üzerinde F# görmek için.
