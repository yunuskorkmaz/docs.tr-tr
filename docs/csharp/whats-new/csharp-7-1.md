---
title: C# 7,1 sürümündeki yenilikler
description: C# 7,1 sürümündeki yeni özelliklere genel bakış.
ms.date: 04/09/2019
ms.openlocfilehash: 5d2d6f51b6422f5b4db5c6bd275b5ffce1f695f8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714588"
---
# <a name="whats-new-in-c-71"></a>C# 7,1 sürümündeki yenilikler

C#7,1, C# dilin ilk nokta sürümüdür. Dil için artan bir sürüm temposunda işaretler. Yeni özellikleri daha erken kullanabilirsiniz, her yeni özellik için idealdir. C#7,1, derleyiciyi belirtilen dilin sürümüyle eşleşecek şekilde yapılandırma yeteneğini ekler. Bu sayede, dil sürümlerini yükseltme kararına araçları yükseltme kararını ayırmanızı sağlayabilirsiniz.

C#7,1, [dil sürümü seçimi](../language-reference/configure-language-version.md) yapılandırma öğesini, üç yeni dil özelliğini ve yeni derleyici davranışını ekler.

Bu sürümdeki yeni dil özellikleri şunlardır:

- [`async` `Main` yöntemi](#async-main)
  - Bir uygulama için giriş noktası `async` değiştiriciye sahip olabilir.
- [`default` değişmez ifadesi](#default-literal-expressions)
  - Hedef türü çıkarsanamıyor varsayılan değer ifadelerinde varsayılan değişmez ifadeleri kullanabilirsiniz.
- [Gösterilen demet öğesi adları](#inferred-tuple-element-names)
  - Kayıt düzeni öğelerinin adları, birçok durumda demet başlatmasıyla çıkarsanamıyor.
- [Genel tür parametrelerinde model eşleştirme](#pattern-matching-on-generic-type-parameters)
  - Türü genel bir tür parametresi olan değişkenlerde model eşleşme ifadeleri kullanabilirsiniz.

Son olarak, derleyici `-refout` iki seçeneğe sahiptir ve bu denetim [Başvuru derleme üretimini](#reference-assembly-generation)`-refonly`.

En son özellikleri bir nokta sürümünde kullanmak için, [Derleyici dil sürümünü yapılandırmanız](../language-reference/configure-language-version.md) ve sürümü seçmeniz gerekir.

Bu makalenin geri kalanında her özelliğe bir genel bakış sunulmaktadır. Her bir özellik için, arkasında yatan bir düşünme olduğunu öğrenirsiniz. Söz dizimini öğrenirsiniz. Ortamınızdaki bu özellikleri, `dotnet try` genel aracını kullanarak inceleyebilirsiniz:

1. [DotNet-TRY](https://github.com/dotnet/try/blob/master/README.md#setup) küresel aracını yükler.
1. [DotNet/TRY-Samples](https://github.com/dotnet/try-samples) deposunu kopyalayın.
1. *TRY-Samples* deposu için geçerli dizini *csharp7* alt dizinine ayarlayın.
1. `dotnet try`'i çalıştırın.

## <a name="async-main"></a>Zaman uyumsuz ana

*Async Main* yöntemi `Main` yönteminde `await` kullanmanıza olanak sağlar.
Daha önce yazmanız gerekir:

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

Artık şunu yazabilirsiniz:

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

Programınız çıkış kodu döndürmezse, bir <xref:System.Threading.Tasks.Task>döndüren `Main` yöntemi bildirebilirsiniz:

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

Programlama kılavuzundaki [zaman uyumsuz ana](../programming-guide/main-and-command-args/index.md) makaledeki ayrıntılar hakkında daha fazla bilgi edinebilirsiniz.

## <a name="default-literal-expressions"></a>Varsayılan değişmez değer ifadeleri

Varsayılan değişmez değer ifadeleri varsayılan değer ifadelerine yönelik bir geliştirmedir.
Bu ifadeler varsayılan değere bir değişken başlatır. Daha önce yazdığınız yer:

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

Artık başlatmanın sağ tarafındaki türü atlayabilirsiniz:

```csharp
Func<string, bool> whereClause = default;
```

Daha fazla bilgi için [varsayılan işleç](../language-reference/operators/default.md) makalesinin [varsayılan değişmez değeri](../language-reference/operators/default.md#default-literal) bölümüne bakın.

## <a name="inferred-tuple-element-names"></a>Gösterilen demet öğesi adları

Bu özellik 7,0 ' de C# tanıtılan tanımlama grupları özelliği için küçük bir geliştirmedir. Bir tanımlama grubunu başlattığınızda, atamanın sağ tarafında kullanılan değişkenler demet öğeleri için istediğiniz adlarla aynıdır:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

Kayıt düzeni öğelerinin adları 7,1 içinde C# kayıt kümesini başlatmak için kullanılan değişkenlerden çıkarsanamıyor:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

Bu özellik hakkında daha fazla bilgi için [Tanımlama grupları](../tuples.md) makalesinde bulabilirsiniz.

## <a name="pattern-matching-on-generic-type-parameters"></a>Genel tür parametrelerinde model eşleştirme

7,1 ile C# başlayarak, `is` ve `switch` tür deseninin model ifadesi bir genel tür parametresinin türüne sahip olabilir. Bu, `struct` ya da `class` türler olabilecek türler denetlenirken ve kutulamayı önlemek istediğiniz durumlarda yararlı olabilir.

## <a name="reference-assembly-generation"></a>Başvuru derlemesi oluşturma

*Yalnızca başvuru derlemeler*üreten iki yeni derleyici seçeneği vardır: [-refout](../language-reference/compiler-options/refout-compiler-option.md) ve [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).
Bağlantılı makaleler, bu seçenekleri ve başvuru derlemelerini daha ayrıntılı bir şekilde açıklamaktadır.
