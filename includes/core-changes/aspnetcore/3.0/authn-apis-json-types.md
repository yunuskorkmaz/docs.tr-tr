---
ms.openlocfilehash: b4499637cd5fff015335e0cdb3c6cf1c3ea6cff0
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81637190"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a>Kimlik doğrulama: Newtonsoft.Json türleri değiştirildi

Core 3.0ASP.NET, `Newtonsoft.Json` Kimlik Doğrulama API'lerinde kullanılan `System.Text.Json` türler türleri ile değiştirilmiştir. Aşağıdaki durumlar dışında, Kimlik Doğrulama paketlerinin temel kullanımı etkilenmez:

* [Aspnet-contrib'den](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers)olanlar gibi OAuth sağlayıcılarından türetilen sınıflar.
* Gelişmiş talep manipülasyon uygulamaları.

Daha fazla bilgi için [dotnet/aspnetcore#7105'e](https://github.com/dotnet/aspnetcore/pull/7105)bakın. Tartışma için [dotnet/aspnetcore#7289'a](https://github.com/dotnet/aspnetcore/issues/7289)bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="recommended-action"></a>Önerilen eylem

Türemiş OAuth uygulamaları için, en `JObject.Parse` yaygın `JsonDocument.Parse` değişiklik `CreateTicketAsync` [burada](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40)gösterildiği gibi geçersiz kılma ile değiştirmektir. `JsonDocument``IDisposable`uygular.

Aşağıdaki liste bilinen değişiklikleri özetleyerek:

- <xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType>olur. `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)` Tüm türetilmiş `ClaimAction` uygulamalar benzer şekilde etkilenir.
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType>Olur`MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType>Olur`MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext>eski bir yapıcı kaldırıldı ve diğer `JObject` ile `JsonElement`değiştirildi . Özellik `User` ve `RunClaimActions` yöntem eşleşecek şekilde güncelleştirildi.
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)>şimdi yerine tür `JsonDocument` bir parametre `JObject`kabul eder. Özellik `Response` eşleşecek şekilde güncelleştirildi. `OAuthTokenResponse`şimdi tek kullanımlık ve `OAuthHandler`tarafından bertaraf edilecektir . Türetilmiş OAuth `ExchangeCodeAsync` uygulamaları geçersiz veya elden `JsonDocument` `OAuthTokenResponse`çıkarmak gerekmez.
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType>'den' `JsonDocument`e `JObject` değiştirildi.
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType>'den' `JsonElement`e `JObject` değiştirildi.
- [TwitterHandler.CreateTicketAsync(ClaimsIdentity,AuthenticationProperties,AccessToken,JObject)](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.authentication.twitter.twitterhandler.createticketasync?view=aspnetcore-2.2#Microsoft_AspNetCore_Authentication_Twitter_TwitterHandler_CreateTicketAsync_System_Security_Claims_ClaimsIdentity_Microsoft_AspNetCore_Authentication_AuthenticationProperties_Microsoft_AspNetCore_Authentication_Twitter_AccessToken_Newtonsoft_Json_Linq_JObject_) son parametresi `JObject` `JsonElement`değiştirildi. Değiştirme yöntemi <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,System.Text.Json.JsonElement)?displayProperty=nameWithType>.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

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
