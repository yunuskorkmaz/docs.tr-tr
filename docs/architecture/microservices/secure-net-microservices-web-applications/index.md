---
title: .NET MikroHizmetler ve Web Uygulamalarının Güvenliğini Sağlama
description: .NET Microservices ve Web Applications güvenlik - ASP.NET Core web uygulamalarında kimlik doğrulama seçeneklerini tanıyın.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 0ac2591f8650e9f8cf29560735a9ec803d29ee4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628338"
---
# <a name="make-secure-net-microservices-and-web-applications"></a>Güvenli olun .NET Microservices ve Web Uygulamaları

Mikro hizmetlerde ve web uygulamalarında güvenlik le ilgili o kadar çok yön vardır ki, konu bunun gibi birkaç kitabı kolayca alabilir, bu nedenle bu bölümde kimlik doğrulama, yetkilendirme ve uygulama sırlarına odaklanacağız.

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a>.NET mikrohizmetlerde ve web uygulamalarında kimlik doğrulamayı uygulayın

Bir hizmet tarafından yayınlanan kaynakların ve API'lerin belirli güvenilir kullanıcılar veya istemcilerle sınırlı olması genellikle gereklidir. Bu tür API düzeyinde güven kararları vermenin ilk adımı kimlik doğrulamadır. Kimlik doğrulama, kullanıcının kimliğini güvenilir bir şekilde doğrulama işlemidir.

Mikro hizmet senaryolarında kimlik doğrulama genellikle merkezi olarak işlenir. Bir API Ağ Geçidi kullanıyorsanız, ağ geçidi Şekil 9-1'de gösterildiği gibi kimlik doğrulaması yapmak için iyi bir yerdir. Bu yaklaşımı kullanırsanız, ağ geçidinden gelen iletileri doğrulamak için ek güvenlik olmadığı sürece, tek tek mikro hizmetlere doğrudan (API Ağ Geçidi olmadan) ulaşılamayacağından emin olun.

![İstemci mobil uygulamasının arka uçla nasıl etkileşimde olduğunu gösteren diyagram.](./media/index/api-gateway-centralized-authentication.png)

**Şekil 9-1**. API Ağ Geçidi ile merkezi kimlik doğrulama

API Ağ Geçidi kimlik doğrulamasını merkezileştirdiğinde, istekleri mikro hizmetlere iletirken kullanıcı bilgilerini ekler. Hizmetlere doğrudan erişilebiliyorsa, Azure Etkin Dizini gibi bir kimlik doğrulama hizmeti veya güvenlik belirteci hizmeti (STS) olarak hareket eden özel bir kimlik doğrulama mikro hizmeti, kullanıcıların kimliğini doğrulamak için kullanılabilir. Güven kararları, güvenlik belirteçleri veya tanımlama bilgileriyle hizmetler arasında paylaşılır. (Bu belirteçler, gerekirse [çerez paylaşımı](/aspnet/core/security/cookie-sharing)uygulanarak ASP.NET Core uygulamaları arasında paylaşılabilir.) Bu desen Şekil 9-2'de gösterilmiştir.

![Arka uç mikro hizmetleri aracılığıyla kimlik doğrulamasını gösteren diyagram.](./media/index/identity-microservice-authentication.png)

**Şekil 9-2**. Kimlik microservice tarafından kimlik doğrulama; güven bir yetkilendirme belirteci kullanılarak paylaşılır

Mikro hizmetlere doğrudan erişildiğinde, kimlik doğrulama ve yetkilendirme yi içeren güven, mikro hizmetler arasında paylaşılan özel bir microservice tarafından verilen bir güvenlik belirteci tarafından işlenir.

### <a name="authenticate-with-aspnet-core-identity"></a>ASP.NET Temel Kimlikle Kimlik Doğrulama

bir uygulamanın kullanıcılarını tanımlamak için ASP.NET Core'daki birincil mekanizma [ASP.NET Çekirdek Kimlik](/aspnet/core/security/authentication/identity) üyelik sistemidir. ASP.NET Core Identity, geliştirici tarafından yapılandırılan bir veri deposunda kullanıcı bilgilerini (oturum açma bilgileri, roller ve talepler dahil) saklar. Genellikle, ASP.NET Çekirdek Kimlik veri deposu `Microsoft.AspNetCore.Identity.EntityFrameworkCore` pakette sağlanan bir Entity Framework deposudur. Ancak, kimlik bilgilerini Azure Tablo Depolama, CosmosDB veya diğer konumlarda depolamak için özel mağazalar veya diğer üçüncü taraf paketleri kullanılabilir.

> [!TIP]
> ASP.NET Core 2.1 ve daha sonra bir [Razor Class Kitaplığı](/aspnet/core/razor-pages/ui-class)olarak [ASP.NET Çekirdek Kimlik](/aspnet/core/security/authentication/identity) sağlar, böylece önceki sürümlerde olduğu gibi, projenizde gerekli kodun çok görmezsiniz. İhtiyaçlarınıza uygun kimlik kodunu nasıl özelleştirdiğinize ilişkin ayrıntılar [için, ASP.NET Core projelerinde İskele Kimliği'ne](/aspnet/core/security/authentication/scaffold-identity)bakın.

Aşağıdaki kod, tek tek seçilen ASP.NET Core Web Application MVC 3.1 proje şablonundan alınır. Yöntemde Entity Framework Core kullanarak ASP.NET Çekirdek `Startup.ConfigureServices` Kimliğin nasıl yapılandırılabildiğini gösterir.

```csharp
public void ConfigureServices(IServiceCollection services)
{
    //...
    services.AddDbContext<ApplicationDbContext>(options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection")));

    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddRazorPages();
    //...
}
```

ASP.NET Çekirdek Kimlik yapılandırıldıktan sonra, `app.UseAuthentication()` `endpoints.MapRazorPages()` `Startup.Configure` hizmetin yönteminde aşağıdaki kodda gösterildiği gibi ve ekleyerek bunu etkinleştirin:

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    //...
    app.UseRouting();

    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapRazorPages();
    });
    //...
}
```

> [!IMPORTANT]
> Önseki kodundaki satırlar, Kimliğin doğru çalışması için **GÖSTERİlEN SİPARİşTE OLMALIDIR.**

ASP.NET Çekirdek Kimlik kullanmak birkaç senaryoya olanak sağlar:

- UserManager türünü (userManager.CreateAsync) kullanarak yeni kullanıcı bilgileri oluşturun.

- SignInManager türünü kullanarak kullanıcıların kimliğini doğrulayın. Doğrudan oturum `signInManager.SignInAsync` açmayı veya `signInManager.PasswordSignInAsync` kullanıcının parolasının doğru olduğunu doğrulamak ve oturum açmanızı kullanabilirsiniz.

- Bir tarayıcıdan sonraki isteklerin oturum açmış bir kullanıcının kimliğini ve taleplerini içerecek şekilde çerezde depolanan bilgilere (ASP.NET Çekirdek Kimlik aracı tarafından okunan) dayalı olarak bir kullanıcıyı tanımlayın.

ASP.NET Çekirdek Kimlik de [iki faktörlü kimlik doğrulaması](/aspnet/core/security/authentication/2fa)destekler.

Yerel bir kullanıcı veri deposundan yararlanan ve tanımlama bilgilerini kullanan istekler arasında kimlik kalıcı olan kimlik doğrulama senaryoları için (MVC web uygulamalarında olduğu gibi), ASP.NET Çekirdek Kimlik önerilen bir çözümdür.

### <a name="authenticate-with-external-providers"></a>Harici sağlayıcılarla kimlik doğrulaması

ASP.NET Core, kullanıcıların [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) akışları aracılığıyla oturum açmalarına izin vermek için [harici kimlik doğrulama sağlayıcılarının](/aspnet/core/security/authentication/social/) kullanılmasını da destekler. Bu, kullanıcıların Microsoft, Google, Facebook veya Twitter gibi sağlayıcılardan gelen mevcut kimlik doğrulama işlemlerini kullanarak oturum açabileceği ve bu kimlikleri uygulamanızda ASP.NET Bir Çekirdek kimliğiyle ilişkilendirebileceği anlamına gelir.

Daha önce de belirtildiği gibi kimlik doğrulama ara ware dahil olmak `app.UseAuthentication()` üzere, dış kimlik doğrulaması `Startup` kullanmak için, yöntemi kullanarak, ayrıca aşağıdaki örnekte gösterildiği gibi dış sağlayıcı kayıt gerekir:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    //...
    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddAuthentication()
        .AddMicrosoftAccount(microsoftOptions =>
        {
            microsoftOptions.ClientId = Configuration["Authentication:Microsoft:ClientId"];
            microsoftOptions.ClientSecret = Configuration["Authentication:Microsoft:ClientSecret"];
        })
        .AddGoogle(googleOptions => { ... })
        .AddTwitter(twitterOptions => { ... })
        .AddFacebook(facebookOptions => { ... });
    //...
}
```

Popüler dış kimlik doğrulama sağlayıcıları ve bunların ilişkili NuGet paketleri aşağıdaki tabloda gösterilir:

| **Sağlayıcı**  | **Paket**                                          |
| ------------- | ---------------------------------------------------- |
| **Microsoft** | **Microsoft.AspNetCore.Authentication.MicrosoftAccount** |
| **Google**    | **Microsoft.AspNetCore.Authentication.Google**           |
| **Facebook**  | **Microsoft.AspNetCore.Authentication.Facebook**         |
| **Twitter**   | **Microsoft.AspNetCore.Authentication.Twitter**          |

Her durumda, satıcıya bağımlı olan ve genellikle şunları içeren bir uygulama kayıt yordamı tamamlamanız gerekir:

1. İstemci Başvuru Kimliği alma.
2. İstemci Uygulama Sırrı Alma.
3. Yetkilendirme ara yazılımı ve kayıtlı sağlayıcı tarafından işlenen bir yeniden yönlendirme URL'sini yapılandırma
4. İsteğe bağlı olarak, oturum dışı bir URL'yi, Tek Oturum Açma (SSO) senaryosunda oturum açma işlemlerini düzgün bir şekilde işlemek için yapılandırmak.

Uygulamanızı harici bir sağlayıcı için yapılandırma hakkında ayrıntılı bilgi [için, ASP.NET Çekirdek belgelerinde Dış sağlayıcı kimlik doğrulaması'na](/aspnet/core/security/authentication/social/)bakın).

>[!TIP]
>Tüm ayrıntılar, daha önce bahsedilen yetkilendirme aracıları ve hizmetleri tarafından işlenir. Bu nedenle, Visual Studio'da, şekil 9-3'te gösterildiği gibi, daha önce bahsedilen kimlik doğrulama sağlayıcılarını kaydetmenin yanı sıra, ASP.NET Kodu web uygulama projesini oluştururken **Bireysel Kullanıcı Hesabı** kimlik doğrulama seçeneğini seçmeniz gerekir.

![Yeni ASP.NET Çekirdek Web Uygulaması iletişim kutusunun ekran görüntüsü.](./media/index/select-individual-user-account-authentication-option.png)

**Şekil 9-3**. Visual Studio 2019'da bir web uygulama projesi oluştururken harici kimlik doğrulaması kullanmak için Bireysel Kullanıcı Hesapları seçeneğini seçme.

Daha önce listelenen dış kimlik doğrulama sağlayıcılarına ek olarak, daha birçok dış kimlik doğrulama sağlayıcısı kullanmak için ara yazılım sağlayan üçüncü taraf paketleri de mevcuttur. Bir liste için GitHub'daki [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) deposuna bakın.

Ayrıca bazı özel ihtiyacı çözmek için kendi dış kimlik doğrulama aracı oluşturabilirsiniz.

### <a name="authenticate-with-bearer-tokens"></a>Taşıyıcı belirteçleriyle kimlik doğrulaması

Temel Kimlik (veya Kimlik artı harici kimlik doğrulama sağlayıcıları) ASP.NET ile kimlik doğrulama, kullanıcı bilgilerini bir çerezde depolamanın uygun olduğu birçok web uygulama senaryosunda iyi çalışır. Ancak diğer senaryolarda, tanımlama bilgileri kalıcı veri ve iletim doğal bir araç değildir.

Örneğin, Tek Sayfa Uygulamaları (SPA'lar), yerel istemciler ve hatta diğer Web API'leri tarafından erişilebilen yeniden kullanılabilir uç noktaları ortaya çıkaran ASP.NET Core Web API'sinde, genellikle taşıyıcı belirteç kimlik doğrulaması kullanmak istersiniz. Bu tür uygulamalar tanımlama bilgileriyle çalışmaz, ancak taşıyıcı belirteci kolayca alabilir ve sonraki isteklerin yetkilendirme üstbilgisine ekleyebilir. Belirteç kimlik doğrulamasını etkinleştirmek için, ASP.NET Core [OAuth 2.0](https://oauth.net/2/) ve [OpenID Connect'i](https://openid.net/connect/)kullanmak için çeşitli seçenekleri destekler.

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a>OpenID Connect veya OAuth 2.0 Kimlik sağlayıcısıyla kimlik doğrulaması

Kullanıcı bilgileri Azure Active Directory'de veya OpenID Connect veya OAuth 2.0'ı destekleyen başka bir kimlik çözümünde depolanıyorsa, OpenID Connect iş akışını kullanarak kimlik doğrulaması yapmak için **Microsoft.AspNetCore.Authentication.OpenIdConnect** paketini kullanabilirsiniz. Örneğin, eShopOnContainers Identity.Api microservice doğrulaması için, bir ASP.NET Core web uygulaması aşağıdaki basitleştirilmiş örnekte gösterildiği `Startup.cs`gibi bu paketten ara ware kullanabilirsiniz:

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseAuthentication();
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
    });
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");
    var callBackUrl = Configuration.GetValue<string>("CallBackUrl");
    var sessionCookieLifetime = configuration.GetValue("SessionCookieLifetimeMinutes", 60);

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;
    })
    .AddCookie(setup => setup.ExpireTimeSpan = TimeSpan.FromMinutes(sessionCookieLifetime))
    .AddOpenIdConnect(options =>
    {
        options.SignInScheme = CookieAuthenticationDefaults.AuthenticationScheme;
        options.Authority = identityUrl.ToString();
        options.SignedOutRedirectUri = callBackUrl.ToString();
        options.ClientId = useLoadTest ? "mvctest" : "mvc";
        options.ClientSecret = "secret";
        options.ResponseType = useLoadTest ? "code id_token token" : "code id_token";
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

Tüm kullanıcı bilgileri depolama ve kimlik doğrulama Kimlik hizmeti tarafından işlenir, çünkü bu iş akışını kullandığınızda, ASP.NET Çekirdek Kimlik aracı gerekli olmadığını unutmayın.

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a>ASP.NET Core hizmetinden güvenlik belirteçleri verme

Harici kimlik sağlayıcısı kullanmak yerine yerel ASP.NET Çekirdek Kimlik kullanıcıları için güvenlik belirteçleri vermeyi tercih ederseniz, bazı iyi üçüncü taraf kitaplıklarından yararlanabilirsiniz.

[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) ve [OpenIddict,](https://github.com/openiddict/openiddict-core) ASP.NET Core hizmetinden güvenlik belirteçleri çıkarmanıza izin vermek için ASP.NET Çekirdek Kimlikle kolayca entegre olan OpenID Connect sağlayıcılarıdır. [IdentityServer4 belgeleri,](https://identityserver4.readthedocs.io/en/latest/) kitaplığı kullanmak için ayrıntılı talimatlara sahiptir. Ancak, belirteçleri vermek için IdentityServer4 kullanarak temel adımları aşağıdaki gibidir.

1. Uygulamayı ararsın. IdentityServer'ı, uygulamanın HTTP istek işleme ardışık hattına IdentityServer4 eklemek için Başlangıç.Configure yönteminde kullanın. Bu, kitaplığın OpenID Connect ve /connect/token gibi OAuth2 uç noktalarına istekler sunmasını sağlar.

2. IdentityServer4'i Startup.ConfigureServices'de, hizmetlere çağrı yaparak yapılandırAbilirsiniz. AddIdentityServer.

3. Aşağıdaki verileri ayarlayarak kimlik sunucusunu yapılandırAbilirsiniz:

   - İmzalamak için kullanılacak [kimlik bilgileri.](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html)

   - Kullanıcıların erişmek isteyebileceği [Kimlik ve API kaynakları:](https://identityserver4.readthedocs.io/en/latest/topics/resources.html)

      - API kaynakları, kullanıcının bir erişim belirteciyle erişebileceği korumalı verileri veya işlevselliği temsil ediyor. API kaynağına örnek olarak, yetkilendirme gerektiren bir web API 'si (veya API kümesi) olur.

      - Kimlik kaynakları, bir kullanıcıyı tanımlamak için istemciye verilen bilgileri (talepleri) temsil eder. Talepler, kullanıcı adını, e-posta adresini ve benzeri bilgileri içerebilir.

   - Jeton istemek için bağlanacak [istemciler.](https://identityserver4.readthedocs.io/en/latest/topics/clients.html)

   - [ASP.NET Çekirdek Kimlik](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) veya bir alternatif gibi kullanıcı bilgileri için depolama mekanizması.

IdentityServer4'ün kullanması için istemciler ve kaynaklar <xref:System.Collections.Generic.IEnumerable%601> belirttiğiniz zaman, uygun türde bir koleksiyonu bellek istemcisi veya kaynak depolarını alan yöntemlere geçirebilirsiniz. Veya daha karmaşık senaryolar için, Bağımlılık Enjeksiyonu aracılığıyla istemci veya kaynak sağlayıcı türleri sağlayabilirsiniz.

IdentityServer4'in bellek içi kaynakları ve özel bir IClientStore türü tarafından sağlanan istemcileri kullanması için örnek bir yapılandırma aşağıdaki örnek gibi görünebilir:

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //...
    services.AddSingleton<IClientStore, CustomClientStore>();
    services.AddIdentityServer()
        .AddSigningCredential("CN=sts")
        .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
        .AddAspNetIdentity<ApplicationUser>();
    //...
}
```

### <a name="consume-security-tokens"></a>Güvenlik belirteçlerini tüketin

OpenID Connect bitiş noktasına karşı kimlik doğrulaması veya kendi güvenlik belirteçlerinizi verme bazı senaryoları kapsar. Ancak, farklı bir hizmet tarafından sağlanan geçerli güvenlik belirteçleri olan kullanıcılara erişimi sınırlaması gereken bir hizmete ne deilmelidir?

Bu senaryo için, JWT belirteçlerini işleyen kimlik doğrulama aracı **Microsoft.AspNetCore.Authentication.JwtBearer** paketinde kullanılabilir. JWT , "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" anlamına gelir ve güvenlik taleplerini iletmek için ortak bir güvenlik belirteci biçimidir (RFC 7519 tarafından tanımlanır). Bu tür belirteçleri tüketmek için ara ware nasıl kullanılacağı basitleştirilmiş bir örnek bu kod parçası gibi görünebilir, eShopOnContainers Ordering.Api microservice alınan.

```csharp
// Startup.cs

public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    // Configure the pipeline to use authentication
    app.UseAuthentication();
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
    });
}

public void ConfigureServices(IServiceCollection services)
{
    var identityUrl = Configuration.GetValue<string>("IdentityUrl");

    // Add Authentication services

    services.AddAuthentication(options =>
    {
        options.DefaultAuthenticateScheme = AspNetCore.Authentication.JwtBearer.JwtBearerDefaults.AuthenticationScheme;
        options.DefaultChallengeScheme = AspNetCore.Authentication.JwtBearer.JwtBearerDefaults.AuthenticationScheme;

    }).AddJwtBearer(options =>
    {
        options.Authority = identityUrl;
        options.RequireHttpsMetadata = false;
        options.Audience = "orders";
    });
}
```

Bu kullanımdaki parametreler şunlardır:

- `Audience`gelen belirteci veya belirteç erişim verdiği kaynak alıcısını temsil eder. Bu parametrede belirtilen değer belirteçteki parametreyle eşleşmiyorsa, belirteç reddedilir.

- `Authority`belirteç veren kimlik doğrulama sunucusunun adresidir. JWT taşıyıcı kimlik doğrulaması aracı, belirteç imzasını doğrulamak için kullanılabilecek ortak anahtarı almak için bu URI'yi kullanır. Ara yazılım, belirteçteki `iss` parametrenin bu URI ile eşleştiğini de doğrular.

Başka bir `RequireHttpsMetadata`parametre, , test amaçlı yararlıdır; sertifikaların olmadığı ortamlarda test edilebilmeniz için bu parametreyi yanlış olarak ayarlarsınız. Gerçek dünyadaki dağıtımlarda, JWT taşıyıcı belirteçleri her zaman yalnızca HTTPS üzerinden geçirilmelidir.

Bu ara yazılım yerinde, JWT belirteçleri otomatik olarak yetkilendirme üstbilgisinden ayıklanır. Daha sonra deserialized, doğrulanır (ve `Audience` `Authority` parametrelerdeki değerleri kullanarak) ve daha sonra MVC eylemleri veya yetkilendirme filtreleri tarafından başvurulacak kullanıcı bilgileri olarak saklanır.

JWT taşıyıcı kimlik doğrulama aracı, yetki yoksa belirteci doğrulamak için yerel bir sertifika kullanmak gibi daha gelişmiş senaryoları da destekleyebilir. Bu senaryo `TokenValidationParameters` `JwtBearerOptions` için, nesnebir nesne belirtebilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

- **Çerezleri uygulamalar arasında paylaşma** \
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- **Kimliğe Giriş** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **Rick Anderson' ı. SMS ile iki faktörlü kimlik doğrulama** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- **Facebook, Google ve diğer harici sağlayıcıları kullanarak kimlik doğrulamayı etkinleştirme** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- **Michell Anicas. OAuth 2'ye Giriş** \
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- **AspNet.Security.OAuth.Providers** (ASP.NET OAuth sağlayıcıları için GitHub repo) \
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- **IdentityServer4. Resmi belgeler** \
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
>[Önceki](../implement-resilient-applications/monitor-app-health.md)
>[Sonraki](authorization-net-microservices-web-applications.md)
