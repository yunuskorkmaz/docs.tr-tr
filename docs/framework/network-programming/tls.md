---
title: .NET Framework ile Aktarım Katmanı Güvenliği (TLS) en iyi uygulamalar
description: Aktarım Katmanı Güvenliği (TLS) kullanarak .NET Framework ile en iyi uygulamaları açıklar
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
ms.openlocfilehash: 41814129d038f8cb1ab98db0c7a4e0cbd7e7cd54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="transport-layer-security-tls-best-practices-with-the-net-framework"></a>.NET Framework ile Aktarım Katmanı Güvenliği (TLS) en iyi uygulamalar

Aktarım Katmanı Güvenliği (TLS) Protokolü Internet üzerinden iletilen bilgiler gizliliğinizi korumaya yardımcı olmak için tasarlanmış bir endüstri standardıdır. [TLS 1.2](https://tools.ietf.org/html/rfc5246) önceki sürümlere göre güvenlik geliştirmelerini sağlar ve yeni yayımlanmış standardıdır. TLS 1.2 sonunda değiştirilecek tarafından [TLS 1.3](https://tools.ietf.org/html/draft-ietf-tls-tls13-22). Bu makalede TLS protokolünü kullanan .NET Framework uygulamaları güvenliğini sağlamak için öneriler sunar.

.NET Framework uygulamaları güvenli kalmasını sağlamak için TLS sürümü gereken **değil** sabit kodlanmış olmalıdır. .NET framework uygulamaları işletim sistemi (OS) destekliyor TLS sürümünü kullanmanız gerekir.

Bu belgede olan geliştiriciler hedefler:

- Kullanarak doğrudan <xref:System.Net> API'leri (örneğin, <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> ve <xref:System.Net.Security.SslStream?displayProperty=nameWithType>).
- WCF istemcileri ve Hizmetleri kullanarak kullanarak doğrudan <xref:System.ServiceModel?displayProperty=nameWithType> ad alanı.
- Kullanarak [Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) Web ve çalışan rolleri barındırmak ve uygulamanızı çalıştırın. Bkz: [Azure Cloud Services](#azure-cloud-services) bölümü.

Öneririz:

- .NET Framework 4.7 veya sonraki sürümlerinde, uygulamalarınızı hedefleyin. .NET Framework 4.7.1 veya sonraki sürümler, WCF uygulamalarını hedefleyin.
- TLS sürüm belirtmeyin. TLS sürüm kullanmaya karar OS izin vermek için kodunuzu yapılandırın.
- Bir TLS veya SSL sürümü belirtmeden doğrulamak için bir tam kodu denetimi gerçekleştirin.

Uygulamanızı izin verdiğinde TLS sürümü işletim sistemi seçin:

- Bu, otomatik olarak yeni protokoller gelecekte gibi TLS 1.3 eklenen bir yararlanır.
- İşletim sistemi güvenli olmaması için bulunan protokolleri engeller.

Bölüm [kodunuzu denetleme ve kod değişiklik](#audit-your-code-and-make-code-changes) denetleme ve kodunuzu güncelleme kapsar.

Bu makalede, uygulamanızı hedefler ve üzerinde çalışan .NET Framework sürümü için kullanılabilir en güçlü güvenliği etkinleştirmek açıklanmaktadır. Bir uygulamayı açıkça güvenlik protokol ve sürüm ayarlar, dışında başka bir yol kabul eder ve .NET Framework ve işletim sistemi varsayılan davranışı iptal çevrilir. TLS 1.2 bağlantı anlaşması yapabilmek için uygulamanızın istiyorsanız, daha düşük bir TLS sürümü açıkça ayarlama TLS 1.2 bağlantı engeller.

Cmdlet'e kod Protokolü sürüm yoksayılamaz, TLS 1.2 belirttiğiniz kesinlikle öneririz. Tanımlama ve TLS 1.0 bağımlılıklarını kaldırma hakkında yönergeler için karşıdan [TLS 1.0 sorunu çözme](https://www.microsoft.com/download/details.aspx?id=55266) teknik incelemesi.

WCF destekler TLS1.0, 1.1 ve 1.2 varsayılan .NET Framework 4.7 olarak. .NET Framework 4.7.1 ile başlayarak, WCF varsayılan işletim sistemi sürümü yapılandırılmış. Bir uygulama ile açıkça yapılandırılmışsa `SslProtocols.None`, WCF NetTcp aktarım kullanırken, işletim sistemi varsayılan ayarını kullanır.

Bu belgede GitHub sorunu hakkında sorular sorabilirsiniz [Aktarım Katmanı Güvenliği (TLS) en iyi uygulamalar .NET Framework ile](https://github.com/dotnet/docs/issues/4675).

## <a name="audit-your-code-and-make-code-changes"></a>Kodunuzu denetleme ve kod değişiklikleri yapın

ASP.NET uygulamaları için incelemek `<system.web><httpRuntime targetFramework>` öğesinin _web.config_ hedeflenen .NET Framework sürümünü kullandığınızı doğrulayın.

Windows Forms ve diğer uygulamalar için bkz: [nasıl yapılır: .NET Framework sürümü hedef](/visualstudio/ide/how-to-target-a-version-of-the-dotnet-framework).

Belirli bir TLS veya SSL sürümü kullanmadığınızı doğrulamak için aşağıdaki bölümleri kullanın.

## <a name="if-your-app-targets-net-framework-47-or-later-versions"></a>Uygulamanız .NET Framework 4.7 veya sonraki sürümler hedefliyorsa

Aşağıdaki bölümler, belirli bir TLS veya SSL sürümü kullanmadığınızı doğrulamak gösterilmektedir.

### <a name="for-http-networking"></a>HTTP ağ

<xref:System.Net.ServicePointManager>, varsayılan olarak en iyi güvenlik protokol ve sürüm seçme işletim sistemi için .NET Framework 4.7 ve sonraki sürümlerinde kullanma. Varsayılan işletim sistemi en iyi seçenek almak için mümkünse için bir değer ayarlamanız gerekmez <xref:System.Net.ServicePointManager.SecurityProtocol> özelliği. Aksi takdirde kümesine <xref:System.Net.SecurityProtocolType.SystemDefault>.

Bu makalenin sonraki bölümlerinde, .NET Framework 4.7 veya sonraki sürümler için HTTP ağ hedeflerken ilgili değildir.

### <a name="for-tcp-sockets-networking"></a>Ağ iletişimi için TCP yuvaları

<xref:System.Net.Security.SslStream>, varsayılan olarak en iyi güvenlik protokol ve sürüm seçme işletim sistemi için .NET Framework 4.7 ve sonraki sürümlerinde kullanma. Varsayılan işletim sistemi en iyi seçenek almak için mümkünse yöntemi aşırı kullanmayın <xref:System.Net.Security.SslStream> açık bir alın <xref:System.Security.Authentication.SslProtocols> parametresi. Aksi takdirde geçirmek <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. Kullanmamanızı öneririz <xref:System.Security.Authentication.SslProtocols.Default>; ayar `SslProtocols.Default` SSL 3.0 /TLS 1.0 kullanımını zorlar ve TLS 1.2 engeller.

İçin bir değer ayarlamanız gerekmez <xref:System.Net.ServicePointManager.SecurityProtocol> özelliği (için HTTP ağ iletişimi).

Yöntemi aşırı kullanmayan <xref:System.Net.Security.SslStream> açık bir alın <xref:System.Security.Authentication.SslProtocols> parametresi (TCP Yuvaları ağ). .NET Framework 4.7 veya sonraki sürümler uygulamanıza hedefini değiştirdiğinizde, en iyi yöntemler öneri aşağıdaki.

.NET Framework 4.7 veya sonraki sürümler için TCP hedefleme ağ yuva olduğunda bu konunun geri kalanında ilgili değildir.

<a name="wcf-tcp-cert"></a>

### <a name="for-wcf-tcp-transport-using-transport-security-with-certificate-credentials"></a>Taşıma güvenliği sertifikası kimlik bilgilerini kullanarak WCF TCP taşıma

WCF aynı ağ yığınını .NET Framework'ün rest kullanır.

4.7.1 hedefliyorsanız, WCF açıkça yapılandırılmış olmadığı sürece varsayılan olarak en iyi güvenlik protokolü seçmek işletim sistemi izin verecek şekilde yapılandırılır:

- Uygulama yapılandırma dosyanızda.
- **Veya**, kaynak kodu, uygulamanızda.

Varsayılan olarak, .NET Framework 4.7 ve sonraki sürümlerinde TLS 1.2 kullanmak üzere yapılandırılmış ve TLS 1.1 veya TLS 1.0 kullanarak bağlantılara izin verir. İşletim Sisteminin en iyi güvenlik protokolünü kullanmak için bağlama yapılandırarak seçmenize izin vermek için WCF yapılandırma <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. Bu, üzerinde ayarlanabilir <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>. `SslProtocols.None` erişilebilir <xref:System.ServiceModel.NetTcpSecurity.Transport>. `NetTcpSecurity.Transport` erişilebilir <xref:System.ServiceModel.NetTcpBinding.Security>.

Özel bağlama kullanıyorsanız:

- İşletim Sisteminin ayarlayarak en iyi güvenlik protokolü seçin izin vermek için WCF yapılandırma <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols> kullanmak için <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>.
- **Veya** yapılandırma yolu ile kullanılan protokol yapılandırma `system.serviceModel/bindings/customBinding/binding/sslStreamSecurity:sslProtocols`.

Kullanıcısıysanız **değil** özel bağlama kullanma **ve** Yapılandırması'nı kullanarak, WCF bağlama ayarladığınız, yapılandırma yolu ile kullanılan protokolü `system.serviceModel/bindings/netTcpBinding/binding/security/transport:sslProtocols`.

### <a name="for-wcf-message-security-with-certificate-credentials"></a>Sertifika kimlik bilgileri ile için WCF ileti güvenliği

.NET framework 4.7 ve sonraki sürümlerinde varsayılan olarak belirtilen protokolünü kullanır <xref:System.Net.ServicePointManager.SecurityProtocol> özelliği. Zaman [AppContextSwitch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` ayarlanır `true`, WCF en iyi protokol TLS 1.0 kadar seçer.

## <a name="if-your-app-targets-a-net-framework-version-earlier-than-47"></a>Uygulamanız .NET Framework sürüm 4.7'den önceki hedefliyorsa

Aşağıdaki bölümlerde kullanarak belirli bir TLS veya SSL sürümü ayarları doğrulamak için kodunuzu denetle:

### <a name="for-net-framework-46---462-and-not-wcf"></a>.NET Framework 4.6 - 4.6.2 ve WCF değil

Ayarlama `DontEnableSystemDefaultTlsVersions` `AppContext` geçiş `false`. Bkz: [AppContext anahtarlar yoluyla güvenlik yapılandırma](#configuring-security-via-appcontext-switches).

### <a name="for-wcf-using-net-framework-46---462-using-tcp-transport-security-with-certificate-credentials"></a>WCF için .NET Framework 4.6 - TCP taşıma güvenliği sertifikası kimlik bilgilerini kullanarak 4.6.2 kullanma

En son işletim sistemi düzeltme eklerini yüklemeniz gerekir. Bkz: [güvenlik güncelleştirmeleri](#security-updates).

Bir iletişim kuralı sürüm açıkça yapılandırmadığınız sürece WCF framework TLS 1.2 kadar kullanılabilir en yüksek protokol otomatik olarak seçer. Daha fazla bilgi için önceki bölümde bkz [taşıma güvenliği sertifikası kimlik bilgilerini kullanarak için WCF TCP Aktarım](#wcf-tcp-cert).

### <a name="for-net-framework-35---451-and-not-wcf"></a>.NET Framework 3.5 - 4.5.1 ve WCF değil

.NET Framework 4.7 veya sonraki sürümler için uygulamanızı yükseltme öneririz. Yükseltemiyorsanız, aşağıdaki adımları uygulayın. .NET Framework 4.7 veya sonraki sürümler için'ı yükseltmeden belirli bir noktada gelecekte uygulamanızı başarısız olabilir.

Ayarlama [SchUseStrongCrypto](#schusestrongcrypto) ve [SystemDefaultTlsVersions](#systemdefaulttlsversions) kayıt defteri anahtarlarını 1. Bkz: [Windows kayıt defteri aracılığıyla güvenliği yapılandırma](#configuring-security-via-the-windows-registry). .NET Framework sürüm 3.5 destekleyen `SchUseStrongCrypto` yalnızca zaman açık bir TLS değer geçirilen bayrak.

.NET Framework 3.5 üzerinde çalıştırıyorsanız, TLS 1.2 programınız tarafından belirtilebilir böylece etkin bir düzeltme eki yüklemeniz gerekir:

| [KB3154518](https://support.microsoft.com/kb/3154518) | Güvenilirlik toplaması HR-1605 - Windows 7 SP1 ve Server 2008 R2 SP1 üzerinde .NET Framework 3.5.1 TLS sistem varsayılan sürümleri için destek dahil |
| --- | --- |
| [KB3154519](https://support.microsoft.com/kb/3154519) | Güvenilirlik toplaması HR-1605 - TLS sistem varsayılan .NET Framework 3.5 Windows Server 2012 dahil sürümleri için destek |
| [KB3154520](https://support.microsoft.com/kb/3154520) | Güvenilirlik toplaması HR-1605 - TLS sistem varsayılan sürümleri için destek dahil Windows 8.1 ve Windows Server 2012 R2 üzerinde .NET Framework 3.5 |
| [KB3156421](https://support.microsoft.com/kb/3156421) | .NET Framework 4.5.2 ve 4.5.1 Windows 1605 düzeltme dökümü 3154521 |

### <a name="for-wcf-using-net-framework-35---452-using-tcp-transport-security-with-certificate-credentials"></a>WCF için .NET Framework 3.5 - TCP taşıma güvenliği sertifikası kimlik bilgilerini kullanarak 4.5.2 kullanma

Bu WCF framework'ün değerleri SSL 3.0 ve TLS 1.0 kullanmak için sabit kodlanmış sürümleridir. Bu değerler değiştirilemez. Güncelleştirme ve TLS 1.1 ve 1.2 kullanmak için NET Framework 4.6 veya sonraki sürümler için yeniden hedefleyin.

## <a name="if-your-app-targets-net-framework-35"></a>Uygulamanız .NET Framework 3.5 hedefliyorsa

.NET framework veya işletim sistemi çekme izin vererek yerine bir güvenlik protokolü güvenlik protokolü açıkça ayarlamanız gerekir, ekleme `SecurityProtocolTypeExtensions` ve `SslProtocolsExtension` kodunuza numaralandırmalar. `SecurityProtocolTypeExtensions` ve `SslProtocolsExtension` için değerler arasında `Tls12`, `Tls11`ve `SystemDefault` değeri. Bkz: [TLS sistem varsayılan Windows 8.1 ve Windows Server 2012 R2 üzerinde .NET Framework 3.5 dahil sürümleri için destek](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework).

<a name="configuring-security-via-appcontext-switches"></a>

## <a name="configuring-security-via-appcontext-switches-for-net-framework-46-or-later-versions"></a>Güvenlik AppContext aracılığıyla yapılandırma geçer (.NET Framework 4.6 veya sonraki sürümler)

[AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) Bu bölümde açıklanan anahtarları ilgili ise, uygulama hedefler ya da çalışır, .NET Framework 4.6 veya sonraki sürümler. Varsayılan olarak ya da bunları açıkça ayarlayarak anahtarları olup olmayacağını `false` mümkünse. Bir veya iki anahtarlar yoluyla güvenlik yapılandırmak istiyorsanız, bir güvenlik protokolü değeri kodunuzda belirtmeyin; Bunu yaparsanız, bu nedenle kaçmış anahtarlar geçersiz kılarsınız.

HTTP ağ yaptığınız olup olmadığını anahtarlar aynı etkiye sahiptir (<xref:System.Net.ServicePointManager>) veya TCP Yuvaları ağ (<xref:System.Net.Security.SslStream>).

### <a name="switchsystemnetdontenableschusestrongcrypto"></a>Switch.System.Net.DontEnableSchUseStrongCrypto

Değerini `false` için `Switch.System.Net.DontEnableSchUseStrongCrypto` güçlü şifreleme kullanmak uygulamanızı neden olur. Değerini `false` için `DontEnableSchUseStrongCrypto` daha güvenli ağ protokollerini (TLS 1.2, TLS 1.1 ve TLS 1.0) kullanır ve güvenli olmayan protokolleri engeller. Daha fazla bilgi için bkz: [SCH_USE_STRONG_CRYPTO bayrağı](#the-schusestrongcrypto-flag). Değerini `true` uygulamanız için güçlü şifreleme devre dışı bırakır.

Uygulamanız .NET Framework 4.6 veya sonraki sürümler hedefliyorsa, bu anahtar için varsayılan olarak `false`. Öneririz güvenli varsayılan olmasıdır. Uygulamanız .NET Framework 4.6 üzerinde çalışır, ancak önceki bir sürümünü hedefler, anahtar için varsayılan olarak `true`. Bu durumda, açıkça ayarlamanız `false`.

`DontEnableSchUseStrongCrypto` yalnızca bir oluşmalıdır `true` güçlü şifreleme desteği ve yükseltilemez eski hizmetlerine bağlanmak gerekiyorsa.

### <a name="switchsystemnetdontenablesystemdefaulttlsversions"></a>Switch.System.Net.DontEnableSystemDefaultTlsVersions

Değerini `false` için `Switch.System.Net.DontEnableSystemDefaultTlsVersions` işletim sisteminin protokolünü seçmenize izin vermek, uygulamanızın neden olur. Değerini `true` uygulamanız .NET Framework tarafından çekilen protokoller kullanmasına neden olur.

Uygulamanız .NET Framework 4.7 veya sonraki sürümler hedefliyorsa, bu anahtar için varsayılan olarak `false`. Öneririz güvenli bir varsayılan olmasıdır. Uygulamanız .NET Framework 4.7 veya sonraki sürümlerinde çalışır, ancak önceki bir sürümünü hedefler, anahtar için varsayılan olarak `true`. Bu durumda, açıkça ayarlamanız `false`.

### <a name="switchsystemservicemodeldisableusingservicepointmanagersecurityprotocols"></a>Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols

Değerini `false` için `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` tanımlı değeri kullanmak uygulamanızı neden `ServicePointManager.SecurityProtocols` sertifikası kimlik bilgilerini kullanarak ileti güvenliği için. Değerini `true` TLS1.0 kadar kullanılabilir en yüksek protokolünü kullanır

.NET Framework 4.7 ve sonraki sürümlerini hedefleyen uygulamalar için varsayılan olarak bu değer `false`. .NET Framework 4.6.2 hedefleyen uygulamalar için ve önceki sürümleri, bu değer için varsayılan olarak `true`.

### <a name="switchsystemservicemodeldontenablesystemdefaulttlsversions"></a>Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions

Değerini `false` için `Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions` işletim sisteminin protokolünü seçmenize izin vermek için varsayılan yapılandırmayı ayarlar. Değerini `true` TLS1.2 kadar kullanılabilir en yüksek protokol için varsayılan ayarlar.

.NET Framework 4.7.1 ve sonraki sürümlerini hedefleyen uygulamalar için varsayılan olarak bu değer `false`. .NET Framework 4.7 ve önceki hedefleyen uygulamalar için varsayılan olarak bu değer `true`.

TLS protokolleri hakkında daha fazla bilgi için bkz: [azaltma: TLS protokolleri](../migration-guide/mitigation-tls-protocols.md). Hakkında daha fazla bilgi için `AppContext` anahtarlar bkz [ `<AppContextSwitchOverrides> Element` ](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

## <a name="configuring-security-via-the-windows-registry"></a>Windows kayıt defteri aracılığıyla güvenliği yapılandırma

Aşağıdakilerden birini veya her ikisi de ayarlıyorsanız `AppContext` anahtarları bir seçenek değildir, bu bölümde açıklanan Windows kayıt defteri anahtarları, uygulamanızın kullandığı güvenlik protokollerini kontrol edebilirsiniz. Aşağıdakilerden birini veya her ikisini de kullanmanız mümkün olmayabilir `AppContext` uygulamanız .NET Framework sürümü 4.6'den önceki hedefler ya da yapılandırma dosyasını düzenleyemezsiniz geçer. Güvenlik kayıt defteri ile yapılandırmak istiyorsanız, bir güvenlik protokolü değeri kodunuzda belirtmeyin; Bunu yaparsanız, bu nedenle kayıt defteri geçersiz kılarsınız.

Kayıt defteri anahtarlarını adlarını ilgili adlarına benzer `AppContext` olmadan anahtarları bir `DontEnable` adına etkileşimlidir. Örneğin, `AppContext` geçiş `DontEnableSchUseStrongCrypto` kayıt defteri anahtarı adlı [SchUseStrongCrypto](#schusestrongcrypto).

Bu anahtarlar var olduğu yeni bir güvenlik düzeltme eki tüm .NET Framework sürümlerinde kullanılabilir. Bkz: [güvenlik güncelleştirmeleri](#security-updates).

HTTP ağ yaptığınız olup olmadığını aşağıda açıklanan kayıt defteri anahtarlarını tümünün aynı etkiye sahiptir (<xref:System.Net.ServicePointManager>) veya TCP Yuvaları ağ (<xref:System.Net.Security.SslStream>).

### <a name="schusestrongcrypto"></a>SchUseStrongCrypto

`HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SchUseStrongCrypto` Kayıt defteri anahtarı DWORD türünde değerine sahip. 1 değeri, güçlü şifreleme kullanmak uygulamanızı neden olur. Güçlü şifreleme daha güvenli ağ protokollerini (TLS 1.2, TLS 1.1 ve TLS 1.0) kullanır ve güvenli olmayan protokolleri engeller. 0 değeri, güçlü şifreleme devre dışı bırakır. Daha fazla bilgi için bkz: [SCH_USE_STRONG_CRYPTO bayrağı](#the-schusestrongcrypto-flag).

Uygulamanız .NET Framework 4.6 veya sonraki sürümler hedefliyorsa, bu anahtar değerini 1 olarak varsayar. Öneririz güvenli bir varsayılan olmasıdır. Uygulamanız .NET Framework 4.6 üzerinde çalışır, ancak önceki bir sürümünü hedefler, anahtar varsayılanı 0. Bu durumda, açıkça değerini 1 olarak ayarlamanız gerekir.

Güçlü şifreleme desteği ve yükseltilemez eski hizmetlerine bağlanmak gerekiyorsa bu anahtar yalnızca 0 değeri olmalıdır.

### <a name="systemdefaulttlsversions"></a>SystemDefaultTlsVersions

`HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SystemDefaultTlsVersions` Kayıt defteri anahtarı DWORD türünde değerine sahip. 1 değeri, işletim sisteminin protokolünü seçmenize izin vermek, uygulamanızın neden olur. 0 değeri uygulamanız .NET Framework tarafından çekilen protokoller kullanmasına neden olur.

`<VERSION>` v4.0.30319 (.NET Framework 4 ve üzeri için) veya v2.0.50727 (.NET Framework 3.5 için) olması gerekir.

Uygulamanız .NET Framework 4.7 veya sonraki sürümler hedefliyorsa, bu anahtar değerini 1 olarak varsayar. Öneririz güvenli bir varsayılan olmasıdır. Uygulamanız .NET Framework 4.7 veya sonraki sürümlerinde çalışır, ancak önceki bir sürümünü hedefler, anahtar 0 olarak varsayar. Bu durumda, açıkça değerini 1 olarak ayarlamanız gerekir.

Daha fazla bilgi için bkz: [güncelleştirme Windows 10 sürüm 1511 için toplu ve Windows Server 2016 Technical Preview 4: 10 Mayıs 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016).

.NET framework 3.5.1 ile daha fazla bilgi için bkz: [TLS sistem varsayılan Windows 7 SP1 ve Server 2008 R2 SP1 üzerinde .NET Framework 3.5.1 dahil sürümleri için destek](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework).

Aşağıdaki _. REG_ dosyasını, en güvenli değerlerine kayıt defteri anahtarları ve bunların türevleri ayarlar:

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

## <a name="configuring-schannel-protocols-in-the-windows-registry"></a>Windows Kayıt Defteri'nde Schannel protokolleri yapılandırma

İstemci ve/veya sunucu uygulamanızı görüşür protokoller üzerinden hassas bir denetim için kayıt defterini kullanabilirsiniz. Uygulamanızın ağ Schannel gider (için başka bir ad olduğu [güvenli kanal](https://msdn.microsoft.com/library/windows/desktop/aa380123). Yapılandırarak `Schannel`, uygulamanızın davranışını yapılandırabilirsiniz.

İle başlayan `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols` kayıt defteri anahtarı. Bu anahtarın altında tüm alt kümesinde oluşturabilirsiniz `SSL 2.0`, `SSL 3.0`, `TLS 1.0`, `TLS 1.1`, ve `TLS 1.2`. Her bu anahtarlarını altında alt anahtarları oluşturabilirsiniz `Client` ve/veya `Server`. Altında `Client` ve `Server`, DWORD değerlerini oluşturabilirsiniz `DisabledByDefault` (0 veya 1) ve `Enabled` (0 veya 0xFFFFFFFF).

## <a name="the-schusestrongcrypto-flag"></a>SCH_USE_STRONG_CRYPTO bayrağı

Bu etkinleştirildiğinde (varsayılan olarak, tarafından bir `AppContext` geçiş, veya Windows kayıt defteri tarafından), .NET Framework kullanan `SCH_USE_STRONG_CRYPTO` TLS güvenlik protokolü, uygulamanız istediğinde, bayrak. `SCH_USE_STRONG_CRYPTO` Bayrağı ile varsayılan olarak, etkinleştirilebilir `AppContext` geçiş, veya kayıt defteri ile. İşletim sistemi bayrak geçirir `Schannel`bilinen zayıf şifreleme algoritmalarını devre dışı bırakmak için talimatını için paketleri ve aksi durumda daha iyi birlikte çalışabilirlik için etkinleştirilebilir TLS/SSL protokol sürümleri şifre. Daha fazla bilgi için bkz.:

- [Güvenli kanal](https://msdn.microsoft.com/library/windows/desktop/aa380123)
- [SCHANNEL_CRED yapısı](https://msdn.microsoft.com/library/windows/desktop/aa379810)

`SCH_USE_STRONG_CRYPTO` Bayrağı için geçirilen de `Schannel` açıkça kullandığınızda `Tls` (TLS 1.0) `Tls11`, veya `Tls12` değerlerini numaralandırılan <xref:System.Net.SecurityProtocolType> veya <xref:System.Security.Authentication.SslProtocols>.

## <a name="security-updates"></a>Güvenlik güncelleştirmeleri

Bu makalede en iyi uygulamaları en son güvenlik güncelleştirmelerinin yüklenmesini bağlıdır. Bu güncelleştirmeler Gelişmiş .NET Framework 4.7 ve daha yeni özellikleri kullanma yeteneğini içerir. En son güvenlik güncelleştirmelerini uygulamanız .NET Framework 4.7 ve sonraki sürümleri çalışıyorsa (önceki bir sürümünü hedefleyen olsa bile) önemlidir.

TLS kullanmak için en iyi sürümünü seçmek işletim sistemi izin vermek için .NET Framework'ü güncelleştirmek için en az yüklemeniz gerekir:

- [.NET Framework Ağustos 2017 kalite toplaması önizlemesini](https://blogs.msdn.microsoft.com/dotnet/2017/08/16/net-framework-august-2017-preview-of-quality-rollup).
- **Veya** [.NET Framework Eylül 2017 güvenliği ve kalite toplaması](https://blogs.msdn.microsoft.com/dotnet/2017/09/12/net-framework-september-2017-security-and-quality-rollup).

Ayrıca bkz.:

- [.NET framework sürümleri ve bağımlılıkları](../migration-guide/versions-and-dependencies.md)
- [Nasıl yapılır: hangi .NET Framework sürümlerinin yüklü olduğunu belirleme](../migration-guide/how-to-determine-which-versions-are-installed.md).

## <a name="support-for-tls-12"></a>TLS 1.2 desteği

TLS 1.2, işletim sistemi ve .NET Framework sürümünü anlaşmak üzere uygulamanız için hem TLS 1.2 desteklemesi gerekir.

**TLS 1.2 desteklemek için işletim sistemi gereksinimleri**

Etkinleştirmek veya TLS 1.2 ve/veya TLS 1.1 onları destekleyen bir sistemde yeniden etkinleştirmek için bkz: [Aktarım Katmanı Güvenliği (TLS) kayıt defteri ayarları](/windows-server/security/tls/tls-registry-settings).

| **İŞLETİM SİSTEMİ** | **TLS 1.2 desteği** |
| --- | --- |
| Windows 10</br>Windows Server 2016 | Desteklenen ve varsayılan olarak etkindir. |
| Windows 8.1</br>Windows Server 2012 R2 | Desteklenen ve varsayılan olarak etkindir. |
| Windows 8.0</br>Windows Server 2012 | Desteklenen ve varsayılan olarak etkindir. |
| Windows 7 SP1</br>Windows Server 2008 R2 SP1 | , Varsayılan olarak etkin değildir ancak desteklenir. Bkz: [Aktarım Katmanı Güvenliği (TLS) kayıt defteri ayarları](/windows-server/security/tls/tls-registry-settings) TLS 1.2 etkinleştirme hakkında ayrıntılar için web sayfası. |
| Windows Server 2008 | TLS 1.2 ve TLS 1.1 desteği güncelleştirilmesi gerekiyor. Bkz: [Windows Server 2008 SP2'de TLS 1.1 ve TLS 1.2 desteği eklemek için güncelleştirme](https://support.microsoft.com/help/4019276/update-to-add-support-for-tls-1-1-and-tls-1-2-in-windows-server-2008-s). |
| Windows Vista | Desteklenmez. |

Hangi TLS/SSL protokolleri etkin her Windows sürümü varsayılan olarak daha fazla bilgi için bkz [protokolleri de TLS/SSL'deki (Schannel SSP)](https://msdn.microsoft.com/library/windows/desktop/mt808159).

**.NET Framework 3.5 TLS 1.2 desteğiyle gereksinimleri**

Bu tablo, TLS 1.2 .NET Framework 3.5 ile desteklemek gereken işletim sistemi güncelleştirme gösterir. Tüm işletim sistemi güncelleştirmeleri uygulamanızı öneririz.

| **İŞLETİM SİSTEMİ** | **TLS 1.2 .NET Framework 3.5 ile desteklemek için gereken en düşük güncelleştirme** |
| --- | --- |
| Windows 10</br>Windows Server 2016 | [Windows 10 sürüm 1511 için toplu güncelleştirme ve Windows Server 2016 Technical Preview 4: 10 Mayıs 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016) |
| Windows 8.1</br>Windows Server 2012 R2 | [TLS sistem varsayılan Windows 8.1 ve Windows Server 2012 R2 üzerinde .NET Framework 3.5 dahil sürümleri için destek](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 8.0</br>Windows Server 2012 | [TLS sistem varsayılan .NET Framework 3.5 Windows Server 2012 dahil sürümleri için destek](https://support.microsoft.com/help/3154519/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 7 SP1</br>Windows Server 2008 R2 SP1 | [TLS sistem varsayılan Windows 7 SP1 ve Server 2008 R2 SP1 üzerinde .NET Framework 3.5.1 dahil sürümleri için destek](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Server 2008 | [TLS sistem varsayılan Windows Vista SP2 ve Server 2008 SP2 üzerinde .NET Framework 2.0 SP2 dahil sürümleri için destek](https://support.microsoft.com/help/3154517/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Vista | Desteklenmez |

## <a name="azure-cloud-services"></a>Azure bulut Hizmetleri

Kullanıyorsanız [Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) barındırmak ve uygulamanızı çalıştırmak için Web ve çalışan rolleri desteklemek için TLS 1.2 dikkate almanız gereken bazı noktalar vardır.

### <a name="net-framework-47-is-not-installed-on-azure-guest-os-by-default"></a>.NET framework 4.7 varsayılan olarak Azure konuk işletim sisteminde yüklü değil

En son Azure konuk işletim sistemi ailesi 5 sürümde (Windows Server 2016) yüklü en son sürümü 4.6.2 değil. Her Azure konuk işletim sisteminde hangi .NET Framework sürümlerinin yüklendiğini görmek için bkz: [Azure konuk işletim sistemi sürümleri ve SDK uyumluluk matrisi](https://docs.microsoft.com/azure/cloud-services/cloud-services-guestos-update-matrix).

Uygulamanızı Azure konuk işletim sistemi sürümünde kullanılabilir olmayan bir .NET Framework sürüm hedefliyorsa, kendiniz yüklemeniz gerekir. Bkz: [Azure bulut hizmeti rollerinde .NET yükleme](https://docs.microsoft.com/azure/cloud-services/cloud-services-dotnet-install-dotnet). Framework yüklemesi bir yeniden başlatma gerektirirse, hizmet rolleri de için hazır duruma girmeden önce yeniden başlatılabilir.

### <a name="azure-guest-os-registry-settings"></a>Azure konuk işletim sistemi kayıt defteri ayarları

Azure konuk işletim sistemi görüntü için [Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) zaten `SchUseStrongCrypto` kayıt defteri anahtarı değerini 1 olarak ayarlayın. Daha fazla bilgi için bkz: [SchUseStrongCrypto](#schusestrongcrypto).

Ayarlama [SystemDefaultTlsVersions](#systemdefaulttlsversions) kayıt defteri anahtarının 1. Bkz: [Windows kayıt defteri aracılığıyla güvenliği yapılandırma](#configuring-security-via-the-windows-registry).
