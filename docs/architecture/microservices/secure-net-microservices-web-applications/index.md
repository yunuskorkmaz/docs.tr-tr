---
title: .NET mikro hizmetleri ve Web uygulamalarının güvenliğini sağlama
description: .NET mikro hizmetleri ve Web uygulamalarında güvenlik-ASP.NET Core Web uygulamalarında kimlik doğrulama seçeneklerini öğrenin.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 0894465858e3503e2eddb5299b404f7ba95fdd6a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296477"
---
# <a name="make-secure-net-microservices-and-web-applications"></a>Güvenli .NET mikro hizmetleri ve Web uygulamaları oluşturun

Mikro hizmetlerde ve Web uygulamalarında güvenlikle ilgili olarak konunun bu şekilde birçok kitap alabilmesini sağlayacak pek çok konu vardır. Bu bölümde, kimlik doğrulama, yetkilendirme ve uygulama gizliliklerine odaklanacağız.

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a>.NET mikro hizmetleri ve Web uygulamalarında kimlik doğrulaması uygulama

Genellikle bir hizmet tarafından yayımlanan kaynakların ve API 'Lerin belirli Güvenilen Kullanıcı veya istemcilerle sınırlı olması gerekir. Bu tür API düzeyi güven kararlarını yapmanın ilk adımı kimlik doğrulamadır. Kimlik doğrulaması, bir kullanıcının kimliğini güvenilir bir şekilde doğrulama işlemidir.

Mikro hizmet senaryolarında, kimlik doğrulaması genellikle merkezi olarak işlenir. Bir API ağ geçidi kullanıyorsanız, Şekil 9-1 ' de gösterildiği gibi ağ geçidi kimlik doğrulaması için iyi bir yerdir. Bu yaklaşımı kullanırsanız, ağ geçidinden gelen veya olmayan iletilerin kimlik doğrulamasını yapmak için ek bir güvenlik yoksa, tek tek mikro hizmetlere doğrudan ulaşılamadığından emin olun (API ağ geçidi olmadan).

![API Gateway kimlik doğrulamasını merkezileştiren, istekleri mikro hizmetlere iletirken Kullanıcı bilgilerini ekler.](./media/image1.png)

**Şekil 9-1**. API ağ geçidiyle merkezi kimlik doğrulaması

Hizmetlere doğrudan erişilemiyorsa, kullanıcıların kimliğini doğrulamak için Azure Active Directory gibi bir kimlik doğrulama hizmeti veya güvenlik belirteci hizmeti (STS) görevi gören ayrılmış bir kimlik doğrulama mikro hizmeti kullanılabilir. Güven kararları, güvenlik belirteçleri veya tanımlama bilgileriyle hizmetler arasında paylaşılır. (Bu belirteçler, gerekirse [tanımlama bilgisi paylaşımı](/aspnet/core/security/cookie-sharing)uygulayarak ASP.NET Core uygulamalar arasında paylaşılabilir.) Bu model Şekil 9-2 ' de gösterilmiştir.

![Mikro hizmetlere doğrudan erişildiğinde, kimlik doğrulaması ve yetkilendirme içeren güven, mikro hizmetler arasında paylaşılan, adanmış bir mikro hizmet tarafından verilen bir güvenlik belirteci tarafından işlenir.](./media/image2.png)

**Şekil 9-2**. Kimlik mikro hizmetine göre kimlik doğrulaması; güven, bir yetkilendirme belirteci kullanılarak paylaşılır

### <a name="authenticate-with-aspnet-core-identity"></a>ASP.NET Core kimliğiyle kimlik doğrulama

Bir uygulamanın kullanıcılarını tanımlamak için ASP.NET Core birincil mekanizması [ASP.NET Core kimlik](/aspnet/core/security/authentication/identity) üyelik sistemidir. ASP.NET Core kimlik, geliştirici tarafından yapılandırılan bir veri deposundaki kullanıcı bilgilerini (oturum açma bilgileri, roller ve talepler dahil) depolar. Genellikle ASP.NET Core Identity veri deposu, `Microsoft.AspNetCore.Identity.EntityFrameworkCore` pakette belirtilen bir Entity Framework deposudur. Ancak, Azure Tablo depolama, CosmosDB veya diğer konumlarda kimlik bilgilerini depolamak için özel mağazalar veya diğer üçüncü taraf paketleri kullanılabilir.

Aşağıdaki kod, bireysel kullanıcı hesabı kimlik doğrulaması seçili olan ASP.NET Core Web uygulaması proje şablonundan alınmıştır. Başlangıç. ConfigureServices yönteminde EntityFramework. Core kullanılarak ASP.NET Core kimliğin nasıl yapılandırılacağını gösterir.

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

ASP.NET Core kimlik yapılandırıldıktan sonra, uygulamayı çağırarak etkinleştirin. Hizmetin `Startup.Configure` yönteminde useıdentity.

ASP.NET Core kimlik kullanmak çeşitli senaryolara izin vermez:

- UserManager türünü (userManager. CreateAsync) kullanarak yeni kullanıcı bilgileri oluşturun.

- SignInManager türünü kullanarak kullanıcıların kimliğini doğrulayın. Doğrudan oturum açmak `signInManager.SignInAsync` için veya `signInManager.PasswordSignInAsync` kullanıcının parolasının doğru olduğunu doğrulamak için ' yi kullanabilir ve sonra da ' de oturum açabilirsiniz.

- Bir tarayıcıdan gelen isteklerin, oturum açan kullanıcının kimlik ve taleplerini içermesi için bir tanımlama bilgisinde depolanan (ASP.NET Core Identity ara yazılımı tarafından okunan) bilgileri temel alan bir kullanıcıyı tanımlama.

ASP.NET Core kimlik [iki öğeli kimlik doğrulamasını](/aspnet/core/security/authentication/2fa)da destekler.

Yerel bir kullanıcı veri deposunu kullanan ve tanımlama bilgilerini kullanarak istekler arasında kimlik (MVC web uygulamaları için tipik olarak) tutan kimlik doğrulama senaryolarında, ASP.NET Core kimlik önerilen bir çözümdür.

### <a name="authenticate-with-external-providers"></a>Dış sağlayıcılarla kimlik doğrulama

ASP.NET Core Ayrıca, kullanıcıların [OAuth 2,0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) akışları aracılığıyla oturum açmasını sağlamak için [dış kimlik doğrulama sağlayıcılarının](/aspnet/core/security/authentication/social/) kullanılmasını da destekler. Bu, kullanıcıların Microsoft, Google, Facebook veya Twitter gibi sağlayıcılardan mevcut kimlik doğrulama süreçlerini kullanarak oturum açabileceği ve bu kimlikleri uygulamanızdaki bir ASP.NET Core kimlikle ilişkilendirebileceği anlamına gelir.

Dış kimlik doğrulamasını kullanmak için uygulamanızın HTTP istek işleme ardışık düzenine uygun kimlik doğrulama ara yazılımını dahil edersiniz. Bu ara yazılım, kimlik doğrulama sağlayıcısından URI yolları döndürmek, kimlik bilgilerini yakalamak ve SignInManager. Getexternalloginınfo yöntemi aracılığıyla kullanılabilir hale getirmek için istekleri işlemekten sorumludur.

Popüler dış kimlik doğrulama sağlayıcıları ve bunlarla ilişkili NuGet paketleri aşağıdaki tabloda gösterilmiştir:

| **Sağlayıcı**  | **Paket**                                          |
| ------------- | ---------------------------------------------------- |
| **Microsoft** | **Microsoft. AspNetCore. Authentication. MicrosoftAccount** |
| **Google**    | **Microsoft. AspNetCore. Authentication. Google**           |
| **'A**  | **Microsoft. AspNetCore. Authentication. Facebook**         |
| **Twitter**   | **Microsoft. AspNetCore. Authentication. Twitter**          |

Her durumda, ara yazılım ' `app.Use{ExternalProvider}Authentication` de `Startup.Configure`olduğu gibi bir kayıt yöntemine çağrı ile kaydedilir. Bu kayıt yöntemleri, sağlayıcının gerektirdiği şekilde uygulama KIMLIĞI ve gizli bilgiler (örneğin, bir parola) içeren bir seçenek nesnesi alır. Dış kimlik doğrulama sağlayıcıları, kullanıcıya hangi uygulamanın kimlik erişimi istediğini bildirmek için uygulamanın kaydolmasını ( [ASP.NET Core belgelerde](/aspnet/core/security/authentication/social/)açıklandığı gibi) gerektirir.

Ara yazılım `Startup.Configure`uygulamasına kaydedildikten sonra, kullanıcılardan herhangi bir denetleyici eyleminden oturum açmasını isteyebilirsiniz. Bunu yapmak için kimlik doğrulama sağlayıcısının adını `AuthenticationProperties` ve yeniden yönlendirme URL 'sini içeren bir nesne oluşturursunuz. Daha sonra `AuthenticationProperties` nesneyi geçiren bir sınama yanıtı döndürün. Aşağıdaki kod buna bir örnek gösterir.

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

RedirectUrl parametresi, kullanıcının kimliği doğrulandıktan sonra dış sağlayıcının yeniden yönlendirileceği URL 'YI içerir. URL, aşağıdaki Basitleştirilmiş örnekte olduğu gibi, dış kimlik bilgilerine göre kullanıcıyı imzalayamayacak bir eylemi temsil etmelidir:

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

Visual Studio 'da ASP.NET Code Web uygulaması projesini oluştururken **bireysel kullanıcı hesabı** kimlik doğrulaması seçeneğini belirlerseniz, Şekil 9-3 ' de gösterildiği gibi, bir dış sağlayıcı ile oturum açmak için gereken tüm kodlar zaten projede bulunur.

![Yeni ASP.NET Core Web uygulamasına yönelik iletişim kutusu, kimlik doğrulamasını değiştirmek için düğmeyi vurgular.](./media/image3.png)

**Şekil 9-3**. Web uygulaması projesi oluştururken dış kimlik doğrulaması kullanma seçeneği seçme

Daha önce listelenen dış kimlik doğrulama sağlayıcılarının yanı sıra, birçok daha fazla dış kimlik doğrulama sağlayıcısının kullanılmasına yönelik ara yazılım sağlayan üçüncü taraf paketleri de mevcuttur. Bir liste için bkz. GitHub 'da [Aspnet. Security. OAuth. Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) deposu.

Ayrıca, özel ihtiyaçları çözümlemek için kendi dış kimlik doğrulama ara yazılımını da oluşturabilirsiniz.

### <a name="authenticate-with-bearer-tokens"></a>Taşıyıcı belirteçleriyle kimlik doğrulama

ASP.NET Core kimliği (veya kimlik Plus dış kimlik doğrulama sağlayıcıları) ile kimlik doğrulaması, Kullanıcı bilgilerini bir tanımlama bilgisinde depolamanın uygun olduğu birçok Web uygulaması senaryosunda iyi çalışacaktır. Diğer senaryolarda, tanımlama bilgileri kalıcı ve veri iletimi gibi doğal bir yöntem değildir.

Örneğin, tek sayfalı uygulamalar (maça 'Lar) tarafından, yerel istemciler tarafından veya diğer Web API 'Leri tarafından erişilebilen yeniden kullanılabilir uç noktaları sunan bir ASP.NET Core Web API 'sinde, genellikle bunun yerine taşıyıcı belirteç kimlik doğrulamasını kullanmak istersiniz. Bu tür uygulamalar tanımlama bilgileriyle çalışmaz, ancak bir taşıyıcı belirtecini kolayca alabilir ve sonraki isteklerin yetkilendirme üstbilgisine dahil edebilir. Belirteç kimlik doğrulamasını etkinleştirmek için ASP.NET Core, [OAuth 2,0](https://oauth.net/2/) ve [OpenID Connect](https://openid.net/connect/)kullanımına yönelik çeşitli seçenekleri destekler.

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a>OpenID Connect veya OAuth 2,0 kimlik sağlayıcısı ile kimlik doğrulama

Kullanıcı bilgileri Azure Active Directory veya OpenID Connect ya da OAuth 2,0 ' ı destekleyen başka bir kimlik çözümünde depolanıyorsa, OpenID Connect kullanarak kimlik doğrulamak için **Microsoft. AspNetCore. Authentication. Openıdconnect** paketini kullanabilirsiniz akışıyla. Örneğin, eShopOnContainers 'daki Identity. API mikro hizmeti kimlik doğrulaması için, bir ASP.NET Core Web uygulaması aşağıdaki Basitleştirilmiş örnekte `Startup.cs`gösterildiği gibi bu paketteki ara yazılımı kullanabilir:

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

Bu iş akışını kullandığınızda, tüm Kullanıcı bilgileri depolama ve kimlik doğrulama kimlik hizmeti tarafından işlendiği için ASP.NET Core Identity ara yazılımı gerekli değildir.

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a>ASP.NET Core hizmetinden güvenlik belirteçleri verme

Dış kimlik sağlayıcısı kullanmak yerine yerel ASP.NET Core Identity kullanıcıları için güvenlik belirteçleri vermek isterseniz, bazı iyi üçüncü taraf kitaplıklarından yararlanabilirsiniz.

[Identityserver4](https://github.com/IdentityServer/IdentityServer4) ve [Openıddict](https://github.com/openiddict/openiddict-core) , bir ASP.NET Core hizmetinden güvenlik belirteçleri vermesini sağlamak üzere ASP.NET Core kimlikle kolayca tümleştirilen OpenID Connect sağlayıcılarıdır. [Identityserver4 belgeleri](https://identityserver4.readthedocs.io/en/latest/) , kitaplığı kullanmaya yönelik ayrıntılı yönergeler içerir. Ancak, belirteçleri vermek için ıdentityserver4 kullanmanın temel adımları aşağıdaki gibidir.

1. Uygulamayı çağırabilirsiniz. Useıdentityserver başlangıç. uygulamanın HTTP istek işleme ardışık düzenine ıdentityserver4 eklemek için yöntemi yapılandırın. Bu, kitaplığın OpenID Connect ve/Connect/tokengibi OAuth2 uç noktalarına istek sunmasını sağlar.

2. Identityserver4, Service 'e bir çağrı yaparak Startup. ConfigureServices içinde yapılandırırsınız. Addentityserver.

3. Aşağıdaki verileri ayarlayarak kimlik sunucusunu yapılandırırsınız:

   - İmzalama için kullanılacak [kimlik bilgileri](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) .

   - Kullanıcıların erişim isteyebilecek [kimlik ve API kaynakları](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) :

      - API kaynakları, bir kullanıcının bir erişim belirteciyle erişebileceği korumalı verileri veya işlevselliği temsil eder. Bir API kaynağına bir örnek, yetkilendirme gerektiren bir Web API 'SI (veya API kümesi) olacaktır.

      - Kimlik kaynakları, bir kullanıcıyı tanımlamak için bir istemciye verilen bilgileri (talepler) temsil eder. Talepler Kullanıcı adı, e-posta adresi vb. içerebilir.

   - Belirteçleri istemek için bağlantı yapılacak [istemciler](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) .

   - [ASP.NET Core kimliği](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) veya alternatif gibi Kullanıcı bilgileri için depolama mekanizması.

Identityserver4 için kullanılacak istemcileri ve kaynakları belirttiğinizde, bellek içi istemci veya kaynak depoları alan <xref:System.Collections.Generic.IEnumerable%601> yöntemlere uygun türde bir koleksiyon geçirebilirsiniz. Ya da daha karmaşık senaryolar için, bağımlılık ekleme yoluyla istemci veya kaynak sağlayıcısı türleri sağlayabilirsiniz.

Identityserver4 için, bellek içi kaynakları ve özel bir ılientstore türü tarafından sunulan istemcileri kullanmak için örnek bir yapılandırma aşağıdaki örnekteki gibi görünebilir:

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

### <a name="consume-security-tokens"></a>Güvenlik belirteçlerini kullanma

Bir OpenID Connect uç noktasına karşı kimlik doğrulaması veya kendi güvenlik belirteçlerinizi verme bazı senaryolar içerir. Ancak, yalnızca farklı bir hizmet tarafından sunulan geçerli güvenlik belirteçleri olan kullanıcılarla erişimi sınırlamaya yönelik bir hizmet hakkında ne var?

Bu senaryo için, JWT belirteçlerini işleyen kimlik doğrulama ara yazılımı **Microsoft. AspNetCore. Authentication. Jwttaşıyıcı** paketinde bulunabilir. JWT, "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" için temsil eder ve güvenlik taleplerini iletişim kurmak için ortak bir güvenlik belirteci BIÇIMIDIR (RFC 7519 tarafından tanımlanır). Bu tür belirteçleri kullanmak için ara yazılımın nasıl kullanılacağına ilişkin basitleştirilmiş bir örnek, sıralama. API mikro hizmeti olan eShopOnContainers 'dan alınan bu kod parçası gibi görünebilir.

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

Bu kullanımdaki parametreler şunlardır:

- `Audience`gelen belirtecin veya belirtecin erişim izni verdiği kaynağın alıcısını temsil eder. Bu parametrede belirtilen değer, belirteçteki parametreyle eşleşmezse, belirteç reddedilir.

- `Authority`, belirteç veren kimlik doğrulama sunucusunun adresidir. JWT taşıyıcı kimlik doğrulama ara yazılımı, belirtecin imzasını doğrulamak için kullanılabilecek ortak anahtarı almak için bu URI 'yi kullanır. Ara yazılım, belirteçteki `iss` parametrenin bu URI ile eşleştiğini de onaylar.

Başka bir parametre `RequireHttpsMetadata`, test amaçları için yararlıdır; bu parametreyi yanlış olarak ayarlarsanız, sertifikalarınızın olmadığı ortamlarda test edebilirsiniz. Gerçek dünyada dağıtımlarda, JWT taşıyıcı belirteçlerinin her zaman yalnızca HTTPS üzerinden geçirilmesi gerekir.

Bu ara yazılım söz konusu olduğunda, JWT belirteçleri yetkilendirme başlıklarından otomatik olarak ayıklanır. Daha sonra bunlar seri durumdan silinir, onaylanır ( `Audience` ve `Authority` parametrelerdeki değerler kullanılarak) ve daha sonra MVC eylemleri veya Yetkilendirme filtreleri tarafından başvurulmak üzere Kullanıcı bilgileri olarak depolanır.

JWT taşıyıcı kimlik doğrulama ara yazılımı, yetkili kullanılamıyorsa bir belirteci doğrulamak için yerel bir sertifika kullanma gibi daha gelişmiş senaryoları da destekleyebilir. Bu senaryo için, `TokenValidationParameters` `JwtBearerOptions` nesnesinde bir nesne belirtebilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

- **Uygulamalar arasında tanımlama bilgilerini paylaşma** \
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- **Kimliğe giriş** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **Rick Anderson. SMS ile iki öğeli kimlik doğrulama** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- **Facebook, Google ve diğer dış sağlayıcıları kullanarak kimlik doğrulamasını etkinleştirme** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- **Michell Anıas. OAuth 2 ' ye giriş** \
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- **Aspnet. Security. OAuth. Providers** (ASP.net OAuth sağlayıcıları için GitHub deposu) \
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- **Danny Strock. Azure AD 'yi bir ASP.NET Core Web uygulamasıyla tümleştirme** \
  <https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/>

- **Identityserver4. Resmi belgeler** \
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
>[Önceki](../implement-resilient-applications/monitor-app-health.md)İleri
>[](authorization-net-microservices-web-applications.md)
