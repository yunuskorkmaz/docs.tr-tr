---
title: Varsayılan arabirim yöntemlerini kullanarak mixin türleri oluşturma
description: Varsayılan arabirim üyelerini kullanarak uygulayıcılar için isteğe bağlı varsayılan uygulamalara sahip arabirimleri genişletebilirsiniz.
ms.technology: csharp-advanced-concepts
ms.date: 10/04/2019
ms.openlocfilehash: ee0536ef51f9bea3e6851be23cc19fa28cc6916b
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134369"
---
# <a name="tutorial-mix-functionality-in-when-creating-classes-using-interfaces-with-default-interface-methods"></a>Öğretici: Varsayılan arabirim yöntemleriyle arabirimleri kullanarak sınıf oluştururken işlevselliği karıştırın

.NET Core 3.0'daki C# 8.0 ile başlayarak, bir arabirimin üyesini beyan ettiğinizde bir uygulama tanımlayabilirsiniz. Bu özellik, arabirimlerde bildirilen özellikler için varsayılan uygulamaları tanımlayabileceğiniz yeni özellikler sağlar. Sınıflar işlevselliği ne zaman geçersiz kılacaklarını, varsayılan işlevselliği ne zaman kullanacaklarını ve ayrı özellikler için destek bildirmeyecekleri zaman ları seçebilirler.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> * Ayrık özellikleri açıklayan uygulamalarla arabirimler oluşturun.
> * Varsayılan uygulamaları kullanan sınıflar oluşturun.
> * Varsayılan uygulamaların bazılarını veya tümünün geçersiz kılındığını belirten sınıflar oluşturun.

## <a name="prerequisites"></a>Ön koşullar

C# 8.0 derleyicisi de dahil olmak üzere .NET Core'u çalıştıracak şekilde makinenizi ayarlamanız gerekir. C# 8.0 derleyicisi [Visual Studio 2019 sürümü 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)veya [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) veya daha sonra ile başlayarak kullanılabilir.

## <a name="limitations-of-extension-methods"></a>Uzatma yöntemlerinin sınırlamaları

Arabirimin bir parçası olarak görünen davranışı uygulamanın bir yolu, varsayılan davranışı sağlayan [uzantı yöntemlerini](../programming-guide/classes-and-structs/extension-methods.md) tanımlamaktır. Arabirimler, bu arabirimi uygulayan herhangi bir sınıf için daha büyük bir yüzey alanı sağlarken en az üye kümesini bildirir. Örneğin, herhangi bir <xref:System.Linq.Enumerable> dizinin LINQ sorgusunun kaynağı olmasını sağlayan uzantı yöntemleri.

Uzantı yöntemleri, bildirilen değişken türü kullanılarak derleme zamanında çözülür. Arabirimi uygulayan sınıflar, herhangi bir uzantı yöntemi için daha iyi bir uygulama sağlayabilir. Derleyicinin bu uygulamayı seçmesi için değişken bildirimleruygulama türüyle eşleşmelidir. Derleme zamanı türü arabirimle eşleştiğinde, yöntem çağrıları uzantı yöntemiyle çözülür. Uzantı yöntemleriyle ilgili bir diğer endişe, bu yöntemlere uzantı yöntemlerini içeren sınıfın erişilebildiği her yerde erişilebilir olmasıdır. Sınıflar, uzantı yöntemlerinde bildirilen özellikleri sağlamaları gerektiğini veya sağlamaması gerektiğini beyan edemez.

C# 8.0 ile başlayarak varsayılan uygulamaları arabirim yöntemleri olarak bildirebilirsiniz. Daha sonra, her sınıf varsayılan uygulamayı otomatik olarak kullanır. Daha iyi bir uygulama sağlayabilir herhangi bir sınıf daha iyi bir algoritma ile arabirim yöntemi tanımı geçersiz kılabilir. Bir anlamda, bu teknik [uzantı yöntemlerini](../programming-guide/classes-and-structs/extension-methods.md)nasıl kullanabileceğinize benzer.

Bu makalede, varsayılan arabirim uygulamalarının yeni senaryoları nasıl etkinleştireceğini öğreneceksiniz.

## <a name="design-the-application"></a>Uygulamayı tasarla

Bir ev otomasyonu uygulaması düşünün. Muhtemelen ışıklar ve göstergeler için boyunca kullanılabilir birçok farklı türleri var. Her ışık API'leri açıp kapatmak ve geçerli durumu bildirmek için desteklemelidir. Bazı ışıklar ve göstergeler şu gibi diğer özellikleri destekleyebilir:

- Işığı açın, sonra bir zamanlayıcıdan sonra kapatın.
- Işığı bir süre için yanıp sön.

Bu genişletilmiş özelliklerden bazıları, en az kümeyi destekleyen aygıtlarda taklit edilebilir. Bu, varsayılan bir uygulama sağlamaanlamına geldiğini gösterir. Yerleşik daha fazla özelliklere sahip olan aygıtlar için, aygıt yazılımı yerel yetenekleri kullanır. Diğer ışıklar için, arabirimi uygulamayı ve varsayılan uygulamayı kullanmayı seçebilirler.

Varsayılan arabirim üyeleri, bu senaryo için uzantı yöntemlerine göre daha iyi bir çözümdür. Sınıf yazarları hangi arabirimleri uygulamak için seçtiklerini denetleyebilir. Seçtikleri bu arabirimler yöntem olarak kullanılabilir. Buna ek olarak, varsayılan arabirim yöntemleri varsayılan olarak sanal olduğundan, yöntem gönderme her zaman sınıftaki uygulamayı seçer.

Bu farklılıkları göstermek için kodu oluşturalım.

## <a name="create-interfaces"></a>Arayüzler oluşturma

Tüm ışıklar için davranışı tanımlayan arabirimi oluşturarak başlayın:

[!code-csharp[Declare base interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetILightInterfaceV1)]

Temel bir havai aydınlatma fikstürü, aşağıdaki kodda gösterildiği gibi bu arabirimi uygulayabilir:

[!code-csharp[First overhead light](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetOverheadLightV1)]

Bu öğreticide, kod IoT aygıtlarını yönlendirmez, ancak konsola ileti ler yazarak bu etkinlikleri taklit eder. Evinizi otomatikleştirerek kodu keşfedebilirsiniz.

Ardından, bir zaman anından sonra otomatik olarak kapanabilen bir ışık için arabirimi tanımlayalım:

[!code-csharp[pure Timer interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetPureTimerInterface)]

Havai ışığa temel bir uygulama ekleyebilirsiniz, ancak daha iyi bir çözüm `virtual` varsayılan bir uygulama sağlamak için bu arabirim tanımını değiştirmektir:

[!code-csharp[Timer interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ITimerLight.cs?name=SnippetTimerLightFinal)]

Bu değişikliği ekleyerek, `OverheadLight` sınıf arabirimi için destek beyan ederek zamanlayıcı işlevini uygulayabilir:

```csharp
public class OverheadLight : ITimerLight { }
```

Farklı bir ışık türü daha gelişmiş bir protokolü destekleyebilir. Aşağıdaki kodda gösterildiği `TurnOnFor`gibi, kendi uygulamasını sağlayabilir:

[!code-csharp[Override the timer function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/HalogenLight.cs?name=SnippetHalogenLight)]

Sanal sınıf yöntemlerinin geçersiz kılınması `TurnOnFor` `HalogenLight` yerine, sınıftaki `override` bildirim anahtar sözcüğü kullanmaz.

## <a name="mix-and-match-capabilities"></a>Karıştırma ve eşleştirme özellikleri

Daha gelişmiş özellikler tanıttıkça varsayılan arabirim yöntemlerinin avantajları daha da netleşir. Arabirimleri kullanmak, yetenekleri karıştırmanızı ve eşleştirmenizi sağlar. Ayrıca, her sınıf yazarının varsayılan uygulama ile özel bir uygulama arasında seçim yapma olanağı sağlar. Yanıp sönen bir ışık için varsayılan uygulama içeren bir arabirim ekleyelim:

[!code-csharp[Define the blinking light interface](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/IBlinkingLight.cs?name=SnippetBlinkingLight)]

Varsayılan uygulama herhangi bir ışığın yanıp sönmesini sağlar. Genel akış ışığı varsayılan uygulamayı kullanarak hem zamanlayıcı hem de yanıp sönme özellikleri ekleyebilir:

[!code-csharp[Use the default blink function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/OverheadLight.cs?name=SnippetOverheadLight)]

Yeni bir ışık `LEDLight` türü, hem zamanlayıcı işlevini hem de doğrudan yanıp sönme işlevini destekler. Bu ışık stili hem `ITimerLight` `IBlinkingLight` arabirimleri hem de `Blink` arabirimleri uygular ve yöntemi geçersiz kılar:

[!code-csharp[Override the blink function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/LEDLight.cs?name=SnippetLEDLight)]

A, `ExtraFancyLight` yanıp sönen ve zamanlayıcı işlevlerini doğrudan destekleyebilir:

[!code-csharp[Override the blink and timer function](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ExtraFancyLight.cs?name=SnippetExtraFancyLight)]

Daha `HalogenLight` önce oluşturduğunuz yanıp sönme desteklemez. Bu nedenle, desteklenen `IBlinkingLight` arabirimler listesine eklemeyin.

## <a name="detect-the-light-types-using-pattern-matching"></a>Desen eşleştirmesini kullanarak ışık türlerini algılama

Sonra, biraz test kodu yazalım. Hangi arabirimleri desteklediğini inceleyerek Bir ışığın yeteneklerini belirlemek için C#'ın [desen eşleştirme](../pattern-matching.md) özelliğinden yararlanabilirsiniz.  Aşağıdaki yöntem, her ışığın desteklenen özelliklerini uygular:

[!code-csharp[Test a light's capabilities](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetTestLightFunctions)]

Yönteminizdeki `Main` aşağıdaki kod, sırayla her ışık türünü oluşturur ve bu ışığı sınar:

[!code-csharp[Test a light's capabilities](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetMainMethod)]

## <a name="how-the-compiler-determines-best-implementation"></a>Derleyici en iyi uygulamayı nasıl belirler?

Bu senaryo, herhangi bir uygulama olmadan bir temel arabirim gösterir. `ILight` Arabirime bir yöntem eklemek yeni karmaşıklıklar sunar. Varsayılan arabirim yöntemlerini yöneten dil kuralları, birden çok türetilmiş arabirim uygulayan somut sınıflar üzerindeki etkiyi en aza indirir. Orijinal arabirimi, kullanımını nasıl değiştirdiğini göstermek için yeni bir yöntemle geliştirelim. Her gösterge ışığı, güç durumunu numaralandırılmış bir değer olarak bildirebilir:

[!code-csharp[Enumeration for power status](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetPowerStatus)]

Varsayılan uygulama hiçbir güç varsayar:

[!code-csharp[Report a default power status](~/samples/snippets/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetILightInterface)]

Bu `ExtraFancyLight` değişiklikler, `ILight` arabirim ve türetilmiş arabirimler için destek beyan `ITimerLight` `IBlinkingLight`etse de, temiz bir şekilde derlenir ve . `ILight` Arabirimde bildirilen yalnızca bir "en yakın" uygulama vardır. Geçersiz kılma bildiren herhangi bir sınıf "en yakın" uygulama olur. Önceki sınıflarda, diğer türemiş arabirimlerin üyelerini geçersiz kıldıran örnekler gördünüz.

Birden çok türetilmiş arabirimde aynı yöntemi geçersiz kılmaktan kaçının. Bunu yapmak, bir sınıf her iki türemiş arabirimi de uyguladığında belirsiz bir yöntem çağrısı oluşturur. Derleyici tek bir daha iyi yöntem seçemez, bu nedenle hata sorunu yayınlar. Örneğin, hem bir `IBlinkingLight` `ITimerLight` geçersiz kılma uygulanan `PowerStatus`ve `OverheadLight` uygulanan, daha belirli bir geçersiz kılma sağlamak gerekir. Aksi takdirde, derleyici iki türetilmiş arabirimdeki uygulamalar arasında seçim yapamaz. Genellikle arabirim tanımlarını küçük tutarak ve tek bir özelliğe odaklanarak bu durumu önleyebilirsiniz. Bu senaryoda, bir ışığın her yeteneği kendi arabirimidir; birden çok arabirim yalnızca sınıflar tarafından devralınır.

Bu örnek, sınıflara karıştırılabilecek ayrı özellikler tanımlayabileceğiniz bir senaryo gösterir. Desteklenen işlevleri, bir sınıf destekleyen arabirimler bildirerek herhangi bir desteklenen işlevselliği bildirirsiniz. Sanal varsayılan arabirim yöntemlerinin kullanımı, sınıfların arabirim yöntemlerinin herhangi biri veya tümü için farklı bir uygulama kullanmasını veya tanımlamasını sağlar. Bu dil yeteneği, oluşturmakta olduğunuz gerçek dünya sistemlerini modellemek için yeni yollar sağlar. Varsayılan arabirim yöntemleri, bu özelliklerin sanal uygulamalarını kullanarak farklı özellikleri karıştırıp eşleştirebilecek ilgili sınıfları ifade etmek için daha net bir yol sağlar.
