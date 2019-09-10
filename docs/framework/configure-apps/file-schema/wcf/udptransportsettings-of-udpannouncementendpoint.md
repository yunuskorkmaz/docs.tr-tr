---
title: <udpTransportSettings> / <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: a7ddff1a-5eed-4bbc-8580-b95ef8890e1f
ms.openlocfilehash: b67bdf825948dffe18aabe91b0de236eb929bccc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854854"
---
# <a name="udptransportsettings-of-udpannouncementendpoint"></a>\<\<UdpAnnouncementEndpoint > UdpTransportSettings >
Bu yapılandırma öğesi [ \<UdpAnnouncementEndpoint >](udpannouncementendpoint.md)için UDP taşıma ayarlarını gösterir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<udpAnnouncementEndpoint >** ](udpannouncementendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<updTransportSettings >**  

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
|Duplicatemessagegeçmişini uzunluğu|Yinelenen iletileri tanımlamak için taşıma tarafından kullanılan en fazla ileti karması sayısını belirten bir tamsayı.  Yinelenen algılama işlemi, TransportManager düzeyinde yapılır. Bu özelliğin 0 olarak ayarlanması yinelenen algılamayı devre dışı bırakır.<br /><br /> Bu öznitelik, sistem yöneticilerinin veya geliştiricilerin yinelenen ileti algılama algoritmalarını kapatmasına izin verir. Kendi yinelenen algılama algoritmanızı uygulamak istiyorsanız bu işlem istenebilir.<br /><br /> Varsayılan değer 4112 ' dir.|  
|maxBufferPoolSize|Taşıma tarafından kullanılan tüm arabellek havuzlarının en büyük boyutunu belirten bir tamsayı.|  
|maxMulticastRetransmitCount|İletinin en fazla kaç kez yeniden gönderilmesi gerektiğini belirten bir tamsayı (ilk gönderme 'ya ek olarak).<br /><br /> Varsayılan değer 2 ' dir.|  
|maxPendingMessageCount|Tek bir kanal örneği için InputQueue öğesinden alınmış ancak henüz kaldırılmayan en fazla ileti sayısını belirten bir tamsayı.  InputQueue, bekleyen ileti sayısı sınırına ulaşmışsa ileti bırakılır.<br /><br /> Varsayılan değer 32 ' dir.|  
|maxReceivedMessageSize|Bağlama tarafından işlenebilecek bir iletinin en büyük boyutunu belirten bir tamsayı.<br /><br /> Varsayılan değer 65507 ' dir.|  
|maxUnicastRetransmitCount|İletinin en fazla kaç kez yeniden gönderilmesi gerektiğini belirten bir tamsayı (ilk gönderme 'ya ek olarak).  İleti bir tek noktaya yayın adresine gönderilirse ve karşılık gelen bir RelatesTo üstbilgisiyle yanıt iletisi alındığında, yeniden iletim erken sonlandırılabilir (yapılandırılan sayıda yeniden gönderilmeden önce).<br /><br /> Varsayılan değer 1’dir.|  
|multicastInterfaceId|Çoklu bilgisayarlı makinelerde çok noktaya yayın trafiği gönderirken ve alırken kullanılması gereken ağ bağdaştırıcısını benzersiz şekilde tanımlayan bir dize. Çalışma zamanında, aktarım bu öznitelik değerini, daha sonra `IP_MULTICAST_IF` ve `IPV6_MULTICAST_IF` yuva seçeneklerini ayarlamak için kullanılan arabirim dizinini aramak için kullanır.  Varsa, çok noktaya yayın grubuna katılırken de aynı arabirim dizini kullanılacaktır.<br /><br /> Varsayılan değer `null` şeklindedir.|  
|socketReceiveBufferSize|Temeldeki WinSock yuvasında Alım arabelleği boyutunu belirten bir tamsayı.<br /><br /> Alma kanalının bir kullanıcısı, verileri alırken sistemin nasıl davranacağını denetlemek için bağlama üzerinde bu özniteliği kullanabilir.  Örneğin, bu öznitelik için daha yüksek bir değere sahip gelen WCF iletilerini kullanan bir uygulama, iletilerin, uygulamanın onları işlemesini beklerken WinSock arabelleğine yığmasını sağlar.  Aynı durumda daha düşük bir değer kullanılması, iletilerin bırakılmasına neden olur. Bu öznitelik, temeldeki Winsock `SO_RCVBUF` yuva seçeneğini gösterir. Bu öznitelik değeri en az boyut `maxReceivedMessageSize`olmalıdır.   Değerinden küçük bir değere ayarlanması çalışma zamanı özel `maxReceivedMessageSize` durumuna neden olur.<br /><br /> Varsayılan değer 65536 ' dir.|  
|timeToLive|Çok noktaya yayın paketinin geçebileceğine yönelik ağ segmenti atlamalarının sayısını belirten bir tamsayı.  Bu öznitelik, `IP_MULTICAST_TTL` ve `IP_TTL` yuva seçenekleriyle ilişkili işlevselliği gösterir.<br /><br /> Varsayılan değer 1’dir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<udpAnnouncementEndpoint >](udpannouncementendpoint.md)|Sabit duyuru sözleşmesine ve UDP aktarım bağlamaya sahip standart bir uç nokta.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Discovery.UdpTransportSettings>
