---
title: <transport> / <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: 1cb165fed9266307335482166116c4c1d62efe7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152963"
---
# <a name="transport-of-msmqintegrationbinding"></a>\<\<msmqIntegrationBinding> taşıma>
İleti Sıraya tümleştirme aktarımı için güvenlik ayarlarını tanımlar.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bağlayıcı>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<güvenlik>**](security-of-msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ulaşım>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<security>
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelikleri, alt öğeleri ve üst öğeleri açıklar  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|İletinin MSMQ aktarım tarafından nasıl doğrulanmış olması gerektiğini belirtir. Bu `None`ayarlanırsa, `msmqProtectionLevel` öznitelik değeri de `None`ayarlanmalıdır.<br /><br /> Geçerli değerler şunlardır:<br /><br /> - Yok: Kimlik doğrulaması yok.<br />- WindowsDomain: Kimlik doğrulama mekanizması, iletiyle ilişkili SID için X.509 sertifikasını almak için Active Directory kullanır. Bu daha sonra, kullanıcının kuyruğa yazma izni olduğundan emin olmak için kuyruğun ACL'sini denetlemek için kullanılır.<br />- Sertifika: Kanal sertifika deposundan sertifika alır.<br /><br /> Varsayılan değer WindowsDomain'dir. Bu öznitelik türündedir. <xref:System.ServiceModel.MsmqAuthenticationMode>|  
|`msmqEncryptionAlgorithm`|İleti sıra yöneticileri arasında ileti aktarırken ileti şifrelemesi için kullanılacak algoritmayı belirtir. Geçerli değerler şunlardır:<br /><br /> - RC4Stream<br />- AES<br /><br /> Varsayılan değer RC4Stream'dir. Bu öznitelik türündedir. <xref:System.ServiceModel.MsmqEncryptionAlgorithm>|  
|`msmqProtectionLevel`|İletinin MSMQ aktarım düzeyinde nasıl güvenli olduğunu belirtir. Şifreleme ileti bütünlüğünü sağlarken, EncryptAndSign hem ileti bütünlüğünü hem de reddetmeyi sağlar; yani, mesaj gerçekten gönderenden gelir ve gönderen dedikleri kişidir.<br /><br /> - Geçerli değerler şunlardır:<br />- Yok: Koruma yok.<br />- İşaret: Mesajlar imzalanır.<br />- EncryptAndSign: İletiler şifrelenir ve imzalanır.<br /><br /> Varsayılan değer İşarettir. Bu öznitelik tür ProtectionLevel'dir.|  
|`msmqSecureHashAlgorithm`|- İmzaların bir parçası olarak özetin hesaplanmasında kullanılacak algoritmayı belirtir. Geçerli değerler şunlardır:<br />- MD5<br />- SHA1<br />- SHA256<br />- SHA512<br /><br /> Varsayılan değer SHA1'dir. Bu öznitelik türündedir. <xref:System.ServiceModel.MsmqSecureHashAlgorithm><br>MD5 ve SHA1 ile çarpışma sorunları nedeniyle, Microsoft SHA256 veya daha iyi önerir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 None  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<güvenlik>](security-of-basichttpbinding.md)|MSMQ bağlamanın güvenlik ayarlarını tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe, İleti Sıraya tümleştirme aktarımiçin güvenlik ayarlarını kapsüller. Ayarlar, hem İleti Sıralı tümleştirme hem de sıraya alınan aktarımlar için aynıdır. Kimlik Doğrulama Modu, Şifreleme Algoritması, Güvenli Karma Algoritması ve Koruma Düzeyini ayarlamanızı sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlayıcı>](bindings.md)
