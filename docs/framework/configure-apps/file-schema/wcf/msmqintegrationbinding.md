---
title: '&lt;MsmqIntegrationBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- msmqIntegrationBinding Element
ms.assetid: edf277f3-e3bf-4ed8-9f55-83b5788430a7
ms.openlocfilehash: 1493cb6f9588ee618b085186b3bb63476a9a8930
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841024"
---
# <a name="ltmsmqintegrationbindinggt"></a>&lt;MsmqIntegrationBinding&gt;
MSMQ yönlendirme iletileri tarafından sıraya alma desteği sağlayan bir bağlama tanımlar.  
  
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
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|closeTimeout|A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|customDeadLetterQueue|Aktarım veya teslim başarısız olan veya süresi dolmuş olan iletileri yerleştirildiği uygulama başına yitirmiş kuyruk konumunu içeren bir URI.<br /><br /> Teslim edilemeyen bir kuyruğa gönderen bir uygulama teslim başarısız olmuş süresi dolan iletileri için Kuyruk yöneticisi kuyruğudur.<br /><br /> Tarafından belirtilen URI <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> net.msmq şeması kullanması gerekir.|  
|deadLetterQueue|A <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>.value varsa kullanmak için eski ileti sırası türünü belirtme<br /><br /> Eski ileti sırası uygulamaya teslim edilmesi için başarısız olan iletiler aktarılacak konumdur.<br /><br /> ExactlyOnce güvencesi gerektiğinden iletiler için (yani, `exactlyOnce` özniteliği `true`), bu öznitelik varsayılan olarak, MSMQ sistem genelinde işlem eski ileti sırası için.<br /><br /> Bu öznitelik varsayılan olarak hiçbir Güvenceleri gerektiren iletileri `null`.|  
|dayanıklı|Sürekli veya geçici sırasındaki ileti olup olmadığını belirten bir Boole değeri. Geçici bir ileti çalışmazken kalıcı bir ileti kuyruğu manager kilitlenme devam eder. Uygulamalar düşük gecikme süresi gerektirir ve ara sıra kayıp iletiler tolere edebilen geçici iletileri yararlıdır. Varsa `exactlyOnce` özniteliği `true`, iletileri dayanıklı olması gerekir. Varsayılan, `true` değeridir.|  
|exactlyOnce|Her ileti yalnızca bir kere teslim olup olmadığını gösteren bir Boole değeri. Gönderen sonra teslim hatalarının bildirilir. Zaman `durable` olduğu `false`, bu öznitelik yoksayılır ve iletileri teslim güvencesi aktarılır. Varsayılan, `true` değeridir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|maxReceivedMessageSize|Bu bağlama tarafından işlenen en büyük ileti boyutu, üst bilgiler, dahil, bayt cinsinden tanımlayan pozitif bir tamsayı. Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alırsınız. Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur. 65536 varsayılandır. Bu ileti boyutuna bağlı hizmet reddi (DoS) saldırılarına maruz kalma riskinizi sınırlamak içindir.|  
|maxRetryCycles|Poison ileti algılama özelliği tarafından kullanılan yeniden deneme döngüsü sayısını belirten bir tamsayı. Tüm döngüleri, tüm teslim denemesi başarısız olduğunda bir ileti zehirli ileti haline gelir. Varsayılan değer 2'dir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|name|Bağlama yapılandırma adını içeren bir dize. Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip. Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|opentimeout =|A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|receiveErrorHandling|A <xref:System.ServiceModel.ReceiveErrorHandling> poison ve nondispatchable iletileri nasıl işlendiğini belirten bir değer.|  
|receiveRetryCount|Uygulamaya uygulama kuyruktan bir ileti aktarımını başarısız olursa en fazla hemen yeniden deneme sayısını belirten bir tamsayı sıra yöneticisini denemelidir.<br /><br /> Teslim denemeleri sayısı üst sınırına ve ileti uygulama tarafından erişilen değil, ardından ileti yeniden teslim için bir yeniden deneme kuyruğu daha sonraki bir zamanda gönderilir. İletiyi gönderen sıranın aktarılır önce geçen süreyi tarafından denetlenir `retryCycleDelay`. Yeniden deneme ulaşma döngüleri, `maxRetryCycles` değer, iletinin ya da zarar ileti kuyruğa gönderilir veya negatif onayı gönderene gönderilir.|  
|receiveTimeout|A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:10:00 ' dir.|  
|receiveContextEnabled|Sıralarındaki iletileri işleme etkinleştirilmişse bağlam olmadığını belirten Boolean bir değer alır. Bu ayarlandığında `true`hizmet ", işleme başlamak için kuyruktaki bir iletiye Gözat" ve, herhangi bir şey yanlış giden bir özel durum varsa, kuyrukta kalır. Hizmetler ayrıca "iletileri daha sonraki bir noktada bir işleme süresi, yeniden deneme kilitleyebilirsiniz". ReceiveContext "ileti kuyruktan kaldırılabilmesi için bir kez işlenen tamamlama" için bir mekanizma sağlar. İletileri artık ağ üzerinden okunan ve yazılan yeniden sıralar gönderildiğini ve tek bir ileti işlenirken farklı hizmet örnekleri arasında geçirmek değildir.|  
|retryCycleDelay|Anında teslim edilemeyen bir iletiyi teslim etmeye çalışırken deneme arasındaki gecikmeyi belirten bir TimeSpan değeri dolaşır. En düşük bekleyin yalnızca zaman gerçek bir bekleme süresi uzun olabilir çünkü değeri tanımlar. Varsayılan değer 00:30:00 ' dir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|SendTimeout|A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|serializationFormat|İleti gövdesini serileştirmek için kullanılan biçimi tanımlar. Bu öznitelik türünde <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat>.|  
|timeToLive|Ne kadar ileti belirten bir TimeSpan değeri geçerli süreleri dolmadan ve teslim edilemeyen kuyruğa alınan önce. 1.00:00:00 varsayılandır.<br /><br /> Bu öznitelik, bunlar alıcı uygulamalar tarafından işlenmeden önce zamana duyarlı iletileri eski hale gelmediğinden emin olmak için ayarlanır. Belirtilen zaman aralığı içinde alıcı uygulama tarafından tüketilmeyen bir kuyruktaki bir iletiyi süresi dolmuş kabul edilir. Süresi dolan iletileri geçerliliğini yitirmiş kuyruk adı verilen özel kuyruğa gönderilir. Geçerliliğini yitirmiş kuyruk konumu ile ayarlanır `DeadLetterQueue` özniteliği veya uygun varsayılana dayalı Güvenceleri üzerinde.|  
|useMsmqTracing|İletileri bu bağlama tarafından işlenen olup olmadığını belirten bir Boole değeri izlenip izlenmemesini gerektiğini. Varsayılan, `false` değeridir. İzleme etkin olduğunda, rapor iletileri oluşturulur ve rapor kuyruğa gönderilen ileti ayrıldığında ya da bir Message Queuing bilgisayar ulaştığında her zaman.|  
|useSourceJournal|Bu bağlama tarafından işlenen iletilerin kopyalarını belirten bir Boole değeri kaynak günlüğü depolanması gerekir. Varsayılan, `false` değeridir.<br /><br /> Bilgisayarın giden sırasının bıraktıysanız iletileri kaydını tutmak istediğiniz sıraya alınmış uygulamalar iletilerin günlük kuyruğuna kopyalayabilirsiniz. Giden sırasının bir iletiyi bırakır ve ileti hedef bilgisayarda alındı bir bildirim alındıktan sonra iletinin bir kopyasını gönderen bilgisayarın sistem günlüğü kuyrukta tutulur.|  
  
## <a name="serializationformat-attribute"></a>{serializationFormat} Özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|Xml|XML biçimi|  
|İkili|İkili biçimi|  
|ActiveX|ActiveX biçimi|  
|ByteArray|Bir bayt dizisi nesneyi serileştirir.|  
|Akış|Bir akış şeklinde biçimlendirilmiş gövdesi|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-msmqintegrationbinding.md)|Bağlama için güvenlik ayarlarını tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlamaları >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu bağlama öğesi, COM, MSMQ yerel API'lerin veya tanımlanan türleri kullanan mevcut MSMQ uygulamaları'ndan mesajlar alır ve ileti göndermek Windows Communication Foundation (WCF) uygulamalarını etkinleştirmek için kullanılabilir <xref:System.Messaging?displayProperty=nameWithType> ad alanı, Aktarım Güvenceleri sıranın adres yolları iletileri arızaya depolanmalıdır olup olmadığını belirtmek için bu yapılandırma öğesi ve iletilerin nasıl korumalı ve kimlik doğrulaması kullanabilirsiniz. Daha fazla bilgi için [nasıl yapılır: WCF uç noktaları ve Message Queuing uygulamaları ile Exchange ileti](../../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md).  
  
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
 [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [WCF'de Kuyruklar](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
