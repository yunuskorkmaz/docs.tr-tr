---
title: Desteklenmeyen Senaryolar
ms.date: 03/30/2017
ms.assetid: 72027d0f-146d-40c5-9d72-e94392c8bb40
ms.openlocfilehash: cc40ccbf83e92404dca07344fae0a6f56f92cefa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955316"
---
# <a name="unsupported-scenarios"></a>Desteklenmeyen Senaryolar
Çeşitli nedenlerle Windows Communication Foundation (WCF) bazı belirli güvenlik senaryolarını desteklemez. Örneğin, [!INCLUDE[wxp](../../../../includes/wxp-md.md)] giriş sürümü SSPI veya Kerberos kimlik doğrulama protokollerini uygulamaz ve bu nedenle WCF, bu platformda Windows kimlik doğrulaması ile bir hizmetin çalıştırılmasını desteklemez. Windows XP Home Edition altında WCF çalıştırılırken Kullanıcı adı/parola ve HTTP/HTTPS tümleşik kimlik doğrulaması gibi diğer kimlik doğrulama mekanizmaları desteklenir.  
  
## <a name="impersonation-scenarios"></a>Kimliğe bürünme senaryoları  
  
### <a name="impersonated-identity-might-not-flow-when-clients-make-asynchronous-calls"></a>Istemciler zaman uyumsuz çağrılar yaparken kimliğe bürünme kimliği Akamayabilir  
 Bir WCF istemcisi, kimliğe bürünme altında Windows kimlik doğrulaması kullanarak bir WCF hizmetine zaman uyumsuz çağrılar yaptığında kimlik doğrulaması, kimliğe bürünülmüş kimlik yerine istemci işleminin kimliğiyle meydana gelebilir.  
  
### <a name="windows-xp-and-secure-context-token-cookie-enabled"></a>Windows XP ve güvenli bağlam belirteci tanımlama bilgisi etkin  
 WCF, kimliğe bürünme özelliğini desteklemez ve <xref:System.InvalidOperationException> aşağıdaki koşullar mevcut olduğunda oluşturulur:  
  
- İşletim sistemi [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
- Kimlik doğrulama modu bir Windows kimliği ile sonuçlanır.  
  
- <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> Öğesinin özelliği olarak ayarlanır<xref:System.ServiceModel.ImpersonationOption.Required>. <xref:System.ServiceModel.OperationBehaviorAttribute>  
  
- Durum tabanlı bir güvenlik bağlamı belirteci (SCT) oluşturulur (varsayılan olarak, oluşturma devre dışıdır).  
  
 Durum tabanlı SCT yalnızca özel bir bağlama kullanılarak oluşturulabilir. Daha fazla bilgi için [nasıl yapılır: Güvenli bir oturum](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)Için güvenlik bağlamı belirteci oluşturun.) Kodda, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> belirteç, <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%28System.ServiceModel.Channels.SecurityBindingElement%2CSystem.Boolean%29?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%28System.Boolean%29?displayProperty=nameWithType> veya yöntemini kullanarak bir güvenlik bağlama öğesi (ya da) oluşturarak ve `requireCancellation` parametresi olarak `false`ayarlanarak etkinleştirilir. Parametresi, SCT 'nin önbelleğe alınmasını ifade eder. Değeri, durum tabanlı `false` SCT özelliğini sağlar.  
  
 Alternatif olarak, yapılandırmada, belirteç`customBinding`bir < > oluşturarak ve sonra bir <`security`> `authenticationMode` öğesi eklenerek ve `true`özniteliği SecureConversation ve `requireSecurityContextCancellation` özniteliği olarak ayarlanarak etkinleştirilir.  
  
> [!NOTE]
> Önceki gereksinimler özeldir. Örneğin, bir Windows <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> kimliği ile sonuçlanan, ancak bir SCT oluşturmayan bir bağlama öğesi oluşturur. Bu nedenle, `Required` seçeneğini üzerinde [!INCLUDE[wxp](../../../../includes/wxp-md.md)]seçeneğiyle kullanabilirsiniz.  
  
### <a name="possible-aspnet-conflict"></a>Olası ASP.NET çakışması  
 WCF ve ASP.NET, kimliğe bürünme özelliğini etkinleştirebilir veya devre dışı bırakabilir. ASP.NET bir WCF uygulaması barındırıyorsa, WCF ve ASP.NET yapılandırma ayarları arasında bir çakışma var olabilir. Çakışma durumunda, bu, ASP.NET Kimliğe bürünme ayarı öncelikli olarak <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> <xref:System.ServiceModel.ImpersonationOption.NotAllowed>ayarlanmadığı takdirde WCF ayarı önceliklidir.  
  
### <a name="assembly-loads-may-fail-under-impersonation"></a>Derleme yüklemeleri, kimliğe bürünme altında başarısız olabilir  
 Kimliğe bürünülmüş bağlamın bir derlemeyi yüklemek için erişim hakları yoksa ve ilk kez ortak dil çalışma zamanı (CLR) bu AppDomain için derlemeyi yüklemeye çalışıyorsa, <xref:System.AppDomain> hatayı önbelleğe alır. Daha sonra bu derlemeyi (veya derlemeleri) yükleme girişimleri, kimliğe bürünme geri alındıktan sonra bile başarısız olur ve geri döndürülmüş bağlam derlemeyi yüklemek için erişim haklarına sahip olsa bile. Bunun nedeni, CLR 'nin Kullanıcı bağlamı değiştirildikten sonra yükü yeniden denemeyecektir. Hatadan kurtarmak için uygulama etki alanını yeniden başlatmanız gerekir.  
  
> [!NOTE]
> <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> Sınıfının özelliği için varsayılan değer. <xref:System.Security.Principal.TokenImpersonationLevel.Identification> <xref:System.ServiceModel.Security.WindowsClientCredential> Çoğu durumda, kimlik düzeyi kimliğe bürünme bağlamının herhangi bir ek derlemeyi yükleme izni yoktur. Bu varsayılan değerdir, bu nedenle farkında olmak üzere çok yaygın bir durumdur. Kimliğe bürünme işlemi `SeImpersonate` ayrıcalığına sahip olmadığında, kimlik düzeyi kimliğe bürünme da oluşur. Daha fazla bilgi için bkz. [temsil ve kimliğe bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
### <a name="delegation-requires-credential-negotiation"></a>Temsili kimlik bilgisi anlaşması gerektirir  
 Kerberos kimlik doğrulama protokolünü temsilcisiyle birlikte kullanmak için, Kerberos protokolünü kimlik bilgisi anlaşmasına (bazen çok aşamalı veya çok adımlı Kerberos olarak adlandırılır) uygulamanız gerekir. Kimlik bilgisi anlaşması olmadan Kerberos kimlik doğrulaması uygularsanız (bazen tek veya tek seferlik Kerberos olarak adlandırılır), bir özel durum oluşturulur. Kimlik bilgisi anlaşmasını uygulama hakkında daha fazla bilgi için bkz. [Windows kimlik doğrulama hatalarını ayıklama](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md).  
  
## <a name="cryptography"></a>To  
  
### <a name="sha-256-supported-only-for-symmetric-key-usages"></a>SHA-256 yalnızca simetrik anahtar kullanımları için desteklenir  
 WCF, sistem tarafından belirtilen bağlamalarda algoritma paketini kullanarak belirtebileceğiniz çeşitli şifreleme ve imza özeti oluşturma algoritmalarını destekler. WCF, daha iyi güvenlik için imza Özet karmaları oluşturmak amacıyla güvenli karma algoritması (SHA) 2 algoritmalarını, özellikle SHA-256 ' i destekler. Bu sürüm, yalnızca Kerberos anahtarları gibi simetrik anahtar kullanımları için SHA-256 ' ı destekler ve iletiyi imzalamak için bir X. 509.440 sertifikası kullanılmaz. WCF, WinFX 'de RSA-SHA256 için desteklenmeyen destek olmaması nedeniyle, SHA-256 karması kullanılarak RSA imzalarını (X. 509.440 sertifikalarında kullanılır) desteklemez.  
  
### <a name="fips-compliant-sha-256-hashes-not-supported"></a>FIPS uyumlu SHA-256 karmaları desteklenmez  
 WCF, SHA-256 FIPS uyumlu karmaları desteklemez, bu nedenle SHA-256 kullanan algoritma paketleri, FIPS uyumlu algoritmaların kullanılması gereken sistemlerde WCF tarafından desteklenmez.  
  
### <a name="fips-compliant-algorithms-may-fail-if-registry-is-edited"></a>Kayıt defteri düzenlendiğinde FIPS uyumlu algoritmalar başarısız olabilir  
 Yerel güvenlik ayarları Microsoft Yönetim Konsolu (MMC) ek bileşenini kullanarak Federal bilgi Işleme standartları (FIPS) ile uyumlu algoritmaları etkinleştirebilir ve devre dışı bırakabilirsiniz. Ayrıca, kayıt defterindeki ayarına erişebilirsiniz. Ancak, WCF 'nin ayarı sıfırlamak için kayıt defterini kullanmayı desteklemediğini unutmayın. Değer 1 veya 0 ' dan farklı bir değere ayarlandıysa, CLR ve işletim sistemi arasında tutarsız sonuçlar meydana gelebilir.  
  
### <a name="fips-compliant-aes-encryption-limitation"></a>FIPS uyumlu AES şifreleme sınırlaması  
 FIPS uyumlu AES şifrelemesi, kimlik düzeyi kimliğe bürünme altında çift yönlü geri çağırmalar içinde çalışmaz.  
  
### <a name="cngksp-certificates"></a>CNG/KSP sertifikaları  
 *Şifreleme API 'SI: Yeni nesil (CNG)* , CryptoAPI için uzun süreli değiştirmedir. Bu API [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)] ve sonraki Windows sürümlerinde yönetilmeyen kodda kullanılabilir.  
  
 .NET Framework 4.6.1 ve önceki sürümler, CNG/KSP sertifikalarını işlemek için eski CryptoAPI 'yi kullandıkları için bu sertifikaları desteklemez. Bu sertifikaların .NET Framework 4.6.1 ve önceki sürümleriyle kullanımı bir özel duruma neden olur.  
  
 Bir sertifikanın KSP kullanıp kullanmadığını söylemek için iki olası yol vardır:  
  
- ' İ `dwProvType` yapın ve döndürülen 'ıinceleyin.`CertGetCertificateContextProperty` `p/invoke` `CertGetCertificateContextProperty`  
  
- Sertifikaları sorgulamak için komut satırından komutunukullanın.`certutil` Daha fazla bilgi için bkz. [sertifika sorunlarını giderme Için Certutil görevleri](https://go.microsoft.com/fwlink/?LinkId=120056).  
  
## <a name="message-security-fails-if-using-aspnet-impersonation-and-aspnet-compatibility-is-required"></a>ASP.NET Kimliğe bürünme ve ASP.NET uyumluluğu kullanılması gerekiyorsa ileti güvenliği başarısız olur  
 WCF, istemci kimlik doğrulamasının oluşmasını engelleyebileceğinden aşağıdaki ayar birleşimini desteklemez:  
  
- ASP.NET Kimliğe bürünme etkindir. Bu, < `impersonate` `identity`> öğesinin özniteliği olarak `true`ayarlanarak Web. config dosyasında yapılır.  
  
- ASP.NET uyumluluk modu, `aspNetCompatibilityEnabled` [ \<ServiceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) özniteliği olarak `true`ayarlanarak etkinleştirilir.  
  
- İleti modu güvenliği kullanılır.  
  
 Geçici çözüm, ASP.NET uyumluluk modunu Kapatbir şekilde çalışır. Ya da ASP.NET uyumluluk modu gerekliyse, ASP.NET Kimliğe bürünme özelliğini devre dışı bırakın ve bunun yerine WCF tarafından belirtilen kimliğe bürünme özelliğini kullanın. Daha fazla bilgi için bkz. [temsil ve kimliğe bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="ipv6-literal-address-failure"></a>IPv6 değişmez değer adresi hatası  
 İstemci ve hizmet aynı makineden olduğunda güvenlik istekleri başarısız olur ve hizmet için IPv6 değişmez adresler kullanılır.  
  
 Hizmet ve istemci farklı makinelerinizde, sabit IPv6 adresleri çalışır.  
  
## <a name="wsdl-retrieval-failures-with-federated-trust"></a>Federasyon güveniyle WSDL alma sorunları  
 WCF, Federasyon güven zincirindeki her düğüm için tam olarak bir WSDL belgesi gerektirir. Uç noktaları belirtirken bir döngü ayarlanmamaya dikkat edin. Döngülerin ortaya çıkarılabileceği bir yol, aynı WSDL belgesinde iki veya daha fazla bağlantıyla federasyon güven zincirlerinin WSDL indirmesi kullanmaktır. Bu sorunu oluşturabilecek yaygın bir senaryo, güvenlik belirteci sunucusunun ve hizmetin aynı ServiceHost içinde bulunduğu bir Federasyon hizmetidir.  
  
 Bu durumun bir örneği, aşağıdaki üç uç nokta adresini içeren bir hizmettir:  
  
- `http://localhost/CalculatorService/service`(hizmet)  
  
- `http://localhost/CalculatorService/issue_ticket`(STS)  
  
- `http://localhost/CalculatorService/mex`(meta veri uç noktası)  
  
 Bu bir özel durum oluşturur.  
  
 `issue_ticket` Uç noktayı başka bir yere yerleştirerek bu senaryonun çalışmasını sağlayabilirsiniz.  
  
## <a name="wsdl-import-attributes-can-be-lost"></a>WSDL Içeri aktarma öznitelikleri kaybolabilir  
 Bir wsdl içeri aktarma işlemi yaparken WCF, `<wst:Claims>` bir `RST` şablondaki öğe üzerindeki öznitelikleri izlemeyi kaybeder. Bu durum doğrudan talep türü koleksiyonları kullanmak yerine veya `<Claims>` `IssuedSecurityTokenRequestParameters.AdditionalRequestParameters` ' de `WSFederationHttpBinding.Security.Message.TokenRequestParameters` belirttiğinizde bir wsdl içeri aktarma işlemi sırasında gerçekleşir.  İçeri aktarma öznitelikleri kaybederse, bağlama WSDL aracılığıyla doğru şekilde geri dönmez ve bu nedenle istemci tarafında yanlış.  
  
 Bu, içeri aktarma işlemi yapıldıktan sonra bağlamayı doğrudan istemci üzerinde değiştirmektir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Bilgilerin Açığa Çıkması](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Ayrıcalıkların Yükseltilmesi](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Hizmet Reddi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [İzinsiz Değişiklik](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Yeniden Yürütme Saldırıları](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
