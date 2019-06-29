---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 0e56bb5c9e485559d712281a51e79f54c9661b5a
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423132"
---
# <a name="connectionpoolsettings"></a>\<Namedpipetransport >
Adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<namePipeTransport>  
\<Namedpipetransport >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`groupName`|Giden kanallar için kullanılan bağlantı havuzu adını tanımlayan bir dize. Akış modunda bağlantıları, bağlantı havuzu devre dışı anlamına gelir paylaşılmaz. Varsayılan bir "varsayılan" dizesidir. Belirli bir istemci bağlantılarını ayrı gruplar halinde ayırmak için bu değeri değiştirebilirsiniz.|  
|`idleTimeout`|Bir pozitif <xref:System.TimeSpan> bağlantı boşta kalabileceği kesilmeden önce en uzun süreyi belirtir. Varsayılan değer 00:02:00 ' dir.|  
|`maxOutboundConnectionsPerEndpoint`|En fazla hizmet tarafından başlatılan bir uzak uç noktasına bağlantı sayısını belirten pozitif bir tamsayı. Sınırı aşan bağlantılar, sınırın altına bir alan kullanılabilir duruma gelene kadar kuyruğa alınır. `idleTimeout` Hangi bağlantıları kalır sıraya alınan bir özel durum önce süresini sınırlar. Varsayılan değer 10'dur.<br /><br /> Bu öznitelik istemcisi eşzamanlı etkin bağlantılar için belirli hizmet uç noktası sayısını sınırlar. Bu değer daha etkin istemci bağlantıları sağlayarak aşılıyorsa, hizmetin istemciye yanıt vermeyen görünebilir. Bu durumda, bu değeri belirli bir uç nokta için beklenen eşzamanlı istemci bağlantısına maksimum sayısını aşmaya ayarlanması.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<namedPipeTransport>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|Adlandırılmış kanalları kullanarak ileti aktarılması bir kanal neden olan bir taşıma tanımlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Taşımalar](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Taşıma Seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
