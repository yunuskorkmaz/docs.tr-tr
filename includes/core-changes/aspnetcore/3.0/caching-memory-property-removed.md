---
ms.openlocfilehash: 2c1362d6982206b14475f77700add0bae61da173
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902009"
---
### <a name="caching-compactonmemorypressure-property-removed"></a><span data-ttu-id="abbc3-101">Önbelleğe alma: CompactOnMemoryPressure özelliği kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="abbc3-101">Caching: CompactOnMemoryPressure property removed</span></span>

<span data-ttu-id="abbc3-102">ASP.NET Core 3.0 sürümü [eski MemoryCacheOptions API'leri](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18)kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="abbc3-102">The ASP.NET Core 3.0 release removed the [obsolete MemoryCacheOptions APIs](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span></span>

#### <a name="change-description"></a><span data-ttu-id="abbc3-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="abbc3-103">Change description</span></span>

<span data-ttu-id="abbc3-104">Bu değişiklik [aspnet/Caching#221'in](https://github.com/aspnet/Caching/issues/221)devamıdır.</span><span class="sxs-lookup"><span data-stu-id="abbc3-104">This change is a follow-up to [aspnet/Caching#221](https://github.com/aspnet/Caching/issues/221).</span></span> <span data-ttu-id="abbc3-105">Tartışmak için [dotnet/extensions#1062'ye](https://github.com/dotnet/extensions/issues/1062)bakın.</span><span class="sxs-lookup"><span data-stu-id="abbc3-105">For discussion, see [dotnet/extensions#1062](https://github.com/dotnet/extensions/issues/1062).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="abbc3-106">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="abbc3-106">Version introduced</span></span>

<span data-ttu-id="abbc3-107">3,0</span><span class="sxs-lookup"><span data-stu-id="abbc3-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="abbc3-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="abbc3-108">Old behavior</span></span>

<span data-ttu-id="abbc3-109">`MemoryCacheOptions.CompactOnMemoryPressure`mülkiyet mevcuttu.</span><span class="sxs-lookup"><span data-stu-id="abbc3-109">`MemoryCacheOptions.CompactOnMemoryPressure` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="abbc3-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="abbc3-110">New behavior</span></span>

<span data-ttu-id="abbc3-111">Mülk `MemoryCacheOptions.CompactOnMemoryPressure` kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="abbc3-111">The `MemoryCacheOptions.CompactOnMemoryPressure` property has been removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="abbc3-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="abbc3-112">Reason for change</span></span>

<span data-ttu-id="abbc3-113">Önbelleğin otomatik olarak sıkıştırılarak sorunlara neden oldu.</span><span class="sxs-lookup"><span data-stu-id="abbc3-113">Automatically compacting the cache caused problems.</span></span> <span data-ttu-id="abbc3-114">Beklenmeyen davranışları önlemek için önbellek yalnızca gerektiğinde sıkıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="abbc3-114">To avoid unexpected behavior, the cache should only be compacted when needed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="abbc3-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="abbc3-115">Recommended action</span></span>

<span data-ttu-id="abbc3-116">Önbelleği sıkıştırmak için, `MemoryCache` downcast ve gerektiğinde arayın. `Compact`</span><span class="sxs-lookup"><span data-stu-id="abbc3-116">To compact the cache, downcast to `MemoryCache` and call `Compact` when needed.</span></span>

#### <a name="category"></a><span data-ttu-id="abbc3-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="abbc3-117">Category</span></span>

<span data-ttu-id="abbc3-118">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="abbc3-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="abbc3-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="abbc3-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
