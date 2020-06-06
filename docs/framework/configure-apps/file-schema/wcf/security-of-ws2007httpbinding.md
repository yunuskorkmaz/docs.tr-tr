---
title: <security> / <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: e88f55f3651d1ccd55631dce13a0349ac2772624
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736394"
---
# <a name="security-of-ws2007httpbinding"></a>\<security> / \<ws2007HttpBinding>
Öğesiyle kullanılan güvenlik ayarlarını temsil eder [\<ws2007HttpBinding>](ws2007httpbinding.md) .  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
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
|`mode`|Seçim. Uygulanan güvenlik türünü belirtir. Varsayılan değer: `Message`.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.SecurityMode> .|  
  
## <a name="mode-attribute"></a>Mode özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`None`|Güvenlik devre dışı bırakıldı.|  
|`Transport`|Güvenlik, HTTPS kullanılarak sağlanır. Hizmetin Güvenli Yuva Katmanı (SSL) sertifikalarıyla yapılandırılması gerekir. İleti HTTPS kullanılarak tamamen güvenli hale getirilir ve hizmetin SSL sertifikası kullanılarak istemcinin kimliği doğrulanır. İstemci kimlik doğrulaması, `ClientCredentials` öğesinin özniteliği aracılığıyla denetlenir [\<transport>](transport-of-ws2007httpbinding.md) .|  
|`Message`|Güvenlik, SOAP iletisi güvenliği kullanılarak sağlanır. Varsayılan olarak, SOAP gövdesi şifrelenir ve imzalanır. Bu mod, hizmet kimlik bilgilerinin, istemci bant dışı, kullanılacak algoritma paketini ve ileti gövdesine hangi koruma düzeyi üzerinden uygulanacağını gibi çeşitli özellikler sunar <xref:System.ServiceModel.Security.SecurityMessageProperty> . İstemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.|  
|`TransportWithMessageCredential`|Bu modda, HTTPS bütünlük, gizlilik ve sunucu kimlik doğrulaması sağlar ve SOAP iletisi güvenliği istemci kimlik doğrulaması sağlar. Varsayılan olarak, istemci kimlik doğrulaması her oturum için bir kez gerçekleştirilir ve kimlik doğrulama sonuçları oturum süresince önbelleğe alınır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<transport>](transport-of-ws2007httpbinding.md)|Taşıma güvenlik ayarlarını tanımlar. Bu öğe türüne karşılık gelir <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> . Bu ayarlar yalnızca, mod aktarım olarak ayarlandığında uygulanır.|  
|[\<message>](message-of-ws2007httpbinding.md)|İleti için güvenlik ayarlarını tanımlar. Bu öğe türüne karşılık gelir <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> . Bu ayarlar, mod aktarım olarak ayarlandığında uygulanmaz.|  
  
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
- [\<binding>](bindings.md)
