---
title: C# 7.1 yenilikler nelerdir?
description: C# 7.1 içindeki yeni özelliklere genel bakış.
ms.date: 08/16/2017
ms.openlocfilehash: 565db102284424f9d8f6fa04ec9c74b52c9da0e6
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728660"
---
# <a name="whats-new-in-c-71"></a>C# 7.1 yenilikler nelerdir?

C# 7.1, C# dili için ilk noktası sürümüdür. Artan sürüm tempoyla dil için işaretler. Her yeni özellik hazır olduğunda, yeni özelliklerin daha erken, ideal olarak kullanabilirsiniz. C# 7.1 derleyici dil belirtilen sürümüyle eşleşecek şekilde yapılandırma olanağını ekler. Bu, dil sürümlerini yükseltmek için karar araçları yükseltmeye karar ayırmanıza olanak sağlar.

C# 7.1 ekler [dil sürümü seçimi](../language-reference/configure-language-version.md) yapılandırma öğesi, üç yeni dil özellikleri ve yeni derleyici davranışı.

Bu sürümdeki yeni diz özellikleri şunlardır:

* [`async` `Main` Yöntemi](#async-main)
  - Bir uygulama için giriş noktası olabilir `async` değiştiricisi.
* [`default` Sabit ifadeleri](#default-literal-expressions)
  - Hedef türü çıkarsanabileceği olduğunda, varsayılan değeri ifadelerinde varsayılan değişmez değer ifadeleri kullanabilirsiniz.
* [Çıkarsanan tanımlama grubu öğe adları](#inferred-tuple-element-names)
  - Başlığın öğeleri adlarını, çoğu durumda tanımlama grubu başlatılmasından çıkarsanabileceği.

Son olarak, derleyici iki seçenek vardır `/refout` ve `/refonly` denetleyen [başvuru derleme oluşturma](#reference-assembly-generation).

Noktası sürümündeki yeni özellikleri kullanmak için yapmanız [derleyici dil sürümünü yapılandırmanız](../language-reference/configure-language-version.md) ve sürümü seçin.

## <a name="async-main"></a>Zaman uyumsuz ana

Bir *zaman uyumsuz ana* yöntemi kullanmanıza olanak sağlayan `await` içinde `Main` yöntemi.
Daha önce yazma gerekir:

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

Şimdi yazabilirsiniz:

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

Programınızı bir çıkış kodu varsa döndürmez, bildirebilirsiniz bir `Main` döndüren yöntemi bir <xref:System.Threading.Tasks.Task>:

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

Daha fazla bilgiyi ayrıntılar hakkında [zaman uyumsuz ana](../programming-guide/main-and-command-args/index.md) konusu programlama kılavuzu.

## <a name="default-literal-expressions"></a>Varsayılan sabit ifadeleri

Varsayılan değişmez değer varsayılan değer ifadeleri yüklenene ifadelerini.
Bu ifade bir değişken varsayılan değere başlatır. Daha önce burada yazarsınız:

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

Sağ taraftaki başlatma türü artık atlayabilirsiniz:

```csharp
Func<string, bool> whereClause = default;
```

Üzerinde C# programlama kılavuzu konusundaki bu geliştirme hakkında daha fazla bilgiyi [varsayılan değeri ifadeleri](../programming-guide/statements-expressions-operators/default-value-expressions.md).

Bu geliştirme, ayrıca bazı ayrıştırma kurallarının değiştirir [default anahtar sözcüğü](../language-reference/keywords/default.md).

## <a name="inferred-tuple-element-names"></a>Çıkarsanan tanımlama grubu öğe adları

Bu özellik, C# 7. 0'sunulan diziler özellikle küçük bir yeniliktir. Bir tanımlama grubu başlattığınızda birçok kez atama için sağ tarafında kullanılan değişkenler tanımlama grubu öğeleri için istediğiniz adları aynıdır:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

Başlığın öğeleri adları C# 7.1 düzeninde başlatmak için kullanılan değişkenlerden çıkarsanabileceği:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

Bu özellik hakkında daha fazla bilgiyi [diziler](../tuples.md) konu.

## <a name="reference-assembly-generation"></a>Başvuru derleme oluşturma

Üreten iki yeni derleyici seçenekleri vardır *yalnızca başvuru derlemeleri*: [/refout](../language-reference/compiler-options/refout-compiler-option.md) ve [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).
Bağlantılı konulardan Bu seçenekler ve daha ayrıntılı başvuru derlemeleri açıklamaktadır.
