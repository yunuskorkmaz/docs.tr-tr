---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032803"
---
### <a name="kestrel-connection-adapters-removed"></a><span data-ttu-id="95752-101">Kestrel: bağlantı bağdaştırıcıları kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="95752-101">Kestrel: Connection adapters removed</span></span>

<span data-ttu-id="95752-102">"Pubternal" API 'Lerini uygulamasına taşıma kapsamında `public` , bir kavramı `IConnectionAdapter` Kestrel öğesinden kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="95752-102">As part of the move to move "pubternal" APIs to `public`, the concept of an `IConnectionAdapter` was removed from Kestrel.</span></span> <span data-ttu-id="95752-103">Bağlantı bağdaştırıcıları bağlantı ara yazılımı ile değiştiriliyor (ASP.NET Core işlem hattındaki HTTP ara hattına benzer ancak alt düzey bağlantılar için).</span><span class="sxs-lookup"><span data-stu-id="95752-103">Connection adapters are being replaced with connection middleware (similar to HTTP middleware in the ASP.NET Core pipeline, but for lower-level connections).</span></span> <span data-ttu-id="95752-104">HTTPS ve bağlantı günlüğü bağlantı bağdaştırıcılarından bağlantı ara yazılıma taşındı.</span><span class="sxs-lookup"><span data-stu-id="95752-104">HTTPS and connection logging have moved from connection adapters to connection middleware.</span></span> <span data-ttu-id="95752-105">Bu uzantı yöntemleri sorunsuz şekilde çalışmaya devam etmelidir, ancak uygulama ayrıntıları değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="95752-105">Those extension methods should continue to work seamlessly, but the implementation details have changed.</span></span>

<span data-ttu-id="95752-106">Daha fazla bilgi için bkz. [DotNet/aspnetcore # 11412](https://github.com/dotnet/aspnetcore/pull/11412).</span><span class="sxs-lookup"><span data-stu-id="95752-106">For more information, see [dotnet/aspnetcore#11412](https://github.com/dotnet/aspnetcore/pull/11412).</span></span> <span data-ttu-id="95752-107">Tartışma için bkz. [DotNet/aspnetcore # 11475](https://github.com/dotnet/aspnetcore/issues/11475).</span><span class="sxs-lookup"><span data-stu-id="95752-107">For discussion, see [dotnet/aspnetcore#11475](https://github.com/dotnet/aspnetcore/issues/11475).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="95752-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="95752-108">Version introduced</span></span>

<span data-ttu-id="95752-109">3,0</span><span class="sxs-lookup"><span data-stu-id="95752-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="95752-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="95752-110">Old behavior</span></span>

<span data-ttu-id="95752-111">Kestrel genişletilebilirlik bileşenleri kullanılarak oluşturulmuştur `IConnectionAdapter` .</span><span class="sxs-lookup"><span data-stu-id="95752-111">Kestrel extensibility components were created using `IConnectionAdapter`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="95752-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="95752-112">New behavior</span></span>

<span data-ttu-id="95752-113">Kestrel genişletilebilirlik bileşenleri, [Ara yazılım](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="95752-113">Kestrel extensibility components are created as [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="95752-114">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="95752-114">Reason for change</span></span>

<span data-ttu-id="95752-115">Bu değişiklik, daha esnek bir genişletilebilirlik mimarisi sağlamaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="95752-115">This change is intended to provide a more flexible extensibility architecture.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="95752-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="95752-116">Recommended action</span></span>

<span data-ttu-id="95752-117">Tüm uygulamalarını, `IConnectionAdapter` [burada](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)gösterildiği gibi yeni ara yazılım düzenlerini kullanacak şekilde dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="95752-117">Convert any implementations of `IConnectionAdapter` to use the new middleware pattern as shown [here](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="category"></a><span data-ttu-id="95752-118">Kategori</span><span class="sxs-lookup"><span data-stu-id="95752-118">Category</span></span>

<span data-ttu-id="95752-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="95752-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="95752-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="95752-120">Affected APIs</span></span>

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
