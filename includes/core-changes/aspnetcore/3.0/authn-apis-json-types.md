---
ms.openlocfilehash: 9bdfcca2fd03e24a636be3340f5057dc3f39358e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539611"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a>Kimlik doğrulaması: değiştirilmekte olan türler üzerinde Newtonsoft.Js

ASP.NET Core 3,0 ' de, `Newtonsoft.Json` kimlik doğrulama API 'lerinde kullanılan türler türlerle değiştirilmiştir `System.Text.Json` . Aşağıdaki durumlar hariç, kimlik doğrulama paketlerinin temel kullanımı etkilenmemiştir:

* , [ASPNET-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers)gibi OAuth sağlayıcılardan türetilmiş sınıflar.
* Gelişmiş talep işleme uygulamaları.

Daha fazla bilgi için bkz. [DotNet/aspnetcore # 7105](https://github.com/dotnet/aspnetcore/pull/7105). Tartışma için bkz. [DotNet/aspnetcore # 7289](https://github.com/dotnet/aspnetcore/issues/7289).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="recommended-action"></a>Önerilen eylem

Türetilmiş OAuth uygulamaları için en yaygın değişiklik, `JObject.Parse` `JsonDocument.Parse` `CreateTicketAsync` [burada](https://github.com/dotnet/aspnetcore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40)gösterildiği gibi, geçersiz kılmada ile değiştirilebilir. `JsonDocument` uygular `IDisposable` .

Aşağıdaki listede bilinen değişiklikler özetlenmektedir:

- <xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> olur `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)` . Tüm türetilmiş uygulamaları `ClaimAction` benzer şekilde etkilenir.
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> geldiğinde `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> geldiğinde `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> Eski bir Oluşturucu kaldırılmış ve diğeri `JObject` ile değiştirildi `JsonElement` . `User`Özelliği ve `RunClaimActions` yöntemi eşleşecek şekilde güncelleştirildi.
- <xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> Artık yerine türünde bir parametre kabul eder `JsonDocument` `JObject` . `Response`Özellik eşleşecek şekilde güncelleştirildi. `OAuthTokenResponse` Artık atılabilir ve tarafından aktiften kaldırılacak `OAuthHandler` . Türetilmiş OAuth uygulamalarının üzerine yazma `ExchangeCodeAsync` , veya öğesini atmak zorunda değildir `JsonDocument` `OAuthTokenResponse` .
- <xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> iken `JObject` olarak değiştirildi `JsonDocument` .
- <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> iken `JObject` olarak değiştirildi `JsonElement` .
- ' [Dallı, '. CreateTicketAsync (ClaimsIdentity, AuthenticationProperties, AccessToken, JObject)](/dotnet/api/microsoft.aspnetcore.authentication.twitter.twitterhandler.createticketasync?view=aspnetcore-2.2#Microsoft_AspNetCore_Authentication_Twitter_TwitterHandler_CreateTicketAsync_System_Security_Claims_ClaimsIdentity_Microsoft_AspNetCore_Authentication_AuthenticationProperties_Microsoft_AspNetCore_Authentication_Twitter_AccessToken_Newtonsoft_Json_Linq_JObject_) öğesinin son parametresi olarak değiştirildi `JObject` `JsonElement` . Değiştirme yöntemi <xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,System.Text.Json.JsonElement)?displayProperty=nameWithType> .

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
