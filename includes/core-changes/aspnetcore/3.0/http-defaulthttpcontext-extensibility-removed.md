---
ms.openlocfilehash: 9d138f79fcede4acac837f8d7793aa343ced737c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032771"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a><span data-ttu-id="97855-101">HTTP: DefaultHttpContext genişletilebilirliği kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="97855-101">HTTP: DefaultHttpContext extensibility removed</span></span>

<span data-ttu-id="97855-102">ASP.NET Core 3,0 performans geliştirmelerinden bir parçası olarak, ' nin genişletilebilirliği `DefaultHttpContext` kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="97855-102">As part of ASP.NET Core 3.0 performance improvements, the extensibility of `DefaultHttpContext` was removed.</span></span> <span data-ttu-id="97855-103">Sınıfı artık `sealed` .</span><span class="sxs-lookup"><span data-stu-id="97855-103">The class is now `sealed`.</span></span> <span data-ttu-id="97855-104">Daha fazla bilgi için bkz. [DotNet/aspnetcore # 6504](https://github.com/dotnet/aspnetcore/pull/6504).</span><span class="sxs-lookup"><span data-stu-id="97855-104">For more information, see [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504).</span></span>

<span data-ttu-id="97855-105">Birim testleriniz kullanıyorsa `Mock<DefaultHttpContext>` , `Mock<HttpContext>` veya `new DefaultHttpContext()` yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="97855-105">If your unit tests use `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` or `new DefaultHttpContext()` instead.</span></span>

<span data-ttu-id="97855-106">Tartışma için bkz. [DotNet/aspnetcore # 6534](https://github.com/dotnet/aspnetcore/issues/6534).</span><span class="sxs-lookup"><span data-stu-id="97855-106">For discussion, see [dotnet/aspnetcore#6534](https://github.com/dotnet/aspnetcore/issues/6534).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="97855-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="97855-107">Version introduced</span></span>

<span data-ttu-id="97855-108">3,0</span><span class="sxs-lookup"><span data-stu-id="97855-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="97855-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="97855-109">Old behavior</span></span>

<span data-ttu-id="97855-110">Sınıflar öğesinden türetilebilir `DefaultHttpContext` .</span><span class="sxs-lookup"><span data-stu-id="97855-110">Classes can derive from `DefaultHttpContext`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="97855-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="97855-111">New behavior</span></span>

<span data-ttu-id="97855-112">Sınıflar öğesinden türetilemez `DefaultHttpContext` .</span><span class="sxs-lookup"><span data-stu-id="97855-112">Classes can't derive from `DefaultHttpContext`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="97855-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="97855-113">Reason for change</span></span>

<span data-ttu-id="97855-114">Genişletilebilirlik, başlangıçta havuza izin verecek şekilde sağlandı `HttpContext` , ancak gereksiz karmaşıklık ve başka iyileştirmeler getirmiştir.</span><span class="sxs-lookup"><span data-stu-id="97855-114">The extensibility was provided initially to allow pooling of the `HttpContext`, but it introduced unnecessary complexity and impeded other optimizations.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="97855-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="97855-115">Recommended action</span></span>

<span data-ttu-id="97855-116">`Mock<DefaultHttpContext>`Birim testlerinizde kullanıyorsanız, `Mock<HttpContext>` bunun yerine kullanmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="97855-116">If you're using `Mock<DefaultHttpContext>` in your unit tests, begin using `Mock<HttpContext>` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="97855-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="97855-117">Category</span></span>

<span data-ttu-id="97855-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="97855-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="97855-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="97855-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
