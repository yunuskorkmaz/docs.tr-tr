---
ms.openlocfilehash: 1b4b0aba3ea24682ae972bf283ac387692c83781
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75902011"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a><span data-ttu-id="b5b27-101">HTTP: DefaultHttpContext genişletilebilirliği kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="b5b27-101">HTTP: DefaultHttpContext extensibility removed</span></span>

<span data-ttu-id="b5b27-102">ASP.NET Core 3,0 performans geliştirmelerinden bir parçası olarak, `DefaultHttpContext` genişletilebilirliği kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b5b27-102">As part of ASP.NET Core 3.0 performance improvements, the extensibility of `DefaultHttpContext` was removed.</span></span> <span data-ttu-id="b5b27-103">Sınıf artık `sealed`.</span><span class="sxs-lookup"><span data-stu-id="b5b27-103">The class is now `sealed`.</span></span> <span data-ttu-id="b5b27-104">Daha fazla bilgi için bkz. [DotNet/aspnetcore # 6504](https://github.com/dotnet/aspnetcore/pull/6504).</span><span class="sxs-lookup"><span data-stu-id="b5b27-104">For more information, see [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504).</span></span>

<span data-ttu-id="b5b27-105">Birim testleriniz `Mock<DefaultHttpContext>`kullanıyorsa, bunun yerine `Mock<HttpContext>` kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5b27-105">If your unit tests use `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` instead.</span></span>

<span data-ttu-id="b5b27-106">Tartışma için bkz. [DotNet/aspnetcore # 6534](https://github.com/dotnet/aspnetcore/issues/6534).</span><span class="sxs-lookup"><span data-stu-id="b5b27-106">For discussion, see [dotnet/aspnetcore#6534](https://github.com/dotnet/aspnetcore/issues/6534).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b5b27-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="b5b27-107">Version introduced</span></span>

<span data-ttu-id="b5b27-108">3.0</span><span class="sxs-lookup"><span data-stu-id="b5b27-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b5b27-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="b5b27-109">Old behavior</span></span>

<span data-ttu-id="b5b27-110">Sınıflar `DefaultHttpContext`türetilebilir.</span><span class="sxs-lookup"><span data-stu-id="b5b27-110">Classes can derive from `DefaultHttpContext`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b5b27-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="b5b27-111">New behavior</span></span>

<span data-ttu-id="b5b27-112">Sınıflar `DefaultHttpContext`türetilemiyor.</span><span class="sxs-lookup"><span data-stu-id="b5b27-112">Classes can't derive from `DefaultHttpContext`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b5b27-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="b5b27-113">Reason for change</span></span>

<span data-ttu-id="b5b27-114">Genişletilebilirlik, başlangıçta `HttpContext`havuza izin verecek şekilde sağlandı, ancak gereksiz karmaşıklık ve başka iyileştirmeler getirmiştir.</span><span class="sxs-lookup"><span data-stu-id="b5b27-114">The extensibility was provided initially to allow pooling of the `HttpContext`, but it introduced unnecessary complexity and impeded other optimizations.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b5b27-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="b5b27-115">Recommended action</span></span>

<span data-ttu-id="b5b27-116">Birim testlerinizde `Mock<DefaultHttpContext>` kullanıyorsanız, bunun yerine `Mock<HttpContext>` kullanmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="b5b27-116">If you're using `Mock<DefaultHttpContext>` in your unit tests, begin using `Mock<HttpContext>` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="b5b27-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="b5b27-117">Category</span></span>

<span data-ttu-id="b5b27-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b5b27-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b5b27-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b5b27-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
