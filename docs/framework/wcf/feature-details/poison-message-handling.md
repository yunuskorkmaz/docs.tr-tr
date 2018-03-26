---
title: Zehirli İleti İşleme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d1c5e5a-7928-4a80-95ed-d8da211b8595
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8202c9f715944c6d556c0023444475838cfd5eab
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="poison-message-handling"></a>Zehirli İleti İşleme
A *zehir iletisi* uygulama Teslim girişimleri üst sınırını aştı iletisidir. Sıra tabanlı bir uygulama hataları nedeniyle bir ileti işleyemediğinde bu durum ortaya çıkabilir. Güvenilirlik taleplerini karşılamak üzere kuyruğa alınan bir uygulamayı bir işlem altında iletilerini alır. İleti altında yeni bir işlem denenir kuyruğa alınan iletinin alındığı işlem durduruluyor iletinin kuyrukta bırakır, böylece. İptal etmek işlem neden olan sorunu düzeltilmezse alma işlemini yapan uygulamanın alma ve teslim deneme sayısı aşıldı kadar aynı iletiyi durduruluyor döngü ve zehir iletisi sonuçları takılı.  
  
 Bir ileti zararlı bir ileti için birçok nedeni olabilir. Uygulamaya özel en yaygın nedenleri. Örneğin, bir uygulama bir iletiyi kuyruktan okur ve bazı veritabanı işlemleri yapar, uygulamanın işlem iptal için neden veritabanı üzerinde bir kilit almak başarısız olabilir. Veritabanı işlem durduruldu çünkü uygulamanın iletiyi ikinci kez yeniden okuyun ve veritabanı üzerinde bir kilit edinmeye başka bir çabayı neden sırasındaki ileti kalır. İletileri geçersiz bilgiler içeriyorsa zararlı olabilir. Örneğin, bir satın alma siparişi geçersiz müşteri numarası içerebilir. Bu durumlarda, uygulamanın gönüllü hareketi iptal ve zararlı bir ileti olmasını ileti zorlayabilirsiniz.  
  
 Nadir durumlarda, iletileri uygulamaya gönderilen başarısız olabilir. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Katmanı bulmak ileti ile ilgili bir sorun gibi ileti yanlış çerçeve sahipse, geçersiz bir ileti kimlik bilgileri bağlı veya geçersiz action üstbilgisi için. Bu durumlarda, uygulama hiçbir zaman iletiyi alır; Ancak, ileti zararlı bir ileti hala olabilir ve el ile işlenmesi.  
  
## <a name="handling-poison-messages"></a>Zehirli ileti işleme  
 İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], zehirli ileti işleme uygulamaya gönderilen iletileri veya uygulamaya gönderilir ancak nedeniyle işlenecek başarısız iletileri uğraşmanız alıcı uygulamanın bir mekanizma sağlar uygulamaya özgü nedenleri. Zehirli ileti işleme her kullanılabilir sıraya alınan bağlamaları aşağıdaki özellikleri tarafından yapılandırılır:  
  
-   `ReceiveRetryCount`. Bir iletinin teslimini uygulama sırasından uygulamaya yeniden deneneceğini maksimum sayısını gösterir. bir tamsayı değeri. Varsayılan değer 5'tir. Bu, burada hemen bir yeniden deneme sorun gibi bir veritabanı üzerinde geçici bir kilitlenme ile giderir durumda yeterlidir.  
  
-   `MaxRetryCycles`. En fazla yeniden deneme döngüsü sayısını belirten bir tamsayı değeri. Bir ileti uygulama sırasından yeniden deneme iletiler alt kuyruğuna ve yeniden deneme alt sırasına geri uygulama kuyruğuna teslim yeniden çalıştırmayı deneyin gelen yapılandırılabilir bir gecikmeden sonra aktarma bir yeniden deneme döngüsü oluşur. Varsayılan değer 2'dir. Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)], ileti denenir en fazla (`ReceiveRetryCount` + 1) * (`MaxRetryCycles` + 1) kez. `MaxRetryCycles` üzerinde göz ardı [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   `RetryCycleDelay`. Gecikme süresi arasında döngüleri yeniden deneyin. Varsayılan değer 30 dakikadır. `MaxRetryCycles` ve `RetryCycleDelay` birlikte burada düzenli bir gecikmeden sonra bir yeniden deneme giderir sorun sorunu gidermek için bir mekanizma sağlar. Örneğin, bu işlem yürütme bekleme SQL Server'da ayarlanan kilitli bir satır işler.  
  
-   `ReceiveErrorHandling`. En fazla yeniden deneme sayısı çalıştı sonra teslim başarısız oldu bir ileti için gerçekleştirilecek eylemi belirtir numaralandırması. Değerleri hataya, Drop Reddet olabilir ve taşıyın. Hata varsayılan seçenektir.  
  
-   Hata. Bu seçenek bir hataya neden olan dinleyiciyi gönderir `ServiceHost` hataya için. Uygulama sırasından ileti işlemeye devam etmeden önce iletiyi uygulama sırasından bazı dış mekanizması tarafından kaldırılması gerekir.  
  
-   Bırakın. Bu seçenek zehir iletisi bırakır ve ileti hiçbir zaman uygulamaya teslim edilir. Varsa iletinin `TimeToLive` özelliği sona erdi bu noktada, ardından iletiyi gönderenin sahipsiz sıraya görünebilir. Aksi durumda, ileti herhangi bir yerde görünmez. Bu seçenek, kullanıcı ileti kaybolursa yapmanız gerekenler tanımlanmamış olduğunu gösterir.  
  
-   Reddeder. Bu seçenek yalnızca kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)]. Bu, Message Queuing (uygulama ileti alamıyor gönderme sıra yöneticisi olumsuz bildirim göndermek için MSMQ) bildirir. İleti gönderme sırası yöneticisinin sahipsiz sıraya konur.  
  
-   Taşıyın. Bu seçenek yalnızca kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)]. Bu, daha sonra bir poison ileti işleme uygulaması tarafından işlenmek poison ileti kuyruğuna zehir iletisi taşır. Uygulama sırasındaki sırasına poison ileti sırasıdır. Poison ileti işleme uygulaması olabilir bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zararlı sıradaki iletileri okur hizmet. Zararlı sıranın uygulama sırasındaki sırasına olan ve net.msmq:// çözülebilir\<*makine adı*>/*applicationQueue*; zehirleme, burada  *makine adı* sıranın bulunduğu bilgisayarın adıdır ve *applicationQueue* uygulamaya özgü sıranın adıdır.  
  
 Bir ileti için gerçekleştirilen teslim denemelerin sayısı şunlardır:  
  
-   ((ReceiveRetryCount+1) * (MaxRetryCycles + 1)) üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
-   (ReceiveRetryCount + 1) üzerindeki [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
> [!NOTE]
>  Yeniden deneme yok başarıyla teslim bir ileti için yapılır.  
  
 Bir ileti okundu denemesi sayısı izlemek için [!INCLUDE[wv](../../../../includes/wv-md.md)] ileti sayısını sayar taşıma count özelliğini iptalleri ve sayar dayanıklı ileti özelliği uygulama sıranın arasında taşır korur ve Alt sıralar. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Kanal alma yeniden deneme sayısı ve yeniden deneme döngüsü sayısı işlem için bunları kullanır. Üzerinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)], durdurma sayısı bellek tarafından korunur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanal ve uygulama başarısız olursa sıfırlanır. Ayrıca, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanal durdurma sayar belleği en fazla 256 iletiler için herhangi bir zamanda tutun. 257th ileti salt okunur ise, en eski ileti durdurma sayısı sıfırlanır.  
  
 Durdurma sayısı ve count özelliklerini, hizmet işlemi işlemi bağlam aracılığıyla kullanılabilir taşıyın. Aşağıdaki kod örneğinde, bunlara erişmek gösterilmiştir.  
  
 [!code-csharp[S_UE_MSMQ_Poison#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/service.cs#1)]  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iki standart sıraya alınan bağlamaları sağlar:  
  
-   <xref:System.ServiceModel.NetMsmqBinding>. A [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] bağlama sırası tabanlı iletişim diğer gerçekleştirmek için uygun [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uç noktaları.  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Var olan Message Queuing uygulamaları ile iletişim kurmak için uygun bir bağlama.  
  
> [!NOTE]
>  Gereksinimlerine göre bu bağlamaların özelliklerinde değiştirebilir, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti. İşleme mekanizması tüm zehirli ileti alıcı uygulamaya yereldir. Alma işlemini yapan uygulamanın sonuçta durdurur ve gönderene olumsuz bildirim gönderir sürece gönderen uygulama görünmeyen bir işlemdir. Bu durumda, iletiyi gönderenin sahipsiz sıraya taşınır.  
  
## <a name="best-practice-handling-msmqpoisonmessageexception"></a>En iyi yöntem: MsmqPoisonMessageException işleme  
 Hizmet bir ileti zararlı olduğunu belirlediğinde, sıraya alınan aktarım oluşturur bir <xref:System.ServiceModel.MsmqPoisonMessageException> içeren `LookupId` zehirli ileti.  
  
 Alıcı uygulamanın uygulayabilirsiniz <xref:System.ServiceModel.Dispatcher.IErrorHandler> uygulama gerektiriyor hataları işlemek için arabirim. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Üzerinden hata işleme ve bildirme denetimini genişletme](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md).  
  
 Uygulama hizmeti sıradaki iletileri kalan erişebilmesi için bir zehirli ileti sırası zarar iletileri taşır otomatik zehirli ileti işleme çeşit gerektirebilir. Poison ileti özel durumlarını dinlemek için hata işleyicisine mekanizmasını kullanarak olduğu tek senaryo olduğunda <xref:System.ServiceModel.Configuration.MsmqBindingElementBase.ReceiveErrorHandling%2A> ayar <xref:System.ServiceModel.ReceiveErrorHandling.Fault>. Message Queuing 3.0 poison ileti örnek bu davranış gösterir. Aşağıda, en iyi uygulamalar dahil olmak üzere zarar iletileri işlemek için uygulanması gereken adımlar açıklanmaktadır:  
  
1.  Uygulamanızın gereksinimlerine zararlı ayarlarınızı yansıtacak emin olun. Ayarları ile çalışırken, üzerinde Message Queuing özelliklerini arasındaki farklar anladığınızdan emin olun [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
2.  Gerekirse, uygulama `IErrorHandler` poison ileti hataları işlemek için. Ayar olmadığından `ReceiveErrorHandling` için `Fault` sıradaki zehir iletisi taşımak için veya bir dış bağımlı sorunu gidermek için el ile bir mekanizma gerekir tipik kullanım uygulamaktır `IErrorHandler` zaman `ReceiveErrorHandling` ayarlanır `Fault`, olarak Aşağıdaki kodda gösterildiği.  
  
     [!code-csharp[S_UE_MSMQ_Poison#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonerrorhandler.cs#2)]  
  
3.  Oluşturma bir `PoisonBehaviorAttribute` , hizmet davranışı kullanabilirsiniz. Davranış yükler `IErrorHandler` dağıtıcı üzerinde. Aşağıdaki kod örneğine bakın.  
  
     [!code-csharp[S_UE_MSMQ_Poison#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonbehaviorattribute.cs#3)]  
  
4.  Hizmetinizi zararlı davranışı özniteliğiyle açıklama emin olun.  
  
  
  
 Ayrıca, varsa `ReceiveErrorHandling` ayarlanır `Fault`, `ServiceHost` zehir iletisi karşılaşıldığında hataları. Hatalı olay takma ve hizmetini kapatın, düzeltme girişimlerinde bulunun ve yeniden başlatın. Örneğin, `LookupId` içinde <xref:System.ServiceModel.MsmqPoisonMessageException> yayılmadan `IErrorHandler` not ettiğiniz ve hizmet ana hataları kullandığınızda `System.Messaging` sıra kullanımından ileti almak için API `LookupId` iletiden kaldırmak için Kuyruk ve bazı dış deposunda veya başka bir kuyruğa ileti deposu. Daha sonra yeniden başlatabilirsiniz `ServiceHost` normal işleme devam etmek için. [Zehirli ileti işleme MSMQ 4.0](../../../../docs/framework/wcf/samples/poison-message-handling-in-msmq-4-0.md) Bu davranış gösterir.  
  
## <a name="transaction-time-out-and-poison-messages"></a>İşlem zaman aşımı ve zarar iletileri  
 Hataların bir sınıf sıraya alınan aktarım kanalı ve kullanıcı kodu arasında gerçekleşebilir. Bu hatalar Katmanlar ileti güvenlik katmanı veya mantığı gönderme hizmeti gibi ortası tarafından algılanabilir. Örneğin, eksik bir X.509 sertifikası SOAP güvenlik katmanı algıladı ve eksik eylem olduğunuz nerede ileti uygulamaya gönderilen durumları. Bu gerçekleştiğinde, hizmet modeli ileti bırakır. İletinin işlemde okuyun ve işlem zaman aşımına uğrar sağlanan bu işlem için bir sonuç olamaz olduğundan iptal eder ve iletiyi yerleştirin geri sıraya. Diğer bir deyişle, belirli bir bir sınıf hataların için işlem değil hemen durdurmak ancak bu işlem zaman aşımına uğrayana kadar bekler. Kullanarak bir hizmet için işlem zaman aşımını değiştirebilirsiniz <xref:System.ServiceModel.ServiceBehaviorAttribute>.  
  
 Bilgisayar genelinde işlem zaman aşımı süresini değiştirmek için machine.config dosyasının değiştirmek ve uygun işlem zaman aşımını ayarlama. İşlem kümesi zaman aşımı bağlı olarak, dikkat çekmek üzere işlem sonunda durdurur ve yeniden kuyruğa gider ve kendi durdurma sayısı artırılır önemlidir. Sonuç olarak, ileti zararlı haline gelir ve sağ değerlendirme göre kullanıcı ayarları yapılır.  
  
## <a name="sessions-and-poison-messages"></a>Oturumlar ve zarar iletileri  
 Bir oturum tek bir ileti aynı yeniden deneme ve poison ileti işleme yordamları uğradığında. Zehirli ileti için daha önce listelenen özellikleri tüm oturum için geçerlidir. Bu, tüm oturum yeniden denenir ve ileti reddedilirse son poison ileti sırası veya gönderenin sahipsiz sırayı giden anlamına gelir.  
  
## <a name="batching-and-poison-messages"></a>Toplu işleme ve zarar iletileri  
 Bir ileti zararlı bir ileti olur ve bir toplu iş parçası ise, toplu işin tamamını geri alınır ve aynı anda tek bir ileti okuma kanal döndürür. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Toplu işleme, bkz: [bir işlemde toplu ileti](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
  
## <a name="poison-message-handling-for-messages-in-a-poison-queue"></a>Poison ileti zararlı sıradaki iletiler için işleme  
 Bir ileti poison ileti sıraya yerleştirildiğinde poison ileti işleme bitmez. Poison ileti sıradaki iletiler hala okuyun ve işlenmiş. Son zarar alt sırasına iletileri okunurken poison ileti işleme ayarların bir alt kümesini kullanabilirsiniz. Geçerli ayarları `ReceiveRetryCount` ve `ReceiveErrorHandling`. Ayarlayabileceğiniz `ReceiveErrorHandling` , reddetme, bırakma veya hata. `MaxRetryCycles` göz ardı edilir ve varsa bir özel durum `ReceiveErrorHandling` taşımak için ayarlanır.  
  
## <a name="windows-vista-windows-server-2003-and-windows-xp-differences"></a>Windows Vista, Windows Server 2003 ve Windows XP farkları  
 Daha önce belirtildiği gibi tüm poison ileti işleme ayarlarının uygulanacağı [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. Aşağıdaki anahtarı Message Queuing arasındaki farklar hakkında [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], [!INCLUDE[wxp](../../../../includes/wxp-md.md)], ve [!INCLUDE[wv](../../../../includes/wv-md.md)] poison ileti işleme için uygundur:  
  
-   Message Queuing [!INCLUDE[wv](../../../../includes/wv-md.md)] sıralar, destekler ancak [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)] sıralar desteklemez. Alt sıralar poison-ileti işleme kullanılır. Yeniden deneme sıralarındaki ve zararlı sıranın poison ileti işleme ayarlara göre oluşturulan uygulama sırasındaki sıralara markalarıdır. `MaxRetryCycles` Kaç tane oluşturmak için sıralar yeniden deneme belirler. Bu nedenle, çalışırken [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] veya [!INCLUDE[wxp](../../../../includes/wxp-md.md)], `MaxRetryCycles` göz ardı edilir ve `ReceiveErrorHandling.Move` verilmez.  
  
-   Message Queuing [!INCLUDE[wv](../../../../includes/wv-md.md)] destekler negatif bildirim, sırada [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)] desteklemez. Olumsuz bildirim alma sıra Yöneticisi'nden sahipsiz sıraya reddedilen ileti yerleştirmek gönderme sıra Yöneticisi neden olur. Bu nedenle, `ReceiveErrorHandling.Reject` ile izin verilmiyor [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   Message Queuing [!INCLUDE[wv](../../../../includes/wv-md.md)] ileti teslimi kaç kez sayısını tutar bir ileti özelliği denemesi destekler. Bu iptal sayısı özelliği kullanılabilir değil [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aynı iletiyi birden fazla tarafından okunduğunda bu özelliği doğru bir değer içeremez mümkün olacak şekilde durdurma sayısı bellekte saklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] grubunda hizmet.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kuyruklara Genel Bakış](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [Windows Vista, Windows Server 2003 ve Windows XP'de Kuyruğa Alma Özelliği Arasındaki Farklar](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
