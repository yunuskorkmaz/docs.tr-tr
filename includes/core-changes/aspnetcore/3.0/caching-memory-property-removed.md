---
ms.openlocfilehash: 2c1362d6982206b14475f77700add0bae61da173
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75902009"
---
### <a name="caching-compactonmemorypressure-property-removed"></a><span data-ttu-id="1b72c-101">Önbelleğe alma: CompactOnMemoryPressure özelliği kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="1b72c-101">Caching: CompactOnMemoryPressure property removed</span></span>

<span data-ttu-id="1b72c-102">ASP.NET Core 3,0 sürümü, [kullanılmayan MemoryCacheOptions API 'lerini](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18)kaldırdı.</span><span class="sxs-lookup"><span data-stu-id="1b72c-102">The ASP.NET Core 3.0 release removed the [obsolete MemoryCacheOptions APIs](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span></span>

#### <a name="change-description"></a><span data-ttu-id="1b72c-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="1b72c-103">Change description</span></span>

<span data-ttu-id="1b72c-104">Bu değişiklik, [ASPNET/önbelleğe alma #](https://github.com/aspnet/Caching/issues/221), için bir izleme.</span><span class="sxs-lookup"><span data-stu-id="1b72c-104">This change is a follow-up to [aspnet/Caching#221](https://github.com/aspnet/Caching/issues/221).</span></span> <span data-ttu-id="1b72c-105">Tartışma için bkz. [DotNet/Extensions # 1062](https://github.com/dotnet/extensions/issues/1062).</span><span class="sxs-lookup"><span data-stu-id="1b72c-105">For discussion, see [dotnet/extensions#1062](https://github.com/dotnet/extensions/issues/1062).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1b72c-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="1b72c-106">Version introduced</span></span>

<span data-ttu-id="1b72c-107">3.0</span><span class="sxs-lookup"><span data-stu-id="1b72c-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1b72c-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="1b72c-108">Old behavior</span></span>

<span data-ttu-id="1b72c-109">`MemoryCacheOptions.CompactOnMemoryPressure` özellik var.</span><span class="sxs-lookup"><span data-stu-id="1b72c-109">`MemoryCacheOptions.CompactOnMemoryPressure` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1b72c-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="1b72c-110">New behavior</span></span>

<span data-ttu-id="1b72c-111">`MemoryCacheOptions.CompactOnMemoryPressure` özelliği kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1b72c-111">The `MemoryCacheOptions.CompactOnMemoryPressure` property has been removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1b72c-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="1b72c-112">Reason for change</span></span>

<span data-ttu-id="1b72c-113">Önbelleği otomatik olarak sıkıştırmak sorunlara neden oldu.</span><span class="sxs-lookup"><span data-stu-id="1b72c-113">Automatically compacting the cache caused problems.</span></span> <span data-ttu-id="1b72c-114">Beklenmeyen davranışları önlemek için, önbelleğin yalnızca gerektiğinde sıkıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b72c-114">To avoid unexpected behavior, the cache should only be compacted when needed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1b72c-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="1b72c-115">Recommended action</span></span>

<span data-ttu-id="1b72c-116">Önbelleği sıkıştırmak için, `MemoryCache` Alta ve gerektiğinde `Compact` çağırın.</span><span class="sxs-lookup"><span data-stu-id="1b72c-116">To compact the cache, downcast to `MemoryCache` and call `Compact` when needed.</span></span>

#### <a name="category"></a><span data-ttu-id="1b72c-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="1b72c-117">Category</span></span>

<span data-ttu-id="1b72c-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1b72c-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1b72c-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="1b72c-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
