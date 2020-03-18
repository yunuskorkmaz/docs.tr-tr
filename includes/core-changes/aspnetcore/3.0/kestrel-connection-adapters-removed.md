---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901714"
---
### <a name="kestrel-connection-adapters-removed"></a><span data-ttu-id="785ba-101">Kerkenez: Bağlantı bağdaştırıcıları kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="785ba-101">Kestrel: Connection adapters removed</span></span>

<span data-ttu-id="785ba-102">"Pubternal" API'leri taşımak için `public`hareketin bir `IConnectionAdapter` parçası olarak, bir kavramı Kerkenez kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="785ba-102">As part of the move to move "pubternal" APIs to `public`, the concept of an `IConnectionAdapter` was removed from Kestrel.</span></span> <span data-ttu-id="785ba-103">Bağlantı bağdaştırıcıları bağlantı ara yazılımları ile değiştirilmektedir (ASP.NET Core ardışık lıktaki HTTP ara yazılımlarına benzer, ancak alt düzey bağlantılar için).</span><span class="sxs-lookup"><span data-stu-id="785ba-103">Connection adapters are being replaced with connection middleware (similar to HTTP middleware in the ASP.NET Core pipeline, but for lower-level connections).</span></span> <span data-ttu-id="785ba-104">HTTPS ve bağlantı günlüğü bağlantı bağdaştırıcılarından bağlantı ara yazılımlarına geçti.</span><span class="sxs-lookup"><span data-stu-id="785ba-104">HTTPS and connection logging have moved from connection adapters to connection middleware.</span></span> <span data-ttu-id="785ba-105">Bu uzantı yöntemleri sorunsuz çalışmaya devam etmelidir, ancak uygulama ayrıntıları değişti.</span><span class="sxs-lookup"><span data-stu-id="785ba-105">Those extension methods should continue to work seamlessly, but the implementation details have changed.</span></span>

<span data-ttu-id="785ba-106">Daha fazla bilgi için [dotnet/aspnetcore#11412'ye](https://github.com/dotnet/aspnetcore/pull/11412)bakın.</span><span class="sxs-lookup"><span data-stu-id="785ba-106">For more information, see [dotnet/aspnetcore#11412](https://github.com/dotnet/aspnetcore/pull/11412).</span></span> <span data-ttu-id="785ba-107">Tartışma için [dotnet/aspnetcore#11475'e](https://github.com/dotnet/aspnetcore/issues/11475)bakın.</span><span class="sxs-lookup"><span data-stu-id="785ba-107">For discussion, see [dotnet/aspnetcore#11475](https://github.com/dotnet/aspnetcore/issues/11475).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="785ba-108">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="785ba-108">Version introduced</span></span>

<span data-ttu-id="785ba-109">3,0</span><span class="sxs-lookup"><span data-stu-id="785ba-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="785ba-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="785ba-110">Old behavior</span></span>

<span data-ttu-id="785ba-111">Kerkenez ekstensibilite `IConnectionAdapter`bileşenleri kullanılarak oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="785ba-111">Kestrel extensibility components were created using `IConnectionAdapter`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="785ba-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="785ba-112">New behavior</span></span>

<span data-ttu-id="785ba-113">Kerkenez ekstensibilite bileşenleri [ara yazılım](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="785ba-113">Kestrel extensibility components are created as [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="785ba-114">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="785ba-114">Reason for change</span></span>

<span data-ttu-id="785ba-115">Bu değişiklik, daha esnek bir genişletilebilirlik mimarisi sağlamak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="785ba-115">This change is intended to provide a more flexible extensibility architecture.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="785ba-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="785ba-116">Recommended action</span></span>

<span data-ttu-id="785ba-117">Burada gösterildiği gibi `IConnectionAdapter` yeni ara yazılım deseni [here](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)kullanmak için herhangi bir uygulama dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="785ba-117">Convert any implementations of `IConnectionAdapter` to use the new middleware pattern as shown [here](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="category"></a><span data-ttu-id="785ba-118">Kategori</span><span class="sxs-lookup"><span data-stu-id="785ba-118">Category</span></span>

<span data-ttu-id="785ba-119">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="785ba-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="785ba-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="785ba-120">Affected APIs</span></span>

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
