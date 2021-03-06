---
title: 'Son değişiklik: LastIndexOf, boş arama dizelerinin geliştirilmiş işlemesini içeriyor'
description: LastIndexOf ve ilgili API 'Lerin artık sıfır uzunluklu bir alt dizeyi ararken doğru değerleri döndürdüğü çekirdek .NET kitaplıklarında .NET 5 ' teki son değişiklik hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 9dc34300d867fe1bb9264494b3f2261bad2c1eea
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257433"
---
# <a name="lastindexof-has-improved-handling-of-empty-search-strings"></a><span data-ttu-id="fe7e5-103">LastIndexOf, boş arama dizelerinin yönetimini iyileştirmiştir</span><span class="sxs-lookup"><span data-stu-id="fe7e5-103">LastIndexOf has improved handling of empty search strings</span></span>

<span data-ttu-id="fe7e5-104"><xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> ve ilgili API 'Ler artık daha büyük bir dize içinde sıfır uzunluklu (veya sıfır uzunluklu eşdeğer) alt dize ararken doğru değerleri döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="fe7e5-104"><xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> and related APIs now return correct values when searching for a zero-length (or zero-length equivalent) substring within a larger string.</span></span>

## <a name="change-description"></a><span data-ttu-id="fe7e5-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="fe7e5-105">Change description</span></span>

<span data-ttu-id="fe7e5-106">.NET Framework ve .NET Core 1,0-3,1 ' de, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> çağıran sıfır uzunluklu alt dizeyi ararken Ilgili API 'ler yanlış bir değer döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="fe7e5-106">In .NET Framework and .NET Core 1.0 - 3.1, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> and related APIs might return an incorrect value when the caller searches for a zero-length substring.</span></span>

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '4' (incorrect)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '0' (incorrect)
```

<span data-ttu-id="fe7e5-107">.NET 5 ' den itibaren, bu API 'Ler için doğru değeri döndürür `LastIndexOf` .</span><span class="sxs-lookup"><span data-stu-id="fe7e5-107">Starting with .NET 5, these APIs return the correct value for `LastIndexOf`.</span></span>

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '5' (correct)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '5' (correct)
```

<span data-ttu-id="fe7e5-108">Bu örneklerde `5` doğru yanıt olduğundan, `"Hello".Substring(5)` `"Hello".AsSpan().Slice(5)` her ikisi de, aranan boş alt dizeye eşit ölçüde eşit olan boş bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fe7e5-108">In these examples, `5` is the correct answer because `"Hello".Substring(5)` and `"Hello".AsSpan().Slice(5)` both produce an empty string, which is trivially equal to the empty substring that is sought.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="fe7e5-109">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="fe7e5-109">Reason for change</span></span>

<span data-ttu-id="fe7e5-110">Bu değişiklik, .NET 5 için dize işlemede oluşan genel hata düzeltme çabalarının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="fe7e5-110">This change was part of an overall bug fixing effort around string handling for .NET 5.</span></span> <span data-ttu-id="fe7e5-111">Ayrıca Windows ve Windows dışı platformlar arasındaki davranışımızın birleşmesini de sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe7e5-111">It also helps unify our behavior between Windows and non-Windows platforms.</span></span> <span data-ttu-id="fe7e5-112">Daha fazla bilgi için bkz. [DotNet/Runtime # 13383](https://github.com/dotnet/runtime/issues/13383) ve [DotNet/Runtime # #13382](https://github.com/dotnet/runtime/issues/13382).</span><span class="sxs-lookup"><span data-stu-id="fe7e5-112">For more information, see [dotnet/runtime#13383](https://github.com/dotnet/runtime/issues/13383) and [dotnet/runtime##13382](https://github.com/dotnet/runtime/issues/13382).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="fe7e5-113">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="fe7e5-113">Version introduced</span></span>

<span data-ttu-id="fe7e5-114">5.0</span><span class="sxs-lookup"><span data-stu-id="fe7e5-114">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="fe7e5-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="fe7e5-115">Recommended action</span></span>

<span data-ttu-id="fe7e5-116">Herhangi bir işlem yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fe7e5-116">You don't need to take any action.</span></span> <span data-ttu-id="fe7e5-117">.NET 5 çalışma zamanı, yeni davranışları otomatik olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe7e5-117">The .NET 5 runtime provides the new behaviors automatically.</span></span>

<span data-ttu-id="fe7e5-118">Eski davranışı geri yüklemek için bir uyumluluk anahtarı yok.</span><span class="sxs-lookup"><span data-stu-id="fe7e5-118">There is no compatibility switch to restore the old behavior.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="fe7e5-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="fe7e5-119">Affected APIs</span></span>

- <xref:System.String.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.Globalization.CompareInfo.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.MemoryExtensions.LastIndexOf%2A?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `Overload:System.String.LastIndexOf`
- `Overload:System.Globalization.CompareInfo.LastIndexOf`
- `Overload:System.MemoryExtensions.LastIndexOf`

-->
