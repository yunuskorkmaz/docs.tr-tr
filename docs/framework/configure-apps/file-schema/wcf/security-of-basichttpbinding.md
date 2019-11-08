---
title: <security> / <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: c8e4f2d000a155eecd2a6c7faaaf4af525b24ca3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738710"
---
# <a name="security-of-basichttpbinding"></a>\<güvenlik > \<basicHttpBinding >
[\<basicHttpBinding >](basichttpbinding.md)'nin güvenlik yeteneklerini tanımlar.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<basicHttpBinding >** ](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<güvenlik >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|mod|İsteğe bağlı. Kullanılan güvenlik türünü belirtir. Varsayılan, `None` değeridir. Bu öznitelik <xref:System.ServiceModel.BasicHttpSecurityMode>türündedir.|  
  
## <a name="mode-attribute"></a>Mode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok.|-İletiler aktarım sırasında güvenli değildir.|  
|Aktarım|Güvenlik, HTTPS taşıması kullanılarak sağlanır. SOAP iletilerinin HTTPS kullanılarak güvenliği sağlanır. Hizmetin, hizmetin X. 509.440 sertifikası kullanılarak istemcinin kimliği doğrulanır. İstemcinin kimliği, sağlanan ClientCredentialType kullanılarak doğrulanır. [\<taşıma >](transport-of-basichttpbinding.md)bakın.|  
|İleti|Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır. Varsayılan olarak, gövde şifrelenir ve imzalanır. Bu bağlama için, sistem, sunucu sertifikasının bant dışı istemciye sağlanması gerekir. Bu bağlama için geçerli `ClientCredentialType` `Certificate`.|  
|TransportWithMessageCredential|Bütünlük, gizlilik ve sunucu kimlik doğrulaması, aktarım güvenliği tarafından sağlanır. İstemci kimlik doğrulaması, SOAP iletisi güvenliği aracılığıyla sağlanır. Bu mod, Kullanıcı Kullanıcı adı/parola kullanarak kimlik doğrulaması yapıldığında ve ileti aktarımını güvenli hale getirmek için mevcut bir HTTP dağıtımı olduğunda geçerlidir.|  
|Yalnızca transportcredential|Bu mod ileti bütünlüğü ve gizliliği sağlamaz. HTTP tabanlı istemci kimlik doğrulaması sağlar. Bu mod dikkatli kullanılmalıdır. Aktarım güvenliğinin diğer yollarla (IPSec gibi) sağlandığı ve yalnızca WCF altyapısı tarafından istemci kimlik doğrulamasının sağlandığı ortamlarda kullanılması gerekir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<taşıma >](transport-of-basichttpbinding.md)|Temel bir HTTP hizmeti için taşıma güvenlik ayarlarını tanımlar. Bu öğe <xref:System.ServiceModel.HttpTransportSecurity>karşılık gelir.|  
|[\<ileti >](message-of-basichttpbinding.md)|Temel bir HTTP hizmeti için ileti güvenlik ayarlarını tanımlar. Bu öğe <xref:System.ServiceModel.BasicHttpMessageSecurity>karşılık gelir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|bağlama|[\<basicHttpBinding >](basichttpbinding.md)bağlama öğesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, SOAP iletisi güvenli değildir ve istemcinin kimliği doğrulanmaz. Bu öğe `basicHttpBinding` öğesi için ek güvenlik ayarlarını yapılandırmanızı sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Kimlik Bilgisi Türü Seçme](../../../wcf/feature-details/selecting-a-credential-type.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\< bağlama >](bindings.md)
