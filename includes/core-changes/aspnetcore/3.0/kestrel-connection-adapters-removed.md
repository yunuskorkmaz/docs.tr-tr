---
ms.openlocfilehash: a916af91670dc9c5ceb2ff759cd8ae308fb2c2dc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393994"
---
### <a name="kestrel-connection-adapters-removed"></a><span data-ttu-id="2a90e-101">Kestrel: bağlantı bağdaştırıcıları kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="2a90e-101">Kestrel: Connection adapters removed</span></span>

<span data-ttu-id="2a90e-102">"Pubternal" API 'Lerini `public` ' a taşımanın bir parçası olarak, `IConnectionAdapter` kavramı Kestrel ' den kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="2a90e-102">As part of the move to move "pubternal" APIs to `public`, the concept of an `IConnectionAdapter` was removed from Kestrel.</span></span> <span data-ttu-id="2a90e-103">Bağlantı bağdaştırıcıları bağlantı ara yazılımı ile değiştiriliyor (ASP.NET Core işlem hattındaki HTTP ara hattına benzer ancak alt düzey bağlantılar için).</span><span class="sxs-lookup"><span data-stu-id="2a90e-103">Connection adapters are being replaced with connection middleware (similar to HTTP middleware in the ASP.NET Core pipeline, but for lower-level connections).</span></span> <span data-ttu-id="2a90e-104">HTTPS ve bağlantı günlüğü bağlantı bağdaştırıcılarından bağlantı ara yazılıma taşındı.</span><span class="sxs-lookup"><span data-stu-id="2a90e-104">HTTPS and connection logging have moved from connection adapters to connection middleware.</span></span> <span data-ttu-id="2a90e-105">Bu uzantı yöntemleri sorunsuz şekilde çalışmaya devam etmelidir, ancak uygulama ayrıntıları değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="2a90e-105">Those extension methods should continue to work seamlessly, but the implementation details have changed.</span></span>

<span data-ttu-id="2a90e-106">Daha fazla bilgi için bkz. [ASPNET/AspNetCore # 11412](https://github.com/aspnet/AspNetCore/pull/11412).</span><span class="sxs-lookup"><span data-stu-id="2a90e-106">For more information, see [aspnet/AspNetCore#11412](https://github.com/aspnet/AspNetCore/pull/11412).</span></span> <span data-ttu-id="2a90e-107">Tartışma için bkz. [ASPNET/AspNetCore # 11475](https://github.com/aspnet/AspNetCore/issues/11475).</span><span class="sxs-lookup"><span data-stu-id="2a90e-107">For discussion, see [aspnet/AspNetCore#11475](https://github.com/aspnet/AspNetCore/issues/11475).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2a90e-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="2a90e-108">Version introduced</span></span>

<span data-ttu-id="2a90e-109">3.0</span><span class="sxs-lookup"><span data-stu-id="2a90e-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="2a90e-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="2a90e-110">Old behavior</span></span>

<span data-ttu-id="2a90e-111">@No__t-0 kullanılarak Kestrel genişletilebilirlik bileşenleri oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="2a90e-111">Kestrel extensibility components were created using `IConnectionAdapter`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="2a90e-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="2a90e-112">New behavior</span></span>

<span data-ttu-id="2a90e-113">Kestrel genişletilebilirlik bileşenleri, [Ara yazılım](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2a90e-113">Kestrel extensibility components are created as [middleware](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="2a90e-114">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="2a90e-114">Reason for change</span></span>

<span data-ttu-id="2a90e-115">Bu değişiklik, daha esnek bir genişletilebilirlik mimarisi sağlamaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="2a90e-115">This change is intended to provide a more flexible extensibility architecture.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2a90e-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="2a90e-116">Recommended action</span></span>

<span data-ttu-id="2a90e-117">@No__t-0 ' ın tüm uygulamalarını, [burada](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f)gösterildiği gibi yeni ara yazılım düzenlerini kullanacak şekilde dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="2a90e-117">Convert any implementations of `IConnectionAdapter` to use the new middleware pattern as shown [here](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="category"></a><span data-ttu-id="2a90e-118">Kategori</span><span class="sxs-lookup"><span data-stu-id="2a90e-118">Category</span></span>

<span data-ttu-id="2a90e-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2a90e-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2a90e-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="2a90e-120">Affected APIs</span></span>

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
