---
ms.openlocfilehash: 9d138f79fcede4acac837f8d7793aa343ced737c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78290735"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a><span data-ttu-id="c0dbd-101">HTTP: VarsayılanHttpContext genişletilebilirlik kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="c0dbd-101">HTTP: DefaultHttpContext extensibility removed</span></span>

<span data-ttu-id="c0dbd-102">Core 3.0 performans geliştirmelerinin ASP.NET bir parçası olarak, genişletilebilirlik `DefaultHttpContext` kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="c0dbd-102">As part of ASP.NET Core 3.0 performance improvements, the extensibility of `DefaultHttpContext` was removed.</span></span> <span data-ttu-id="c0dbd-103">Sınıf şimdi. `sealed`</span><span class="sxs-lookup"><span data-stu-id="c0dbd-103">The class is now `sealed`.</span></span> <span data-ttu-id="c0dbd-104">Daha fazla bilgi için [dotnet/aspnetcore#6504'e](https://github.com/dotnet/aspnetcore/pull/6504)bakın.</span><span class="sxs-lookup"><span data-stu-id="c0dbd-104">For more information, see [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504).</span></span>

<span data-ttu-id="c0dbd-105">Birim testleriniz `Mock<DefaultHttpContext>`kullanıyorsa, kullanın `Mock<HttpContext>` veya `new DefaultHttpContext()` bunun yerine.</span><span class="sxs-lookup"><span data-stu-id="c0dbd-105">If your unit tests use `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` or `new DefaultHttpContext()` instead.</span></span>

<span data-ttu-id="c0dbd-106">Tartışma için [dotnet/aspnetcore#6534'e](https://github.com/dotnet/aspnetcore/issues/6534)bakın.</span><span class="sxs-lookup"><span data-stu-id="c0dbd-106">For discussion, see [dotnet/aspnetcore#6534](https://github.com/dotnet/aspnetcore/issues/6534).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c0dbd-107">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="c0dbd-107">Version introduced</span></span>

<span data-ttu-id="c0dbd-108">3,0</span><span class="sxs-lookup"><span data-stu-id="c0dbd-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="c0dbd-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="c0dbd-109">Old behavior</span></span>

<span data-ttu-id="c0dbd-110">Sınıflar dan `DefaultHttpContext`türetilebilir.</span><span class="sxs-lookup"><span data-stu-id="c0dbd-110">Classes can derive from `DefaultHttpContext`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="c0dbd-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="c0dbd-111">New behavior</span></span>

<span data-ttu-id="c0dbd-112">Sınıflar. `DefaultHttpContext`</span><span class="sxs-lookup"><span data-stu-id="c0dbd-112">Classes can't derive from `DefaultHttpContext`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c0dbd-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="c0dbd-113">Reason for change</span></span>

<span data-ttu-id="c0dbd-114">Genişletilebilirlik başlangıçta havuzlama izin vermek için `HttpContext`sağlanmıştır , ama gereksiz karmaşıklığı tanıttı ve diğer optimizasyonlar engelledi.</span><span class="sxs-lookup"><span data-stu-id="c0dbd-114">The extensibility was provided initially to allow pooling of the `HttpContext`, but it introduced unnecessary complexity and impeded other optimizations.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c0dbd-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c0dbd-115">Recommended action</span></span>

<span data-ttu-id="c0dbd-116">Birim testlerinizde `Mock<DefaultHttpContext>` kullanıyorsanız, bunun yerine `Mock<HttpContext>` kullanmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="c0dbd-116">If you're using `Mock<DefaultHttpContext>` in your unit tests, begin using `Mock<HttpContext>` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="c0dbd-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="c0dbd-117">Category</span></span>

<span data-ttu-id="c0dbd-118">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="c0dbd-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c0dbd-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c0dbd-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
