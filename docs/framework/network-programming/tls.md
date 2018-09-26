---
title: .NET Framework ile Aktarım Katmanı Güvenliği (TLS) en iyi uygulamalar
description: Aktarım Katmanı Güvenliği (TLS) ile .NET Framework kullanarak en iyi uygulamalar açıklanmaktadır
ms.date: 03/15/2018
helpviewer_keywords:
- sending data, Internet security
- protocols, Internet security
- Network security
- network resources, Internet security
- receiving data, Internet security
- authentication [.NET Framework], Internet security
- Internet, security
- security [.NET Framework], Internet
- permissions [.NET Framework], Internet
author: blowdart
ms.openlocfilehash: a421b73edc1dd90be53d301d12160d39abe78f90
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47111366"
---
# <a name="transport-layer-security-tls-best-practices-with-the-net-framework"></a>.NET Framework ile Aktarım Katmanı Güvenliği (TLS) en iyi uygulamalar

Aktarım Katmanı Güvenliği (TLS) Internet üzerinden iletilen bilgilerinin gizliliğinin korunmasına yardımcı olmak için tasarlanmış bir endüstri standardı protokolüdür. [TLS 1.2](https://tools.ietf.org/html/rfc5246) önceki sürümlere göre güvenlik geliştirmeleri sağlar ve yeni yayımlanmış standardıdır. TLS 1.2 sonunda değiştirilecektir tarafından [TLS 1.3](https://tools.ietf.org/html/draft-ietf-tls-tls13-22). Bu makalede, TLS protokolünü kullanan .NET Framework uygulamalarını güvenli hale getirmek için öneriler sunar.

TLS sürümü .NET Framework uygulamaları güvenli kalmasını sağlamak için gereken **değil** gömülebilir. .NET framework uygulamaları, işletim sistemi (OS) destekleyen TLS sürümünü kullanmanız gerekir.

Bu belge olan geliştiriciler hedefler:

- Kullanarak doğrudan <xref:System.Net> API'leri (örneğin, <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> ve <xref:System.Net.Security.SslStream?displayProperty=nameWithType>).
- WCF istemcileri ve Hizmetleri kullanarak kullanarak doğrudan <xref:System.ServiceModel?displayProperty=nameWithType> ad alanı.
- Kullanarak [Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) barındırmak ve uygulamanızı çalıştırmak için Web ve çalışan rolleri. Bkz: [Azure Cloud Services](#azure-cloud-services) bölümü.

Olmasını öneririz:

- .NET Framework 4.7 veya sonraki sürümler uygulamalarınızın hedefleyin. Hedef .NET Framework 4.7.1 veya WCF uygulamalarınıza sonraki sürümleri.
- TLS sürümü belirtmeyin. TLS sürüm kullanmaya karar işletim sistemi izin vermek için kodunuzu yapılandırın.
- Bir TLS veya SSL sürümü belirtmeden doğrulamak için bir kod kapsamlı denetleme gerçekleştirir.

İşletim sistemi uygulamanızın olanak sağlayan TLS sürümünü seçin:

- Bu, otomatik olarak gelecekte gibi TLS 1.3 eklenen yeni protokolleri bir yararlanır.
- İşletim sistemi, güvenli olmaması bulunan protokolleri engeller.

Bölüm [kod değişiklikleri yapabilir ve kodunuzun denetim](#audit-your-code-and-make-code-changes) denetim ve kodunuzu güncelleme kapsar.

Bu makalede, uygulamanızı hedefleyen ve üzerinde çalıştığı .NET Framework sürümü için kullanılabilen en güçlü güvenlik seçeneğini etkinleştirmek açıklanmaktadır. Bir uygulama güvenlik protokol ve sürüm açıkça ayarlar, herhangi bir alternatif dışında kabul eder ve .NET Framework ve işletim sistemi varsayılan davranışı iptal kabul eder. TLS 1.2 bağlantı anlaşması çalıştırabilmesi için uygulamanızı isterseniz, daha düşük TLS sürümü için açık olarak ayarlama, TLS 1.2 bağlantı engeller.

Runbook'a kod protokol sürümü yoksayılamaz, TLS 1.2 belirtmenizi kesinlikle öneririz. Tanımlama ve TLS 1.0 bağımlılıklarını kaldırma hakkında yönergeler için karşıdan [TLS 1.0 sorun çözme](https://www.microsoft.com/download/details.aspx?id=55266) teknik incelemesi.

WCF destekler TLS1.0, 1.1 ve 1.2 varsayılan olarak .NET Framework 4.7. .NET Framework 4.7.1 ile başlayarak, WCF varsayılan işletim sistemi sürümü yapılandırılmış. Bir uygulama ile açıkça yapılandırıldıysa `SslProtocols.None`, WCF, işletim sistemi varsayılan ayar NetTcp taşıma kullanırken kullanır.

Bu belgede bir GitHub sorunu hakkında sorular sorabilirsiniz [Aktarım Katmanı Güvenliği (TLS) en iyi yöntemler .NET Framework ile](https://github.com/dotnet/docs/issues/4675).

## <a name="audit-your-code-and-make-code-changes"></a>Kod değişiklikleri yapabilir ve kodunuzun denetim

ASP.NET uygulamaları için İnceleme `<system.web><httpRuntime targetFramework>` öğesinin _web.config_ .NET Framework'ün hedeflenen sürümünü kullandığınızı doğrulayın.

Windows Forms ve diğer uygulamalar için bkz: [nasıl yapılır: .NET Framework sürümü hedefleme](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

Belirli bir TLS veya SSL sürümünü kullanmıyorsunuz demektir doğrulamak için aşağıdaki bölümleri kullanın.

## <a name="if-your-app-targets-net-framework-47-or-later-versions"></a>Uygulamanızı .NET Framework 4.7 veya sonraki sürümlerini hedefliyse

Aşağıdaki bölümlerde, belirli bir TLS veya SSL sürümünü kullanmıyorsunuz demektir nasıl doğrulayacağınızı.

### <a name="for-http-networking"></a>HTTP ağ

<xref:System.Net.ServicePointManager>, varsayılan olarak işletim sistemi sürümü ve en iyi güvenlik protokolü seçme için .NET Framework 4.7 ve üzeri sürümler. Varsayılan işletim sistemi en iyi seçenek almak için mümkün olduğunda, bir değer ayarlamamanız <xref:System.Net.ServicePointManager.SecurityProtocol> özelliği. Aksi takdirde, kümesine <xref:System.Net.SecurityProtocolType.SystemDefault>.

Bu makalenin geri kalanında, .NET Framework 4.7 veya sonraki sürümler için HTTP ağ hedeflenirken ilgili değildir.

### <a name="for-tcp-sockets-networking"></a>Ağ iletişimi TCP yuvaları için

<xref:System.Net.Security.SslStream>, varsayılan olarak işletim sistemi sürümü ve en iyi güvenlik protokolü seçme için .NET Framework 4.7 ve üzeri sürümler. Varsayılan işletim sistemi en iyi seçenek almak için mümkün olduğunda, yöntemi aşırı yüklemeleri kullanmayın <xref:System.Net.Security.SslStream> açık bir alır <xref:System.Security.Authentication.SslProtocols> parametresi. Aksi halde geçirmek <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. Kullanmamanızı öneririz <xref:System.Security.Authentication.SslProtocols.Default>; ayar `SslProtocols.Default` SSL 3.0 /TLS 1.0 kullanımını zorlar ve TLS 1.2 engeller.

İçin bir değer ayarlamamanız <xref:System.Net.ServicePointManager.SecurityProtocol> özellik (HTTP ağ).

Yöntemi aşırı yüklemeleri kullanmayın <xref:System.Net.Security.SslStream> açık bir alır <xref:System.Security.Authentication.SslProtocols> parametresi (TCP Yuvaları ağ). .NET Framework 4.7 veya sonraki sürümler için uygulamanızı yeniden hedeflediğinizde, en iyi yöntemler öneri aşağıdaki.

.NET Framework 4.7 veya sonraki sürümleri için TCP hedefleme ağ yuvaları olduğunda, bu konunun geri kalanı ilgili değildir.

<a name="wcf-tcp-cert"></a>

### <a name="for-wcf-tcp-transport-using-transport-security-with-certificate-credentials"></a>Sertifika kimlik bilgileri ile Aktarım güvenliği kullanarak WCF TCP için taşıma

WCF aynı ağ yığınını .NET Framework'ün rest kullanır.

4.7.1 hedefliyorsanız, WCF açıkça yapılandırılmış sürece varsayılan olarak en iyi güvenlik protokolünü seçin işletim sistemi izin verecek şekilde yapılandırılır:

- Uygulama yapılandırma dosyanızda.
- **Veya**, uygulamanızdaki bir kaynak kodu.

Varsayılan olarak, .NET Framework 4.7 ve sonraki sürümlerinde TLS 1.2 kullanmak üzere yapılandırılmış ve TLS 1.1 veya TLS 1.0 kullanarak bağlantılara izin verir. İşletim sisteminde, bağlama kullanmak için yapılandırarak en iyi güvenlik protokolünü seçin izin vermek için WCF yapılandırma <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. Bu, üzerinde ayarlanabilir <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>. `SslProtocols.None` erişilebilir <xref:System.ServiceModel.NetTcpSecurity.Transport>. `NetTcpSecurity.Transport` erişilebilir <xref:System.ServiceModel.NetTcpBinding.Security>.

Özel bağlama kullanıyorsanız:

- En iyi güvenlik protokolü ayarlayarak seçmek işletim sistemi izin vermek için WCF yapılandırma <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols> kullanılacak <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>.
- **Veya** yapılandırma yolu ile kullanılan protokol yapılandırma `system.serviceModel/bindings/customBinding/binding/sslStreamSecurity:sslProtocols`.

Size **değil** özel bağlama kullanma **ve** Yapılandırması'nı kullanarak, WCF bağlama tutunun, yapılandırma yolu ile kullanılan protokol kümesi `system.serviceModel/bindings/netTcpBinding/binding/security/transport:sslProtocols`.

### <a name="for-wcf-message-security-with-certificate-credentials"></a>Sertifika kimlik bilgileriyle için WCF ileti güvenliği

.NET framework 4.7 ve sonraki sürümlerinde varsayılan olarak, belirtilen protokolünü kullanır <xref:System.Net.ServicePointManager.SecurityProtocol> özelliği. Zaman [AppContextSwitch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` ayarlanır `true`, WCF, en iyi protokol TLS 1.0 kadar seçer.

## <a name="if-your-app-targets-a-net-framework-version-earlier-than-47"></a>Uygulamanızı 4.7'den önceki bir .NET Framework sürümünü hedefler

Kodunuzu aşağıdaki bölümleri kullanarak belirli bir TLS veya SSL sürüm ayarları doğrulamak için Denetim:

### <a name="for-net-framework-46---462-and-not-wcf"></a>.NET Framework 4.6 - 4.6.2 ve WCF değil

Ayarlama `DontEnableSystemDefaultTlsVersions` `AppContext` geçin `false`. Bkz: [AppContext anahtarlar aracılığıyla güvenlik yapılandırma](#configuring-security-via-appcontext-switches).

### <a name="for-wcf-using-net-framework-46---462-using-tcp-transport-security-with-certificate-credentials"></a>WCF için .NET Framework 4.6 - sertifika kimlik bilgileriyle TCP Aktarım güvenliği kullanarak 4.6.2 kullanma

En son işletim sistemi düzeltme ekleri yüklemeniz gerekir. Bkz: [güvenlik güncelleştirmeleri](#security-updates).

Protokol sürümü açıkça yapılandırmadığınız sürece WCF framework en yüksek protokol TLS 1.2 en fazla kullanılabilir otomatik olarak seçer. Daha fazla bilgi için bkz: önceki bölümde [sertifika kimlik bilgileri ile Aktarım güvenliği kullanarak WCF TCP için aktarım](#wcf-tcp-cert).

### <a name="for-net-framework-35---452-and-not-wcf"></a>.NET Framework 3.5 - 4.5.2 ve WCF değil

Uygulamanızı .NET Framework 4.7 veya sonraki sürümler için yükseltme öneririz. Yükseltemiyorsanız, aşağıdaki adımları uygulayın. .NET Framework 4.7 veya sonraki sürümler için yükseltene kadar belirli bir noktada gelecekte uygulamanızın başarısız olabilir.

Ayarlama [SchUseStrongCrypto](#schusestrongcrypto) ve [SystemDefaultTlsVersions](#systemdefaulttlsversions) kayıt defteri anahtarlarını 1. Bkz: [yapılandırma Windows kayıt defteri aracılığıyla güvenlik](#configuring-security-via-the-windows-registry). .NET Framework sürüm 3.5 destekler `SchUseStrongCrypto` bayrak yalnızca açık TLS değeri zaman geçirilir.

.NET Framework 3.5 üzerinde çalıştırıyorsanız, TLS 1.2 programınız tarafından belirtilebilir böylece, sık erişimli bir düzeltme eki yüklemeniz gerekir:

| [KB3154518](https://support.microsoft.com/kb/3154518) | Windows 7 SP1 ve Windows 2008 Server R2 SP1 .NET Framework 3.5.1 güvenilirlik toplaması HR-1605 - TLS sistem varsayılan sürümleri için destek dahil |
| --- | --- |
| [KB3154519](https://support.microsoft.com/kb/3154519) | Güvenilirlik toplaması HR-1605 - TLS sistem varsayılan Windows Server 2012'de .NET Framework 3.5 dahil sürümleri için destek |
| [KB3154520](https://support.microsoft.com/kb/3154520) | Güvenilirlik toplaması HR-1605 - TLS sistem varsayılan sürümleri için destek dahil Windows 8.1 ve Windows Server 2012 R2 üzerinde .NET Framework 3.5 |
| [KB3156421](https://support.microsoft.com/kb/3156421) | .NET Framework 4.5.2 ve Windows üzerinde 4.5.1 1605 düzeltme dökümü 3154521 |

### <a name="for-wcf-using-net-framework-35---452-using-tcp-transport-security-with-certificate-credentials"></a>WCF için .NET Framework 3.5 - sertifika kimlik bilgileriyle TCP Aktarım güvenliği kullanarak 4.5.2 kullanma

WCF framework'ün bu sürümlerini değerlerini SSL 3.0 ve TLS 1.0 kullanmak için sabittir. Bu değerleri değiştirilemez. Güncelleştirme ve TLS 1.1 ve 1.2 kullanmak için NET Framework 4.6 veya sonraki sürümler için yeniden hedeflendir gerekir.

## <a name="if-your-app-targets-net-framework-35"></a>Uygulamanızı .NET Framework 3.5 olmasını istiyorsanız

.NET framework veya işletim sistemi çekme izin vermek yerine bir güvenlik protokolü güvenlik protokolü açıkça ayarlamanız gerekir, ekleme `SecurityProtocolTypeExtensions` ve `SslProtocolsExtension` kodunuzda sabit listeleri. `SecurityProtocolTypeExtensions` ve `SslProtocolsExtension` için değerler `Tls12`, `Tls11`ve `SystemDefault` değeri. Bkz: [TLS sistem varsayılan Windows 8.1 ve Windows Server 2012 R2'de .NET Framework 3.5 dahil sürümleri için destek](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework).

<a name="configuring-security-via-appcontext-switches"></a>

## <a name="configuring-security-via-appcontext-switches-for-net-framework-46-or-later-versions"></a>Anahtarları (.NET Framework 4.6 veya sonraki sürümler) AppContext aracılığıyla güvenliği yapılandırma

[AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) anahtarları Bu bölümde açıklanan ilgili değilse, uygulama hedefler ya da .NET Framework 4.6 veya sonraki sürümler üzerinde çalışır. Varsayılan olarak ya da açıkça ayarlayarak anahtarlar gerekip gerekmediğini `false` mümkünse. Ardından biri veya her ikisi anahtarlar aracılığıyla güvenlik yapılandırmak istiyorsanız, bir güvenlik protokolü değeri kodunuzda belirtmeyin; Bunun yapılması, bu nedenle kaçmış anahtarlar geçersiz kılarsınız.

HTTP ağ yaptığınızı olmadığını anahtarlar aynı etkiye sahiptir (<xref:System.Net.ServicePointManager>) veya TCP Yuvaları Ağ iletişimi (<xref:System.Net.Security.SslStream>).

### <a name="switchsystemnetdontenableschusestrongcrypto"></a>Switch.System.Net.DontEnableSchUseStrongCrypto

Değerini `false` için `Switch.System.Net.DontEnableSchUseStrongCrypto` güçlü şifreleme kullanmak için uygulamanızı neden olur. Değerini `false` için `DontEnableSchUseStrongCrypto` (TLS 1.2, TLS 1.1 ve TLS 1.0) daha güvenli ağ protokollerini kullanır ve güvenli olmayan protokolleri engeller. Daha fazla bilgi için bkz. [SCH_USE_STRONG_CRYPTO bayrağı](#the-schusestrongcrypto-flag). Değerini `true` uygulamanız için güçlü şifreleme devre dışı bırakır.

Uygulamanızı .NET Framework 4.6 veya üzeri sürümlerini hedefliyorsa, bu anahtar için varsayılan olarak `false`. Öneririz güvenli varsayılan olmasıdır. Uygulamanızı .NET Framework 4.6 üzerinde çalışır, ancak önceki bir sürümü hedefliyorsa, anahtar için varsayılan olarak `true`. Bu durumda, açıkça ayarlayın `false`.

`DontEnableSchUseStrongCrypto` yalnızca bir değeri olmalıdır `true` güçlü şifreleme desteği ve Yükseltilemeyen eski hizmetlere bağlanmanız gerekirse.

### <a name="switchsystemnetdontenablesystemdefaulttlsversions"></a>Switch.System.Net.DontEnableSystemDefaultTlsVersions

Değerini `false` için `Switch.System.Net.DontEnableSystemDefaultTlsVersions` uygulamanızın protokol seçin işletim sisteminin neden olur. Değerini `true` .NET Framework tarafından çekilen protokolleri kullanmak için uygulamanızı neden olur.

Uygulamanızı .NET Framework 4.7 veya sonraki sürümlerini hedefliyorsa, bu anahtar için varsayılan olarak `false`. Önerdiğimiz güvenli varsayılan olmasıdır. Uygulamanızı .NET Framework 4.7 veya sonraki sürümler üzerinde çalışır, ancak önceki bir sürümü hedefliyorsa, anahtar için varsayılan olarak `true`. Bu durumda, açıkça ayarlayın `false`.

### <a name="switchsystemservicemodeldisableusingservicepointmanagersecurityprotocols"></a>Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols

Değerini `false` için `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` tanımlı değeri kullanmak uygulamanızın `ServicePointManager.SecurityProtocols` için ileti güvenliği sertifikası kimlik bilgilerini kullanarak. Değerini `true` TLS1.0 kadar kullanılabilen en yüksek protokolünü kullanır

Bu değeri varsayılan olarak .NET Framework 4.7 ve sonraki sürümleri hedefleyen uygulamalarda, `false`. .NET Framework 4.6.2'yi hedefleyen uygulamalar için ve bu değeri daha önce varsayılan olarak `true`.

### <a name="switchsystemservicemodeldontenablesystemdefaulttlsversions"></a>Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions

Değerini `false` için `Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions` işletim sisteminin protokol için varsayılan yapılandırmayı ayarlar. Değerini `true` TLS1.2 kadar kullanılabilen en yüksek protokol için varsayılan ayarlar.

Bu değeri varsayılan olarak .NET Framework 4.7.1 ve sonraki sürümleri hedefleyen uygulamalarda, `false`. Bu değeri varsayılan olarak .NET Framework 4.7 ve önceki sürümleri hedefleyen uygulamalarda, `true`.

TLS protokolleri hakkında daha fazla bilgi için bkz. [azaltma: TLS protokolleri](../migration-guide/mitigation-tls-protocols.md). Hakkında daha fazla bilgi için `AppContext` anahtarları bkz [ `<AppContextSwitchOverrides> Element` ](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

## <a name="configuring-security-via-the-windows-registry"></a>Windows kayıt defteri aracılığıyla güvenliği yapılandırma

> [!WARNING]
> Kayıt defteri anahtarlarını ayarlamak sistem üzerindeki tüm uygulamaları etkiler. Yalnızca makine tam denetimi sizdedir ve kayıt defterindeki değişiklikleri kontrol edebilirsiniz, bu seçeneği kullanın.

Birini veya ikisini de ayarlıyorsanız `AppContext` anahtarları bir seçenek değildir, bu bölümde açıklanan Windows kayıt defteri anahtarları ile uygulamanızın kullandığı güvenlik protokollerini denetleyebilirsiniz. Aşağıdakilerden birini veya her ikisi de kullanmanız mümkün olmayabilir `AppContext` uygulamanızı 4.6'den önceki bir .NET Framework sürümünü hedefler ve yapılandırma dosyası düzenleyemezsiniz geçer. Ardından güvenlik kayıt defteri ile yapılandırmak istiyorsanız, kodunuzdaki güvenlik protokolü değeri belirtmeyin; Bunun yapılması, bu nedenle kayıt defteri geçersiz kılarsınız.

Adlara karşılık gelen kayıt defteri anahtarlarını adlarını benzer `AppContext` anahtarları olmadan bir `DontEnable` adına etkileşimlidir. Örneğin, `AppContext` geçiş `DontEnableSchUseStrongCrypto` kayıt defteri anahtarı adlı [SchUseStrongCrypto](#schusestrongcrypto).

Bu anahtarlar, var olan en son güvenlik düzeltme eki tüm .NET Framework sürümlerinde kullanılabilir. Bkz: [güvenlik güncelleştirmeleri](#security-updates).

HTTP ağ yaptığınızı olmadığını aşağıda açıklanan kayıt defteri anahtarlarını tümünün aynı etkiye sahiptir (<xref:System.Net.ServicePointManager>) veya TCP Yuvaları Ağ iletişimi (<xref:System.Net.Security.SslStream>).

### <a name="schusestrongcrypto"></a>SchUseStrongCrypto

`HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SchUseStrongCrypto` Kayıt defteri anahtarı DWORD türünde bir değer içeriyor. 1 değeri, güçlü şifreleme kullanmak için uygulamanızı neden olur. Güçlü şifreleme, daha güvenli ağ protokollerini (TLS 1.2, TLS 1.1 ve TLS 1.0) kullanır ve güvenli olmayan protokolleri engeller. 0 değeri güçlü şifreleme devre dışı bırakır. Daha fazla bilgi için [SCH_USE_STRONG_CRYPTO bayrağı](#the-schusestrongcrypto-flag).

Uygulamanızı .NET Framework 4.6 veya üzeri sürümlerini hedefliyorsa, bu anahtarı değerini 1 olarak varsayılan olarak. Önerdiğimiz güvenli varsayılan olmasıdır. Uygulamanızı .NET Framework 4.6 üzerinde çalışır, ancak önceki bir sürümü hedefliyorsa, anahtar 0 olarak varsayılır. Bu durumda, 1 olarak açıkça değerini ayarlamanız gerekir.

Güçlü şifreleme desteği ve Yükseltilemeyen eski hizmetlere bağlanmanız gerekirse bu anahtar yalnızca 0 değeri olmalıdır.

### <a name="systemdefaulttlsversions"></a>SystemDefaultTlsVersions

`HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SystemDefaultTlsVersions` Kayıt defteri anahtarı DWORD türünde bir değer içeriyor. 1 değeri işletim sisteminin protokol seçin için uygulamanızı neden olur. 0 değeri, .NET Framework tarafından çekilen protokolleri kullanmak için uygulamanızı neden olur.

`<VERSION>` v4.0.30319 (.NET Framework 4 ve üzeri için) veya v2.0.50727 (.NET Framework 3.5 için) olmalıdır.

Uygulamanızı .NET Framework 4.7 veya sonraki sürümlerini hedefliyorsa, bu anahtarı değerini 1 olarak varsayılan olarak. Önerdiğimiz güvenli varsayılan olmasıdır. Uygulamanızı .NET Framework 4.7 veya sonraki sürümler üzerinde çalışır, ancak önceki bir sürümü hedefliyorsa, anahtar 0 olarak varsayılır. Bu durumda, 1 olarak açıkça değerini ayarlamanız gerekir.

Daha fazla bilgi için bkz. [güncelleştirme Windows 10 sürüm 1511 için toplu ve Windows Server 2016 Technical Preview 4: 10 Mayıs 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016).

.NET framework 3.5.1 ile daha fazla bilgi için [TLS sistem varsayılan Windows 7 SP1 ve Windows 2008 Server R2 SP1 üzerinde .NET Framework 3.5.1 dahil sürümleri için destek](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework).

Aşağıdaki _. REG_ dosyası kayıt defteri anahtarları ve bunların türevleri en güvenli değerlerini ayarlar:

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\v2.0.50727]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v2.0.50727]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]
"SystemDefaultTlsVersions"=dword:00000001
"SchUseStrongCrypto"=dword:00000001
```

## <a name="configuring-schannel-protocols-in-the-windows-registry"></a>Windows kayıt defterinde Schannel protokolleri yapılandırma

Kayıt defteri, istemci ve/veya sunucu uygulamanızı görüşür protokolleri üzerinde ayrıntılı denetim için kullanabilirsiniz. Uygulamanızın ağ Schannel geçer (başka bir ad olduğu [güvenli kanal](/windows/desktop/SecAuthN/secure-channel). Yapılandırarak `Schannel`, uygulamanızın davranışını yapılandırabilirsiniz.

İle başlayan `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols` kayıt defteri anahtarı. Bu anahtarı tüm alt kümesinde oluşturabilirsiniz `SSL 2.0`, `SSL 3.0`, `TLS 1.0`, `TLS 1.1`, ve `TLS 1.2`. Her bu alt altında alt oluşturabilirsiniz `Client` ve/veya `Server`. Altında `Client` ve `Server`, DWORD değerlerini oluşturabilirsiniz `DisabledByDefault` (0 veya 1) ve `Enabled` (0 veya 0xFFFFFFFF).

## <a name="the-schusestrongcrypto-flag"></a>SCH_USE_STRONG_CRYPTO bayrağı

Bu etkinleştirildiğinde (varsayılan olarak, tarafından bir `AppContext` geçiş, veya Windows kayıt defteri), .NET Framework kullanan `SCH_USE_STRONG_CRYPTO` TLS güvenlik protokolü, uygulamanız istediğinde, bayrak. `SCH_USE_STRONG_CRYPTO` Bayrağı ile varsayılan olarak, etkinleştirilebilir `AppContext` geçiş, veya kayıt defteri ile. İşletim sistemi bayrak geçirir `Schannel`bilinen zayıf şifreleme algoritmalarına devre dışı bırakmak için yönlendirmek için paketleri ve aksi takdirde daha iyi birlikte çalışabilirlik için etkinleştirilebilir TLS/SSL protokolü sürümlerini şifre. Daha fazla bilgi için bkz.:

- [Güvenli kanal](/windows/desktop/SecAuthN/secure-channel)
- [SCHANNEL_CRED yapısı](/windows/desktop/api/schannel/ns-schannel-_schannel_cred)

`SCH_USE_STRONG_CRYPTO` Bayrağı için geçirilen ayrıca `Schannel` açıkça kullandığınızda `Tls` (TLS 1.0) `Tls11`, veya `Tls12` listelenmiş değerlerinden biri <xref:System.Net.SecurityProtocolType> veya <xref:System.Security.Authentication.SslProtocols>.

## <a name="security-updates"></a>Güvenlik güncelleştirmeleri

Bu makalede en iyi uygulamaları en son güvenlik güncelleştirmelerinin yüklenmesini bağlıdır. Bu güncelleştirmeler Gelişmiş .NET Framework 4.7 ve sonraki özellik kullanma yeteneğini içerir. En son güvenlik güncelleştirmeleri, uygulamanız .NET Framework 4.7 ve sonraki sürümleri çalışıyorsa (önceki bir sürümü hedefliyorsa olsa bile) önemlidir.

İşletim sisteminin en iyi kullanmak için TLS sürümünü seçmek için .NET Framework'ü güncelleştirmek için en az yüklemeniz gerekir:

- [Kalite paketi .NET Framework Ağustos 2017 önizlemesi](https://blogs.msdn.microsoft.com/dotnet/2017/08/16/net-framework-august-2017-preview-of-quality-rollup).
- **Veya** [.NET Framework Eylül 2017 güvenlik ve kalite toplaması](https://blogs.msdn.microsoft.com/dotnet/2017/09/12/net-framework-september-2017-security-and-quality-rollup).

Ayrıca bkz:

- [.NET framework sürümleri ve bağımlılıkları](../migration-guide/versions-and-dependencies.md)
- [Nasıl yapılır: hangi .NET Framework sürümlerinin yüklü olduğunu belirleme](../migration-guide/how-to-determine-which-versions-are-installed.md).

## <a name="support-for-tls-12"></a>TLS 1.2 desteği

TLS 1.2, işletim sistemi ve .NET Framework sürümünü anlaşmak üzere uygulamanız için TLS 1.2 desteklemek her ikisi de gerekir.

**TLS 1.2 desteği için işletim sistemi gereksinimleri**

Etkinleştirmek veya TLS 1.2 ve/veya TLS 1.1, bunları destekleyen bir sistemde yeniden etkinleştirmek için bkz: [Aktarım Katmanı Güvenliği (TLS) kayıt defteri ayarları](/windows-server/security/tls/tls-registry-settings).

| **İŞLETİM SİSTEMİ** | **TLS 1.2 desteği** |
| --- | --- |
| Windows 10</br>Windows Server 2016 | Desteklenen ve varsayılan olarak etkindir. |
| Windows 8.1</br>Windows Server 2012 R2 | Desteklenen ve varsayılan olarak etkindir. |
| Windows 8.0</br>Windows Server 2012 | Desteklenen ve varsayılan olarak etkindir. |
| Windows 7 SP1</br>Windows Server 2008 R2 SP1 | , Varsayılan olarak etkin değildir ancak desteklenir. Bkz: [Aktarım Katmanı Güvenliği (TLS) kayıt defteri ayarları](/windows-server/security/tls/tls-registry-settings) TLS 1.2 etkinleştirme hakkında daha fazla ayrıntı için web sayfası. |
| Windows Server 2008 | TLS 1.2 ve TLS 1.1 desteği güncelleştirilmesi gerekiyor. Bkz: [Windows Server 2008 SP2'de TLS 1.1 ve TLS 1.2 desteği eklemek için güncelleştirme](https://support.microsoft.com/help/4019276/update-to-add-support-for-tls-1-1-and-tls-1-2-in-windows-server-2008-s). |
| Windows Vista | Desteklenmez. |

Hangi TLS/SSL protokolleri Windows'ın her sürümünde varsayılan olarak etkinleştirilir daha fazla bilgi için bkz [protokolleri de TLS/SSL'deki (Schannel SSP)](https://msdn.microsoft.com/library/windows/desktop/mt808159).

**.NET Framework 3.5 ile TLS 1.2 Destek gereksinimleri**

Bu tablo, .NET Framework 3.5 ile TLS 1.2 desteklemek ihtiyacınız olacak işletim sistemi güncelleştirmesine gösterir. Tüm işletim sistemi güncelleştirmeleri uygulamanızı öneririz.

| **İŞLETİM SİSTEMİ** | **.NET Framework 3.5 ile TLS 1.2 desteklemek için gereken en düşük güncelleştirme** |
| --- | --- |
| Windows 10</br>Windows Server 2016 | [Windows 10 sürüm 1511 için toplu güncelleştirme ve Windows Server 2016 Technical Preview 4: 10 Mayıs 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016) |
| Windows 8.1</br>Windows Server 2012 R2 | [TLS sistem varsayılan Windows 8.1 ve Windows Server 2012 R2 üzerinde .NET Framework 3.5 dahil sürümleri için destek](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 8.0</br>Windows Server 2012 | [TLS sistem varsayılan Windows Server 2012'de .NET Framework 3.5 dahil sürümleri için destek](https://support.microsoft.com/help/3154519/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 7 SP1</br>Windows Server 2008 R2 SP1 | [TLS sistem varsayılan .NET Framework 3.5.1 Windows 7 SP1 ve Windows 2008 Server R2 SP1 üzerine de dahil sürümleri için destek](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Server 2008 | [TLS sistem varsayılan Windows Vista SP2 ve Server 2008 SP2 üzerinde .NET Framework 2.0 SP2 dahil sürümleri için destek](https://support.microsoft.com/help/3154517/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Vista | Desteklenmez |

## <a name="azure-cloud-services"></a>Azure bulut Hizmetleri

Kullanıyorsanız [Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) Web ve çalışan rolleri, barındırma ve çalıştırma, uygulamanız için TLS 1.2 desteği için dikkate almanız gereken bazı noktalar vardır.

### <a name="net-framework-47-is-not-installed-on-azure-guest-os-by-default"></a>.NET framework 4.7 varsayılan olarak Azure konuk işletim sisteminde yüklü değil

En son Azure konuk işletim sistemi ailesi 5 sürümde (Windows Server 2016) yüklü en son sürüm 4.6.2 ' dir. Her Azure konuk işletim sisteminde .NET Framework'ün hangi sürümlerinin yüklü olduğunu görmek için bkz: [Azure konuk işletim sistemi sürümleri ve SDK uyumluluk matrisi](https://docs.microsoft.com/azure/cloud-services/cloud-services-guestos-update-matrix).

Uygulamanızı Azure konuk işletim sistemi sürümünde kullanılabilir olmayan bir .NET Framework sürümünü hedefler, kendiniz yüklemeniz gerekir. Bkz: [Azure bulut hizmeti rollerinde .NET yükleme](https://docs.microsoft.com/azure/cloud-services/cloud-services-dotnet-install-dotnet). Framework yüklemesi yeniden başlatma gerektirirse, hizmet rolleri de hazır duruma girmeden önce yeniden başlatılabilir.

### <a name="azure-guest-os-registry-settings"></a>Azure konuk işletim sistemi kayıt defteri ayarları

Azure konuk işletim sistemi görüntüsü için [Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) zaten `SchUseStrongCrypto` kayıt defteri anahtarı değerini 1 olarak ayarlayın. Daha fazla bilgi için [SchUseStrongCrypto](#schusestrongcrypto).

Ayarlama [SystemDefaultTlsVersions](#systemdefaulttlsversions) kayıt defteri anahtarı 1. Bkz: [yapılandırma Windows kayıt defteri aracılığıyla güvenlik](#configuring-security-via-the-windows-registry).
