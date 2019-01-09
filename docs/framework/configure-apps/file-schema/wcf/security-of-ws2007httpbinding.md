---
title: '&lt;ws2007HttpBinding&gt; &lt;güvenliği&gt;'
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: a7bb6816c5b34e608b5010aba308ccd9d870d398
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145920"
---
# <a name="ltsecuritygt-of-ltws2007httpbindinggt"></a>&lt;ws2007HttpBinding&gt; &lt;güvenliği&gt;
İle kullanılan güvenlik ayarlarını temsil eden [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) öğesi.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<ws2007HttpBinding>  
\<bağlama >  
\<Güvenlik >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>
  <bindings>
    <ws2007HttpBinding>
      <binding name = "String">
        <security mode="None/Message/Transport/TransportWithMessageCredential">
          <transport>
          </transport>
          <message>
          </message>
        </security>
      </binding>
    </ws2007HttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`mode`|-İsteğe bağlı. Uygulanan güvenlik türünü belirtir. Varsayılan, `Message` değeridir.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>mod özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`None`|Güvenlik devre dışı bırakıldı.|  
|`Transport`|HTTPS kullanarak güvenliği sağlanır. Hizmet ile Güvenli Yuva Katmanı (SSL) sertifikalarını yapılandırılması gerekir. İleti tamamen HTTPS kullanan güvenli ve hizmet hizmet SSL sertifikasını kullanarak istemci tarafından doğrulanır. İstemci kimlik doğrulaması aracılığıyla denetlenir `ClientCredentials` özniteliği [ \<aktarım >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) öğesi.|  
|`Message`|SOAP ileti güveliği kullanarak güvenliği sağlanır. Varsayılan olarak, SOAP gövdesi imzalı ve şifrelenir. Çeşitli hizmet kimlik bilgilerini kullanmak için algoritma paketini olan bant dışı istemci kullanılabilir olup gibi özellikler, bu mod sunar ve ileti gövdesi ile uygulamak için koruma düzeyini <xref:System.ServiceModel.Security.SecurityMessageProperty>. İstemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir ve kimlik doğrulama sonuçlarını oturum süresi boyunca önbelleğe alınır.|  
|`TransportWithMessageCredential`|Bu modda, HTTPS kimlik doğrulaması bütünlüğü ve gizliliği sağlar ve istemci kimlik doğrulaması SOAP ileti güvenliği sağlar. Varsayılan olarak, istemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir ve kimlik doğrulama sonuçlarını oturum süresi boyunca önbelleğe alınır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<taşıma >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md)|Taşıma güvenlik ayarlarını tanımlar. Bu öğe için karşılık gelen <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> türü. Bu ayarlar, yalnızca taşıma için modu ayarlandığında uygulanır.|  
|[\<İleti >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|İleti için güvenlik ayarlarını tanımlar. Bu öğe için karşılık gelen <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> türü. Taşıma imkanı kullanılarak modu ayarlandığında, bu ayarlar uygulanmaz.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|HTTP taşıma uygulamalar için güvenli bir bağlama.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe, WS - uygulama hizmetleri ile birlikte çalışabilirlik için tasarlanmıştır * belirtimleri. Bu bağlama için Aktarım güvenliği HTTP veya HTTPS üzerinden Güvenli Yuva Katmanı (SSL) olan.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)
