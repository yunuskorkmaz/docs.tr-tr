---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: fece74e76f879eff51f154eab8c8edea2c27119e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772404"
---
# <a name="msmqtransportsecurity"></a>\<msmqTransportSecurity>
Özel bağlama için MSMQ taşıma güvenlik ayarlarını belirtir.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<msmqIntegration >  
\<msmqTransportSecurity>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|İletinin MSMQ taşıma tarafından nasıl doğrulacağını belirtir. Bu ayarlanırsa `None`, değerini `msmqProtectionLevel` özniteliği de ayarlanması gerekir `None`.<br /><br /> Geçerli değerler şunlardır:<br /><br /> -Yok: Kimlik doğrulaması yok.<br />-   Windows: Kimlik doğrulama mekanizması, SID iletiyle ilişkili için X.509 sertifikası almak için Active Directory kullanır. Bu, daha sonra kullanıcı emin olmak için ACL kuyruğun kuyruğa yazmak için yeterli izne sahip olmadığını denetlemek için kullanılır.<br />-Sertifikası: Kanal sertifikayı sertifika deposundan alır.<br /><br /> Windows varsayılan değerdir. Bu öznitelik türünde <xref:System.ServiceModel.MsmqAuthenticationMode>.|  
|`msmqEncryptionAlgorithm`|Etkin ileti şifreleme için iletileri ileti sıra yöneticileri arasında transfer ederken kullanılan algoritmayı belirtir. Geçerli değerler şunlardır:<br /><br /> -RC4Stream<br />-AES<br /><br /> RC4Stream varsayılan değerdir. Bu öznitelik türünde <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|`msmqProtectionLevel`|İletinin MSMQ taşıma düzeyinde güvenliği nasıl belirtir. İleti bütünlüğü hem takası EncryptAndSign sağlar ancak şifreleme ileti bütünlüğü sağlar; diğer bir deyişle, ileti gönderen gerçekten gelir ve gönderen kim kendisinin kendisinin olduğunu söylüyor. Geçerli değerler şunlardır:<br /><br /> -Yok: Koruma yok.<br />-Oturum: İmzalı iletiler.<br />-   EncryptAndSign: İletileri şifrelenir ve imzalanmış.<br /><br /> Oturum varsayılan değerdir. Bu öznitelik türünde <xref:System.Net.Security.ProtectionLevel>.|  
|`msmqSecureHashAlgorithm`|İmzanın bir parçası Özet işlem alanında kullanılan algoritmayı belirtir. Geçerli değerler şunlardır:<br /><br /> -MD5<br />-   SHA1<br />-   SHA256<br />-   SHA512<br /><br /> Varsayılan, SHA1 değeridir. Bu öznitelik türünde <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.<br>Çakışma sorunları nedeniyle MD5 ve SHA1, SHA256 veya iyi Microsoft önerir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<msmqIntegration >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegration.md)|Message Queuing (MSMQ) gönderen veya alıcı ile etkileşimi için gereken ayarları belirtir.|  
|[\<msmqTransport>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqtransport.md)|Yerel MSMQ protokolünü kullanan bir Windows Communication Foundation (WCF) hizmeti için sıraya alma iletişim özelliklerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Aktarım güvenliği hakkında daha fazla bilgi için bkz. [aktarım güvenliği](../../../../../docs/framework/wcf/feature-details/transport-security.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [WCF'de Kuyruklar](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [Taşımalar](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Taşıma Seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Aktarım Güvenliği](../../../../../docs/framework/wcf/feature-details/transport-security.md)
