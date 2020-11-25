---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032756"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a><span data-ttu-id="299f1-101">Barındırma: ObjectPoolProvider WebHostBuilder bağımlılıklarından kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="299f1-101">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>

<span data-ttu-id="299f1-102">Yürütme için ASP.NET Core daha fazla ödeme yapma kapsamında, `ObjectPoolProvider` ana bağımlılıklar kümesinden kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="299f1-102">As part of making ASP.NET Core more pay for play, the `ObjectPoolProvider` was removed from the main set of dependencies.</span></span> <span data-ttu-id="299f1-103">Artık bağlı olan belirli bileşenler kendisini `ObjectPoolProvider` ekler.</span><span class="sxs-lookup"><span data-stu-id="299f1-103">Specific components relying on `ObjectPoolProvider` now add it themselves.</span></span>

<span data-ttu-id="299f1-104">Tartışma için bkz. [DotNet/aspnetcore # 5944](https://github.com/dotnet/aspnetcore/issues/5944).</span><span class="sxs-lookup"><span data-stu-id="299f1-104">For discussion, see [dotnet/aspnetcore#5944](https://github.com/dotnet/aspnetcore/issues/5944).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="299f1-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="299f1-105">Version introduced</span></span>

<span data-ttu-id="299f1-106">3,0</span><span class="sxs-lookup"><span data-stu-id="299f1-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="299f1-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="299f1-107">Old behavior</span></span>

<span data-ttu-id="299f1-108">`WebHostBuilder``ObjectPoolProvider`dı kapsayıcısında varsayılan olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="299f1-108">`WebHostBuilder` provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="299f1-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="299f1-109">New behavior</span></span>

<span data-ttu-id="299f1-110">`WebHostBuilder` Artık `ObjectPoolProvider` Varsayılan olarak dı kapsayıcısında sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="299f1-110">`WebHostBuilder` no longer provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="299f1-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="299f1-111">Reason for change</span></span>

<span data-ttu-id="299f1-112">Bu değişiklik ASP.NET Core yürütmek için daha fazla ödeme yapmak üzere yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="299f1-112">This change was made to make ASP.NET Core more pay for play.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="299f1-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="299f1-113">Recommended action</span></span>

<span data-ttu-id="299f1-114">Bileşeniniz gerektiriyorsa `ObjectPoolProvider` , bağımlılıklarınızın aracılığıyla eklenmesi gerekir `IServiceCollection` .</span><span class="sxs-lookup"><span data-stu-id="299f1-114">If your component requires `ObjectPoolProvider`, it needs to be added to your dependencies via the `IServiceCollection`.</span></span>

#### <a name="category"></a><span data-ttu-id="299f1-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="299f1-115">Category</span></span>

<span data-ttu-id="299f1-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="299f1-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="299f1-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="299f1-117">Affected APIs</span></span>

<span data-ttu-id="299f1-118">Yok</span><span class="sxs-lookup"><span data-stu-id="299f1-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
