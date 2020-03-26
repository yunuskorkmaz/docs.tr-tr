---
title: .NET Framework ile Taşıma Katmanı Güvenliği (TLS) en iyi uygulamaları
description: .NET Framework ile Aktarım Katmanı Güvenliği (TLS) kullanarak en iyi uygulamaları açıklar
ms.date: 10/22/2018
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
ms.openlocfilehash: d1218e5db2ee4fc0ec044c6e0aa16187390708b0
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134381"
---
# <a name="transport-layer-security-tls-best-practices-with-the-net-framework"></a>.NET Framework ile Taşıma Katmanı Güvenliği (TLS) en iyi uygulamaları

Ulaşım Katmanı Güvenliği (TLS) protokolü, Internet üzerinden iletilen bilgilerin gizliliğini korumaya yardımcı olmak için tasarlanmış bir endüstri standardıdır. [TLS 1.2,](https://tools.ietf.org/html/rfc5246) önceki sürümlere göre güvenlik iyileştirmeleri sağlayan bir standarttır. TLS 1.2 sonunda daha hızlı ve daha iyi güvenlik vardır yeni yayımlanan standart [TLS 1.3](https://tools.ietf.org/html/rfc8446) ile değiştirilecektir. Bu makalede, TLS protokolünü kullanan .NET Framework uygulamalarının güvenliğini sağlamak için öneriler sunuz.

.NET Framework uygulamalarının güvenli kalmasını sağlamak için **not** TLS sürümü kodlanmamalıdır. .NET Framework uygulamaları, işletim sisteminin (OS) desteklediği TLS sürümünü kullanmalıdır.

Bu belge, şu şekilde olan geliştiricileri hedefler:

- Doğrudan API'leri <xref:System.Net> kullanarak <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> (örneğin, ve). <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- Ad alanını kullanarak Doğrudan WCF istemcilerini <xref:System.ServiceModel?displayProperty=nameWithType> ve hizmetlerini kullanma.

Şunları yapmanızı öneririz:

- Uygulamalarınızda .NET Framework 4.7 veya sonraki sürümlerihedefleyin. WCF uygulamalarınızda .NET Framework 4.7.1 veya sonraki sürümlerihedefleyin.
- TLS sürümünü belirtmeyin. TLS sürümünde işletim sistemi karar verecek şekilde kodunuzu yapılandırın.
- TLS veya SSL sürümü belirtmediğinizi doğrulamak için kapsamlı bir kod denetimi gerçekleştirin.

Uygulamanız işletim sistemi TLS sürümünü seçmesine izin verdiğinde:

- Gelecekte eklenen TLS 1.3 gibi yeni protokollerden otomatik olarak yararlanır.
- İşletim sistemi, güvenli olmadığı keşfedilen protokolleri engeller.

[Kodunuzu denetle ve kod değişiklikleri yapmak](#audit-your-code-and-make-code-changes) bölümü, kodunuzu denetlemeyi ve güncellemeyi kapsar.

Bu makalede, uygulamanızın hedefleyip çalıştığı .NET Framework sürümü için mevcut en güçlü güvenliği nasıl etkinleştirinsağlayacağıaçık. Bir uygulama açıkça bir güvenlik protokolü ve sürümü belirlediğinde, başka bir alternatifi devre dışı bırakıp .NET Framework ve OS varsayılan davranışını devre dışı bırakmaz. Uygulamanızın TLS 1.2 bağlantısı üzerinde anlaşma yapabilmesini istiyorsanız, açıkça daha düşük bir TLS sürümüne ayar yapmak TLS 1.2 bağlantısını engeller.

Bir protokol sürümünü niçin kodlamaktan kaçınamıyorsanız, TLS 1.2 belirtmenizi şiddetle öneririz. TLS 1.0 bağımlılıklarını belirleme ve kaldırma kılavuzu için [TLS 1.0 Problem ilerle meyplerini](https://www.microsoft.com/download/details.aspx?id=55266) indirin.

WCF TLS1.0, 1.1 ve 1.2'yi .NET Framework 4.7'de varsayılan olarak destekler. .NET Framework 4.7.1 ile başlayarak, WCF işletim sistemi yapılandırılmış sürümü varsayılan. Bir uygulama açıkça `SslProtocols.None`yapılandırılırsa, WCF NetTcp aktarımını kullanırken işletim sistemi varsayılan ayarını kullanır.

Bu belge yle ilgili soruları .NET Framework ile GitHub sorunu [Taşıma Katmanı Güvenliği 'nde (TLS) en iyi uygulamalarda](https://github.com/dotnet/docs/issues/4675)sorabilirsiniz.

## <a name="audit-your-code-and-make-code-changes"></a>Kodunuzu denetle ve kod değişiklikleri yapma

ASP.NET uygulamalar için,.NET Framework'ün amaçlanan sürümünü kullandığınızı doğrulamak için `<system.web><httpRuntime targetFramework>` _web.config_ öğesini inceleyin.

Windows Formları ve diğer uygulamalar için [bkz.](/visualstudio/ide/visual-studio-multi-targeting-overview)

Belirli bir TLS veya SSL sürümünü kullanmadığınızı doğrulamak için aşağıdaki bölümleri kullanın.

## <a name="if-your-app-targets-net-framework-47-or-later-versions"></a>Uygulamanız .NET Framework 4.7 veya sonraki sürümleri hedefliyorsa

Aşağıdaki bölümlerde belirli bir TLS veya SSL sürümünü kullanmadığınızı nasıl doğrulayabileceğiniz gösterin.

### <a name="for-http-networking"></a>HTTP ağ için

<xref:System.Net.ServicePointManager>, .NET Framework 4.7 ve sonraki sürümleri kullanarak, işletim sistemi yapılandırılmış varsayılan güvenlik protokolü kullanır. Varsayılan işletim sistemi seçimini almak için, mümkünse, <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> özellik için varsayılan <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>olarak .

Ayar, <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType> işletim <xref:System.Net.ServicePointManager> sistemi tarafından yapılandırılan varsayılan güvenlik protokolünün kullanılmasına neden olduğundan, uygulamanız çalıştırdığı işletim sistemine bağlı olarak farklı şekilde çalışabilir. Örneğin, Windows 7 SP1 TLS 1.0 kullanırken, Windows 8 ve Windows 10 TLS 1.2 kullanır.

BU makalenin geri kalanı, HTTP ağ için .NET Framework 4.7 veya sonraki sürümlerini hedeflerken ilgili değildir.

### <a name="for-tcp-sockets-networking"></a>TCP soketleri ağ için

<xref:System.Net.Security.SslStream>, .NET Framework 4.7 ve sonraki sürümleri kullanarak, en iyi güvenlik protokolü ve sürümünü seçerek işletim sistemi varsayılan. Varsayılan işletim sistemi en iyi seçim almak için, mümkünse, bu <xref:System.Net.Security.SslStream> <xref:System.Security.Authentication.SslProtocols> açık bir parametre almak yöntemi aşırı kullanmayın. Aksi takdirde, geçmek <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>. Kullanmamanızı <xref:System.Security.Authentication.SslProtocols.Default>öneririz; ayar, `SslProtocols.Default` SSL 3.0 /TLS 1.0 kullanımını zorlar ve TLS 1.2'yi önler.

Özellik için bir değer <xref:System.Net.ServicePointManager.SecurityProtocol> ayarlamayın (HTTP ağ için).

Açık <xref:System.Net.Security.SslStream> <xref:System.Security.Authentication.SslProtocols> bir parametre (TCP soketleri ağ için) almak yöntemi aşırı kullanmayın. Uygulamanızı .NET Framework 4.7 veya sonraki sürümlere yeniden hedeflediğinizde, en iyi uygulama önerisini takip ediyor olacaksınız.

TCP soketleri ağı için .NET Framework 4.7 veya sonraki sürümleri hedeflenirken bu konunun geri kalanı ilgili değildir.

<a name="wcf-tcp-cert"></a>

### <a name="for-wcf-tcp-transport-using-transport-security-with-certificate-credentials"></a>Sertifika kimlik bilgilerini içeren taşıma güvenliğini kullanan WCF TCP taşıması için

WCF, .NET Framework'ün geri kalanıyla aynı ağ yığınını kullanır.

4.7.1 hedefliyorsanız, WCF açıkça yapılandırılmadığı sürece, işletim sistemi varsayılan olarak en iyi güvenlik protokolünü seçmesine izin verecek şekilde yapılandırılmıştır:

- Uygulama yapılandırma dosyanızda.
- **Veya,** kaynak kodunda uygulamanızda.

Varsayılan olarak,.NET Framework 4.7 ve sonraki sürümler TLS 1.2 kullanacak şekilde yapılandırılır ve TLS 1.1 veya TLS 1.0 kullanarak bağlantılara izin verir. WCF'yi, bağlamanızı kullanmak <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>üzere yapılandırarak işletim sistemi en iyi güvenlik protokolünü seçmesine izin verecek şekilde yapılandırın. Bu ayarlanabilir. <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols> `SslProtocols.None`adresinden <xref:System.ServiceModel.NetTcpSecurity.Transport>erişilebilir. `NetTcpSecurity.Transport`adresinden <xref:System.ServiceModel.NetTcpBinding.Security>erişilebilir.

Özel bir bağlama kullanıyorsanız:

- WCF'yi, işletim sistemi kullanımı <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols> <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>ayarlayarak en iyi güvenlik protokolünü seçmesine izin verecek şekilde yapılandırın.
- **Veya** yapılandırma yolu `system.serviceModel/bindings/customBinding/binding/sslStreamSecurity:sslProtocols`ile kullanılan protokolü yapılandırın.

Özel bir bağlama **kullanmıyorsanız** **ve** yapılandırmayı kullanarak WCF bağlamanızı ayarlıyorsanız, yapılandırma `system.serviceModel/bindings/netTcpBinding/binding/security/transport:sslProtocols`yolu ile kullanılan protokolü ayarlayın.

### <a name="for-wcf-message-security-with-certificate-credentials"></a>Sertifika kimlik bilgilerine sahip WCF İleti Güvenliği için

.NET Framework 4.7 ve sonraki sürümler varsayılan <xref:System.Net.ServicePointManager.SecurityProtocol> olarak özellikte belirtilen protokolü kullanır. [AppContextSwitch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` `true`ayarlandığında, WCF TLS 1.0'a kadar en iyi protokolü seçer.

## <a name="if-your-app-targets-a-net-framework-version-earlier-than-47"></a>Uygulamanız 4,7'den önce bir .NET Framework sürümünü hedefliyorsa

Aşağıdaki bölümleri kullanarak belirli bir TLS veya SSL sürümü ayarlamadığınızı doğrulamak için kodunuzu denetlayın:

### <a name="for-net-framework-46---462-and-not-wcf"></a>.NET Framework 4.6 - 4.6.2 için değil, WCF

Anahtarı `DontEnableSystemDefaultTlsVersions` `AppContext` ' `false`ya ayarlama Bkz. [AppContext anahtarları ile güvenliği yapılandırma.](#configuring-security-via-appcontext-switches)

### <a name="for-wcf-using-net-framework-46---462-using-tcp-transport-security-with-certificate-credentials"></a>WCF için .NET Framework 4.6 - 4.6.2 kullanarak Sertifika Kimlik Bilgileri ile TCP taşıma güvenliğini kullanarak

En son işletim sistemi yamaları yüklemeniz gerekir. [Bkz. Güvenlik güncelleştirmeleri.](#security-updates)

WCF çerçevesi, bir protokol sürümünü açıkça yapılandırmadığınız sürece TLS 1.2'ye kadar kullanılabilen en yüksek protokolü otomatik olarak seçer. Daha fazla bilgi için, [sertifika kimlik bilgilerini içeren aktarım güvenliğini kullanarak WCF TCP aktarımiçin](#wcf-tcp-cert)önceki bölüme bakın.

### <a name="for-net-framework-35---452-and-not-wcf"></a>.NET Framework 3.5 - 4.5.2 için ve WCF için değil

Uygulamanızı .NET Framework 4.7 veya sonraki sürümlere yükseltmenizi öneririz. Yükseltme yapamıyorsanız, aşağıdaki adımları izleyin.

[SchUseStrongCrypto](#schusestrongcrypto) ve [SystemDefaultTlsVersions](#systemdefaulttlsversions) kayıt defteri anahtarlarını 1 olarak ayarlayın. Bkz. [Windows Kayıt Defteri üzerinden güvenliği yapılandırma.](#configuring-security-via-the-windows-registry) .NET Framework sürüm 3.5 `SchUseStrongCrypto` bayrağı yalnızca açık bir TLS değeri geçirildiğinde destekler.

.NET Framework 3.5 üzerinde çalışıyorsanız, TLS 1.2'nin programınız tarafından belirtilen bir sıcak yama yüklemeniz gerekir:

| [KB3154518](https://support.microsoft.com/kb/3154518) | Güvenilirlik Rollup HR-1605 - Windows 7 SP1 ve Server 2008 R2 SP1'de .NET Framework 3.5.1'de yer alan TLS Sistem Varsayılan Sürümleri desteği |
| --- | --- |
| [KB3154519](https://support.microsoft.com/kb/3154519) | Güvenilirlik Rollup HR-1605 - Windows Server 2012'de .NET Framework 3.5'te yer alan TLS Sistem Varsayılan Sürümleri için destek |
| [KB3154520](https://support.microsoft.com/kb/3154520) | Güvenilirlik Rollup HR-1605 -Windows 8.1 ve Windows Server 2012 R2.NET Framework 3.5'te yer alan TLS Sistem Varsayılan Sürümleri için destek |
| [KB3156421](https://support.microsoft.com/kb/3156421) | 1605 Hotfix rollup 3154521 .NET Framework 4.5.2 ve 4.5.1 Için Windows |

### <a name="for-wcf-using-net-framework-35---452-using-tcp-transport-security-with-certificate-credentials"></a>WCF için .NET Framework 3.5 - 4.5.2 kullanarak Sertifika Kimlik Bilgileri ile TCP taşıma güvenliğini kullanarak

WCF çerçevesinin bu sürümleri SSL 3.0 ve TLS 1.0 değerlerini kullanmak üzere kodlanır. Bu değerler değiştirilemez. TLS 1.1 ve 1.2'yi kullanmak için NET Framework 4.6 veya sonraki sürümleri güncelleştirmeli ve yeniden hedeflemeniz gerekir.

## <a name="if-your-app-targets-net-framework-35"></a>Uygulamanız .NET Framework 3.5'i hedefliyorsa

.NET veya OS'nin güvenlik protokolünü seçmesine izin vermek yerine `SecurityProtocolTypeExtensions` açıkça `SslProtocolsExtension` bir güvenlik protokolü ayarlamanız gerekiyorsa, kodunuza ekleme ve ekleme ler ekleyin. `SecurityProtocolTypeExtensions`ve `SslProtocolsExtension` , `Tls12`ve `Tls11` `SystemDefault` değer için değerleri içerir. Daha fazla bilgi [için, Windows 8.1 ve Windows Server 2012 R2'de .NET Framework 3.5'te yer alan TLS Sistem Varsayılan Sürümleri Desteği'ne](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework)bakın.

<a name="configuring-security-via-appcontext-switches"></a>

## <a name="configuring-security-via-appcontext-switches-for-net-framework-46-or-later-versions"></a>AppContext anahtarları ile güvenliği yapılandırma (.NET Framework 4.6 veya sonraki sürümler için)

Bu bölümde açıklanan [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) anahtarları, uygulamanız .NET Framework 4.6 veya daha sonraki sürümleri hedefliyorsa veya üzerinde çalışıyorsa alakalıdır. İster varsayılan olarak, ister açıkça ayarlayarak, anahtarlar mümkünse olmalıdır. `false` Güvenliği bir veya her iki anahtar üzerinden yapılandırmak istiyorsanız, kodunuzda bir güvenlik protokolü değeri belirtmeyin; bunu yapmak anahtarı (es) geçersiz kılar.

Anahtarlar, ISTER HTTP ağ ( )<xref:System.Net.ServicePointManager>ister TCP soketleri ağ<xref:System.Net.Security.SslStream>() yapıyor olun aynı etkiye sahiptir.

### <a name="switchsystemnetdontenableschusestrongcrypto"></a>Switch.System.Net.DontEnableSchUseStrongCrypto

For `Switch.System.Net.DontEnableSchUseStrongCrypto` değeri `false` uygulamanızın güçlü şifreleme kullanmasına neden olur. Daha güvenli `false` `DontEnableSchUseStrongCrypto` ağ protokolleri (TLS 1.2, TLS 1.1 ve TLS 1.0) kullanımları için bir değer ve güvenli olmayan protokolleri engeller. Daha fazla bilgi için [SCH_USE_STRONG_CRYPTO bayrağına](#the-sch_use_strong_crypto-flag)bakın. Uygulamanız `true` için güçlü şifrelemeyi devre dışı düşürme değeri.

Uygulamanız .NET Framework 4.6 veya daha sonraki sürümleri `false`hedefliyorsa, bu anahtar varsayılan olarak . Bu güvenli bir varsayılan, biz tavsiye ediyoruz. Uygulamanız .NET Framework 4.6'da çalışıyorsa, ancak önceki `true`bir sürümü hedefliyorsa, anahtar varsayılan olarak . Bu durumda, açıkça '' olarak `false`ayarlamanız gerekir.

`DontEnableSchUseStrongCrypto`yalnızca güçlü şifrelemeyi `true` desteklemeyen ve yükseltilmeyen eski hizmetlere bağlanmanız gerekiyorsa bir değere sahip olmanız gerekir.

### <a name="switchsystemnetdontenablesystemdefaulttlsversions"></a>Switch.System.Net.DontEnableSystemDefaultTlsVersions

`false` For `Switch.System.Net.DontEnableSystemDefaultTlsVersions` değeri, uygulamanızın işletim sisteminin protokolü seçmesine izin almasına neden olur. Uygulamanızın `true` .NET Framework tarafından seçilen protokolleri kullanmasına neden olan bir değerdir.

Uygulamanız .NET Framework 4.7 veya sonraki sürümleri hedefliyorsa, bu anahtar varsayılan olarak `false`. Bu, önerdiğimiz güvenli bir varsayılandır. Uygulamanız .NET Framework 4.7 veya daha sonraki sürümlerde çalışıyorsa, `true`ancak daha önceki bir sürümü hedefliyorsa, anahtar varsayılan olarak . Bu durumda, açıkça '' olarak `false`ayarlamanız gerekir.

### <a name="switchsystemservicemodeldisableusingservicepointmanagersecurityprotocols"></a>Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols

"for" `false` `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` değeri, uygulamanızın sertifika kimlik `ServicePointManager.SecurityProtocols` bilgilerini kullanarak ileti güvenliği için tanımlanan değeri kullanmasına neden olur. TLS1.0'a kadar mevcut en yüksek protokolü kullanma değeri `true`

.NET Framework 4.7 ve sonraki sürümleri hedefleyen uygulamalar için `false`bu değer varsayılan . .NET Framework 4.6.2 ve daha öncesini hedefleyen uygulamalar `true`için bu değer varsayılan .

### <a name="switchsystemservicemodeldontenablesystemdefaulttlsversions"></a>Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions

`false` For `Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions` değeri, işletim sisteminin protokolü seçmesine izin vermek için varsayılan yapılandırmayı ayarlar. `true` Değer, varsayılan değeri kullanılabilir en yüksek protokole ayarlar, TLS1.2'ye kadar.

.NET Framework 4.7.1 ve sonraki sürümleri hedefleyen uygulamalar için `false`bu değer varsayılan . .NET Framework 4.7 ve daha önceki leri hedefleyen `true`uygulamalariçin bu değer varsayılan .

TLS protokolleri hakkında daha fazla bilgi için [bkz: Azaltma: TLS Protokolleri.](../migration-guide/mitigation-tls-protocols.md) Anahtarlar hakkında `AppContext` daha fazla [`<AppContextSwitchOverrides> Element`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)bilgi için bkz.

## <a name="configuring-security-via-the-windows-registry"></a>Windows Kayıt Defteri üzerinden güvenliği yapılandırma

> [!WARNING]
> Kayıt defteri anahtarlarını ayarlamak sistemdeki tüm uygulamaları etkiler. Bu seçeneği yalnızca makinenin tam denetimindeyseniz ve kayıt defterindeki değişiklikleri denetleyebilirseniz kullanın.

Bir veya her `AppContext` iki anahtarı ayarlamak bir seçenek değilse, uygulamanızın kullandığı güvenlik protokollerini bu bölümde açıklanan Windows Registry anahtarlarıyla denetleyebilirsiniz. Uygulamanız .NET Framework 4.5.2 veya önceki sürümlerde çalışıyorsa veya yapılandırma dosyasını düzenlemebilmiyorsanız, anahtarlardan birini veya her ikisini `AppContext` de kullanamayabilirsiniz. Güvenliği kayıt defteriyle yapılandırmak istiyorsanız, kodunuzda bir güvenlik protokolü değeri belirtmeyin; bunu yapmak, kayıt defteri ayarını geçersiz kılar.

Kayıt defteri anahtarlarının adları, ilgili `AppContext` anahtarların adlarına benzer, `DontEnable` ancak ada hazırlık sızdırılır. Örneğin, `AppContext` anahtar `DontEnableSchUseStrongCrypto` [SchUseStrongCrypto](#schusestrongcrypto)adlı kayıt defteri anahtarıdır.

Bu anahtarlar, yeni bir güvenlik düzeltme eki bulunan tüm .NET Framework sürümlerinde kullanılabilir. [Bkz. Güvenlik güncelleştirmeleri.](#security-updates)

Aşağıda açıklanan tüm kayıt defteri anahtarları, HTTP ağ ()<xref:System.Net.ServicePointManager>veya TCP soketleri ağ<xref:System.Net.Security.SslStream>() yapıyor sanız aynı etkiye sahiptir.

### <a name="schusestrongcrypto"></a>SchuseStrongCrypto

Kayıt `HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SchUseStrongCrypto` defteri anahtarıdword türünde bir değere sahiptir. 1 değeri uygulamanızın güçlü şifreleme kullanmasına neden olur. Güçlü şifreleme, daha güvenli ağ protokolleri (TLS 1.2, TLS 1.1 ve TLS 1.0) kullanır ve güvenli olmayan protokolleri engeller. 0 değeri güçlü şifrelemeyi devre dışı kılabilir. Daha fazla bilgi için [SCH_USE_STRONG_CRYPTO bayrağına](#the-sch_use_strong_crypto-flag)bakın.

Uygulamanız .NET Framework 4.6 veya sonraki sürümleri hedefliyorsa, bu anahtar varsayılan değeri 1 olarak alır. Bu, önerdiğimiz güvenli bir varsayılandır. Uygulamanız .NET Framework 4.5.2 veya önceki sürümleri hedefliyorsa, anahtar varsayılan olarak 0'a ayarlanır. Bu durumda, değerini açıkça 1 olarak ayarlamanız gerekir.

Bu anahtarın değeri yalnızca güçlü şifrelemeyi desteklemeyen ve yükseltilmeyen eski hizmetlere bağlanmanız gerekiyorsa 0 değerine sahip olmalıdır.

### <a name="systemdefaulttlsversions"></a>SystemDefaultTlsVersions

Kayıt `HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SystemDefaultTlsVersions` defteri anahtarıdword türünde bir değere sahiptir. 1 değeri, uygulamanızın işletim sisteminin protokolü seçmesine izin almasına neden olur. 0 değeri, uygulamanızın .NET Framework tarafından seçilen protokolleri kullanmasına neden olur.

`<VERSION>`v4.0.30319 (.NET Framework 4 ve üzeri için) veya v2.0.50727 (.NET Framework 3.5 için) olmalıdır.

Uygulamanız .NET Framework 4.7 veya sonraki sürümleri hedefliyorsa, bu anahtar varsayılan değeri 1 olarak alır. Bu, önerdiğimiz güvenli bir varsayılandır. Uygulamanız .NET Framework 4.6.1 veya önceki sürümleri hedefliyorsa, anahtar varsayılan olarak 0'a ayarlanır. Bu durumda, değerini açıkça 1 olarak ayarlamanız gerekir.

Daha fazla bilgi [için Windows 10 Sürüm 1511 ve Windows Server 2016 Teknik Önizleme 4: 10 Mayıs 2016 için Kümülatif Güncelleştirme'ye](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016)bakın.

.NET Framework 3.5.1 ile ilgili daha fazla bilgi [için, Windows 7 SP1 ve Server 2008 R2 SP1'de .NET Framework 3.5.1'de yer alan TLS Sistem Varsayılan Sürümleri](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework)desteğine bakın.

Aşağıdaki _. REG_ dosyası, kayıt defteri anahtarlarını ve bunların türevlerini en güvenli değerlerine ayarlar:

```text
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

## <a name="configuring-schannel-protocols-in-the-windows-registry"></a>Windows Kayıt Defteri'nde Schannel protokollerini yapılandırma

Kayıt defterini, istemcinizin ve/veya sunucu uygulamanızın müzakere ettiği protokoller üzerinde ince gelişmiş denetim için kullanabilirsiniz. Uygulamanızın ağ Schannel [(Güvenli Kanal](/windows/desktop/SecAuthN/secure-channel)için başka bir addır. Yapılayarak `Schannel`uygulamanızın davranışını yapılandırabilirsiniz.

Kayıt defteri `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols` anahtarıyla başlayın. Bu tuşun altında, `SSL 2.0`, , `SSL 3.0` `TLS 1.0` `TLS 1.1`, ve `TLS 1.2`. Bu alt tuşların her birinin altında, alt tuşlar `Client` ve/veya. `Server` Altında `Client` `Server`ve, DWORD değerleri `DisabledByDefault` (0 veya `Enabled` 1) ve (0 veya 0xFFFFFFFF) oluşturabilirsiniz.

## <a name="the-sch_use_strong_crypto-flag"></a><a name="the-sch_use_strong_crypto-flag"></a>SCH_USE_STRONG_CRYPTO bayrağı

Etkinleştirildiğinde (varsayılan olarak, bir `AppContext` anahtar veya Windows Kayıt Defteri tarafından), .NET `SCH_USE_STRONG_CRYPTO` Framework uygulamanız bir TLS güvenlik protokolü istediğinde bayrağı kullanır. Bayrak `SCH_USE_STRONG_CRYPTO` varsayılan olarak, `AppContext` anahtarla veya Kayıt Defteri ile etkinleştirilebilir. İşletim sistemi, `Schannel`bilinen zayıf şifreleme algoritmalarını, şifreleme paketlerini ve daha iyi birlikte çalışabilirlik için etkinleştirilebilecek TLS/SSL iletişim kuralı sürümlerini devre dışı bırakmatalimatı vermek için bayrağı geçer. Daha fazla bilgi için bkz.

- [Güvenli Kanal](/windows/desktop/SecAuthN/secure-channel)
- [SCHANNEL_CRED yapısı](/windows/win32/api/schannel/ns-schannel-schannel_cred)

`SCH_USE_STRONG_CRYPTO` Bayrak, `Schannel` `Tls` (TLS 1.0) `Tls11`veya numaralandırılmış değerleri açıkça `Tls12` kullandığınızda da <xref:System.Net.SecurityProtocolType> geçirilir. <xref:System.Security.Authentication.SslProtocols>

## <a name="security-updates"></a>Güvenlik güncelleştirmeleri

Bu makaledeki en iyi uygulamalar, yüklenen son güvenlik güncelleştirmelerine bağlıdır. Bu güncelleştirmeler gelişmiş .NET Framework 4.7 ve sonraki özellikleri kullanma olanağını içerir. Uygulamanız .NET Framework 4.7 ve sonraki sürümlerinde çalışıyorsa (daha önceki bir sürümü hedefalse bile) son güvenlik güncelleştirmeleri önemlidir.

.NET Framework'ü güncelleştirerek işletim sisteminin tls'nin en iyi sürümünü seçmesine izin vermek için en az yüklemeniz gerekir:

- [.NET Framework Ağustos 2017 Kalite Toplama Önizlemesi](https://devblogs.microsoft.com/dotnet/net-framework-august-2017-preview-of-quality-rollup/).
- **Veya** [.NET Framework Eylül 2017 Güvenlik ve Kalite Toplama](https://devblogs.microsoft.com/dotnet/net-framework-september-2017-security-and-quality-rollup/).

Ayrıca bkz:

- [.NET Framework Sürümleri ve Bağımlılıkları](../migration-guide/versions-and-dependencies.md)
- [Nasıl Yapılır: Hangi .NET Framework Sürümlerinin Yüklü olduğunu belirleyin.](../migration-guide/how-to-determine-which-versions-are-installed.md)

## <a name="support-for-tls-12"></a>TLS 1.2 Desteği

Uygulamanızın TLS 1.2 ile pazarlık edebilmek için, işletim sistemi ve .NET Framework sürümünün TLS 1.2'yi desteklemesi gerekir.

**TLS 1.2 desteği sunmak için işletim sistemi gereksinimleri**

TLS 1.2 ve/veya TLS 1.1'i destekleyen bir sistemde etkinleştirmek veya yeniden etkinleştirmek için [Taşıma Katmanı Güvenliği (TLS) kayıt defteri ayarlarına](/windows-server/security/tls/tls-registry-settings)bakın.

| **İşletim Sistemi** | **TLS 1.2 desteği** |
| --- | --- |
| Windows 10<br>Windows Server 2016 | Desteklenen ve varsayılan olarak etkinleştirildi. |
| Windows 8.1<br>Windows Server 2012 R2 | Desteklenen ve varsayılan olarak etkinleştirildi. |
| Windows 8.0<br>Windows Server 2012 | Desteklenen ve varsayılan olarak etkinleştirildi. |
| Windows 7 SP1<br>Windows Server 2008 R2 SP1 | Desteklenen, ancak varsayılan olarak etkin değil. TLS 1.2'yi etkinleştirme hakkında ayrıntılı bilgi için [Taşıma Katmanı Güvenliği (TLS) kayıt defteri ayarları](/windows-server/security/tls/tls-registry-settings) web sayfasına bakın. |
| Windows Server 2008 | TLS 1.2 ve TLS 1.1 desteği için güncelleme gerekmektedir. [Windows Server 2008 SP2'de TLS 1.1 ve TLS 1.2 desteği eklemek için Güncelleme'ye](https://support.microsoft.com/help/4019276/update-to-add-support-for-tls-1-1-and-tls-1-2-in-windows-server-2008-s)bakın. |
| Windows Vista | Desteklenmiyor. |

Windows'un her sürümünde varsayılan olarak hangi TLS/SSL protokollerinin etkinleştirildiği hakkında bilgi için [TLS/SSL (Schannel SSP) protokollerine](/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-)bakın.

**.NET Framework 3.5 ile TLS 1.2 desteği sunmaya yönelik gereksinimler**

Bu tablo, .NET Framework 3.5 ile TLS 1.2'yi desteklemeniz gereken işletim sistemi güncelleştirmesini gösterir. Tüm işletim sistemi güncelleştirmelerini uygulamanızı öneririz.

| **İşletim Sistemi** | **.NET Framework 3.5 ile TLS 1.2'yi desteklemek için gereken minimum güncelleme** |
| --- | --- |
| Windows 10<br>Windows Server 2016 | [Windows 10 Sürüm 1511 ve Windows Server 2016 Teknik Önizleme 4 Için Kümülatif Güncelleştirme 4: 10 Mayıs 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016) |
| Windows 8.1<br>Windows Server 2012 R2 | [Windows 8.1 ve Windows Server 2012 R2'de .NET Framework 3.5'te yer alan TLS Sistem Varsayılan Sürümleri desteği](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 8.0<br>Windows Server 2012 | [Windows Server 2012'de .NET Framework 3.5'te yer alan TLS Sistem Varsayılan Sürümleri desteği](https://support.microsoft.com/help/3154519/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 7 SP1<br>Windows Server 2008 R2 SP1 | [Windows 7 SP1 ve Server 2008 R2 SP1'de .NET Framework 3.5.1'de yer alan TLS Sistem Varsayılan Sürümleri desteği](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Server 2008 | [Windows Vista SP2 ve Server 2008 SP2'de .NET Framework 2.0 SP2'de yer alan TLS Sistem Varsayılan Sürümleri desteği](https://support.microsoft.com/help/3154517/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Vista | Desteklenmiyor |
