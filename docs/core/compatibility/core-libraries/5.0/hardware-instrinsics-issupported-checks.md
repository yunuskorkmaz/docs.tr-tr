---
title: 'Son değişiklik: donanım içi IsSupported denetimleri iç içe türler için farklılık gösterebilir'
description: X64 'Ün kontrol edildiği çekirdek .NET kitaplıklarında .NET 5 ile ilgili son değişiklik hakkında bilgi edinin. Donanım iç öğeleri için desteklenen ısbıg, artık farklı bir sonuç verebilir.
ms.date: 11/01/2020
ms.openlocfilehash: 5c6049ad5881c0389870cfd5e1550f8358c67599
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257459"
---
# <a name="hardware-intrinsic-issupported-checks-may-differ-for-nested-types"></a><span data-ttu-id="693fb-103">Donanım iç tarafından desteklenen denetimler iç içe türler için farklılık gösterebilir</span><span class="sxs-lookup"><span data-stu-id="693fb-103">Hardware intrinsic IsSupported checks may differ for nested types</span></span>

<span data-ttu-id="693fb-104">`<Isa>.X64.IsSupported`' Nin, `<Isa>` <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType> ad alanındaki sınıfların başvurduğu, artık önceki .net sürümlerine farklı bir sonuç üretebileceği denetleniyor.</span><span class="sxs-lookup"><span data-stu-id="693fb-104">Checking `<Isa>.X64.IsSupported`, where `<Isa>` refers to the classes in the <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType> namespace, may now produce a different result to previous versions of .NET.</span></span>

> [!TIP]
> <span data-ttu-id="693fb-105">*ISA* , sektör standardı mimarisi için temsil eder.</span><span class="sxs-lookup"><span data-stu-id="693fb-105">*ISA* stands for industry standard architecture.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="693fb-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="693fb-106">Version introduced</span></span>

<span data-ttu-id="693fb-107">5.0</span><span class="sxs-lookup"><span data-stu-id="693fb-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="693fb-108">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="693fb-108">Change description</span></span>

<span data-ttu-id="693fb-109">.NET 'in önceki sürümlerinde, bazı <xref:System.Runtime.Intrinsics.X86> donanım içi türler, örneğin, <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType> iç içe geçmiş bir `X64` sınıf sunmaz.</span><span class="sxs-lookup"><span data-stu-id="693fb-109">In previous versions of .NET, some of the <xref:System.Runtime.Intrinsics.X86> hardware-intrinsic types, for example, <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType>, didn't expose a nested `X64` class.</span></span> <span data-ttu-id="693fb-110">Bu türler için, bir `<Isa>.X64.IsSupported` `IsSupported` üst sınıfının iç içe sınıfındaki bir özelliğe çözüldü `X64` `<Isa>` .</span><span class="sxs-lookup"><span data-stu-id="693fb-110">For these types, calling `<Isa>.X64.IsSupported` resolved to an `IsSupported` property on a nested `X64` class of a parent class of `<Isa>`.</span></span> <span data-ttu-id="693fb-111">Bu, özelliği `true` döndüğünde bile döndürebilse anlamına gelir `<Isa>.IsSupported` `false` .</span><span class="sxs-lookup"><span data-stu-id="693fb-111">This meant that the property could return `true` even when `<Isa>.IsSupported` returns `false`.</span></span>

<span data-ttu-id="693fb-112">.NET 5 ve sonraki sürümlerinde tüm <xref:System.Runtime.Intrinsics.X86> türler, `X64` desteği uygun şekilde raporlayan iç içe bir sınıf kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="693fb-112">In .NET 5 and later versions, all of the <xref:System.Runtime.Intrinsics.X86> types expose a nested `X64` class that appropriately reports support.</span></span> <span data-ttu-id="693fb-113">Bu, genel hiyerarşinin doğru kalmasını sağlar ve bu durumda olduğu gibi `<Isa>.X64.IsSupported` `true` `<Isa>.IsSupported` kabul edilebilir `true` .</span><span class="sxs-lookup"><span data-stu-id="693fb-113">This ensures that the general hierarchy remains correct, and that if `<Isa>.X64.IsSupported` is `true`, then `<Isa>.IsSupported` can also be assumed to be `true`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="693fb-114">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="693fb-114">Reason for change</span></span>

<span data-ttu-id="693fb-115">Varsa `<Isa>.X64.IsSupported` `true` , `<Isa>.IsSupported` aynı zamanda olarak da ima edilir `true` .</span><span class="sxs-lookup"><span data-stu-id="693fb-115">It was intended that if `<Isa>.X64.IsSupported` is `true`, `<Isa>.IsSupported` is also implied to be `true`.</span></span> <span data-ttu-id="693fb-116">Ancak, üye çözümlemenin C# ' ta çalışmasına bağlı olarak, iç içe yerleştirilmiş bir sınıfı olmayan sınıflar `X64` her zaman durum olmadığı ve Kullanıcı kodundaki hatalara işaret eden bir durum ortaya çıkardı.</span><span class="sxs-lookup"><span data-stu-id="693fb-116">However, due to how member resolution works in C#, classes that didn't have a nested `X64` class exposed a situation where this wasn't always the case and led to bugs in user code.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="693fb-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="693fb-117">Recommended action</span></span>

<span data-ttu-id="693fb-118">Gerekirse, uygun ISA 'yı denetlemeyi denetleyen kodu ayarlayın `IsSupported` .</span><span class="sxs-lookup"><span data-stu-id="693fb-118">If necessary, adjust code that checks `IsSupported` to check for the appropriate ISA.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="693fb-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="693fb-119">Affected APIs</span></span>

- <xref:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported`

-->
