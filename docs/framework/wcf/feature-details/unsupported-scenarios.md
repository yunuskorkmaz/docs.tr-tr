---
title: Desteklenmeyen Senaryolar
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 72027d0f-146d-40c5-9d72-e94392c8bb40
caps.latest.revision: 43
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7738eba66619e8a312ed2f9bd43142dbb097b259
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="unsupported-scenarios"></a>Desteklenmeyen Senaryolar
Çeşitli nedenlerle [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bazı belirli güvenlik senaryoları desteklemez. Örneğin, [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition SSPI veya Kerberos kimlik doğrulama protokolleri uygulamaz ve bu nedenle [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bu platformda Windows kimlik doğrulaması ile bir hizmeti çalıştıran desteklemiyor. Kullanıcı adı/parola ve HTTP/HTTPS ile tümleşik kimlik doğrulaması gibi diğer kimlik doğrulama mekanizmaları çalıştırırken desteklenen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Windows XP Home Edition altında.  
  
## <a name="impersonation-scenarios"></a>Kimliğe bürünme senaryoları  
  
### <a name="impersonated-identity-might-not-flow-when-clients-make-asynchronous-calls"></a>İstemcilerin zaman uyumsuz çağrılar yaptığınızda Kimliğine bürünülen kimlik akış değil  
 Bir WCF istemcisi kimliğe bürünme altında Windows kimlik doğrulaması kullanan bir WCF hizmetini zaman uyumsuz çağrılar, kimlik doğrulama Kimliğine bürünülen kimlik yerine istemci işlemin kimliğini ortaya çıkabilir.  
  
### <a name="windows-xp-and-secure-context-token-cookie-enabled"></a>Windows XP ve etkin güvenli bağlam belirteci tanımlama bilgisi  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Kimliğe bürünme desteklemez ve bir <xref:System.InvalidOperationException> aşağıdaki koşulların zaman oluşturulur:  
  
-   İşletim sistemi [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   Kimlik doğrulama modu, bir Windows kimlik sonuçlanır.  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> Özelliği <xref:System.ServiceModel.OperationBehaviorAttribute> ayarlanır <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
-   Bir durum tabanlı güvenlik bağlamı belirteci (SCT) oluşturulur (varsayılan olarak, oluşturma devre dışıdır).  
  
 Durum tabanlı SCT yalnızca özel bağlama kullanılarak oluşturulabilir. Daha fazla bilgi için bkz: [nasıl yapılır: güvenli oturum açmak için bir güvenlik bağlamı belirteci oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).) Bir güvenlik bağlama öğesi oluşturarak, kodda belirtecinin etkinleştirilip etkinleştirilmediğini (ya da <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> veya <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>) kullanarak <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%28System.Boolean%29?displayProperty=nameWithType> veya <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%28System.ServiceModel.Channels.SecurityBindingElement%2CSystem.Boolean%29?displayProperty=nameWithType> yöntemi ve ayarı `requireCancellation` parametresi `false`. Parametresi SCT önbelleğe almayı gösterir. Ayar değeri `false` durum tabanlı SCT özelliği sağlar.  
  
 Alternatif olarak, yapılandırmada, belirteç oluşturarak etkin bir <`customBinding`>, ardından ekleyerek bir <`security`> öğesi ve ayarı `authenticationMode` özniteliği için SecureConversation ve `requireSecurityContextCancellation` özniteliğini `true`.  
  
> [!NOTE]
>  Yukarıdaki gereksinimleri özgüdür. Örneğin, <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> sonuçları bir Windows kimliği, ancak bir SCT oluşturmaz bir bağlama öğesi oluşturur. Bu nedenle, kendisiyle kullanabilirsiniz `Required` seçeneği [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
### <a name="possible-aspnet-conflict"></a>Olası bir ASP.NET çakışma  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] her ikisi de etkinleştirebilir veya kimliğe bürünme devre dışı bırakın. Zaman [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] konakları bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama, bir çakışma arasında bulunabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] yapılandırma ayarları. Çakışma, durumunda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ayarı önceliklidir, sürece <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> özelliği ayarlanmış <xref:System.ServiceModel.ImpersonationOption.NotAllowed>, bu durumda [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] kimliğe bürünme ayarı öncelik alır.  
  
### <a name="assembly-loads-may-fail-under-impersonation"></a>Derleme yüklerini altında kimliğe bürünme başarısız olabilir  
 Kimliğine bürünülen bağlamı bir derlemeyi yüklemeye erişim haklarına sahip değil ve ilk kez kullanıyorsanız ortak dil çalışma zamanı (CLR) o AppDomain için derleme yüklenmeye çalışılıyor <xref:System.AppDomain> hata önbelleğe alır. Bu derleme (veya derlemeler) yüklemek için sonraki denemeleri başarısız, kimliğe bürünme ve olsa bile döndürme sonra bile döndürülen bağlam derlemeyi yüklemek için erişim haklarına sahip. Kullanıcı bağlamı değiştirildikten sonra CLR yük yeniden denemez olmasıdır. Hatadan kurtarmak için uygulama etki alanı yeniden başlatmanız gerekir.  
  
> [!NOTE]
>  İçin varsayılan değer <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> özelliği <xref:System.ServiceModel.Security.WindowsClientCredential> sınıfı <xref:System.Security.Principal.TokenImpersonationLevel.Identification>. Çoğu durumda, bir kimlik düzeyi kimliğe bürünme bağlamı herhangi bir ek derlemeler yükleme izni yok. Bu dikkat edilmesi gereken çok yaygın bir durumdur için varsayılan değer budur. Kimliğe bürünme kimlik düzeyi de oluşur özellikleri alınırken işlem olmadığı zaman `SeImpersonate` ayrıcalık. Daha fazla bilgi için bkz: [temsilcilik ve kimliğe bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
### <a name="delegation-requires-credential-negotiation"></a>Kimlik bilgileri görüşmesi temsilci gerektirir  
 Temsilci ile Kerberos kimlik doğrulama protokolünü kullanmak için Kerberos protokolünü (çok leg ya da çok adımlı Kerberos de denir) kimlik bilgileri görüşmesi ile uygulamalıdır. Kerberos kimlik doğrulaması (bazen tek adımda ya da tek leg Kerberos denir) kimlik bilgileri görüşmesi uygularsanız, özel durum oluşur. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] kimlik bilgileri görüşmesi uygulamak için bkz: nasıl [hata ayıklama Windows kimlik doğrulama hataları](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md).  
  
## <a name="cryptography"></a>Belirttiğiniz Bu, bir WSDL içe aktarma sırasında  doğrudan  veya  talep türü koleksiyonları doğrudan kullanmak yerine.  
  
### <a name="sha-256-supported-only-for-symmetric-key-usages"></a>Öznitelikleri alma kaybederse olduğundan, bağlama değil WSDL gidiş dönüş düzgün bir şekilde yapar ve bu nedenle istemci tarafında doğru değil.  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Düzeltme alma yaptıktan sonra bağlama doğrudan istemcide değiştirmektir. Gelişmiş güvenlik için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] imza Özet karmaları oluşturmak için güvenli karma algoritması (SHA) 2 algoritmalarını, özellikle SHA-256 destekler. Bu sürüm yalnızca Kerberos anahtarları gibi simetrik anahtar kullanımlar için SHA-256 destekler ve burada bir X.509 sertifikası değil iletiyi imzalamak için kullanılır. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] RSA imzalar (X.509 sertifikaları kullanılır) desteklemiyor RSA-SHA256 için SHA-256 karma desteği geçerli olmaması nedeniyle kullanarak [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
### <a name="fips-compliant-sha-256-hashes-not-supported"></a>FIPS uyumlu SHA-256 karma desteklenmiyor  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] SHA-256 kullanmasını algoritması paketleri tarafından desteklenmeyen şekilde desteklemediğinden SHA-256 FIPS uyumlu karmaları mu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sistemlerde FIPS uyumlu algoritmaları kullanımını burada gereklidir.  
  
### <a name="fips-compliant-algorithms-may-fail-if-registry-is-edited"></a>Kayıt defteri düzenlenirse FIPS uyumlu algoritmaları başarısız olabilir  
 Etkinleştirin ve Federal Bilgi işleme standartları (FIPS) - yerel güvenlik ayarları Microsoft Yönetim Konsolu (MMC) ek kullanarak uyumlu algoritmaları - devre dışı bırak. Kayıt defterindeki ayar da erişebilirsiniz. Ancak, unutmayın, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kayıt defteri ayarını sıfırlamak için kullanılmasını desteklemez. Değer için herhangi bir şey 1 veya 0 dışında ayarlanırsa, CLR ve işletim sistemi arasında tutarsız sonuçlar oluşabilir.  
  
### <a name="fips-compliant-aes-encryption-limitation"></a>FIPS uyumlu AES şifreleme sınırlama  
 FIPS uyumlu AES şifreleme düzeyi kimliğe bürünme kimlik altında çift yönlü geri aramalar çalışmaz.  
  
### <a name="cngksp-certificates"></a>CNG/KSP sertifikaları  
 *Şifreleme API'si: Yeni nesil (CNG)* CryptoAPI uzun vadeli yerini alır. Bu API üzerinde yönetilmeyen kodunda kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)] ve sonraki Windows sürümlerinde.  
  
 Eski CryptoAPI CNG/KSP sertifikaları işlemek için kullandıkları için .NET framework 4.6.1 ve önceki sürümleri bu sertifikaları desteklemez. .NET Framework 4.6.1 ve önceki sürümleriyle bu sertifikaların kullanılması, bir özel durum neden olur.  
  
 Bir sertifika KSP kullanıp kullanmadığını bildirmek için iki olası yolu vardır:  
  
-   Yapmak bir `p/invoke` , `CertGetCertificateContextProperty`ve incelemek `dwProvType` döndürülen üzerinde `CertGetCertificateContextProperty`.  
  
-   Kullanım `certutil` sertifikaları sorgulamak için komut satırından komutu. Daha fazla bilgi için bkz: [sertifikaları sorunlarını gidermeye yönelik Certutil görevleri](http://go.microsoft.com/fwlink/?LinkId=120056).  
  
## <a name="message-security-fails-if-using-aspnet-impersonation-and-aspnet-compatibility-is-required"></a>ASP.NET kimliğe bürünme ve ASP.NET uyumluluğu kullanarak gerekliyse ileti güvenlik başarısız  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci kimlik doğrulaması oluşmasını engellediğinden ayarları aşağıdaki bileşimi desteklemez:  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Kimliğe bürünme etkinleştirilir. Bu Web.config dosyasında ayarlayarak yapılır `impersonate` özniteliği <`identity`> öğesine `true`.  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Uyumluluk modu etkin ayarlayarak `aspNetCompatibilityEnabled` özniteliği [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) için `true`.  
  
-   İleti mod güvenliği kullanılır.  
  
 Devre dışı bırakmak için geçici çözüm olan [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uyumluluk modunda. Veya, eğer [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] uyumluluk modu gereklidir, devre dışı bırakma [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] kimliğe bürünme özelliğini ve kullanım [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-kimliğe bürünme yerine sağlanan. Daha fazla bilgi için bkz: [temsilcilik ve kimliğe bürünme](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="ipv6-literal-address-failure"></a>IPv6 değişmez değer adresi hatası  
 Güvenlik istekleri istemci ve hizmet aynı makinede IPv6 değişmez adreslerini hizmeti için kullanılan olduğunda ve başarısız.  
  
 İstemci ve hizmet farklı makinelerde olması durumunda iş değişmez değer IPv6 adresleri.  
  
## <a name="wsdl-retrieval-failures-with-federated-trust"></a>Federe güven ile WSDL alma hataları  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] federe güven zincirinde her düğüm için tam olarak bir WSDL belge gerektirir. Döngü uç noktaları belirtirken ayarlanmadı dikkat edin. Döngüler ortaya çıkabilecek bir yolu, aynı WSDL belgesinde iki veya daha fazla bağlantılarla federe güven zincirleri WSDL yüklenmesini kullanıyor. Bu sorunu üretebilir yaygın bir senaryo güvenlik belirteci sunucusu ve hizmeti aynı ServiceHost içinde bulunduğu federe bir hizmettir.  
  
 Bu durum aşağıdaki üç uç nokta adresleri hizmetiyle örneğidir:  
  
-   http://localhost/CalculatorService/service (hizmeti)  
  
-   http://localhost/CalculatorService/issue_ticket (STS)  
  
-   http://localhost/CalculatorService/mex (meta veri uç noktası)  
  
 Bir özel durum oluşturur.  
  
 Koyarak iş bu senaryo yapabileceğiniz `issue_ticket` başka bir uç nokta.  
  
## <a name="wsdl-import-attributes-can-be-lost"></a>WSDL içe aktarma öznitelikleri olabilir kaybedildi  
 WCF üzerinde öznitelikleri izini kaybeder bir `<wst:Claims>` öğesinde bir `RST` WSDL içe aktarma yaparken şablonu. Belirttiğiniz Bu, bir WSDL içe aktarma sırasında `<Claims>` doğrudan `WSFederationHttpBinding.Security.Message.TokenRequestParameters` veya `IssuedSecurityTokenRequestParameters.AdditionalRequestParameters` talep türü koleksiyonları doğrudan kullanmak yerine.  Öznitelikleri alma kaybederse olduğundan, bağlama değil WSDL gidiş dönüş düzgün bir şekilde yapar ve bu nedenle istemci tarafında doğru değil.  
  
 Düzeltme alma yaptıktan sonra bağlama doğrudan istemcide değiştirmektir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Bilgilerin Açığa Çıkması](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Ayrıcalıkların Yükseltilmesi](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Hizmet Reddi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [İzinsiz Değişiklik](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Yeniden Yürütme Saldırıları](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
