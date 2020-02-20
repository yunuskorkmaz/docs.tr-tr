---
title: Model eşleştirme C# Kılavuzu
description: İçindeki desenler eşleşen ifadeler hakkında bilgi edininC#
ms.date: 04/10/2019
ms.technology: csharp-fundamentals
ms.assetid: 1e575c32-2e2b-4425-9dca-7d118f3ed15b
ms.openlocfilehash: db509a0ebf1e205e9996ba8102757fe8c0b9ea3a
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77501622"
---
# <a name="pattern-matching"></a>Desen Eşleştirme

Desenler bir değerin belirli bir *şekle*sahip olduğunu ve eşleşen şekline sahip olduğu zaman değerden bilgi *ayıklayabilirler* . Model eşleştirme, günümüzde zaten kullandığınız algoritmalar için daha kısa sözdizimi sağlar. Mevcut söz dizimini kullanarak model eşleştirme algoritmaları zaten oluşturmuş olursunuz. Değerleri test eden `if` veya `switch` deyimlerini yazarsınız. Daha sonra, bu deyimler eşleşiyorsa, bu değerden bilgi ayıklar ve bunları kullanabilirsiniz. Yeni sözdizimi öğeleri, zaten bildiğiniz deyimlere yönelik uzantılardır: `is` ve `switch`. Bu yeni uzantılar bir değeri test eden ve bu bilgileri ayıklayarak birleştirir.

Bu makalede, nasıl okunabilir, kısa kod etkinleştirmesinin nasıl yapıldığını gösteren yeni sözdizimine bakacağız. Desen eşleştirme, verilerin ve kodun ayrıldığı ve verilerin ve bunları işleyen yöntemlerin sıkı bir şekilde birbirine bağlı olduğu nesne odaklı tasarımlardan farklı olarak, verilerin ve kodun ayrıldığı deyimler sunar.

Bu yeni deyimleri göstermek için, model eşleştirme deyimlerini kullanarak geometrik şekilleri temsil eden yapılarla çalışmaalım. Nesnenin çalışma zamanı türüne göre nesne davranışını özelleştirmek için sınıf hiyerarşileri oluşturma ve [sanal yöntemleri oluşturma ve geçersiz kılınan Yöntemler](methods.md#inherited) hakkında bilgi sahibisiniz.

Bu teknikler, bir sınıf hiyerarşisinde yapılandırılmamış veriler için mümkün değildir. Veriler ve Yöntemler ayrı olduğunda, diğer araçlara ihtiyacınız vardır. Yeni *model eşleştirme* yapıları, verileri incelemek ve bu verilerin herhangi bir koşuluna göre denetim akışını işlemek için temizleyici sözdizimini etkinleştirir. Bir değişkenin değerini test eden `if` deyimlerini ve `switch` zaten yazın. Bir değişkenin türünü test eden `is` deyimlerini yazarsınız. *Model eşleştirme* , bu deyimlere yeni yetenekler ekler.

Bu makalede, farklı geometrik şekillerin alanını hesaplayan bir yöntem oluşturacaksınız. Ancak, nesne yönelimli teknikler için bir daha olmadan ve farklı şekiller için bir sınıf hiyerarşisi oluşturmadan bunu yapabilirsiniz.
Bunun yerine *model eşleştirmeyi* kullanacaksınız.
Bu örneğe giderek, bu kodun bir nesne hiyerarşisi olarak nasıl yapılandırıldığı ile karşıtlığı vardır. Sorgu ve işleme gereken veriler bir sınıf hiyerarşisi olmadığında, desen eşleştirme zarif tasarımları mümkün değildir.

Bir soyut şekil tanımıyla başlamak ve farklı özel şekil sınıfları eklemek yerine, yalnızca geometrik şekillerin her biri için yalnızca basit veri tanımlarıyla başlayalım.

[!code-csharp[ShapeDefinitions](../../samples/csharp/PatternMatching/Shapes.cs#01_ShapeDefinitions "Shape definitions")]

Bu yapılardan, bazı şekillerin alanını hesaplayan bir yöntem yazalım.

## <a name="the-is-type-pattern-expression"></a>`is` tür deseninin ifadesi

7,0 C# öncesinde, her türü bir dizi `if` ve `is` deyimlerde test etmeniz gerekir:

[!code-csharp[ClassicIsExpression](../../samples/csharp/PatternMatching/GeometricUtilities.cs#02_ClassicIsExpression "Classic type pattern using is")]

Yukarıdaki kod, *tür deseninin*klasik bir ifadesidir: türünü tespit etmek ve bu türe göre farklı bir eylem almak için bir değişkeni test etiyorsunuz.

Bu kod, test başarılı olursa bir değişken atamak için `is` ifadesi uzantıları kullanılarak daha kolay hale gelir:

[!code-csharp[IsPatternExpression](../../samples/csharp/PatternMatching/GeometricUtilities.cs#03_IsPatternExpression "is pattern expression")]

Bu güncelleştirilmiş sürümde, `is` ifadesi her ikisi de değişkeni sınar ve uygun türdeki yeni bir değişkene atar. Ayrıca, bu sürümün bir `struct``Rectangle` türünü de içerdiğine dikkat edin. Yeni `is` ifadesi, değer türleri ve başvuru türleri ile birlikte kullanılabilir.

Bir eşleştirme ifadesinin sonuçlarının yanlış kullanılmasını önlemenize yardımcı olacak şekilde, model eşleştirme ifadelerine yönelik dil kuralları. Yukarıdaki örnekte, `s`, `c`ve `r` değişkenleri yalnızca kapsamdadır ve ilgili model eşleştirme ifadelerinde `true` sonuçları olduğunda kesinlikle atanır. Başka bir konumda herhangi bir değişken kullanmayı denerseniz, kodunuz derleyici hataları oluşturur.

Bu kuralların her ikisini de kapsam ile başlayarak ayrıntılı bir şekilde incelim. `c` değişkeni yalnızca ilk `if` deyimin `else` dalında kapsamdadır. `s` değişkeni, metot `ComputeAreaModernIs`kapsamdadır. Bunun nedeni, `if` deyimin her bir dalı değişkenler için ayrı bir kapsam oluşturur. Ancak, `if` deyimin kendisi değildir. Diğer bir deyişle, `if` bildiriminde belirtilen değişkenlerin `if` bildirimiyle aynı kapsamda (Bu durumda, yöntemi). Bu davranış, model eşleştirmeye özgü değildir, ancak değişken kapsamları ve `if` ve `else` deyimleri için tanımlanan davranıştır.

`c` ve `s` değişkenleri, kesin olarak atanan doğru mekanizmasından dolayı ilgili `if` deyimleri doğru olduğunda atanır.

> [!TIP]
> Bu konudaki örneklerde, `if` deyiminin `true` dalında eşleşme değişkenini kesin bir şekilde atayan bir model eşleştirme `is` ifadesi, önerilen yapıyı kullanır.
> `if (!(shape is Square s))` diyerek mantığı ters çevirebilirsiniz ve `s` değişkeni yalnızca `false` dalında kesinlikle atanmasını sağlayabilirsiniz. Bu geçerli C#olsa da, mantığın izlenmesi daha kafa karıştırıcı olduğundan önerilmez.

Bu kurallar, bu düzenin karşılanmadığı zaman bir model eşleştirme ifadesinin sonucuna yanlışlıkla erişmeniz çok düşüktür.

## <a name="using-pattern-matching-switch-statements"></a>Model eşleştirme `switch` deyimlerini kullanma

Aynı zamanda, diğer şekil türlerini desteklemeniz gerekebilir. Test ettiğiniz koşulların sayısı arttıkça, `is` deseninin eşleşen ifadelerin kullanımı fazla olabilir. Denetlemek istediğiniz her türde `if` deyimlerinin gerektirmesinin yanı sıra, girişin tek bir türle eşleşmesi durumunda `is` ifadeleri test etmek için sınırlandırılır. Bu durumda, `switch` deseninin eşleşen ifadelerin daha iyi bir seçenek haline geldiğini göreceksiniz. 

Geleneksel `switch` deyimi bir desenli ifadedir: sabit örüntü destekleniyor.
Bir değişkeni `case` ifadesinde kullanılan herhangi bir sabitle karşılaştırabilirsiniz:

[!code-csharp[ClassicSwitch](../../samples/csharp/PatternMatching/GeometricUtilities.cs#04_ClassicSwitch "Classic switch statement")]

`switch` deyimin desteklediği tek desenler sabit bir modeldir. Sayısal türlerle ve `string` türüyle daha fazla sınırlandırıldı.
Bu kısıtlamalar kaldırılmıştır ve artık tür modelini kullanarak bir `switch` ifadesini yazabilirsiniz:

[!code-csharp[Switch Type Pattern](../../samples/csharp/PatternMatching/GeometricUtilities.cs#05_SwitchTypePattern "Compute with `switch` expression")]

`switch` ifadesiyle eşleşen desenler, geleneksel C stili `switch` ifadesini kullanan geliştiriciler için tanıdık sözdizimini kullanır. Her `case` değerlendirilir ve giriş değişkeniyle eşleşen koşulun altındaki kod yürütülür. Kod yürütme, bir Case ifadesinden sonrakine "düşmüyor". `case` deyimin sözdizimi her bir `case` `break`, `return`veya `goto`ile bitmesidir.

> [!NOTE]
> Başka bir etikete atlanacak `goto` deyimleri yalnızca sabit model için geçerlidir (klasik switch deyimi).

`switch` ifadesini düzenleyen önemli yeni kurallar vardır. `switch` ifadesindeki değişkenin türüyle ilgili kısıtlamalar kaldırılmıştır.
Bu örnekteki `object` gibi herhangi bir tür kullanılabilir. Case ifadeleri artık sabit değerlerle sınırlı değildir. Bu sınırlamanın kaldırılması, yeniden sıralama `switch` bölümlerinin bir programın davranışını değiştirebileceği anlamına gelir.

Sabit değerlerle sınırlı olduğunda, birden fazla `case` etiketi `switch` ifadesinin değeriyle eşleşemez. Her `switch` bölümünün bir sonraki bölüme düşmemelidir ve `switch` bölümlerinin davranışı etkilemeden herhangi bir sırada yeniden düzenlenebilir olması için bunu birleştirin.
Artık, daha Genelleştirilmiş `switch` ifadelerle, her bölümün sırası önemlidir. `switch` ifadeleri metin sırasına göre değerlendirilir. Yürütme aktarımları, `switch` ifadesiyle eşleşen ilk `switch` etiketine aktarılır.  
`default` durum yalnızca başka bir durum etiketi eşleşmezse yürütülür. `default` durum, metin sırası ne olursa olsun son olarak değerlendirilir. `default` bir durum yoksa ve diğer `case` deyimlerinin hiçbiri eşleşmezse, yürütme, `switch` deyiminden sonraki deyimde devam eder. `case` etiket kodunun hiçbiri yürütülmez.

## <a name="when-clauses-in-case-expressions"></a>`case` ifadelerinde `when` yan tümceleri

`case` etiketinde bir `when` yan tümcesini kullanarak 0 alanı olan şekiller için özel durumlar yapabilirsiniz. Yüz uzunluğu 0 olan bir kare veya yarıçapı 0 olan bir daire 0 alanına sahiptir. `case` etiketinde `when` yan tümcesini kullanarak bu koşulu belirtirsiniz:  

[!code-csharp[ComputeDegenerateShapes](../../samples/csharp/PatternMatching/GeometricUtilities.cs#07_ComputeDegenerateShapes "Compute shapes with 0 area")]

Bu değişiklik, yeni sözdizimi hakkında bazı önemli noktaları gösterir. İlk olarak, birden çok `case` etiketi bir `switch` bölümüne uygulanabilir. Bu etiketlerin herhangi biri `true`olduğunda, ekstre bloğu yürütülür. Bu örnekte, `switch` ifadesi bir daire ya da 0 alanı olan bir kare ise, yöntem 0 sabitini döndürür.

Bu örnek, ilk `switch` bloğunun iki `case` etiketlerinde iki farklı değişken tanıtır. Bu `switch` bloğundaki deyimlerin `c` (daire için) veya `s` (kare için) değişkenlerini kullandığına dikkat edin.
Bu değişkenlerden hiçbiri kesinlikle bu `switch` bloğunda atanmaz.
Bu durumlardan biri eşleşiyorsa, değişkenlerden açıkça biri atanır.
Ancak, çalışma zamanında eşleşeceğinden, derleme zamanında *hangisinin* atandığını söylemek olanaksızdır. Bu nedenle, aynı blok için birden çok `case` etiketi kullandığınızda, `case` bildiriminde yeni bir değişken açıklamaz veya yalnızca `when` yan tümcesindeki değişkenini kullanacaksınız.

Bu şekilleri 0 alanla eklediyseniz, daha fazla şekil türü ekleyelim: dikdörtgen ve üçgen:

[!code-csharp[AddRectangleAndTriangle](../../samples/csharp/PatternMatching/GeometricUtilities.cs#09_AddRectangleAndTriangle "Add rectangle and triangle")]

 Bu değişiklik kümesi, Yeni şekillerin her biri için bozuk Case ve Labels ve blokların `case` Etiketler ekler. 

Son olarak, bağımsız değişkenin `null`olmamasını sağlamak için `null` bir durum ekleyebilirsiniz:

[!code-csharp[NullCase](../../samples/csharp/PatternMatching/GeometricUtilities.cs#10_NullCase "Add null case")]

`null` deseninin özel davranışı ilginç olduğundan, düzendeki sabit `null` bir tür olmadığından, ancak herhangi bir başvuru türüne veya null yapılabilir türe dönüştürülebildiğinden. `null`, herhangi bir türe dönüştürmek yerine, değişkenin derleme zamanı türünden bağımsız olarak, bir `null` değerinin herhangi bir tür düzeniyle eşleşmeyeceğini tanımlar. Bu davranış yeni `switch` tabanlı tür deseninin `is` ifadesiyle tutarlı olmasını sağlar: `is` deyimleri, denetlenen değer `null`olduğunda her zaman `false` döndürür. Ayrıca daha basittir: türü denetledikten sonra, ek null bir denetim gerekmez. Yukarıdaki örneklerin herhangi bir durum bloklarında hiçbir null denetim olmadığını ve tür örüntüsünün eşleşmesi null olmayan bir değer garantisi olduğundan, bu durum gerekli değildir.

## <a name="var-declarations-in-case-expressions"></a>`case` ifadelerinde `var` bildirimleri

Eşleşme ifadelerinden biri olarak `var` giriş, model eşleştirmesinde yeni kurallar tanıtır.

İlk kural `var` bildirimi normal tür çıkarımı kurallarını izliyorsa: tür, anahtar ifadesinin statik türü olarak algılanır. Bu kuraldan, türü her zaman eşleşir.

İkinci kural, `var` bildiriminde diğer tür deseninin içerdiği null denetimi yoktur. Bu, değişkenin null olabileceği ve bu durumda null bir denetim olması gerektiği anlamına gelir.

Bu iki kural birçok örnekte, bir `case` ifadesinde `var` bildirimi `default` ifadesiyle aynı koşullara uyan anlamına gelir.
`default` durum için varsayılan olmayan herhangi bir durum tercih edildiği için, `default` durumu hiçbir şekilde yürütülmeyecektir.

> [!NOTE]
> Derleyici, `default` bir durumun yazıldığı ancak hiçbir zaman yürütülebileceği durumlarda uyarı göstermez. Bu, olası tüm durumlar listelendiğinde geçerli `switch` deyimin davranışıyla tutarlıdır.

Üçüncü kural, `var` bir durumun yararlı olabileceği yerleri kullanır. Girişin bir dize olduğu ve bilinen komut değerlerini aradığınız bir model eşleşmesi yaptığınızı düşünün. Şöyle bir işlem yazabilirsiniz:

[!code-csharp[VarCaseExpression](../../samples/csharp/PatternMatching/Program.cs#VarCaseExpression "use a var case expression to filter white space")]

`var` durum `null`, boş dize veya yalnızca boşluk içeren herhangi bir dizeyle eşleşir. Önceki kodun, yanlışlıkla bir <xref:System.NullReferenceException>oluşturmadığından emin olmak için `?.` işlecini kullandığına dikkat edin. `default` durum, bu komut ayrıştırıcısı tarafından anlaşılmayan diğer dize değerlerini işler.

Bu, bir `default` ifadesinden farklı bir `var` Case ifadesini düşünmek isteyebileceğiniz bir örnektir.

## <a name="conclusions"></a>Sonuçlar

*Model eşleştirme yapıları* , bir devralma hiyerarşisi tarafından ilgili olmayan farklı değişkenler ve türler arasında denetim akışını kolayca yönetmenizi sağlar. Ayrıca, değişkende test ettiğiniz herhangi bir koşulu kullanmak için mantığı da denetleyebilirsiniz. Daha fazla dağıtılmış uygulama oluştururken daha sık ihtiyacınız olacak desenler ve deyimler sayesinde, verilerin ve bu verileri işleyen yöntemlerin ayrı olduğu durumlar vardır. Bu örnekte kullanılan şekil yapıların hiçbir yöntem içermediğini, yalnızca salt okunurdur özellikleri olduğunu fark edeceksiniz.
Model eşleştirme, herhangi bir veri türü ile birlikte çalışabilir. Nesneyi inceleyecek ve bu koşullara göre denetim akışı kararları veren ifadeler yazarsınız.

Bu örnekteki kodu, bir soyut `Shape` için bir sınıf hiyerarşisi oluşturmaktan ve her biri, alanı hesaplamak için bir sanal yöntemin kendi uygulamalarına sahip olan belirli türetilmiş şekillerin, bu örnekten karşılaştırın. Genellikle, verilerle çalışırken ve veri depolama sorunlarını davranış kaygılarından ayırmak istediğinizde, model eşleştirme ifadelerinin çok faydalı bir araç olduğunu fark edeceksiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: veri türlerini genişletmek için model eşleştirme özelliklerini kullanma](tutorials/pattern-matching.md)
