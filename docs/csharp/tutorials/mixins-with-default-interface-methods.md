---
title: Varsayılan arabirim yöntemlerini kullanarak Mixin türleri oluşturma
description: Varsayılan arabirim üyelerini kullanarak, uygulamaları uygulayıcılar için isteğe bağlı varsayılan uygulamalarla genişletebilirsiniz.
ms.technology: csharp-advanced-concepts
ms.date: 10/04/2019
ms.openlocfilehash: 0095d76eadfe0c6a1b30bf8a0c5000509f5e1bf9
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396705"
---
# <a name="tutorial-mix-functionality-in-when-creating-classes-using-interfaces-with-default-interface-methods"></a>Öğretici: varsayılan arabirim yöntemleriyle arabirimleri kullanarak sınıf oluştururken içindeki işlevselliği karıştırma

.NET Core 3,0 ' de C# 8,0 ' den başlayarak bir arabirimin üyesini bildirdiğinizde bir uygulama tanımlayabilirsiniz. Bu özellik, arabirimlerde belirtilen özellikler için varsayılan uygulamaları tanımlayabileceğiniz yeni yetenekler sağlar. Sınıflar işlevin ne zaman geçersiz kılınacağını, varsayılan işlevselliğin ne zaman kullanılacağını ve ayrık özellikler için ne zaman destek bildirelemeyeceğini seçebilir.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> * Ayrık özellikleri tanımlayan uygulamalarla arabirim oluşturun.
> * Varsayılan uygulamaları kullanan sınıflar oluşturun.
> * Varsayılan uygulamaların bazılarını veya tümünü geçersiz kılan sınıflar oluşturun.

## <a name="prerequisites"></a>Ön koşullar

C# 8,0 derleyicisi dahil olmak üzere makinenizi .NET Core çalıştıracak şekilde ayarlamanız gerekir. C# 8,0 derleyicisi, [Visual Studio 2019 sürüm 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)veya [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download/dotnet-core) veya sonraki sürümleriyle başlayarak kullanılabilir.

## <a name="limitations-of-extension-methods"></a>Uzantı yöntemlerinin sınırlamaları

Bir arabirimin parçası olarak görünen davranışı uygulayabileceğiniz yollardan biri, varsayılan davranışı sağlayan [Uzantı yöntemlerini](../programming-guide/classes-and-structs/extension-methods.md) tanımlamaktır. Arabirimler, bu arabirimi uygulayan her sınıf için daha büyük bir yüzey alanı sağlarken, minimum üye kümesini bildirir. Örneğin, içindeki uzantı yöntemleri <xref:System.Linq.Enumerable> BIR LINQ sorgusunun kaynağı olmak üzere herhangi bir sıra için uygulama sağlar.

Uzantı yöntemleri, değişkenin belirtilen türü kullanılarak derleme zamanında çözümlenir. Arabirimini uygulayan sınıflar, herhangi bir genişletme yöntemi için daha iyi bir uygulama sağlayabilir. Derleyicinin bu uygulamayı seçmesini sağlamak için değişken bildirimlerinin uygulama türüyle eşleşmesi gerekir. Derleme zamanı türü arabirimiyle eşleştiğinde, Yöntem çağrıları uzantı yöntemine çözümlenir. Uzantı yöntemleriyle ilgili başka bir sorun da bu yöntemlere uzantı yöntemlerini içeren sınıfın erişilebilir olduğu her yerde erişilebilir. Sınıflar, uzantı yöntemlerinde belirtilen özellikleri sağlamalıdır veya sağlamamaları gerekip gerekmediğini bildiremez.

C# 8,0 ' den başlayarak varsayılan uygulamaları arabirim yöntemleri olarak bildirebilirsiniz. Ardından, her sınıf otomatik olarak varsayılan uygulamayı kullanır. Daha iyi bir uygulama sağlayabilen herhangi bir sınıf arabirim yöntemi tanımını daha iyi bir algoritmayla geçersiz kılabilir. Bu teknik, tek bir anlamda, [Uzantı yöntemlerini](../programming-guide/classes-and-structs/extension-methods.md)nasıl kullanabileceğiniz ile benzer şekilde ses olarak da kullanabilir.

Bu makalede, varsayılan arabirim uygulamalarının yeni senaryoları nasıl etkinleştirdiklerini öğreneceksiniz.

## <a name="design-the-application"></a>Uygulamayı tasarlama

Bir giriş otomasyon uygulaması düşünün. Belki de şirket genelinde kullanılabilecek birçok farklı ışık ve gösterge türü vardır. Her ışığın açıp kapatmak ve geçerli durumu raporlamak için API 'Leri desteklemesi gerekir. Bazı ışıklar ve göstergeler, gibi diğer özellikleri destekleyebilir:

- Işığı açın, sonra bir zamanlayıcının ardından devre dışı bırakın.
- Bir süre için ışığı yanıp söndürme.

Bu genişletilmiş yeteneklerin bazıları, en az kümeyi destekleyen cihazlarda öykünüyolabilir. Bu, varsayılan bir uygulama sağlamayı gösterir. İçinde daha fazla özelliğe yerleşik olan cihazlar için, cihaz yazılımı yerel özellikleri kullanır. Diğer ışıklar için, arabirimi uygulamayı ve varsayılan uygulamayı kullanmayı seçebilirler.

Varsayılan arabirim üyeleri bu senaryoya uzantı yöntemlerinden daha iyi bir çözümdür. Sınıf yazarları, hangi arabirimlerin uygulanacağını seçebilecekleri denetleyebilir. Tercih ettikleri arabirimler yöntemler olarak kullanılabilir. Ek olarak, varsayılan arabirim yöntemleri varsayılan olarak sanal olduğundan, yöntemi dağıtım her zaman sınıfındaki uygulamayı seçer.

Bu farklılıkları göstermek için kodu oluşturalım.

## <a name="create-interfaces"></a>Arabirim oluşturma

Tüm ışıklarının davranışını tanımlayan arabirimi oluşturarak başlayın:

[!code-csharp[Declare base interface](./snippets/mixins-with-default-interface-methods/UnusedExampleCode.cs?name=SnippetILightInterfaceV1)]

Temel bir ek yük hafif armakodu, aşağıdaki kodda gösterildiği gibi bu arabirimi uygulayabilir:

[!code-csharp[First overhead light](./snippets/mixins-with-default-interface-methods/UnusedExampleCode.cs?name=SnippetOverheadLightV1)]

Bu öğreticide, kod IoT cihazlarını sürücüden almaz, ancak konsola ileti yazarak bu etkinliklere öykünür. Evinizi otomatikleştirmeden kodu keşfedebilirsiniz.

Daha sonra, bir zaman aşımından sonra otomatik olarak kapatıbir ışığın arabirimini tanımlayalim:

[!code-csharp[pure Timer interface](./snippets/mixins-with-default-interface-methods/UnusedExampleCode.cs?name=SnippetPureTimerInterface)]

Ek yük ışığıyla temel bir uygulama ekleyebilirsiniz, ancak daha iyi bir çözüm, bu arabirim tanımını varsayılan bir uygulama sağlamak üzere değiştirmektir `virtual` :

[!code-csharp[Timer interface](./snippets/mixins-with-default-interface-methods/ITimerLight.cs?name=SnippetTimerLightFinal)]

Bu değişiklik eklendiğinde `OverheadLight` sınıf, arabirim için destek bildirerek Zamanlayıcı işlevini uygulayabilir:

```csharp
public class OverheadLight : ITimerLight { }
```

Farklı bir ışık türü, daha karmaşık bir protokolü destekleyebilir. `TurnOnFor`Aşağıdaki kodda gösterildiği gibi, için kendi uygulamasını sağlayabilir:

[!code-csharp[Override the timer function](./snippets/mixins-with-default-interface-methods/HalogenLight.cs?name=SnippetHalogenLight)]

Sanal Sınıf yöntemlerinin geçersiz kılınmasından farklı olarak, `TurnOnFor` sınıfındaki bildirimi `HalogenLight` `override` anahtar sözcüğünü kullanmaz.

## <a name="mix-and-match-capabilities"></a>Karıştırma ve eşleştirme özellikleri

Daha gelişmiş özellikleri tanıtdığınızda varsayılan arabirim yöntemlerinin avantajları daha net hale gelir. Arabirimleri kullanmak, özellikleri karıştırmanızı ve eşleştirmeye olanak sağlar. Ayrıca, her sınıf yazarının varsayılan uygulama ve özel bir uygulama arasında seçim yapmasına olanak sağlar. Yanıp sönen bir ışık için varsayılan uygulamayla bir arabirim ekleyelim:

[!code-csharp[Define the blinking light interface](./snippets/mixins-with-default-interface-methods/IBlinkingLight.cs?name=SnippetBlinkingLight)]

Varsayılan uygulama herhangi bir ışığın yanıp sönmesini sağlar. Ek yük ışığı, varsayılan uygulamayı kullanarak hem Zamanlayıcı hem de yanıp sönme özellikleri ekleyebilir:

[!code-csharp[Use the default blink function](./snippets/mixins-with-default-interface-methods/OverheadLight.cs?name=SnippetOverheadLight)]

Yeni bir ışık türü, `LEDLight` doğrudan Zamanlayıcı işlevini ve BLINK işlevini destekler. Bu ışık stili hem hem de `ITimerLight` `IBlinkingLight` arabirimlerini uygular ve yöntemi geçersiz kılar `Blink` :

[!code-csharp[Override the blink function](./snippets/mixins-with-default-interface-methods/LEDLight.cs?name=SnippetLEDLight)]

`ExtraFancyLight`, Doğrudan yanıp sönme ve süreölçer işlevlerini destekleyebilir:

[!code-csharp[Override the blink and timer function](./snippets/mixins-with-default-interface-methods/ExtraFancyLight.cs?name=SnippetExtraFancyLight)]

`HalogenLight`Daha önce oluşturduğunuz bu, yanıp sönmesini desteklememektedir. Bu nedenle, öğesini `IBlinkingLight` desteklenen arabirimlerin listesine eklemeyin.

## <a name="detect-the-light-types-using-pattern-matching"></a>Model eşleştirmeyi kullanarak ışık türlerini Algıla

Daha sonra bazı test kodu yazalım. Hangi arabirimlerin destekleyeceğini inceleyerek ışığın yeteneklerini anlamak için C# ' nin [model eşleme](../pattern-matching.md) özelliğinden yararlanabilirsiniz.  Aşağıdaki yöntem her bir ışığın desteklenen yeteneklerini alıştırmaları:

[!code-csharp[Test a light's capabilities](./snippets/mixins-with-default-interface-methods/Program.cs?name=SnippetTestLightFunctions)]

Yönteminizin aşağıdaki kodu `Main` sırayla her ışık türünü oluşturur ve bu ışığı sınar:

[!code-csharp[Test a light's capabilities](./snippets/mixins-with-default-interface-methods/Program.cs?name=SnippetMainMethod)]

## <a name="how-the-compiler-determines-best-implementation"></a>Derleyicinin en iyi uygulamayı nasıl belirlediği

Bu senaryo, herhangi bir uygulama olmadan temel bir arabirim gösterir. Arabirimine bir yöntemi eklemek `ILight` Yeni karmaşıklıkları tanıtır. Varsayılan arabirim yöntemlerini yöneten dil kuralları, birden fazla türetilmiş arabirimi uygulayan somut sınıflarda etkiyi en aza indirir. Bunun nasıl kullanıldığını göstermek için yeni bir yöntemi olan özgün arabirimi geliştirelim. Her gösterge ışığı, güç durumunu numaralandırılmış bir değer olarak rapor edebilir:

[!code-csharp[Enumeration for power status](./snippets/mixins-with-default-interface-methods/ILight.cs?name=SnippetPowerStatus)]

Varsayılan uygulama hiçbir güç içermez:

[!code-csharp[Report a default power status](./snippets/mixins-with-default-interface-methods/ILight.cs?name=SnippetILightInterface)]

Bu değişiklikler, `ExtraFancyLight` `ILight` arabirim ve hem türetilmiş arabirimler hem de ve için destek bildirse de düzgün şekilde `ITimerLight` derlenir `IBlinkingLight` . Arabiriminde belirtilen yalnızca bir "en yakın" uygulama vardır `ILight` . Bir geçersiz kılma belirten herhangi bir sınıf "en yakın" uygulama haline gelir. Diğer türetilmiş arabirimlerin üyelerini içeren önceki sınıflarda örnekleri gördünüz.

Birden çok türetilmiş arabirimde aynı yöntemi geçersiz kılmaktan kaçının. Bunun yapılması, bir sınıf hem türetilmiş arabirimleri her uygularsa belirsiz bir yöntem çağrısı oluşturur. Derleyici bir hata verecek şekilde tek bir daha iyi yöntem seçemiyor. Örneğin, her ikisi de için `IBlinkingLight` `ITimerLight` bir geçersiz kılma uyguladıysanız, öğesinin `PowerStatus` `OverheadLight` daha belirli bir geçersiz kılma sağlaması gerekir. Aksi halde, derleyici iki türetilmiş arabirimde uygulamalar arasında seçim yapamıyor. Bu durum genellikle, arabirim tanımlarını küçük tutarak tek bir özelliğe odaklanarak önleyebilirsiniz. Bu senaryoda, bir ışığın her özelliği kendi arayüzüdür; birden çok arabirim yalnızca sınıflar tarafından devralınır.

Bu örnekte, sınıflara karışabilir ayrık Özellikler tanımlayabileceğiniz bir senaryo gösterilmektedir. Bir sınıfın desteklediği arabirimleri bildirerek, desteklenen herhangi bir işlev kümesini bildirirsiniz. Sanal varsayılan arabirim yöntemlerinin kullanımı, sınıfların herhangi bir veya tüm arabirim yöntemleri için farklı bir uygulama kullanmasını sağlar veya tanımlar. Bu dil özelliği, oluşturmakta olduğunuz gerçek dünya sistemlerini modellemek için yeni yollar sağlar. Varsayılan arabirim yöntemleri, bu özelliklerin sanal uygulamalarını kullanarak farklı özelliklerle karıştırabilecek ve eşleşebilecek ilgili sınıfları hızlı bir şekilde ifade etmenin daha net bir yolunu sağlar.
