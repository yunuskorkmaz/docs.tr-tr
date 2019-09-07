---
title: <msmqTransport>
ms.date: 03/30/2017
ms.assetid: 19d89f35-76ac-49dc-832b-e8bec2d5e33b
ms.openlocfilehash: 0948df37a97f51076747485d0b6074f14b3f9d58
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397923"
---
# <a name="msmqtransport"></a>\<msmqTransport >
Bir kanalın özel bir bağlamaya dahil edildiğinde MSMQ aktarımında iletileri aktarmasına neden olur.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<msmqTransport >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<msmqTransport customDeadLetterQueue="Uri"
               deadLetterQueue="Custom/None/System"
               durable="Boolean"
               exactlyOnce="Boolean"
               manualAddressing="Boolean"
               maxBufferPoolSize="Integer"
               maxImmediateRetries="Integer"
               maxPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               maxRetryCycles="Integer"
               queueTransferProtocol="Native/Srmp/SrmpSecure"
               rejectAfterLastRetry="Boolean"
               retryCycleDelay="TimeSpan"
               timeToLive="TimeSpan"
               useActiveDirectory="Boolean"
               useSourceJournal="Boolean"
               useMsmqTracing="Boolean"
               ...>
  <msmqTransportSecurity>
  </msmqTransportSecurity>
</msmqTransport>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|customDeadLetterQueue|Zaman aşımına uğradığı veya uygulamaya teslim edilemeyen iletiler aktarılırken, uygulama başına atılacak mektup sırasının konumunu belirten bir URI.<br /><br /> ExactlyOnce için gerekli olan (yani, `exactlyOnce` olarak `true`ayarlanmış) iletiler için, bu öznitelik MSMQ 'daki sistem genelindeki işlem atılacak mektup kuyruğuna varsayılan olarak ayarlanır.<br /><br /> Herhangi bir değer olmaması gereken (yani, `exactlyOnce` olarak `false`ayarlanmış) iletilerde, bu özniteliğin varsayılan değeri olarak `null`ayarlanır.<br /><br /> Değerin net. MSMQ şemasını kullanması gerekir. Varsayılan, `null` değeridir.<br /><br /> `deadLetterQueue` `null`Veya olarak`System`ayarlandıysa, bu özniteliğin `None` olarak ayarlanması gerekir. Bu öznitelik değilse `null` `deadLetterQueue` , olarak `Custom`ayarlanması gerekir.|  
|Özelliğinde|Kullanılacak atılacak ileti sırası türünü belirtir.<br /><br /> Geçerli değerler şunlardır<br /><br /> Özel Özel sahipsiz sıra.<br />Seçim Sahipsiz sıra kullanılmayacak.<br />Sistemin Sistem sahipsiz sırasını kullanın.<br /><br /> Bu öznitelik, DeadLetterQueue türündedir.|  
|durable|Bu bağlama tarafından işlenen iletilerin dayanıklı veya geçici olup olmadığını belirten bir Boolean değer. Varsayılan, `true` değeridir.<br /><br /> Kalıcı bir ileti bir sıra Yöneticisi kilitlenmesiyle çalışır, geçici bir ileti değildir. Geçici iletiler, uygulamalar daha düşük gecikme süresi gerektirdiğinde ve zaman zaman kaybolmuş iletileri kabul edebildiği durumlarda faydalıdır.<br /><br /> `exactlyOnce` Olarak`true`ayarlanırsa, iletilerin dayanıklı olması gerekir.|  
|exactlyOnce|Bu bağlama tarafından işlenen iletilerin tam olarak bir kez alınıp alınmayacağını belirten bir Boole değeri. Varsayılan, `true` değeridir.<br /><br /> Bir ileti, gerek olmadan veya bunlarla gönderilebilir. Güvence, bir uygulamanın gönderilen iletinin teslim edilen ileti kuyruğuna ulaştığından emin olmasını sağlar, aksi takdirde uygulama bunu yok sayılma sırası okuyarak tespit edebilir.<br /><br /> `exactlyOnce`, olarak `true`ayarlandığında, MSMQ 'nun gönderilen iletinin teslim edilen ileti kuyruğuna bir kez ve yalnızca bir kez teslim edildiğini ve teslim başarısız olursa ileti atılacak ileti kuyruğuna gönderilmesini sağlar.<br /><br /> Ayarlanmış ile `exactlyOnce`gönderileniletiler yalnızcabirişlemkuyruğunagönderilmelidir.`true`|  
|manualAddressing|Kullanıcının ileti adreslemesinin denetimini almasını sağlayan bir Boole değeri. Bu özellik genellikle yönlendirici senaryolarında kullanılır; burada uygulama, bir ileti göndermek için bir kaç hedefe sahip olduğunu belirler.<br /><br /> Olarak `true`ayarlandığında, kanal iletinin zaten giderilmiş olduğunu varsayar ve buna ek bilgi eklemez. Böylece Kullanıcı her iletiyi ayrı ayrı adresedebilir.<br /><br /> Olarak ayarlandığında `false`, varsayılan Windows Communication Foundation (WCF) adres mekanizması tüm iletiler için otomatik olarak adresler oluşturur.<br /><br /> Varsayılan, `false` değeridir.|  
|maxBufferPoolSize|Arabellek havuzunun maksimum boyutunu belirten pozitif bir tamsayı. Varsayılan değer 524288 ' dir.<br /><br /> WCF 'in birçok bölümü arabellekleri kullanır. Her kullanıldıkları sırada arabellekleri oluşturma ve yok etme, her zaman pahalıdır ve arabellekler için çöp toplama de pahalıdır. Arabellek havuzları ile havuzdan bir arabellek alabilir, bunu kullanabilir ve işiniz bittiğinde havuza döndürebilirsiniz. Bu nedenle, arabelleklerin oluşturulmasıyla ve yok edilirken ek yük önlenmiş olur.|  
|maxImmediateRetries|Uygulama sırasından okunan bir ileti üzerinde en fazla anında yeniden deneme girişimi sayısını belirten bir tamsayı. Varsayılan değer 5 ' tir.<br /><br /> İleti için anında yeniden deneme sayısı üst sınırı deneniyorsa ve ileti uygulama tarafından tüketilmezse ileti, daha sonraki bir zamanda yeniden denemek için yeniden deneme kuyruğuna gönderilir. Yeniden deneme döngüsü belirtilmemişse iletiler, zarar iletisi kuyruğuna gönderilir ya da bir negatif bildirim gönderene geri gönderilir.|  
|maxPoolSize|Havuzun maksimum boyutunu belirten pozitif bir tamsayı. Varsayılan değer 524288 ' dir.|  
|maxReceivedMessageSize|Üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı. İletiyi gönderen ileti alıcı için çok büyük olduğunda bir SOAP hatası alır. Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur. Varsayılan değer 65536 ' dir.|  
|Maxretrydöngüleri|İleti alma uygulamasına iletileri teslim girişiminde bulunan en fazla yeniden deneme döngüsü sayısını belirten bir tamsayı. Varsayılan, <xref:System.Int32.MaxValue> değeridir.<br /><br /> Tek bir yeniden deneme çevrimi, bir uygulamaya belirtilen sayıda ileti sunmaya çalışır. Yapılan deneme sayısı `maxImmediateRetries` özniteliği tarafından ayarlanır. Dağıtım denemeleri tükendikten sonra uygulama iletiyi tüketmezse ileti bir yeniden deneme kuyruğuna gönderilir. Sonraki yeniden deneme döngüleri, yeniden deneme sırasından uygulama kuyruğuna döndürülen iletiden oluşur ve bu, bir gecikmeden sonra bir gecikmeden `retryCycleDelay` sonra, uygulamaya teslim girişiminde yer verir. `maxRetryCycles` Özniteliği, uygulamanın iletiyi teslim etmeyi denemek için kullandığı yeniden deneme döngüsü sayısını belirtir.|  
|queueTransferProtocol|Bu bağlamanın kullandığı sıraya alınmış iletişim kanalı aktarımını belirtir. Geçerli değerler şunlardır<br /><br /> Yerel  Yerel MSMQ protokolünü kullanın.<br />SRMP  SOAP Güvenilir Mesajlaşma protokolünü (SRMP) kullanın.<br />-SrmpSecure: SOAP Güvenilir Mesajlaşma Protokolü güvenli (SRMPS) aktarımını kullanın.<br /><br /> Bu öznitelik türü <xref:System.ServiceModel.QueueTransferProtocol>.<br /><br /> SOAP Güvenilir Mesajlaşma protokolünü kullanırken MSMQ Active Directory adresleme 'yi desteklemediğinden, olarak `useActiveDirectory` `true`ayarlandığında bu özniteliği SRMP veya srmps olarak ayarlayamazsınız.|  
|rejectAfterLastRetry|En fazla yeniden deneme sayısı denendikten sonra teslim başarısız olan bir ileti için hangi eylemin yapılacağını belirten bir Boole değeri.<br /><br /> `true`, gönderene negatif bir bildirim döndürüldüğünden ve ileti bırakıldığında, `false` iletinin zarar iletisi kuyruğuna gönderildiği anlamına gelir. Varsayılan, `false` değeridir.<br /><br /> Değer ise `false`, alıcı uygulama, zarar iletilerini işlemek için zarar iletisi kuyruğunu okuyabilir (yani tesliminin başarısız olduğu iletiler).<br /><br /> MSMQ 3,0, gönderene negatif bir bildirim döndürmeyi desteklemez, bu nedenle bu öznitelik MSMQ 3,0 ' de yok sayılır.|  
|retryCycleDelay|Anında <xref:System.TimeSpan> teslim edilmemiş bir iletiyi teslim etmeye çalışırken deneme döngüleri arasındaki gecikme süresini belirten bir. Varsayılan değer 00:10:00 ' dir.<br /><br /> Tek bir yeniden deneme çevrimi, alıcı uygulamaya belirtilen sayıda ileti sunmaya çalışır. Yapılan deneme sayısı `maxImmediateRetries` özniteliği tarafından belirtilir. Uygulamanın belirtilen sayıda anında yeniden denemeden sonra iletiyi tüketmesi durumunda ileti bir yeniden deneme kuyruğuna gönderilir. Sonraki yeniden deneme döngüleri, yeniden deneme sırasından uygulama kuyruğuna döndürülen iletiden oluşur ve bu, bir gecikmeden sonra bir gecikmeden `retryCycleDelay` sonra, uygulamaya teslim girişiminde yer verir. Yeniden deneme döngüsü sayısı özniteliğe göre `maxRetryCycles` belirtilir.|  
|timeToLive|İletilerin <xref:System.TimeSpan> , zaman aşımına geçmeden önce ne kadar geçerli olduğunu ve atılacak ileti kuyruğuna yerleştirileceğini belirten bir. Varsayılan değer 1,00:00:00, bu da 1 gün anlamına gelir.<br /><br /> Bu öznitelik, zaman duyarlı iletilerin, alıcı uygulamalar tarafından işlenmeden önce eski hale gelmemesini sağlamak üzere ayarlanır. Belirtilen zaman aralığı içinde alıcı uygulama tarafından tüketilmeyen bir kuyruktaki ileti, süresi dolmaya yönelik olarak kabul edilir. Süre dolmayan iletiler, atılacak ileti sırası adlı özel bir kuyruğa gönderilir. Etkin olmayan ileti sırasının konumu, `customDeadLetterQueue` özniteliğiyle veya uygun varsayılan değer ile belirlenir.|  
|UseActiveDirectory|Sıra adreslerinin Active Directory kullanılarak dönüştürülmesi gerekip gerekmediğini belirten bir Boole değeri.<br /><br /> MSMQ kuyruğu adresleri, yol adlarından veya doğrudan biçim adlarından oluşabilir. Doğrudan biçim adıyla, MSMQ, DNS, NetBIOS veya IP kullanarak bilgisayar adını çözer. Bir yol adıyla, MSMQ Active Directory kullanarak bilgisayar adını çözer. Varsayılan olarak, Windows Communication Framework (WCF) sıraya alınan aktarım, bir ileti sırasının URI 'sini doğrudan biçim adına dönüştürür. Bu özniteliği `true`' a ayarlayarak bir uygulama, sıraya alınan taşımanın DNS, NetBIOS veya IP yerine Active Directory kullanarak bilgisayar adını çözmesi gerektiğini belirtebilir.|  
|useMsmqTracing|Bu bağlama tarafından işlenen iletilerin izlenip izlenmeyeceğini belirten bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> İzleme etkinleştirildiğinde, ileti Message Queuing bilgisayara her ayrıldığında veya ulaştığında rapor iletileri oluşturulur ve rapor kuyruğuna gönderilir.|  
|useSourceJournal|Bu bağlama tarafından işlenen iletilerin kopyalarının kaynak günlük kuyruğunda depolanması gerekip gerekmediğini belirten bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Bilgisayarın giden sırasının ayrılmasına sahip bir ileti kaydını tutmak isteyen sıraya alınmış uygulamalar iletileri bir günlük kuyruğuna kopyalayabilir. İleti, giden sırasından ayrıldığında ve iletinin hedef bilgisayarda alındığı bir bildirim alındıktan sonra iletinin bir kopyası gönderen bilgisayarın sistem günlüğü kuyruğunda tutulur.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<msmqTransportSecurity >](msmqtransportsecurity.md)|Bu bağlama için taşıma güvenlik ayarlarını belirtir. Bu öğe türündedir <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../misc/binding.md)|Özel bağlamanın tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `msmqTransport` Öğesi, kullanıcının sıraya alınmış iletişim kanalının özelliklerini ayarlamanıza olanak sağlar. Kuyruğa alınan iletişim kanalı, taşıması için Message Queuing kullanır.  
  
 Bu bağlama öğesi, Message Queuing standart bağlama (`netMsmqBinding`) tarafından kullanılan varsayılan bağlama öğesidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.MsmqTransportElement>
- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [WCF'de Kuyruklar](../../../wcf/feature-details/queues-in-wcf.md)
- [Taşımalar](../../../wcf/feature-details/transports.md)
- [Taşıma Seçme](../../../wcf/feature-details/choosing-a-transport.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
