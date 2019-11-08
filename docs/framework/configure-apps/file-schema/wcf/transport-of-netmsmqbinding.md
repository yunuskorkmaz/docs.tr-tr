---
title: <transport> / <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: 0df17832818e6e4e7c8e551fabaf4f5241807a74
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736005"
---
# <a name="transport-of-netmsmqbinding"></a>\<netMsmqBinding > \<taşıma >
Taşıma güvenlik ayarlarını tanımlar.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netMsmqBinding >** ](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<güvenlik >** ](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<taşıma >**  
  
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
|msmqAuthenticationMode|İletinin MSMQ taşıması tarafından nasıl doğrulanabilmesi gerektiğini belirtir. Geçerli değerler şunlardır:<br /><br /> -None: kimlik doğrulaması yok.<br />-WindowsDomain: kimlik doğrulama mekanizması, iletiyle ilişkili güvenlik tanımlayıcısı için X. 509.440 sertifikasını almak üzere Active Directory kullanır. Bu daha sonra kullanıcının sıra için yazma iznine sahip olduğundan emin olmak üzere kuyruğun ACL 'sini denetlemek için kullanılır.<br />-Sertifika: Kanal sertifikayı sertifika deposundan alır.<br /><br /> Varsayılan, `WindowsDomain` değeridir.<br /><br /> Bu öznitelik `None`olarak ayarlandıysa, `msmqProtectionLevel` özniteliği de `None`olarak ayarlanmalıdır. Bu öznitelik <xref:System.ServiceModel.MsmqAuthenticationMode> türündedir|  
|Msmqencryptionalgoritması|Message Queue yöneticileri arasında ileti aktarılırken ileti şifreleme için kullanılacak algoritmayı belirtir. Geçerli değerler şunlardır:<br /><br /> - RC4Stream<br />-AES<br />-Varsayılan değer `RC4Stream`. Bu öznitelik <xref:System.ServiceModel.MsmqEncryptionAlgorithm>türündedir.|  
|msmqProtectionLevel|MSMQ taşıması düzeyinde iletilerin güvenli hale getirilme yöntemini belirtir. Şifreleme ileti bütünlüğünü sağlar, oturum açma ve şifreleme hem ileti bütünlüğünü hem de Red olmamasını sağlar. Diğer bir deyişle, ileti gerçekten gönderenden geldi ve gönderen kim olduğunu söylüyor. Geçerli değerler şunlardır:<br /><br /> -None: koruma yok.<br />-Sign: Iletiler imzalanır.<br />-EncryptAndSign: Iletiler şifrelenir ve imzalanır.<br />-Varsayılan `Sign`.|  
|msmqSecureHashAlgorithm|İleti özetinin bilgi işlem için kullanılacak karma algoritmasını belirtir. Geçerli değerler şunlardır:<br /><br /> -MD5<br />-SHA1<br />-SHA256<br />-SHA512 olur<br /><br /> Varsayılan, `SHA1` değeridir. Bu öznitelik <xref:System.ServiceModel.MsmqSecureHashAlgorithm>türündedir.<br>MD5 ve SHA1 ile ilgili çarpışma sorunları nedeniyle, Microsoft SHA256 veya daha iyi bir performans öneriyor.|  
  
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
- [\< bağlama >](bindings.md)
