---
title: 'F # turu'
description: "F # kod örnekleriyle birlikte bu tur dilde programlama önemli özelliklerinden bazıları inceleyin."
keywords: "Visual f #, f # işlevsel programlama, .NET, turu"
author: cartermp
ms.author: phcart
ms.date: 02/28/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 49775139-082e-442f-b5a2-dd402399b5d2
ms.openlocfilehash: 7327573a25aa62af28570b4a8662235f3e41a972
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="tour-of-f"></a>F # turu #

F # hakkında bilgi edinmek için en iyi okuma ve yazma F # kodu yoludur.  Bu makalede, F # dili önemli özelliklerinden bazıları aracılığıyla bir tur görevi görür ve makinenizde yürütebilir bazı kod parçacıkları verin.  Bir geliştirme ortamını ayarlama bilgi edinmek için kullanıma [Başlarken](tutorials/getting-started/index.md).

İki birincil kavram vardır F #'ta: İşlevler ve türleri.  Bu tur, bu iki kavrama kalan dil özellikleri vurgulamak.

## <a name="functions-and-modules"></a>İşlevler ve modülleri

En temel herhangi bir F # programı parçalarıdır ***işlevleri*** halinde düzenlenmiştir ***modülleri***.  [İşlevler](language-reference/functions/index.md) çıkışları üretmek girişleri çalışma gerçekleştirme ve altında düzenlenmiştir [modülleri](language-reference/modules.md), F # şeyler grubunda birincil yol olduğu.  Kullanılarak tanımlanır [ `let` bağlama](language-reference/functions/let-bindings.md), işlevin bir ad verin ve bağımsız değişkenleri tanımlayın.

[!code-fsharp[BasicFunctions](../../samples/snippets/fsharp/tour.fs#L101-L133)]

`let` bağlamaları de bir değer bir değişkende diğer diller için benzer bir ad için bağ nasıl değil.  `let` bağlamaları değil ***değişmez*** yerinde anlamına gelen bir değer veya işlevi için bir ad bağlandıktan sonra değiştirilemez, varsayılan olarak,.  Değişkenleri olan diğer dillerde aksine budur ***değişebilir***, değerlerine anlamı değiştirilebilir herhangi bir noktada süre.  Değişebilir bir bağlama gerektiriyorsa, kullanabileceğiniz `let mutable ...` sözdizimi.

[!code-fsharp[Immutability](../../samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a>Sayı, Boole değerlerini ve dizeler

F # aynı temel bir .NET dili olarak destekler [ilkel türler](language-reference/primitive-types.md) .NET içinde yok.

İşte nasıl çeşitli sayısal türler F #'de gösterilir:

[!code-fsharp[Numbers](../../samples/snippets/fsharp/tour.fs#L49-L68)]

Boole değerleri işte ve temel koşullu mantık gerçekleştirme gibi görünür:

[!code-fsharp[Bools](../../samples/snippets/fsharp/tour.fs#L142-L152)]

Ve hangi basic işte [dize](language-reference/strings.md) işleme gibi görünür:

[!code-fsharp[Strings](../../samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a>Demetler

[Diziler](language-reference/tuples.md) bir sorun teşkil F # şunlardır.  Kendilerini değerleri olarak kabul adlandırılmamış ancak sıralı değerler, gruplandırması oldukları.  Bunları, diğer değerleri toplanır değerleri olarak düşünün.  Bunlar kolayca birden fazla değer döndüren bir işleve veya bazı geçici kolaylık sağlaması için değerleri gruplandırma gibi birçok kullanımı vardır.

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L186-L203)]

F # 4.1 itibariyle, ayrıca oluşturabileceğiniz `struct` diziler.  Bu ayrıca tam olarak aynı zamanda C# 7/Visual Basic 15 başlıkları ile çalışmanız `struct` tanımlama grupları:

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L205-L218)]

Çünkü dikkate almak önemlidir `struct` diziler değer türleri, bir tanımlama grubu başvurmak için örtük olarak dönüştürülemiyor veya tam tersi.  Bir başvuru ve yapı tanımlama grubu arasında açıkça dönüştürmeniz gerekir.

## <a name="pipelines-and-composition"></a>Ardışık Düzen ve oluşturma

Yöneltme işleçleri (`|>`, `<|`, `||>`, `<||`, `|||>`, `<|||`) ve birleşim işleçleri (`>>` ve `<<`) F # verileri işlerken, yaygın olarak kullanılır.  Bu işleçlere esnek bir şekilde işlevlerin "ardışık" kurmanızı sağlayan işlevlerdir.  Aşağıdaki örnekte basit bir işlev ardışık düzen oluşturmak için bu işleçlere avantajlarından nasıl ele geçirebilir aracılığıyla anlatılmaktadır.

[!code-fsharp[Pipelines](../../samples/snippets/fsharp/tour.fs#L227-L300)]

Yukarıdaki örnek yapılan F #'ın listesi işleme İşlevler, birinci sınıf işlevleri dahil olmak üzere, birçok özellik kullanımını ve [kısmi uygulama](language-reference/functions/index.md#partial-application-of-arguments).  Bu kavramları her derin bir anlayış Gelişmiş biraz hale karşın, bu işlevler ardışık düzen oluştururken verileri işlemek için ne kadar kolay kullanılabilir açık olmalıdır.

## <a name="lists-arrays-and-sequences"></a>Listeleri, dizileri ve dizileri

Listeleri, dizileri ve dizileri üç birincil koleksiyonu F # core Kitaplığı'nda türleridir.

[Listeler](language-reference/lists.md) sıralı, değişmez aynı türde öğelerinin koleksiyonlarıdır.  Bunlar ayrı olarak bağlı, yani büyük varsa bunlar numaralandırması ancak rasgele erişim ve birleştirme için kötü bir seçim yöneliktir listeleridir.  Bu genellikle ayrı olarak bağlı bir liste listeleri temsil etmek için kullanmayın diğer popüler dilde listelerinde aksine.

[!code-fsharp[Lists](../../samples/snippets/fsharp/tour.fs#L309-L359)]

[Diziler](language-reference/arrays.md) sabit boyutlu, olan *değişebilir* aynı türdeki öğeleri koleksiyonu.  Bunlar öğelerinin hızlı rastgele erişimini desteklemek ve yalnızca bitişik bellek bloklarını olduklarından F # listeler daha hızlıdır.

[!code-fsharp[Arrays](../../samples/snippets/fsharp/tour.fs#L368-L407)]

[Dizileri](language-reference/sequences.md) öğeleri, aynı türdeki tüm mantıksal bir dizi.  Bunlar, listeler ve Diziler, öğeleri mantıksal bir dizi halinde, "Görünüm" yeterli'den daha genel bir tür olan.  Bunlar olabilir çünkü bunlar da göze ***yavaş***, yalnızca ihtiyaç duyulduğunda öğeleri hesaplanabilir anlamına gelir.

[!code-fsharp[Sequences](../../samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a>Özyinelemeli İşlevler

Koleksiyonları veya öğelerin sıralarının işleme genellikle yapılır ile [özyineleme](language-reference/functions/index.md#recursive-functions) F #.  F # döngüler ve kesinlik temelli programlama desteği olsa da, özyineleme doğruluğu garanti etmek daha kolay bulup tercih edilir.

>[!NOTE]
Aşağıdaki örnek deseni ile eşleşen birini kullanır `match` ifade.  Bu temel yapıyı bu makalenin sonraki bölümlerinde ele alınmaktadır.

[!code-fsharp[RecursiveFunctions](../../samples/snippets/fsharp/tour.fs#L461-L500)]

F # de Tail çağrısı iyileştirmesi için tam destek, yalnızca bir döngü yapısı kadar hızlı; böylece özyinelemeli çağrılara en iyi duruma getirmek için bir yol yoktur.

## <a name="record-and-discriminated-union-types"></a>Kayıt ve ayrılmış birleşim türleri

Kayıt ve birleşim türlerini F # kodunda kullanılan iki temel veri türleri ve genellikle bir F # programında verileri temsil etmek için en iyi yoludur.  Bu sınıflar benzer diğer dillerde sağlar ancak birincil farklılıkları yapısal eşitlik semantiklerine sahip biridir.  Bunun anlamı, "yerel" karşılaştırılabilir ve eşitlik basittir - yalnızca bir diğerine eşit olup olmadığını denetleyin.

[Kayıtları](language-reference/records.md) toplama (örneğin, yöntemler) isteğe bağlı üyeleriyle adlandırılmış değerleri şunlardır.  C# veya Java ile sahibiyseniz, ardından bu yapısal eşitlik olduğu ve seremoni daha az POCOs veya Pojo'lar - benzer geliyor olmalıdır.

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L507-L559)]

F # 4.1 itibariyle, kayıt olarak da gösterebilir `struct`s.  Bu gerçekleştirilir `[<Struct>]` özniteliği:

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L561-L568)]

[Birleşimler (DUs)](language-reference/discriminated-unions.md) adlandırılmış forms veya durumları sayısı olabilen değerlerdir.  Bulunan tür depolanan verileri birkaç farklı değerlerden biri olabilir.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L575-L631)]

DUs olarak da kullanabilirsiniz *tek durum ayrılmış birleşimler*, ilkel türler modelleme etki alanı ile yardımcı olacak.  Çoğu zaman, dizeleri ve başka ilkel türler bir şeyi temsil etmek için kullanılır ve böylece özel bir anlamı verilir.  Ancak, verileri yalnızca ilkel gösterimini kullanarak yanlışlıkla yanlış bir değer atama içinde sonuçlanabilir!  Her ayrı tek çalışması UNION olarak bilgi türünü temsil eden Bu senaryoda doğruluk uygulayabilir.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L633-L654)]

Temel alınan değeri bir tek durumda ayrılmış birleşim içinde almak için yukarıdaki örnek gösterdiği gibi açıkça unwrap gerekir.

Ayrıca, DUs da özyinelemeli tanımları kolayca ağaçları ve kendiliğinden özyinelemeli verilerini temsil eden olanak tanıyan destekler.  Örneğin, işte içeren bir ikili arama ağacı nasıl gösterebilir `exists` ve `insert` işlevleri.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L656-L683)]

DUs veri türü ağacında özyinelemeli yapısını temsil eden izin olduğundan, bu yinelemeli yapısına işletim basittir ve doğruluğu garanti eder.  Ayrıca desen eşleştirme aşağıda gösterildiği gibi desteklenmiyor.

Ayrıca, DUs olarak gösterebilir `struct`s `[<Struct>]` özniteliği:

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L685-L696)]

Ancak, bunu yaparken göz önünde bulundurmanız gereken iki önemli şey vardır:

1. Yapı DU yinelemeli olarak tanımlanan olamaz.
2. Yapı DU her kendi örneklerinin benzersiz adlara sahip olmalıdır.

Yukarıdaki takip edilmemesi bir derleme hataya neden olur.

## <a name="pattern-matching"></a>Desen Eşleştirme

[Desen eşleştirme](language-reference/pattern-matching.md) F # türleri üzerinde işletim doğruluk sağlayan F # dili özelliğidir.  Yukarıdaki örneklerde, büyük olasılıkla oldukça biraz fark `match x with ...` sözdizimi.  Bu yapı, veri türleri, tüm olası durumları ne bilinen aracılığıyla bir veri türü kapsamlı bir desen eşleştirme kullanırken dikkate almak için zorlamak için "Şekil" anlayabileceği derleyici sağlar.  Bu doğruluk için son derece güçlüdür ve "ne normalde bir çalışma zamanı sorun derleme zamanı içine olacağını yükseltmek için" zekice kullanılabilir.

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L705-L739)]

Toplu de kullanabilirsiniz `function` oluşturan işlevler kullanımını yazarken, yararlı olan desen eşleştirme için yapı [kısmi uygulama](language-reference/functions/index.md#partial-application-of-arguments):

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L741-L759)]

Bir şey fark kullanımıdır `_` düzeni.  Bu olarak bilinir [joker karakter deseni](language-reference/pattern-matching.md#wildcard-pattern), "I olmayan önemli bir şey nedir" ifadesini içeren bir yolu değil.  Güvenli olmasına karşın, kapsamlı desen eşleştirme yanlışlıkla atlamak ve artık yararlı derleme zamanı enforcements kullanarak dikkatli yoksa `_`.  Ayrıştırılmış türü belirli parçalarını hakkında önemli değil, en iyi kullanıldığında ifade ile eşleşen bir deseni tüm anlamlı durumlarda numaralandırıldığı zaman eşleştirme veya son yan tümcesi olduğunda desen.

[Etkin desenler](language-reference/active-patterns.md) desen eşleştirme ile kullanmak için başka bir güçlü yapı şunlardır.  Desen eşleştirme çağrısı sitede ayırma özel formları içine giriş verisi bölüm olanak sağlar.  Bunlar ayrıca, böylece bölüm bir işlevi olarak tanımlamanızı sağlar parametreli olabilir.  Etkin desenler desteklemek için önceki örnekte genişletme şuna benzer:

[!code-fsharp[ActivePatterns](../../samples/snippets/fsharp/tour.fs#L761-L783)]

## <a name="optional-types"></a>İsteğe bağlı türleri

Ayrılmış birleşim türlerinin bir özel durum seçenek türü, F # core kitaplık parçası olan şekilde yararlıdır.

[Seçenek türü](language-reference/options.md) iki durumda birini temsil eden bir tür: bir değer veya hiç bir şey.  Burada bir değer olabilir veya belirli bir işlemi sağlamayabilir herhangi bir senaryoda kullanılır.  Bu daha sonra bir çalışma zamanı sorun yerine bir derleme zamanı sorun kolaylaştırarak her iki durumda için hesap için zorlar.  Bunlar genellikle API'leri kullanılan nerede `null` böylece hakkında endişelenmeye gerek gereksinimini kullanılan bunun yerine, "hiçbir şey" temsil etmek için `NullReferenceException` birçok durumda.

[!code-fsharp[Options](../../samples/snippets/fsharp/tour.fs#L791-L811)]

## <a name="units-of-measure"></a>Ölçü Birimleri

Bir benzersiz F #'ın tür sistemi ölçü aracılığıyla sayısal değişmez değerleri için içerik sağlama yeteneği özelliğidir.

[Ölçü birimleri](language-reference/units-of-measure.md) ölçümler gibi bir birim için sayısal bir tür ilişkilendirmenizi izin ve sahip işlevleri gerçekleştirmek iş sayısal değişmez değerler yerine birimleri.  Bu, geçirilen sayısal değişmez değerleri türlerini anlamlı bir bağlamında, böylece çalışma zamanı hataları ortadan kaldırılır, bu tür iş ile ilişkili doğrulamak derleyici sağlar.

[!code-fsharp[UnitsOfMeasure](../../samples/snippets/fsharp/tour.fs#L818-L839)]

F # Core kitaplık birçok SI birim türleri ve birim dönüştürmeleri tanımlar.  Daha fazla bilgi için kullanıma [Microsoft.FSharp.Data.unitsystems.sı Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d).

## <a name="classes-and-interfaces"></a>Sınıflar ve arabirimler

F # de sahip .NET sınıfları için tam destek [arabirimleri](language-reference/interfaces.md), [soyut sınıflar](language-reference/abstract-classes.md), [devralma](language-reference/inheritance.md)ve benzeri.

[Sınıfları](language-reference/classes.md) .NET nesneleri temsil türleri hangi özellikleri, yöntemleri ve olayları olarak sahip kendi [üyeleri](language-reference/members/index.md).

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L848-L877)]

Genel sınıfları tanımlama ayrıca çok basittir.

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L884-L905)]

Bir arabirim için ya da kullanabilirsiniz `interface ... with` sözdizimi veya bir [nesne ifadesi](language-reference/object-expressions.md).

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L912-L931)]

## <a name="which-types-to-use"></a>Hangi tür kullanımı

Sınıfları, kayıtları, ayrılmış birleşimler ve diziler varlığını önemli bir soruya müşteri adayları: hangi kullanmalısınız?  Çoğu her şeyi gibi hayatta, yanıt koşullarınıza üzerinde bağlıdır.

Diziler birden fazla değer döndüren bir işlevden ve bir geçici toplama değerlerin bir değer olarak kullanmak için mükemmeldir.

Bir "adımından yukarı" etiketleri ve isteğe bağlı bir üye için destek adlı bir tanımlama grubu kayıtlarıdır.  Bunlar, bir veri aktarım sırasında program aracılığıyla düşük seremoni gösterimini için mükemmeldir.  Yapısal eşitlik sahip oldukları için karşılaştırma kullanımı kolaydır.

Ayrılmış birleşimler birçok kullanır sahip ancak bunları "veri sahip olabileceği tüm olası şekiller için" hesap için desen eşleştirme birlikte kullanan yapabilmek için çekirdek avantaj olmalıdır.  

Sınıfları, bilgileri temsil eder ve ayrıca bu bilgileri işlevine tie gerektiğinde gibi nedeniyle, büyük sayıda için mükemmeldir.  Bazı verileri, kavramsal olarak bağlı işlevselliği olduğunda altın kural, sınıflar ve ilkeler Object-Oriented programlama büyük fayda kullanmaktır.  Bu diller için neredeyse her şeyi sınıfları kullandıkça da tercih edilen veri türü C# ve Visual Basic ile birlikte çalışırken sınıflarıdır.

## <a name="next-steps"></a>Sonraki Adımlar

Bazı dil birincil özellikleri gördüğünüze göre ilk, F # programları yazmak hazır olmalıdır!  Kullanıma [Başlarken](tutorials/getting-started/index.md) geliştirme ortamınızı ayarlama ve bazı kodlar yazmak öğrenin.

Daha fazla bilgi almak için sonraki adımlar, ister olabilir, ancak öneririz [ilk sınıf değerleri olarak işlevler](introduction-to-functional-programming/functions-as-first-class-values.md) <!--[Introduction to Functional Programming in F#](introduction-to-functional-programming/index.md)--> işlevsel programlama kavramları ile rahat almak için.  Bunlar, F # sağlam programlar oluşturulmasında gerekli olacaktır.

Ayrıca, kullanıma [F # dili başvurusu](language-reference/index.md) kavramsal içeriğin geniş kapsamlı bir koleksiyon F # görmek için.
