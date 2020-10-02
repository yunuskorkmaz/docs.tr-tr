---
ms.openlocfilehash: de35df21d1887bc95a3106edba312c53daad8b68
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654750"
---
### <a name="netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5"></a><span data-ttu-id="b5139-101">NETCOREAPP3_1 Önişlemci sembolü .NET 5 hedeflenirken tanımlanmaz</span><span class="sxs-lookup"><span data-stu-id="b5139-101">NETCOREAPP3_1 preprocessor symbol is not defined when targeting .NET 5</span></span>

<span data-ttu-id="b5139-102">.NET 5,0 RC2 ve sonraki sürümlerinde, projeler artık önceki sürümler için ön işlemci sembolleri tanımlamıyor, ancak yalnızca hedeflerine ait olan sürüm için.</span><span class="sxs-lookup"><span data-stu-id="b5139-102">In .NET 5.0 RC2 and later versions, projects no longer define preprocessor symbols for earlier versions, but only for the version that they target.</span></span> <span data-ttu-id="b5139-103">Bu, .NET Core 1,0-3,1 ile aynı davranıştır.</span><span class="sxs-lookup"><span data-stu-id="b5139-103">This is the same behavior as .NET Core 1.0 - 3.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b5139-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="b5139-104">Version introduced</span></span>

<span data-ttu-id="b5139-105">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="b5139-105">5.0 RC2</span></span>

#### <a name="change-description"></a><span data-ttu-id="b5139-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="b5139-106">Change description</span></span>

<span data-ttu-id="b5139-107">.NET 5,0 Preview 7 ' de RC1 ile, hedeflenen projeler `net5.0` hem hem `NETCOREAPP3_1` de `NET5_0` Önişlemci sembollerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b5139-107">In .NET 5.0 preview 7 through RC1, projects that target `net5.0` define both `NETCOREAPP3_1` and `NET5_0` preprocessor symbols.</span></span> <span data-ttu-id="b5139-108">Bu davranış değişikliğinin arkasındaki amaç, .NET 5,0 ile başlayarak koşullu derleme [sembolleri birikimli olur](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md#preprocessor-symbols).</span><span class="sxs-lookup"><span data-stu-id="b5139-108">The intent behind this behavior change was that starting with .NET 5.0, conditional compilation [symbols would be cumulative](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md#preprocessor-symbols).</span></span>

<span data-ttu-id="b5139-109">.NET 5,0 RC2 ve üzeri sürümlerde, projeler yalnızca hedef Framework takma adları (tfd) için, daha önceki sürümler için değil, sembolleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b5139-109">In .NET 5.0 RC2 and later, projects only define symbols for the target framework monikers (TFM) that it targets and not for any earlier versions.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b5139-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="b5139-110">Reason for change</span></span>

<span data-ttu-id="b5139-111">Preview 7 ' den değişiklik, müşteri geri bildirimi nedeniyle geri döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b5139-111">The change from preview 7 was reverted due to customer feedback.</span></span> <span data-ttu-id="b5139-112">Önceki sürümler için sembolleri ve karıştırılan müşterileri tanımlama ve C# derleyicisinde bir hata olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="b5139-112">Defining symbols for earlier versions surprised and confused customers, and some assumed it was a bug in the C# compiler.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b5139-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="b5139-113">Recommended action</span></span>

<span data-ttu-id="b5139-114">`#if`Mantığınızın `NETCOREAPP3_1` Proje `net5.0` ya da daha yüksek bir hedef olduğunda tanımlı olduğunu varsaymıyor olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b5139-114">Make sure that your `#if` logic doesn't assume that `NETCOREAPP3_1` is defined when the project targets `net5.0` or higher.</span></span> <span data-ttu-id="b5139-115">Bunun yerine, `NETCOREAPP3_1` yalnızca proje açıkça hedeflediğinde tanımlı olduğunu varsayın `netcoreapp3.1` .</span><span class="sxs-lookup"><span data-stu-id="b5139-115">Instead, assume that `NETCOREAPP3_1` is only defined when the project explicitly targets `netcoreapp3.1`.</span></span>

<span data-ttu-id="b5139-116">Örneğin, projeniz .NET Core 2,1 ve .NET Core 3,1 için çoklu hedeflerse ve .NET Core 3,1 ' de tanıtılan API 'Leri çağırırsanız, `#if` mantığınızın aşağıdaki gibi görünmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="b5139-116">For example, if your project multitargets for .NET Core 2.1 and .NET Core 3.1 and you call APIs that were introduced in .NET Core 3.1, your `#if` logic should look as follows:</span></span>

```csharp
#if NETCOREAPP2_1 || NETCOREAPP3_0
    // Fallback behavior for old versions.
#elif NETCOREAPP
    // Behavior for .NET Core 3.1 and later.
#endif
```

#### <a name="category"></a><span data-ttu-id="b5139-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="b5139-117">Category</span></span>

<span data-ttu-id="b5139-118">MSBuild</span><span class="sxs-lookup"><span data-stu-id="b5139-118">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b5139-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b5139-119">Affected APIs</span></span>

<span data-ttu-id="b5139-120">Yok</span><span class="sxs-lookup"><span data-stu-id="b5139-120">N/A</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
