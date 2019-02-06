---
title: <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: a68b44d7-7799-43a3-9e63-f07c782810a6
ms.openlocfilehash: 22303a81d32369e77f745d32ff1f66e21a3c3156
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759411"
---
# <a name="netmsmqbinding"></a>\<netMsmqBinding>
Çapraz makine haberleşmesi için kuyruğa alınan bir bağlama tanımlar.  
  
 \<system.ServiceModel>  
\<bağlamaları >  
\<netMsmqBinding>  
  
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
|`closeTimeout`|A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|`customDeadLetterQueue`|Aktarım veya teslim başarısız olan veya süresi dolmuş olan iletileri yerleştirildiği uygulama başına yitirmiş kuyruk konumunu içeren bir URI.<br /><br /> Teslim edilemeyen bir kuyruğa gönderen bir uygulama teslim başarısız olmuş süresi dolan iletileri için Kuyruk yöneticisi kuyruğudur.<br /><br /> Tarafından belirtilen URI <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> net.msmq şeması kullanması gerekir.|  
|`deadLetterQueue`|A <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> varsa kullanmak için eski ileti sırası türünü belirten değer.<br /><br /> Eski ileti sırası uygulamaya teslim edilmesi için başarısız olan iletileri burada aktarılacak yerdir.<br /><br /> Gerektiren iletileri `exactlyOnce` güvencesi (diğer bir deyişle, `exactlyOnce` özniteliği `true`), bu öznitelik varsayılan olarak, MSMQ sistem genelinde işlem eski ileti sırası için.<br /><br /> Bu öznitelik varsayılan olarak hiçbir Güvenceleri gerektiren iletileri `null`.|  
|`durable`|Sürekli veya geçici sırasındaki ileti olup olmadığını belirten bir Boole değeri. Geçici bir ileti çalışmazken kalıcı bir ileti kuyruğu manager kilitlenme devam eder. Uygulamalar düşük gecikme süresi gerektirir ve ara sıra kayıp iletiler tolere edebilen geçici iletileri yararlıdır. Varsa `exactlyOnce` özniteliği `true`, iletileri dayanıklı olması gerekir. Varsayılan, `true` değeridir.|  
|`exactlyOnce`|Bu bağlama tarafından işlenen her ileti yalnızca bir kere teslim olup olmadığını gösteren bir Boole değeri. Gönderen sonra teslim hatalarının bildirilir. Zaman `durable` olduğu `false`, bu öznitelik yoksayılır ve iletileri teslim güvencesi aktarılır. Varsayılan, `true` değeridir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|`maxBufferPoolSize`|Bu bağlama için en fazla arabellek havuzunun boyutunu belirten bir tamsayı. Varsayılan değer 8'dir.|  
|`maxReceivedMessageSize`|Bu bağlama tarafından işlenen en büyük ileti boyutu, üst bilgiler, dahil, bayt cinsinden tanımlayan pozitif bir tamsayı. Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alırsınız. Alıcı, iletiyi bırakır ve izleme günlüğüne etkinliğin bir giriş oluşturur. 65536 varsayılandır. Bu ileti boyutuna bağlı hizmet reddi (DoS) saldırılarına maruz kalma riskinizi sınırlamak içindir.|  
|`maxRetryCycles`|Poison ileti algılama özelliği tarafından kullanılan yeniden deneme döngüsü sayısını belirten bir tamsayı. Tüm döngüleri, tüm teslim denemesi başarısız olduğunda bir ileti zehirli ileti haline gelir. Varsayılan değer 3'tür. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|`name`|Gerekli öznitelik. Bağlama yapılandırma adını içeren bir dize. Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip. Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|`QueueTransferProtocol`|Geçerli bir <xref:System.ServiceModel.QueueTransferProtocol> bu bağlamanın kullandığı sıraya konmuş iletişim kanal taşımasını belirten bir değer. MSMQ Active Directory SOAP Güvenilir Mesajlaşma Protokolü kullanılırken adresleme desteklemez. Bu nedenle, bu öznitelik ayarlanmamalıdır `Srmp` veya `Srmps` olduğunda `useActiveDirectory` özniteliği `true`.|  
|`receiveErrorHandling`|A <xref:System.ServiceModel.ReceiveErrorHandling> poison ve nondispatchable iletileri nasıl işlendiğini belirten bir değer.|  
|`receiveRetryCount`|En fazla kaç kez belirten bir tamsayı, yeniden deneme kuyruğa aktarmadan önce bir ileti göndermek sıra yöneticisini denemelidir.|  
|`receiveTimeout`|A <xref:System.TimeSpan> tamamlamak alma işlemi için sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:10:00 ' dir.|  
|`retryCycleDelay`|Anında teslim edilemeyen bir iletiyi teslim etmeye çalışırken deneme arasındaki gecikmeyi belirten bir TimeSpan değeri dolaşır. En düşük bekleyin yalnızca zaman gerçek bir bekleme süresi uzun olabilir çünkü değeri tanımlar. Varsayılan değer 00:10:00 ' dir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|`sendTimeout`|A <xref:System.TimeSpan> tamamlamak bir gönderme işlemi için sağlanan zaman aralığını belirten bir değer. Bu değer, büyük veya buna eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|`timeToLive`|Ne kadar ileti belirten bir TimeSpan değeri geçerli süreleri dolmadan ve teslim edilemeyen kuyruğa alınan önce. 1.00:00:00 varsayılandır.<br /><br /> Bu öznitelik, bunlar alıcı uygulamalar tarafından işlenmeden önce zamana duyarlı iletileri eski hale gelmediğinden emin olmak için ayarlanır. Belirtilen zaman aralığı içinde alıcı uygulama tarafından tüketilmeyen bir kuyruktaki bir iletiyi süresi dolmuş kabul edilir. Süresi dolan iletileri geçerliliğini yitirmiş kuyruk adı verilen özel kuyruğa gönderilir. Geçerliliğini yitirmiş kuyruk konumu ile ayarlanır `DeadLetterQueue` özniteliği veya uygun varsayılana dayalı Güvenceleri üzerinde.|  
|`usingActiveDirectory`|Kuyruk adreslerinin Active Directory kullanılarak dönüştürülüp dönüştürülmemesi olmadığını belirten bir Boole değeri.<br /><br /> MSMQ kuyruk adresleri yol adları veya doğrudan biçim adlarından oluşabilir. Doğrudan biçim adı ile DNS, NetBIOS veya IP kullanarak bilgisayar adını MSMQ çözümler. Bir yol adı ile MSMQ Active Directory kullanarak bilgisayar adını çözümler.<br /><br /> Varsayılan olarak, Windows Communication Foundation (WCF) aktarım dönüştürür doğrudan biçim adını bir ileti kuyruğuna URI'sini kuyruğa alındı. Ayarlayarak `UseActiveDirectory` özelliği true olarak bir uygulama belirtebilirsiniz sıraya alınan aktarım Active Directory yerine DNS, NetBIOS veya IP kullanarak bilgisayar adını çözümlenmelidir.|  
|`useMsmqTracing`|İletileri bu bağlama tarafından işlenen olup olmadığını belirten bir Boole değeri izlenip izlenmemesini gerektiğini. Varsayılan, `false` değeridir. İzleme etkin olduğunda, rapor iletileri oluşturulur ve rapor kuyruğa gönderilen ileti ayrıldığında ya da bir Message Queuing bilgisayar ulaştığında her zaman.|  
|`useSourceJournal`|Bu bağlama tarafından işlenen iletilerin kopyalarını belirten bir Boole değeri kaynak günlüğü depolanması gerekir. Varsayılan, `false` değeridir.<br /><br /> Bilgisayarın giden sırasının bıraktıysanız iletileri kaydını tutmak istediğiniz sıraya alınmış uygulamalar iletilerin günlük kuyruğuna kopyalayabilirsiniz. Giden sırasının bir iletiyi bırakır ve ileti hedef bilgisayarda alındı bir bildirim alındıktan sonra iletinin bir kopyasını gönderen bilgisayarın sistem günlüğü kuyrukta tutulur.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Bu bağlama ile yapılandırılan bir bitiş noktası tarafından işlenen SOAP iletilerinin karmaşıklığını kısıtlamalar tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Bağlama için güvenlik ayarlarını tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlamaları >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Bu öğe, standart ve özel bağlamalar koleksiyonunu tutar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `netMsmqBinding` Bağlama Microsoft Message Queuing (MSMQ) bir aktarım olarak yararlanarak queuing için destek sağlar ve gevşek bağlantılı uygulamalar, hata Yalıtımı seviyelendirme ve bağlantısı kesilmiş işlemleri yükler için destek sağlar. Bu özellikler için bkz [wcf'de kuyruklar](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
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
- [\<bağlama >](../../../../../docs/framework/misc/binding.md)
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [WCF'de Kuyruklar](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
