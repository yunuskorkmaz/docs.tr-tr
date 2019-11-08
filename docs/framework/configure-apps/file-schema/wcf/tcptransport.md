---
title: <tcpTransport>
ms.date: 03/30/2017
ms.assetid: 8fcd18c1-9958-42e7-b442-7903f7bdb563
ms.openlocfilehash: 6761d090206e55e58001ea2bb885eaa69f26d9eb
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738643"
---
# <a name="tcptransport"></a>\<tcpTransport >
Özel bir bağlama için iletileri aktarmak amacıyla bir kanal tarafından kullanılabilen bir TCP taşıması tanımlar.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<tcpTransport >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<tcpTransport channelInitializationTimeout="TimeSpan"
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
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          leaseTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</tcpTransport>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|ChannelInitializationTimeout|Kabul edilecek bir kanalın başlatılması için zaman sınırını alır veya ayarlar.  Bir kanalın, saniyeler içinde kesilmeden önce başlatma durumunda olabilecek en uzun süre. Bu kota, bir TCP bağlantısının, .NET Ileti çerçeveleme protokolünü kullanarak kimliğini doğrulamak için zaman alabilir. Sunucunun kimlik doğrulamasını gerçekleştirmek için yeterli bilgi olmadan önce bir istemcinin bazı ilk verileri gönderebilmesi gerekir. Varsayılan değer 30 saniyedir.|  
|connectionBufferSize|İstemci veya hizmetten alınan bir seri hale getirilmiş ileti öbeğini iletmek için kullanılan arabelleğin boyutunu alır veya ayarlar.|  
|hostNameComparisonMode|URI ile eşleştirilirken, ana bilgisayar adının hizmete erişmek için kullanılıp kullanılmadığını gösteren bir değer alır veya ayarlar.|  
|listenBacklog|Bir Web hizmeti için bekleyen sıraya alınmış bağlantı isteği sayısı üst sınırı. `connectionLeaseTimeout` özniteliği, bir bağlantı özel durumu oluşturmadan önce istemcinin bağlı olmasını bekleyeceği süreyi sınırlandırır. Bu, bir Web hizmeti için Beklemede olabilecek en fazla sıraya alınmış bağlantı isteği sayısını denetleyen bir yuva düzeyi özelliğidir. ListenBacklog çok düşük olduğunda, WCF istekleri kabul etmeyi durdurur ve bu nedenle sunucu, mevcut sıraya alınmış bağlantılardan bazılarını yapana kadar yeni bağlantı vermez. Varsayılan değer 16 * işlemci sayısıdır.|  
|manualAddressing|İletinin el ile adreslenmesi gerekip gerekmediğini gösteren bir değer alır veya ayarlar.|  
|maxBufferPoolSize|Taşıma tarafından kullanılan tüm arabellek havuzlarının en büyük boyutunu alır veya ayarlar.|  
|maxBufferSize|Kullanılacak arabelleğin en büyük boyutunu alır veya ayarlar. Akışlı iletiler için bu değer en azından, arabelleğe alınmış modda okunan ileti üstbilgilerinin en büyük olası boyutu olmalıdır.|  
|maxOutputDelay|Bir ileti öbeğinin veya bir tam iletinin gönderilmeden önce bellekte ara belleğe kalabileceği maksimum zaman aralığını alır veya ayarlar.|  
|maxPendingAccepts|Hizmete gelen bağlantıları işlemek için kullanılabilen bekleyen zaman uyumsuz kabul etme işlemlerinin maksimum sayısını alır veya ayarlar.|  
|maxPendingConnections|Hizmette gönderimi bekleyen en fazla bağlantı sayısını alır veya ayarlar.|  
|Değerini|Alınabilecek izin verilen en fazla ileti boyutunu alır ve ayarlar.|  
|portSharingEnabled|Bu bağlantı için TCP bağlantı noktası paylaşımının etkin olup olmadığını belirten bir Boole değeri. Bu `false`, her bağlama kendi özel bağlantı noktasını kullanır. Varsayılan, `false` değeridir.<br /><br /> Bu ayar yalnızca hizmetler için geçerlidir. İstemciler etkilenmez.<br /><br /> Bu ayarın kullanılması için, başlangıç türünü el Ile veya otomatik olarak değiştirerek Windows Communication Foundation (WCF) TCP bağlantı noktası paylaşım hizmeti 'nin etkinleştirilmesi gerekir|  
|teredoEnabled|Teredo 'Nun (güvenlik duvarlarının arkasındaki istemcileri adresleme teknolojisinin) etkin olup olmadığını belirten bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Bu özellik, temel alınan TCP yuvası için Teredo 'Yu sunar. Daha fazla bilgi için bkz. [Teredo 'Ya genel bakış](https://go.microsoft.com/fwlink/?LinkId=95339).<br /><br /> Bu özellik yalnızca [!INCLUDE[wxpsp2](../../../../../includes/wxpsp2-md.md)] ve [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)]uygulanabilir. [!INCLUDE[wv](../../../../../includes/wv-md.md)], Teredo için makine genelinde bir yapılandırma seçeneğine sahiptir, bu nedenle Vista çalıştırılırken bu özellik yok sayılır. Teredo, istemci ve hizmet makinelerinin hem Microsoft IPv6 yığınının yüklü olmasını hem de Teredo kullanımı için doğru şekilde yapılandırılmasını gerektirir. Teredo yapılandırma hakkında daha fazla bilgi için bkz. [Teredo 'Ya genel bakış](https://go.microsoft.com/fwlink/?LinkId=95339). Daha fazla bilgi için bkz. [Windows Server 2003 teknoloji merkezleri](https://go.microsoft.com/fwlink/?LinkId=49888).|  
|transferMode|İletilerin arabelleğe alınıp alınmayacağını veya bağlantı yönelimli aktarımla akışını gösteren bir değer alır veya ayarlar.|  
|connectionPoolSettings|Adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\< bağlama >](bindings.md)|Özel bağlamanın tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu aktarım, "net. TCP:/hostname: Port/path" biçimindeki URI 'Leri kullanır. Diğer URI bileşenleri isteğe bağlıdır.  
  
 `tcpTransport` öğesi, TCP aktarma protokolünü uygulayan özel bir bağlama oluşturmak için başlangıç noktasıdır. Bu aktarım, WCF-WCF iletişimi için iyileştirilmiştir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.TcpTransportElement>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Taşımalar](../../../wcf/feature-details/transports.md)
- [Taşıma Seçme](../../../wcf/feature-details/choosing-a-transport.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
