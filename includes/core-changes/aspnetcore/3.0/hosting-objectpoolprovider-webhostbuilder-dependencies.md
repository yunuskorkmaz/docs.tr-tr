---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901687"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a><span data-ttu-id="982be-101">Barındırma: ObjectPoolProvider WebHostBuilder bağımlılıklarından kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="982be-101">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>

<span data-ttu-id="982be-102">ASP.NET Core yürütmek için daha fazla ödeme yapma kapsamında, `ObjectPoolProvider` ana bağımlılıklar kümesinden kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="982be-102">As part of making ASP.NET Core more pay for play, the `ObjectPoolProvider` was removed from the main set of dependencies.</span></span> <span data-ttu-id="982be-103">`ObjectPoolProvider` bağlı belirli bileşenler artık kendisini ekler.</span><span class="sxs-lookup"><span data-stu-id="982be-103">Specific components relying on `ObjectPoolProvider` now add it themselves.</span></span>

<span data-ttu-id="982be-104">Tartışma için bkz. [DotNet/aspnetcore # 5944](https://github.com/dotnet/aspnetcore/issues/5944).</span><span class="sxs-lookup"><span data-stu-id="982be-104">For discussion, see [dotnet/aspnetcore#5944](https://github.com/dotnet/aspnetcore/issues/5944).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="982be-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="982be-105">Version introduced</span></span>

<span data-ttu-id="982be-106">3.0</span><span class="sxs-lookup"><span data-stu-id="982be-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="982be-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="982be-107">Old behavior</span></span>

<span data-ttu-id="982be-108">`WebHostBuilder`, DI kapsayıcısında varsayılan olarak `ObjectPoolProvider` sağlar.</span><span class="sxs-lookup"><span data-stu-id="982be-108">`WebHostBuilder` provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="982be-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="982be-109">New behavior</span></span>

<span data-ttu-id="982be-110">`WebHostBuilder` artık varsayılan olarak DI kapsayıcısında `ObjectPoolProvider` sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="982be-110">`WebHostBuilder` no longer provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="982be-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="982be-111">Reason for change</span></span>

<span data-ttu-id="982be-112">Bu değişiklik ASP.NET Core yürütmek için daha fazla ödeme yapmak üzere yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="982be-112">This change was made to make ASP.NET Core more pay for play.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="982be-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="982be-113">Recommended action</span></span>

<span data-ttu-id="982be-114">Bileşeniniz `ObjectPoolProvider`gerektiriyorsa, `IServiceCollection`aracılığıyla bağımlılıklarınızın eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="982be-114">If your component requires `ObjectPoolProvider`, it needs to be added to your dependencies via the `IServiceCollection`.</span></span>

#### <a name="category"></a><span data-ttu-id="982be-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="982be-115">Category</span></span>

<span data-ttu-id="982be-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="982be-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="982be-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="982be-117">Affected APIs</span></span>

<span data-ttu-id="982be-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="982be-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
