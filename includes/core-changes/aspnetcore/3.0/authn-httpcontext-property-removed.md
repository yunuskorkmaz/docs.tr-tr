---
ms.openlocfilehash: 2945465bb6a3a362dc640641056712dffd73d559
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394054"
---
### <a name="authentication-httpcontextauthentication-property-removed"></a>Kimlik doğrulaması: HttpContext. Authentication özelliği kaldırıldı

@No__t-1 ' deki kullanım dışı `Authentication` özelliği kaldırılmıştır.

#### <a name="change-description"></a>Açıklamayı Değiştir

[ASPNET/AspNetCore # 6504](https://github.com/aspnet/AspNetCore/pull/6504)'ın bir parçası olarak, `HttpContext` ' de kullanım dışı `Authentication` özelliği kaldırılmıştır. @No__t-0 özelliği 2,0 tarihinden itibaren kullanımdan kaldırılmıştır. Kullanım dışı bırakılan bu özelliği kullanarak kodu yeni değiştirme API 'Lerine geçirmek için bir [Geçiş Kılavuzu](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions) yayımlandı. Eski ASP.NET Core 1. x kimlik doğrulama yığını ile ilgili kalan kullanılmayan sınıflar/API 'Ler, COMMIT [aspnet/AspNetCore@d7a7c65](https://github.com/aspnet/AspNetCore/commit/d7a7c65)' de kaldırılmıştır.

Tartışma için bkz. [ASPNET/AspNetCore # 6533](https://github.com/aspnet/AspNetCore/issues/6533).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="reason-for-change"></a>Değişiklik nedeni

ASP.NET Core 1,0 API 'Leri, <xref:Microsoft.AspNetCore.Authentication.AuthenticationHttpContextExtensions?displayProperty=fullName> ' daki uzantı yöntemleriyle değiştirilmiştir.

#### <a name="recommended-action"></a>Önerilen eylem

[Geçiş kılavuzuna](/aspnet/core/migration/1x-to-2x/identity-2x?view=aspnetcore-2.2#use-httpcontext-authentication-extensions)bakın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

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
