---
ms.openlocfilehash: 60ebcd9fc9ca18c33d31b82ba5020426d22a7d5a
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901704"
---
### <a name="authentication-httpcontextauthentication-property-removed"></a><span data-ttu-id="b6deb-101">Kimlik doğrulaması: HttpContext. Authentication özelliği kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="b6deb-101">Authentication: HttpContext.Authentication property removed</span></span>

<span data-ttu-id="b6deb-102">`HttpContext` üzerinde kullanım dışı `Authentication` özelliği kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b6deb-102">The deprecated `Authentication` property on `HttpContext` has been removed.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b6deb-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="b6deb-103">Change description</span></span>

<span data-ttu-id="b6deb-104">[DotNet/aspnetcore # 6504](https://github.com/dotnet/aspnetcore/pull/6504)bir parçası olarak, `HttpContext` üzerinde kullanım dışı `Authentication` özelliği kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b6deb-104">As part of [dotnet/aspnetcore#6504](https://github.com/dotnet/aspnetcore/pull/6504), the deprecated `Authentication` property on `HttpContext` has been removed.</span></span> <span data-ttu-id="b6deb-105">`Authentication` özelliği 2,0 tarihinden itibaren kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b6deb-105">The `Authentication` property has been deprecated since 2.0.</span></span> <span data-ttu-id="b6deb-106">Kullanım dışı bırakılan bu özelliği kullanarak kodu yeni değiştirme API 'Lerine geçirmek için bir [Geçiş Kılavuzu](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) yayımlandı.</span><span class="sxs-lookup"><span data-stu-id="b6deb-106">A [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) was published to migrate code using this deprecated property to the new replacement APIs.</span></span> <span data-ttu-id="b6deb-107">Eski ASP.NET Core 1. x kimlik doğrulama yığını ile ilgili kalan kullanılmayan sınıflar/API 'Ler, COMMIT [dotnet/aspnetcore@d7a7c65](https://github.com/dotnet/aspnetcore/commit/d7a7c65)kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b6deb-107">The remaining unused classes / APIs related to the old ASP.NET Core 1.x authentication stack were removed in commit [dotnet/aspnetcore@d7a7c65](https://github.com/dotnet/aspnetcore/commit/d7a7c65).</span></span>

<span data-ttu-id="b6deb-108">Tartışma için bkz. [DotNet/aspnetcore # 6533](https://github.com/dotnet/aspnetcore/issues/6533).</span><span class="sxs-lookup"><span data-stu-id="b6deb-108">For discussion, see [dotnet/aspnetcore#6533](https://github.com/dotnet/aspnetcore/issues/6533).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b6deb-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="b6deb-109">Version introduced</span></span>

<span data-ttu-id="b6deb-110">3.0</span><span class="sxs-lookup"><span data-stu-id="b6deb-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b6deb-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="b6deb-111">Reason for change</span></span>

<span data-ttu-id="b6deb-112">ASP.NET Core 1,0 API 'Leri, <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>uzantı yöntemleriyle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b6deb-112">ASP.NET Core 1.0 APIs have been replaced by extension methods in <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName>.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b6deb-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="b6deb-113">Recommended action</span></span>

<span data-ttu-id="b6deb-114">[Geçiş kılavuzuna](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions)bakın.</span><span class="sxs-lookup"><span data-stu-id="b6deb-114">See the [migration guide](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions).</span></span>

#### <a name="category"></a><span data-ttu-id="b6deb-115">Kategori</span><span class="sxs-lookup"><span data-stu-id="b6deb-115">Category</span></span>

<span data-ttu-id="b6deb-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b6deb-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b6deb-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b6deb-117">Affected APIs</span></span>

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
