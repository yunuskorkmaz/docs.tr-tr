---
title: '&lt;netMsmqBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a68b44d7-7799-43a3-9e63-f07c782810a6
caps.latest.revision: "35"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 32aa057f36786412a5569e7c9190ae6ed9c0aa99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltnetmsmqbindinggt"></a>&lt;netMsmqBinding&gt;
Makineler arası iletişim için uygun bir sıralı bağlama tanımlar.  
  
 \<Sistem. ServiceModel >  
\<bağlamaları >  
\<netMsmqBinding >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<netMsmqBinding>  
    <binding   
       closeTimeout="TimeSpan"   
       customDeadLetterQueue="Uri"  
       deadLetterQueue="Uri"  
       durable="Boolean"  
       exactlyOnce="Boolean"   
       maxBufferPoolSize="Integer"  
       maxReceivedMessageSize"Integer"  
       maxRetryCycles="Integer"   
       name="string"   
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
       useMsmqTracing="Boolean  
       useSourceJournal="Boolean"  
          <security>  
                  <message    
                        algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="None/Windows/UserName/Certificate/InfoCard "/>  
                  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
            msmqEncryptionAlgorithm="RC4Stream/AES"  
            msmqProtectionLevel="None/Sign/EncryptAndSign"  
            msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
          </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />   </binding></netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`closeTimeout`|A <xref:System.TimeSpan> bir kapatma işlemi tamamlamak sağlanan zaman aralığı belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|`customDeadLetterQueue`|Süresi dolan veya aktarımı veya teslim başarısız olmuş iletileri yerleştirildiği uygulama başına sahipsiz sıra konumunu içeren bir URI.<br /><br /> Sahipsiz Sıra Yöneticisi için teslim başarısız süresi dolan iletileri gönderen uygulaması bulunan bir sıra sırasıdır.<br /><br /> Belirtilen URI <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> net.msmq şeması kullanması gerekir.|  
|`deadLetterQueue`|A <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> varsa kullanmak için eski ileti sırası türünü belirten değer.<br /><br /> Sahipsiz Sıra uygulamaya teslim başarısız iletileri burada aktarılacak yerdir.<br /><br /> Gerektiren iletileri için `exactlyOnce` güvence (diğer bir deyişle, `exactlyOnce` özniteliği `true`), bu öznitelik Varsayılanları MSMQ sistem genelinde işlem sahipsiz sıraya.<br /><br /> Bu öznitelik varsayılan olarak hiçbir garanti vermediğini gerektiren iletileri `null`.|  
|`durable`|İleti dayanıklı veya sıradaki volatile olup olmadığını belirten bir Boole değeri. Geçici bir ileti çalışmazken dayanıklı bir ileti sırası Yöneticisi kilitlenme devam eder. Uygulamalar düşük gecikme süresi gerektirir ve nadiren kayıp iletilerle dayanabilir volatile iletileri yararlı olur. Varsa `exactlyOnce` özniteliği `true`, iletileri dayanıklı olması gerekir. Varsayılan, `true` değeridir.|  
|`exactlyOnce`|Bu bağlama tarafından işlenen her ileti yalnızca bir kere teslim olup olmadığını gösteren bir Boole değeri. Gönderenin ardından teslim hatalarının bildirilir. Zaman `durable` olan `false`, bu öznitelik dikkate alınmaz ve iletileri teslim güvence aktarılır. Varsayılan, `true` değeridir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A>.|  
|`maxBufferPoolSize`|Bu bağlama için en büyük arabellek havuzu boyutu belirten bir tamsayı. Varsayılan 8'dir.|  
|`maxReceivedMessageSize`|Bu bağlama tarafından işlenen başlıkları dahil bayt cinsinden maksimum ileti boyutu tanımlayan bir pozitif tamsayı. Bu sınırı aşan bir ileti gönderen bir SOAP hatasını alır. Alıcı iletiyi bırakır ve izleme günlüğüne olay bir giriş oluşturur. 65536 varsayılandır. Bu ileti boyutuna bağlı hizmet reddi (DoS) saldırılarına maruz sınırlamak için tasarlanmıştır.|  
|`maxRetryCycles`|Poison ileti algılama özelliği tarafından kullanılan yeniden deneme döngüsü sayısını belirten bir tamsayı. Tüm döngü tüm Teslim girişimleri başarısız olduğunda bir ileti zararlı bir ileti haline gelir. Varsayılan değer 3'tür. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>.|  
|`name`|Gerekli öznitelik. Bağlama yapılandırma adını içeren dize. Bağlama için bir tanımlayıcı olarak kullanıldığından, bu değer benzersiz olmalıdır. İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir. Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|A <xref:System.TimeSpan> tamamlamak açık işlem için sağlanan zaman aralığını belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|`QueueTransferProtocol`|Geçerli bir <xref:System.ServiceModel.QueueTransferProtocol> bu bağlamayı kullanan kuyruğa alınan iletişim kanalı aktarım belirten değer. MSMQ Active Directory SOAP Güvenilir Mesajlaşma Protokolü kullanılırken adresleme desteklemez. Bu nedenle, bu öznitelik ayarlamalıdır değil `Srmp` veya `Srmps` zaman `u``seActiveDirectory` özniteliği `true`.|  
|`receiveErrorHandling`|A <xref:System.ServiceModel.ReceiveErrorHandling> poison ve nondispatchable iletileri nasıl işleneceğini belirten değer.|  
|`receiveRetryCount`|En fazla kaç kez belirten bir tamsayı, yeniden deneme kuyruğuna aktarmadan önce bir ileti göndermek sıra yöneticisini denemelidir.|  
|`receiveTimeout`|A <xref:System.TimeSpan> bir alma işleminin tamamlanması için sağlanan zaman aralığı belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:10: 00'dır.|  
|`retryCycleDelay`|Yeniden deneme arasındaki gecikme süresini belirten bir TimeSpan değeri hemen teslim edilemeyen bir ileti teslim çalışılırken geçiş yapar. En düşük bekleyin yalnızca zaman gerçek bekleme süresi uzun olabileceğinden değeri tanımlar. Varsayılan değer 00:10: 00'dır. Daha fazla bilgi için bkz. <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A>.|  
|`sendTimeout`|A <xref:System.TimeSpan> bir gönderme işleminin tamamlanması için sağlanan zaman aralığı belirten değer. Bu değer sıfırdan büyük veya eşit olmalıdır <xref:System.TimeSpan.Zero>. Varsayılan değer 00:01:00 ' dir.|  
|`timeToLive`|Ne kadar süreyle iletileri belirten bir TimeSpan değeri geçerli süresi ve teslim edilemeyen kuyruğuna önce. 1.00:00:00 varsayılandır.<br /><br /> Bu öznitelik, alıcı uygulamalar tarafından işlenmeden önce zamana duyarlı iletileri eski hale gelmediğinden emin olmak için ayarlanır. Belirtilen zaman aralığı içinde alıcı uygulama tarafından tüketilmeyen bir kuyruktaki ileti süresinin kabul edilir. Süresi dolan iletileri sahipsiz sıra adı verilen özel kuyruğuna gönderilir. Sahipsiz Sıra konumu ile ayarlanır `DeadLetterQueue` uygun varsayılana göre sağlandığına üzerinde veya öznitelik.|  
|`usingActiveDirectory`|Active Directory kullanarak sıra adreslerini dönüştürülmesi gerekiyorsa belirten bir Boole değeri.<br /><br /> MSMQ sıra adreslerini yol adları veya doğrudan biçim adları oluşabilir. Bir doğrudan biçim adıyla MSMQ DNS, NetBIOS veya IP kullanarak bilgisayar adını çözümler. Bir yol adı ile MSMQ Active Directory kullanarak bilgisayar adını çözümler.<br /><br /> Varsayılan olarak, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] sıraya alınan aktarım, doğrudan biçim adına bir ileti sırası URI'sini dönüştürür. Ayarlayarak `UseActiveDirectory` özelliğinin true, bir uygulama belirtebilirsiniz sıraya alınan aktarım Active Directory yerine DNS, NetBIOS veya IP kullanarak bilgisayar adını çözümlenmelidir.|  
|`useMsmqTracing`|Bu bağlama tarafından işlenen iletileri olup olmadığını belirten bir Boole değeri izlenen. Varsayılan, `false` değeridir. İzleme etkinleştirildiğinde Raporu iletilerini oluşturulur ve ileti ayrıldığında ya da bir Message Queuing bilgisayar ulaştığında her zaman rapor sırasına gönderilir.|  
|`useSourceJournal`|Bu bağlama tarafından işlenen iletilerin kopyalarını belirten bir Boole değeri kaynak günlüğünde depolanması gerekir. Varsayılan, `false` değeridir.<br /><br /> Bilgisayarın giden sırasının bıraktıysanız iletileri kaydını tutmak istediğiniz sıraya alınan uygulamaları iletileri günlük kuyruğuna kopyalayabilirsiniz. Giden sırasının bir ileti bırakır ve ileti hedef bilgisayarda alındı bir bildirim alındıktan sonra iletinin bir kopyasını gönderen bilgisayarın sistem günlük sırasındaki tutulur.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Bu bağlama ile yapılandırılan uç noktaları tarafından işlenen SOAP iletilerine karmaşıklığını kısıtlamalar tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|Bağlama için güvenlik ayarlarını tanımlar. Bu öğe türünde <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlamaları >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Bu öğe, standart ve özel bağlamaları koleksiyonunu içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `netMsmqBinding` Bağlama Microsoft Message Queuing (MSMQ) bir taşıma olarak yararlanarak queuing için destek sağlar ve geniş bağlı uygulamalar, hata yalıtım seviyelendirme ve bağlantısı kesilmiş işlemlerini yük için destek sağlar. Bu özelliklerin tartışma için bkz [wcf'de kuyruklar](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).  
  
## <a name="example"></a>Örnek  
  
```xml  
<configuration>  
<system.ServiceModel>  
    <bindings>  
           <netMsmqBinding>  
                <binding   
                         closeTimeout="00:00:10"   
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
            </netMsmqBinding>  
    </bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.Configuration.NetMsmqBindingElement>  
 [\<bağlama >](../../../../../docs/framework/misc/binding.md)  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Sistem tarafından sağlanan bağlamaları yapılandırma](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [Wcf'de kuyruklar](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
