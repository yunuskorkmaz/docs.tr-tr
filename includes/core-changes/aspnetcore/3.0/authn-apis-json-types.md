---
ms.openlocfilehash: ad451329d7b9ec15bc8b3c49159346d79944d692
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394258"
---
### <a name="authentication-newtonsoftjson-types-replaced"></a><span data-ttu-id="7a7e5-101">Kimlik doğrulaması: Newtonsoft. JSON türleri değişti</span><span class="sxs-lookup"><span data-stu-id="7a7e5-101">Authentication: Newtonsoft.Json types replaced</span></span>

<span data-ttu-id="7a7e5-102">ASP.NET Core 3,0 ' de, kimlik doğrulama API 'Lerinde kullanılan `Newtonsoft.Json` türler `System.Text.Json` türleriyle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7a7e5-102">In ASP.NET Core 3.0, `Newtonsoft.Json` types used in Authentication APIs have been replaced with `System.Text.Json` types.</span></span> <span data-ttu-id="7a7e5-103">Aşağıdaki durumlar hariç, kimlik doğrulama paketlerinin temel kullanımı etkilenmemiştir:</span><span class="sxs-lookup"><span data-stu-id="7a7e5-103">Except for the following cases, basic usage of the Authentication packages remains unaffected:</span></span>

* <span data-ttu-id="7a7e5-104">, [ASPNET-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers)gibi OAuth sağlayıcılardan türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="7a7e5-104">Classes derived from the OAuth providers, such as those from [aspnet-contrib](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers).</span></span>
* <span data-ttu-id="7a7e5-105">Gelişmiş talep işleme uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="7a7e5-105">Advanced claim manipulation implementations.</span></span>

<span data-ttu-id="7a7e5-106">Daha fazla bilgi için bkz. [ASPNET/AspNetCore # 7105](https://github.com/aspnet/AspNetCore/pull/7105).</span><span class="sxs-lookup"><span data-stu-id="7a7e5-106">For more information, see [aspnet/AspNetCore#7105](https://github.com/aspnet/AspNetCore/pull/7105).</span></span> <span data-ttu-id="7a7e5-107">Tartışma için bkz. [ASPNET/AspNetCore # 7289](https://github.com/aspnet/AspNetCore/issues/7289).</span><span class="sxs-lookup"><span data-stu-id="7a7e5-107">For discussion, see [aspnet/AspNetCore#7289](https://github.com/aspnet/AspNetCore/issues/7289).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7a7e5-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7a7e5-108">Version introduced</span></span>

<span data-ttu-id="7a7e5-109">3,0</span><span class="sxs-lookup"><span data-stu-id="7a7e5-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7a7e5-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="7a7e5-110">Recommended action</span></span>

<span data-ttu-id="7a7e5-111">Türetilmiş OAuth uygulamaları için en yaygın değişiklik, [burada](https://github.com/aspnet/AspNetCore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40)gösterildiği gibi `CreateTicketAsync` geçersiz kılmada `JsonDocument.Parse` `JObject.Parse`.</span><span class="sxs-lookup"><span data-stu-id="7a7e5-111">For derived OAuth implementations, the most common change is to replace `JObject.Parse` with `JsonDocument.Parse` in the `CreateTicketAsync` override as shown [here](https://github.com/aspnet/AspNetCore/pull/7105/files?utf8=%E2%9C%93&diff=unified&w=1#diff-e1c9f9740a6fe8021020a6f249c589b0L40).</span></span> <span data-ttu-id="7a7e5-112">`JsonDocument` `IDisposable`uygular.</span><span class="sxs-lookup"><span data-stu-id="7a7e5-112">`JsonDocument` implements `IDisposable`.</span></span>

<span data-ttu-id="7a7e5-113">Aşağıdaki listede bilinen değişiklikler özetlenmektedir:</span><span class="sxs-lookup"><span data-stu-id="7a7e5-113">The following list outlines known changes:</span></span>

- <span data-ttu-id="7a7e5-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`olur.</span><span class="sxs-lookup"><span data-stu-id="7a7e5-114"><xref:Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimAction.Run(Newtonsoft.Json.Linq.JObject,System.Security.Claims.ClaimsIdentity,System.String)?displayProperty=nameWithType> becomes `ClaimAction.Run(JsonElement userData, ClaimsIdentity identity, string issuer)`.</span></span> <span data-ttu-id="7a7e5-115">`ClaimAction` türetilen tüm uygulamalar benzer şekilde etkilenir.</span><span class="sxs-lookup"><span data-stu-id="7a7e5-115">All derived implementations of `ClaimAction` are similarly affected.</span></span>
- <span data-ttu-id="7a7e5-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)` olur</span><span class="sxs-lookup"><span data-stu-id="7a7e5-116"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="7a7e5-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)` olur</span><span class="sxs-lookup"><span data-stu-id="7a7e5-117"><xref:Microsoft.AspNetCore.Authentication.ClaimActionCollectionMapExtensions.MapCustomJson(Microsoft.AspNetCore.Authentication.OAuth.Claims.ClaimActionCollection,System.String,System.String,System.Func{Newtonsoft.Json.Linq.JObject,System.String})?displayProperty=nameWithType> becomes `MapCustomJson(this ClaimActionCollection collection, string claimType, string valueType, Func<JsonElement, string> resolver)`</span></span>
- <span data-ttu-id="7a7e5-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> eski bir Oluşturucu kaldırılmıştır ve diğer `JObject` `JsonElement`ile değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7a7e5-118"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthCreatingTicketContext> has had one old constructor removed and the other replaced `JObject` with `JsonElement`.</span></span> <span data-ttu-id="7a7e5-119">`User` özelliği ve `RunClaimActions` yöntemi eşleşecek şekilde güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="7a7e5-119">The `User` property and `RunClaimActions` method have been updated to match.</span></span>
- <span data-ttu-id="7a7e5-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> artık `JObject`yerine `JsonDocument` türünde bir parametre kabul eder.</span><span class="sxs-lookup"><span data-stu-id="7a7e5-120"><xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse.Success(Newtonsoft.Json.Linq.JObject)> now accepts a parameter of type `JsonDocument` instead of `JObject`.</span></span> <span data-ttu-id="7a7e5-121">`Response` özelliği eşleşecek şekilde güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="7a7e5-121">The `Response` property has been updated to match.</span></span> <span data-ttu-id="7a7e5-122">`OAuthTokenResponse` artık atılabilir ve `OAuthHandler`tarafından bırakılacak.</span><span class="sxs-lookup"><span data-stu-id="7a7e5-122">`OAuthTokenResponse` is now disposable and will be disposed by `OAuthHandler`.</span></span> <span data-ttu-id="7a7e5-123">`ExchangeCodeAsync` geçersiz kılan türetilmiş OAuth uygulamalarının `JsonDocument` veya `OAuthTokenResponse`atma gereksinimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="7a7e5-123">Derived OAuth implementations overriding `ExchangeCodeAsync` don't need to dispose the `JsonDocument` or `OAuthTokenResponse`.</span></span>
- <span data-ttu-id="7a7e5-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> `JObject` `JsonDocument`olarak değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="7a7e5-124"><xref:Microsoft.AspNetCore.Authentication.OpenIdConnect.UserInformationReceivedContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonDocument`.</span></span>
- <span data-ttu-id="7a7e5-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> `JObject` `JsonElement`olarak değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="7a7e5-125"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterCreatingTicketContext.User?displayProperty=nameWithType> changed from `JObject` to `JsonElement`.</span></span>
- <span data-ttu-id="7a7e5-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType>, `JObject` kabul `JsonElement`olarak değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="7a7e5-126"><xref:Microsoft.AspNetCore.Authentication.Twitter.TwitterHandler.CreateTicketAsync(System.Security.Claims.ClaimsIdentity,Microsoft.AspNetCore.Authentication.AuthenticationProperties,Microsoft.AspNetCore.Authentication.Twitter.AccessToken,Newtonsoft.Json.Linq.JObject)?displayProperty=nameWithType> changed from accepting `JObject` to `JsonElement`.</span></span>

#### <a name="category"></a><span data-ttu-id="7a7e5-127">Kategori</span><span class="sxs-lookup"><span data-stu-id="7a7e5-127">Category</span></span>

<span data-ttu-id="7a7e5-128">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7a7e5-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7a7e5-129">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7a7e5-129">Affected APIs</span></span>

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
