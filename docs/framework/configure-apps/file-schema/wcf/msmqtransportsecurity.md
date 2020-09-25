---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: 9d28f3f08e9c3984c055567df03f2839709a1522
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204651"
---
# \<msmqTransportSecurity>

Özel bağlama için MSMQ taşıma güvenlik ayarlarını belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegration>**](msmqintegration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqTransportSecurity>**  
  
## <a name="syntax"></a>Syntax  
  
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
|`msmqAuthenticationMode`|İletinin MSMQ taşıması tarafından nasıl doğrulanabilmesi gerektiğini belirtir. Bu olarak ayarlanırsa `None` , `msmqProtectionLevel` özniteliğinin değeri de olarak ayarlanmalıdır `None` .<br /><br /> Geçerli değerler şunlardır:<br /><br /> -None: kimlik doğrulaması yok.<br />-Windows: kimlik doğrulama mekanizması, iletiyle ilişkili SID için X. 509.440 sertifikasını almak üzere Active Directory kullanır. Bu daha sonra kullanıcının sıraya yazma izni olduğundan emin olmak için kuyruğun ACL 'sini denetlemek üzere kullanılır.<br />-Sertifika: Kanal, sertifika deposundan sertifikayı alır.<br /><br /> Varsayılan değer Windows ' dır. Bu öznitelik türü <xref:System.ServiceModel.MsmqAuthenticationMode> .|  
|`msmqEncryptionAlgorithm`|Message Queue yöneticileri arasında ileti aktarılırken ileti şifreleme için kullanılacak algoritmayı belirtir. Geçerli değerler şunlardır:<br /><br /> - RC4Stream<br />-AES<br /><br /> Varsayılan değer RC4Stream ' dir. Bu öznitelik türü <xref:System.ServiceModel.MsmqEncryptionAlgorithm> .|  
|`msmqProtectionLevel`|İletinin MSMQ taşıma düzeyinde nasıl güvenlik altına alınacağını belirtir. Şifreleme, her iki ileti bütünlüğünü ve Red olmamasını sağlarken, şifreleme ileti bütünlüğünü sağlar; diğer bir deyişle, ileti gerçekten gönderenden gelir ve gönderici kim olduğunu söyledikleri kişidir. Geçerli değerler şunlardır:<br /><br /> -None: koruma yok.<br />-Sign: Iletiler imzalanır.<br />-EncryptAndSign: Iletiler şifrelenir ve imzalanır.<br /><br /> Varsayılan değer, Işaret ' dır. Bu öznitelik türü <xref:System.Net.Security.ProtectionLevel> .|  
|`msmqSecureHashAlgorithm`|İmzaların bir parçası olarak Özet hesaplanırken kullanılacak algoritmayı belirtir. Geçerli değerler şunlardır:<br /><br /> -MD5<br />-SHA1<br />-SHA256<br />-SHA512 olur<br /><br /> Varsayılan değer SHA1 ' dır. Bu öznitelik türü <xref:System.ServiceModel.MsmqSecureHashAlgorithm> .<br>MD5 ve SHA1 ile ilgili çarpışma sorunları nedeniyle, Microsoft SHA256 veya daha iyi bir performans öneriyor.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<msmqIntegration>](msmqintegration.md)|Message Queuing (MSMQ) gönderici veya alıcısıyla etkileşim için gereken ayarları belirtir.|  
|[\<msmqTransport>](msmqtransport.md)|Yerel MSMQ protokolünü kullanan bir Windows Communication Foundation (WCF) hizmeti için sıraya alma iletişim özelliklerini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Taşıma güvenliği hakkında daha fazla bilgi için bkz. [Transport Security](../../../wcf/feature-details/transport-security.md).  
  
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
- [Taşıma Güvenliği](../../../wcf/feature-details/transport-security.md)
