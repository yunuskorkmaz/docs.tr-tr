---
title: ASP.NET Çekirdek kırma değişiklikleri
titleSuffix: ''
description: ASP.NET Core'daki kırılma değişikliklerini listeler.
ms.date: 03/27/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 95057425614d7c717154ecfb687db2b9a6ca4a18
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391253"
---
# <a name="aspnet-core-breaking-changes"></a><span data-ttu-id="aceda-103">ASP.NET Çekirdek kırma değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="aceda-103">ASP.NET Core breaking changes</span></span>

<span data-ttu-id="aceda-104">ASP.NET Core, .NET Core tarafından kullanılan web uygulaması geliştirme özelliklerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="aceda-104">ASP.NET Core provides the web app development features used by .NET Core.</span></span>

<span data-ttu-id="aceda-105">Aşağıdaki kesme değişiklikleri bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="aceda-105">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="aceda-106">Eski Antiforgery, CORS, Teşhis, MVC ve Yönlendirme API'leri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="aceda-106">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [<span data-ttu-id="aceda-107">Kimlik doğrulama: Google+ amortismanı</span><span class="sxs-lookup"><span data-stu-id="aceda-107">Authentication: Google+ deprecation</span></span>](#authentication-google-deprecated-and-replaced)
- [<span data-ttu-id="aceda-108">Kimlik doğrulama: HttpContext.Authentication özelliği kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="aceda-108">Authentication: HttpContext.Authentication property removed</span></span>](#authentication-httpcontextauthentication-property-removed)
- [<span data-ttu-id="aceda-109">Kimlik doğrulama: Newtonsoft.Json türleri değiştirildi</span><span class="sxs-lookup"><span data-stu-id="aceda-109">Authentication: Newtonsoft.Json types replaced</span></span>](#authentication-newtonsoftjson-types-replaced)
- [<span data-ttu-id="aceda-110">Kimlik doğrulama: OAuthHandler ExchangeCodeAsync imza değiştirildi</span><span class="sxs-lookup"><span data-stu-id="aceda-110">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [<span data-ttu-id="aceda-111">Yetkilendirme: AddAuthorization aşırı yükü farklı derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="aceda-111">Authorization: AddAuthorization overload moved to different assembly</span></span>](#authorization-addauthorization-overload-moved-to-different-assembly)
- [<span data-ttu-id="aceda-112">Yetkilendirme: IAllowAnonymous YetkilendirmeFilterContext.Filters kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="aceda-112">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [<span data-ttu-id="aceda-113">Yetkilendirme: IAuthorizationPolicyProvider uygulamaları yeni bir yöntem gerektirir</span><span class="sxs-lookup"><span data-stu-id="aceda-113">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [<span data-ttu-id="aceda-114">Azure: Microsoft tarafından önceden belirlenmiş Azure tümleştirme paketleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="aceda-114">Azure: Microsoft-prefixed Azure integration packages removed</span></span>](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [<span data-ttu-id="aceda-115">Önbelleğe alma: CompactOnMemoryPressure özelliği kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="aceda-115">Caching: CompactOnMemoryPressure property removed</span></span>](#caching-compactonmemorypressure-property-removed)
- [<span data-ttu-id="aceda-116">Önbelleğe alma: Microsoft.Extensions.Caching.SqlServer yeni SqlClient paketi kullanır</span><span class="sxs-lookup"><span data-stu-id="aceda-116">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [<span data-ttu-id="aceda-117">Önbelleğe alma: YanıtCaching "pubternal" türleri iç değiştirildi</span><span class="sxs-lookup"><span data-stu-id="aceda-117">Caching: ResponseCaching "pubternal" types changed to internal</span></span>](#caching-responsecaching-pubternal-types-changed-to-internal)
- [<span data-ttu-id="aceda-118">Veri Koruması: DataProtection.AzureStorage yeni Azure Depolama API'leri kullanır</span><span class="sxs-lookup"><span data-stu-id="aceda-118">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [<span data-ttu-id="aceda-119">Hosting: AspNetCoreModule V1 Windows Hosting Paketi kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="aceda-119">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [<span data-ttu-id="aceda-120">Barındırma: Genel ana bilgisayar Başlangıç yapıcı enjeksiyonu kısıtlar</span><span class="sxs-lookup"><span data-stu-id="aceda-120">Hosting: Generic host restricts Startup constructor injection</span></span>](#hosting-generic-host-restricts-startup-constructor-injection)
- [<span data-ttu-id="aceda-121">Barındırma: IIS işlem dışı uygulamalar için HTTPS yeniden yönlendirmesi etkin</span><span class="sxs-lookup"><span data-stu-id="aceda-121">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [<span data-ttu-id="aceda-122">Hosting: IHostingEnvironment ve IApplicationLifetime türleri değiştirildi</span><span class="sxs-lookup"><span data-stu-id="aceda-122">Hosting: IHostingEnvironment and IApplicationLifetime types replaced</span></span>](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="aceda-123">Barındırma: ObjectPoolProvider WebHostBuilder bağımlılıkları kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="aceda-123">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [<span data-ttu-id="aceda-124">HTTP: Tarayıcı SameSite değişiklikleri kimlik doğrulamayı etkiler</span><span class="sxs-lookup"><span data-stu-id="aceda-124">HTTP: Browser SameSite changes impact authentication</span></span>](#http-browser-samesite-changes-impact-authentication)
- [<span data-ttu-id="aceda-125">HTTP: VarsayılanHttpContext genişletilebilirlik kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="aceda-125">HTTP: DefaultHttpContext extensibility removed</span></span>](#http-defaulthttpcontext-extensibility-removed)
- [<span data-ttu-id="aceda-126">HTTP: Başlıkadları alanları yalnızca statik olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="aceda-126">HTTP: HeaderNames fields changed to static readonly</span></span>](#http-headernames-constants-changed-to-static-readonly)
- [<span data-ttu-id="aceda-127">HTTP: Yanıt gövde altyapı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="aceda-127">HTTP: Response body infrastructure changes</span></span>](#http-response-body-infrastructure-changes)
- [<span data-ttu-id="aceda-128">HTTP: Bazı çerez SameSite varsayılan değerleri değişti</span><span class="sxs-lookup"><span data-stu-id="aceda-128">HTTP: Some cookie SameSite default values changed</span></span>](#http-some-cookie-samesite-defaults-changed-to-none)
- [<span data-ttu-id="aceda-129">HTTP: Synchronous IO varsayılan olarak devre dışı</span><span class="sxs-lookup"><span data-stu-id="aceda-129">HTTP: Synchronous IO disabled by default</span></span>](#http-synchronous-io-disabled-in-all-servers)
- [<span data-ttu-id="aceda-130">Kimlik: AddDefaultUI yöntemi aşırı kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="aceda-130">Identity: AddDefaultUI method overload removed</span></span>](#identity-adddefaultui-method-overload-removed)
- [<span data-ttu-id="aceda-131">Kimlik: UI Bootstrap sürüm değişikliği</span><span class="sxs-lookup"><span data-stu-id="aceda-131">Identity: UI Bootstrap version change</span></span>](#identity-default-bootstrap-version-of-ui-changed)
- [<span data-ttu-id="aceda-132">Kimlik: SignInAsync kimliği doğrulanmamış kimlik için özel durum atar</span><span class="sxs-lookup"><span data-stu-id="aceda-132">Identity: SignInAsync throws exception for unauthenticated identity</span></span>](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [<span data-ttu-id="aceda-133">Kimlik: SignInManager constructor yeni parametre kabul eder</span><span class="sxs-lookup"><span data-stu-id="aceda-133">Identity: SignInManager constructor accepts new parameter</span></span>](#identity-signinmanager-constructor-accepts-new-parameter)
- [<span data-ttu-id="aceda-134">Kimlik: UI statik web varlıkları özelliğini kullanır</span><span class="sxs-lookup"><span data-stu-id="aceda-134">Identity: UI uses static web assets feature</span></span>](#identity-ui-uses-static-web-assets-feature)
- [<span data-ttu-id="aceda-135">Kerkenez: Bağlantı bağdaştırıcıları kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="aceda-135">Kestrel: Connection adapters removed</span></span>](#kestrel-connection-adapters-removed)
- [<span data-ttu-id="aceda-136">Kerkenez: Boş HTTPS derlemesi kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="aceda-136">Kestrel: Empty HTTPS assembly removed</span></span>](#kestrel-empty-https-assembly-removed)
- [<span data-ttu-id="aceda-137">Kerkenez: İstek römork başlıkları yeni koleksiyona taşındı</span><span class="sxs-lookup"><span data-stu-id="aceda-137">Kestrel: Request trailer headers moved to new collection</span></span>](#kestrel-request-trailer-headers-moved-to-new-collection)
- [<span data-ttu-id="aceda-138">Kerkenez: Taşıma soyutlama katmanı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="aceda-138">Kestrel: Transport abstraction layer changes</span></span>](#kestrel-transport-abstractions-removed-and-made-public)
- [<span data-ttu-id="aceda-139">Yerelleştirme: API'ler eski olarak işaretlenmiş</span><span class="sxs-lookup"><span data-stu-id="aceda-139">Localization: APIs marked obsolete</span></span>](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [<span data-ttu-id="aceda-140">Günlük: DebugLogger sınıfı dahili yaptı</span><span class="sxs-lookup"><span data-stu-id="aceda-140">Logging: DebugLogger class made internal</span></span>](#logging-debuglogger-class-made-internal)
- [<span data-ttu-id="aceda-141">MVC: Denetleyici eylem Async soneki kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="aceda-141">MVC: Controller action Async suffix removed</span></span>](#mvc-async-suffix-trimmed-from-controller-action-names)
- [<span data-ttu-id="aceda-142">MVC: JsonResult Microsoft.AspNetCore.Mvc.Core taşındı</span><span class="sxs-lookup"><span data-stu-id="aceda-142">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [<span data-ttu-id="aceda-143">MVC: Precompilation aracı amortismana</span><span class="sxs-lookup"><span data-stu-id="aceda-143">MVC: Precompilation tool deprecated</span></span>](#mvc-precompilation-tool-deprecated)
- [<span data-ttu-id="aceda-144">MVC: Türleri dahili olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="aceda-144">MVC: Types changed to internal</span></span>](#mvc-pubternal-types-changed-to-internal)
- [<span data-ttu-id="aceda-145">MVC: Web API uyumluluk şim kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="aceda-145">MVC: Web API compatibility shim removed</span></span>](#mvc-web-api-compatibility-shim-removed)
- [<span data-ttu-id="aceda-146">Razor: Runtime derleme bir paket taşındı</span><span class="sxs-lookup"><span data-stu-id="aceda-146">Razor: Runtime compilation moved to a package</span></span>](#razor-runtime-compilation-moved-to-a-package)
- [<span data-ttu-id="aceda-147">Oturum durumu: Eski API'ler kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="aceda-147">Session state: Obsolete APIs removed</span></span>](#session-state-obsolete-apis-removed)
- [<span data-ttu-id="aceda-148">Paylaşılan çerçeve: Microsoft.AspNetCore.App'ten derleme kaldırma</span><span class="sxs-lookup"><span data-stu-id="aceda-148">Shared framework: Assembly removal from Microsoft.AspNetCore.App</span></span>](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [<span data-ttu-id="aceda-149">Paylaşılan çerçeve: Microsoft.AspNetCore.All kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="aceda-149">Shared framework: Microsoft.AspNetCore.All removed</span></span>](#shared-framework-removed-microsoftaspnetcoreall)
- [<span data-ttu-id="aceda-150">SignalR: HandshakeProtocol.SuccessHandshakeData değiştirildi</span><span class="sxs-lookup"><span data-stu-id="aceda-150">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [<span data-ttu-id="aceda-151">SignalR: HubConnection yöntemleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="aceda-151">SignalR: HubConnection methods removed</span></span>](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [<span data-ttu-id="aceda-152">SignalR: HubConnectionContext yapıcılar değişti</span><span class="sxs-lookup"><span data-stu-id="aceda-152">SignalR: HubConnectionContext constructors changed</span></span>](#signalr-hubconnectioncontext-constructors-changed)
- [<span data-ttu-id="aceda-153">SignalR: JavaScript istemci paketi adı değişikliği</span><span class="sxs-lookup"><span data-stu-id="aceda-153">SignalR: JavaScript client package name change</span></span>](#signalr-javascript-client-package-name-changed)
- [<span data-ttu-id="aceda-154">SignalR: MessagePack Hub Protokolü MessagePack 2.x paketine taşındı</span><span class="sxs-lookup"><span data-stu-id="aceda-154">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [<span data-ttu-id="aceda-155">SignalR: Eski API'ler</span><span class="sxs-lookup"><span data-stu-id="aceda-155">SignalR: Obsolete APIs</span></span>](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [<span data-ttu-id="aceda-156">SignalR: UseSignalR ve UseConnections yöntemleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="aceda-156">SignalR: UseSignalR and UseConnections methods removed</span></span>](#signalr-usesignalr-and-useconnections-methods-removed)
- [<span data-ttu-id="aceda-157">SP'ler: SpaServices ve NodeServices logger geri dönüş varsayılan değişikliği konsol</span><span class="sxs-lookup"><span data-stu-id="aceda-157">SPAs: SpaServices and NodeServices console logger fallback default change</span></span>](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [<span data-ttu-id="aceda-158">STA'lar: SpaServices ve NodeServices eski işaretlenmiş</span><span class="sxs-lookup"><span data-stu-id="aceda-158">SPAs: SpaServices and NodeServices marked obsolete</span></span>](#spas-spaservices-and-nodeservices-marked-obsolete)
- [<span data-ttu-id="aceda-159">Statik dosyalar: CSV içerik türü standartlara uygun olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="aceda-159">Static files: CSV content type changed to standards-compliant</span></span>](#static-files-csv-content-type-changed-to-standards-compliant)
- [<span data-ttu-id="aceda-160">Hedef çerçeve: .NET Framework desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="aceda-160">Target framework: .NET Framework not supported</span></span>](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a><span data-ttu-id="aceda-161">ASP.NET Çekirdek 5.0</span><span class="sxs-lookup"><span data-stu-id="aceda-161">ASP.NET Core 5.0</span></span>

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-package.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

[!INCLUDE[Static files: CSV content type changed to standards-compliant](~/includes/core-changes/aspnetcore/5.0/static-files-csv-content-type-changed.md)]

***

## <a name="aspnet-core-31"></a><span data-ttu-id="aceda-162">ASP.NET Çekirdek 3.1</span><span class="sxs-lookup"><span data-stu-id="aceda-162">ASP.NET Core 3.1</span></span>

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a><span data-ttu-id="aceda-163">ASP.NET Çekirdek 3.0</span><span class="sxs-lookup"><span data-stu-id="aceda-163">ASP.NET Core 3.0</span></span>

[!INCLUDE[Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed](~/includes/core-changes/aspnetcore/3.0/obsolete-apis-removed.md)]

***

[!INCLUDE[Authentication: Google+ deprecation](~/includes/core-changes/aspnetcore/3.0/authn-google-plus-authn-changes.md)]

***

[!INCLUDE[Authentication: HttpContext.Authentication property removed](~/includes/core-changes/aspnetcore/3.0/authn-httpcontext-property-removed.md)]

***

[!INCLUDE[Authentication: Newtonsoft.Json types replaced](~/includes/core-changes/aspnetcore/3.0/authn-apis-json-types.md)]

***

[!INCLUDE[Authentication: OAuthHandler ExchangeCodeAsync signature changed](~/includes/core-changes/aspnetcore/3.0/authn-exchangecodeasync-signature-change.md)]

***

[!INCLUDE[Authorization: AddAuthorization overload assembly change](~/includes/core-changes/aspnetcore/3.0/authz-assembly-change.md)]

***

[!INCLUDE[Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters](~/includes/core-changes/aspnetcore/3.0/authz-iallowanonymous-removed-from-collection.md)]

***

[!INCLUDE[Authorization: IAuthorizationPolicyProvider implementations require new method](~/includes/core-changes/aspnetcore/3.0/authz-iauthzpolicyprovider-new-method.md)]

***

[!INCLUDE[Caching: CompactOnMemoryPressure property removed](~/includes/core-changes/aspnetcore/3.0/caching-memory-property-removed.md)]

***

[!INCLUDE[Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package](~/includes/core-changes/aspnetcore/3.0/caching-new-sqlclient-package.md)]

***

[!INCLUDE[Caching: ResponseCaching types changed to internal](~/includes/core-changes/aspnetcore/3.0/caching-response-pubternal-to-internal.md)]

***

[!INCLUDE[Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs](~/includes/core-changes/aspnetcore/3.0/dataprotection-azstorage-using-azstorage-apis.md)]

***

[!INCLUDE[Hosting: ANCM version 1 removed from hosting bundle](~/includes/core-changes/aspnetcore/3.0/hosting-ancmv1-hosting-bundle-removal.md)]

***

[!INCLUDE[Hosting: Generic host restriction on Startup constructor injection](~/includes/core-changes/aspnetcore/3.0/hosting-generic-host-startup-ctor-restriction.md)]

***

[!INCLUDE[Hosting: HTTPS redirection enabled for IIS OutOfProcess](~/includes/core-changes/aspnetcore/3.0/hosting-https-redirection-iis-outofprocess.md)]

***

[!INCLUDE[Hosting: IHostingEnvironment and IApplicationLifetime types replaced](~/includes/core-changes/aspnetcore/3.0/hosting-ihostingenv-iapplifetime-types-replaced.md)]

***

[!INCLUDE[Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies](~/includes/core-changes/aspnetcore/3.0/hosting-objectpoolprovider-webhostbuilder-dependencies.md)]

***

[!INCLUDE[HTTP: DefaultHttpContext extensibility removed](~/includes/core-changes/aspnetcore/3.0/http-defaulthttpcontext-extensibility-removed.md)]

***

[!INCLUDE[HTTP: HeaderNames fields changed to static readonly](~/includes/core-changes/aspnetcore/3.0/http-headernames-constants-staticreadonly.md)]

***

[!INCLUDE[HTTP: Response body infrastructure changes](~/includes/core-changes/aspnetcore/3.0/http-response-body-changes.md)]

***

[!INCLUDE[HTTP: Some cookie SameSite default values changed](~/includes/core-changes/aspnetcore/3.0/http-cookie-samesite-defaults-change.md)]

***

[!INCLUDE[HTTP: Synchronous IO disabled by default](~/includes/core-changes/aspnetcore/3.0/http-synchronous-io-disabled.md)]

***

[!INCLUDE[Identity: AddDefaultUI method overload removed](~/includes/core-changes/aspnetcore/3.0/identity-ui-adddefaultui-overload-removed.md)]

***

[!INCLUDE[Identity: UI Bootstrap version change](~/includes/core-changes/aspnetcore/3.0/identity-ui-bootstrap-version.md)]

***

[!INCLUDE[Identity: SignInAsync throws exception for unauthenticated identity](~/includes/core-changes/aspnetcore/3.0/identity-signinasync-throws-exception.md)]

***

[!INCLUDE[Identity: SignInManager constructor accepts new parameter](~/includes/core-changes/aspnetcore/3.0/identity-signinmanager-ctor-parameter.md)]

***

[!INCLUDE[Identity: UI uses static web assets feature](~/includes/core-changes/aspnetcore/3.0/identity-ui-static-web-assets.md)]

***

[!INCLUDE[Kestrel: Connection adapters removed](~/includes/core-changes/aspnetcore/3.0/kestrel-connection-adapters-removed.md)]

***

[!INCLUDE[Kestrel: Empty HTTPS assembly removed](~/includes/core-changes/aspnetcore/3.0/kestrel-empty-assembly-removed.md)]

***

[!INCLUDE[Kestrel: Request trailer headers moved to new collection](~/includes/core-changes/aspnetcore/3.0/kestrel-request-trailer-headers.md)]

***

[!INCLUDE[Kestrel: Transport abstraction layer changes](~/includes/core-changes/aspnetcore/3.0/kestrel-transport-abstractions.md)]

***

[!INCLUDE[Localization: APIs marked obsolete](~/includes/core-changes/aspnetcore/3.0/localization-apis-marked-obsolete.md)]

***

[!INCLUDE[Logging: DebugLogger class made internal](~/includes/core-changes/aspnetcore/3.0/logging-debuglogger-to-internal.md)]

***

[!INCLUDE[MVC: Controller action Async suffix removed](~/includes/core-changes/aspnetcore/3.0/mvc-action-async-suffix-trimmed.md)]

***

[!INCLUDE[MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core](~/includes/core-changes/aspnetcore/3.0/mvc-jsonresult-moved.md)]

***

[!INCLUDE[MVC: Precompilation tool deprecated](~/includes/core-changes/aspnetcore/3.0/mvc-precompilation-tool-deprecated.md)]

***

[!INCLUDE[MVC: Types changed to internal](~/includes/core-changes/aspnetcore/3.0/mvc-pubternal-to-internal.md)]

***

[!INCLUDE[MVC: Web API compatibility shim removed](~/includes/core-changes/aspnetcore/3.0/mvc-webapi-compat-shim-removed.md)]

***

[!INCLUDE[Razor: Runtime compilation moved to a package](~/includes/core-changes/aspnetcore/3.0/razor-runtime-compilation-package.md)]

***

[!INCLUDE[Session state: Obsolete APIs removed](~/includes/core-changes/aspnetcore/3.0/session-obsolete-apis-removed.md)]

***

[!INCLUDE[Shared framework: Assembly removal from Microsoft.AspNetCore.App](~/includes/core-changes/aspnetcore/3.0/sharedfx-app-shared-framework-assemblies.md)]

***

[!INCLUDE[Shared framework: Microsoft.AspNetCore.All removed](~/includes/core-changes/aspnetcore/3.0/sharedfx-all-framework-removed.md)]

***

[!INCLUDE[SignalR: HandshakeProtocol.SuccessHandshakeData replaced](~/includes/core-changes/aspnetcore/3.0/signalr-successhandshakedata-replaced.md)]

***

[!INCLUDE[SignalR: HubConnection methods removed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnection-methods-removed.md)]

***

[!INCLUDE[SignalR: HubConnectionContext constructors changed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnectioncontext-ctors.md)]

***

[!INCLUDE[SignalR: JavaScript client package name change](~/includes/core-changes/aspnetcore/3.0/signalr-js-client-package-name.md)]

***

[!INCLUDE[SignalR: Obsolete APIs](~/includes/core-changes/aspnetcore/3.0/signalr-obsolete-apis.md)]

***

[!INCLUDE[SPAs: SpaServices and NodeServices marked obsolete](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-obsolete.md)]

***

[!INCLUDE[SPAs: SpaServices and NodeServices console logger fallback default change](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-fallback.md)]

***

[!INCLUDE[Target framework: .NET Framework not supported](~/includes/core-changes/aspnetcore/3.0/targetfx-netfx-tfm-support.md)]

***
