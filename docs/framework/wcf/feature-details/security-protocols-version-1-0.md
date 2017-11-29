---
title: "Güvenlik Protokolleri sürüm 1.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee3402d2-1076-410b-a3cb-fae0372bd7af
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f40c79ad1a6eedc2b1de4dffa9de5b48aeb8e6f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="security-protocols-version-10"></a>Güvenlik Protokolleri sürüm 1.0
Web Hizmetleri Güvenlik protokolleri, tüm mevcut Kurumsal güvenlik gereksinimlerini Mesajlaşma kapak Web Hizmetleri güvenlik mekanizmaları sağlar. Bu bölümde açıklanmıştır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] sürüm 1.0 ayrıntıları (uygulanan <xref:System.ServiceModel.Channels.SecurityBindingElement>) güvenlik protokolleri aşağıdaki Web Hizmetleri için.  
  
|Belirtim/belgesi|Bağlantı|  
|-|-|  
|WSS: SOAP iletisi güvenlik 1.0|http://docs.oasis-Open.org/WSS/2004/01/oasis-200401-WSS-SOAP-Message-Security-1.0.PDF|  
|WSS: Kullanıcı belirteci profili 1.0|http://docs.oasis-Open.org/WSS/2004/01/oasis-200401-WSS-username-Token-Profile-1.0.PDF|  
|WSS: X509 profili 1.0 belirteci.|http://docs.oasis-Open.org/WSS/2004/01/oasis-200401-WSS-x509-Token-Profile-1.0.PDF|  
|WSS: SAML 1.1 belirteci profili 1.0|http://docs.oasis-Open.org/WSS/oasis-WSS-SAML-Token-Profile-1.0.PDF|  
|WSS: SOAP iletisi güvenlik 1.1|http://www.oasis-Open.org/committees/download.php/16790/WSS-V1.1-spec-OS-SOAPMessageSecurity.PDF|  
|WSS kullanıcıadı belirteci Profil 1.1|http://docs.oasis-Open.org/WSS/2004/01/oasis-200401-WSS-username-Token-Profile-1.0.PDF|  
|WSS: X.509 belirteci Profil 1.1|http://www.oasis-Open.org/committees/download.php/16785/WSS-V1.1-spec-OS-x509TokenProfile.PDF|  
|WSS: Kerberos belirteci Profil 1.1|http://www.oasis-Open.org/committees/download.php/16788/WSS-V1.1-spec-OS-KerberosTokenProfile.PDF|  
|WSS: SAML 1.1 belirteci Profil 1.1|http://www.oasis-Open.org/committees/download.php/16768/WSS-V1.1-spec-OS-SAMLTokenProfile.PDF|  
|WS-güvenli konuşma|http://msdn.microsoft.com/ws/2005/02/ws-Secure-Conversation/|  
|WS-Trust|http://msdn.microsoft.com/ws/2005/02/WS-Trust/|  
|Uygulama Not:<br /><br /> WS-Trust TLS el sıkışma için kullanma|Yayımlanacak|  
|Uygulama Not:<br /><br /> WS-Trust SPNEGO için kullanma|Yayımlanacak|  
|Uygulama Not:<br /><br /> Web Hizmetleri uç nokta başvuruları adresleme ve kimlik|Yayımlanacak|  
|WS-SecurityPolicy 1.1<br /><br /> (2005/07)|http://msdn.microsoft.com/ws/2005/07/ws-Security-Policy/<br /><br /> OASIS WS-SX teknik komitesi http://www.oasis-open.org/archives/ws-sx/200512/msg00017.html gönderilen ayrıntıyla açıklayan hata bilgilerini tarafından dayanıklıdır gibi|  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], sürüm 1, Web Hizmetleri güvenlik yapılandırması için temel olarak kullanılabilecek 17 kimlik doğrulama modları sağlar. Her iki modda gibi dağıtım gereksinimleri, ortak bir dizi için optimize edilmiştir:  
  
-   Hizmet ve istemci kimlik doğrulaması için kullanılan kimlik bilgileri.  
  
-   İleti veya taşıma güvenlik koruma mekanizması.  
  
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
  
 Bu tür kimlik doğrulama modları kullanarak uç noktaları WS-SecurityPolicy (WS-SP) kullanarak kendi güvenlik gereksinimlerini hızlı. Bu belgede güvenlik üstbilgi ve her kimlik doğrulama modu için altyapı iletileri yapısını açıklar ve ilkeleri ve iletileri örnekleri sağlar.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]uygulamalar arasında çok ileti iletişimlerini korumak için güvenli oturumlar desteği sağlamak için WS-SecureConversation yararlanır.  "Güvenli oturumlar" aşağıdaki uygulama ayrıntıları için bkz.  
  
 Kimlik doğrulama modları yanı sıra [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çoğu ileti güvenlik tabanlı kimlik doğrulama modları, örneğin geçerli ortak koruma mekanizmalarını denetleyen ayarları sağlar: İmza karşılık şifreleme işlemleri, algoritma paketleri sırasını anahtar türetme ve imza onayı.  
  
 Bu belgede, aşağıdaki ön ekleri ve ad alanları kullanılır.  
  
|önek|Ad Alanı|  
|------------|---------------|  
|s|http://www.w3.org/2003/05/SOAP-Envelope|  
|SP|http://schemas.xmlsoap.org/ws/2005/07/securityPolicy|  
|bir|http://www.w3.org/2005/08/Addressing|  
|wsse|HENÜZ BELİRLENMEDİ – OASIS WSS 1.0 URI|  
|wsse11|HENÜZ BELİRLENMEDİ – OASIS WSS 1.1 URI|  
|wsu|Henüz Belirlenmedi – OASIS WSS 1.0 yardımcı programı URI|  
|DS|Henüz Belirlenmedi – W3C XMLDSig URI|  
|WST|Henüz Belirlenmedi – WS-Trust 2005/02 URI|  
|wssc|Henüz Belirlenmedi – WS-SecureConversation 2005/02 URI|  
|wsaw|Henüz Belirlenmedi - WS adresleme İlkesi ad alanı|  
|WSP|http://schemas.xmlsoap.org/ws/2004/09/Policy|  
|mssp|http://schemas.microsoft.com/ws/2005/07/securityPolicy|  
  
## <a name="1-token-profiles"></a>1. Belirteç profilleri  
 Web Hizmetleri Güvenlik belirtimleri kimlik bilgisi güvenlik belirteçlerini temsil eder. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Aşağıdaki belirteç türlerini destekler:  
  
### <a name="11-usernametoken"></a>1.1 UsernameToken  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Aşağıdaki kısıtlamalar UsernameToken10 ve UsernameToken11 profilleriyle aşağıdaki gibidir:  
  
 UsernameToken\Password öğede R1101 PasswordType özniteliği atlanmış gerekir veya #PasswordText (varsayılan) değerine sahip.  
  
 Bir genişletilebilirlik kullanarak #PasswordDigest uygulayabilirsiniz. Yeterli güvenli parola koruma mekanizması olarak #PasswordDigest genellikle mistaken olduğunu gözlenmiştir. Ancak #PasswordDigest UsernameToken şifrelenmesi için bir alternatif olarak sunulamıyor. Birincil #PasswordDigest yeniden yürütme saldırılarına karşı koruma hedefidir. İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kimlik doğrulama modları, yeniden yürütme saldırı tehditleri azaltıldığından ileti imzalarını kullanarak.  
  
 B1102 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hiçbir zaman UsernameToken Nonce ve oluşturulan alt öğeleri yayar.  
  
 Bu alt öğeleri yeniden yürütme algılaması yardımcı olmak üzere tasarlanmıştır. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Bunun yerine ileti imzalarını kullanır.  
  
 OASIS WSS SOAP iletisi güvenlik UsernameToken Profil 1.1 (UsernameToken11) anahtar türetme parola özelliğini kullanıma sunmuştur.  
  
 B1103 UsernameToken parola için anahtar türevi değil kullanılmalıdır ve bu nedenle şifreleme işlemleri için.  
  
 Stratejinin: parolalar genellikle şifreleme işlemleri için kullanılacak zayıf olarak kabul edilir.  
  
### <a name="12-x509-token"></a>x 509 belirteci 1.2  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]bir kimlik bilgisi türü X509v3 sertifika destekler ve X509TokenProfile1.0 ve X509TokenProfile1.1 aşağıdaki kısıtlamalarla izler:  
  
 Bir X509v3 sertifika içerdiğinde BinarySecurityToken öğesindeki R1201 ValueType özniteliği değeri #X509v3 olması gerekir.  
  
 WSS belirteci profili 1.0 ve 1.&#1;X509PKIPathv1 ve #PKCS7 olarak da tanımlayın X509 türleri değeri. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Bu tür desteklemez.  
  
 R1202 SubjectKeyIdentifier (SKI) uzantısı ise bir X509 mevcut sertifika wsse:KeyIdentifier olmalıdır dış başvurular belirteci için kullanılan, ValueType ile #X509SubjectKeyIdentifier ve içeriğini base64 ile kodlanmış değeri özniteliği Sertifikanın SKI uzantısı.  
  
 SKI başvuruları yaygın olarak uygulanan ve yüksek oranda birlikte çalışabilir dış başvuru türünde olmasını kanıtlanmış.  
  
 R1203 Dış başvuru X509 için güvenlik belirteci olmamalıdır ds:X509IssuerSerial'ı kullanın.  
  
 R1204 varsa X509TokenProfile1.1, bir dış başvuru X509 güvenlik belirteci kullanmalıdır WS güvenliği 1.1 tarafından sunulan parmak izi için kullanılıyor.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]X509IssuerSerial destekler. Bununla birlikte çalışabilirlik sorunları vardır X509IssuerSerial: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir dizeyi X509IssuerSerial iki değerleri karşılaştırmak için kullanılır. Bu nedenle bir konu adı bileşenleri yeniden sıralar ve gönderir bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir sertifika için bir başvuru hizmet, bulunan olmayabilir.  
  
### <a name="13-kerberos-token"></a>1.3 Kerberos belirteci  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]aşağıdaki kısıtlamaları olan Windows kimlik doğrulaması amacıyla KerberosTokenProfile1.1 destekler:  
  
 R1301 A Kerberos belirteci gerekir taşıyan bir GSS değerini GSS_API ve Kerberos belirtimi tanımlandığı gibi Kerberos v4 AP_REQ Sarmalanan ve değer #GSS_Kerberosv5_AP_REQ ValueType özniteliğiyle olması gerekir.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Kerberos AP-REQ, olmayan bir tam AP-talep kullanan GSS Sarmalanan Bu bir güvenlik en iyi uygulamadır.  
  
### <a name="14-saml-v11-token"></a>1.4 SAML v1.1 belirteci  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]WSS SAML belirteci profillerini 1.0 ve 1.1 için SAML v1.1 belirteçleri destekler. SAML belirteci biçimleri diğer sürümleri uygulamak mümkündür.  
  
### <a name="15-security-context-token"></a>1.5 güvenlik bağlamı belirteci  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Güvenlik bağlamı belirteci (WS-SecureCoversation sunulan SCT) destekler. SCT SecureConversation içinde de kurulmuş bir güvenlik bağlamı belirtmek için kullanılan TLS ve SSPI ikili anlaşma protokolleri gibi aşağıda açıklanmıştır.  
  
## <a name="2-common-message-security-parameters"></a>2. Ortak ileti güvenlik parametreleri  
  
### <a name="21-timestamp"></a>2.1 zaman damgası  
 Zaman damgası varlığı kullanılarak denetlenir <xref:System.ServiceModel.Channels.SecurityBindingElement.IncludeTimestamp%2A> özelliği <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]her zaman wsse:TimeStamp wsse ile serileştiren: oluşturulan ve wsse: alanları süresi dolar. İmzalama kullanıldığında wsse:TimeStamp her zaman imzalanır.  
  
### <a name="22-protection-order"></a>2.2 protection sırası  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ileti koruma sırasını "Önce oturum şifrelemek" ve "Şifrelemek önce oturum" (Güvenlik İlkesi 1.1) destekler. "Şifrele önce oturum" nedenlere için önerilir: WS-güvenlik 1.1 SignatureConfirmation mekanizması kullanılır ve imza şifrelenmiş içerik üzerinde yapar sürece iletileri şifrelemek önce oturum ile korunan imza değiştirme saldırılara açık daha zor denetleme.  
  
### <a name="23-signature-protection"></a>2.3 imza koruma  
 Önce oturum şifrelemek kullanıldığında (özellikle özel belirteç zayıf anahtar malzemesi ile kullanıldığında) şifrelenmiş içeriği veya imzalama anahtarı tahmin için deneme yanılma saldırıları önlemek için imza korumak için önerilir.  
  
### <a name="24-algorithm-suite"></a>2.4 algoritması paketi  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Güvenlik İlkesi 1.1 içinde listelenen tüm algoritması paketlerini destekler.  
  
### <a name="25-key-derivation"></a>2.5 anahtar türetme  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]"Simetrik anahtarları için anahtar türetme" WS-SecureConversation açıklandığı gibi kullanır.  
  
### <a name="26-signature-confirmation"></a>2.6 imza onayı  
 İmza onayı imzaları kümesini korumak için ortadaki adam saldırılarına karşı koruma olarak olabilir.  
  
### <a name="27-security-header-layout"></a>2.7 güvenlik üstbilgi düzeni  
 Her kimlik doğrulama modu güvenlik üstbilgisi için belirli bir düzen açıklar. Güvenlik üstbilgisi içinde yarı sıralı öğelerdir. Güvenlik üstbilgi alt öğelerin sırasını tanımlamak için aşağıdaki güvenlik üstbilgi düzeni modları WS-güvenlik ilkesini tanımlar:  
  
|||  
|-|-|  
|Katı|Öğeler "kullanılmadan önce bildirmek" prensibi güvenlik ilkesi Bölüm 7.7.1 genel göre numaralı düzeni kuralları açıklanan güvenlik üstbilgi aşağıdaki eklenir.|  
|Belirsiz|Öğeleri için WSS uyan herhangi bir sırada güvenlik üstbilgisi eklenir: SOAP ileti güvenliği.|  
|LaxTimestampFirst|İlk öğe dışında güvenlik üstbilgisinde Lax bir wsse:Timestamp aynı olmalıdır|  
|LaxTimestampLast|Bir wsse:Timestamp son öğe dışında güvenlik üstbilgisinde belirsiz olarak aynı olmalıdır|  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]tüm dört modları için güvenlik üstbilgi düzenini destekler. Aşağıdaki kimlik doğrulama modları için güvenlik üstbilgi yapısı ve ileti örnekler "Strict" modu izleyin.  
  
## <a name="2-common-message-security-parameters"></a>2. Ortak ileti güvenlik parametreleri  
 Bu bölüm, istemci ve hizmet tarafından alınıp iletilerindeki güvenlik üst bilgisi yapısı gösteren örnekler yanı sıra her kimlik doğrulama modu için örnek ilkeleri sağlar.  
  
### <a name="61-transport-protection"></a>6.1 taşıma koruma  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]güvenli aktarım iletileri korumak için kullanmak beş kimlik doğrulama modları sağlar; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport ve SspiNegotiatedOverTransport.  
  
 Bu kimlik doğrulama modları SecurityPolicy içinde açıklanan aktarım bağlama kullanılarak oluşturulur. UserNameOverTransport için kimlik doğrulama modu UsernameToken imzalı destekleme belirteci ' dir. Kimlik doğrulama modları belirteç imzalı onaylama belirteç olarak görünür. Ek C.1.2 ve C.1.3, SecurityPolicy ayrıntı güvenlik üstbilgisi yerleşiminde açıklanmaktadır. Aşağıdaki örnek güvenlik üstbilgileri bir belirli kimlik doğrulama modu katı düzenini gösterir.  
  
 Tüm durumlarda belirteçleri "Anahtarlar türetilen" özelliğinin değeri "false".  
  
 Aktarım bağlama çeşitli özelliklerinin değerleri aşağıdaki gibidir:  
  
 Zaman damgası: true  
  
 Güvenlik üstbilgi Düzen: katı  
  
 Algoritma paketini: Basic256  
  
#### <a name="611-usernameovertransport"></a>6.1.1 UsernameOverTransport  
 Bu kimlik doğrulama modu ile SOAP katmanında başlatıcıdan alıcının her zaman gönderilen imzalı bir destekleme belirteci olarak görünen bir kullanıcı adı belirteci ile istemci kimliğini doğrular. Hizmet, aktarım katmanında bir X.509 sertifikası kullanılarak doğrulanır. Kullanılan bağlama aktarım bağlama ' dir.  
  
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
  
 Güvenlik üstbilgi düzeni  
  
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
 Bu kimlik doğrulama modu bir X.509 kullanarak istemcinin kimliğini doğrular SOAP katmanında başlatıcıdan alıcıya gönderilen her zaman bir onaylama destekleme belirteci olarak göründüğü sertifika. Hizmet, aktarım katmanında bir X.509 sertifikası kullanılarak doğrulanır. Kullanılan bağlama aktarım bağlama ' dir.  
  
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
  
 Güvenlik üstbilgi düzeni  
  
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
 Bu kimlik doğrulama modu ile istemci hizmeti için bu nedenle, kimlik doğrulama kullanmaz, ancak yerine bir güvenlik belirteci hizmeti (STS) tarafından verilmiş bir belirteç sunar ve paylaşılan anahtar bilgi kanıtlar. Verilen belirteç SOAP katmanında başlatıcıdan alıcıya gönderilen her zaman bir onaylama destekleme belirteci olarak görünür. Hizmet, aktarım katmanında bir X.509 sertifikası kullanılarak doğrulanır. Bağlama aktarım bağlama ' dir.  
  
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
  
 Güvenlik üstbilgi düzeni  
  
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
 Bu kimlik doğrulama modu ile bir Kerberos anahtarı kullanarak hizmete istemci kimliğini doğrular. Kerberos belirteci SOAP katmanında bir onaylama destekleme belirteci görünür. Hizmet, aktarım katmanında bir X.509 sertifikası kullanılarak doğrulanır. Bağlama aktarım bağlama ' dir.  
  
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
  
 Güvenlik üstbilgi düzeni  
  
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
 Bu modda, istemci ve sunucu kimlik doğrulaması gerçekleştirmek için anlaşması protokolü kullanılır. Kerberos Mümkünse, kullanılan aksi NTLM. Sonuçta elde edilen SCT SOAP katmanında başlatıcıdan alıcıya gönderilen her zaman bir onaylama destekleme belirteci olarak görünür. Hizmet, ayrıca aktarım katmanında bir X.509 sertifikası tarafından doğrulanır. Kullanılan bağlama aktarım bağlama ' dir. "SPNEGO" (anlaşma) açıklar nasıl [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-Trust ile SSPI ikili anlaşma protokolünü kullanır. SCT SPNEGO el sıkışma kurulduktan sonra bu bölümde güvenlik üstbilgi örnek verilmiştir.  
  
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
 WS-Trust ikili anlaşma kullanarak SPNEGO el sıkışma ile güvenlik bağlamı belirteci kurulduktan sonra uygulama iletileri güvenlik üstbilgileri şu yapıda vardır.  
  
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
  
### <a name="62-using-x509-certificates-for-service-authentication"></a>6.2 X.509 sertifikalarını hizmet kimlik doğrulaması kullanma  
 Bu bölümde aşağıdaki kimlik doğrulama modları açıklanır: MutualCertificate WSS1.0, karşılıklı CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate ve IssuedTokenForCertificate.  
  
#### <a name="621-mutualcertificate-wss10"></a>6.2.1 MutualCertificate WSS1.0  
 Bu kimlik doğrulama modu bir X.509 kullanarak istemcinin kimliğini doğrular, başlatıcı belirteç olarak SOAP katmanında göründüğü sertifika. Hizmet, ayrıca bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır.  
  
 Aşağıdaki özellik değerlerini asimetrik bir bağlamayla kullanılan bağlama şöyledir:  
  
 Başlatıcı belirteç: ekleme modu için .../IncludeToken/AlwaysToRecipient ayarlandığında istemcinin X.509 sertifikası  
  
 Alıcı belirteç: Sunucu X.509 sertifikası kullanıcının, ekleme moduyla .../IncludeToken/Never ayarlanır  
  
 Simge koruma: yanlış  
  
 Tüm üstbilgi ve gövde imzalar: True  
  
 Koruma sırasını: SignBeforeEncrypt  
  
 İmza şifrelemek: True  
  
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
 Bu kimlik doğrulama modu bir X.509 kullanarak istemcinin kimliğini doğrular, başlatıcı belirteç olarak SOAP katmanında göründüğü sertifika. Hizmet, ayrıca bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır.  
  
 Aşağıdaki özellik değerlerini asimetrik bir bağlamayla kullanılan bağlama şöyledir:  
  
 Başlatıcı belirteç: İstemcinin X509 sertifikası ekleme modu için .../IncludeToken/AlwaysToRecipient ayarlanır  
  
 Alıcı belirteç: Sunucunun X509 sertifikası ekleme modu için .../IncludeToken/AlwaysToInitiator ayarlanır  
  
 Simge koruma: yanlış  
  
 Tüm üstbilgi ve gövde imzalar: True  
  
 Koruma sırasını: SignBeforeEncrypt  
  
 İmza şifrelemek: True  
  
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
  
#### <a name="623-using-symmetricbinding-with-x509-service-authentication"></a>6.2.3 SymmetricBinding X.509 hizmet kimlik doğrulaması ile kullanma  
 "WSS10" X509 ile senaryoları için sınırlı destek sağlanan belirteçleri. Örneğin, yalnızca hizmet X509 belirteci kullanarak iletileri için imza ve şifreleme koruma sağlamak üzere hiçbir yolu yoktu. "WSS11" EncryptedKey kullanımını simetrik belirteç olarak kullanıma sunuldu. Şimdi hizmetin X.509 sertifikası şifrelenmiş geçici bir anahtar istek ve yanıt iletileri koruma için kullanılabilir. 6.4 bölümünde açıklanan kimlik doğrulama modları bu deseni kullanır.  
  
 WS-SecurityPolicy hizmetiyle SymmetricBinding kullanarak bu deseni açıklar X509 koruma belirteci olarak simge.  
  
 Kimlik doğrulama modları AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 ve IssuedTokenForCertificate tüm sp:SymmetricBinding benzer bir örneğini aşağıdaki özellik değerleriyle kullanın:  
  
 Koruma simgesi: Sunucunun X509 sertifikası ekleme modu için .../IncludeToken/Never ayarlanır  
Simge koruma: yanlış  
  
 Tüm üstbilgi ve gövde imzalar: True  
  
 Koruma sırasını: SignBeforeEncrypt  
  
 İmza şifrelemek: True  
  
 Yukarıdaki kimlik doğrulama modları yalnızca kullandıkları destek belirteçleri göre farklılık gösterir. AnonymousForCertificate destekleyen herhangi bir belirtece sahip değil ve MutualCertificate WSS 1.1 sahip istemcinin X509 bir destek belirteçleri onaylama olarak sertifika, UserNameForCertificate sahip bir kullanıcı adı belirteci imzalı destekleme belirteci olarak ve IssuedTokenForCertificate bir onaylama destekleme belirteci verilen belirteç vardır.  
  
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
 Bu kimlik doğrulama modu ile istemci anonimdir ve hizmeti bir X.509 sertifikası kullanılarak doğrulanır. Kullanılan bağlama 6.4.2 anlatıldığı gibi simetrik bağlama bir örneğidir.  
  
 İlke  
  
 Ayrıntılar bağlama için yukarıdaki 6.2.3 "ilke" konusuna bakın  
  
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
 Bu kimlik doğrulama modu ile istemci hizmeti görünen bir kullanıcı adı belirteci SOAP katmanında imzalı destekleme belirteci olarak kullanarak kimliğini doğrular. Hizmet bir X.509 sertifikası kullanarak istemcinin kimliğini doğrular. Kullanılan bağlama simetrik bağlama hizmet ortak anahtarıyla şifrelenir istemci tarafından oluşturulan bir anahtarı olan koruma belirtecine sahip olur.  
  
 İlke  
  
 Ayrıntılar bağlama için yukarıdaki 6.2.3 "ilke" konusuna bakın  
  
 Destek belirteci imzalayan  
  
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
 Bu kimlik doğrulama modu bir X.509 kullanarak istemcinin kimliğini doğrular, SOAP katmanında bir onaylama destekleme belirteci olarak göründüğü sertifika. Hizmet, ayrıca bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır. Kullanılan bağlama simetrik bağlama hizmet ortak anahtarıyla şifrelenir istemci tarafından oluşturulan bir anahtarı olan koruma belirtecine sahip olur.  
  
 İlke  
  
 İlke 6.2.3 bağlama ayrıntıları için bkz.  
  
 Belirteç destekleme onaylama  
  
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
 Bu kimlik doğrulaması ile istemci hizmeti için bu nedenle, ancak bunun yerine kimlik doğrulamasını yapmaz modu STS tarafından verilmiş bir belirteç gösterir ve paylaşılan anahtar bilgi kanıtlar. Verilen belirteç SOAP katmanında bir onaylama destekleme belirteci görünür. Hizmet bir X.509 sertifikası kullanarak istemcinin kimliğini doğrular. Kullanılan bağlama simetrik bağlama hizmet ortak anahtarıyla şifrelenir istemci tarafından oluşturulan bir anahtarı olan koruma belirtecine sahip olur.  
  
 İlke  
  
 İlke 6.2.3 Bağlama Ayrıntılar için bkz.  
  
 Belirteç destekleme onaylama  
  
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
 Bu kimlik doğrulama modu ile bir Kerberos anahtarı kullanarak hizmete istemci kimliğini doğrular. Bu aynı anahtar Ayrıca sunucu kimlik doğrulaması sağlar. Kullanılan bağlama simetrik bağlama aşağıdaki özelliklere sahip olur;  
  
 Koruma simgesi: Kerberos bileti için .../IncludeToken/Once ekleme modu ayarlanır  
Simge koruma: yanlış  
  
 Tüm üstbilgi ve gövde imzalar: True  
  
 Koruma sırasını: SignBeforeEncrypt  
  
 İmza şifrelemek: True  
  
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
 İstemci hizmete kimlik doğrulama kullanmaz, bu kimlik doğrulama modu ile bu nedenle yerine istemci bir STS tarafından verilmiş bir belirteç gösterir ve paylaşılan anahtar bilgi kanıtlar. Hizmet istemcisi için bu nedenle kimlik doğrulaması yapılamıyor, bunun yerine STS şifreler paylaşılan anahtar verilen belirteç bir parçası olarak sağlayacak şekilde yalnızca hizmeti anahtarı şifresini çözebilir. Aşağıdaki özelliklerle simetrik bağlama kullanılan bağlama gibidir;  
  
 Koruma: Belirteci belirteç, ekleme modu için .../IncludeToken/AlwaysToRecipient ayarlanır  
Simge koruma: yanlış  
  
 Tüm üstbilgi ve gövde imzalar: True  
  
 Koruma sırasını: SignBeforeEncrypt  
  
 İmza şifrelemek: True  
  
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
  
### <a name="65-using-sslnegotiated-for-service-authentication"></a>6.5 SslNegotiated hizmet kimlik doğrulaması kullanma  
 Bu bölümde bir grup bir güvenlik bağlamı belirteci başına WS-anahtar değeri anlaşılan WS-Trust (WS-T) RST TLS protokolünü yürüterek SecureConversation (WS-SC) olan koruma belirteci ile bir simetrik bağlamayı kullanan kimlik doğrulama modları açıklanır / RSTR iletileri. WS-Trust kullanarak TLS el sıkışma uygulama ayrıntılarını TLSNEGO içinde açıklanmıştır. Burada ileti örneklerde SCT ilişkili güvenlik bağlamına sahip bir el sıkışması önceden oluşturulmuş varsayacağız.  
  
 Kullanılan bağlama simetrik bağlama aşağıdaki özelliklere sahip olur;  
  
 Koruma simgesi: SslContextToken, .../IncludeToken/Never için ekleme modu ayarlanır  
Simge koruma: yanlış  
  
 Tüm üstbilgi ve gövde imzalar: True  
  
 Koruma sırasını: SignBeforeEncrypt  
  
 İmza şifrelemek: True  
  
#### <a name="651-policy-for-sslnegotiated-service-authentication"></a>6.5.1 SslNegotiated hizmeti kimlik doğrulama için İlkesi  
 Bu bölümdeki tüm kimlik doğrulama modu için ilke benzerdir ve yalnızca özel imzalı destekleme veya kullanılan belirteçleri onaylama tarafından farklıdır.  
  
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
 Bu kimlik doğrulama modu ile istemci anonimdir ve hizmeti bir X.509 sertifikası kullanılarak doğrulanır. Kullanılan bağlama 6.5.1 yukarıda açıklandığı gibi simetrik bağlama bir örneğidir.  
  
 İlke  
  
 6.5.1 Bağlama Ayrıntılar için bkz.  
  
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
 Bu kimlik doğrulaması ile görüntülenen bir kullanıcı adı belirteci SOAP katmanında imzalı destekleme belirteci olarak kullanan istemci modu kimliğini doğrular. Hizmet, bir X.509 sertifikası kullanılarak doğrulanır. Kullanılan bağlama 6.5.1 anlatıldığı gibi simetrik bağlama bir örneğidir.  
  
 İlke  
  
 Ayrıntılar bağlama için yukarıdaki 6.5.1 bölümüne bakın  
  
 Destek belirteci imzalayan  
  
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
 Bu kimlik doğrulaması ile istemci hizmeti için bu nedenle, ancak bunun yerine kimlik doğrulamasını yapmaz modu bir STS tarafından verilmiş bir belirteç gösterir ve paylaşılan anahtar bilgi kanıtlar. Verilen belirteç SOAP katmanında bir onaylama destekleme belirteci görünür. Hizmet, bir X.509 sertifikası kullanılarak doğrulanır. Kullanılan bağlama 6.5.1 yukarıda açıklandığı gibi simetrik bağlama bir örneğidir.  
  
 İlke  
  
 Ayrıntılar bağlama için yukarıdaki 6.5.1 bölümüne bakın  
  
 Belirteç destekleme onaylama  
  
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
 Bu kimlik doğrulama modu ile istemci ve hizmet X.509 sertifikalarını kullanarak kimlik doğrulaması. Kullanılan bağlama 6.5.1 yukarıda açıklandığı gibi simetrik bağlama bir örneğidir.  
  
 İlke  
  
 Ayrıntılar bağlama için yukarıdaki 6.5.1 bölümüne bakın  
  
 Belirteç destekleme onaylama  
  
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
 Bu kimlik doğrulama modu ile istemci ve sunucu kimlik doğrulaması gerçekleştirmek için anlaşması protokolü kullanılır. Kerberos Mümkünse, kullanılan aksi NTLM. Kullanılan bağlama simetrik bağlama aşağıdaki özelliklere sahip olur;  
  
 Koruma simgesi: SpnegoContextToken, .../IncludeToken/AlwaysToRecipient için ekleme modu ayarlanır  
Simge koruma: yanlış  
  
 Tüm üstbilgi ve gövde imzalar: True  
  
 Koruma sırasını: SignBeforeEncrypt  
  
 İmza şifrelemek: True  
  
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
 Kullanılan bağlama simetrik bağlama SCT WS-SecureConversation (WS-SC) başına olan koruma belirtecine sahip olur. SCT göre kendisini anlaşma protokolünü kullanan bir simetrik bağlama olan iç içe bir bağlama, WS-Trust (WS-Trust) veya WS-SecureConversation (WS-SC) kullanılarak belirlenir. Anlaşma Protokolü, mümkün olduğunda istemci ve sunucu kimlik doğrulaması gerçekleştirmek için Kerberos kullanır. Kerberos kullanılamaz, NTLM olarak geri döner.  
  
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
