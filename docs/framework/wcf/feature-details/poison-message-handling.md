---
title: Zehirli İleti İşleme
ms.date: 03/30/2017
ms.assetid: 8d1c5e5a-7928-4a80-95ed-d8da211b8595
ms.openlocfilehash: d219c18bb072684deb6cc1d8a2d17b1989762151
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590572"
---
# <a name="poison-message-handling"></a>Zehirli İleti İşleme
*Zararlı ileti* , uygulamaya yönelik en fazla teslim deneme sayısını aşmış bir iletidir. Bu durum, kuyruk tabanlı bir uygulama hatalar nedeniyle bir iletiyi işleyemediği zaman ortaya çıkabilir. Bir sıraya alınmış uygulama, güvenilirlik taleplerini karşılamak için bir işlem altında iletileri alır. Sıraya alınan bir iletinin alındığı işlemi iptal etmek, iletinin yeni bir işlem altında yeniden deneneceği şekilde kuyruktaki iletiyi bırakır. İşlemin iptaline neden olan sorun düzeltilmezse, alıcı uygulama, en fazla sayıda teslim denemesi aşılıncaya ve bir zarar iletisi sonuçlarıyla aynı iletiyi alıp iptal etmeden bir döngüde kalabilir.  
  
 Birçok nedenden dolayı bir ileti bir zarar iletisi olabilir. En yaygın nedenler uygulamaya özgüdür. Örneğin, bir uygulama kuyruktan bir ileti okur ve bazı veritabanı işlemlerini gerçekleştirdiğinde, uygulama veritabanında bir kilit alamaz ve işlemin iptal edilmesini sağlar. Veritabanı işlemi durdurulduğundan, ileti kuyrukta kalır, bu da uygulamanın iletiyi ikinci kez yeniden kullanmasına ve veritabanında kilit edinmeye yönelik başka bir girişim yapmasına neden olur. Ayrıca, geçersiz bilgiler içeriyorsa iletiler zarar verebilir. Örneğin, bir satınalma siparişi geçersiz bir müşteri numarası içerebilir. Bu durumlarda, uygulama gönüllü olarak işlemi iptal edebilir ve iletiyi bir zarar iletisi haline zorlayabilir.  
  
 Nadir durumlarda, iletiler uygulamaya dağıtılması başarısız olabilir. Windows Communication Foundation (WCF) katmanı, iletide yanlış çerçeve varsa, kendisine bağlı geçersiz ileti kimlik bilgileri veya geçersiz bir eylem üstbilgisi gibi iletiyle ilgili bir sorun bulabilir. Bu durumlarda, uygulama hiçbir zaman iletiyi almaz; Ancak, ileti hala zarar görmüş bir ileti haline gelebilir ve el ile işlenebilir.  
  
## <a name="handling-poison-messages"></a>Zarar Iletilerini işleme  
 WCF 'de, zehirli ileti işleme, uygulamaya dağıtılan ve uygulamaya özel nedenlerden dolayı işlenemeyecek olan, uygulamaya veya iletilere iletilemez olan iletilerle ilgilenmek için alıcı bir uygulama mekanizması sağlar. Her kullanılabilir sıraya alınmış bağlamaların her birinde aşağıdaki özelliklerle, zehirli ileti işlemeyi yapılandırın:  
  
- `ReceiveRetryCount`. Uygulama kuyruğundan uygulamaya bir ileti teslimini yeniden deneme sayısının üst sınırını belirten bir tamsayı değeri. Varsayılan değer 5 ' tir. Bu, bir veritabanında geçici bir kilitlenme gibi bir anında yeniden denemenin sorunu düzelttiği durumlarda yeterlidir.  
  
- `MaxRetryCycles`. En fazla yeniden deneme döngüsü sayısını belirten bir tamsayı değeri. Yeniden deneme çevrimi, bir iletiyi uygulama kuyruğundan yeniden deneme alt sırasına ve yapılandırılabilir bir gecikmeden sonra yeniden deneme alt sırasından yeniden uygulama kuyruğuna aktarma işleminden oluşur. Varsayılan değer 2 ' dir. Windows Vista 'da ileti en fazla ( `ReceiveRetryCount` + 1) * ( `MaxRetryCycles` + 1) kez denenir. `MaxRetryCycles`Windows Server 2003 ve Windows XP 'de yok sayılır.  
  
- `RetryCycleDelay`. Yeniden deneme döngüleri arasındaki gecikme süresi. Varsayılan değer 30 dakikadır. `MaxRetryCycles`ve `RetryCycleDelay` birlikte, düzenli bir gecikmeden sonra yeniden denenmede sorunu çözdükleri sorunu gidermeye yönelik bir mekanizma sağlar. Örneğin, bu, bekleyen işlem işleme SQL Server bir kilitli satırı işler.  
  
- `ReceiveErrorHandling`. En fazla yeniden deneme sayısı denendikten sonra teslim başarısız olan bir ileti için gerçekleştirilecek eylemi belirten bir sabit listesi. Değerler hata, bırakma, reddetme ve taşıma olabilir. Varsayılan seçenek hatadır.  
  
- Dayanıklı. Bu seçenek, hata hatasına neden olan dinleyiciye bir hata gönderir `ServiceHost` . Uygulamanın sıradan iletileri işlemeye devam edebilmesi için, iletinin bazı dış mekanizmadan uygulama kuyruğundan kaldırılması gerekir.  
  
- Açılan. Bu seçenek, zarar iletisini bırakır ve ileti hiçbir şekilde uygulamaya teslim değildir. `TimeToLive`Bu noktada iletinin özelliğinin süresi dolmuşsa ileti gönderenin teslim edilemeyen ileti kuyruğunda görünebilir. Aksi takdirde, ileti herhangi bir yerde görünmez. Bu seçenek, iletinin kaybolması durumunda kullanıcının ne yapılacağını belirtmediğini belirtir.  
  
- Mesi. Bu seçenek yalnızca Windows Vista 'da kullanılabilir. Bu, Message Queuing (MSMQ) ' nin, uygulamanın iletiyi alamaması için gönderme kuyruğu yöneticisine olumsuz bir bildirim göndermesini sağlar. İleti, gönderme kuyruğu yöneticisinin atılacak ileti kuyruğuna yerleştirilir.  
  
- Geçiş. Bu seçenek yalnızca Windows Vista 'da kullanılabilir. Bu, zarar iletisini daha sonra bir zarar iletisi işleme uygulaması tarafından işlenmek üzere bir zarar iletisi kuyruğuna taşIar. Poison-Message kuyruğu, uygulama sırasının bir alt sıranız. Zararlı ileti işleme uygulaması, zarar sırasındaki iletileri okuyan bir WCF hizmeti olabilir. Zarar sırası, uygulama sırasının bir alt sıranız ve net. MSMQ:// \<*machine-name*> / *applicationQueue*;p oison olarak çözülebilir. burada *makine adı* sıranın bulunduğu bilgisayarın adı ve *applicationQueue* uygulamaya özgü kuyruğun adıdır.  
  
Aşağıda, bir ileti için yapılan en fazla teslim denemesi sayısı verilmiştir:  
  
- ((ReceiveRetryCount + 1) * (Maxretrydöngülerini + 1)) Windows Vista 'da.  
  
- (ReceiveRetryCount + 1) Windows Server 2003 ve Windows XP 'de.  
  
> [!NOTE]
> Başarıyla teslim edilen bir ileti için yeniden deneme yapılmadı.  
  
 İleti okuma girişimi sayısını izlemek için, Windows Vista, uygulamanın sırası ve alt sıraları arasında iletinin kaç kez hareket edeceğini sayan bir taşıma sayısı özelliğinin sayısını sayan sürekli bir ileti özelliği tutar. WCF kanalı, alma yeniden deneme sayısı ve yeniden deneme döngüsü sayısını hesaplamak için bunları kullanır. Windows Server 2003 ve Windows XP 'de, durdurma sayısı WCF kanalı tarafından bellekte tutulur ve uygulama başarısız olursa sıfırlanır. Ayrıca, WCF kanalı, her zaman bellekte en fazla 256 ileti için iptal sayısını tutabilir. Bir 257th iletisi okunsa, en eski iletinin durdurma sayısı sıfırlanır.  
  
 Durdurma sayısı ve taşıma sayısı özellikleri, işlem bağlamı aracılığıyla hizmet işlemi için kullanılabilir. Aşağıdaki kod örneğinde nasıl erişebileceğiniz gösterilmektedir.  
  
 [!code-csharp[S_UE_MSMQ_Poison#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/service.cs#1)]  
  
 WCF, iki standart sıraya alınmış bağlama sağlar:  
  
- <xref:System.ServiceModel.NetMsmqBinding>. Diğer WCF uç noktaları ile sıra tabanlı iletişim gerçekleştirmek için uygun bir .NET Framework bağlama.  
  
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Mevcut Message Queuing uygulamalarla iletişim kurmak için uygun bir bağlama.  
  
> [!NOTE]
> WCF hizmetinizin gereksinimlerine bağlı olarak bu bağlamalardaki özellikleri değiştirebilirsiniz. Tüm zarar iletisi işleme mekanizması, alıcı uygulamada yereldir. Alma uygulaması son olarak durdurulmadığı ve gönderene olumsuz bir bildirim gönderen sürece işlem gönderme uygulaması tarafından görünmez. Bu durumda, ileti gönderenin teslim edilemeyen ileti kuyruğuna taşınır.  
  
## <a name="best-practice-handling-msmqpoisonmessageexception"></a>En iyi yöntem: Msmqkirmessageexception Işleme  
 Hizmet bir iletinin Poison olduğunu belirlediğinde, sıradaki aktarım, <xref:System.ServiceModel.MsmqPoisonMessageException> zarar iletisini içeren bir oluşturur `LookupId` .  
  
 Alıcı bir uygulama <xref:System.ServiceModel.Dispatcher.IErrorHandler> , uygulamanın gerektirdiği hataları işlemek için arabirimi uygulayabilir. Daha fazla bilgi için bkz. [hata işleme ve raporlama üzerinde denetimi genişletme](../samples/extending-control-over-error-handling-and-reporting.md).  
  
 Uygulama, bir hizmetin sıradaki iletilerin geri kalanına erişebilmeleri için, zarar iletilerini bir zarar iletisi kuyruğuna taşırken, zarar iletilerinin bir dizi otomatik işlemesini gerektirebilir. Zarar iletisi özel durumlarını dinlemek için hata işleyici mekanizmasını kullanmanın tek senaryosu <xref:System.ServiceModel.Configuration.MsmqBindingElementBase.ReceiveErrorHandling%2A> ayarın olarak ayarlanmıştır <xref:System.ServiceModel.ReceiveErrorHandling.Fault> . Message Queuing 3,0 için zehirli ileti örneği bu davranışı gösterir. Aşağıda, en iyi yöntemler de dahil olmak üzere, zarar iletilerini işlemek için gereken adımlar özetlenmektedir:  
  
1. Zarar ayarlarınızın uygulamanızın gereksinimlerini yansıttığından emin olun. Ayarlarla çalışırken, Windows Vista, Windows Server 2003 ve Windows XP 'de Message Queuing özellikleri arasındaki farklılıkları anladığınızdan emin olun.  
  
2. Gerekirse, `IErrorHandler` zarar iletisi hatalarını işlemek için öğesini uygulayın. İçin ayarı `ReceiveErrorHandling` , `Fault` zarar iletisini kuyruktan taşımak veya bir dış bağımlı sorunu düzeltmek için el ile bir mekanizma gerektirdiğinden, `IErrorHandler` `ReceiveErrorHandling` `Fault` aşağıdaki kodda gösterildiği gibi tipik kullanım olarak ayarlandığında uygulanır.  
  
     [!code-csharp[S_UE_MSMQ_Poison#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonerrorhandler.cs#2)]  
  
3. `PoisonBehaviorAttribute`Hizmet davranışının kullanabileceği bir oluştur. Davranışı `IErrorHandler` dağıtıcıya yüklenir. Aşağıdaki kod örneğine bakın.  
  
     [!code-csharp[S_UE_MSMQ_Poison#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonbehaviorattribute.cs#3)]  
  
4. Hizmetinizin Poison Behavior özniteliğiyle açıklaneklendiğinden emin olun.  

 Buna ek olarak,,,,,,,, `ReceiveErrorHandling` `Fault` `ServiceHost` zarar iletisi ile karşılaşıldığında hata olur. Hatalı olaya bağlanabilir ve hizmeti kapatabilir, düzeltici eylemler gerçekleştirebilir ve yeniden başlatabilirsiniz. Örneğin, `LookupId` <xref:System.ServiceModel.MsmqPoisonMessageException> öğesine yayıldığı `IErrorHandler` ve hizmet ana bilgisayarı hataları olduğunda, iletiyi `System.Messaging` `LookupId` kuyruktan kaldırmak ve iletiyi bazı dış depolardan ya da başka bir sıraya depolamak için kullanarak kuyruktan ileti almak için API 'sini kullanabilirsiniz. `ServiceHost`Normal işlemeyi sürdürmeye daha sonra yeniden başlatabilirsiniz. [MSMQ 4,0 ' de zarar Iletisi işleme](../samples/poison-message-handling-in-msmq-4-0.md) bu davranışı gösterir.  
  
## <a name="transaction-time-out-and-poison-messages"></a>İşlem zaman aşımı ve zarar Iletileri  
 Sıraya alınan aktarım kanalı ve Kullanıcı kodu arasında bir hata sınıfı meydana gelebilir. Bu hatalar, ileti güvenliği katmanı veya hizmet dağıtma mantığı gibi içindeki katmanlar tarafından algılanabilir. Örneğin, SOAP güvenlik katmanında eksik bir X. 509.440 sertifikası algılandı ve eksik bir eylem, iletinin uygulamaya dağıtıldığı durumlardır. Bu durumda, hizmet modeli iletiyi bırakır. İleti bir işlem içinde okunduğu ve bu işlem için bir sonuç sağlanamadığından, işlem zaman aşımına uğrar, iptal edilir ve ileti kuyruğa geri konur. Diğer bir deyişle, belirli bir hata sınıfı için işlem hemen iptal edilmez ancak işlem zaman aşımına uğrayana kadar bekler. Kullanarak bir hizmet için işlem zaman aşımını değiştirebilirsiniz <xref:System.ServiceModel.ServiceBehaviorAttribute> .  
  
 Bilgisayar genelinde işlem zaman aşımını değiştirmek için Machine. config dosyasını değiştirin ve uygun işlem zaman aşımını ayarlayın. İşlem sırasında ayarlanan zaman aşımına bağlı olarak, işlemin sonunda iptal edilir ve kuyruğa geri döner ve iptal sayısının artmasını unutmayın. Sonuç olarak, ileti zarar haline gelir ve doğru değerlendirme Kullanıcı ayarlarına göre yapılır.  
  
## <a name="sessions-and-poison-messages"></a>Oturumlar ve zarar Iletileri  
 Bir oturum, aynı yeniden deneme ve zarar iletisi işleme yordamlarına tek bir ileti olarak girer. Daha önce zarar iletileri için listelenen özellikler tüm oturum için geçerlidir. Bu, tüm oturumun yeniden deneneceği ve ileti reddedilirse son bir zarar iletisi kuyruğuna ya da gönderenin atılacak ileti kuyruğuna gittiği anlamına gelir.  
  
## <a name="batching-and-poison-messages"></a>Toplu ve zarar Iletileri  
 Bir ileti bir zarar iletisi haline gelirse ve bir toplu işin parçasıysa, tüm toplu işlem geri alınır ve kanal tek seferde bir ileti okumak üzere döndürülür. Toplu işleme hakkında daha fazla bilgi için bkz. [işlem Içindeki Iletileri toplu işleme](batching-messages-in-a-transaction.md)  
  
## <a name="poison-message-handling-for-messages-in-a-poison-queue"></a>Zarar sırasındaki Iletiler için zehirli ileti Işleme  
 Poison-Message kuyruğuna bir ileti yerleştirildiğinde, zehirli ileti işleme bitmez. Zarar iletisi sırasındaki iletiler yine de okunmalıdır ve işlenmelidir. Son zarar alt sırasından gelen iletileri okurken, zarar iletisi işleme ayarlarının bir alt kümesini kullanabilirsiniz. Geçerli ayarlar `ReceiveRetryCount` ve ' dir `ReceiveErrorHandling` . `ReceiveErrorHandling`Bırakma, reddetme veya hata olarak ayarlayabilirsiniz. `MaxRetryCycles`yok sayılır ve Move olarak ayarlandıysa bir özel durum oluşturulur `ReceiveErrorHandling` .  
  
## <a name="windows-vista-windows-server-2003-and-windows-xp-differences"></a>Windows Vista, Windows Server 2003 ve Windows XP farkları  
 Daha önce belirtildiği gibi, tüm Poison-Message işleme ayarları Windows Server 2003 ve Windows XP için geçerlidir. Windows Server 2003, Windows XP ve Windows Vista 'daki Message Queuing arasındaki aşağıdaki önemli farklılıklar, zehirli ileti işleme ile ilgilidir:  
  
- Windows Vista 'daki Message Queuing alt sıraları destekler, ancak Windows Server 2003 ve Windows XP alt sıraları desteklemez. Alt sıralar, zehirli ileti işlemede kullanılır. Yeniden deneme kuyrukları ve zarar sırası, zarar iletisi işleme ayarlarına göre oluşturulan uygulama kuyruğu için alt çizglardır. , `MaxRetryCycles` Oluşturulacak yeniden deneme alt sıraların sayısını belirler. Bu nedenle, Windows Server 2003 veya Windows XP 'de çalışırken `MaxRetryCycles` yok sayılır ve `ReceiveErrorHandling.Move` buna izin verilmez.  
  
- Windows Vista 'daki Message Queuing negatif bildirimi destekler, ancak Windows Server 2003 ve Windows XP desteklemez. Alma kuyruğu yöneticisinin olumsuz bir bildirimi, gönderme kuyruğu yöneticisinin reddedilen iletiyi atılacak ileti kuyruğuna yerleştirmesini sağlar. Bu nedenle, `ReceiveErrorHandling.Reject` Windows Server 2003 ve WINDOWS XP 'de buna izin verilmez.  
  
- Windows Vista 'daki Message Queuing ileti tesliminin denenme sayısını tutan bir ileti özelliğini destekler. Bu Abort Count özelliği Windows Server 2003 ve Windows XP 'de kullanılamaz. WCF, bellekteki durdurma sayısını korur, bu nedenle aynı ileti bir grupta birden fazla WCF hizmeti tarafından okunabildiği zaman bu özelliğin doğru bir değer içermemesi olasıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kuyruklar Genel Bakış](queues-overview.md)
- [Windows Vista, Windows Server 2003 ve Windows XP'de Kuyruğa Alma Özelliği Arasındaki Farklar](diff-in-queue-in-vista-server-2003-windows-xp.md)
- [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](../specifying-and-handling-faults-in-contracts-and-services.md)
