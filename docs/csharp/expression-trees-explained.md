---
title: İfade ağaçları açıklanmıştır
description: İfade ağaçları ve nasıl yürütmeden önce dış yürütme ve İnceleme kod çevirme algoritmaları yararlı oldukları hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: bbcdd339-86eb-4ae5-9911-4c214a39a92d
ms.openlocfilehash: 97cba9e5ec388729d23fb2689dfc1842a42af9b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216875"
---
# <a name="expression-trees-explained"></a>İfade ağaçları açıklanmıştır

[Önceki--genel bakış](expression-trees.md)

Bir ifade ağacına kodu tanımlayan bir veri yapısıdır. Bunlar, bir derleyici kodu çözümlemek ve derlenmiş çıktı üretmek için kullandığı aynı yapıları temel alır. Bu öğreticide okurken oldukça biraz benzerlik ifade ağaçları Roslyn API'leri oluşturmak için kullanılan türleri arasındaki fark edeceksiniz [Çözümleyicileri ve CodeFixes](https://github.com/dotnet/roslyn-analyzers).
(Çözümleyicileri ve CodeFixes kodu statik çözümlemesi ve olası düzeltmeler için bir geliştirici önerebilir NuGet paketlerdir.) Kavram benzer ve sonuç anlamlı bir şekilde kaynak kodunu incelenmesi izin veren bir veri yapısıdır. Ancak, ifade ağaçları sınıfları ve API'leri Roslyn API'ları daha farklı bir dizi temel alır.
    
Basit bir örneğe bakalım.
Bir kod satırı şöyledir:
```csharp
var sum = 1 + 2;
```
Bu bir ifade ağacına çözümlemek için olsaydı, ağaç birçok düğümlerini içerir.
Atama değişken bildirimi deyimiyle en dıştaki düğümdür (`var sum = 1 + 2;`) o en dıştaki düğüm birkaç alt düğümleri içerir: bir değişken bildirimi, bir atama işleci ve sağ tarafındaki eşittir işareti temsil eden bir ifade. İfade başka ek işlemi ve ayrıca sol ve sağ işlenenleri temsil eden ifadelere bölünmüştür.

Şimdi biraz daha sağ tarafındaki eşittir işareti olun ifadeleri detaya.
İfade `1 + 2`. Bu ikili bir ifadedir. Daha açık belirtmek gerekirse bir ikili Toplama ifadesi değil. Bir ikili Toplama ifadesi toplama ifadesinin sol ve sağ düğümleri temsil eden iki alt sahiptir. Her iki düğüm sabit ifadeler şunlardır: sol işleneni değerdir `1`, ve sağ işleneni değerdir `2`.

Görsel olarak, tüm deyimi bir ağacıdır: kök düğümde başlatın ve ağacında deyimi yapar kodu görmek için her düğüme seyahat:

- Atama deyimiyle değişken bildirimi (`var sum = 1 + 2;`)
    * Örtük değişken türü bildirimi (`var sum`)
        - Örtük var anahtar sözcüğü (`var`)
        - Değişken adı bildirimi (`sum`)
    * Atama işleci (`=`)
    * İkili Toplama ifadesi (`1 + 2`)
        - Sol işleneni (`1`)
        - Toplama işleci (`+`)
        - Sağ işleneni (`2`)

Bu karmaşık görünebilir, ancak çok güçlü bir özelliktir. Aynı işlemi çok daha karmaşık ifadeler bozabilir. Bu ifade göz önünde bulundurun:
```csharp
var finalAnswer = this.SecretSauceFunction(
    currentState.createInterimResult(), currentState.createSecondValue(1, 2),
    decisionServer.considerFinalOptions("hello")) +
    MoreSecretSauce('A', DateTime.Now, true);
```

Yukarıdaki aynı zamanda bir atamasına sahip bir değişken bildirimi ifadesidir.
Bu örnekte, sağ taraftaki atamasının çok daha karmaşık bir ağacıdır.
Bu ifade parçalayın, ancak ne farklı düğümler olabilir göz önünde bulundurun yapacağım değil. Geçerli nesneyi kullanarak bir alıcı, açık olan bir yöntem çağrıları vardır `this` alıcı, mevcut bir. Yöntem çağrıları diğer alıcı nesneleri kullanarak, farklı türlerde sabit bir bağımsız değişken. Ve son olarak, bir ikili Toplama işleci yok. Dönüş türüne bağlı olarak `SecretSauceFunction()` veya `MoreSecretSauce()`, bu ikili Toplama işleci sınıfı için tanımlanmış ikili Toplama işleci için bir statik yöntem çağrısı çözümleme bir geçersiz kılınan Toplama işleci için bir yöntem çağrısı olabilir.

Algılanan bu karmaşıklıktan rağmen yukarıdaki ifadeyi ilk örnek olarak kolayca olarak gittiğinizde bir ağaç yapısı oluşturur. İfade yaprak düğümlerin bulmak için alt düğümleri geçme tutmak. Üst düğüm kendi alt öğelerine başvurular varsa ve her düğüm ne tür bir düğümü tanımlar bir özelliğe sahiptir.

Bir ifade ağacına yapısını çok tutarlıdır. Temel bilgileri öğrendiğinize sonra bir ifade ağacına temsil edilir olduğunda bile en karmaşık kod anlayabilirsiniz. Veri yapısı içinde şıklık nasıl C# Derleyici en karmaşık C# programları çözümleyebilir ve bu karmaşık kaynak kodundan uygun çıkış oluşturma açıklanmaktadır.

İfade ağaçları yapısıyla tanıdık sonra hızlı bir şekilde elde bilgi, pek çok daha Gelişmiş senaryolar ile çalışmanıza olanak sağlar bulacaksınız. İfade ağaçları inanılmaz gücü yoktur.

Diğer ortamlarda yürütmek için algoritmaları çevirme ek olarak, ifade ağaçları yürütmeden önce kodu incelemek algoritmaları yazmayı kolaylaştırmak için kullanılabilir. Bir yöntemi olan bağımsız değişkenler ifadelerini ve kod çalıştırmadan önce bu ifadeleri inceleyin yazabilirsiniz. İfade ağacına kodu tam gösterimidir: herhangi bir alt ifade değerlerini görebilirsiniz.
Yöntem ve özellik adları görebilirsiniz. Tüm sabit ifadeler değerini görebilirsiniz.
Bir ifade ağacına yürütülebilir bir temsilci dönüştürmek ve kod yürütebilir.

İfade ağaçları API'leri neredeyse tüm geçerli kod yapısını temsil eden ağaçları oluşturmanızı sağlar. Ancak, işleri olabildiğince basit tutmak için bazı C# deyimleri bir ifade ağacına olarak oluşturulamıyor. Bir örnektir zaman uyumsuz ifadeleri (kullanarak `async` ve `await` anahtar sözcükler). Zaman uyumsuz algoritmaları gereksinimlerinizi ihtiyacınız varsa işlemek gerekir `Task` derleyici desteği kullanan yerine doğrudan nesneleri. Başka bir döngüler oluşturmada olur. Bunlar kullanarak oluşturduğunuz genellikle `for`, `foreach`, `while` veya `do` döngüler. Gördüğünüz gibi [bu serideki sonraki](expression-trees-building.md), ile tek döngü ifade için ifade ağaçları API'lerini destekleyen `break` ve `continue` döngü yinelenen denetim ifadeleri.

Yapamayacağınız tek şey, bir ifade ağacına Değiştir ' dir.  İfade ağaçları değişmez veri yapılarını ' dir. (Değiştirin) bir ifade ağacına kesilecek istiyorsanız, bir kopyası özgün, ancak istenen değişikliklerinizi içeren yeni bir ağaç oluşturmanız gerekir. 

[Sonraki--Framework destekleyen ifade ağaçları türleri](expression-classes.md)
