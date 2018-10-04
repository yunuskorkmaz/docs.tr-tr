---
title: '&lt;netMsmqBinding&gt; &lt;iletisi&gt;'
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 124d53ae24b627c35863fda4cd8f404057978f1e
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48579094"
---
# <a name="ltmessagegt-of-ltnetmsmqbindinggt"></a>&lt;netMsmqBinding&gt; &lt;iletisi&gt;
SOAP ileti güvenlik ayarları bu tanımlar `netMsmqBinding` bağlama.  
  
 \<system.ServiceModel>  
\<bağlamaları >  
\<netMsmqBinding >  
\<bağlama >  
\<Güvenlik >  
\<İleti >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<netMsmqBinding>  
    <binding>  
      <security>  
         <message   
                      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />  
    </security>  
</netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|algorithmSuite|İletinin MSMQ taşıma gönderilen iletiler için ileti tabanlı güvenlik elde etmek için kullanılan şifreleme ve anahtar-wrap algoritmaları ayarlar.<br /><br /> Varsayılan değer `Aes256` şeklindedir. Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|  
|clientCredentialType|MSMQ taşıma gönderilen iletiler için istemci kimlik doğrulaması yapılırken kullanılacak kimlik bilgisi türünü belirtir. Geçerli değerler şunlardır:<br /><br /> -Yok: Bu, anonim istemcilerle etkileşime geçmek bir hizmet sağlar. Hizmet ya da istemci kimlik bilgileri gerektirir.<br />-Windows: Bu bir Windows kimlik bilgisi kimliği doğrulanmış bağlamı altında olacak şekilde SOAP değişimleri sağlar. Bu, her zaman Kerberos tabanlı kimlik doğrulaması gerçekleştirir.<br />-UserName: Bu hizmet gerektirecek şekilde sağlar, istemci kimlik doğrulaması kullanarak bir kullanıcı adı kimlik bilgisi. Kimlik bilgisi bu durumda kullanarak belirtilmesi gerekiyor `clientCredentials` davranışı **dikkat:** Windows Communication Foundation (WCF) ve bu anahtarları için parola kullanmaya Özet veya türetme anahtarı parola gönderme desteklemiyor ileti güvenliği. Bu nedenle, WCF exchange kullanıcı adı kimlik bilgileri kullanılırken sağlandığını zorlar. Bu mod, hizmet sertifikası kullanarak istemci tarafı belirtilmesini gerektirir `clientCredential` davranışı ve `serviceCertificate`. <br /><br /> -Sertifika: Bu hizmet gerektirecek şekilde sağlar, istemci kimlik doğrulaması kullanarak bir sertifika. İstemci kimlik bilgisi bu durumda kullanarak belirtilmesi gerekiyor `clientCredentials` davranışı. Hizmet kimlik bilgisi bu durumda kullanarak belirtilmesi gerekiyor `clientCredentials` belirterek davranışı `serviceCertificate`.<br />-CardSpace: Böylece hizmet istemek, istemci kimlik doğrulaması kullanarak bir CardSpace. `serviceCertiifcate` İçinde sağlanmalıdır `clientCredential` davranışı.<br /><br /> Varsayılan değer `Windows` şeklindedir. Bu öznitelik türünde <xref:System.ServiceModel.MessageCredentialType>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Bir bağlama için güvenlik ayarlarını tanımlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>  
 <xref:System.ServiceModel.MessageSecurityOverMsmq>  
 [WCF'de Kuyruklar](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
