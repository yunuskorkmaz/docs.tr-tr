---
title: F# Turu
description: Kod örnekleri ile bu turda F# programlama dilinin bazı temel özelliklerini inceleyin.
ms.date: 11/06/2018
ms.openlocfilehash: cfea2827dcec65f9e3606e8528179029e1f2db84
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423813"
---
# <a name="tour-of-f"></a>F\# turu

' İ öğrenmenin F# en iyi yolu, kodu okumanız F# ve yazmaktır. Bu makale, F# dilin bazı önemli özelliklerinden bir tur görevi görür ve makinenizde yürütebilmeniz için bazı kod parçacıklarını sağlar. Geliştirme ortamı ayarlama hakkında bilgi edinmek [için Başlarken 'e göz atın.](get-started/index.md)

' De F#iki birincil kavram vardır: işlevler ve türler.  Bu tur, bu iki kavrama giren dilin özelliklerini vurgulayacak.

## <a name="executing-the-code-online"></a>Kodu çevrimiçi olarak yürütme

Makinenizde F# yüklü değilse, [Webassembly üzerinde TRY F# ](https://tryfsharp.fsbolero.io/)ile tarayıcınızda tüm örnekleri çalıştırabilirsiniz. Fable, doğrudan tarayıcınızda yürüten F# bir diyalekdır. REPL 'da izleyen örnekleri görüntülemek için, > örnekleri gözden geçirin ve Fable REPL 'un sol taraftaki menü çubuğunda **> turu F# öğrenin** .

## <a name="functions-and-modules"></a>İşlevler ve modüller

Herhangi bir F# programın en temel parçaları, ***modüller***halinde düzenlenmiş ***işlevlerdir*** .  [İşlevler](./language-reference/functions/index.md) , çıktılar oluşturmak için girişler üzerinde çalışır ve bunları gruplandırmanız gereken birincil yoldur [modüller](./language-reference/modules.md)altında düzenlenir F#.  Bu, işleve bir ad veren ve bağımsız değişkenlerini tanımlayan [`let` bağlama](./language-reference/functions/let-bindings.md)kullanılarak tanımlanır.

[!code-fsharp[BasicFunctions](~/samples/snippets/fsharp/tour.fs#L101-L133)]

`let` bağlamaları Ayrıca, diğer dillerdeki bir değişkene benzer şekilde bir değeri bir ada bağlamalardır.  `let` bağlamaları varsayılan olarak ***sabittir*** , yani bir değer veya işlev bir ada bağlandığında, yerinde değiştirilemez.  Bu, ***değişebilir***olan diğer dillerdeki değişkenlere karşılık gelir, yani değerleri zaman içinde herhangi bir noktada değiştirilebilir.  Kesilebilir bir bağlamaya ihtiyacınız varsa `let mutable ...` söz dizimini kullanabilirsiniz.

[!code-fsharp[Immutability](~/samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a>Sayılar, Boole değerleri ve dizeler

.NET dili olarak, F# .NET sürümünde var olan temel [temel türleri](language-reference/basic-types.md) destekler.

Aşağıda çeşitli sayısal türlerin temsil edildiği gösterilmektedir F#:

[!code-fsharp[Numbers](~/samples/snippets/fsharp/tour.fs#L49-L68)]

Aşağıda, hangi Boole değerleri ve temel koşullu mantık gerçekleştiriliyor şöyle görünür:

[!code-fsharp[Bools](~/samples/snippets/fsharp/tour.fs#L142-L152)]

İşte temel [dize](./language-reference/strings.md) işleme şöyle görünür:

[!code-fsharp[Strings](~/samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a>Demetler

[Tanımlama grupları](./language-reference/tuples.md) , içinde F#büyük bir işlem içerir.  Bunlar, değerler olarak kabul edilebilir adsız, ancak sıralı değerler grubudur.  Bunları diğer değerlerden toplanmış değerler olarak düşünün.  Bir işlevden çok sayıda değer döndürme veya bazı geçici kolaylık için değerleri gruplama gibi birçok kullanımı vardır.

[!code-fsharp[Tuples](~/samples/snippets/fsharp/tour.fs#L186-L203)]

F# 4,1 itibariyle `struct` tanımlama grupları da oluşturabilirsiniz.  Bunlar ayrıca, aynı zamanda `struct` tanımlama grupları olan C# 7/Visual Basic 15 tanımlama grupları ile tamamen birlikte çalışır:

[!code-fsharp[Tuples](~/samples/snippets/fsharp/tour.fs#L205-L218)]

`struct` tanımlama grupları değer türleri olduğundan, örtülü olarak başvuru tanımlama gruplarına dönüştürülemediği veya bunun tersi unutulmamalıdır.  Bir başvuru ve yapı grubu arasında açıkça dönüştürmeniz gerekir.

## <a name="pipelines-and-composition"></a>İşlem hatları ve kompozisyon

`|>` gibi kanal işleçleri, içindeki F#verileri işlerken kapsamlı bir şekilde kullanılır. Bu işleçler, işlevlerin "işlem hatlarını" esnek bir şekilde oluşturmanızı sağlayan işlevlerdir. Aşağıdaki örnek, basit bir işlevsel işlem hattı oluşturmak için bu işleçlerden nasıl yararlanacağınızı göstermektedir:

[!code-fsharp[Pipelines](~/samples/snippets/fsharp/tour.fs#L227-L282)]

Önceki örnek F#, liste işleme işlevleri, birinci sınıf işlevler ve [kısmi uygulama](./language-reference/functions/index.md#partial-application-of-arguments)dahil olmak üzere birçok özelliğinin kullanımını yaptı. Bu kavramların her birinin derinlemesine bir şekilde anlaşılmasına rağmen, işlem hatları oluştururken verileri işlemek için ne kadar kolay bir şekilde işlev kullanılabileceğini de net bir şekilde kullanabilirsiniz.

## <a name="lists-arrays-and-sequences"></a>Listeler, diziler ve diziler

Listeler, diziler ve diziler, F# çekirdek kitaplığındaki üç birincil koleksiyon türüdür.

[Listeler](./language-reference/lists.md) sıralanmış, aynı türde öğelerin sabit koleksiyonlarıdır.  Bunlar, listedir bağlantılı listelerdir, bu, numaralandırma için amaçlılar, ancak büyük olmaları durumunda rastgele erişim ve birleştirme için zayıf bir seçimdir.  Bu, genellikle listeleri temsil etmek için listedir bağlantılı bir liste kullanmayan diğer popüler dillerdeki listelerin aksine.

[!code-fsharp[Lists](~/samples/snippets/fsharp/tour.fs#L309-L359)]

[Diziler](./language-reference/arrays.md) aynı türdeki öğelerin sabit boyutlu ve *değişebilir* koleksiyonlarıdır.  Öğelerin hızlı rastgele erişimini destekler ve yalnızca bitişik bellek blokları olduklarından F# listelerden daha hızlıdır.

[!code-fsharp[Arrays](~/samples/snippets/fsharp/tour.fs#L368-L407)]

[Diziler](./language-reference/sequences.md) , hepsi aynı türde olan mantıksal bir öğe dizisidir.  Bunlar, listelerden ve dizilerden herhangi bir mantıksal dizi öğe için "görünümlerinizle" olmayan daha genel bir türdür.  Ayrıca, bu öğeler ***yavaş***olabildiğinden, öğelerin yalnızca gerektiğinde hesaplanabilecek anlamına gelir.

[!code-fsharp[Sequences](~/samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a>Özyinelemeli İşlevler

Koleksiyonları veya öğe dizilerini işlemek genellikle içinde F# [özyineleme](./language-reference/functions/index.md#recursive-functions) ile yapılır.  , F# Döngüler ve kesinlik temelli programlama desteğiyle birlikte doğruluğu güvence altına almak daha kolay olduğundan özyineleme tercih edilir.

> [!NOTE]
> Aşağıdaki örnek, `match` ifadesi ile eşleşen düzenin kullanımını sağlar.  Bu temel yapı, bu makalenin ilerleyen kısımlarında ele alınmıştır.

[!code-fsharp[RecursiveFunctions](~/samples/snippets/fsharp/tour.fs#L461-L500)]

F#Ayrıca, bir döngü yapısı kadar hızlı olacak şekilde özyinelemeli çağrıları en iyi duruma getirmenin bir yolu olan kuyruk çağrısı Iyileştirmesi için tam destek içerir.

## <a name="record-and-discriminated-union-types"></a>Kayıt ve ayırt edici birleşim türleri

Kayıt ve birleşim türleri F# kodda kullanılan iki temel veri türüdür ve genellikle bir F# programdaki verileri göstermenin en iyi yoludur.  Bu, diğer dillerdeki sınıflara benzer olsa da, birincil farklarından biri yapısal eşitlik semantiklerinden biridir.  Bu, "yerel olarak" karşılaştırılabilir ve eşitlik basit oldukları anlamına gelir. yalnızca birinin diğerine eşit olup olmadığını kontrol edin.

[Kayıtlar](./language-reference/records.md) , isteğe bağlı üyelere (örneğin, Yöntemler) sahip adlandırılmış değerlerin toplamıdır.  C# Ya da Java hakkında bilginiz varsa, bu, yalnızca yapısal eşitlik ve daha az sertifika Içeren Pocos veya POJOs 'ye benzer.

[!code-fsharp[Records](~/samples/snippets/fsharp/tour.fs#L507-L559)]

F# 4,1 itibariyle kayıtları `struct`s olarak da temsil edebilirsiniz.  Bu, `[<Struct>]` özniteliğiyle yapılır:

[!code-fsharp[Records](~/samples/snippets/fsharp/tour.fs#L561-L568)]

[Ayırt edici birleşimler (PDU)](./language-reference/discriminated-unions.md) , bir dizi adlandırılmış form veya durum olabilen değerlerdir.  Tür içinde depolanan veriler, birkaç farklı değerden biri olabilir.

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L575-L631)]

Ayrıca, temel türler üzerinde etki alanı modellemeye yardımcı olması için, aynı zamanda *ayrılmış birleşimler*olarak aynı şekilde kullanabilirsiniz.  Genellikle, dizeler ve diğer temel türler bir şeyi temsil etmek için kullanılır ve bu nedenle belirli bir anlamı verilir.  Ancak, yalnızca verilerin temel gösteriminin kullanılması yanlışlıkla yanlış bir değer atanmasına neden olabilir!  Her bir bilgi türünü ayrı tek durum birleşimi olarak temsil etmek, bu senaryoda doğruluğu zorunlu kılabilir.

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L633-L654)]

Yukarıdaki örnekte gösterildiği gibi, temel alınan değeri tek örnekli ayırt edici bir birleşimde almak için, açıkça sarmalaması geri alınmalıdır.

Ayrıca, iletimetriyi kolayca ve doğal olarak özyinelemeli verileri göstermenize olanak tanıyan özyinelemeli tanımları da destekler.  Örneğin, `exists` ve `insert` işlevlerle bir Ikili arama ağacını nasıl temsil edebilirsiniz.

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L656-L683)]

Çünkü, veri türü içindeki ağacın özyinelemeli yapısını temsil etmeniz izin sağladığından, bu özyinelemeli yapı üzerinde çalışma basittir ve doğruluğu garanti eder.  Ayrıca, aşağıda gösterildiği gibi, model eşleştirmesinde de desteklenir.

Ayrıca, `[<Struct>]` özniteliğiyle `struct`s olarak aynı şekilde temsil edebilirsiniz:

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L685-L696)]

Ancak, bunu yaparken göz önünde bulundurmanız gereken iki önemli nokta vardır:

1. Bir struct DU özyinelemeli olarak tanımlanamaz.
2. Bir struct 'ın her biri için benzersiz adlara sahip olması gerekir.

Yukarıdaki işlemin başarısız olması, derleme hatasına neden olur.

## <a name="pattern-matching"></a>Desen Eşleştirme

[Model eşleştirme](./language-reference/pattern-matching.md) , türler F# üzerinde F# çalışma için doğruluğu sağlayan dil özelliğidir.  Yukarıdaki örneklerde büyük olasılıkla `match x with ...` bir sözdizimi olduğunu fark etmiş olursunuz.  Bu yapı, veri türlerinin "şeklini" anlayan bir veri türü kullanırken tüm olası durumları hesaba zorlaştırmaya zorlamak için derleyicinin izin verdiği "şekli" olan derleyiciye izin verir.  Bu, doğruluk açısından güçlü bir inanılmaz ve normalde derleme zamanında çalışma zamanı olması gereken şeyleri "kaldırmak" için yeniden kullanılabilir.

[!code-fsharp[PatternMatching](~/samples/snippets/fsharp/tour.fs#L705-L742)]

Fark ettiğiniz bir şey `_` deseninin kullanımı olduğunu fark etmiş olabilirsiniz.  Bu, "bir şeyin ne olduğunu merak ediyorum" şeklinde bir yol gösteren [joker karakter stili](./language-reference/pattern-matching.md#wildcard-pattern)olarak bilinir.  Kullanışlı olsa da, `_`kullanımı konusunda dikkatli olmadığınız durumlarda, ayrıntılı bir şekilde eşleştirmeyi daha da atlayabilirsiniz ve derleme zamanı zorlamalarından artık faydalanabilirsiniz.  Bir model eşleştirme ifadesinde tüm anlamlı durumları Numaralandırdığınızda, bu en iyi şekilde, kalıp eşleme veya son yan tümce için belirli parçaları önemsemezseniz kullanılır.

[Etkin desenler](./language-reference/active-patterns.md) , desen eşleştirme ile kullanmak için başka bir güçlü yapıdır.  Bu kişiler, giriş verilerini özel formlara bölümleyerek, bu dosyaları model eşleştirme çağrı sitesinde oluşturmayı sağlar.  Bunlar ayrıca parametrelenebilir ve bu sayede bölümü bir işlev olarak tanımlamaya izin verir.  Etkin desenleri desteklemek için önceki örneğin genişletilmesi şuna benzer:

[!code-fsharp[ActivePatterns](~/samples/snippets/fsharp/tour.fs#L764-L786)]

## <a name="optional-types"></a>İsteğe bağlı türler

Ayırt edici birleşim türlerinin bir özel durumu, seçenek türüdür ve bu, F# Çekirdek Kitaplığı 'nın bir parçası olduğundan kullanışlıdır.

[Seçenek türü](./language-reference/options.md) , iki durumlardan birini temsil eden bir türdür: bir değer veya hiç bir şey yok.  Bir değerin belirli bir işlemden kaynaklanan veya neden olabileceği herhangi bir senaryoda kullanılır.  Bu, her iki durumda da size bir çalışma zamanı sorunu yerine bir derleme zamanı sorunu sunarak hesaba zorlar.  Bunlar genellikle `null`, bunun yerine "hiçbir şey" göstermek için kullanıldığı API 'lerde kullanılır, bu nedenle birçok durumda `NullReferenceException` endişelenmenize gerek kalmaz.

[!code-fsharp[Options](~/samples/snippets/fsharp/tour.fs#L789-L814)]

## <a name="units-of-measure"></a>Ölçü Birimleri

Tür sisteminin benzersiz bir F#özelliği, ölçü birimleri aracılığıyla sayısal sabit değerler için bağlam sağlayabilmesidir.

[Ölçü birimleri](./language-reference/units-of-measure.md) , sayısal bir türü ölçüm gibi bir birimle ilişkilendirmenize ve işlevlerin sayısal değişmez değerler yerine birimlerde çalışma gerçekleştirmesini sağlar.  Bu, derleyicinin verilen sayısal sabit değer türlerinin belirli bir bağlam altında anlamlı olduğunu doğrulamasını ve bu sayede çalışma zamanı hatalarını ilgili çalışma türüyle ortadan kaldırmayı sağlar.

[!code-fsharp[UnitsOfMeasure](~/samples/snippets/fsharp/tour.fs#L817-L842)]

F# Çekirdek KITAPLıK birçok sı birim türünü ve birim dönüştürmeleri tanımlar.  Daha fazla bilgi edinmek için [Microsoft.FSharp.Data.UnitSystems.sı ad alanına](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d)göz atın.

## <a name="classes-and-interfaces"></a>Sınıflar ve arabirimler

F#Ayrıca .NET sınıfları, [arabirimler](./language-reference/interfaces.md), [soyut sınıflar](./language-reference/abstract-classes.md), [Devralma](./language-reference/inheritance.md)vb. için de tam desteğe sahiptir.

[Sınıflar](./language-reference/classes.md) , [üyeleri](./language-reference/members/index.md)olarak özelliklere, yöntemlere ve olaylara sahip olabilen .net nesnelerini temsil eden türlerdir.

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L845-L880)]

Genel sınıfların tanımlanması de çok basittir.

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L883-L908)]

Bir arabirim uygulamak için `interface ... with` söz dizimini veya bir [nesne ifadesini](./language-reference/object-expressions.md)kullanabilirsiniz.

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L911-L934)]

## <a name="which-types-to-use"></a>Kullanılacak türler

Sınıfların, kayıtların, ayırt edici birleşimlerin ve tanımlama gruplarının varlığı, önemli bir soruya yol açar: kullanmanız gerekir mi?  Her şeyin yaşam süresi gibi, yanıt sizin koşullara bağlıdır.

Tanımlama alanları, bir işlevden birden çok değer döndürmek ve değerin kendisi olarak geçici bir toplama değeri kullanmak için idealdir.

Kayıtlar, adlandırılmış etiketlere sahip olan ve isteğe bağlı Üyeler için desteğe sahip olan başlıkların "adım adım".  Bunlar, programınız aracılığıyla geçiş sırasında verilerin düşük boyutlu bir gösterimi için harika.  Yapısal eşitlik içerdiğinden, karşılaştırma ile kullanımı kolaydır.

Ayrılmış birleşimlerin birçok kullanımı vardır, ancak temel avantajı, bir verilerin sahip olduğu tüm olası "şekillerin" hesabına yönelik model eşleştirme ile birlikte kullanabiliyor.  

Sınıflar, bilgileri temsil etmeniz gerektiğinde ve ayrıca bu bilgileri işlevlere bağlamak gibi çok sayıda nedenden dolayı harika bir yoldur.  Bir Thumb kuralı olarak, bazı verilere kavramsal olarak bağlı olan işlevselliğe sahip olduğunuzda, sınıfları ve nesne odaklı programlama ilkelerini kullanmak büyük bir avantajdır.  Sınıflar, C# ve Visual Basic birlikte çalışırken tercih edilen veri türüdür ve bu diller neredeyse her şey için sınıflar kullanır.

## <a name="next-steps"></a>Sonraki Adımlar

Artık dilin birincil özelliklerinden bazılarını gördüğünüze göre, ilk F# programlarınızı yazmaya hazır olmanız gerekir!  Geliştirme ortamınızı ayarlamayı ve kod yazmayı öğrenmek [için Başlarken ' e göz](get-started/index.md) atın.

Daha fazla bilgi edinmek için sonraki adımlar istediğiniz gibi olabilir, ancak temel fonksiyonel programlama kavramlarını rahat bir şekilde sağlamak için [' de F# işlevsel programlamaya giriş](./introduction-to-functional-programming/index.md) yapmanız önerilir.  Bu, ortamında güçlü programlar oluşturmak için gereklidir F#.

Ayrıca, ayrıntılı bir kavramsal içerik koleksiyonunu görmek için [ F# dil başvurusunu](./language-reference/index.md) inceleyin F#.
