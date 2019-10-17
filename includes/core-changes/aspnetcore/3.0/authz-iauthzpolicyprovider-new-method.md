---
ms.openlocfilehash: a16d443a37fb0bb5f6bdc4a39e7dcb4f91c54ead
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394249"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a><span data-ttu-id="a7386-101">Yetkilendirme: ıauthorizationpolicyprovider uygulamaları için yeni yöntem gerekir</span><span class="sxs-lookup"><span data-stu-id="a7386-101">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>

<span data-ttu-id="a7386-102">ASP.NET Core 3,0 ' de, yeni bir `GetFallbackPolicyAsync` yöntemi `IAuthorizationPolicyProvider` ' e eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="a7386-102">In ASP.NET Core 3.0, a new `GetFallbackPolicyAsync` method was added to `IAuthorizationPolicyProvider`.</span></span> <span data-ttu-id="a7386-103">Bu geri dönüş ilkesi, ilke belirtilmediğinde yetkilendirme ara yazılımı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a7386-103">This fallback policy is used by the authorization middleware when no policy is specified.</span></span>

<span data-ttu-id="a7386-104">Daha fazla bilgi için bkz. [ASPNET/AspNetCore # 9759](https://github.com/aspnet/AspNetCore/pull/9759).</span><span class="sxs-lookup"><span data-stu-id="a7386-104">For more information, see [aspnet/AspNetCore#9759](https://github.com/aspnet/AspNetCore/pull/9759).</span></span> 

#### <a name="version-introduced"></a><span data-ttu-id="a7386-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a7386-105">Version introduced</span></span>

<span data-ttu-id="a7386-106">3.0</span><span class="sxs-lookup"><span data-stu-id="a7386-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a7386-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="a7386-107">Old behavior</span></span>

<span data-ttu-id="a7386-108">@No__t-0 uygulamaları `GetFallbackPolicyAsync` yöntemi gerektirmiyor.</span><span class="sxs-lookup"><span data-stu-id="a7386-108">Implementations of `IAuthorizationPolicyProvider` didn't require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a7386-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="a7386-109">New behavior</span></span>

<span data-ttu-id="a7386-110">@No__t-0 uygulamaları `GetFallbackPolicyAsync` yöntemi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a7386-110">Implementations of `IAuthorizationPolicyProvider` require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a7386-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="a7386-111">Reason for change</span></span>

<span data-ttu-id="a7386-112">Yeni @no__t için yeni bir yöntem gerekiyordu, hiçbir ilke belirtilmediğinde kullanılacak-0.</span><span class="sxs-lookup"><span data-stu-id="a7386-112">A new method was needed for the new `AuthorizationMiddleware` to use when no policy is specified.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a7386-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a7386-113">Recommended action</span></span>

<span data-ttu-id="a7386-114">@No__t-0 yöntemini `IAuthorizationPolicyProvider` ' in uygulamalarına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a7386-114">Add the `GetFallbackPolicyAsync` method to your implementations of `IAuthorizationPolicyProvider`.</span></span>

#### <a name="category"></a><span data-ttu-id="a7386-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="a7386-115">Category</span></span>

<span data-ttu-id="a7386-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a7386-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a7386-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a7386-117">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
