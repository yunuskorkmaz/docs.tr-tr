---
ms.openlocfilehash: 7b5ae84d02b83a10a4b9e002fc2ed4ee0833b84c
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198596"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a><span data-ttu-id="9f69b-101">HTTP: DefaultHttpContext genişletilebilirliği kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="9f69b-101">HTTP: DefaultHttpContext extensibility removed</span></span>

<span data-ttu-id="9f69b-102">ASP.NET Core 3,0 performans geliştirmelerinden bir parçası olarak, `DefaultHttpContext` ' ın genişletilebilirliği kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="9f69b-102">As part of ASP.NET Core 3.0 performance improvements, the extensibility of `DefaultHttpContext` was removed.</span></span> <span data-ttu-id="9f69b-103">Sınıf artık `sealed` ' dır.</span><span class="sxs-lookup"><span data-stu-id="9f69b-103">The class is now `sealed`.</span></span> <span data-ttu-id="9f69b-104">Daha fazla bilgi için bkz. [ASPNET/AspNetCore # 6504](https://github.com/aspnet/AspNetCore/pull/6504).</span><span class="sxs-lookup"><span data-stu-id="9f69b-104">For more information, see [aspnet/AspNetCore#6504](https://github.com/aspnet/AspNetCore/pull/6504).</span></span>

<span data-ttu-id="9f69b-105">Birim testleriniz `Mock<DefaultHttpContext>` kullanıyorsa, bunun yerine `Mock<HttpContext>` kullanın.</span><span class="sxs-lookup"><span data-stu-id="9f69b-105">If your unit tests use `Mock<DefaultHttpContext>`, use `Mock<HttpContext>` instead.</span></span>

<span data-ttu-id="9f69b-106">Tartışma için bkz. [ASPNET/AspNetCore # 6534](https://github.com/aspnet/AspNetCore/issues/6534).</span><span class="sxs-lookup"><span data-stu-id="9f69b-106">For discussion, see [aspnet/AspNetCore#6534](https://github.com/aspnet/AspNetCore/issues/6534).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9f69b-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="9f69b-107">Version introduced</span></span>

<span data-ttu-id="9f69b-108">3.0</span><span class="sxs-lookup"><span data-stu-id="9f69b-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9f69b-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="9f69b-109">Old behavior</span></span>

<span data-ttu-id="9f69b-110">Sınıflar `DefaultHttpContext` ' dan türetilebilir.</span><span class="sxs-lookup"><span data-stu-id="9f69b-110">Classes can derive from `DefaultHttpContext`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9f69b-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="9f69b-111">New behavior</span></span>

<span data-ttu-id="9f69b-112">Sınıflar `DefaultHttpContext` ' dan türetilemez.</span><span class="sxs-lookup"><span data-stu-id="9f69b-112">Classes can't derive from `DefaultHttpContext`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9f69b-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="9f69b-113">Reason for change</span></span>

<span data-ttu-id="9f69b-114">Genişletilebilirlik başlangıçta `HttpContext` ' a havuza izin vermek için sağlanmış, ancak gereksiz karmaşıklık ve daha önce diğer iyileştirmeler getirmiştir.</span><span class="sxs-lookup"><span data-stu-id="9f69b-114">The extensibility was provided initially to allow pooling of the `HttpContext`, but it introduced unnecessary complexity and impeded other optimizations.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9f69b-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="9f69b-115">Recommended action</span></span>

<span data-ttu-id="9f69b-116">Birim testlerinizde `Mock<DefaultHttpContext>` kullanıyorsanız, bunun yerine `Mock<HttpContext>` ' i kullanmaya başlayın.</span><span class="sxs-lookup"><span data-stu-id="9f69b-116">If you're using `Mock<DefaultHttpContext>` in your unit tests, begin using `Mock<HttpContext>` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="9f69b-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="9f69b-117">Category</span></span>

<span data-ttu-id="9f69b-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9f69b-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9f69b-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9f69b-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
