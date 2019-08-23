---
title: <security> / <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 1bbc3a460ce707e71b72a469af2e03acd8dc79e5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936695"
---
# <a name="security-of-netmsmqbinding"></a>\<\<NetMsmqBinding > Güvenlik >
MSMQ bağlamasının güvenlik ayarlarını tanımlar. Aktarım veya SOAP güvenliğinin etkinleştirilip etkinleştirilmeyeceğini ve bu durumda hangi kimlik doğrulama modunun ve koruma düzeylerinin kullanımda olduğunu belirtir.  
  
 \<system.ServiceModel>  
\<bağlama >  
\<netMsmqBinding >  
\<bağlama >  
\<Güvenlik >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<security mode="None/Transport/Message/Both">
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
             clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|mod|Bütünlüğü, gizliliği ve kimlik doğrulamasını denetleyen güvenlik türünü belirtir. Geçerli değerler şunlardır:<br /><br /> Seçim Bu, güvenliği devre dışı bırakır.<br />Aktarım Koruma ve kimlik doğrulama, taşıma tarafından sunulur. Bu, iki kuyruk yöneticisi arasındaki ileti güvenliği için geçerlidir. Uygulama ve kuyruk Yöneticisi arasında bir güvenlik sunulmaz. Mevcut MSMQ uygulamaları, bu tür güvenlik moduyla işlevsel olarak eşdeğerdir.<br />Mesaj Son uç uygulama güvenliğini belirtir. Aktarım katmanında bir güvenlik sunulmaz. Bu, diğer standart bağlamalar tarafından sunulan güvenliğe benzerdir.<br />İs Hem aktarım hem de SOAP mesajlaşma katmanında güvenlik sağlar. Aynı kimlik bilgileri her iki düzeyde de gereklidir.<br /><br /> Varsayılan değer Aktarım ' dır. Bu öznitelik türü <xref:System.ServiceModel.NetMsmqSecurityMode>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<ileti >](message-of-netmsmqbinding.md)|SOAP iletisi güvenlik ayarlarını tanımlar. Bu öğe türündedir <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.|  
|[\<Taşıma >](transport-of-netmsmqbinding.md)|MSMQ taşıması için güvenlik ayarlarını tanımlar. Bu öğe türündedir <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|bağlama|NetMsmqBinding > bağlama öğesi [ \<](netmsmqbinding.md)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../misc/binding.md)
- [WCF'de Kuyruklar](../../../wcf/feature-details/queues-in-wcf.md)
