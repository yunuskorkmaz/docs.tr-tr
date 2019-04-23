---
title: <connectionPoolSettings> / <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
ms.openlocfilehash: 93363c5ff1753ff02956404da7697780078c9839
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129980"
---
# <a name="connectionpoolsettings-of-tcptransport"></a>\<Namedpipetransport >, \<Connectionpoolsettings >
TCP aktarımı için ek bağlantı havuzu ayarlarını belirtir.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<Connectionpoolsettings >  
\<Namedpipetransport >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        leaseTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`groupName`|Giden kanallar için kullanılan bağlantı havuzu adını tanımlayan bir dize. Akış modunda bağlantıları, bağlantı havuzu devre dışı anlamına gelir paylaşılmaz. Varsayılan bir "varsayılan" dizesidir. Belirli bir istemci bağlantılarını ayrı gruplar halinde ayırmak için bu değeri değiştirebilirsiniz.|  
|`idleTimeout`|Bir pozitif <xref:System.TimeSpan> bağlantı boşta kalabileceği kesilmeden önce en uzun süreyi belirtir. Varsayılan değer 00:02:00 ' dir.|  
|`leaseTimeout`|A <xref:System.TimeSpan> etkin bir bağlantı kapalı geçecek süreyi belirtir. Varsayılan değer 00:05:00 ' dir.<br /><br /> Bağlantı önbelleğe ve etkin aktarım sırasında değil döndürüldü sonra bir bağlantı kapalı. Yeni bağlantı kümesi tarafından önbellek sınıra kadar her uç nokta için gereken TCP taşıma tarafından kullanılan bağlantı önbelleği oluşturur `maxOutboundConnectionsPerEndpoint.`|  
|`maxOutboundConnectionsPerEndpoint`|En fazla hizmet tarafından başlatılan bir uzak uç noktasına bağlantı sayısını belirten pozitif bir tamsayı. Sınırı aşan bağlantılar, sınırın altına bir alan kullanılabilir duruma gelene kadar kuyruğa alınır. `idleTimeout` Hangi bağlantıları kalır sıraya alınan bir özel durum önce süresini sınırlar. Varsayılan değer 10'dur.<br /><br /> Bu öznitelik istemcisi eşzamanlı etkin bağlantılar için belirli hizmet uç noktası sayısını sınırlar. Bu değer daha etkin istemci bağlantıları sağlayarak aşılıyorsa, hizmetin istemciye yanıt vermeyen görünebilir. Bu durumda, bu değeri belirli bir uç nokta için beklenen eşzamanlı istemci bağlantısına maksimum sayısını aşmaya ayarlanması.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<namedPipeTransport>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|Adlandırılmış kanalları kullanarak ileti aktarılması bir kanal neden olan bir taşıma tanımlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Taşımalar](../../../../../docs/framework/wcf/feature-details/transports.md)
- [Taşıma Seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
