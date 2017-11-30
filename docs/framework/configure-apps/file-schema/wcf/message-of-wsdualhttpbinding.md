---
title: '&lt;wsDualHttpBinding&gt; &lt;iletisi&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75101744-eed8-4d61-91f4-5fc4473a21f2
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c2d4eda0a1975da4518d077b6cfa779a8e764a66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmessagegt-of-ltwsdualhttpbindinggt"></a>&lt;wsDualHttpBinding&gt; &lt;iletisi&gt;
İleti düzeyi güvenlik için tanımlar [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).  
  
 \<Sistem. ServiceModel >  
\<bağlamaları >  
\<wsDualHttpBinding >  
\<bağlama >  
\<Güvenlik >  
\<İleti >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<message   
      clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
     negotiateServiceCredential="Boolean"  
   algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"/>  
</message>  
```  
  
## <a name="type"></a>Tür  
 <xref:System.ServiceModel.MessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|algorithmSuite|İsteğe bağlı. İleti şifreleme ve anahtar-wrap algoritmaları ayarlar. Algoritmaları ve anahtar boyutları tarafından belirlenen <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> sınıfı. Bu algoritmalar, güvenlik ilkesi dili (WS-SecurityPolicy) belirtiminde belirtilen eşlenir.<br /><br /> Aşağıda için olası değerler konusuna bakın. Varsayılan değer `Basic256` şeklindedir.|  
|clientCredentialType|İsteğe bağlı. Güvenlik modu kullanılarak gerçekleştirme istemci kimlik doğrulaması olduğunda kullanılacak kimlik bilgileri türünü belirtir `Message`. Aşağıda için olası değerler konusuna bakın. Varsayılan, `Windows` değeridir.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.MessageCredentialType>.|  
|negotiateServiceCredential|İsteğe bağlı. Hizmet kimlik bilgilerini bant dışı istemcide sağlanan veya anlaşma işlemi aracılığıyla istemcisine hizmetinden alınan belirten bir Boole değeri. Bu tür bir anlaşma precursor normal ileti Exchange'e ' dir.<br /><br /> Varsa `clientCredentialType` özniteliği eşittir None, kullanıcı adı veya sertifika, bu öznitelik ayarını `false` hizmet sertifikası bant dışı istemcide kullanılabilir olduğunu ve istemci hizmet sertifikasını belirtmek için ihtiyaç duyduğu gelir (kullanma [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) içinde [ \<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) hizmet davranışı. Bu mod, WS-Trust ve WS-SecureConversation uygulayan SOAP yığınları ile birlikte çalışabilir.<br /><br /> Varsa `ClientCredentialType` özniteliği `Windows`, bu öznitelik ayarını `false` Kerberos kimlik doğrulaması tabanlı belirtir. Bu, istemci ve hizmet aynı Kerberos etki alanının parçası olması gerektiği anlamına gelir. Bu mod uygulayan Kerberos belirteci profil (OASIS WSS TC tanımlandığı gibi) WS-Trust ve WS-SecureConversation yanı sıra SOAP yığınları birlikte çalışabilir. Bu öznitelik olduğunda `true`, SOAP iletileri üzerinden SPNego exchange tünelleri .NET SOAP anlaşması neden olur.<br /><br /> Varsayılan, `true` değeridir.|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Basic128|İleti özeti için Sha1 ve Rsa oaep mgf1p Aes128 şifreleme anahtarı kaydırma için kullanın.|  
|Basic192|Aes192 şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.|  
|Basic256|Aes256 şifreleme, Sha1 oaep Rsa mgf1p anahtar kaydırma için ileti özeti için kullanın.|  
|Basic256Rsa15|İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Aes256 kullanın.|  
|Basic192Rsa15|İleti şifreleme, ileti özeti için Sha1 ve anahtar sarma Rsa15 için Aes192 kullanın.|  
|TripleDes|TripleDes şifreleme kullanmak, Sha1 ileti özeti için oaep Rsa mgf1p anahtar kaydırma için.|  
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
|Yok.|Bu hizmetin anonim istemcilerle etkileşime girmesine izin verir. Hizmet tarafında bu hizmeti istemci kimlik gerektirmez gösterir. İstemcide, bu istemciyi istemci kimlik sağlamaz gösterir.|  
|Windows|SOAP alışverişleri Windows kimlik bilgisi kimliği doğrulanmış bağlamı altında olmasını sağlar. Varsa `negotiateServiceCredential` özniteliği `true`, bu bir SSPI anlaşması veya Kerberos (birlikte çalışabilen standart) ya da gerçekleştirir.|  
|UserName|Hizmetinin gerektiren izin verir, istemci kimlik doğrulaması kullanıcı adı kimlik bilgilerini kullanarak. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]bir parola Özet gönderirken ya da parola kullanarak ve böyle anahtarların ileti güvenliği için kullanarak anahtarları türetme desteklemez. Bu nedenle, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] taşıma kullanıcı adı kimlik bilgileri kullanılırken güvenli zorlar. Bu kimlik bilgisi modu birlikte çalışabilir exchange veya temel çalışabilen olmayan bir anlaşma sonuçlanır `negotiateServiceCredential` özniteliği.|  
|Sertifika|Hizmetinin gerektiren izin verir, istemci kimlik doğrulaması kullanarak bir sertifika. İleti güvenlik modu kullanılıyorsa ve `negotiateServiceCredential` özniteliği `false`, istemci ile hizmet sertifikası hazırlanması gerekir.|  
|IssuedToken|Genellikle bir güvenlik belirteci hizmeti tarafından verilen özel bir belirteç belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsdualhttpbinding.md)|Güvenlik özelliklerini tanımlayan [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSDualHttpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>  
 <xref:System.ServiceModel.MessageSecurityOverHttp>  
 [Hizmetler ve istemcileri güvenli hale getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem tarafından sağlanan bağlamaları yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
