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
# <a name="make-secure-net-microservices-and-web-applications"></a><span data-ttu-id="09ceb-103">Güvenli olun .NET Microservices ve Web Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="09ceb-103">Make secure .NET Microservices and Web Applications</span></span>

<span data-ttu-id="09ceb-104">Mikro hizmetlerde ve web uygulamalarında güvenlik le ilgili o kadar çok yön vardır ki, konu bunun gibi birkaç kitabı kolayca alabilir, bu nedenle bu bölümde kimlik doğrulama, yetkilendirme ve uygulama sırlarına odaklanacağız.</span><span class="sxs-lookup"><span data-stu-id="09ceb-104">There are so many aspects about security in microservices and web applications that the topic could easy take several books like this one so, in this section, we'll focus on authentication, authorization, and application secrets.</span></span>

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a><span data-ttu-id="09ceb-105">.NET mikrohizmetlerde ve web uygulamalarında kimlik doğrulamayı uygulayın</span><span class="sxs-lookup"><span data-stu-id="09ceb-105">Implement authentication in .NET microservices and web applications</span></span>

<span data-ttu-id="09ceb-106">Bir hizmet tarafından yayınlanan kaynakların ve API'lerin belirli güvenilir kullanıcılar veya istemcilerle sınırlı olması genellikle gereklidir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-106">It's often necessary for resources and APIs published by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="09ceb-107">Bu tür API düzeyinde güven kararları vermenin ilk adımı kimlik doğrulamadır.</span><span class="sxs-lookup"><span data-stu-id="09ceb-107">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="09ceb-108">Kimlik doğrulama, kullanıcının kimliğini güvenilir bir şekilde doğrulama işlemidir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-108">Authentication is the process of reliably verify a user’s identity.</span></span>

<span data-ttu-id="09ceb-109">Mikro hizmet senaryolarında kimlik doğrulama genellikle merkezi olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-109">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="09ceb-110">Bir API Ağ Geçidi kullanıyorsanız, ağ geçidi Şekil 9-1'de gösterildiği gibi kimlik doğrulaması yapmak için iyi bir yerdir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-110">If you're using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 9-1.</span></span> <span data-ttu-id="09ceb-111">Bu yaklaşımı kullanırsanız, ağ geçidinden gelen iletileri doğrulamak için ek güvenlik olmadığı sürece, tek tek mikro hizmetlere doğrudan (API Ağ Geçidi olmadan) ulaşılamayacağından emin olun.</span><span class="sxs-lookup"><span data-stu-id="09ceb-111">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![İstemci mobil uygulamasının arka uçla nasıl etkileşimde olduğunu gösteren diyagram.](./media/index/api-gateway-centralized-authentication.png)

<span data-ttu-id="09ceb-113">**Şekil 9-1**.</span><span class="sxs-lookup"><span data-stu-id="09ceb-113">**Figure 9-1**.</span></span> <span data-ttu-id="09ceb-114">API Ağ Geçidi ile merkezi kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="09ceb-114">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="09ceb-115">API Ağ Geçidi kimlik doğrulamasını merkezileştirdiğinde, istekleri mikro hizmetlere iletirken kullanıcı bilgilerini ekler.</span><span class="sxs-lookup"><span data-stu-id="09ceb-115">When the API Gateway centralizes authentication, it adds user information when forwarding requests to the microservices.</span></span> <span data-ttu-id="09ceb-116">Hizmetlere doğrudan erişilebiliyorsa, Azure Etkin Dizini gibi bir kimlik doğrulama hizmeti veya güvenlik belirteci hizmeti (STS) olarak hareket eden özel bir kimlik doğrulama mikro hizmeti, kullanıcıların kimliğini doğrulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-116">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="09ceb-117">Güven kararları, güvenlik belirteçleri veya tanımlama bilgileriyle hizmetler arasında paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="09ceb-117">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="09ceb-118">(Bu belirteçler, gerekirse [çerez paylaşımı](/aspnet/core/security/cookie-sharing)uygulanarak ASP.NET Core uygulamaları arasında paylaşılabilir.) Bu desen Şekil 9-2'de gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-118">(These tokens can be shared between ASP.NET Core applications, if needed, by implementing [cookie sharing](/aspnet/core/security/cookie-sharing).) This pattern is illustrated in Figure 9-2.</span></span>

![Arka uç mikro hizmetleri aracılığıyla kimlik doğrulamasını gösteren diyagram.](./media/index/identity-microservice-authentication.png)

<span data-ttu-id="09ceb-120">**Şekil 9-2**.</span><span class="sxs-lookup"><span data-stu-id="09ceb-120">**Figure 9-2**.</span></span> <span data-ttu-id="09ceb-121">Kimlik microservice tarafından kimlik doğrulama; güven bir yetkilendirme belirteci kullanılarak paylaşılır</span><span class="sxs-lookup"><span data-stu-id="09ceb-121">Authentication by identity microservice; trust is shared using an authorization token</span></span>

<span data-ttu-id="09ceb-122">Mikro hizmetlere doğrudan erişildiğinde, kimlik doğrulama ve yetkilendirme yi içeren güven, mikro hizmetler arasında paylaşılan özel bir microservice tarafından verilen bir güvenlik belirteci tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-122">When microservices are accessed directly, trust, that includes authentication and authorization, is handled by a security token issued by a dedicated microservice, shared between microservices.</span></span>

### <a name="authenticate-with-aspnet-core-identity"></a><span data-ttu-id="09ceb-123">ASP.NET Temel Kimlikle Kimlik Doğrulama</span><span class="sxs-lookup"><span data-stu-id="09ceb-123">Authenticate with ASP.NET Core Identity</span></span>

<span data-ttu-id="09ceb-124">bir uygulamanın kullanıcılarını tanımlamak için ASP.NET Core'daki birincil mekanizma [ASP.NET Çekirdek Kimlik](/aspnet/core/security/authentication/identity) üyelik sistemidir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-124">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="09ceb-125">ASP.NET Core Identity, geliştirici tarafından yapılandırılan bir veri deposunda kullanıcı bilgilerini (oturum açma bilgileri, roller ve talepler dahil) saklar.</span><span class="sxs-lookup"><span data-stu-id="09ceb-125">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="09ceb-126">Genellikle, ASP.NET Çekirdek Kimlik veri deposu `Microsoft.AspNetCore.Identity.EntityFrameworkCore` pakette sağlanan bir Entity Framework deposudur.</span><span class="sxs-lookup"><span data-stu-id="09ceb-126">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` package.</span></span> <span data-ttu-id="09ceb-127">Ancak, kimlik bilgilerini Azure Tablo Depolama, CosmosDB veya diğer konumlarda depolamak için özel mağazalar veya diğer üçüncü taraf paketleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-127">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, CosmosDB, or other locations.</span></span>

> [!TIP]
> <span data-ttu-id="09ceb-128">ASP.NET Core 2.1 ve daha sonra bir [Razor Class Kitaplığı](/aspnet/core/razor-pages/ui-class)olarak [ASP.NET Çekirdek Kimlik](/aspnet/core/security/authentication/identity) sağlar, böylece önceki sürümlerde olduğu gibi, projenizde gerekli kodun çok görmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="09ceb-128">ASP.NET Core 2.1 and later provides [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) as a [Razor Class Library](/aspnet/core/razor-pages/ui-class), so you won't see much of the necessary code in your project, as was the case for previous versions.</span></span> <span data-ttu-id="09ceb-129">İhtiyaçlarınıza uygun kimlik kodunu nasıl özelleştirdiğinize ilişkin ayrıntılar [için, ASP.NET Core projelerinde İskele Kimliği'ne](/aspnet/core/security/authentication/scaffold-identity)bakın.</span><span class="sxs-lookup"><span data-stu-id="09ceb-129">For details on how to customize the Identity code to suit your needs, see [Scaffold Identity in ASP.NET Core projects](/aspnet/core/security/authentication/scaffold-identity).</span></span>

<span data-ttu-id="09ceb-130">Aşağıdaki kod, tek tek seçilen ASP.NET Core Web Application MVC 3.1 proje şablonundan alınır.</span><span class="sxs-lookup"><span data-stu-id="09ceb-130">The following code is taken from the ASP.NET Core Web Application MVC 3.1 project template with individual user account authentication selected.</span></span> <span data-ttu-id="09ceb-131">Yöntemde Entity Framework Core kullanarak ASP.NET Çekirdek `Startup.ConfigureServices` Kimliğin nasıl yapılandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-131">It shows how to configure ASP.NET Core Identity using Entity Framework Core in the `Startup.ConfigureServices` method.</span></span>

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

<span data-ttu-id="09ceb-132">ASP.NET Çekirdek Kimlik yapılandırıldıktan sonra, `app.UseAuthentication()` `endpoints.MapRazorPages()` `Startup.Configure` hizmetin yönteminde aşağıdaki kodda gösterildiği gibi ve ekleyerek bunu etkinleştirin:</span><span class="sxs-lookup"><span data-stu-id="09ceb-132">Once ASP.NET Core Identity is configured, you enable it by adding the `app.UseAuthentication()` and `endpoints.MapRazorPages()` as shown in the following code in the service's `Startup.Configure` method:</span></span>

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
> <span data-ttu-id="09ceb-133">Önseki kodundaki satırlar, Kimliğin doğru çalışması için **GÖSTERİlEN SİPARİşTE OLMALIDIR.**</span><span class="sxs-lookup"><span data-stu-id="09ceb-133">The lines in the preceeding code **MUST BE IN THE ORDER SHOWN** for Identity to work correctly.</span></span>

<span data-ttu-id="09ceb-134">ASP.NET Çekirdek Kimlik kullanmak birkaç senaryoya olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="09ceb-134">Using ASP.NET Core Identity enables several scenarios:</span></span>

- <span data-ttu-id="09ceb-135">UserManager türünü (userManager.CreateAsync) kullanarak yeni kullanıcı bilgileri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="09ceb-135">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

- <span data-ttu-id="09ceb-136">SignInManager türünü kullanarak kullanıcıların kimliğini doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="09ceb-136">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="09ceb-137">Doğrudan oturum `signInManager.SignInAsync` açmayı veya `signInManager.PasswordSignInAsync` kullanıcının parolasının doğru olduğunu doğrulamak ve oturum açmanızı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09ceb-137">You can use `signInManager.SignInAsync` to sign in directly, or `signInManager.PasswordSignInAsync` to confirm the user’s password is correct and then sign them in.</span></span>

- <span data-ttu-id="09ceb-138">Bir tarayıcıdan sonraki isteklerin oturum açmış bir kullanıcının kimliğini ve taleplerini içerecek şekilde çerezde depolanan bilgilere (ASP.NET Çekirdek Kimlik aracı tarafından okunan) dayalı olarak bir kullanıcıyı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="09ceb-138">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="09ceb-139">ASP.NET Çekirdek Kimlik de [iki faktörlü kimlik doğrulaması](/aspnet/core/security/authentication/2fa)destekler.</span><span class="sxs-lookup"><span data-stu-id="09ceb-139">ASP.NET Core Identity also supports [two-factor authentication](/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="09ceb-140">Yerel bir kullanıcı veri deposundan yararlanan ve tanımlama bilgilerini kullanan istekler arasında kimlik kalıcı olan kimlik doğrulama senaryoları için (MVC web uygulamalarında olduğu gibi), ASP.NET Çekirdek Kimlik önerilen bir çözümdür.</span><span class="sxs-lookup"><span data-stu-id="09ceb-140">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

### <a name="authenticate-with-external-providers"></a><span data-ttu-id="09ceb-141">Harici sağlayıcılarla kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="09ceb-141">Authenticate with external providers</span></span>

<span data-ttu-id="09ceb-142">ASP.NET Core, kullanıcıların [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) akışları aracılığıyla oturum açmalarına izin vermek için [harici kimlik doğrulama sağlayıcılarının](/aspnet/core/security/authentication/social/) kullanılmasını da destekler.</span><span class="sxs-lookup"><span data-stu-id="09ceb-142">ASP.NET Core also supports using [external authentication providers](/aspnet/core/security/authentication/social/) to let users sign in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="09ceb-143">Bu, kullanıcıların Microsoft, Google, Facebook veya Twitter gibi sağlayıcılardan gelen mevcut kimlik doğrulama işlemlerini kullanarak oturum açabileceği ve bu kimlikleri uygulamanızda ASP.NET Bir Çekirdek kimliğiyle ilişkilendirebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-143">This means that users can sign in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="09ceb-144">Daha önce de belirtildiği gibi kimlik doğrulama ara ware dahil olmak `app.UseAuthentication()` üzere, dış kimlik doğrulaması `Startup` kullanmak için, yöntemi kullanarak, ayrıca aşağıdaki örnekte gösterildiği gibi dış sağlayıcı kayıt gerekir:</span><span class="sxs-lookup"><span data-stu-id="09ceb-144">To use external authentication, besides including the authentication middleware as mentioned before, using the `app.UseAuthentication()` method, you also have to register the external provider in `Startup` as shown in the following example:</span></span>

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

<span data-ttu-id="09ceb-145">Popüler dış kimlik doğrulama sağlayıcıları ve bunların ilişkili NuGet paketleri aşağıdaki tabloda gösterilir:</span><span class="sxs-lookup"><span data-stu-id="09ceb-145">Popular external authentication providers and their associated NuGet packages are shown in the following table:</span></span>

| <span data-ttu-id="09ceb-146">**Sağlayıcı**</span><span class="sxs-lookup"><span data-stu-id="09ceb-146">**Provider**</span></span>  | <span data-ttu-id="09ceb-147">**Paket**</span><span class="sxs-lookup"><span data-stu-id="09ceb-147">**Package**</span></span>                                          |
| ------------- | ---------------------------------------------------- |
| <span data-ttu-id="09ceb-148">**Microsoft**</span><span class="sxs-lookup"><span data-stu-id="09ceb-148">**Microsoft**</span></span> | <span data-ttu-id="09ceb-149">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span><span class="sxs-lookup"><span data-stu-id="09ceb-149">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span></span> |
| <span data-ttu-id="09ceb-150">**Google**</span><span class="sxs-lookup"><span data-stu-id="09ceb-150">**Google**</span></span>    | <span data-ttu-id="09ceb-151">**Microsoft.AspNetCore.Authentication.Google**</span><span class="sxs-lookup"><span data-stu-id="09ceb-151">**Microsoft.AspNetCore.Authentication.Google**</span></span>           |
| <span data-ttu-id="09ceb-152">**Facebook**</span><span class="sxs-lookup"><span data-stu-id="09ceb-152">**Facebook**</span></span>  | <span data-ttu-id="09ceb-153">**Microsoft.AspNetCore.Authentication.Facebook**</span><span class="sxs-lookup"><span data-stu-id="09ceb-153">**Microsoft.AspNetCore.Authentication.Facebook**</span></span>         |
| <span data-ttu-id="09ceb-154">**Twitter**</span><span class="sxs-lookup"><span data-stu-id="09ceb-154">**Twitter**</span></span>   | <span data-ttu-id="09ceb-155">**Microsoft.AspNetCore.Authentication.Twitter**</span><span class="sxs-lookup"><span data-stu-id="09ceb-155">**Microsoft.AspNetCore.Authentication.Twitter**</span></span>          |

<span data-ttu-id="09ceb-156">Her durumda, satıcıya bağımlı olan ve genellikle şunları içeren bir uygulama kayıt yordamı tamamlamanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="09ceb-156">In all cases, you must complete an application registration procedure that is vendor dependent and that usually involves:</span></span>

1. <span data-ttu-id="09ceb-157">İstemci Başvuru Kimliği alma.</span><span class="sxs-lookup"><span data-stu-id="09ceb-157">Getting a Client Application ID.</span></span>
2. <span data-ttu-id="09ceb-158">İstemci Uygulama Sırrı Alma.</span><span class="sxs-lookup"><span data-stu-id="09ceb-158">Getting a Client Application Secret.</span></span>
3. <span data-ttu-id="09ceb-159">Yetkilendirme ara yazılımı ve kayıtlı sağlayıcı tarafından işlenen bir yeniden yönlendirme URL'sini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="09ceb-159">Configuring an redirection URL, that's handled by the authorization middleware and the registered provider</span></span>
4. <span data-ttu-id="09ceb-160">İsteğe bağlı olarak, oturum dışı bir URL'yi, Tek Oturum Açma (SSO) senaryosunda oturum açma işlemlerini düzgün bir şekilde işlemek için yapılandırmak.</span><span class="sxs-lookup"><span data-stu-id="09ceb-160">Optionally, configuring a sign-out URL to properly handle sign out in a Single Sign On (SSO) scenario.</span></span>

<span data-ttu-id="09ceb-161">Uygulamanızı harici bir sağlayıcı için yapılandırma hakkında ayrıntılı bilgi [için, ASP.NET Çekirdek belgelerinde Dış sağlayıcı kimlik doğrulaması'na](/aspnet/core/security/authentication/social/)bakın).</span><span class="sxs-lookup"><span data-stu-id="09ceb-161">For details on configuring your app for an external provider, see the [External provider authentication in the ASP.NET Core documentation](/aspnet/core/security/authentication/social/)).</span></span>

>[!TIP]
><span data-ttu-id="09ceb-162">Tüm ayrıntılar, daha önce bahsedilen yetkilendirme aracıları ve hizmetleri tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-162">All details are handled by the authorization middleware and services previously mentioned.</span></span> <span data-ttu-id="09ceb-163">Bu nedenle, Visual Studio'da, şekil 9-3'te gösterildiği gibi, daha önce bahsedilen kimlik doğrulama sağlayıcılarını kaydetmenin yanı sıra, ASP.NET Kodu web uygulama projesini oluştururken **Bireysel Kullanıcı Hesabı** kimlik doğrulama seçeneğini seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-163">So, you just have to choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, as shown in Figure 9-3, besides registering the authentication providers previously mentioned.</span></span>

![Yeni ASP.NET Çekirdek Web Uygulaması iletişim kutusunun ekran görüntüsü.](./media/index/select-individual-user-account-authentication-option.png)

<span data-ttu-id="09ceb-165">**Şekil 9-3**.</span><span class="sxs-lookup"><span data-stu-id="09ceb-165">**Figure 9-3**.</span></span> <span data-ttu-id="09ceb-166">Visual Studio 2019'da bir web uygulama projesi oluştururken harici kimlik doğrulaması kullanmak için Bireysel Kullanıcı Hesapları seçeneğini seçme.</span><span class="sxs-lookup"><span data-stu-id="09ceb-166">Selecting the Individual User Accounts option, for using external authentication, when creating a web application project in Visual Studio 2019.</span></span>

<span data-ttu-id="09ceb-167">Daha önce listelenen dış kimlik doğrulama sağlayıcılarına ek olarak, daha birçok dış kimlik doğrulama sağlayıcısı kullanmak için ara yazılım sağlayan üçüncü taraf paketleri de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="09ceb-167">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="09ceb-168">Bir liste için GitHub'daki [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) deposuna bakın.</span><span class="sxs-lookup"><span data-stu-id="09ceb-168">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repository on GitHub.</span></span>

<span data-ttu-id="09ceb-169">Ayrıca bazı özel ihtiyacı çözmek için kendi dış kimlik doğrulama aracı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09ceb-169">You can also create your own external authentication middleware to solve some special need.</span></span>

### <a name="authenticate-with-bearer-tokens"></a><span data-ttu-id="09ceb-170">Taşıyıcı belirteçleriyle kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="09ceb-170">Authenticate with bearer tokens</span></span>

<span data-ttu-id="09ceb-171">Temel Kimlik (veya Kimlik artı harici kimlik doğrulama sağlayıcıları) ASP.NET ile kimlik doğrulama, kullanıcı bilgilerini bir çerezde depolamanın uygun olduğu birçok web uygulama senaryosunda iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="09ceb-171">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="09ceb-172">Ancak diğer senaryolarda, tanımlama bilgileri kalıcı veri ve iletim doğal bir araç değildir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-172">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="09ceb-173">Örneğin, Tek Sayfa Uygulamaları (SPA'lar), yerel istemciler ve hatta diğer Web API'leri tarafından erişilebilen yeniden kullanılabilir uç noktaları ortaya çıkaran ASP.NET Core Web API'sinde, genellikle taşıyıcı belirteç kimlik doğrulaması kullanmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="09ceb-173">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="09ceb-174">Bu tür uygulamalar tanımlama bilgileriyle çalışmaz, ancak taşıyıcı belirteci kolayca alabilir ve sonraki isteklerin yetkilendirme üstbilgisine ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-174">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="09ceb-175">Belirteç kimlik doğrulamasını etkinleştirmek için, ASP.NET Core [OAuth 2.0](https://oauth.net/2/) ve [OpenID Connect'i](https://openid.net/connect/)kullanmak için çeşitli seçenekleri destekler.</span><span class="sxs-lookup"><span data-stu-id="09ceb-175">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="09ceb-176">OpenID Connect veya OAuth 2.0 Kimlik sağlayıcısıyla kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="09ceb-176">Authenticate with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="09ceb-177">Kullanıcı bilgileri Azure Active Directory'de veya OpenID Connect veya OAuth 2.0'ı destekleyen başka bir kimlik çözümünde depolanıyorsa, OpenID Connect iş akışını kullanarak kimlik doğrulaması yapmak için **Microsoft.AspNetCore.Authentication.OpenIdConnect** paketini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09ceb-177">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the **Microsoft.AspNetCore.Authentication.OpenIdConnect** package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="09ceb-178">Örneğin, eShopOnContainers Identity.Api microservice doğrulaması için, bir ASP.NET Core web uygulaması aşağıdaki basitleştirilmiş örnekte gösterildiği `Startup.cs`gibi bu paketten ara ware kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="09ceb-178">For example, to authenticate to the Identity.Api microservice in eShopOnContainers, an ASP.NET Core web application can use middleware from that package as shown in the following simplified example in `Startup.cs`:</span></span>

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

<span data-ttu-id="09ceb-179">Tüm kullanıcı bilgileri depolama ve kimlik doğrulama Kimlik hizmeti tarafından işlenir, çünkü bu iş akışını kullandığınızda, ASP.NET Çekirdek Kimlik aracı gerekli olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="09ceb-179">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by the Identity service.</span></span>

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="09ceb-180">ASP.NET Core hizmetinden güvenlik belirteçleri verme</span><span class="sxs-lookup"><span data-stu-id="09ceb-180">Issue security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="09ceb-181">Harici kimlik sağlayıcısı kullanmak yerine yerel ASP.NET Çekirdek Kimlik kullanıcıları için güvenlik belirteçleri vermeyi tercih ederseniz, bazı iyi üçüncü taraf kitaplıklarından yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09ceb-181">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="09ceb-182">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) ve [OpenIddict,](https://github.com/openiddict/openiddict-core) ASP.NET Core hizmetinden güvenlik belirteçleri çıkarmanıza izin vermek için ASP.NET Çekirdek Kimlikle kolayca entegre olan OpenID Connect sağlayıcılarıdır.</span><span class="sxs-lookup"><span data-stu-id="09ceb-182">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="09ceb-183">[IdentityServer4 belgeleri,](https://identityserver4.readthedocs.io/en/latest/) kitaplığı kullanmak için ayrıntılı talimatlara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-183">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/latest/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="09ceb-184">Ancak, belirteçleri vermek için IdentityServer4 kullanarak temel adımları aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-184">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1. <span data-ttu-id="09ceb-185">Uygulamayı ararsın. IdentityServer'ı, uygulamanın HTTP istek işleme ardışık hattına IdentityServer4 eklemek için Başlangıç.Configure yönteminde kullanın.</span><span class="sxs-lookup"><span data-stu-id="09ceb-185">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="09ceb-186">Bu, kitaplığın OpenID Connect ve /connect/token gibi OAuth2 uç noktalarına istekler sunmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="09ceb-186">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2. <span data-ttu-id="09ceb-187">IdentityServer4'i Startup.ConfigureServices'de, hizmetlere çağrı yaparak yapılandırAbilirsiniz. AddIdentityServer.</span><span class="sxs-lookup"><span data-stu-id="09ceb-187">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3. <span data-ttu-id="09ceb-188">Aşağıdaki verileri ayarlayarak kimlik sunucusunu yapılandırAbilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="09ceb-188">You configure identity server by setting the following data:</span></span>

   - <span data-ttu-id="09ceb-189">İmzalamak için kullanılacak [kimlik bilgileri.](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html)</span><span class="sxs-lookup"><span data-stu-id="09ceb-189">The [credentials](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) to use for signing.</span></span>

   - <span data-ttu-id="09ceb-190">Kullanıcıların erişmek isteyebileceği [Kimlik ve API kaynakları:](https://identityserver4.readthedocs.io/en/latest/topics/resources.html)</span><span class="sxs-lookup"><span data-stu-id="09ceb-190">The [Identity and API resources](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) that users might request access to:</span></span>

      - <span data-ttu-id="09ceb-191">API kaynakları, kullanıcının bir erişim belirteciyle erişebileceği korumalı verileri veya işlevselliği temsil ediyor.</span><span class="sxs-lookup"><span data-stu-id="09ceb-191">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="09ceb-192">API kaynağına örnek olarak, yetkilendirme gerektiren bir web API 'si (veya API kümesi) olur.</span><span class="sxs-lookup"><span data-stu-id="09ceb-192">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

      - <span data-ttu-id="09ceb-193">Kimlik kaynakları, bir kullanıcıyı tanımlamak için istemciye verilen bilgileri (talepleri) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="09ceb-193">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="09ceb-194">Talepler, kullanıcı adını, e-posta adresini ve benzeri bilgileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-194">The claims might include the user name, email address, and so on.</span></span>

   - <span data-ttu-id="09ceb-195">Jeton istemek için bağlanacak [istemciler.](https://identityserver4.readthedocs.io/en/latest/topics/clients.html)</span><span class="sxs-lookup"><span data-stu-id="09ceb-195">The [clients](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) that will be connecting in order to request tokens.</span></span>

   - <span data-ttu-id="09ceb-196">[ASP.NET Çekirdek Kimlik](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) veya bir alternatif gibi kullanıcı bilgileri için depolama mekanizması.</span><span class="sxs-lookup"><span data-stu-id="09ceb-196">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) or an alternative.</span></span>

<span data-ttu-id="09ceb-197">IdentityServer4'ün kullanması için istemciler ve kaynaklar <xref:System.Collections.Generic.IEnumerable%601> belirttiğiniz zaman, uygun türde bir koleksiyonu bellek istemcisi veya kaynak depolarını alan yöntemlere geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09ceb-197">When you specify clients and resources for IdentityServer4 to use, you can pass an <xref:System.Collections.Generic.IEnumerable%601> collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="09ceb-198">Veya daha karmaşık senaryolar için, Bağımlılık Enjeksiyonu aracılığıyla istemci veya kaynak sağlayıcı türleri sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09ceb-198">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="09ceb-199">IdentityServer4'in bellek içi kaynakları ve özel bir IClientStore türü tarafından sağlanan istemcileri kullanması için örnek bir yapılandırma aşağıdaki örnek gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="09ceb-199">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

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

### <a name="consume-security-tokens"></a><span data-ttu-id="09ceb-200">Güvenlik belirteçlerini tüketin</span><span class="sxs-lookup"><span data-stu-id="09ceb-200">Consume security tokens</span></span>

<span data-ttu-id="09ceb-201">OpenID Connect bitiş noktasına karşı kimlik doğrulaması veya kendi güvenlik belirteçlerinizi verme bazı senaryoları kapsar.</span><span class="sxs-lookup"><span data-stu-id="09ceb-201">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="09ceb-202">Ancak, farklı bir hizmet tarafından sağlanan geçerli güvenlik belirteçleri olan kullanıcılara erişimi sınırlaması gereken bir hizmete ne deilmelidir?</span><span class="sxs-lookup"><span data-stu-id="09ceb-202">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="09ceb-203">Bu senaryo için, JWT belirteçlerini işleyen kimlik doğrulama aracı **Microsoft.AspNetCore.Authentication.JwtBearer** paketinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-203">For that scenario, authentication middleware that handles JWT tokens is available in the **Microsoft.AspNetCore.Authentication.JwtBearer** package.</span></span> <span data-ttu-id="09ceb-204">JWT , "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" anlamına gelir ve güvenlik taleplerini iletmek için ortak bir güvenlik belirteci biçimidir (RFC 7519 tarafından tanımlanır).</span><span class="sxs-lookup"><span data-stu-id="09ceb-204">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="09ceb-205">Bu tür belirteçleri tüketmek için ara ware nasıl kullanılacağı basitleştirilmiş bir örnek bu kod parçası gibi görünebilir, eShopOnContainers Ordering.Api microservice alınan.</span><span class="sxs-lookup"><span data-stu-id="09ceb-205">A simplified example of how to use middleware to consume such tokens might look like this code fragment, taken from the Ordering.Api microservice of eShopOnContainers.</span></span>

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

<span data-ttu-id="09ceb-206">Bu kullanımdaki parametreler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="09ceb-206">The parameters in this usage are:</span></span>

- <span data-ttu-id="09ceb-207">`Audience`gelen belirteci veya belirteç erişim verdiği kaynak alıcısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="09ceb-207">`Audience` represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="09ceb-208">Bu parametrede belirtilen değer belirteçteki parametreyle eşleşmiyorsa, belirteç reddedilir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-208">If the value specified in this parameter does not match the parameter in the token, the token will be rejected.</span></span>

- <span data-ttu-id="09ceb-209">`Authority`belirteç veren kimlik doğrulama sunucusunun adresidir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-209">`Authority` is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="09ceb-210">JWT taşıyıcı kimlik doğrulaması aracı, belirteç imzasını doğrulamak için kullanılabilecek ortak anahtarı almak için bu URI'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="09ceb-210">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="09ceb-211">Ara yazılım, belirteçteki `iss` parametrenin bu URI ile eşleştiğini de doğrular.</span><span class="sxs-lookup"><span data-stu-id="09ceb-211">The middleware also confirms that the `iss` parameter in the token matches this URI.</span></span>

<span data-ttu-id="09ceb-212">Başka bir `RequireHttpsMetadata`parametre, , test amaçlı yararlıdır; sertifikaların olmadığı ortamlarda test edilebilmeniz için bu parametreyi yanlış olarak ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="09ceb-212">Another parameter, `RequireHttpsMetadata`, is useful for testing purposes; you set this parameter to false so you can test in environments where you don't have certificates.</span></span> <span data-ttu-id="09ceb-213">Gerçek dünyadaki dağıtımlarda, JWT taşıyıcı belirteçleri her zaman yalnızca HTTPS üzerinden geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-213">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="09ceb-214">Bu ara yazılım yerinde, JWT belirteçleri otomatik olarak yetkilendirme üstbilgisinden ayıklanır.</span><span class="sxs-lookup"><span data-stu-id="09ceb-214">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="09ceb-215">Daha sonra deserialized, doğrulanır (ve `Audience` `Authority` parametrelerdeki değerleri kullanarak) ve daha sonra MVC eylemleri veya yetkilendirme filtreleri tarafından başvurulacak kullanıcı bilgileri olarak saklanır.</span><span class="sxs-lookup"><span data-stu-id="09ceb-215">They are then deserialized, validated (using the values in the `Audience` and `Authority` parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="09ceb-216">JWT taşıyıcı kimlik doğrulama aracı, yetki yoksa belirteci doğrulamak için yerel bir sertifika kullanmak gibi daha gelişmiş senaryoları da destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="09ceb-216">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="09ceb-217">Bu senaryo `TokenValidationParameters` `JwtBearerOptions` için, nesnebir nesne belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09ceb-217">For this scenario, you can specify a `TokenValidationParameters` object in the `JwtBearerOptions` object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="09ceb-218">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="09ceb-218">Additional resources</span></span>

- <span data-ttu-id="09ceb-219">**Çerezleri uygulamalar arasında paylaşma** </span><span class="sxs-lookup"><span data-stu-id="09ceb-219">**Sharing cookies between applications** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- <span data-ttu-id="09ceb-220">**Kimliğe Giriş** </span><span class="sxs-lookup"><span data-stu-id="09ceb-220">**Introduction to Identity** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="09ceb-221">**Rick Anderson' ı. SMS ile iki faktörlü kimlik doğrulama** </span><span class="sxs-lookup"><span data-stu-id="09ceb-221">**Rick Anderson. Two-factor authentication with SMS** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- <span data-ttu-id="09ceb-222">**Facebook, Google ve diğer harici sağlayıcıları kullanarak kimlik doğrulamayı etkinleştirme** </span><span class="sxs-lookup"><span data-stu-id="09ceb-222">**Enabling authentication using Facebook, Google and other external providers** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- <span data-ttu-id="09ceb-223">**Michell Anicas. OAuth 2'ye Giriş** </span><span class="sxs-lookup"><span data-stu-id="09ceb-223">**Michell Anicas. An Introduction to OAuth 2** </span></span>\
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- <span data-ttu-id="09ceb-224">**AspNet.Security.OAuth.Providers** (ASP.NET OAuth sağlayıcıları için GitHub repo) </span><span class="sxs-lookup"><span data-stu-id="09ceb-224">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers) </span></span>\
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- <span data-ttu-id="09ceb-225">**IdentityServer4. Resmi belgeler** </span><span class="sxs-lookup"><span data-stu-id="09ceb-225">**IdentityServer4. Official documentation** </span></span>\
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
><span data-ttu-id="09ceb-226">[Önceki](../implement-resilient-applications/monitor-app-health.md)
>[Sonraki](authorization-net-microservices-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="09ceb-226">[Previous](../implement-resilient-applications/monitor-app-health.md)
[Next](authorization-net-microservices-web-applications.md)</span></span>
