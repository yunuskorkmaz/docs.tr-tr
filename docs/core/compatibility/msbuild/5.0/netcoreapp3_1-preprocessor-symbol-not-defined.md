---
title: 'Son değişiklik: NETCOREAPP3_1 ön işlemci sembolü .NET 5 hedeflenirken tanımlanmaz'
description: .NET 5 ' teki son değişiklik hakkında bilgi edinin. burada, projeler artık önceki sürümler için önişlemci sembolleri tanımlamaz.
ms.date: 09/17/2020
ms.openlocfilehash: 390c8f5af97510db4652f3f42db577e6de158020
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256536"
---
# <a name="netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5"></a><span data-ttu-id="a4ad5-103">NETCOREAPP3_1 Önişlemci sembolü .NET 5 hedeflenirken tanımlanmaz</span><span class="sxs-lookup"><span data-stu-id="a4ad5-103">NETCOREAPP3_1 preprocessor symbol is not defined when targeting .NET 5</span></span>

<span data-ttu-id="a4ad5-104">.NET 5 RC2 ve sonraki sürümlerinde, projeler artık önceki sürümler için ön işlemci sembolleri tanımlamıyor, ancak yalnızca hedeflerine ait olan sürüm için.</span><span class="sxs-lookup"><span data-stu-id="a4ad5-104">In .NET 5 RC2 and later versions, projects no longer define preprocessor symbols for earlier versions, but only for the version that they target.</span></span> <span data-ttu-id="a4ad5-105">Bu, .NET Core 1,0-3,1 ile aynı davranıştır.</span><span class="sxs-lookup"><span data-stu-id="a4ad5-105">This is the same behavior as .NET Core 1.0 - 3.1.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a4ad5-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a4ad5-106">Version introduced</span></span>

<span data-ttu-id="a4ad5-107">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="a4ad5-107">5.0 RC2</span></span>

## <a name="change-description"></a><span data-ttu-id="a4ad5-108">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="a4ad5-108">Change description</span></span>

<span data-ttu-id="a4ad5-109">.NET 5 Preview 7 ' de RC1 ile, hedeflenen projeler `net5.0` hem hem `NETCOREAPP3_1` de `NET5_0` Önişlemci sembollerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a4ad5-109">In .NET 5 preview 7 through RC1, projects that target `net5.0` define both `NETCOREAPP3_1` and `NET5_0` preprocessor symbols.</span></span> <span data-ttu-id="a4ad5-110">Bu davranış değişikliğinin arkasındaki amaç, .NET 5 ' den itibaren Koşullu derleme [sembolleri birikimli olur](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md#preprocessor-symbols).</span><span class="sxs-lookup"><span data-stu-id="a4ad5-110">The intent behind this behavior change was that starting with .NET 5, conditional compilation [symbols would be cumulative](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md#preprocessor-symbols).</span></span>

<span data-ttu-id="a4ad5-111">.NET 5 RC2 ve üzeri sürümlerde, projeler yalnızca hedef Framework takma adları (tfd) için, daha önceki sürümler için değil, sembolleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a4ad5-111">In .NET 5 RC2 and later, projects only define symbols for the target framework monikers (TFM) that it targets and not for any earlier versions.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="a4ad5-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="a4ad5-112">Reason for change</span></span>

<span data-ttu-id="a4ad5-113">Preview 7 ' den değişiklik, müşteri geri bildirimi nedeniyle geri döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a4ad5-113">The change from preview 7 was reverted due to customer feedback.</span></span> <span data-ttu-id="a4ad5-114">Önceki sürümler için sembolleri ve karıştırılan müşterileri tanımlama ve C# derleyicisinde bir hata olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="a4ad5-114">Defining symbols for earlier versions surprised and confused customers, and some assumed it was a bug in the C# compiler.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a4ad5-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a4ad5-115">Recommended action</span></span>

<span data-ttu-id="a4ad5-116">`#if`Mantığınızın `NETCOREAPP3_1` Proje `net5.0` ya da daha yüksek bir hedef olduğunda tanımlı olduğunu varsaymıyor olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a4ad5-116">Make sure that your `#if` logic doesn't assume that `NETCOREAPP3_1` is defined when the project targets `net5.0` or higher.</span></span> <span data-ttu-id="a4ad5-117">Bunun yerine, `NETCOREAPP3_1` yalnızca proje açıkça hedeflediğinde tanımlı olduğunu varsayın `netcoreapp3.1` .</span><span class="sxs-lookup"><span data-stu-id="a4ad5-117">Instead, assume that `NETCOREAPP3_1` is only defined when the project explicitly targets `netcoreapp3.1`.</span></span>

<span data-ttu-id="a4ad5-118">Örneğin, projeniz .NET Core 2,1 ve .NET Core 3,1 için çoklu hedeflerse ve .NET Core 3,1 ' de tanıtılan API 'Leri çağırırsanız, `#if` mantığınızın aşağıdaki gibi görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="a4ad5-118">For example, if your project multitargets for .NET Core 2.1 and .NET Core 3.1 and you call APIs that were introduced in .NET Core 3.1, your `#if` logic should look as follows:</span></span>

```csharp
#if NETCOREAPP2_1 || NETCOREAPP3_0
    // Fallback behavior for old versions.
#elif NETCOREAPP
    // Behavior for .NET Core 3.1 and later.
#endif
```

## <a name="affected-apis"></a><span data-ttu-id="a4ad5-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a4ad5-119">Affected APIs</span></span>

<span data-ttu-id="a4ad5-120">Yok</span><span class="sxs-lookup"><span data-stu-id="a4ad5-120">N/A</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
