---
title: '&lt;Connectionpoolsettings&gt;'
ms.date: 03/30/2017
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
ms.openlocfilehash: 4141b0f6493c51048ad60accdc1d5ee9bac01231
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751083"
---
# <a name="lttcptransportgt"></a>&lt;Connectionpoolsettings&gt;
Özel bağlama için bir kanalı aktarımları iletileri tarafından kullanılabilecek bir TCP taşıma tanımlar.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<Connectionpoolsettings >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<tcpTransport   
      channelInitializationTimeout="TimeSpan"   
      connectionBufferSize="Integer"   
      hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
      listenBacklog="Integer"  
      manualAddressing="Boolean"   
      maxBufferPoolSize="Integer"  
      maxBufferSize="Integer"  
      maxOutputDelay="TimeSpan"  
      maxPendingAccepts="Integer"   
      maxPendingConnections="Integer"  
      maxReceivedMessageSize="Integer"   
      portSharingEnabled="Boolean"  
      teredoEnabled="Boolean"  
      transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse" >  
      <connectionPoolSettings  
            groupName="String"  
            idleTimeout"TimeSpan"  
            leaseTimeout="TimeSpan"  
            maxOutboundConnectionsPerEndpopint="Integer" />  
</tcpTransport>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|ChannelInitializationTimeout|Alır veya kabul edilmesi için bir kanal başlatma zaman sınırını ayarlar.  En uzun süreyi saniye cinsinden kesilmeden önce bir kanal başlatma durumda olabilir. Bu kota bir TCP bağlantısı .net kullanarak kendi kimliğini doğrulamak için atabileceğiniz saati içeren ileti çerçeveleme protokolü. Bir istemci, sunucu kimlik doğrulaması gerçekleştirmek için yeterli bilgiye sahip bazı ilk veri göndermeniz gerekir. Varsayılan değer 30 saniyedir.|  
|ConnectionBufferSize|Alır veya ayarlar istemci veya hizmet hattan serileştirilmiş iletide öbeğini iletmek için kullanılan arabellek boyutu.|  
|hostNameComparisonMode|Alır veya ana bilgisayar üzerinde URI'yi eşleştirirken hizmete erişmek için kullanılıp kullanılmayacağını belirten bir değer ayarlar.|  
|listenBacklog|Bekleyen sıraya alınan bağlantı isteği sayısının bir Web hizmeti. `connectionLeaseTimeout` Öznitelik, istemci bağlantı özel durumuyla atmadan önce bağlanması için bekleyeceği süreyi sınırlar. Bu bekleyen sıraya alınan bağlantı isteği sayısının denetleyen bir yuva düzeyi özelliktir Web hizmeti. ListenBacklog çok düşük olduğunda, WCF istekleri kabul etmeyi ve sunucu bazı varolan sıraya alınan bağlantıları kabul edene kadar bu nedenle yeni bağlantıları bırakın. 16 varsayılandır * işlemcilerin sayısı.|  
|manualAddressing|Alır veya el ile ileti adresleme gerekip gerekmediğini belirten bir değer ayarlar.|  
|maxBufferPoolSize|Alır veya ayarlar aktarım tarafından kullanılan arabellek havuzlarını en büyük boyutu.|  
|maxBufferSize|Alır veya ayarlar kullanılacak arabelleğin en büyük boyutu. Akış iletileri için bu değer arabelleğe alınan modunda okuma ileti üstbilgilerini olası en büyük boyutunu en az olmalıdır.|  
|maxOutputDelay|Alır veya üst aralığı gönderilmeden önce bir ileti veya tam bir ileti öbeğini bellekte arabelleğe alınan kalabileceği süreyi ayarlar.|  
|maxPendingAccepts|Alır veya ayarlar en fazla bekleyen zaman uyumsuz işleme gelen bağlantılar hizmeti için kullanılabilen işlemleri kabul edin.|  
|maxPendingConnections|Alır veya gönderme hizmeti üzerinde bekleyen bağlantı sayısının üst sınırını ayarlar.|  
|maxReceivedMessageSize|Alır ve alınabilmesi için izin verilen maksimum ileti boyutu ayarlar.|  
|portSharingEnabled|Bu bağlantı için TCP bağlantı noktası paylaşma etkin olup olmadığını belirten bir Boole değeri. Bu ise `false`, her bağlama kendi özel bağlantı noktasını kullanır. Varsayılan, `false` değeridir.<br /><br /> Bu ayar yalnızca Hizmetleri için geçerlidir. İstemcileri etkilenmez.<br /><br /> Bu ayarı kullanarak Windows Communication Foundation (WCF) TCP bağlantı noktası Paylaşımı hizmeti başlangıç türünü el ile veya otomatik olarak değiştirerek etkinleştirme gerektirir|  
|teredoEnabled|Teredo (güvenlik duvarının arkasındaki adresleme istemciler için bir teknoloji) etkin olup olmadığını belirten bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Bu özellik, temel alınan TCP yuva için Teredo etkinleştirir. Daha fazla bilgi için bkz: [Teredo genel bakış](http://go.microsoft.com/fwlink/?LinkId=95339).<br /><br /> Bu özellik yalnızca geçerli [!INCLUDE[wxpsp2](../../../../../includes/wxpsp2-md.md)] ve [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)]. [!INCLUDE[wv](../../../../../includes/wv-md.md)] Teredo için bir makine genelinde yapılandırma seçeneği vardır şekilde Vista çalıştırırken, bu özellik yoksayılır. Teredo, hizmet ve istemci makineleri yüklenip Teredo kullanımı için yapılandırıldığını Microsoft IPv6 yığını sahip olmasını gerektirir. Teredo yapılandırma hakkında daha fazla bilgi için bkz: [Teredo genel bakış](http://go.microsoft.com/fwlink/?LinkId=95339). Daha fazla bilgi için bkz: [Windows Server 2003 teknolojisi merkezleri](http://go.microsoft.com/fwlink/?LinkId=49888).|  
|transferMode|Alır veya iletilerin ara belleğe veya ile bağlantı yönelimli aktarma akışı olup olmadığını belirten bir değer ayarlar.|  
|connectionPoolSettings|Bir adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama özelliklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 URI biçiminde bu aktarım kullanır "net.tcp://hostname: bağlantı noktası/yol". URI bileşenlerle isteğe bağlıdır.  
  
 `tcpTransport` Öğesidir başlangıç noktası için bir özel, bağlama oluşturma TCP aktarım protokolünü uygular. Bu aktarım WCF WCF iletişimi için optimize edilmiştir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.TcpTransportElement>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Taşımalar](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [Taşıma Seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
