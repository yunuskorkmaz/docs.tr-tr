---
title: C# 7.1 Yenilikleri
description: C# 7.1'deki yeni özelliklere genel bakış.
ms.date: 04/09/2019
ms.openlocfilehash: 5d2d6f51b6422f5b4db5c6bd275b5ffce1f695f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399709"
---
# <a name="whats-new-in-c-71"></a>C# 7.1 Yenilikleri

C# 7.1, C# dilinin ilk noktasıdır. Bu dil için artan bir sürüm cadence işaretler. Yeni özellikleri, ideal olarak her yeni özellik hazır olduğunda daha erken kullanabilirsiniz. C# 7.1, derleyiciyi dilin belirli bir sürümüyle eşleşecek şekilde yapılandırma olanağı ekler. Bu, araçları yükseltme kararını dil sürümlerini yükseltme kararından ayırmanızı sağlar.

C# 7.1 [dil sürümü seçimi](../language-reference/configure-language-version.md) yapılandırma öğesi, üç yeni dil özellikleri ve yeni derleyici davranışı ekler.

Bu sürümdeki yeni dil özellikleri şunlardır:

- [`async``Main` yöntem](#async-main)
  - Bir uygulama için giriş noktası `async` değiştirici olabilir.
- [`default`gerçek ifadeler](#default-literal-expressions)
  - Varsayılan değer ifadelerinde varsayılan gerçek ifadeleri, hedef türü çıkarılabilirken kullanabilirsiniz.
- [Çıkarılan tuple öğesi adları](#inferred-tuple-element-names)
  - Tuple elemanlarının adları birçok durumda tuple başlatma çıkarılabilir.
- [Genel tür parametreleri üzerinde desen eşleştirme](#pattern-matching-on-generic-type-parameters)
  - Türü genel bir tür parametresi olan değişkenlerde desen eşleştirme ifadeleri kullanabilirsiniz.

Son olarak, derleyici `-refout` iki `-refonly` seçenek vardır ve bu kontrol [referans derleme nesil.](#reference-assembly-generation)

Bir nokta sürümündeki en son özellikleri kullanmak için [derleyici dili sürümünü yapılandırmanız](../language-reference/configure-language-version.md) ve sürümü seçmeniz gerekir.

Bu makalenin geri kalanı her özelliğin genel bir özetini sağlar. Her özellik için, bunun arkasındaki mantığı öğreneceksiniz. Sözdizimini öğreneceksin. `dotnet try` Bu özellikleri ortamınızda genel aracı kullanarak keşfedebilirsiniz:

1. [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global aracını yükleyin.
1. [Dotnet/try-samples](https://github.com/dotnet/try-samples) deposunu klonla.
1. *Deneme örnekleri* deposu için geçerli dizini *csharp7* alt dizinine ayarlayın.
1. `dotnet try` öğesini çalıştırın.

## <a name="async-main"></a>Async ana

Async *ana* yöntemi yönteminizde `await` `Main` kullanmanıza olanak sağlar.
Daha önce yazmanız gerekir:

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

Programınız bir çıkış kodu döndürmüyorsa, `Main` bir yöntem <xref:System.Threading.Tasks.Task>bildirebilirsiniz:

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

Programlama kılavuzundaki [async ana](../programming-guide/main-and-command-args/index.md) makalesinde ayrıntılar hakkında daha fazla bilgi edinebilirsiniz.

## <a name="default-literal-expressions"></a>Varsayılan gerçek ifadeler

Varsayılan gerçek ifadeler varsayılan değer ifadeleri için bir geliştirme vardır.
Bu ifadeler varsayılan değeriçin bir değişken ilerler. Daha önce yazacağınız yer:

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

Şimdi başbaşlatmanın sağ tarafındaki türü atlayabilirsiniz:

```csharp
Func<string, bool> whereClause = default;
```

Daha fazla bilgi için varsayılan [işleç](../language-reference/operators/default.md) makalesinin [varsayılan gerçek](../language-reference/operators/default.md#default-literal) bölümüne bakın.

## <a name="inferred-tuple-element-names"></a>Çıkarılan tuple öğesi adları

Bu özellik, C# 7.0'da tanıtılan tuples özelliğine küçük bir geliştirmedir. Çoğu zaman bir tuple'ı başharflediğinizde, atamanın sağ tarafı için kullanılan değişkenler, tuple öğeleri için istediğiniz adlarla aynıdır:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

Tuple elemanlarının adları C# 7.1'deki tuple'ı initiallaştırmak için kullanılan değişkenlerden çıkarılabilir:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

Bu özellik hakkında daha fazla bilgi için [Tuples](../tuples.md) makalesinde bulabilirsiniz.

## <a name="pattern-matching-on-generic-type-parameters"></a>Genel tür parametreleri üzerinde desen eşleştirme

C# 7.1 ile başlayarak, `is` desen `switch` ifadesi ve tür deseni genel bir tür parametresi türüne sahip olabilir. Bu, ya veya `struct` `class` tür olabilir türleri denetler ve kutulama önlemek istediğiniz de en yararlı olabilir.

## <a name="reference-assembly-generation"></a>Referans montaj üretimi

*Yalnızca referans derlemeleri*oluşturan iki yeni derleyici seçeneği vardır: [-refout](../language-reference/compiler-options/refout-compiler-option.md) ve [-refonly.](../language-reference/compiler-options/refonly-compiler-option.md)
Bağlantılı makaleler bu seçenekleri ve başvuru derlemelerini daha ayrıntılı olarak açıklar.
