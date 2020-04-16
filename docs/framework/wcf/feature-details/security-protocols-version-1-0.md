---
title: Güvenlik Protokolleri sürüm 1.0
ms.date: 03/30/2017
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
ms.openlocfilehash: 0b86d870350d8728134cd2b42bbeb232183535bc
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463799"
---
# <a name="security-protocols-version-10"></a>Güvenlik Protokolleri sürüm 1.0
Web Hizmetleri Güvenlik Protokolleri, varolan tüm kurumsal ileti güvenlik gereksinimlerini kapsayan Web hizmetleri güvenlik mekanizmaları sağlar. Bu bölümde, aşağıdaki Web hizmetleri güvenlik protokolleri için Windows Communication <xref:System.ServiceModel.Channels.SecurityBindingElement>Foundation (WCF) sürüm 1.0 ayrıntıları (uygulandığında) açıklanmaktadır.  
  
|Belirtim/Belge|Bağlantı|  
|-|-|  
|WSS: SOAP İleti Güvenliği 1.0|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf>|
|WSS: Kullanıcı Adı Belirteç Profili 1.0|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|WSS: X509 Jeton Profili 1.0|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf>|
|WSS: SAML 1.1 Belirteç Profili 1.0|<https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf>|
|WSS: SOAP İleti Güvenliği 1.1|<https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf>|
|WSS Kullanıcı Adı Belirteç Profili 1.1|<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf>|
|WSS: X.509 Jeton Profili 1.1|<https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf>|
|WSS: Kerberos Token Profil 1.1|<https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf>|
|WSS: SAML 1.1 Belirteç Profili 1.1|<https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf>|
|WS-Güvenli Konuşma|<https://specs.xmlsoap.org/ws/2005/02/sc/WS-SecureConversation.pdf>|
|WS-Güven|<https://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf>|
|Uygulama Notu:<br /><br /> TLS El Sıkışması için WS-Trust kullanma|Yayınlanacak|  
|Uygulama Notu:<br /><br /> SPNEGO için WS-Trust'ı kullanma|Yayınlanacak|  
|Uygulama Notu:<br /><br /> Uç Nokta Referansları Ve Kimliğini Ele Veren Web Hizmetleri|Yayınlanacak|  
|WS-SecurityPolicy 1.1<br /><br /> (2005/07)|<https://specs.xmlsoap.org/ws/2005/07/securitypolicy/ws-securitypolicy.pdf><br /><br /> olarak OASIS WS-SX Teknik Komitesi'ne sunulan [errata](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html) tarafından değiştirildi |  
  
 Sürüm 1 olan WCF, Web hizmetleri güvenlik yapılandırması için temel olarak kullanılabilecek 17 kimlik doğrulama modu sağlar. Her mod, şu gibi yaygın bir dağıtım gereksinimi kümesi için en iyi duruma getirilmiştir:  
  
- İstemci ve hizmetin kimliğini doğrulamak için kullanılan kimlik bilgileri.  
  
- İleti veya taşıma güvenlik koruma mekanizmaları.  
  
- İleti alışverişi desenleri.  
  
|Kimlik Doğrulaması Modu|İstemci Kimlik Doğrulaması|Sunucu Kimlik Doğrulama|Mod|  
|-------------------------|---------------------------|---------------------------|----------|  
|Kullanıcı Adı OverTransport|Kullanıcı adı/şifre|X509|Aktarım|  
|SertifikaOverTransport|X509|X509|Aktarım|  
|KerberosOverTransport|Windows|X509|Aktarım|  
|IssuedTokenOverTransport|Federe|X509|Aktarım|  
|SspiNegotiatedOverTransport|Windows Sspi Müzakere|Windows Sspi Müzakere|Aktarım|  
|Anonim ForCertificate|Hiçbiri|X509|İleti|  
|Kullanıcı AdıForCertificate|Kullanıcı adı/şifre|X509|İleti|  
|MutualCertificate|X509|X509|İleti|  
|MutualCertificateDuplex|X509|X509|İleti|  
|VerilenTokenForCertificate|Federe|X509|İleti|  
|Kerberos|Windows|Windows|İleti|  
|IssuedToken|Federe|Federe|İleti|  
|SspiNegotiated|Windows Sspi Müzakere|Windows Sspi Müzakere|İleti|  
|AnonimForSslNegotiated|Hiçbiri|X509, TLS-Nego|İleti|  
|Kullanıcı AdıForSslNegotiated|Kullanıcı adı/şifre|X509, TLS-Nego|İleti|  
|MutualSslNegotiated|X509|X509, TLS-Nego|İleti|  
|IssuedTokenForSslNegotiated|Federe|X509, TLS-Nego|İleti|  
  
 Bu tür kimlik doğrulama modlarını kullanan uç noktalar, WS-SecurityPolicy (WS-SP) kullanarak güvenlik gereksinimlerini ifade edebilir. Bu belge, her kimlik doğrulama modu için güvenlik üstbilgive altyapı iletilerinin yapısını açıklar ve ilkeler ve iletiörnekleri sağlar.  
  
 WCF, uygulamalar arasındaki çoklu ileti alışverişini korumak için güvenli oturum desteği sağlamak için WS-SecureConversation'dan yararlanır.  Uygulama ayrıntıları için aşağıdaki "Güvenli Oturumlar" adlı bilgiye bakın.  
  
 Kimlik doğrulama modlarına ek olarak WCF, çoğu ileti güvenliği tabanlı kimlik doğrulama moduna uygulanan yaygın koruma mekanizmalarını denetlemek için ayarlar sağlar( örneğin: imza ve şifreleme işlemleri ne sırayla, algoritma paketleri, anahtar türetme ve imza onayı.  
  
 Bu belgede aşağıdaki önekler ve ad alanları kullanılır.  
  
|Ön ek|Ad Alanı|  
|------------|---------------|  
|s|<http://www.w3.org/2003/05/soap-envelope/>|
|sp|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/>|
|a|<http://www.w3.org/2005/08/addressing>|  
|wsse|TBD - OASIS WSS 1.0 URI|  
|wsse11|TBD - OASIS WSS 1.1 URI|  
|Wsu|TBD - OASIS WSS 1.0 Yardımcı Program URI|  
|Ds|TBD - W3C XMLDSig URI|  
|Wst|TBD - WS-Trust 2005/02 URI|  
|wssc|TBD - WS-SecureConversation 2005/02 URI|  
|testere|TBD - WS adresleme ilkesi ad alanı|  
|wsp|<http://schemas.xmlsoap.org/ws/2004/09/policy>|  
|mssp|<http://schemas.xmlsoap.org/ws/2005/07/securitypolicy>|
  
## <a name="1-token-profiles"></a>1. Belirteç Profilleri  
 Web Hizmetleri Güvenlik belirtimleri, kimlik bilgileri güvenlik belirteçleri olarak temsil eder. WCF aşağıdaki belirteç türlerini destekler:  
  
### <a name="11-usernametoken"></a>1.1 Kullanıcı AdıToken  
 WCF aşağıdaki kısıtlamalar ile UsernameToken10 ve UsernameToken11 profilleri izler:  
  
 R1101 PasswordType özniteliği Üzerinde UsernameToken\Password öğesi ya atlanmalıdır ya da değeri #PasswordText (varsayılan).  
  
 Bir genişletilebilirlik kullanarak #PasswordDigest uygulayabilirsiniz. #PasswordDigest'nin genellikle yeterince güvenli bir parola koruma mekanizması olarak karıştırıldığı gözlenmiştir. Ancak #PasswordDigest, Kullanıcı Adı Token'in şifrelemesinin yerini tutamaz. #PasswordDigest birincil amacı tekrar saldırılarına karşı korumadır. WCF kimlik doğrulama modlarında, ileti imzaları kullanılarak yeniden oynatma saldırı tehditleri azaltılır.  
  
 B1102 WCF, Kullanıcı adı Token'in Nonce ve Oluşturulan alt öğelerini asla yayar.  
  
 Bu alt öğeler, yeniden algılamaya yardımcı olmak için tasarlanmıştır. WCF bunun yerine ileti imzalarını kullanır.  
  
 OASIS WSS SOAP Message Security Kullanıcı AdıToken Profil 1.1 (UsernameToken11) şifre özelliğinden anahtar türetme tanıttı.  
  
 B1103 Kullanıcı AdıToken şifresi anahtar türetme ve bu nedenle şifreleme işlemleri için kullanılmamalıdır.  
  
 Mantığı: parolalar genellikle şifreleme işlemleri için kullanılmak üzere çok zayıf olarak kabul edilir.  
  
### <a name="12-x509-token"></a>1.2 X509 Jeton  
 WCF, X509v3 sertifikalarını kimlik bilgisi türü olarak destekler ve X509TokenProfile1.0 ve X509TokenProfile1.1'i aşağıdaki kısıtlamalarla izler:  
  
 R1201 BinarySecurityToken öğesindeki ValueType özniteliği, X509v3 sertifikası içerdiğinde değer #X509v3 olmalıdır.  
  
 WSS X509 Belirteç Profili 1.0 ve 1.1 de #X509PKIPathv1 tanımlar ve #PKCS7 değer türleri olarak tanımlar. WCF bu türleri desteklemez.  
  
 R1202 X509 sertifikasında SubjectKeyIdentifier (SKI) uzantısı varsa, wsSE:KeyIdentifier belirteci için dış başvurular için, ValueType özniteliği #X509SubjectKeyIdentifier ve içeriği sertifikanın SKI uzantısının temel 64 kodlanmış değeri ile birlikte kullanılmalıdır.  
  
 İsKİ referansları yaygın olarak uygulanmakta ve son derece birlikte çalışabilir bir dış referans türü olduğu kanıtlanmıştır.  
  
 R1203 X509 Güvenlik Jetonuna harici bir başvuru ds:X509IssuerSerial kullanmamalıdır.  
  
 R1204 X509TokenProfile1.1 kullanılıyorsa, X509 Güvenlik Belirteci'ne harici bir başvuru WS-Security 1.1 tarafından tanıtılan parmak izini kullanmalıdır.  
  
 WCF X509IssuerSerial destekler. Ancak X509IssuerSerial ile birlikte çalışabilirlik sorunları vardır: WCF X509IssuerSerial iki değerleri karşılaştırmak için bir dize kullanır. Bu nedenle, bir kişi Konu Adı'nın bileşenlerini yeniden sipariş ederse ve bir WCF hizmetine bir sertifikareferansı gönderirse, bu belge bulunamayabilir.  
  
### <a name="13-kerberos-token"></a>1.3 Kerberos Jetonu  
 WCF, Windows kimlik doğrulaması amacıyla Aşağıdaki kısıtlamalarla KerberosTokenProfile1.1'i destekler:  
  
 R1301 A Kerberos Belirteci, GSS_API ve Kerberos belirtiminde tanımlandığı gibi GSS sarılmış Kerberos v4 AP_REQ değerini taşımalı ve #GSS_Kerberosv5_AP_REQ değerine sahip ValueType özelliğine sahip olmalıdır.  
  
 WCF GSS sarılmış Kerberos AP-REQ değil, çıplak BIR AP-REQ kullanır. Bu bir güvenlik en iyi uygulamadır.  
  
### <a name="14-saml-v11-token"></a>1.4 SAML v1.1 Belirteci  
 WCF, SAML v1.1 belirteçleri için WSS SAML Token profilleri 1.0 ve 1.1'i destekler. SAML belirteç biçimlerinin diğer sürümlerini uygulamak mümkündür.  
  
### <a name="15-security-context-token"></a>1.5 Güvenlik Bağlam ı belirteç  
 WCF, WS-SecureConversation'da tanıtılan Güvenlik Bağlamı Belirteci'ni (SCT) destekler. SCT, SecureConversation'da kurulan bir güvenlik bağlamını ve aşağıda açıklanan ikili müzakere protokollerini TLS ve SSPI'yi temsil etmek için kullanılır.  
  
## <a name="2-common-message-security-parameters"></a>2. Ortak İleti Güvenlik Parametreleri  
  
### <a name="21-timestamp"></a>2.1 Zaman Damgası  
 Zaman damgası varlığı <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfın özelliği kullanılarak denetlenir. WCF her zaman wsse:TimeStamp ile wsse:Created ve wsse:Expires alanları ile serihale eder. WsSe:TimeStamp imzalandığında her zaman imzalanır.  
  
### <a name="22-protection-order"></a>2.2 Koruma Emri  
 WCF, "Şifrelemeden Önce İmzala" ve "İmzadan Önce Şifreleme" ileti koruma emrini destekler (Güvenlik İlkesi 1.1). "Şifrelemeden Önce İmzala" gibi nedenlerle önerilir: WS-Security 1.1 SignatureConfirmation mekanizması kullanılmadığı ve şifreli içeriğe yönelik imza denetimi zorlaştırmadığı sürece İmzadan Önce Şifrele ile korunan iletiler imza ikame saldırılarına açıktır.  
  
### <a name="23-signature-protection"></a>2.3 İmza Koruması  
 İşaretten Önce Şifrele kullanıldığında, şifrelenmiş içeriği veya imzalama anahtarını tahmin etmek için kaba kuvvet saldırılarını önlemek için imzanın korunması önerilir (özellikle zayıf anahtar malzemesiyle özel bir belirteç kullanıldığında).  
  
### <a name="24-algorithm-suite"></a>2.4 Algoritma Paketi  
 WCF, Security Policy 1.1'de listelenen tüm algoritma paketlerini destekler.  
  
### <a name="25-key-derivation"></a>2.5 Anahtar Türetme  
 WCF, WS-SecureConversation'da açıklandığı gibi "Simetrik tuşlar için Anahtar Türetme"yi kullanır.  
  
### <a name="26-signature-confirmation"></a>2.6 İmza Onayı  
 İmza onayı, imza kümesini korumak için aracı insan saldırılarına karşı koruma olarak olabilir.  
  
### <a name="27-security-header-layout"></a>2.7 Güvenlik Üstbilgi Düzeni  
 Her kimlik doğrulama modu, güvenlik üstbilgisi için belirli bir düzeni açıklar. Güvenlik üstbilgisindeki öğeler yarı sıralıdır. WS-Security İlkesi, güvenlik üstbilgi alt öğelerinin sırasını tanımlamak için aşağıdaki güvenlik üstbilgi düzeni modlarını tanımlar:  
  
|||  
|-|-|  
|Katı|Öğeler, "kullanmadan önce bildir" ilkesine göre Güvenlik Politikası bölüm 7.7.1'de açıklanan numaralı düzen kurallarını izleyerek güvenlik üstbilgisine eklenir.|  
|Lax|Öğeler WSS: SOAP Message Security uygun herhangi bir sırada güvenlik üstbilgi eklenir.|  
|LaxTimestampİlk|Güvenlik üstbilgisindeki ilk öğenin wsse olması dışında Lax ile aynıdır:Zaman damgası|  
|LaxTimestampLast|Güvenlik üstbilgisindeki son öğenin bir wsse olması dışında gevşek olarak aynıdır:Zaman damgası|  
  
 WCF, güvenlik üstbilgi düzeni için dört modu da destekler. Aşağıdaki kimlik doğrulama modları için güvenlik üstbilgi yapısı ve ileti örnekleri "Katı" modunu izleyin.  
  
## <a name="2-common-message-security-parameters"></a>2. Ortak İleti Güvenlik Parametreleri  
 Bu bölümde, istemci ve hizmet tarafından değiştirilen iletilerde güvenlik üstbilgi yapısını gösteren örneklerle birlikte her kimlik doğrulama modu için örnek ilkeler sağlar.  
  
### <a name="61-transport-protection"></a>6.1 Taşıma Koruması  
 WCF, iletileri korumak için güvenli aktarım kullanan beş kimlik doğrulama modu sağlar; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport ve SspiNegotiatedOverTransport.  
  
 Bu kimlik doğrulama modları SecurityPolicy'de açıklanan aktarım bağlama kullanılarak oluşturulur. UserNameOverTransport kimlik doğrulama modu için UsernameToken imzalı destekleyici bir belirteçtir. Diğer kimlik doğrulama modları için belirteç imzalı bir onaylama belirteci olarak görünür. SecurityPolicy'nin Ek C.1.2 ve C.1.3 güvenlik üstbilgi düzenini ayrıntılı olarak açıklar. Aşağıdaki örnek güvenlik üstbilgisi, belirli bir kimlik doğrulama modu için Sıkı düzeni gösterir.  
  
 Tüm durumlarda belirteçler için "Türemiş Anahtarlar" özelliğinin değeri "yanlış"tır.  
  
 Aktarım bağlamanın çeşitli özelliklerinin değerleri aşağıdaki gibidir:  
  
 Zaman damgası: doğru  
  
 Güvenlik Üstbilgi Düzeni: Katı  
  
 Algoritma Paketi: Basic256  
  
#### <a name="611-usernameovertransport"></a>6.1.1 Kullanıcı AdıOverTransport  
 Bu kimlik doğrulama moduyla istemci, SOAP katmanında her zaman başlatıcıdan alıcıya gönderilen imzalı destekleyici bir belirteç olarak görünen bir Kullanıcı Adı Belirteci ile kimlik doğrulaması verir. Hizmet, aktarım katmanında x.509 sertifikası kullanılarak doğrulanır. Kullanılan bağlama bir aktarım bağlayıcısidır.  
  
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
  
 Güvenlik Üstbilgi Düzeni  
  
 İstek  
  
```xml  
<wsse:Security>  
  <wsu:Timestamp u:Id="_0">  
  ...  
  </wsu:Timestamp>  
  <wsse:UsernameToken>  
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
  
#### <a name="612-certificateovertransport"></a>6.1.2 Taşıma Fazla Taşıma Sertifikası  
 Bu kimlik doğrulama modu ile istemci, SOAP katmanında her zaman başlatıcıdan alıcıya gönderilen destekleyici bir belirteç olarak görünen bir X.509 sertifikası kullanarak kimlik doğrulaması verir. Hizmet, aktarım katmanında x.509 sertifikası kullanılarak doğrulanır. Kullanılan bağlama bir aktarım bağlayıcısidır.  
  
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
  
 Güvenlik Üstbilgi Düzeni  
  
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
 Bu kimlik doğrulama modu ile istemci hizmete doğrudoğrulama yapmaz, ancak daha çok bir Güvenlik Belirteç Hizmeti (STS) tarafından verilen bir belirteç sunar ve paylaşılan bir anahtar bilgisini kanıtlıyor. Verilen belirteç, SABUN katmanında her zaman başlatıcıdan alıcıya gönderilen destekleyici bir belirteç olarak görünür. Hizmet, aktarım katmanında x.509 sertifikası kullanılarak doğrulanır. Bağlama bir aktarım bağlayıcısidır.  
  
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
  
 Güvenlik Üstbilgi Düzeni  
  
 İstek  
  
```xml  
<wsse:Security s:mustUnderstand="1" >  
  <wsu:Timestamp>  
  ...  
  </wsu:Timestamp>  
  <saml:Assertion>  
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
 Bu kimlik doğrulama modu ile istemci bir Kerberos bileti kullanarak hizmete kimlik doğrular. Kerberos belirteci SOAP katmanında destekleyici bir belirteç olarak görünür. Hizmet, aktarım katmanında x.509 sertifikası kullanılarak doğrulanır. Bağlama bir aktarım bağlayıcısidır.  
  
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
  
 Güvenlik Üstbilgi Düzeni  
  
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
 Bu modda istemci ve sunucu kimlik doğrulaması gerçekleştirmek için bir anlaşma protokolü kullanılır. Kerberos mümkünse kullanılır, aksi takdirde NTLM. Elde edilen Ct, SOAP katmanında her zaman başlatıcıdan alıcıya gönderilen destekleyici bir belirteç olarak görünür. Hizmet ayrıca taşıma katmanında X.509 sertifikası ile doğrulanır. Kullanılan bağlama bir aktarım bağlayıcısidır. "SPNEGO" (müzakere) WCF WS-Trust ile SSPI ikili müzakere protokolü nasıl kullandığını açıklar. Bu bölümdeki güvenlik üstbilgi örnekleri, SPNEGO el sıkışması yoluyla SCT kurulduktan sonra dır.  
  
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
  
### <a name="security-header-examples"></a>Güvenlik Üstbilgi Örnekleri  
 Güvenlik Bağlam ıken WS-Trust İkili Müzakere kullanarak SPNEGO el sıkışma yoluyla kurulduktan sonra, uygulama iletileri aşağıdaki yapıya sahip güvenlik başlıkları var.  
  
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
  
### <a name="62-using-x509-certificates-for-service-authentication"></a>6.2 Hizmet Kimlik Doğrulaması için X.509 Sertifikalarının Kullanılması  
 Bu bölümde aşağıdaki kimlik doğrulama modları açıklanmaktadır: MutualCertificate WSS1.0, Mutual CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate ve IssuedTokenForCertificate.  
  
#### <a name="621-mutualcertificate-wss10"></a>6.2.1 Karşılıklı Sertifika WSS1.0  
 Bu kimlik doğrulama modu ile istemci, SOAP katmanında başlatıcı belirteci olarak görünen bir X.509 sertifikası kullanarak kimlik doğrulaması verir. Hizmet ayrıca X.509 sertifikası kullanılarak da doğrulanır.  
  
 Kullanılan bağlama, aşağıdaki özellik değerleriyle asimetrik bir bağlamadır:  
  
 Başlatıcı Belirteci: istemcinin X.509 sertifikası, dahil etme modu .../IncludeToken/AlwaysToRecipient olarak ayarlanmış  
  
 Alıcı Belirteci: Sunucunun X.509 Sertifikası, dahil etme modu ile ayarlanır .../IncludeToken/Never  
  
 Belirteç Koruması: False  
  
 Tüm Üstbilgi Ve Gövde İmzaları: Doğru  
  
 Koruma Emri: SignBeforeEncrypt  
  
 İmzayı Şifrele: Doğru  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
 Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign  
  
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
 Bu kimlik doğrulama modu ile istemci, SOAP katmanında başlatıcı belirteci olarak görünen bir X.509 sertifikası kullanarak kimlik doğrulaması verir. Hizmet ayrıca X.509 sertifikası kullanılarak da doğrulanır.  
  
 Kullanılan bağlama, aşağıdaki özellik değerleriyle asimetrik bir bağlamadır:  
  
 Başlatıcı Belirteci: Müşterinin X509 Sertifikası, ekleme modu .../IncludeToken/AlwaysToRecipient olarak ayarlanır  
  
 Alıcı Belirteci: Sunucunun X509 Sertifikası, ekleme modu .../IncludeToken/AlwaysToInitiator olarak ayarlanır  
  
 Belirteç Koruması: False  
  
 Tüm Üstbilgi Ve Gövde İmzaları: Doğru  
  
 Koruma Emri: SignBeforeEncrypt  
  
 İmzayı Şifrele: Doğru  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature  
 İstek ve Yanıt  
  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign  
 İstek ve Yanıt  
  
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
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a>6.2.3 X.509 Hizmet Kimlik Doğrulaması ile Simetrik Bağlama Kullanma  
 "WSS10", X509 belirteçleri olan senaryolar için sınırlı destek sağladı. Örneğin, yalnızca Hizmet X509 belirteci kullanarak iletiler için imza ve şifreleme koruması sağlamanın bir yolu yoktu. "WSS11" şifreli anahtar kullanımını simetrik bir belirteç olarak tanıttı. Şimdi, hizmetin X.509 sertifikası için şifrelenmiş geçici bir anahtar hem istek hem de yanıt iletileri koruması için kullanılabilir. Aşağıdaki bölüm 6.4'te açıklanan kimlik doğrulama modları bu deseni kullanır.  
  
 WS-SecurityPolicy bu deseni koruma belirteci olarak X509 hizmeti ile Simetribağlayıcı kullanarak tanımlar.  
  
 Kimlik doğrulama modları AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 ve IssuedTokenForCertificate'un tümü benzer bir sp örneğini kullanır:Aşağıdaki özellik değerleriyle Simetrik Bağlama:  
  
 Koruma Belirteci: Sunucunun X509 Sertifikası, ekleme modu .../IncludeToken/Never olarak ayarlanır  
Belirteç Koruması: False  
  
 Tüm Üstbilgi Ve Gövde İmzaları: Doğru  
  
 Koruma Emri: SignBeforeEncrypt  
  
 İmzayı Şifrele: Doğru  
  
 Yukarıdaki kimlik doğrulama modları yalnızca kullandıkları destekleyici belirteçlere göre farklılık gösterir. AnonymousForCertificate herhangi bir destekleyici belirteçleri yok, MutualCertificate WSS 1.1 destekleyici belirteçleri destekleyici bir istemcinin X509 sertifikasına sahiptir, UserNameForCertificate imzalı bir destekleyici belirteç olarak bir Kullanıcı Adı Belirteci vardır ve IssuedTokenForCertificate destekleyici belirteci olarak verilen belirteç vardır.  
  
 İlke  
  
 Simetrik Bağlama  
  
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
  
#### <a name="624-anonymousforcertificate"></a>6.2.4 Anonim ForCertificate  
 Bu kimlik doğrulama modu ile istemci anonimdir ve hizmet x.509 sertifikası kullanılarak kimlik doğrulanır. Kullanılan bağlama 6.4.2'de açıklandığı gibi simetrik bağlama örneğidir.  
  
 İlke  
  
 Bağlayıcı ayrıntılar için yukarıdaki 6.2.3'teki "İlke"  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign  
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
  
#### <a name="625-usernameforcertificate"></a>6.2.5 Kullanıcı AdıForCertificate  
 Bu kimlik doğrulama modu ile istemci, SOAP katmanında imzalı destekleyici belirteç olarak görünen bir Kullanıcı Adı Belirteci kullanarak hizmete kimlik doğrular. Hizmet, X.509 sertifikası kullanarak istemciye kimlik doğrular. Kullanılan bağlama, istemci tarafından oluşturulan ve hizmetin ortak anahtarıyla şifrelenmiş bir anahtar olan koruma belirteci ile simetrik bir bağlamadır.  
  
 İlke  
  
 Bağlayıcı ayrıntılar için yukarıdaki 6.2.3'teki "İlke"  
  
 İmzalı Destekleyici Belirteç  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign  
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
  
#### <a name="626-mutualcertificate-wss-11"></a>6.2.6 Karşılıklı Sertifika (WSS 1.1)  
 Bu kimlik doğrulama modu ile istemci, SOAP katmanında destekleyici bir belirteç olarak görünen bir X.509 sertifikası kullanarak kimlik doğrulaması verir. Hizmet ayrıca X.509 sertifikası kullanılarak da doğrulanır. Kullanılan bağlama, istemci tarafından oluşturulan ve hizmetin ortak anahtarıyla şifrelenmiş bir anahtar olan koruma belirteci ile simetrik bir bağlamadır.  
  
 İlke  
  
 Bağlayıcı ayrıntılar için 6.2.3'teki Politikaya bakın  
  
 Destekleyici Belirteç  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign  
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
  
#### <a name="627-issuedtokenforcertificate"></a>6.2.7 Verilen TokenForCertificate  
 Bu kimlik doğrulama modu ile istemci hizmete doğrudoğrulama yapmaz, ancak bunun yerine bir STS tarafından verilen bir belirteç sunar ve paylaşılan bir anahtar bilgisini kanıtlıyor. Verilen belirteç, SOAP katmanında destekleyici bir belirteç olarak görünür. Hizmet, X.509 sertifikası kullanarak istemciye kimlik doğrular. Kullanılan bağlama, istemci tarafından oluşturulan ve hizmetin ortak anahtarıyla şifrelenmiş bir anahtar olan koruma belirteci ile simetrik bir bağlamadır.  
  
 İlke  
  
 Bağlayıcı ayrıntılar için yukarıdaki 6.2.3'teki Politikaya bakın  
  
 Destekleyici Belirteç  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign  
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
 Bu kimlik doğrulama modu ile istemci bir Kerberos bileti kullanarak hizmete kimlik doğrular. Aynı bilet aynı zamanda sunucu kimlik doğrulaması sağlar. Kullanılan bağlama aşağıdaki özelliklere sahip simetrik bir bağlamadır;  
  
 Koruma Belirteci: Kerberos Bilet, dahil etme modu ayarlanır .../IncludeToken/Once  
Belirteç Koruması: False  
  
 Tüm Üstbilgi Ve Gövde İmzaları: Doğru  
  
 Koruma Emri: SignBeforeEncrypt  
  
 İmzayı Şifrele: Doğru  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign  
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
  
#### <a name="64-issuedtoken"></a>6.4 İhraç Edilen Token  
 Bu kimlik doğrulama modu ile istemci hizmete kimlik doğrulamaz, bu nedenle, istemci bir STS tarafından verilen bir belirteç sunar ve paylaşılan bir anahtar hakkındaki bilgileri kanıtlar. Hizmet istemciye doğrulanmaz, bunun yerine STS paylaşılan anahtarı verilen belirtecinin bir parçası olarak şifreler, bu şekilde yalnızca hizmet anahtarın şifresini çözebilir. Kullanılan bağlama aşağıdaki özelliklere sahip simetrik bağlama olarak;  
  
 Koruma Belirteci: Verilen Belirteç, dahil etme modu .../IncludeToken/AlwaysToRecipient olarak ayarlanır  
Belirteç Koruması: False  
  
 Tüm Üstbilgi Ve Gövde İmzaları: Doğru  
  
 Koruma Emri: SignBeforeEncrypt  
  
 İmzayı Şifrele: Doğru  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign  
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
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a>6.5 Hizmet Kimlik Doğrulaması için SslNegotiated'i Kullanma  
 Bu bölümde, WS-Trust (WS-T) RST/RSTR iletileri üzerinden TLS protokolü yürütülerek anahtar değeri görüşülen WS-SecureConversation (WS-SC) başına güvenlik bağlamı belirteci olan koruma belirteci ile simetrik bir bağlama kullanan bir kimlik doğrulama modu grubu açıklanmaktadır. WS-Trust kullanılarak TLS el sıkışma uygulamasının ayrıntıları TLSNEGO'da açıklanmıştır. Burada ileti örneklerinde, ilişkili bir güvenlik bağlamına sahip ÖST'nin el sıkışma yoluyla zaten kurulduğunu varsayacağız.  
  
 Kullanılan bağlama aşağıdaki özelliklere sahip simetrik bir bağlamadır;  
  
 Koruma Belirteci: SslContextToken, ekleme modu ayarlanır .../IncludeToken/Never  
Belirteç Koruması: False  
  
 Tüm Üstbilgi Ve Gövde İmzaları: Doğru  
  
 Koruma Emri: SignBeforeEncrypt  
  
 İmzayı Şifrele: Doğru  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a>6.5.1 SslNegotiated hizmet kimlik doğrulaması için politika  
 Bu bölümdeki tüm kimlik doğrulama modları için ilke benzerdir ve yalnızca kullanılan belirli imzalı destekleyici veya destekleyici belirteçlerle farklılık gösterir.  
  
```xml  
<wsp:Policy wsu:Id='SslNegotiated_policy' >  
  <wsp:ExactlyOne>  
    <wsp:All>  
      <sp:SymmetricBinding>  
        <wsp:Policy>  
          <sp:ProtectionToken>  
            <wsp:Policy>  
              <mssp:SslContextToken sp:IncludeToken='http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient'>  
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
  
#### <a name="652-anonymousforsslnegotiated"></a>6.5.2 AnonimForSslNegotiated  
 Bu kimlik doğrulama modu ile istemci anonimdir ve hizmet x.509 sertifikası kullanılarak kimlik doğrulanır. Kullanılan bağlama yukarıdaki 6.5.1'de açıklandığı gibi simetrik bağlama örneğidir.  
  
 İlke  
  
 Bağlayıcı ayrıntılar için yukarıdaki 6.5.1'deki Politika'ya bakın.  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign  
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
  
#### <a name="653-usernameforsslnegotiated"></a>6.5.3 Kullanıcı AdıForSslNegotiated  
 Bu kimlik doğrulama modu ile istemci, SOAP katmanında imzalı destekleyici belirteç olarak görünen bir Kullanıcı Adı Belirteci kullanılarak kimlik doğrulanır. Hizmet, X.509 sertifikası kullanılarak kimlik doğrulanır. Kullanılan bağlama 6.5.1'de açıklandığı gibi simetrik bağlama örneğidir.  
  
 İlke  
  
 Bağlayıcı ayrıntılar için yukarıdaki bölüm 6.5.1'e bakın  
  
 İmzalı Destekleyici Belirteç  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign  
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
  
#### <a name="654-issuedtokenforsslnegotiated"></a>6.5.4 VerilenTokenForSslNegotiated  
 Bu kimlik doğrulama modu ile istemci hizmete doğrudoğrulama yapmaz, ancak bunun yerine bir STS tarafından verilen bir belirteç sunar ve paylaşılan bir anahtar bilgisini kanıtlıyor. Verilen belirteç, SOAP katmanında destekleyici bir belirteç olarak görünür. Hizmet, X.509 sertifikası kullanılarak kimlik doğrulanır. Kullanılan bağlama yukarıdaki 6.5.1'de açıklandığı gibi simetrik bağlama örneğidir.  
  
 İlke  
  
 Bağlayıcı ayrıntılar için yukarıdaki bölüm 6.5.1'e bakın  
  
 Destekleyici Belirteç  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign  
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
  
#### <a name="655-mutualsslnegotiated"></a>6.5.5 KarşılıklıSslNegotiated  
 Bu kimlik doğrulama modu ile istemci ve hizmet X.509 sertifikalarını kullanarak kimlik doğrulaması yapın. Kullanılan bağlama yukarıdaki 6.5.1'de açıklandığı gibi simetrik bağlama örneğidir.  
  
 İlke  
  
 Bağlayıcı ayrıntılar için yukarıdaki bölüm 6.5.1'e bakın  
  
 Destekleyici Belirteç  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign  
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
 Bu kimlik doğrulama modu ile istemci ve sunucu kimlik doğrulaması gerçekleştirmek için bir anlaşma protokolü kullanılır. Kerberos mümkünse kullanılır, aksi takdirde NTLM. Kullanılan bağlama aşağıdaki özelliklere sahip simetrik bir bağlamadır;  
  
 Koruma Belirteci: SpnegoContextToken, ekleme modu ayarlanır .../IncludeToken/AlwaysToRecipient  
Belirteç Koruması: False  
  
 Tüm Üstbilgi Ve Gövde İmzaları: Doğru  
  
 Koruma Emri: SignBeforeEncrypt  
  
 İmzayı Şifrele: Doğru  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign  
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
  
### <a name="67-secureconversation"></a>6.7 Güvenli Konuşma  
 Kullanılan bağlama, koruma belirteci ws-SecureConversation (WS-SC) başına Bir SCT olan simetrik bir bağlamadır. SCT, kendisi bir müzakere protokolü kullanan simetrik bir bağlayıcı olan iç içe bir bağlama ya göre WS-Trust (WS-Trust) veya WS-SecureConversation (WS-SC) kullanılarak görüşülür. Müzakere protokolü mümkünse istemci ve sunucu kimlik doğrulaması gerçekleştirmek için Kerberos kullanır. Kerberos kullanılamıyorsa, NTLM'ye geri döner.  
  
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
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik Üstbilgi Örnekleri: SignBeforeEncrypt, EncryptSignature  
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
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik Üstbilgi Örnekleri: EncryptBeforeSign  
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
