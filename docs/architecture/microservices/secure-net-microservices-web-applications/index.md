---
title: .NET mikro hizmetleri ve Web uygulamalarının güvenliğini sağlama
description: .NET mikro hizmetleri ve Web uygulamalarında güvenlik-ASP.NET Core Web uygulamalarında kimlik doğrulama seçeneklerini öğrenin.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: f405b4199e8239e86c4799a649c3d87811d99828
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798847"
---
# <a name="make-secure-net-microservices-and-web-applications"></a><span data-ttu-id="4fa10-103">Güvenli .NET mikro hizmetleri ve Web uygulamaları oluşturun</span><span class="sxs-lookup"><span data-stu-id="4fa10-103">Make secure .NET Microservices and Web Applications</span></span>

<span data-ttu-id="4fa10-104">Mikro hizmetlerde ve Web uygulamalarında güvenlikle ilgili olarak konunun bu şekilde birçok kitap alabilmesini sağlayacak pek çok konu vardır. Bu bölümde, kimlik doğrulama, yetkilendirme ve uygulama gizliliklerine odaklanacağız.</span><span class="sxs-lookup"><span data-stu-id="4fa10-104">There are so many aspects about security in microservices and web applications that the topic could easy take several books like this one so, in this section, we'll focus on authentication, authorization, and application secrets.</span></span>

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a><span data-ttu-id="4fa10-105">.NET mikro hizmetleri ve Web uygulamalarında kimlik doğrulaması uygulama</span><span class="sxs-lookup"><span data-stu-id="4fa10-105">Implement authentication in .NET microservices and web applications</span></span>

<span data-ttu-id="4fa10-106">Genellikle bir hizmet tarafından yayımlanan kaynakların ve API 'Lerin belirli Güvenilen Kullanıcı veya istemcilerle sınırlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-106">It's often necessary for resources and APIs published by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="4fa10-107">Bu tür API düzeyi güven kararlarını yapmanın ilk adımı kimlik doğrulamadır.</span><span class="sxs-lookup"><span data-stu-id="4fa10-107">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="4fa10-108">Kimlik doğrulaması, bir kullanıcının kimliğini güvenilir bir şekilde doğrulama işlemidir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-108">Authentication is the process of reliably verify a user’s identity.</span></span>

<span data-ttu-id="4fa10-109">Mikro hizmet senaryolarında, kimlik doğrulaması genellikle merkezi olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-109">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="4fa10-110">Bir API ağ geçidi kullanıyorsanız, Şekil 9-1 ' de gösterildiği gibi ağ geçidi kimlik doğrulaması için iyi bir yerdir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-110">If you're using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 9-1.</span></span> <span data-ttu-id="4fa10-111">Bu yaklaşımı kullanırsanız, ağ geçidinden gelen veya olmayan iletilerin kimlik doğrulamasını yapmak için ek bir güvenlik yoksa, tek tek mikro hizmetlere doğrudan ulaşılamadığından emin olun (API ağ geçidi olmadan).</span><span class="sxs-lookup"><span data-stu-id="4fa10-111">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![API Gateway kimlik doğrulamasını merkezileştiren, istekleri mikro hizmetlere iletirken Kullanıcı bilgilerini ekler.](./media/image1.png)

<span data-ttu-id="4fa10-113">**Şekil 9-1**.</span><span class="sxs-lookup"><span data-stu-id="4fa10-113">**Figure 9-1**.</span></span> <span data-ttu-id="4fa10-114">API ağ geçidiyle merkezi kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="4fa10-114">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="4fa10-115">Hizmetlere doğrudan erişilemiyorsa, kullanıcıların kimliğini doğrulamak için Azure Active Directory gibi bir kimlik doğrulama hizmeti veya güvenlik belirteci hizmeti (STS) görevi gören ayrılmış bir kimlik doğrulama mikro hizmeti kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-115">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="4fa10-116">Güven kararları, güvenlik belirteçleri veya tanımlama bilgileriyle hizmetler arasında paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="4fa10-116">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="4fa10-117">(Bu belirteçler, gerekirse [tanımlama bilgisi paylaşımı](/aspnet/core/security/cookie-sharing)uygulayarak ASP.NET Core uygulamalar arasında paylaşılabilir.) Bu model Şekil 9-2 ' de gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-117">(These tokens can be shared between ASP.NET Core applications, if needed, by implementing [cookie sharing](/aspnet/core/security/cookie-sharing).) This pattern is illustrated in Figure 9-2.</span></span>

![Mikro hizmetlere doğrudan erişildiğinde, kimlik doğrulaması ve yetkilendirme içeren güven, mikro hizmetler arasında paylaşılan bir özel mikro hizmet tarafından verilen bir güvenlik belirteci tarafından işlenir.](./media/image2.png)

<span data-ttu-id="4fa10-119">**Şekil 9-2**.</span><span class="sxs-lookup"><span data-stu-id="4fa10-119">**Figure 9-2**.</span></span> <span data-ttu-id="4fa10-120">Kimlik mikro hizmetine göre kimlik doğrulaması; güven, bir yetkilendirme belirteci kullanılarak paylaşılır</span><span class="sxs-lookup"><span data-stu-id="4fa10-120">Authentication by identity microservice; trust is shared using an authorization token</span></span>

### <a name="authenticate-with-aspnet-core-identity"></a><span data-ttu-id="4fa10-121">ASP.NET Core kimliğiyle kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="4fa10-121">Authenticate with ASP.NET Core Identity</span></span>

<span data-ttu-id="4fa10-122">Bir uygulamanın kullanıcılarını tanımlamak için ASP.NET Core birincil mekanizması [ASP.NET Core kimlik](/aspnet/core/security/authentication/identity) üyelik sistemidir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-122">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="4fa10-123">ASP.NET Core kimlik, geliştirici tarafından yapılandırılan bir veri deposundaki kullanıcı bilgilerini (oturum açma bilgileri, roller ve talepler dahil) depolar.</span><span class="sxs-lookup"><span data-stu-id="4fa10-123">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="4fa10-124">Genellikle, ASP.NET Core Identity veri deposu `Microsoft.AspNetCore.Identity.EntityFrameworkCore` paketinde sunulan bir Entity Framework deposudur.</span><span class="sxs-lookup"><span data-stu-id="4fa10-124">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` package.</span></span> <span data-ttu-id="4fa10-125">Ancak, Azure Tablo depolama, CosmosDB veya diğer konumlarda kimlik bilgilerini depolamak için özel mağazalar veya diğer üçüncü taraf paketleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-125">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, CosmosDB, or other locations.</span></span>

<span data-ttu-id="4fa10-126">Aşağıdaki kod, bireysel kullanıcı hesabı kimlik doğrulaması seçili olan ASP.NET Core Web uygulaması proje şablonundan alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="4fa10-126">The following code is taken from the ASP.NET Core Web Application project template with individual user account authentication selected.</span></span> <span data-ttu-id="4fa10-127">Başlangıç. ConfigureServices yönteminde EntityFramework. Core kullanılarak ASP.NET Core kimliğin nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-127">It shows how to configure ASP.NET Core Identity using EntityFramework.Core in the Startup.ConfigureServices method.</span></span>

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

<span data-ttu-id="4fa10-128">ASP.NET Core kimlik yapılandırıldıktan sonra, uygulamayı çağırarak etkinleştirin. Hizmetin `Startup.Configure` yönteminde Useıdentity.</span><span class="sxs-lookup"><span data-stu-id="4fa10-128">Once ASP.NET Core Identity is configured, you enable it by calling app.UseIdentity in the service’s `Startup.Configure` method.</span></span>

<span data-ttu-id="4fa10-129">ASP.NET Core kimlik kullanmak çeşitli senaryolara izin vermez:</span><span class="sxs-lookup"><span data-stu-id="4fa10-129">Using ASP.NET Core Identity enables several scenarios:</span></span>

- <span data-ttu-id="4fa10-130">UserManager türünü (userManager. CreateAsync) kullanarak yeni kullanıcı bilgileri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4fa10-130">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

- <span data-ttu-id="4fa10-131">SignInManager türünü kullanarak kullanıcıların kimliğini doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="4fa10-131">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="4fa10-132">Doğrudan oturum açmak için `signInManager.SignInAsync` kullanabilir veya kullanıcının parolasının doğru olduğunu doğrulamak için `signInManager.PasswordSignInAsync` ve sonra da oturum açın.</span><span class="sxs-lookup"><span data-stu-id="4fa10-132">You can use `signInManager.SignInAsync` to sign in directly, or `signInManager.PasswordSignInAsync` to confirm the user’s password is correct and then sign them in.</span></span>

- <span data-ttu-id="4fa10-133">Bir tarayıcıdan gelen isteklerin, oturum açan kullanıcının kimlik ve taleplerini içermesi için bir tanımlama bilgisinde depolanan (ASP.NET Core Identity ara yazılımı tarafından okunan) bilgileri temel alan bir kullanıcıyı tanımlama.</span><span class="sxs-lookup"><span data-stu-id="4fa10-133">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="4fa10-134">ASP.NET Core kimlik [iki öğeli kimlik doğrulamasını](/aspnet/core/security/authentication/2fa)da destekler.</span><span class="sxs-lookup"><span data-stu-id="4fa10-134">ASP.NET Core Identity also supports [two-factor authentication](/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="4fa10-135">Yerel bir kullanıcı veri deposunu kullanan ve tanımlama bilgilerini kullanarak istekler arasında kimlik (MVC web uygulamaları için tipik olarak) tutan kimlik doğrulama senaryolarında, ASP.NET Core kimlik önerilen bir çözümdür.</span><span class="sxs-lookup"><span data-stu-id="4fa10-135">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

### <a name="authenticate-with-external-providers"></a><span data-ttu-id="4fa10-136">Dış sağlayıcılarla kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="4fa10-136">Authenticate with external providers</span></span>

<span data-ttu-id="4fa10-137">ASP.NET Core Ayrıca, kullanıcıların [OAuth 2,0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) akışları aracılığıyla oturum açmasını sağlamak için [dış kimlik doğrulama sağlayıcılarının](/aspnet/core/security/authentication/social/) kullanılmasını da destekler.</span><span class="sxs-lookup"><span data-stu-id="4fa10-137">ASP.NET Core also supports using [external authentication providers](/aspnet/core/security/authentication/social/) to let users sign in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="4fa10-138">Bu, kullanıcıların Microsoft, Google, Facebook veya Twitter gibi sağlayıcılardan mevcut kimlik doğrulama süreçlerini kullanarak oturum açabileceği ve bu kimlikleri uygulamanızdaki bir ASP.NET Core kimlikle ilişkilendirebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-138">This means that users can sign in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="4fa10-139">Dış kimlik doğrulamasını kullanmak için uygulamanızın HTTP istek işleme ardışık düzenine uygun kimlik doğrulama ara yazılımını dahil edersiniz.</span><span class="sxs-lookup"><span data-stu-id="4fa10-139">To use external authentication, you include the appropriate authentication middleware in your application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="4fa10-140">Bu ara yazılım, kimlik doğrulama sağlayıcısından URI yolları döndürmek, kimlik bilgilerini yakalamak ve SignInManager. Getexternalloginınfo yöntemi aracılığıyla kullanılabilir hale getirmek için istekleri işlemekten sorumludur.</span><span class="sxs-lookup"><span data-stu-id="4fa10-140">This middleware is responsible for handling requests to return URI routes from the authentication provider, capturing identity information, and making it available via the SignInManager.GetExternalLoginInfo method.</span></span>

<span data-ttu-id="4fa10-141">Popüler dış kimlik doğrulama sağlayıcıları ve bunlarla ilişkili NuGet paketleri aşağıdaki tabloda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4fa10-141">Popular external authentication providers and their associated NuGet packages are shown in the following table:</span></span>

| <span data-ttu-id="4fa10-142">**Sağlayıcısını**</span><span class="sxs-lookup"><span data-stu-id="4fa10-142">**Provider**</span></span>  | <span data-ttu-id="4fa10-143">**Paket**</span><span class="sxs-lookup"><span data-stu-id="4fa10-143">**Package**</span></span>                                          |
| ------------- | ---------------------------------------------------- |
| <span data-ttu-id="4fa10-144">**MICROSOFT**</span><span class="sxs-lookup"><span data-stu-id="4fa10-144">**Microsoft**</span></span> | <span data-ttu-id="4fa10-145">**Microsoft. AspNetCore. Authentication. MicrosoftAccount**</span><span class="sxs-lookup"><span data-stu-id="4fa10-145">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span></span> |
| <span data-ttu-id="4fa10-146">**Google**</span><span class="sxs-lookup"><span data-stu-id="4fa10-146">**Google**</span></span>    | <span data-ttu-id="4fa10-147">**Microsoft. AspNetCore. Authentication. Google**</span><span class="sxs-lookup"><span data-stu-id="4fa10-147">**Microsoft.AspNetCore.Authentication.Google**</span></span>           |
| <span data-ttu-id="4fa10-148">**'A**</span><span class="sxs-lookup"><span data-stu-id="4fa10-148">**Facebook**</span></span>  | <span data-ttu-id="4fa10-149">**Microsoft. AspNetCore. Authentication. Facebook**</span><span class="sxs-lookup"><span data-stu-id="4fa10-149">**Microsoft.AspNetCore.Authentication.Facebook**</span></span>         |
| <span data-ttu-id="4fa10-150">**Twitter**</span><span class="sxs-lookup"><span data-stu-id="4fa10-150">**Twitter**</span></span>   | <span data-ttu-id="4fa10-151">**Microsoft. AspNetCore. Authentication. Twitter**</span><span class="sxs-lookup"><span data-stu-id="4fa10-151">**Microsoft.AspNetCore.Authentication.Twitter**</span></span>          |

<span data-ttu-id="4fa10-152">Her durumda, ara yazılım `Startup.Configure``app.Use{ExternalProvider}Authentication` benzer bir kayıt yöntemi çağrısıyla kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-152">In all cases, the middleware is registered with a call to a registration method similar to `app.Use{ExternalProvider}Authentication` in `Startup.Configure`.</span></span> <span data-ttu-id="4fa10-153">Bu kayıt yöntemleri, sağlayıcının gerektirdiği şekilde uygulama KIMLIĞI ve gizli bilgiler (örneğin, bir parola) içeren bir seçenek nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="4fa10-153">These registration methods take an options object that contains an application ID and secret information (a password, for instance), as needed by the provider.</span></span> <span data-ttu-id="4fa10-154">Dış kimlik doğrulama sağlayıcıları, kullanıcıya hangi uygulamanın kimlik erişimi istediğini bildirmek için uygulamanın kaydolmasını ( [ASP.NET Core belgelerde](/aspnet/core/security/authentication/social/)açıklandığı gibi) gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-154">External authentication providers require the application to be registered (as explained in [ASP.NET Core documentation](/aspnet/core/security/authentication/social/)) so that they can inform the user what application is requesting access to their identity.</span></span>

<span data-ttu-id="4fa10-155">Ara yazılım `Startup.Configure`bir kez kaydolduktan sonra, kullanıcılardan herhangi bir denetleyici eyleminden oturum açmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fa10-155">Once the middleware is registered in `Startup.Configure`, you can prompt users to sign in from any controller action.</span></span> <span data-ttu-id="4fa10-156">Bunu yapmak için kimlik doğrulama sağlayıcısının adını ve yeniden yönlendirme URL 'sini içeren bir `AuthenticationProperties` nesnesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4fa10-156">To do this, you create an `AuthenticationProperties` object that includes the authentication provider’s name and a redirect URL.</span></span> <span data-ttu-id="4fa10-157">Daha sonra `AuthenticationProperties` nesnesini geçiren bir sınama yanıtı döndürün.</span><span class="sxs-lookup"><span data-stu-id="4fa10-157">You then return a Challenge response that passes the `AuthenticationProperties` object.</span></span> <span data-ttu-id="4fa10-158">Aşağıdaki kod buna bir örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-158">The following code shows an example of this.</span></span>

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

<span data-ttu-id="4fa10-159">RedirectUrl parametresi, kullanıcının kimliği doğrulandıktan sonra dış sağlayıcının yeniden yönlendirileceği URL 'YI içerir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-159">The redirectUrl parameter includes the URL that the external provider should redirect to once the user has authenticated.</span></span> <span data-ttu-id="4fa10-160">URL, aşağıdaki Basitleştirilmiş örnekte olduğu gibi, dış kimlik bilgilerine göre kullanıcıyı imzalayamayacak bir eylemi temsil etmelidir:</span><span class="sxs-lookup"><span data-stu-id="4fa10-160">The URL should represent an action that will sign the user in based on external identity information, as in the following simplified example:</span></span>

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

<span data-ttu-id="4fa10-161">Visual Studio 'da ASP.NET Code Web uygulaması projesini oluştururken **bireysel kullanıcı hesabı** kimlik doğrulaması seçeneğini belirlerseniz, Şekil 9-3 ' de gösterildiği gibi, bir dış sağlayıcı ile oturum açmak için gereken tüm kodlar zaten projede bulunur.</span><span class="sxs-lookup"><span data-stu-id="4fa10-161">If you choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, all the code necessary to sign in with an external provider is already in the project, as shown in Figure 9-3.</span></span>

![Yeni ASP.NET Core Web uygulamasına yönelik iletişim kutusu, kimlik doğrulamasını değiştirmek için düğmeyi vurgular.](./media/image3.png)

<span data-ttu-id="4fa10-163">**Şekil 9-3**.</span><span class="sxs-lookup"><span data-stu-id="4fa10-163">**Figure 9-3**.</span></span> <span data-ttu-id="4fa10-164">Web uygulaması projesi oluştururken dış kimlik doğrulaması kullanma seçeneği seçme</span><span class="sxs-lookup"><span data-stu-id="4fa10-164">Selecting an option for using external authentication when creating a web application project</span></span>

<span data-ttu-id="4fa10-165">Daha önce listelenen dış kimlik doğrulama sağlayıcılarının yanı sıra, birçok daha fazla dış kimlik doğrulama sağlayıcısının kullanılmasına yönelik ara yazılım sağlayan üçüncü taraf paketleri de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="4fa10-165">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="4fa10-166">Bir liste için bkz. GitHub 'da [Aspnet. Security. OAuth. Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) deposu.</span><span class="sxs-lookup"><span data-stu-id="4fa10-166">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repo on GitHub.</span></span>

<span data-ttu-id="4fa10-167">Ayrıca, özel ihtiyaçları çözümlemek için kendi dış kimlik doğrulama ara yazılımını da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fa10-167">You can also create your own external authentication middleware to solve some special need.</span></span>

### <a name="authenticate-with-bearer-tokens"></a><span data-ttu-id="4fa10-168">Taşıyıcı belirteçleriyle kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="4fa10-168">Authenticate with bearer tokens</span></span>

<span data-ttu-id="4fa10-169">ASP.NET Core kimliği (veya kimlik Plus dış kimlik doğrulama sağlayıcıları) ile kimlik doğrulaması, Kullanıcı bilgilerini bir tanımlama bilgisinde depolamanın uygun olduğu birçok Web uygulaması senaryosunda iyi çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="4fa10-169">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="4fa10-170">Diğer senaryolarda, tanımlama bilgileri kalıcı ve veri iletimi gibi doğal bir yöntem değildir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-170">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="4fa10-171">Örneğin, tek sayfalı uygulamalar (maça 'Lar) tarafından, yerel istemciler tarafından veya diğer Web API 'Leri tarafından erişilebilen yeniden kullanılabilir uç noktaları sunan bir ASP.NET Core Web API 'sinde, genellikle bunun yerine taşıyıcı belirteç kimlik doğrulamasını kullanmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="4fa10-171">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="4fa10-172">Bu tür uygulamalar tanımlama bilgileriyle çalışmaz, ancak bir taşıyıcı belirtecini kolayca alabilir ve sonraki isteklerin yetkilendirme üstbilgisine dahil edebilir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-172">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="4fa10-173">Belirteç kimlik doğrulamasını etkinleştirmek için ASP.NET Core, [OAuth 2,0](https://oauth.net/2/) ve [OpenID Connect](https://openid.net/connect/)kullanımına yönelik çeşitli seçenekleri destekler.</span><span class="sxs-lookup"><span data-stu-id="4fa10-173">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="4fa10-174">OpenID Connect veya OAuth 2,0 kimlik sağlayıcısı ile kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="4fa10-174">Authenticate with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="4fa10-175">Kullanıcı bilgileri Azure Active Directory veya OpenID Connect ya da OAuth 2,0 ' ı destekleyen başka bir kimlik çözümünde depolanıyorsa, OpenID Connect kullanarak kimlik doğrulamak için **Microsoft. AspNetCore. Authentication. Openıdconnect** paketini kullanabilirsiniz akışıyla.</span><span class="sxs-lookup"><span data-stu-id="4fa10-175">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the **Microsoft.AspNetCore.Authentication.OpenIdConnect** package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="4fa10-176">Örneğin, eShopOnContainers 'daki Identity. API mikro hizmeti için kimlik doğrulaması yapmak üzere, bir ASP.NET Core Web uygulaması, aşağıdaki Basitleştirilmiş örnekte gösterildiği gibi bu paketteki ara yazılımı kullanabilir `Startup.cs`:</span><span class="sxs-lookup"><span data-stu-id="4fa10-176">For example, to authenticate to the Identity.Api microservice in eShopOnContainers, an ASP.NET Core web application can use middleware from that package as shown in the following simplified example in `Startup.cs`:</span></span>

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

<span data-ttu-id="4fa10-177">Bu iş akışını kullandığınızda, tüm Kullanıcı bilgileri depolama ve kimlik doğrulama kimlik hizmeti tarafından işlendiği için ASP.NET Core Identity ara yazılımı gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-177">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by the Identity service.</span></span>

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="4fa10-178">ASP.NET Core hizmetinden güvenlik belirteçleri verme</span><span class="sxs-lookup"><span data-stu-id="4fa10-178">Issue security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="4fa10-179">Dış kimlik sağlayıcısı kullanmak yerine yerel ASP.NET Core Identity kullanıcıları için güvenlik belirteçleri vermek isterseniz, bazı iyi üçüncü taraf kitaplıklarından yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fa10-179">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="4fa10-180">[Identityserver4](https://github.com/IdentityServer/IdentityServer4) ve [Openıddict](https://github.com/openiddict/openiddict-core) , bir ASP.NET Core hizmetinden güvenlik belirteçleri vermesini sağlamak üzere ASP.NET Core kimlikle kolayca tümleştirilen OpenID Connect sağlayıcılarıdır.</span><span class="sxs-lookup"><span data-stu-id="4fa10-180">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="4fa10-181">[Identityserver4 belgeleri](https://identityserver4.readthedocs.io/en/latest/) , kitaplığı kullanmaya yönelik ayrıntılı yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-181">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/latest/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="4fa10-182">Ancak, belirteçleri vermek için ıdentityserver4 kullanmanın temel adımları aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-182">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1. <span data-ttu-id="4fa10-183">Uygulamayı çağırabilirsiniz. Useıdentityserver başlangıç. uygulamanın HTTP istek işleme ardışık düzenine ıdentityserver4 eklemek için yöntemi yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="4fa10-183">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="4fa10-184">Bu, kitaplığın OpenID Connect ve/Connect/tokengibi OAuth2 uç noktalarına istek sunmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4fa10-184">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2. <span data-ttu-id="4fa10-185">Identityserver4, Service 'e bir çağrı yaparak Startup. ConfigureServices içinde yapılandırırsınız. Addentityserver.</span><span class="sxs-lookup"><span data-stu-id="4fa10-185">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3. <span data-ttu-id="4fa10-186">Aşağıdaki verileri ayarlayarak kimlik sunucusunu yapılandırırsınız:</span><span class="sxs-lookup"><span data-stu-id="4fa10-186">You configure identity server by setting the following data:</span></span>

   - <span data-ttu-id="4fa10-187">İmzalama için kullanılacak [kimlik bilgileri](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) .</span><span class="sxs-lookup"><span data-stu-id="4fa10-187">The [credentials](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) to use for signing.</span></span>

   - <span data-ttu-id="4fa10-188">Kullanıcıların erişim isteyebilecek [kimlik ve API kaynakları](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) :</span><span class="sxs-lookup"><span data-stu-id="4fa10-188">The [Identity and API resources](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) that users might request access to:</span></span>

      - <span data-ttu-id="4fa10-189">API kaynakları, bir kullanıcının bir erişim belirteciyle erişebileceği korumalı verileri veya işlevselliği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4fa10-189">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="4fa10-190">Bir API kaynağına bir örnek, yetkilendirme gerektiren bir Web API 'SI (veya API kümesi) olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4fa10-190">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

      - <span data-ttu-id="4fa10-191">Kimlik kaynakları, bir kullanıcıyı tanımlamak için bir istemciye verilen bilgileri (talepler) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4fa10-191">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="4fa10-192">Talepler Kullanıcı adı, e-posta adresi vb. içerebilir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-192">The claims might include the user name, email address, and so on.</span></span>

   - <span data-ttu-id="4fa10-193">Belirteçleri istemek için bağlantı yapılacak [istemciler](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) .</span><span class="sxs-lookup"><span data-stu-id="4fa10-193">The [clients](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) that will be connecting in order to request tokens.</span></span>

   - <span data-ttu-id="4fa10-194">[ASP.NET Core kimliği](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) veya alternatif gibi Kullanıcı bilgileri için depolama mekanizması.</span><span class="sxs-lookup"><span data-stu-id="4fa10-194">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) or an alternative.</span></span>

<span data-ttu-id="4fa10-195">Identityserver4 için kullanılacak istemcileri ve kaynakları belirttiğinizde, uygun türdeki bir <xref:System.Collections.Generic.IEnumerable%601> koleksiyonunu bellek içi istemci veya kaynak depoları alan yöntemlere geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fa10-195">When you specify clients and resources for IdentityServer4 to use, you can pass an <xref:System.Collections.Generic.IEnumerable%601> collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="4fa10-196">Ya da daha karmaşık senaryolar için, bağımlılık ekleme yoluyla istemci veya kaynak sağlayıcısı türleri sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fa10-196">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="4fa10-197">Identityserver4 için, bellek içi kaynakları ve özel bir ılientstore türü tarafından sunulan istemcileri kullanmak için örnek bir yapılandırma aşağıdaki örnekteki gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="4fa10-197">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

### <a name="consume-security-tokens"></a><span data-ttu-id="4fa10-198">Güvenlik belirteçlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="4fa10-198">Consume security tokens</span></span>

<span data-ttu-id="4fa10-199">Bir OpenID Connect uç noktasına karşı kimlik doğrulaması veya kendi güvenlik belirteçlerinizi verme bazı senaryolar içerir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-199">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="4fa10-200">Ancak, yalnızca farklı bir hizmet tarafından sunulan geçerli güvenlik belirteçleri olan kullanıcılarla erişimi sınırlamaya yönelik bir hizmet hakkında ne var?</span><span class="sxs-lookup"><span data-stu-id="4fa10-200">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="4fa10-201">Bu senaryo için, JWT belirteçlerini işleyen kimlik doğrulama ara yazılımı **Microsoft. AspNetCore. Authentication. Jwttaşıyıcı** paketinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-201">For that scenario, authentication middleware that handles JWT tokens is available in the **Microsoft.AspNetCore.Authentication.JwtBearer** package.</span></span> <span data-ttu-id="4fa10-202">JWT, "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" için temsil eder ve güvenlik taleplerini iletişim kurmak için ortak bir güvenlik belirteci BIÇIMIDIR (RFC 7519 tarafından tanımlanır).</span><span class="sxs-lookup"><span data-stu-id="4fa10-202">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="4fa10-203">Bu tür belirteçleri kullanmak için ara yazılımın nasıl kullanılacağına ilişkin basitleştirilmiş bir örnek, sıralama. API mikro hizmeti olan eShopOnContainers 'dan alınan bu kod parçası gibi görünebilir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-203">A simplified example of how to use middleware to consume such tokens might look like this code fragment, taken from the Ordering.Api microservice of eShopOnContainers.</span></span>

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

<span data-ttu-id="4fa10-204">Bu kullanımdaki parametreler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4fa10-204">The parameters in this usage are:</span></span>

- <span data-ttu-id="4fa10-205">`Audience`, gelen belirtecin veya belirtecin erişim izni verdiği kaynağın alıcısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4fa10-205">`Audience` represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="4fa10-206">Bu parametrede belirtilen değer, belirteçteki parametreyle eşleşmezse, belirteç reddedilir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-206">If the value specified in this parameter does not match the parameter in the token, the token will be rejected.</span></span>

- <span data-ttu-id="4fa10-207">`Authority`, belirteç veren kimlik doğrulama sunucusunun adresidir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-207">`Authority` is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="4fa10-208">JWT taşıyıcı kimlik doğrulama ara yazılımı, belirtecin imzasını doğrulamak için kullanılabilecek ortak anahtarı almak için bu URI 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="4fa10-208">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="4fa10-209">Ara yazılım, belirteçteki `iss` parametresinin bu URI ile eşleştiğini de onaylar.</span><span class="sxs-lookup"><span data-stu-id="4fa10-209">The middleware also confirms that the `iss` parameter in the token matches this URI.</span></span>

<span data-ttu-id="4fa10-210">`RequireHttpsMetadata`başka bir parametre, test amaçları için yararlıdır; Bu parametreyi yanlış olarak ayarlarsanız, sertifikalarınızın olmadığı ortamlarda test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fa10-210">Another parameter, `RequireHttpsMetadata`, is useful for testing purposes; you set this parameter to false so you can test in environments where you don't have certificates.</span></span> <span data-ttu-id="4fa10-211">Gerçek dünyada dağıtımlarda, JWT taşıyıcı belirteçlerinin her zaman yalnızca HTTPS üzerinden geçirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-211">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="4fa10-212">Bu ara yazılım söz konusu olduğunda, JWT belirteçleri yetkilendirme başlıklarından otomatik olarak ayıklanır.</span><span class="sxs-lookup"><span data-stu-id="4fa10-212">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="4fa10-213">Daha sonra bunlar seri durumdan silinir, onaylanır (`Audience` ve `Authority` parametrelerdeki değerler kullanılarak) ve daha sonra MVC eylemleri veya Yetkilendirme filtreleri tarafından başvurulmak üzere Kullanıcı bilgileri olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="4fa10-213">They are then deserialized, validated (using the values in the `Audience` and `Authority` parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="4fa10-214">JWT taşıyıcı kimlik doğrulama ara yazılımı, yetkili kullanılamıyorsa bir belirteci doğrulamak için yerel bir sertifika kullanma gibi daha gelişmiş senaryoları da destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="4fa10-214">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="4fa10-215">Bu senaryo için, `JwtBearerOptions` nesnesinde bir `TokenValidationParameters` nesnesi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4fa10-215">For this scenario, you can specify a `TokenValidationParameters` object in the `JwtBearerOptions` object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="4fa10-216">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="4fa10-216">Additional resources</span></span>

- <span data-ttu-id="4fa10-217">**Uygulamalar arasında tanımlama bilgilerini paylaşma** </span><span class="sxs-lookup"><span data-stu-id="4fa10-217">**Sharing cookies between applications** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/cookie-sharing](/aspnet/core/security/cookie-sharing)

- <span data-ttu-id="4fa10-218">**Kimlik \ giriş**</span><span class="sxs-lookup"><span data-stu-id="4fa10-218">**Introduction to Identity** \</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="4fa10-219">**Rick Anderson. SMS \ ile iki öğeli kimlik doğrulama**</span><span class="sxs-lookup"><span data-stu-id="4fa10-219">**Rick Anderson. Two-factor authentication with SMS** \</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authentication/2fa](/aspnet/core/security/authentication/2fa)

- <span data-ttu-id="4fa10-220">**Facebook, Google ve diğer dış sağlayıcıları kullanarak kimlik doğrulamasını etkinleştirme** </span><span class="sxs-lookup"><span data-stu-id="4fa10-220">**Enabling authentication using Facebook, Google and other external providers** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/social/](/aspnet/core/security/authentication/social/)

- <span data-ttu-id="4fa10-221">**Michell Anıas. OAuth 2 \ giriş**</span><span class="sxs-lookup"><span data-stu-id="4fa10-221">**Michell Anicas. An Introduction to OAuth 2** \</span></span>
  <https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2>

- <span data-ttu-id="4fa10-222">**Aspnet. Security. OAuth. Providers** (ASP.net OAuth sağlayıcıları için GitHub deposu) </span><span class="sxs-lookup"><span data-stu-id="4fa10-222">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers) </span></span>\
  <https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src>

- <span data-ttu-id="4fa10-223">**Identityserver4. Resmi belgeler** </span><span class="sxs-lookup"><span data-stu-id="4fa10-223">**IdentityServer4. Official documentation** </span></span>\
  <https://identityserver4.readthedocs.io/en/latest/>

>[!div class="step-by-step"]
><span data-ttu-id="4fa10-224">[Önceki](../implement-resilient-applications/monitor-app-health.md)
>[İleri](authorization-net-microservices-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="4fa10-224">[Previous](../implement-resilient-applications/monitor-app-health.md)
[Next](authorization-net-microservices-web-applications.md)</span></span>
