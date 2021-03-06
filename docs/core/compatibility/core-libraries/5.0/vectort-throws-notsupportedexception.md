---
title: 'Son değişiklik: vektör, <T> NotSupportedException oluşturur'
description: Çekirdek .NET kitaplıklarında, vektör 'in <T> her zaman desteklenmeyen tür parametreleri için bir özel durum oluşturan .NET 5 ' teki son değişiklik hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: dccd39c01f4debd7d1432195e7f3cb14aeda5f65
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257017"
---
# <a name="vectort-always-throws-notsupportedexception-for-unsupported-types"></a><span data-ttu-id="e75f0-103">Vektör, \<T> Desteklenmeyen türler için her zaman NotSupportedException oluşturur</span><span class="sxs-lookup"><span data-stu-id="e75f0-103">Vector\<T> always throws NotSupportedException for unsupported types</span></span>

<span data-ttu-id="e75f0-104"><xref:System.Numerics.Vector%601?displayProperty=nameWithType> Artık, <xref:System.NotSupportedException> desteklenmeyen tür parametreleri için her zaman bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e75f0-104"><xref:System.Numerics.Vector%601?displayProperty=nameWithType> now always throws a <xref:System.NotSupportedException> for unsupported type parameters.</span></span>

## <a name="change-description"></a><span data-ttu-id="e75f0-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="e75f0-105">Change description</span></span>

<span data-ttu-id="e75f0-106">Daha önce, üyeleri <xref:System.Numerics.Vector%601> <xref:System.NotSupportedException> Desteklenmeyen bir tür olduğunda her zaman bir oluşturmaz `T` . [](#unsupported-types)</span><span class="sxs-lookup"><span data-stu-id="e75f0-106">Previously, members of <xref:System.Numerics.Vector%601> would not always throw a <xref:System.NotSupportedException> when `T` was an [unsupported type](#unsupported-types).</span></span> <span data-ttu-id="e75f0-107">Donanım hızlandırmasının desteklediği kod yolları nedeniyle özel durum her zaman oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="e75f0-107">The exception wasn't always thrown because of code paths that supported hardware acceleration.</span></span> <span data-ttu-id="e75f0-108">Örneğin, `Vector<bool> + Vector<bool>` ARM32 gibi `default` donanım hızlandırmayan platformlarda bir özel durum oluşturmak yerine döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e75f0-108">For example, `Vector<bool> + Vector<bool>` returned `default` instead of throwing an exception on platforms that have no hardware acceleration, such as ARM32.</span></span> <span data-ttu-id="e75f0-109">Desteklenmeyen türler için, <xref:System.Numerics.Vector%601> Üyeler farklı platformlarda ve donanım yapılandırmalarında tutarsız davranışlar sergilen.</span><span class="sxs-lookup"><span data-stu-id="e75f0-109">For unsupported types, <xref:System.Numerics.Vector%601> members exhibited inconsistent behavior across different platforms and hardware configurations.</span></span>

<span data-ttu-id="e75f0-110">.NET 5 ' den başlayarak, <xref:System.Numerics.Vector%601> Üyeler <xref:System.NotSupportedException> `T` desteklenen bir tür olmadığında her zaman tüm donanım yapılandırmalarında bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e75f0-110">Starting in .NET 5, <xref:System.Numerics.Vector%601> members always throw a <xref:System.NotSupportedException> on all hardware configurations when `T` is not a supported type.</span></span>

### <a name="unsupported-types"></a><span data-ttu-id="e75f0-111">Desteklenmeyen türler</span><span class="sxs-lookup"><span data-stu-id="e75f0-111">Unsupported types</span></span>

<span data-ttu-id="e75f0-112">Tür parametresi için desteklenen türler <xref:System.Numerics.Vector%601> şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e75f0-112">The supported types for the type parameter of <xref:System.Numerics.Vector%601> are:</span></span>

- `byte`
- `sbyte`
- `short`
- `ushort`
- `int`
- `uint`
- `long`
- `ulong`
- `float`
- `double`

<span data-ttu-id="e75f0-113">Desteklenen türler değişmemiştir, ancak gelecekte değişebilir.</span><span class="sxs-lookup"><span data-stu-id="e75f0-113">The supported types have not changed, however, they may change in the future.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="e75f0-114">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e75f0-114">Version introduced</span></span>

<span data-ttu-id="e75f0-115">5.0</span><span class="sxs-lookup"><span data-stu-id="e75f0-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e75f0-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e75f0-116">Recommended action</span></span>

<span data-ttu-id="e75f0-117">Tür parametresi için desteklenmeyen bir tür kullanmayın <xref:System.Numerics.Vector%601> .</span><span class="sxs-lookup"><span data-stu-id="e75f0-117">Don't use an unsupported type for the type parameter of <xref:System.Numerics.Vector%601>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e75f0-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e75f0-118">Affected APIs</span></span>

- <span data-ttu-id="e75f0-119"><xref:System.Numerics.Vector%601?displayProperty=fullName> ve tüm üyelerini</span><span class="sxs-lookup"><span data-stu-id="e75f0-119"><xref:System.Numerics.Vector%601?displayProperty=fullName> and all its members</span></span>

<!--

#### Category

Core .NET libraries

### Affected APIs

- ``T:System.Numerics.Vector`1``

-->
