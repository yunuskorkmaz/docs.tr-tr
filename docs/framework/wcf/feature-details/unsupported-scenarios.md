---
title: Desteklenmeyen Senaryolar
ms.date: 03/30/2017
ms.assetid: 72027d0f-146d-40c5-9d72-e94392c8bb40
ms.openlocfilehash: 12012f3e0c0c3b0d10c5faebfb2de881f5de3917
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178782"
---
# <a name="unsupported-scenarios"></a>Desteklenmeyen Senaryolar
Çeşitli nedenlerden dolayı Windows Communication Foundation (WCF) bazı belirli güvenlik senaryoları desteklemez. Örneğin, [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition SSPI veya Kerberos kimlik doğrulama protokolleri uygulamaz ve bu nedenle WCF hizmet Windows kimlik doğrulaması ile bu platform üzerinde çalıştırılmasını desteklemez. Kullanıcı adı/parola ve HTTP/HTTPS tümleşik kimlik doğrulaması gibi diğer kimlik doğrulama mekanizmaları, WCF, Windows XP Home Edition altında çalışırken desteklenir.  
  
## <a name="impersonation-scenarios"></a>Kimliğe bürünme senaryoları  
  
### <a name="impersonated-identity-might-not-flow-when-clients-make-asynchronous-calls"></a>İstemciler, zaman uyumsuz çağrı yaptığınızda başkasının kimliğine bürünülerek gerçekleştirilen kimlik akış değil  
 Bir WCF istemcisi bürünmeyle Windows kimlik doğrulaması kullanarak bir WCF hizmetini zaman uyumsuz çağrılar, kimlik doğrulaması başkasının kimliğine bürünülerek gerçekleştirilen kimlik yerine istemci işlem kimliği ile gerçekleşebilir.  
  
### <a name="windows-xp-and-secure-context-token-cookie-enabled"></a>Windows XP ve etkin güvenli bağlam belirteci tanımlama bilgisi  
 WCF kimliğe bürünme desteklemez ve bir <xref:System.InvalidOperationException> aşağıdaki koşulların oluşturulur:  
  
-   İşletim sistemi [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   Bir Windows kimliği kimlik doğrulama modu sonuçları.  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> Özelliği <xref:System.ServiceModel.OperationBehaviorAttribute> ayarlanır <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
-   Bir durum tabanlı güvenlik bağlamı belirteci (SCT) oluşturulur (oluşturma, varsayılan olarak devre dışıdır).  
  
 Durum tabanlı SCT yalnızca özel bir bağlama kullanarak oluşturulabilir. Daha fazla bilgi için [nasıl yapılır: Bir güvenlik bağlamı oluşturmak için güvenli bir oturum belirteci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).) Bir güvenlik bağlama öğesi oluşturarak, kod içinde belirtecinin etkinleştirilip etkinleştirilmediğini (ya da <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> veya <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>) kullanarak <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%28System.Boolean%29?displayProperty=nameWithType> veya <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%28System.ServiceModel.Channels.SecurityBindingElement%2CSystem.Boolean%29?displayProperty=nameWithType> yöntemi ve ayarı `requireCancellation` parametresi `false`. Parametresi SCT önbelleğe almayı gösterir. Değerini `false` durum tabanlı SCT özelliği sağlar.  
  
 Alternatif olarak, yapılandırmada belirteci oluşturarak etkin bir <`customBinding`>, ardından ekleyerek bir <`security`> öğesi ve ayarı `authenticationMode` özniteliği için SecureConversation ve `requireSecurityContextCancellation` özniteliğini `true`.  
  
> [!NOTE]
>  Yukarıdaki gereksinimlerine özgüdür. Örneğin, <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> yer alan bir Windows kimliği, ancak bir SCT belirlemez bir bağlama öğesi oluşturur. Bu nedenle, kendisiyle kullanabilirsiniz `Required` seçeneğini [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
### <a name="possible-aspnet-conflict"></a>Olası bir ASP.NET çakışma  
 WCF ve [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] her ikisini de etkinleştirmek veya kimliğe bürünme devre dışı bırakabilirsiniz. Zaman [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] barındıran bir WCF uygulaması, WCF arasında bir çakışma mevcut olabilir ve [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] yapılandırma ayarları. Çakışma olması durumunda, WCF ayarı, sürece önceliklidir <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> özelliği <xref:System.ServiceModel.ImpersonationOption.NotAllowed>, bu durumda [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] kimliğe bürünme ayarı öncelik kazanır.  
  
### <a name="assembly-loads-may-fail-under-impersonation"></a>Derleme yüklerini altında kimliğe bürünme başarısız olabilir  
 Başkasının kimliğine bürünülerek gerçekleştirilen bağlamı bir derlemeyi yüklemek için erişim haklarına sahip değil ve ilk kez ise ortak dil çalışma zamanı (CLR), AppDomain için derlemeyi yüklenmeye çalışılıyor <xref:System.AppDomain> hatası önbelleğe alır. Bu derleme (veya derlemeleri) yüklemek için sonraki denemeler başarısız, bile kimliğe bürünme ve bile geri döndürdükten sonra dönüştürülen içerik derlemesini yüklemek için erişim haklarına sahiptir. Kullanıcı bağlamı değiştirildikten sonra CLR yük yeniden denemez olmasıdır. Hatadan kurtarmak için uygulama etki alanını yeniden başlatmanız gerekir.  
  
> [!NOTE]
>  İçin varsayılan değer <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> özelliği <xref:System.ServiceModel.Security.WindowsClientCredential> sınıfı <xref:System.Security.Principal.TokenImpersonationLevel.Identification>. Çoğu durumda, bir kimlik düzeyinde kimliğe bürünülmüş bağlamdaki herhangi bir ek derlemeler yüklemek için herhangi bir hak vardır. Bu farkında olması çok yaygın bir durumdur için varsayılan değer budur. Kimlik düzeyinde kimliğe bürünme özellikleri alınırken işlem olmadığı zaman da oluşur `SeImpersonate` ayrıcalık. Daha fazla bilgi için [temsilcilik ve kimliğe bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
### <a name="delegation-requires-credential-negotiation"></a>Kimlik bilgileri görüşmesi temsilci gerektirir  
 Temsilci ile Kerberos kimlik doğrulama protokolünü kullanmak için Kerberos protokolü ile kimlik bilgileri görüşmesi (bazen çok oluşturan veya çok adımlı Kerberos denir) uygulamalıdır. Kerberos kimlik doğrulaması (Kerberos kesin veya tek oluşturan denir) kimlik bilgileri görüşmesi uygularsanız, bir özel durum oluşturulur. Kimlik bilgileri görüşmesi gerçekleştirme hakkında daha fazla bilgi için bkz. [Windows kimlik doğrulama hatalarını hata ayıklama](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md).  
  
## <a name="cryptography"></a>Şifreleme  
  
### <a name="sha-256-supported-only-for-symmetric-key-usages"></a>SHA-256 yalnızca simetrik anahtar kullanımları için desteklenir  
 WCF çeşitli şifreleme ve sistem tarafından sağlanan bağlamalar algoritma paketini kullanarak belirtebilirsiniz imza Özet oluşturma algoritmaları destekler. Gelişmiş güvenlik için imza Özet karmaları oluşturmak için güvenli karma algoritması (SHA) 2 algoritmalarını, özellikle SHA-256, WCF destekler. Bu sürüm yalnızca Kerberos anahtarları gibi simetrik anahtar kullanımları için SHA-256 destekler ve burada bir X.509 sertifikası iletiyi imzalamak üzere kullanılmaz. WCF RSA imzalar (X.509 sertifikaları kullanılır) desteklemediği için RSA-SHA256 SHA-256 karma destek geçerli olmaması nedeniyle kullanarak [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
### <a name="fips-compliant-sha-256-hashes-not-supported"></a>FIPS uyumlu SHA-256 karma desteklenmiyor  
 SHA-256 kullanan algoritması paketleri WCF tarafından FIPS uyumlu algoritmaları kullanımını gerekli olduğu sistemlerde desteklenmez bu nedenle, WCF SHA-256'yı FIPS uyumlu karmaları desteklemez.  
  
### <a name="fips-compliant-algorithms-may-fail-if-registry-is-edited"></a>Kayıt defteri düzenlediyseniz FIPS uyumlu algoritmaları başarısız olabilir  
 Etkinleştirebilir ve Federal Bilgi işleme standartları (FIPS) - yerel güvenlik ayarları Microsoft Yönetim Konsolu (MMC) ek bileşeni kullanılarak uyumlu algoritmalar - devre dışı bırak. Kayıt defteri ayarı da erişebilirsiniz. Ancak, WCF ayarını sıfırlamak için kayıt defterini kullanarak desteklemiyor unutmayın. Değeri için herhangi bir şey dışında 1 veya 0 olarak ayarlanırsa CLR ve işletim sistemi arasında tutarsız sonuçlar ortaya çıkabilir.  
  
### <a name="fips-compliant-aes-encryption-limitation"></a>FIPS uyumlu AES şifreleme sınırlama  
 FIPS uyumlu AES şifreleme çift yönlü geri çağırmalar düzeyi kimliğe bürünme kimlik altında çalışmaz.  
  
### <a name="cngksp-certificates"></a>CNG/KSP sertifikaları  
 *Şifreleme API'si: Yeni nesil (CNG)* CryptoAPI uzun vadeli yerini alır. Bu API üzerinde yönetilmeyen kodda kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)] ve sonraki Windows sürümlerinde.  
  
 Eski CryptoAPI CNG/KSP sertifikaları işlemek için kullandıkları için .NET framework 4.6.1 ve önceki sürümleri bu sertifikaları desteklemez. .NET Framework 4.6.1 ve önceki sürümleri bu sertifikaların kullanılması, bir özel durum neden olur.  
  
 Bir sertifika KSP kullanıp kullanmadığını bildirmek için olası iki yolu vardır:  
  
-   Yapmak bir `p/invoke` , `CertGetCertificateContextProperty`ve incelemek `dwProvType` döndürülen üzerinde `CertGetCertificateContextProperty`.  
  
-   Kullanım `certutil` sertifikaları'nı sorgulamak için komut satırından komutu. Daha fazla bilgi için [sertifikalarının sorunlarını gidermek için Certutil görevleri](https://go.microsoft.com/fwlink/?LinkId=120056).  
  
## <a name="message-security-fails-if-using-aspnet-impersonation-and-aspnet-compatibility-is-required"></a>ASP.NET kimliğe bürünme ve ASP.NET uyumluluk kullanarak gerekliyse ileti güvenlik başarısız  
 İstemci kimlik doğrulaması, oluşmasını engellediğinden WCF ayarları aşağıdaki birleşimi desteklemez:  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Kimliğe bürünme etkinleştirilir. Bu Web.config dosyasında ayarlayarak yapılır `impersonate` özniteliği <`identity`> öğesine `true`.  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Uyumluluk modu etkin ayarlayarak `aspNetCompatibilityEnabled` özniteliği [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) için `true`.  
  
-   İleti modu güvenliği kullanılır.  
  
 Devre dışı bırakmak için geçici olduğu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uyumluluk modu. Veya [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uyumluluk modu gereklidir, devre dışı bırakma [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] kimliğe bürünme özelliğini ve WCF tarafından sağlanan kimliğe bürünme özelliğini kullanın. Daha fazla bilgi için [temsilcilik ve kimliğe bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="ipv6-literal-address-failure"></a>IPv6 adresi değişmez değer hatası  
 Hizmet ve istemci aynı makinede olan ve değişmez değer IPv6 adresleri hizmeti için kullanılan güvenlik istekleri başarısız.  
  
 Hizmet ve istemci, farklı makinelerde olması durumunda iş değişmez değer IPv6 yöneliktir.  
  
## <a name="wsdl-retrieval-failures-with-federated-trust"></a>Federe güven ile WSDL alma hataları  
 WCF federe güven zincirinde her düğüm için tam olarak bir WSDL belgesi gerektirir. Bir döngü uç noktaları belirtirken ayarlanmadı dikkat edin. Bir yolu, döngüleri oluşabilir aynı WSDL belgesinde iki veya daha fazla bağlantı ile bir federasyon güven zincirleri WSDL indirilmesini kullanıyor. Bu sorunu oluşturabilecek yaygın bir senaryo güvenlik belirteci sunucusu ve hizmeti aynı ServiceHost içinde bulunduğu federe bir hizmettir.  
  
 Bu durum aşağıdaki üç uç nokta adresleri bir hizmet örneğidir:  
  
- `http://localhost/CalculatorService/service` (hizmet)  
  
- `http://localhost/CalculatorService/issue_ticket` (STS)  
  
- `http://localhost/CalculatorService/mex` (meta veri uç noktası)  
  
 Bu, özel durum oluşturur.  
  
 Yerleştirerek bu senaryo yapabileceğiniz `issue_ticket` başka bir uç nokta.  
  
## <a name="wsdl-import-attributes-can-be-lost"></a>WSDL içeri aktarma öznitelik olabilir kaybedildi  
 WCF izleme özniteliklerini üzerinde kaybeder bir `<wst:Claims>` öğesinde bir `RST` bir WSDL içeri aktarma yaparken şablonu. Bir WSDL içeri aktarma sırasında böyle belirtirseniz `<Claims>` doğrudan `WSFederationHttpBinding.Security.Message.TokenRequestParameters` veya `IssuedSecurityTokenRequestParameters.AdditionalRequestParameters` talep türü koleksiyonları doğrudan kullanmak yerine.  Öznitelikleri alma kaybeder bağlama değil WSDL gidiş dönüş düzgün bir şekilde yapar ve bu nedenle istemci tarafında yanlış.  
  
 Düzeltme içeri aktarma yaptıktan sonra istemci üzerinde doğrudan bağlama değiştirmektir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Bilgilerin Açığa Çıkması](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Ayrıcalıkların Yükseltilmesi](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Hizmet Reddi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [İzinsiz Değişiklik](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Yeniden Yürütme Saldırıları](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
