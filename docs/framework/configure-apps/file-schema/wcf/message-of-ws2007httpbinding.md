---
title: '&lt;ws2007HttpBinding&gt; &lt;iletisi&gt;'
ms.date: 03/30/2017
ms.assetid: 9ffd8db6-84a8-4b38-a9fe-2cb1a87a1c97
ms.openlocfilehash: a8f448f40dbbf5fabbbd833cb9366c3911045f95
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43470031"
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
|`algorithmSuite`|İleti şifreleme ve anahtar-wrap algoritmaları ayarlar. Algoritmalar ve anahtar boyutları tarafından belirlenen <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> sınıfı. Bu algoritmalar, güvenlik ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen platformlarla eşlenir.<br /><br /> Basic256 varsayılan değerdir.|  
|`clientCredentialType`|İsteğe bağlı. Güvenlik modunu kullanarak istemci kimlik doğrulaması yapılırken kullanılacak kimlik bilgisi türünü belirten `Message` veya `TransportWithMessageCredentials`. Aşağıdaki tabloda numaralandırma değerlerinden bakın. Windows varsayılandır.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.MessageCredentialType>.|  
|`establishSecurityContext`|Güvenlik kanalı güvenli bir oturum oluşturur olup olmadığını belirleyen bir değer. Güvenli bir oturum uygulama mesaj alışverişleri önce bir güvenlik bağlamı belirteci (SCT) oluşturur. Güvenlik kanalı SCT kurulduğunda sunar bir <xref:System.ServiceModel.Channels.ISession> üst kanallar için arabirim. Güvenli oturumlar kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: güvenli oturum oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md).<br /><br /> Varsayılan değer `true` şeklindedir.|  
|`negotiateServiceCredential`|İsteğe bağlı. Hizmet kimlik bilgisi İstemci bant dışı sağlanan veya anlaşma işlemi aracılığıyla istemcisine hizmetten alınan olup olmadığını belirten bir değeri. Böyle bir anlaşma normal ileti değişimi için bir precursor ' dir.<br /><br /> Varsa `clientCredentialType` özniteliği eşittir hiçbiri, kullanıcı adı veya sertifika, bu öznitelik ayarını `false` hizmet sertifikası istemciyi bant dışından kullanılabilir olduğunu ve istemci ( kullanarakhizmetsertifikasıbelirtmelisinizanlamınagelir.[ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) içinde [ \<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) hizmet davranışı. Bu mod, WS-Güven ve WS-SecureConversation uygulayan SOAP yığınlarıyla birlikte çalışabilir.<br /><br /> Varsa `ClientCredentialType` özniteliği `Windows`, bu öznitelik ayarını `false` Kerberos kimlik doğrulaması tabanlı belirtir. Başka bir deyişle, hizmet ve istemci aynı Kerberos etki alanının parçası olmalıdır. Bu mod, Kerberos belirteci profil WS-Güven ve WS-SecureConversation yanı sıra (OASIS WSS TC sırasında tanımlanan) uygulayan SOAP yığınları ile birlikte çalışabilir.<br /><br /> Bu öznitelik olduğunda `true`, tüneller bir .NET SOAP anlaşması neden <xref:System.ServiceModel.Security.Tokens.ServiceModelSecurityTokenTypes.Spnego%2A> SOAP iletileri üzerinden exchange.<br /><br /> Varsayılan, `true` değeridir.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Basic128|İleti özeti için Sha1 ve Rsa oaep mgf1p Aes128 şifreleme anahtarı kaydırma için kullanın.|  
|Basic192|İleti özeti, anahtar kaydırma için Rsa-oaep mgf1p için Sha1 Aes192 şifrelemesi kullanın.|  
|Basic256|İleti özeti, anahtar kaydırma için Rsa-oaep mgf1p için Sha1 Aes256 şifrelemesi kullanın.|  
|Basic256Rsa15|İleti şifreleme, ileti özeti için Sha1 ve anahtar kaydırma için Rsa15 Aes256 kullanın.|  
|Basic192Rsa15|İleti şifreleme, ileti özeti için Sha1 ve anahtar kaydırma için Rsa15 Aes192 kullanın.|  
|TripleDes|İleti özeti, anahtar kaydırma için Rsa-oaep mgf1p için Sha1 TripleDes şifrelemesi kullanın.|  
|Basic128Rsa15|İleti özeti için Sha1 ve anahtar kaydırma için Rsa15 ileti şifreleme için Aes128'i kullanın.|  
|TripleDesRsa15|İleti özeti için Sha1 ve anahtar kaydırma için Rsa15 TripleDes şifrelemesi kullanın.|  
|Basic128Sha256|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p Aes256 kullanın.|  
|Basic192Sha256|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p Aes192 kullanın.|  
|Basic256Sha256|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p Aes256 kullanın.|  
|TripleDesSha256|TripleDes ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p ileti şifreleme için kullanın.|  
|Basic128Sha256Rsa15|İleti özeti için Sha256 ve anahtar kaydırma için Rsa15 ileti şifreleme için Aes128'i kullanın.|  
|Basic192Sha256Rsa15|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 Aes192 kullanın.|  
|Basic256Sha256Rsa15|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 Aes256 kullanın.|  
|TripleDesSha256Rsa15|TripleDes ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 ileti şifreleme için kullanın.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`None`|Bu, anonim istemcilerle etkileşime geçmek bir hizmet sağlar. Hizmette, bu hizmeti herhangi bir istemci kimlik bilgilerini gerektirmeyeceğini belirtir. İstemcide, istemcinin bir istemci kimlik bilgileri sağlamaz gösterir.|  
|`Certificate`|Gerekli izin verir, istemci kimlik doğrulaması kullanarak bir sertifika. Varsa `message` güvenlik modu kullanılır ve `negotiateServiceCredential` özniteliği `false`, istemci ile hizmet sertifikası sağlanması gerekir.|  
|`IssuedToken`|Genellikle bir güvenlik belirteci hizmeti (STS) tarafından verilen bir özel simgeyi belirtir.|  
|`UserName`|Gerekli izin verir, istemci kimlik doğrulaması kullanarak bir `UserName` kimlik bilgisi. WCF parola özeti gönderme veya parola ve ileti güvenliği için bu anahtarları kullanarak anahtarlar türetme desteklemez. Bu nedenle, taşıma kullanırken, güvenli WCF zorlar `UserName` kimlik bilgileri. Bu kimlik bilgisi modu birlikte çalışabilen bir exchange ya da temel bir birlikte çalışabilen olmayan anlaşma sonuçlanır `negotiateServiceCredential` özniteliği.|  
|`Windows`|SOAP değişimleri, kimliği doğrulanmış bağlamı altında olmasını sağlayan bir `Windows` kimlik bilgisi. Varsa `negotiateServiceCredential` özniteliği `true`, bu bir SSPI anlaşması veya Kerberos (birlikte çalışabilen standart) ya da gerçekleştirir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|Güvenlik ayarlarını tanımlayan bir [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.NonDualMessageSecurityOverHttpElement>  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
