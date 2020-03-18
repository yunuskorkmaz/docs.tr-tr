---
title: Desen Eşleştirme - C# Kılavuzu
description: "C'deki desen eşleştirme ifadeleri hakkında bilgi edinin #"
ms.date: 04/10/2019
ms.technology: csharp-fundamentals
ms.assetid: 1e575c32-2e2b-4425-9dca-7d118f3ed15b
ms.openlocfilehash: 0c302499543c90bd01427e2791435968d580f644
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170390"
---
# <a name="pattern-matching"></a>Desen Eşleştirme

Desenler, bir değerin belirli bir *şekle*sahip olduğunu ve eşleşen şekle sahip olduğunda değerden bilgi *ayıklayabildiği* kadar sınar. Desen eşleştirme, bugün zaten kullandığınız algoritmalar için daha kısa sözdizimi sağlar. Varolan sözdizimini kullanarak desen eşleştirme algoritmaları zaten oluşturursunuz. Değerleri `if` sınamak için yazınız veya `switch` deyimlersiniz. Daha sonra, bu ifadeler eşleştiğinde, bu değerden bilgileri ayıklar ve kullanırsınız. Yeni sözdizimi öğeleri, zaten aşina olduğunuz deyimlerin `is` `switch`uzantılarıdır: ve . Bu yeni uzantılar bir değeri sınayıp bu bilgileri ayıklamakla birleştirir.

Bu makalede, okunabilir, kısa kod sağlar nasıl göstermek için yeni sözdizimi bakacağız. Desen eşleştirme, verilerin ve bunları manipüle eden yöntemlerin sıkıca birleştiği nesne yönelimli tasarımların aksine, verilerin ve kodun ayrıldığı deyimleri sağlar.

Bu yeni deyimleri göstermek için, desen eşleştirme ifadelerini kullanarak geometrik şekilleri temsil eden yapılarla çalışalım. Büyük olasılıkla sınıf hiyerarşileri oluşturma ve nesnenin çalışma zamanı türüne göre nesne davranışını özelleştirmek için [sanal yöntemler ve geçersiz kılınan yöntemler](methods.md#inherited) oluşturmaya aşinasınızdır.

Bu teknikler, sınıf hiyerarşisinde yapılandırılan veriler için mümkün değildir. Veriler ve yöntemler ayrı olduğunda, başka araçlara ihtiyacınız vardır. Yeni *desen eşleştirme* yapıları, verileri incelemek için daha temiz sözdizimini etkinleştirir ve bu verilerin herhangi bir durumuna göre denetim akışını manipüle eder. Zaten ifadeler `if` yazmak `switch` ve bir değişkenin değerini test. Bir `is` değişkenin türünü sınanan ifadeler yazarsınız. *Desen eşleştirme* bu ifadelere yeni özellikler ekler.

Bu makalede, farklı geometrik şekillerin alanını hesaplayan bir yöntem oluşturacaksınız. Ancak, nesne yönelimli tekniklere başvurmadan ve farklı şekiller için bir sınıf hiyerarşisi oluşturmadan bunu yapacaksınız.
Bunun yerine *desen eşleştirme* kullanırsınız.
Bu örnekten geçerken, bu kodu nesne hiyerarşisi olarak nasıl yapılandırışla karşılaştırın. Sorgulamanız ve işlemeniz gereken veriler bir sınıf hiyerarşisi değilse, desen eşleştirme zarif tasarımlar sağlar.

Soyut şekil tanımıyla başlayıp farklı şekil sınıfları eklemek yerine, geometrik şekillerin her biri için basit veri tanımlarıyla başlayalım:

[!code-csharp[ShapeDefinitions](../../samples/snippets/csharp/PatternMatching/Shapes.cs#01_ShapeDefinitions "Shape definitions")]

Bu yapılardan, bir şeklin alanını hesaplayan bir yöntem yazalım.

## <a name="the-is-type-pattern-expression"></a>Tür `is` deseni ifadesi

C# 7.0'dan önce, her türü bir dizi `if` `is` ve deyimde test etmeniz gerekir:

[!code-csharp[ClassicIsExpression](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#02_ClassicIsExpression "Classic type pattern using is")]

Yukarıdaki kod *tür deseninin*klasik bir ifadesidir : Bir değişkeni türünü belirlemek için sınamak ve bu türe göre farklı bir eylem demlersiniz.

Bu kod, test başarılı olursa `is` bir değişken atamak için ifade uzantıları kullanarak daha basit hale gelir:

[!code-csharp[IsPatternExpression](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#03_IsPatternExpression "is pattern expression")]

Bu güncelleştirilmiş sürümde, `is` ifade hem değişkeni sınar hem de uygun türde yeni bir değişkene atar. Ayrıca, bu sürümü `Rectangle` n . `struct` Yeni `is` ifade, başvuru türlerinin yanı sıra değer türleri ile birlikte çalışır.

Desen eşleştirme ifadeleri için dil kuralları, eşleşme ifadesinin sonuçlarını yanlış kullanmaktan kaçınmanıza yardımcı olur. Yukarıdaki örnekte, değişkenler `s` `c`, `r` ve yalnızca kapsam içindedir ve ilgili desen `true` eşleşmeifadeleri sonuçları olduğunda kesinlikle atanır. Her iki değişkeni de başka bir konumda kullanmaya çalışırsanız, kodunuz derleyici hataları oluşturur.

Kapsamdan başlayarak bu kuralların her ikisini de ayrıntılı olarak inceleyelim. Değişken `c` yalnızca ilk `else` `if` ifadenin dalında kapsamdadır. Değişken `s` yöntemde `ComputeAreaModernIs`kapsam içindedir. Bunun nedeni, bir `if` deyimin her dalı değişkenler için ayrı bir kapsam oluşturmasıdır. Ancak, `if` ifadenin kendisi değil. Bu, `if` deyimde bildirilen değişkenlerin `if` deyimle aynı kapsamda olduğu anlamına gelir (bu durumda yöntem.) Bu davranış desen eşleştirmesine özgü değildir, ancak değişken kapsamlar `if` `else` ve deyimler için tanımlanmış davranıştır.

Değişkenler `c` ve `s` ilgili `if` ifadeler doğru olduğunda, gerçek mekanizma zaman kesinlikle atanan nedeniyle atanır.

> [!TIP]
> Bu konudaki örnekler, bir desen eşleşmesi `is` ifadesinin `true` `if` ifadenin deyiminin dalındaki eşleşme değişkenini kesinlikle atadığı önerilen yapıyı kullanır.
> Söyleyerek `if (!(shape is Square s))` mantığı tersine çevirebilirsiniz `s` ve değişken kesinlikle yalnızca `false` dalda atanır. Bu geçerli C# olsa da, mantığı takip etmek daha kafa karıştırıcı olduğundan önerilmez.

Bu kurallar, bu desen karşılanmadığında yanlışlıkla bir desen eşleşmesi ifadesinin sonucuna erişme olasılığının düşük olduğu anlamına gelir.

## <a name="using-pattern-matching-switch-statements"></a>Desen eşleştirme `switch` ifadelerini kullanma

Zaman geçtikçe, diğer şekil türlerini desteklemeniz gerekebilir. Test ettiğiniz koşulların sayısı arttıkça, `is` desen eşleşen ifadeleri kullanarak hantal hale gelebilir bulacaksınız. Denetlemek istediğiniz her `if` türde deyim ler gerektirmesinin `is` yanı sıra, giriş tek bir türle eşleşip eşleşmediyse ifadeler sınamayla sınırlıdır. Bu durumda, `switch` desen eşleşen ifadeler daha iyi bir seçim olur bulacaksınız.

Geleneksel `switch` ifade bir desen ifadesiydi: sabit deseni destekledi.
Bir değişkeni bir deyimde kullanılan `case` herhangi bir sabitle karşılaştırabilirsiniz:

[!code-csharp[ClassicSwitch](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#04_ClassicSwitch "Classic switch statement")]

`switch` İfade tarafından desteklenen tek desen sabit desen oldu. Daha fazla sayısal türleri ve `string` türü ile sınırlıydı.
Bu kısıtlamalar kaldırıldı ve şimdi tür `switch` deseni kullanarak bir deyim yazabilirsiniz:

[!code-csharp[Switch Type Pattern](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#05_SwitchTypePattern "Compute with `switch` expression")]

Desen eşleştirme `switch` deyimi, geleneksel C stili `switch` deyimini kullanan geliştiriciler için tanıdık sözdizimini kullanır. Her `case` biri değerlendirilir ve giriş değişkeni ile eşleşen koşulun altındaki kod yürütülür. Kod yürütme bir servis talebi ifadesinden diğerine "düşemez"; `case` deyiminin sözdizimi, her `case` bir `break`ucun bir , `return`veya `goto`.

> [!NOTE]
> Başka `goto` bir etikete atlamak için ifadeler yalnızca sabit desen (klasik anahtar deyimi) için geçerlidir.

İfadeyi `switch` yöneten önemli yeni kurallar vardır. İfadedeki değişkenin türüne `switch` ilişkin kısıtlamalar kaldırıldı.
Bu örnekte `object` olduğu gibi herhangi bir tür kullanılabilir. Servis talebi ifadeleri artık sabit değerlerle sınırlı değildir. Bu sınırlamanın kaldırılması, `switch` bölümleri yeniden sıralamanın bir programın davranışını değiştirebileceği anlamına gelir.

Sabit değerlerle sınırlı olduğunda, `case` en fazla bir etiket `switch` ifadenin değeriyle eşleşemez. Bunu, her `switch` bölümün bir sonraki bölüme düşmemesi gerektiği kuralıyla `switch` birleştirin ve bölümleri davranışı etkilemeden herhangi bir sırada yeniden düzenlenebileceğini söyledi.
Şimdi, daha genelifadeler `switch` ile, her bölümün sırası önemlidir. İfadeler `switch` metin sırasına göre değerlendirilir. Yürütme, `switch` ifadeyle `switch` eşleşen ilk etikete aktar.  
Servis `default` talebi yalnızca başka bir servis talebi etiketi eşleşmezse yürütülür. Dava, `default` metin seli ne olursa olsun en son değerlendirilir. Herhangi bir durum `default` yoksa ve diğer `case` ifadelerin hiçbiri eşleşmezse, `switch` açıklamanın ardından yapılan açıklamada yürütme devam eder. Etiketler kodunun `case` hiçbiri yürütülmez.

## <a name="when-clauses-in-case-expressions"></a>`when`ifadelerdeki `case` yan tümceler

`case` Etiketüzerinde bir `when` yan tümce kullanarak 0 alanına sahip bu şekiller için özel durumlar yapabilirsiniz. Yan uzunluğu 0 olan bir kare veya 0 yarıçapı olan bir daire0 alana sahiptir. Bu koşulu `when` `case` etikette bir yan tümce kullanarak belirtirsiniz:  

[!code-csharp[ComputeDegenerateShapes](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#07_ComputeDegenerateShapes "Compute shapes with 0 area")]

Bu değişiklik, yeni sözdizimi hakkında birkaç önemli noktayı gösterir. İlk olarak, birden çok `case` `switch` etiket bir bölüme uygulanabilir. Bu etiketlerden herhangi biri `true`. Bu durumda, `switch` ifade bir daire veya 0 alana sahip bir kare ise, yöntem 0 sabitini döndürür.

Bu örnek, ilk `case` `switch` blok için iki etikette iki farklı değişken tanır. Bu `switch` bloktaki deyimlerin değişkenleri `c` (daire için) veya `s` (kare için) kullanmadığını unutmayın.
Bu değişkenlerden hiçbiri kesinlikle bu `switch` blokta atanır.
Bu durumlardan biri eşleşirse, açıkça değişkenlerden biri atanmıştır.
Ancak, derle zamanında *hangisinin* atandığını söylemek imkansızdır, çünkü her iki durumda da çalışma zamanında eşleşebilir. Bu nedenle, çoğu zaman aynı `case` blok için birden çok etiket kullandığınızda, `case` deyimde yeni bir değişken tanıtamazsınız `when` veya yalnızca yan tümcedeki değişkeni kullanırsınız.

0 alana sahip bu şekilleri ekledikten sonra, birkaç şekil türü daha ekleyelim: bir dikdörtgen ve üçgen:

[!code-csharp[AddRectangleAndTriangle](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#09_AddRectangleAndTriangle "Add rectangle and triangle")]

 Bu değişiklik kümesi, dejenere servis talebi için etiketler, yeni şekillerin her biri için etiketler ve bloklar ekler. `case`

Son olarak, bağımsız `null` değişkenin aşağıdakilerden `null`emin olmak için bir servis talebi ekleyebilirsiniz:

[!code-csharp[NullCase](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#10_NullCase "Add null case")]

`null` Desendeki sabitin `null` bir türü olmadığından, ancak herhangi bir başvuru türüne veya nullable türüne dönüştürülebildiği için desen için özel davranış ilginçtir. Dil, a'yı `null` herhangi bir türe `null` dönüştürmek yerine, değişkenin derleme zamanı türünden bağımsız olarak bir değerin herhangi bir tür deseniyle eşleşmeymeyeceğini tanımlar. Bu davranış, `switch` yeni tabanlı tür `is` deseni `is` deyimle `false` tutarlı hale getirir: `null`denetlenen değer işaretlendiğinde deyimler her zaman geri döner. Aynı zamanda daha basittir: türü kontrol ettiğinizde, ek bir null çekgerekmez. Yukarıdaki örneklerin hiçbir servis talebi bloğunda null denetim olmamasından görebilirsiniz: tür deseni eşleştirmenin null olmayan bir değeri garanti etmesi gerektiğinden, bunlar gerekli değildir.

## <a name="var-declarations-in-case-expressions"></a>`var`ifadelerdeki `case` bildirimler

Eşmaç `var` ifadelerinden biri olarak giriş, desen eşleşmesine yeni kurallar sunar.

İlk kural, bildirimin `var` normal tür çıkarım kurallarını izlemesidir: Tür, anahtar ifadesinin statik türü olarak kabul edilir. Bu kurala göre, tür her zaman eşleşir.

İkinci kural, bir `var` bildirimin diğer tür desen ifadelerinin içerdiği null denetimine sahip olmamasıdır. Bu, değişkenin null olabileceği ve bu durumda null çek gerektiği anlamına gelir.

Bu iki kural, birçok durumda, `var` bir `case` ifadedeki bir bildirimin `default` ifadeyle aynı koşullarla eşleştiğini anlamına gelir.
Varsayılan olmayan herhangi bir servis `default` talebi servis `default` talebi için tercih olduğundan, servis talebi asla yürütülmeyecektir.

> [!NOTE]
> Derleyici, bir `default` servis talebinin yazıldığı durumlarda bir uyarı yapmaz, ancak hiçbir zaman yürütülmez. Bu, olası `switch` tüm durumların listelendiği geçerli deyim davranışıyla tutarlıdır.

Üçüncü kural, bir `var` servis talebinin yararlı olabileceği kullanımları tanır. Girişin bir dize olduğu ve bilinen komut değerlerini aradığınız bir desen eşleşmesi yaptığınızı düşünün. Şöyle bir şey yazabilirsiniz:

[!code-csharp[VarCaseExpression](../../samples/snippets/csharp/PatternMatching/Program.cs#VarCaseExpression "use a var case expression to filter white space")]

`var` Büyük/küçük `null`harf eşleşmeleri, boş dize veya yalnızca beyaz boşluk içeren herhangi bir dize. Önceki kodun `?.` yanlışlıkla bir <xref:System.NullReferenceException>. Servis `default` talebi, bu komut parer tarafından anlaşılmayan diğer dize değerlerini işler.

Bu, bir ifadeden farklı bir `var` durum ifadesini dikkate `default` almak isteyebileceğiniz bir örnektir.

## <a name="conclusions"></a>Sonuçlar

*Desen Eşleştirme yapıları,* devralma hiyerarşisi ile ilişkili olmayan farklı değişkenler ve türler arasındaki denetim akışını kolayca yönetmenize olanak tanır. Ayrıca, değişken üzerinde test ettiğiniz herhangi bir koşulu kullanmak için mantığı da denetleyebilirsiniz. Daha fazla dağıtılmış uygulama oluştururken, verilerin ve bu verileri işleme yöntemlerinin ayrı olduğu daha sık ihtiyaç dizinlere ve deyimlere olanak tanır. Bu örnekte kullanılan şekil yapılarının herhangi bir yöntem içermediğini, yalnızca salt okunur özellikler içerdiğini fark edeceksiniz.
Desen Eşleştirme herhangi bir veri türüyle çalışır. Nesneyi inceleyen ifadeler yazar ve bu koşullara göre denetim akışı kararları verirsiniz.

Bu örnekteki kodu, alanı hesaplamak için kendi sanal yöntem `Shape` uygulamasıyla soyut ve belirli türemiş şekiller için sınıf hiyerarşisi oluşturarak izleyen tasarımla karşılaştırın. Verilerle çalışırken ve veri depolama yla ilgili endişeleri davranış kaygılarından ayırmak istediğinizde desen eşleştirme ifadelerinin çok yararlı bir araç olabileceğini sık sık göreceksiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: Veri türlerini genişletmek için desen eşleştirme özelliklerini kullanma](tutorials/pattern-matching.md)
