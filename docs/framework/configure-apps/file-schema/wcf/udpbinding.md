---
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 743eaa281fef233ddc2e8af5cee890bd10ce0963
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941189"
---
# <a name="udpbinding"></a>\<udpBinding >
<xref:System.ServiceModel.UdpBinding> Bağlamayı yapılandırmak için kullanılan bir yapılandırma öğesi.  
  
 \<system.ServiceModel>  
\<bağlama >  
\<udpBinding >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<udpBinding>
  <binding closeTimeout="TimeSpan"
           duplicateMessageHistoryLength="Integer"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxPendingMessagesTotalSize="Integer"
           maxReceivedMessageSize="Integer"
           maxRetransmitCount="Integer"
           multicastInterfaceId="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           timeToLive="TimeSpan">
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`closeTimeout`|Bir <xref:System.TimeSpan> kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır. Varsayılan değer 00:01:00 ' dir.|  
|`duplicateMessageHistoryLength`|Yinelenen ileti geçmişi uzunluğunu belirten bir tamsayı değeri.|  
|`maxBufferPoolSize`|Kanaldan ileti alan ileti arabelleklerinin Yöneticisi tarafından kullanılmak üzere ayrılan en fazla bellek miktarını belirten bir tamsayı değeri. Varsayılan değer 524288 (0X80000) bayttır.|  
|`maxBufferSize`|Bu bağlama ile yapılandırılan bir uç nokta için işlendiğinde iletileri depolayan bir arabelleğin bayt cinsinden en büyük boyutunu belirten bir tamsayı değeri. Varsayılan değer 65.536 bayttır.|  
|`maxPendingMessagesTotalSize`|Tek bir kanal örneği için Giriş sırasından alınan ancak henüz kaldırılmayan en fazla ileti sayısını belirten bir tamsayı değeri.|  
|`maxReceivedMessageSize`|Bu bağlama ile yapılandırılmış bir kanalda alınabilecek bir ileti için üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu tanımlayan pozitif bir tamsayı. İleti alıcı için çok büyükse gönderici bir SOAP hatası alıyor. Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur. Varsayılan değer 65.536 bayttır.|  
|`maxRetransmitCount`|En fazla yeniden aktarım iletisi sayısını belirten bir tamsayı değeri.|  
|`multicastInterfaceId`|Çok noktaya yayın arabirim KIMLIĞINI belirten bir tamsayı değeri.|  
|`name`|Bağlamanın yapılandırma adını içeren bir dize. Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır. Her bağlamada bir ve `name` özniteliği `namespace` , hizmetin meta verilerinde benzersiz bir şekilde tanımlayan bir ve özniteliği vardır. Ayrıca, bu ad aynı türdeki bağlamalar arasında benzersizdir. İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.|  
|`openTimeout`|Bir <xref:System.TimeSpan> açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır. Varsayılan değer 00:01:00 ' dir.|  
|`receiveTimeout`|Alma <xref:System.TimeSpan> işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır. Varsayılan değer 00:10:00 ' dir.|  
|`sendTimeout`|Bir <xref:System.TimeSpan> gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır. Varsayılan değer 00:01:00 ' dir.|  
|`textEncoding`|Bağlamadaki ileti yayma için kullanılacak karakter kümesi kodlamasını ayarlar. Geçerli değerler şunlardır:<br /><br /> -Bigendianunıcode: Unicode Bigenyen kodlaması.<br />Kodlamaları 16 bit kodlama.<br />UTF8 8 bit kodlama<br /><br /> Varsayılan değer UTF8 ' dir. Bu öznitelik türü <xref:System.Text.Encoding>.|  
|`timeToLive`|Bağlama için yaşam süresini belirten bir TimeSpan değeri.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar. Bu öğe türündedir <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](bindings.md)|Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 UdpBinding, WCF hizmetlerinin UDP taşıması üzerinden iletişim kurmasına izin verir. İstemcinin bir hizmete ileti gönderdiği ve geri yanıt bekleyebileceği "yangın ve unut" ileti değişimlerini sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.ServiceModel.UdpBinding> <`udpBinding`> öğesi kullanılarak nasıl yapılandırılacağını gösterir.  
  
```xml  
<udpBinding>
  <binding  closeTimeout="00:10:00"
            duplicateMessageHistoryLength="100"
            maxBufferPoolSize="100"
            maxPendingMessagesTotalSize="100000"
            maxReceivedMessageSize="65536"
            maxRetransmitCount="10"
            multicastInterfaceId="00000"
            name="myUdpBinding"
            openTimeout="00:10:00"
            receiveTimeout="00:10:00"
            sendTimeout="00:10:00"
            textEncoding="utf-8"
            timeToLive="00:10:00">
    <readerQuotas />
  </binding>
</udpBinding>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<bağlama >](../../../misc/binding.md)
