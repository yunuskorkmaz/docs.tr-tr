---
title: "Güvenlik Protokolleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security [WCF], protocols
ms.assetid: 57ffcbea-807c-4e43-a41c-44b3db8ed2af
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 25a6e333b81b337ad0c34de0c0ae097a5cff5601
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="security-protocols"></a>Güvenlik Protokolleri
Web Hizmetleri Güvenlik protokolleri, tüm mevcut Kurumsal güvenlik gereksinimlerini Mesajlaşma kapak Web Hizmetleri güvenlik mekanizmaları sağlar. Bu bölümde açıklanmıştır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ayrıntıları (uygulanan <xref:System.ServiceModel.Channels.SecurityBindingElement>) güvenlik protokolleri aşağıdaki Web Hizmetleri için.  
  
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
|WS-güvenli konuşma 1.3|http://docs.oasis-Open.org/ws-SX/ws-SecureConversation/200512/ws-SecureConversation-1.3-OS.PDF|  
|WS-Trust 1.3|http://docs.oasis-Open.org/ws-SX/WS-Trust/200512/WS-Trust-1.3-OS.PDF|  
|Uygulama Not:<br /><br /> WS-Trust TLS el sıkışma için kullanma|Yayımlanacak|  
|Uygulama Not:<br /><br /> WS-Trust SPNEGO için kullanma|Yayımlanacak|  
|Uygulama Not:<br /><br /> Web Hizmetleri uç nokta başvuruları adresleme ve kimlik|Yayımlanacak|  
|WS-SecurityPolicy 1.2 (2007/04)|http://www.oasis-Open.org/committees/download.php/23821/ws-securityPolicy-1.2-spec-cs.PDF|  
  
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
|SP|http://docs.oasis-Open.org/ws-SX/ws-securityPolicy/200702|  
|bir|http://www.w3.org/2005/08/Addressing|  
|wsse|HENÜZ BELİRLENMEDİ – OASIS WSS 1.0 URI|  
|wsse11|HENÜZ BELİRLENMEDİ – OASIS WSS 1.1 URI|  
|wsu|http://docs.oasis-Open.org/WSS/2004/01/oasis-200401-WSS-wssecurity-Utility-1.0.xsd|  
|DS|Henüz Belirlenmedi – W3C XMLDSig URI|  
|WST|Henüz Belirlenmedi – WS-Trust 2005/02 URI|  
|wssc|Henüz Belirlenmedi – WS-SecureConversation 2005/02 URI|  
|wsaw|http://www.w3.org/2006/05/Addressing/WSDL|  
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
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ileti koruma sırasını "Önce oturum şifrelemek" ve "Şifrelemek önce oturum" (Güvenlik İlkesi 1.2) destekler. "Şifrele önce oturum" nedenlere için önerilir: WS-güvenlik 1.1 SignatureConfirmation mekanizması kullanılır ve imza şifrelenmiş içerik üzerinde yapar sürece iletileri şifrelemek önce oturum ile korunan imza değiştirme saldırılara açık daha zor denetleme.  
  
### <a name="23-signature-protection"></a>2.3 imza koruma  
 Önce oturum şifrelemek kullanıldığında (özellikle özel belirteç zayıf anahtar malzemesi ile kullanıldığında) şifrelenmiş içeriği veya imzalama anahtarı tahmin için deneme yanılma saldırıları önlemek için imza korumak için önerilir.  
  
### <a name="24-algorithm-suite"></a>2.4 algoritması paketi  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Güvenlik İlkesi 1.2 içinde listelenen tüm algoritması paketlerini destekler.  
  
### <a name="25-key-derivation"></a>2.5 anahtar türetme  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]"Simetrik anahtarları için anahtar türetme" WS-SecureConversation açıklandığı gibi kullanır.  
  
### <a name="26-signature-confirmation"></a>2.6 imza onayı  
 İmza onayı olarak ortadaki adam saldırılarına karşı koruma imzaları kümesini korumak için kullanılabilir.  
  
### <a name="27-security-header-layout"></a>2.7 güvenlik üstbilgi düzeni  
 Her kimlik doğrulama modu güvenlik üstbilgisi için belirli bir düzen açıklar. Güvenlik üstbilgisi içinde yarı sıralı öğelerdir. Güvenlik üstbilgi alt öğelerin sırasını tanımlamak için aşağıdaki güvenlik üstbilgi düzeni modları WS-güvenlik ilkesini tanımlar:  
  
|||  
|-|-|  
|Katı|Öğeler "kullanılmadan önce bildirmek" prensibi güvenlik ilkesi Bölüm 7.7.1 genel göre numaralı düzeni kuralları açıklanan güvenlik üstbilgi aşağıdaki eklenir.|  
|Belirsiz|Öğeleri için WSS uyan herhangi bir sırada güvenlik üstbilgisi eklenir: SOAP ileti güvenliği.|  
|LaxTimestampFirst|İlk öğe dışında güvenlik üstbilgisinde Lax bir wsse:Timestamp aynı olmalıdır|  
|LaxTimestampLast|Bir wsse:Timestamp son öğe dışında güvenlik üstbilgisinde belirsiz olarak aynı olmalıdır|  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]tüm dört modları için güvenlik üstbilgi düzenini destekler. Aşağıdaki kimlik doğrulama modları için güvenlik üstbilgi yapısı ve ileti örnekler "Strict" modu izleyin.  
  
## <a name="3-common-message-security-parameters"></a>3. Ortak ileti güvenlik parametreleri  
 Bu bölüm, istemci ve hizmet tarafından alınıp iletilerindeki güvenlik üst bilgisi yapısı gösteren örnekler yanı sıra her kimlik doğrulama modu için örnek ilkeleri sağlar.  
  
### <a name="31-transport-protection"></a>3.1 taşıma koruma  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]güvenli aktarım iletileri korumak için kullanmak beş kimlik doğrulama modları sağlar; UserNameOverTransport, CertificateOverTransport, KerberosOverTransport, IssuedTokenOverTransport ve SspiNegotiatedOverTransport.  
  
 Bu kimlik doğrulama modları SecurityPolicy içinde açıklanan aktarım bağlama kullanılarak oluşturulur. UserNameOverTransport için kimlik doğrulama modu UsernameToken imzalı destekleme belirteci ' dir. Kimlik doğrulama modları belirteç imzalı onaylama belirteç olarak görünür. Ek C.1.2 ve C.1.3, SecurityPolicy ayrıntı güvenlik üstbilgisi yerleşiminde açıklanmaktadır. Aşağıdaki örnek güvenlik üstbilgileri bir belirli kimlik doğrulama modu katı düzenini gösterir.  
  
 Tüm durumlarda belirteçleri "Anahtarlar türetilen" özelliğinin değeri "false".  
  
 Aktarım bağlama çeşitli özelliklerinin değerleri aşağıdaki gibidir:  
  
 Zaman damgası: true  
  
 Güvenlik üstbilgi Düzen: katı  
  
 Algoritma paketini: Basic256  
  
#### <a name="311-usernameovertransport"></a>3.1.1 UsernameOverTransport  
 Bu kimlik doğrulama modu ile SOAP katmanında başlatıcıdan alıcının her zaman gönderilen imzalı bir destekleme belirteci olarak görünen bir kullanıcı adı belirteci ile istemci kimliğini doğrular. Hizmet, aktarım katmanında bir X.509 sertifikası kullanılarak doğrulanır. Kullanılan bağlama aktarım bağlama ' dir.  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="UserNameOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 Güvenlik üstbilgi düzeni  
  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><o:UsernameToken u:Id="uuid-b96fbb3a-e646-4403-9473-2e5ffc733ff8-1"> ... </o:UsernameToken></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
#### <a name="312-certificateovertransport"></a>3.1.2 CertificateOverTransport  
 Bu kimlik doğrulama modu bir X.509 kullanarak istemcinin kimliğini doğrular SOAP katmanında başlatıcıdan alıcıya gönderilen her zaman bir onaylama destekleme belirteci olarak göründüğü sertifika. Hizmet, aktarım katmanında bir X.509 sertifikası kullanılarak doğrulanır. Kullanılan bağlama aktarım bağlama ' dir. CertificateOverTransport yalnızca SOAP gövdesi SOAP üstbilgileri imzalar. TransportWithMessageCredentials güvenlik modu tarafından kullanılan kimlik doğrulama modu budur. Kimlik doğrulama ileti kimlik bilgilerini kullanarak yapıldığından yalnızca SOAP üstbilgileri imzalanmıştır.  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="CertificateOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token><sp:SignedParts><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 Güvenlik üstbilgi düzeni  
  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
#### <a name="313-issuedtokenovertransport"></a>3.1.3 IssuedTokenOverTransport  
 Bu kimlik doğrulama modu ile istemci hizmeti için bu nedenle, kimlik doğrulama kullanmaz, ancak yerine bir güvenlik belirteci hizmeti (STS) tarafından verilmiş bir belirteç sunar ve paylaşılan anahtar bilgi kanıtlar. Verilen belirteç SOAP katmanında başlatıcıdan alıcıya gönderilen her zaman bir onaylama destekleme belirteci olarak görünür. Hizmet, aktarım katmanında bir X.509 sertifikası kullanılarak doğrulanır. Bağlama aktarım bağlama ' dir.  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken><sp:SignedParts><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy  
```  
  
 Güvenlik üstbilgi düzeni  
  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-67692bb6-85b7-4299-8587-3ce60086b0d2-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-fab7e1b2-8dc4-412b-bda9-b95a4f836815-16" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-fab7e1b2-8dc4-412b-bda9-b95a4f836815-21"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
#### <a name="314-kerberosovertransport"></a>3.1.4 KerberosOverTransport  
 Bu kimlik doğrulama modu ile bir Kerberos anahtarı kullanarak hizmete istemci kimliğini doğrular. Kerberos belirteci SOAP katmanında bir onaylama destekleme belirteci görünür. Hizmet, aktarım katmanında bir X.509 sertifikası kullanılarak doğrulanır. Bağlama aktarım bağlama ' dir.  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="KerberosOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic128/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:KerberosToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Once"><wsp:Policy><sp:WssGssKerberosV5ApReqToken11/></wsp:Policy></sp:KerberosToken><sp:SignedParts><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 Güvenlik üstbilgi düzeni  
  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
#### <a name="315-sspinegotiatedovertransport"></a>3.1.5 SspiNegotiatedOverTransport  
 Bu modda, istemci ve sunucu kimlik doğrulaması gerçekleştirmek için anlaşması protokolü kullanılır. Kerberos Mümkünse, kullanılan aksi NTLM. Sonuçta elde edilen SCT SOAP katmanında başlatıcıdan alıcıya gönderilen her zaman bir onaylama destekleme belirteci olarak görünür. Hizmet, ayrıca aktarım katmanında bir X.509 sertifikası tarafından doğrulanır. Kullanılan bağlama aktarım bağlama ' dir. "SPNEGO" (anlaşma) açıklar nasıl [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-Trust ile SSPI ikili anlaşma protokolünü kullanır. SCT SPNEGO el sıkışma kurulduktan sonra bu bölümde güvenlik üstbilgi örnek verilmiştir.  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="SspiNegotiatedOverTransport_policy"><wsp:ExactlyOne><wsp:All><sp:TransportBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:TransportToken><wsp:Policy><sp:HttpsToken/></wsp:Policy></sp:TransportToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/></wsp:Policy></sp:TransportBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></sp:SpnegoContextToken><sp:SignedParts><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples"></a>Güvenlik üstbilgi örnekler  
 WS-Trust ikili anlaşma kullanarak SPNEGO el sıkışma ile güvenlik bağlamı belirteci kurulduktan sonra uygulama iletileri güvenlik üstbilgileri şu yapıda vardır.  
  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-9a29d087-5dae-4d40-bf86-5746d9d30eca-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="_0"> ... </u:Timestamp></o:Security>  
```  
  
### <a name="32-using-x509-certificates-for-service-authentication"></a>3.2 X.509 sertifikalarını hizmet kimlik doğrulaması kullanma  
 Bu bölümde aşağıdaki kimlik doğrulama modları açıklanır: MutualCertificate WSS1.0, karşılıklı CertificateDuplex, MutualCertificate WSS1.1, AnonymousForCertificate, UserNameForCertificate ve IssuedTokenForCertificate.  
  
#### <a name="321-mutualcertificate-wss10"></a>3.2.1 MutualCertificate WSS1.0  
 Bu kimlik doğrulama modu bir X.509 kullanarak istemcinin kimliğini doğrular, başlatıcı belirteç olarak SOAP katmanında göründüğü sertifika. Hizmet, ayrıca bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır. SOAP üstbilgileri ve SOAP gövdesi oturum açtınız. Simetrik anahtar oluşturulur ve aktarım sertifikayla alıcı için şifrelenir.  
  
 Aşağıdaki özellik değerlerini asimetrik bir bağlamayla kullanılan bağlama şöyledir:  
  
 Başlatıcı belirteç: ekleme modu için .../IncludeToken/AlwaysToRecipient ayarlandığında istemcinin X.509 sertifikası  
  
 Alıcı belirteç: Sunucu X.509 sertifikası kullanıcının, ekleme moduyla .../IncludeToken/Never ayarlanır  
  
 Simge koruma: yanlış  
  
 Tüm üstbilgi ve gövde imzalar: True  
  
 Koruma sırasını: SignBeforeEncrypt  
  
 İmza şifrelemek: True  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss10 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/></wsp:Policy></sp:Wss10><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-39cb393e-9da8-4d5d-b273-540ef614569b-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><e:EncryptedData Id="_7" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"> <u:Timestamp u:Id="uuid-3d742930-70d3-4d7e-aa0a-8721128dc115-8"> ... </u:Timestamp><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><e:EncryptedData Id="_5" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss10 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/></wsp:Policy></sp:Wss10><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-73da3e21-abff-4294-a910-e75303d280cc-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-02f276b6-804f-480d-99e9-2e90fc76ab27-3"> ... </u:Timestamp><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="322-mutualcertificateduplex"></a>3.2.2 MutualCertificateDuplex  
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
<wsp:Policy wsu:Id="MutualCertificateDuplex_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToInitiator"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><cdp:CompositeDuplex xmlns:cdp="http://schemas.microsoft.com/net/2006/06/duplex"/><ow:OneWay xmlns:ow="http://schemas.microsoft.com/ws/2005/05/routing/policy"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek ve yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-4dec3da4-b572-4654-ba4d-4a2f84a87510-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><e:EncryptedData Id="_7" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificateDuplex_policy"><wsp:ExactlyOne><wsp:All><sp:AsymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:InitiatorToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:InitiatorToken><sp:RecipientToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToInitiator"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:RecipientToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:AsymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><cdp:CompositeDuplex xmlns:cdp="http://schemas.microsoft.com/net/2006/06/duplex"/><ow:OneWay xmlns:ow="http://schemas.microsoft.com/ws/2005/05/routing/policy"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek ve yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-b0e23feb-cd2d-4dc1-bad9-284bc45f3be3-1"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><e:EncryptedKey Id="_0" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="323-using-symmetricbinding-with-x509-service-authentication"></a>3.2.3 SymmetricBinding X.509 hizmet kimlik doğrulaması ile kullanma  
 "WSS10" X509 ile senaryoları için sınırlı destek sağlanan belirteçleri. Örneğin, yalnızca hizmet X509 belirteci kullanarak iletileri için imza ve şifreleme koruma sağlamak üzere hiçbir yolu yoktu. "WSS11" EncryptedKey kullanımını simetrik belirteç olarak kullanıma sunuldu. Şimdi hizmetin X.509 sertifikası şifrelenmiş geçici bir anahtar istek ve yanıt iletileri koruma için kullanılabilir. 3.4 bölümünde açıklanan kimlik doğrulama modları bu deseni kullanır.  
  
 WS-SecurityPolicy hizmetiyle SymmetricBinding kullanarak bu deseni açıklar X509 koruma belirteci olarak simge.  
  
 Kimlik doğrulama modları AnonymousForCertificate, UsernameForCertificate, MutualCertificate WSS11 ve IssuedTokenForCertificate tüm sp:SymmetricBinding benzer bir örneğini aşağıdaki özellik değerleriyle kullanın:  
  
 Koruma simgesi: Sunucunun X509 sertifikası ekleme modu için .../IncludeToken/Never ayarlanır  
Simge koruma: yanlış  
  
 Tüm üstbilgi ve gövde imzalar: True  
  
 Koruma sırasını: SignBeforeEncrypt  
  
 İmza şifrelemek: True  
  
 Yukarıdaki kimlik doğrulama modları yalnızca kullandıkları destek belirteçleri göre farklılık gösterir. AnonymousForCertificate destekleyen herhangi bir belirtece sahip değil ve MutualCertificate WSS 1.1 sahip istemcinin X509 bir destek belirteçleri onaylama olarak sertifika, UserNameForCertificate sahip bir kullanıcı adı belirteci imzalı destekleme belirteci olarak ve IssuedTokenForCertificate bir onaylama destekleme belirteci verilen belirteç vardır.  
  
#### <a name="324-anonymousforcertificate"></a>3.2.4 AnonymousForCertificate  
 Bu kimlik doğrulama modu ile istemci anonimdir ve hizmeti bir X.509 sertifikası kullanılarak doğrulanır. Kullanılan bağlama 3.4.2 anlatıldığı gibi simetrik bağlama bir örneğidir.  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="AnonymousforCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-4de2d2a1-6266-4a02-93e6-242a1ac2aeb3-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-4de2d2a1-6266-4a02-93e6-242a1ac2aeb3-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-b06cb481-3176-4c56-af35-c38252bb6c78-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_2" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_7" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="AnonymousforCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-562aac68-8cdd-45d5-bc03-df662e6ed048-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-562aac68-8cdd-45d5-bc03-df662e6ed048-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-15b48260-23da-424d-8dc4-8f4e150fb8cf-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><k:SignatureConfirmation u:Id="_2" Value="ALF+QNGmWn2k3LpWEDIzSBgTkvo=" xmlns:k="http://docs.oasis-open.org/wss/oasis-wss-wssecurity-secext-1.1.xsd"></k:SignatureConfirmation><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="325-usernameforcertificate"></a>3.2.5 UserNameForCertificate  
 Bu kimlik doğrulama modu ile istemci hizmeti görünen bir kullanıcı adı belirteci SOAP katmanında imzalı destekleme belirteci olarak kullanarak kimliğini doğrular. Hizmet bir X.509 sertifikası kullanarak istemcinin kimliğini doğrular. Kullanılan bağlama simetrik bağlama hizmet ortak anahtarıyla şifrelenir istemci tarafından oluşturulan bir anahtarı olan koruma belirtecine sahip olur.  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="UserNameForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><http:BasicAuthentication xmlns:http="http://schemas.microsoft.com/ws/06/2004/policy/http"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-27196139-acb9-410f-a2c6-51d20d24278b-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-27196139-acb9-410f-a2c6-51d20d24278b-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-681226f7-126a-4806-b732-fcca097cd7a8-5"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="UserNameForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><http:BasicAuthentication xmlns:http="http://schemas.microsoft.com/ws/06/2004/policy/http"/><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-8276d8b7-74a0-4257-b8a5-e25350e7c2d4-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-8276d8b7-74a0-4257-b8a5-e25350e7c2d4-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-8a7ad353-f071-49dc-90dd-5ad2e9abd40a-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="326-mutualcertificate-wss-11"></a>3.2.6 MutualCertificate (WSS 1.1)  
 Bu kimlik doğrulama modu bir X.509 kullanarak istemcinin kimliğini doğrular, SOAP katmanında bir onaylama destekleme belirteci olarak göründüğü sertifika. Hizmet, ayrıca bir X.509 sertifikası kullanılarak kimlik doğrulaması yapılır. Kullanılan bağlama simetrik bağlama hizmet ortak anahtarıyla şifrelenir istemci tarafından oluşturulan bir anahtarı olan koruma belirtecine sahip olur.  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-75305d4e-f54f-4e36-9de9-45b6d2053c80-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-75305d4e-f54f-4e36-9de9-45b6d2053c80-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_2" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><o:BinarySecurityToken> ...</o:BinarySecurityToken><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_10" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-8c73fa91-f95b-40ff-b088-48118e6fadcf-5"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_3" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_10" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="MutualCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-0b940a9e-606f-43b9-b05d-a162043529bc-2"> ... </u:Timestamp><e:EncryptedKey Id="uuid-0b940a9e-606f-43b9-b05d-a162043529bc-1" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedKey><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><o:BinarySecurityToken> ... </o:BinarySecurityToken><Signature Id="_2" xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-67dacc31-4a50-4866-b673-ccc03e156337-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><k:SignatureConfirmation u:Id="_2" Value="mYyksUQKkK27Fd6hmgOiqFwvudk=" xmlns:k="http://docs.oasis-open.org/wss/oasis-wss-wssecurity-secext-1.1.xsd"></k:SignatureConfirmation><k:SignatureConfirmation u:Id="_3" Value="SreOZ4Rr2BcXjFQFvgN55ERypI/1/86hdWThE5lav0eYIxF1OCzQgZF+y7cQ82t+g3CRnLbE3c52DqMpY/HXlrdMct3m3rnpDH+fqdhNY4fE+M2v4zUMFR7uxDKWcEm9zZpmUvJCDfJRfKRaKjy5cTbccRKqSxw7HAqOYnqibA4=" xmlns:k="http://docs.oasis-open.org/wss/oasis-wss-wssecurity-secext-1.1.xsd"></k:SignatureConfirmation><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="327-issuedtokenforcertificate"></a>3.2.7 IssuedTokenForCertificate  
 Bu kimlik doğrulaması ile istemci hizmeti için bu nedenle, ancak bunun yerine kimlik doğrulamasını yapmaz modu STS tarafından verilmiş bir belirteç gösterir ve paylaşılan anahtar bilgi kanıtlar. Verilen belirteç SOAP katmanında bir onaylama destekleme belirteci görünür. Hizmet bir X.509 sertifikası kullanarak istemcinin kimliğini doğrular. Kullanılan bağlama simetrik bağlama hizmet ortak anahtarıyla şifrelenir istemci tarafından oluşturulan bir anahtarı olan koruma belirtecine sahip olur.  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-1d2c03e6-0b69-4483-903a-6ef9b9d286ed-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-3f0f57fa-046d-40c0-919f-d0d7aa640b9f-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-3f0f57fa-046d-40c0-919f-d0d7aa640b9f-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForCertificate_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:X509Token sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Never"><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireThumbprintReference/><sp:WssX509V3Token10/></wsp:Policy></sp:X509Token></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-de1c51aa-2ecc-4e70-b6bd-9dca58331fa7-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-96c5e80a-9b87-4c6f-af77-752ca65cf607-16" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-96c5e80a-9b87-4c6f-af77-752ca65cf607-21"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
## <a name="33-kerberos"></a>3.3 Kerberos  
 Bu kimlik doğrulama modu ile bir Kerberos anahtarı kullanarak hizmete istemci kimliğini doğrular. Bu aynı anahtar Ayrıca sunucu kimlik doğrulaması sağlar. Kullanılan bağlama simetrik bağlama aşağıdaki özelliklere sahip olur;  
  
 Koruma simgesi: Kerberos bileti için .../IncludeToken/Once ekleme modu ayarlanır  
Simge koruma: yanlış  
  
 Tüm üstbilgi ve gövde imzalar: True  
  
 Koruma sırasını: SignBeforeEncrypt  
  
 İmza şifrelemek: True  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="Kerberos_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:KerberosToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Once"><wsp:Policy><sp:RequireDerivedKeys/><sp:WssGssKerberosV5ApReqToken11/></wsp:Policy></sp:KerberosToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic128/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e8f6dc3b-407d-4387-bd33-97aedfd8bf13-2"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-7b03568e-66ae-49da-82ee-5d12d372876e-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="Kerberos_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:KerberosToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/Once"><wsp:Policy><sp:RequireDerivedKeys/><sp:WssGssKerberosV5ApReqToken11/></wsp:Policy></sp:KerberosToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic128/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d29247f0-f220-4e81-9a8d-a15f5ac31072-2"> ... </u:Timestamp><o:BinarySecurityToken> ... </o:BinarySecurityToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-9025b930-4f15-42fe-8e78-35d3a3480177-2"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="34-issuedtoken"></a>3.4 IssuedToken  
 İstemci hizmete kimlik doğrulama kullanmaz, bu kimlik doğrulama modu ile bu nedenle yerine istemci bir STS tarafından verilmiş bir belirteç gösterir ve paylaşılan anahtar bilgi kanıtlar. Hizmet istemcisi için bu nedenle kimlik doğrulaması yapılamıyor, bunun yerine STS şifreler paylaşılan anahtar verilen belirteç bir parçası olarak sağlayacak şekilde yalnızca hizmeti anahtarı şifresini çözebilir. Aşağıdaki özelliklerle simetrik bağlama kullanılan bağlama gibidir;  
  
 Koruma: Belirteci belirteç, ekleme modu için .../IncludeToken/AlwaysToRecipient ayarlanır  
Simge koruma: yanlış  
  
 Tüm üstbilgi ve gövde imzalar: True  
  
 Koruma sırasını: SignBeforeEncrypt  
  
 İmza şifrelemek: True  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="IssuedToken_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-61ce3989-bc38-4d67-8262-6232c9d49a26-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-7e2d2617-1c28-465a-be30-de4a78cfc0e2-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-7e2d2617-1c28-465a-be30-de4a78cfc0e2-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>    
```  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="IssuedToken_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ...  </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-1dc8bdef-4202-4e08-8a5e-ab94da579dec-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-7e004f51-63a3-4069-9b03-6a1a311a3181-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-7e004f51-63a3-4069-9b03-6a1a311a3181-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> </c:DerivedKeyToken> ... <c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
### <a name="35-using-sslnegotiated-for-service-authentication"></a>3.5 SslNegotiated hizmet kimlik doğrulaması kullanma  
 Bu bölümde bir grup bir güvenlik bağlamı belirteci başına WS-anahtar değeri anlaşılan WS-Trust (WS-T) RST TLS protokolünü yürüterek SecureConversation (WS-SC) olan koruma belirteci ile bir simetrik bağlamayı kullanan kimlik doğrulama modları açıklanır / RSTR iletileri. WS-Trust kullanarak TLS el sıkışma uygulama ayrıntılarını TLSNEGO içinde açıklanmıştır. Burada ileti örneklerde SCT ilişkili güvenlik bağlamına sahip bir el sıkışması önceden oluşturulmuş varsayacağız.  
  
 Kullanılan bağlama simetrik bağlama aşağıdaki özelliklere sahip olur;  
  
 Koruma simgesi: SslContextToken, .../IncludeToken/Never için ekleme modu ayarlanır  
Simge koruma: yanlış  
  
 Tüm üstbilgi ve gövde imzalar: True  
  
 Koruma sırasını: SignBeforeEncrypt  
  
 İmza şifrelemek: True  
  
#### <a name="351-policy-for-sslnegotiated-service-authentication"></a>3.5.1 SslNegotiated hizmeti kimlik doğrulama için İlkesi  
 Bu bölümdeki tüm kimlik doğrulama modu için ilke benzerdir ve yalnızca özel imzalı destekleme veya kullanılan belirteçleri onaylama tarafından farklıdır.  
  
#### <a name="352-anonymousforsslnegotiated"></a>3.5.2'de AnonymousForSslNegotiated  
 Bu kimlik doğrulama modu ile istemci anonimdir ve hizmeti bir X.509 sertifikası kullanılarak doğrulanır. Kullanılan bağlama 3.5.1 yukarıda açıklandığı gibi simetrik bağlama bir örneğidir.  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="AnonymousForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-f4b86ce2-4ba6-4c55-bac1-2e920fc6d5db-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-d21ec2b8-99f5-443c-a4c6-a4d40619187e-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d21ec2b8-99f5-443c-a4c6-a4d40619187e-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="AnonymousForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-c84b24b9-39e0-4cc3-99e2-cec088f1b9eb-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-df206ad9-1ee2-46d7-9fb4-6e4631c9762f-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-df206ad9-1ee2-46d7-9fb4-6e4631c9762f-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="353-usernameforsslnegotiated"></a>3.5.3 UserNameForSslNegotiated  
 Bu kimlik doğrulaması ile görüntülenen bir kullanıcı adı belirteci SOAP katmanında imzalı destekleme belirteci olarak kullanan istemci modu kimliğini doğrular. Hizmet, bir X.509 sertifikası kullanılarak doğrulanır. Kullanılan bağlama 3.5.1 içinde açıklandığı gibi simetrik bağlama bir örneğidir.  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="UserNameForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-3d1a12c3-e690-474a-a223-a346fc0329a9-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-137ea768-7d49-404b-87eb-f11d9c7154aa-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_9" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-137ea768-7d49-404b-87eb-f11d9c7154aa-5"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="UserNameForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:SignedEncryptedSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:UsernameToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:WssUsernameToken10/></wsp:Policy></sp:UsernameToken></wsp:Policy></sp:SignedEncryptedSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-56e931e8-20c2-457f-a83e-8fcd6b92c258-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-83d053cb-03a0-4461-9616-86475cf083c4-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-83d053cb-03a0-4461-9616-86475cf083c4-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
#### <a name="354-issuedtokenforsslnegotiated"></a>3.5.4 IssuedTokenForSslNegotiated  
 Bu kimlik doğrulaması ile istemci hizmeti için bu nedenle, ancak bunun yerine kimlik doğrulamasını yapmaz modu bir STS tarafından verilmiş bir belirteç gösterir ve paylaşılan anahtar bilgi kanıtlar. Verilen belirteç SOAP katmanında bir onaylama destekleme belirteci görünür. Hizmet, bir X.509 sertifikası kullanılarak doğrulanır. Kullanılan bağlama 3.5.1 yukarıda açıklandığı gibi simetrik bağlama bir örneğidir.  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ... </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-b19fb2e7-8f0c-45c1-b62c-45d6ff6d57e7-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-199509f9-7963-42b7-b340-7598ee261d5a-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-199509f9-7963-42b7-b340-7598ee261d5a-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="IssuedTokenForSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:EndorsingSupportingTokens xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:IssuedToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><Issuer xmlns="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><Address xmlns="http://www.w3.org/2005/08/addressing">http://www.w3.org/2005/08/addressing/anonymous</Address><Metadata xmlns="http://www.w3.org/2005/08/addressing"><Metadata xmlns="http://schemas.xmlsoap.org/ws/2004/09/mex" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"><wsx:MetadataSection xmlns=""><wsx:MetadataReference><Address xmlns="http://www.w3.org/2005/08/addressing"> ... </Address><Identity xmlns="http://schemas.xmlsoap.org/ws/2006/02/addressingidentity"><Dns> ... </Dns></Identity></wsx:MetadataReference></wsx:MetadataSection></Metadata></Metadata></Issuer><sp:RequestSecurityTokenTemplate><trust:KeyType xmlns:trust="http://docs.oasis-open.org/ws-sx/ws-trust/200512">http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey</trust:KeyType></sp:RequestSecurityTokenTemplate><wsp:Policy><sp:RequireDerivedKeys/><sp:RequireInternalReference/></wsp:Policy></sp:IssuedToken></wsp:Policy></sp:EndorsingSupportingTokens><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/><sp:RequireSignatureConfirmation/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>    
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d75104d5-313e-440f-b112-db8aff57a5fe-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-e668caab-b7e4-4056-ac42-4015ae2a67a6-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e668caab-b7e4-4056-ac42-4015ae2a67a6-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
#### <a name="355-mutualsslnegotiated"></a>3.5.5 MutualSslNegotiated  
 Bu kimlik doğrulama modu ile istemci ve hizmet X.509 sertifikalarını kullanarak kimlik doğrulaması. Kullanılan bağlama 3.5.1 yukarıda açıklandığı gibi simetrik bağlama bir örneğidir.  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="MutualSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><mssp:RequireClientCertificate/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d1e6037e-8a64-494f-9447-07d3125b81b5-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-e4b73625-3011-4f6d-a6f9-4d682e860801-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e4b73625-3011-4f6d-a6f9-4d682e860801-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="MutualSslNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><mssp:SslContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient" xmlns:mssp="http://schemas.microsoft.com/ws/2005/07/securitypolicy"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><mssp:RequireClientCertificate/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></mssp:SslContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>   
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-c2a6ab10-889a-4ee1-871d-05410c90fc10-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-ede0bd89-1f7e-4453-96ed-13e58c7ba8fe-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-ede0bd89-1f7e-4453-96ed-13e58c7ba8fe-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
### <a name="36-sspinegotiated"></a>3.6 SspiNegotiated  
 Bu kimlik doğrulama modu ile istemci ve sunucu kimlik doğrulaması gerçekleştirmek için anlaşması protokolü kullanılır. Kerberos Mümkünse, kullanılan aksi NTLM. Kullanılan bağlama simetrik bağlama aşağıdaki özelliklere sahip olur;  
  
 Koruma simgesi: SpnegoContextToken, .../IncludeToken/AlwaysToRecipient için ekleme modu ayarlanır  
Simge koruma: yanlış  
  
 Tüm üstbilgi ve gövde imzalar: True  
  
 Koruma sırasını: SignBeforeEncrypt  
  
 İmza şifrelemek: True  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="SspiNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-9a954fcb-4df2-4610-9800-f542f2b5130a-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-554d8cfc-e956-43db-9abb-afcafd024347-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-554d8cfc-e956-43db-9abb-afcafd024347-4"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>   
```  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="SspiNegotiated_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:MustNotSendCancel/><sp:MustNotSendAmend/><sp:MustNotSendRenew/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-f1673773-f9a7-4b43-b13b-405e7dd4a6e3-4"> ... </u:Timestamp><sc:SecurityContextToken u:Id="uuid-e0aabc81-6942-4fe6-81bc-9def184565ea-1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:SecurityContextToken><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-e0aabc81-6942-4fe6-81bc-9def184565ea-3"> ... </u:Timestamp><sc:DerivedKeyToken u:Id="_1" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><sc:DerivedKeyToken u:Id="_0" xmlns:sc="http://docs.oasis-open.org/ws-sx/ws-secureconversation/200512"> ... </sc:DerivedKeyToken><Signature xmlns="http://www.w3.org/2000/09/xmldsig#"> ... </Signature><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList></o:Security>  
```  
  
### <a name="37-secureconversation"></a>3.7 SecureConversation  
 Kullanılan bağlama simetrik bağlama SCT WS-SecureConversation (WS-SC) başına olan koruma belirtecine sahip olur. SCT göre kendisini anlaşma protokolünü kullanan bir simetrik bağlama olan iç içe bir bağlama, WS-Trust (WS-Trust) veya WS-SecureConversation (WS-SC) kullanılarak belirlenir. Anlaşma Protokolü, mümkün olduğunda istemci ve sunucu kimlik doğrulaması gerçekleştirmek için Kerberos kullanır. Kerberos kullanılamaz, NTLM olarak geri döner.  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="SecureConversation_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SecureConversationToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:BootstrapPolicy><wsp:Policy><sp:SignedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="From" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="FaultTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="ReplyTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="MessageID" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="RelatesTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="Action" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts><sp:EncryptedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/></sp:EncryptedParts><sp:SymmetricBinding xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust10 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust10></wsp:Policy></sp:BootstrapPolicy><sp:MustNotSendAmend/></wsp:Policy></sp:SecureConversationToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-signbeforeencrypt-encryptsignature"></a>Güvenlik üstbilgi örnekler: SignBeforeEncrypt, EncryptSignature  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-f01c6159-f159-454d-bd97-bbcc9b8e25d3-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-582920d7-14a7-4adc-8091-e1f92d7d8055-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-582920d7-14a7-4adc-8091-e1f92d7d8055-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 İlke  
  
```xml  
<wsp:Policy wsu:Id="SecureConversation_policy"><wsp:ExactlyOne><wsp:All><sp:SymmetricBinding xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SecureConversationToken sp:IncludeToken="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/><sp:BootstrapPolicy><wsp:Policy><sp:SignedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/><sp:Header Name="To" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="From" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="FaultTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="ReplyTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="MessageID" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="RelatesTo" Namespace="http://www.w3.org/2005/08/addressing"/><sp:Header Name="Action" Namespace="http://www.w3.org/2005/08/addressing"/></sp:SignedParts><sp:EncryptedParts xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><sp:Body/></sp:EncryptedParts><sp:SymmetricBinding xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:ProtectionToken><wsp:Policy><sp:SpnegoContextToken sp:IncludeToken="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy/IncludeToken/AlwaysToRecipient"><wsp:Policy><sp:RequireDerivedKeys/></wsp:Policy></sp:SpnegoContextToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptSignature/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust10 xmlns:sp="http://schemas.xmlsoap.org/ws/2005/07/securitypolicy"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust10></wsp:Policy></sp:BootstrapPolicy><sp:MustNotSendAmend/></wsp:Policy></sp:SecureConversationToken></wsp:Policy></sp:ProtectionToken><sp:AlgorithmSuite><wsp:Policy><sp:Basic256/></wsp:Policy></sp:AlgorithmSuite><sp:Layout><wsp:Policy><sp:Strict/></wsp:Policy></sp:Layout><sp:IncludeTimestamp/><sp:EncryptBeforeSigning/><sp:OnlySignEntireHeadersAndBody/></wsp:Policy></sp:SymmetricBinding><sp:Wss11 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportRefKeyIdentifier/><sp:MustSupportRefIssuerSerial/><sp:MustSupportRefThumbprint/><sp:MustSupportRefEncryptedKey/></wsp:Policy></sp:Wss11><sp:Trust13 xmlns:sp="http://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702"><wsp:Policy><sp:MustSupportIssuedTokens/><sp:RequireClientEntropy/><sp:RequireServerEntropy/></wsp:Policy></sp:Trust13><wsaw:UsingAddressing/></wsp:All></wsp:ExactlyOne></wsp:Policy>  
```  
  
### <a name="security-header-examples-encryptbeforesign"></a>Güvenlik üstbilgi örnekler: EncryptBeforeSign  
 İstek  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-d57e6342-1c68-4095-a0c1-41979088a944-5"> ... </u:Timestamp><c:SecurityContextToken u:Id="uuid-9b22407d-b914-4c41-9105-1cf8cf7c3fe5-1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:SecurityContextToken><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_8" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```  
  
 Yanıt  
  
```xml  
<o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"><u:Timestamp u:Id="uuid-9b22407d-b914-4c41-9105-1cf8cf7c3fe5-6"> ... </u:Timestamp><c:DerivedKeyToken u:Id="_0" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><c:DerivedKeyToken u:Id="_1" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc"> ... </c:DerivedKeyToken><e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:ReferenceList><e:EncryptedData Id="_6" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#"> ... </e:EncryptedData></o:Security>  
```
