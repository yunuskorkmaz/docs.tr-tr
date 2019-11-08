---
title: <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: a68b44d7-7799-43a3-9e63-f07c782810a6
ms.openlocfilehash: 4bc8884b2d4cb6f8201e2038894c69d0805bddda
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738825"
---
# <a name="netmsmqbinding"></a>netMsmqBinding > \<
Makineler arası iletişim için uygun bir sıraya alınmış bağlamayı tanımlar.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<netMsmqBinding >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<netMsmqBinding>
  <binding closeTimeout="TimeSpan"
           customDeadLetterQueue="Uri"
           deadLetterQueue="Uri"
           durable="Boolean"
           exactlyOnce="Boolean"
           maxBufferPoolSize="Integer"
           maxReceivedMessageSize="Integer"
           maxRetryCycles="Integer"
           name="String"
           openTimeout="TimeSpan"
           poisonMessageHandling="Disabled/EnabledIfSupported"
           queueTransferProtocol="Native/Srmp/SrmpSecure"
           receiveErrorHandling="Drop/Fault/Move/Reject"
           receiveTimeout="TimeSpan"
           receiveRetryCount="Integer"
           rejectAfterLastRetry="Boolean"
           retryCycleDelay="TimeSpan"
           sendTimeout="TimeSpan"
           timeToLive="TimeSpan"
           useActiveDirectory="Boolean"
           useMsmqTracing="Boolean"
           useSourceJournal="Boolean">
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/InfoCard" />
      <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`closeTimeout`|Bir kapatma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri. Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır. Varsayılan değer 00:01:00 ' dir.|  
|`customDeadLetterQueue`|Zaman aşımına uğradı veya başarısız aktarım ya da teslimi olan iletilerin yerleştirildiği, uygulama başına atılacak mektup sırasının konumunu içeren bir URI.<br /><br /> Sahipsiz sıra, teslim edilemeyen süre dolmayan iletiler için gönderen uygulamanın kuyruk yöneticisinde bir sıradır.<br /><br /> <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> tarafından belirtilen URI 'nin net. MSMQ şemasını kullanması gerekir.|  
|`deadLetterQueue`|Varsa, ne tür bir atılacak ileti sırasının kullanılacağını belirten <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> değeri.<br /><br /> Atılacak ileti sırası, uygulamaya teslim edilemeyen iletilerin aktarılacağı yerdir.<br /><br /> `exactlyOnce` güvencesi gerektiren iletiler için (yani, `exactlyOnce` özniteliği `true`), bu öznitelik, MSMQ 'daki sistem genelindeki işlem atılacak mektup kuyruğuna varsayılan olarak ayarlanır.<br /><br /> Hiçbir kullanım gerektirmeyen iletiler için, bu özniteliğin varsayılan değeri `null`olur.|  
|`durable`|İletinin kuyrukta dayanıklı mi yoksa geçici mi olduğunu belirten bir Boole değeri. Kalıcı bir ileti bir sıra Yöneticisi kilitlenmesiyle çalışır, geçici bir ileti değildir. Geçici iletiler, uygulamalar daha düşük gecikme süresi gerektirdiğinde ve zaman zaman kaybolmuş iletileri kabul edebildiği durumlarda faydalıdır. `exactlyOnce` özniteliği `true`olarak ayarlanırsa, iletilerin dayanıklı olması gerekir. Varsayılan, `true` değeridir.|  
|`exactlyOnce`|Bu bağlama tarafından işlenen her bir iletinin yalnızca bir kez teslim edilip edilmediğini gösteren Boolean bir değer. Ardından, gönderen teslim arızalarına göre bilgilendirilir. `durable` `false`olduğunda, bu öznitelik yok sayılır ve iletiler teslim güvencesi olmadan aktarılır. Varsayılan, `true` değeridir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|`maxBufferPoolSize`|Bu bağlama için en büyük arabellek havuzu boyutunu belirten bir tamsayı. Varsayılan değer 8 ' dir.|  
|`maxReceivedMessageSize`|Bu bağlama tarafından işlenen üst bilgiler dahil olmak üzere bayt cinsinden en büyük ileti boyutunu tanımlayan pozitif bir tamsayı. Bu sınırı aşan bir iletiyi gönderen bir SOAP hatası alır. Alıcı, iletiyi bırakır ve izleme günlüğünde olayın bir girişini oluşturur. Varsayılan değer 65536 ' dir. İleti boyutu sınırı, hizmet reddi (DoS) saldırılarına maruz kalma olasılığını sınırlandırmaya yöneliktir.|  
|`maxRetryCycles`|Zarar iletisi algılama özelliği tarafından kullanılan yeniden deneme döngüsü sayısını belirten bir tamsayı. Tüm Döngülerde tüm teslim denemeleri başarısız olduğunda bir ileti bir zarar iletisi haline gelir. Varsayılan değer 3 ' dir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|`name`|Gerekli öznitelik. Bağlamanın yapılandırma adını içeren bir dize. Bağlama için bir kimlik olarak kullanıldığından, bu değer benzersiz olmalıdır. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak bağlamalar ve davranışları bir ada sahip olmak için gerekli değildir. Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.|  
|`openTimeout`|Bir açık işlemin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri. Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır. Varsayılan değer 00:01:00 ' dir.|  
|`QueueTransferProtocol`|Bu bağlamanın kullandığı sıraya alınmış iletişim kanalı aktarımını belirten geçerli bir <xref:System.ServiceModel.QueueTransferProtocol> değeri. MSMQ, SOAP Güvenilir Mesajlaşma Protokolü kullanırken Active Directory adreslemeyi desteklemez. Bu nedenle, `useActiveDirectory` özniteliği `true`olarak ayarlandığında, bu özniteliği `Srmp` veya `Srmps` olarak ayarlayamazsınız.|  
|`receiveErrorHandling`|Zebilen ve dağıtılabilir iletilerin nasıl işleneceğini belirten <xref:System.ServiceModel.ReceiveErrorHandling> bir değer.|  
|`receiveRetryCount`|Sıra yöneticisinin yeniden deneme kuyruğuna aktarmadan önce bir ileti göndermek için kaç kez denemesi gerektiğini belirten bir tamsayı.|  
|`receiveTimeout`|Alma işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri. Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır. Varsayılan değer 00:10:00 ' dir.|  
|`retryCycleDelay`|Anında teslim edilmemiş bir iletiyi teslim etmeye çalışırken yeniden deneme döngüleri arasındaki gecikme süresini belirten bir TimeSpan değeri. Değer yalnızca en düşük bekleme süresini tanımlar çünkü gerçek bekleme süresi daha uzun olabilir. Varsayılan değer 00:10:00 ' dir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|`sendTimeout`|Bir gönderme işleminin tamamlanabilmesi için belirtilen zaman aralığını belirten bir <xref:System.TimeSpan> değeri. Bu değer, <xref:System.TimeSpan.Zero>eşit veya ondan büyük olmalıdır. Varsayılan değer 00:01:00 ' dir.|  
|`timeToLive`|İletilerin süre dolmadan önce ne kadar süreyle geçerli olduğunu belirten bir TimeSpan değeri ve atılacak ileti kuyruğuna yerleştirirsiniz. Varsayılan değer 1.00:00:00 ' dır.<br /><br /> Bu öznitelik, zaman duyarlı iletilerin, alıcı uygulamalar tarafından işlenmeden önce eski hale gelmemesini sağlamak üzere ayarlanır. Belirtilen zaman aralığı içinde alıcı uygulama tarafından tüketilmeyen bir kuyruktaki ileti, süresi dolmaya yönelik olarak kabul edilir. Süre dolmayan iletiler, atılacak ileti sırası adlı özel bir kuyruğa gönderilir. Atılacak ileti sırasının konumu, `DeadLetterQueue` özniteliğiyle veya uygun varsayılan değer ile belirlenir.|  
|`usingActiveDirectory`|Sıra adreslerinin Active Directory kullanılarak dönüştürülmesi gerekip gerekmediğini belirten bir Boole değeri.<br /><br /> MSMQ kuyruğu adresleri, yol adlarından veya doğrudan biçim adlarından oluşabilir. Doğrudan biçim adıyla, MSMQ, DNS, NetBIOS veya IP kullanarak bilgisayar adını çözer. Bir yol adıyla, MSMQ Active Directory kullanarak bilgisayar adını çözer.<br /><br /> Varsayılan olarak, Windows Communication Foundation (WCF) sıraya alınan aktarım, bir ileti sırasının URI 'sini doğrudan biçim adına dönüştürür. `UseActiveDirectory` özelliği true olarak ayarlandığında, bir uygulama sıraya alınan taşımanın DNS, NetBIOS veya IP yerine Active Directory kullanarak bilgisayar adını çözmesi gerektiğini belirtebilir.|  
|`useMsmqTracing`|Bu bağlama tarafından işlenen iletilerin izlenip izlenmeyeceğini belirten bir Boole değeri. Varsayılan, `false` değeridir. İzleme etkinleştirildiğinde, ileti Message Queuing bilgisayara her ayrıldığında veya ulaştığında rapor iletileri oluşturulur ve rapor kuyruğuna gönderilir.|  
|`useSourceJournal`|Bu bağlama tarafından işlenen iletilerin kopyalarını belirten bir Boole değeri, kaynak günlüğünde depolanmalıdır. Varsayılan, `false` değeridir.<br /><br /> Bilgisayarın giden sırasının ayrılmasına sahip bir ileti kaydını tutmak isteyen sıraya alınmış uygulamalar iletileri bir günlük kuyruğuna kopyalayabilir. İleti, giden sırasından ayrıldığında ve iletinin hedef bilgisayarda alındığı bir bildirim alındıktan sonra iletinin bir kopyası gönderen bilgisayarın sistem günlüğü kuyruğunda tutulur.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Bu bağlama ile yapılandırılan uç noktalar tarafından işlenebileceğini SOAP iletilerinin karmaşıklığı üzerindeki kısıtlamaları tanımlar. Bu öğe <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>türündedir.|  
|[\<Güvenlik >](security-of-netmsmqbinding.md)|Bağlama için güvenlik ayarlarını tanımlar. Bu öğe <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>türündedir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bindings >](bindings.md)|Bu öğe, standart ve özel bağlamaların bir koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `netMsmqBinding` bağlama, bir taşıma olarak Microsoft Message Queuing (MSMQ) kullanarak sıraya alma desteği sağlar ve gevşek olarak bağlanmış uygulamalar, hata yalıtımı, yük dengeleme ve bağlantısı kesik işlemler için destek sağlar. Bu özelliklerle ilgili bir tartışma için bkz. [WCF 'de kuyruklar](../../../wcf/feature-details/queues-in-wcf.md).  
  
## <a name="example"></a>Örnek  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <netMsmqBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 deadLetterQueue="net.msmq://localhost/blah"
                 durable="true"
                 exactlyOnce="true"
                 maxReceivedMessageSize="1000"
                 maxRetries="11"
                 maxRetryCycles="12"
                 poisonMessageHandling="Disabled"
                 rejectAfterLastRetry="false"
                 retryCycleDelay="00:05:55"
                 timeToLive="00:11:11"
                 sourceJournal="true"
                 useMsmqTracing="true"
                 useActiveDirectory="true">
          <security>
            <message clientCredentialType="Windows" />
          </security>
        </binding>
      </netMsmqBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.NetMsmqBinding>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement>
- [\< bağlama >](bindings.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [WCF'de Kuyruklar](../../../wcf/feature-details/queues-in-wcf.md)
