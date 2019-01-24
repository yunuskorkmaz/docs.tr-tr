---
title: '&lt;Udpannouncementendpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 842d92e9-6199-4ec5-b2d1-58533054e1f0
ms.openlocfilehash: 58931cb70f83378740093615adf89a437e32ff2e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667199"
---
# <a name="ltudptransportsettingsgt"></a>&lt;Udpannouncementendpoint&gt;
Bu yapılandırma öğesi için UDP taşıma ayarları sunan [ \<udpDiscoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md).  
  
\<system.ServiceModel>  
\<standardEndpoints >  
\<udpDiscoveryEndpoint >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint>
        <updTransportSettings duplicateMessageHistoryLength="Integer"
                              maxBufferPoolSize="Integer"
                              maxMulticastRetransmitCount="Integer"
                              maxPendingMessageCount="Integer"
                              maxReceivedMessageSize="Integer"
                              maxUnicastRetransmitCount="Integer"
                              multicastInterfaceId="String"
                              socketReceiveBufferSize="Integer"
                              timeToLive="Integer" />
      </standardEndpoint>
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|duplicateMessageHistoryLength|Yinelenen iletileri tanımlamak için taşıma tarafından kullanılan ileti karmaları en fazla sayısını belirten bir tamsayı.  Yinelenen algılama TransportManager düzeyinde gerçekleştirilir. Bu özelliğin 0 olarak ayarlanması, yinelenen algılama devre dışı bırakır.<br /><br /> Bu öznitelik, sistem yöneticileri veya yinelenen ileti algılama algoritmalarını etkinleştirmek için geliştiricilerin sağlar. Bu, kendi yinelenen algılama algoritması uygulamak istiyorsanız istenebilir.<br /><br /> 4112 varsayılandır.|  
|maxBufferPoolSize|Taşıma tarafından kullanılan tüm arabellek havuzu en büyük boyutunu belirten bir tamsayı.|  
|maxMulticastRetransmitCount|İleti (ek olarak ilk gönderme) iletilmelidir maksimum sayısını belirten bir tamsayı.<br /><br /> Varsayılan değer 2'dir.|  
|maxPendingMessageCount|Aldı, ancak henüz bir tek bir kanalı örneği için InputQueue kaldırılır iletilerinin maksimum sayısını belirten bir tamsayı.  InputQueue bekleyen ileti sayısı sınırına erişti, ileti bırakılır.<br /><br /> Varsayılan değer 32'dir.|  
|maxReceivedMessageSize|Bağlama tarafından işlenebilen bir ileti boyut üst sınırını belirten bir tamsayı.<br /><br /> 65507 varsayılan değerdir.|  
|maxUnicastRetransmitCount|İleti (ek olarak ilk gönderme) iletilmelidir maksimum sayısını belirten bir tamsayı.  İleti bir tek noktaya yayın adresine gönderilir ve karşılık gelen bir RelatesTo üst bilgisi ile bir yanıt iletisi alındığında, yeniden iletim erken (yapılandırılmış kaç kez yeniden göndermeden önce) sonlandırabilir.<br /><br /> Varsayılan değer 1’dir.|  
|multicastInterfaceId|Çok noktaya yayın trafiğine çok ana bilgisayarlı makinelerde gönderip kullanılmalıdır ağ bağdaştırıcısı benzersiz olarak tanımlayan bir dize. Çalışma zamanında, ardından ayarlamak için kullanılan arabirim dizinini aramak için bu öznitelik değeri aktarımını kullanacak `IP_MULTICAST_IF` ve `IPV6_MULTICAST_IF` yuva seçenekleri.  Aynı arabirim dizinini çok noktaya yayın grubu birleştirilirken varsa kullanılır.<br /><br /> Varsayılan değer `null` şeklindedir.|  
|socketReceiveBufferSize|Temel alınan WinSock yuva alma arabellek boyutunu belirten bir tamsayı.<br /><br /> Bir kullanıcı teslim alma kanal veri aldığında sistem nasıl davranacağını denetlemek için Binding üstündeki bu özniteliği kullanabilirsiniz.  Örneğin, gelen WCF iletileri en yüksek eşik kullanan bir uygulamayı göz önünde bulundurulduğunda, bu öznitelik için daha yüksek bir değer kullanarak uygulamayı bunları işleyebilmesi için beklenirken WinSock arabellekteki karşılaştırın iletileri çalıştırmasına olanak tanır.  Daha düşük bir değere aynı durumda kullanarak bırakılmak iletilerinde neden olur. Bu öznitelik temel alınan WinSock sunan `SO_RCVBUF` yuva seçeneği. Bu öznitelik değeri en az boyutu olmalıdır `maxReceivedMessageSize`.   Bu daha küçük bir değere ayarlanması `maxReceivedMessageSize` bir çalışma zamanı özel durumuna neden.<br /><br /> 65536 varsayılan değerdir.|  
|timeToLive|Çok noktaya yayın paketi erişebilen ağ segment durak sayısını belirten bir tamsayı.  Bu öznitelik ile ilişkili işlevselliği kullanıma sunan `IP_MULTICAST_TTL` ve `IP_TTL` yuva seçenekleri.<br /><br /> Varsayılan değer 1’dir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<udpDiscoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md)|Bulma bağlama sözleşme ve UDP taşıma düzeltmiştir standart bitiş noktası.|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Discovery.UdpTransportSettings>
