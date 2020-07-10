---
title: C# 7.1 Yenilikleri
description: C# 7,1 ' deki yeni özelliklere genel bakış.
ms.date: 04/09/2019
ms.openlocfilehash: fe6e49eb01e24a27bc7970900c05150378ab194a
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174776"
---
# <a name="whats-new-in-c-71"></a>C# 7.1 Yenilikleri

C# 7,1, C# dilinin ilk noktası sürümüdür. Dil için artan bir sürüm temposunda işaretler. Yeni özellikleri daha erken kullanabilirsiniz, her yeni özellik için idealdir. C# 7,1, derleyiciyi belirtilen dilin sürümüyle eşleşecek şekilde yapılandırma yeteneğini ekler. Bu sayede, dil sürümlerini yükseltme kararına araçları yükseltme kararını ayırmanızı sağlayabilirsiniz.

C# 7,1, [dil sürümü seçimi](../language-reference/configure-language-version.md) yapılandırma öğesini, üç yeni dil özelliğini ve yeni derleyici davranışını ekler.

Bu sürümdeki yeni dil özellikleri şunlardır:

- [`async``Main`yöntemi](#async-main)
  - Bir uygulama için giriş noktası değiştiriciye sahip olabilir `async` .
- [`default`değişmez değer ifadeleri](#default-literal-expressions)
  - Hedef türü çıkarsanamıyor varsayılan değer ifadelerinde varsayılan değişmez ifadeleri kullanabilirsiniz.
- [Gösterilen demet öğesi adları](#inferred-tuple-element-names)
  - Kayıt düzeni öğelerinin adları, birçok durumda demet başlatmasıyla çıkarsanamıyor.
- [Genel tür parametrelerinde model eşleştirme](#pattern-matching-on-generic-type-parameters)
  - Türü genel bir tür parametresi olan değişkenlerde model eşleşme ifadeleri kullanabilirsiniz.

Son olarak, derleyici iki seçeneğe sahiptir `-refout` ve `-refonly` Bu, [Başvuru derleme üretimini](#reference-assembly-generation)denetler.

En son özellikleri bir nokta sürümünde kullanmak için, [Derleyici dil sürümünü yapılandırmanız](../language-reference/configure-language-version.md) ve sürümü seçmeniz gerekir.

Bu makalenin geri kalanında her özelliğe bir genel bakış sunulmaktadır. Her bir özellik için, arkasında yatan bir düşünme olduğunu öğrenirsiniz. Söz dizimini öğrenirsiniz. Genel aracı kullanarak ortamınızdaki bu özellikleri keşfedebilirsiniz `dotnet try` :

1. [DotNet-TRY](https://github.com/dotnet/try/blob/master/README.md#setup) küresel aracını yükler.
1. [DotNet/TRY-Samples](https://github.com/dotnet/try-samples) deposunu kopyalayın.
1. *TRY-Samples* deposu için geçerli dizini *csharp7* alt dizinine ayarlayın.
1. Şu komutu çalıştırın: `dotnet try`.

## <a name="async-main"></a>Zaman uyumsuz ana

*Zaman uyumsuz Main* yöntemi, `await` yöntekinizdeki kullanmanıza olanak sağlar `Main` .
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

Programınız çıkış kodu döndürmezse, şunu `Main` döndüren bir yöntem bildirebilirsiniz <xref:System.Threading.Tasks.Task> :

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

Bu özellik C# 7,0 ' de tanıtılan tanımlama grupları özelliği için küçük bir geliştirmedir. Bir tanımlama grubunu başlattığınızda, atamanın sağ tarafında kullanılan değişkenler demet öğeleri için istediğiniz adlarla aynıdır:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

Kayıt düzeni öğelerinin adları C# 7,1 ' de kayıt kümesini başlatmak için kullanılan değişkenlerden çıkarsanamıyor:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

[Demet türleri](../language-reference/builtin-types/value-tuples.md) makalesinde bu özellik hakkında daha fazla bilgi edinebilirsiniz.

## <a name="pattern-matching-on-generic-type-parameters"></a>Genel tür parametrelerinde model eşleştirme

C# 7,1 ile başlayarak, `is` ve `switch` tür deseninin model ifadesi bir genel tür parametresinin türüne sahip olabilir. Bu, ya da türünde olabilecek türler denetlenirken `struct` `class` ve kutulamayı önlemek istediğiniz durumlarda yararlı olabilir.

## <a name="reference-assembly-generation"></a>Başvuru derlemesi oluşturma

*Yalnızca başvuru derlemeler*üreten iki yeni derleyici seçeneği vardır: [-refout](../language-reference/compiler-options/refout-compiler-option.md) ve [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).
Bağlantılı makaleler, bu seçenekleri ve başvuru derlemelerini daha ayrıntılı bir şekilde açıklamaktadır.
