---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: 5899c609b3cf52c4a275ba6fb10c5826fcf37f1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153015"
---
# <a name="msmqtransportsecurity"></a>\<msmqTransportSecurity>
Özel bir bağlama için MSMQ taşıma güvenlik ayarlarını belirtir.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bağlayıcı>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqEntegrasyon>**](msmqintegration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqTransportSecurity>**  
  
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
|`msmqAuthenticationMode`|İletinin MSMQ aktarım tarafından nasıl doğrulanmış olması gerektiğini belirtir. Bu `None`ayarlanırsa, `msmqProtectionLevel` öznitelik değeri de `None`ayarlanmalıdır.<br /><br /> Geçerli değerler şunlardır:<br /><br /> - Yok: Kimlik doğrulaması yok.<br />- Windows: Kimlik doğrulama mekanizması, iletiyle ilişkili SID için X.509 sertifikasını almak için Etkin Dizin kullanır. Bu daha sonra, kullanıcının kuyruğa yazma izni olduğundan emin olmak için kuyruğun ACL'sini denetlemek için kullanılır.<br />- Sertifika: Kanal sertifika deposundan sertifika alır.<br /><br /> Varsayılan değer Windows'dur. Bu öznitelik türündedir. <xref:System.ServiceModel.MsmqAuthenticationMode>|  
|`msmqEncryptionAlgorithm`|İleti sıra yöneticileri arasında ileti aktarırken ileti şifrelemesi için kullanılacak algoritmayı belirtir. Geçerli değerler şunlardır:<br /><br /> - RC4Stream<br />- AES<br /><br /> Varsayılan değer RC4Stream'dir. Bu öznitelik türündedir. <xref:System.ServiceModel.MsmqEncryptionAlgorithm>|  
|`msmqProtectionLevel`|İletinin MSMQ aktarım düzeyinde nasıl güvenli olduğunu belirtir. Şifreleme ileti bütünlüğünü sağlarken, EncryptAndSign hem ileti bütünlüğünü hem de reddetmeyi sağlar; yani, mesaj gerçekten gönderenden gelir ve gönderen dedikleri kişidir. Geçerli değerler şunlardır:<br /><br /> - Yok: Koruma yok.<br />- İşaret: Mesajlar imzalanır.<br />- EncryptAndSign: İletiler şifrelenir ve imzalanır.<br /><br /> Varsayılan değer İşarettir. Bu öznitelik türündedir. <xref:System.Net.Security.ProtectionLevel>|  
|`msmqSecureHashAlgorithm`|İmzaların bir parçası olarak özetin hesaplanmasında kullanılacak algoritmayı belirtir. Geçerli değerler şunlardır:<br /><br /> - MD5<br />- SHA1<br />- SHA256<br />- SHA512<br /><br /> Varsayılan değer SHA1'dir. Bu öznitelik türündedir. <xref:System.ServiceModel.MsmqSecureHashAlgorithm><br>MD5 ve SHA1 ile çarpışma sorunları nedeniyle, Microsoft SHA256 veya daha iyi önerir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<msmqEntegrasyon>](msmqintegration.md)|İleti Sıralaması (MSMQ) gönderen veya alıcısı ile etkileşim için gereken ayarları belirtir.|  
|[\<msmqUlaşım>](msmqtransport.md)|Yerel MSMQ protokolünü kullanan bir Windows Communication Foundation (WCF) hizmetiiçin sıraya giren iletişim özelliklerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Aktarım güvenliği hakkında daha fazla bilgi için [Transport Security'ye](../../../wcf/feature-details/transport-security.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [WCF'de Kuyruklar](../../../wcf/feature-details/queues-in-wcf.md)
- [Taşımalar](../../../wcf/feature-details/transports.md)
- [Taşıma Seçme](../../../wcf/feature-details/choosing-a-transport.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Aktarım Güvenliği](../../../wcf/feature-details/transport-security.md)
