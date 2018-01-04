---
title: ".NET mikro ve Web uygulamalarının güvenliğini sağlama"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | .NET mikro ve Web uygulamalarının güvenliğini sağlama"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6281442f42b511170f83eaeb1c940a35a566e519
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="securing-net-microservices-and-web-applications"></a>.NET mikro ve Web uygulamalarının güvenliğini sağlama

Kaynakları ve bir hizmet tarafından kullanıma sunulan API'ler belirli güvenilen kullanıcıların veya istemcileri ile sınırlı olması için genellikle gereklidir. Kimlik doğrulaması bu tür bir API düzeyinde güven kararları yapmak için ilk adımdır. Kimlik doğrulama güvenilir bir şekilde bir kullanıcının kimliğini ascertaining işlemidir.

Mikro hizmet senaryolarda, kimlik doğrulama genellikle merkezi olarak işlenir. Bir API ağ geçidi kullanıyorsanız, Ağ Geçidi kimlik doğrulaması için uygun bir Şekil 11-1'de gösterildiği gibi yerdir. Bu yaklaşımı kullanın, ek güvenlik iletilerin kimlik doğrulaması yerinde olup olmadığını Ağ Geçidi'nden veya geldikleri olmadıkça tek tek mikro doğrudan (API ağ geçidi) ulaşılamıyor emin olun.

![](./media/image1.png)

**Şekil 11-1**. Bir API ağ geçidi ile kimlik doğrulamasını Merkezi

Hizmetleri doğrudan erişilebilir değilse, bir kimlik doğrulama hizmeti Azure Active Directory veya bir güvenlik belirteci hizmeti (STS), kullanıcıların kimliklerini doğrulamak için kullanılabilir davranan bir özel kimlik doğrulama mikro hizmet ister. Güven kararları güvenlik belirteçleri veya tanımlama bilgilerini hizmetleriyle arasında paylaşılır. (Bu, gerekirse, ASP.NET Core ile uygulamalar arasında paylaşılabilir [veri koruma hizmetleri](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) Bu model, Şekil 11-2'de gösterilmiştir.

![](./media/image2.png)

**Şekil 11-2**. Kimlik doğrulama kimlik mikro hizmet tarafından; bir yetkilendirme belirtecini kullanarak güven paylaşılan

## <a name="authenticating-using-aspnet-core-identity"></a>ASP.NET Core kimliğini kullanarak kimlik doğrulaması

Bir uygulamanın kullanıcıları tanımlamak için ASP.NET Core birincil mekanizma olan [ASP.NET Core kimliği](https://docs.microsoft.com/aspnet/core/security/authentication/identity) üyelik sistemi. ASP.NET Core kimlik geliştirici tarafından yapılandırılan bir veri deposu (oturum açma bilgileri, rolleri ve talepler dahil) kullanıcı bilgilerini depolar. Genellikle, ASP.NET Core kimliği veri deposu Microsoft.AspNetCore.Identity.EntityFrameworkCore paketinde sağlanan bir Entity Framework deposudur. Ancak, özel depoları veya diğer üçüncü taraf paketlerden Azure Table Storage, DocumentDB veya başka konumlara kimlik bilgilerini depolamak için kullanılabilir.

Aşağıdaki kod, seçili tek tek kullanıcı hesabı kimlik doğrulaması ile ASP.NET çekirdek Web uygulaması proje şablonu alınır. ASP.NET Core EntityFramework.Core Startup.ConfigureServices yöntemiyle kimliğinin nasıl yapılandırılacağını gösterir.

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

ASP.NET Core kimliği yapılandırıldıktan sonra çağıran uygulama tarafından etkinleştirin. Hizmetin Startup.Configure yönteminde UseIdentity.

ASP.NET kodu kimliğini kullanarak birkaç senaryo sağlar:

-   Yeni kullanıcı bilgilerini UserManager türünü (userManager.CreateAsync) kullanarak oluşturun.

-   SignInManager türü kullanan kullanıcıları doğrula. Doğrudan oturum açmak için signInManager.SignInAsync kullanabilir veya kullanıcının parolayı onaylamak için signInManager.PasswordSignInAsync doğru olduğundan ve bunları oturum açın.

-   Böylece bir tarayıcı gelen sonraki istekleri oturum açmış kullanıcının kimlik ve talepleri içerir (hangi ASP.NET Core kimliği ara yazılımı tarafından okunur) bir tanımlama bilgisinde depolanan bilgilere dayanarak bir kullanıcıyı tanımlamak.

ASP.NET Core kimliği de destekler [iki öğeli kimlik doğrulama](https://docs.microsoft.com/aspnet/core/security/authentication/2fa).

Bir yerel kullanıcı veri deposunu olun kimlik doğrulama senaryoları kullanın ve kimlik (MVC web uygulamaları için tipik olarak) tanımlama bilgilerini kullanarak istekler arasında kalıcı hale getirmek için ASP.NET Core kimliği önerilen bir çözümdür.

## <a name="authenticating-using-external-providers"></a>Dış sağlayıcılar kullanarak kimlik doğrulaması

ASP.NET Core de destekler kullanarak [Dış kimlik doğrulama sağlayıcıları](https://docs.microsoft.com/aspnet/core/security/authentication/social/) aracılığıyla oturum açmasına izin vermek için [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) akışları. Bu, kullanıcıların Microsoft, Google, Facebook ve Twitter gibi sağlayıcılarından var olan kimlik doğrulama işlemleri kullanarak oturum açın ve ASP.NET Core Kimlikteki uygulamanızda bu kimlikleri ilişkilendirmek anlamına gelir.

Dış kimlik doğrulama kullanmak için uygulamanızın HTTP istek ardışık düzen işleme uygun yetkilendirme Ara yazılımının ekleyin. Bu ara yazılım kimlik bilgilerini yakalama ve SignInManager.GetExternalLoginInfo yöntemi yoluyla kullanılabilir hale getirme kimlik doğrulama sağlayıcısı URI yollar döndürmek işleme isteklerinin sorumludur.

Popüler Dış kimlik doğrulama sağlayıcıları ve bunların ilişkili NuGet paketleri, aşağıda gösterilmektedir.

**Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount

**Google:** Microsoft.AspNetCore.Authentication.Google

**Facebook:** Microsoft.AspNetCore.Authentication.Facebook

**Twitter:** Microsoft.AspNetCore.Authentication.Twitter

Her durumda, ara yazılım app ile benzer bir kayıt yöntemine yapılan bir çağrı kayıtlı. {ExternalProvider} kimlik doğrulaması Startup.Configure kullanın. Bu kayıt yöntemleri bir uygulama kimliği ve gizli bilgi içeren bir seçenekleri nesne alın (bir parola örneği için), sağlayıcı tarafından gerektiği şekilde. Dış kimlik doğrulama sağlayıcıları kaydedilmesi için uygulama gerektirir (açıklandığı gibi [ASP.NET Core belgeleri](https://docs.microsoft.com/aspnet/core/security/authentication/social/)) böylece hangi uygulama kimliğini erişmek isteyen kullanıcının bilgilendirebilir.

Ara yazılım içinde Startup.Configure kaydedildiğinde, her denetleyici eylemini oturum açmak için kullanıcılar isteyebilir. Bunu yapmak için kimlik doğrulama sağlayıcısının adını ve bir yönlendirme URL'si içeren bir AuthenticationProperties nesnesi oluşturun. Ardından AuthenticationProperties nesnesi iletir bir sınama yanıtı döndürür. Aşağıdaki kod, bunun bir örneğini gösterir.

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

Redirecturl'yi parametresi, kullanıcı kimliğini doğrulamasından sonra dış sağlayıcı yönlendirilmeniz gerekir URL içerir. URL kullanıcı Basitleştirilmiş aşağıdaki örnekteki gibi dış kimlik bilgileri temel alarak oturum açacak bir eylemi temsil etmelidir:

```csharp
// Sign in the user with this external login provider if the user
// already has a login.
var result = await _signInManager.ExternalLoginSignInAsync(info.LoginProvider, info.ProviderKey, isPersistent: false);

if (result.Succeeded)
{
    return RedirectToLocal(returnUrl);
}
else
{
    ApplicationUser newUser = new ApplicationUser
    {
        // The user object can be constructed with claims from the
        // external authentication provider, combined with information
        // supplied by the user after they have authenticated with
        // the external provider.
        UserName = info.Principal.FindFirstValue(ClaimTypes.Name),
        Email = info.Principal.FindFirstValue(ClaimTypes.Email)
    };
    var identityResult = await _userManager.CreateAsync(newUser);
    if (identityResult.Succeeded)
    {
        identityResult = await _userManager.AddLoginAsync(newUser, info);
        if (identityResult.Succeeded)
        {
            await _signInManager.SignInAsync(newUser, isPersistent: false);
        }
        return RedirectToLocal(returnUrl);
    }
}
```

Seçerseniz **tek tek kullanıcı hesabı** Visual Studio'da oturum dış sağlayıcı imzalamak gerekli tüm kod ASP.NET kodunun web uygulaması projesi oluşturduğunuzda, kimlik doğrulama seçenektir zaten projede gösterildiği gibi Şekil 11-3 '.

![https://msdnshared.BLOB.Core.Windows.NET/Media/2016/10/New-Web-App.PNG](./media/image3.png)

**Şekil 11-3**. Bir web uygulaması projesi oluştururken, dış kimlik doğrulama kullanmak için bir seçenek seçme

Ek olarak dış kimlik doğrulama sağlayıcıları üçüncü taraf paketlerden daha önce listelenen pek çok fazla dış kimlik doğrulama sağlayıcıları için ara yazılım sağladığınız kullanılabilir durumdadır. Bir listesi için bkz: [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) bağlantıların github'da.

Ayrıca Elbette, kendi dış kimlik doğrulaması ara yazılımı oluşturmak için mümkündür.

## <a name="authenticating-with-bearer-tokens"></a>Taşıyıcı belirteçleri ile kimlik doğrulaması

ASP.NET Core kimliği (veya kimlik ve Dış kimlik doğrulama sağlayıcıları ile) ve kimlik doğrulama kullanıcı bilgileri depolayan bir tanımlama bilgisinde uygundur iyi birçok web uygulama senaryoları için çalışır. Diğer senaryolarda, ancak, tanımlama bilgilerini kalıcı yapma ve veri aktarırken bir doğal değildir.

Örneğin, bir ASP.NET çekirdek Web API yerel istemciler tarafından tek sayfa uygulamaları (SPAs) tarafından erişilebilen RESTful uç noktalarını kullanıma sunan veya hatta diğer Web API'leri tarafından genellikle taşıyıcı belirteci kimlik doğrulaması yerine kullanmak istediğiniz. Bu tür uygulamalar değil tanımlama bilgileriyle çalışır ancak kolayca taşıyıcı belirtecini almak ve sonraki istekleri yetkilendirme üst bilgi içerir. Belirteç kimlik doğrulamasını etkinleştirmek için ASP.NET Core çeşitli seçenekler kullanmak için destekleyen [OAuth 2.0](https://oauth.net/2/) ve [Openıd Connect](http://openid.net/connect/).

## <a name="authenticating-with-an-openid-connect-or-oauth-20-identity-provider"></a>Bir Openıd Connect veya OAuth 2.0 kimlik sağlayıcısı ile kimlik doğrulaması

Kullanıcı bilgilerini Azure Active Directory veya Openıd Connect veya OAuth 2.0 destekleyen başka bir kimlik çözümü depolanıyorsa, Openıd Connect iş akışını kullanarak kimlik doğrulaması için Microsoft.AspNetCore.Authentication.OpenIdConnect paketi kullanabilirsiniz. Örneğin, [karşı Azure Active Directory kimlik doğrulaması](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/), aşağıdaki örnekte gösterildiği gibi bir ASP.NET Core web uygulaması ara yazılım bu paketten kullanabilirsiniz:

```csharp
// Configure the OWIN pipeline to use OpenID Connect auth
app.UseOpenIdConnectAuthentication(new OpenIdConnectOptions
{
    ClientId = Configuration["AzureAD:ClientId"],
    Authority = String.Format(Configuration["AzureAd:AadInstance"],
    Configuration["AzureAd:Tenant"]),
    ResponseType = OpenIdConnectResponseType.IdToken,
    PostLogoutRedirectUri = Configuration["AzureAd:PostLogoutRedirectUri"]
});
```

Yapılandırma değerleri, uygulamanızın olduğunda oluşturulan Azure Active Directory değerlerdir [bir Azure AD istemcisi olarak kayıtlı](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad). Tüm Azure Active Directory ile kimliği doğrulanan kullanıcılar kimlik doğrulaması gerekiyorsa tek bir istemci kimliği bir uygulamada birden çok mikro arasında paylaşılabilir.

Tüm kullanıcı bilgilerini depolama ve kimlik doğrulama gerçekleştirilir için Azure Active Directory tarafından bu iş akışı kullandığınızda, ASP.NET Core kimliği ara yazılımı gerekli değildir, unutmayın.

## <a name="issuing-security-tokens-from-an-aspnet-core-service"></a>Bir ASP.NET Core hizmetinden güvenlik belirteçleri verme

Yerel ASP.NET Core kimliği kullanıcılar için güvenlik belirteçleri vermek tercih ettiğiniz yerine, bir dış kimlik sağlayıcı kullanarak, bazı iyi üçüncü taraf kitaplıkların yararlanabilirsiniz.

[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) ve [OpenIddict](https://github.com/openiddict/openiddict-core) kolayca sorunu güvenlik belirteçleri bir ASP.NET Core hizmetinden olanak ASP.NET Core kimliği ile tümleşen Openıd Connect sağlayıcılarıdır. [IdentityServer4 belgelerine](https://identityserver4.readthedocs.io/en/release/) kitaplığı kullanmaya yönelik ayrıntılı yönergeler içerir. Ancak, IdentityServer4 sorunu belirteçleri kullanarak yönelik temel adımlar aşağıda belirtilmiştir.

1.  Uygulama çağırın. IdentityServer4 uygulamanın HTTP istek işleme ardışık düzenine eklemek için UseIdentityServer Startup.Configure yöntemi. Bu, Openıd Connect ve /connect/token gibi OAuth2 uç noktaları için isteklere hizmet kitaplığı olanak tanır.

2.  Hizmetler için bir çağrı yaparak IdentityServer4 Startup.ConfigureServices içinde yapılandırın. AddIdentityServer.

3.  Aşağıdaki veriler sağlayarak kimlik sunucusunu yapılandırın:

-   [Kimlik bilgileri](https://identityserver4.readthedocs.io/en/release/topics/crypto.html) imzalama için kullanılacak.

-   [Kimlik ve API kaynakları](https://identityserver4.readthedocs.io/en/release/topics/resources.html) kullanıcıların erişimi isteyebilir:

<!-- -->

-   API kaynakları korumalı veriler veya bir erişim belirteciyle bir kullanıcının erişebildiği işlevleri temsil eder. Bir örnek bir API kaynağı bir web API (veya API kümesi) olabilir yetkilendirme gerektirir.

-   Identity kaynaklar bir istemciye bir kullanıcıyı tanımlamak için verilen bilgileri (talep) temsil eder. Talepler, kullanıcı adı, e-posta adresi vb. içerebilir.

<!-- -->

-   [İstemciler](https://identityserver4.readthedocs.io/en/release/topics/clients.html) , bağlanma belirteçler istemek için.

-   Kullanıcı bilgilerini depolama mekanizmasını gibi [ASP.NET Core kimliği](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) veya alternatif.

İstemcileri ve kaynakları IdentityServer4 için kullanılacak belirttiğinizde, bir IEnumerable geçirebilirsiniz&lt;T&gt; uygun türe bellek içi istemci veya kaynak depoları ele yöntemleri topluluğu. Veya daha karmaşık senaryolar için istemci veya kaynak sağlayıcısı türlerinin bağımlılık ekleme aracılığıyla sağlayabilir.

Bellek içi kaynaklar ve özel bir IClientStore türü tarafından sağlanan istemcileri kullanmak IdentityServer4 için örnek bir yapılandırma aşağıdaki gibi görünebilir:

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

## <a name="consuming-security-tokens"></a>Güvenlik belirteçleri kullanma

Bir Openıd Connect uç nokta karşı kimlik doğrulaması veya kendi güvenlik belirteçleri verme bazı senaryolar ele alınmaktadır. Ancak ne yalnızca geçerli güvenliğe sahip kullanıcılara erişimi sınırlamak için gereken bir hizmet belirteçleri farklı bir hizmet tarafından sağlandı?

Bu senaryo için JWT belirteçleri işleme kimlik doğrulaması ara yazılımı Microsoft.AspNetCore.Authentication.JwtBearer paketinde kullanılabilir. JWT anlamına gelir "[JSON Web belirteci](https://tools.ietf.org/html/rfc7519)" ve güvenlik taleplerini iletişim kurmak için (RFC 7519 tarafından tanımlanan) ortak bir güvenlik belirteci biçimi değil. Ara yazılım bu tür belirteçleri tüketen için nasıl kullanılacağını basit bir örneği aşağıdaki gibi görünebilir. Bu kod ASP.NET Core MVC Ara (app. çağrıları gelmelidir UseMvc).

```csharp
app.UseJwtBearerAuthentication(new JwtBearerOptions()
{
    Audience = "http://localhost:5001/",
    Authority = "http://localhost:5000/",
    AutomaticAuthenticate = true
});
```

Bu kullanım parametrelerinde şunlardır:

-   Hedef kitle gelen belirteci ya da erişim belirteci verir kaynak alıcısı temsil eder. Bu parametrede belirtilen değer belirteci aud parametresinde eşleşmiyorsa, belirteç kabul edilmeyecek.

-   Yetki belirteci veren kimlik doğrulama sunucusu adresidir. JWT taşıyıcı kimlik doğrulaması ara yazılımı bu URI belirtecin imzayı doğrulamak için kullanılan ortak anahtar almak için kullanır. Ara yazılım, ayrıca belirteç ISS parametresinde bu URI ile eşleşip eşleşmediğini onaylar.

-   AutomaticAuthenticate belirtecin tarafından tanımlanan kullanıcı otomatik olarak imzalanması gerektiğini olup olmadığını gösteren bir Boole değeri değil.

Başka bir parametre, RequireHttpsMetadata, bu örnekte kullanılmaz. Sınama amacıyla yararlı olur; Böylece ortamlarında test, bu parametre false olarak burada sertifikası olmayan ayarlayın. Gerçek dünya dağıtımlarda, JWT taşıyıcı belirteçlerini her zaman yalnızca HTTPS üzerinden aktarılmalıdır.

Yerinde bu Ara yazılımla JWT belirteçleri yetkilendirme üstbilgileri otomatik olarak çıkarılır. Bunlar daha sonra seri, (İzleyici ve yetkilisi parametrelerinin değerleri kullanarak) doğrulandı ve MVC eylemler veya yetkilendirme filtreleri daha sonra başvurulmak üzere kullanıcı bilgilerini olarak depolanır.

JWT taşıyıcı kimlik doğrulaması ara yazılımı ayrıca yerel bir sertifika yetkilisi kullanılamıyorsa bir belirteci doğrulamak için kullanma gibi daha Gelişmiş senaryolar destekleyebilir. Bu senaryo için JwtBearerOptions nesnesinde tokenvalidationparameters değerini nesnesi belirtebilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

-   **Uygulamalar arasında tanımlama bilgilerini paylaşımı**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\# Paylaşımı kimlik doğrulama-tanımlama bilgileri-arasında-uygulamalar*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)

-   **Kimlik giriş**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)

-   **Rick Anderson. SMS ile iki öğeli kimlik doğrulama**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)

-   **Facebook, Google ve diğer dış sağlayıcılarını kullanarak etkinleştirme kimlik doğrulaması**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)

-   **Michell Anicas. OAuth 2 giriş**
    [*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)

-   **AspNet.Security.OAuth.Providers** (ASP.NET OAuth sağlayıcıları için GitHub depo.
    [*https://github.com/ASPNET-contrib/AspNet.Security.OAuth.providers/Tree/dev/src*](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

-   **Danny Strockis. Bir ASP.NET Core web uygulamasına Azure AD tümleştirme**
    [*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)

-   **IdentityServer4. Resmi belge**
    [*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)


>[!div class="step-by-step"]
[Önceki] (.. /implement-resilient-Applications/Monitor-App-Health.MD) [sonraki] (yetkilendirme-net-mikro-web-applications.md)
