---
title: Zehirli İleti İşleme
ms.date: 03/30/2017
ms.assetid: 8d1c5e5a-7928-4a80-95ed-d8da211b8595
ms.openlocfilehash: b1f01714d2b4587659682661c05b341d0f50254e
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592857"
---
# <a name="poison-message-handling"></a>Zehirli İleti İşleme
A *zehirli ileti* uygulama teslim denemesi üst sınırını aşan bir ileti. Kuyruk tabanlı bir uygulama hataları nedeniyle bir ileti işleyemediğinde bu durum ortaya çıkabilir. Güvenilirlik taleplerini karşılamak üzere kuyruğa alınan bir uygulamayı bir işlem altında iletileri alır. İletinin yeni bir işlem altında yeniden kuyruğa alınan iletinin alındığı işlem iptal ediliyor iletinin kuyrukta bırakır, böylece. Durdurulacak işlemin neden olan sorun düzeltilmezse alıcı uygulama alma ve teslim denemesi sayısı aşıldı kadar aynı iletiyi iptal ediliyor. döngü ve zehirli ileti sonuçları tıkanıp.  
  
 Bir ileti zehirli ileti için birçok neden olabilir. Uygulamaya özgü en sık karşılaşılan nedenleridir. Örneğin, bir uygulama bir kuyruktan ileti okuyan ve bazı veritabanı işlemleri yapar, bu işlem iptal neden veritabanında kilit almak uygulama başarısız olabilir. Veritabanı işlemi iptal edildi nedeniyle uygulamanın iletiyi ikinci kez yeniden okuyun ve veritabanında kilit için başka bir girişimde sırasındaki ileti kalır. İletileri bunlar geçersiz bilgileri içerdiği durumlarda zararlı olabilir. Örneğin, bir sipariş geçersiz müşteri numarası içeriyor olabilir. Bu durumlarda, uygulama gönüllü olarak işlem iptal ve iletinin zehirli ileti olmaya zorlar.  
  
 Nadir durumlarda, uygulamaya dağıtılan iletileri başarısız olabilir. Windows Communication Foundation (WCF) katmanı, ileti ile ilgili bir sorun da bulabilirsiniz ileti yanlış çerçeve sahipse, geçersiz bir ileti kimlik bilgilerini bağlı veya bir geçersiz eylem üst bilgisi için. Bu durumlarda, uygulama hiçbir zaman iletiyi alır; Ancak, ileti zehirli ileti yine de olabilir ve el ile işlenir.  
  
## <a name="handling-poison-messages"></a>Zehirli ileti işleme  
 WCF'de, zehirli ileti işleme uğraşmanız uygulamaya gönderilen iletileri veya bu uygulamaya gönderilir ancak uygulamaya özgü nedeniyle işlem başarısız iletileri alan bir uygulama için bir mekanizma sağlar. nedenleri. Zehirli ileti işleme, aşağıdaki özellikler kullanılabilir sıraya alınan bağlamalarının her tarafından yapılandırılır:  
  
- `ReceiveRetryCount`. En fazla ileti uygulama teslimini uygulama kuyruğu'ndan yeniden deneme sayısını belirten bir tamsayı değeri. Varsayılan değer 5'tir. Bu, burada hemen yeniden sorun gibi bir veritabanı geçici karşılıklı bir kilitlenme ile düzeltmeleri durumlarda yeterlidir.  
  
- `MaxRetryCycles`. En fazla yeniden deneme döngüsü sayısını belirten bir tamsayı değeri. Bir ileti uygulama kuyruktan yeniden deneme iletiler alt kuyruğuna ve yeniden deneme subqueue geri uygulama kuyruğuna teslim deneyin'den yapılandırılabilir bir gecikmeden sonra aktarma bir yeniden deneme döngüsü oluşur. Varsayılan değer 2'dir. Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)], ileti denenir en fazla (`ReceiveRetryCount` + 1) * (`MaxRetryCycles` + 1) süreleri. `MaxRetryCycles` üzerinde göz ardı edilir [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
- `RetryCycleDelay`. Yeniden deneme döngüleri arasındaki gecikme süresi. Varsayılan değer 30 dakikadır. `MaxRetryCycles` ve `RetryCycleDelay` birlikte düzenli bir gecikmeden sonra bir yeniden deneme sorununu giderir burada sorunu gidermek için bir mekanizma sağlar. Örneğin, işlem yürütme bekleniyor SQL Server'da ayarlanan kilitli bir satır işler.  
  
- `ReceiveErrorHandling`. Yeniden deneme sayısı çalıştı sonra teslim başarısız bir ileti için gerçekleştirilecek eylemi belirten bir sabit listesi. Değerleri, hata, Drop Reddet olabilir ve taşıyın. Hata varsayılan seçenektir.  
  
- Hata. Bu seçenek bir hataya neden olan bir dinleyici için gönderir `ServiceHost` hata için. Uygulama kuyruktan iletileri işleme devam etmeden önce uygulama kuyruktan ileti bazı dış mekanizması tarafından kaldırılmalıdır.  
  
- Aşağı açılır. Bu seçenek zehirli iletiyi bırakır ve ileti hiçbir zaman uygulamaya gönderilir. İse ileti `TimeToLive` özelliği bu noktada doldu ve ardından iletiyi gönderenin eski ileti sırası içinde görünebilir. Aksi durumda, ileti herhangi bir yerde görüntülenmez. Bu seçenek, kullanıcı iletisi kaybolması durumunda yapmanız gerekenler tanımlanmamış olduğunu belirtir.  
  
- Reddet. Bu seçenek yalnızca kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)]. Bu, Message Queuing (uygulama ileti alamıyor gönderen Kuyruk yöneticisi olumsuz bildirim göndermek için MSMQ) bildirir. İleti gönderme sırası yöneticisinin edilemeyen sıraya konur.  
  
- Taşıyın. Bu seçenek yalnızca kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)]. Bu, zehirli ileti poison ileti işleme uygulama tarafından daha sonra işlenmek poison ileti kuyruğuna taşır. Bir alt kuyruk uygulama kuyruğun ileti poison kuyruğudur. Poison ileti işleme uygulama zehirli kuyruktan iletileri okuyan bir WCF Hizmeti olabilir. Zehirli kuyruk bir alt kuyruk uygulama kuyruğun olduğu ve net.msmq:// çözülebilir\<*makine adı*>/*applicationQueue*; zehirli, burada  *makine adı* sıranın bulunduğu bilgisayarın adıdır ve *applicationQueue* uygulamaya özgü Kuyruğun adı.  
  
 Bir ileti için yapılan teslim denemesi sayısı şunlardır:  
  
- ((ReceiveRetryCount+1) * (MaxRetryCycles + 1)) üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
- (ReceiveRetryCount + 1) üzerinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
> [!NOTE]
>  Yeniden deneme yok, başarılı bir şekilde teslim edilen bir ileti için yapılır.  
  
 Bir ileti okuma denemesi sayısını izlemek için [!INCLUDE[wv](../../../../includes/wv-md.md)] iletisini iptal eder ve sayısını sayar bir taşıma sayısı özelliği sayar bir dayanıklı ileti özelliği uygulama sıranın arasında taşır tutar ve sıralar. WCF kanalı bu alma yeniden deneme sayısı ve yeniden deneme döngüsü sayısını hesaplamak için kullanır. Üzerinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)], durdurma sayısı WCF kanalı tarafından bellekte tutulur ve uygulama başarısız olursa sıfırlanır. Ayrıca, WCF kanalı bellek en fazla 256 iletiler için herhangi bir zamanda iptal sayıları tutabilir. 257th iletisini okuyun, sonra en eski ileti durdurma sayısı sıfırlanır.  
  
 Durdurma sayısı ve taşımak için işlem bağlamı aracılığıyla hizmet işlemi sayısı özellikleri kullanılabilir. Aşağıdaki kod örneği, bunlara nasıl gösterir.  
  
 [!code-csharp[S_UE_MSMQ_Poison#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/service.cs#1)]  
  
 WCF iki standart sıraya alınan bağlamalarını sunar:  
  
- <xref:System.ServiceModel.NetMsmqBinding>. Kuyruk tabanlı iletişim diğer WCF uç noktaları ile gerçekleştirmek için uygun bir .NET Framework bağlama.  
  
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Message Queuing var olan uygulamalarla iletişim kurmak için uygun olan bir bağlama.  
  
> [!NOTE]
>  WCF hizmeti gereksinimlerine göre bu bağlamaları özelliklerini değiştirebilirsiniz. Tüm zehirli ileti işleme mekanizması, alıcı uygulamaya yereldir. Alıcı uygulama nihai olarak durdurur ve gönderene negatif bir bildirim gönderir sürece gönderen uygulamaya görünmeyen bir işlemdir. Bu durumda, iletiyi gönderenin eski ileti sırası için taşınır.  
  
## <a name="best-practice-handling-msmqpoisonmessageexception"></a>En iyi yöntem: MsmqPoisonMessageException işleme  
 Hizmetin bir ileti zehirli olduğunu belirlediğinde, sıraya alınan aktarım oluşturur bir <xref:System.ServiceModel.MsmqPoisonMessageException> içeren `LookupId` zehirli ileti.  
  
 Alıcı uygulamanın uygulayabilirsiniz <xref:System.ServiceModel.Dispatcher.IErrorHandler> uygulamanın gerek duyduğu hataları işlemek için arabirim. Daha fazla bilgi için [genişletme denetiminin üzerine hata işleme ve Raporlama](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md).  
  
 Uygulama bazı tür zehirli iletileri zehirli ileti kuyruğuna taşır ve böylece kuyruğundaki iletileri geri kalanını hizmete erişebilir otomatik zehirli ileti işleme gerektirebilir. Hata işleyicisi mekanizması poison ileti özel durumlar için dinleyecek şekilde kullanmak için tek senaryo olduğunda <xref:System.ServiceModel.Configuration.MsmqBindingElementBase.ReceiveErrorHandling%2A> ayarı <xref:System.ServiceModel.ReceiveErrorHandling.Fault>. Message Queuing 3.0 poison ileti örnek, bu davranış gösterir. En iyi uygulamalar da dahil olmak üzere, zehirli iletileri işlemek için gereken adımlar özetlenmektedir:  
  
1. Zehirli ayarlarınızı uygulamanızın gereksinimlerini yansıtacak emin olun. Ayarlarla çalışırken, üzerinde bir Message Queuing yeteneklerini arasındaki farklar anladığınızdan emin olun [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
2. Gerekirse, uygulama `IErrorHandler` poison ileti hataları işlemek için. Ayar olmadığından `ReceiveErrorHandling` için `Fault` sıradaki zehirli ileti taşıma veya bir dış bağımlı sorunu el ile bir mekanizma gerekir tipik kullanım uygulamaktır `IErrorHandler` olduğunda `ReceiveErrorHandling` ayarlanır `Fault`, olarak Aşağıdaki kodda gösterilen.  
  
     [!code-csharp[S_UE_MSMQ_Poison#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonerrorhandler.cs#2)]  
  
3. Oluşturma bir `PoisonBehaviorAttribute` , hizmet davranışı kullanabilirsiniz. Davranış yükler `IErrorHandler` dağıtıcı üzerinde. Aşağıdaki kod örneği bakın.  
  
     [!code-csharp[S_UE_MSMQ_Poison#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonbehaviorattribute.cs#3)]  
  
4. Hizmetinizi zehirli davranışı özniteliği ile açıklanıyor emin olun.  

 Ayrıca, varsa `ReceiveErrorHandling` ayarlanır `Fault`, `ServiceHost` zehirli ileti ile karşılaşıldığında hataları. Hatalı olaya bağlama ve hizmeti Kapat düzeltme girişimlerinde bulunun ve yeniden başlatın. Örneğin, `LookupId` içinde <xref:System.ServiceModel.MsmqPoisonMessageException> yayılır `IErrorHandler` dikkat edilmesi ve hizmet ana bilgisayar hataları kullandığınızda `System.Messaging` kullanarak kuyruk iletisi için API `LookupId` iletiden kaldırmak için Kuyruk ve bazı dış deposunda veya başka bir kuyruğa ileti deposu. Daha sonra yeniden başlatabilirsiniz `ServiceHost` normal işleme devam etmek için. [Zehirli ileti işleme MSMQ 4.0](../../../../docs/framework/wcf/samples/poison-message-handling-in-msmq-4-0.md) Bu davranış gösterir.  
  
## <a name="transaction-time-out-and-poison-messages"></a>İşlem zaman aşımı ve zehirli iletiler  
 Hataların bir sınıf, kuyruğa alınmış taşıma kanalının ve kullanıcı kodu arasında ortaya çıkabilir. Bu hata, ileti güvenlik katmanı veya mantıksal gönderme hizmeti gibi raflarının katmanları tarafından algılanabilir. Örneğin, SOAP güvenlik katmanı eksik bir X.509 sertifikası algılandı ve eksik eylem çalışmaları nereye ileti uygulamaya gönderilen. Bu durumda, hizmet modeli iletiyi bırakır. İletinin işlemde okunur ve işlem zaman aşımına uğrar koşuluyla bu işlem için bir sonuç olamaz çünkü iptal eder ve iletiyi yerleştirildiğini geri kuyruğuna. Diğer bir deyişle, belirli bir bir sınıf hataları için işlem değil hemen iptal ancak bu işlem zaman aşımına uğrayana kadar bekler. Kullanarak bir hizmet için işlem zaman aşımını değiştirebilirsiniz <xref:System.ServiceModel.ServiceBehaviorAttribute>.  
  
 Bilgisayar genelinde bir temele işlem zaman aşımı süresini değiştirmek için machine.config dosyasının değiştirmek ve uygun işlem zaman aşımını ayarlayın. İçinde işlem kümesi zaman aşımı bağlı olarak unutmayın, işlem sonunda durdurur ve kuyruğa döner ve kendi iptal sayısının artırılması önemlidir. Sonuç olarak, zehirli ileti olur ve doğru bir değerlendirme kullanıcı ayarlarına göre yapılır.  
  
## <a name="sessions-and-poison-messages"></a>Oturumlarının ve zehirli iletiler  
 Bir oturum tek bir ileti poison ileti işleme yordamları ve aynı yeniden deneme uygulanır. Zehirli iletiler için daha önce listelenen özellikler, tüm oturum için geçerlidir. Bu, tüm oturumda denenir ve son poison ileti kuyruğu veya gönderenin eski ileti sırası iletiyi reddedilmesi durumunda giden anlamına gelir.  
  
## <a name="batching-and-poison-messages"></a>Toplu işlem ve zehirli iletiler  
 Bir ileti zehirli ileti olur ve bir batch bir parçasıdır, toplu işin tamamını geri alınır ve kanala bir ileti aynı anda okuma döndürür. Toplu işleme hakkında daha fazla bilgi için bkz. [bir işlemde toplu işlem iletileri](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
  
## <a name="poison-message-handling-for-messages-in-a-poison-queue"></a>Poison ileti zehirli kuyruktaki iletileri işleme  
 Poison ileti kuyrukta bir ileti yerleştirildiğinde poison ileti işleme sonlanmıyor. Poison mesaj kuyruğu iletilerinde hala okuyun ve işlenir. Son zehirli subqueue iletileri okunurken poison ileti işleme ayarların bir alt kümesini kullanabilirsiniz. Geçerli ayarları `ReceiveRetryCount` ve `ReceiveErrorHandling`. Ayarlayabileceğiniz `ReceiveErrorHandling` , Red, bırakma veya hata. `MaxRetryCycles` göz ardı edilir ve değilse bir özel durum `ReceiveErrorHandling` taşımak için ayarlanır.  
  
## <a name="windows-vista-windows-server-2003-and-windows-xp-differences"></a>Windows Vista, Windows Server 2003 ve Windows XP farkları  
 Daha önce belirtildiği gibi tüm poison ileti işleme ayarlarının uygulanacağı [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. Aşağıdaki anahtar Message Queuing arasındaki farklar hakkında [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], [!INCLUDE[wxp](../../../../includes/wxp-md.md)], ve [!INCLUDE[wv](../../../../includes/wv-md.md)] poison ileti işleme için uygundur:  
  
- Message Queuing [!INCLUDE[wv](../../../../includes/wv-md.md)] sıralar, destekler ancak [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)] sıralar desteklemez. Poison ileti işlemede kullanılan sıralar. Yeniden deneme kuyrukları ve zehirli kuyruk zarar ileti işleme ayarlara göre oluşturulan uygulama kuyruğa sıralar var. `MaxRetryCycles` Kaç yeniden oluşturmak için sıralar belirler. Bu nedenle, çalışırken [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)], `MaxRetryCycles` göz ardı edilir ve `ReceiveErrorHandling.Move` izin verilmiyor.  
  
- Message Queuing [!INCLUDE[wv](../../../../includes/wv-md.md)] destekler bildirimi, negatif sırada [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)] değildir. Alıcı sırası Yöneticisi'nden negatif bildirim edilemeyen kuyrukta reddedilen ileti yerleştirmek gönderme sıra yöneticisini neden olur. Bu nedenle, `ReceiveErrorHandling.Reject` ile izin verilmiyor [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
- Message Queuing [!INCLUDE[wv](../../../../includes/wv-md.md)] ileti teslimi sürelerini sayısını tutan bir ileti özelliği denenir destekler. Bu durdurma sayısı özelliği kullanılabilir değil [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. Aynı gruptaki birden fazla WCF hizmeti tarafından okunduğunda bu özelliği doğru bir değer içeremez mümkündür WCF durdurma sayısı, bellekte saklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kuyruklara Genel Bakış](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Windows Vista, Windows Server 2003 ve Windows XP'de Kuyruğa Alma Özelliği Arasındaki Farklar](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)
- [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
