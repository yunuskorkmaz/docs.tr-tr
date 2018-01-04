---
title: "&lt;udpAnnouncementEndpoint&gt; için &lt;udpTransportSettings&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7ddff1a-5eed-4bbc-8580-b95ef8890e1f
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a5de8d55d34c2db0d0b1efd5a05024f1dbc4f42
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltudptransportsettingsgt-of-ltudpannouncementendpointgt"></a>&lt;udpAnnouncementEndpoint&gt; için &lt;udpTransportSettings&gt;
Bu yapılandırma öğesi için UDP taşıma ayarları gösteren [ \<udpAnnoucementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpannoucementendpoint.md).  
  
\<Sistem. ServiceModel >  
\<standardEndpoints >  
\<Udptransportsettings >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <udpAnnouncementEndpoint>
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
    </udpAnnouncementEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|duplicateMessageHistoryLength|Yinelenen iletileri tanımlamak için aktarım tarafından kullanılan ileti karmaları en fazla sayısını belirten bir tamsayı.  Yinelenen algılama TransportManager düzeyinde gerçekleştirilir. Bu özellik 0 olarak ayarlanması yinelenen algılama devre dışı bırakır.<br /><br /> Bu öznitelik, sistem yöneticileri veya yinelenen ileti algılama algoritmalarını devre dışı bırakma geliştiriciler sağlar. Bu, kendi yinelenen algılama algoritması uygulamak istiyorsanız tercih edilebilir.<br /><br /> 4112 varsayılandır.|  
|maxBufferPoolSize|Arabellek havuzlarını aktarım tarafından kullanılan en büyük boyutunu belirten bir tamsayı.|  
|maxMulticastRetransmitCount|En fazla kaç kez ileti (ilk gönderme ek olarak) iletilmelidir belirten bir tamsayı.<br /><br /> Varsayılan değer 2'dir.|  
|maxPendingMessageCount|Aldı, ancak henüz bir tek kanal örneğinin InputQueue kaldırıldı iletilerinin sayısını belirten bir tamsayı.  InputQueue bekleyen ileti sayısı sınırına erişti, ileti bırakılır.<br /><br /> Varsayılan değer 32'dir.|  
|MaxReceivedMessageSize|Bağlama tarafından işlenebilen bir ileti boyutu üst sınırı belirten bir tamsayı.<br /><br /> 65507 varsayılan değerdir.|  
|maxUnicastRetransmitCount|En fazla kaç kez ileti (ilk gönderme ek olarak) iletilmelidir belirten bir tamsayı.  İleti bir tek noktaya yayın adresine gönderilir ve karşılık gelen bir RelatesTo üstbilgiyle bir yanıt iletisi aldı, aktarım erken (yapılandırılmış kaç kez yeniden göndermeden önce) sonlandırabilir.<br /><br /> Varsayılan değer 1’dir.|  
|multicastInterfaceId|Çok noktaya yayın trafiğine çok ana bilgisayarlı makinelerdeki gönderilip alınırken kullanılması gereken ağ bağdaştırıcısı benzersiz olarak tanımlayan bir dize. Çalışma zamanında, daha sonra ayarlamak için kullanılan arabirim dizinini aramak için bu öznitelik değeri aktarımını kullanacak `IP_MULTICAST_IF` ve `IPV6_MULTICAST_IF` yuva seçenekleri.  Aynı arabirim dizinini çok noktaya yayın grubu eklerken varsa kullanılır.<br /><br /> Varsayılan değer `null` şeklindedir.|  
|socketReceiveBufferSize|Temel alınan WinSock yuvası üzerinde alış arabelleği boyutu belirten bir tamsayı.<br /><br /> Bir kullanıcı bir alıcı kanalının bu öznitelik veri aldığında sistem nasıl davranacağını denetlemek için bağlamada kullanın.  Örneğin, gelen WCF iletileri maksimum eşik kullanan bir uygulama göz önüne alındığında, bu öznitelik için daha yüksek bir değer kullanarak uygulamayı bunları işleyebilmesi için beklenirken WinSock arabellekte yığın iletileri olanak tanır.  Daha düşük bir değere aynı durumda kullanarak kesiliyor iletilerinde neden olur. Bu öznitelik temel WinSock gösterir `SO_RCVBUF` yuva seçeneği. Bu öznitelik değeri boyutu en az olmalıdır `maxReceivedMessageSize`.   Bir değere küçüktür ayarlamak `maxReceivedMessageSize` çalışma zamanı özel durumuna neden.<br /><br /> Varsayılan değer 65536'dır.|  
|TimeToLive|Çok noktaya yayın paketinin erişebilen ağ kesimi durak sayısını belirten bir tamsayı.  Bu öznitelik ile ilişkili işlevselliği kullanıma sunan `IP_MULTICAST_TTL` ve `IP_TTL` yuva seçenekleri.<br /><br /> Varsayılan değer 1’dir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<udpAnnoucementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpannoucementendpoint.md)|Sözleşme ve UDP bağlama aktarım duyuru sabit sahip standart uç noktası.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Discovery.UdpTransportSettings>
