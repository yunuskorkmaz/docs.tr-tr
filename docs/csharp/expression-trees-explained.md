---
title: İfade Ağaçları Açıklaması
description: İfade ağaçları ve dış yürütmeye yönelik algoritmalarda nasıl yararlı olduğu ve yürütmeden önce kodu İnceleme hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: bbcdd339-86eb-4ae5-9911-4c214a39a92d
ms.openlocfilehash: c5d4b2ad54fab547567d430f11a31542a11d03f3
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104802"
---
# <a name="expression-trees-explained"></a>İfade Ağaçları Açıklaması

[Önceki--genel bakış](expression-trees.md)

Ifade ağacı kodu tanımlayan bir veri yapısıdır. Bunlar, bir derleyicinin kodu çözümlemek ve derlenen çıktıyı oluşturmak için kullandığı yapıları temel alırlar. Bu öğreticiyi okurken, [çözümleyiciler ve kod düzeltmeleri](https://github.com/dotnet/roslyn-analyzers)oluşturmak Için ifade ağaçları ve Roslyn API 'lerinde kullanılan türler arasında çok sayıda benzerlik olduğunu fark edeceksiniz.
(Çözümleyiciler ve kod düzeltmeleri, kodda statik analiz gerçekleştiren ve bir geliştirici için olası düzeltmeler öneren NuGet paketlerdir.) Kavramlar benzerdir ve nihai sonuç, kaynak kodun anlamlı bir şekilde incelemesini sağlayan bir veri yapısıdır. Ancak, Ifade ağaçları, Roslyn API 'Lerine göre tamamen farklı bir sınıf ve API kümesine dayanır.

Basit bir örneğe bakalım.
Aşağıda bir kod satırı verilmiştir:

```csharp
var sum = 1 + 2;
```

Bunu bir ifade ağacı olarak çözümlüyorsanız, ağaç birkaç düğüm içerir.
En dıştaki düğüm, birden çok alt düğüm içeren (`var sum = 1 + 2;`) bir değişken bildirimi, atama işleci ve eşittir işaretinin sağ tarafını temsil eden bir ifade olan bir değişken bildirim deyimidir. Bu ifade, toplama işlemini ve ek olarak sol ve sağ işlenenleri temsil eden ifadelere daha fazla bölünmüştür.

Eşittir işaretinin sağ tarafını oluşturan ifadelerle biraz daha fazla ayrıntıya bakalım.
İfade `1 + 2`. Bu bir ikili ifadedir. Daha özel olarak, bu bir ikili ekleme ifadesidir. İkili ekleme ifadesinde, ek ifadenin sol ve sağ düğümleri temsil eden iki alt öğe vardır. Burada her iki düğüm de sabit ifadelerdir: Sol işlenen değerdir `1`ve sağ işlenen değerdir `2`.

Görsel olarak, tüm deyimin bir ağaç olması gerekir: Kök düğümden başlayabilir ve bu ifadeyi oluşturan kodu görmek için ağaçtaki her bir düğüme yolculuk yapabilirsiniz:

- Atama (`var sum = 1 + 2;`) ile değişken bildirimi ekstresi
  - Örtük değişken türü bildirimi (`var sum`)
    - Örtük var anahtar sözcüğü`var`()
    - Değişken adı bildirimi (`sum`)
  - Atama işleci (`=`)
  - İkili ekleme ifadesi (`1 + 2`)
    - Sol işlenen (`1`)
    - Toplama işleci (`+`)
    - Right işleneni (`2`)

Bu karmaşık görünebilir, ancak çok güçlüdür. Aynı süreci izleyerek, daha karmaşık ifadeler de oluşturabilirsiniz. Şu ifadeyi göz önünde bulundurun:

```csharp
var finalAnswer = this.SecretSauceFunction(
    currentState.createInterimResult(), currentState.createSecondValue(1, 2),
    decisionServer.considerFinalOptions("hello")) +
    MoreSecretSauce('A', DateTime.Now, true);
```

Yukarıdaki ifade ayrıca atama içeren bir değişken bildirimidir.
Bu örnekte, atamanın sağ tarafı çok daha karmaşık bir ağacdır.
Bu ifadeyi parçalara ayırmayı istemiyorum, ancak farklı düğümlerin ne olabileceğini düşünün. Geçerli nesneyi, bir alıcı olarak kullanan ve açık `this` alıcısı olan, diğeri olmayan yöntem çağrıları vardır. Diğer alıcı nesnelerini kullanan Yöntem çağrıları vardır, farklı türlerde sabit bağımsız değişkenler vardır. Son olarak, bir ikili toplama işleci vardır. `SecretSauceFunction()` Veya`MoreSecretSauce()`dönüş türüne bağlı olarak, bu ikili ek işleci, geçersiz kılınan bir toplama işlecine bir yöntem çağrısı olabilir ve bir sınıf için tanımlanan ikili toplama işlecine bir statik yöntem çağrısına çözüm verebilir.

Bu algılanan karmaşıklığa rağmen yukarıdaki ifade, ilk örnek olarak kolayca gezinilede bir ağaç yapısı oluşturur. İfadede yaprak düğümleri bulmak için alt düğümlerin geçiş tutulmasını sağlayabilirsiniz. Üst düğümlerin alt öğelerine başvuruları olacaktır ve her düğüm, ne tür bir düğüm olduğunu açıklayan bir özelliğe sahiptir.

Bir ifade ağacının yapısı çok tutarlıdır. Temel bilgileri öğrendikten sonra, bir ifade ağacı olarak temsil edildiğinde en karmaşık kodu bile anlayabilirsiniz. Veri yapısındaki inceliğini, C# derleyicinin en karmaşık C# programları nasıl çözümleyebileceğini ve bu karmaşık kaynak kodundan doğru çıktı oluşturmasına nasıl yönelik olduğunu açıklar.

İfade ağaçları yapısına alışdıktan sonra, elde ettiğiniz bilgileri daha fazla ve daha fazla gelişmiş senaryolarla çalışmanıza olanak tanıcaksınız. İfade ağaçları için inanılmaz güç vardır.

Algoritmaları başka ortamlarda yürütmek üzere çevirmenin yanı sıra, kod yürütmeden önce kodu İnceleme algoritmalarının yazmayı kolaylaştırmak için ifade ağaçları kullanılabilir. Bağımsız değişkenleri ifade olan bir yöntem yazabilir ve ardından kodu yürütmeden önce bu ifadeleri inceleyebilirsiniz. Ifade ağacı kodun tam bir gösterimidir: herhangi bir alt ifadenin değerlerini görebilirsiniz.
Yöntem ve özellik adlarını görebilirsiniz. Herhangi bir sabit ifadenin değerini görebilirsiniz.
Ayrıca, bir ifade ağacını yürütülebilir bir temsilciye dönüştürebilir ve kodu yürütebilirsiniz.

Ifade ağaçları için API 'Ler, neredeyse tüm geçerli kod yapısını temsil eden ağaçlar oluşturmanızı sağlar. Ancak, şeyleri mümkün olduğunca basit tutmak için bir ifade ağacında C# bazı ıoms oluşturulamaz. Bir örnek, zaman uyumsuz ifadelerdir ( `async` ve `await` anahtar kelimeleri kullanılarak). Gereksinimleriniz zaman uyumsuz algoritmalar gerektiriyorsa, derleyici desteğine göre değil, `Task` nesneleri doğrudan işlemeniz gerekir. Başka bir döngü de oluşturmaktır. Genellikle,, `for` `while` veya `foreach` döngülerini`do` kullanarak bunları oluşturursunuz. [Bu serinin ilerleyen kısımlarında](expression-trees-building.md)göreceğiniz gibi, ifade ağaçları için API 'ler, ve `break` `continue` ile döngüyü tekrarlayarak belirten ifadelerle tek bir döngü ifadesi destekler.

Yapamayacağınız her şey bir ifade ağacını değiştirmektir.  İfade ağaçları değişmez veri yapılarıdır. Bir ifade ağacını bulunmamalıdır (değiştirmek) istiyorsanız, orijinalin bir kopyası olan, ancak istediğiniz değişikliklerle yeni bir ağaç oluşturmanız gerekir.

[Ifade ağaçlarını destekleyen bir sonraki--çerçeve türleri](expression-classes.md)
