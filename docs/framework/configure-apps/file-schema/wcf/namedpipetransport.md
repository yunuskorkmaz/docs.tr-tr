---
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 4582066098feaf50b33b083de56bcb8c3e04df0f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204625"
---
# \<namedPipeTransport>

Bir kanalın özel bir bağlamaya dahil edildiğinde adlandırılmış kanalları kullanarak ileti aktarmasına neden olan bir taşıma tanımlar.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedPipeTransport>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<namedPipeTransport channelInitializationTimeout="TimeSpan"
                    connectionBufferSize="Integer"
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                    manualAddressing="Boolean"
                    maxBufferPoolSize="Integer"
                    maxBufferSize="Integer"
                    maxOutputDelay="TimeSpan"
                    maxPendingAccepts="Integer"
                    maxPendingConnections="Integer"
                    maxReceivedMessageSize="Integer"
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  

Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|ChannelInitializationTimeout|<xref:System.TimeSpan>Bir kanalın kesilmeden önce başlatma durumunda olabilecek en uzun süreyi belirleyen bir değeri alır veya ayarlar.|  
|ConnectionBufferSize|İstemci veya hizmetten alınan bir seri hale getirilmiş ileti öbeğini iletmek için kullanılan arabelleğin boyutunu alır veya ayarlar.|  
|hostNameComparisonMode|URI ile eşleştirilirken, ana bilgisayar adının hizmete erişmek için kullanılıp kullanılmadığını gösteren bir değer alır veya ayarlar.|  
|manualAddressing|İletinin el ile adreslenmesi gerekip gerekmediğini gösteren bir değer alır veya ayarlar.|  
|maxBufferPoolSize|Taşıma tarafından kullanılan arabellek havuzlarının en büyük boyutunu bayt cinsinden alır veya ayarlar.|  
|maxBufferSize|Kullanılacak arabelleğin en büyük boyutunu alır veya ayarlar. Akışlı iletiler için bu değer en azından, arabelleğe alınmış modda okunan ileti üstbilgilerinin en büyük olası boyutu olmalıdır.|  
|maxOutputDelay|Bir ileti öbeğinin veya bir tam iletinin gönderilmeden önce bellekte ara belleğe kalabileceği maksimum zaman aralığını alır veya ayarlar.|  
|maxPendingAccepts|Bir hizmetin hizmete gelen bağlantıları işlemeye yönelik bir dinleyici üzerinde bekleyebilen en fazla kanal sayısını alır veya ayarlar.|  
|maxPendingConnections|Hizmette gönderimi bekleyen en fazla bağlantı sayısını alır veya ayarlar.|  
|Değerini|Alınabilecek izin verilen en büyük ileti boyutunu bayt cinsinden alır ve ayarlar.|  
|transferMode|İletilerin arabelleğe alınıp alınmayacağını veya bağlantı yönelimli aktarımla akışını gösteren bir değer alır veya ayarlar.|  
|[\<connectionPoolSettings> durumunu \<namedPipeTransport>](connectionpoolsettings.md)|Adlandırılmış kanal bağlama için ek bağlantı havuzu ayarlarını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|Özel bağlamanın tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  

Bu aktarım, "net. pipe:/hostname/path" biçimindeki URI 'Leri kullanır. Diğer URI bileşenleri isteğe bağlıdır.  
  
`namedPipeTransport`Öğesi, adlandırılmış kanallar aktarım protokolünü uygulayan özel bir bağlama oluşturmak için başlangıç noktasıdır. Bu aktarım, makine içi Windows Communication Foundation (WCF)-WCF iletişimi için kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Taşımalar](../../../wcf/feature-details/transports.md)
- [Taşıma Seçme](../../../wcf/feature-details/choosing-a-transport.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
