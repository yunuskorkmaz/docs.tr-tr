---
title: '&lt;msmqIntegration&gt;'
ms.date: 03/30/2017
ms.assetid: ab677405-1ffe-457a-803f-00c1770e51e2
ms.openlocfilehash: 36c71546dd481d634210901b20ddeaa86d5c81a4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltmsmqintegrationgt"></a>&lt;msmqIntegration&gt;
Özel bağlama için MSMQ taşıma belirtir.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<msmqIntegration >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<msmqIntegration>  
        customDeadLetterQueue="Uri"  
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
    useMsmqTracing="Boolean"  
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
|customDeadLetterQueue|Süresi dolmuş veya uygulamaya teslim edilecek başarısız iletileri burada aktarılır uygulama başına sahipsiz sıra konumunu gösteren bir URI.<br /><br /> ExactlyOnce çıkışların gerektir iletileri için (diğer bir deyişle, `exactlyOnce` ayarlanır `true`), bu öznitelik Varsayılanları MSMQ sistem genelinde işlem sahipsiz sıraya.<br /><br /> Hiçbir garanti vermediğini gerektiren iletileri için (diğer bir deyişle, `exactlyOnce` ayarlanır `false`), bu öznitelik için varsayılan olarak `null`.<br /><br /> Değeri net.msmq şeması kullanması gerekir. Varsayılan, `null` değeridir.<br /><br /> Varsa `d``eadLetterQueue` ayarlanır `None` veya `System`, bu öznitelik ayarlamak sonra `null`. Bu öznitelik yoksa `null`, ardından `deadLetterQueue` ayarlanmalıdır `Custom`.|  
|deadLetterQueue|Sahipsiz sıra kullanılacak türünü belirtir.<br /><br /> Geçerli değerler arasında<br /><br /> -Özel: Özel sahipsiz sıraya.<br />-: Sahipsiz sıra kullanılacak Yok'tur.<br />-Sistem: Sistem sahipsiz sıraya kullanın.<br /><br /> Bu öznitelik DeadLetterQueue türüdür.|  
|dayanıklı|Bu bağlama tarafından işlenen iletilerin kalıcı veya geçici olup olmadığını belirten bir Boole değeri. Varsayılan, `true` değeridir.<br /><br /> Geçici bir ileti çalışmazken dayanıklı bir ileti sırası Yöneticisi kilitlenme devam eder. Uygulamalar düşük gecikme süresi gerektirir ve nadiren kayıp iletilerle dayanabilir volatile iletileri yararlı olur.<br /><br /> Varsa `exactlyOnce` ayarlanır `true`, iletileri dayanıklı olması gerekir.|  
|exactlyOnce|Bu bağlama tarafından işlenen iletilerin tam olarak bir kez alınan olup olmadığını belirten bir Boole değeri. Varsayılan, `true` değeridir.<br /><br /> Bir ileti ile veya olmadan çıkışların gönderilebilir. Uygulamaya gönderilen bir ileti alıcı ileti sıraya ulaştı veya belirlemediyseniz, uygulama bu sahipsiz sıra okuyarak belirleyebilirsiniz emin olmak için bir güvence sağlar.<br /><br /> `exactlyOnce`, ayarlandığında `true`, MSMQ gönderilen iletiyi, yalnızca tek bir kez alıcı ileti kuyruğuna teslim edilir ve teslim başarısız olursa, ileti sahipsiz sıraya gönderilen sağlayacak gösterir.<br /><br /> İle gönderilen iletileri `exactlyOnce` kümesine `true` yalnızca bu bir işlem sırası gönderilmelidir.|  
|manualAddressing|Kullanıcının ileti adresleme denetimini olanak tanıyan bir Boole değeri. Bu özellik genellikle burada hangisinin bir ileti göndermek için birden fazla hedef uygulama belirler yönlendirici senaryolarda kullanılır.<br /><br /> Ayarlandığında `true`, ileti zaten giderilmiş ve ek bilgiler için eklemez kanal varsayar. Kullanıcı daha sonra her ileti tek tek ele alabilir.<br /><br /> Ayarlandığında `false`, varsayılan Windows Communication Foundation (WCF) adresleme mekanizması adresleri tüm iletiler için otomatik olarak oluşturur.<br /><br /> Varsayılan, `false` değeridir.|  
|maxBufferPoolSize|Arabellek havuzu boyutunun üst sınırını belirtir pozitif bir tamsayı. 524288 varsayılandır.<br /><br /> WCF pek çok bölümü arabellekleri kullanın. Oluşturma ve her defa arabellek yok etme pahalıdır ve atık toplama arabellekleri için de pahalıdır. Arabellek havuzu ile havuzdan bir arabellek ayırın, kullanmak ve tamamladıktan sonra havuza geri dönemez. Bu nedenle oluşturma ve yok etme arabellekleri ek yük önlenmiş olur.|  
|maxImmediateRetries|Uygulama sırasından okunan bir ileti üzerinde hemen yeniden deneme sayısını belirten bir tamsayı çalışır... Varsayılan değer 5'tir.<br /><br /> İleti için hemen yeniden deneme sayısı çalıştı ve ileti uygulama tarafından tüketilmeyen, daha sonraki bir noktada zamanında yeniden deneniyor için Yeniden Dene'yi kuyruğuna ileti gönderilir. Yeniden deneme döngüsü belirtilirse, ardından iletileri ya da gönderilir zehirli ileti kuyruğuna veya gönderene olumsuz bildirim gönderilir.|  
|maxReceivedMessageSize|Üst bilgileri de dahil olmak üzere bayt cinsinden maksimum ileti boyutu belirtir pozitif bir tamsayı. İleti alıcı için çok büyük olduğunda bir ileti gönderen bir SOAP hatasını alır. Alıcı iletiyi bırakır ve izleme günlüğüne olay bir giriş oluşturur. 65536 varsayılandır.|  
|maxRetryCycles|En fazla yeniden deneme sayısını belirten bir tamsayı iletileri teslim alma işlemini yapan uygulamanın için girişiminde geçiş yapar. Varsayılan, <xref:System.Int32.MaxValue> değeridir.<br /><br /> Bir ileti bir uygulamanın belirtilen sayıda sunmak tek bir yeniden deneme döngüsü çalışır. Gerçekleştirilen denemelerin sayısı belirlediği `maxImmediateRetries` özniteliği. İleti teslim girişimleri tüketmiş sonra kullanmak üzere uygulama başarısız olursa yeniden kuyruğa ileti gönderilir. Sonraki yeniden deneme döngüsü tarafından belirtilen bir gecikmeden sonra uygulamaya tekrar teslim denemek için yeniden deneme sıradan uygulama kuyruğuna döndürülen ileti oluşur `retryCycleDelay` özniteliği. `maxRetryCycles` Özniteliği, uygulamanın kullandığı teslim etmeyi denemek için yeniden deneme döngüsü sayısını belirtir.|  
|rejectAfterLastRetry|Bir Boole değeri en fazla yeniden deneme sayısı denemelerinin sonra teslim başarısız oldu bir ileti için gerçekleştirilecek eylemi belirtir.<br /><br /> `true` olumsuz bildirim gönderene döndürülür ve ileti bırakılan anlamına gelir; `false` ileti zehirli ileti kuyruğa gönderilir anlamına gelir. Varsayılan, `false` değeridir.<br /><br /> Değer ise `false`, alma işlemini yapan uygulamanın zarar iletileri (diğer bir deyişle, teslim başarısız olmuş iletileri) işlemek için zehirli ileti sırası okuyabilirsiniz.<br /><br /> MSMQ 3.0 MSMQ 3. 0'bu öznitelik yoksayılacak şekilde olumsuz bildirim gönderene iade desteklemez.|  
|retryCycleDelay|A <xref:System.TimeSpan> yeniden deneme döngüsü arasındaki gecikme süresini belirleyen hemen teslim edilemeyen bir ileti teslim çalışılırken. Varsayılan değer 00:10: 00'dır.<br /><br /> İleti alıcı uygulama tarafından belirtilen sayıda sunmak tek bir yeniden deneme döngüsü çalışır. Gerçekleştirilen denemelerin sayısı tarafından belirtilen `maxImmediateRetries` özniteliği. İleti belirtilen hemen yeniden deneme sayısı sonra kullanmak üzere uygulama başarısız olursa yeniden kuyruğa ileti gönderilir. Sonraki yeniden deneme döngüsü tarafından belirtilen bir gecikmeden sonra uygulamaya tekrar teslim denemek için yeniden deneme sıradan uygulama kuyruğuna döndürülen ileti oluşur `retryCycleDelay` özniteliği. Yeniden deneme döngüsü sayısını tarafından belirtilen `maxRetryCycles` özniteliği.|  
|serializationFormat|Bir MSMQ iletisinin bir parçası olarak gönderilen nesneleri serileştirmek için kullanılan biçimlendirici belirtir. Geçerli değerler:<br /><br /> -ActiveX: COM nesneleri seri hale getirme ActiveX biçimlendirici kullanılır.<br />-İkili: ikili paket nesneyi Serileştirir.<br />-ByteArray: bir bayt dizisi nesneyi Serileştirir.<br />-Akış: nesneyi bir akışa Serileştirir.<br />-Xml: XML paket nesneyi Serileştirir. XML varsayılandır.<br /><br /> Bu öznitelik türünde <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat>.|  
|TimeToLive|A <xref:System.TimeSpan> iletileri süresi ve teslim edilemeyen Kuyruğa koymak önce ne kadar süreyle geçerlidir belirtir. 1 gün anlamına gelir 1.00:00:00 varsayılandır.<br /><br /> Bu öznitelik, alıcı uygulamalar tarafından işlenmeden önce zamana duyarlı iletileri eski hale gelmediğinden emin olmak için ayarlanır. Belirtilen zaman aralığı içinde alıcı uygulama tarafından tüketilmeyen bir kuyruktaki ileti süresinin kabul edilir. Süresi dolan iletileri sahipsiz sıra adı verilen özel kuyruğuna gönderilir. Sahipsiz Sıra konumu ile ayarlanır `customDeadLetterQueue` uygun varsayılana göre sağlandığına üzerinde veya öznitelik.|  
|useMsmqTracing|Bu bağlama tarafından işlenen iletileri olup olmadığını belirten bir Boole değeri izlenen. Varsayılan, `false` değeridir.<br /><br /> İzleme etkinleştirildiğinde Raporu iletilerini oluşturulur ve ileti ayrıldığında ya da bir Message Queuing bilgisayar ulaştığında her zaman rapor sırasına gönderilir.|  
|useSourceJournal|Bu bağlama tarafından işlenen iletilerin kopyalarını kaynak günlük sırasındaki depolanması gerekip gerekmediğini belirten bir Boole değeri. Varsayılan, `false` değeridir.<br /><br /> Bilgisayarın giden sırasının bıraktıysanız iletileri kaydını tutmak istediğiniz sıraya alınan uygulamaları iletileri günlük kuyruğuna kopyalayabilirsiniz. Giden sırasının bir ileti bırakır ve ileti hedef bilgisayarda alındı bir bildirim alındıktan sonra iletinin bir kopyasını gönderen bilgisayarın sistem günlük sırasındaki tutulur.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|msmqTransportSecurity|Bu bağlama için Aktarım güvenlik ayarlarını belirtir. Bu öğe türünde <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama özelliklerini tanımlar.|  
  
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
