---
title: Desen eşleştirme C# Kılavuzu
description: Desen eşleştirme ifadelerinde C# öğrenin
ms.date: 01/24/2017
ms.assetid: 1e575c32-2e2b-4425-9dca-7d118f3ed15b
ms.openlocfilehash: fa327dafe3f924d22b5f0d459eb0b6c7ba60a684
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43255347"
---
# <a name="pattern-matching"></a>Desen Eşleştirme #

Desenler test değeri belirli bir sahip *şekli*ve *ayıklamak* eşleşen şekil sahip olduğunda bu değerden daha fazla bilgi. Desen eşleştirme bugün kullanmakta olduğunuz algoritmaları için daha kısa bir söz dizimi sağlar. Zaten mevcut söz dizimini kullanarak algoritmaları desen de oluşturun. Yazdığınız `if` veya `switch` test değerleri deyimleri. Ardından bu deyimleri eşleştiğinde ayıklayın ve bu değer bilgileri kullanın. Yeni sözdizimi öğeleri, zaten alışık deyimleri uzantılarıdır: `is` ve `switch`. Bu yeni uzantılar bir değer test etme ve bu bilgileri ayıklamak birleştirin.

Bu konu başlığında, okunabilir, kısa kodu nasıl bağlayabileceğinizi göstermek için yeni sözdizimine inceleyeceğiz. Desen eşleştirme deyimleri burada veri ve kod, burada veri ve üzerlerinde değişiklik yöntemleri sıkı şekilde bağlı nesne yönelimli tasarımlarında ayrıldığı sağlar.

Bu yeni deyimleri göstermek için ifadeleri desen kullanarak geometrik şekiller temsil eden yapılar ile çalışalım. Sınıf Hiyerarşiler oluşturma ve oluşturma ile biliyor [sanal ve geçersiz kılınan yöntemleri](methods.md#inherited) nesnenin çalışma zamanı türüne göre nesne davranışını özelleştirebilirsiniz.

Bu tekniklerin bir sınıf hiyerarşisini, yapısal olmayan veriler için mümkün değildir. Verilere ve yöntemlere ayrı diğer araçları gerekir. Yeni *desen eşleştirme* verilerini inceleme ve düzenleme denetim akışı verileri bir koşula göre temizleme söz dizimi yapıları etkinleştirin. Zaten yazma `if` deyimleri ve `switch` bir değişkenin değeri test edin. Yazdığınız `is` bir değişkenin türünü test deyimleri. *Desen eşleştirme* bu deyimleri için yeni özellikleri ekler.

Bu konu başlığında, farklı geometrik şekiller alanını hesaplayan bir yöntem oluşturacaksınız. Ancak, nesne yönelimli teknikleri ile maksimum ve farklı şekilleri için bir sınıf hiyerarşisi oluşturma olmadan gerçekleştirirsiniz.
Kullanacağınız *desen eşleştirme* yerine.
Bu kod ile nasıl, bir nesne hiyerarşisine yapılandırılmış olması, bu örnek giderken, karşılaştırın. Verileri sorgulama ve düzenleme gerekir, bir sınıf hiyerarşisi olmadığı durumlarda, desen eşleştirme çok zarif bir tasarım sağlar.

Bir soyut şekil tanımı ile başlayan ve farklı belirli şekil sınıfları eklemek yerine, bunun yerine basit verilerle yalnızca tanımları her geometrik şekiller başlayalım:

[!code-csharp[ShapeDefinitions](../../samples/csharp/PatternMatching/Shapes.cs#01_ShapeDefinitions "Shape definitions")]

Bu yapıları, bazı şekli alanını hesaplayan bir yöntem yazalım.

## <a name="the-is-type-pattern-expression"></a>`is` Desen ifadesi yazın

C# 7.0 önce bir dizide her tür test gerekecektir `if` ve `is` ifadeleri:

[!code-csharp[ClassicIsExpression](../../samples/csharp/PatternMatching/GeometricUtilities.cs#02_ClassicIsExpression "Classic type pattern using is")]

Yukarıdaki kod, klasik bir ifade olduğunu *türü deseni*: bir değişkenin türünü ve bu türüne göre farklı bir eylem gerçekleştirmesine belirlemek için test ettiğiniz.

Bu kod daha basit hale uzantılarını kullanarak `is` ifade bir değişken ise test atamak için başarılı olur:

[!code-csharp[IsPatternExpression](../../samples/csharp/PatternMatching/GeometricUtilities.cs#03_IsPatternExpression "is pattern expression")]

Bu güncelleştirilmiş sürüm `is` ifade hem değişken test eder ve uygun türde yeni bir değişkene atar. Ayrıca, bu sürüm içeren bildirim `Rectangle` türünü bir `struct`. Yeni `is` ifade, başvuru türleri yanı sıra değer türleri ile çalışır.

Desen eşleştirme ifadeler için dil kuralları bir eşleme ifadesi sonuçlarını kötüye önlemenize yardımcı. Değişkenleri yukarıdaki örnekte `s`, `c`, ve `r` yalnızca kapsamındaki ve ilgili deseni eşleşme ifadeleri olduğunda kesinlikle atanan `true` sonuçları. Başka bir konuma ya da değişken kullanmayı denerseniz, kodunuzu derleyici hataları oluşturur.

Ayrıntılı kapsam ile başlayarak, bu kuralların her ikisi de inceleyelim. Değişken `c` kapsamındaki yalnızca `else` ilk dal `if` deyimi. Değişken `s` yöntemi kapsam içinde `ComputeAreaModernIs`. Çünkü her dal, bir `if` ifade değişkenleri için ayrı bir kapsam oluşturur. Ancak, `if` beyannamesi desteklemez. İçinde bildirilmiş değişkenlerin anlamına `if` deyimi olan aynı kapsamda `if` deyimi (Bu durumda yöntem.) Bu davranışı desen eşleştirme için özel değildir ancak değişken kapsam için tanımlı bir davranıştır ve `if` ve `else` deyimleri.

Değişkenleri `c` ve `s` ne zaman atanmış olan ilgili `if` deyimleri true kesinlikle atanan nedeniyle zaman true mekanizması.

> [!TIP]
> Bu konudaki örnekler önerilen yapısı, bir desen eşleme yerlerde kullanın. `is` ifade kesinlikle atar eşleşme değişkende `true` dalı `if` deyimi.
> Mantığı tarafından bildiren tersine çevirebilir `if (!(shape is Square s))` ve değişken `s` kesinlikle yalnızca atanmış olur `false` dal. Bu geçerli bir C# olsa da, mantıksal izlemek daha karmaşık olduğu için önerilmez.

Bu kurallar, bir desen eşleştirme ifadesi sonucu bu desene karşılanmadığı yanlışlıkla erişim olasılığının düşük olduğu anlamına gelir.

## <a name="using-pattern-matching-switch-statements"></a>Desen eşleştirme kullanarak `switch` deyimleri

Zaman gibi diğer şekil türleri desteklemek gerekebilir. Test koşulları sayısı arttıkça, kullanmanın bulabilirsiniz `is` desen eşleştirme ifadelerinde zahmetli hale gelebilir. Gerektiren ek olarak `if` deyimleri, kontrol etmek istediğiniz her türüne `is` ifadeleri tek bir tür giriş eşleşmesi durumunda test sınırlıdır. Bu durumda, bulabilirsiniz `switch` desen eşleştirme ifadeleri daha iyi bir seçim haline gelir. 

Geleneksel `switch` ifade olan bir desen ifadesi: sabit desen desteklenir.
Kullanılan tüm sabit bir değişkene kıyaslayarak bir `case` deyimi:

[!code-csharp[ClassicSwitch](../../samples/csharp/PatternMatching/GeometricUtilities.cs#04_ClassicSwitch "Classic switch statement")]

Tarafından desteklenen tek desen `switch` ifadesi sabit desen oluştu. Daha fazla sınırlıdır sayısal türleri olan ve `string` türü.
Bu kısıtlamaları kaldırılmış ve artık yazabileceğiniz bir `switch` türü desenini kullanarak deyimi:

[!code-csharp[Switch Type Pattern](../../samples/csharp/PatternMatching/GeometricUtilities.cs#05_SwitchTypePattern "Compute with `switch` expression")]

Desen eşleştirme `switch` deyimi geleneksel C stili kullanan geliştiriciler için tanıdık sözdizimini kullanan `switch` deyimi. Her `case` değerlendirilir ve giriş değişkeni eşleşen koşul altında kod yürütülür. Kod yürütmeyi "bir case ifadesinden sonraki geçemez"; söz dizimi `case` deyimi gerektirir, her `case` sonunda bir `break`, `return`, veya `goto`.

> [!NOTE]
> `goto` Başka bir etikete atlanamaz deyimleri yalnızca sabit desenini (Klasik switch deyimi) geçerlidir.

Düzenleyen önemli yeni kurallar `switch` deyimi. Değişken türünü kısıtlamalar `switch` ifadesi kaldırıldı.
Gibi herhangi türdeki `object` Bu örnekte, kullanılabilir. Case ifadesi, artık sabit değerleri için sınırlı değildir. Bu sınırlama kaldırma anlamına gelir, yeniden sıralama `switch` bölümler, programın davranışını değişebilir.

Birden fazla sabit değerleri için sınırlı olduğunda `case` etiketle değerinin eşleşen `switch` ifade. Bu kuralla birleştirme, her `switch` bölüm gerekir değil sonraki bölüme dönüş yapmasına ve onu izleyen `switch` bölümleri düzenlenmeyecek herhangi bir sırada davranışını etkilemeden.
Artık, daha fazla genelleştirilmiş ile `switch` ifadeleri, her bölümün sırası önemlidir. `switch` İfadeleri, metinsel sırayla değerlendirilir. Yürütme için ilk aktarır `switch` eşleşen etiket `switch` ifade.  
Unutmayın `default` çalışması, yalnızca diğer bir durum etiketi eşleşen yürütülür. `default` Çalışması bağımsız olarak metinsel sırası son olarak değerlendirilir. Yoksa hiçbir `default` çalışması ve diğer hiçbiri `case` ifadeleri eşleşen, yürütme devam deyimi aşağıdaki `switch` deyimi. Hiçbiri `case` etiketleri kod yürütülür.

## <a name="when-clauses-in-case-expressions"></a>`when` yan tümcelerinde `case` ifadeleri

0 alanı kullanarak bu şekilleri için özel durumlar yapabileceğiniz bir `when` yan tümcesi `case` etiketi. Bir kare yan uzunluğu 0 ile veya bir daire ile bir RADIUS 0 0 alanı vardır. Bu koşul kullanarak belirttiğiniz bir `when` yan tümcesi `case` etiketi:  

[!code-csharp[ComputeDegenerateShapes](../../samples/csharp/PatternMatching/GeometricUtilities.cs#07_ComputeDegenerateShapes "Compute shapes with 0 area")]

Bu değişiklik birkaç önemli noktaları hakkında yeni söz dizimini gösterir. İlk olarak, birden çok `case` etiketleri için uygulanabilir `switch` bölümü. Deyim bloğu yürütülür etiketlerin hiçbirini olduğunda `true`. Bu örnekte, `switch` ifade bir daire ya da bir kare 0 alanı, 0 sabiti yöntemi döndürür.

Bu örnek iki iki farklı değişken tanıtır `case` ilk etiket `switch` blok. Dikkat Bu tablolarda `switch` bloğu ya da değişkenleri kullanmayın `c` (daire için) veya `s` (için kare).
Bu değişkenleri hiçbiri kesinlikle bu atanan `switch` blok.
Bu durumların herhangi birini eşleşirse, açıkça bir değişken atandı.
Söyleyin mümkün değildir ancak *hangi* her iki durumda da, çalışma zamanında eşleşen derleme zamanında, atanmıştır. Bu nedenle, çoğu kez kullandığınızda, birden çok `case` etiketleri aynı blok için yeni bir değişkende neden olmaz `case` deyimi veya yalnızca kullanacağı değişkeninde `when` yan tümcesi.

0 alanı bu şekillerle eklediğiniz birkaç daha fazla şekil türleri ekleyelim: bir üçgen ve bir dikdörtgen:

[!code-csharp[AddRectangleAndTriangle](../../samples/csharp/PatternMatching/GeometricUtilities.cs#09_AddRectangleAndTriangle "Add rectangle and triangle")]

 Bu değişiklik kümesini ekler `case` bozuk durum etiketlerini ve etiketleri ve her yeni şekiller engeller. 

Son olarak, ekleyebileceğiniz bir `null` bağımsız değişken değil emin olmak için durum `null`:

[!code-csharp[NullCase](../../samples/csharp/PatternMatching/GeometricUtilities.cs#10_NullCase "Add null case")]

İçin özel bir davranış `null` desendir ilginç çünkü sabiti `null` desende bir tür yoksa ancak herhangi bir başvuru türüyle veya Null olabilen bir türle dönüştürülebilir. Yerine dönüştürme bir `null` dil herhangi bir türü tanımlayan bir `null` değer değişkenin derleme zamanı türünden bağımsız olarak herhangi bir türü desen eşleşmez. Bu davranış yeni yapar `switch` desenine türü ile tutarlı `is` deyimi: `is` return deyimleri her zaman `false` denetlenen değer olduğunda `null`. Ayrıca basittir: türü denetledikten sonra ek bir null denetimi gerekmez. Hiçbir null bulunmasına durum blokları yukarıdaki örnekleri hiçbirinde denetler görebilirsiniz: boş olmayan bir değer türü desen eşleştirme garanti olduğundan gerekli değildir.

## <a name="var-declarations-in-case-expressions"></a>`var` bildirimlerinde `case` ifadeleri

Giriş `var` desen eşleşmesi için eşleşmesi ifadelerden biri tanıtan yeni kurallar.

İlk kuralı olan `var` bildirimi izleyen normal türü çıkarım kuralları: türü anahtar ifadenin statik türü olarak algılanır. Bu kuraldan türü her zaman eşleşir.

İkinci kuralı olan bir `var` bildirimi, diğer tür deseni ifadeler içeren null denetimi sahip değil. Bu değişkeni boş olabilir ve bu durumda null denetimi gereklidir anlamına gelir.

Çoğu durumda, bu iki kural anlamına bir `var` bildiriminde bir `case` ifadeyle eşleşen aynı koşullarda bir `default` ifade.
Herhangi bir varsayılan olmayan çalışması için tercih edilen olduğundan `default` durumda `default` durumu hiçbir zaman yürütülecek.

> [!NOTE]
> Derleyici, bu durumda bir uyarı vermez burada bir `default` çalışması yazıldı, ancak hiçbir zaman yürütülür. Bu tutarlıdır geçerli `switch` deyimi davranışı nerede tüm olası durumların listeleniyor.

Üçüncü kuralı kullanan tanıtır burada bir `var` çalışması yararlı olabilir. Burada Giriş bir dizedir ve, bilinen komut değerler için arama deseni eşleştirmesini yaptığınızı hayal edin. Benzer bir şey yazabiliriz:

[!code-csharp[VarCaseExpression](../../samples/csharp/PatternMatching/Program.cs#VarCaseExpression "use a var case expression to filter white space")]

`var` Eşleşen servis talebi `null`, boş bir dize veya yalnızca boşluk içeren herhangi bir dize. Önceki kod bildirim `?.` işleci, yanlışlıkla oluşturmaz emin olmak için bir <xref:System.NullReferenceException>. `default` Durumu işler bu komut ayrıştırıcı tarafından anlaşılmayan herhangi bir dize değeri.

Bu bir yere göz önünde bulundurun isteyebilirsiniz örnektir bir `var` case farklı ifade bir `default` ifade.

## <a name="conclusions"></a>Sonuçları

*Eşleşen yapıları desen* denetim akışı farklı değişkenler ve devralma hiyerarşisi tarafından ilgili olmayan türler arasında kolayca yönetmenize olanak sağlar. Değişkenin üzerine her türlü koşul test kullanılacak mantıksal de denetleyebilirsiniz. Ancak, desenler ve deyimler veri ve bu verileri işleyen yöntemler ayrı olduğu daha dağıtılmış uygulamalar oluşturmak daha sık ihtiyaç duyacağınız etkinleştirir. Bu örnekte kullanılan şekli yapılar herhangi bir yöntem içermediğini fark edeceksiniz yalnızca salt okunur özellikler.
Herhangi bir veri türü ile Works desen. Nesne İnceleme ifadeler yazabilirsiniz ve bu koşullara göre denetim akışı kararlar.

Bu örnek için bir soyut bir sınıf hiyerarşisi oluşturmaktan izlenir tasarımı ile koddan karşılaştırma `Shape` ve türetilen özel şekiller her alanı hesaplamak için sanal bir yöntem, kendi uygulama. Genellikle, verilerle çalışma ve veri depolama endişelere yer bırakmadan davranışı endişelere yer bırakmadan ayırmak istediğiniz desen eşleştirme ifadeleri çok kullanışlı bir aracı olabilir bulabilirsiniz.

