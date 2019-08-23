---
title: <transport> / <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: 859bc00557f66e27d7bd82a16704fc59c6044613
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934724"
---
# <a name="transport-of-msmqintegrationbinding"></a>\<\<MsmqIntegrationBinding > taşıma >
Message Queuing tümleştirme taşıması için güvenlik ayarlarını tanımlar.  
  
 \<system.ServiceModel>  
\<bağlama >  
msmqIntegrationBinding  
\<bağlama >  
\<Güvenlik >  
\<Taşıma >  
  
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
 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|İletinin MSMQ taşıması tarafından nasıl doğrulanabilmesi gerektiğini belirtir. Bu olarak `None`ayarlanırsa, `msmqProtectionLevel` özniteliğinin değeri de olarak `None`ayarlanmalıdır.<br /><br /> Geçerli değerler şunlardır:<br /><br /> Seçim Kimlik doğrulaması yok.<br />-WindowsDomain: Kimlik doğrulama mekanizması, iletiyle ilişkili SID için X. 509.440 sertifikasını almak üzere Active Directory kullanır. Bu daha sonra kullanıcının sıraya yazma izni olduğundan emin olmak için kuyruğun ACL 'sini denetlemek üzere kullanılır.<br />Sertifika Kanal, sertifika deposundan sertifikayı alır.<br /><br /> Varsayılan değer WindowsDomain ' dir. Bu öznitelik türü <xref:System.ServiceModel.MsmqAuthenticationMode>.|  
|`msmqEncryptionAlgorithm`|Message Queue yöneticileri arasında ileti aktarılırken ileti şifreleme için kullanılacak algoritmayı belirtir. Geçerli değerler şunlardır:<br /><br /> - RC4Stream<br />-AES<br /><br /> Varsayılan değer RC4Stream ' dir. Bu öznitelik türü <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|`msmqProtectionLevel`|İletinin MSMQ taşıma düzeyinde nasıl güvenlik altına alınacağını belirtir. Şifreleme, her iki ileti bütünlüğünü ve Red olmamasını sağlarken, şifreleme ileti bütünlüğünü sağlar; diğer bir deyişle, ileti gerçekten gönderenden geliyor ve gönderen kim olduğunu söylüyor.<br /><br /> -Geçerli değerler aşağıdakileri içerir:<br />Seçim Koruma yok.<br />İmzalayabilirsiniz İletiler imzalanır.<br />EncryptAndSign özelliğini İletiler şifrelenir ve imzalanır.<br /><br /> Varsayılan değer, Işaret ' dır. Bu öznitelik ProtectionLevel türündedir.|  
|`msmqSecureHashAlgorithm`|-İmzaların bir parçası olarak Özet hesaplanırken kullanılacak algoritmayı belirtir. Geçerli değerler şunlardır:<br />-MD5<br />-   SHA1<br />-   SHA256<br />-   SHA512<br /><br /> Varsayılan değer SHA1 ' dır. Bu öznitelik türü <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.<br>MD5 ve SHA1 ile ilgili çarpışma sorunları nedeniyle, Microsoft SHA256 veya daha iyi bir performans öneriyor.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](security-of-basichttpbinding.md)|MSMQ bağlamasının güvenlik ayarlarını tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe Message Queuing tümleştirme aktarımının güvenlik ayarlarını kapsar. Bu ayarlar hem Message Queuing tümleştirme hem de sıraya alınmış aktarımlara yöneliktir. Kimlik doğrulama modu, şifreleme algoritması, güvenli karma algoritması ve koruma düzeyini ayarlamanıza olanak sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../misc/binding.md)
