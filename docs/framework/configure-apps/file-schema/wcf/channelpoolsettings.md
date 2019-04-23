---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: ca1f680e2de67984dfcec49b3d262799000a2625
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102589"
---
# <a name="channelpoolsettings"></a>\<channelPoolSettings >
Özel bağlama için kanal havuzu ayarlarını belirtir.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<oneWay>  
\<channelPoolSettings >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`idleTimeout`|Bir pozitif <xref:System.TimeSpan> havuzdaki kanalların boşta kalabileceği kesilmeden önce en uzun süreyi belirtir. Varsayılan değer 00:02:00 ' dir.|  
|`leaseTimeout`|A <xref:System.TimeSpan> sonra havuza geri döndürülen bir kanal kapalı zaman aralığını belirtir. Varsayılan değer 00:10:00 ' dir.|  
|`maxOutboundChannelsPerEndpoint`|Her uzak uç noktası için havuzda depolanabilen kanal maksimum sayısını belirten pozitif bir tamsayı. Varsayılan değer 10'dur.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<oneWay>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|Paket için özel bir bağlama yönlendirme sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kotalar, kaynakların aşırı kullanımını önlemek için bir ilke mekanizması kullanılır. Bunlar, kötü amaçlı veya istenmeyen hizmet reddi (DOS) saldırıları engeller. Bu öğe, kanal kotalar özel bir kanalda ayarlarken kullanın.  
  
 `ChannelPoolSettings` üç kotaları belirtir:  
  
-   `idleTimeout` Kota, sunucu üzerinde uzun bir süre için kaynakları bağlamadan üzerinde kullanan hizmet reddi (DOS) saldırıları azaltmak için kullanılır. İstemcide, doğru değeri ayarı ile hizmetine güvenilirliğini artırabilirsiniz. Varsayılan değer, bir ölçülü uygun kaynakların ayrılması üzerinde temel alır. Bu, bir geliştirme ortamı ve küçük yükleme senaryoları için uygundur. Hizmet yöneticileri, bir yükleme kaynaklar yetersiz çalışıyorsa veya ek kaynakların kullanılabilirliğini rağmen bağlantı sayısı değeri gözden geçirmelidir.  
  
-   `leaseTimeout` Kotası için kullanılan yük Dengeleyiciler ile tümleştirme ve güvenilirliği için. Varsayılan değer, bir Klasik kaynakların ayrılması üzerinde temel alır. Bu, bir geliştirme ortamı ve küçük yükleme senaryoları için uygundur. Hizmet yöneticileri, bir yükleme kaynaklar yetersiz çalışıyorsa veya ek kaynakların kullanılabilirliğini rağmen bağlantı sayısı değeri gözden geçirmelidir.  
  
-   `maxOutboundChannelsPerEndpoint` Kota önbellek sınırlarını hem sunucu hem de istemci üzerinde ayarlar ve güvenilirliğini artırmak için kullanılır. Varsayılan değer, bir geliştirme ortamı ve küçük yükleme senaryoları için uygun olan ölçülü uygun kaynakların ayrılması dayanır. Hizmet yöneticileri, bir yükleme kaynaklar yetersiz çalışıyorsa veya ek kaynakların kullanılabilirliğini rağmen bağlantı sayısı değeri gözden geçirmelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<oneWay>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
