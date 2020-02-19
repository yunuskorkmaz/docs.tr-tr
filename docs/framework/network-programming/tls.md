---
title: .NET Framework ile Aktarım Katmanı Güvenliği (TLS) en iyi uygulamaları
description: .NET Framework ile Aktarım Katmanı Güvenliği (TLS) kullanan en iyi uygulamaları açıklar
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
ms.openlocfilehash: bae6bf6a1a5d87241b619bf024c099c48af6af43
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452688"
---
# <a name="transport-layer-security-tls-best-practices-with-the-net-framework"></a>.NET Framework ile Aktarım Katmanı Güvenliği (TLS) en iyi uygulamaları

Aktarım Katmanı Güvenliği (TLS) protokolü, Internet üzerinden gönderilen bilgilerin gizliliğini korumaya yardımcı olmak üzere tasarlanmış bir sektör standardıdır. [TLS 1,2](https://tools.ietf.org/html/rfc5246) , önceki sürümlere yönelik güvenlik geliştirmeleri sağlayan bir standarttır. TLS 1,2, daha hızlı ve güvenliği artmıştır ve en yeni yayınlanan standart [TLS 1,3](https://tools.ietf.org/html/rfc8446) ile değiştirilmiştir. Bu makalede, TLS protokolünü kullanan .NET Framework uygulamalarının güvenliğini sağlamaya yönelik öneriler sunulmaktadır.

.NET Framework uygulamaların güvende kalmasını sağlamak için TLS sürümü **sabit olarak kodlanmamalıdır.** .NET Framework uygulamalar, işletim sisteminin (OS) desteklediği TLS sürümünü kullanmalıdır.

Bu belge şunları hedefler:

- <xref:System.Net> API 'Leri kullanarak doğrudan (örneğin, <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> ve <xref:System.Net.Security.SslStream?displayProperty=nameWithType>).
- <xref:System.ServiceModel?displayProperty=nameWithType> ad alanını kullanarak WCF istemcileri ve hizmetlerini doğrudan kullanarak.
- Uygulamanızı barındırmak ve çalıştırmak için [Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) Web ve çalışan rollerini kullanma. [Azure Cloud Services](#azure-cloud-services) bölümüne bakın.

Şunları yapmanızı öneririz:

- Uygulamalarınızda .NET Framework 4,7 veya sonraki sürümleri hedefleyin. WCF uygulamalarınızda .NET Framework 4.7.1 veya üzeri sürümleri hedefleyin.
- TLS sürümünü belirtmeyin. İşletim sisteminin TLS sürümünde karar vermesini sağlamak için kodunuzu yapılandırın.
- Bir TLS veya SSL sürümü belirtmediğinizi doğrulamak için kapsamlı bir kod denetimi gerçekleştirin.

Uygulamanız işletim sistemi için TLS sürümünü seçmesini sağlar:

- Bu, ileride eklenen TLS 1,3 gibi yeni protokollerin avantajlarından yararlanır.
- İşletim sistemi, bulduğu protokollerin güvenli hale getirilmesine izin vermez.

Kodunuzun denetimini [denetlemesi ve kod değişikliklerinin](#audit-your-code-and-make-code-changes) güncelleştirilmesi, kodunuzun denetlenmesini ve güncelleştirilmesini kapsamaktadır.

Bu makalede, uygulamanızın hedeflediği ve üzerinde çalıştığı .NET Framework sürümü için kullanılabilen en güçlü güvenlik nasıl etkinleştirileceği açıklanır. Bir uygulama açık olarak bir güvenlik protokolü ve sürümü ayarlarsa, diğer diğer alternatifler ve .NET Framework ve işletim sistemi varsayılan davranışının dışına çıkar. Uygulamanızın bir TLS 1,2 bağlantısı anlaşmasına sahip olmasını istiyorsanız, daha düşük bir TLS sürümüne açıkça ayarlamak TLS 1,2 bağlantısını engeller.

Bir protokol sürümünün kodlanmasını önlemek için TLS 1,2 belirtmenizi önemle tavsiye ederiz. TLS 1,0 bağımlılıklarını tanımlama ve kaldırma hakkında yönergeler için, [tls 1,0 sorun](https://www.microsoft.com/download/details.aspx?id=55266) teknik incelemesini karşıdan yükleyin.

WCF, .NET Framework 4,7 ' de varsayılan olarak TLS 1.0, 1,1 ve 1,2 ' ü destekler. .NET Framework 4.7.1 ile başlayarak, WCF varsayılan olarak işletim sistemi tarafından yapılandırılan sürüme göre yapılır. Bir uygulama `SslProtocols.None`ile açıkça yapılandırıldıysa, WCF, NetTcp aktarımını kullanırken işletim sistemi varsayılan ayarını kullanır.

Bu belge hakkında, GitHub sorun [Aktarım Katmanı Güvenliği (TLS) en iyi uygulamalarında](https://github.com/dotnet/docs/issues/4675)bu belgeyle ilgili soru sorabilirsiniz .NET Framework.

## <a name="audit-your-code-and-make-code-changes"></a>Kodunuzu denetleme ve kod değişiklikleri yapma

ASP.NET uygulamalar için, .NET Framework hedeflenen sürümünü kullandığınızı doğrulamak üzere _Web. config_ ' in `<system.web><httpRuntime targetFramework>` öğesini inceleyin.

Windows Forms ve diğer uygulamalar için bkz. [nasıl yapılır: .NET Framework bir sürümünü hedefleme](/visualstudio/ide/visual-studio-multi-targeting-overview).

Belirli bir TLS veya SSL sürümü kullanmadığınız doğrulamak için aşağıdaki bölümleri kullanın.

## <a name="if-your-app-targets-net-framework-47-or-later-versions"></a>Uygulamanız .NET Framework 4,7 veya sonraki sürümlerini hedefliyorsa

Aşağıdaki bölümlerde, belirli bir TLS veya SSL sürümü kullanmadığınız nasıl doğrulanımız gösterilmektedir.

### <a name="for-http-networking"></a>HTTP ağı için

<xref:System.Net.ServicePointManager>, .NET Framework 4,7 ve sonraki sürümleri kullanarak işletim sisteminde yapılandırılmış varsayılan güvenlik protokolünü kullanır. Mümkünse varsayılan işletim sistemi seçimini almak için, <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>varsayılan olarak <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> özelliği için bir değer ayarlayamazsınız.

<xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType> ayarı <xref:System.Net.ServicePointManager> işletim sistemi tarafından yapılandırılan varsayılan güvenlik protokolünü kullanmasına neden olduğundan, uygulamanız üzerinde çalıştığı IŞLETIM sistemine göre farklı şekilde çalışabilir. Örneğin, Windows 7 SP1, Windows 8 ve Windows 10 TLS 1,2 kullanırken TLS 1,0 kullanır.

Bu makalenin geri kalanı, HTTP ağı için .NET Framework 4,7 veya sonraki sürümleri hedeflerken ilgili değildir.

### <a name="for-tcp-sockets-networking"></a>TCP yuvaları ağı için

<xref:System.Net.Security.SslStream>, .NET Framework 4,7 ve sonraki sürümleri kullanarak en iyi güvenlik protokolü ve sürümünü seçme işletim sistemi varsayılan olarak belirlenmiştir. Mümkünse varsayılan işletim sistemi en iyi seçimini almak için, açık bir <xref:System.Security.Authentication.SslProtocols> parametresi alan <xref:System.Net.Security.SslStream> 'nin yöntem aşırı yüklerini kullanmayın. Aksi takdirde, <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>geçirin. <xref:System.Security.Authentication.SslProtocols.Default>kullanmanızı öneririz; `SslProtocols.Default` ayarı SSL 3,0/TLS 1,0 kullanımını zorlar ve TLS 1,2 ' i engeller.

<xref:System.Net.ServicePointManager.SecurityProtocol> özelliği için bir değer ayarlama (HTTP ağı için).

Açık bir <xref:System.Security.Authentication.SslProtocols> parametresi alan <xref:System.Net.Security.SslStream> (TCP yuvaları ağı için) yöntem aşırı yüklerini kullanmayın. Uygulamanızı 4,7 veya sonraki sürümlere .NET Framework yeniden hedeflemeniz durumunda en iyi yöntemler önerisi takip edersiniz.

Bu konunun geri kalanı, TCP yuvaları ağı için .NET Framework 4,7 veya sonraki sürümleri hedeflerken ilgili değildir.

<a name="wcf-tcp-cert"></a>

### <a name="for-wcf-tcp-transport-using-transport-security-with-certificate-credentials"></a>Sertifika kimlik bilgileriyle aktarım güvenliğini kullanan WCF TCP taşıması için

WCF, .NET Framework geri kalanı ile aynı ağ yığınını kullanır.

4\.7.1 hedefliyorsanız, WCF açıkça yapılandırılmadığı takdirde, işletim sisteminin varsayılan olarak en iyi güvenlik protokolünü seçmesine izin verecek şekilde yapılandırılır:

- Uygulama yapılandırma dosyanızda.
- Kaynak kodundaki uygulamanızda **veya**.

Varsayılan olarak, .NET Framework 4,7 ve sonraki sürümler TLS 1,2 kullanacak şekilde yapılandırılmıştır ve TLS 1,1 veya TLS 1,0 kullanılarak bağlantılara izin verir. <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>kullanmak için bağlamayı yapılandırarak işletim sisteminin en iyi güvenlik protokolünü seçmesine izin vermek için WCF 'yi yapılandırın. Bu, <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>ayarlanabilir. `SslProtocols.None` <xref:System.ServiceModel.NetTcpSecurity.Transport>erişilebilir. `NetTcpSecurity.Transport` <xref:System.ServiceModel.NetTcpBinding.Security>erişilebilir.

Özel bir bağlama kullanıyorsanız:

- <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>kullanmak üzere <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols> ayarlayarak, işletim sisteminin en iyi güvenlik protokolünü seçmesine izin vermek için WCF 'yi yapılandırın.
- **Veya** `system.serviceModel/bindings/customBinding/binding/sslStreamSecurity:sslProtocols`yapılandırma yoluyla kullanılan protokolü yapılandırın.

Özel bir bağlama kullanmıyorsanız **ve** **yapılandırma kullanarak WCF** bağlamasını ayarlıyorsanız, `system.serviceModel/bindings/netTcpBinding/binding/security/transport:sslProtocols`yapılandırma yoluyla kullanılan protokolü ayarlayın.

### <a name="for-wcf-message-security-with-certificate-credentials"></a>Sertifika kimlik bilgileriyle WCF Ileti güvenliği için

.NET Framework 4,7 ve sonraki sürümleri, varsayılan olarak <xref:System.Net.ServicePointManager.SecurityProtocol> özelliğinde belirtilen protokolü kullanır. [Appcontextswitch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` `true`olarak AYARLANDıĞıNDA, WCF en iyi protokol olan TLS 1,0 ' i seçer.

## <a name="if-your-app-targets-a-net-framework-version-earlier-than-47"></a>Uygulamanız 4,7 sürümünden önceki bir .NET Framework sürümünü hedefliyorsa

Aşağıdaki bölümleri kullanarak belirli bir TLS veya SSL sürümü ayarlamadığınızı doğrulamak için kodunuzu denetleyin:

### <a name="for-net-framework-46---462-and-not-wcf"></a>.NET Framework 4,6-4.6.2 ve WCF değil

`DontEnableSystemDefaultTlsVersions` `AppContext` anahtarını `false`olarak ayarlayın. Bkz. [AppContext anahtarları aracılığıyla güvenliği yapılandırma](#configuring-security-via-appcontext-switches).

### <a name="for-wcf-using-net-framework-46---462-using-tcp-transport-security-with-certificate-credentials"></a>.NET Framework 4,6-4.6.2 kullanan WCF için sertifika kimlik bilgileriyle TCP aktarım güvenliği kullanma

En son işletim sistemi düzeltme eklerini yüklemelisiniz. Bkz. [güvenlik güncelleştirmeleri](#security-updates).

WCF çerçevesi, açıkça bir protokol sürümü yapılandırmadığınız takdirde TLS 1,2 'e kadar kullanılabilir en yüksek protokolü otomatik olarak seçer. Daha fazla bilgi için, [sertifika kimlik bilgileriyle Transport Security 'yi kullanarak WCF TCP aktarımı için](#wcf-tcp-cert)yukarıdaki bölüme bakın.

### <a name="for-net-framework-35---452-and-not-wcf"></a>.NET Framework 3,5-4.5.2 ve WCF değil

Uygulamanızı .NET Framework 4,7 veya sonraki sürümlere yükseltmenizi öneririz. Yükseltmezsiniz, aşağıdaki adımları uygulayın. Gelecekteki bir noktada uygulamanız .NET Framework 4,7 veya sonraki sürümlere yükseltilene kadar başarısız olabilir.

[Schusestrongşifre](#schusestrongcrypto) ve [Systemdefaulttlsversions](#systemdefaulttlsversions) kayıt defteri anahtarlarını 1 olarak ayarlayın. Bkz. [Windows kayıt defteri aracılığıyla güvenliği yapılandırma](#configuring-security-via-the-windows-registry). .NET Framework sürüm 3,5, yalnızca açık bir TLS değeri geçirildiğinde `SchUseStrongCrypto` bayrağını destekler.

.NET Framework 3,5 ' de çalıştırıyorsanız, program tarafından TLS 1,2 ' nin belirtibilmesi için bir sık yama yüklemeniz gerekir:

| [KB3154518](https://support.microsoft.com/kb/3154518) | Güvenilirlik toplaması HR-1605-Windows 7 SP1 ve Server 2008 R2 SP1 'de .NET Framework 3.5.1 'de bulunan TLS sistem varsayılan sürümleri için destek |
| --- | --- |
| [KB3154519](https://support.microsoft.com/kb/3154519) | Güvenilirlik toplaması HR-1605-Windows 2012 Server 'daki .NET Framework 3,5 ' de bulunan TLS sistem varsayılan sürümleri desteği |
| [KB3154520](https://support.microsoft.com/kb/3154520) | Güvenilirlik toplaması HR-1605-Windows 8.1 ve Windows Server 2012 R2 'de 3,5 .NET Framework bulunan TLS sistem varsayılan sürümleri için destek |
| [KB3156421](https://support.microsoft.com/kb/3156421) | Windows üzerinde .NET Framework 4.5.2 ve 4.5.1 için 1605 düzeltme paketi 3154521 |

### <a name="for-wcf-using-net-framework-35---452-using-tcp-transport-security-with-certificate-credentials"></a>.NET Framework 3,5-4.5.2 kullanan WCF için sertifika kimlik bilgileriyle TCP aktarım güvenliği kullanma

WCF çerçevesinin bu sürümleri, SSL 3,0 ve TLS 1,0 değerlerini kullanmak üzere sabit olarak kodlanmıştır. Bu değerler değiştirilemez. TLS 1,1 ve 1,2 ' i kullanmak için NET Framework 4,6 veya sonraki sürümlerini güncelleştirmeniz ve yeniden hedeflemeniz gerekir.

## <a name="if-your-app-targets-net-framework-35"></a>Uygulamanız 3,5 .NET Framework hedefliyorsa

.NET veya işletim sisteminin güvenlik protokolünü seçmesine izin vermek yerine açıkça bir güvenlik protokolü ayarlamanız gerekiyorsa, kodunuza `SecurityProtocolTypeExtensions` ve `SslProtocolsExtension` numaralandırmalar ekleyin. `SecurityProtocolTypeExtensions` ve `SslProtocolsExtension` `Tls12`, `Tls11`ve `SystemDefault` değeri için değerler içerir. Daha fazla bilgi için bkz. [Windows 8.1 ve Windows Server 2012 R2 'de .NET Framework 3,5 ' de bulunan TLS sistem varsayılan sürümleri Için destek](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework).

<a name="configuring-security-via-appcontext-switches"></a>

## <a name="configuring-security-via-appcontext-switches-for-net-framework-46-or-later-versions"></a>AppContext anahtarları aracılığıyla güvenliği yapılandırma (.NET Framework 4,6 veya sonraki sürümler için)

Bu bölümde açıklanan [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) geçişleri, uygulamanız .NET Framework 4,6 veya sonraki sürümleri hedefliyorsa veya üzerinde çalışıyorsa ilgilidir. Varsayılan olarak veya açıkça ayarlanarak, mümkünse anahtarlar `false` olmalıdır. Güvenliği bir veya her iki anahtarla yapılandırmak istiyorsanız, kodunuzda bir güvenlik protokolü değeri belirtmeyin; Bunu yapmak, anahtar (lar) öğesini geçersiz kılar.

Anahtarlar, HTTP ağı (<xref:System.Net.ServicePointManager>) veya TCP yuvaları ağı (<xref:System.Net.Security.SslStream>) yapıp yapsanız da aynı etkiye sahiptir.

### <a name="switchsystemnetdontenableschusestrongcrypto"></a>Switch.System.Net.DontEnableSchUseStrongCrypto

`Switch.System.Net.DontEnableSchUseStrongCrypto` için `false` değeri, uygulamanızın güçlü şifreleme kullanmasına neden olur. `DontEnableSchUseStrongCrypto` için `false` değeri, daha güvenli ağ protokolleri (TLS 1,2, TLS 1,1 ve TLS 1,0) kullanır ve güvenli olmayan protokolleri engeller. Daha fazla bilgi için [SCH_USE_STRONG_CRYPTO bayrağına](#the-sch_use_strong_crypto-flag)bakın. `true` değeri uygulamanız için güçlü şifrelemeyi devre dışı bırakır.

Uygulamanız .NET Framework 4,6 veya sonraki sürümlerini hedefliyorsa, bu anahtar varsayılan olarak `false`. Bu, önerdiğimiz güvenli bir varsayılan seçenektir. Uygulamanız .NET Framework 4,6 üzerinde çalışıyorsa, ancak önceki bir sürümü hedefliyorsa, anahtar varsayılan olarak `true`. Bu durumda, açıkça `false`olarak ayarlamanız gerekir.

`DontEnableSchUseStrongCrypto`, güçlü şifrelemeyi desteklemeyen ve yükseltilemeyen eski hizmetlere bağlanmanız gerekiyorsa `true` bir değere sahip olmalıdır.

### <a name="switchsystemnetdontenablesystemdefaulttlsversions"></a>Switch.System.Net.DontEnableSystemDefaultTlsVersions

`Switch.System.Net.DontEnableSystemDefaultTlsVersions` için `false` değeri, uygulamanızın işletim sisteminin Protokolü seçmesine izin vermesine neden olur. `true` değeri, uygulamanızın .NET Framework tarafından çekilen protokolleri kullanmasına neden olur.

Uygulamanız .NET Framework 4,7 veya sonraki sürümlerini hedefliyorsa, bu anahtar varsayılan olarak `false`. Bu, önerdiğimiz güvenli bir varsayılan seçenektir. Uygulamanız .NET Framework 4,7 veya sonraki sürümlerde çalışıyorsa, ancak önceki bir sürümü hedefliyorsa, anahtar varsayılan olarak `true`. Bu durumda, açıkça `false`olarak ayarlamanız gerekir.

### <a name="switchsystemservicemodeldisableusingservicepointmanagersecurityprotocols"></a>Switch. System. ServiceModel. DisableUsingServicePointManagerSecurityProtocols

`Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` için `false` değeri, uygulamanızın sertifika kimlik bilgilerini kullanarak ileti güvenliği için `ServicePointManager.SecurityProtocols` tanımlı değeri kullanmasına neden olur. `true` değeri en yüksek protokolü kullanır ve TLS 1.0 'a kadar kullanılabilir

.NET Framework 4,7 ve sonraki sürümleri hedefleyen uygulamalar için, bu değer varsayılan olarak `false`. .NET Framework 4.6.2 ve önceki sürümleri hedefleyen uygulamalar için, bu değer varsayılan olarak `true`.

### <a name="switchsystemservicemodeldontenablesystemdefaulttlsversions"></a>Switch. System. ServiceModel. DontEnableSystemDefaultTlsVersions

`Switch.System.ServiceModel.DontEnableSystemDefaultTlsVersions` için `false` değeri, işletim sisteminin Protokolü seçmesini sağlamak için varsayılan yapılandırmayı ayarlar. `true` değeri, varsayılan olarak en yüksek protokol olan TLS 1.2 'ye kadar ayarlanır.

.NET Framework 4.7.1 ve sonraki sürümleri hedefleyen uygulamalar için, bu değer varsayılan olarak `false`. .NET Framework 4,7 ve önceki sürümleri hedefleyen uygulamalar için, bu değer varsayılan olarak `true`.

TLS protokolleri hakkında daha fazla bilgi için bkz. [azaltma: TLS protokolleri](../migration-guide/mitigation-tls-protocols.md). `AppContext` anahtarları hakkında daha fazla bilgi için bkz. [`<AppContextSwitchOverrides> Element`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md).

## <a name="configuring-security-via-the-windows-registry"></a>Windows kayıt defteri aracılığıyla güvenliği yapılandırma

> [!WARNING]
> Kayıt defteri anahtarlarının ayarlanması sistemdeki tüm uygulamaları etkiler. Bu seçeneği yalnızca makinenin tam denetimine sahipseniz ve kayıt defterindeki değişiklikleri Denetleyebiliyorsanız kullanın.

`AppContext` anahtarlar bir veya her ikisi de ayarlandığında, uygulamanızın kullandığı güvenlik protokollerini bu bölümde açıklanan Windows kayıt defteri anahtarlarıyla denetleyebilirsiniz. Uygulamanız .NET Framework 4.5.2 veya önceki sürümlerde çalışıyorsa veya yapılandırma dosyasını düzenleyemeyeceksiniz, `AppContext` anahtarlarından birini veya her ikisini birden kullanamazsınız. Kayıt defteriyle güvenlik yapılandırmak istiyorsanız, kodunuzda bir güvenlik protokolü değeri belirtmeyin; Bunun yapılması kayıt defteri ayarını geçersiz kılar.

Kayıt defteri anahtarlarının adları, karşılık gelen `AppContext` anahtarlarının adlarına benzerdir ancak ada `DontEnable` eklenmiş olmaz. Örneğin, `AppContext` Switch `DontEnableSchUseStrongCrypto`, [Schusestrongşifre](#schusestrongcrypto)adlı kayıt defteri anahtarıdır.

Bu anahtarlar, son kullanılan güvenlik düzeltme eki olan tüm .NET Framework sürümlerde kullanılabilir. Bkz. [güvenlik güncelleştirmeleri](#security-updates).

Aşağıda açıklanan kayıt defteri anahtarlarının hepsi, HTTP ağı (<xref:System.Net.ServicePointManager>) veya TCP yuvaları ağı (<xref:System.Net.Security.SslStream>) yapıp yapsanız aynı etkiye sahiptir.

### <a name="schusestrongcrypto"></a>SchUseStrongCrypto

`HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SchUseStrongCrypto` kayıt defteri anahtarının DWORD türünde bir değeri vardır. 1 değeri, uygulamanızın güçlü şifrelemeyi kullanmasına neden olur. Güçlü şifreleme daha güvenli ağ protokolleri (TLS 1,2, TLS 1,1 ve TLS 1,0) kullanır ve güvenli olmayan protokolleri engeller. 0 değeri güçlü şifrelemeyi devre dışı bırakır. Daha fazla bilgi için [SCH_USE_STRONG_CRYPTO bayrağına](#the-sch_use_strong_crypto-flag)bakın.

Uygulamanız .NET Framework 4,6 veya sonraki sürümlerini hedefliyorsa, bu anahtar varsayılan değer olan 1 ' dir. Bu, önerdiğimiz güvenli bir varsayılan seçenektir. Uygulamanız .NET Framework 4,6 üzerinde çalışıyorsa, ancak önceki bir sürümü hedefliyorsa, anahtar varsayılan olarak 0 olur. Bu durumda, değerini açıkça 1 olarak ayarlamanız gerekir.

Bu anahtar yalnızca, güçlü şifrelemeyi desteklemeyen eski hizmetlere bağlanmanız gerekiyorsa 0 değerine sahip olmalıdır ve yükseltilemiyor.

### <a name="systemdefaulttlsversions"></a>SystemDefaultTlsVersions

`HKEY_LOCAL_MACHINE\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\<VERSION>: SystemDefaultTlsVersions` kayıt defteri anahtarının DWORD türünde bir değeri vardır. 1 değeri, uygulamanızın işletim sisteminin Protokolü seçmesine izin vermesine neden olur. 0 değeri, uygulamanızın .NET Framework tarafından çekilen protokolleri kullanmasına neden olur.

`<VERSION>` v 4.0.30319 (.NET Framework 4 ve üzeri için) veya v 2.0.50727 (.NET Framework 3,5 için) olmalıdır.

Uygulamanız .NET Framework 4,7 veya sonraki sürümlerini hedefliyorsa, bu anahtar varsayılan değer olan 1 ' dir. Bu, önerdiğimiz güvenli bir varsayılan seçenektir. Uygulamanız .NET Framework 4,7 veya sonraki sürümlerde çalışıyorsa, ancak önceki bir sürümü hedefliyorsa, anahtar varsayılan olarak 0 olur. Bu durumda, değerini açıkça 1 olarak ayarlamanız gerekir.

Daha fazla bilgi için bkz. [Windows 10 sürüm 1511 Için toplu güncelleştirme ve Windows Server 2016 Technical Preview 4:10 mayıs 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016).

.NET Framework 3.5.1 hakkında daha fazla bilgi için bkz. [Windows 7 SP1 ve Server 2008 R2 SP1 'de .NET Framework 3.5.1 'da bulunan TLS sistem varsayılan sürümleri Için destek](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework).

Şunları yapın _. REG_ dosyası kayıt defteri anahtarlarını ve türevlerini en güvenli değerlerine ayarlar:

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

## <a name="configuring-schannel-protocols-in-the-windows-registry"></a>Windows kayıt defterinde Schannel protokollerini yapılandırma

İstemci ve/veya sunucu uygulamanızın görüşdiği protokoller üzerinde ayrıntılı denetim için kayıt defterini kullanabilirsiniz. Uygulamanızın ağı Schannel üzerinden yapılır ( [güvenli kanal](/windows/desktop/SecAuthN/secure-channel)için başka bir addır. `Schannel`yapılandırarak uygulamanızın davranışını yapılandırabilirsiniz.

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols` kayıt defteri anahtarıyla başlayın. Bu anahtar altında, küme `SSL 2.0`, `SSL 3.0`, `TLS 1.0`, `TLS 1.1`ve `TLS 1.2`için herhangi bir alt anahtar oluşturabilirsiniz. Bu alt anahtarların her biri altında, `Client` ve/veya `Server`alt anahtarlar oluşturabilirsiniz. `Client` ve `Server`altında, `DisabledByDefault` (0 veya 1) ve `Enabled` (0 veya 0xFFFFFFFF) DWORD değerleri oluşturabilirsiniz.

## <a name="the-sch_use_strong_crypto-flag"></a>SCH_USE_STRONG_CRYPTO bayrağı

Etkinleştirildiğinde (varsayılan olarak, bir `AppContext` anahtarıyla veya Windows kayıt defteri tarafından), uygulamanız bir TLS güvenlik protokolü istediğinde .NET Framework `SCH_USE_STRONG_CRYPTO` bayrağını kullanır. `SCH_USE_STRONG_CRYPTO` bayrağı varsayılan olarak, `AppContext` anahtarıyla veya kayıt defteriyle etkinleştirilebilir. İşletim sistemi, daha iyi birlikte çalışabilirlik için devre dışı bırakılacak bilinen zayıf şifreleme algoritmalarını, şifre paketlerini ve TLS/SSL protokolü sürümlerini devre dışı bırakmayı bildirmek için bayrağını `Schannel`geçirir. Daha fazla bilgi için bkz.

- [Güvenli kanal](/windows/desktop/SecAuthN/secure-channel)
- [SCHANNEL_CRED yapısı](/windows/win32/api/schannel/ns-schannel-schannel_cred)

`SCH_USE_STRONG_CRYPTO` bayrağı Ayrıca, `Tls12` veya <xref:System.Net.SecurityProtocolType> `Tls` (TLS 1,0), `Tls11`veya <xref:System.Security.Authentication.SslProtocols>numaralandırılmış değerleri açıkça kullandığınızda `Schannel` ' a geçirilir.

## <a name="security-updates"></a>Güvenlik güncelleştirmeleri

Bu makaledeki en iyi uygulamalar, yüklenmekte olan en son güvenlik güncelleştirmelerine bağlıdır. Bu güncelleştirmeler, gelişmiş .NET Framework 4,7 ve sonraki özelliklerini kullanma imkanını içerir. Uygulamanız .NET Framework 4,7 ' de ve sonraki sürümlerde çalışıyorsa (önceki bir sürümü hedefliyorsa bile) son güvenlik güncelleştirmeleri önemlidir.

İşletim sisteminin kullanılacak en iyi TLS sürümünü seçmesine izin vermek üzere .NET Framework güncelleştirmek için, en azından şunu yüklemelisiniz:

- [Kalite toplamasının .NET Framework ağustos 2017 önizlemesi](https://devblogs.microsoft.com/dotnet/net-framework-august-2017-preview-of-quality-rollup/).
- **Ya** da [Eylül 2017 güvenlik ve kalite toplamasının .NET Framework](https://devblogs.microsoft.com/dotnet/net-framework-september-2017-security-and-quality-rollup/).

Ayrıca bkz:

- [.NET Framework Sürümleri ve Bağımlılıkları](../migration-guide/versions-and-dependencies.md)
- [Nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](../migration-guide/how-to-determine-which-versions-are-installed.md).

## <a name="support-for-tls-12"></a>TLS 1.2 desteği

Uygulamanızın TLS 1,2 anlaşması yapması için, işletim sisteminin ve .NET Framework sürümünün her ikisi de TLS 1,2 ' i desteklemelidir.

**TLS 1.2 desteği sunmak için işletim sistemi gereksinimleri**

TLS 1,2 ve/veya TLS 1,1 'yi destekleyen bir sistemde etkinleştirmek veya yeniden etkinleştirmek için bkz. [Aktarım Katmanı Güvenliği (TLS) kayıt defteri ayarları](/windows-server/security/tls/tls-registry-settings).

| **OS** | **TLS 1,2 desteği** |
| --- | --- |
| Windows 10<br>Windows Server 2016 | Desteklenen ve varsayılan olarak etkindir. |
| Windows 8.1<br>Windows Server 2012 R2 | Desteklenen ve varsayılan olarak etkindir. |
| Windows 8,0<br>Windows Server 2012 | Desteklenen ve varsayılan olarak etkindir. |
| Windows 7 SP1<br>Windows Server 2008 R2 SP1 | , Varsayılan olarak etkin değildir ancak desteklenir. TLS 1,2 ' i etkinleştirme hakkında daha fazla bilgi için bkz. [Aktarım Katmanı Güvenliği (TLS) kayıt defteri ayarları](/windows-server/security/tls/tls-registry-settings) Web sayfası. |
| Windows Server 2008 | TLS 1,2 ve TLS 1,1 desteği için bir güncelleştirme gerekiyor. [Windows Server 2008 SP2 'de tls 1,1 ve tls 1,2 desteği eklemek Için güncelleştirme](https://support.microsoft.com/help/4019276/update-to-add-support-for-tls-1-1-and-tls-1-2-in-windows-server-2008-s)bölümüne bakın. |
| Windows Vista | Desteklenmiyor. |

Her Windows sürümünde varsayılan olarak hangi TLS/SSL protokollerinin etkinleştirildiği hakkında bilgi için bkz. [TLS/SSL (Schannel SSP) protokolleri](/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-).

**.NET Framework 3.5 ile TLS 1.2 desteği sunmaya yönelik gereksinimler**

Bu tabloda, .NET Framework 3,5 ile TLS 1,2 ' i desteklemeniz gereken işletim sistemi güncelleştirmesi gösterilmektedir. Tüm işletim sistemi güncelleştirmelerini uygulamanızı öneririz.

| **OS** | **.NET Framework 3,5 ile TLS 1,2 ' i desteklemek için gereken en düşük güncelleştirme** |
| --- | --- |
| Windows 10<br>Windows Server 2016 | [Windows 10 sürüm 1511 ve Windows Server 2016 Technical Preview 4 için toplu güncelleştirme: 10 Mayıs 2016](https://support.microsoft.com/help/3156421/cumulative-update-for-windows-10-version-1511-and-windows-server-2016) |
| Windows 8.1<br>Windows Server 2012 R2 | [Windows 8.1 ve Windows Server 2012 R2 'de .NET Framework 3,5 ' de bulunan TLS sistem varsayılan sürümleri için destek](https://support.microsoft.com/help/3154520/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 8,0<br>Windows Server 2012 | [Windows Server 2012 ' de .NET Framework 3,5 ' de bulunan TLS sistemi varsayılan sürümleri için destek](https://support.microsoft.com/help/3154519/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows 7 SP1<br>Windows Server 2008 R2 SP1 | [Windows 7 SP1 ve Server 2008 R2 SP1 'de .NET Framework 3.5.1 'de bulunan TLS sistem varsayılan sürümleri için destek](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Server 2008 | [Windows Vista SP2 ve Server 2008 SP2 'de .NET Framework 2,0 SP2 'de bulunan TLS sistem varsayılan sürümleri için destek](https://support.microsoft.com/help/3154517/support-for-tls-system-default-versions-included-in-the--net-framework) |
| Windows Vista | Desteklenmiyor |

## <a name="azure-cloud-services"></a>Azure Cloud Services

Uygulamanızı barındırmak ve çalıştırmak için [Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) Web ve çalışan rolleri KULLANıYORSANıZ, TLS 1,2 ' i desteklemek için dikkate almanız gereken bazı noktalar vardır.

### <a name="net-framework-47-is-not-installed-on-azure-guest-os-by-default"></a>.NET Framework 4,7, Azure Konuk işletim sisteminde varsayılan olarak yüklü değil

En son Azure Konuk işletim sistemi ailesi 5 sürümünde yüklü en son sürüm (Windows Server 2016) 4.6.2 ' dir. Her bir Azure Konuk IŞLETIM sisteminde hangi .NET Framework sürümlerinin yüklü olduğunu görmek için bkz. [Azure Konuk işletim sistemi sürümleri ve SDK uyumluluk matrisi](https://docs.microsoft.com/azure/cloud-services/cloud-services-guestos-update-matrix).

Uygulamanız Azure Konuk işletim sistemi sürümünde kullanılamayan bir .NET Framework sürümünü hedefliyorsa, kendiniz yüklemeniz gerekir. Bkz. [Azure bulut hizmeti rollerine .net 'ı yükler](https://docs.microsoft.com/azure/cloud-services/cloud-services-dotnet-install-dotnet). Çerçeve yüklemesi için bir yeniden başlatma gerekiyorsa, hizmet rolleri, hazırlık durumuna girmeden önce de yeniden başlatılabilir.

### <a name="azure-guest-os-registry-settings"></a>Azure Konuk işletim sistemi kayıt defteri ayarları

[Azure Cloud Services](https://azure.microsoft.com/services/cloud-services/) Için Azure Konuk Işletim sistemi ailesi 5 görüntüsünün `SchUseStrongCrypto` kayıt defteri anahtarı zaten 1 değerine ayarlanmış. Daha fazla bilgi için bkz. [Schusestrongşifre](#schusestrongcrypto).

[Systemdefaulttlsversions](#systemdefaulttlsversions) kayıt defteri anahtarını 1 olarak ayarlayın. Bkz. [Windows kayıt defteri aracılığıyla güvenliği yapılandırma](#configuring-security-via-the-windows-registry).
