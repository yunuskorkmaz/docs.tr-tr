---
title: ASP.NET Core son değişiklikler
titleSuffix: ''
description: ASP.NET Core 'deki son değişiklikleri listeler.
ms.date: 07/10/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 1a3c8b04bc574822f1576ca0720ed7a01c303880
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281686"
---
# <a name="aspnet-core-breaking-changes"></a><span data-ttu-id="96b83-103">ASP.NET Core son değişiklikler</span><span class="sxs-lookup"><span data-stu-id="96b83-103">ASP.NET Core breaking changes</span></span>

<span data-ttu-id="96b83-104">ASP.NET Core .NET Core tarafından kullanılan Web uygulaması geliştirme özelliklerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="96b83-104">ASP.NET Core provides the web app development features used by .NET Core.</span></span>

<span data-ttu-id="96b83-105">Aşağıdaki son değişiklikler bu sayfada belgelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="96b83-105">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="96b83-106">Kullanılmayan Antiforgery, CORS, tanılama, MVC ve yönlendirme API 'Leri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="96b83-106">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [<span data-ttu-id="96b83-107">Kimlik doğrulaması: Google + kullanımdan kaldırma</span><span class="sxs-lookup"><span data-stu-id="96b83-107">Authentication: Google+ deprecation</span></span>](#authentication-google-deprecated-and-replaced)
- [<span data-ttu-id="96b83-108">Kimlik doğrulaması: HttpContext. Authentication özelliği kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="96b83-108">Authentication: HttpContext.Authentication property removed</span></span>](#authentication-httpcontextauthentication-property-removed)
- [<span data-ttu-id="96b83-109">Kimlik doğrulaması: değiştirilmekte olan türler üzerinde Newtonsoft.Js</span><span class="sxs-lookup"><span data-stu-id="96b83-109">Authentication: Newtonsoft.Json types replaced</span></span>](#authentication-newtonsoftjson-types-replaced)
- [<span data-ttu-id="96b83-110">Kimlik doğrulaması: OAuthHandler ExchangeCodeAsync imzası değişti</span><span class="sxs-lookup"><span data-stu-id="96b83-110">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [<span data-ttu-id="96b83-111">Yetkilendirme: Addaduthorleştirme aşırı yüklemesi farklı bir derlemeye taşındı</span><span class="sxs-lookup"><span data-stu-id="96b83-111">Authorization: AddAuthorization overload moved to different assembly</span></span>](#authorization-addauthorization-overload-moved-to-different-assembly)
- [<span data-ttu-id="96b83-112">Yetkilendirme: ıallowanonymous, AuthorizationFilterContext. Filters öğesinden kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="96b83-112">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [<span data-ttu-id="96b83-113">Yetkilendirme: ıauthorizationpolicyprovider uygulamaları için yeni yöntem gerekir</span><span class="sxs-lookup"><span data-stu-id="96b83-113">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [<span data-ttu-id="96b83-114">Azure: Microsoft 'un ön eki olan Azure tümleştirme paketleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="96b83-114">Azure: Microsoft-prefixed Azure integration packages removed</span></span>](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [<span data-ttu-id="96b83-115">Blazor: derleme zamanında bileşenlerden çok önemli olan boşluk</span><span class="sxs-lookup"><span data-stu-id="96b83-115">Blazor: Insignificant whitespace trimmed from components at compile time</span></span>](#blazor-insignificant-whitespace-trimmed-from-components-at-compile-time)
- [<span data-ttu-id="96b83-116">Önbelleğe alma: CompactOnMemoryPressure özelliği kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="96b83-116">Caching: CompactOnMemoryPressure property removed</span></span>](#caching-compactonmemorypressure-property-removed)
- [<span data-ttu-id="96b83-117">Önbelleğe alma: Microsoft. Extensions. Caching. SqlServer yeni SqlClient paketini kullanır</span><span class="sxs-lookup"><span data-stu-id="96b83-117">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [<span data-ttu-id="96b83-118">Önbelleğe alma: ResponseCaching "pubternal" türleri iç olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="96b83-118">Caching: ResponseCaching "pubternal" types changed to internal</span></span>](#caching-responsecaching-pubternal-types-changed-to-internal)
- [<span data-ttu-id="96b83-119">Veri koruma: DataProtection. AzureStorage yeni Azure depolama API 'Lerini kullanır</span><span class="sxs-lookup"><span data-stu-id="96b83-119">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [<span data-ttu-id="96b83-120">Uzantılar: bazı NuGet paketlerini etkileyen paket başvuru değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="96b83-120">Extensions: Package reference changes affecting some NuGet packages</span></span>](#extensions-package-reference-changes-affecting-some-nuget-packages)
- [<span data-ttu-id="96b83-121">Barındırma: AspNetCoreModule v1 Windows barındırma paketinden kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="96b83-121">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [<span data-ttu-id="96b83-122">Barındırma: genel ana bilgisayar, başlangıç Oluşturucu ekleme işlemini kısıtlar</span><span class="sxs-lookup"><span data-stu-id="96b83-122">Hosting: Generic host restricts Startup constructor injection</span></span>](#hosting-generic-host-restricts-startup-constructor-injection)
- [<span data-ttu-id="96b83-123">Barındırma: IIS işlem dışı uygulamalar için HTTPS yönlendirmesi etkinleştirildi</span><span class="sxs-lookup"><span data-stu-id="96b83-123">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [<span data-ttu-id="96b83-124">Barındırma: ıhostingenvironment ve ıapplicationlifetime türleri değişti</span><span class="sxs-lookup"><span data-stu-id="96b83-124">Hosting: IHostingEnvironment and IApplicationLifetime types replaced</span></span>](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="96b83-125">Barındırma: ObjectPoolProvider WebHostBuilder bağımlılıklarından kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="96b83-125">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [<span data-ttu-id="96b83-126">HTTP: Kestrel ve IIS BadHttpRequestException türleri artık kullanılmıyor ve değiştirilmiş olarak işaretlendi</span><span class="sxs-lookup"><span data-stu-id="96b83-126">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>](#http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="96b83-127">HTTP: Browser SameSite değişikliklerinin etkisi kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="96b83-127">HTTP: Browser SameSite changes impact authentication</span></span>](#http-browser-samesite-changes-impact-authentication)
- [<span data-ttu-id="96b83-128">HTTP: DefaultHttpContext genişletilebilirliği kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="96b83-128">HTTP: DefaultHttpContext extensibility removed</span></span>](#http-defaulthttpcontext-extensibility-removed)
- [<span data-ttu-id="96b83-129">HTTP: HeaderNames alanları statik ReadOnly olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="96b83-129">HTTP: HeaderNames fields changed to static readonly</span></span>](#http-headernames-constants-changed-to-static-readonly)
- [<span data-ttu-id="96b83-130">HTTP: ıhttpclientfactory günlük tamsayı durum kodları tarafından oluşturulan HttpClient örnekleri</span><span class="sxs-lookup"><span data-stu-id="96b83-130">HTTP: HttpClient instances created by IHttpClientFactory log integer status codes</span></span>](#http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes)
- [<span data-ttu-id="96b83-131">HTTP: yanıt gövdesi altyapı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="96b83-131">HTTP: Response body infrastructure changes</span></span>](#http-response-body-infrastructure-changes)
- [<span data-ttu-id="96b83-132">HTTP: bazı tanımlama bilgisi SameSite varsayılan değerleri değiştirildi</span><span class="sxs-lookup"><span data-stu-id="96b83-132">HTTP: Some cookie SameSite default values changed</span></span>](#http-some-cookie-samesite-defaults-changed-to-none)
- [<span data-ttu-id="96b83-133">HTTP: zaman uyumlu GÇ varsayılan olarak devre dışıdır</span><span class="sxs-lookup"><span data-stu-id="96b83-133">HTTP: Synchronous IO disabled by default</span></span>](#http-synchronous-io-disabled-in-all-servers)
- [<span data-ttu-id="96b83-134">HttpSys: Istemci sertifikası yeniden anlaşması varsayılan olarak devre dışıdır</span><span class="sxs-lookup"><span data-stu-id="96b83-134">HttpSys: Client certificate renegotiation disabled by default</span></span>](#httpsys-client-certificate-renegotiation-disabled-by-default)
- [<span data-ttu-id="96b83-135">Kimlik: Adddefaultuı yöntemi aşırı yüklemesi kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="96b83-135">Identity: AddDefaultUI method overload removed</span></span>](#identity-adddefaultui-method-overload-removed)
- [<span data-ttu-id="96b83-136">Kimlik: UI önyükleme sürümü değişikliği</span><span class="sxs-lookup"><span data-stu-id="96b83-136">Identity: UI Bootstrap version change</span></span>](#identity-default-bootstrap-version-of-ui-changed)
- [<span data-ttu-id="96b83-137">Kimlik: Signınasync kimliği doğrulanmamış kimlik için özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="96b83-137">Identity: SignInAsync throws exception for unauthenticated identity</span></span>](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [<span data-ttu-id="96b83-138">Kimlik: SignInManager Oluşturucusu yeni parametreyi kabul ediyor</span><span class="sxs-lookup"><span data-stu-id="96b83-138">Identity: SignInManager constructor accepts new parameter</span></span>](#identity-signinmanager-constructor-accepts-new-parameter)
- [<span data-ttu-id="96b83-139">Kimlik: UI statik Web varlıkları özelliğini kullanır</span><span class="sxs-lookup"><span data-stu-id="96b83-139">Identity: UI uses static web assets feature</span></span>](#identity-ui-uses-static-web-assets-feature)
- [<span data-ttu-id="96b83-140">IIS: URL yeniden yazma ara yazılımı sorgu dizeleri korunur</span><span class="sxs-lookup"><span data-stu-id="96b83-140">IIS: UrlRewrite middleware query strings are preserved</span></span>](#iis-urlrewrite-middleware-query-strings-are-preserved)
- [<span data-ttu-id="96b83-141">Kestrel: çalışma zamanında varsayılan olarak algılanan yapılandırma değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="96b83-141">Kestrel: Configuration changes at run time detected by default</span></span>](#kestrel-configuration-changes-at-run-time-detected-by-default)
- [<span data-ttu-id="96b83-142">Kestrel: bağlantı bağdaştırıcıları kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="96b83-142">Kestrel: Connection adapters removed</span></span>](#kestrel-connection-adapters-removed)
- [<span data-ttu-id="96b83-143">Kestrel: desteklenen varsayılan TLS protokol sürümleri değiştirildi</span><span class="sxs-lookup"><span data-stu-id="96b83-143">Kestrel: Default supported TLS protocol versions changed</span></span>](#kestrel-default-supported-tls-protocol-versions-changed)
- [<span data-ttu-id="96b83-144">Kestrel: boş HTTPS derlemesi kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="96b83-144">Kestrel: Empty HTTPS assembly removed</span></span>](#kestrel-empty-https-assembly-removed)
- [<span data-ttu-id="96b83-145">Kestrel: HTTP/2 uyumsuz Windows sürümlerinde TLS üzerinden devre dışı bırakıldı</span><span class="sxs-lookup"><span data-stu-id="96b83-145">Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions</span></span>](#kestrel-http2-disabled-over-tls-on-incompatible-windows-versions)
- [<span data-ttu-id="96b83-146">Kestrel: yeni koleksiyona taşınan artbilgisi üstbilgileri ıste</span><span class="sxs-lookup"><span data-stu-id="96b83-146">Kestrel: Request trailer headers moved to new collection</span></span>](#kestrel-request-trailer-headers-moved-to-new-collection)
- [<span data-ttu-id="96b83-147">Kestrel: aktarım soyutlama katmanı değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="96b83-147">Kestrel: Transport abstraction layer changes</span></span>](#kestrel-transport-abstractions-removed-and-made-public)
- [<span data-ttu-id="96b83-148">Yerelleştirme: kullanım dışı olarak işaretlenen API 'Ler</span><span class="sxs-lookup"><span data-stu-id="96b83-148">Localization: APIs marked obsolete</span></span>](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [<span data-ttu-id="96b83-149">Yerelleştirme: "Pubternal" API 'Leri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="96b83-149">Localization: "Pubternal" APIs removed</span></span>](#localization-pubternal-apis-removed)
- [<span data-ttu-id="96b83-150">Yerelleştirme: gereksiz Oluşturucu istek yerelleştirme ara yazılım ortamında kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="96b83-150">Localization: Obsolete constructor removed in request localization middleware</span></span>](#localization-obsolete-constructor-removed-in-request-localization-middleware)
- [<span data-ttu-id="96b83-151">Yerelleştirme: ResourceManagerWithCultureStringLocalizer Class ve WithCulture arabirim üyesi kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="96b83-151">Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed</span></span>](#localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed)
- [<span data-ttu-id="96b83-152">Günlüğe kaydetme: Debuggünlükçü sınıfı iç oluşturulmuş</span><span class="sxs-lookup"><span data-stu-id="96b83-152">Logging: DebugLogger class made internal</span></span>](#logging-debuglogger-class-made-internal)
- [<span data-ttu-id="96b83-153">MVC: denetleyici eylemi zaman uyumsuz son ek kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="96b83-153">MVC: Controller action Async suffix removed</span></span>](#mvc-async-suffix-trimmed-from-controller-action-names)
- [<span data-ttu-id="96b83-154">MVC: JsonResult, Microsoft. AspNetCore. Mvc. Core 'a taşındı</span><span class="sxs-lookup"><span data-stu-id="96b83-154">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [<span data-ttu-id="96b83-155">MVC: ön derleme aracı kullanım dışı</span><span class="sxs-lookup"><span data-stu-id="96b83-155">MVC: Precompilation tool deprecated</span></span>](#mvc-precompilation-tool-deprecated)
- [<span data-ttu-id="96b83-156">MVC: türler internal olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="96b83-156">MVC: Types changed to internal</span></span>](#mvc-pubternal-types-changed-to-internal)
- [<span data-ttu-id="96b83-157">MVC: Web API 'SI uyumluluk dolgusu kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="96b83-157">MVC: Web API compatibility shim removed</span></span>](#mvc-web-api-compatibility-shim-removed)
- [<span data-ttu-id="96b83-158">Razor: çalışma zamanı derlemesi bir pakete taşındı</span><span class="sxs-lookup"><span data-stu-id="96b83-158">Razor: Runtime compilation moved to a package</span></span>](#razor-runtime-compilation-moved-to-a-package)
- [<span data-ttu-id="96b83-159">Oturum durumu: kullanılmayan API 'Ler kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="96b83-159">Session state: Obsolete APIs removed</span></span>](#session-state-obsolete-apis-removed)
- [<span data-ttu-id="96b83-160">Paylaşılan çerçeve: Microsoft. AspNetCore. app 'ten derleme kaldırma</span><span class="sxs-lookup"><span data-stu-id="96b83-160">Shared framework: Assembly removal from Microsoft.AspNetCore.App</span></span>](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [<span data-ttu-id="96b83-161">Paylaşılan çerçeve: Microsoft. AspNetCore. All kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="96b83-161">Shared framework: Microsoft.AspNetCore.All removed</span></span>](#shared-framework-removed-microsoftaspnetcoreall)
- [<span data-ttu-id="96b83-162">SignalR: HandshakeProtocol. Başarıkıandshakedata değişti</span><span class="sxs-lookup"><span data-stu-id="96b83-162">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [<span data-ttu-id="96b83-163">SignalR: HubConnection yöntemleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="96b83-163">SignalR: HubConnection methods removed</span></span>](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [<span data-ttu-id="96b83-164">SignalR: HubConnectionContext oluşturucuları değişti</span><span class="sxs-lookup"><span data-stu-id="96b83-164">SignalR: HubConnectionContext constructors changed</span></span>](#signalr-hubconnectioncontext-constructors-changed)
- [<span data-ttu-id="96b83-165">SignalR: JavaScript istemci paketi adı değişikliği</span><span class="sxs-lookup"><span data-stu-id="96b83-165">SignalR: JavaScript client package name change</span></span>](#signalr-javascript-client-package-name-changed)
- [<span data-ttu-id="96b83-166">SignalR: MessagePack 2. x paketine taşınan MessagePack hub Protokolü</span><span class="sxs-lookup"><span data-stu-id="96b83-166">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [<span data-ttu-id="96b83-167">SignalR: MessagePack hub protokol seçenekleri türü değişti</span><span class="sxs-lookup"><span data-stu-id="96b83-167">SignalR: MessagePack Hub Protocol options type changed</span></span>](#signalr-messagepack-hub-protocol-options-type-changed)
- [<span data-ttu-id="96b83-168">SignalR: kullanılmayan API 'Ler</span><span class="sxs-lookup"><span data-stu-id="96b83-168">SignalR: Obsolete APIs</span></span>](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [<span data-ttu-id="96b83-169">SignalR: UseSignalR ve UseConnections yöntemleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="96b83-169">SignalR: UseSignalR and UseConnections methods removed</span></span>](#signalr-usesignalr-and-useconnections-methods-removed)
- [<span data-ttu-id="96b83-170">Maça 'Lar: SpaServices ve NodeServices konsol günlükçü geri dönüş varsayılan değişikliği</span><span class="sxs-lookup"><span data-stu-id="96b83-170">SPAs: SpaServices and NodeServices console logger fallback default change</span></span>](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [<span data-ttu-id="96b83-171">Maça 'Lar: gereksiz olarak işaretlenen SpaServices ve NodeServices</span><span class="sxs-lookup"><span data-stu-id="96b83-171">SPAs: SpaServices and NodeServices marked obsolete</span></span>](#spas-spaservices-and-nodeservices-marked-obsolete)
- [<span data-ttu-id="96b83-172">Statik dosyalar: CSV içerik türü, standartlara uyumlu olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="96b83-172">Static files: CSV content type changed to standards-compliant</span></span>](#static-files-csv-content-type-changed-to-standards-compliant)
- [<span data-ttu-id="96b83-173">Hedef Framework: .NET Framework desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="96b83-173">Target framework: .NET Framework not supported</span></span>](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a><span data-ttu-id="96b83-174">ASP.NET Core 5,0</span><span class="sxs-lookup"><span data-stu-id="96b83-174">ASP.NET Core 5.0</span></span>

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE[Blazor: Insignificant whitespace trimmed from components at compile time](~/includes/core-changes/aspnetcore/5.0/blazor-components-trim-insignificant-whitespace.md)]

***

[!INCLUDE[Extensions: Package reference changes](~/includes/core-changes/aspnetcore/5.0/extensions-package-reference-changes.md)]

***

[!INCLUDE[HTTP: HttpClient instances created by IHttpClientFactory log integer status codes](~/includes/core-changes/aspnetcore/5.0/http-httpclient-instances-log-integer-status-codes.md)]

***

[!INCLUDE[HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced](~/includes/core-changes/aspnetcore/5.0/http-badhttprequestexception-obsolete.md)]

***

[!INCLUDE[HttpSys: Client certificate renegotiation disabled by default](~/includes/core-changes/aspnetcore/5.0/httpsys-client-certificate-renegotiation-disabled-by-default.md)]

***

[!INCLUDE[IIS: UrlRewrite middleware query strings are preserved](~/includes/core-changes/aspnetcore/5.0/iis-urlrewrite-middleware-query-strings-are-preserved.md)]

***

[!INCLUDE[Kestrel: Configuration changes at run time detected by default](~/includes/core-changes/aspnetcore/5.0/kestrel-configuration-changes-at-run-time-detected-by-default.md)]

***
[!INCLUDE[Kestrel: Default supported TLS protocol versions changed](~/includes/core-changes/aspnetcore/5.0/kestrel-default-supported-tls-protocol-versions-changed.md)]

***

[!INCLUDE[Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions](~/includes/core-changes/aspnetcore/5.0/kestrel-disables-http2-over-tls.md)]

***

[!INCLUDE[Localization: "Pubternal" APIs removed](~/includes/core-changes/aspnetcore/5.0/localization-pubternal-apis-removed.md)]

***

[!INCLUDE[Localization: Obsolete constructor removed in request localization middleware](~/includes/core-changes/aspnetcore/5.0/localization-requestlocalizationmiddleware-constructor-removed.md)]

***

[!INCLUDE[Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed](~/includes/core-changes/aspnetcore/5.0/localization-members-removed.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-package.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol options type changed](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-hub-protocol-options-changed.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

[!INCLUDE[Static files: CSV content type changed to standards-compliant](~/includes/core-changes/aspnetcore/5.0/static-files-csv-content-type-changed.md)]

***

## <a name="aspnet-core-31"></a><span data-ttu-id="96b83-175">ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="96b83-175">ASP.NET Core 3.1</span></span>

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a><span data-ttu-id="96b83-176">ASP.NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="96b83-176">ASP.NET Core 3.0</span></span>

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
