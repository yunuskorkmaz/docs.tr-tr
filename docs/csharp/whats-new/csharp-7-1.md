---
title: İçindeki yenilikler C# 7.1
description: İçinde yeni özelliklere genel bakış C# 7.1.
ms.date: 04/09/2019
ms.openlocfilehash: c79c8576f9cbbd921ebf30bd84ee5a817d6dc6e7
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480969"
---
# <a name="whats-new-in-c-71"></a>İçindeki yenilikler C# 7.1

C#ilk noktası sürüm 7.1 olan C# dili. Bunu bir daha yüksek bir yayın temposudur dil için işaretler. Her yeni özellik hazır olduğunda, yeni özellikleri daha çabuk, ideal olarak kullanabilirsiniz. C#Derleyicinin, belirtilen bir dile sürümüyle eşleşecek şekilde yapılandırma becerisi 7.1 ekler. Dil sürümleri yükseltme kararı araçları yükseltme kararı ayırmanıza olanak sağlar.

C#7.1 ekler [dil sürüm seçimi](../language-reference/configure-language-version.md) yapılandırma öğesi, üç yeni dil özellikleri ve yeni derleyici davranışı.

Bu sürümdeki yeni diz özellikleri şunlardır:

* [`async` `Main` yöntemi](#async-main)
  - Bir uygulama için giriş noktası `async` değiştiricisi.
* [`default` değişmez ifadeleri](#default-literal-expressions)
  - Hedef türü çıkarımı yapılan varsayılan değer ifadeleri toplama varsayılan sabit değer ifadeleri kullanabilirsiniz.
* [Çıkarsanan demet öğesi adları](#inferred-tuple-element-names)
  - Demet öğelerinin adlarını, çoğu durumda demet başlatma içinden gösterilen.
* [Genel tür parametrelerinde desen](#pattern-matching-on-generic-type-parameters)
  - Genel tür parametresi türü olan değişkenlerde deseni eşleşme ifadeleri kullanabilirsiniz.

Son olarak, derleyici iki seçeneğe sahiptir `/refout` ve `/refonly` denetleyen [başvuru bütünleştirilmiş kod oluşturmayı](#reference-assembly-generation).

Bir nokta sürümde en son özellikleri kullanmak için yapmanız [derleyici dil sürüm yapılandırma](../language-reference/configure-language-version.md) ve sürüm seçin.

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

Oluşturan iki yeni derleyici seçenek *yalnızca başvuru derlemeleri*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) ve [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).
Bağlantısı verilen makalelerden Bu seçenekler ve daha ayrıntılı başvuru bütünleştirilmiş kodları açıklanmaktadır.
