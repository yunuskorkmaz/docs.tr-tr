---
title: ASP.NET Core son değişiklikler
titleSuffix: ''
description: ASP.NET Core 'deki son değişiklikleri listeler.
ms.date: 09/11/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 4c3167e9cad193b6a5a11be399e8be529df3be55
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539610"
---
# <a name="aspnet-core-breaking-changes"></a>ASP.NET Core son değişiklikler

ASP.NET Core .NET Core tarafından kullanılan Web uygulaması geliştirme özelliklerini sağlar.

Belirli bir sürümdeki son değişiklikler için aşağıdaki bağlantılardan birini seçin:

* [ASP.NET Core 5,0](#aspnet-core-50)
* [ASP.NET Core 3,1](#aspnet-core-31)
* [ASP.NET Core 3,0](#aspnet-core-30)

ASP.NET Core 3,0, 3,1 ve 5,0 ' deki aşağıdaki son değişiklikler bu sayfada belgelenmiştir:

- [Kullanılmayan Antiforgery, CORS, tanılama, MVC ve yönlendirme API 'Leri kaldırıldı](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [Kimlik doğrulaması: AzureAD. UI ve AzureADB2C. UI API 'Leri ve kullanım dışı olarak işaretlenen paketler](#authentication-azureadui-and-azureadb2cui-apis-and-packages-marked-obsolete)
- [Kimlik doğrulaması: Google + kullanımdan kaldırma](#authentication-google-deprecated-and-replaced)
- [Kimlik doğrulaması: HttpContext. Authentication özelliği kaldırıldı](#authentication-httpcontextauthentication-property-removed)
- [Kimlik doğrulaması: değiştirilmekte olan türler üzerinde Newtonsoft.Js](#authentication-newtonsoftjson-types-replaced)
- [Kimlik doğrulaması: OAuthHandler ExchangeCodeAsync imzası değişti](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [Yetkilendirme: Addaduthorleştirme aşırı yüklemesi farklı bir derlemeye taşındı](#authorization-addauthorization-overload-moved-to-different-assembly)
- [Yetkilendirme: ıallowanonymous, AuthorizationFilterContext. Filters öğesinden kaldırıldı](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [Yetkilendirme: ıauthorizationpolicyprovider uygulamaları için yeni yöntem gerekir](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [Yetkilendirme: uç nokta yönlendirmesinde kaynak HttpContext 'dir](#authorization-resource-in-endpoint-routing-is-httpcontext)
- [Azure: Microsoft 'un ön eki olan Azure tümleştirme paketleri kaldırıldı](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [BinaryFormatter serileştirme yöntemleri artık kullanılmıyor ve ASP.NET uygulamalarında yasaklanmış](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps)
- [Blazor: derleme zamanında bileşenlerden çok önemli olan boşluk](#blazor-insignificant-whitespace-trimmed-from-components-at-compile-time)
- [Blazor: RenderTreeFrame ReadOnly ortak alanları özellikler haline geldi](#blazor-rendertreeframe-readonly-public-fields-have-become-properties)
- [Blazor: NuGet paketlerinin hedef çerçevesi değiştirildi](#blazor-target-framework-of-nuget-packages-changed)
- [Önbelleğe alma: CompactOnMemoryPressure özelliği kaldırıldı](#caching-compactonmemorypressure-property-removed)
- [Önbelleğe alma: Microsoft. Extensions. Caching. SqlServer yeni SqlClient paketini kullanır](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [Önbelleğe alma: ResponseCaching "pubternal" türleri iç olarak değiştirildi](#caching-responsecaching-pubternal-types-changed-to-internal)
- [Veri koruma: DataProtection. AzureStorage yeni Azure depolama API 'Lerini kullanır](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [Uzantılar: bazı NuGet paketlerini etkileyen paket başvuru değişiklikleri](#extensions-package-reference-changes-affecting-some-nuget-packages)
- [Barındırma: AspNetCoreModule v1 Windows barındırma paketinden kaldırıldı](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [Barındırma: genel ana bilgisayar, başlangıç Oluşturucu ekleme işlemini kısıtlar](#hosting-generic-host-restricts-startup-constructor-injection)
- [Barındırma: IIS işlem dışı uygulamalar için HTTPS yönlendirmesi etkinleştirildi](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [Barındırma: ıhostingenvironment ve ıapplicationlifetime türleri değişti](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [Barındırma: ObjectPoolProvider WebHostBuilder bağımlılıklarından kaldırıldı](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [HTTP: Kestrel ve IIS BadHttpRequestException türleri artık kullanılmıyor ve değiştirilmiş olarak işaretlendi](#http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced)
- [HTTP: Browser SameSite değişikliklerinin etkisi kimlik doğrulaması](#http-browser-samesite-changes-impact-authentication)
- [HTTP: DefaultHttpContext genişletilebilirliği kaldırıldı](#http-defaulthttpcontext-extensibility-removed)
- [HTTP: HeaderNames alanları statik ReadOnly olarak değiştirildi](#http-headernames-constants-changed-to-static-readonly)
- [HTTP: ıhttpclientfactory günlük tamsayı durum kodları tarafından oluşturulan HttpClient örnekleri](#http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes)
- [HTTP: yanıt gövdesi altyapı değişiklikleri](#http-response-body-infrastructure-changes)
- [HTTP: bazı tanımlama bilgisi SameSite varsayılan değerleri değiştirildi](#http-some-cookie-samesite-defaults-changed-to-none)
- [HTTP: zaman uyumlu GÇ varsayılan olarak devre dışıdır](#http-synchronous-io-disabled-in-all-servers)
- [HttpSys: Istemci sertifikası yeniden anlaşması varsayılan olarak devre dışıdır](#httpsys-client-certificate-renegotiation-disabled-by-default)
- [Kimlik: Adddefaultuı yöntemi aşırı yüklemesi kaldırıldı](#identity-adddefaultui-method-overload-removed)
- [Kimlik: UI önyükleme sürümü değişikliği](#identity-default-bootstrap-version-of-ui-changed)
- [Kimlik: Signınasync kimliği doğrulanmamış kimlik için özel durum oluşturur](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [Kimlik: SignInManager Oluşturucusu yeni parametreyi kabul ediyor](#identity-signinmanager-constructor-accepts-new-parameter)
- [Kimlik: UI statik Web varlıkları özelliğini kullanır](#identity-ui-uses-static-web-assets-feature)
- [IIS: URL yeniden yazma ara yazılımı sorgu dizeleri korunur](#iis-urlrewrite-middleware-query-strings-are-preserved)
- [Kestrel: çalışma zamanında varsayılan olarak algılanan yapılandırma değişiklikleri](#kestrel-configuration-changes-at-run-time-detected-by-default)
- [Kestrel: bağlantı bağdaştırıcıları kaldırıldı](#kestrel-connection-adapters-removed)
- [Kestrel: desteklenen varsayılan TLS protokol sürümleri değiştirildi](#kestrel-default-supported-tls-protocol-versions-changed)
- [Kestrel: boş HTTPS derlemesi kaldırıldı](#kestrel-empty-https-assembly-removed)
- [Kestrel: HTTP/2 uyumsuz Windows sürümlerinde TLS üzerinden devre dışı bırakıldı](#kestrel-http2-disabled-over-tls-on-incompatible-windows-versions)
- [Kestrel: libuv taşıması eski olarak işaretlendi](#kestrel-libuv-transport-marked-as-obsolete)
- [Kestrel: yeni koleksiyona taşınan artbilgisi üstbilgileri ıste](#kestrel-request-trailer-headers-moved-to-new-collection)
- [Kestrel: aktarım soyutlama katmanı değişiklikleri](#kestrel-transport-abstractions-removed-and-made-public)
- [Yerelleştirme: kullanım dışı olarak işaretlenen API 'Ler](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [Yerelleştirme: "Pubternal" API 'Leri kaldırıldı](#localization-pubternal-apis-removed)
- [Yerelleştirme: gereksiz Oluşturucu istek yerelleştirme ara yazılım ortamında kaldırıldı](#localization-obsolete-constructor-removed-in-request-localization-middleware)
- [Yerelleştirme: ResourceManagerWithCultureStringLocalizer Class ve WithCulture arabirim üyesi kaldırıldı](#localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed)
- [Günlüğe kaydetme: Debuggünlükçü sınıfı iç oluşturulmuş](#logging-debuglogger-class-made-internal)
- [Ara yazılım: veritabanı hatası sayfası eski olarak işaretlendi](#middleware-database-error-page-marked-as-obsolete)
- [Ara yazılım: özel durum Işleyicisi ara yazılımı, işleyici bulunmazsa özgün özel durum oluşturur](#middleware-exception-handler-middleware-throws-original-exception-if-handler-not-found)
- [MVC: denetleyici eylemi zaman uyumsuz son ek kaldırıldı](#mvc-async-suffix-trimmed-from-controller-action-names)
- [MVC: JsonResult, Microsoft. AspNetCore. Mvc. Core 'a taşındı](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [MVC: ön derleme aracı kullanım dışı](#mvc-precompilation-tool-deprecated)
- [MVC: türler internal olarak değiştirildi](#mvc-pubternal-types-changed-to-internal)
- [MVC: Web API 'SI uyumluluk dolgusu kaldırıldı](#mvc-web-api-compatibility-shim-removed)
- [Razor: RazorTemplateEngine API 'SI kaldırıldı](#razor-razortemplateengine-api-removed)
- [Razor: çalışma zamanı derlemesi bir pakete taşındı](#razor-runtime-compilation-moved-to-a-package)
- [Güvenlik: tanımlama bilgisi ad kodlaması kaldırıldı](#security-cookie-name-encoding-removed)
- [Güvenlik: IdentityModel NuGet paket sürümleri güncelleştirildi](#security-identitymodel-nuget-package-versions-updated)
- [Oturum durumu: kullanılmayan API 'Ler kaldırıldı](#session-state-obsolete-apis-removed)
- [Paylaşılan çerçeve: Microsoft. AspNetCore. app 'ten derleme kaldırma](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [Paylaşılan çerçeve: Microsoft. AspNetCore. All kaldırıldı](#shared-framework-removed-microsoftaspnetcoreall)
- [SignalR: HandshakeProtocol. Başarıkıandshakedata değişti](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [SignalR: HubConnection yöntemleri kaldırıldı](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [SignalR: HubConnectionContext oluşturucuları değişti](#signalr-hubconnectioncontext-constructors-changed)
- [SignalR: JavaScript istemci paketi adı değişikliği](#signalr-javascript-client-package-name-changed)
- [SignalR: MessagePack 2. x paketine taşınan MessagePack hub Protokolü](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [SignalR: MessagePack hub protokol seçenekleri türü değişti](#signalr-messagepack-hub-protocol-options-type-changed)
- [SignalR: kullanılmayan API 'Ler](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [SignalR: UseSignalR ve UseConnections yöntemleri kaldırıldı](#signalr-usesignalr-and-useconnections-methods-removed)
- [Maça 'Lar: SpaServices ve NodeServices konsol günlükçü geri dönüş varsayılan değişikliği](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [Maça 'Lar: gereksiz olarak işaretlenen SpaServices ve NodeServices](#spas-spaservices-and-nodeservices-marked-obsolete)
- [Statik dosyalar: CSV içerik türü, standartlara uyumlu olarak değiştirildi](#static-files-csv-content-type-changed-to-standards-compliant)
- [Hedef Framework: .NET Framework desteklenmiyor](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a>ASP.NET Core 5,0

[!INCLUDE[Authentication: AzureAD.UI and AzureADB2C.UI APIs and packages marked obsolete](~/includes/core-changes/aspnetcore/5.0/authentication-aad-packages-obsolete.md)]

***

[!INCLUDE[Authorization: Resource in endpoint routing is HttpContext](~/includes/core-changes/aspnetcore/5.0/authorization-resource-in-endpoint-routing.md)]

***

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE [binaryformatter-serialization-obsolete](../../../includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

***

[!INCLUDE[Blazor: Insignificant whitespace trimmed from components at compile time](~/includes/core-changes/aspnetcore/5.0/blazor-components-trim-insignificant-whitespace.md)]

***

[!INCLUDE[Blazor: RenderTreeFrame readonly public fields have become properties](~/includes/core-changes/aspnetcore/5.0/blazor-rendertreeframe-fields-become-properties.md)]

***

[!INCLUDE[Blazor: Target framework of NuGet packages changed](~/includes/core-changes/aspnetcore/5.0/blazor-packages-target-framework-changed.md)]

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

[!INCLUDE[Kestrel: Libuv transport marked as obsolete](~/includes/core-changes/aspnetcore/5.0/kestrel-libuv-transport-obsolete.md)]

***

[!INCLUDE[Localization: "Pubternal" APIs removed](~/includes/core-changes/aspnetcore/5.0/localization-pubternal-apis-removed.md)]

***

[!INCLUDE[Localization: Obsolete constructor removed in request localization middleware](~/includes/core-changes/aspnetcore/5.0/localization-requestlocalizationmiddleware-constructor-removed.md)]

***

[!INCLUDE[Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed](~/includes/core-changes/aspnetcore/5.0/localization-members-removed.md)]

***

[!INCLUDE[Middleware: Database error page marked as obsolete](~/includes/core-changes/aspnetcore/5.0/middleware-database-error-page-obsolete.md)]

***

[!INCLUDE[Middleware: Exception Handler Middleware throws original exception if handler not found](~/includes/core-changes/aspnetcore/5.0/middleware-exception-handler-throws-original-exception.md)]

***

[!INCLUDE[Security: Cookie name encoding removed](~/includes/core-changes/aspnetcore/5.0/security-cookie-name-encoding-removed.md)]

***

[!INCLUDE[Security: IdentityModel NuGet package versions updated](~/includes/core-changes/aspnetcore/5.0/security-identitymodel-nuget-package-versions-updated.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-package.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol options type changed](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-hub-protocol-options-changed.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

[!INCLUDE[Static files: CSV content type changed to standards-compliant](~/includes/core-changes/aspnetcore/5.0/static-files-csv-content-type-changed.md)]

***

## <a name="aspnet-core-31"></a>ASP.NET Core 3,1

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a>ASP.NET Core 3,0

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

[!INCLUDE[Razor: RazorTemplatEengine API removed](~/includes/core-changes/aspnetcore/3.0/razor-razortemplateengine-api-removed.md)]

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
