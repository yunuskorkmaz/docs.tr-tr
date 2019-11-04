---
title: Güvenlik Protokolleri sürüm 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
ms.openlocfilehash: e22150d21638cffdf804008c32285f900bb1e263
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459048"
---
# <a name="security-protocols-version-10"></a>Güvenlik Protokolleri sürüm 1.0
Web Hizmetleri Güvenliği protokolleri, mevcut tüm kurumsal mesajlaşma güvenlik gereksinimlerini kapsayan Web Hizmetleri güvenlik mekanizmaları sağlar. Bu bölümde, aşağıdaki Web Hizmetleri güvenlik protokollerinin Windows Communication Foundation (WCF) sürüm 1,0 ayrıntıları (<xref:System.ServiceModel.Channels.SecurityBindingElement>uygulanır) açıklanmaktadır.  
  
|Belirtim/belge|Bağlantı|  
|-|-|  
|WSS: SOAP Iletisi güvenliği 1,0|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|
|WSS: Kullanıcı adı belirteç profili 1,0|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|WSS: x509 belirteç profili 1,0|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|
|WSS: SAML 1,1 belirteç profili 1,0|<https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|
|WSS: SOAP Iletisi güvenliği 1,1|<https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|
|WSS Kullanıcı adı belirteç profili 1,1|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|WSS: X. 509.440 belirteç profili 1,1|<https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|
|WSS: Kerberos belirteç profili 1,1|<https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|
|WSS: SAML 1,1 belirteç profili 1,1|<https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|
|WS-Secure konuşması|<https://specs.xmlsoap.org/ws/2005/02/sc/WS-SecureConversation.pdf>|
|WS-Trust|<https://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf>|
|Uygulama notunun:<br /><br /> TLS el sıkışması için WS-Trust kullanma|Yayımlanacak|  
|Uygulama notunun:<br /><br /> SPNEGO için WS-Trust kullanma|Yayımlanacak|  
|Uygulama notunun:<br /><br /> Web Hizmetleri, uç nokta başvurularını ve kimliğini adresleyen|Yayımlanacak|  
|WS-SecurityPolicy 1,1<br /><br /> (2005/07)|<https://specs.xmlsoap.org/ws/2005/07/securitypolicy/ws-securitypolicy.pdf><br /><br /> OASSıS WS-SX Technical komite 'a gönderilen [Errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) tarafından değiştirilen |  
  
 WCF, sürüm 1, Web Hizmetleri güvenlik yapılandırması için temel olarak kullanılabilecek 17 kimlik doğrulama modu sağlar. Her mod ortak bir dağıtım gereksinimleri kümesi için iyileştirilmiştir, örneğin:  
  
- İstemci ve hizmetin kimliğini doğrulamak için kullanılan kimlik bilgileri.  
  
- İleti veya aktarım güvenliği koruma mekanizmaları.  
  
- İleti değişimi desenleri.  
  
|Kimlik doğrulama modu|İstemci kimlik doğrulaması|Sunucu kimlik doğrulaması|Mod|  
|-------------------------|---------------------------|---------------------------|----------|  
|UserNameOverTransport|Kullanıcı adı/parola|X509|Aktarım|  
|CertificateOverTransport|X509|X509|Aktarım|  
|KerberosOverTransport|Windows|X509|Aktarım|  
|IssuedTokenOverTransport|Federasyon|X509|Aktarım|  
|SspiNegotiatedOverTransport|Üzerinde anlaşılan Windows SSPI|Üzerinde anlaşılan Windows SSPI|Aktarım|  
|AnonymousForCertificate|Yok.|X509|İleti|  
|UserNameForCertificate|Kullanıcı adı/parola|X509|İleti|  
|Çoklu sertifika|X509|X509|İleti|  
|Değişken Uıalcertificateduplex|X509|X509|İleti|  
|IssuedTokenForCertificate|Federasyon|X509|İleti|  
|Kerberos|Windows|Windows|İleti|  
|IssuedToken|Federasyon|Federasyon|İleti|  
|SspiNegotiated|Üzerinde anlaşılan Windows SSPI|Üzerinde anlaşılan Windows SSPI|İleti|  
|Anonymousforsslanlaşmalı|Yok.|X509, TLS-Nego|İleti|  
|Usernameforsslanlaşmalı|Kullanıcı adı/parola|X509, TLS-Nego|İleti|  
|Değişken anlaşmalı|X509|X509, TLS-Nego|İleti|  
|Issuedtokenforsslanlaşmalı|Federasyon|X509, TLS-Nego|İleti|  
  
 Bu tür kimlik doğrulama modlarını kullanan uç noktalar, WS-SecurityPolicy (WS-SP) kullanarak güvenlik gereksinimlerini ifade edebilir. Bu belgede, her kimlik doğrulama modu için güvenlik üst bilgisi ve altyapı iletilerinin yapısı açıklanmakta ve ilke ve ileti örnekleri verilmektedir.  
  
 WCF, uygulamalar arasında çok ileti alışverişlerini korumak için güvenli oturumlar desteği sağlamak üzere WS-SecureConversation kullanır.  Uygulama ayrıntıları için aşağıda "güvenli oturumlar" başlığına bakın.  
  
 WCF, kimlik doğrulama modlarına ek olarak, çoğu ileti güvenlik tabanlı kimlik doğrulama modu için uygulanan genel koruma mekanizmalarını denetlemek için ayarlar sağlar; örneğin: imza sırası, şifreleme işlemleri, algoritma paketleri, anahtar türetme ve imza onayı.  
  
 Bu belgede aşağıdaki ön ekler ve ad alanları kullanılır.  
  
|koy|Ad Alanı|  
|------------|---------------|  
|s|<http://www.w3.org/2003/05/soap-envelope/>|
|SP2|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/>|
|A|<http://www.w3.org/2005/08/addressing>|  
|WSO|TBD – OASSıS WSS 1,0 URI 'SI|  
|wsse11|TBD – OASSıS WSS 1,1 URI 'SI|  
|WSU dili|TBD – OASSıS WSS 1,0 yardımcı programı URI 'SI|  
|FID|TBD – W3C XMLDSIG URI 'SI|  
|WST|TBD – WS-Trust 2005/02 URI|  
|wssc|TBD – WS-SecureConversation 2005/02 URI 'SI|  
|Wonu dili|TBD-WS-adresleme ilkesi ad alanı|  
|WSP|<http://schemas.xmlsoap.org/ws/2004/09/policy>|  
|MSSP|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy>|
  
## <a name="1-token-profiles"></a>1. belirteç profilleri  
 Web Hizmetleri Güvenliği belirtimleri güvenlik belirteçleri olarak kimlik bilgisini temsil eder. WCF aşağıdaki belirteç türlerini destekler:  
  
### <a name="11-usernametoken"></a>1,1 UsernameToken  
 WCF aşağıdaki kısıtlamalara sahip UsernameToken10 ve UsernameToken11 profillerini izler:  
  
 UsernameToken\Password öğesinde R1101 PasswordType özniteliği atlanmış veya değer #PasswordText (varsayılan) olmalıdır.  
  
 Bunlardan biri, genişletilebilirlik kullanarak #PasswordDigest uygulayabilir. #PasswordDigest genellikle yeterince güvenli bir parola koruma mekanizması olması gözlemlenmiştir. Ancak #PasswordDigest, UsernameToken şifrelemesinin bir alternatifi olarak kullanılamaz. #PasswordDigest birincil amacı, yeniden yürütme saldırılarına karşı koruma sağlamaktır. WCF kimlik doğrulama modlarında, yeniden yürütme saldırı tehditleri ileti imzaları kullanılarak azaltıldığında.  
  
 B1102 WCF hiçbir şekilde hiçbir şekilde anahtar vermez ve UsernameToken alt öğelerini oluşturmuştur.  
  
 Bu alt öğeler, yeniden yürütmeyi algılamaya yardımcı olmayı amaçlar. WCF bunun yerine ileti imzalarını kullanır.  
  
 OASSıS WSS SOAP Iletisi güvenliği UsernameToken profili 1,1 (UsernameToken11) parola özelliğinden anahtar türetme sunmuştur.  
  
 B1103 UsernameToken parolası, anahtar türetmede kullanılmamalıdır ve bu nedenle şifreleme işlemleri için kullanılmamalıdır.  
  
 Korale: parolalar genellikle şifreleme işlemleri için kullanılmak üzere çok zayıf kabul edilir.  
  
### <a name="12-x509-token"></a>1,2 x509 belirteci  
 WCF, kimlik bilgisi türü olarak X509v3 sertifikalarını destekler ve aşağıdaki kısıtlamalara sahip X509TokenProfile 1.0 ve X509TokenProfile 1.1 ' i izler:  
  
 R1201, BinarySecurityToken öğesindeki ValueType özniteliği bir X509v3 sertifikası içerdiğinde değer #X509v3 sahip olmalıdır.  
  
 WSS x509 belirteç profili 1,0 ve 1,1 de #X509PKIPathv1 ve #PKCS7 değer türleri olarak tanımlar. WCF bu türleri desteklemez.  
  
 R1202 bir x509 sertifikası içinde bir subjectKeyIdentifier (kayak) uzantısı varsa, ' nin ValueType özniteliğiyle birlikte #X509SubjectKeyIdentifier ve içerik Base64 kodlamalı değeri olan, belirteç için dış başvurular için anahtar tanımlayıcısı kullanılmalıdır. Sertifikanın Kayak uzantısı.  
  
 Kayak başvuruları yaygın olarak uygulanırlar ve yüksek oranda çalışabilen bir dış başvuru türü olarak kanıtlanmış olur.  
  
 R1203 x509 güvenlik belirtecine bir dış başvuru DS: X509IssuerSerial KULLANMAMALıDıR.  
  
 R1204 X509TokenProfile 1.1 kullanılıyorsa, x509 güvenlik belirteci için bir dış başvuru, WS-Security 1,1 tarafından tanıtılan parmak izini kullanmalıdır.  
  
 WCF, X509IssuerSerial destekler. Ancak X509IssuerSerial ile birlikte çalışabilirlik sorunları vardır: WCF, X509IssuerSerial 'in iki değerini karşılaştırmak için bir dize kullanır. Bu nedenle, konu adının bileşenlerini yeniden sipariş eden bir, bir WCF hizmetine bir sertifikaya başvuru gönderirse, bu durum bulunamamıştır.  
  
### <a name="13-kerberos-token"></a>1,3 Kerberos belirteci  
 WCF, Windows kimlik doğrulaması amacıyla aşağıdaki kısıtlamalara sahip KerberosTokenProfile 1.1 'yi destekler:  
  
 R1301 bir Kerberos belirtecinin, GSS_API ve Kerberos belirtiminde tanımlanan bir GSS sarmalanmış Kerberos v4 AP_REQ değerini taşıması ve #GSS_Kerberosv5_AP_REQ değeri ile ValueType özniteliğine sahip olması gerekir.  
  
 WCF, tam bir AP-REQ değil, GSS sarmalanmış Kerberos AP-REQ kullanır. Bu en iyi güvenlik uygulamasıdır.  
  
### <a name="14-saml-v11-token"></a>1,4 SAML v 1.1 belirteci  
 WCF, SAML v 1.1 belirteçleri için WSS SAML belirteci profilleri 1,0 ve 1,1 ' ü destekler. SAML belirteci biçimlerinin diğer sürümlerini uygulamak mümkündür.  
  
### <a name="15-security-context-token"></a>1,5 güvenlik bağlamı belirteci  
 WCF, WS-SecureConversation ' de tanıtılan güvenlik bağlamı belirtecini (SCT) destekler. SCT, SecureConversation 'de kurulu bir güvenlik bağlamını ve aşağıda açıklanan ikili anlaşma protokolleri TLS ve SSPI 'yi temsil etmek için kullanılır.  
  
## <a name="2-common-message-security-parameters"></a>2. ortak Ileti güvenlik parametreleri  
  
### <a name="21-timestamp"></a>2,1 zaman damgası  
 Zaman damgası varlığı, <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfının <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> özelliği kullanılarak denetlenir. WCF her zaman wsse: Created ve wsse: Expires alanları ile zaman damgası olarak serileştirir. Wsse: imza kullanıldığında zaman damgası her zaman imzalanır.  
  
### <a name="22-protection-order"></a>2,2 koruma sırası  
 WCF, "şifrelemeden önce Imzala" ve "oturum açmadan önce şifreleyin" (Güvenlik Ilkesi 1,1) ileti koruma sırasını destekler. Aşağıdakiler dahil olmak üzere "şifrelemeden önce imzala" önerilir: oturum açmadan önce şifrelemeden korunan iletiler, WS-Security 1,1 SignatureConfirmation mekanizması kullanılmadığı ve şifrelenmiş içerik üzerinde bir imza açık değilse imza değiştirme saldırılarına açık olur Denetim daha zordur.  
  
### <a name="23-signature-protection"></a>2,3 imza koruması  
 İmza kullanılmadan önce şifrelendiğinde, şifrelenmiş içeriği veya imzalama anahtarını tahmin etmeye yönelik deneme yanılma saldırılarını engellemek için imzayı korumanız önerilir (özellikle de, zayıf anahtar malzemeyle özel bir belirteç kullanıldığında).  
  
### <a name="24-algorithm-suite"></a>2,4 algoritma paketi  
 WCF, Güvenlik Ilkesi 1,1 ' de listelenen tüm algoritma paketlerini destekler.  
  
### <a name="25-key-derivation"></a>2,5 anahtar türetme  
 WCF, WS-SecureConversation bölümünde açıklandığı gibi "simetrik anahtarlar için anahtar türetme" kullanır.  
  
### <a name="26-signature-confirmation"></a>2,6 imza onayı  
 İmza onaylama, imza kümesini korumak için ortadaki adam saldırılarına karşı koruma sağlayabilir.  
  
### <a name="27-security-header-layout"></a>2,7 güvenlik üst bilgisi düzeni  
 Her kimlik doğrulama modu, güvenlik üst bilgisi için belirli bir düzeni tanımlar. Güvenlik üst bilgisi içindeki öğeler yarı sıralanır. Güvenlik üst bilgisi alt öğelerinin sırasını tanımlamak için, WS-Güvenlik Ilkesi aşağıdaki güvenlik üst bilgisi düzen modlarını tanımlar:  
  
|||  
|-|-|  
|Sert|Öğeler, Güvenlik Ilkesi bölümünde açıklanan numaralandırılmış düzen kurallarından sonra, "kullanmadan önce bildir" genel ilkesine göre güvenlik üstbilgisine eklenir.|  
|LAX|Öğeler, WSS: SOAP Iletisi güvenliğine uyan herhangi bir sırada güvenlik başlığına eklenir.|  
|Önce Laxtimestamp|Güvenlik üst bilgisindeki ilk öğenin bir WSO: Timestamp olması dışında LAX ile aynı|  
|Laxtimestamp son|Güvenlik üstbilgisindeki son öğenin bir WSO: Timestamp olması dışında LAX ile aynı|  
  
 WCF, güvenlik üst bilgisi düzeni için dört modunu destekler. Güvenlik üst bilgisi yapısı ve aşağıdaki kimlik doğrulama modları için ileti örnekleri "katı" modunu izler.  
  
## <a name="2-common-message-security-parameters"></a>2. ortak Ileti güvenlik parametreleri  
 Bu bölümde, istemci ve hizmet tarafından değiştirilen iletilerde güvenlik üst bilgi yapısını gösteren örneklerle birlikte her bir kimlik doğrulama modu için örnek ilkeler sağlanır.  
  
### <a name="61-transport-protection"></a>6,1 taşıma koruması  
 WCF, iletileri korumak için güvenli aktarım kullanan beş kimlik doğrulama modu sağlar; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport ve SspiNegotiatedOverTransport.  
  
 Bu kimlik doğrulama modları, SecurityPolicy ' de açıklanan aktarım bağlaması kullanılarak oluşturulur. UserNameOverTransport kimlik doğrulama modu için UsernameToken imzalı bir destekleme belirtecidir. Diğer kimlik doğrulama modlarında, belirteç imzalı bir onaylama belirteci olarak görünür. Ek C. 1.2 ve C. 1.3 SecurityPolicy, güvenlik üst bilgisi yerleşimini ayrıntılı olarak anlatmaktadır. Aşağıdaki örnek güvenlik üstbilgileri, belirli bir kimlik doğrulama modu için katı düzeni gösterir.  
  
 Her durumda belirteçlerin "türetilmiş anahtarlar" özelliğinin değeri "false" şeklindedir.  
  
 Aktarım bağlamasının çeşitli özelliklerinin değerleri şunlardır:  
  
 Zaman damgası: true  
  
 Güvenlik üst bilgisi düzeni: katı  
  
 Algoritma paketi: Basic256  
  
#### <a name="611-usernameovertransport"></a>6.1.1 UsernameOverTransport  
 Bu kimlik doğrulama modu ile istemci, SOAP katmanında, her zaman başlatıcıdan alıcıya gönderilen imzalı bir destekleme belirteci olarak görünen bir Kullanıcı adı belirteci ile kimlik doğrular. Hizmetin kimliği, aktarım katmanında bir X. 509.440 sertifikası kullanılarak yapılır. Kullanılan bağlama bir aktarım bağlamadır.  
  
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
  
 Yanıtıyla  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="612-certificateovertransport"></a>6.1.2 CertificateOverTransport  
 Bu kimlik doğrulama modunda, istemci, her zaman başlatıcıdan alıcıya gönderilen bir onaylama destekleme belirteci olarak SOAP katmanında görünen bir X. 509.440 sertifikası kullanarak kimlik doğrular. Hizmetin kimliği, aktarım katmanında bir X. 509.440 sertifikası kullanılarak yapılır. Kullanılan bağlama bir aktarım bağlamadır.  
  
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
  
 Yanıtıyla  
  
```xml  
<o:Security>  
  <u:Timestamp u:Id="_0">  
  ...  
  </u:Timestamp>  
</o:Security>  
```  
  
#### <a name="613-issuedtokenovertransport"></a>6.1.3 IssuedTokenOverTransport  
 Bu kimlik doğrulama modunda, istemci hizmette kimlik doğrulaması yapmaz, ancak bunun yerine güvenlik belirteci hizmeti (STS) tarafından verilen bir belirteç ve paylaşılan bir anahtar hakkında bilgi sahibi olduğunu gösterir. Verilen belirteç, her zaman başlatıcıdan alıcıya gönderilen bir onaylama destekleme belirteci olarak SOAP katmanında görünür. Hizmetin kimliği, aktarım katmanında bir X. 509.440 sertifikası kullanılarak yapılır. Bağlama bir aktarım bağlamadır.  
  
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
  
 Yanıtıyla  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="614-kerberosovertransport"></a>6.1.4 KerberosOverTransport  
 Bu kimlik doğrulama modunda istemci Kerberos bileti kullanarak hizmeti doğrular. Kerberos belirteci, SOAP katmanında bir onaylama destekleme belirteci olarak görünür. Hizmetin kimliği, aktarım katmanında bir X. 509.440 sertifikası kullanılarak yapılır. Bağlama bir aktarım bağlamadır.  
  
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
  
 Yanıtıyla  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
#### <a name="615-sspinegotiatedovertransport"></a>6.1.5 SspiNegotiatedOverTransport  
 Bu modda istemci ve sunucu kimlik doğrulamasını gerçekleştirmek için bir anlaşma protokolü kullanılır. Mümkünse, Kerberos kullanılır, aksi takdirde NTLM kullanılır. Elde edilen SCT, her zaman başlatıcıdan alıcıya gönderilen bir onaylama destekleme belirteci olarak SOAP katmanında görünür. Ayrıca hizmet, aktarım katmanında bir X. 509.440 sertifikası tarafından da doğrulanır. Kullanılan bağlama bir aktarım bağlamadır. "SPNEGO" (anlaşma), WCF 'nin WS-Trust ile SSPI ikili anlaşma protokolünü nasıl kullandığını açıklar. Bu bölümdeki güvenlik üst bilgisi örnekleri, SPNEGO el sıkışma aracılığıyla SCT oluşturulduktan sonra verilmiştir.  
  
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
  
### <a name="security-header-examples"></a>Güvenlik üst bilgisi örnekleri  
 Güvenlik bağlamı belirteci, WS-Trust Ikili anlaşması kullanılarak SPNEGO Handshake aracılığıyla kurulduktan sonra, uygulama iletilerinde aşağıdaki yapıyla güvenlik üst bilgileri bulunur.  
  
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
  
 Yanıtıyla  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
</wsse:Security>  
```  
  
### <a name="62-using-x509-certificates-for-service-authentication"></a>Hizmet kimlik doğrulaması için X. 509.440 sertifikalarını kullanma 6,2  
 Bu bölümde şu kimlik doğrulama modları açıklanmaktadır: Mulualcertificate WSS 1.0, karşılıklı CertificateDuplex, Mulualcertificate WSS 1.1, AnonymousForCertificate, UserNameForCertificate ve IssuedTokenForCertificate.  
  
#### <a name="621-mutualcertificate-wss10"></a>6.2.1 Mulualcertificate WSS 1.0  
 Bu kimlik doğrulama modunda istemci, başlatıcı belirteci olarak SOAP katmanında görünen bir X. 509.440 sertifikası kullanarak kimlik doğrular. Ayrıca, hizmet bir X. 509.440 sertifikası kullanılarak doğrulanır.  
  
 Kullanılan bağlama, aşağıdaki özellik değerleriyle asimetrik bir bağlamadır:  
  
 Başlatıcı belirteci: ekleme modu. ../IncludeToken/AlwaysToRecipient olarak ayarlanan istemcinin X. 509.440 sertifikası  
  
 Alıcı belirteci: sunucu X. 509.440 sertifikası, dahil etme modu ayarlandı. ../Includetoken/No  
  
 Belirteç koruması: false  
  
 Tüm başlık ve gövde Imzaları: doğru  
  
 Koruma sırası: SignBeforeEncrypt  
  
 Imzayı şifreleyin: doğru  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
 Yanıtıyla  
  
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
  
 Güvenlik üst bilgisi örnekleri: EncryptBeforeSign  
  
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
  
 Yanıtıyla  
  
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
  
#### <a name="622-mutualcertificateduplex"></a>6.2.2 Mulualcertificateduplex  
 Bu kimlik doğrulama modunda istemci, başlatıcı belirteci olarak SOAP katmanında görünen bir X. 509.440 sertifikası kullanarak kimlik doğrular. Ayrıca, hizmet bir X. 509.440 sertifikası kullanılarak doğrulanır.  
  
 Kullanılan bağlama, aşağıdaki özellik değerleriyle asimetrik bir bağlamadır:  
  
 Başlatıcı belirteci: Istemcinin x509 sertifikası, ekleme modu. ../IncludeToken/AlwaysToRecipient olarak ayarlandı  
  
 Alıcı belirteci: sunucunun x509 sertifikası, dahil etme modu. ../ıncludetoken/AlwaysToInitiator olarak ayarlandı  
  
 Belirteç koruması: false  
  
 Tüm başlık ve gövde Imzaları: doğru  
  
 Koruma sırası: SignBeforeEncrypt  
  
 Imzayı şifreleyin: doğru  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üst bilgisi örnekleri: EncryptBeforeSign  
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
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a>X. 509.440 hizmeti kimlik doğrulamasıyla SymmetricBinding kullanarak 6.2.3  
 "WSS10", x509 belirteçleri olan senaryolar için sınırlı destek sağlamıştır. Örneğin, yalnızca Service x509 belirtecini kullanan iletiler için imza ve şifreleme koruması sağlanması mümkün değildir. "WSS11", EncryptedKey öğesinin kullanımını simetrik bir belirteç olarak getirdi. Artık hem istek hem de yanıt iletileri koruması için hizmetin X. 509.440 sertifikası için şifrelenmiş bir geçici anahtar kullanılabilir. Aşağıdaki 6,4 bölümünde açıklanan kimlik doğrulama modları bu kalıbı kullanır.  
  
 WS-SecurityPolicy, koruma belirteci olarak Service x509 belirteci ile SymmetricBinding kullanarak bu kalıbı açıklar.  
  
 Kimlik doğrulama modları AnonymousForCertificate, UsernameForCertificate, Mulualcertificate WSS11 ve IssuedTokenForCertificate All, aşağıdaki özellik değerleriyle benzer bir SP: SymmetricBinding örneği kullanır:  
  
 Koruma belirteci: sunucunun x509 sertifikası, içerme modu olarak ayarlandı. ../Includetoken/hiçbir  
Belirteç koruması: false  
  
 Tüm başlık ve gövde Imzaları: doğru  
  
 Koruma sırası: SignBeforeEncrypt  
  
 Imzayı şifreleyin: doğru  
  
 Yukarıdaki kimlik doğrulama modları yalnızca kullandıkları destekleyici belirteçlere göre farklılık gösterir. AnonymousForCertificate içinde herhangi bir destekleme belirteci yok 1,1, çok sayıda çoklu Kullanıcı tarafından desteklenen bir destekleme belirteçleri, UserNameForCertificate, imzalı destekleyici belirteç olarak bir Kullanıcı adı belirteci içeriyor ve IssuedTokenForCertificate verilen belirteci, bir onaylama destekleme belirteci olarak içeriyor.  
  
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
 Bu kimlik doğrulama modunda, istemci anonimdir ve hizmetin kimliği bir X. 509.440 sertifikası kullanılarak yapılır. Kullanılan bağlama, 6.4.2 içinde açıklandığı gibi simetrik bağlamanın bir örneğidir.  
  
 İlke  
  
 Bağlama ayrıntıları için yukarıdaki 6.2.3 içindeki "Ilke" başlığına bakın  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
 Yanıtıyla  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üst bilgisi örnekleri: EncryptBeforeSign  
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
  
 Yanıtıyla  
  
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
 Bu kimlik doğrulama modunda istemci, SOAP katmanında imzalı destekleyici belirteç olarak görünen bir Kullanıcı adı belirteci kullanarak hizmette kimlik doğrulaması yapar. Hizmet, bir X. 509.440 sertifikası kullanarak istemcinin kimliğini doğrular. Kullanılan bağlama, koruma belirtecinin istemci tarafından oluşturulan ve hizmetin ortak anahtarıyla şifrelenen bir anahtar olduğu simetrik bir bağlamadır.  
  
 İlke  
  
 Bağlama ayrıntıları için yukarıdaki 6.2.3 içindeki "Ilke" başlığına bakın  
  
 İmzalı destekleme belirteci  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
 Yanıtıyla  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üst bilgisi örnekleri: EncryptBeforeSign  
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
  
 Yanıtıyla  
  
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
  
#### <a name="626-mutualcertificate-wss-11"></a>6.2.6 Mulualcertificate (WSS 1,1)  
 Bu kimlik doğrulama modunda istemci, SOAP katmanında bir destekleme desteği belirteci olarak görünen bir X. 509.440 sertifikası kullanarak kimlik doğrular. Ayrıca, hizmet bir X. 509.440 sertifikası kullanılarak doğrulanır. Kullanılan bağlama, koruma belirtecinin istemci tarafından oluşturulan ve hizmetin ortak anahtarıyla şifrelenen bir anahtar olduğu simetrik bir bağlamadır.  
  
 İlke  
  
 Bağlama ayrıntıları için bkz. 6.2.3 içinde Ilke  
  
 Destekleyici belirteç onaylama  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
 Yanıtıyla  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üst bilgisi örnekleri: EncryptBeforeSign  
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
  
 Yanıtıyla  
  
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
 Bu kimlik doğrulama modunda istemci, bu şekilde hizmette kimlik doğrulaması yapmaz, ancak bunun yerine STS tarafından verilen bir belirteç ve paylaşılan anahtar hakkında bilgi sahibi olduğunu gösterir. Verilen belirteç, SOAP katmanında bir onaylama destekleme belirteci olarak görünür. Hizmet, bir X. 509.440 sertifikası kullanarak istemcinin kimliğini doğrular. Kullanılan bağlama, koruma belirtecinin istemci tarafından oluşturulan ve hizmetin ortak anahtarıyla şifrelenen bir anahtar olduğu simetrik bir bağlamadır.  
  
 İlke  
  
 Bağlama ayrıntıları için yukarıdaki 6.2.3 içindeki Ilkeye bakın  
  
 Destekleyici belirteç onaylama  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
 Yanıtıyla  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üst bilgisi örnekleri: EncryptBeforeSign  
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
  
 Yanıtıyla  
  
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
  
## <a name="63-kerberos"></a>6,3 Kerberos  
 Bu kimlik doğrulama modunda istemci Kerberos bileti kullanarak hizmeti doğrular. Aynı bilet aynı zamanda sunucu kimlik doğrulaması da sağlar. Kullanılan bağlama, aşağıdaki özelliklerle simetrik bir bağlamadır;  
  
 Koruma belirteci: Kerberos bileti, ekleme modu. ../IncludeToken/Once olarak ayarlandı  
Belirteç koruması: false  
  
 Tüm başlık ve gövde Imzaları: doğru  
  
 Koruma sırası: SignBeforeEncrypt  
  
 Imzayı şifreleyin: doğru  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
 Yanıtıyla  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üst bilgisi örnekleri: EncryptBeforeSign  
 İstek  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
 Yanıtıyla  
  
```xml  
<wsse:Security>  
TBD  
</wsse:Security>  
```  
  
#### <a name="64-issuedtoken"></a>6,4 IssuedToken  
 Bu kimlik doğrulama modunda, istemci hizmette kimlik doğrulaması yapmaz, bunun yerine istemci, STS tarafından verilen bir belirteç ve paylaşılan bir anahtar hakkında bilgi sahibi olduğunu gösterir. Bu hizmet, istemci tarafından kimlik doğrulaması değil, bu nedenle, STS, paylaşılan anahtarı yalnızca hizmetin şifresini çözebilmesini sağlayan, verilen belirtecin bir parçası olarak şifreler. Kullanılan bağlama, aşağıdaki özelliklerle simetrik bağlama olarak verilmiştir;  
  
 Koruma belirteci: verilen belirteç, ekleme modu. ../IncludeToken/AlwaysToRecipient olarak ayarlandı  
Belirteç koruması: false  
  
 Tüm başlık ve gövde Imzaları: doğru  
  
 Koruma sırası: SignBeforeEncrypt  
  
 Imzayı şifreleyin: doğru  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
 Yanıtıyla  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üst bilgisi örnekleri: EncryptBeforeSign  
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
  
 Yanıtıyla  
  
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
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a>Hizmet kimlik doğrulaması için Sslanlaşmalı kullanma 6,5  
 Bu bölümde, WS-Trust (WS-T) RST/üzerinde TLS protokolünü yürüterek, anahtar değerine anlaşılan, her WS-SecureConversation (WS-SC) başına bir güvenlik bağlamı belirteci olan bir kimlik doğrulama modu grubu açıklanmaktadır. RSTR iletileri. WS-Trust kullanılarak TLS el sıkışma uygulamasının ayrıntıları TLSNEGO içinde açıklanmaktadır. Burada ileti örneklerinde, ilişkili bir güvenlik bağlamı olan SCT 'nin bir el sıkışma aracılığıyla zaten kurulduğu varsayılmaktadır.  
  
 Kullanılan bağlama, aşağıdaki özelliklerle simetrik bir bağlamadır;  
  
 Koruma belirteci: SslContextToken, ekleme modu olarak ayarlandı. ../Includetoken/hiçbir  
Belirteç koruması: false  
  
 Tüm başlık ve gövde Imzaları: doğru  
  
 Koruma sırası: SignBeforeEncrypt  
  
 Imzayı şifreleyin: doğru  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a>Sslanlaşmalı hizmet kimlik doğrulaması için 6.5.1 ilkesi  
 Bu bölümdeki tüm kimlik doğrulama modları için ilke benzerdir ve yalnızca belirli imzalı destekleyici veya onaylama belirteçlerine göre farklılık gösterir.  
  
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
  
#### <a name="652-anonymousforsslnegotiated"></a>6.5.2 Anonymousforsslanlaşmalı  
 Bu kimlik doğrulama modunda, istemci anonimdir ve hizmetin kimliği bir X. 509.440 sertifikası kullanılarak yapılır. Kullanılan bağlama, yukarıdaki 6.5.1 açıklanan simetrik bağlamanın bir örneğidir.  
  
 İlke  
  
 Bağlama ayrıntıları için yukarıdaki 6.5.1 içindeki Ilkeye bakın.  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
 Yanıtıyla  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üst bilgisi örnekleri: EncryptBeforeSign  
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
  
 Yanıtıyla  
  
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
  
#### <a name="653-usernameforsslnegotiated"></a>6.5.3 Usernameforsslanlaşmalı  
 Bu kimlik doğrulama modunda istemci, SOAP katmanında imzalı destekleyici belirteç olarak görünen bir Kullanıcı adı belirteci kullanarak kimlik doğrular. Hizmetin kimliği bir X. 509.440 sertifikası kullanılarak yapılır. Kullanılan bağlama, 6.5.1 içinde açıklandığı gibi simetrik bağlamanın bir örneğidir.  
  
 İlke  
  
 Bağlama ayrıntıları için yukarıdaki 6.5.1 bölümüne bakın  
  
 İmzalı destekleme belirteci  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
 Yanıtıyla  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üst bilgisi örnekleri: EncryptBeforeSign  
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
  
 Yanıtıyla  
  
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
  
#### <a name="654-issuedtokenforsslnegotiated"></a>6.5.4 ıssuedtokenforsslanlaşmalı  
 Bu kimlik doğrulama modunda istemci, bu şekilde hizmette kimlik doğrulaması yapmaz, ancak bunun yerine STS tarafından verilen bir belirteç ve paylaşılan anahtar hakkında bilgi sahibi olduğunu gösterir. Verilen belirteç, SOAP katmanında bir onaylama destekleme belirteci olarak görünür. Hizmetin kimliği bir X. 509.440 sertifikası kullanılarak yapılır. Kullanılan bağlama, yukarıdaki 6.5.1 açıklanan simetrik bağlamanın bir örneğidir.  
  
 İlke  
  
 Bağlama ayrıntıları için yukarıdaki 6.5.1 bölümüne bakın  
  
 Destekleyici belirteç onaylama  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
 Yanıtıyla  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üst bilgisi örnekleri: EncryptBeforeSign  
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
  
 Yanıtıyla  
  
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
  
#### <a name="655-mutualsslnegotiated"></a>6.5.5 Mulualsslanlaşmalı  
 Bu kimlik doğrulama moduyla, istemci ve hizmet X. 509.440 sertifikalarını kullanarak kimlik doğrular. Kullanılan bağlama, yukarıdaki 6.5.1 açıklanan simetrik bağlamanın bir örneğidir.  
  
 İlke  
  
 Bağlama ayrıntıları için yukarıdaki 6.5.1 bölümüne bakın  
  
 Destekleyici belirteç onaylama  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
 Yanıtıyla  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üst bilgisi örnekleri: EncryptBeforeSign  
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
  
 Yanıtıyla  
  
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
  
### <a name="66-sspinegotiated"></a>6,6 SspiNegotiated  
 Bu kimlik doğrulama modunda, istemci ve sunucu kimlik doğrulamasını gerçekleştirmek için bir anlaşma protokolü kullanılır. Mümkünse, Kerberos kullanılır, aksi takdirde NTLM kullanılır. Kullanılan bağlama, aşağıdaki özelliklerle simetrik bir bağlamadır;  
  
 Koruma belirteci: SpnegoContextToken, ekleme modu. ../ıncludetoken/AlwaysToRecipient olarak ayarlandı  
Belirteç koruması: false  
  
 Tüm başlık ve gövde Imzaları: doğru  
  
 Koruma sırası: SignBeforeEncrypt  
  
 Imzayı şifreleyin: doğru  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
 Yanıtıyla  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üst bilgisi örnekleri: EncryptBeforeSign  
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
  
 Yanıtıyla  
  
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
  
### <a name="67-secureconversation"></a>6,7 SecureConversation  
 Kullanılan bağlama, bir WS-SecureConversation (WS-SC) başına bir SCT olan koruma belirtecine sahip simetrik bir bağlamadır. SCT, bir anlaşma Protokolü kullanan simetrik bağlama olan, iç içe bir bağlamaya göre WS-Trust (WS-Trust) veya WS-SecureConversation (WS-SC) kullanılarak görüşülür. Anlaşma Protokolü, mümkünse istemci ve sunucu kimlik doğrulaması gerçekleştirmek için Kerberos kullanır. Kerberos kullanılmıyorsa, NTLM 'ye geri döner.  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üst bilgisi örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
 Yanıtıyla  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üst bilgisi örnekleri: EncryptBeforeSign  
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
  
 Yanıtıyla  
  
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
