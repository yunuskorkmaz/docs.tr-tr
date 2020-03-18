---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901773"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a><span data-ttu-id="cdb8a-101">Yetkilendirme: IAuthorizationPolicyProvider uygulamaları yeni bir yöntem gerektirir</span><span class="sxs-lookup"><span data-stu-id="cdb8a-101">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>

<span data-ttu-id="cdb8a-102">core 3.0ASP.NETde `IAuthorizationPolicyProvider`yeni `GetFallbackPolicyAsync` bir yöntem eklendi.</span><span class="sxs-lookup"><span data-stu-id="cdb8a-102">In ASP.NET Core 3.0, a new `GetFallbackPolicyAsync` method was added to `IAuthorizationPolicyProvider`.</span></span> <span data-ttu-id="cdb8a-103">Bu geri dönüş ilkesi, hiçbir ilke belirtilmediğinde yetkilendirme aracı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cdb8a-103">This fallback policy is used by the authorization middleware when no policy is specified.</span></span>

<span data-ttu-id="cdb8a-104">Daha fazla bilgi için [dotnet/aspnetcore#9759'a](https://github.com/dotnet/aspnetcore/pull/9759)bakın.</span><span class="sxs-lookup"><span data-stu-id="cdb8a-104">For more information, see [dotnet/aspnetcore#9759](https://github.com/dotnet/aspnetcore/pull/9759).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cdb8a-105">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="cdb8a-105">Version introduced</span></span>

<span data-ttu-id="cdb8a-106">3,0</span><span class="sxs-lookup"><span data-stu-id="cdb8a-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="cdb8a-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="cdb8a-107">Old behavior</span></span>

<span data-ttu-id="cdb8a-108">Uygulamaları bir `IAuthorizationPolicyProvider` `GetFallbackPolicyAsync` yöntem gerektirmedi.</span><span class="sxs-lookup"><span data-stu-id="cdb8a-108">Implementations of `IAuthorizationPolicyProvider` didn't require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="cdb8a-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="cdb8a-109">New behavior</span></span>

<span data-ttu-id="cdb8a-110">Uygulamaları bir `IAuthorizationPolicyProvider` `GetFallbackPolicyAsync` yöntem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cdb8a-110">Implementations of `IAuthorizationPolicyProvider` require a `GetFallbackPolicyAsync` method.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="cdb8a-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="cdb8a-111">Reason for change</span></span>

<span data-ttu-id="cdb8a-112">İlke belirtilmediğinde yeninin `AuthorizationMiddleware` kullanması için yeni bir yöntem gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="cdb8a-112">A new method was needed for the new `AuthorizationMiddleware` to use when no policy is specified.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cdb8a-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="cdb8a-113">Recommended action</span></span>

<span data-ttu-id="cdb8a-114">Uygulamalarınıza `GetFallbackPolicyAsync` yöntemi `IAuthorizationPolicyProvider`ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cdb8a-114">Add the `GetFallbackPolicyAsync` method to your implementations of `IAuthorizationPolicyProvider`.</span></span>

#### <a name="category"></a><span data-ttu-id="cdb8a-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="cdb8a-115">Category</span></span>

<span data-ttu-id="cdb8a-116">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="cdb8a-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cdb8a-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="cdb8a-117">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
