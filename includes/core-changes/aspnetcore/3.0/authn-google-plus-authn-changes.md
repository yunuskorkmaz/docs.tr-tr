---
ms.openlocfilehash: 14d80f25c34465caa6dec10e5704fe0a3cbccc71
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96477281"
---
### <a name="authentication-google-deprecated-and-replaced"></a>Kimlik doğrulaması: Google + kullanım dışı ve değiştirilmiş

Google, ilk olarak 28 Ocak 2019 tarihinden itibaren, uygulamalar için Google + oturum açmayı [kapatmaya](https://developers.google.com/+/api-shutdown) başlıyor.

#### <a name="change-description"></a>Açıklamayı Değiştir

ASP.NET 4. x ve ASP.NET Core, Web Apps 'te Google hesabı kullanıcılarının kimliğini doğrulamak için Google + oturum açma API 'Lerini kullanıyor. Etkilenen NuGet paketleri, ASP.NET Web Forms ve MVC ile için [Microsoft. AspNetCore. Authentication. Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) for ASP.NET Core ve [Microsoft. Owin. Security. Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) ' dir `Microsoft.Owin` .

Google 'ın değiştirme API 'Leri farklı bir veri kaynağı ve biçimi kullanır. Yapısal değişiklikler için aşağıda belirtilen Azaltıcı Etkenler ve çözümler. Uygulamalar, verilerin hala gereksinimlerini karşıladığından emin olmalıdır. Örneğin adlar, e-posta adresleri, profil bağlantıları ve profil fotoğrafları, daha önce daha çok farklı değerler sağlayabilir.

#### <a name="version-introduced"></a>Sunulan sürüm

Tüm sürümler. Bu değişiklik ASP.NET Core dış.

#### <a name="recommended-action"></a>Önerilen eylem

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a>ASP.NET Web Forms ve MVC ile Owin

`Microsoft.Owin`3.1.0 ve üzeri için geçici bir risk azaltma [burada](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635)özetlenmiştir. Uygulamalar, veri biçimindeki değişiklikleri denetlemek için azaltma ile testi tamamlamalıdır. 4.0.1 'i bir düzeltmeyle yayınlama planları vardır `Microsoft.Owin` . Önceki sürümleri kullanan uygulamalar 4.0.1 sürümüne güncellemelidir.

##### <a name="aspnet-core-1x"></a>ASP.NET Core 1. x

[Owin ASP.NET Web Forms ve MVC ile olan](#owin-with-aspnet-web-forms-and-mvc) azaltıcı etken, 1. x ASP.NET Core uyarlanabilirler. 1. x, [yaşam durumunun sonuna](https://dotnet.microsoft.com/platform/support-policy) ulaştığı için NuGet paket yamaları planlanmadı.

##### <a name="aspnet-core-2x"></a>ASP.NET Core 2. x

`Microsoft.AspNetCore.Authentication.Google`Sürüm 2. x için, mevcut çağrlarınızı `AddGoogle` `Startup.ConfigureServices` aşağıdaki kodla değiştirin:

```csharp
.AddGoogle(o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.UserInformationEndpoint = "https://www.googleapis.com/oauth2/v2/userinfo";
    o.ClaimActions.Clear();
    o.ClaimActions.MapJsonKey(ClaimTypes.NameIdentifier, "id");
    o.ClaimActions.MapJsonKey(ClaimTypes.Name, "name");
    o.ClaimActions.MapJsonKey(ClaimTypes.GivenName, "given_name");
    o.ClaimActions.MapJsonKey(ClaimTypes.Surname, "family_name");
    o.ClaimActions.MapJsonKey("urn:google:profile", "link");
    o.ClaimActions.MapJsonKey(ClaimTypes.Email, "email");
});
```

Şubat 2,1 ve 2,2 yamaları önceki yeniden yapılandırma yeni varsayılan olarak eklenmiştir. ASP.NET Core 2,0 için bir düzeltme eki planlanmıyor çünkü [yaşam sonuna](https://dotnet.microsoft.com/platform/support-policy)ulaştı.

##### <a name="aspnet-core-30"></a>ASP.NET Core 3,0

ASP.NET Core 2. x için verilen risk azaltma, ASP.NET Core 3,0 için de kullanılabilir. Gelecekteki 3,0 önizlemelerde `Microsoft.AspNetCore.Authentication.Google` paket kaldırılabilir. Kullanıcılar, `Microsoft.AspNetCore.Authentication.OpenIdConnect` bunun yerine öğesine yönlendirilir. Aşağıdaki kod, içindeki ile nasıl değiştirileceğini `AddGoogle` gösterir `AddOpenIdConnect` `Startup.ConfigureServices` . Bu değişiklik, ASP.NET Core 2,0 ve üzeri sürümlerle kullanılabilir ve gerektiğinde ASP.NET Core 1. x için uyarlanmıştır.

```csharp
.AddOpenIdConnect("Google", o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.Authority = "https://accounts.google.com";
    o.ResponseType = OpenIdConnectResponseType.Code;
    o.CallbackPath = "/signin-google"; // Or register the default "/signin-oidc"
    o.Scope.Add("email");
});
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();
```

#### <a name="category"></a>Category

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
