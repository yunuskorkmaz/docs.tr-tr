---
title: Güvenlik Protokolleri sürüm 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
ms.openlocfilehash: 684ab50b6dab4b97577acf7673ed14c53e5af13e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183951"
---
# <a name="security-protocols-version-10"></a>Güvenlik Protokolleri sürüm 1.0
Web Hizmetleri Güvenlik protokollerini tüm var olan Kurumsal güvenlik gereksinimlerini Mesajlaşma kapsayan Web Hizmetleri güvenlik mekanizmaları sağlar. Bu bölümde Windows Communication Foundation (WCF) sürüm 1.0 ayrıntılarını açıklar (uygulanan <xref:System.ServiceModel.Channels.SecurityBindingElement>) güvenlik protokollerini aşağıdaki Web Hizmetleri için.  
  
|Belirtimi/belge|Bağlantı|  
|-|-|  
|WSS: SOAP ileti güvenliği 1.0|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|
|WSS: Kullanıcı adı belirteci profili 1.0|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|WSS: X509 profili 1.0 belirteç.|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|
|WSS: SAML 1.1 belirteç profili 1.0|<https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|
|WSS: SOAP ileti güvenliği 1.1|<https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|
|WSS kullanıcı adı belirteci Profil 1.1|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|WSS: X.509 belirteci Profil 1.1|<https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|
|WSS: Kerberos belirteci Profil 1.1|<https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|
|WSS: SAML 1.1 belirteç Profil 1.1|<https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|
|WS-Secure Conversation|<http://specs.xmlsoap.org/ws/2005/02/sc/WS-SecureConversation.pdf>|
|WS-Güven|<http://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf>|
|Uygulama Not:<br /><br /> WS-Trust TLS el sıkışma için kullanma|Yayımlanacak|  
|Uygulama Not:<br /><br /> WS-Trust SPNEGO için kullanma|Yayımlanacak|  
|Uygulama Not:<br /><br /> Web uç noktası başvuruları adresleme ve kimlik Hizmetleri|Yayımlanacak|  
|WS-SecurityPolicy 1.1<br /><br /> (2005/07)|<http://specs.xmlsoap.org/ws/2005/07/securitypolicy/ws-securitypolicy.pdf><br /><br /> tarafından düzeltilir gibi [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) OASIS WS-SX teknik komitesi gönderildi |  
  
 WCF, sürüm 1, Web Hizmetleri güvenlik yapılandırması için temel olarak kullanılabilecek 17 kimlik doğrulama modları sağlar. Her modu gibi dağıtım gereksinimleri, ortak bir dizi için optimize edilmiştir:  
  
-   Hizmet ve istemci kimlik doğrulaması için kullanılan kimlik bilgileri.  
  
-   İleti veya aktarım güvenlik koruma mekanizması.  
  
-   İleti exchange desenleri.  
  
|Kimlik doğrulama modu|İstemci kimlik doğrulaması|Sunucu kimlik doğrulaması|Mod|  
|-------------------------|---------------------------|---------------------------|----------|  
|UserNameOverTransport|Kullanıcı adı/parola|X509|Taşıma|  
|CertificateOverTransport|X509|X509|Taşıma|  
|KerberosOverTransport|Windows|X509|Taşıma|  
|IssuedTokenOverTransport|Federasyon|X509|Taşıma|  
|SspiNegotiatedOverTransport|Windows SSPI anlaşması|Windows SSPI anlaşması|Taşıma|  
|AnonymousForCertificate|Yok.|X509|İleti|  
|UserNameForCertificate|Kullanıcı adı/parola|X509|İleti|  
|MutualCertificate|X509|X509|İleti|  
|MutualCertificateDuplex|X509|X509|İleti|  
|IssuedTokenForCertificate|Federasyon|X509|İleti|  
|Kerberos|Windows|Windows|İleti|  
|IssuedToken|Federasyon|Federasyon|İleti|  
|SspiNegotiated|Windows SSPI anlaşması|Windows SSPI anlaşması|İleti|  
|AnonymousForSslNegotiated|Yok.|X509, TLS Nego|İleti|  
|UserNameForSslNegotiated|Kullanıcı adı/parola|X509, TLS Nego|İleti|  
|MutualSslNegotiated|X509|X509, TLS Nego|İleti|  
|IssuedTokenForSslNegotiated|Federasyon|X509, TLS Nego|İleti|  
  
 Bu tür bir kimlik doğrulama modları kullanarak uç noktaları, WS-SecurityPolicy (WS-SP) kullanarak kendi güvenlik gereksinimleri ifade edebilir. Bu belge, güvenlik üstbilgi ve her kimlik doğrulama modu için altyapı iletileri yapısını açıklar ve ilkeleri ve iletileri örneklerini sağlar.  
  
 Güvenli oturumlar uygulamalar arasında çok ileti iletişimlerini korumak için destek sağlamak için WS-SecureConversation WCF yararlanır.  "Güvenli oturumlar" aşağıdaki uygulama ayrıntıları için bkz.  
  
 Kimlik doğrulama modları yanı sıra WCF çoğu ileti güvenlik tabanlı kimlik doğrulama modları, örneğin geçerli genel koruma mekanizması denetleyen ayarları sağlar: İmza ve şifreleme işlemleri, algoritma paketleri, anahtar türetme sırası ve imza onayı.  
  
 Bu belgede, aşağıdaki ön ekleri ve ad alanları kullanılır.  
  
|Ön eki|Ad Alanı|  
|------------|---------------|  
|s|<https://www.w3.org/2003/05/soap-envelope/>|
|SP|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/>|
|a|<https://www.w3.org/2005/08/addressing>|  
|wsse|TBD – OASIS WSS 1.0 URI'Sİ|  
|wsse11|TBD – OASIS WSS 1.1 URI'Sİ|  
|wsu|TBD – OASIS WSS 1.0 yardımcı programı URI'si|  
|DS|TBD – W3C XMLDSig URI'si|  
|WST|TBD – WS-Trust 2005/02 URI'si|  
|wssc|TBD – WS-SecureConversation 2005/02 URI'si|  
|wsaw|TBD - WS-Addressing policy ad alanı|  
|WSP|<http://schemas.xmlsoap.org/ws/2004/09/policy>|  
|mssp|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy>|
  
## <a name="1-token-profiles"></a>1. Belirteç profilleri  
 Web Hizmetleri Güvenlik belirtimleri kimlik bilgisi güvenlik belirteçleri temsil eder. WCF aşağıdaki belirteç türlerini destekler:  
  
### <a name="11-usernametoken"></a>1.1 UsernameToken  
 WCF UsernameToken10 ve UsernameToken11 profilleriyle aşağıdaki kısıtlamaları aşağıdaki gibidir:  
  
 UsernameToken\Password öğesindeki R1101 PasswordType özniteliği ya da atlanmış olabilir veya #PasswordText (varsayılan) bir değer olamaz.  
  
 Bir genişletilebilirlik kullanarak #PasswordDigest uygulayabilirsiniz. Yeterince güvenli parola koruma mekanizması olarak #PasswordDigest genellikle mistaken gözlenmiştir. Ancak #PasswordDigest UsernameToken şifrelenmesi için bir alternatif olarak hizmet veremez. #PasswordDigest birincil amacı yeniden yürütme saldırılarına karşı bir korumadır. WCF kimlik doğrulama modları ileti imzalarını kullanarak yeniden yürütme saldırı tehditlerine azalır.  
  
 B1102 WCF UsernameToken Nonce ve oluşturulan alt öğeleri hiçbir zaman yayar.  
  
 Bu alt öğeleri yeniden yürütme algılaması yardımcı olmak için tasarlanmıştır. Bunun yerine, WCF ileti imzalarını kullanır.  
  
 OASIS WSS SOAP ileti güvenlik UsernameToken Profile 1.1 (UsernameToken11) anahtar türetme parola özelliğini kullanıma sunmuştur.  
  
 B1103 UsernameToken parola için anahtar türetme değil kullanılmalıdır ve bu nedenle şifreleme işlemleri için.  
  
 Stratejinin: parolaları genel şifreleme işlemleri için kullanılacak zayıf olarak kabul edilir.  
  
### <a name="12-x509-token"></a>x 509 belirteci 1.2  
 WCF X509v3 sertifikalarını bir kimlik bilgisi türü olarak destekler ve aşağıdaki kısıtlamalarla X509TokenProfile1.0 ve X509TokenProfile1.1 izler:  
  
 X509v3 sertifika içerdiğinde BinarySecurityToken öğesindeki R1201 ValueType özniteliği değeri #X509v3 olması gerekir.  
  
 Değer türleri WSS X509 da belirteci profili 1.0 ve 1.1 #X509PKIPathv1 ve #PKCS7 olarak tanımlayın. WCF bu türleri desteklemez.  
  
 R1202 SubjectKeyIdentifier (KAYAK) uzantı ise x X509 içinde mevcut sertifika wsse:KeyIdentifier olmalıdır belirtecine dış başvurular için kullanılan, ValueType ile #X509SubjectKeyIdentifier ve içeriğini base64 ile kodlanmış, öznitelik değeri Sertifikanın KAYAK uzantısı.  
  
 KAYAK başvuruları yaygın olarak uygulanan ve kendini kanıtlamış bir yüksek düzeyde birlikte çalışabilen bir dış başvuru türü olması.  
  
 R1203 Dış başvuru X509 için güvenlik belirteci olmamalıdır ds:X509IssuerSerial'ı kullanın.  
  
 R1204 varsa X509TokenProfile1.1, bir dış başvuru X509 güvenlik belirteci kullanmalıdır WS-güvenlik 1.1 tarafından sunulan parmak izi için kullanılıyor.  
  
 WCF X509IssuerSerial destekler. Ancak vardır X509IssuerSerial ile birlikte çalışabilirlik sorunlarını: WCF X509IssuerSerial iki değerlerini karşılaştırmak için bir dize kullanır. Bir konu adı bileşenleri yeniden sıralar ve bir WCF hizmeti için bir sertifika başvuru gönderir, bu nedenle, bulunamamış olabilir.  
  
### <a name="13-kerberos-token"></a>1.3 Kerberos belirteci  
 WCF KerberosTokenProfile1.1 aşağıdaki kısıtlamaları olan Windows kimlik doğrulaması amacıyla destekler:  
  
 R1301 bir Kerberos belirteci gerekir taşıyan bir GSS değerini Kerberos v4 AP_REQ GSS_API Kerberos belirtimi ile tanımlanan sarmalandı ve değer #GSS_Kerberosv5_AP_REQ ValueType özniteliğiyle olması gerekir.  
  
 WCF kullanan GSS Kerberos AP-REQ, olmayan bir çıplak AP-talep sarmalanmış Bu bir güvenlik en iyi uygulamadır.  
  
### <a name="14-saml-v11-token"></a>1.4 SAML v1.1 belirteci  
 WCF WSS SAML belirteci profilleri 1.0 ve 1.1 için SAML v1.1 belirteçleri destekler. SAML belirteci biçimleri'nın diğer sürümlerinin uygulamak mümkündür.  
  
### <a name="15-security-context-token"></a>1.5 güvenlik bağlamı belirteci  
 WCF güvenlik bağlamı belirteci (WS-SecureCoversation sunulan SCT) destekler. SCT SecureConversation içinde de oluşturulan bir güvenlik bağlamı temsil etmek için kullanılan ikili anlaşma TLS ve SSPI protokoller olarak aşağıda açıklanmıştır.  
  
## <a name="2-common-message-security-parameters"></a>2. Ortak ileti güvenlik parametreleri  
  
### <a name="21-timestamp"></a>2.1 zaman damgası  
 Zaman damgası varlığı kullanılarak denetlenir <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> özelliği <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı. WCF wsse:TimeStamp wsse ile her zaman serileştiren: oluşturulan ve wsse: alanları süresi dolar. İmzalama kullanıldığında wsse:TimeStamp her zaman imzalanır.  
  
### <a name="22-protection-order"></a>2.2 koruma sırası  
 WCF ileti koruma sırası "Önce oturum şifrelemek" ve "Şifrelemek önce oturumu" (Güvenlik İlkesi 1.1) destekler. "Şifrele önce oturum" gibi nedenlerle önerilir: WS-güvenlik 1.1 SignatureConfirmation mekanizması kullanılır ve imza şifrelenmiş içerik üzerinde yapar sürece iletileri şifrelemek önce oturum ile korunan imza değiştirme saldırılara açık daha sıkı denetim.  
  
### <a name="23-signature-protection"></a>2.3 imza koruma  
 Şifreleme önce oturum kullanıldığında, şifrelenmiş içerik veya imzalama anahtarı tahmin için (özellikle özel belirteç zayıf anahtar malzemesi ile kullanıldığında) deneme yanılma saldırıları önlemek için imza korumak için önerilir.  
  
### <a name="24-algorithm-suite"></a>2.4 algoritması paketi  
 WCF güvenlik ilkesi 1.1 içinde listelenen tüm algoritması paketlerini destekler.  
  
### <a name="25-key-derivation"></a>2.5 anahtar türetme  
 WCF "Anahtar türetme simetrik anahtarlar için" WS-SecureConversation açıklandığı gibi kullanır.  
  
### <a name="26-signature-confirmation"></a>2.6 imza onayı  
 İmza onayı imzaları kümesini korumak için ortadaki adam saldırılarına karşı koruma olarak olabilir.  
  
### <a name="27-security-header-layout"></a>2.7 güvenlik üst bilgisi düzeni  
 Her kimlik doğrulama modu, güvenlik üst bilgisi için belirli bir düzen açıklar. Güvenlik üst bilgisi içinde yarı sıralı öğeleridir. Güvenlik üst bilgi alt öğelerin sırasını tanımlamak için aşağıdaki güvenlik üst bilgisi düzeni modları WS-Security Policy tanımlar:  
  
|||  
|-|-|  
|Katı|Öğeleri "kullanılmadan önce bildirme" ilkesi numaralı düzeni kuralları bölüme 7.7.1 genel göre Güvenlik İlkesi'nde açıklanan güvenlik üst bilgi aşağıdaki eklenir.|  
|Belirsiz|WSS için uygun olan herhangi bir sırada güvenlik üst öğeleri eklendi: SOAP ileti güvenliği.|  
|LaxTimestampFirst|İlk öğe dışında güvenlik üstbilgisinde Lax bir wsse:Timestamp aynı olmalıdır|  
|LaxTimestampLast|Belirsiz bir wsse:Timestamp güvenlik üst bilgisindeki son öğe olmalıdır dışında aynı|  
  
 WCF güvenlik üst bilgisi düzeni için tüm dört modlarını destekler. Güvenlik üst bilgisi yapısı ve ileti örnekleri aşağıdaki kimlik doğrulama modları için "Strict" modu izleyin.  
  
## <a name="2-common-message-security-parameters"></a>2. Ortak ileti güvenlik parametreleri  
 Bu bölümde, hizmet ve istemci tarafından alınıp verilen iletileri güvenlik üst bilgisi yapısı gösteren örneklerinin yanı sıra her bir kimlik doğrulama modu örnek ilkeleri sağlar.  
  
### <a name="61-transport-protection"></a>6.1 taşıma koruma  
 WCF mesajlarını korumak için güvenli aktarım kullanan beş kimlik doğrulama modları sağlar. UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport ve SspiNegotiatedOverTransport.  
  
 Bu kimlik doğrulama modları SecurityPolicy içinde açıklanan aktarım bağlama kullanılarak oluşturulur. UserNameOverTransport için kimlik doğrulama modu UsernameToken imzalı destekleme belirteci ' dir. Bir kimlik doğrulama modları için belirteç imzalı ve onaylanan bir belirteç görünür. Ek C.1.2 ve C.1.3, SecurityPolicy ayrıntılı güvenlik üst bilgisi düzeni açıklanmaktadır. Aşağıdaki örnekte güvenlik üst bilgileri bir belirli kimlik doğrulama modu katı düzenini gösterir.  
  
 Tüm durumlarda belirteçleri "Türetilmiş anahtarları" özelliği "false" değeridir.  
  
 Aktarım bağlama çeşitli özelliklerin değerlerini aşağıdaki gibidir:  
  
 Zaman damgası: true  
  
 Güvenlik üst bilgisi düzeni: katı  
  
 Algoritma paketini: Basic256  
  
#### <a name="611-usernameovertransport"></a>6.1.1 UsernameOverTransport  
 Bu kimlik doğrulama modu SOAP katmanında başlatıcıdan alıcının her zaman gönderilen imzalı destekleme belirteci olarak görüntülenen bir kullanıcı adı belirteci ile istemci kimliğini doğrular. Aktarım katmanında bir X.509 sertifikası kullanarak hizmet kimlik doğrulaması yapılır. Kullanılan bağlama aktarım bağlama ' dir.  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id='UsernameOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:SignedSupportingTokens >  
        <wsp:Policy>  
          <sp:UsernameToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:WssUsernameToken10 />   
            </wsp:Policy>  
          </sp:UsernameToken>  
        </wsp:Policy>  
      </sp:SignedSupportingTokens>  
      <sp:Wss11 >  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10 >  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 Güvenlik üst bilgisi düzeni  
  
 İstek  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:UsernameToken ... >  
  ...  
  </wsse:UsernameToken>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a>6.1.2 CertificateOverTransport  
 SOAP katmanında başlatıcıdan alıcıya gönderilen her zaman bir onaylama destekleme belirteci olarak göründüğü bu kimlik doğrulama modu istemci kimlik doğrulaması kullanarak bir X.509 sertifikası. Aktarım katmanında bir X.509 sertifikası kullanarak hizmet kimlik doğrulaması yapılır. Kullanılan bağlama aktarım bağlama ' dir.  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id='CertificateOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding xmlns:sp='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy' >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
             <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy>  
              <sp:RequireThumbprintReference />   
              <sp:WssX509V3Token10 />   
            </wsp:Policy>  
          </sp:X509Token>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 Güvenlik üst bilgisi düzeni  
  
 İstek  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wse:Timestamp u:Id="_0">  
  ...  
  </wse:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a>6.1.3 IssuedTokenOverTransport  
 Bu kimlik doğrulama modu ile istemci hizmeti için bu nedenle, kimlik doğrulaması yapmaz ancak yerine bir güvenlik belirteci hizmeti (STS) tarafından verilmiş bir belirteç sunar ve paylaşılan anahtar bilgi kanıtlar. Verilen belirteç SOAP katmanında başlatıcıdan alıcıya gönderilen her zaman bir onaylama destekleme belirteci olarak görünür. Aktarım katmanında bir X.509 sertifikası kullanarak hizmet kimlik doğrulaması yapılır. Aktarım bağlama bağlamadır.  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id='IssuedTokenOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding >  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:IssuedToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <sp:RequestSecurityTokenTemplate>  
              <wst:KeyType>  
              http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
              </wst:KeyType>   
            </sp:RequestSecurityTokenTemplate>  
            <wsp:Policy>  
              <sp:RequireInternalReference />   
            </wsp:Policy>  
          </sp:IssuedToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 Güvenlik üst bilgisi düzeni  
  
 İstek  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion ...>  
  ...  
  </saml:Assertion>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a>6.1.4 KerberosOverTransport  
 Bu kimlik doğrulama modu ile bir Kerberos anahtarı kullanarak hizmete istemcinin kimliğini doğrular. Kerberos belirteci SOAP katmanında bir onaylama destekleme belirteci görünür. Aktarım katmanında bir X.509 sertifikası kullanarak hizmet kimlik doğrulaması yapılır. Aktarım bağlama bağlamadır.  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id='KerberosOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:KerberosToken  
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
            <wsp:Policy>  
              <sp:WssGssKerberosV5ApReqToken11 />   
            </wsp:Policy>  
          </sp:KerberosToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 Güvenlik üst bilgisi düzeni  
  
 İstek  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken ValueType="...#GSS_Kerberosv5_AP_REQ">  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a>6.1.5 SspiNegotiatedOverTransport  
 Bu modda, istemci ve sunucu kimlik doğrulaması gerçekleştirmek üzere bir anlaşma protokolü kullanılır. Kerberos Mümkünse, kullanılan aksi NTLM. Sonuçta elde edilen SCT SOAP katmanında başlatıcıdan alıcılara gönderilen her zaman bir onaylama destekleme belirteci olarak görünür. Hizmet, ayrıca aktarım katmanında bir X.509 sertifikası tarafından doğrulanır. Kullanılan bağlama aktarım bağlama ' dir. "SPNEGO" (anlaşması) WCF SSPI ikili anlaşma protokolü WS-Trust ile nasıl kullandığını açıklar. SCT SPNEGO anlaşma oluşturulduktan sonra güvenlik üst bilgisi bu bölümdeki verilebilir.  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id='SspiNegotiatedOverTransport_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:TransportBinding>  
        <wsp:Policy>  
          <sp:TransportToken>  
            <wsp:Policy>  
              <sp:HttpsToken RequireClientCertificate='false' />   
            </wsp:Policy>  
          </sp:TransportToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
        </wsp:Policy>  
      </sp:TransportBinding>  
      <sp:EndorsingSupportingTokens>  
        <wsp:Policy>  
          <sp:SpnegoContextToken   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
            <wsp:Policy />   
          </sp:SpnegoContextToken>  
          <sp:SignedParts>  
            <sp:Header Name='To'   
Namespace='http://www.w3.org/2005/08/addressing' />   
          </sp:SignedParts>  
        </wsp:Policy>  
      </sp:EndorsingSupportingTokens>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples"></a>Güvenlik üstbilgi örnekler  
 Güvenlik bağlamı belirteci SPNEGO el sıkışması WS-Trust ikili anlaşması kullanılarak kurulduktan sonra uygulama iletileri güvenlik üst bilgileri aşağıdaki yapıya sahip olması.  
  
 İstek  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:SecurityContextToken u:Id="uuid-2202746a-7725-453d-8747-809cb718dab0-29" >  
  ...  
  </wssc:SecurityContextToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a>6.2 hizmet kimlik doğrulaması için X.509 sertifikaları kullanma  
 Bu bölümde aşağıdaki kimlik doğrulama modları açıklanır: MutualCertificate WSS1.0, karşılıklı CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate ve IssuedTokenForCertificate.  
  
#### <a name="621-mutualcertificate-wss10"></a>6.2.1 MutualCertificate WSS1.0  
 Başlatıcı belirteciyle SOAP katmanında görünen bu kimlik doğrulama modu istemci kimlik doğrulaması kullanarak bir X.509 sertifikası. Hizmet, ayrıca bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır.  
  
 Aşağıdaki özellik değerlerini asimetrik bir bağlamayla kullanılan bağlama şöyledir:  
  
 Başlatıcı belirteci: ekleme modu ayarlamak için .../IncludeToken/AlwaysToRecipient istemcinin X.509 sertifikası  
  
 Alıcı belirteci: Sunucu X.509 sertifikası kullanıcının, ekleme moduyla .../IncludeToken/Never ayarlanır  
  
 Belirteç koruma: False  
  
 Tüm üst bilgisi ve gövdesi imzalar: True  
  
 Koruma sırasını: SignBeforeEncrypt  
  
 Şifreleme imzası: True  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificate_WSS10_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Güvenlik üstbilgi örnekler: EncryptBeforeSign  
  
 İstek  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="622-mutualcertificateduplex"></a>6.2.2 MutualCertificateDuplex  
 Başlatıcı belirteciyle SOAP katmanında görünen bu kimlik doğrulama modu istemci kimlik doğrulaması kullanarak bir X.509 sertifikası. Hizmet, ayrıca bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır.  
  
 Aşağıdaki özellik değerlerini asimetrik bir bağlamayla kullanılan bağlama şöyledir:  
  
 Başlatıcı belirteci: İstemcinin X509 sertifikası ekleme modu için .../IncludeToken/AlwaysToRecipient ayarlanır  
  
 Alıcı belirteci: Sunucunun X509 sertifikası ekleme modu için .../IncludeToken/AlwaysToInitiator ayarlanır  
  
 Belirteç koruma: False  
  
 Tüm üst bilgisi ve gövdesi imzalar: True  
  
 Koruma sırasını: SignBeforeEncrypt  
  
 Şifreleme imzası: True  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id='MutualCertificateDuplex_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:AsymmetricBinding>  
        <wsp:Policy>  
          <sp:InitiatorToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:InitiatorToken>  
          <sp:RecipientToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToInitiator' >  
                <wsp:Policy>  
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:RecipientToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:AsymmetricBinding>  
      <sp:Wss10>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
        </wsp:Policy>  
      </sp:Wss10>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek ve yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
    <xenc:ReferenceList>  
    ...  
    </xenc:ReferenceList>  
  </xenc:EncryptedKey>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek ve yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a>6.2.3 SymmetricBinding X.509 hizmet kimlik doğrulamasını kullanarak.  
 "WSS10" X509 senaryolarıyla için sınırlı destek sağlanmaktadır belirteçleri. Örneğin, yalnızca hizmet X509 belirteci kullanarak iletileri için imza ve şifreleme koruma sağlamak için hiçbir yolu yoktu. "WSS11" EncryptedKey kullanımını simetrik bir belirteç kullanıma sunuldu. Şimdi hizmetin X.509 sertifikası için şifrelenmiş geçici bir anahtar hem istek hem de yanıt iletilerini koruma için kullanılabilir. ' % S'bölümünde 6.4 açıklanan kimlik doğrulama modları, bu düzeni kullanın.  
  
 WS-SecurityPolicy SymmetricBinding hizmetiyle kullanarak bu deseni açıklar X509 token koruma belirteç.  
  
 Kimlik doğrulama modları AnonymousForCertificate, UsernameForCertificate MutualCertificate WSS11 ve IssuedTokenForCertificate tüm sp:SymmetricBinding benzer bir örneğini aşağıdaki özellik değerleri kullanın:  
  
 Koruma belirteci: Sunucunun X509 sertifikası ekleme modu için .../IncludeToken/Never ayarlanır  
Belirteç koruma: False  
  
 Tüm üst bilgisi ve gövdesi imzalar: True  
  
 Koruma sırasını: SignBeforeEncrypt  
  
 Şifreleme imzası: True  
  
 Yukarıdaki kimlik doğrulama modları, yalnızca kullandıkları destek belirteçleri ile farklı. AnonymousForCertificate destekleyici tarafından istenen belirteçleri yok, MutualCertificate WSS 1.1 sahip istemcinin X509 sertifika bir destek belirteçleri onaylama olarak, UserNameForCertificate sahip bir kullanıcı adı belirteci imzalı destekleme belirteci olarak ve IssuedTokenForCertificate verilen belirtecin bir onaylama destekleme belirteci sahiptir.  
  
 İlke  
  
 Simetrik bağlama  
  
```xml  
<wsp:Policy wsu:Id='SymmetricCert_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:X509Token   
sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Never' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:RequireThumbprintReference />   
                  <sp:WssX509V3Token10 />   
                </wsp:Policy>  
              </sp:X509Token>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />  
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting Token Assertions appear here -->  
      ...  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
          <sp:RequireSignatureConfirmation />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="624-anonymousforcertificate"></a>6.2.4 AnonymousForCertificate  
 Bu kimlik doğrulama modu ile istemci anonimdir ve bir X.509 sertifikası kullanarak hizmet kimlik doğrulaması. Kullanılan bağlama 6.4.2 içinde anlatıldığı gibi simetrik bağlama bir örneğidir.  
  
 İlke  
  
 Yukarıdaki 6.2.3 "ilke" bağlaması ayrıntıları için bkz.  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="625-usernameforcertificate"></a>6.2.5 UserNameForCertificate  
 Bu kimlik doğrulama modu ile görüntülenen bir kullanıcı adı belirteci SOAP katmanında imzalı destekleme belirteci kullanarak hizmete istemcinin kimliğini doğrular. Hizmet bir X.509 sertifikası kullanarak istemcinin kimliğini doğrular. Kullanılan bağlama, hizmetin ortak anahtar ile şifrelenmiş bir istemci tarafından oluşturulan bir anahtarı olan koruma belirtecine sahip simetrik bir bağlamadır.  
  
 İlke  
  
 Yukarıdaki 6.2.3 "ilke" bağlaması ayrıntıları için bkz.  
  
 Destekleme belirteci imzalayan  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />   
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="626-mutualcertificate-wss-11"></a>6.2.6 MutualCertificate (WSS 1.1)  
 SOAP katmanında bir onaylama destekleme belirteci olarak görünen bu kimlik doğrulama modu istemci kimlik doğrulaması kullanarak bir X.509 sertifikası. Hizmet, ayrıca bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır. Kullanılan bağlama, hizmetin ortak anahtar ile şifrelenmiş bir istemci tarafından oluşturulan bir anahtarı olan koruma belirtecine sahip simetrik bir bağlamadır.  
  
 İlke  
  
 İlke 6.2.3 bağlaması ayrıntıları için bkz.  
  
 Onaylama destekleme belirteci  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />   
        <sp:WssX509V3Token10 />   
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="627-issuedtokenforcertificate"></a>6.2.7 IssuedTokenForCertificate  
 Bu kimlik doğrulaması ile istemci hizmete, bu nedenle, ancak bunun yerine kimlik doğrulamasını yapmaz modu STS tarafından verilen bir belirteç verir ve bir paylaşılan anahtar bilgisini kanıtlayan sorgu. Verilen belirteç SOAP katmanında bir onaylama destekleme belirteci görünür. Hizmet bir X.509 sertifikası kullanarak istemcinin kimliğini doğrular. Kullanılan bağlama, hizmetin ortak anahtar ile şifrelenmiş bir istemci tarafından oluşturulan bir anahtarı olan koruma belirtecine sahip simetrik bir bağlamadır.  
  
 İlke  
  
 İlke 6.2.3 bağlama ayrıntıları için bkz.  
  
 Onaylama destekleme belirteci  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
       </wst:KeyType>  
     </sp:RequestSecurityTokenTemplate>  
     <wsp:Policy>  
       <sp:RequireDerivedKeys />   
       <sp:RequireInternalReference />   
     </wsp:Policy>  
   </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <xenc:EncryptedKey>  
  ...  
  </xenc:EncryptedKey>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wssc:DerivedKeyToken>  
  ...  
  </wssc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
## <a name="63-kerberos"></a>6.3 Kerberos  
 Bu kimlik doğrulama modu ile bir Kerberos anahtarı kullanarak hizmete istemcinin kimliğini doğrular. Bu aynı anahtar Ayrıca sunucu kimlik doğrulaması sağlar. Kullanılan bağlama, aşağıdaki özelliklere sahip bir simetrik bağlamadır;  
  
 Koruma belirteci: .../IncludeToken/Once için ekleme modu Kerberos anahtarı ayarlayın  
Belirteç koruma: False  
  
 Tüm üst bilgisi ve gövdesi imzalar: True  
  
 Koruma sırasını: SignBeforeEncrypt  
  
 Şifreleme imzası: True  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id='Kerberos_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:KerberosToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/Once' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:WssGssKerberosV5ApReqToken11 />   
                </wsp:Policy>  
              </sp:KerberosToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic128 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsse:BinarySecurityToken>  
  ...  
  </wsse:BinarySecurityToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a>6.4 IssuedToken  
 İstemci hizmete kimlik doğrulaması yapmaz, bu kimlik doğrulama modu ile bu nedenle, yerine istemci STS tarafından verilen bir belirteç sunar ve paylaşılan anahtar bilgi kanıtlar. İstemcisini, bu nedenle hizmet kimliği, bunun yerine STS şifreler paylaşılan anahtarı verilen belirtecin bir parçası olarak yalnızca hizmet anahtarının şifresini çözüm olacak şekilde. Aşağıdaki özelliklerle simetrik bağlama kullanılan bağlama gibidir;  
  
 Koruma belirteç: Belirteci veren, ekleme modu için .../IncludeToken/AlwaysToRecipient ayarlanır  
Belirteç koruma: False  
  
 Tüm üst bilgisi ve gövdesi imzalar: True  
  
 Koruma sırasını: SignBeforeEncrypt  
  
 Şifreleme imzası: True  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple3_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <sp:RequestSecurityTokenTemplate>  
                  <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
                  </wst:KeyType>   
                </sp:RequestSecurityTokenTemplate>  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:RequireInternalReference />   
                </wsp:Policy>  
              </sp:IssuedToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a>6.5 SslNegotiated hizmet kimlik doğrulaması için kullanma  
 Bu bölümde, bir grup olan bir güvenlik bağlamı belirteci başına WS-anahtar değeri, WS-Trust (WS-T) lk TLS protokolü yürüterek varılır SecureConversation (WS-SC) koruma belirtecine sahip bir simetrik bağlama kullanan kimlik doğrulama modları açıklanır / RSTR iletileri. WS-Trust kullanarak TLS el sıkışma uygulamasının Ayrıntılar TLSNEGO içinde açıklanmıştır. Burada ileti örneklerde SCT ilişkili güvenlik bağlamı ile zaten bir anlaşması kurulan varsayacağız.  
  
 Kullanılan bağlama, aşağıdaki özelliklere sahip bir simetrik bağlamadır;  
  
 Koruma belirteci: SslContextToken, ekleme modu için .../IncludeToken/Never ayarlanır  
Belirteç koruma: False  
  
 Tüm üst bilgisi ve gövdesi imzalar: True  
  
 Koruma sırasını: SignBeforeEncrypt  
  
 Şifreleme imzası: True  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a>6.5.1 SslNegotiated hizmeti kimlik doğrulama İlkesi  
 Bu bölümdeki tüm kimlik doğrulama modları için ilke benzerdir ve yalnızca özel imzalı desteklemenin veya kullanılan belirteçleri onaylama farklılık gösterir.  
  
```xml  
<wsp:Policy wsu:Id='SslNegotiated_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <mssp:SslContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' />  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                </wsp:Policy>  
              </mssp:SslContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <!-- Supporting token assertions go here -->  
      ..  
      <sp:Wss11>   
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
#### <a name="652-anonymousforsslnegotiated"></a>6.5.2 AnonymousForSslNegotiated  
 Bu kimlik doğrulama modu ile istemci anonimdir ve bir X.509 sertifikası kullanarak hizmet kimlik doğrulaması. Kullanılan bağlama 6.5.1 yukarıda açıklandığı gibi simetrik bağlama bir örneğidir.  
  
 İlke  
  
 İlke Bağlama Ayrıntılar için 6.5.1 görürsünüz.  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="653-usernameforsslnegotiated"></a>6.5.3 UserNameForSslNegotiated  
 Bu kimlik doğrulaması ile istemci modunda görüntülenen bir kullanıcı adı belirteci SOAP katmanında imzalı destekleme belirteci kullanarak kimliğini doğrular. Hizmet bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır. Kullanılan bağlama 6.5.1 içinde anlatıldığı gibi simetrik bağlama bir örneğidir.  
  
 İlke  
  
 Bağlaması ayrıntıları için yukarıdaki 6.5.1 bölümüne bakın  
  
 Destekleme belirteci imzalayan  
  
```xml  
<sp:SignedSupportingTokens>  
  <wsp:Policy>  
    <sp:UsernameToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:WssUsernameToken10 />   
      </wsp:Policy>  
    </sp:UsernameToken>  
  </wsp:Policy>  
</sp:SignedSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="654-issuedtokenforsslnegotiated"></a>6.5.4 IssuedTokenForSslNegotiated  
 Bu kimlik doğrulaması ile istemci hizmete, bu nedenle, ancak bunun yerine kimlik doğrulamasını yapmaz modu STS tarafından verilen bir belirteç verir ve bir paylaşılan anahtar bilgisini kanıtlar. Verilen belirteç SOAP katmanında bir onaylama destekleme belirteci görünür. Hizmet bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır. Kullanılan bağlama 6.5.1 yukarıda açıklandığı gibi simetrik bağlama bir örneğidir.  
  
 İlke  
  
 Bağlaması ayrıntıları için yukarıdaki 6.5.1 bölümüne bakın  
  
 Onaylama destekleme belirteci  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:IssuedToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <sp:RequestSecurityTokenTemplate>  
        <wst:KeyType>  
http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey  
        </wst:KeyType>   
      </sp:RequestSecurityTokenTemplate>  
      <wsp:Policy>  
        <sp:RequireDerivedKeys />   
        <sp:RequireInternalReference />   
      </wsp:Policy>  
    </sp:IssuedToken>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <saml:Assertion>  
  ...  
  </saml:Assertion>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsse11:SignatureConfirmation />  
  <wsse11:SignatureConfirmation />  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
#### <a name="655-mutualsslnegotiated"></a>6.5.5 MutualSslNegotiated  
 Bu kimlik doğrulama modu ile hizmet ve istemci X.509 sertifikaları kullanarak kimlik doğrulaması. Kullanılan bağlama 6.5.1 yukarıda açıklandığı gibi simetrik bağlama bir örneğidir.  
  
 İlke  
  
 Bağlaması ayrıntıları için yukarıdaki 6.5.1 bölümüne bakın  
  
 Onaylama destekleme belirteci  
  
```xml  
<sp:EndorsingSupportingTokens>  
  <wsp:Policy>  
    <sp:X509Token sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
      <wsp:Policy>  
        <sp:RequireThumbprintReference />   
        <sp:WssX509V3Token10 />   
      </wsp:Policy>  
    </sp:X509Token>  
  </wsp:Policy>  
</sp:EndorsingSupportingTokens>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="66-sspinegotiated"></a>6.6 SspiNegotiated  
 Bu kimlik doğrulama modu ile istemci ve sunucu kimlik doğrulaması gerçekleştirmek üzere bir anlaşma protokolü kullanılır. Kerberos Mümkünse, kullanılan aksi NTLM. Kullanılan bağlama, aşağıdaki özelliklere sahip bir simetrik bağlamadır;  
  
 Koruma belirteci: SpnegoContextToken, ekleme modu için .../IncludeToken/AlwaysToRecipient ayarlanır  
Belirteç koruma: False  
  
 Tüm üst bilgisi ve gövdesi imzalar: True  
  
 Koruma sırasını: SignBeforeEncrypt  
  
 Şifreleme imzası: True  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id='CustomBinding_ISimple13_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                </wsp:Policy>  
              </sp:SpnegoContextToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
<wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
### <a name="67-secureconversation"></a>6.7 SecureConversation  
 Kullanılan bağlama, WS-SecureConversation (WS-SC) başına bir SCT olan koruma belirtecine sahip simetrik bir bağlamadır. SCT kendisi bir anlaşma protokolünü kullanan, simetrik bir bağlamadır bir iç içe bağlama göre WS-Trust (WS-Trust) veya WS-SecureConversation (WS-SC) kullanılarak belirlenir. Anlaşma Protokolü, mümkün olduğunda istemci ve sunucu kimlik doğrulaması gerçekleştirmek için Kerberos kullanır. Kerberos kullanılamıyorsa, NTLM olarak geri döner.  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id='SecureConversation_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <sp:SecureConversationToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                <wsp:Policy>  
                  <sp:RequireDerivedKeys />   
                  <sp:BootstrapPolicy>  
                    <wsp:Policy>  
                      <sp:SignedParts>  
                        <sp:Body />   
                        <sp:Header Name='To' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='From' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='FaultTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='ReplyTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='MessageID' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='RelatesTo' Namespace='http://www.w3.org/2005/08/addressing' />   
                        <sp:Header Name='Action' Namespace='http://www.w3.org/2005/08/addressing' />   
                      </sp:SignedParts>  
                      <sp:EncryptedParts>  
                        <sp:Body />   
                      </sp:EncryptedParts>  
                      <sp:SymmetricBinding>  
                        <wsp:Policy>  
                          <sp:ProtectionToken>  
                            <wsp:Policy>  
                              <sp:SpnegoContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient' >  
                                <wsp:Policy>  
                                  <sp:RequireDerivedKeys />   
                                </wsp:Policy>  
                              </sp:SpnegoContextToken>  
                            </wsp:Policy>  
                          </sp:ProtectionToken>  
                          <sp:AlgorithmSuite>  
                            <wsp:Policy>  
                              <sp:Basic256 />   
                            </wsp:Policy>  
                          </sp:AlgorithmSuite>  
                          <sp:Layout>  
                            <wsp:Policy>  
                              <sp:Strict />   
                            </wsp:Policy>  
                          </sp:Layout>  
                          <sp:IncludeTimestamp />   
                          <sp:EncryptSignature />   
                          <sp:OnlySignEntireHeadersAndBody />   
                        </wsp:Policy>  
                      </sp:SymmetricBinding>  
                      <sp:Wss11>  
                        <wsp:Policy>  
                          <sp:MustSupportRefKeyIdentifier />   
                          <sp:MustSupportRefIssuerSerial />   
                          <sp:MustSupportRefThumbprint />   
                          <sp:MustSupportRefEncryptedKey />   
                        </wsp:Policy>  
                      </sp:Wss11>  
                      <sp:Trust10>  
                        <wsp:Policy>  
                          <sp:MustSupportIssuedTokens />   
                          <sp:RequireClientEntropy />   
                          <sp:RequireServerEntropy />   
                        </wsp:Policy>  
                      </sp:Trust10>  
                    </wsp:Policy>  
                  </sp:BootstrapPolicy>  
                </wsp:Policy>  
              </sp:SecureConversationToken>  
            </wsp:Policy>  
          </sp:ProtectionToken>  
          <sp:AlgorithmSuite>  
            <wsp:Policy>  
              <sp:Basic256 />   
            </wsp:Policy>  
          </sp:AlgorithmSuite>  
          <sp:Layout>  
            <wsp:Policy>  
              <sp:Strict />   
            </wsp:Policy>  
          </sp:Layout>  
          <sp:IncludeTimestamp />   
          <sp:EncryptSignature />   
          <sp:OnlySignEntireHeadersAndBody />   
        </wsp:Policy>  
      </sp:SymmetricBinding>  
      <sp:Wss11>  
        <wsp:Policy>  
          <sp:MustSupportRefKeyIdentifier />   
          <sp:MustSupportRefIssuerSerial />   
          <sp:MustSupportRefThumbprint />   
          <sp:MustSupportRefEncryptedKey />   
        </wsp:Policy>  
      </sp:Wss11>  
      <sp:Trust10>  
        <wsp:Policy>  
          <sp:MustSupportIssuedTokens />   
          <sp:RequireClientEntropy />   
          <sp:RequireServerEntropy />   
        </wsp:Policy>  
      </sp:Trust10>  
      <wsaw:UsingAddressing />   
    </wsp:All>  
  </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security s:mustUnderstand="1">  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
  <xenc:EncryptedData>  
  ...  
  </xenc:EncryptedData>  
</wsse:Security>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:SecurityContextToken>  
  ...  
  </wsc:SecurityContextToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```  
  
 Yanıt  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <wsc:DerivedKeyToken>  
  ...  
  </wsc:DerivedKeyToken>  
  <ds:Signature>  
  ...  
  </ds:Signature>  
  <xenc:ReferenceList>  
  ...  
  </xenc:ReferenceList>  
</wsse:Security>  
```
