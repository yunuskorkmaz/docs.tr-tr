---
title: .NET mikro Hizmetleri ve Web uygulamalarının güvenliğini sağlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | .NET mikro Hizmetleri ve Web uygulamalarının güvenliğini sağlama
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 7ee559f3881101a2382e6767607d5de1482d74ba
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126477"
---
# <a name="securing-net-microservices-and-web-applications"></a>.NET mikro Hizmetleri ve Web uygulamalarının güvenliğini sağlama

Genellikle, gerekli kaynak ve hizmet tarafından sunulan API'ler belirli güvenilen kullanıcıların veya istemciler için sınırlı olur. Kimlik doğrulaması yaparak bu tür bir API düzeyinde güven kararları için ilk adımdır. Kimlik doğrulaması güvenilir bir şekilde bir kullanıcının kimliğini ascertaining işlemidir.

Mikro hizmet senaryolarda, kimlik doğrulaması genellikle merkezi olarak yönetilir. Bir API ağ geçidi kullanıyorsanız, ağ geçidi kimliğini doğrulamak için uygun bir Şekil 11-1'de gösterildiği yerdir. Bu yaklaşımı kullanın, ek güvenlik iletileri kimlik doğrulaması yerinde olup olmadığını ağ geçidinden veya geldikleri olmadığı sürece her bir mikro hizmetin doğrudan (API ağ geçidi) ulaşılamıyor emin olun.

![](./media/image1.png)

**Şekil 11-1**. Bir API ağ geçidi ile merkezi kimlik doğrulaması

Hizmetleri doğrudan erişilebilir, kimlik doğrulama hizmeti Azure Active Directory veya bir güvenlik belirteci hizmeti (STS), kullanıcıların kimliklerini doğrulamak için kullanılabilir davranan bir özel kimlik doğrulama mikro hizmet gibi. Güven kararları güvenlik belirteçleri veya tanımlama bilgileri ile hizmetler arasında paylaşılır. (Bunlar gerekirse, ASP.NET Core ile uygulamalar arasında paylaşılabilir [veri koruma hizmetleri](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) Bu düzen, Şekil 11-2'de gösterilmiştir.

![](./media/image2.png)

**Şekil 11-2**. Kimlik mikro hizmet olarak kimlik doğrulaması; bir yetkilendirme belirteciyle güven paylaşılan

## <a name="authenticating-using-aspnet-core-identity"></a>ASP.NET Core kimliği kullanarak kimlik doğrulaması

Bir uygulamanın kullanıcıları tanımlamak için birincil mekanizma ASP.NET core'da [ASP.NET Core kimliği](https://docs.microsoft.com/aspnet/core/security/authentication/identity) üyelik sistemi. ASP.NET Core kimliği geliştirici tarafından yapılandırılmış bir veri deposu (oturum açma bilgileri, rolleri ve talep dahil) kullanıcı bilgilerini depolar. Genellikle, ASP.NET Core kimliği veri deposu Microsoft.AspNetCore.Identity.EntityFrameworkCore paketinde sağlanan bir Entity Framework deposudur. Ancak, özel depoları veya diğer üçüncü taraf paketleri Azure tablo depolama, DocumentDB veya diğer konumlardan kimlik bilgilerini depolamak için kullanılabilir.

Aşağıdaki kod, seçilen kullanıcı hesabı kimlik doğrulaması ile ASP.NET Core Web uygulaması proje şablonu alınır. Bu, ASP.NET Core EntityFramework.Core Startup.ConfigureServices yöntemiyle kimliğini yapılandırmak nasıl gösterir.

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

ASP.NET Core kimliği yapılandırıldıktan sonra çağıran uygulama tarafından etkinleştirin. Hizmetin Startup.Configure yönteminde UseIdentity.

ASP.NET Core kimliği kullanarak çeşitli senaryolara olanak tanır:

-   Yeni kullanıcı bilgilerini UserManager türü (userManager.CreateAsync) kullanarak oluşturun.

-   Kullanıcılar SignInManager türü kullanılarak kimlik doğrulaması. SignInManager.SignInAsync doğrudan oturum açmak için kullanabileceğiniz veya kullanıcının parolasını onaylamak için signInManager.PasswordSignInAsync doğru olduğundan ve bunları oturum açın.

-   İstekler bir tarayıcıdan oturum açmış kullanıcının kimlik ve talep içerecektir (Bu, ASP.NET Core kimliği ara yazılımı tarafından okunur) bir tanımlama bilgisinde depolanan bilgilere dayanarak bir kullanıcıya belirleyin.

ASP.NET Core kimliği de destekler [iki öğeli kimlik doğrulama](https://docs.microsoft.com/aspnet/core/security/authentication/2fa).

ASP.NET Core kimliği olun kimlik doğrulama senaryoları bir yerel kullanıcı veri deposunu kullanın ve kimlik (MVC web uygulamaları için tipik olduğu gibi) tanımlama bilgilerini kullanarak istekleri arasında kalıcı hale getirmek için önerilen bir çözümdür.

## <a name="authenticating-using-external-providers"></a>Dış sağlayıcıları kullanarak kimlik doğrulaması

ASP.NET Core da destekler kullanarak [Dış kimlik doğrulama sağlayıcıları](https://docs.microsoft.com/aspnet/core/security/authentication/social/) aracılığıyla oturum açmasına izin vermek için [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) akışlar. Bu, kullanıcıların mevcut kimlik doğrulama işlemi Microsoft, Google, Facebook veya Twitter gibi sağlayıcılarından kullanarak oturum açın ve ASP.NET Core kimliği uygulamanızda kimliklerle ilişkilendirme anlamına gelir.

Dış kimlik doğrulama kullanmak için uygulamanızın HTTP isteği ardışık düzen işleme uygun yetkilendirme Ara yazılımının dahil edin. Bu ara yazılım kimlik sağlayıcısındaki kimlik bilgilerini yakalama ve SignInManager.GetExternalLoginInfo yöntemi aracılığıyla kullanılabilir hale getirme URI yolları döndürülecek işleme isteklerinin sorumludur.

Yaygın Dış kimlik doğrulama sağlayıcıları ve ilişkili NuGet paketlerinin aşağıda gösterilmiştir.

**Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount

**Google:** Microsoft.AspNetCore.Authentication.Google

**Facebook:** Microsoft.AspNetCore.Authentication.Facebook

**Twitter:** Microsoft.AspNetCore.Authentication.Twitter

Her durumda, ara yazılım uygulamasına benzer bir kayıt yöntemi çağrısı ile kaydedilir. Kimlik doğrulaması Startup.Configure {ExternalProvider} kullanın. Bu kayıt yöntemleri bir uygulama kimliği ve gizli bilgi içeren bir seçenekler nesne alır (parola örneği için), sağlayıcı tarafından gerektiğinde. Dış kimlik doğrulama sağlayıcıları uygulamanın kayıtlı olması gerekir (açıklandığı şekilde [ASP.NET Core belgeleri](https://docs.microsoft.com/aspnet/core/security/authentication/social/)), böylece hangi uygulama kimliklerini erişim isteyen kullanıcı bildirebilirsiniz.

Ara yazılım Startup.Configure kaydedildiğinde, kullanıcıların herhangi bir denetleyici eylemden oturum isteyebilir. Bunu yapmak için kimlik doğrulama sağlayıcısının adını ve bir yeniden yönlendirme URL'sini içeren bir AuthenticationProperties nesnesi oluşturun. Ardından AuthenticationProperties nesneyi de iletir bir sınama yanıtı döndürür. Aşağıdaki kod, bunun bir örneğini gösterir.

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

Kullanıcı kimliğini doğrulamasından sonra dış sağlayıcı yönlendirmek URL redirectUrl parametresi içerir. URL, kullanıcı aşağıdaki Basitleştirilmiş örnekte olduğu gibi bir dış kimlik bilgilerine dayalı oturum açacak bir eylem göstermelidir:

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

Seçerseniz **bireysel kullanıcı hesabı** Visual Studio'da bir dış sağlayıcısı ile oturum açmak için gerekli tüm kodlar kod ASP.NET web uygulaması projesi oluşturduğunuzda, kimlik doğrulaması seçeneği olan zaten projede gösterildiği gibi Şekil 11 – 3 '.

![https://msdnshared.blob.core.windows.net/media/2016/10/new-web-app.png](./media/image3.png)

**Şekil 11-3**. Bir web uygulaması projesi oluştururken, dış kimlik doğrulama kullanmak için bir seçeneği

Ek olarak bir dış kimlik doğrulama sağlayıcıları daha önce üçüncü taraf paketlerini listelenen çok fazla dış kimlik doğrulama sağlayıcıları için bir ara yazılım sağladığınız kullanılabilir durumdadır. Bir liste için bkz. [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) github deposu.

Bu da Elbette, kendi dış kimlik doğrulaması ara yazılımı oluşturmak için mümkündür.

## <a name="authenticating-with-bearer-tokens"></a>Taşıyıcı belirteçleri ile kimlik doğrulaması

ASP.NET Core kimliği (veya kimlik ve Dış kimlik doğrulama sağlayıcıları ile) kimlik doğrulaması, kullanıcı bilgileri depolayan bir tanımlama bilgisinde uygun olduğu da birçok web uygulama senaryoları için çalışır. Diğer senaryolarda, ancak tanımlama bilgilerini kalıcı hale getirmeniz ve veri aktarımı doğal bir yol değildir.

Örneğin, bir ASP.NET Core Web API'si yerel istemciler tarafından tek sayfa uygulamaları (Spa'lar) tarafından erişilebilen bir RESTful uç noktalarını kullanıma sunan veya hatta diğer Web API'leri tarafından genellikle taşıyıcı belirteci kimlik doğrulaması yerine kullanmak istediğiniz. Bu tür uygulamalar değil tanımlama bilgileriyle çalışır ancak kolayca bir taşıyıcı belirteç alabilir ve sonraki istekleri yetkilendirme üst bilgisi içerir. Belirteç kimlik doğrulamasını etkinleştirmek için ASP.NET Core çeşitli seçenekler kullanmak için destekleyen [OAuth 2.0](https://oauth.net/2/) ve [Openıd Connect](https://openid.net/connect/).

## <a name="authenticating-with-an-openid-connect-or-oauth-20-identity-provider"></a>Bir Openıd Connect veya OAuth 2.0 kimlik sağlayıcısı ile kimlik doğrulaması

Azure Active Directory veya Openıd Connect veya OAuth 2.0 destekleyen başka bir kimlik çözümü depolanan kullanıcı bilgileri, iş akışının Openıd Connect kullanarak kimlik doğrulaması için Microsoft.AspNetCore.Authentication.OpenIdConnect paketi kullanabilirsiniz. Örneğin, [Azure Active Directory'de kimlik doğrulaması](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/), aşağıdaki örnekte gösterildiği gibi bir ASP.NET Core web uygulaması ara yazılım bu paketten kullanabilirsiniz:

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

Yapılandırma değerleri, uygulamanız olduğunda, oluşturulan Azure Active Directory değerler [bir Azure AD istemci olarak kayıtlı](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad). Tüm Azure Active Directory aracılığıyla kimliği doğrulanmış kullanıcılar kimliklerini doğrulaması gerekiyorsa tek bir istemci kimliği bir uygulamada birden fazla mikro hizmetler arasında paylaşılabilir.

Tüm kullanıcı bilgileri depolama ve kimlik doğrulaması gerçekleştirilir çünkü Azure Active Directory tarafından bu iş akışını kullanırken, ASP.NET Core kimliği ara yazılımı gerekli olmadığını, unutmayın.

## <a name="issuing-security-tokens-from-an-aspnet-core-service"></a>Bir ASP.NET Core hizmeti güvenlik belirteçleri verme

Yerel ASP.NET Core kimliği kullanıcılar için güvenlik belirteçlerini vermek tercih ettiğiniz yerine, bir dış kimlik sağlayıcısı kullanarak, bazı iyi üçüncü taraf kitaplıklar avantajlarından yararlanabilirsiniz.

[Identityserver4](https://github.com/IdentityServer/IdentityServer4) ve [OpenIddict](https://github.com/openiddict/openiddict-core) Openıd Connect sağlayıcılar, ASP.NET Core kimliği ile izin verecek şekilde güvenlik belirteçleri bir ASP.NET Core hizmeti kolayca tümleştirin. [Identityserver4 belgeleri](https://identityserver4.readthedocs.io/en/release/) kitaplığı kullanmak için ayrıntılı yönergeler içerir. Ancak, Identityserver4 sorunu belirteçleri kullanarak için temel adımlar şunlardır.

1.  Uygulama çağırırsınız. Identityserver4 uygulamanın HTTP istek işleme ardışık düzenine eklemek için UseIdentityServer Startup.Configure yöntem. Bu kitaplık OAuth2 uç noktaları /connect/token gibi Openıd Connect ve isteklere hizmet sağlar.

2.  Identityserver4 Hizmetleri çağrısı yaparak Startup.ConfigureServices içinde yapılandırın. AddIdentityServer.

3.  Kimlik sunucusu, aşağıdaki veriler sağlayarak yapılandırın:

-   [Kimlik bilgilerini](https://identityserver4.readthedocs.io/en/release/topics/crypto.html) imzalama için kullanılacak.

-   [Kimlik ve API kaynaklarına](https://identityserver4.readthedocs.io/en/release/topics/resources.html) kullanıcılar için erişim isteyebilir:

<!-- -->

-   API kaynaklarını korumalı veriler veya bir erişim belirteci ile bir kullanıcının erişebildiği işlevleri temsil eder. Örnek bir API kaynağı bir web API (veya API kümesi) verilebilir yetkilendirme gerektirir.

-   Kimlik kaynaklarını bir kullanıcıyı tanımlamak için bir istemci için verilen bilgileri (talep) temsil eder. Talepler, kullanıcı adı, e-posta adresi vb. içerebilir.

<!-- -->

-   [İstemcileri](https://identityserver4.readthedocs.io/en/release/topics/clients.html) , bağlama belirteci istemek için.

-   Kullanıcı bilgileri depolama mekanizması gibi [ASP.NET Core kimliği](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) veya alternatif.

İstemcileri ve Identityserver4 kaynakları kullanmak için belirttiğinizde, bir IEnumerable geçirebilirsiniz&lt;T&gt; bellek içi istemci veya kaynak depolarını ele yöntemleri için uygun türde bir koleksiyonu. Veya daha karmaşık senaryolarda, istemci veya kaynak sağlayıcısı türleri aracılığıyla bağımlılık ekleme sağlayabilir.

Identityserver4 bellek içi kaynaklar ve istemcilere özel bir IClientStore türü tarafından sağlanan kullanmak için örnek bir yapılandırma aşağıdaki örnekteki gibi görünebilir:

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

## <a name="consuming-security-tokens"></a>Güvenlik belirteçleri kullanma

Bir Openıd Connect uç noktasına karşı kimlik doğrulaması veya kendi güvenlik belirteçleri verme bazı senaryolar ele alınmaktadır. Ancak ne yalnızca geçerli güvenliğe sahip kullanıcılara erişimi sınırlamak için gereken hizmet belirteçleri farklı bir hizmet tarafından sağlandı?

Bu senaryo için JWT belirteçlerini işler kimlik doğrulaması ara yazılımı Microsoft.AspNetCore.Authentication.JwtBearer pakette kullanılabilir. JWT anlamına gelen "[JSON Web belirteci](https://tools.ietf.org/html/rfc7519)" ve (RFC 7519 tarafından tanımlanan) ortak bir güvenlik belirteci biçimi güvenlik talepleri iletişim kurmak için. Tür belirteçleri kullanmasını ara yazılımı kullanmak nasıl basit bir örneği aşağıdaki örnekteki gibi görünebilir. Bu kod (uygulama. ASP.NET Core MVC Ara çağrıları önce gelmelidir UseMvc).

```csharp
app.UseJwtBearerAuthentication(new JwtBearerOptions()
{
    Audience = "http://localhost:5001/",
    Authority = "http://localhost:5000/",
    AutomaticAuthenticate = true
});
```

Bu kullanımı Parametreler şunlardır:

-   İzleyici, gelen belirteci veya erişim belirteci verir kaynak alıcısı temsil eder. Bu parametrede belirtilen değer belirteci aud parametresinde eşleşmiyorsa, belirteç reddedilir.

-   Yetki belirteci verilirken kimlik doğrulaması sunucusunun adresidir. JWT taşıyıcı kimlik doğrulaması ara yazılımı, belirtecin imzayı doğrulamak için kullanılacak ortak anahtarı almak için bu URI kullanır. Ara yazılım ayrıca belirteç ISS parametresinde bu URI eşleştiğini doğrular.

-   AutomaticAuthenticate belirteci tarafından tanımlanan kullanıcı otomatik olarak imzalanması gerektiğini olup olmadığını gösteren bir Boole değeridir.

Başka bir parametre, RequireHttpsMetadata, bu örnekte kullanılmaz. Test amacıyla kullanışlıdır. Böylece ortamlarında test, bu parametre false olarak nerede sertifikası olmayan ayarlayın. Gerçek dağıtımlarda, JWT taşıyıcı belirteçlerini her zaman yalnızca HTTPS üzerinden geçirilmelidir.

Yerinde bu ara yazılım ile JWT belirteçleri yetkilendirme üst bilgiler otomatik olarak çıkarılır. Bunlar daha sonra seri durumdan, (hedef kitle ve yetkilisi parametrelerinin değerleri kullanarak) ve MVC eylemler veya yetkilendirme filtrelerini daha sonra başvurulmak üzere kullanıcı bilgilerini olarak depolanır.

JWT taşıyıcı kimlik doğrulaması ara yazılımı yerel bir sertifika yetkilisi kullanılabilir değilse, bir belirteci doğrulamak için kullanma gibi daha gelişmiş senaryoları da destekler. Bu senaryo için JwtBearerOptions nesnesinde bir tokenvalidationparameters değerini nesnesi belirtebilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

-   **Tanımlama bilgilerini uygulamalar arasında paylaşma**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sharing-authentication-cookies-between-applications*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)

-   **Kimliğe giriş**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)

-   **Rick Anderson. SMS ile iki öğeli kimlik doğrulama**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)

-   **Facebook, Google ve diğer dış sağlayıcıları kullanarak kimlik doğrulamayı etkinleştirme**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)

-   **Michell Anicas. OAuth 2 giriş**
    [*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)

-   **AspNet.Security.OAuth.Providers** (ASP.NET OAuth sağlayıcıları için GitHub deposunu.
    [*https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src*](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

-   **Danny Strockis. Azure AD'yi bir ASP.NET Core web uygulamasıyla tümleştirme**
    [*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)

-   **Identityserver4. Resmi belgeleri**
    [*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)

>[!div class="step-by-step"]
>[Önceki](../implement-resilient-applications/monitor-app-health.md)
>[İleri](authorization-net-microservices-web-applications.md)