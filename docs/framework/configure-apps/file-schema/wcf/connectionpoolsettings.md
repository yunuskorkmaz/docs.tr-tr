---
title: '&lt;Tcptransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 11500830c7c5fd75a9e2880a5875bd21fb070634
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltconnectionpoolsettingsgt"></a>&lt;Tcptransport&gt;
Bir adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.  
  
 \<system.serviceModel >  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<namePipeTransport >  
\<Namedpipetransport >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<connectionPoolSettings  
        groupName="String"  
    idleTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`groupName`|Giden kanallar için kullanılan bağlantı havuzu adını tanımlayan bir dize. Akış modunda bağlantıları, bağlantı havuzu devre dışı anlamına gelir paylaşılmaz. Varsayılan bir "varsayılan" dizesidir. Belirli bir istemci bağlantılarında ayrı gruplara ayırmak için bu değeri değiştirebilirsiniz.|  
|`idleTimeout`|Bir pozitif <xref:System.TimeSpan> bağlantı boşta kalabileceği kesilmeden önce en uzun süreyi belirtir. Varsayılan değer 00:02:00 ' dir.|  
|`maxOutboundConnectionsPerEndpoint`|Bağlantılar hizmeti tarafından başlatılan uzak bir uç nokta için en fazla sayısını belirtir pozitif bir tamsayı. Sınırı aşan bağlantılar, sınırın altındaki bir alan kullanılabilir duruma gelinceye kadar kuyruğa alınır. `idleTimeout` İçinde bağlantıları kalır sıraya alınmış bir özel durum önce süresini sınırlar. Varsayılan değer 10'dur.<br /><br /> Bu öznitelik, belirli bir hizmet uç noktası istemciden eşzamanlı etkin bağlantı sayısını sınırlar. Bu değer daha etkin istemci bağlantıları sağlayarak aşılırsa hizmeti istemciye yanıt vermeyen görünebilir. Bu durumda, bu değer belirli bir uç beklenen eşzamanlı istemci bağlantılarının üst sınırını aşan ayarlanması.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Connectionpoolsettings >](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|Adlandırılmış kanallar kullanarak ileti aktarılması için bir kanal neden olan bir taşıma tanımlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Taşımalar](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Taşıma Seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
