---
title: .NET mikro hizmetleri ve Web uygulamalarının güvenliğini sağlama
description: .NET mikro hizmetleri ve Web uygulamalarında güvenlik-ASP.NET Core Web uygulamalarında kimlik doğrulama seçeneklerini öğrenin.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: f82212956f5492a51ec99d092e1a5131d1b31313
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77501642"
---
# <a name="make-secure-net-microservices-and-web-applications"></a><span data-ttu-id="67645-103">Güvenli .NET mikro hizmetleri ve Web uygulamaları oluşturun</span><span class="sxs-lookup"><span data-stu-id="67645-103">Make secure .NET Microservices and Web Applications</span></span>

<span data-ttu-id="67645-104">Mikro hizmetlerde ve Web uygulamalarında güvenlikle ilgili olarak konunun bu şekilde birçok kitap alabilmesini sağlayacak pek çok konu vardır. Bu bölümde, kimlik doğrulama, yetkilendirme ve uygulama gizliliklerine odaklanacağız.</span><span class="sxs-lookup"><span data-stu-id="67645-104">There are so many aspects about security in microservices and web applications that the topic could easy take several books like this one so, in this section, we'll focus on authentication, authorization, and application secrets.</span></span>

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a><span data-ttu-id="67645-105">.NET mikro hizmetleri ve Web uygulamalarında kimlik doğrulaması uygulama</span><span class="sxs-lookup"><span data-stu-id="67645-105">Implement authentication in .NET microservices and web applications</span></span>

<span data-ttu-id="67645-106">Genellikle bir hizmet tarafından yayımlanan kaynakların ve API 'Lerin belirli Güvenilen Kullanıcı veya istemcilerle sınırlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="67645-106">It's often necessary for resources and APIs published by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="67645-107">Bu tür API düzeyi güven kararlarını yapmanın ilk adımı kimlik doğrulamadır.</span><span class="sxs-lookup"><span data-stu-id="67645-107">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="67645-108">Kimlik doğrulaması, bir kullanıcının kimliğini güvenilir bir şekilde doğrulama işlemidir.</span><span class="sxs-lookup"><span data-stu-id="67645-108">Authentication is the process of reliably verify a user’s identity.</span></span>

<span data-ttu-id="67645-109">Mikro hizmet senaryolarında, kimlik doğrulaması genellikle merkezi olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="67645-109">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="67645-110">Bir API ağ geçidi kullanıyorsanız, Şekil 9-1 ' de gösterildiği gibi ağ geçidi kimlik doğrulaması için iyi bir yerdir.</span><span class="sxs-lookup"><span data-stu-id="67645-110">If you're using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 9-1.</span></span> <span data-ttu-id="67645-111">Bu yaklaşımı kullanırsanız, ağ geçidinden gelen veya olmayan iletilerin kimlik doğrulamasını yapmak için ek bir güvenlik yoksa, tek tek mikro hizmetlere doğrudan ulaşılamadığından emin olun (API ağ geçidi olmadan).</span><span class="sxs-lookup"><span data-stu-id="67645-111">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![İstemci mobil uygulamasının arka uca nasıl etkileşime gireceğini gösteren diyagram.](./media/index/api-gateway-centralized-authentication.png)

<span data-ttu-id="67645-113">**Şekil 9-1**.</span><span class="sxs-lookup"><span data-stu-id="67645-113">**Figure 9-1**.</span></span> <span data-ttu-id="67645-114">API ağ geçidiyle merkezi kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="67645-114">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="67645-115">API Gateway kimlik doğrulamasını merkezileştiren, istekleri mikro hizmetlere iletirken Kullanıcı bilgilerini ekler.</span><span class="sxs-lookup"><span data-stu-id="67645-115">When the API Gateway centralizes authentication, it adds user information when forwarding requests to the microservices.</span></span> <span data-ttu-id="67645-116">Hizmetlere doğrudan erişilemiyorsa, kullanıcıların kimliğini doğrulamak için Azure Active Directory gibi bir kimlik doğrulama hizmeti veya güvenlik belirteci hizmeti (STS) görevi gören ayrılmış bir kimlik doğrulama mikro hizmeti kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="67645-116">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="67645-117">Güven kararları, güvenlik belirteçleri veya tanımlama bilgileriyle hizmetler arasında paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="67645-117">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="67645-118">(Bu belirteçler, gerekirse [tanımlama bilgisi paylaşımı](/aspnet/core/security/cookie-sharing)uygulayarak ASP.NET Core uygulamalar arasında paylaşılabilir.) Bu model Şekil 9-2 ' de gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="67645-118">(These tokens can be shared between ASP.NET Core applications, if needed, by implementing [cookie sharing](/aspnet/core/security/cookie-sharing).) This pattern is illustrated in Figure 9-2.</span></span>

![Arka uç mikro hizmetleri aracılığıyla kimlik doğrulaması gösteren diyagram.](./media/index/identity-microservice-authentication.png)

<span data-ttu-id="67645-120">**Şekil 9-2**.</span><span class="sxs-lookup"><span data-stu-id="67645-120">**Figure 9-2**.</span></span> <span data-ttu-id="67645-121">Kimlik mikro hizmetine göre kimlik doğrulaması; güven, bir yetkilendirme belirteci kullanılarak paylaşılır</span><span class="sxs-lookup"><span data-stu-id="67645-121">Authentication by identity microservice; trust is shared using an authorization token</span></span>

<span data-ttu-id="67645-122">Mikro hizmetlere doğrudan erişildiğinde, kimlik doğrulaması ve yetkilendirme içeren güven, mikro hizmetler arasında paylaşılan, adanmış bir mikro hizmet tarafından verilen bir güvenlik belirteci tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="67645-122">When microservices are accessed directly, trust, that includes authentication and authorization, is handled by a security token issued by a dedicated microservice, shared between microservices.</span></span>

### <a name="authenticate-with-aspnet-core-identity"></a><span data-ttu-id="67645-123">ASP.NET Core kimliğiyle kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="67645-123">Authenticate with ASP.NET Core Identity</span></span>

<span data-ttu-id="67645-124">Bir uygulamanın kullanıcılarını tanımlamak için ASP.NET Core birincil mekanizması [ASP.NET Core kimlik](/aspnet/core/security/authentication/identity) üyelik sistemidir.</span><span class="sxs-lookup"><span data-stu-id="67645-124">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="67645-125">ASP.NET Core kimlik, geliştirici tarafından yapılandırılan bir veri deposundaki kullanıcı bilgilerini (oturum açma bilgileri, roller ve talepler dahil) depolar.</span><span class="sxs-lookup"><span data-stu-id="67645-125">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="67645-126">Genellikle, ASP.NET Core Identity veri deposu `Microsoft.AspNetCore.Identity.EntityFrameworkCore` paketinde sunulan bir Entity Framework deposudur.</span><span class="sxs-lookup"><span data-stu-id="67645-126">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` package.</span></span> <span data-ttu-id="67645-127">Ancak, Azure Tablo depolama, CosmosDB veya diğer konumlarda kimlik bilgilerini depolamak için özel mağazalar veya diğer üçüncü taraf paketleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="67645-127">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, CosmosDB, or other locations.</span></span>

> [!TIP]
> <span data-ttu-id="67645-128">ASP.NET Core 2,1 ve üzeri, [Razor sınıf kitaplığı](/aspnet/core/razor-pages/ui-class)olarak [ASP.NET Core kimlik](/aspnet/core/security/authentication/identity) sağlar; bu nedenle, önceki sürümlerde olduğu gibi projenizde gerekli kodların çoğunu görmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="67645-128">ASP.NET Core 2.1 and later provides [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) as a [Razor Class Library](/aspnet/core/razor-pages/ui-class), so you won't see much of the necessary code in your project, as was the case for previous versions.</span></span> <span data-ttu-id="67645-129">Kimlik kodunu gereksinimlerinize uyacak şekilde özelleştirmeye ilişkin ayrıntılar için bkz. [ASP.NET Core projelerinde Scaffold Identity](/aspnet/core/security/authentication/scaffold-identity).</span><span class="sxs-lookup"><span data-stu-id="67645-129">For details on how to customize the Identity code to suit your needs, see [Scaffold Identity in ASP.NET Core projects](/aspnet/core/security/authentication/scaffold-identity).</span></span>

<span data-ttu-id="67645-130">Aşağıdaki kod, bireysel kullanıcı hesabı kimlik doğrulaması seçili olan ASP.NET Core Web uygulaması MVC 3,1 proje şablonundan alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="67645-130">The following code is taken from the ASP.NET Core Web Application MVC 3.1 project template with individual user account authentication selected.</span></span> <span data-ttu-id="67645-131">`Startup.ConfigureServices` yönteminde Entity Framework Core kullanılarak ASP.NET Core kimliğin nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="67645-131">It shows how to configure ASP.NET Core Identity using Entity Framework Core in the `Startup.ConfigureServices` method.</span></span>

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

<span data-ttu-id="67645-132">ASP.NET Core kimlik yapılandırıldıktan sonra, hizmetin `Startup.Configure` yönteminde aşağıdaki kodda gösterildiği gibi `app.UseAuthentication()` ve `endpoints.MapRazorPages()` ekleyerek etkinleştirin:</span><span class="sxs-lookup"><span data-stu-id="67645-132">Once ASP.NET Core Identity is configured, you enable it by adding the `app.UseAuthentication()` and `endpoints.MapRazorPages()` as shown in the following code in the service's `Startup.Configure` method:</span></span>

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
> <span data-ttu-id="67645-133">Önceki koddaki satırlar kimliğin düzgün çalışması için **GÖSTERILEN sırada** olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="67645-133">The lines in the preceeding code **MUST BE IN THE ORDER SHOWN** for Identity to work correctly.</span></span>

<span data-ttu-id="67645-134">ASP.NET Core kimlik kullanmak çeşitli senaryolara izin vermez:</span><span class="sxs-lookup"><span data-stu-id="67645-134">Using ASP.NET Core Identity enables several scenarios:</span></span>

- <span data-ttu-id="67645-135">UserManager türünü (userManager. CreateAsync) kullanarak yeni kullanıcı bilgileri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="67645-135">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

- <span data-ttu-id="67645-136">SignInManager türünü kullanarak kullanıcıların kimliğini doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="67645-136">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="67645-137">Doğrudan oturum açmak için `signInManager.SignInAsync` kullanabilir veya kullanıcının parolasının doğru olduğunu doğrulamak için `signInManager.PasswordSignInAsync` ve sonra da oturum açın.</span><span class="sxs-lookup"><span data-stu-id="67645-137">You can use `signInManager.SignInAsync` to sign in directly, or `signInManager.PasswordSignInAsync` to confirm the user’s password is correct and then sign them in.</span></span>

- <span data-ttu-id="67645-138">Bir tarayıcıdan gelen isteklerin, oturum açan kullanıcının kimlik ve taleplerini içermesi için bir tanımlama bilgisinde depolanan (ASP.NET Core Identity ara yazılımı tarafından okunan) bilgileri temel alan bir kullanıcıyı tanımlama.</span><span class="sxs-lookup"><span data-stu-id="67645-138">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="67645-139">ASP.NET Core kimlik [iki öğeli kimlik doğrulamasını](/aspnet/core/security/authentication/2fa)da destekler.</span><span class="sxs-lookup"><span data-stu-id="67645-139">ASP.NET Core Identity also supports [two-factor authentication](/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="67645-140">Yerel bir kullanıcı veri deposunu kullanan ve tanımlama bilgilerini kullanarak istekler arasında kimlik (MVC web uygulamaları için tipik olarak) tutan kimlik doğrulama senaryolarında, ASP.NET Core kimlik önerilen bir çözümdür.</span><span class="sxs-lookup"><span data-stu-id="67645-140">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

### <a name="authenticate-with-external-providers"></a><span data-ttu-id="67645-141">Dış sağlayıcılarla kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="67645-141">Authenticate with external providers</span></span>

<span data-ttu-id="67645-142">ASP.NET Core Ayrıca, kullanıcıların [OAuth 2,0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) akışları aracılığıyla oturum açmasını sağlamak için [dış kimlik doğrulama sağlayıcılarının](/aspnet/core/security/authentication/social/) kullanılmasını da destekler.</span><span class="sxs-lookup"><span data-stu-id="67645-142">ASP.NET Core also supports using [external authentication providers](/aspnet/core/security/authentication/social/) to let users sign in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="67645-143">Bu, kullanıcıların Microsoft, Google, Facebook veya Twitter gibi sağlayıcılardan mevcut kimlik doğrulama süreçlerini kullanarak oturum açabileceği ve bu kimlikleri uygulamanızdaki bir ASP.NET Core kimlikle ilişkilendirebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="67645-143">This means that users can sign in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="67645-144">Daha önce belirtildiği gibi kimlik doğrulama ara yazılımı dahil olmak üzere dış kimlik doğrulamasını kullanmak için, `app.UseAuthentication()` yöntemi kullanılarak dış sağlayıcıyı aşağıdaki örnekte gösterildiği gibi `Startup` kaydetmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="67645-144">To use external authentication, besides including the authentication middleware as mentioned before, using the `app.UseAuthentication()` method, you also have to register the external provider in `Startup` as shown in the following example:</span></span>

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

<span data-ttu-id="67645-145">Popüler dış kimlik doğrulama sağlayıcıları ve bunlarla ilişkili NuGet paketleri aşağıdaki tabloda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="67645-145">Popular external authentication providers and their associated NuGet packages are shown in the following table:</span></span>

| <span data-ttu-id="67645-146">**Sağlayıcı**</span><span class="sxs-lookup"><span data-stu-id="67645-146">**Provider**</span></span>  | <span data-ttu-id="67645-147">**Paket**</span><span class="sxs-lookup"><span data-stu-id="67645-147">**Package**</span></span>                                          |
| ------------- | ---------------------------------------------------- |
| <span data-ttu-id="67645-148">**MICROSOFT**</span><span class="sxs-lookup"><span data-stu-id="67645-148">**Microsoft**</span></span> | <span data-ttu-id="67645-149">**Microsoft. AspNetCore. Authentication. MicrosoftAccount**</span><span class="sxs-lookup"><span data-stu-id="67645-149">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span></span> |
| <span data-ttu-id="67645-150">**Google**</span><span class="sxs-lookup"><span data-stu-id="67645-150">**Google**</span></span>    | <span data-ttu-id="67645-151">**Microsoft. AspNetCore. Authentication. Google**</span><span class="sxs-lookup"><span data-stu-id="67645-151">**Microsoft.AspNetCore.Authentication.Google**</span></span>           |
| <span data-ttu-id="67645-152">**Facebook**</span><span class="sxs-lookup"><span data-stu-id="67645-152">**Facebook**</span></span>  | <span data-ttu-id="67645-153">**Microsoft. AspNetCore. Authentication. Facebook**</span><span class="sxs-lookup"><span data-stu-id="67645-153">**Microsoft.AspNetCore.Authentication.Facebook**</span></span>         |
| <span data-ttu-id="67645-154">**Twitter**</span><span class="sxs-lookup"><span data-stu-id="67645-154">**Twitter**</span></span>   | <span data-ttu-id="67645-155">**Microsoft. AspNetCore. Authentication. Twitter**</span><span class="sxs-lookup"><span data-stu-id="67645-155">**Microsoft.AspNetCore.Authentication.Twitter**</span></span>          |

<span data-ttu-id="67645-156">Her durumda, satıcıya bağımlı olan ve genellikle şunları içeren bir uygulama kayıt yordamını gerçekleştirmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="67645-156">In all cases, you must complete an application registration procedure that is vendor dependent and that usually involves:</span></span>

1. <span data-ttu-id="67645-157">Istemci uygulama KIMLIĞI alınıyor.</span><span class="sxs-lookup"><span data-stu-id="67645-157">Getting a Client Application ID.</span></span>
2. <span data-ttu-id="67645-158">Istemci uygulaması gizli dizisi alınıyor.</span><span class="sxs-lookup"><span data-stu-id="67645-158">Getting a Client Application Secret.</span></span>
3. <span data-ttu-id="67645-159">Yetkilendirme ara yazılımı ve kayıtlı sağlayıcı tarafından işlenen bir yeniden yönlendirme URL 'sini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="67645-159">Configuring an redirection URL, that's handled by the authorization middleware and the registered provider</span></span>
4. <span data-ttu-id="67645-160">İsteğe bağlı olarak, çoklu oturum açma (SSO) senaryosunda oturumu Kapat 'ı düzgün şekilde işlemek için bir oturum kapatma URL 'SI yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="67645-160">Optionally, configuring a sign-out URL to properly handle sign out in a Single Sign On (SSO) scenario.</span></span>

<span data-ttu-id="67645-161">Uygulamanızı bir dış sağlayıcıya yapılandırma hakkında daha fazla bilgi için, [ASP.NET Core belgelerinde dış sağlayıcı kimlik doğrulaması](/aspnet/core/security/authentication/social/)' na bakın.</span><span class="sxs-lookup"><span data-stu-id="67645-161">For details on configuring your app for an external provider, see the [External provider authentication in the ASP.NET Core documentation](/aspnet/core/security/authentication/social/)).</span></span>

> [!TIP]
<span data-ttu-id="67645-162">Tüm ayrıntılar, daha önce bahsedilen yetkilendirme ara yazılımı ve Hizmetleri tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="67645-162">All details are handled by the authorization middleware and services previously mentioned.</span></span> <span data-ttu-id="67645-163">Bu nedenle, Şekil 9-3 ' de gösterildiği gibi, daha önce bahsedilen kimlik doğrulama sağlayıcılarını kaydetmenin yanı sıra, ASP.NET Code Web uygulaması projesini Visual Studio 'da oluştururken yalnızca **bireysel kullanıcı hesabı** kimlik doğrulaması seçeneğini seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="67645-163">So, you just have to choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, as shown in Figure 9-3, besides registering the authentication providers previously mentioned.</span></span>

![Yeni ASP.NET Core Web uygulaması iletişim kutusunun ekran görüntüsü.](./media/index/select-individual-user-account-authentication-option.png)

<span data-ttu-id="67645-165">**Şekil 9-3**.</span><span class="sxs-lookup"><span data-stu-id="67645-165">**Figure 9-3**.</span></span> <span data-ttu-id="67645-166">Visual Studio 2019 ' de bir Web uygulaması projesi oluştururken dış kimlik doğrulaması kullanmak için bireysel kullanıcı hesapları seçeneğini seçme.</span><span class="sxs-lookup"><span data-stu-id="67645-166">Selecting the Individual User Accounts option, for using external authentication, when creating a web application project in Visual Studio 2019.</span></span>

<span data-ttu-id="67645-167">Daha önce listelenen dış kimlik doğrulama sağlayıcılarının yanı sıra, birçok daha fazla dış kimlik doğrulama sağlayıcısının kullanılmasına yönelik ara yazılım sağlayan üçüncü taraf paketleri de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="67645-167">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="67645-168">Bir liste için GitHub 'daki [Aspnet. Security. OAuth. Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) deposuna bakın.</span><span class="sxs-lookup"><span data-stu-id="67645-168">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repository on GitHub.</span></span>

<span data-ttu-id="67645-169">Ayrıca, özel ihtiyaçları çözümlemek için kendi dış kimlik doğrulama ara yazılımını da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67645-169">You can also create your own external authentication middleware to solve some special need.</span></span>

### <a name="authenticate-with-bearer-tokens"></a><span data-ttu-id="67645-170">Taşıyıcı belirteçleriyle kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="67645-170">Authenticate with bearer tokens</span></span>

<span data-ttu-id="67645-171">ASP.NET Core kimliği (veya kimlik Plus dış kimlik doğrulama sağlayıcıları) ile kimlik doğrulaması, Kullanıcı bilgilerini bir tanımlama bilgisinde depolamanın uygun olduğu birçok Web uygulaması senaryosunda iyi çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="67645-171">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="67645-172">Diğer senaryolarda, tanımlama bilgileri kalıcı ve veri iletimi gibi doğal bir yöntem değildir.</span><span class="sxs-lookup"><span data-stu-id="67645-172">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="67645-173">Örneğin, tek sayfalı uygulamalar (maça 'Lar) tarafından, yerel istemciler tarafından veya diğer Web API 'Leri tarafından erişilebilen yeniden kullanılabilir uç noktaları sunan bir ASP.NET Core Web API 'sinde, genellikle bunun yerine taşıyıcı belirteç kimlik doğrulamasını kullanmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="67645-173">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="67645-174">Bu tür uygulamalar tanımlama bilgileriyle çalışmaz, ancak bir taşıyıcı belirtecini kolayca alabilir ve sonraki isteklerin yetkilendirme üstbilgisine dahil edebilir.</span><span class="sxs-lookup"><span data-stu-id="67645-174">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="67645-175">Belirteç kimlik doğrulamasını etkinleştirmek için ASP.NET Core, [OAuth 2,0](https://oauth.net/2/) ve [OpenID Connect](https://openid.net/connect/)kullanımına yönelik çeşitli seçenekleri destekler.</span><span class="sxs-lookup"><span data-stu-id="67645-175">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="67645-176">OpenID Connect veya OAuth 2,0 kimlik sağlayıcısı ile kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="67645-176">Authenticate with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="67645-177">Kullanıcı bilgileri Azure Active Directory veya OpenID Connect ya da OAuth 2,0 ' ı destekleyen başka bir kimlik çözümünde depolanıyorsa, OpenID Connect iş akışını kullanarak kimlik doğrulamak için **Microsoft. AspNetCore. Authentication. Openıdconnect** paketini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67645-177">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the **Microsoft.AspNetCore.Authentication.OpenIdConnect** package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="67645-178">Örneğin, eShopOnContainers 'daki Identity. API mikro hizmeti için kimlik doğrulaması yapmak üzere, bir ASP.NET Core Web uygulaması, aşağıdaki Basitleştirilmiş örnekte gösterildiği gibi bu paketteki ara yazılımı kullanabilir `Startup.cs`:</span><span class="sxs-lookup"><span data-stu-id="67645-178">For example, to authenticate to the Identity.Api microservice in eShopOnContainers, an ASP.NET Core web application can use middleware from that package as shown in the following simplified example in `Startup.cs`:</span></span>

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

<span data-ttu-id="67645-179">Bu iş akışını kullandığınızda, tüm Kullanıcı bilgileri depolama ve kimlik doğrulama kimlik hizmeti tarafından işlendiği için ASP.NET Core Identity ara yazılımı gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="67645-179">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by the Identity service.</span></span>

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="67645-180">ASP.NET Core hizmetinden güvenlik belirteçleri verme</span><span class="sxs-lookup"><span data-stu-id="67645-180">Issue security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="67645-181">Dış kimlik sağlayıcısı kullanmak yerine yerel ASP.NET Core Identity kullanıcıları için güvenlik belirteçleri vermek isterseniz, bazı iyi üçüncü taraf kitaplıklarından yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67645-181">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="67645-182">[Identityserver4](https://github.com/IdentityServer/IdentityServer4) ve [Openıddict](https://github.com/openiddict/openiddict-core) , bir ASP.NET Core hizmetinden güvenlik belirteçleri vermesini sağlamak üzere ASP.NET Core kimlikle kolayca tümleştirilen OpenID Connect sağlayıcılarıdır.</span><span class="sxs-lookup"><span data-stu-id="67645-182">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="67645-183">[Identityserver4 belgeleri](https://identityserver4.readthedocs.io/en/latest/) , kitaplığı kullanmaya yönelik ayrıntılı yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="67645-183">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/latest/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="67645-184">Ancak, belirteçleri vermek için ıdentityserver4 kullanmanın temel adımları aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="67645-184">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1. <span data-ttu-id="67645-185">Uygulamayı çağırabilirsiniz. Useıdentityserver başlangıç. uygulamanın HTTP istek işleme ardışık düzenine ıdentityserver4 eklemek için yöntemi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="67645-185">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="67645-186">Bu, kitaplığın OpenID Connect ve/Connect/tokengibi OAuth2 uç noktalarına istek sunmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="67645-186">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2. <span data-ttu-id="67645-187">Identityserver4, Service 'e bir çağrı yaparak Startup. ConfigureServices içinde yapılandırırsınız. Addentityserver.</span><span class="sxs-lookup"><span data-stu-id="67645-187">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3. <span data-ttu-id="67645-188">Aşağıdaki verileri ayarlayarak kimlik sunucusunu yapılandırırsınız:</span><span class="sxs-lookup"><span data-stu-id="67645-188">You configure identity server by setting the following data:</span></span>

   - <span data-ttu-id="67645-189">İmzalama için kullanılacak [kimlik bilgileri](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) .</span><span class="sxs-lookup"><span data-stu-id="67645-189">The [credentials](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) to use for signing.</span></span>

   - <span data-ttu-id="67645-190">Kullanıcıların erişim isteyebilecek [kimlik ve API kaynakları](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) :</span><span class="sxs-lookup"><span data-stu-id="67645-190">The [Identity and API resources](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) that users might request access to:</span></span>

      - <span data-ttu-id="67645-191">API kaynakları, bir kullanıcının bir erişim belirteciyle erişebileceği korumalı verileri veya işlevselliği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="67645-191">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="67645-192">Bir API kaynağına bir örnek, yetkilendirme gerektiren bir Web API 'SI (veya API kümesi) olacaktır.</span><span class="sxs-lookup"><span data-stu-id="67645-192">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

      - <span data-ttu-id="67645-193">Kimlik kaynakları, bir kullanıcıyı tanımlamak için bir istemciye verilen bilgileri (talepler) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="67645-193">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="67645-194">Talepler Kullanıcı adı, e-posta adresi vb. içerebilir.</span><span class="sxs-lookup"><span data-stu-id="67645-194">The claims might include the user name, email address, and so on.</span></span>

   - <span data-ttu-id="67645-195">Belirteçleri istemek için bağlantı yapılacak [istemciler](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) .</span><span class="sxs-lookup"><span data-stu-id="67645-195">The [clients](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) that will be connecting in order to request tokens.</span></span>

   - <span data-ttu-id="67645-196">[ASP.NET Core kimliği](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) veya alternatif gibi Kullanıcı bilgileri için depolama mekanizması.</span><span class="sxs-lookup"><span data-stu-id="67645-196">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) or an alternative.</span></span>

<span data-ttu-id="67645-197">Identityserver4 için kullanılacak istemcileri ve kaynakları belirttiğinizde, uygun türdeki bir <xref:System.Collections.Generic.IEnumerable%601> koleksiyonunu bellek içi istemci veya kaynak depoları alan yöntemlere geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67645-197">When you specify clients and resources for IdentityServer4 to use, you can pass an <xref:System.Collections.Generic.IEnumerable%601> collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="67645-198">Ya da daha karmaşık senaryolar için, bağımlılık ekleme yoluyla istemci veya kaynak sağlayıcısı türleri sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67645-198">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="67645-199">Identityserver4 için, bellek içi kaynakları ve özel bir ılientstore türü tarafından sunulan istemcileri kullanmak için örnek bir yapılandırma aşağıdaki örnekteki gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="67645-199">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

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

### <a name="consume-security-tokens"></a><span data-ttu-id="67645-200">Güvenlik belirteçlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="67645-200">Consume security tokens</span></span>

<span data-ttu-id="67645-201">Bir OpenID Connect uç noktasına karşı kimlik doğrulaması veya kendi güvenlik belirteçlerinizi verme bazı senaryolar içerir.</span><span class="sxs-lookup"><span data-stu-id="67645-201">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="67645-202">Ancak, yalnızca farklı bir hizmet tarafından sunulan geçerli güvenlik belirteçleri olan kullanıcılarla erişimi sınırlamaya yönelik bir hizmet hakkında ne var?</span><span class="sxs-lookup"><span data-stu-id="67645-202">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="67645-203">Bu senaryo için, JWT belirteçlerini işleyen kimlik doğrulama ara yazılımı **Microsoft. AspNetCore. Authentication. Jwttaşıyıcı** paketinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="67645-203">For that scenario, authentication middleware that handles JWT tokens is available in the **Microsoft.AspNetCore.Authentication.JwtBearer** package.</span></span> <span data-ttu-id="67645-204">JWT, "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" için temsil eder ve güvenlik taleplerini iletişim kurmak için ortak bir güvenlik belirteci BIÇIMIDIR (RFC 7519 tarafından tanımlanır).</span><span class="sxs-lookup"><span data-stu-id="67645-204">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="67645-205">Bu tür belirteçleri kullanmak için ara yazılımın nasıl kullanılacağına ilişkin basitleştirilmiş bir örnek, sıralama. API mikro hizmeti olan eShopOnContainers 'dan alınan bu kod parçası gibi görünebilir.</span><span class="sxs-lookup"><span data-stu-id="67645-205">A simplified example of how to use middleware to consume such tokens might look like this code fragment, taken from the Ordering.Api microservice of eShopOnContainers.</span></span>

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

<span data-ttu-id="67645-206">Bu kullanımdaki parametreler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="67645-206">The parameters in this usage are:</span></span>

- <span data-ttu-id="67645-207">`Audience`, gelen belirtecin veya belirtecin erişim izni verdiği kaynağın alıcısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="67645-207">`Audience` represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="67645-208">Bu parametrede belirtilen değer, belirteçteki parametreyle eşleşmezse, belirteç reddedilir.</span><span class="sxs-lookup"><span data-stu-id="67645-208">If the value specified in this parameter does not match the parameter in the token, the token will be rejected.</span></span>

- <span data-ttu-id="67645-209">`Authority`, belirteç veren kimlik doğrulama sunucusunun adresidir.</span><span class="sxs-lookup"><span data-stu-id="67645-209">`Authority` is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="67645-210">JWT taşıyıcı kimlik doğrulama ara yazılımı, belirtecin imzasını doğrulamak için kullanılabilecek ortak anahtarı almak için bu URI 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="67645-210">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="67645-211">Ara yazılım, belirteçteki `iss` parametresinin bu URI ile eşleştiğini de onaylar.</span><span class="sxs-lookup"><span data-stu-id="67645-211">The middleware also confirms that the `iss` parameter in the token matches this URI.</span></span>

<span data-ttu-id="67645-212">`RequireHttpsMetadata`başka bir parametre, test amaçları için yararlıdır; Bu parametreyi yanlış olarak ayarlarsanız, sertifikalarınızın olmadığı ortamlarda test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67645-212">Another parameter, `RequireHttpsMetadata`, is useful for testing purposes; you set this parameter to false so you can test in environments where you don't have certificates.</span></span> <span data-ttu-id="67645-213">Gerçek dünyada dağıtımlarda, JWT taşıyıcı belirteçlerinin her zaman yalnızca HTTPS üzerinden geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="67645-213">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="67645-214">Bu ara yazılım söz konusu olduğunda, JWT belirteçleri yetkilendirme başlıklarından otomatik olarak ayıklanır.</span><span class="sxs-lookup"><span data-stu-id="67645-214">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="67645-215">Daha sonra bunlar seri durumdan silinir, onaylanır (`Audience` ve `Authority` parametrelerdeki değerler kullanılarak) ve daha sonra MVC eylemleri veya Yetkilendirme filtreleri tarafından başvurulmak üzere Kullanıcı bilgileri olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="67645-215">They are then deserialized, validated (using the values in the `Audience` and `Authority` parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="67645-216">JWT taşıyıcı kimlik doğrulama ara yazılımı, yetkili kullanılamıyorsa bir belirteci doğrulamak için yerel bir sertifika kullanma gibi daha gelişmiş senaryoları da destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="67645-216">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="67645-217">Bu senaryo için, `JwtBearerOptions` nesnesinde bir `TokenValidationParameters` nesnesi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67645-217">For this scenario, you can specify a `TokenValidationParameters` object in the `JwtBearerOptions` object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="67645-218">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="67645-218">Additional resources</span></span>

- <span data-ttu-id="67645-219">**Uygulamalar arasında tanımlama bilgilerini paylaşma** </span><span class="sxs-lookup"><span data-stu-id="67645-219">**Sharing cookies between applications** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- <span data-ttu-id="67645-220">**Kimlik \ giriş**</span><span class="sxs-lookup"><span data-stu-id="67645-220">**Introduction to Identity** \</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="67645-221">**Rick Anderson. SMS \ ile iki öğeli kimlik doğrulama**</span><span class="sxs-lookup"><span data-stu-id="67645-221">**Rick Anderson. Two-factor authentication with SMS** \</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- <span data-ttu-id="67645-222">**Facebook, Google ve diğer dış sağlayıcıları kullanarak kimlik doğrulamasını etkinleştirme** </span><span class="sxs-lookup"><span data-stu-id="67645-222">**Enabling authentication using Facebook, Google and other external providers** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- <span data-ttu-id="67645-223">**Michell Anıas. OAuth 2 \ giriş**</span><span class="sxs-lookup"><span data-stu-id="67645-223">**Michell Anicas. An Introduction to OAuth 2** \</span></span>
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- <span data-ttu-id="67645-224">**Aspnet. Security. OAuth. Providers** (ASP.net OAuth sağlayıcıları için GitHub deposu) </span><span class="sxs-lookup"><span data-stu-id="67645-224">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers) </span></span>\
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- <span data-ttu-id="67645-225">**Identityserver4. Resmi belgeler** </span><span class="sxs-lookup"><span data-stu-id="67645-225">**IdentityServer4. Official documentation** </span></span>\
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
><span data-ttu-id="67645-226">[Önceki](../implement-resilient-applications/monitor-app-health.md)
>[İleri](authorization-net-microservices-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="67645-226">[Previous](../implement-resilient-applications/monitor-app-health.md)
[Next](authorization-net-microservices-web-applications.md)</span></span>
