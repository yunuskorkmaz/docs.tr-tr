---
title: '&lt;msmqIntegration&gt;'
ms.date: 03/30/2017
ms.assetid: ab677405-1ffe-457a-803f-00c1770e51e2
ms.openlocfilehash: 6b1449ec385af2478ee278e9823a005c69ca8dc2
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147856"
---
# <a name="ltmsmqintegrationgt"></a>&lt;msmqIntegration&gt;
Özel bağlama için MSMQ aktarımı belirtir.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<msmqIntegration >  
  
## <a name="syntax"></a>Sözdizimi  
  
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
|customDeadLetterQueue|Uygulama başına yitirmiş kuyruk süresi dolmuş veya uygulamaya teslim edilemedi iletileri burada aktarılır konumu gösteren bir URI.<br /><br /> ExactlyOnce Güvenceleri gerektiren iletiler için (diğer bir deyişle, `exactlyOnce` ayarlanır `true`), bu öznitelik varsayılan olarak, MSMQ sistem genelinde işlem eski ileti sırası için.<br /><br /> Hiçbir Güvenceleri gerektiren iletiler için (diğer bir deyişle, `exactlyOnce` ayarlanır `false`), bu öznitelik varsayılan olarak `null`.<br /><br /> Değer net.msmq şeması kullanması gerekir. Varsayılan, `null` değeridir.<br /><br /> Varsa `deadLetterQueue` ayarlanır `None` veya `System`, sonra da bu özniteliği ayarlanmalıdır `null`. Bu öznitelik yoksa `null`, ardından `deadLetterQueue` ayarlanmalıdır `Custom`.|  
|deadLetterQueue|Kullanılacak geçerliliğini yitirmiş kuyruk türünü belirtir.<br /><br /> Geçerli değerler<br /><br /> -Özel: Özel teslim edilemeyen iletiler sırası.<br />-Yok: Hiçbir teslim edilemeyen iletiler sırası kullanılacağını belirtir.<br />-Sistem: Sistem teslim edilemeyen iletiler sırası kullanın.<br /><br /> Bu öznitelik DeadLetterQueue türüdür.|  
|dayanıklı|Bu bağlama tarafından işlenen iletilerin sürekli veya geçici olup olmadığını belirten bir Boole değeri. Varsayılan, `true` değeridir.<br /><br /> Geçici bir ileti çalışmazken kalıcı bir ileti kuyruğu manager kilitlenme devam eder. Uygulamalar düşük gecikme süresi gerektirir ve ara sıra kayıp iletiler tolere edebilen geçici iletileri yararlıdır.<br /><br /> Varsa `exactlyOnce` ayarlanır `true`, iletileri dayanıklı olması gerekir.|  
|exactlyOnce|Bu bağlama tarafından işlenen iletilerin tam bir kez alınıp alınmayacağını belirten Boolean bir değer. Varsayılan, `true` değeridir.<br /><br /> Bir ileti ile veya olmadan Güvenceleri gönderilebilir. Gönderilen ileti alıcı ileti sıraya ulaştı veya belirlemediyseniz, uygulamanın bu geçerliliğini yitirmiş kuyruk okuyarak belirleyebilirsiniz emin olmak bir uygulama bir güvence sağlar.<br /><br /> `exactlyOnce`, ayarlandığında `true`, MSMQ gönderilen ileti, yalnızca tek bir kez alıcı ileti kuyruğuna teslim edilir ve teslim başarısız olursa edilemeyen iletiler sırasına gönderilen ileti sağlayacak gösterir.<br /><br /> İle gönderilen iletileri `exactlyOnce` kümesine `true` yalnızca bir işlem kuyruğu için gönderilmelidir.|  
|manualAddressing|Kullanıcının ileti adresleme denetimini ele geçirmesine olanak tanıyan bir Boole değeri. Bu özellik, genellikle Uygulama ileti göndermek için çeşitli hedeflere aşağıdakilerden hangisi yeri belirler yönlendirici senaryolarda kullanılır.<br /><br /> Ayarlandığında `true`, kanala ileti zaten ele ve ek bilgiler için eklemez varsayar. Kullanıcı ardından her ileti tek tek ele alabilirsiniz.<br /><br /> Ayarlandığında `false`, varsayılan Windows Communication Foundation (WCF) adresleme mekanizmasını tüm iletiler için adresleri otomatik olarak oluşturur.<br /><br /> Varsayılan, `false` değeridir.|  
|maxBufferPoolSize|Arabellek havuzu en büyük boyutunu belirten pozitif bir tamsayı. 524288 varsayılandır.<br /><br /> WCF pek çok bölümünün arabellekler kullanın. Oluşturma ve arabellek kullanıldıkları her zaman yok etme pahalıdır ve çöp toplama arabellekler için da pahalıdır. Arabellek havuzu ile havuzdan bir arabelleğe almak, kullanmak ve tamamladıktan sonra havuza döndürün. Bu nedenle oluşturmak ve yok etme arabellekler yükü önlenmiş olur.|  
|maxImmediateRetries|Uygulama kuyruktan okuyan bir iletinin hemen yeniden deneme üst sınırını belirten bir tamsayı çalışır. Varsayılan değer 5'tir.<br /><br /> İleti için hemen yeniden deneme sayısı çalıştı ve ileti uygulama tarafından tüketilmeyen, sonraki noktada zamanında yeniden deneme için bir yeniden deneme kuyruğuna ileti gönderilir. Hiçbir yeniden deneme döngüsü belirtilirse, daha sonra iletileri ya da gönderilir zehirli ileti kuyruğa veya gönderene negatif bir bildirim gönderilir.|  
|maxReceivedMessageSize|Üst bilgiler dahil bayt cinsinden en büyük ileti boyutunu belirten pozitif bir tamsayı. İleti alıcısı için çok büyük olduğunda bir ileti gönderen bir SOAP hatasını alır. Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur. 65536 varsayılandır.|  
|maxRetryCycles|Alıcı uygulamasına iletileri teslim girişiminde yeniden deneme döngüsü sayısını belirten bir tamsayı. Varsayılan, <xref:System.Int32.MaxValue> değeridir.<br /><br /> Tek bir yeniden deneme döngüsü, belirtilen sayıda uygulamaya bir iletiyi teslim etmeye çalışır. Yapılan deneme sayısı belirlediği `maxImmediateRetries` özniteliği. İletiyi teslim girişimleri tüketmiş sonra kullanmak uygulama başarısız olursa, bir yeniden deneme kuyruğa ileti gönderilir. Sonraki yeniden deneme döngüsü tarafından belirtilen bir gecikmeden sonra uygulamaya tekrar teslim girişiminde yeniden deneme kuyruktan uygulama kuyruğa döndürülmesi ileti oluşur `retryCycleDelay` özniteliği. `maxRetryCycles` Özniteliği uygulamanın kullandığı iletiyi teslim denemek için yeniden deneme döngüsü sayısını belirtir.|  
|rejectAfterLastRetry|Yeniden deneme sayısı denemelerinden sonra teslim başarısız bir ileti için gerçekleştirilecek eylemi belirten bir Boole değeri.<br /><br /> `true` olumsuz bildirim gönderene döndürülür ve ileti bırakılan anlamına gelir; `false` zehirli ileti kuyruğuna gönderilen ileti anlamına gelir. Varsayılan, `false` değeridir.<br /><br /> Değer ise `false`, zehirli iletiler (diğer bir deyişle, teslimat başarısız olan iletiler) işlemek için zehirli ileti kuyruğa alma uygulaması okuyabilirsiniz.<br /><br /> MSMQ 3.0, MSMQ 3. 0'bu öznitelik yoksayılır bu nedenle negatif bildirim gönderene döndürmeyi desteklemiyor.|  
|retryCycleDelay|A <xref:System.TimeSpan> yeniden deneme döngüleri arasındaki gecikmeyi belirten anında teslim edilemeyen bir iletiyi teslim etmeye çalışırken. Varsayılan değer 00:10:00 ' dir.<br /><br /> Tek bir yeniden deneme döngüsü, belirtilen sayıda alan bir uygulamaya bir iletiyi teslim etmeye çalışır. Yapılan deneme sayısı tarafından belirtilen `maxImmediateRetries` özniteliği. Belirtilen sayıda hemen yeniden deneme iletiyi kullanmak uygulama başarısız olursa, bir yeniden deneme kuyruğa ileti gönderilir. Sonraki yeniden deneme döngüsü tarafından belirtilen bir gecikmeden sonra uygulamaya tekrar teslim girişiminde yeniden deneme kuyruktan uygulama kuyruğa döndürülmesi ileti oluşur `retryCycleDelay` özniteliği. Yeniden deneme döngüsü sayısını tarafından belirtilen `maxRetryCycles` özniteliği.|  
|serializationFormat|Bir MSMQ iletisinin bir parçası olarak gönderilen nesneleri serileştirmek için kullanılan biçimlendiriciyi belirtir. Geçerli değerler:<br /><br /> -ActiveX: COM nesneleri serileştirmek ActiveX biçimlendirici kullanılır.<br />-İkili:  İkili bir paket nesneyi serileştirir.<br />-ByteArray:  Bir bayt dizisi nesneyi serileştirir.<br />-Stream:  Nesneyi bir akışa serileştirir.<br />-Xml:  Bir XML paket nesneyi serileştirir. XML varsayılandır.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat>.|  
|timeToLive|A <xref:System.TimeSpan> iletilerin süreleri dolmadan ve teslim edilemeyen sırasına konmadan önce ne kadar süreyle geçerlidir belirtir. 1 gün yani 1.00:00:00 varsayılandır.<br /><br /> Bu öznitelik, bunlar alıcı uygulamalar tarafından işlenmeden önce zamana duyarlı iletileri eski hale gelmediğinden emin olmak için ayarlanır. Belirtilen zaman aralığı içinde alıcı uygulama tarafından tüketilmeyen bir kuyruktaki bir iletiyi süresi dolmuş kabul edilir. Süresi dolan iletileri geçerliliğini yitirmiş kuyruk adı verilen özel kuyruğa gönderilir. Geçerliliğini yitirmiş kuyruk konumu ile ayarlanır `customDeadLetterQueue` özniteliği veya uygun varsayılana dayalı Güvenceleri üzerinde.|  
|useMsmqTracing|İletileri bu bağlama tarafından işlenen olup olmadığını belirten bir Boole değeri izlenip izlenmemesini gerektiğini. Varsayılan, `false` değeridir.<br /><br /> İzleme etkin olduğunda, rapor iletileri oluşturulur ve rapor kuyruğa gönderilen ileti ayrıldığında ya da bir Message Queuing bilgisayar ulaştığında her zaman.|  
|useSourceJournal|Bu bağlama tarafından işlenen iletilerin kopyalarını kaynak günlük sırasındaki depolanması gerekip gerekmediğini belirten bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Bilgisayarın giden sırasının bıraktıysanız iletileri kaydını tutmak istediğiniz sıraya alınmış uygulamalar iletilerin günlük kuyruğuna kopyalayabilirsiniz. Giden sırasının bir iletiyi bırakır ve ileti hedef bilgisayarda alındı bir bildirim alındıktan sonra iletinin bir kopyasını gönderen bilgisayarın sistem günlüğü kuyrukta tutulur.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|msmqTransportSecurity|Bu bağlama için taşıma güvenlik ayarlarını belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama yeteneklerini tanımlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Taşımalar](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [WCF'de Kuyruklar](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Taşıma Seçme](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
