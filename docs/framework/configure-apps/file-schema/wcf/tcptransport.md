---
title: '&lt;Connectionpoolsettings&gt;'
ms.date: 03/30/2017
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
ms.openlocfilehash: 92590f556d93859e8681eea8f8f05da4f560e150
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43563945"
---
# <a name="lttcptransportgt"></a>&lt;Connectionpoolsettings&gt;
Özel bağlama için iletileri için bir kanal tarafından kullanılabilen bir TCP taşıması tanımlar.  
  
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
|ChannelInitializationTimeout|Alır veya ayarlar zaman sınırını kabul edilmesi için bir kanal başlatılıyor.  En uzun süreyi saniye cinsinden kesilmeden önce bir kanal başlatma durumda olabilir. TCP bağlantısı, .net kullanarak kendi kimliğini doğrulamak için gerçekleştirebileceğiniz zaman bu kotayı içeren ileti çerçeveleme protokolü. Sunucu kimlik doğrulaması gerçekleştirmek için yeterli bilgiye sahip önce bazı ilk veri göndermek bir istemci gerekir. Varsayılan değer 30 saniyedir.|  
|ConnectionBufferSize|Alır veya ayarlar istemci veya hizmet serileştirilmiş ileti öbeğini iletmek için kullanılan arabellek boyutu.|  
|hostNameComparisonMode|Alır veya ayarlar üzerinde URI'yi eşleştirirken hizmete erişmek için ana bilgisayar adının kullanılıp kullanılmadığını gösteren bir değer.|  
|listenBacklog|Bekleyen sıraya alınan bağlantı isteklerinin sayısı için bir Web hizmeti. `connectionLeaseTimeout` Öznitelik sınırlar istemci bağlantısı özel durumu atamadan önce bağlanması için bekleyeceği süre. Bu bekleyen sıraya alınan bağlantı isteklerinin sayısı denetleyen bir yuva düzeyi özelliktir bir Web hizmeti için. ListenBacklog çok düşük olduğunda, WCF istekleri kabul etmeyi ve sunucunun mevcut sıraya alınan bağlantıların bazıları kabul edene kadar bu nedenle yeni bağlantıları bırakın. Varsayılan değer 16 * işlemci sayısı.|  
|manualAddressing|Alır veya iletinin el ile adresleme gerekli olup olmadığını gösteren bir değer ayarlar.|  
|maxBufferPoolSize|Alır veya taşıma tarafından kullanılan tüm arabellek havuzu en büyük boyutunu ayarlar.|  
|maxBufferSize|Alır veya kullanılacak arabelleğin en büyük boyutunu ayarlar. Akış iletileri için bu değer, arabelleğe alınmış modda okuma ait ileti üstbilgilerini olası en büyük boyutunu en az olmalıdır.|  
|MaxOutputDelay|Alır veya gönderilmeden önce ileti veya tam bir ileti bir öbek bellekte arabelleğe alınan kalabileceği süreyi en uzun aralığı ayarlar.|  
|maxPendingAccepts|Alır veya ayarlar sayısı bekleyen zaman uyumsuz işlem hizmetine gelen bağlantılar için kullanılabilen işlemleri kabul edin.|  
|maxPendingConnections|Alır veya ayarlar gönderme hizmetinde bekleyen bağlantıları sayısı.|  
|maxReceivedMessageSize|Alır ve alınabilir izin verilen en büyük ileti boyutunu ayarlar.|  
|portSharingEnabled|Bu bağlantı için TCP bağlantı noktası paylaşımının etkin olup olmadığını belirten bir Boole değeri. Bu ise `false`, her bir bağlaması, kendi özel bağlantı noktasını kullanır. Varsayılan, `false` değeridir.<br /><br /> Bu ayar yalnızca hizmetler için geçerlidir. İstemciler etkilenmez.<br /><br /> Bu ayar kullanılarak el ile veya otomatik başlangıç türünü değiştirerek Windows Communication Foundation (WCF) TCP bağlantı noktası paylaşım hizmetini etkinleştirme gerektirir|  
|teredoEnabled|Teredo (güvenlik duvarının arkasındaki istemcilere için bir teknoloji) etkin olup olmadığını belirten bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Bu özellik, temel alınan bir TCP yuva için Teredo etkinleştirir. Daha fazla bilgi için [Teredo genel bakış](https://go.microsoft.com/fwlink/?LinkId=95339).<br /><br /> Bu özellik yalnızca geçerli [!INCLUDE[wxpsp2](../../../../../includes/wxpsp2-md.md)] ve [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)]. [!INCLUDE[wv](../../../../../includes/wv-md.md)] Teredo için bir makine genelindeki yapılandırma seçeneği etkin şekilde Vista çalıştırırken bu özellik yoksayılır. Teredo, hizmet ve istemci makineleri düzgün yüklendiğinden ve Teredo kullanım için yapılandırıldığından Microsoft IPv6 yığın olmasını gerektirir. Teredo yapılandırma hakkında daha fazla bilgi için bkz. [Teredo genel bakış](https://go.microsoft.com/fwlink/?LinkId=95339). Daha fazla bilgi için [Windows Server 2003 teknoloji merkezlerinde](https://go.microsoft.com/fwlink/?LinkId=49888).|  
|transferMode|Alır veya iletileri ara belleğe veya akışa ile bağlantı sağlamaya yönelik aktarım gösteren bir değer ayarlar.|  
|connectionPoolSettings|Adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu aktarım biçiminde bir URI'leri kullanır "net.tcp://hostname: port/yol". Diğer URI bileşenlerini isteğe bağlıdır.  
  
 `tcpTransport` Öğe başlangıç noktası olan TCP Aktarım Protokolü uygulayan özel bağlamayı oluşturmak için. Bu aktarım WCF WCF iletişim için optimize edilmiştir.  
  
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
