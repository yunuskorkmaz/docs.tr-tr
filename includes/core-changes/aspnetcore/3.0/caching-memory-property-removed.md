---
ms.openlocfilehash: 7d40324e6b0bc4afab9dd39b236f0909f360cc9b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394276"
---
### <a name="caching-compactonmemorypressure-property-removed"></a><span data-ttu-id="eaa40-101">Önbelleğe alma: CompactOnMemoryPressure özelliği kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="eaa40-101">Caching: CompactOnMemoryPressure property removed</span></span>

<span data-ttu-id="eaa40-102">ASP.NET Core 3,0 sürümü, [kullanılmayan MemoryCacheOptions API 'lerini](https://github.com/aspnet/Extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18)kaldırdı.</span><span class="sxs-lookup"><span data-stu-id="eaa40-102">The ASP.NET Core 3.0 release removed the [obsolete MemoryCacheOptions APIs](https://github.com/aspnet/Extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span></span>

#### <a name="change-description"></a><span data-ttu-id="eaa40-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="eaa40-103">Change description</span></span>

<span data-ttu-id="eaa40-104">Bu değişiklik, [ASPNET/önbelleğe alma #](https://github.com/aspnet/Caching/issues/221), için bir izleme.</span><span class="sxs-lookup"><span data-stu-id="eaa40-104">This change is a follow-up to [aspnet/Caching#221](https://github.com/aspnet/Caching/issues/221).</span></span> <span data-ttu-id="eaa40-105">Tartışma için bkz. [ASPNET/Extensions # 1062](https://github.com/aspnet/Extensions/issues/1062).</span><span class="sxs-lookup"><span data-stu-id="eaa40-105">For discussion, see [aspnet/Extensions#1062](https://github.com/aspnet/Extensions/issues/1062).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="eaa40-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="eaa40-106">Version introduced</span></span>

<span data-ttu-id="eaa40-107">3.0</span><span class="sxs-lookup"><span data-stu-id="eaa40-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="eaa40-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="eaa40-108">Old behavior</span></span>

<span data-ttu-id="eaa40-109">`MemoryCacheOptions.CompactOnMemoryPressure` özelliği kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eaa40-109">`MemoryCacheOptions.CompactOnMemoryPressure` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="eaa40-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="eaa40-110">New behavior</span></span>

<span data-ttu-id="eaa40-111">@No__t-0 özelliği kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="eaa40-111">The `MemoryCacheOptions.CompactOnMemoryPressure` property has been removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="eaa40-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="eaa40-112">Reason for change</span></span>

<span data-ttu-id="eaa40-113">Önbelleği otomatik olarak sıkıştırmak sorunlara neden oldu.</span><span class="sxs-lookup"><span data-stu-id="eaa40-113">Automatically compacting the cache caused problems.</span></span> <span data-ttu-id="eaa40-114">Beklenmeyen davranışları önlemek için, önbelleğin yalnızca gerektiğinde sıkıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="eaa40-114">To avoid unexpected behavior, the cache should only be compacted when needed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="eaa40-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="eaa40-115">Recommended action</span></span>

<span data-ttu-id="eaa40-116">Önbelleği sıkıştırmak için, `MemoryCache` ' a Alta ve gerektiğinde `Compact` ' i çağırın.</span><span class="sxs-lookup"><span data-stu-id="eaa40-116">To compact the cache, downcast to `MemoryCache` and call `Compact` when needed.</span></span>

#### <a name="category"></a><span data-ttu-id="eaa40-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="eaa40-117">Category</span></span>

<span data-ttu-id="eaa40-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="eaa40-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eaa40-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="eaa40-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
