---
title: ASP.NET Çekirdek kırma değişiklikleri
titleSuffix: ''
description: ASP.NET Core'daki kırılma değişikliklerini listeler.
ms.date: 03/25/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: eb80be54da8ac0b15d854304e53a7ade7f42da1b
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291713"
---
# <a name="aspnet-core-breaking-changes"></a>ASP.NET Çekirdek kırma değişiklikleri

ASP.NET Core, .NET Core tarafından kullanılan web uygulaması geliştirme özelliklerini sağlar.

Aşağıdaki kesme değişiklikleri bu sayfada belgelenmiştir:

- [Eski Antiforgery, CORS, Teşhis, MVC ve Yönlendirme API'leri kaldırıldı](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [Kimlik doğrulama: Google+ amortismanı](#authentication-google-deprecated-and-replaced)
- [Kimlik doğrulama: HttpContext.Authentication özelliği kaldırıldı](#authentication-httpcontextauthentication-property-removed)
- [Kimlik doğrulama: Newtonsoft.Json türleri değiştirildi](#authentication-newtonsoftjson-types-replaced)
- [Kimlik doğrulama: OAuthHandler ExchangeCodeAsync imza değiştirildi](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [Yetkilendirme: AddAuthorization aşırı yükü farklı derlemeye taşındı](#authorization-addauthorization-overload-moved-to-different-assembly)
- [Yetkilendirme: IAllowAnonymous YetkilendirmeFilterContext.Filters kaldırıldı](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [Yetkilendirme: IAuthorizationPolicyProvider uygulamaları yeni bir yöntem gerektirir](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [Azure: Microsoft tarafından önceden belirlenmiş Azure tümleştirme paketleri kaldırıldı](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [Önbelleğe alma: CompactOnMemoryPressure özelliği kaldırıldı](#caching-compactonmemorypressure-property-removed)
- [Önbelleğe alma: Microsoft.Extensions.Caching.SqlServer yeni SqlClient paketi kullanır](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [Önbelleğe alma: YanıtCaching "pubternal" türleri iç değiştirildi](#caching-responsecaching-pubternal-types-changed-to-internal)
- [Veri Koruması: DataProtection.AzureStorage yeni Azure Depolama API'leri kullanır](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [Hosting: AspNetCoreModule V1 Windows Hosting Paketi kaldırıldı](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [Barındırma: Genel ana bilgisayar Başlangıç yapıcı enjeksiyonu kısıtlar](#hosting-generic-host-restricts-startup-constructor-injection)
- [Barındırma: IIS işlem dışı uygulamalar için HTTPS yeniden yönlendirmesi etkin](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [Hosting: IHostingEnvironment ve IApplicationLifetime türleri değiştirildi](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [Barındırma: ObjectPoolProvider WebHostBuilder bağımlılıkları kaldırıldı](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [HTTP: Tarayıcı SameSite değişiklikleri kimlik doğrulamayı etkiler](#http-browser-samesite-changes-impact-authentication)
- [HTTP: VarsayılanHttpContext genişletilebilirlik kaldırıldı](#http-defaulthttpcontext-extensibility-removed)
- [HTTP: Başlıkadları alanları yalnızca statik olarak değiştirildi](#http-headernames-constants-changed-to-static-readonly)
- [HTTP: Yanıt gövde altyapı değişiklikleri](#http-response-body-infrastructure-changes)
- [HTTP: Bazı çerez SameSite varsayılan değerleri değişti](#http-some-cookie-samesite-defaults-changed-to-none)
- [HTTP: Synchronous IO varsayılan olarak devre dışı](#http-synchronous-io-disabled-in-all-servers)
- [Kimlik: AddDefaultUI yöntemi aşırı kaldırıldı](#identity-adddefaultui-method-overload-removed)
- [Kimlik: UI Bootstrap sürüm değişikliği](#identity-default-bootstrap-version-of-ui-changed)
- [Kimlik: SignInAsync kimliği doğrulanmamış kimlik için özel durum atar](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [Kimlik: SignInManager constructor yeni parametre kabul eder](#identity-signinmanager-constructor-accepts-new-parameter)
- [Kimlik: UI statik web varlıkları özelliğini kullanır](#identity-ui-uses-static-web-assets-feature)
- [Kerkenez: Bağlantı bağdaştırıcıları kaldırıldı](#kestrel-connection-adapters-removed)
- [Kerkenez: Boş HTTPS derlemesi kaldırıldı](#kestrel-empty-https-assembly-removed)
- [Kerkenez: İstek römork başlıkları yeni koleksiyona taşındı](#kestrel-request-trailer-headers-moved-to-new-collection)
- [Kerkenez: Taşıma soyutlama katmanı değişiklikleri](#kestrel-transport-abstractions-removed-and-made-public)
- [Yerelleştirme: API'ler eski olarak işaretlenmiş](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [Günlük: DebugLogger sınıfı dahili yaptı](#logging-debuglogger-class-made-internal)
- [MVC: Denetleyici eylem Async soneki kaldırıldı](#mvc-async-suffix-trimmed-from-controller-action-names)
- [MVC: JsonResult Microsoft.AspNetCore.Mvc.Core taşındı](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [MVC: Precompilation aracı amortismana](#mvc-precompilation-tool-deprecated)
- [MVC: Türleri dahili olarak değiştirildi](#mvc-pubternal-types-changed-to-internal)
- [MVC: Web API uyumluluk şim kaldırıldı](#mvc-web-api-compatibility-shim-removed)
- [Razor: Runtime derleme bir paket taşındı](#razor-runtime-compilation-moved-to-a-package)
- [Oturum durumu: Eski API'ler kaldırıldı](#session-state-obsolete-apis-removed)
- [Paylaşılan çerçeve: Microsoft.AspNetCore.App'ten derleme kaldırma](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [Paylaşılan çerçeve: Microsoft.AspNetCore.All kaldırıldı](#shared-framework-removed-microsoftaspnetcoreall)
- [SignalR: HandshakeProtocol.SuccessHandshakeData değiştirildi](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [SignalR: HubConnection yöntemleri kaldırıldı](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [SignalR: HubConnectionContext yapıcılar değişti](#signalr-hubconnectioncontext-constructors-changed)
- [SignalR: JavaScript istemci paketi adı değişikliği](#signalr-javascript-client-package-name-changed)
- [SignalR: Eski API'ler](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [SignalR: UseSignalR ve UseConnections yöntemleri kaldırıldı](#signalr-usesignalr-and-useconnections-methods-removed)
- [STA'lar: SpaServices ve NodeServices eski işaretlenmiş](#spas-spaservices-and-nodeservices-marked-obsolete)
- [SP'ler: SpaServices ve NodeServices logger geri dönüş varsayılan değişikliği konsol](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [Hedef çerçeve: .NET Framework desteklenmiyor](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a>ASP.NET Çekirdek 5.0

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

## <a name="aspnet-core-31"></a>ASP.NET Çekirdek 3.1

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a>ASP.NET Çekirdek 3.0

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
