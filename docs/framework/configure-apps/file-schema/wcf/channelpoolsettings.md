---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: dd81821c74678cae8602458fe796a72bf5d379e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919553"
---
# <a name="channelpoolsettings"></a>\<channelPoolSettings >
Özel bağlama için kanal havuzu ayarlarını belirtir.  
  
 \<system.serviceModel>  
\<bağlama >  
\<customBinding >  
\<bağlama >  
\<tek yönlü >  
\<channelPoolSettings >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`idleTimeout`|Havuzdaki kanalların <xref:System.TimeSpan> kesilmeden önce boşta kalabileceği maksimum süreyi belirten bir pozitif değer. Varsayılan değer 00:02:00 ' dir.|  
|`leaseTimeout`|Bir <xref:System.TimeSpan> kanalın, havuzdan döndürülmeden sonraki zaman aralığını belirtir. Varsayılan değer 00:10:00 ' dir.|  
|`maxOutboundChannelsPerEndpoint`|Her bir uzak uç nokta için havuzda depolanabilen en fazla kanal sayısını belirten pozitif bir tamsayı. Varsayılan değer 10 ' dur.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<tek yönlü >](oneway.md)|Özel bağlama için paket yönlendirmeye izin vermez.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kotalar, aşırı kaynak tüketimini engellemek için bir ilke mekanizması olarak kullanılır. Kötü amaçlı ya da istenmeden hizmet reddi (DOS) saldırılarını engeller. Özel bir kanalda kanal kotalarını ayarlarken bu öğeyi kullanın.  
  
 `ChannelPoolSettings`Üç kota belirtir:  
  
- `idleTimeout` Kota, kaynakları uzun bir süre için bağlama kullanan sunucuda hizmet reddi (DOS) saldırılarını azaltmak için kullanılır. İstemcide, doğru değeri ayarlamak, hizmetle bağlantı kurma güvenilirliğini artırabilir. Varsayılan değer, kaynakların koruma altına göre ayrılmasını temel alır. Geliştirme ortamı ve küçük yükleme senaryoları için uygundur. Yükleme kaynakları tükeniyorsa veya ek kaynakların kullanılabilirliğine karşın bağlantıların sınırlandırılmaları durumunda hizmet yöneticileri bu değeri incelemelidir.  
  
- Kota `leaseTimeout` , yük dengeleyiciler ile tümleştirme için ve güvenilirliği iyileştirmek için kullanılır. Varsayılan değer, kaynakların klasik bir ayırmasını temel alır. Geliştirme ortamı ve küçük yükleme senaryoları için uygundur. Yükleme kaynakları tükeniyorsa veya ek kaynakların kullanılabilirliğine karşın bağlantıların sınırlandırılmaları durumunda hizmet yöneticileri bu değeri incelemelidir.  
  
- `maxOutboundChannelsPerEndpoint` Kota, hem sunucu hem de istemci üzerindeki önbellek sınırlarını ayarlar ve güvenilirliği artırmak için kullanılır. Varsayılan değer, bir geliştirme ortamı ve küçük yükleme senaryoları için uygun olan kaynakların koruma altına dayalı bir şekilde ayrılmasını temel alır. Yükleme kaynakları tükeniyorsa veya ek kaynakların kullanılabilirliğine karşın bağlantıların sınırlandırılmaları durumunda hizmet yöneticileri bu değeri incelemelidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<tek yönlü >](oneway.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
