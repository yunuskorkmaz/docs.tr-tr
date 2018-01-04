---
title: '&lt;tcpTransport&gt; &lt;connectionPoolSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fbc3aa7-fcc9-4193-99a3-85d31d60d3f7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f0e9c4d34caa16f41e874b7a3880325a6585c230
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltconnectionpoolsettingsgt-of-lttcptransportgt"></a>&lt;tcpTransport&gt; &lt;connectionPoolSettings&gt;
Bir TCP taşıma için ek bağlantı havuzu ayarlarını belirtir.  
  
 \<system.serviceModel >  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<Connectionpoolsettings >  
\<Namedpipetransport >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<connectionPoolSettings  
    groupName="String"  
    idleTimeout"TimeSpan"  
        leaseTimeout="TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`groupName`|Giden kanallar için kullanılan bağlantı havuzu adını tanımlayan bir dize. Akış modunda bağlantıları, bağlantı havuzu devre dışı anlamına gelir paylaşılmaz. Varsayılan bir "varsayılan" dizesidir. Belirli bir istemci bağlantılarında ayrı gruplara ayırmak için bu değeri değiştirebilirsiniz.|  
|`idleTimeout`|Bir pozitif <xref:System.TimeSpan> bağlantı boşta kalabileceği kesilmeden önce en uzun süreyi belirtir. Varsayılan değer 00:02:00 ' dir.|  
|`leaseTimeout`|A <xref:System.TimeSpan> sonra etkin bir bağlantı kapalı süreyi belirtir. Varsayılan değer 00:05:00 ' dir.<br /><br /> Bağlantı önbelleğine ve etkin iletim sırasında değil döndürüldü sonra bağlantı kapalı. Yeni bağlantılar tarafından belirlenen önbellek sınırına kadar her uç noktası için gerekli olarak TCP taşıma tarafından kullanılan bağlantı önbelleği oluşturur`maxOutboundConnectionsPerEndpoint.`|  
|`maxOutboundConnectionsPerEndpoint`|Bağlantılar hizmeti tarafından başlatılan uzak bir uç nokta için en fazla sayısını belirtir pozitif bir tamsayı. Sınırı aşan bağlantılar, sınırın altındaki bir alan kullanılabilir duruma gelinceye kadar kuyruğa alınır. `idleTimeout` İçinde bağlantıları kalır sıraya alınmış bir özel durum önce süresini sınırlar. Varsayılan değer 10'dur.<br /><br /> Bu öznitelik, belirli bir hizmet uç noktası istemciden eşzamanlı etkin bağlantı sayısını sınırlar. Bu değer daha etkin istemci bağlantıları sağlayarak aşılırsa hizmeti istemciye yanıt vermeyen görünebilir. Bu durumda, bu değer belirli bir uç beklenen eşzamanlı istemci bağlantılarının üst sınırını aşan ayarlanması.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Connectionpoolsettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|Adlandırılmış kanallar kullanarak ileti aktarılması için bir kanal neden olan bir taşıma tanımlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.TcpConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Taşımalar](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Taşıma Seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
