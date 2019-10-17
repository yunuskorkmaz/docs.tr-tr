---
ms.openlocfilehash: 177617569a93e09f4c2a05acc21dce362edd58bc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394013"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a><span data-ttu-id="7f658-101">HTTP: DefaultHttpContext genişletilebilirliği kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="7f658-101">HTTP: DefaultHttpContext extensibility removed</span></span>

<span data-ttu-id="7f658-102">ASP.NET Core 3,0 performans geliştirmelerinden bir parçası olarak, `DefaultHttpContext` ' ın genişletilebilirliği kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="7f658-102">As part of ASP.NET Core 3.0 performance improvements, the extensibility of `DefaultHttpContext` was removed.</span></span> <span data-ttu-id="7f658-103">Sınıf artık `sealed` ' dır.</span><span class="sxs-lookup"><span data-stu-id="7f658-103">The class is now `sealed`.</span></span> <span data-ttu-id="7f658-104">Daha fazla bilgi için bkz. [ASPNET/AspNetCore # 6504](https://github.com/aspnet/AspNetCore/pull/6504).</span><span class="sxs-lookup"><span data-stu-id="7f658-104">For more information, see [aspnet/AspNetCore#6504](https://github.com/aspnet/AspNetCore/pull/6504).</span></span>

<span data-ttu-id="7f658-105">Birim testleriniz `Mock<DefaultHttpContext>` kullanıyorsa, bunun yerine `Mock<HttpContext>` kullanın.</span><span class="sxs-lookup"><span data-stu-id="7f658-105">If your unit tests use `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` instead.</span></span> 

<span data-ttu-id="7f658-106">Tartışma için bkz. [ASPNET/AspNetCore # 6534](https://github.com/aspnet/AspNetCore/issues/6534).</span><span class="sxs-lookup"><span data-stu-id="7f658-106">For discussion, see [aspnet/AspNetCore#6534](https://github.com/aspnet/AspNetCore/issues/6534).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7f658-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7f658-107">Version introduced</span></span>

<span data-ttu-id="7f658-108">3.0</span><span class="sxs-lookup"><span data-stu-id="7f658-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7f658-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="7f658-109">Old behavior</span></span>

<span data-ttu-id="7f658-110">Sınıflar `DefaultHttpContext` ' dan türetilebilir.</span><span class="sxs-lookup"><span data-stu-id="7f658-110">Classes can derive from `DefaultHttpContext`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="7f658-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="7f658-111">New behavior</span></span>

<span data-ttu-id="7f658-112">Sınıflar `DefaultHttpContext` ' dan türetilemez.</span><span class="sxs-lookup"><span data-stu-id="7f658-112">Classes can't derive from `DefaultHttpContext`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7f658-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="7f658-113">Reason for change</span></span>

<span data-ttu-id="7f658-114">Genişletilebilirlik başlangıçta `HttpContext` ' a havuza izin vermek için sağlanmış, ancak gereksiz karmaşıklık ve daha önce diğer iyileştirmeler getirmiştir.</span><span class="sxs-lookup"><span data-stu-id="7f658-114">The extensibility was provided initially to allow pooling of the `HttpContext`, but it introduced unnecessary complexity and impeded other optimizations.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7f658-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="7f658-115">Recommended action</span></span>

<span data-ttu-id="7f658-116">Birim testlerinizde `Mock<DefaultHttpContext>` kullanıyorsanız, bunun yerine `Mock<HttpContext>` ' i kullanmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="7f658-116">If you're using `Mock<DefaultHttpContext>` in your unit tests, begin using `Mock<HttpContext>` instead.</span></span> 

#### <a name="category"></a><span data-ttu-id="7f658-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="7f658-117">Category</span></span>

<span data-ttu-id="7f658-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7f658-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7f658-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7f658-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
