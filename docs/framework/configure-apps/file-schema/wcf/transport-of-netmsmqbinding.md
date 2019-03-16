---
title: <transport> , <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: 25dc616aa8801c28b301c6219cc45fe69c43e559
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58039347"
---
# <a name="transport-of-netmsmqbinding"></a>\<Aktarım >, \<netMsmqBinding >
Taşıma güvenlik ayarlarını tanımlar.  
  
 \<system.ServiceModel>  
\<bağlamaları >  
\<netMsmqBinding>  
\<bağlama >  
\<Güvenlik >  
\<taşıma >  
  
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
|msmqAuthenticationMode|İletinin MSMQ taşıma tarafından nasıl doğrulacağını belirtir. Geçerli değerler şunlardır:<br /><br /> -Yok: Kimlik doğrulaması yok.<br />-   WindowsDomain: İletiyle ilişkili güvenlik kimliği için X.509 sertifikası almak için Active Directory kimlik doğrulama mekanizması kullanır. Bu, ardından kullanıcı emin olmak için ACL kuyruğun sıra için yazma iznine sahip olmadığını denetlemek için kullanılır.<br />-Sertifikası: Kanal sertifikayı sertifika deposundan alır.<br /><br /> Varsayılan, `WindowsDomain` değeridir.<br /><br /> Bu öznitelik ayarlanırsa `None`, `msmqProtectionLevel` özniteliği de ayarlanması gerekir `None`. Bu öznitelik türünde <xref:System.ServiceModel.MsmqAuthenticationMode>|  
|msmqEncryptionAlgorithm|Etkin ileti şifreleme için iletileri ileti sıra yöneticileri arasında transfer ederken kullanılan algoritmayı belirtir. Geçerli değerler şunlardır:<br /><br /> -RC4Stream<br />-AES<br />-Varsayılan değer `RC4Stream`. Bu öznitelik türünde <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|msmqProtectionLevel|MSMQ taşıma düzeyinde güvenli şekilde iletileri belirtir. İleti bütünlüğü hem takası ileti bütünlüğü çalışırken işaretini ve şifreleme sağlar şifreleme sağlar. Diğer bir deyişle, ileti gönderen gerçekten geldi ve gönderen kim kendisinin kendisinin olduğunu söylüyor. Geçerli değerler şunlardır:<br /><br /> -Yok: Koruma yok.<br />-Oturum: İmzalı iletiler.<br />-   EncryptAndSign: İletileri şifrelenir ve imzalanmış.<br />-Varsayılan `Sign`.|  
|msmqSecureHashAlgorithm|İleti özeti bilgi işlem için kullanılan karma algoritmasını belirtir. Geçerli değerler şunlardır:<br /><br /> -MD5<br />-   SHA1<br />-   SHA256<br />-   SHA512<br /><br /> Varsayılan, `SHA1` değeridir. Bu öznitelik türünde <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.<br>Çakışma sorunları nedeniyle MD5 ve SHA1, SHA256 veya iyi Microsoft önerir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Hiçbiri  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Sıraya alınan taşımalar için taşıma güvenlik ayarlarını tanımlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [WCF'de Kuyruklar](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../../../docs/framework/misc/binding.md)
