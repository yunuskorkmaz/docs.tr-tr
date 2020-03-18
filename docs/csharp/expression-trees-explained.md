---
title: İfade Ağaçları Açıklaması
description: İfade ağaçları ve yürütmeden önce dış yürütme ve kodu denetleme algoritmaları çevirmede nasıl yararlı oldukları hakkında bilgi edinin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: bbcdd339-86eb-4ae5-9911-4c214a39a92d
ms.openlocfilehash: 12093e9c9246c87cc5ea3aedaca6ba34acacce4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73036987"
---
# <a name="expression-trees-explained"></a>İfade Ağaçları Açıklaması

[Önceki -- Genel Bakış](expression-trees.md)

İfade Ağacı, kodu tanımlayan bir veri yapısıdır. Bunlar, derleyicinin kodu çözümlemek ve derlenmiş çıktıyı oluşturmak için kullandığı yapıları temel alır. Bu öğretici aracılığıyla okurken, İfade Ağaçlar ve [Analizörler ve CodeFixes](https://github.com/dotnet/roslyn-analyzers)oluşturmak için Roslyn API'lerde kullanılan türleri arasında benzerlik biraz fark edeceksiniz.
(Çözümleyiciler ve CodeFixes kod üzerinde statik analiz gerçekleştiren ve bir geliştirici için olası düzeltmeler önerebilir NuGet paketleridir.) Kavramlar benzerdir ve sonuç kaynak kodun anlamlı bir şekilde incelenmesine olanak tanıyan bir veri yapısıdır. Ancak, İfade Ağaçları Roslyn API'lerinden tamamen farklı sınıflara ve API'lere dayanır.

Basit bir örneğe bakalım.
İşte bir kod satırı:

```csharp
var sum = 1 + 2;
```

Bunu bir ifade ağacı olarak çözümleseydiniz, ağaç birkaç düğüm içerir.
En dıştaki düğüm atamaile değişken bildirim`var sum = 1 + 2;`deyimidir ( ) En dıştaki düğüm birkaç alt düğüm içerir: değişken bildirimi, bir atama işleci ve eşitler işaretinin sağ tarafını temsil eden bir ifade. Bu ifade, ekleme işlemini temsil eden ifadelere ve eklemenin sol ve sağ operandlarına daha fazla bölünmüştür.

Eşitler işaretinin sağ tarafını oluşturan ifadelere biraz daha inelim.
İfade. `1 + 2` Bu ikili bir ifade. Daha spesifik olarak, bu bir ikili ekleme ifadesidir. İkili ek ifade, ek ifadenin sol ve sağ düğümlerini temsil eden iki çocuktan içerir. Burada, her iki düğüm de sabit ifadelerdir: Sol `1`operand değeridir ve sağ `2`operand değeridir.

Görsel olarak, tüm deyim bir ağaçtır: Kök düğümünden başlayabilir ve deyimi oluşturan kodu görmek için ağaçtaki her düğüme seyahat edebilirsiniz:

- Atama lı değişken`var sum = 1 + 2;`bildirim deyimi ( )
  - Örtük değişken`var sum`türü bildirimi ( )
    - Örtük var`var`anahtar kelimesi ( )
    - Değişken ad`sum`bildirimi ( )
  - Atama işleci (`=`)
  - İkili ekleme`1 + 2`ifadesi ( )
    - Sol operand`1`( )
    - İlave`+`işleci ( )
    - Sağ operand`2`( )

Bu karmaşık görünebilir, ama çok güçlü. Aynı işlemi takiben, çok daha karmaşık ifadeleri ayrıştırabilirsiniz. Şu ifadeyi göz önünde bulundurun:

```csharp
var finalAnswer = this.SecretSauceFunction(
    currentState.createInterimResult(), currentState.createSecondValue(1, 2),
    decisionServer.considerFinalOptions("hello")) +
    MoreSecretSauce('A', DateTime.Now, true);
```

Yukarıdaki ifade de bir atama ile değişken bildirimidir.
Bu durumda, atamanın sağ tarafı çok daha karmaşık bir ağaçtır.
Bu ifadeyi ayrıştırmayacağım, ama farklı düğümlerin ne olabileceğini düşünün. Geçerli nesneyi alıcı olarak kullanan yöntem çağrıları vardır, `this` açık alıcısı olan, olmayan bir yöntem çağrıları vardır. Diğer alıcı nesneleri kullanarak yöntem çağrıları vardır, farklı türde sabit bağımsız değişkenler vardır. Ve son olarak, bir ikili ekleme işleci vardır. İade türüne bağlı `SecretSauceFunction()` olarak, `MoreSecretSauce()`bu ikili ekleme işleci, bir sınıf için tanımlanan ikili ekleme işleci için statik bir yöntem çağrısı çözme, geçersiz kılınmış bir ek işleç için bir yöntem çağrısı olabilir.

Algılanan bu karmaşıklığa rağmen, yukarıdaki ifade ilk örnek kadar kolay gezinilebilen bir ağaç yapısı oluşturur. İfadede yaprak düğümleri bulmak için alt düğümleri geçiş yapmaya devam edebilirsiniz. Üst düğümlerin çocuklarına referansları olacaktır ve her düğümün ne tür bir düğüm olduğunu açıklayan bir özelliği vardır.

İfade ağacının yapısı çok tutarlıdır. Temel bilgileri öğrendikten sonra, ifade ağacı olarak temsil edildiğinde en karmaşık kodu bile anlayabilirsiniz. Veri yapısındaki zarafet, C# derleyicisinin en karmaşık C# programlarını nasıl analiz edebildiğini ve bu karmaşık kaynak kodundan uygun çıktıyı nasıl oluşturabileceğini açıklar.

İfade ağaçlarının yapısına aşina olduktan sonra, hızlı bir şekilde kazandığınız bilginin çok daha gelişmiş senaryolarla çalışmanızı sağladığını göreceksiniz. Ağaçları ifade etmek için inanılmaz bir güç var.

Diğer ortamlarda yürütmek için algoritmaları çevirmeye ek olarak, ifade ağaçları yürütmeden önce kodu denetleyen algoritmalar yazmayı kolaylaştırmak için kullanılabilir. Bağımsız değişkenleri ifade olan bir yöntem yazabilir ve kodu yürütmeden önce bu ifadeleri inceleyebilirsiniz. İfade Ağacı kodun tam bir temsilidir: herhangi bir alt ifadenin değerlerini görebilirsiniz.
Yöntem ve özellik adlarını görebilirsiniz. Sabit ifadelerin değerini görebilirsiniz.
Ayrıca bir ifade ağacını yürütülebilir bir temsilciye dönüştürebilir ve kodu yürütebilirsiniz.

İfade Ağaçları için API'ler, hemen hemen her geçerli kod yapısını temsil eden ağaçlar oluşturmanıza olanak tanır. Ancak, bazı şeyleri mümkün olduğunca basit tutmak için, bazı C# deyimleri bir ifade ağacında oluşturulamaz. Bir örnek asynchronous ifadeler `async` (ve `await` anahtar kelimeler kullanarak). Gereksinimleriniz eşzamanlı algoritmalar gerektiriyorsa, derleyici desteğine `Task` güvenmek yerine nesneleri doğrudan işlemeniz gerekir. Başka bir döngüler oluşturma. Genellikle, bunları , , `for` `foreach` `while` veya `do` döngüler kullanarak oluşturursunuz. [Bu serinin ilerleyen saatlerinde](expression-trees-building.md)göreceğiniz gibi, ifade ağaçları için API'ler döngüyü yineleyen ifadeleri ve `break` `continue` ifadeleri içeren tek bir döngü ifadesini destekler.

Yapamayacağınız tek şey bir ifade ağacını değiştirmektir.  İfade Ağaçları değişmez veri yapılarıdır. Bir ifade ağacını mutasyona uğratmak (değiştirmek) istiyorsanız, özgün bir kopyasını, ancak istediğiniz değişikliklerle birlikte yeni bir ağaç oluşturmanız gerekir.

[Sonraki -- İfade Ağaçlarını Destekleyen Çerçeve Türleri](expression-classes.md)
