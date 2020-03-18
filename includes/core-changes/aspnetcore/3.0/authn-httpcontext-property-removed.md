---
ms.openlocfilehash: 60ebcd9fc9ca18c33d31b82ba5020426d22a7d5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901704"
---
### <a name="authentication-httpcontextauthentication-property-removed"></a><span data-ttu-id="448f4-101">Kimlik doğrulama: HttpContext.Authentication özelliği kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="448f4-101">Authentication: HttpContext.Authentication property removed</span></span>

<span data-ttu-id="448f4-102">Üzerinde `HttpContext` amortismana `Authentication` alınan özellik kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="448f4-102">The deprecated `Authentication` property on `HttpContext` has been removed.</span></span>

#### <a name="change-description"></a><span data-ttu-id="448f4-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="448f4-103">Change description</span></span>

<span data-ttu-id="448f4-104">[dotnet/aspnetcore#6504'ün](https://github.com/dotnet/aspnetcore/pull/6504)bir parçası olarak, `Authentication` amortismana `HttpContext` alınan özellik kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="448f4-104">As part of [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504), the deprecated `Authentication` property on `HttpContext` has been removed.</span></span> <span data-ttu-id="448f4-105">Mülk `Authentication` 2,0'dan beri amortismana uymuş.</span><span class="sxs-lookup"><span data-stu-id="448f4-105">The `Authentication` property has been deprecated since 2.0.</span></span> <span data-ttu-id="448f4-106">Bu amortismana neden olan özelliği kullanarak kodu yeni yedek API'lere geçirmek için bir [geçiş kılavuzu](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) yayımlandı.</span><span class="sxs-lookup"><span data-stu-id="448f4-106">A [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) was published to migrate code using this deprecated property to the new replacement APIs.</span></span> <span data-ttu-id="448f4-107">Eski ASP.NET Core 1.x kimlik doğrulama yığınıile ilgili kalan kullanılmayan sınıflar [dotnet/aspnetcore@d7a7c65](https://github.com/dotnet/aspnetcore/commit/d7a7c65)/ API'ler commit'de kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="448f4-107">The remaining unused classes / APIs related to the old ASP.NET Core 1.x authentication stack were removed in commit [dotnet/aspnetcore@d7a7c65](https://github.com/dotnet/aspnetcore/commit/d7a7c65).</span></span>

<span data-ttu-id="448f4-108">Tartışma için [dotnet/aspnetcore#6533'e](https://github.com/dotnet/aspnetcore/issues/6533)bakın.</span><span class="sxs-lookup"><span data-stu-id="448f4-108">For discussion, see [dotnet/aspnetcore#6533](https://github.com/dotnet/aspnetcore/issues/6533).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="448f4-109">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="448f4-109">Version introduced</span></span>

<span data-ttu-id="448f4-110">3,0</span><span class="sxs-lookup"><span data-stu-id="448f4-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="448f4-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="448f4-111">Reason for change</span></span>

<span data-ttu-id="448f4-112">ASP.NET Core 1.0 API'leri <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>uzantısı yöntemleri ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="448f4-112">ASP.NET Core 1.0 APIs have been replaced by extension methods in <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="448f4-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="448f4-113">Recommended action</span></span>

<span data-ttu-id="448f4-114">Geçiş [kılavuzuna](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions)bakın.</span><span class="sxs-lookup"><span data-stu-id="448f4-114">See the [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions).</span></span>

#### <a name="category"></a><span data-ttu-id="448f4-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="448f4-115">Category</span></span>

<span data-ttu-id="448f4-116">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="448f4-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="448f4-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="448f4-117">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.Authentication.AuthenticateInfo?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Authentication.AuthenticationManager?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Authentication.AuthenticationProperties?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.AuthenticateContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeBehavior?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.DescribeSchemesContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.IAuthenticationHandler?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.IHttpAuthenticationFeature.Handler?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.SignInContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.Authentication.SignOutContext?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpContext.Authentication?displayProperty=fullName>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Authentication.AuthenticateInfo`
- `T:Microsoft.AspNetCore.Http.Authentication.AuthenticationManager`
- `T:Microsoft.AspNetCore.Http.Authentication.AuthenticationProperties`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.AuthenticateContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeBehavior`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.ChallengeContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.DescribeSchemesContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.IAuthenticationHandler`
- `P:Microsoft.AspNetCore.Http.Features.Authentication.IHttpAuthenticationFeature.Handler`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.SignInContext`
- `T:Microsoft.AspNetCore.Http.Features.Authentication.SignOutContext`
- `P:Microsoft.AspNetCore.Http.HttpContext.Authentication`

-->
