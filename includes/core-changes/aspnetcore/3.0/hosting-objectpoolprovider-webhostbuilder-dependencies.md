---
ms.openlocfilehash: 16b9fde49f513643a37f65f3e926a34fc991c55a
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394317"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a><span data-ttu-id="a60d6-101">Barındırma: ObjectPoolProvider WebHostBuilder bağımlılıklarından kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="a60d6-101">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>

<span data-ttu-id="a60d6-102">ASP.NET Core oynatma için daha fazla ödeme yapma kapsamında, `ObjectPoolProvider` ' ın ana bağımlılıklar kümesinden kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a60d6-102">As part of making ASP.NET Core more pay for play, the `ObjectPoolProvider` was removed from the main set of dependencies.</span></span> <span data-ttu-id="a60d6-103">@No__t-0 ' a bağlı belirli bileşenler artık kendisini ekler.</span><span class="sxs-lookup"><span data-stu-id="a60d6-103">Specific components relying on `ObjectPoolProvider` now add it themselves.</span></span>

<span data-ttu-id="a60d6-104">Tartışma için bkz. [ASPNET/AspNetCore # 5944](https://github.com/aspnet/AspNetCore/issues/5944).</span><span class="sxs-lookup"><span data-stu-id="a60d6-104">For discussion, see [aspnet/AspNetCore#5944](https://github.com/aspnet/AspNetCore/issues/5944).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a60d6-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a60d6-105">Version introduced</span></span>

<span data-ttu-id="a60d6-106">3.0</span><span class="sxs-lookup"><span data-stu-id="a60d6-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a60d6-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="a60d6-107">Old behavior</span></span>

<span data-ttu-id="a60d6-108">`WebHostBuilder`, varsayılan olarak DI kapsayıcısında 1 @no__t sağlar.</span><span class="sxs-lookup"><span data-stu-id="a60d6-108">`WebHostBuilder` provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a60d6-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="a60d6-109">New behavior</span></span>

<span data-ttu-id="a60d6-110">`WebHostBuilder` artık varsayılan olarak DI kapsayıcısında `ObjectPoolProvider` ' i sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="a60d6-110">`WebHostBuilder` no longer provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a60d6-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="a60d6-111">Reason for change</span></span>

<span data-ttu-id="a60d6-112">Bu değişiklik ASP.NET Core yürütmek için daha fazla ödeme yapmak üzere yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a60d6-112">This change was made to make ASP.NET Core more pay for play.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a60d6-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a60d6-113">Recommended action</span></span>

<span data-ttu-id="a60d6-114">Bileşeniniz `ObjectPoolProvider` gerektiriyorsa, `IServiceCollection` aracılığıyla bağımlılıklarınızın eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a60d6-114">If your component requires `ObjectPoolProvider`, it needs to be added to your dependencies via the `IServiceCollection`.</span></span>

#### <a name="category"></a><span data-ttu-id="a60d6-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="a60d6-115">Category</span></span>

<span data-ttu-id="a60d6-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a60d6-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a60d6-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a60d6-117">Affected APIs</span></span>

<span data-ttu-id="a60d6-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="a60d6-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
