---
title: .NET mikro Hizmetleri ve Web uygulamalarının güvenliğini sağlama
description: .NET mikro Hizmetleri ve Web uygulamaları - güvenlik ASP.NET Core web uygulamalarında kimlik doğrulama seçenekleri bilmek alın.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
---
# <a name="make-secure-net-microservices-and-web-applications"></a><span data-ttu-id="48f8d-103">Güvenli .NET mikro Hizmetleri ve Web uygulamaları</span><span class="sxs-lookup"><span data-stu-id="48f8d-103">Make secure .NET Microservices and Web Applications</span></span>

<span data-ttu-id="48f8d-104">Bu bölümde, kimlik doğrulaması, yetkilendirme ve uygulama gizli dizilerini odaklanacağız şekilde konu kolay bunun gibi birkaç books sürebilir, mikro hizmetler ve web uygulamaları'nda güvenlik hakkında çok fazla unsur vardır.</span><span class="sxs-lookup"><span data-stu-id="48f8d-104">There are so many aspects about security in microservices and web applications that the topic could easy take several books like this one so, in this section, we'll focus on authentication, authorization, and application secrets.</span></span>

## <a name="implement-authentication-in-net-microservices-and-web-applications"></a><span data-ttu-id="48f8d-105">.NET mikro Hizmetleri ve web uygulamalarında uygulama kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="48f8d-105">Implement authentication in .NET microservices and web applications</span></span>

<span data-ttu-id="48f8d-106">Genellikle, kaynaklar ve belirli güvenilen kullanıcıların veya istemciler için sınırlı bir hizmet tarafından yayımlanan API'leri için gerekli olur.</span><span class="sxs-lookup"><span data-stu-id="48f8d-106">It's often necessary for resources and APIs published by a service to be limited to certain trusted users or clients.</span></span> <span data-ttu-id="48f8d-107">Kimlik doğrulaması yaparak bu tür bir API düzeyinde güven kararları için ilk adımdır.</span><span class="sxs-lookup"><span data-stu-id="48f8d-107">The first step to making these sorts of API-level trust decisions is authentication.</span></span> <span data-ttu-id="48f8d-108">Kimlik doğrulama işlemi, güvenilir bir şekilde bir kullanıcının kimliğini doğrulamak bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="48f8d-108">Authentication is the process of reliably verify a user’s identity.</span></span>

<span data-ttu-id="48f8d-109">Mikro hizmet senaryolarda, kimlik doğrulaması genellikle merkezi olarak yönetilir.</span><span class="sxs-lookup"><span data-stu-id="48f8d-109">In microservice scenarios, authentication is typically handled centrally.</span></span> <span data-ttu-id="48f8d-110">Bir API ağ geçidi kullanıyorsanız, ağ geçidi kimliğini doğrulamak için uygun bir Şekil 9-1'de gösterildiği yerdir.</span><span class="sxs-lookup"><span data-stu-id="48f8d-110">If you're using an API Gateway, the gateway is a good place to authenticate, as shown in Figure 9-1.</span></span> <span data-ttu-id="48f8d-111">Bu yaklaşımı kullanın, ek güvenlik iletileri kimlik doğrulaması yerinde olup olmadığını ağ geçidinden veya geldikleri olmadığı sürece her bir mikro hizmetin doğrudan (API ağ geçidi) ulaşılamıyor emin olun.</span><span class="sxs-lookup"><span data-stu-id="48f8d-111">If you use this approach, make sure that the individual microservices cannot be reached directly (without the API Gateway) unless additional security is in place to authenticate messages whether they come from the gateway or not.</span></span>

![API Ağ Geçidi kimlik doğrulaması merkezileştirir, mikro hizmetler isteklerini iletirken kullanıcı bilgilerini ekler.](./media/image1.png)

<span data-ttu-id="48f8d-113">**Şekil 9-1**.</span><span class="sxs-lookup"><span data-stu-id="48f8d-113">**Figure 9-1**.</span></span> <span data-ttu-id="48f8d-114">Bir API ağ geçidi ile merkezi kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="48f8d-114">Centralized authentication with an API Gateway</span></span>

<span data-ttu-id="48f8d-115">Hizmetleri doğrudan erişilebilir, kimlik doğrulama hizmeti Azure Active Directory veya bir güvenlik belirteci hizmeti (STS), kullanıcıların kimliklerini doğrulamak için kullanılabilir davranan bir özel kimlik doğrulama mikro hizmet gibi.</span><span class="sxs-lookup"><span data-stu-id="48f8d-115">If services can be accessed directly, an authentication service like Azure Active Directory or a dedicated authentication microservice acting as a security token service (STS) can be used to authenticate users.</span></span> <span data-ttu-id="48f8d-116">Güven kararları güvenlik belirteçleri veya tanımlama bilgileri ile hizmetler arasında paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="48f8d-116">Trust decisions are shared between services with security tokens or cookies.</span></span> <span data-ttu-id="48f8d-117">(Bu belirteçleri uygulayarak gerekirse ASP.NET Core uygulamaları arasında paylaşılabilir [tanımlama bilgisi paylaşımını](/aspnet/core/security/cookie-sharing).) Bu düzen, Şekil 9-2'de gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="48f8d-117">(These tokens can be shared between ASP.NET Core applications, if needed, by implementing [cookie sharing](/aspnet/core/security/cookie-sharing).) This pattern is illustrated in Figure 9-2.</span></span>

![Mikro hizmetler doğrudan erişildiğinde, kimlik doğrulama ve yetkilendirme içerir, güven, mikro hizmetler arasında paylaşılan adanmış bir mikro hizmet veren bir güvenlik belirteci tarafından işlenir.](./media/image2.png)

<span data-ttu-id="48f8d-119">**Şekil 9-2**.</span><span class="sxs-lookup"><span data-stu-id="48f8d-119">**Figure 9-2**.</span></span> <span data-ttu-id="48f8d-120">Kimlik mikro hizmet olarak kimlik doğrulaması; bir yetkilendirme belirteciyle güven paylaşılan</span><span class="sxs-lookup"><span data-stu-id="48f8d-120">Authentication by identity microservice; trust is shared using an authorization token</span></span>

### <a name="authenticate-with-aspnet-core-identity"></a><span data-ttu-id="48f8d-121">ASP.NET Core kimliği ile kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="48f8d-121">Authenticate with ASP.NET Core Identity</span></span>

<span data-ttu-id="48f8d-122">Bir uygulamanın kullanıcıları tanımlamak için birincil mekanizma ASP.NET core'da [ASP.NET Core kimliği](/aspnet/core/security/authentication/identity) üyelik sistemi.</span><span class="sxs-lookup"><span data-stu-id="48f8d-122">The primary mechanism in ASP.NET Core for identifying an application’s users is the [ASP.NET Core Identity](/aspnet/core/security/authentication/identity) membership system.</span></span> <span data-ttu-id="48f8d-123">ASP.NET Core kimliği geliştirici tarafından yapılandırılmış bir veri deposu (oturum açma bilgileri, rolleri ve talep dahil) kullanıcı bilgilerini depolar.</span><span class="sxs-lookup"><span data-stu-id="48f8d-123">ASP.NET Core Identity stores user information (including sign-in information, roles, and claims) in a data store configured by the developer.</span></span> <span data-ttu-id="48f8d-124">Genellikle, ASP.NET Core kimliği veri deposu sağlanan içinde bir Entity Framework deposudur `Microsoft.AspNetCore.Identity.EntityFrameworkCore` paket.</span><span class="sxs-lookup"><span data-stu-id="48f8d-124">Typically, the ASP.NET Core Identity data store is an Entity Framework store provided in the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` package.</span></span> <span data-ttu-id="48f8d-125">Ancak, özel depoları veya diğer üçüncü taraf paketleri Azure tablo depolama, CosmosDB veya diğer konumlardan kimlik bilgilerini depolamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="48f8d-125">However, custom stores or other third-party packages can be used to store identity information in Azure Table Storage, CosmosDB, or other locations.</span></span>

<span data-ttu-id="48f8d-126">Aşağıdaki kod, seçilen kullanıcı hesabı kimlik doğrulaması ile ASP.NET Core Web uygulaması proje şablonu alınır.</span><span class="sxs-lookup"><span data-stu-id="48f8d-126">The following code is taken from the ASP.NET Core Web Application project template with individual user account authentication selected.</span></span> <span data-ttu-id="48f8d-127">Bu, ASP.NET Core EntityFramework.Core Startup.ConfigureServices yöntemiyle kimliğini yapılandırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="48f8d-127">It shows how to configure ASP.NET Core Identity using EntityFramework.Core in the Startup.ConfigureServices method.</span></span>

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
```

<span data-ttu-id="48f8d-128">ASP.NET Core kimliği yapılandırıldıktan sonra çağıran uygulama tarafından etkinleştirin. Hizmetin UseIdentity `Startup.Configure` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="48f8d-128">Once ASP.NET Core Identity is configured, you enable it by calling app.UseIdentity in the service’s `Startup.Configure` method.</span></span>

<span data-ttu-id="48f8d-129">ASP.NET Core kimliği kullanarak çeşitli senaryolara olanak tanır:</span><span class="sxs-lookup"><span data-stu-id="48f8d-129">Using ASP.NET Core Identity enables several scenarios:</span></span>

- <span data-ttu-id="48f8d-130">Yeni kullanıcı bilgilerini UserManager türü (userManager.CreateAsync) kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="48f8d-130">Create new user information using the UserManager type (userManager.CreateAsync).</span></span>

- <span data-ttu-id="48f8d-131">Kullanıcılar SignInManager türü kullanılarak kimlik doğrulaması.</span><span class="sxs-lookup"><span data-stu-id="48f8d-131">Authenticate users using the SignInManager type.</span></span> <span data-ttu-id="48f8d-132">Kullanabileceğiniz `signInManager.SignInAsync` doğrudan oturum açmanız veya `signInManager.PasswordSignInAsync` kullanıcının parolasını doğru olduğunu onaylayın ve ardından bunları oturum açın.</span><span class="sxs-lookup"><span data-stu-id="48f8d-132">You can use `signInManager.SignInAsync` to sign in directly, or `signInManager.PasswordSignInAsync` to confirm the user’s password is correct and then sign them in.</span></span>

- <span data-ttu-id="48f8d-133">İstekler bir tarayıcıdan oturum açmış kullanıcının kimlik ve talep içerecektir (Bu, ASP.NET Core kimliği ara yazılımı tarafından okunur) bir tanımlama bilgisinde depolanan bilgilere dayanarak bir kullanıcıya belirleyin.</span><span class="sxs-lookup"><span data-stu-id="48f8d-133">Identify a user based on information stored in a cookie (which is read by ASP.NET Core Identity middleware) so that subsequent requests from a browser will include a signed-in user’s identity and claims.</span></span>

<span data-ttu-id="48f8d-134">ASP.NET Core kimliği de destekler [iki öğeli kimlik doğrulama](/aspnet/core/security/authentication/2fa).</span><span class="sxs-lookup"><span data-stu-id="48f8d-134">ASP.NET Core Identity also supports [two-factor authentication](/aspnet/core/security/authentication/2fa).</span></span>

<span data-ttu-id="48f8d-135">ASP.NET Core kimliği olun kimlik doğrulama senaryoları bir yerel kullanıcı veri deposunu kullanın ve kimlik (MVC web uygulamaları için tipik olduğu gibi) tanımlama bilgilerini kullanarak istekleri arasında kalıcı hale getirmek için önerilen bir çözümdür.</span><span class="sxs-lookup"><span data-stu-id="48f8d-135">For authentication scenarios that make use of a local user data store and that persist identity between requests using cookies (as is typical for MVC web applications), ASP.NET Core Identity is a recommended solution.</span></span>

### <a name="authenticate-with-external-providers"></a><span data-ttu-id="48f8d-136">Dış sağlayıcıları ile kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="48f8d-136">Authenticate with external providers</span></span>

<span data-ttu-id="48f8d-137">ASP.NET Core da destekler kullanarak [Dış kimlik doğrulama sağlayıcıları](/aspnet/core/security/authentication/social/) aracılığıyla oturum açmasına izin vermek için [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) akışlar.</span><span class="sxs-lookup"><span data-stu-id="48f8d-137">ASP.NET Core also supports using [external authentication providers](/aspnet/core/security/authentication/social/) to let users sign in via [OAuth 2.0](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2) flows.</span></span> <span data-ttu-id="48f8d-138">Bu, kullanıcıların mevcut kimlik doğrulama işlemi Microsoft, Google, Facebook veya Twitter gibi sağlayıcılarından kullanarak oturum açın ve ASP.NET Core kimliği uygulamanızda kimliklerle ilişkilendirme anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="48f8d-138">This means that users can sign in using existing authentication processes from providers like Microsoft, Google, Facebook, or Twitter and associate those identities with an ASP.NET Core identity in your application.</span></span>

<span data-ttu-id="48f8d-139">Dış kimlik doğrulama kullanmak için uygulamanızın HTTP isteği ardışık düzen işleme uygun yetkilendirme Ara yazılımının dahil edin.</span><span class="sxs-lookup"><span data-stu-id="48f8d-139">To use external authentication, you include the appropriate authentication middleware in your application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="48f8d-140">Bu ara yazılım kimlik sağlayıcısındaki kimlik bilgilerini yakalama ve SignInManager.GetExternalLoginInfo yöntemi aracılığıyla kullanılabilir hale getirme URI yolları döndürülecek işleme isteklerinin sorumludur.</span><span class="sxs-lookup"><span data-stu-id="48f8d-140">This middleware is responsible for handling requests to return URI routes from the authentication provider, capturing identity information, and making it available via the SignInManager.GetExternalLoginInfo method.</span></span>

<span data-ttu-id="48f8d-141">Yaygın Dış kimlik doğrulama sağlayıcıları ve bunların ilişkili NuGet paketleri aşağıdaki tabloda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="48f8d-141">Popular external authentication providers and their associated NuGet packages are shown in the following table:</span></span>

| <span data-ttu-id="48f8d-142">**Sağlayıcı**</span><span class="sxs-lookup"><span data-stu-id="48f8d-142">**Provider**</span></span>  | <span data-ttu-id="48f8d-143">**Paket**</span><span class="sxs-lookup"><span data-stu-id="48f8d-143">**Package**</span></span>                                          |
| ------------- | ---------------------------------------------------- |
| <span data-ttu-id="48f8d-144">**Microsoft**</span><span class="sxs-lookup"><span data-stu-id="48f8d-144">**Microsoft**</span></span> | <span data-ttu-id="48f8d-145">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span><span class="sxs-lookup"><span data-stu-id="48f8d-145">**Microsoft.AspNetCore.Authentication.MicrosoftAccount**</span></span> |
| <span data-ttu-id="48f8d-146">**Google**</span><span class="sxs-lookup"><span data-stu-id="48f8d-146">**Google**</span></span>    | <span data-ttu-id="48f8d-147">**Microsoft.AspNetCore.Authentication.Google**</span><span class="sxs-lookup"><span data-stu-id="48f8d-147">**Microsoft.AspNetCore.Authentication.Google**</span></span>           |
| <span data-ttu-id="48f8d-148">**Facebook**</span><span class="sxs-lookup"><span data-stu-id="48f8d-148">**Facebook**</span></span>  | <span data-ttu-id="48f8d-149">**Microsoft.AspNetCore.Authentication.Facebook**</span><span class="sxs-lookup"><span data-stu-id="48f8d-149">**Microsoft.AspNetCore.Authentication.Facebook**</span></span>         |
| <span data-ttu-id="48f8d-150">**Twitter**</span><span class="sxs-lookup"><span data-stu-id="48f8d-150">**Twitter**</span></span>   | <span data-ttu-id="48f8d-151">**Microsoft.AspNetCore.Authentication.Twitter**</span><span class="sxs-lookup"><span data-stu-id="48f8d-151">**Microsoft.AspNetCore.Authentication.Twitter**</span></span>          |

<span data-ttu-id="48f8d-152">Her durumda, ara yazılım için benzer bir kayıt yöntemi çağrısı ile kayıtlı `app.Use{ExternalProvider}Authentication` içinde `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="48f8d-152">In all cases, the middleware is registered with a call to a registration method similar to `app.Use{ExternalProvider}Authentication` in `Startup.Configure`.</span></span> <span data-ttu-id="48f8d-153">Bu kayıt yöntemleri bir uygulama kimliği ve gizli bilgi içeren bir seçenekler nesne alır (parola örneği için), sağlayıcı tarafından gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="48f8d-153">These registration methods take an options object that contains an application ID and secret information (a password, for instance), as needed by the provider.</span></span> <span data-ttu-id="48f8d-154">Dış kimlik doğrulama sağlayıcıları uygulamanın kayıtlı olması gerekir (açıklandığı şekilde [ASP.NET Core belgeleri](/aspnet/core/security/authentication/social/)), böylece hangi uygulama kimliklerini erişim isteyen kullanıcı bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48f8d-154">External authentication providers require the application to be registered (as explained in [ASP.NET Core documentation](/aspnet/core/security/authentication/social/)) so that they can inform the user what application is requesting access to their identity.</span></span>

<span data-ttu-id="48f8d-155">Ara yazılım, kaydedildikten sonra `Startup.Configure`, herhangi bir denetleyici eylemden oturum açmalarını isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="48f8d-155">Once the middleware is registered in `Startup.Configure`, you can prompt users to sign in from any controller action.</span></span> <span data-ttu-id="48f8d-156">Bunu yapmak için oluşturduğunuz bir `AuthenticationProperties` kimlik doğrulama sağlayıcısının adını ve bir yeniden yönlendirme URL'sini içeren bir nesne.</span><span class="sxs-lookup"><span data-stu-id="48f8d-156">To do this, you create an `AuthenticationProperties` object that includes the authentication provider’s name and a redirect URL.</span></span> <span data-ttu-id="48f8d-157">Başarılı bir sınama yanıtı çıkacak `AuthenticationProperties` nesne.</span><span class="sxs-lookup"><span data-stu-id="48f8d-157">You then return a Challenge response that passes the `AuthenticationProperties` object.</span></span> <span data-ttu-id="48f8d-158">Aşağıdaki kod, bunun bir örneğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="48f8d-158">The following code shows an example of this.</span></span>

```csharp
var properties = _signInManager.ConfigureExternalAuthenticationProperties(provider,
    redirectUrl);
return Challenge(properties, provider);
```

<span data-ttu-id="48f8d-159">Kullanıcı kimliğini doğrulamasından sonra dış sağlayıcı yönlendirmek URL redirectUrl parametresi içerir.</span><span class="sxs-lookup"><span data-stu-id="48f8d-159">The redirectUrl parameter includes the URL that the external provider should redirect to once the user has authenticated.</span></span> <span data-ttu-id="48f8d-160">URL, kullanıcı aşağıdaki Basitleştirilmiş örnekte olduğu gibi bir dış kimlik bilgilerine dayalı oturum açacak bir eylem göstermelidir:</span><span class="sxs-lookup"><span data-stu-id="48f8d-160">The URL should represent an action that will sign the user in based on external identity information, as in the following simplified example:</span></span>

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

<span data-ttu-id="48f8d-161">Seçerseniz **bireysel kullanıcı hesabı** Visual Studio'da bir dış sağlayıcısı ile oturum açmak için gerekli tüm kodlar kod ASP.NET web uygulaması projesi oluşturduğunuzda, kimlik doğrulaması seçeneği olan zaten projede gösterildiği gibi Şekil 9-3'te.</span><span class="sxs-lookup"><span data-stu-id="48f8d-161">If you choose the **Individual User Account** authentication option when you create the ASP.NET Code web application project in Visual Studio, all the code necessary to sign in with an external provider is already in the project, as shown in Figure 9-3.</span></span>

![Yeni ASP.NET Core Web kimlik doğrulaması düğmenin vurgulama uygulaması iletişim kutusu.](./media/image3.png)

<span data-ttu-id="48f8d-163">**Şekil 9-3**.</span><span class="sxs-lookup"><span data-stu-id="48f8d-163">**Figure 9-3**.</span></span> <span data-ttu-id="48f8d-164">Bir web uygulaması projesi oluştururken, dış kimlik doğrulama kullanmak için bir seçeneği</span><span class="sxs-lookup"><span data-stu-id="48f8d-164">Selecting an option for using external authentication when creating a web application project</span></span>

<span data-ttu-id="48f8d-165">Ek olarak bir dış kimlik doğrulama sağlayıcıları daha önce üçüncü taraf paketlerini listelenen çok fazla dış kimlik doğrulama sağlayıcıları için bir ara yazılım sağladığınız kullanılabilir durumdadır.</span><span class="sxs-lookup"><span data-stu-id="48f8d-165">In addition to the external authentication providers listed previously, third-party packages are available that provide middleware for using many more external authentication providers.</span></span> <span data-ttu-id="48f8d-166">Bir liste için bkz. [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) github deposu.</span><span class="sxs-lookup"><span data-stu-id="48f8d-166">For a list, see the [AspNet.Security.OAuth.Providers](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src) repo on GitHub.</span></span>

<span data-ttu-id="48f8d-167">Ayrıca, bazı özel gereksinim çözmek için kendi dış kimlik doğrulaması ara yazılımı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48f8d-167">You can also create your own external authentication middleware to solve some special need.</span></span>

### <a name="authenticate-with-bearer-tokens"></a><span data-ttu-id="48f8d-168">Taşıyıcı belirteçleri ile kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="48f8d-168">Authenticate with bearer tokens</span></span>

<span data-ttu-id="48f8d-169">ASP.NET Core kimliği (veya kimlik ve Dış kimlik doğrulama sağlayıcıları ile) kimlik doğrulaması, kullanıcı bilgileri depolayan bir tanımlama bilgisinde uygun olduğu da birçok web uygulama senaryoları için çalışır.</span><span class="sxs-lookup"><span data-stu-id="48f8d-169">Authenticating with ASP.NET Core Identity (or Identity plus external authentication providers) works well for many web application scenarios in which storing user information in a cookie is appropriate.</span></span> <span data-ttu-id="48f8d-170">Diğer senaryolarda, ancak tanımlama bilgilerini kalıcı hale getirmeniz ve veri aktarımı doğal bir yol değildir.</span><span class="sxs-lookup"><span data-stu-id="48f8d-170">In other scenarios, though, cookies are not a natural means of persisting and transmitting data.</span></span>

<span data-ttu-id="48f8d-171">Örneğin, bir ASP.NET Core Web API'si yerel istemciler tarafından tek sayfa uygulamaları (Spa'lar) tarafından erişilebilen bir RESTful uç noktalarını kullanıma sunan veya hatta diğer Web API'leri tarafından genellikle taşıyıcı belirteci kimlik doğrulaması yerine kullanmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="48f8d-171">For example, in an ASP.NET Core Web API that exposes RESTful endpoints that might be accessed by Single Page Applications (SPAs), by native clients, or even by other Web APIs, you typically want to use bearer token authentication instead.</span></span> <span data-ttu-id="48f8d-172">Bu tür uygulamalar değil tanımlama bilgileriyle çalışır ancak kolayca bir taşıyıcı belirteç alabilir ve sonraki istekleri yetkilendirme üst bilgisi içerir.</span><span class="sxs-lookup"><span data-stu-id="48f8d-172">These types of applications do not work with cookies, but can easily retrieve a bearer token and include it in the authorization header of subsequent requests.</span></span> <span data-ttu-id="48f8d-173">Belirteç kimlik doğrulamasını etkinleştirmek için ASP.NET Core çeşitli seçenekler kullanmak için destekleyen [OAuth 2.0](https://oauth.net/2/) ve [Openıd Connect](https://openid.net/connect/).</span><span class="sxs-lookup"><span data-stu-id="48f8d-173">To enable token authentication, ASP.NET Core supports several options for using [OAuth 2.0](https://oauth.net/2/) and [OpenID Connect](https://openid.net/connect/).</span></span>

### <a name="authenticate-with-an-openid-connect-or-oauth-20-identity-provider"></a><span data-ttu-id="48f8d-174">Bir Openıd Connect veya OAuth 2.0 kimlik sağlayıcısı ile kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="48f8d-174">Authenticate with an OpenID Connect or OAuth 2.0 Identity provider</span></span>

<span data-ttu-id="48f8d-175">Kullanıcı bilgilerini Azure Active Directory veya Openıd Connect veya OAuth 2.0 destekleyen başka bir kimlik çözümü içinde depolanıyorsa, kullanabileceğiniz **Microsoft.AspNetCore.Authentication.OpenIdConnect** paket kullanılarak kimlik doğrulaması Openıd Connect akışı.</span><span class="sxs-lookup"><span data-stu-id="48f8d-175">If user information is stored in Azure Active Directory or another identity solution that supports OpenID Connect or OAuth 2.0, you can use the **Microsoft.AspNetCore.Authentication.OpenIdConnect** package to authenticate using the OpenID Connect workflow.</span></span> <span data-ttu-id="48f8d-176">Örneğin, hizmetine Identity.Api mikro hizmet kimlik doğrulaması için bir ASP.NET Core web uygulaması ara yazılım bu paketten aşağıdaki Basitleştirilmiş örnekte gösterildiği gibi kullanabilirsiniz `Startup.cs`:</span><span class="sxs-lookup"><span data-stu-id="48f8d-176">For example, to authenticate to the Identity.Api microservice in eShopOnContainers, an ASP.NET Core web application can use middleware from that package as shown in the following simplified example in `Startup.cs`:</span></span>

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

<span data-ttu-id="48f8d-177">Bu iş akışını kullanırken, ASP.NET Core kimliği ara yazılımı gerekli olmadığını, tüm kullanıcı bilgileri depolama ve kimlik doğrulaması gerçekleştirilir çünkü kimlik hizmeti tarafından unutmayın.</span><span class="sxs-lookup"><span data-stu-id="48f8d-177">Note that when you use this workflow, the ASP.NET Core Identity middleware is not needed, because all user information storage and authentication is handled by the Identity service.</span></span>

### <a name="issue-security-tokens-from-an-aspnet-core-service"></a><span data-ttu-id="48f8d-178">Bir ASP.NET Core hizmeti güvenlik belirteçleri</span><span class="sxs-lookup"><span data-stu-id="48f8d-178">Issue security tokens from an ASP.NET Core service</span></span>

<span data-ttu-id="48f8d-179">Yerel ASP.NET Core kimliği kullanıcılar için güvenlik belirteçlerini vermek tercih ettiğiniz yerine, bir dış kimlik sağlayıcısı kullanarak, bazı iyi üçüncü taraf kitaplıklar avantajlarından yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48f8d-179">If you prefer to issue security tokens for local ASP.NET Core Identity users rather than using an external identity provider, you can take advantage of some good third-party libraries.</span></span>

<span data-ttu-id="48f8d-180">[Identityserver4](https://github.com/IdentityServer/IdentityServer4) ve [OpenIddict](https://github.com/openiddict/openiddict-core) Openıd Connect sağlayıcılar, ASP.NET Core kimliği ile izin verecek şekilde güvenlik belirteçleri bir ASP.NET Core hizmeti kolayca tümleştirin.</span><span class="sxs-lookup"><span data-stu-id="48f8d-180">[IdentityServer4](https://github.com/IdentityServer/IdentityServer4) and [OpenIddict](https://github.com/openiddict/openiddict-core) are OpenID Connect providers that integrate easily with ASP.NET Core Identity to let you issue security tokens from an ASP.NET Core service.</span></span> <span data-ttu-id="48f8d-181">[Identityserver4 belgeleri](https://identityserver4.readthedocs.io/en/latest/) kitaplığı kullanmak için ayrıntılı yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="48f8d-181">The [IdentityServer4 documentation](https://identityserver4.readthedocs.io/en/latest/) has in-depth instructions for using the library.</span></span> <span data-ttu-id="48f8d-182">Ancak, Identityserver4 sorunu belirteçleri kullanarak için temel adımlar şunlardır.</span><span class="sxs-lookup"><span data-stu-id="48f8d-182">However, the basic steps to using IdentityServer4 to issue tokens are as follows.</span></span>

1. <span data-ttu-id="48f8d-183">Uygulama çağırırsınız. Identityserver4 uygulamanın HTTP istek işleme ardışık düzenine eklemek için UseIdentityServer Startup.Configure yöntem.</span><span class="sxs-lookup"><span data-stu-id="48f8d-183">You call app.UseIdentityServer in the Startup.Configure method to add IdentityServer4 to the application’s HTTP request processing pipeline.</span></span> <span data-ttu-id="48f8d-184">Bu kitaplık OAuth2 uç noktaları /connect/token gibi Openıd Connect ve isteklere hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="48f8d-184">This lets the library serve requests to OpenID Connect and OAuth2 endpoints like /connect/token.</span></span>

2. <span data-ttu-id="48f8d-185">Identityserver4 Hizmetleri çağrısı yaparak Startup.ConfigureServices içinde yapılandırın. AddIdentityServer.</span><span class="sxs-lookup"><span data-stu-id="48f8d-185">You configure IdentityServer4 in Startup.ConfigureServices by making a call to services.AddIdentityServer.</span></span>

3. <span data-ttu-id="48f8d-186">Kimlik sunucusu, aşağıdaki veriler ayarlayarak yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="48f8d-186">You configure identity server by setting the following data:</span></span>

   - <span data-ttu-id="48f8d-187">[Kimlik bilgilerini](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) imzalama için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="48f8d-187">The [credentials](https://identityserver4.readthedocs.io/en/latest/topics/crypto.html) to use for signing.</span></span>

   - <span data-ttu-id="48f8d-188">[Kimlik ve API kaynaklarına](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) kullanıcılar için erişim isteyebilir:</span><span class="sxs-lookup"><span data-stu-id="48f8d-188">The [Identity and API resources](https://identityserver4.readthedocs.io/en/latest/topics/resources.html) that users might request access to:</span></span>

      - <span data-ttu-id="48f8d-189">API kaynaklarını korumalı veriler veya bir erişim belirteci ile bir kullanıcının erişebildiği işlevleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="48f8d-189">API resources represent protected data or functionality that a user can access with an access token.</span></span> <span data-ttu-id="48f8d-190">Örnek bir API kaynağı bir web API (veya API kümesi) verilebilir yetkilendirme gerektirir.</span><span class="sxs-lookup"><span data-stu-id="48f8d-190">An example of an API resource would be a web API (or set of APIs) that requires authorization.</span></span>

      - <span data-ttu-id="48f8d-191">Kimlik kaynaklarını bir kullanıcıyı tanımlamak için bir istemci için verilen bilgileri (talep) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="48f8d-191">Identity resources represent information (claims) that are given to a client to identify a user.</span></span> <span data-ttu-id="48f8d-192">Talepler, kullanıcı adı, e-posta adresi vb. içerebilir.</span><span class="sxs-lookup"><span data-stu-id="48f8d-192">The claims might include the user name, email address, and so on.</span></span>

   - <span data-ttu-id="48f8d-193">[İstemcileri](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) , bağlama belirteci istemek için.</span><span class="sxs-lookup"><span data-stu-id="48f8d-193">The [clients](https://identityserver4.readthedocs.io/en/latest/topics/clients.html) that will be connecting in order to request tokens.</span></span>

   - <span data-ttu-id="48f8d-194">Kullanıcı bilgileri depolama mekanizması gibi [ASP.NET Core kimliği](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) veya alternatif.</span><span class="sxs-lookup"><span data-stu-id="48f8d-194">The storage mechanism for user information, such as [ASP.NET Core Identity](https://identityserver4.readthedocs.io/en/latest/quickstarts/0_overview.html) or an alternative.</span></span>

<span data-ttu-id="48f8d-195">İstemcileri ve Identityserver4 kaynakları kullanmak için belirttiğinizde, geçirebilirsiniz bir <xref:System.Collections.Generic.IEnumerable%601> bellek içi istemci veya kaynak depolarını ele yöntemleri için uygun türde bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="48f8d-195">When you specify clients and resources for IdentityServer4 to use, you can pass an <xref:System.Collections.Generic.IEnumerable%601> collection of the appropriate type to methods that take in-memory client or resource stores.</span></span> <span data-ttu-id="48f8d-196">Veya daha karmaşık senaryolarda, istemci veya kaynak sağlayıcısı türleri aracılığıyla bağımlılık ekleme sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="48f8d-196">Or for more complex scenarios, you can provide client or resource provider types via Dependency Injection.</span></span>

<span data-ttu-id="48f8d-197">Identityserver4 bellek içi kaynaklar ve istemcilere özel bir IClientStore türü tarafından sağlanan kullanmak için örnek bir yapılandırma aşağıdaki örnekteki gibi görünebilir:</span><span class="sxs-lookup"><span data-stu-id="48f8d-197">A sample configuration for IdentityServer4 to use in-memory resources and clients provided by a custom IClientStore type might look like the following example:</span></span>

```csharp
// Add IdentityServer services
services.AddSingleton<IClientStore, CustomClientStore>();
services.AddIdentityServer()
    .AddSigningCredential("CN=sts")
    .AddInMemoryApiResources(MyApiResourceProvider.GetAllResources())
    .AddAspNetIdentity<ApplicationUser>();
```

### <a name="consume-security-tokens"></a><span data-ttu-id="48f8d-198">Güvenlik belirteçleri kullanma</span><span class="sxs-lookup"><span data-stu-id="48f8d-198">Consume security tokens</span></span>

<span data-ttu-id="48f8d-199">Bir Openıd Connect uç noktasına karşı kimlik doğrulaması veya kendi güvenlik belirteçleri verme bazı senaryolar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="48f8d-199">Authenticating against an OpenID Connect endpoint or issuing your own security tokens covers some scenarios.</span></span> <span data-ttu-id="48f8d-200">Ancak ne yalnızca geçerli güvenliğe sahip kullanıcılara erişimi sınırlamak için gereken hizmet belirteçleri farklı bir hizmet tarafından sağlandı?</span><span class="sxs-lookup"><span data-stu-id="48f8d-200">But what about a service that simply needs to limit access to those users who have valid security tokens that were provided by a different service?</span></span>

<span data-ttu-id="48f8d-201">Bu senaryo için JWT belirteçlerini işler kimlik doğrulaması ara yazılımı kullanılabilir **Microsoft.AspNetCore.Authentication.JwtBearer** paket.</span><span class="sxs-lookup"><span data-stu-id="48f8d-201">For that scenario, authentication middleware that handles JWT tokens is available in the **Microsoft.AspNetCore.Authentication.JwtBearer** package.</span></span> <span data-ttu-id="48f8d-202">JWT anlamına gelen "[JSON Web belirteci](https://tools.ietf.org/html/rfc7519)" ve (RFC 7519 tarafından tanımlanan) ortak bir güvenlik belirteci biçimi güvenlik talepleri iletişim kurmak için.</span><span class="sxs-lookup"><span data-stu-id="48f8d-202">JWT stands for "[JSON Web Token](https://tools.ietf.org/html/rfc7519)" and is a common security token format (defined by RFC 7519) for communicating security claims.</span></span> <span data-ttu-id="48f8d-203">Basitleştirilmiş bir ara yazılım bu tür belirteçleri tüketen için nasıl kullanılacağını örneği hizmetine Ordering.Api mikro hizmet alınan bu kod parçası gibi görünebilir.</span><span class="sxs-lookup"><span data-stu-id="48f8d-203">A simplified example of how to use middleware to consume such tokens might look like this code fragment, taken from the Ordering.Api microservice of eShopOnContainers.</span></span>

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

<span data-ttu-id="48f8d-204">Bu kullanımı Parametreler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="48f8d-204">The parameters in this usage are:</span></span>

- <span data-ttu-id="48f8d-205">`Audience` gelen belirteci veya erişim belirteci verir kaynak alıcısı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="48f8d-205">`Audience` represents the receiver of the incoming token or the resource that the token grants access to.</span></span> <span data-ttu-id="48f8d-206">Bu parametrede belirtilen değer belirteci parametreyi eşleşmiyorsa, belirteç reddedilir.</span><span class="sxs-lookup"><span data-stu-id="48f8d-206">If the value specified in this parameter does not match the parameter in the token, the token will be rejected.</span></span>

- <span data-ttu-id="48f8d-207">`Authority` belirteci veren kimlik doğrulaması sunucusunun adresidir.</span><span class="sxs-lookup"><span data-stu-id="48f8d-207">`Authority` is the address of the token-issuing authentication server.</span></span> <span data-ttu-id="48f8d-208">JWT taşıyıcı kimlik doğrulaması ara yazılımı, belirtecin imzayı doğrulamak için kullanılacak ortak anahtarı almak için bu URI kullanır.</span><span class="sxs-lookup"><span data-stu-id="48f8d-208">The JWT bearer authentication middleware uses this URI to get the public key that can be used to validate the token's signature.</span></span> <span data-ttu-id="48f8d-209">Ara yazılım Ayrıca, onaylar `iss` belirteç parametresi bu URI ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="48f8d-209">The middleware also confirms that the `iss` parameter in the token matches this URI.</span></span>

<span data-ttu-id="48f8d-210">Başka bir parametre `RequireHttpsMetadata`, test amacıyla; yararlıdır ortamlarında test etmek, bu parametre false olarak burada yoksa sertifikaları ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="48f8d-210">Another parameter, `RequireHttpsMetadata`, is useful for testing purposes; you set this parameter to false so you can test in environments where you don't have certificates.</span></span> <span data-ttu-id="48f8d-211">Gerçek dağıtımlarda, JWT taşıyıcı belirteçlerini her zaman yalnızca HTTPS üzerinden geçirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="48f8d-211">In real-world deployments, JWT bearer tokens should always be passed only over HTTPS.</span></span>

<span data-ttu-id="48f8d-212">Yerinde bu ara yazılım ile JWT belirteçleri yetkilendirme üst bilgiler otomatik olarak çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="48f8d-212">With this middleware in place, JWT tokens are automatically extracted from authorization headers.</span></span> <span data-ttu-id="48f8d-213">Bunlar daha sonra seri durumdan çıkarılmakta, doğrulanmış (değerleri `Audience` ve `Authority` parametreleri) ve daha sonra MVC eylemler veya yetkilendirme filtreleri tarafından başvurulabilmesi için kullanıcı bilgilerini olarak depolanmış.</span><span class="sxs-lookup"><span data-stu-id="48f8d-213">They are then deserialized, validated (using the values in the `Audience` and `Authority` parameters), and stored as user information to be referenced later by MVC actions or authorization filters.</span></span>

<span data-ttu-id="48f8d-214">JWT taşıyıcı kimlik doğrulaması ara yazılımı yerel bir sertifika yetkilisi kullanılabilir değilse, bir belirteci doğrulamak için kullanma gibi daha gelişmiş senaryoları da destekler.</span><span class="sxs-lookup"><span data-stu-id="48f8d-214">The JWT bearer authentication middleware can also support more advanced scenarios, such as using a local certificate to validate a token if the authority is not available.</span></span> <span data-ttu-id="48f8d-215">Bu senaryo için belirttiğiniz bir `TokenValidationParameters` nesnesine `JwtBearerOptions` nesne.</span><span class="sxs-lookup"><span data-stu-id="48f8d-215">For this scenario, you can specify a `TokenValidationParameters` object in the `JwtBearerOptions` object.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="48f8d-216">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="48f8d-216">Additional resources</span></span>

- <span data-ttu-id="48f8d-217">**Tanımlama bilgilerini uygulamalar arasında paylaşma** \\</span><span class="sxs-lookup"><span data-stu-id="48f8d-217">**Sharing cookies between applications** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/security/cookie-sharing*](/aspnet/core/security/cookie-sharing)

- <span data-ttu-id="48f8d-218">**Kimliğe giriş** \\</span><span class="sxs-lookup"><span data-stu-id="48f8d-218">**Introduction to Identity** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="48f8d-219">**Rick Anderson. SMS ile iki öğeli kimlik doğrulama** \\</span><span class="sxs-lookup"><span data-stu-id="48f8d-219">**Rick Anderson. Two-factor authentication with SMS** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/security/authentication/2fa*](/aspnet/core/security/authentication/2fa)

- <span data-ttu-id="48f8d-220">**Facebook, Google ve diğer dış sağlayıcıları kullanarak kimlik doğrulamayı etkinleştirme** \\</span><span class="sxs-lookup"><span data-stu-id="48f8d-220">**Enabling authentication using Facebook, Google and other external providers** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/security/authentication/social/*](/aspnet/core/security/authentication/social/)

- <span data-ttu-id="48f8d-221">**Michell Anicas. OAuth 2 giriş** \\</span><span class="sxs-lookup"><span data-stu-id="48f8d-221">**Michell Anicas. An Introduction to OAuth 2** \\</span></span>
  [*https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2*](https://www.digitalocean.com/community/tutorials/an-introduction-to-oauth-2)

- <span data-ttu-id="48f8d-222">**AspNet.Security.OAuth.Providers** (ASP.NET OAuth sağlayıcıları için GitHub deposunu) \\</span><span class="sxs-lookup"><span data-stu-id="48f8d-222">**AspNet.Security.OAuth.Providers** (GitHub repo for ASP.NET OAuth providers) \\</span></span>
  [*https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src*](https://github.com/aspnet-contrib/AspNet.Security.OAuth.Providers/tree/dev/src)

- <span data-ttu-id="48f8d-223">**Danny Strockis. Azure AD'yi bir ASP.NET Core web uygulamasıyla tümleştirme** \\</span><span class="sxs-lookup"><span data-stu-id="48f8d-223">**Danny Strockis. Integrating Azure AD into an ASP.NET Core web app** \\</span></span>
  [*https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/*](https://azure.microsoft.com/resources/samples/active-directory-dotnet-webapp-openidconnect-aspnetcore/)

- <span data-ttu-id="48f8d-224">**Identityserver4. Resmi belgeleri** \\</span><span class="sxs-lookup"><span data-stu-id="48f8d-224">**IdentityServer4. Official documentation** \\</span></span>
  *<https://identityserver4.readthedocs.io/en/latest/>*

>[!div class="step-by-step"]
><span data-ttu-id="48f8d-225">[Önceki](../implement-resilient-applications/monitor-app-health.md)
>[İleri](authorization-net-microservices-web-applications.md)</span><span class="sxs-lookup"><span data-stu-id="48f8d-225">[Previous](../implement-resilient-applications/monitor-app-health.md)
[Next](authorization-net-microservices-web-applications.md)</span></span>
