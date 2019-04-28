---
title: İfade ağaçları açıklaması
description: İfade ağaçları ve nasıl yürütmeden önce dış yürütme ve İnceleme kod çevirme algoritmaları yararlı oldukları hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: bbcdd339-86eb-4ae5-9911-4c214a39a92d
ms.openlocfilehash: 3bad826bb58ff361688d3e13497343661e7edbd3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646611"
---
# <a name="expression-trees-explained"></a>İfade ağaçları açıklaması

[Önceki--genel bakış](expression-trees.md)

İfade ağacı kodu tanımlayan bir veri yapısıdır. Bunlar, bir derleyici kodu analiz edin ve derlenen Çıkışta oluşturmak için kullandığı aynı yapıları temel alır. Bu öğreticide belirtildiği gibi olayın benzerlik ifade ağaçları ve Roslyn API'leri oluşturmak için kullanılan türleri arasındaki fark edeceksiniz [Çözümleyicileri ve CodeFixes](https://github.com/dotnet/roslyn-analyzers).
(Kodu statik analizini ve bir geliştirici için olası düzeltmeleri önerebilir NuGet paketlerini Çözümleyicileri ve CodeFixes içindir.) Kavram benzer ve sonuç anlamlı bir şekilde kaynak kod incelemesini sağlayan bir veri yapısıdır. Ancak, ifade ağaçları sınıfları ve Roslyn API'leri API tamamen farklı bir kümesini temel alır.

Basit bir örneğe bakalım.
Bir kod satırı aşağıda verilmiştir:

```csharp
var sum = 1 + 2;
```

Bu bir ifade ağacı çözümlemek için olsaydı, birkaç düğüm ağacı içerir.
Bir değişken bildirimi deyimiyle atama en dıştaki düğümüdür (`var sum = 1 + 2;`) en dıştaki düğüm birkaç alt düğümleri içerir: bir değişken bildirimi, bir atama işleci ve sağ tarafında eşittir işareti temsil eden bir ifade. İfade başka toplama işlemi ve ayrıca sol ve sağ işleneni temsil eden ifadelere alt bölümlere.

Şimdi biraz daha eşittir işareti sağ tarafındaki olun ifadeler detayına.
İfade `1 + 2`. İkili ifade olmasıdır. Daha açık belirtmek gerekirse, bir ikili ayrıca ifadesidir. İkili ek ifade bir toplama ifadesinin sol ve sağ düğümleri temsil eden iki alt sahiptir. Aşağıda, her iki düğüm de sabit ifadeler verilmiştir: Sol işlenen değerdir `1`, ve sağ işlenen değer `2`.

Görsel olarak, tüm ifade ağacı şudur: Kök düğümde başlatın ve deyim yapan kodu görmek için ağacında her bir düğümüne seyahat:

- Değişken bildirimi deyimiyle Ataması (`var sum = 1 + 2;`)
  * Örtük değişken türü bildirimi (`var sum`)
    - Örtük var anahtar sözcüğü (`var`)
    - Değişken bildirimi (`sum`)
  * Atama işleci (`=`)
  * İkili ek ifade (`1 + 2`)
    - Sol işleneni (`1`)
    - Toplama işleci (`+`)
    - Sağ işlenen (`2`)

Bu karmaşık görünebilir, ancak çok güçlü bir özelliktir. Aynı işlemi çok daha karmaşık ifadeler bozabilir. Bu ifadeyi göz önünde bulundurun:

```csharp
var finalAnswer = this.SecretSauceFunction(
    currentState.createInterimResult(), currentState.createSecondValue(1, 2),
    decisionServer.considerFinalOptions("hello")) +
    MoreSecretSauce('A', DateTime.Now, true);
```

Yukarıdaki ayrıca bir değişken bildirimi bir atama ifadesidir.
Bu örnekte, sağ taraftaki atamasının çok daha karmaşık bir ağacıdır.
Bu ifade ayırmak, ancak ne farklı düğümleri olabilir göz önünde bulundurun tıklıyorum değil. Geçerli nesneyi kullanarak bir alıcı, açık olan bir yöntem çağrıları vardır `this` alıcı, daha önceden bir tane. Yöntem çağrıları diğer alıcı nesneleri kullanarak, farklı türden sabit bağımsız değişkenleri vardır. Ve son olarak, bir ikili Toplama işleci yoktur. Dönüş türüne bağlı olarak `SecretSauceFunction()` veya `MoreSecretSauce()`, bu ikili Toplama işleci için bir sınıf için tanımlanmış ikili Toplama işleci bir statik yöntem çağrısına çözümleme bir geçersiz kılınan bir toplama işlecinin metot çağrısı olabilir.

Algılanan bu karmaşıklığı rağmen yukarıdaki ifadeyi olarak ilk örnek olarak kolayca gittiğinizde bir ağaç yapısı oluşturur. Geçiş ifadesinde yaprak düğümleri bulmak için alt düğümleri tutun. Üst düğüm alt öğelerini başvurular varsa ve her düğüm, ne tür bir düğümü tanımlar bir özelliğe sahiptir.

İfade ağacı yapısını çok tutarlıdır. Temel öğrendikten sonra bir ifade ağacı temsil edilen zaman bile en karmaşık kod anlayabilirsiniz. Veri yapısı, şıklık açıklar nasıl C# derleyici en karmaşık analiz etmek C# programları ve o karmaşık kaynak kodundan uygun çıkış oluşturun.

İfade ağaçları yapısını tanıdık sonra hızlı bir şekilde elde ettiğiniz bilgi çok daha Gelişmiş senaryolar ile çalışmanıza olanak sağlayan bulabilirsiniz. İfade ağaçlarında yapılan inanılmaz gücü yoktur.

Diğer ortamlarda yürütmek için algoritmalar çevirme ek olarak, ifade ağaçları yürütmeden önce kod İnceleme algoritmaları yazmayı kolaylaştırmak için kullanılabilir. Bir yöntem bağımsız değişkenleri, ifadeler ve kodu yürütmeden önce söz konusu ifadelerden inceleyin yazabilirsiniz. İfade ağacı kod tam gösterimidir: herhangi bir alt ifade değerleri görebilirsiniz.
Yöntem ve özellik adları görebilirsiniz. Herhangi bir sabit ifadeler değeri görebilirsiniz.
Yürütülebilir bir temsilciye bir ifade ağacı dönüştürmek ve kod yürütebilir.

İfade ağaçları yönelik API'ler neredeyse tüm geçerli kod yapısını temsil eden ağaçları oluşturmanıza olanak sağlar. Ancak, bazı şeyler mümkün olduğunca basit tutmak için C# deyimleri içinde bir ifade ağacı oluşturulamıyor. Zaman uyumsuz ifadeleri bir örnek verilmiştir (kullanarak `async` ve `await` anahtar sözcükleri). Zaman uyumsuz algoritmaları gereksinimlerinizi ihtiyacınız varsa, işlemek gerekir `Task` derleyici desteğe güvenin yerine doğrudan nesneleri. Döngüler oluşturmak da başka bir özelliktir. Genellikle, bu kullanarak oluşturursunuz `for`, `foreach`, `while` veya `do` döngüleri. Gördüğünüz gibi [bu serideki sonraki](expression-trees-building.md), bir tek döngü ifadesi desteklemek için ifade ağaçları API'leri `break` ve `continue` döngü yinelenen denetim ifadeleri.

Yapamayacağınız tek şey, bir ifade ağacı değiştirdiğiniz yerdir.  İfade ağaçları sabit veri yapılarıdır. (Değiştirin) bir ifade ağacı bulunmamalıdır istiyorsanız, bir kopyası özgün, ancak istediğiniz değişiklikleri içeren yeni bir ağaç oluşturmanız gerekir.

[Sonraki--İfade ağaçlarını destekleyen çerçeve türleri](expression-classes.md)
