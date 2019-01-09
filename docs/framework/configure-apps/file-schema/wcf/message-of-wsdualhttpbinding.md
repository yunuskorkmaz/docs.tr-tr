---
title: '&lt;wsDualHttpBinding&gt; &lt;iletisi&gt;'
ms.date: 03/30/2017
ms.assetid: 75101744-eed8-4d61-91f4-5fc4473a21f2
ms.openlocfilehash: 4aec0bf3c88bcbb634c1b6ab44cbb0bcdf2f24e5
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147518"
---
# <a name="ltmessagegt-of-ltwsdualhttpbindinggt"></a>&lt;wsDualHttpBinding&gt; &lt;iletisi&gt;
İçin ileti düzeyi güvenliği tanımlar [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).  
  
 \<system.ServiceModel>  
\<bağlamaları >  
\<wsDualHttpBinding >  
\<bağlama >  
\<Güvenlik >  
\<İleti >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
         negotiateServiceCredential="Boolean"
         algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
</message>
```  
  
## <a name="type"></a>Tür  
 <xref:System.ServiceModel.MessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|algorithmSuite|İsteğe bağlı. İleti şifreleme ve anahtar-wrap algoritmaları ayarlar. Algoritmalar ve anahtar boyutları tarafından belirlenen <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> sınıfı. Bu algoritmalar, güvenlik ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen platformlarla eşlenir.<br /><br /> Aşağıda olası değerler için bkz. Varsayılan değer `Basic256` şeklindedir.|  
|clientCredentialType|İsteğe bağlı. Güvenlik modunu kullanarak gerçekleştirme istemci kimlik doğrulaması gerektiğinde kullanılmak üzere kimlik bilgisi türünü belirten `Message`. Aşağıda olası değerler için bkz. Varsayılan, `Windows` değeridir.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.MessageCredentialType>.|  
|negotiateServiceCredential|İsteğe bağlı. Hizmet kimlik bilgisi İstemci bant dışı sağlanan veya anlaşma işlemi aracılığıyla istemcisine hizmetten alınan belirten bir Boole değeri. Böyle bir anlaşma normal ileti değişimi için bir precursor ' dir.<br /><br /> Varsa `clientCredentialType` özniteliği eşittir hiçbiri, kullanıcı adı veya sertifika, bu öznitelik ayarını `false` hizmet sertifikası istemciyi bant dışından kullanılabilir olduğunu ve hizmet sertifikasını belirtmek gereken istemci gelir (kullanma [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) içinde [ \<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) hizmet davranışı. Bu mod, WS-Güven ve WS-SecureConversation uygulayan SOAP yığınlarıyla birlikte çalışabilir.<br /><br /> Varsa `ClientCredentialType` özniteliği `Windows`, bu öznitelik ayarını `false` Kerberos kimlik doğrulaması tabanlı belirtir. Başka bir deyişle, hizmet ve istemci aynı Kerberos etki alanının parçası olmalıdır. Bu mod, Kerberos belirteci profil WS-Güven ve WS-SecureConversation yanı sıra (OASIS WSS TC sırasında tanımlanan) uygulayan SOAP yığınları ile birlikte çalışabilir. Bu öznitelik olduğunda `true`, SPNego exchange tüneller SOAP iletilerini bir .NET SOAP anlaşması neden olur.<br /><br /> Varsayılan, `true` değeridir.|  
  
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
|Hiçbiri|Bu, anonim istemcilerle etkileşime geçmek bir hizmet sağlar. Hizmet tarafında, bu hizmeti herhangi bir istemci kimlik bilgilerini gerektirmeyeceğini belirtir. İstemcide, istemcinin bir istemci kimlik bilgileri sağlamaz gösterir.|  
|Windows|SOAP değişimleri, Windows kimlik bilgisi kimliği doğrulanmış bağlamı altında olmasını sağlar. Varsa `negotiateServiceCredential` özniteliği `true`, bu bir SSPI anlaşması veya Kerberos (birlikte çalışabilen standart) ya da gerçekleştirir.|  
|UserName|Gerekli izin verir, istemci kimlik doğrulaması kullanarak bir kullanıcı adı kimlik bilgisi. WCF parola özeti gönderme veya parola ve ileti güvenliği için bu anahtarları kullanarak anahtarlar türetme desteklemez. Bu nedenle, WCF aktarma UserName kimlik bilgileri kullanırken, güvenli olduğundan emin zorlar. Bu kimlik bilgisi modu birlikte çalışabilen bir exchange ya da temel bir birlikte çalışabilen olmayan anlaşma sonuçlanır `negotiateServiceCredential` özniteliği.|  
|Sertifika|Gerekli izin verir, istemci kimlik doğrulaması kullanarak bir sertifika. İleti güvenlik modunu kullanılıyorsa ve `negotiateServiceCredential` özniteliği `false`, istemcinin hizmet sertifikası ile sağlanması gerekir.|  
|IssuedToken|Genellikle bir güvenlik belirteci hizmeti tarafından verilen bir özel simgeyi belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsdualhttpbinding.md)|Güvenlik yeteneklerini tanımlar [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSDualHttpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>  
 <xref:System.ServiceModel.MessageSecurityOverHttp>  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
