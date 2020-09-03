---
title: Model eşleştirme-C# Kılavuzu
description: "C 'de desenler eşleştirme ifadeleri hakkında bilgi edinin #"
ms.date: 04/10/2019
ms.technology: csharp-fundamentals
ms.assetid: 1e575c32-2e2b-4425-9dca-7d118f3ed15b
ms.openlocfilehash: 2dd1401e3ef22a02f327e44ff884182ee3e22278
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89415000"
---
# <a name="pattern-matching"></a>Desen Eşleştirme

Desenler bir değerin belirli bir *şekle*sahip olduğunu ve eşleşen şekline sahip olduğu zaman değerden bilgi *ayıklayabilirler* . Model eşleştirme, günümüzde zaten kullandığınız algoritmalar için daha kısa sözdizimi sağlar. Mevcut söz dizimini kullanarak model eşleştirme algoritmaları zaten oluşturmuş olursunuz. `if` `switch` Değerleri test eden bir yazın. Daha sonra, bu deyimler eşleşiyorsa, bu değerden bilgi ayıklar ve bunları kullanabilirsiniz. Yeni sözdizimi öğeleri, zaten bildiğiniz deyimlere yönelik uzantılardır: `is` ve `switch` . Bu yeni uzantılar bir değeri test eden ve bu bilgileri ayıklayarak birleştirir.

Bu makalede, nasıl okunabilir, kısa kod etkinleştirmesinin nasıl yapıldığını gösteren yeni sözdizimine bakacağız. Desen eşleştirme, verilerin ve kodun ayrıldığı ve verilerin ve bunları işleyen yöntemlerin sıkı bir şekilde birbirine bağlı olduğu nesne odaklı tasarımlardan farklı olarak, verilerin ve kodun ayrıldığı deyimler sunar.

Bu yeni deyimleri göstermek için, model eşleştirme deyimlerini kullanarak geometrik şekilleri temsil eden yapılarla çalışmaalım. Nesnenin çalışma zamanı türüne göre nesne davranışını özelleştirmek için sınıf hiyerarşileri oluşturma ve [sanal yöntemleri oluşturma ve geçersiz kılınan Yöntemler](methods.md#inherited) hakkında bilgi sahibisiniz.

Bu teknikler, bir sınıf hiyerarşisinde yapılandırılmamış veriler için mümkün değildir. Veriler ve Yöntemler ayrı olduğunda, diğer araçlara ihtiyacınız vardır. Yeni *model eşleştirme* yapıları, verileri incelemek ve bu verilerin herhangi bir koşuluna göre denetim akışını işlemek için temizleyici sözdizimini etkinleştirir. Zaten `if` `switch` bir değişkenin değerini test eden deyimleri yazarsınız. `is`Bir değişkenin türünü test eden deyimler yazarsınız. *Model eşleştirme* , bu deyimlere yeni yetenekler ekler.

Bu makalede, farklı geometrik şekillerin alanını hesaplayan bir yöntem oluşturacaksınız. Ancak, nesne yönelimli teknikler için bir daha olmadan ve farklı şekiller için bir sınıf hiyerarşisi oluşturmadan bunu yapabilirsiniz.
Bunun yerine *model eşleştirmeyi* kullanacaksınız.
Bu örneğe giderek, bu kodun bir nesne hiyerarşisi olarak nasıl yapılandırıldığı ile karşıtlığı vardır. Sorgu ve işleme gereken veriler bir sınıf hiyerarşisi olmadığında, desen eşleştirme zarif tasarımları mümkün değildir.

Bir soyut şekil tanımıyla başlamak ve farklı özel şekil sınıfları eklemek yerine, yalnızca geometrik şekillerin her biri için yalnızca basit veri tanımlarıyla başlayalım.

[!code-csharp[ShapeDefinitions](../../samples/snippets/csharp/PatternMatching/Shapes.cs#01_ShapeDefinitions "Shape definitions")]

Bu yapılardan, bazı şekillerin alanını hesaplayan bir yöntem yazalım.

## <a name="the-is-type-pattern-expression"></a>`is`Tür deseninin ifadesi

C# 7,0 ' den önce, her türü bir dizi `if` ve deyimde test etmeniz gerekir `is` :

[!code-csharp[ClassicIsExpression](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#02_ClassicIsExpression "Classic type pattern using is")]

Yukarıdaki kod, *tür deseninin*klasik bir ifadesidir: türünü tespit etmek ve bu türe göre farklı bir eylem almak için bir değişkeni test etiyorsunuz.

Bu kod `is` , test başarılı olursa bir değişken atamak için ifade uzantıları kullanılarak daha basit hale gelir:

[!code-csharp[IsPatternExpression](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#03_IsPatternExpression "is pattern expression")]

Bu güncelleştirilmiş sürümde, `is` ifadenin her ikisi de değişkeni sınar ve uygun türdeki yeni bir değişkene atar. Ayrıca, bu sürümün bir olan türünü de içerdiğine dikkat edin `Rectangle` `struct` . Yeni `is` ifade, değer türleri ve başvuru türleri ile birlikte kullanılabilir.

Bir eşleştirme ifadesinin sonuçlarının yanlış kullanılmasını önlemenize yardımcı olacak şekilde, model eşleştirme ifadelerine yönelik dil kuralları. Yukarıdaki örnekte,, `s` `c` ve değişkenleri `r` yalnızca kapsamdadır ve ilgili model eşleşme ifadeleri sonuçlara sahip olduğunda kesinlikle atanır `true` . Başka bir konumda herhangi bir değişken kullanmayı denerseniz, kodunuz derleyici hataları oluşturur.

Bu kuralların her ikisini de kapsam ile başlayarak ayrıntılı bir şekilde incelim. Değişken `c` yalnızca `else` ilk deyimin dalında kapsamdadır `if` . Değişkeni `s` yönteminde kapsam içinde `ComputeAreaModernIs` . Çünkü bir deyimin her dalı `if` değişkenler için ayrı bir kapsam oluşturur. Ancak, `if` deyimin kendisi değildir. Bu, bildiriminde belirtilen değişkenlerin `if` `if` deyimlerle aynı kapsamda (Bu durumda yöntem) olduğu anlamına gelir. Bu davranış, model eşleştirmeye özgü değildir, ancak değişken kapsamları ve deyimleri için tanımlanan davranıştır `if` `else` .

Değişkenler `c` ve `s` ilgili deyimler true olduğunda, kesin olarak `if` atanan doğru mekanizmaya göre atanır.

> [!TIP]
> Bu konudaki örneklerde, bir model eşleştirme `is` ifadesinin `true` deyimin dalındaki Match değişkenini kesinlikle atayan önerilen yapı kullanılır `if` .
> Mantığa göre ters çevirebilirsiniz `if (!(shape is Square s))` ve değişken `s` yalnızca dalda kesinlikle atanır `false` . Bu geçerli bir C# olsa da, mantığın izlenmesi daha kafa karıştırıcı olduğundan önerilmez.

Bu kurallar, bu düzenin karşılanmadığı zaman bir model eşleştirme ifadesinin sonucuna yanlışlıkla erişmeniz çok düşüktür.

## <a name="using-pattern-matching-switch-statements"></a>Model eşleştirme `switch` deyimlerini kullanma

Aynı zamanda, diğer şekil türlerini desteklemeniz gerekebilir. Test ettiğiniz koşulların sayısı arttıkça, `is` model eşleştirme ifadelerinin kullanımı için bir tamsayı gelebileceğinizi göreceksiniz. Denetlemek istediğiniz her türde deyim gerektirmesinin yanı sıra `if` , `is` giriş tek bir türle eşleşiyorsa, ifadeler test ile sınırlıdır. Bu durumda, `switch` düzenin eşleşen ifadelerin daha iyi bir seçenek haline geldiğini göreceksiniz.

Geleneksel `switch` deyim bir desenli ifade idi: sabit örüntü destekleniyor.
Bir değişkeni bir ifadede kullanılan herhangi bir sabitle karşılaştırabilirsiniz `case` :

[!code-csharp[ClassicSwitch](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#04_ClassicSwitch "Classic switch statement")]

Deyimin desteklediği tek desenler sabit bir `switch` modeldir. Sayısal türlerle ve türle daha fazla sınırlandırıldı `string` .
Bu kısıtlamalar kaldırılmıştır ve artık `switch` tür modelini kullanarak bir ifade yazabilirsiniz:

[!code-csharp[Switch Type Pattern](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#05_SwitchTypePattern "Compute with `switch` expression")]

Model eşleştirme `switch` deyimleri, geleneksel C stili ifadesini kullanan geliştiriciler için tanıdık sözdizimini kullanır `switch` . Her biri `case` değerlendirilir ve giriş değişkeniyle eşleşen koşulun altındaki kod yürütülür. Kod yürütme, bir Case ifadesinden sonrakine "düşmüyor". `case` deyimin sözdizimi her `case` bir uçta `break` , veya ile gerektirir `return` `goto` .

> [!NOTE]
> `goto`Başka bir etikete atlanacak deyimler yalnızca sabit model için geçerlidir (klasik switch deyimi).

Bildirisini düzenleyen önemli yeni kurallar vardır `switch` . İfadedeki değişkenin türüyle ilgili kısıtlamalar `switch` kaldırılmıştır.
Bu örnekte olduğu gibi herhangi bir tür `object` kullanılabilir. Case ifadeleri artık sabit değerlerle sınırlı değildir. Bu sınırlamanın kaldırılması, yeniden sıralama `switch` bölümlerinin bir programın davranışını değiştirebileceği anlamına gelir.

Sabit değerlerle sınırlı olduğunda, `case` ifadenin değeriyle birden fazla etiket eşleşmeyebilir `switch` . Her `switch` bölümün bir sonraki bölüme dönmesi gereken kuralla birlikte birleştirin ve `switch` bölümler, davranışları etkilemeden herhangi bir sırada yeniden düzenlenebilir.
Artık, daha Genelleştirilmiş `switch` ifadelerle, her bölümün sırası önemli. `switch`İfadeler metin sırasına göre değerlendirilir. Yürütme `switch` , deyimle eşleşen ilk etikete aktarır `switch` .  
`default`Durum yalnızca başka bir Case etiketi eşleşmezse yürütülür. Bu `default` durum, metin sırası ne olursa olsun son olarak değerlendirilir. `default`Böyle bir durum yoksa ve diğer `case` deyimlerden hiçbiri eşleşmezse, yürütme deyimden sonraki deyimde devam eder `switch` . `case`Etiket kodunun hiçbiri yürütülmez.

## <a name="when-clauses-in-case-expressions"></a>`when``case`deyimlerdeki yan tümceler

Etikette yan tümcesini kullanarak 0 alanı olan bu şekiller için özel durumlar yapabilirsiniz `when` `case` . Yüz uzunluğu 0 olan bir kare veya yarıçapı 0 olan bir daire 0 alanına sahiptir. Bu koşulu `when` , etiket üzerinde bir yan tümce kullanarak belirtirsiniz `case` :  

[!code-csharp[ComputeDegenerateShapes](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#07_ComputeDegenerateShapes "Compute shapes with 0 area")]

Bu değişiklik, yeni sözdizimi hakkında bazı önemli noktaları gösterir. İlk olarak, `case` bir bölüme birden çok etiket uygulanabilir `switch` . Bu etiketlerin herhangi biri olduğunda, ekstre bloğu yürütülür `true` . Bu örnekte, `switch` ifade bir daire ya da 0 alanı olan bir kare ise, yöntem 0 sabitini döndürür.

Bu örnek `case` , ilk blok için iki etiket içinde iki farklı değişken tanıtır `switch` . Bu `switch` bloktaki deyimlerin değişkenlerini `c` (daire için) veya `s` (kare için) kullandığına dikkat edin.
Bu değişkenlerden hiçbiri kesinlikle bu bloğa atanmamıştır `switch` .
Bu durumlardan biri eşleşiyorsa, değişkenlerden açıkça biri atanır.
Ancak, çalışma zamanında eşleşeceğinden, derleme zamanında *hangisinin* atandığını söylemek olanaksızdır. Bu nedenle, aynı blok için birden çok etiket kullandığınızda çoğu zaman `case` deyimde yeni bir değişken sunmaz `case` ya da değişkeni yalnızca `when` yan tümcesinde kullanacaksınız.

Bu şekilleri 0 alanla eklediyseniz, daha fazla şekil türü ekleyelim: dikdörtgen ve üçgen:

[!code-csharp[AddRectangleAndTriangle](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#09_AddRectangleAndTriangle "Add rectangle and triangle")]

 Bu değişiklik kümesi `case` , Yeni şekillerin her biri için bozuk Case ve Labels ve blokların etiketlerini ekler.

Son olarak, `null` bağımsız değişkenin olmamasını sağlamak için büyük/küçük harf ekleyebilirsiniz `null` :

[!code-csharp[NullCase](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#10_NullCase "Add null case")]

Düzendeki `null` Constant `null` bir tür içermediğinden, ancak herhangi bir başvuru türüne veya null yapılabilir değer türüne dönüştürülebildiğinden, model için özel davranış ilginç değildir. `null`, Bir türü herhangi bir türe dönüştürmek yerine, `null` değişkenin derleme zamanı türünden bağımsız olarak bir değerin herhangi bir tür düzeniyle eşleşmeyeceğini tanımlar. Bu davranış, yeni `switch` tabanlı tür deseninin deyimle tutarlı olmasını sağlar `is` : `is` deyimler, `false` denetlenen değer olduğunda her zaman döndürülür `null` . Ayrıca daha basittir: türü denetledikten sonra, ek null bir denetim gerekmez. Yukarıdaki örneklerin herhangi bir durum bloklarında hiçbir null denetim olmadığını ve tür örüntüsünün eşleşmesi null olmayan bir değer garantisi olduğundan, bu durum gerekli değildir.

## <a name="var-declarations-in-case-expressions"></a>`var``case`deyimlerdeki bildirimler

`var`Eşleşme ifadelerinden biri olarak giriş, model eşleşmesi için yeni kurallar sağlar.

İlk kural `var` bildirimin normal tür çıkarımı kurallarını takip ediyor: tür, anahtar ifadesinin statik türü olarak algılanır. Bu kuraldan, türü her zaman eşleşir.

İkinci kural, bir `var` bildirimin diğer tür deseninin içerdiği null denetimini içermediği bir bildirimde bulunur. Bu, değişkenin null olabileceği ve bu durumda null bir denetim olması gerektiği anlamına gelir.

Bu iki kural, `var` bir ifadedeki bir bildirimin bir `case` ifadeyle aynı koşullara uyan birçok örnekte olduğu anlamına gelir `default` .
Durum için varsayılan olmayan bir durum tercih edildiği için `default` , `default` Bu durum hiçbir şekilde yürütülmez.

> [!NOTE]
> Derleyici, bir `default` Servis talebinin yazıldığı ancak hiçbir zaman yürütülebileceği durumlarda uyarı göstermez. Bu, `switch` tüm olası durumların listelendiği geçerli ifade davranışıyla tutarlıdır.

Üçüncü kural, bir `var` Servis talebinin yararlı olabileceğini kullanır. Girişin bir dize olduğu ve bilinen komut değerlerini aradığınız bir model eşleşmesi yaptığınızı düşünün. Şöyle bir işlem yazabilirsiniz:

[!code-csharp[VarCaseExpression](../../samples/snippets/csharp/PatternMatching/Program.cs#VarCaseExpression "use a var case expression to filter white space")]

`var`Durum `null` , boş dize veya yalnızca boşluk içeren herhangi bir dize ile eşleşir. Önceki kodun, `?.` yanlışlıkla bir oluşturmadığından emin olmak için işlecini kullandığına dikkat edin <xref:System.NullReferenceException> . `default`Durum, bu komut ayrıştırıcısı tarafından anlaşılmayan diğer dize değerlerini işler.

Bu, `var` bir ifadeden farklı bir Case ifadesini düşünmek isteyebileceğiniz bir örnektir `default` .

## <a name="conclusions"></a>Sonuçlar

*Model eşleştirme yapıları* , bir devralma hiyerarşisi tarafından ilgili olmayan farklı değişkenler ve türler arasında denetim akışını kolayca yönetmenizi sağlar. Ayrıca, değişkende test ettiğiniz herhangi bir koşulu kullanmak için mantığı da denetleyebilirsiniz. Daha fazla dağıtılmış uygulama oluştururken daha sık ihtiyacınız olacak desenler ve deyimler sayesinde, verilerin ve bu verileri işleyen yöntemlerin ayrı olduğu durumlar vardır. Bu örnekte kullanılan şekil yapıların hiçbir yöntem içermediğini, yalnızca salt okunurdur özellikleri olduğunu fark edeceksiniz.
Model eşleştirme, herhangi bir veri türü ile birlikte çalışabilir. Nesneyi inceleyecek ve bu koşullara göre denetim akışı kararları veren ifadeler yazarsınız.

Bu örnekteki kodu, bir soyut `Shape` ve belirli türetilmiş şekillerin her biri, alanı hesaplamak için kendi sanal yöntem uygulamalarına sahip olan bir sınıf hiyerarşisi oluşturmaktan izlenecek tasarımla karşılaştırın. Genellikle, verilerle çalışırken ve veri depolama sorunlarını davranış kaygılarından ayırmak istediğinizde, model eşleştirme ifadelerinin çok faydalı bir araç olduğunu fark edeceksiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: veri türlerini genişletmek için model eşleştirme özelliklerini kullanma](tutorials/pattern-matching.md)
