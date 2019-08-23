---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 5c9dbec13dd0d71ba1b92ea971d067540013b6f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940316"
---
# <a name="websocketsettings"></a>\<webSocketSettings >
Web yuva ayarlarını belirtmek için kullanılan bir yapılandırma öğesi.  
  
\<system.ServiceModel>  
\<bağlama >  
\<netHttpBinding>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="Boolean"
                       disablePayloadMasking="Boolean"
                       keepAliveInterval="TimeSpan"
                       maxPendingConnections="Integer"
                       receiveBufferSize="Integer"
                       sendBufferSize="Integer"
                       subProtocol="String"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Createnocertificate Ationonconnection|Bağlantı kurulduğunda bir bildirimin gönderilip gönderilmeyeceğini belirtir.|  
|Disablepayloadmaskeleme|Web yuva maskeleme 'nin devre dışı bırakılıp bırakılmadığını belirtir.|  
|Keepaliveınterval|Canlı tut aralığını belirtir.|  
|maxPendingConnections|Hizmette gönderimi bekleyen en fazla bağlantı sayısını belirtir.|  
|receiveBufferSize|Alma arabelleğinin boyutunu belirtir.|  
|sendBufferSize|Gönderme arabelleğinin boyutunu belirtir.|  
|Alt protokolü|Web yuvası alt protokolünü belirtir.|  
|transportUsage|Web Yuvaları ne zaman kullanılacağını belirtir.|  
  
## <a name="transportusage-attribute"></a>transportUsage özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|WhenDuplex|Sözleşme çift yönlü olduğunda Web soketi protokolünü kullanın.|  
|Her zaman|Sözleşmeye bakılmaksızın her zaman Web soketi protokolünü kullanın.|  
|hiçbir zaman|Web yuvası protokolünü hiçbir şekilde kullanmayın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|\<netHttpBinding>|NetHttpBinding belirtir|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, \<WebSocketSettings > öğesinin nasıl kullanılacağını gösterir.  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="true"
                       disablePayloadMasking="false"
                       keepAliveInterval="00:10:00"
                       maxPendingConnections="100"
                       receiveBufferSize="1000"
                       sendBufferSize="1000"
                       subProtocol="Soap"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../misc/binding.md)
