---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901687"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a><span data-ttu-id="2193b-101">Barındırma: ObjectPoolProvider WebHostBuilder bağımlılıkları kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="2193b-101">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>

<span data-ttu-id="2193b-102">ASP.NET Core'un oyun için daha `ObjectPoolProvider` fazla ödeme yapmasını sağlamanın bir parçası olarak, bu bağımlılıklar ana kümeden çıkarıldı.</span><span class="sxs-lookup"><span data-stu-id="2193b-102">As part of making ASP.NET Core more pay for play, the `ObjectPoolProvider` was removed from the main set of dependencies.</span></span> <span data-ttu-id="2193b-103">`ObjectPoolProvider` Şimdi güvenen belirli bileşenler kendilerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2193b-103">Specific components relying on `ObjectPoolProvider` now add it themselves.</span></span>

<span data-ttu-id="2193b-104">Tartışma için [dotnet/aspnetcore#5944'e](https://github.com/dotnet/aspnetcore/issues/5944)bakın.</span><span class="sxs-lookup"><span data-stu-id="2193b-104">For discussion, see [dotnet/aspnetcore#5944](https://github.com/dotnet/aspnetcore/issues/5944).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2193b-105">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="2193b-105">Version introduced</span></span>

<span data-ttu-id="2193b-106">3,0</span><span class="sxs-lookup"><span data-stu-id="2193b-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="2193b-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="2193b-107">Old behavior</span></span>

<span data-ttu-id="2193b-108">`WebHostBuilder`di `ObjectPoolProvider` kapsayıcıda varsayılan olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2193b-108">`WebHostBuilder` provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="2193b-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="2193b-109">New behavior</span></span>

<span data-ttu-id="2193b-110">`WebHostBuilder`artık varsayılan `ObjectPoolProvider` olarak DI kapsayıcısında sağlar.</span><span class="sxs-lookup"><span data-stu-id="2193b-110">`WebHostBuilder` no longer provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="2193b-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="2193b-111">Reason for change</span></span>

<span data-ttu-id="2193b-112">Bu değişiklik ASP.NET Core oyun için daha fazla ödeme yapmak için yapıldı.</span><span class="sxs-lookup"><span data-stu-id="2193b-112">This change was made to make ASP.NET Core more pay for play.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2193b-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="2193b-113">Recommended action</span></span>

<span data-ttu-id="2193b-114">Bileşeniniz bunu `ObjectPoolProvider`gerektiriyorsa, `IServiceCollection`bağımlılıklarınıza .</span><span class="sxs-lookup"><span data-stu-id="2193b-114">If your component requires `ObjectPoolProvider`, it needs to be added to your dependencies via the `IServiceCollection`.</span></span>

#### <a name="category"></a><span data-ttu-id="2193b-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="2193b-115">Category</span></span>

<span data-ttu-id="2193b-116">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="2193b-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2193b-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="2193b-117">Affected APIs</span></span>

<span data-ttu-id="2193b-118">None</span><span class="sxs-lookup"><span data-stu-id="2193b-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
