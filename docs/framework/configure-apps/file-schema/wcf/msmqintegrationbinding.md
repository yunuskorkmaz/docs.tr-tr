---
title: <msmqIntegrationBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- msmqIntegrationBinding Element
ms.assetid: edf277f3-e3bf-4ed8-9f55-83b5788430a7
ms.openlocfilehash: b692d0610a975247d74798feff2411317db68dfd
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397748"
---
# <a name="msmqintegrationbinding"></a>\<MsmqIntegrationBinding >
MSMQ aracılığıyla iletileri yönlendirerek sıraya alma desteği sağlayan bir bağlamayı tanımlar.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<MsmqIntegrationBinding >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<msmqIntegrationBinding>
  <binding closeTimeout="TimeSpan"
           customDeadLetterQueue="Uri"
           deadLetterQueue="Uri"
           durable="Boolean"
           exactlyOnce="Boolean"
           maxReceivedMessageSize="Integer"
           maxRetryCycles="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveContextEnabled="Boolean"
           receiveErrorHandling="Drop/Fault/Move/Reject"
           receiveTimeout="TimeSpan"
           receiveRetryCount="Integer"
           retryCycleDelay="TimeSpan"
           sendTimeout="TimeSpan"
           serializationFormat="XML/Binary/ActiveX/ByteArray/Stream"
           timeToLive="TimeSpan"
           useMsmqTracing="Boolean"
           useSourceJournal="Boolean">
  </binding>
</msmqIntegrationBinding>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|closeTimeout|Bir <xref:System.TimeSpan> kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır. Varsayılan değer 00:01:00 ' dir.|  
|customDeadLetterQueue|Zaman aşımına uğradı veya başarısız aktarım ya da teslimi olan iletilerin yerleştirildiği, uygulama başına atılacak mektup sırasının konumunu içeren bir URI.<br /><br /> Sahipsiz sıra, teslim edilemeyen süre dolmayan iletiler için gönderen uygulamanın kuyruk yöneticisinde bir sıradır.<br /><br /> Tarafından <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> belirtilen URI 'nin net. MSMQ şemasını kullanması gerekir.|  
|Özelliğinde|Bir <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>. değer varsa, ne tür bir atılacak ileti sırası kullanılacağını belirten.<br /><br /> Atılacak bir sıra, uygulamaya teslim edilemeyen iletilerin aktarılacağı konumdur.<br /><br /> ExactlyOnce güvencesi gerektiren (yani, `exactlyOnce` özniteliği olarak `true`ayarlanmış) iletiler için, bu öznitelik MSMQ 'daki sistem genelinde işlem atılacak mektup kuyruğuna varsayılan olarak ayarlanır.<br /><br /> Herhangi bir değer gerektirmeyen iletiler için, bu öznitelik varsayılan olarak `null`olur.|  
|durable|İletinin kuyrukta dayanıklı mi yoksa geçici mi olduğunu belirten bir Boole değeri. Kalıcı bir ileti bir sıra Yöneticisi kilitlenmesiyle çalışır, geçici bir ileti değildir. Geçici iletiler, uygulamalar daha düşük gecikme süresi gerektirdiğinde ve zaman zaman kaybolmuş iletileri kabul edebildiği durumlarda faydalıdır. `exactlyOnce` Özniteliği olarak`true`ayarlandıysa, iletilerin dayanıklı olması gerekir. Varsayılan, `true` değeridir.|  
|exactlyOnce|Her iletinin yalnızca bir kez teslim edilip edilmediğini belirten Boolean bir değer. Ardından, gönderen teslim arızalarına göre bilgilendirilir. Ne zaman `durable` , bu öznitelik yok sayılır ve iletiler teslim güvencesi olmadan aktarılır. `false` Varsayılan, `true` değeridir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|maxReceivedMessageSize|Bu bağlama tarafından işlenen üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu tanımlayan pozitif bir tamsayı. Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır. Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur. Varsayılan değer 65536 ' dir. İleti boyutu sınırı, hizmet reddi (DoS) saldırılarına maruz kalma olasılığını sınırlandırmaya yöneliktir.|  
|Maxretrydöngüleri|Zarar iletisi algılama özelliği tarafından kullanılan yeniden deneme döngüsü sayısını belirten bir tamsayı. Tüm Döngülerde tüm teslim denemeleri başarısız olduğunda bir ileti bir zarar iletisi haline gelir. Varsayılan değer 2 ' dir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|name|Bağlamanın yapılandırma adını içeren bir dize. Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır. İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.|  
|openTimeout|Bir <xref:System.TimeSpan> açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır. Varsayılan değer 00:01:00 ' dir.|  
|receiveErrorHandling|Zebilen ve dağıtılabilir iletilerin nasıl işleneceğini belirten bir <xref:System.ServiceModel.ReceiveErrorHandling> değer.|  
|receiveRetryCount|Sıra yöneticisinin uygulama kuyruğundan uygulamaya bir ileti iletimi başarısız olursa, en fazla çabuk yeniden deneme sayısını belirten bir tamsayı.<br /><br /> En fazla teslim denemesi sayısına ulaşıldığında ve ileti uygulama tarafından erişilmezse, ileti daha sonra yeniden teslim için yeniden deneme kuyruğuna gönderilir. İleti gönderme kuyruğuna geri aktarılmadan önceki zaman miktarı tarafından `retryCycleDelay`denetlenir. Yeniden deneme döngüsü `maxRetryCycles` değere ulaştıysanız, ileti, zarar iletisi kuyruğuna gönderilir ya da bir negatif alındı bildirimi gönderene geri gönderilir.|  
|receiveTimeout|Alma <xref:System.TimeSpan> işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır. Varsayılan değer 00:10:00 ' dir.|  
|receiveContextEnabled|Kuyruklarda iletileri işlemeye yönelik alma bağlamının etkinleştirilip etkinleştirilmediğini belirten bir Boole değeri. Bu olarak `true`ayarlandığında, bir hizmet, işleme başlamak için kuyruktaki bir iletiyi "göz atmayı" ve bir işlem yanlış olursa ve bir özel durum oluşursa, kuyrukta kalır. Hizmetler Ayrıca, daha sonraki bir zamanda işlemeyi yeniden denemek için iletileri "kilitler". ReceiveContext, kuyruktan kaldırılmadan önce iletiyi işlendiğinde "tamamlamak" için bir mekanizma sağlar. İletiler artık ağ üzerinden sıralara okunamaz ve yeniden yazılmaz ve tek tek iletiler, işleme sırasında farklı hizmet örneklerinde geri alınmaz.|  
|retryCycleDelay|Anında teslim edilmemiş bir iletiyi teslim etmeye çalışırken yeniden deneme döngüleri arasındaki gecikme süresini belirten bir TimeSpan değeri. Değer yalnızca en düşük bekleme süresini tanımlar çünkü gerçek bekleme süresi daha uzun olabilir. Varsayılan değer 00:30:00 ' dir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|Binding üstündeki SendTimeout|Bir <xref:System.TimeSpan> gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir değer. Bu değer, değerinden büyük veya buna eşit <xref:System.TimeSpan.Zero>olmalıdır. Varsayılan değer 00:01:00 ' dir.|  
|serializationFormat|İleti gövdesinin serileştirilmesi için kullanılan biçimi tanımlar. Bu öznitelik türü <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat>.|  
|timeToLive|İletilerin süre dolmadan önce ne kadar süreyle geçerli olduğunu belirten bir TimeSpan değeri ve atılacak ileti kuyruğuna yerleştirirsiniz. Varsayılan değer 1.00:00:00 ' dır.<br /><br /> Bu öznitelik, zaman duyarlı iletilerin, alıcı uygulamalar tarafından işlenmeden önce eski hale gelmemesini sağlamak üzere ayarlanır. Belirtilen zaman aralığı içinde alıcı uygulama tarafından tüketilmeyen bir kuyruktaki ileti, süresi dolmaya yönelik olarak kabul edilir. Süre dolmayan iletiler, atılacak ileti sırası adlı özel bir kuyruğa gönderilir. Etkin olmayan ileti sırasının konumu, `DeadLetterQueue` özniteliğiyle veya uygun varsayılan değer ile belirlenir.|  
|useMsmqTracing|Bu bağlama tarafından işlenen iletilerin izlenip izlenmeyeceğini belirten bir Boole değeri. Varsayılan, `false` değeridir. İzleme etkinleştirildiğinde, ileti Message Queuing bilgisayara her ayrıldığında veya ulaştığında rapor iletileri oluşturulur ve rapor kuyruğuna gönderilir.|  
|useSourceJournal|Bu bağlama tarafından işlenen iletilerin kopyalarını belirten bir Boole değeri, kaynak günlüğünde depolanmalıdır. Varsayılan, `false` değeridir.<br /><br /> Bilgisayarın giden sırasının ayrılmasına sahip bir ileti kaydını tutmak isteyen sıraya alınmış uygulamalar iletileri bir günlük kuyruğuna kopyalayabilir. İleti, giden sırasından ayrıldığında ve iletinin hedef bilgisayarda alındığı bir bildirim alındıktan sonra iletinin bir kopyası gönderen bilgisayarın sistem günlüğü kuyruğunda tutulur.|  
  
## <a name="serializationformat-attribute"></a>{serializationFormat} Özniteliğe  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Xml|XML biçimi|  
|İkili|İkili biçim|  
|ActiveX|ActiveX biçimi|  
|ByteArray|Nesneyi bayt dizisine dizleştirir.|  
|Akış|Akış olarak biçimlendirilen gövde|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](security-of-msmqintegrationbinding.md)|Bağlama için güvenlik ayarlarını tanımlar. Bu öğe türündedir <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](bindings.md)|Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu bağlama öğesi, Windows Communication Foundation (WCF) uygulamalarının com, MSMQ Native API 'ler veya <xref:System.Messaging?displayProperty=nameWithType> ad alanında tanımlanan türler kullanan mevcut MSMQ uygulamalarından ileti göndermesini ve iletileri almasını sağlamak için kullanılabilir. Bu yapılandırma öğesini, kuyruğu adresetmenin yollarını belirtmek, kesintileri aktarmak, iletilerin silinme halinde depolanması gerekip gerekmediğini ve iletilerin korunması ve kimlik doğrulamasının nasıl yapılacağını belirlemek için kullanabilir. Daha fazla bilgi için [nasıl yapılır: WCF uç noktaları ve Message Queuing uygulamalarla](../../../wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)ileti alışverişi yapın.  
  
## <a name="example"></a>Örnek  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <msmqIntegrationBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 deadLetterQueue="net.msmq://localhost/blah"
                 durable="true"
                 exactlyOnce="true"
                 maxReceivedMessageSize="1000"
                 maxImmediateRetries="11"
                 maxRetryCycles="12"
                 poisonMessageHandling="Disabled"
                 rejectAfterLastRetry="false"
                 retryCycleDelay="00:05:55"
                 timeToLive="00:11:11"
                 useSourceJournal="true"
                 useMsmqTracing="true"
                 serializationFormat="Binary">
          <security mode="None" />
        </binding>
      </msmqIntegrationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>
- [\<bağlama >](../../../misc/binding.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [WCF'de Kuyruklar](../../../wcf/feature-details/queues-in-wcf.md)
