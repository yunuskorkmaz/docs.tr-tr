---
title: İçindeki yenilikler C# 7.1
description: İçinde yeni özelliklere genel bakış C# 7.1.
ms.date: 04/09/2019
ms.openlocfilehash: a95111b6f217a2ca5c520c2d4d70efa0e23742f9
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347610"
---
# <a name="whats-new-in-c-71"></a>İçindeki yenilikler C# 7.1

C#ilk noktası sürüm 7.1 olan C# dili. Bunu bir daha yüksek bir yayın temposudur dil için işaretler. Her yeni özellik hazır olduğunda, yeni özellikleri daha çabuk, ideal olarak kullanabilirsiniz. C#Derleyicinin, belirtilen bir dile sürümüyle eşleşecek şekilde yapılandırma becerisi 7.1 ekler. Dil sürümleri yükseltme kararı araçları yükseltme kararı ayırmanıza olanak sağlar.

C#7.1 ekler [dil sürüm seçimi](../language-reference/configure-language-version.md) yapılandırma öğesi, üç yeni dil özellikleri ve yeni derleyici davranışı.

Bu sürümdeki yeni diz özellikleri şunlardır:

* [`async` `Main` Yöntemi](#async-main)
  - Bir uygulama için giriş noktası `async` değiştiricisi.
* [`default` değişmez ifadeleri](#default-literal-expressions)
  - Hedef türü çıkarımı yapılan varsayılan değer ifadeleri toplama varsayılan sabit değer ifadeleri kullanabilirsiniz.
* [Çıkarsanan demet öğesi adları](#inferred-tuple-element-names)
  - Demet öğelerinin adlarını, çoğu durumda demet başlatma içinden gösterilen.
* [Genel tür parametrelerinde desen](#pattern-matching-on-generic-type-parameters)
  - Genel tür parametresi türü olan değişkenlerde deseni eşleşme ifadeleri kullanabilirsiniz.

Son olarak, derleyici iki seçeneğe sahiptir `-refout` ve `-refonly` denetleyen [başvuru bütünleştirilmiş kod oluşturmayı](#reference-assembly-generation).

Bir nokta sürümde en son özellikleri kullanmak için yapmanız [derleyici dil sürüm yapılandırma](../language-reference/configure-language-version.md) ve sürüm seçin.

Bu makalenin geri kalanında her özelliğine genel bakış sağlar. Her bir özellik için ardındaki mantık öğreneceksiniz. Söz dizimi öğreneceksiniz. Bu özellikleri kullanarak ortamınıza keşfedebilirsiniz `dotnet try` genel aracı:

1. Yükleme [dotnet deneyin](https://github.com/dotnet/try/blob/master/README.md#setup) genel aracı.
1. Kopya [dotnet/try-samples](https://github.com/dotnet/try-samples) depo.
1. Geçerli dizin kümesine *csharp7* alt *deneyin-samples* depo.
1. `dotnet try`'i çalıştırın.

## <a name="async-main"></a>Zaman uyumsuz ana

Bir *async main* yöntemi kullanmanıza olanak sağlar `await` içinde `Main` yöntemi.
Daha önce yazmanız gerekir:

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

Artık yazabilirsiniz:

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

Programınız bir çıkış kodu, döndürmüyor, bildirebilirsiniz bir `Main` döndüren yöntem bir <xref:System.Threading.Tasks.Task>:

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

Daha fazla bilgi edinebilirsiniz hakkında ayrıntılar [async main](../programming-guide/main-and-command-args/index.md) Programlama Kılavuzu'nda makale.

## <a name="default-literal-expressions"></a>Varsayılan değişmez değer ifadeleri

Varsayılan değişmez ifadelerinde bir geliştirme için varsayılan değer ifadeleri toplama var.
Bu ifadeler, varsayılan değer için bir değişken başlatın. Daha önce burada yazmalısınız:

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

Sağ taraftaki başlatma türü artık atlayabilirsiniz:

```csharp
Func<string, bool> whereClause = default;
```

İçinde bu geliştirme hakkında daha fazla bilgi C# Programming Guide makale [varsayılan değer ifadeleri](../programming-guide/statements-expressions-operators/default-value-expressions.md).

Bu geliştirme ayrıca bazı ayrıştırma kurallarını değiştirir [default anahtar sözcüğü](../language-reference/keywords/default.md).

## <a name="inferred-tuple-element-names"></a>Çıkarsanan demet öğesi adları

Bu özellik de kullanıma sunulan diziler özellik için küçük bir geliştirmedir C# 7.0. Bir demet başlattığınızda birden çok kez dizi öğeleri için istediğiniz adları aynı atama için sağ tarafında kullanılan değişkenleri şunlardır:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

Değişkenlerden düzeninde başlatmak için kullanılan tanımlama grubu öğelerinin adlarını çıkarılan C# 7.1:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

' Deki bu özellik hakkında daha fazla bilgi [diziler](../tuples.md) makalesi.

## <a name="pattern-matching-on-generic-type-parameters"></a>Genel tür parametrelerinde desen

İle başlayarak C# 7.1, desen ifadesi `is` ve `switch` türü deseni bir genel tür parametre türüne sahip olabilir. Bu olabilir ya da denetimi türlerinden en yararlı olabilir `struct` veya `class` türleri ve kutulama önlemek istiyor.

## <a name="reference-assembly-generation"></a>Başvuru derleme oluşturma

Oluşturan iki yeni derleyici seçenek *yalnızca başvuru derlemeleri*: [- refonly](../language-reference/compiler-options/refout-compiler-option.md) ve [- refonly](../language-reference/compiler-options/refonly-compiler-option.md).
Bağlantısı verilen makalelerden Bu seçenekler ve daha ayrıntılı başvuru bütünleştirilmiş kodları açıklanmaktadır.
