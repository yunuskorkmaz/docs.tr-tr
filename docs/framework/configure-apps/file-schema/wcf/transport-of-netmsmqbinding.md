---
title: <transport> / <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: cc47c01cccc931e81ba57ab37ad9e3accfaa693b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152937"
---
# <a name="transport-of-netmsmqbinding"></a>\<\<netMsmqBağlama> taşıma>
Aktarım güvenlik ayarlarını tanımlar.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBağlama>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bağlayıcı>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<güvenlik>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ulaşım>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<netMsmqBinding>
  <binding>
    <security>
      <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    </security>
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|msmqAuthenticationMode|İletinin MSMQ aktarım tarafından nasıl doğrulanmış olması gerektiğini belirtir. Geçerli değerler şunlardır:<br /><br /> - Yok: Kimlik doğrulaması yok.<br />- WindowsEtki Alanı: Kimlik doğrulama mekanizması, iletiyle ilişkili güvenlik tanımlayıcısı için X.509 sertifikasını almak için Etkin Dizin kullanır. Bu daha sonra kullanıcının kuyruk için yazma izni olduğundan emin olmak için sıranın ACL denetlemek için kullanılır.<br />- Sertifika: Kanal sertifika deposundan sertifikayı alır.<br /><br /> Varsayılan değer: `WindowsDomain`.<br /><br /> Bu öznitelik `None`ayarlanmışsa, `msmqProtectionLevel` öznitelik de . `None` Bu öznitelik türü<xref:System.ServiceModel.MsmqAuthenticationMode>|  
|msmqEncryptionAlgoritma|İleti sıra yöneticileri arasında ileti aktarırken ileti şifrelemesi için kullanılacak algoritmayı belirtir. Geçerli değerler şunlardır:<br /><br /> - RC4Stream<br />- AES<br />- Varsayılan `RC4Stream`değer. Bu öznitelik türündedir. <xref:System.ServiceModel.MsmqEncryptionAlgorithm>|  
|msmqProtectionLevel|İletilerin MSMQ aktarım düzeyinde nasıl güvenli hale olduğunu belirtir. Şifreleme ileti bütünlüğünü sağlarken, imza ve şifreleme hem ileti bütünlüğünü hem de reddetmeyi sağlar. Yani, mesaj gerçekten gönderen den geldi ve gönderen onlar olduğunu söylüyorlar kimdir. Geçerli değerler şunlardır:<br /><br /> - Yok: Koruma yok.<br />- İşaret: Mesajlar imzalanır.<br />- EncryptAndSign: İletiler şifrelenir ve imzalanır.<br />- Varsayılan `Sign`değer.|  
|msmqSecureHashAlgorithm|İleti özetini hesaplamak için kullanılacak karma algoritmayı belirtir. Geçerli değerler şunlardır:<br /><br /> - MD5<br />- SHA1<br />- SHA256<br />- SHA512<br /><br /> Varsayılan değer: `SHA1`. Bu öznitelik türündedir. <xref:System.ServiceModel.MsmqSecureHashAlgorithm><br>MD5 ve SHA1 ile çarpışma sorunları nedeniyle, Microsoft SHA256 veya daha iyi önerir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 None  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<güvenlik>](security-of-netmsmqbinding.md)|Sıralı taşımalar için aktarım güvenlik ayarlarını tanımlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [WCF'de Kuyruklar](../../../wcf/feature-details/queues-in-wcf.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlayıcı>](bindings.md)
