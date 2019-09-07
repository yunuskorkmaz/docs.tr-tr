---
title: <security> / <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: 00a933892376c2dc9771752beaf76d4994554968
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399890"
---
# <a name="security-of-basichttpbinding"></a>\<\<BasicHttpBinding > Güvenlik >
[ \<BasicHttpBinding >](basichttpbinding.md)'nin güvenlik yeteneklerini tanımlar.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<basicHttpBinding >** ](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Güvenlik >**  
  
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
|mod|İsteğe bağlı. Kullanılan güvenlik türünü belirtir. Varsayılan, `None` değeridir. Bu öznitelik türü <xref:System.ServiceModel.BasicHttpSecurityMode>.|  
  
## <a name="mode-attribute"></a>mode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Yok.|-İletiler aktarım sırasında güvenli değildir.|  
|Aktarım|Güvenlik, HTTPS taşıması kullanılarak sağlanır. SOAP iletilerinin HTTPS kullanılarak güvenliği sağlanır. Hizmetin, hizmetin X. 509.440 sertifikası kullanılarak istemcinin kimliği doğrulanır. İstemcinin kimliği, sağlanan ClientCredentialType kullanılarak doğrulanır. Aktarım > bakın. [ \<](transport-of-basichttpbinding.md)|  
|`Message`|Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır. Varsayılan olarak, gövde şifrelenir ve imzalanır. Bu bağlama için, sistem, sunucu sertifikasının bant dışı istemciye sağlanması gerekir. `ClientCredentialType` Bu`Certificate`bağlama için geçerli tek geçerlidir.|  
|TransportWithMessageCredential|Bütünlük, gizlilik ve sunucu kimlik doğrulaması, aktarım güvenliği tarafından sağlanır. İstemci kimlik doğrulaması, SOAP iletisi güvenliği aracılığıyla sağlanır. Bu mod, Kullanıcı Kullanıcı adı/parola kullanarak kimlik doğrulaması yapıldığında ve ileti aktarımını güvenli hale getirmek için mevcut bir HTTP dağıtımı olduğunda geçerlidir.|  
|Yalnızca transportcredential|Bu mod ileti bütünlüğü ve gizliliği sağlamaz. HTTP tabanlı istemci kimlik doğrulaması sağlar. Bu mod dikkatli kullanılmalıdır. Aktarım güvenliğinin diğer yollarla (IPSec gibi) sağlandığı ve yalnızca WCF altyapısı tarafından istemci kimlik doğrulamasının sağlandığı ortamlarda kullanılması gerekir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Taşıma >](transport-of-basichttpbinding.md)|Temel bir HTTP hizmeti için taşıma güvenlik ayarlarını tanımlar. Bu öğe öğesine <xref:System.ServiceModel.HttpTransportSecurity>karşılık gelir.|  
|[\<ileti >](message-of-basichttpbinding.md)|Temel bir HTTP hizmeti için ileti güvenlik ayarlarını tanımlar. Bu öğe öğesine <xref:System.ServiceModel.BasicHttpMessageSecurity>karşılık gelir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|bağlama|BasicHttpBinding > Binding öğesi. [ \<](basichttpbinding.md)|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, SOAP iletisi güvenli değildir ve istemcinin kimliği doğrulanmaz. Bu öğe, `basicHttpBinding` öğesi için ek güvenlik ayarları yapılandırmanıza olanak sağlar.  
  
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
- [\<bağlama >](../../../misc/binding.md)
