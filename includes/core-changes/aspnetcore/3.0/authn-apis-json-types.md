---
ms.openlocfilehash: 494e792d63a611cdaedf3e40aa607cfbb0420ae4
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75902044"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a>Kimlik doğrulaması: Newtonsoft. JSON türleri değişti

ASP.NET Core 3,0 ' de, kimlik doğrulama API 'Lerinde kullanılan `Newtonsoft.Json` türler `System.Text.Json` türleriyle değiştirilmiştir. Aşağıdaki durumlar hariç, kimlik doğrulama paketlerinin temel kullanımı etkilenmemiştir:

* , [ASPNET-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers)gibi OAuth sağlayıcılardan türetilmiş sınıflar.
* Gelişmiş talep işleme uygulamaları.

Daha fazla bilgi için bkz. [DotNet/aspnetcore # 7105](https://github.com/dotnet/aspnetcore/pull/7105). Tartışma için bkz. [DotNet/aspnetcore # 7289](https://github.com/dotnet/aspnetcore/issues/7289).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Türetilmiş OAuth uygulamaları için en yaygın değişiklik, [burada](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40)gösterildiği gibi `CreateTicketAsync` geçersiz kılmada `JsonDocument.Parse` `JObject.Parse`. `JsonDocument` `IDisposable`uygular.

Aşağıdaki listede bilinen değişiklikler özetlenmektedir:

- <xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`olur. `ClaimAction` türetilen tüm uygulamalar benzer şekilde etkilenir.
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)` olur
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)` olur
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> eski bir Oluşturucu kaldırılmıştır ve diğer `JObject` `JsonElement`ile değiştirilmiştir. `User` özelliği ve `RunClaimActions` yöntemi eşleşecek şekilde güncelleştirildi.
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> artık `JObject`yerine `JsonDocument` türünde bir parametre kabul eder. `Response` özelliği eşleşecek şekilde güncelleştirildi. `OAuthTokenResponse` artık atılabilir ve `OAuthHandler`tarafından bırakılacak. `ExchangeCodeAsync` geçersiz kılan türetilmiş OAuth uygulamalarının `JsonDocument` veya `OAuthTokenResponse`atma gereksinimi yoktur.
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> `JObject` `JsonDocument`olarak değiştirildi.
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> `JObject` `JsonElement`olarak değiştirildi.
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType>, `JObject` kabul `JsonElement`olarak değiştirildi.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.AspNetCore.Authentication.Facebook?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.Google?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.MicrosoftAccount?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.OAuth?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Authentication.Twitter?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Authentication.Facebook`
- `N:Microsoft.AspNetCore.Authentication.Google`
- `N:Microsoft.AspNetCore.Authentication.MicrosoftAccount`
- `N:Microsoft.AspNetCore.Authentication.OAuth`
- `N:Microsoft.AspNetCore.Authentication.OpenIdConnect`
- `N:Microsoft.AspNetCore.Authentication.Twitter`

-->
