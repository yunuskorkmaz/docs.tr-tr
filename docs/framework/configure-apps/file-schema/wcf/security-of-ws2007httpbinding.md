---
title: <security> / <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: a895df027bee7430e51e76c480136a49b6b2a0be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936570"
---
# <a name="security-of-ws2007httpbinding"></a>\<\<WS2007HttpBinding > Güvenlik >
WS2007HttpBinding > öğesiyle kullanılan [ \<](ws2007httpbinding.md) güvenlik ayarlarını temsil eder.  
  
 \<system.serviceModel>  
\<bağlama >  
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
|`mode`|Seçim. Uygulanan güvenlik türünü belirtir. Varsayılan, `Message` değeridir.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>Mode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`None`|Güvenlik devre dışı bırakıldı.|  
|`Transport`|Güvenlik, HTTPS kullanılarak sağlanır. Hizmetin Güvenli Yuva Katmanı (SSL) sertifikalarıyla yapılandırılması gerekir. İleti HTTPS kullanılarak tamamen güvenli hale getirilir ve hizmetin SSL sertifikası kullanılarak istemcinin kimliği doğrulanır. İstemci kimlik doğrulaması, [ \<Transport >](transport-of-ws2007httpbinding.md) öğesi `ClientCredentials` özniteliği aracılığıyla denetlenir.|  
|`Message`|Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır. Varsayılan olarak, SOAP gövdesi şifrelenir ve imzalanır. Bu mod, hizmet kimlik bilgilerinin, istemci bant dışı, kullanılacak algoritma paketini ve ileti gövdesine hangi koruma düzeyi üzerinden <xref:System.ServiceModel.Security.SecurityMessageProperty>uygulanacağını gibi çeşitli özellikler sunar. İstemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.|  
|`TransportWithMessageCredential`|Bu modda, HTTPS bütünlük, gizlilik ve sunucu kimlik doğrulaması sağlar ve SOAP iletisi güvenliği istemci kimlik doğrulaması sağlar. Varsayılan olarak, istemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Taşıma >](transport-of-ws2007httpbinding.md)|Taşıma güvenlik ayarlarını tanımlar. Bu öğe <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> türüne karşılık gelir. Bu ayarlar yalnızca, mod aktarım olarak ayarlandığında uygulanır.|  
|[\<ileti >](message-of-ws2007httpbinding.md)|İleti için güvenlik ayarlarını tanımlar. Bu öğe <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> türüne karşılık gelir. Bu ayarlar, mod aktarım olarak ayarlandığında uygulanmaz.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<ws2007HttpBinding>](ws2007httpbinding.md)|HTTP taşıma uygulamaları için güvenli bağlama.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe, WS-* belirtimlerini uygulayan hizmetlerle birlikte çalışabilirlik için tasarlanmıştır. Bu bağlama için taşıma güvenliği HTTP veya HTTPS üzerinden Güvenli Yuva Katmanı (SSL).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../misc/binding.md)
