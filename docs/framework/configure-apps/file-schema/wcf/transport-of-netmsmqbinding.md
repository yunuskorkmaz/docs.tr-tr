---
title: <transport> / <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: d6588e36a8a9420aa37837305aa904763c90781d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399355"
---
# <a name="transport-of-netmsmqbinding"></a>\<\<NetMsmqBinding > taşıma >
Taşıma güvenlik ayarlarını tanımlar.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netMsmqBinding >** ](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Güvenlik >** ](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Taşıma >**  
  
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
|msmqAuthenticationMode|İletinin MSMQ taşıması tarafından nasıl doğrulanabilmesi gerektiğini belirtir. Geçerli değerler şunlardır:<br /><br /> Seçim Kimlik doğrulaması yok.<br />-WindowsDomain: Kimlik doğrulama mekanizması, iletiyle ilişkili güvenlik tanımlayıcısı için X. 509.440 sertifikasını almak üzere Active Directory kullanır. Bu daha sonra kullanıcının sıra için yazma iznine sahip olduğundan emin olmak üzere kuyruğun ACL 'sini denetlemek için kullanılır.<br />Sertifika Kanal, sertifika deposundan sertifikayı alır.<br /><br /> Varsayılan, `WindowsDomain` değeridir.<br /><br /> Bu öznitelik olarak `None`ayarlandıysa `msmqProtectionLevel` , özniteliği de olarak `None`ayarlanmalıdır. Bu öznitelik türü<xref:System.ServiceModel.MsmqAuthenticationMode>|  
|Msmqencryptionalgoritması|Message Queue yöneticileri arasında ileti aktarılırken ileti şifreleme için kullanılacak algoritmayı belirtir. Geçerli değerler şunlardır:<br /><br /> - RC4Stream<br />-AES<br />-Varsayılan değer `RC4Stream`. Bu öznitelik türü <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.|  
|msmqProtectionLevel|MSMQ taşıması düzeyinde iletilerin güvenli hale getirilme yöntemini belirtir. Şifreleme ileti bütünlüğünü sağlar, oturum açma ve şifreleme hem ileti bütünlüğünü hem de Red olmamasını sağlar. Diğer bir deyişle, ileti gerçekten gönderenden geldi ve gönderen kim olduğunu söylüyor. Geçerli değerler şunlardır:<br /><br /> Seçim Koruma yok.<br />İmzalayabilirsiniz İletiler imzalanır.<br />EncryptAndSign özelliğini İletiler şifrelenir ve imzalanır.<br />-Varsayılan `Sign`değer.|  
|msmqSecureHashAlgorithm|İleti özetinin bilgi işlem için kullanılacak karma algoritmasını belirtir. Geçerli değerler şunlardır:<br /><br /> -MD5<br />-   SHA1<br />-   SHA256<br />-   SHA512<br /><br /> Varsayılan, `SHA1` değeridir. Bu öznitelik türü <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.<br>MD5 ve SHA1 ile ilgili çarpışma sorunları nedeniyle, Microsoft SHA256 veya daha iyi bir performans öneriyor.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](security-of-netmsmqbinding.md)|Sıraya alınan taşıtlar için taşıma güvenlik ayarlarını tanımlar.|  
  
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
- [\<bağlama >](../../../misc/binding.md)
