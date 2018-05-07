---
title: '&lt;netMsmqBinding&gt; &lt;iletisi&gt;'
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 0e947667c414079f24398b401456efd56bf9922c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="ltmessagegt-of-ltnetmsmqbindinggt"></a>&lt;netMsmqBinding&gt; &lt;iletisi&gt;
SOAP iletisi güvenlik ayarlarını bu tanımlar `netMsmqBinding` bağlama.  
  
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
|algorithmSuite|İletinin MSMQ aktarımı üzerinden gönderilen iletiler için ileti tabanlı güvenlik elde etmek için kullanılan şifreleme ve anahtar-wrap algoritmaları ayarlar.<br /><br /> Varsayılan değer `Aes256` şeklindedir. Bu öznitelik türünde <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|  
|clientCredentialType|MSMQ taşıma gönderilen iletiler için istemci kimlik doğrulaması yapılırken kullanılacak kimlik bilgileri türünü belirtir. Geçerli değerler şunlardır:<br /><br /> -Hiçbiri: Bu, hizmetin anonim istemcilerle etkileşime girmesine izin verir. Hizmetin ne istemci bir kimlik bilgisi gerektirir.<br />-Windows: Bu SOAP alışverişleri Windows kimlik bilgisi kimliği doğrulanmış bağlamı altında olmasını sağlar. Bu her zaman Kerberos tabanlı kimlik doğrulaması gerçekleştirir.<br />-UserName: Bu gerektirecek şekilde hizmetini etkinleştirir, istemci kimlik doğrulaması kullanıcı adı kimlik bilgilerini kullanarak. Kimlik bilgisi bu durumda kullanarak belirtilmesi gerekiyor `clientCredentials` davranışı **dikkat:** Windows Communication Foundation (WCF) parola kullanarak ve böyle tuşlarıyla için Özet veya türetme anahtarları bir parola gönderme desteklemiyor ileti güvenliği. Bu nedenle, WCF exchange kullanıcı adı kimlik bilgileri kullanılırken güvenli zorlar. Bu mod hizmet sertifikası kullanarak istemci tarafı belirtilmesini gerektirir `clientCredential` davranışı ve `serviceCertificate`. <br /><br /> -Sertifika: Bu gerektirecek şekilde hizmetini etkinleştirir, istemci kimlik doğrulaması kullanarak bir sertifika. İstemci kimlik bilgileri bu durumda kullanarak belirtilmesi gerekiyor `clientCredentials` davranışı. Hizmet kimlik bilgilerini bu durumda kullanarak belirtilmesi gerekiyor `clientCredentials` belirterek davranış `serviceCertificate`.<br />-CardSpace: Bu hizmet gerektirecek şekilde sağlar, istemci kimlik doğrulaması bir CardSpace kullanma. `serviceCertiifcate` İçinde sağlanmalıdır `clientCredential` davranışı.<br /><br /> Varsayılan değer `Windows` şeklindedir. Bu öznitelik türünde <xref:System.ServiceModel.MessageCredentialType>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Bağlama için güvenlik ayarlarını tanımlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>  
 <xref:System.ServiceModel.MessageSecurityOverMsmq>  
 [WCF'de Kuyruklar](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
