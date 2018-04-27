---
title: .NET mikro ve Web uygulamalarının güvenliğini sağlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | .NET mikro ve Web uygulamalarının güvenliğini sağlama
keywords: Docker, mikro, ASP.NET, kapsayıcı
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0ca69ada16fbb5a6757da96a7ea64d2113c15b6f
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="securing-net-microservices-and-web-applications"></a><span data-ttu-id="a5aad-104">.NET mikro ve Web uygulamalarının güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="a5aad-104">Securing .NET Microservices and Web Applications</span></span>

<span data-ttu-id="a5aad-105">Kaynakları ve bir hizmet tarafından kullanıma sunulan API'ler belirli güvenilen kullanıcıların veya istemcileri ile sınırlı olması için genellikle gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-105">It is often necessary for resources and APIs exposed by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="a5aad-106">Kimlik doğrulaması bu tür bir API düzeyinde güven kararları yapmak için ilk adımdır.</span><span class="sxs-lookup"><span data-stu-id="a5aad-106">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="a5aad-107">Kimlik doğrulama güvenilir bir şekilde bir kullanıcının kimliğini ascertaining işlemidir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-107">Authentication is the process of reliably ascertaining a user’s identity.</span></span>

<span data-ttu-id="a5aad-108">Mikro hizmet senaryolarda, kimlik doğrulama genellikle merkezi olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-108">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="a5aad-109">Bir API ağ geçidi kullanıyorsanız, Ağ Geçidi kimlik doğrulaması için uygun bir Şekil 11-1'de gösterildiği gibi yerdir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-109">If you are using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 11-1.</span></span> <span data-ttu-id="a5aad-110">Bu yaklaşımı kullanın, ek güvenlik iletilerin kimlik doğrulaması yerinde olup olmadığını Ağ Geçidi'nden veya geldikleri olmadıkça tek tek mikro doğrudan (API ağ geçidi) ulaşılamıyor emin olun.</span><span class="sxs-lookup"><span data-stu-id="a5aad-110">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![](./media/image1.png)

<span data-ttu-id="a5aad-111">**Şekil 11-1**.</span><span class="sxs-lookup"><span data-stu-id="a5aad-111">**Figure 11-1**.</span></span> <span data-ttu-id="a5aad-112">Bir API ağ geçidi ile kimlik doğrulamasını Merkezi</span><span class="sxs-lookup"><span data-stu-id="a5aad-112">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="a5aad-113">Hizmetleri doğrudan erişilebilir değilse, bir kimlik doğrulama hizmeti Azure Active Directory veya bir güvenlik belirteci hizmeti (STS), kullanıcıların kimliklerini doğrulamak için kullanılabilir davranan bir özel kimlik doğrulama mikro hizmet ister.</span><span class="sxs-lookup"><span data-stu-id="a5aad-113">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="a5aad-114">Güven kararları güvenlik belirteçleri veya tanımlama bilgilerini hizmetleriyle arasında paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="a5aad-114">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="a5aad-115">(Bu, gerekirse, ASP.NET Core ile uygulamalar arasında paylaşılabilir [veri koruma hizmetleri](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) Bu model, Şekil 11-2'de gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-115">(These can be shared between applications, if needed, in ASP.NET Core with [data protection services](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) This pattern is illustrated in Figure 11-2.</span></span>

![](./media/image2.png)

<span data-ttu-id="a5aad-116">**Şekil 11-2**.</span><span class="sxs-lookup"><span data-stu-id="a5aad-116">**Figure 11-2**.</span></span> <span data-ttu-id="a5aad-117">Kimlik doğrulama kimlik mikro hizmet tarafından; bir yetkilendirme belirtecini kullanarak güven paylaşılan</span><span class="sxs-lookup"><span data-stu-id="a5aad-117">Authentication by identity microservice; trust is shared using an authorization token</span></span>

## <a name="authenticating-using-aspnet-core-identity"></a><span data-ttu-id="a5aad-118">ASP.NET Core kimliğini kullanarak kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="a5aad-118">Authenticating using ASP.NET Core Identity</span></span>

<span data-ttu-id="a5aad-119">Bir uygulamanın kullanıcıları tanımlamak için ASP.NET Core birincil mekanizma olan [ASP.NET Core kimliği](https://docs.microsoft.com/aspnet/core/security/authentication/identity) üyelik sistemi.</span><span class="sxs-lookup"><span data-stu-id="a5aad-119">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](https://docs.microsoft.com/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="a5aad-120">ASP.NET Core kimlik geliştirici tarafından yapılandırılan bir veri deposu (oturum açma bilgileri, rolleri ve talepler dahil) kullanıcı bilgilerini depolar.</span><span class="sxs-lookup"><span data-stu-id="a5aad-120">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="a5aad-121">Genellikle, ASP.NET Core kimliği veri deposu Microsoft.AspNetCore.Identity.EntityFrameworkCore paketinde sağlanan bir Entity Framework deposudur.</span><span class="sxs-lookup"><span data-stu-id="a5aad-121">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the Microsoft.AspNetCore.Identity.EntityFrameworkCore package.</span></span> <span data-ttu-id="a5aad-122">Ancak, özel depoları veya diğer üçüncü taraf paketlerden Azure Table Storage, DocumentDB veya başka konumlara kimlik bilgilerini depolamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-122">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, DocumentDB, or other locations.</span></span>

<span data-ttu-id="a5aad-123">Aşağıdaki kod, seçili tek tek kullanıcı hesabı kimlik doğrulaması ile ASP.NET çekirdek Web uygulaması proje şablonu alınır.</span><span class="sxs-lookup"><span data-stu-id="a5aad-123">The following code is taken from the ASP.NET Core Web Application project template with individual user account authentication selected.</span></span> <span data-ttu-id="a5aad-124">ASP.NET Core EntityFramework.Core Startup.ConfigureServices yöntemiyle kimliğinin nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-124">It shows how to configure ASP.NET Core Identity using EntityFramework.Core in the Startup.ConfigureServices method.</span></span>

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

<span data-ttu-id="a5aad-125">ASP.NET Core kimliği yapılandırıldıktan sonra çağıran uygulama tarafından etkinleştirin. Hizmetin Startup.Configure yönteminde UseIdentity.</span><span class="sxs-lookup"><span data-stu-id="a5aad-125">Once ASP.NET Core Identity is configured, you enable it by calling app.UseIdentity in the service’s Startup.Configure method.</span></span>

<span data-ttu-id="a5aad-126">ASP.NET kodu kimliğini kullanarak birkaç senaryo sağlar:</span><span class="sxs-lookup"><span data-stu-id="a5aad-126">Using ASP.NET Code Identity enables several scenarios:</span></span>

-   <span data-ttu-id="a5aad-127">Yeni kullanıcı bilgilerini UserManager türünü (userManager.CreateAsync) kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a5aad-127">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

-   <span data-ttu-id="a5aad-128">SignInManager türü kullanan kullanıcıları doğrula.</span><span class="sxs-lookup"><span data-stu-id="a5aad-128">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="a5aad-129">Doğrudan oturum açmak için signInManager.SignInAsync kullanabilir veya kullanıcının parolayı onaylamak için signInManager.PasswordSignInAsync doğru olduğundan ve bunları oturum açın.</span><span class="sxs-lookup"><span data-stu-id="a5aad-129">You can use signInManager.SignInAsync to sign in directly, or signInManager.PasswordSignInAsync to confirm the user’s password is correct and then sign them in.</span></span>

-   <span data-ttu-id="a5aad-130">Böylece bir tarayıcı gelen sonraki istekleri oturum açmış kullanıcının kimlik ve talepleri içerir (hangi ASP.NET Core kimliği ara yazılımı tarafından okunur) bir tanımlama bilgisinde depolanan bilgilere dayanarak bir kullanıcıyı tanımlamak.</span><span class="sxs-lookup"><span data-stu-id="a5aad-130">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="a5aad-131">ASP.NET Core kimliği de destekler [iki öğeli kimlik doğrulama](https://docs.microsoft.com/aspnet/core/security/authentication/2fa).</span><span class="sxs-lookup"><span data-stu-id="a5aad-131">ASP.NET Core Identity also supports [two-factor authentication](https://docs.microsoft.com/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="a5aad-132">Bir yerel kullanıcı veri deposunu olun kimlik doğrulama senaryoları kullanın ve kimlik (MVC web uygulamaları için tipik olarak) tanımlama bilgilerini kullanarak istekler arasında kalıcı hale getirmek için ASP.NET Core kimliği önerilen bir çözümdür.</span><span class="sxs-lookup"><span data-stu-id="a5aad-132">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

## <a name="authenticating-using-external-providers"></a><span data-ttu-id="a5aad-133">Dış sağlayıcılar kullanarak kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="a5aad-133">Authenticating using external providers</span></span>

<span data-ttu-id="a5aad-134">ASP.NET Core de destekler kullanarak [Dış kimlik doğrulama sağlayıcıları](https://docs.microsoft.com/aspnet/core/security/authentication/social/) aracılığıyla oturum açmasına izin vermek için [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) akışları.</span><span class="sxs-lookup"><span data-stu-id="a5aad-134">ASP.NET Core also supports using [external authentication providers](https://docs.microsoft.com/aspnet/core/security/authentication/social/) to let users log in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="a5aad-135">Bu, kullanıcıların Microsoft, Google, Facebook ve Twitter gibi sağlayıcılarından var olan kimlik doğrulama işlemleri kullanarak oturum açın ve ASP.NET Core Kimlikteki uygulamanızda bu kimlikleri ilişkilendirmek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-135">This means that users can log in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="a5aad-136">Dış kimlik doğrulama kullanmak için uygulamanızın HTTP istek ardışık düzen işleme uygun yetkilendirme Ara yazılımının ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a5aad-136">To use external authentication, you include the appropriate authentication middleware in your application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="a5aad-137">Bu ara yazılım kimlik bilgilerini yakalama ve SignInManager.GetExternalLoginInfo yöntemi yoluyla kullanılabilir hale getirme kimlik doğrulama sağlayıcısı URI yollar döndürmek işleme isteklerinin sorumludur.</span><span class="sxs-lookup"><span data-stu-id="a5aad-137">This middleware is responsible for handling requests to return URI routes from the authentication provider, capturing identity information, and making it available via the SignInManager.GetExternalLoginInfo method.</span></span>

<span data-ttu-id="a5aad-138">Popüler Dış kimlik doğrulama sağlayıcıları ve bunların ilişkili NuGet paketleri, aşağıda gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-138">Popular external authentication providers and their associated NuGet packages are shown below.</span></span>

<span data-ttu-id="a5aad-139">**Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount</span><span class="sxs-lookup"><span data-stu-id="a5aad-139">**Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount</span></span>

<span data-ttu-id="a5aad-140">**Google:** Microsoft.AspNetCore.Authentication.Google</span><span class="sxs-lookup"><span data-stu-id="a5aad-140">**Google:** Microsoft.AspNetCore.Authentication.Google</span></span>

<span data-ttu-id="a5aad-141">**Facebook:** Microsoft.AspNetCore.Authentication.Facebook</span><span class="sxs-lookup"><span data-stu-id="a5aad-141">**Facebook:** Microsoft.AspNetCore.Authentication.Facebook</span></span>

<span data-ttu-id="a5aad-142">**Twitter:** Microsoft.AspNetCore.Authentication.Twitter</span><span class="sxs-lookup"><span data-stu-id="a5aad-142">**Twitter:** Microsoft.AspNetCore.Authentication.Twitter</span></span>

<span data-ttu-id="a5aad-143">Her durumda, ara yazılım app ile benzer bir kayıt yöntemine yapılan bir çağrı kayıtlı. {ExternalProvider} kimlik doğrulaması Startup.Configure kullanın.</span><span class="sxs-lookup"><span data-stu-id="a5aad-143">In all cases, the middleware is registered with a call to a registration method similar to app.Use{ExternalProvider}Authentication in Startup.Configure.</span></span> <span data-ttu-id="a5aad-144">Bu kayıt yöntemleri bir uygulama kimliği ve gizli bilgi içeren bir seçenekleri nesne alın (bir parola örneği için), sağlayıcı tarafından gerektiği şekilde.</span><span class="sxs-lookup"><span data-stu-id="a5aad-144">These registration methods take an options object that contains an application ID and secret information (a password, for instance), as needed by the provider.</span></span> <span data-ttu-id="a5aad-145">Dış kimlik doğrulama sağlayıcıları kaydedilmesi için uygulama gerektirir (açıklandığı gibi [ASP.NET Core belgeleri](https://docs.microsoft.com/aspnet/core/security/authentication/social/)) böylece hangi uygulama kimliğini erişmek isteyen kullanıcının bilgilendirebilir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-145">External authentication providers require the application to be registered (as explained in [ASP.NET Core documentation](https://docs.microsoft.com/aspnet/core/security/authentication/social/)) so that they can inform the user what application is requesting access to their identity.</span></span>

<span data-ttu-id="a5aad-146">Ara yazılım içinde Startup.Configure kaydedildiğinde, her denetleyici eylemini oturum açmak için kullanıcılar isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-146">Once the middleware is registered in Startup.Configure, you can prompt users to log in from any controller action.</span></span> <span data-ttu-id="a5aad-147">Bunu yapmak için kimlik doğrulama sağlayıcısının adını ve bir yönlendirme URL'si içeren bir AuthenticationProperties nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a5aad-147">To do this, you create an AuthenticationProperties object that includes the authentication provider’s name and a redirect URL.</span></span> <span data-ttu-id="a5aad-148">Ardından AuthenticationProperties nesnesi iletir bir sınama yanıtı döndürür.</span><span class="sxs-lookup"><span data-stu-id="a5aad-148">You then return a Challenge response that passes the AuthenticationProperties object.</span></span> <span data-ttu-id="a5aad-149">Aşağıdaki kod, bunun bir örneğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-149">The following code shows an example of this.</span></span>

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

<span data-ttu-id="a5aad-150">Redirecturl'yi parametresi, kullanıcı kimliğini doğrulamasından sonra dış sağlayıcı yönlendirilmeniz gerekir URL içerir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-150">The redirectUrl parameter includes the URL that the external provider should redirect to once the user has authenticated.</span></span> <span data-ttu-id="a5aad-151">URL kullanıcı Basitleştirilmiş aşağıdaki örnekteki gibi dış kimlik bilgileri temel alarak oturum açacak bir eylemi temsil etmelidir:</span><span class="sxs-lookup"><span data-stu-id="a5aad-151">The URL should represent an action that will sign the user in based on external identity information, as in the following simplified example:</span></span>

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

<span data-ttu-id="a5aad-152">Seçerseniz **tek tek kullanıcı hesabı** Visual Studio'da oturum dış sağlayıcı imzalamak gerekli tüm kod ASP.NET kodunun web uygulaması projesi oluşturduğunuzda, kimlik doğrulama seçenektir zaten projede gösterildiği gibi Şekil 11-3 '.</span><span class="sxs-lookup"><span data-stu-id="a5aad-152">If you choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, all the code necessary to sign in with an external provider is already in the project, as shown in Figure 11-3.</span></span>

![https://msdnshared.blob.core.windows.net/media/2016/10/new-web-app.png](./media/image3.png)

<span data-ttu-id="a5aad-153">**Şekil 11-3**.</span><span class="sxs-lookup"><span data-stu-id="a5aad-153">**Figure 11-3**.</span></span> <span data-ttu-id="a5aad-154">Bir web uygulaması projesi oluştururken, dış kimlik doğrulama kullanmak için bir seçenek seçme</span><span class="sxs-lookup"><span data-stu-id="a5aad-154">Selecting an option for using external authentication when creating a web application project</span></span>

<span data-ttu-id="a5aad-155">Ek olarak dış kimlik doğrulama sağlayıcıları üçüncü taraf paketlerden daha önce listelenen pek çok fazla dış kimlik doğrulama sağlayıcıları için ara yazılım sağladığınız kullanılabilir durumdadır.</span><span class="sxs-lookup"><span data-stu-id="a5aad-155">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="a5aad-156">Bir listesi için bkz: [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) bağlantıların github'da.</span><span class="sxs-lookup"><span data-stu-id="a5aad-156">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repo on GitHub.</span></span>

<span data-ttu-id="a5aad-157">Ayrıca Elbette, kendi dış kimlik doğrulaması ara yazılımı oluşturmak için mümkündür.</span><span class="sxs-lookup"><span data-stu-id="a5aad-157">It is also possible, of course, to create your own external authentication middleware.</span></span>

## <a name="authenticating-with-bearer-tokens"></a><span data-ttu-id="a5aad-158">Taşıyıcı belirteçleri ile kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="a5aad-158">Authenticating with bearer tokens</span></span>

<span data-ttu-id="a5aad-159">ASP.NET Core kimliği (veya kimlik ve Dış kimlik doğrulama sağlayıcıları ile) ve kimlik doğrulama kullanıcı bilgileri depolayan bir tanımlama bilgisinde uygundur iyi birçok web uygulama senaryoları için çalışır.</span><span class="sxs-lookup"><span data-stu-id="a5aad-159">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="a5aad-160">Diğer senaryolarda, ancak, tanımlama bilgilerini kalıcı yapma ve veri aktarırken bir doğal değildir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-160">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="a5aad-161">Örneğin, bir ASP.NET çekirdek Web API yerel istemciler tarafından tek sayfa uygulamaları (SPAs) tarafından erişilebilen RESTful uç noktalarını kullanıma sunan veya hatta diğer Web API'leri tarafından genellikle taşıyıcı belirteci kimlik doğrulaması yerine kullanmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="a5aad-161">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="a5aad-162">Bu tür uygulamalar değil tanımlama bilgileriyle çalışır ancak kolayca taşıyıcı belirtecini almak ve sonraki istekleri yetkilendirme üst bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-162">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="a5aad-163">Belirteç kimlik doğrulamasını etkinleştirmek için ASP.NET Core çeşitli seçenekler kullanmak için destekleyen [OAuth 2.0](https://oauth.net/2/) ve [Openıd Connect](https://openid.net/connect/).</span><span class="sxs-lookup"><span data-stu-id="a5aad-163">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

## <a name="authenticating-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="a5aad-164">Bir Openıd Connect veya OAuth 2.0 kimlik sağlayıcısı ile kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="a5aad-164">Authenticating with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="a5aad-165">Kullanıcı bilgilerini Azure Active Directory veya Openıd Connect veya OAuth 2.0 destekleyen başka bir kimlik çözümü depolanıyorsa, Openıd Connect iş akışını kullanarak kimlik doğrulaması için Microsoft.AspNetCore.Authentication.OpenIdConnect paketi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5aad-165">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the Microsoft.AspNetCore.Authentication.OpenIdConnect package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="a5aad-166">Örneğin, [karşı Azure Active Directory kimlik doğrulaması](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/), aşağıdaki örnekte gösterildiği gibi bir ASP.NET Core web uygulaması ara yazılım bu paketten kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a5aad-166">For example, to [authenticate against Azure Active Directory](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/), an ASP.NET Core web application can use middleware from that package as shown in the following example:</span></span>

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

<span data-ttu-id="a5aad-167">Yapılandırma değerleri, uygulamanızın olduğunda oluşturulan Azure Active Directory değerlerdir [bir Azure AD istemcisi olarak kayıtlı](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad).</span><span class="sxs-lookup"><span data-stu-id="a5aad-167">The configuration values are Azure Active Directory values that are created when your application is [registered as an Azure AD client](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad).</span></span> <span data-ttu-id="a5aad-168">Tüm Azure Active Directory ile kimliği doğrulanan kullanıcılar kimlik doğrulaması gerekiyorsa tek bir istemci kimliği bir uygulamada birden çok mikro arasında paylaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-168">A single client ID can be shared among multiple microservices in an application if they all need to authenticate users authenticated via Azure Active Directory.</span></span>

<span data-ttu-id="a5aad-169">Tüm kullanıcı bilgilerini depolama ve kimlik doğrulama gerçekleştirilir için Azure Active Directory tarafından bu iş akışı kullandığınızda, ASP.NET Core kimliği ara yazılımı gerekli değildir, unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a5aad-169">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by Azure Active Directory.</span></span>

## <a name="issuing-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="a5aad-170">Bir ASP.NET Core hizmetinden güvenlik belirteçleri verme</span><span class="sxs-lookup"><span data-stu-id="a5aad-170">Issuing security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="a5aad-171">Yerel ASP.NET Core kimliği kullanıcılar için güvenlik belirteçleri vermek tercih ettiğiniz yerine, bir dış kimlik sağlayıcı kullanarak, bazı iyi üçüncü taraf kitaplıkların yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5aad-171">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="a5aad-172">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) ve [OpenIddict](https://github.com/openiddict/openiddict-core) kolayca sorunu güvenlik belirteçleri bir ASP.NET Core hizmetinden olanak ASP.NET Core kimliği ile tümleşen Openıd Connect sağlayıcılarıdır.</span><span class="sxs-lookup"><span data-stu-id="a5aad-172">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="a5aad-173">[IdentityServer4 belgelerine](https://identityserver4.readthedocs.io/en/release/) kitaplığı kullanmaya yönelik ayrıntılı yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-173">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/release/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="a5aad-174">Ancak, IdentityServer4 sorunu belirteçleri kullanarak yönelik temel adımlar aşağıda belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-174">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1.  <span data-ttu-id="a5aad-175">Uygulama çağırın. IdentityServer4 uygulamanın HTTP istek işleme ardışık düzenine eklemek için UseIdentityServer Startup.Configure yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a5aad-175">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="a5aad-176">Bu, Openıd Connect ve /connect/token gibi OAuth2 uç noktaları için isteklere hizmet kitaplığı olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a5aad-176">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2.  <span data-ttu-id="a5aad-177">Hizmetler için bir çağrı yaparak IdentityServer4 Startup.ConfigureServices içinde yapılandırın. AddIdentityServer.</span><span class="sxs-lookup"><span data-stu-id="a5aad-177">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3.  <span data-ttu-id="a5aad-178">Aşağıdaki veriler sağlayarak kimlik sunucusunu yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="a5aad-178">You configure identity server by providing the following data:</span></span>

-   <span data-ttu-id="a5aad-179">[Kimlik bilgileri](https://identityserver4.readthedocs.io/en/release/topics/crypto.html) imzalama için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="a5aad-179">The [credentials](https://identityserver4.readthedocs.io/en/release/topics/crypto.html) to use for signing.</span></span>

-   <span data-ttu-id="a5aad-180">[Kimlik ve API kaynakları](https://identityserver4.readthedocs.io/en/release/topics/resources.html) kullanıcıların erişimi isteyebilir:</span><span class="sxs-lookup"><span data-stu-id="a5aad-180">The [Identity and API resources](https://identityserver4.readthedocs.io/en/release/topics/resources.html) that users might request access to:</span></span>

<!-- -->

-   <span data-ttu-id="a5aad-181">API kaynakları korumalı veriler veya bir erişim belirteciyle bir kullanıcının erişebildiği işlevleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a5aad-181">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="a5aad-182">Bir örnek bir API kaynağı bir web API (veya API kümesi) olabilir yetkilendirme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-182">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

-   <span data-ttu-id="a5aad-183">Identity kaynaklar bir istemciye bir kullanıcıyı tanımlamak için verilen bilgileri (talep) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a5aad-183">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="a5aad-184">Talepler, kullanıcı adı, e-posta adresi vb. içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-184">The claims might include the user name, email address, and so on.</span></span>

<!-- -->

-   <span data-ttu-id="a5aad-185">[İstemciler](https://identityserver4.readthedocs.io/en/release/topics/clients.html) , bağlanma belirteçler istemek için.</span><span class="sxs-lookup"><span data-stu-id="a5aad-185">The [clients](https://identityserver4.readthedocs.io/en/release/topics/clients.html) that will be connecting in order to request tokens.</span></span>

-   <span data-ttu-id="a5aad-186">Kullanıcı bilgilerini depolama mekanizmasını gibi [ASP.NET Core kimliği](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) veya alternatif.</span><span class="sxs-lookup"><span data-stu-id="a5aad-186">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) or an alternative.</span></span>

<span data-ttu-id="a5aad-187">İstemcileri ve kaynakları IdentityServer4 için kullanılacak belirttiğinizde, bir IEnumerable geçirebilirsiniz&lt;T&gt; uygun türe bellek içi istemci veya kaynak depoları ele yöntemleri topluluğu.</span><span class="sxs-lookup"><span data-stu-id="a5aad-187">When you specify clients and resources for IdentityServer4 to use, you can pass an IEnumerable&lt;T&gt; collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="a5aad-188">Veya daha karmaşık senaryolar için istemci veya kaynak sağlayıcısı türlerinin bağımlılık ekleme aracılığıyla sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-188">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="a5aad-189">Bellek içi kaynaklar ve özel bir IClientStore türü tarafından sağlanan istemcileri kullanmak IdentityServer4 için örnek bir yapılandırma aşağıdaki gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="a5aad-189">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

## <a name="consuming-security-tokens"></a><span data-ttu-id="a5aad-190">Güvenlik belirteçleri kullanma</span><span class="sxs-lookup"><span data-stu-id="a5aad-190">Consuming security tokens</span></span>

<span data-ttu-id="a5aad-191">Bir Openıd Connect uç nokta karşı kimlik doğrulaması veya kendi güvenlik belirteçleri verme bazı senaryolar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a5aad-191">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="a5aad-192">Ancak ne yalnızca geçerli güvenliğe sahip kullanıcılara erişimi sınırlamak için gereken bir hizmet belirteçleri farklı bir hizmet tarafından sağlandı?</span><span class="sxs-lookup"><span data-stu-id="a5aad-192">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="a5aad-193">Bu senaryo için JWT belirteçleri işleme kimlik doğrulaması ara yazılımı Microsoft.AspNetCore.Authentication.JwtBearer paketinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-193">For that scenario, authentication middleware that handles JWT tokens is available in the Microsoft.AspNetCore.Authentication.JwtBearer package.</span></span> <span data-ttu-id="a5aad-194">JWT anlamına gelir "[JSON Web belirteci](https://tools.ietf.org/html/rfc7519)" ve güvenlik taleplerini iletişim kurmak için (RFC 7519 tarafından tanımlanan) ortak bir güvenlik belirteci biçimi değil.</span><span class="sxs-lookup"><span data-stu-id="a5aad-194">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="a5aad-195">Ara yazılım bu tür belirteçleri tüketen için nasıl kullanılacağını basit bir örneği aşağıdaki gibi görünebilir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-195">A simple example of how to use middleware to consume such tokens might look like the following example.</span></span> <span data-ttu-id="a5aad-196">Bu kod ASP.NET Core MVC Ara (app. çağrıları gelmelidir UseMvc).</span><span class="sxs-lookup"><span data-stu-id="a5aad-196">This code must precede calls to ASP.NET Core MVC middleware (app.UseMvc).</span></span>

```csharp
app.UseJwtBearerAuthentication(new JwtBearerOptions()
{
    Audience = "http://localhost:5001/",
    Authority = "http://localhost:5000/",
    AutomaticAuthenticate = true
});
```

<span data-ttu-id="a5aad-197">Bu kullanım parametrelerinde şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a5aad-197">The parameters in this usage are:</span></span>

-   <span data-ttu-id="a5aad-198">Hedef kitle gelen belirteci ya da erişim belirteci verir kaynak alıcısı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a5aad-198">Audience represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="a5aad-199">Bu parametrede belirtilen değer belirteci aud parametresinde eşleşmiyorsa, belirteç kabul edilmeyecek.</span><span class="sxs-lookup"><span data-stu-id="a5aad-199">If the value specified in this parameter does not match the aud parameter in the token, the token will be rejected.</span></span>

-   <span data-ttu-id="a5aad-200">Yetki belirteci veren kimlik doğrulama sunucusu adresidir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-200">Authority is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="a5aad-201">JWT taşıyıcı kimlik doğrulaması ara yazılımı bu URI belirtecin imzayı doğrulamak için kullanılan ortak anahtar almak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="a5aad-201">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="a5aad-202">Ara yazılım, ayrıca belirteç ISS parametresinde bu URI ile eşleşip eşleşmediğini onaylar.</span><span class="sxs-lookup"><span data-stu-id="a5aad-202">The middleware also confirms that the iss parameter in the token matches this URI.</span></span>

-   <span data-ttu-id="a5aad-203">AutomaticAuthenticate belirtecin tarafından tanımlanan kullanıcı otomatik olarak imzalanması gerektiğini olup olmadığını gösteren bir Boole değeri değil.</span><span class="sxs-lookup"><span data-stu-id="a5aad-203">AutomaticAuthenticate is a Boolean value that indicates whether the user defined by the token should be automatically signed in.</span></span>

<span data-ttu-id="a5aad-204">Başka bir parametre, RequireHttpsMetadata, bu örnekte kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="a5aad-204">Another parameter, RequireHttpsMetadata, is not used in this example.</span></span> <span data-ttu-id="a5aad-205">Sınama amacıyla yararlı olur; Böylece ortamlarında test, bu parametre false olarak burada sertifikası olmayan ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a5aad-205">It is useful for testing purposes; you set this parameter to false so that you can test in environments where you do not have certificates.</span></span> <span data-ttu-id="a5aad-206">Gerçek dünya dağıtımlarda, JWT taşıyıcı belirteçlerini her zaman yalnızca HTTPS üzerinden aktarılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a5aad-206">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="a5aad-207">Yerinde bu Ara yazılımla JWT belirteçleri yetkilendirme üstbilgileri otomatik olarak çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="a5aad-207">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="a5aad-208">Bunlar daha sonra seri, (İzleyici ve yetkilisi parametrelerinin değerleri kullanarak) doğrulandı ve MVC eylemler veya yetkilendirme filtreleri daha sonra başvurulmak üzere kullanıcı bilgilerini olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="a5aad-208">They are then deserialized, validated (using the values in the Audience and Authority parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="a5aad-209">JWT taşıyıcı kimlik doğrulaması ara yazılımı ayrıca yerel bir sertifika yetkilisi kullanılamıyorsa bir belirteci doğrulamak için kullanma gibi daha Gelişmiş senaryolar destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a5aad-209">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="a5aad-210">Bu senaryo için JwtBearerOptions nesnesinde tokenvalidationparameters değerini nesnesi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5aad-210">For this scenario, you can specify a TokenValidationParameters object in the JwtBearerOptions object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="a5aad-211">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="a5aad-211">Additional resources</span></span>

-   <span data-ttu-id="a5aad-212">**Uygulamalar arasında tanımlama bilgilerini paylaşımı**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#paylaşımı kimlik doğrulama-tanımlama bilgileri-arasında-uygulamalar*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)</span><span class="sxs-lookup"><span data-stu-id="a5aad-212">**Sharing cookies between applications**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sharing-authentication-cookies-between-applications*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)</span></span>

-   <span data-ttu-id="a5aad-213">**Kimlik giriş**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span><span class="sxs-lookup"><span data-stu-id="a5aad-213">**Introduction to Identity**
[*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span></span>

-   <span data-ttu-id="a5aad-214">**Rick Anderson. SMS ile iki öğeli kimlik doğrulama**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)</span><span class="sxs-lookup"><span data-stu-id="a5aad-214">**Rick Anderson. Two-factor authentication with SMS**
[*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)</span></span>

-   <span data-ttu-id="a5aad-215">**Facebook, Google ve diğer dış sağlayıcılarını kullanarak kimlik doğrulamasını etkinleştirme**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)</span><span class="sxs-lookup"><span data-stu-id="a5aad-215">**Enabling authentication using Facebook, Google and other external providers**
[*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)</span></span>

-   <span data-ttu-id="a5aad-216">**Michell Anicas. OAuth 2 giriş**
    [*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)</span><span class="sxs-lookup"><span data-stu-id="a5aad-216">**Michell Anicas. An Introduction to OAuth 2**
[*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)</span></span>

-   <span data-ttu-id="a5aad-217">**AspNet.Security.OAuth.Providers** (ASP.NET OAuth sağlayıcıları için GitHub depo.</span><span class="sxs-lookup"><span data-stu-id="a5aad-217">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers.</span></span>
    [*https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src*](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

-   <span data-ttu-id="a5aad-218">**Danny Strockis. Bir ASP.NET Core web uygulamasına Azure AD tümleştirme**
    [*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)</span><span class="sxs-lookup"><span data-stu-id="a5aad-218">**Danny Strockis. Integrating Azure AD into an ASP.NET Core web app**
[*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)</span></span>

-   <span data-ttu-id="a5aad-219">**IdentityServer4. Resmi belge**
    [*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)</span><span class="sxs-lookup"><span data-stu-id="a5aad-219">**IdentityServer4. Official documentation**
[*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="a5aad-220">[Önceki] (.. /implement-resilient-Applications/Monitor-App-Health.MD) [sonraki] (yetkilendirme-net-mikro-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="a5aad-220">[Previous] (../implement-resilient-applications/monitor-app-health.md) [Next] (authorization-net-microservices-web-applications.md)</span></span>
