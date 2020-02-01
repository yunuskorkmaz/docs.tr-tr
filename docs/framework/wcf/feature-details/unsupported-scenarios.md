---
title: Desteklenmeyen Senaryolar
ms.date: 03/30/2017
ms.assetid: 72027d0f-146d-40c5-9d72-e94392c8bb40
ms.openlocfilehash: b643e6df8a877860ce36fc6ee34c4e4ca08ec748
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921166"
---
# <a name="unsupported-scenarios"></a>Desteklenmeyen senaryolar

Çeşitli nedenlerle Windows Communication Foundation (WCF) bazı belirli güvenlik senaryolarını desteklemez. Örneğin, Windows XP Home Edition SSPI veya Kerberos kimlik doğrulama protokollerini uygulamaz ve bu nedenle WCF, bu platformda Windows kimlik doğrulamasına sahip bir hizmetin çalıştırılmasını desteklemez. Windows XP Home Edition altında WCF çalıştırılırken Kullanıcı adı/parola ve HTTP/HTTPS tümleşik kimlik doğrulaması gibi diğer kimlik doğrulama mekanizmaları desteklenir.

## <a name="impersonation-scenarios"></a>Kimliğe bürünme senaryoları

### <a name="impersonated-identity-might-not-flow-when-clients-make-asynchronous-calls"></a>İstemciler zaman uyumsuz çağrılar yaparken kimliğe bürünme kimliği akamayabilir
 Bir WCF istemcisi, kimliğe bürünme altında Windows kimlik doğrulaması kullanarak bir WCF hizmetine zaman uyumsuz çağrılar yaptığında kimlik doğrulaması, kimliğe bürünülmüş kimlik yerine istemci işleminin kimliğiyle meydana gelebilir.

### <a name="windows-xp-and-secure-context-token-cookie-enabled"></a>Windows XP ve güvenli bağlam belirteci tanımlama bilgisi etkin

WCF, kimliğe bürünme özelliğini desteklemez ve aşağıdaki koşullar mevcut olduğunda bir <xref:System.InvalidOperationException> oluşur:

- İşletim sistemi Windows XP 'dir.

- Kimlik doğrulama modu bir Windows kimliği ile sonuçlanır.

- <xref:System.ServiceModel.OperationBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> özelliği <xref:System.ServiceModel.ImpersonationOption.Required>olarak ayarlanmıştır.

- Durum tabanlı bir güvenlik bağlamı belirteci (SCT) oluşturulur (varsayılan olarak, oluşturma devre dışıdır).

 Durum tabanlı SCT yalnızca özel bir bağlama kullanılarak oluşturulabilir. Daha fazla bilgi için bkz. [nasıl yapılır: güvenli bir oturum Için güvenlik bağlamı belirteci oluşturma](how-to-create-a-security-context-token-for-a-secure-session.md).) Kod içinde, belirteç, <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%28System.Boolean%29?displayProperty=nameWithType> veya <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%28System.ServiceModel.Channels.SecurityBindingElement%2CSystem.Boolean%29?displayProperty=nameWithType> yöntemini kullanarak bir güvenlik bağlama öğesi (<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ya da <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>) oluşturularak etkinleştirilir ve `requireCancellation` parametresini `false`olarak ayarlar. Parametresi, SCT 'nin önbelleğe alınmasını ifade eder. Değerin `false` olarak ayarlanması durum tabanlı SCT özelliğini sağlar.

 Alternatif olarak, yapılandırma ' da, belirteç bir <`customBinding`oluşturarak >, sonra bir <`security`> öğesi eklenerek ve `authenticationMode` özniteliği SecureConversation ve `requireSecurityContextCancellation` özniteliği `true`olarak ayarlanarak etkinleştirilir.

> [!NOTE]
> Önceki gereksinimler özeldir. Örneğin <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A>, Windows kimliği ile sonuçlanan ancak bir SCT oluşturmayan bir bağlama öğesi oluşturur. Bu nedenle, Windows XP 'de `Required` seçeneğiyle kullanabilirsiniz.

### <a name="possible-aspnet-conflict"></a>Olası ASP.NET çakışması

WCF ve ASP.NET, kimliğe bürünme özelliğini etkinleştirebilir veya devre dışı bırakabilir. ASP.NET bir WCF uygulaması barındırıyorsa, WCF ve ASP.NET yapılandırma ayarları arasında bir çakışma var olabilir. Çakışma durumunda, <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> özelliği <xref:System.ServiceModel.ImpersonationOption.NotAllowed>olarak ayarlanmadıkça WCF ayarı önceliklidir, bu durumda ASP.NET Kimliğe bürünme ayarı öncelikli olur.

### <a name="assembly-loads-may-fail-under-impersonation"></a>Derleme yüklemeleri, kimliğe bürünme altında başarısız olabilir

Kimliğe bürünülmüş bağlamın bir derlemeyi yüklemek için erişim hakları yoksa ve ilk kez ortak dil çalışma zamanı (CLR) bu AppDomain için derlemeyi yüklemeye çalışıyorsa, <xref:System.AppDomain> hatayı önbelleğe alır. Daha sonra bu derlemeyi (veya derlemeleri) yükleme girişimleri, kimliğe bürünme geri alındıktan sonra bile başarısız olur ve geri döndürülmüş bağlam derlemeyi yüklemek için erişim haklarına sahip olsa bile. Bunun nedeni, CLR 'nin Kullanıcı bağlamı değiştirildikten sonra yükü yeniden oluşturmaz. Hatadan kurtarmak için uygulama etki alanını yeniden başlatmanız gerekir.

> [!NOTE]
> <xref:System.ServiceModel.Security.WindowsClientCredential> sınıfının <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> özelliği için varsayılan değer <xref:System.Security.Principal.TokenImpersonationLevel.Identification>. Çoğu durumda, kimlik düzeyi kimliğe bürünme bağlamının herhangi bir ek derlemeyi yükleme izni yoktur. Bu varsayılan değerdir, bu nedenle farkında olmak üzere çok yaygın bir durumdur. Kimliğe bürünme işlemi `SeImpersonate` ayrıcalığına sahip olmadığında, kimlik düzeyi kimliğe bürünme da oluşur. Daha fazla bilgi için bkz. [temsil ve kimliğe bürünme](delegation-and-impersonation-with-wcf.md).

### <a name="delegation-requires-credential-negotiation"></a>Temsili kimlik bilgisi anlaşması gerektirir

Kerberos kimlik doğrulama protokolünü temsilcisiyle birlikte kullanmak için, Kerberos protokolünü kimlik bilgisi anlaşmasına (bazen çok aşamalı veya çok adımlı Kerberos olarak adlandırılır) uygulamanız gerekir. Kimlik bilgisi anlaşması olmadan Kerberos kimlik doğrulaması uygularsanız (bazen tek veya tek seferlik Kerberos olarak adlandırılır), bir özel durum oluşturulur. Kimlik bilgisi anlaşmasını uygulama hakkında daha fazla bilgi için bkz. [Windows kimlik doğrulama hatalarını ayıklama](debugging-windows-authentication-errors.md).

## <a name="cryptography"></a>Şifreleme

### <a name="sha-256-supported-only-for-symmetric-key-usages"></a>SHA-256 yalnızca simetrik anahtar kullanımları için desteklenir

WCF, sistem tarafından belirtilen bağlamalarda algoritma paketini kullanarak belirtebileceğiniz çeşitli şifreleme ve imza özeti oluşturma algoritmalarını destekler. WCF, daha iyi güvenlik için imza Özet karmaları oluşturmak amacıyla güvenli karma algoritması (SHA) 2 algoritmalarını, özellikle SHA-256 ' i destekler. Bu sürüm, yalnızca Kerberos anahtarları gibi simetrik anahtar kullanımları için SHA-256 ' ı destekler ve iletiyi imzalamak için bir X. 509.440 sertifikası kullanılmaz. WCF, WinFX 'de RSA-SHA256 için desteklenmeyen destek olmaması nedeniyle, SHA-256 karması kullanılarak RSA imzalarını (X. 509.440 sertifikalarında kullanılır) desteklemez.

### <a name="fips-compliant-sha-256-hashes-not-supported"></a>FIPS uyumlu SHA-256 karmaları desteklenmez

WCF, SHA-256 FIPS uyumlu karmaları desteklemez, bu nedenle SHA-256 kullanan algoritma paketleri, FIPS uyumlu algoritmaların kullanılması gereken sistemlerde WCF tarafından desteklenmez.

### <a name="fips-compliant-algorithms-may-fail-if-registry-is-edited"></a>Kayıt defteri düzenlendiğinde FIPS uyumlu algoritmalar başarısız olabilir

Yerel güvenlik ayarları Microsoft Yönetim Konsolu (MMC) ek bileşenini kullanarak Federal bilgi Işleme standartları (FIPS) ile uyumlu algoritmaları etkinleştirebilir ve devre dışı bırakabilirsiniz. Ayrıca, kayıt defterindeki ayarına erişebilirsiniz. Ancak, WCF 'nin ayarı sıfırlamak için kayıt defterini kullanmayı desteklemediğini unutmayın. Değer 1 veya 0 ' dan farklı bir değere ayarlandıysa, CLR ve işletim sistemi arasında tutarsız sonuçlar meydana gelebilir.

### <a name="fips-compliant-aes-encryption-limitation"></a>FIPS uyumlu AES şifreleme sınırlaması

FIPS uyumlu AES şifrelemesi, kimlik düzeyi kimliğe bürünme altında çift yönlü geri çağırmalar içinde çalışmaz.

### <a name="cngksp-certificates"></a>CNG/KSP sertifikaları

*Şifreleme API 'si: yeni nesil (CNG)* , CryptoAPI 'nin uzun süreli yerini alır. Bu API, Windows Vista, Windows Server 2008 ve sonraki Windows sürümlerinde yönetilmeyen kodda kullanılabilir.

 .NET Framework 4.6.1 ve önceki sürümler, CNG/KSP sertifikalarını işlemek için eski CryptoAPI 'yi kullandıkları için bu sertifikaları desteklemez. Bu sertifikaların .NET Framework 4.6.1 ve önceki sürümleriyle kullanımı bir özel duruma neden olur.

 Bir sertifikanın KSP kullanıp kullanmadığını söylemek için iki olası yol vardır:

- `CertGetCertificateContextProperty``p/invoke` yapın ve döndürülen `CertGetCertificateContextProperty``dwProvType` inceleyin.

- Sertifikaları sorgulamak için komut satırından `certutil` komutunu kullanın. Daha fazla bilgi için bkz. [sertifika sorunlarını giderme Için Certutil görevleri](https://docs.microsoft.com/previous-versions/orphan-topics/ws.10/cc772619(v=ws.10)).

## <a name="message-security-fails-if-using-aspnet-impersonation-and-aspnet-compatibility-is-required"></a>ASP.NET Kimliğe bürünme ve ASP.NET uyumluluğu kullanılması gerekiyorsa ileti güvenliği başarısız olur

WCF, istemci kimlik doğrulamasının oluşmasını engelleyebileceğinden aşağıdaki ayar birleşimini desteklemez:

- ASP.NET Kimliğe bürünme etkindir. Bu, <`identity`> öğesinin `impersonate` özniteliği `true`olarak ayarlanarak Web. config dosyasında yapılır.

- ASP.NET uyumluluk modu, [\<serviceHostingEnvironment >](../../configure-apps/file-schema/wcf/servicehostingenvironment.md) `aspNetCompatibilityEnabled` özniteliği `true`olarak ayarlanarak etkinleştirilir.

- İleti modu güvenliği kullanılır.

Geçici çözüm, ASP.NET uyumluluk modunu Kapatbir şekilde çalışır. Ya da ASP.NET uyumluluk modu gerekliyse, ASP.NET Kimliğe bürünme özelliğini devre dışı bırakın ve bunun yerine WCF tarafından belirtilen kimliğe bürünme özelliğini kullanın. Daha fazla bilgi için bkz. [temsil ve kimliğe bürünme](delegation-and-impersonation-with-wcf.md).

## <a name="ipv6-literal-address-failure"></a>IPv6 değişmez değer adresi hatası

İstemci ve hizmet aynı makineden olduğunda güvenlik istekleri başarısız olur ve hizmet için IPv6 değişmez adresler kullanılır.

 Hizmet ve istemci farklı makinelerinizde, sabit IPv6 adresleri çalışır.

## <a name="wsdl-retrieval-failures-with-federated-trust"></a>Federasyon güveniyle WSDL alma sorunları

WCF, Federasyon güven zincirindeki her düğüm için tam olarak bir WSDL belgesi gerektirir. Uç noktaları belirtirken bir döngü ayarlanmamaya dikkat edin. Döngülerin ortaya çıkarılabileceği bir yol, aynı WSDL belgesinde iki veya daha fazla bağlantıyla federasyon güven zincirlerinin WSDL indirmesi kullanmaktır. Bu sorunu oluşturabilecek yaygın bir senaryo, güvenlik belirteci sunucusunun ve hizmetin aynı ServiceHost içinde bulunduğu bir Federasyon hizmetidir.

 Bu durumun bir örneği, aşağıdaki üç uç nokta adresini içeren bir hizmettir:

- `http://localhost/CalculatorService/service` (hizmet)

- `http://localhost/CalculatorService/issue_ticket` (STS)

- `http://localhost/CalculatorService/mex` (meta veri uç noktası)

 Bu bir özel durum oluşturur.

 `issue_ticket` uç noktasını başka bir yere yerleştirerek bu senaryonun çalışmasını sağlayabilirsiniz.

## <a name="wsdl-import-attributes-can-be-lost"></a>WSDL içeri aktarma öznitelikleri kaybolabilir

Bir WSDL içeri aktarma işlemi sırasında WCF, bir `RST` şablonundaki `<wst:Claims>` öğesindeki özniteliklerin izlenmesini kaybeder. Bu, doğrudan talep türü koleksiyonları kullanmak yerine doğrudan `WSFederationHttpBinding.Security.Message.TokenRequestParameters` veya `IssuedSecurityTokenRequestParameters.AdditionalRequestParameters` `<Claims>` belirtirseniz, WSDL içeri aktarma sırasında gerçekleşir.  İçeri aktarma öznitelikleri kaybederse, bağlama WSDL aracılığıyla doğru şekilde geri dönmez ve bu nedenle istemci tarafında yanlış.

 Bu, içeri aktarma işlemi yapıldıktan sonra bağlamayı doğrudan istemci üzerinde değiştirmektir.

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik Konuları](security-considerations-in-wcf.md)
- [Bilgilerin Açığa Çıkması](information-disclosure.md)
- [Ayrıcalıkların Yükseltilmesi](elevation-of-privilege.md)
- [Hizmet Reddi](denial-of-service.md)
- [İzinsiz Değişiklik](tampering.md)
- [Yeniden Yürütme Saldırıları](replay-attacks.md)
