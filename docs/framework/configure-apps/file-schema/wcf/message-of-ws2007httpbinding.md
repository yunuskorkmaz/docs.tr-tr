---
title: '&lt;ws2007HttpBinding&gt; &lt;iletisi&gt;'
ms.date: 03/30/2017
ms.assetid: 9ffd8db6-84a8-4b38-a9fe-2cb1a87a1c97
ms.openlocfilehash: d3449735222d02857ee11ef6d20914c1e9a018a7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltmessagegt-of-ltws2007httpbindinggt"></a>&lt;ws2007HttpBinding&gt; &lt;iletisi&gt;
İleti düzeyi güvenliği ayarlarını tanımlar [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) öğesi.  
  
 \<system.ServiceModel>  
\<bağlamaları >  
\<ws2007HttpBinding>  
\<bağlama >  
\<Güvenlik >  
\<İleti >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<ws2007HttpBinding>  
 <binding >  
  <security>  
   <message clientCredentialType =  
    "None/Windows/UserName/Certificate/IssuedToken"  
    establishSecurityContext="Boolean"  
    negotiateServiceCredential="Boolean"  
    algorithmSuite= Enumeration. See algorithmSuite Attribute below.  
    defaultProtectionLevel="None/Sign/EncryptionAndSign" />  
  </security>  
 </binding>  
</ws2007HttpBinding>  
```  
  
## <a name="type"></a>Tür  
 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`algorithmSuite`|İleti şifreleme ve anahtar-wrap algoritmaları ayarlar. Algoritmaları ve anahtar boyutları tarafından belirlenen <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> sınıfı. Bu algoritmalar, güvenlik ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen eşlenir.<br /><br /> Basic256 varsayılan değerdir.|  
|`clientCredentialType`|İsteğe bağlı. Güvenlik modunu kullanarak istemci kimlik doğrulaması yapılırken kullanılacak kimlik bilgileri türünü belirtir `Message` veya `TransportWithMessageCredentials`. Aşağıdaki tabloda numaralandırma değerlerinin bakın. Windows varsayılandır.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.MessageCredentialType>.|  
|`establishSecurityContext`|Güvenlik kanalını güvenli oturum kurar olup olmadığını belirleyen bir değer. Güvenli bir oturum, uygulama ileti değiş tokuşu önce bir güvenlik bağlamı belirteci (SCT) oluşturur. SCT kurulduğunda güvenlik kanalı sunan bir <xref:System.ServiceModel.Channels.ISession> üst kanallarında arabirimi. Güvenli oturumlar kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: güvenli oturum oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md).<br /><br /> Varsayılan değer `true` şeklindedir.|  
|`negotiateServiceCredential`|İsteğe bağlı. Hizmet kimlik bilgilerini bant dışı istemcide sağlanan veya anlaşma işlemi aracılığıyla istemcisine hizmetinden alınan olup olmadığını belirten bir değer. Bu tür bir anlaşma precursor normal ileti Exchange'e ' dir.<br /><br /> Varsa `clientCredentialType` özniteliği eşittir None, kullanıcı adı veya sertifika, bu öznitelik ayarını `false` hizmet sertifikası bant dışı istemcide kullanılabilir olduğunu ve istemci ( kullanarakhizmetsertifikasıbelirtmelisinizgelir.[ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) içinde [ \<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) hizmet davranışı. Bu mod, WS-Trust ve WS-SecureConversation uygulamak SOAP yığınları ile birlikte çalışabilir.<br /><br /> Varsa `ClientCredentialType` özniteliği `Windows`, bu öznitelik ayarını `false` Kerberos kimlik doğrulaması tabanlı belirtir. Bu, istemci ve hizmet aynı Kerberos etki alanının parçası olması gerektiği anlamına gelir. Bu mod uygulayan Kerberos belirteci profil (OASIS WSS TC tanımlandığı gibi) WS-Trust ve WS-SecureConversation yanı sıra SOAP yığınları birlikte çalışabilir.<br /><br /> Bu öznitelik olduğunda `true`, tünelleri .NET SOAP anlaşması neden <xref:System.ServiceModel.Security.Tokens.ServiceModelSecurityTokenTypes.Spnego%2A> SOAP iletilerine üzerinden exchange.<br /><br /> Varsayılan, `true` değeridir.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Basic128|İleti özeti için Sha1 ve Rsa oaep mgf1p Aes128 şifreleme anahtarı kaydırma için kullanın.|  
|Basic192|Aes192 şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.|  
|Basic256|Aes256 şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.|  
|Basic256Rsa15|İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Aes256 kullanın.|  
|Basic192Rsa15|İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Aes192 kullanın.|  
|TripleDes|TripleDes şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.|  
|Basic128Rsa15|İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Aes128 kullanın.|  
|TripleDesRsa15|TripleDes şifreleme, ileti özeti için Sha1 ve Rsa15 anahtar kaydırma için kullanın.|  
|Basic128Sha256|İleti şifreleme, ileti özeti için Sha256 ve oaep Rsa mgf1p anahtar kaydırma için için Aes256 kullanın.|  
|Basic192Sha256|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p için Aes192 kullanın.|  
|Basic256Sha256|İleti şifreleme, ileti özeti için Sha256 ve oaep Rsa mgf1p anahtar kaydırma için için Aes256 kullanın.|  
|TripleDesSha256|TripleDes ileti şifreleme, ileti özeti için Sha256 ve oaep Rsa mgf1p anahtar kaydırma için kullanın.|  
|Basic128Sha256Rsa15|İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Aes128 kullanın.|  
|Basic192Sha256Rsa15|İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Aes192 kullanın.|  
|Basic256Sha256Rsa15|İleti şifreleme, ileti özeti için Sha256 ve anahtar sarma Rsa15 için Aes256 kullanın.|  
|TripleDesSha256Rsa15|TripleDes ileti şifreleme, ileti özeti için Sha256 ve Rsa15 anahtar kaydırma için kullanın.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`None`|Bu hizmetin anonim istemcilerle etkileşime girmesine izin verir. Hizmette bu hizmeti istemci kimlik gerektirmez gösterir. İstemcide, bu istemciyi istemci kimlik sağlamaz gösterir.|  
|`Certificate`|Hizmetinin gerektiren izin verir, istemci kimlik doğrulaması kullanarak bir sertifika. Varsa `message` güvenlik modu kullanılır ve `negotiateServiceCredential` özniteliği `false`, istemci ile hizmet sertifikası sağlanmalıdır.|  
|`IssuedToken`|Genellikle bir güvenlik belirteci hizmeti (STS) tarafından verilen özel bir belirteç belirtir.|  
|`UserName`|Hizmetinin gerektiren izin verir, istemci kimlik doğrulaması kullanarak bir `UserName` kimlik bilgisi. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] bir parola Özet gönderirken ya da parola kullanarak ve böyle anahtarların ileti güvenliği için kullanarak anahtarları türetme desteklemez. Bu nedenle, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] taşıma kullanırken güvenli zorlar `UserName` kimlik bilgileri. Bu kimlik bilgisi modu birlikte çalışabilir exchange veya temel çalışabilen olmayan bir anlaşma sonuçlanır `negotiateServiceCredential` özniteliği.|  
|`Windows`|Kimliği doğrulanmış bağlamı altında olacak şekilde SOAP alışverişleri sağlayan bir `Windows` kimlik bilgisi. Varsa `negotiateServiceCredential` özniteliği `true`, bu bir SSPI anlaşması veya Kerberos (birlikte çalışabilen standart) ya da gerçekleştirir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|İçin güvenlik ayarlarını tanımlayan bir [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.NonDualMessageSecurityOverHttpElement>  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
