---
ms.openlocfilehash: c634c43e72d345721f2d8f2e9f45760e927a86ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393945"
---
### <a name="authentication-google-deprecated-and-replaced"></a>Kimlik doğrulama: Google+ amortismana uğradı ve değiştirildi

Google, uygulamalar için Google+ Oturum Açma'yı 28 Ocak 2019'dan itibaren [kapatmaya](https://developers.google.com/+/api-shutdown) başlıyor.

#### <a name="change-description"></a>Açıklamayı değiştir

ASP.NET 4.x ve ASP.NET Core, Google hesap kullanıcılarının web uygulamalarındaki kimliğini doğrulamak için Google+ Oturum Açma API'lerini kullanıyor. Etkilenen NuGet paketleri ASP.NET Web Formları ve MVC ile ASP.NET Core ve [Microsoft.Owin.Security.Google](https://www.nuget.org/packages/Microsoft.Owin.Security.Google/) için `Microsoft.Owin` [Microsoft.AspNetCore.Authentication.Google](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Google/) vardır.

Google'ın yedek API'leri farklı bir veri kaynağı ve biçimi kullanır. Aşağıda sağlanan azaltıcı etkenler ve çözümler yapısal değişiklikleri hesaba kattır. Uygulamalar, verilerin gereksinimlerini hala karşıladığından doğrulanmalıdır. Örneğin, adlar, e-posta adresleri, profil bağlantıları ve profil fotoğrafları öncekinden çok farklı değerler sağlayabilir.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

Tüm versiyonları. Bu değişiklik ASP.NET Core'un dışındadır.

#### <a name="recommended-action"></a>Önerilen eylem

##### <a name="owin-with-aspnet-web-forms-and-mvc"></a>ASP.NET Web Formları ve MVC ile Owin

3.1.0 ve sonrası için, `Microsoft.Owin` geçici bir azaltma [burada](https://github.com/aspnet/AspNetKatana/issues/251#issuecomment-449587635)özetlenmiştir. Uygulamalar, veri biçimindeki değişiklikleri denetlemek için azaltma yla testleri tamamlamalıdır. Bir düzeltme ile `Microsoft.Owin` 4.0.1 serbest bırakmak için planlar vardır. Önceki sürümlerden herhangi bir sürümü kullanan uygulamaların sürüm 4.0.1'e güncellemesi gerekir.

##### <a name="aspnet-core-1x"></a>ASP.NET Çekirdek 1.x

[ASP.NET Web Formları ve MVC ile Owin](#owin-with-aspnet-web-forms-and-mvc) azaltma core 1.x ASP.NET adapte edilebilir. 1.x [yaşam durumunun sonuna ulaştığından](https://dotnet.microsoft.com/platform/support-policy) NuGet paket düzeltme emaları planlanmamıştır.

##### <a name="aspnet-core-2x"></a>ASP.NET Çekirdek 2.x

`Microsoft.AspNetCore.Authentication.Google` Sürüm 2.x için, mevcut `AddGoogle` aramanızı aşağıdaki `Startup.ConfigureServices` kodla değiştirin:

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

Şubat 2.1 ve 2.2 yamaları, önceki yeniden yapılandırmayı yeni varsayılan olarak içeriyordu. [Yaşamın sonuna](https://dotnet.microsoft.com/platform/support-policy)ulaştığından ASP.NET Core 2.0 için hiçbir yama planlanmamıştır.

##### <a name="aspnet-core-30"></a>ASP.NET Çekirdek 3.0

Core 2.x ASP.NET için verilen azaltma, Core 3.0'ı ASP.NET için de kullanılabilir. Gelecek 3.0 önizlemelerinde `Microsoft.AspNetCore.Authentication.Google` paket kaldırılabilir. Kullanıcılar `Microsoft.AspNetCore.Authentication.OpenIdConnect` bunun yerine yönlendirilir. Aşağıdaki kod' un `AddGoogle` nasıl `AddOpenIdConnect` `Startup.ConfigureServices`değiştirilen ile değiştirilen Bu değiştirme ASP.NET Core 2.0 ve daha sonra kullanılabilir ve gerektiğinde Core 1.x ASP.NET için uyarlanabilir.

```csharp
.AddOpenIdConnect("Google", o =>
{
    o.ClientId = Configuration["Authentication:Google:ClientId"];
    o.ClientSecret = Configuration["Authentication:Google:ClientSecret"];
    o.Authority = "https://accounts.google.com";
    o.ResponseType = OpenIdConnectResponseType.Code;
    o.CallbackPath = "/signin-google"; // Or register the default "/sigin-oidc"
    o.Scope.Add("email");
});
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();
```

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=fullName>

<!-- 

#### Affected APIs

`N:Microsoft.AspNetCore.Authentication.Google`

-->
