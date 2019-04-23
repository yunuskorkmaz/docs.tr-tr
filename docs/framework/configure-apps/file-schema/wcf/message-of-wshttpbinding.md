---
title: <message> / <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 621abbde-590b-454d-90ac-68dc3c69c720
ms.openlocfilehash: 4d9b46b6c148f9280f6504b9bccdf644ab451c00
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102680"
---
# <a name="message-of-wshttpbinding"></a>\<İleti >, \<wsHttpBinding >
İleti düzeyi güvenliği ayarlarını tanımlar [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 \<system.ServiceModel>  
\<bağlamaları >  
\<wsHttpBinding>  
\<bağlama >  
\<Güvenlik >  
\<İleti >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
         establishSecurityContext="Boolean"
         negotiateServiceCredential="Boolean" />
```  
  
## <a name="type"></a>Tür  
 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|algorithmSuite|İleti şifreleme ve anahtar-wrap algoritmaları ayarlar. Algoritmalar ve anahtar boyutları tarafından belirlenen <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> sınıfı. Bu algoritmalar, güvenlik ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen platformlarla eşlenir.<br /><br /> Varsayılan değer `Basic256` şeklindedir.|  
|clientCredentialType|İsteğe bağlı. Güvenlik modunu kullanarak gerçekleştirme istemci kimlik doğrulaması gerektiğinde kullanılmak üzere kimlik bilgisi türünü belirten `Message` veya `TransportWithMessageCredentials`. Aşağıdaki sabit listesi değerleri bakın. Varsayılan, `Windows` değeridir.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.MessageCredentialType>.|  
|establishSecurityContext|Güvenlik kanalı güvenli bir oturum oluşturur olup olmadığını belirleyen bir Boole değeri. Güvenli bir oturum uygulama mesaj alışverişleri önce bir güvenlik bağlamı belirteci (SCT) oluşturur. Güvenlik kanalı SCT kurulduğunda sunar bir <xref:System.ServiceModel.Channels.ISession> üst kanallar için arabirim. Güvenli oturumlar kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Güvenli oturum oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md).<br /><br /> Varsayılan değer `true` şeklindedir.|  
|negotiateServiceCredential|İsteğe bağlı. Hizmeti kimlik bilgileri bant dışı istemcide sağlanan veya anlaşma işlemi aracılığıyla istemcisine hizmetten alınan olup olmadığını belirten bir Boole değeri. Böyle bir anlaşma normal ileti değişimi için bir precursor ' dir.<br /><br /> Varsa `clientCredentialType` özniteliği eşittir hiçbiri, kullanıcı adı veya sertifika, bu öznitelik ayarını `false` hizmet sertifikası istemciyi bant dışından kullanılabilir olduğunu ve hizmet sertifikasını belirtmek gereken istemci gelir (kullanma [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) içinde [ \<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) hizmet davranışı. Bu mod, WS-Güven ve WS-SecureConversation uygulayan SOAP yığınlarıyla birlikte çalışabilir.<br /><br /> Varsa `ClientCredentialType` özniteliği `Windows`, bu öznitelik ayarını `false` Kerberos kimlik doğrulaması tabanlı belirtir. Başka bir deyişle, hizmet ve istemci aynı Kerberos etki alanının parçası olmalıdır. Bu mod, Kerberos belirteci profil WS-Güven ve WS-SecureConversation yanı sıra (OASIS WSS TC sırasında tanımlanan) uygulayan SOAP yığınları ile birlikte çalışabilir.<br /><br /> Bu öznitelik olduğunda `true`, SPNego exchange tüneller SOAP iletilerini bir .NET SOAP anlaşması neden olur.<br /><br /> Varsayılan, `true` değeridir.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Basic128|İleti özeti için Sha1 ve Rsa oaep mgf1p Basic128 şifreleme anahtarı kaydırma için kullanın.|  
|Basic192|İleti özeti, anahtar kaydırma için Rsa-oaep mgf1p için Sha1 Basic192 şifrelemesi kullanın.|  
|Basic256|İleti özeti, anahtar kaydırma için Rsa-oaep mgf1p için Sha1 Basic256 şifrelemesi kullanın.|  
|Basic256Rsa15|İleti şifreleme, ileti özeti için Sha1 ve anahtar kaydırma için Rsa15 Basic256 kullanın.|  
|Basic192Rsa15|İleti şifreleme, ileti özeti için Sha1 ve anahtar kaydırma için Rsa15 Basic192 kullanın.|  
|TripleDes|İleti özeti, anahtar kaydırma için Rsa-oaep mgf1p için Sha1 TripleDes şifrelemesi kullanın.|  
|Basic128Rsa15|İleti şifreleme, ileti özeti için Sha1 ve anahtar kaydırma için Rsa15 Basic128 kullanın.|  
|TripleDesRsa15|İleti özeti için Sha1 ve anahtar kaydırma için Rsa15 TripleDes şifrelemesi kullanın.|  
|Basic128Sha256|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p Basic256 kullanın.|  
|Basic192Sha256|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p Basic192 kullanın.|  
|Basic256Sha256|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p Basic256 kullanın.|  
|TripleDesSha256|TripleDes ileti özeti için Sha256 ve anahtar kaydırma için Rsa-oaep mgf1p ileti şifreleme için kullanın.|  
|Basic128Sha256Rsa15|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 Basic128 kullanın.|  
|Basic192Sha256Rsa15|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 Basic192 kullanın.|  
|Basic256Sha256Rsa15|İleti şifreleme, ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 Basic256 kullanın.|  
|TripleDesSha256Rsa15|TripleDes ileti özeti için Sha256 ve anahtar kaydırma için Rsa15 ileti şifreleme için kullanın.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|None|Bu, anonim istemcilerle etkileşime geçmek bir hizmet sağlar. Hizmet tarafında, bu hizmeti herhangi bir istemci kimlik bilgilerini gerektirmeyeceğini belirtir. İstemcide, istemcinin bir istemci kimlik bilgileri sağlamaz gösterir.|  
|Sertifika|Gerekli izin verir, istemci kimlik doğrulaması kullanarak bir sertifika. İleti güvenlik modunu kullanılıyorsa ve `negotiateServiceCredential` özniteliği `false`, istemcinin hizmet sertifikası ile sağlanması gerekir.|  
|IssuedToken|Genellikle bir güvenlik belirteci hizmeti tarafından verilen bir özel simgeyi belirtir.|  
|UserName|Gerekli izin verir, istemci kimlik doğrulaması kullanarak bir kullanıcı adı kimlik bilgisi. WCF parola özeti gönderme veya parola ve ileti güvenliği için bu anahtarları kullanarak anahtarlar türetme desteklemez. Bu nedenle, WCF aktarma UserName kimlik bilgileri kullanırken, güvenli olduğundan emin zorlar. Bu kimlik bilgisi modu birlikte çalışabilen bir exchange ya da temel bir birlikte çalışabilen olmayan anlaşma sonuçlanır `negotiateServiceCredential` özniteliği.|  
|Windows|SOAP değişimleri, Windows kimlik bilgisi kimliği doğrulanmış bağlamı altında olmasını sağlar. Varsa `negotiateServiceCredential` özniteliği `true`, bu bir SSPI anlaşması veya Kerberos (birlikte çalışabilen standart) ya da gerçekleştirir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|Güvenlik ayarlarını tanımlayan bir [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.NonDualMessageSecurityOverHttpElement>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../../../docs/framework/misc/binding.md)
