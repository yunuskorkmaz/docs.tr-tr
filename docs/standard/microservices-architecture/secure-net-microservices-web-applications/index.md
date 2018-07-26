---
title: .NET mikro Hizmetleri ve Web uygulamalarının güvenliğini sağlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | .NET mikro Hizmetleri ve Web uygulamalarının güvenliğini sağlama
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 0e55a68432dfd44c7a73ae51512f50d481ae100c
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37937039"
---
# <a name="securing-net-microservices-and-web-applications"></a><span data-ttu-id="e1033-103">.NET mikro Hizmetleri ve Web uygulamalarının güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="e1033-103">Securing .NET Microservices and Web Applications</span></span>

<span data-ttu-id="e1033-104">Genellikle, gerekli kaynak ve hizmet tarafından sunulan API'ler belirli güvenilen kullanıcıların veya istemciler için sınırlı olur.</span><span class="sxs-lookup"><span data-stu-id="e1033-104">It is often necessary for resources and APIs exposed by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="e1033-105">Kimlik doğrulaması yaparak bu tür bir API düzeyinde güven kararları için ilk adımdır.</span><span class="sxs-lookup"><span data-stu-id="e1033-105">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="e1033-106">Kimlik doğrulaması güvenilir bir şekilde bir kullanıcının kimliğini ascertaining işlemidir.</span><span class="sxs-lookup"><span data-stu-id="e1033-106">Authentication is the process of reliably ascertaining a user’s identity.</span></span>

<span data-ttu-id="e1033-107">Mikro hizmet senaryolarda, kimlik doğrulaması genellikle merkezi olarak yönetilir.</span><span class="sxs-lookup"><span data-stu-id="e1033-107">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="e1033-108">Bir API ağ geçidi kullanıyorsanız, ağ geçidi kimliğini doğrulamak için uygun bir Şekil 11-1'de gösterildiği yerdir.</span><span class="sxs-lookup"><span data-stu-id="e1033-108">If you are using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 11-1.</span></span> <span data-ttu-id="e1033-109">Bu yaklaşımı kullanın, ek güvenlik iletileri kimlik doğrulaması yerinde olup olmadığını ağ geçidinden veya geldikleri olmadığı sürece her bir mikro hizmetin doğrudan (API ağ geçidi) ulaşılamıyor emin olun.</span><span class="sxs-lookup"><span data-stu-id="e1033-109">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![](./media/image1.png)

<span data-ttu-id="e1033-110">**Şekil 11-1**.</span><span class="sxs-lookup"><span data-stu-id="e1033-110">**Figure 11-1**.</span></span> <span data-ttu-id="e1033-111">Bir API ağ geçidi ile merkezi kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="e1033-111">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="e1033-112">Hizmetleri doğrudan erişilebilir, kimlik doğrulama hizmeti Azure Active Directory veya bir güvenlik belirteci hizmeti (STS), kullanıcıların kimliklerini doğrulamak için kullanılabilir davranan bir özel kimlik doğrulama mikro hizmet gibi.</span><span class="sxs-lookup"><span data-stu-id="e1033-112">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="e1033-113">Güven kararları güvenlik belirteçleri veya tanımlama bilgileri ile hizmetler arasında paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="e1033-113">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="e1033-114">(Bunlar gerekirse, ASP.NET Core ile uygulamalar arasında paylaşılabilir [veri koruma hizmetleri](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) Bu düzen, Şekil 11-2'de gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e1033-114">(These can be shared between applications, if needed, in ASP.NET Core with [data protection services](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications).) This pattern is illustrated in Figure 11-2.</span></span>

![](./media/image2.png)

<span data-ttu-id="e1033-115">**Şekil 11-2**.</span><span class="sxs-lookup"><span data-stu-id="e1033-115">**Figure 11-2**.</span></span> <span data-ttu-id="e1033-116">Kimlik mikro hizmet olarak kimlik doğrulaması; bir yetkilendirme belirteciyle güven paylaşılan</span><span class="sxs-lookup"><span data-stu-id="e1033-116">Authentication by identity microservice; trust is shared using an authorization token</span></span>

## <a name="authenticating-using-aspnet-core-identity"></a><span data-ttu-id="e1033-117">ASP.NET Core kimliği kullanarak kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="e1033-117">Authenticating using ASP.NET Core Identity</span></span>

<span data-ttu-id="e1033-118">Bir uygulamanın kullanıcıları tanımlamak için birincil mekanizma ASP.NET core'da [ASP.NET Core kimliği](https://docs.microsoft.com/aspnet/core/security/authentication/identity) üyelik sistemi.</span><span class="sxs-lookup"><span data-stu-id="e1033-118">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](https://docs.microsoft.com/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="e1033-119">ASP.NET Core kimliği geliştirici tarafından yapılandırılmış bir veri deposu (oturum açma bilgileri, rolleri ve talep dahil) kullanıcı bilgilerini depolar.</span><span class="sxs-lookup"><span data-stu-id="e1033-119">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="e1033-120">Genellikle, ASP.NET Core kimliği veri deposu Microsoft.AspNetCore.Identity.EntityFrameworkCore paketinde sağlanan bir Entity Framework deposudur.</span><span class="sxs-lookup"><span data-stu-id="e1033-120">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the Microsoft.AspNetCore.Identity.EntityFrameworkCore package.</span></span> <span data-ttu-id="e1033-121">Ancak, özel depoları veya diğer üçüncü taraf paketleri Azure tablo depolama, DocumentDB veya diğer konumlardan kimlik bilgilerini depolamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e1033-121">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, DocumentDB, or other locations.</span></span>

<span data-ttu-id="e1033-122">Aşağıdaki kod, seçilen kullanıcı hesabı kimlik doğrulaması ile ASP.NET Core Web uygulaması proje şablonu alınır.</span><span class="sxs-lookup"><span data-stu-id="e1033-122">The following code is taken from the ASP.NET Core Web Application project template with individual user account authentication selected.</span></span> <span data-ttu-id="e1033-123">Bu, ASP.NET Core EntityFramework.Core Startup.ConfigureServices yöntemiyle kimliğini yapılandırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1033-123">It shows how to configure ASP.NET Core Identity using EntityFramework.Core in the Startup.ConfigureServices method.</span></span>

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

<span data-ttu-id="e1033-124">ASP.NET Core kimliği yapılandırıldıktan sonra çağıran uygulama tarafından etkinleştirin. Hizmetin Startup.Configure yönteminde UseIdentity.</span><span class="sxs-lookup"><span data-stu-id="e1033-124">Once ASP.NET Core Identity is configured, you enable it by calling app.UseIdentity in the service’s Startup.Configure method.</span></span>

<span data-ttu-id="e1033-125">ASP.NET Core kimliği kullanarak çeşitli senaryolara olanak tanır:</span><span class="sxs-lookup"><span data-stu-id="e1033-125">Using ASP.NET Core Identity enables several scenarios:</span></span>

-   <span data-ttu-id="e1033-126">Yeni kullanıcı bilgilerini UserManager türü (userManager.CreateAsync) kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e1033-126">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

-   <span data-ttu-id="e1033-127">Kullanıcılar SignInManager türü kullanılarak kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="e1033-127">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="e1033-128">SignInManager.SignInAsync doğrudan oturum açmak için kullanabileceğiniz veya kullanıcının parolasını onaylamak için signInManager.PasswordSignInAsync doğru olduğundan ve bunları oturum açın.</span><span class="sxs-lookup"><span data-stu-id="e1033-128">You can use signInManager.SignInAsync to sign in directly, or signInManager.PasswordSignInAsync to confirm the user’s password is correct and then sign them in.</span></span>

-   <span data-ttu-id="e1033-129">İstekler bir tarayıcıdan oturum açmış kullanıcının kimlik ve talep içerecektir (Bu, ASP.NET Core kimliği ara yazılımı tarafından okunur) bir tanımlama bilgisinde depolanan bilgilere dayanarak bir kullanıcıya belirleyin.</span><span class="sxs-lookup"><span data-stu-id="e1033-129">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="e1033-130">ASP.NET Core kimliği de destekler [iki öğeli kimlik doğrulama](https://docs.microsoft.com/aspnet/core/security/authentication/2fa).</span><span class="sxs-lookup"><span data-stu-id="e1033-130">ASP.NET Core Identity also supports [two-factor authentication](https://docs.microsoft.com/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="e1033-131">ASP.NET Core kimliği olun kimlik doğrulama senaryoları bir yerel kullanıcı veri deposunu kullanın ve kimlik (MVC web uygulamaları için tipik olduğu gibi) tanımlama bilgilerini kullanarak istekleri arasında kalıcı hale getirmek için önerilen bir çözümdür.</span><span class="sxs-lookup"><span data-stu-id="e1033-131">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

## <a name="authenticating-using-external-providers"></a><span data-ttu-id="e1033-132">Dış sağlayıcıları kullanarak kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="e1033-132">Authenticating using external providers</span></span>

<span data-ttu-id="e1033-133">ASP.NET Core da destekler kullanarak [Dış kimlik doğrulama sağlayıcıları](https://docs.microsoft.com/aspnet/core/security/authentication/social/) aracılığıyla oturum açmasına izin vermek için [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) akışlar.</span><span class="sxs-lookup"><span data-stu-id="e1033-133">ASP.NET Core also supports using [external authentication providers](https://docs.microsoft.com/aspnet/core/security/authentication/social/) to let users log in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="e1033-134">Bu, kullanıcıların mevcut kimlik doğrulama işlemi Microsoft, Google, Facebook veya Twitter gibi sağlayıcılarından kullanarak oturum açın ve ASP.NET Core kimliği uygulamanızda kimliklerle ilişkilendirme anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e1033-134">This means that users can log in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="e1033-135">Dış kimlik doğrulama kullanmak için uygulamanızın HTTP isteği ardışık düzen işleme uygun yetkilendirme Ara yazılımının dahil edin.</span><span class="sxs-lookup"><span data-stu-id="e1033-135">To use external authentication, you include the appropriate authentication middleware in your application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="e1033-136">Bu ara yazılım kimlik sağlayıcısındaki kimlik bilgilerini yakalama ve SignInManager.GetExternalLoginInfo yöntemi aracılığıyla kullanılabilir hale getirme URI yolları döndürülecek işleme isteklerinin sorumludur.</span><span class="sxs-lookup"><span data-stu-id="e1033-136">This middleware is responsible for handling requests to return URI routes from the authentication provider, capturing identity information, and making it available via the SignInManager.GetExternalLoginInfo method.</span></span>

<span data-ttu-id="e1033-137">Yaygın Dış kimlik doğrulama sağlayıcıları ve ilişkili NuGet paketlerinin aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e1033-137">Popular external authentication providers and their associated NuGet packages are shown below.</span></span>

<span data-ttu-id="e1033-138">**Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount</span><span class="sxs-lookup"><span data-stu-id="e1033-138">**Microsoft:** Microsoft.AspNetCore.Authentication.MicrosoftAccount</span></span>

<span data-ttu-id="e1033-139">**Google:** Microsoft.AspNetCore.Authentication.Google</span><span class="sxs-lookup"><span data-stu-id="e1033-139">**Google:** Microsoft.AspNetCore.Authentication.Google</span></span>

<span data-ttu-id="e1033-140">**Facebook:** Microsoft.AspNetCore.Authentication.Facebook</span><span class="sxs-lookup"><span data-stu-id="e1033-140">**Facebook:** Microsoft.AspNetCore.Authentication.Facebook</span></span>

<span data-ttu-id="e1033-141">**Twitter:** Microsoft.AspNetCore.Authentication.Twitter</span><span class="sxs-lookup"><span data-stu-id="e1033-141">**Twitter:** Microsoft.AspNetCore.Authentication.Twitter</span></span>

<span data-ttu-id="e1033-142">Her durumda, ara yazılım uygulamasına benzer bir kayıt yöntemi çağrısı ile kaydedilir. Kimlik doğrulaması Startup.Configure {ExternalProvider} kullanın.</span><span class="sxs-lookup"><span data-stu-id="e1033-142">In all cases, the middleware is registered with a call to a registration method similar to app.Use{ExternalProvider}Authentication in Startup.Configure.</span></span> <span data-ttu-id="e1033-143">Bu kayıt yöntemleri bir uygulama kimliği ve gizli bilgi içeren bir seçenekler nesne alır (parola örneği için), sağlayıcı tarafından gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="e1033-143">These registration methods take an options object that contains an application ID and secret information (a password, for instance), as needed by the provider.</span></span> <span data-ttu-id="e1033-144">Dış kimlik doğrulama sağlayıcıları uygulamanın kayıtlı olması gerekir (açıklandığı şekilde [ASP.NET Core belgeleri](https://docs.microsoft.com/aspnet/core/security/authentication/social/)), böylece hangi uygulama kimliklerini erişim isteyen kullanıcı bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1033-144">External authentication providers require the application to be registered (as explained in [ASP.NET Core documentation](https://docs.microsoft.com/aspnet/core/security/authentication/social/)) so that they can inform the user what application is requesting access to their identity.</span></span>

<span data-ttu-id="e1033-145">Ara yazılım Startup.Configure kaydedildiğinde, kullanıcıların herhangi bir denetleyici eylemden oturum isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="e1033-145">Once the middleware is registered in Startup.Configure, you can prompt users to log in from any controller action.</span></span> <span data-ttu-id="e1033-146">Bunu yapmak için kimlik doğrulama sağlayıcısının adını ve bir yeniden yönlendirme URL'sini içeren bir AuthenticationProperties nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e1033-146">To do this, you create an AuthenticationProperties object that includes the authentication provider’s name and a redirect URL.</span></span> <span data-ttu-id="e1033-147">Ardından AuthenticationProperties nesneyi de iletir bir sınama yanıtı döndürür.</span><span class="sxs-lookup"><span data-stu-id="e1033-147">You then return a Challenge response that passes the AuthenticationProperties object.</span></span> <span data-ttu-id="e1033-148">Aşağıdaki kod, bunun bir örneğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1033-148">The following code shows an example of this.</span></span>

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

<span data-ttu-id="e1033-149">Kullanıcı kimliğini doğrulamasından sonra dış sağlayıcı yönlendirmek URL redirectUrl parametresi içerir.</span><span class="sxs-lookup"><span data-stu-id="e1033-149">The redirectUrl parameter includes the URL that the external provider should redirect to once the user has authenticated.</span></span> <span data-ttu-id="e1033-150">URL, kullanıcı aşağıdaki Basitleştirilmiş örnekte olduğu gibi bir dış kimlik bilgilerine dayalı oturum açacak bir eylem göstermelidir:</span><span class="sxs-lookup"><span data-stu-id="e1033-150">The URL should represent an action that will sign the user in based on external identity information, as in the following simplified example:</span></span>

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

<span data-ttu-id="e1033-151">Seçerseniz **bireysel kullanıcı hesabı** Visual Studio'da bir dış sağlayıcısı ile oturum açmak için gerekli tüm kodlar kod ASP.NET web uygulaması projesi oluşturduğunuzda, kimlik doğrulaması seçeneği olan zaten projede gösterildiği gibi Şekil 11 – 3 '.</span><span class="sxs-lookup"><span data-stu-id="e1033-151">If you choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, all the code necessary to sign in with an external provider is already in the project, as shown in Figure 11-3.</span></span>

![https://msdnshared.blob.core.windows.net/media/2016/10/new-web-app.png](./media/image3.png)

<span data-ttu-id="e1033-152">**Şekil 11-3**.</span><span class="sxs-lookup"><span data-stu-id="e1033-152">**Figure 11-3**.</span></span> <span data-ttu-id="e1033-153">Bir web uygulaması projesi oluştururken, dış kimlik doğrulama kullanmak için bir seçeneği</span><span class="sxs-lookup"><span data-stu-id="e1033-153">Selecting an option for using external authentication when creating a web application project</span></span>

<span data-ttu-id="e1033-154">Ek olarak bir dış kimlik doğrulama sağlayıcıları daha önce üçüncü taraf paketlerini listelenen çok fazla dış kimlik doğrulama sağlayıcıları için bir ara yazılım sağladığınız kullanılabilir durumdadır.</span><span class="sxs-lookup"><span data-stu-id="e1033-154">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="e1033-155">Bir liste için bkz. [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) github deposu.</span><span class="sxs-lookup"><span data-stu-id="e1033-155">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repo on GitHub.</span></span>

<span data-ttu-id="e1033-156">Bu da Elbette, kendi dış kimlik doğrulaması ara yazılımı oluşturmak için mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e1033-156">It is also possible, of course, to create your own external authentication middleware.</span></span>

## <a name="authenticating-with-bearer-tokens"></a><span data-ttu-id="e1033-157">Taşıyıcı belirteçleri ile kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="e1033-157">Authenticating with bearer tokens</span></span>

<span data-ttu-id="e1033-158">ASP.NET Core kimliği (veya kimlik ve Dış kimlik doğrulama sağlayıcıları ile) kimlik doğrulaması, kullanıcı bilgileri depolayan bir tanımlama bilgisinde uygun olduğu da birçok web uygulama senaryoları için çalışır.</span><span class="sxs-lookup"><span data-stu-id="e1033-158">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="e1033-159">Diğer senaryolarda, ancak tanımlama bilgilerini kalıcı hale getirmeniz ve veri aktarımı doğal bir yol değildir.</span><span class="sxs-lookup"><span data-stu-id="e1033-159">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="e1033-160">Örneğin, bir ASP.NET Core Web API'si yerel istemciler tarafından tek sayfa uygulamaları (Spa'lar) tarafından erişilebilen bir RESTful uç noktalarını kullanıma sunan veya hatta diğer Web API'leri tarafından genellikle taşıyıcı belirteci kimlik doğrulaması yerine kullanmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="e1033-160">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="e1033-161">Bu tür uygulamalar değil tanımlama bilgileriyle çalışır ancak kolayca bir taşıyıcı belirteç alabilir ve sonraki istekleri yetkilendirme üst bilgisi içerir.</span><span class="sxs-lookup"><span data-stu-id="e1033-161">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="e1033-162">Belirteç kimlik doğrulamasını etkinleştirmek için ASP.NET Core çeşitli seçenekler kullanmak için destekleyen [OAuth 2.0](https://oauth.net/2/) ve [Openıd Connect](https://openid.net/connect/).</span><span class="sxs-lookup"><span data-stu-id="e1033-162">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

## <a name="authenticating-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="e1033-163">Bir Openıd Connect veya OAuth 2.0 kimlik sağlayıcısı ile kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="e1033-163">Authenticating with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="e1033-164">Azure Active Directory veya Openıd Connect veya OAuth 2.0 destekleyen başka bir kimlik çözümü depolanan kullanıcı bilgileri, iş akışının Openıd Connect kullanarak kimlik doğrulaması için Microsoft.AspNetCore.Authentication.OpenIdConnect paketi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1033-164">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the Microsoft.AspNetCore.Authentication.OpenIdConnect package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="e1033-165">Örneğin, [Azure Active Directory'de kimlik doğrulaması](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/), aşağıdaki örnekte gösterildiği gibi bir ASP.NET Core web uygulaması ara yazılım bu paketten kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e1033-165">For example, to [authenticate against Azure Active Directory](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/), an ASP.NET Core web application can use middleware from that package as shown in the following example:</span></span>

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

<span data-ttu-id="e1033-166">Yapılandırma değerleri, uygulamanız olduğunda, oluşturulan Azure Active Directory değerler [bir Azure AD istemci olarak kayıtlı](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad).</span><span class="sxs-lookup"><span data-stu-id="e1033-166">The configuration values are Azure Active Directory values that are created when your application is [registered as an Azure AD client](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad).</span></span> <span data-ttu-id="e1033-167">Tüm Azure Active Directory aracılığıyla kimliği doğrulanmış kullanıcılar kimliklerini doğrulaması gerekiyorsa tek bir istemci kimliği bir uygulamada birden fazla mikro hizmetler arasında paylaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="e1033-167">A single client ID can be shared among multiple microservices in an application if they all need to authenticate users authenticated via Azure Active Directory.</span></span>

<span data-ttu-id="e1033-168">Tüm kullanıcı bilgileri depolama ve kimlik doğrulaması gerçekleştirilir çünkü Azure Active Directory tarafından bu iş akışını kullanırken, ASP.NET Core kimliği ara yazılımı gerekli olmadığını, unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e1033-168">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by Azure Active Directory.</span></span>

## <a name="issuing-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="e1033-169">Bir ASP.NET Core hizmeti güvenlik belirteçleri verme</span><span class="sxs-lookup"><span data-stu-id="e1033-169">Issuing security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="e1033-170">Yerel ASP.NET Core kimliği kullanıcılar için güvenlik belirteçlerini vermek tercih ettiğiniz yerine, bir dış kimlik sağlayıcısı kullanarak, bazı iyi üçüncü taraf kitaplıklar avantajlarından yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1033-170">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="e1033-171">[Identityserver4](https://github.com/IdentityServer/IdentityServer4) ve [OpenIddict](https://github.com/openiddict/openiddict-core) Openıd Connect sağlayıcılar, ASP.NET Core kimliği ile izin verecek şekilde güvenlik belirteçleri bir ASP.NET Core hizmeti kolayca tümleştirin.</span><span class="sxs-lookup"><span data-stu-id="e1033-171">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="e1033-172">[Identityserver4 belgeleri](https://identityserver4.readthedocs.io/en/release/) kitaplığı kullanmak için ayrıntılı yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="e1033-172">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/release/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="e1033-173">Ancak, Identityserver4 sorunu belirteçleri kullanarak için temel adımlar şunlardır.</span><span class="sxs-lookup"><span data-stu-id="e1033-173">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1.  <span data-ttu-id="e1033-174">Uygulama çağırırsınız. Identityserver4 uygulamanın HTTP istek işleme ardışık düzenine eklemek için UseIdentityServer Startup.Configure yöntem.</span><span class="sxs-lookup"><span data-stu-id="e1033-174">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="e1033-175">Bu kitaplık OAuth2 uç noktaları /connect/token gibi Openıd Connect ve isteklere hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1033-175">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2.  <span data-ttu-id="e1033-176">Identityserver4 Hizmetleri çağrısı yaparak Startup.ConfigureServices içinde yapılandırın. AddIdentityServer.</span><span class="sxs-lookup"><span data-stu-id="e1033-176">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3.  <span data-ttu-id="e1033-177">Kimlik sunucusu, aşağıdaki veriler sağlayarak yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="e1033-177">You configure identity server by providing the following data:</span></span>

-   <span data-ttu-id="e1033-178">[Kimlik bilgilerini](https://identityserver4.readthedocs.io/en/release/topics/crypto.html) imzalama için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="e1033-178">The [credentials](https://identityserver4.readthedocs.io/en/release/topics/crypto.html) to use for signing.</span></span>

-   <span data-ttu-id="e1033-179">[Kimlik ve API kaynaklarına](https://identityserver4.readthedocs.io/en/release/topics/resources.html) kullanıcılar için erişim isteyebilir:</span><span class="sxs-lookup"><span data-stu-id="e1033-179">The [Identity and API resources](https://identityserver4.readthedocs.io/en/release/topics/resources.html) that users might request access to:</span></span>

<!-- -->

-   <span data-ttu-id="e1033-180">API kaynaklarını korumalı veriler veya bir erişim belirteci ile bir kullanıcının erişebildiği işlevleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e1033-180">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="e1033-181">Örnek bir API kaynağı bir web API (veya API kümesi) verilebilir yetkilendirme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e1033-181">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

-   <span data-ttu-id="e1033-182">Kimlik kaynaklarını bir kullanıcıyı tanımlamak için bir istemci için verilen bilgileri (talep) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e1033-182">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="e1033-183">Talepler, kullanıcı adı, e-posta adresi vb. içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e1033-183">The claims might include the user name, email address, and so on.</span></span>

<!-- -->

-   <span data-ttu-id="e1033-184">[İstemcileri](https://identityserver4.readthedocs.io/en/release/topics/clients.html) , bağlama belirteci istemek için.</span><span class="sxs-lookup"><span data-stu-id="e1033-184">The [clients](https://identityserver4.readthedocs.io/en/release/topics/clients.html) that will be connecting in order to request tokens.</span></span>

-   <span data-ttu-id="e1033-185">Kullanıcı bilgileri depolama mekanizması gibi [ASP.NET Core kimliği](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) veya alternatif.</span><span class="sxs-lookup"><span data-stu-id="e1033-185">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/release/quickstarts/6_aspnet_identity.html) or an alternative.</span></span>

<span data-ttu-id="e1033-186">İstemcileri ve Identityserver4 kaynakları kullanmak için belirttiğinizde, bir IEnumerable geçirebilirsiniz&lt;T&gt; bellek içi istemci veya kaynak depolarını ele yöntemleri için uygun türde bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="e1033-186">When you specify clients and resources for IdentityServer4 to use, you can pass an IEnumerable&lt;T&gt; collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="e1033-187">Veya daha karmaşık senaryolarda, istemci veya kaynak sağlayıcısı türleri aracılığıyla bağımlılık ekleme sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="e1033-187">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="e1033-188">Identityserver4 bellek içi kaynaklar ve istemcilere özel bir IClientStore türü tarafından sağlanan kullanmak için örnek bir yapılandırma aşağıdaki örnekteki gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="e1033-188">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

## <a name="consuming-security-tokens"></a><span data-ttu-id="e1033-189">Güvenlik belirteçleri kullanma</span><span class="sxs-lookup"><span data-stu-id="e1033-189">Consuming security tokens</span></span>

<span data-ttu-id="e1033-190">Bir Openıd Connect uç noktasına karşı kimlik doğrulaması veya kendi güvenlik belirteçleri verme bazı senaryolar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e1033-190">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="e1033-191">Ancak ne yalnızca geçerli güvenliğe sahip kullanıcılara erişimi sınırlamak için gereken hizmet belirteçleri farklı bir hizmet tarafından sağlandı?</span><span class="sxs-lookup"><span data-stu-id="e1033-191">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="e1033-192">Bu senaryo için JWT belirteçlerini işler kimlik doğrulaması ara yazılımı Microsoft.AspNetCore.Authentication.JwtBearer pakette kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e1033-192">For that scenario, authentication middleware that handles JWT tokens is available in the Microsoft.AspNetCore.Authentication.JwtBearer package.</span></span> <span data-ttu-id="e1033-193">JWT anlamına gelen "[JSON Web belirteci](https://tools.ietf.org/html/rfc7519)" ve (RFC 7519 tarafından tanımlanan) ortak bir güvenlik belirteci biçimi güvenlik talepleri iletişim kurmak için.</span><span class="sxs-lookup"><span data-stu-id="e1033-193">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="e1033-194">Tür belirteçleri kullanmasını ara yazılımı kullanmak nasıl basit bir örneği aşağıdaki örnekteki gibi görünebilir.</span><span class="sxs-lookup"><span data-stu-id="e1033-194">A simple example of how to use middleware to consume such tokens might look like the following example.</span></span> <span data-ttu-id="e1033-195">Bu kod (uygulama. ASP.NET Core MVC Ara çağrıları önce gelmelidir UseMvc).</span><span class="sxs-lookup"><span data-stu-id="e1033-195">This code must precede calls to ASP.NET Core MVC middleware (app.UseMvc).</span></span>

```csharp
app.UseJwtBearerAuthentication(new JwtBearerOptions()
{
    Audience = "http://localhost:5001/",
    Authority = "http://localhost:5000/",
    AutomaticAuthenticate = true
});
```

<span data-ttu-id="e1033-196">Bu kullanımı Parametreler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e1033-196">The parameters in this usage are:</span></span>

-   <span data-ttu-id="e1033-197">İzleyici, gelen belirteci veya erişim belirteci verir kaynak alıcısı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e1033-197">Audience represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="e1033-198">Bu parametrede belirtilen değer belirteci aud parametresinde eşleşmiyorsa, belirteç reddedilir.</span><span class="sxs-lookup"><span data-stu-id="e1033-198">If the value specified in this parameter does not match the aud parameter in the token, the token will be rejected.</span></span>

-   <span data-ttu-id="e1033-199">Yetki belirteci verilirken kimlik doğrulaması sunucusunun adresidir.</span><span class="sxs-lookup"><span data-stu-id="e1033-199">Authority is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="e1033-200">JWT taşıyıcı kimlik doğrulaması ara yazılımı, belirtecin imzayı doğrulamak için kullanılacak ortak anahtarı almak için bu URI kullanır.</span><span class="sxs-lookup"><span data-stu-id="e1033-200">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="e1033-201">Ara yazılım ayrıca belirteç ISS parametresinde bu URI eşleştiğini doğrular.</span><span class="sxs-lookup"><span data-stu-id="e1033-201">The middleware also confirms that the iss parameter in the token matches this URI.</span></span>

-   <span data-ttu-id="e1033-202">AutomaticAuthenticate belirteci tarafından tanımlanan kullanıcı otomatik olarak imzalanması gerektiğini olup olmadığını gösteren bir Boole değeridir.</span><span class="sxs-lookup"><span data-stu-id="e1033-202">AutomaticAuthenticate is a Boolean value that indicates whether the user defined by the token should be automatically signed in.</span></span>

<span data-ttu-id="e1033-203">Başka bir parametre, RequireHttpsMetadata, bu örnekte kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="e1033-203">Another parameter, RequireHttpsMetadata, is not used in this example.</span></span> <span data-ttu-id="e1033-204">Test amacıyla kullanışlıdır. Böylece ortamlarında test, bu parametre false olarak nerede sertifikası olmayan ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e1033-204">It is useful for testing purposes; you set this parameter to false so that you can test in environments where you do not have certificates.</span></span> <span data-ttu-id="e1033-205">Gerçek dağıtımlarda, JWT taşıyıcı belirteçlerini her zaman yalnızca HTTPS üzerinden geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e1033-205">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="e1033-206">Yerinde bu ara yazılım ile JWT belirteçleri yetkilendirme üst bilgiler otomatik olarak çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="e1033-206">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="e1033-207">Bunlar daha sonra seri durumdan, (hedef kitle ve yetkilisi parametrelerinin değerleri kullanarak) ve MVC eylemler veya yetkilendirme filtrelerini daha sonra başvurulmak üzere kullanıcı bilgilerini olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="e1033-207">They are then deserialized, validated (using the values in the Audience and Authority parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="e1033-208">JWT taşıyıcı kimlik doğrulaması ara yazılımı yerel bir sertifika yetkilisi kullanılabilir değilse, bir belirteci doğrulamak için kullanma gibi daha gelişmiş senaryoları da destekler.</span><span class="sxs-lookup"><span data-stu-id="e1033-208">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="e1033-209">Bu senaryo için JwtBearerOptions nesnesinde bir tokenvalidationparameters değerini nesnesi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1033-209">For this scenario, you can specify a TokenValidationParameters object in the JwtBearerOptions object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e1033-210">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="e1033-210">Additional resources</span></span>

-   <span data-ttu-id="e1033-211">**Tanımlama bilgilerini uygulamalar arasında paylaşma**
    [*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sharing-authentication-cookies-between-applications*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)</span><span class="sxs-lookup"><span data-stu-id="e1033-211">**Sharing cookies between applications**
[*https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing\#sharing-authentication-cookies-between-applications*](https://docs.microsoft.com/aspnet/core/security/data-protection/compatibility/cookie-sharing#sharing-authentication-cookies-between-applications)</span></span>

-   <span data-ttu-id="e1033-212">**Kimliğe giriş**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span><span class="sxs-lookup"><span data-stu-id="e1033-212">**Introduction to Identity**
[*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span></span>

-   <span data-ttu-id="e1033-213">**Rick Anderson. SMS ile iki öğeli kimlik doğrulama**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)</span><span class="sxs-lookup"><span data-stu-id="e1033-213">**Rick Anderson. Two-factor authentication with SMS**
[*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](https://docs.microsoft.com/aspnet/core/security/authentication/2fa)</span></span>

-   <span data-ttu-id="e1033-214">**Facebook, Google ve diğer dış sağlayıcıları kullanarak kimlik doğrulamayı etkinleştirme**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)</span><span class="sxs-lookup"><span data-stu-id="e1033-214">**Enabling authentication using Facebook, Google and other external providers**
[*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](https://docs.microsoft.com/aspnet/core/security/authentication/social/)</span></span>

-   <span data-ttu-id="e1033-215">**Michell Anicas. OAuth 2 giriş**
    [*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)</span><span class="sxs-lookup"><span data-stu-id="e1033-215">**Michell Anicas. An Introduction to OAuth 2**
[*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)</span></span>

-   <span data-ttu-id="e1033-216">**AspNet.Security.OAuth.Providers** (ASP.NET OAuth sağlayıcıları için GitHub deposunu.</span><span class="sxs-lookup"><span data-stu-id="e1033-216">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers.</span></span>
    [*https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src*](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

-   <span data-ttu-id="e1033-217">**Danny Strockis. Azure AD'yi bir ASP.NET Core web uygulamasıyla tümleştirme**
    [*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)</span><span class="sxs-lookup"><span data-stu-id="e1033-217">**Danny Strockis. Integrating Azure AD into an ASP.NET Core web app**
[*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)</span></span>

-   <span data-ttu-id="e1033-218">**Identityserver4. Resmi belgeleri**
    [*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)</span><span class="sxs-lookup"><span data-stu-id="e1033-218">**IdentityServer4. Official documentation**
[*https://identityserver4.readthedocs.io/en/release/*](https://identityserver4.readthedocs.io/en/release/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="e1033-219">[Önceki](../implement-resilient-applications/monitor-app-health.md)
[İleri](authorization-net-microservices-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="e1033-219">[Previous](../implement-resilient-applications/monitor-app-health.md)
[Next](authorization-net-microservices-web-applications.md)</span></span>
