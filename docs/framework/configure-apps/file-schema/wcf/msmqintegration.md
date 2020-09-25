---
title: <msmqIntegration>
ms.date: 03/30/2017
ms.assetid: ab677405-1ffe-457a-803f-00c1770e51e2
ms.openlocfilehash: 66f7e3ba145441926ed11227a0ba82ff21925cf7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204690"
---
# \<msmqIntegration>

Özel bağlama için MSMQ aktarımı belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqIntegration>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<msmqIntegration customDeadLetterQueue="Uri"
                 deadLetterQueue="Custom/None/System"
                 durable="Boolean"
                 exactlyOnce="Boolean"
                 manualAddressing="Boolean"
                 maxBufferPoolSize="Integer"
                 maxImmediateRetries="Integer"
                 maxReceivedMessageSize="Integer"
                 maxRetryCycles="Integer"
                 rejectAfterLastRetry="Boolean"
                 retryCycleDelay="TimeSpan"
                 serializationFormat="XML/Binary/ActiveX/ByteArray/Stream"
                 timeToLive="TimeSpan"
                 useSourceJournal="Boolean"
                 useMsmqTracing="Boolean">
  <msmqTransportSecurity>
  </msmqTransportSecurity>
</msmqIntegration>
```  
  
## <a name="type"></a>Tür  

 `Type`  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|customDeadLetterQueue|Zaman aşımına uğradığı veya uygulamaya teslim edilemeyen iletiler aktarılırken, uygulama başına atılacak mektup sırasının konumunu belirten bir URI.<br /><br /> ExactlyOnce için gerekli olan (yani, `exactlyOnce` olarak ayarlanmış) iletiler için `true` , bu öznitelik MSMQ 'daki sistem genelindeki işlem atılacak mektup kuyruğuna varsayılan olarak ayarlanır.<br /><br /> Herhangi bir değer olmaması gereken (yani, `exactlyOnce` olarak ayarlanmış `false` ) iletilerde, bu özniteliğin varsayılan değeri olarak ayarlanır `null` .<br /><br /> Değerin net. MSMQ şemasını kullanması gerekir. Varsayılan değer: `null`.<br /><br /> `deadLetterQueue`Veya olarak ayarlandıysa `None` `System` , bu özniteliğin olarak ayarlanması gerekir `null` . Bu öznitelik değilse `null` , `deadLetterQueue` olarak ayarlanması gerekir `Custom` .|  
|Özelliğinde|Kullanılacak atılacak ileti sırası türünü belirtir.<br /><br /> Geçerli değerler şunlardır<br /><br /> -Custom: özel sahipsiz sıra.<br />-None: hiçbir sahipsiz sıra kullanılmaz.<br />-Sistem: sistem sahipsiz kuyruğunu kullanın.<br /><br /> Bu öznitelik, DeadLetterQueue türündedir.|  
|üretilen|Bu bağlama tarafından işlenen iletilerin dayanıklı veya geçici olup olmadığını belirten bir Boolean değer. Varsayılan değer: `true`.<br /><br /> Kalıcı bir ileti bir sıra Yöneticisi kilitlenmesiyle çalışır, geçici bir ileti değildir. Geçici iletiler, uygulamalar daha düşük gecikme süresi gerektirdiğinde ve zaman zaman kaybolmuş iletileri kabul edebildiği durumlarda faydalıdır.<br /><br /> `exactlyOnce`Olarak ayarlanırsa `true` , iletilerin dayanıklı olması gerekir.|  
|exactlyOnce|Bu bağlama tarafından işlenen iletilerin tam olarak bir kez alınıp alınmayacağını belirten bir Boole değeri. Varsayılan değer: `true`.<br /><br /> Bir ileti, gerek olmadan veya bunlarla gönderilebilir. Güvence, bir uygulamanın gönderilen iletinin teslim edilen ileti kuyruğuna ulaştığından emin olmasını sağlar, aksi takdirde uygulama bunu yok sayılma sırası okuyarak tespit edebilir.<br /><br /> `exactlyOnce`, olarak ayarlandığında `true` , MSMQ 'nun gönderilen iletinin teslim edilen ileti kuyruğuna bir kez ve yalnızca bir kez teslim edildiğini ve teslim başarısız olursa ileti atılacak ileti kuyruğuna gönderilmesini sağlar.<br /><br /> Ayarlanmış ile gönderilen iletiler `exactlyOnce` `true` yalnızca bir işlem kuyruğuna gönderilmelidir.|  
|manualAddressing|Kullanıcının ileti adreslemesinin denetimini almasını sağlayan bir Boole değeri. Bu özellik genellikle yönlendirici senaryolarında kullanılır; burada uygulama, bir ileti göndermek için bir kaç hedefe sahip olduğunu belirler.<br /><br /> Olarak ayarlandığında `true` , kanal iletinin zaten giderilmiş olduğunu varsayar ve buna ek bilgi eklemez. Böylece Kullanıcı her iletiyi ayrı ayrı adresedebilir.<br /><br /> Olarak ayarlandığında `false` , varsayılan Windows Communication Foundation (WCF) adres mekanizması tüm iletiler için otomatik olarak adresler oluşturur.<br /><br /> Varsayılan değer: `false`.|  
|maxBufferPoolSize|Arabellek havuzunun maksimum boyutunu belirten pozitif bir tamsayı. Varsayılan değer 524288 ' dir.<br /><br /> WCF 'in birçok bölümü arabellekleri kullanır. Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır. Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz. Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.|  
|maxImmediateRetries|Uygulama sırasından okunan bir ileti üzerinde en fazla anında yeniden deneme girişimi sayısını belirten bir tamsayı. Varsayılan değer 5 ' tir.<br /><br /> İleti için anında yeniden deneme sayısı üst sınırı deneniyorsa ve ileti uygulama tarafından tüketilmezse ileti, daha sonraki bir zamanda yeniden denemek için yeniden deneme kuyruğuna gönderilir. Yeniden deneme döngüsü belirtilmemişse iletiler, zarar iletisi kuyruğuna gönderilir ya da bir negatif bildirim gönderene geri gönderilir.|  
|Değerini|Üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı. İletiyi gönderen ileti alıcı için çok büyük olduğunda bir SOAP hatası alır. Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur. Varsayılan değer 65536 ' dir.|  
|Maxretrydöngüleri|İleti alma uygulamasına iletileri teslim girişiminde bulunan en fazla yeniden deneme döngüsü sayısını belirten bir tamsayı. Varsayılan değer: <xref:System.Int32.MaxValue>.<br /><br /> Tek bir yeniden deneme çevrimi, bir uygulamaya belirtilen sayıda ileti sunmaya çalışır. Yapılan deneme sayısı özniteliği tarafından ayarlanır `maxImmediateRetries` . Dağıtım denemeleri tükendikten sonra uygulama iletiyi tüketmezse ileti bir yeniden deneme kuyruğuna gönderilir. Sonraki yeniden deneme döngüleri, yeniden deneme sırasından uygulama kuyruğuna döndürülen iletiden oluşur ve bu, bir gecikmeden sonra bir gecikmeden sonra, uygulamaya teslim girişiminde yer verir `retryCycleDelay` . `maxRetryCycles`Özniteliği, uygulamanın iletiyi teslim etmeyi denemek için kullandığı yeniden deneme döngüsü sayısını belirtir.|  
|rejectAfterLastRetry|En fazla yeniden deneme sayısı denendikten sonra teslim başarısız olan bir ileti için hangi eylemin yapılacağını belirten bir Boole değeri.<br /><br /> `true` , gönderene negatif bir bildirim döndürüldüğünden ve ileti bırakıldığında, `false` iletinin zarar iletisi kuyruğuna gönderildiği anlamına gelir. Varsayılan değer: `false`.<br /><br /> Değer ise `false` , alıcı uygulama, zarar iletilerini işlemek için zarar iletisi kuyruğunu okuyabilir (yani tesliminin başarısız olduğu iletiler).<br /><br /> MSMQ 3,0, gönderene negatif bir bildirim döndürmeyi desteklemez, bu nedenle bu öznitelik MSMQ 3,0 ' de yok sayılır.|  
|retryCycleDelay|<xref:System.TimeSpan>Anında teslim edilmemiş bir iletiyi teslim etmeye çalışırken deneme döngüleri arasındaki gecikme süresini belirten bir. Varsayılan değer 00:10:00 ' dir.<br /><br /> Tek bir yeniden deneme çevrimi, alıcı uygulamaya belirtilen sayıda ileti sunmaya çalışır. Yapılan deneme sayısı özniteliği tarafından belirtilir `maxImmediateRetries` . Uygulamanın belirtilen sayıda anında yeniden denemeden sonra iletiyi tüketmesi durumunda ileti bir yeniden deneme kuyruğuna gönderilir. Sonraki yeniden deneme döngüleri, yeniden deneme sırasından uygulama kuyruğuna döndürülen iletiden oluşur ve bu, bir gecikmeden sonra bir gecikmeden sonra, uygulamaya teslim girişiminde yer verir `retryCycleDelay` . Yeniden deneme döngüsü sayısı özniteliğe göre belirtilir `maxRetryCycles` .|  
|serializationFormat|MSMQ iletisinin bir parçası olarak gönderilen nesneleri seri hale getirmek için kullanılan biçimlendirici öğesini belirtir. Geçerli değerler şunlardır<br /><br /> -ActiveX: COM nesneleri serileştirilirken ActiveX biçimlendirici kullanılır.<br />-Binary: nesneyi ikili bir pakete Dizleştirir.<br />-ByteArray: nesneyi bayt dizisine Dizleştirir.<br />-Stream: nesneyi bir akışa seri hale getirir.<br />-XML: nesneyi bir XML paketine seri hale getirir. Varsayılan değer XML 'dir.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat> .|  
|timeToLive|<xref:System.TimeSpan>İletilerin, zaman aşımına geçmeden önce ne kadar geçerli olduğunu ve atılacak ileti kuyruğuna yerleştirileceğini belirten bir. Varsayılan değer 1,00:00:00, bu da 1 gün anlamına gelir.<br /><br /> Bu öznitelik, zaman duyarlı iletilerin, alıcı uygulamalar tarafından işlenmeden önce eski hale gelmemesini sağlamak üzere ayarlanır. Belirtilen zaman aralığı içinde alıcı uygulama tarafından tüketilmeyen bir kuyruktaki ileti, süresi dolmaya yönelik olarak kabul edilir. Süre dolmayan iletiler, atılacak ileti sırası adlı özel bir kuyruğa gönderilir. Etkin olmayan ileti sırasının konumu, `customDeadLetterQueue` özniteliğiyle veya uygun varsayılan değer ile belirlenir.|  
|useMsmqTracing|Bu bağlama tarafından işlenen iletilerin izlenip izlenmeyeceğini belirten bir Boole değeri. Varsayılan değer: `false`.<br /><br /> İzleme etkinleştirildiğinde, ileti Message Queuing bilgisayara her ayrıldığında veya ulaştığında rapor iletileri oluşturulur ve rapor kuyruğuna gönderilir.|  
|useSourceJournal|Bu bağlama tarafından işlenen iletilerin kopyalarının kaynak günlük kuyruğunda depolanması gerekip gerekmediğini belirten bir Boole değeri. Varsayılan değer: `false`.<br /><br /> Bilgisayarın giden sırasının ayrılmasına sahip bir ileti kaydını tutmak isteyen sıraya alınmış uygulamalar iletileri bir günlük kuyruğuna kopyalayabilir. İleti, giden sırasından ayrıldığında ve iletinin hedef bilgisayarda alındığı bir bildirim alındıktan sonra iletinin bir kopyası gönderen bilgisayarın sistem günlüğü kuyruğunda tutulur.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|msmqTransportSecurity|Bu bağlama için taşıma güvenlik ayarlarını belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement> .|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|Özel bağlamanın tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.MsmqIntegrationElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Taşımalar](../../../wcf/feature-details/transports.md)
- [WCF'de Kuyruklar](../../../wcf/feature-details/queues-in-wcf.md)
- [Taşıma Seçme](../../../wcf/feature-details/choosing-a-transport.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
