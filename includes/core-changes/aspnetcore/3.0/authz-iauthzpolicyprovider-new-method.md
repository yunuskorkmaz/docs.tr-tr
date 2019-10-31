---
ms.openlocfilehash: 74b989a2413d2192f7cf5208e400eaed879ea096
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198587"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a><span data-ttu-id="045a9-101">Yetkilendirme: ıauthorizationpolicyprovider uygulamaları için yeni yöntem gerekir</span><span class="sxs-lookup"><span data-stu-id="045a9-101">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>

<span data-ttu-id="045a9-102">ASP.NET Core 3,0 ' de, yeni bir `GetFallbackPolicyAsync` yöntemi `IAuthorizationPolicyProvider` ' e eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="045a9-102">In ASP.NET Core 3.0, a new `GetFallbackPolicyAsync` method was added to `IAuthorizationPolicyProvider`.</span></span> <span data-ttu-id="045a9-103">Bu geri dönüş ilkesi, ilke belirtilmediğinde yetkilendirme ara yazılımı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="045a9-103">This fallback policy is used by the authorization middleware when no policy is specified.</span></span>

<span data-ttu-id="045a9-104">Daha fazla bilgi için bkz. [ASPNET/AspNetCore # 9759](https://github.com/aspnet/AspNetCore/pull/9759).</span><span class="sxs-lookup"><span data-stu-id="045a9-104">For more information, see [aspnet/AspNetCore#9759](https://github.com/aspnet/AspNetCore/pull/9759).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="045a9-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="045a9-105">Version introduced</span></span>

<span data-ttu-id="045a9-106">3.0</span><span class="sxs-lookup"><span data-stu-id="045a9-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="045a9-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="045a9-107">Old behavior</span></span>

<span data-ttu-id="045a9-108">`IAuthorizationPolicyProvider` uygulamalarında `GetFallbackPolicyAsync` yöntemi gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="045a9-108">Implementations of `IAuthorizationPolicyProvider` didn't require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="045a9-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="045a9-109">New behavior</span></span>

<span data-ttu-id="045a9-110">`IAuthorizationPolicyProvider` uygulamaları `GetFallbackPolicyAsync` bir yöntem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="045a9-110">Implementations of `IAuthorizationPolicyProvider` require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="045a9-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="045a9-111">Reason for change</span></span>

<span data-ttu-id="045a9-112">Yeni `AuthorizationMiddleware` bir ilke belirtilmediğinde kullanması için yeni bir yöntem gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="045a9-112">A new method was needed for the new `AuthorizationMiddleware` to use when no policy is specified.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="045a9-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="045a9-113">Recommended action</span></span>

<span data-ttu-id="045a9-114">`GetFallbackPolicyAsync` yöntemini `IAuthorizationPolicyProvider`uygulamanıza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="045a9-114">Add the `GetFallbackPolicyAsync` method to your implementations of `IAuthorizationPolicyProvider`.</span></span>

#### <a name="category"></a><span data-ttu-id="045a9-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="045a9-115">Category</span></span>

<span data-ttu-id="045a9-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="045a9-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="045a9-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="045a9-117">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
