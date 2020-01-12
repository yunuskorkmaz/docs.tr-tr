---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901773"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a><span data-ttu-id="5aa43-101">Yetkilendirme: ıauthorizationpolicyprovider uygulamaları için yeni yöntem gerekir</span><span class="sxs-lookup"><span data-stu-id="5aa43-101">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>

<span data-ttu-id="5aa43-102">ASP.NET Core 3,0 ' de, `IAuthorizationPolicyProvider`yeni bir `GetFallbackPolicyAsync` yöntemi eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="5aa43-102">In ASP.NET Core 3.0, a new `GetFallbackPolicyAsync` method was added to `IAuthorizationPolicyProvider`.</span></span> <span data-ttu-id="5aa43-103">Bu geri dönüş ilkesi, ilke belirtilmediğinde yetkilendirme ara yazılımı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5aa43-103">This fallback policy is used by the authorization middleware when no policy is specified.</span></span>

<span data-ttu-id="5aa43-104">Daha fazla bilgi için bkz. [DotNet/aspnetcore # 9759](https://github.com/dotnet/aspnetcore/pull/9759).</span><span class="sxs-lookup"><span data-stu-id="5aa43-104">For more information, see [dotnet/aspnetcore#9759](https://github.com/dotnet/aspnetcore/pull/9759).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5aa43-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5aa43-105">Version introduced</span></span>

<span data-ttu-id="5aa43-106">3.0</span><span class="sxs-lookup"><span data-stu-id="5aa43-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5aa43-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="5aa43-107">Old behavior</span></span>

<span data-ttu-id="5aa43-108">`IAuthorizationPolicyProvider` uygulamalarında `GetFallbackPolicyAsync` yöntemi gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="5aa43-108">Implementations of `IAuthorizationPolicyProvider` didn't require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="5aa43-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="5aa43-109">New behavior</span></span>

<span data-ttu-id="5aa43-110">`IAuthorizationPolicyProvider` uygulamaları `GetFallbackPolicyAsync` bir yöntem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5aa43-110">Implementations of `IAuthorizationPolicyProvider` require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5aa43-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="5aa43-111">Reason for change</span></span>

<span data-ttu-id="5aa43-112">Yeni `AuthorizationMiddleware` bir ilke belirtilmediğinde kullanması için yeni bir yöntem gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="5aa43-112">A new method was needed for the new `AuthorizationMiddleware` to use when no policy is specified.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5aa43-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="5aa43-113">Recommended action</span></span>

<span data-ttu-id="5aa43-114">`GetFallbackPolicyAsync` yöntemini `IAuthorizationPolicyProvider`uygulamanıza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5aa43-114">Add the `GetFallbackPolicyAsync` method to your implementations of `IAuthorizationPolicyProvider`.</span></span>

#### <a name="category"></a><span data-ttu-id="5aa43-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="5aa43-115">Category</span></span>

<span data-ttu-id="5aa43-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5aa43-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5aa43-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="5aa43-117">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
