---
title: <security> / <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 5b74c95ef2933fcf7e8d49aed89d95acbd288b80
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936703"
---
# <a name="security-of-msmqintegrationbinding"></a>\<\<MsmqIntegrationBinding > Güvenlik >
Message Queuing (MSMQ) tümleştirme kanalının taşıma güvenlik ayarlarını tanımlar.  
  
 \<system.ServiceModel>  
\<bağlama >  
msmqIntegrationBinding  
\<bağlama >  
\<Güvenlik >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<msmqIntegrationBinding>
  <binding>
    <security mode="None/Transport">
      <transport msmqAuthenticationMode="None/Windows/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
      <message algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               defaultProtectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</msmqIntegrationBinding>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|mod|Message Queuing tümleştirme kanalı ile bütünlüğü, gizliliği ve kimlik doğrulamasını denetleyen güvenlik türünü belirtir. Geçerli değerler şunlardır:<br /><br /> Seçim Bu, güvenliği devre dışı bırakır.<br />Aktarım Koruma ve kimlik doğrulama, taşıma tarafından sunulur. Bu, iki kuyruk yöneticisi arasındaki ileti güvenliği için geçerlidir. Uygulama ve kuyruk Yöneticisi arasında bir güvenlik sunulmaz. Mevcut MSMQ uygulamaları, bu tür güvenlik moduyla işlevsel olarak eşdeğerdir.<br /><br /> Varsayılan değer `Transport` şeklindedir. Bu öznitelik türü <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Taşıma >](transport-of-msmqintegrationbinding.md)|Message Queuing tümleştirme taşıması için güvenlik ayarlarını tanımlar. Bu öğe türündedir <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../misc/binding.md)|[ \<MsmqIntegrationBinding](msmqintegrationbinding.md)'in Binding öğesi >.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [WCF'de Kuyruklar](../../../wcf/feature-details/queues-in-wcf.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../misc/binding.md)
- [\<MsmqIntegrationBinding >](msmqintegrationbinding.md)
