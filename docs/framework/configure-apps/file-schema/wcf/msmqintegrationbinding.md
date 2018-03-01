---
title: '&lt;msmqIntegrationBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- msmqIntegrationBinding Element
ms.assetid: edf277f3-e3bf-4ed8-9f55-83b5788430a7
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0715952077db755386a0381f68ccc6e33705a031
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ltmsmqintegrationbindinggt"></a>&lt;msmqIntegrationBinding&gt;
MSMQ aracılığıyla yönlendirme ileti kuyruğa alma desteği sağlayan bir bağlama tanımlar.  
  
 \<system.ServiceModel>  
\<bağlamaları >  
msmqIntegrationBinding  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<msmqIntegrationBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       customDeadLetterQueue="Uri"  
       deadLetterQueue="Uri"  
       durable="Boolean"  
       exactlyOnce="Boolean"   
       maxReceivedMessageSize"Integer"  
       maxRetryCycles="Integer"   
       name="string"   
       openTimeout="TimeSpan"        receiveContextEnabled="Boolean"  
       receiveErrorHandling="Drop/Fault/Move/Reject"  
       receiveTimeout="TimeSpan"   
       receiveRetryCount="Integer"  
       retryCycleDelay="TimeSpan"    
       sendTimeout="TimeSpan"   
       serializationFormat="XML/Binary/ActiveX/ByteArray/Stream">  
       timeToLive="TimeSpan"    
       useMsmqTracing="Boolean  
       useSourceJournal="Boolean"  
   </binding>  
</msmqIntegrationBinding>   
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt öğelerini ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|closeTimeout|A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığı belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|customDeadLetterQueue|Süresi dolan veya aktarımı veya teslim başarısız olmuş iletileri yerleştirildiği uygulama başına sahipsiz sıra konumunu içeren bir URI.<br /><br /> Sahipsiz Sıra Yöneticisi için teslim başarısız süresi dolan iletileri gönderen uygulaması bulunan bir sıra sırasıdır.<br /><br /> Belirtilen URI <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> net.msmq şeması kullanması gerekir.|  
|deadLetterQueue|A <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>.value varsa kullanmak için eski ileti sırası türünü belirtme<br /><br /> Sahipsiz Sıra uygulamaya teslim başarısız iletileri aktarılacak konumdur.<br /><br /> ExactlyOnce güvenliği gerektiren iletileri için (yani, `exactlyOnce` özniteliği `true`), bu öznitelik Varsayılanları MSMQ sistem genelinde işlem sahipsiz sıraya.<br /><br /> Bu öznitelik varsayılan olarak hiçbir garanti vermediğini gerektiren iletileri `null`.|  
|dayanıklı|İleti dayanıklı veya sıradaki volatile olup olmadığını belirten bir Boole değeri. Geçici bir ileti çalışmazken dayanıklı bir ileti sırası Yöneticisi kilitlenme devam eder. Uygulamalar düşük gecikme süresi gerektirir ve nadiren kayıp iletilerle dayanabilir volatile iletileri yararlı olur. Varsa `exactlyOnce` özniteliği `true`, iletileri dayanıklı olması gerekir. Varsayılan, `true` değeridir.|  
|exactlyOnce|Her ileti yalnızca bir kere teslim olup olmadığını gösteren bir Boole değeri. Gönderenin ardından teslim hatalarının bildirilir. Zaman `durable` olan `false`, bu öznitelik dikkate alınmaz ve iletileri teslim güvence aktarılır. Varsayılan, `true` değeridir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|maxReceivedMessageSize|Bu bağlama tarafından işlenen başlıkları dahil bayt cinsinden maksimum ileti boyutu tanımlayan bir pozitif tamsayı. Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alır. Alıcı iletiyi bırakır ve izleme günlüğüne olay bir giriş oluşturur. 65536 varsayılandır. Bu ileti boyutuna bağlı hizmet reddi (DoS) saldırılarına maruz sınırlamak için tasarlanmıştır.|  
|maxRetryCycles|Poison ileti algılama özelliği tarafından kullanılan yeniden deneme döngüsü sayısını belirten bir tamsayı. Tüm döngü tüm Teslim girişimleri başarısız olduğunda bir ileti zararlı bir ileti haline gelir. Varsayılan değer 2'dir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|name|Bağlama yapılandırma adını içeren dize. Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir. Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|receiveErrorHandling|A <xref:System.ServiceModel.ReceiveErrorHandling> poison ve nondispatchable iletileri nasıl işleneceğini belirten değer.|  
|receiveRetryCount|Uygulama uygulama sırasından ileti aktarımını başarısız olursa hemen yeniden deneme sayısını belirten bir tamsayı sıra yöneticisini denemeniz gerekir.<br /><br /> Teslim deneme sayısı üst sınırına ve ileti uygulama tarafından erişilen değil, ardından ileti yeniden teslim için Yeniden Dene'yi sırasına daha sonraki bir zamanda gönderilir. İletinin gönderen sıranın aktarılır önceki süreyi tarafından denetlenen `retryCycleDelay`. Yeniden deneme ulaşma döngüleri varsa `maxRetryCycles` değeri, ileti ya da poison ileti kuyruğa gönderilir veya gönderene olumsuz bildirim gönderilir.|  
|receiveTimeout|A <xref:System.TimeSpan> bir alma işleminin tamamlanması için sağlanan zaman aralığı belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:10: 00'dır.|  
|receiveContextEnabled|Olduğunu belirten bir Boole değeri sıralarındaki iletileri işleme etkinleştirilmişse bağlamını alır. Bu ayarlandığında `true`, bir hizmeti ", işleme başlamak için bir ileti sırasına iletiye göz atabilirsiniz" ve, herhangi bir şey yanlış gider ve bir özel durum, sıranın üzerinde kalır. Hizmetleri de "sonraki bir zamanda işleme süresi, yeniden denemek için iletileri kilitleyebilirsiniz". ReceiveContext "iletiyi sıradan kaldırılan bir kez işlenir Tamamlanıyor" için bir mekanizma sağlar. İletileri artık ağ üzerinden okuma ve yazılı yeniden sıralar yorumlanır ve tek bir ileti işleme sırasında farklı hizmet örnekleri arasında geçirmek değil.|  
|retryCycleDelay|Yeniden deneme arasındaki gecikme süresini belirten bir TimeSpan değeri hemen teslim edilemeyen bir ileti teslim çalışılırken geçiş yapar. En düşük bekleyin yalnızca zaman gerçek bekleme süresi uzun olabileceğinden değeri tanımlar. Varsayılan değer 00:30: 00'dır. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|sendTimeout|A <xref:System.TimeSpan> bir gönderme işleminin tamamlanması için sağlanan zaman aralığı belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|serializationFormat|İleti gövdesini serileştirmek için kullanılan biçim tanımlar. Bu öznitelik türünde <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat>.|  
|timeToLive|Ne kadar süreyle iletileri belirten bir TimeSpan değeri geçerli süresi ve teslim edilemeyen kuyruğuna önce. 1.00:00:00 varsayılandır.<br /><br /> Bu öznitelik, alıcı uygulamalar tarafından işlenmeden önce zamana duyarlı iletileri eski hale gelmediğinden emin olmak için ayarlanır. Belirtilen zaman aralığı içinde alıcı uygulama tarafından tüketilmeyen bir kuyruktaki ileti süresinin kabul edilir. Süresi dolan iletileri sahipsiz sıra adı verilen özel kuyruğuna gönderilir. Sahipsiz Sıra konumu ile ayarlanır `DeadLetterQueue` uygun varsayılana göre sağlandığına üzerinde veya öznitelik.|  
|useMsmqTracing|Bu bağlama tarafından işlenen iletileri olup olmadığını belirten bir Boole değeri izlenen. Varsayılan, `false` değeridir. İzleme etkinleştirildiğinde Raporu iletilerini oluşturulur ve ileti ayrıldığında ya da bir Message Queuing bilgisayar ulaştığında her zaman rapor sırasına gönderilir.|  
|useSourceJournal|Bu bağlama tarafından işlenen iletilerin kopyalarını belirten bir Boole değeri kaynak günlüğünde depolanması gerekir. Varsayılan, `false` değeridir.<br /><br /> Bilgisayarın giden sırasının bıraktıysanız iletileri kaydını tutmak istediğiniz sıraya alınan uygulamaları iletileri günlük kuyruğuna kopyalayabilirsiniz. Giden sırasının bir ileti bırakır ve ileti hedef bilgisayarda alındı bir bildirim alındıktan sonra iletinin bir kopyasını gönderen bilgisayarın sistem günlük sırasındaki tutulur.|  
  
## <a name="serializationformat-attribute"></a>{serializationFormat} Özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Xml|XML biçimi|  
|İkili|İkili biçimi|  
|ActiveX|ActiveX biçimi|  
|ByteArray|Bir bayt dizisi nesneyi serileştirir.|  
|Akış|Bir akış olarak biçimlendirilmiş gövdesi|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-msmqintegrationbinding.md)|Bağlama için güvenlik ayarlarını tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlamaları >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Bu öğe, standart ve özel bağlamaları koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu bağlama öğesi ileti göndermek ve COM, MSMQ yerel API'leri veya tanımlanan türler kullanan mevcut MSMQ uygulamalardan iletileri almak Windows Communication Foundation (WCF) uygulamalarını etkinleştirmek için kullanılabilir <xref:System.Messaging?displayProperty=nameWithType> ad alanı, Aktarım çıkışların sıranın adres yolları iletileri işlemi depolanmalıdır olup olmadığını belirtmek için bu yapılandırma öğesi ve iletileri nasıl korumalı ve kimlik doğrulaması kullanabilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: WCF uç noktaları ve Message Queuing uygulamaları ile Exchange iletileri](../../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md).  
  
## <a name="example"></a>Örnek  
  
```xml  
<configuration>  
<system.ServiceModel>  
    <bindings>  
       <msmqIntegrationBinding>  
           <binding   
                    closeTimeout="00:00:10"   
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
       </msmqIntegrationBinding  
   </bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [WCF'de Kuyruklar](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
