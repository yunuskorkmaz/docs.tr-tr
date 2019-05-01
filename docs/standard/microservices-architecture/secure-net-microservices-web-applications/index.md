---
title: .NET mikro Hizmetleri ve Web uygulamalarının güvenliğini sağlama
description: .NET mikro Hizmetleri ve Web uygulamaları - güvenlik ASP.NET Core web uygulamalarında kimlik doğrulama seçenekleri bilmek alın.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 0894465858e3503e2eddb5299b404f7ba95fdd6a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019685"
---
# <a name="make-secure-net-microservices-and-web-applications"></a>Güvenli .NET mikro Hizmetleri ve Web uygulamaları

Bu bölümde, kimlik doğrulaması, yetkilendirme ve uygulama gizli dizilerini odaklanacağız şekilde konu kolay bunun gibi birkaç books sürebilir, mikro hizmetler ve web uygulamaları'nda güvenlik hakkında çok fazla unsur vardır.

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a>.NET mikro Hizmetleri ve web uygulamalarında uygulama kimlik doğrulaması

Genellikle, kaynaklar ve belirli güvenilen kullanıcıların veya istemciler için sınırlı bir hizmet tarafından yayımlanan API'leri için gerekli olur. Kimlik doğrulaması yaparak bu tür bir API düzeyinde güven kararları için ilk adımdır. Kimlik doğrulama işlemi, güvenilir bir şekilde bir kullanıcının kimliğini doğrulamak bağlıdır.

Mikro hizmet senaryolarda, kimlik doğrulaması genellikle merkezi olarak yönetilir. Bir API ağ geçidi kullanıyorsanız, ağ geçidi kimliğini doğrulamak için uygun bir Şekil 9-1'de gösterildiği yerdir. Bu yaklaşımı kullanın, ek güvenlik iletileri kimlik doğrulaması yerinde olup olmadığını ağ geçidinden veya geldikleri olmadığı sürece her bir mikro hizmetin doğrudan (API ağ geçidi) ulaşılamıyor emin olun.

![API Ağ Geçidi kimlik doğrulaması merkezileştirir, mikro hizmetler isteklerini iletirken kullanıcı bilgilerini ekler.](./media/image1.png)

**Şekil 9-1**. Bir API ağ geçidi ile merkezi kimlik doğrulaması

Hizmetleri doğrudan erişilebilir, kimlik doğrulama hizmeti Azure Active Directory veya bir güvenlik belirteci hizmeti (STS), kullanıcıların kimliklerini doğrulamak için kullanılabilir davranan bir özel kimlik doğrulama mikro hizmet gibi. Güven kararları güvenlik belirteçleri veya tanımlama bilgileri ile hizmetler arasında paylaşılır. (Bu belirteçleri uygulayarak gerekirse ASP.NET Core uygulamaları arasında paylaşılabilir [tanımlama bilgisi paylaşımını](/aspnet/core/security/cookie-sharing).) Bu düzen, Şekil 9-2'de gösterilmiştir.

![Mikro hizmetler doğrudan erişildiğinde, kimlik doğrulama ve yetkilendirme içerir, güven, mikro hizmetler arasında paylaşılan adanmış bir mikro hizmet veren bir güvenlik belirteci tarafından işlenir.](./media/image2.png)

**Şekil 9-2**. Kimlik mikro hizmet olarak kimlik doğrulaması; bir yetkilendirme belirteciyle güven paylaşılan

### <a name="authenticate-with-aspnet-core-identity"></a>ASP.NET Core kimliği ile kimlik doğrulaması

Bir uygulamanın kullanıcıları tanımlamak için birincil mekanizma ASP.NET core'da [ASP.NET Core kimliği](/aspnet/core/security/authentication/identity) üyelik sistemi. ASP.NET Core kimliği geliştirici tarafından yapılandırılmış bir veri deposu (oturum açma bilgileri, rolleri ve talep dahil) kullanıcı bilgilerini depolar. Genellikle, ASP.NET Core kimliği veri deposu sağlanan içinde bir Entity Framework deposudur `Microsoft.AspNetCore.Identity.EntityFrameworkCore` paket. Ancak, özel depoları veya diğer üçüncü taraf paketleri Azure tablo depolama, CosmosDB veya diğer konumlardan kimlik bilgilerini depolamak için kullanılabilir.

Aşağıdaki kod, seçilen kullanıcı hesabı kimlik doğrulaması ile ASP.NET Core Web uygulaması proje şablonu alınır. Bu, ASP.NET Core EntityFramework.Core Startup.ConfigureServices yöntemiyle kimliğini yapılandırmak nasıl gösterir.

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

ASP.NET Core kimliği yapılandırıldıktan sonra çağıran uygulama tarafından etkinleştirin. Hizmetin UseIdentity `Startup.Configure` yöntemi.

ASP.NET Core kimliği kullanarak çeşitli senaryolara olanak tanır:

- Yeni kullanıcı bilgilerini UserManager türü (userManager.CreateAsync) kullanarak oluşturun.

- Kullanıcılar SignInManager türü kullanılarak kimlik doğrulaması. Kullanabileceğiniz `signInManager.SignInAsync` doğrudan oturum açmanız veya `signInManager.PasswordSignInAsync` kullanıcının parolasını doğru olduğunu onaylayın ve ardından bunları oturum açın.

- İstekler bir tarayıcıdan oturum açmış kullanıcının kimlik ve talep içerecektir (Bu, ASP.NET Core kimliği ara yazılımı tarafından okunur) bir tanımlama bilgisinde depolanan bilgilere dayanarak bir kullanıcıya belirleyin.

ASP.NET Core kimliği de destekler [iki öğeli kimlik doğrulama](/aspnet/core/security/authentication/2fa).

ASP.NET Core kimliği olun kimlik doğrulama senaryoları bir yerel kullanıcı veri deposunu kullanın ve kimlik (MVC web uygulamaları için tipik olduğu gibi) tanımlama bilgilerini kullanarak istekleri arasında kalıcı hale getirmek için önerilen bir çözümdür.

### <a name="authenticate-with-external-providers"></a>Dış sağlayıcıları ile kimlik doğrulama

ASP.NET Core da destekler kullanarak [Dış kimlik doğrulama sağlayıcıları](/aspnet/core/security/authentication/social/) aracılığıyla oturum açmasına izin vermek için [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) akışlar. Bu, kullanıcıların mevcut kimlik doğrulama işlemi Microsoft, Google, Facebook veya Twitter gibi sağlayıcılarından kullanarak oturum açın ve ASP.NET Core kimliği uygulamanızda kimliklerle ilişkilendirme anlamına gelir.

Dış kimlik doğrulama kullanmak için uygulamanızın HTTP isteği ardışık düzen işleme uygun yetkilendirme Ara yazılımının dahil edin. Bu ara yazılım kimlik sağlayıcısındaki kimlik bilgilerini yakalama ve SignInManager.GetExternalLoginInfo yöntemi aracılığıyla kullanılabilir hale getirme URI yolları döndürülecek işleme isteklerinin sorumludur.

Yaygın Dış kimlik doğrulama sağlayıcıları ve bunların ilişkili NuGet paketleri aşağıdaki tabloda gösterilmiştir:

| **Sağlayıcı**  | **Paket**                                          |
| ------------- | ---------------------------------------------------- |
| **Microsoft** | **Microsoft.AspNetCore.Authentication.MicrosoftAccount** |
| **Google**    | **Microsoft.AspNetCore.Authentication.Google**           |
| **Facebook**  | **Microsoft.AspNetCore.Authentication.Facebook**         |
| **Twitter**   | **Microsoft.AspNetCore.Authentication.Twitter**          |

Her durumda, ara yazılım için benzer bir kayıt yöntemi çağrısı ile kayıtlı `app.Use{ExternalProvider}Authentication` içinde `Startup.Configure`. Bu kayıt yöntemleri bir uygulama kimliği ve gizli bilgi içeren bir seçenekler nesne alır (parola örneği için), sağlayıcı tarafından gerektiğinde. Dış kimlik doğrulama sağlayıcıları uygulamanın kayıtlı olması gerekir (açıklandığı şekilde [ASP.NET Core belgeleri](/aspnet/core/security/authentication/social/)), böylece hangi uygulama kimliklerini erişim isteyen kullanıcı bildirebilirsiniz.

Ara yazılım, kaydedildikten sonra `Startup.Configure`, herhangi bir denetleyici eylemden oturum açmalarını isteyebilir. Bunu yapmak için oluşturduğunuz bir `AuthenticationProperties` kimlik doğrulama sağlayıcısının adını ve bir yeniden yönlendirme URL'sini içeren bir nesne. Başarılı bir sınama yanıtı çıkacak `AuthenticationProperties` nesne. Aşağıdaki kod, bunun bir örneğini gösterir.

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

Seçerseniz **bireysel kullanıcı hesabı** Visual Studio'da bir dış sağlayıcısı ile oturum açmak için gerekli tüm kodlar kod ASP.NET web uygulaması projesi oluşturduğunuzda, kimlik doğrulaması seçeneği olan zaten projede gösterildiği gibi Şekil 9-3'te.

![Yeni ASP.NET Core Web kimlik doğrulaması düğmenin vurgulama uygulaması iletişim kutusu.](./media/image3.png)

**Şekil 9-3**. Bir web uygulaması projesi oluştururken, dış kimlik doğrulama kullanmak için bir seçeneği

Ek olarak bir dış kimlik doğrulama sağlayıcıları daha önce üçüncü taraf paketlerini listelenen çok fazla dış kimlik doğrulama sağlayıcıları için bir ara yazılım sağladığınız kullanılabilir durumdadır. Bir liste için bkz. [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) github deposu.

Ayrıca, bazı özel gereksinim çözmek için kendi dış kimlik doğrulaması ara yazılımı oluşturabilirsiniz.

### <a name="authenticate-with-bearer-tokens"></a>Taşıyıcı belirteçleri ile kimlik doğrulaması

ASP.NET Core kimliği (veya kimlik ve Dış kimlik doğrulama sağlayıcıları ile) kimlik doğrulaması, kullanıcı bilgileri depolayan bir tanımlama bilgisinde uygun olduğu da birçok web uygulama senaryoları için çalışır. Diğer senaryolarda, ancak tanımlama bilgilerini kalıcı hale getirmeniz ve veri aktarımı doğal bir yol değildir.

Örneğin, bir ASP.NET Core Web API'si yerel istemciler tarafından tek sayfa uygulamaları (Spa'lar) tarafından erişilebilen bir RESTful uç noktalarını kullanıma sunan veya hatta diğer Web API'leri tarafından genellikle taşıyıcı belirteci kimlik doğrulaması yerine kullanmak istediğiniz. Bu tür uygulamalar değil tanımlama bilgileriyle çalışır ancak kolayca bir taşıyıcı belirteç alabilir ve sonraki istekleri yetkilendirme üst bilgisi içerir. Belirteç kimlik doğrulamasını etkinleştirmek için ASP.NET Core çeşitli seçenekler kullanmak için destekleyen [OAuth 2.0](https://oauth.net/2/) ve [Openıd Connect](https://openid.net/connect/).

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a>Bir Openıd Connect veya OAuth 2.0 kimlik sağlayıcısı ile kimlik doğrulaması

Kullanıcı bilgilerini Azure Active Directory veya Openıd Connect veya OAuth 2.0 destekleyen başka bir kimlik çözümü içinde depolanıyorsa, kullanabileceğiniz **Microsoft.AspNetCore.Authentication.OpenIdConnect** paket kullanılarak kimlik doğrulaması Openıd Connect akışı. Örneğin, hizmetine Identity.Api mikro hizmet kimlik doğrulaması için bir ASP.NET Core web uygulaması ara yazılım bu paketten aşağıdaki Basitleştirilmiş örnekte gösterildiği gibi kullanabilirsiniz `Startup.cs`:

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    // Configure the pipeline to use authentication
    app.UseAuthentication();
    //…
    app.UseMvc();
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");
    var callBackUrl = Configuration.GetValue<string>("CallBackUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = OpenIdConnectDefaults.AuthenticationScheme;
    })
    .AddCookie()
    .AddOpenIdConnect(options =>
    {
        options.SignInScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.Authority = identityUrl;
        options.SignedOutRedirectUri = callBackUrl;
        options.ClientSecret = "secret";
        options.SaveTokens = true;
        options.GetClaimsFromUserInfoEndpoint = true;
        options.RequireHttpsMetadata = false;
        options.Scope.Add("openid");
        options.Scope.Add("profile");
        options.Scope.Add("orders");
        options.Scope.Add("basket");
        options.Scope.Add("marketing");
        options.Scope.Add("locations");
        options.Scope.Add("webshoppingagg");
        options.Scope.Add("orders.signalrhub");
    });
}
```

Bu iş akışını kullanırken, ASP.NET Core kimliği ara yazılımı gerekli olmadığını, tüm kullanıcı bilgileri depolama ve kimlik doğrulaması gerçekleştirilir çünkü kimlik hizmeti tarafından unutmayın.

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a>Bir ASP.NET Core hizmeti güvenlik belirteçleri

Yerel ASP.NET Core kimliği kullanıcılar için güvenlik belirteçlerini vermek tercih ettiğiniz yerine, bir dış kimlik sağlayıcısı kullanarak, bazı iyi üçüncü taraf kitaplıklar avantajlarından yararlanabilirsiniz.

[Identityserver4](https://github.com/IdentityServer/IdentityServer4) ve [OpenIddict](https://github.com/openiddict/openiddict-core) Openıd Connect sağlayıcılar, ASP.NET Core kimliği ile izin verecek şekilde güvenlik belirteçleri bir ASP.NET Core hizmeti kolayca tümleştirin. [Identityserver4 belgeleri](https://identityserver4.readthedocs.io/en/latest/) kitaplığı kullanmak için ayrıntılı yönergeler içerir. Ancak, Identityserver4 sorunu belirteçleri kullanarak için temel adımlar şunlardır.

1. Uygulama çağırırsınız. Identityserver4 uygulamanın HTTP istek işleme ardışık düzenine eklemek için UseIdentityServer Startup.Configure yöntem. Bu kitaplık OAuth2 uç noktaları /connect/token gibi Openıd Connect ve isteklere hizmet sağlar.

2. Identityserver4 Hizmetleri çağrısı yaparak Startup.ConfigureServices içinde yapılandırın. AddIdentityServer.

3. Kimlik sunucusu, aşağıdaki veriler ayarlayarak yapılandırın:

   - [Kimlik bilgilerini](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) imzalama için kullanılacak.

   - [Kimlik ve API kaynaklarına](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) kullanıcılar için erişim isteyebilir:

      - API kaynaklarını korumalı veriler veya bir erişim belirteci ile bir kullanıcının erişebildiği işlevleri temsil eder. Örnek bir API kaynağı bir web API (veya API kümesi) verilebilir yetkilendirme gerektirir.

      - Kimlik kaynaklarını bir kullanıcıyı tanımlamak için bir istemci için verilen bilgileri (talep) temsil eder. Talepler, kullanıcı adı, e-posta adresi vb. içerebilir.

   - [İstemcileri](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) , bağlama belirteci istemek için.

   - Kullanıcı bilgileri depolama mekanizması gibi [ASP.NET Core kimliği](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) veya alternatif.

İstemcileri ve Identityserver4 kaynakları kullanmak için belirttiğinizde, geçirebilirsiniz bir <xref:System.Collections.Generic.IEnumerable%601> bellek içi istemci veya kaynak depolarını ele yöntemleri için uygun türde bir koleksiyonu. Veya daha karmaşık senaryolarda, istemci veya kaynak sağlayıcısı türleri aracılığıyla bağımlılık ekleme sağlayabilir.

Identityserver4 bellek içi kaynaklar ve istemcilere özel bir IClientStore türü tarafından sağlanan kullanmak için örnek bir yapılandırma aşağıdaki örnekteki gibi görünebilir:

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

### <a name="consume-security-tokens"></a>Güvenlik belirteçleri kullanma

Bir Openıd Connect uç noktasına karşı kimlik doğrulaması veya kendi güvenlik belirteçleri verme bazı senaryolar ele alınmaktadır. Ancak ne yalnızca geçerli güvenliğe sahip kullanıcılara erişimi sınırlamak için gereken hizmet belirteçleri farklı bir hizmet tarafından sağlandı?

Bu senaryo için JWT belirteçlerini işler kimlik doğrulaması ara yazılımı kullanılabilir **Microsoft.AspNetCore.Authentication.JwtBearer** paket. JWT anlamına gelen "[JSON Web belirteci](https://tools.ietf.org/html/rfc7519)" ve (RFC 7519 tarafından tanımlanan) ortak bir güvenlik belirteci biçimi güvenlik talepleri iletişim kurmak için. Basitleştirilmiş bir ara yazılım bu tür belirteçleri tüketen için nasıl kullanılacağını örneği hizmetine Ordering.Api mikro hizmet alınan bu kod parçası gibi görünebilir.

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    // Configure the pipeline to use authentication
    app.UseAuthentication();
    //…
    app.UseMvc();
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;

    }).AddJwtBearer(options =>
    {
        options.Authority = identityUrl;
        options.RequireHttpsMetadata = false;
        options.Audience = "orders";
    });
}
```

Bu kullanımı Parametreler şunlardır:

- `Audience` gelen belirteci veya erişim belirteci verir kaynak alıcısı temsil eder. Bu parametrede belirtilen değer belirteci parametreyi eşleşmiyorsa, belirteç reddedilir.

- `Authority` belirteci veren kimlik doğrulaması sunucusunun adresidir. JWT taşıyıcı kimlik doğrulaması ara yazılımı, belirtecin imzayı doğrulamak için kullanılacak ortak anahtarı almak için bu URI kullanır. Ara yazılım Ayrıca, onaylar `iss` belirteç parametresi bu URI ile eşleşir.

Başka bir parametre `RequireHttpsMetadata`, test amacıyla; yararlıdır ortamlarında test etmek, bu parametre false olarak burada yoksa sertifikaları ayarlayın. Gerçek dağıtımlarda, JWT taşıyıcı belirteçlerini her zaman yalnızca HTTPS üzerinden geçirilmelidir.

Yerinde bu ara yazılım ile JWT belirteçleri yetkilendirme üst bilgiler otomatik olarak çıkarılır. Bunlar daha sonra seri durumdan çıkarılmakta, doğrulanmış (değerleri `Audience` ve `Authority` parametreleri) ve daha sonra MVC eylemler veya yetkilendirme filtreleri tarafından başvurulabilmesi için kullanıcı bilgilerini olarak depolanmış.

JWT taşıyıcı kimlik doğrulaması ara yazılımı yerel bir sertifika yetkilisi kullanılabilir değilse, bir belirteci doğrulamak için kullanma gibi daha gelişmiş senaryoları da destekler. Bu senaryo için belirttiğiniz bir `TokenValidationParameters` nesnesine `JwtBearerOptions` nesne.

## <a name="additional-resources"></a>Ek kaynaklar

- **Tanımlama bilgilerini uygulamalar arasında paylaşma** \
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- **Kimliğe giriş** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **Rick Anderson. SMS ile iki öğeli kimlik doğrulama** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- **Facebook, Google ve diğer dış sağlayıcıları kullanarak kimlik doğrulamayı etkinleştirme** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- **Michell Anicas. OAuth 2 giriş** \
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- **AspNet.Security.OAuth.Providers** (ASP.NET OAuth sağlayıcıları için GitHub deposunu) \
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- **Danny Strockis. Azure AD'yi bir ASP.NET Core web uygulamasıyla tümleştirme** \
  <https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/>

- **Identityserver4. Resmi belgeleri** \
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
>[Önceki](../implement-resilient-applications/monitor-app-health.md)
>[İleri](authorization-net-microservices-web-applications.md)
