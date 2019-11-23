---
title: Cloud Native uygulamalar için IdentityServer
description: Azure için Cloud Native .NET uygulamaları tasarlama | IdentityServer
ms.date: 06/30/2019
ms.openlocfilehash: 3797214685d20109b2c5dc4440ae5fc64dfddce6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087261"
---
# <a name="identityserver-for-cloud-native-applications"></a><span data-ttu-id="e9bdb-103">Bulutta yerel uygulamalar için IdentityServer</span><span class="sxs-lookup"><span data-stu-id="e9bdb-103">IdentityServer for cloud-native applications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="e9bdb-104">IdentityServer, ASP.NET Core için OpenID Connect (OıDC) ve OAuth 2,0 standartları uygulayan açık kaynaklı bir kimlik doğrulama sunucusudur.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-104">IdentityServer is an open-source authentication server that implements OpenID Connect (OIDC) and OAuth 2.0 standards for ASP.NET Core.</span></span> <span data-ttu-id="e9bdb-105">Web, yerel, mobil veya API uç noktaları olsun, tüm uygulamalarınıza yönelik isteklerin kimliklerinin doğrulanması için ortak bir yol sağlamak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-105">It's designed to provide a common way to authenticate requests to all of your applications, whether they're web, native, mobile, or API endpoints.</span></span> <span data-ttu-id="e9bdb-106">IdentityServer, birden çok uygulama ve uygulama türü için çoklu oturum açma (SSO) uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-106">IdentityServer can be used to implement Single Sign-On (SSO) for multiple applications and application types.</span></span> <span data-ttu-id="e9bdb-107">Kullanıcı arabirimi olmadan, genellikle belirteç verme, doğrulama ve yenileme içeren hizmet tabanlı kimlik doğrulaması ile, oturum açma formları ve benzer kullanıcı arabirimleri aracılığıyla gerçek kullanıcıların kimliğini doğrulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-107">It can be used to authenticate actual users via sign-in forms and similar user interfaces as well as service-based authentication that typically involves token issuance, verification, and renewal without any user interface.</span></span> <span data-ttu-id="e9bdb-108">IdentityServer, özelleştirilebilir bir çözüm olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-108">IdentityServer is designed to be a customizable solution.</span></span> <span data-ttu-id="e9bdb-109">Her örnek genellikle tek bir kuruluşa ve/veya uygulama gereksinimlerine uyacak şekilde özelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-109">Each instance is typically customized to suit an individual organization and/or set of applications' needs.</span></span>

## <a name="common-web-app-scenarios"></a><span data-ttu-id="e9bdb-110">Ortak Web uygulaması senaryoları</span><span class="sxs-lookup"><span data-stu-id="e9bdb-110">Common web app scenarios</span></span>

<span data-ttu-id="e9bdb-111">Genellikle, uygulamaların aşağıdaki senaryolardan bazılarını veya tümünü desteklemesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="e9bdb-111">Typically, applications need to support some or all of the following scenarios:</span></span>

- <span data-ttu-id="e9bdb-112">İnsan kullanıcıları Web uygulamalarına bir tarayıcıyla erişiyor.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-112">Human users accessing web applications with a browser.</span></span>
- <span data-ttu-id="e9bdb-113">Tarayıcı tabanlı uygulamalardan arka uç Web API 'Lerine erişen insan kullanıcıları.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-113">Human users accessing back-end Web APIs from browser-based apps.</span></span>
- <span data-ttu-id="e9bdb-114">Mobil/yerel istemcilerde, arka uç Web API 'Lerine erişen insan kullanıcıları.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-114">Human users on mobile/native clients accessing back-end Web APIs.</span></span>
- <span data-ttu-id="e9bdb-115">Arka uç Web API 'Lerine erişen diğer uygulamalar (etkin bir kullanıcı veya Kullanıcı arabirimi olmadan).</span><span class="sxs-lookup"><span data-stu-id="e9bdb-115">Other applications accessing back-end Web APIs (without an active user or user interface).</span></span>
- <span data-ttu-id="e9bdb-116">Herhangi bir uygulamanın kendi kimliğini kullanarak veya kullanıcının kimliğine temsilci atamak için diğer Web API 'Leriyle etkileşmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-116">Any application may need to interact with other Web APIs, using its own identity or delegating to the user's identity.</span></span>

<span data-ttu-id="e9bdb-117">**şekil 8-1**](./media/application-types.png)
uygulama türlerini ve senaryolarını ![.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-117">![Application types and scenarios](./media/application-types.png)
**Figure 8-1**.</span></span> <span data-ttu-id="e9bdb-118">Uygulama türleri ve senaryolar.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-118">Application types and scenarios.</span></span>

<span data-ttu-id="e9bdb-119">Bu senaryoların her birinde, sunulan işlevlerin yetkisiz kullanıma karşı korunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-119">In each of these scenarios, the exposed functionality needs to be secured against unauthorized use.</span></span> <span data-ttu-id="e9bdb-120">Bu, genellikle bir kaynak için istek yapan kullanıcının veya sorumlunun kimlik doğrulamasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-120">At a minimum, this typically requires authenticating the user or principal making a request for a resource.</span></span> <span data-ttu-id="e9bdb-121">Bu kimlik doğrulaması SAML2p, WS-beslenir veya OpenID Connect gibi birkaç ortak protokolden birini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-121">This authentication may use one of several common protocols such as SAML2p, WS-Fed, or OpenID Connect.</span></span> <span data-ttu-id="e9bdb-122">API 'lerle iletişim kurmak genellikle OAuth2 protokolünü ve güvenlik belirteçleri desteğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-122">Communicating with APIs typically uses the OAuth2 protocol and its support for security tokens.</span></span> <span data-ttu-id="e9bdb-123">Bu kritik çapraz güvenlik sorunlarının ve uygulama ayrıntılarının uygulamalardan ayrılması, tutarlılığı sağlar ve güvenlik ve bakım özelliklerini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-123">Separating these critical cross-cutting security concerns and their implementation details from the applications themselves ensures consistency and improves security and maintainability.</span></span> <span data-ttu-id="e9bdb-124">Bu kaygıları IdentityServer gibi özel bir ürünle dış olarak eklemek, her uygulamanın bu sorunların kendisini çözmesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-124">Outsourcing these concerns to a dedicated product like IdentityServer helps the requirement for every application to solve these problems itself.</span></span>

<span data-ttu-id="e9bdb-125">IdentityServer, bir ASP.NET Core uygulaması içinde çalışan ara yazılım sağlar ve OpenID Connect ve OAuth2 için destek ekler (bkz. [desteklenen özellikler](http://docs.identityserver.io/en/latest/intro/specs.html)).</span><span class="sxs-lookup"><span data-stu-id="e9bdb-125">IdentityServer provides middleware that runs within an ASP.NET Core application and adds support for OpenID Connect and OAuth2 (see [supported specifications](http://docs.identityserver.io/en/latest/intro/specs.html)).</span></span> <span data-ttu-id="e9bdb-126">Kuruluşlar, tüm belirteç tabanlı güvenlik protokollerinde STS görevi gören IdentityServer ara yazılımını kullanarak kendi ASP.NET Core uygulamalarını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-126">Organizations would create their own ASP.NET Core app using IdentityServer middleware to act as the STS for all of their token-based security protocols.</span></span> <span data-ttu-id="e9bdb-127">IdentityServer ara yazılımı, aşağıdakiler dahil olmak üzere standart işlevleri desteklemek için uç noktalar sunar:</span><span class="sxs-lookup"><span data-stu-id="e9bdb-127">The IdentityServer middleware exposes endpoints to support standard functionality, including:</span></span>

- <span data-ttu-id="e9bdb-128">Yetkilendirme (son kullanıcının kimliğini doğrulama)</span><span class="sxs-lookup"><span data-stu-id="e9bdb-128">Authorize (authenticate the end user)</span></span>
- <span data-ttu-id="e9bdb-129">Belirteç (bir belirteci programlama yoluyla isteme)</span><span class="sxs-lookup"><span data-stu-id="e9bdb-129">Token (request a token programmatically)</span></span>
- <span data-ttu-id="e9bdb-130">Bulma (sunucu hakkındaki meta veriler)</span><span class="sxs-lookup"><span data-stu-id="e9bdb-130">Discovery (metadata about the server)</span></span>
- <span data-ttu-id="e9bdb-131">Kullanıcı bilgileri (geçerli bir erişim belirteciyle Kullanıcı bilgilerini al)</span><span class="sxs-lookup"><span data-stu-id="e9bdb-131">User Info (get user information with a valid access token)</span></span>
- <span data-ttu-id="e9bdb-132">Cihaz yetkilendirmesi (cihaz akışı yetkilendirmesini başlatmak için kullanılır)</span><span class="sxs-lookup"><span data-stu-id="e9bdb-132">Device Authorization (used to start device flow authorization)</span></span>
- <span data-ttu-id="e9bdb-133">İç denetim (belirteç doğrulama)</span><span class="sxs-lookup"><span data-stu-id="e9bdb-133">Introspection (token validation)</span></span>
- <span data-ttu-id="e9bdb-134">İptal (belirteç iptali)</span><span class="sxs-lookup"><span data-stu-id="e9bdb-134">Revocation (token revocation)</span></span>
- <span data-ttu-id="e9bdb-135">Oturumu sonlandır (tüm uygulamalarda çoklu oturum açmayı Tetikle)</span><span class="sxs-lookup"><span data-stu-id="e9bdb-135">End Session (trigger single sign-out across all apps)</span></span>

## <a name="getting-started"></a><span data-ttu-id="e9bdb-136">Başlarken</span><span class="sxs-lookup"><span data-stu-id="e9bdb-136">Getting started</span></span>

<span data-ttu-id="e9bdb-137">Identityserver4 açık kaynak ve ücretsiz olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-137">IdentityServer4 is open-source and free to use.</span></span> <span data-ttu-id="e9bdb-138">Bunu, NuGet paketlerini kullanarak uygulamalarınıza ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-138">You can add it to your applications using its NuGet packages.</span></span> <span data-ttu-id="e9bdb-139">Ana paket, 4.000.000 defa indirilen [ıdentityserver4](https://www.nuget.org/packages/IdentityServer4/) .</span><span class="sxs-lookup"><span data-stu-id="e9bdb-139">The main package is [IdentityServer4](https://www.nuget.org/packages/IdentityServer4/) that has been downloaded over four million times.</span></span> <span data-ttu-id="e9bdb-140">Temel paket, herhangi bir kullanıcı arabirimi kodu içermez ve yalnızca bellek yapılandırmasında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-140">The base package doesn't include any user interface code and only supports in memory configuration.</span></span> <span data-ttu-id="e9bdb-141">Veritabanını bir veritabanıyla birlikte kullanmak için, IdentityServer için yapılandırma ve işletimsel verileri depolamak üzere Entity Framework Core kullanan [ıdentityserver4. EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) gibi bir veri sağlayıcısı da isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-141">To use it with a database, you'll also want a data provider like [IdentityServer4.EntityFramework](https://www.nuget.org/packages/IdentityServer4.EntityFramework) that uses Entity Framework Core to store configuration and operational data for IdentityServer.</span></span> <span data-ttu-id="e9bdb-142">Kullanıcı arabirimi için, oturum açma için destek eklemek ve IdentityServer ara yazılımını kullanarak oturumu kapatmak için [hızlı başlangıç Kullanıcı arabirimi deposundan](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI) ASP.NET Core MVC Uygulamanıza dosya kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-142">For user interface, you can copy files from the [Quickstart UI repository](https://github.com/IdentityServer/IdentityServer4.Quickstart.UI) into your ASP.NET Core MVC application to add support for sign in and sign out using IdentityServer middleware.</span></span>

## <a name="configuration"></a><span data-ttu-id="e9bdb-143">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e9bdb-143">Configuration</span></span>

<span data-ttu-id="e9bdb-144">IdentityServer, her bir özel yüklemenin parçası olarak yapılandırılabilen farklı protokol türlerini ve sosyal kimlik doğrulama sağlayıcılarını destekler.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-144">IdentityServer supports different kinds of protocols and social authentication providers that can be configured as part of each custom installation.</span></span> <span data-ttu-id="e9bdb-145">Bu, genellikle `ConfigureServices` yönteminde ASP.NET Core uygulamasının `Startup` sınıfında yapılır.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-145">This is typically done in the ASP.NET Core application's `Startup` class in the `ConfigureServices` method.</span></span> <span data-ttu-id="e9bdb-146">Yapılandırma desteklenen protokollerin ve kullanılacak sunucuların ve uç noktaların yollarını belirtmeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-146">The configuration involves specifying the supported protocols and the paths to the servers and endpoints that will be used.</span></span> <span data-ttu-id="e9bdb-147">Şekil 8-2, ıdentityserver4 hızlı başlangıç Kullanıcı arabirimi projesinden alınan bir örnek yapılandırmayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="e9bdb-147">Figure 8-2 shows an example configuration taken from the IdentityServer4 Quickstart UI project:</span></span>

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();

        // some details omitted
        services.AddIdentityServer();

          services.AddAuthentication()
            .AddGoogle("Google", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;

                options.ClientId = "<insert here>";
                options.ClientSecret = "<inser here>";
            })
            .AddOpenIdConnect("demoidsrv", "IdentityServer", options =>
            {
                options.SignInScheme = IdentityServerConstants.ExternalCookieAuthenticationScheme;
                options.SignOutScheme = IdentityServerConstants.SignoutScheme;

                options.Authority = "https://demo.identityserver.io/";
                options.ClientId = "implicit";
                options.ResponseType = "id_token";
                options.SaveTokens = true;
                options.CallbackPath = new PathString("/signin-idsrv");
                options.SignedOutCallbackPath = new PathString("/signout-callback-idsrv");
                options.RemoteSignOutPath = new PathString("/signout-idsrv");

                options.TokenValidationParameters = new TokenValidationParameters
                {
                    NameClaimType = "name",
                    RoleClaimType = "role"
                };
            });
    }
}
```

<span data-ttu-id="e9bdb-148">**Şekil 8-2**.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-148">**Figure 8-2**.</span></span> <span data-ttu-id="e9bdb-149">IdentityServer yapılandırılıyor.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-149">Configuring IdentityServer.</span></span>

<span data-ttu-id="e9bdb-150">IdentityServer, çeşitli protokolleri ve konfigürasyonları test etmek için kullanılabilecek bir genel tanıtım sitesi de barındırır.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-150">IdentityServer also hosts a public demo site that can be used to test various protocols and configurations.</span></span> <span data-ttu-id="e9bdb-151">[https://demo.identityserver.io/](https://demo.identityserver.io/) konumunda bulunur ve kendisine sunulan `client_id` göre davranışının nasıl yapılandırılacağı hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-151">It's located at [https://demo.identityserver.io/](https://demo.identityserver.io/) and includes information on how to configure its behavior based on the `client_id` provided to it.</span></span>

## <a name="javascript-clients"></a><span data-ttu-id="e9bdb-152">JavaScript istemcileri</span><span class="sxs-lookup"><span data-stu-id="e9bdb-152">JavaScript clients</span></span>

<span data-ttu-id="e9bdb-153">Birçok bulutta yerel uygulama, Ön uçtaki sunucu tarafı API 'Leri ve zengin istemci tek sayfa uygulamaları (maça 'lar) ile faydalanır.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-153">Many cloud-native applications leverage server-side APIs and rich client single page applications (SPAs) on the front end.</span></span> <span data-ttu-id="e9bdb-154">IdentityServer, oturum açma, oturumu kapatma ve Web API 'lerinin belirteç tabanlı kimlik doğrulaması için IdentityServer 'ı kullanabilmesi amacıyla, NPM aracılığıyla bir [JavaScript istemcisi](http://docs.identityserver.io/en/latest/quickstarts/6_javascript_client.html) (`oidc-client.js`) sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-154">IdentityServer ships a [JavaScript client](http://docs.identityserver.io/en/latest/quickstarts/6_javascript_client.html) (`oidc-client.js`) via NPM that can be added to SPAs to enable them to use IdentityServer for sign in, sign out, and token-based authentication of web APIs.</span></span>

## <a name="references"></a><span data-ttu-id="e9bdb-155">Referanslar</span><span class="sxs-lookup"><span data-stu-id="e9bdb-155">References</span></span>

- [<span data-ttu-id="e9bdb-156">IdentityServer belgeleri</span><span class="sxs-lookup"><span data-stu-id="e9bdb-156">IdentityServer documentation</span></span>](http://docs.identityserver.io/en/latest/)
- [<span data-ttu-id="e9bdb-157">Uygulama türleri</span><span class="sxs-lookup"><span data-stu-id="e9bdb-157">Application types</span></span>](https://docs.microsoft.com/azure/active-directory/develop/app-types)
- [<span data-ttu-id="e9bdb-158">JavaScript OıDC istemcisi</span><span class="sxs-lookup"><span data-stu-id="e9bdb-158">JavaScript OIDC client</span></span>](http://docs.identityserver.io/en/latest/quickstarts/6_javascript_client.html)

>[!div class="step-by-step"]
><span data-ttu-id="e9bdb-159">[Önceki](azure-active-directory.md)
>[İleri](security.md)</span><span class="sxs-lookup"><span data-stu-id="e9bdb-159">[Previous](azure-active-directory.md)
[Next](security.md)</span></span>
