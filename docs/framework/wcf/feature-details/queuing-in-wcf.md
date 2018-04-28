---
title: WCF'de Kuyruğa Alma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e98d76ba-1acf-42cd-b137-0f8214661112
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 01dc36c73d9e668dd98cb5ba8b275d3d5177ba61
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="queuing-in-wcf"></a>WCF'de Kuyruğa Alma
Bu bölümde, kuyruğa alınan iletişim kullanmayı açıklar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="queues-as-a-wcf-transport-binding"></a>Bağlama sırası bir WCF olarak taşıma  
 İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ne alınıp sözleşmeleri belirtin. Sözleşmelerin iş bağımlı veya uygulamaya özel ileti alışverişlerinde durumda. İleti değiş tokuşu için kullanılan mekanizma (veya "nasıl") bağlamalar belirtildi. Bağlama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ileti değişimi ayrıntılarını kapsüller. Bunlar kullanıcının aktarım veya bağlamaları temsil Protokolü çeşitli yönlerini denetlemek yapılandırma düğmelerini kullanıma sunar. İçinde queuing [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] birçok kuyruğa alma uygulamaları için büyük bir avantajı herhangi diğer aktarım bağlama gibi işlem görür. Bugün, çok sayıda kuyruğa alma uygulamaları diğer uzak yordam çağrısı (RPC) farklı şekilde yazılır-stil dağıtılan uygulamalar izleyin ve sürdürmek daha zor hale getirme. İle [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], dağıtılmış bir uygulamayı yazma stili çok benzer, izleyin ve bakımını kolaylaştırır. Ayrıca, iş mantığı ayrı olarak Exchange'den mekanizması çıkışı Finansman tarafından taşıma yapılandırmak veya uygulamanın belirli bir kod etkilemeden değişiklik daha kolay olur. Aşağıdaki şekilde bir WCF hizmeti ve bir taşıma olarak MSMQ kullanan istemci yapısını gösterilmektedir.  
  
 ![Sıraya alınan uygulama diyagramı](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "dağıtılmış-sıra-Şekil")  
  
 Önceki rakamdan görüldüğü gibi istemci ve hizmet yalnızca uygulama semantiğini, diğer bir deyişle, sözleşme ve uygulama tanımlamanız gerekir. Hizmet bir sıralı bağlama ile tercih edilen ayarları yapılandırır. İstemcinin kullandığı [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) oluşturmak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci hizmeti ve hizmete iletileri göndermek için kullanılacak bağlamaları açıklayan bir yapılandırma dosyası oluşturmak üzere. Bu nedenle, sıraya alınan ileti göndermek için istemci başlatır bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci ve bunun üzerinde bir işlemi çağırır. Bu ileti iletim kuyruğuna gönderilen ve hedef sıra aktarılan neden olur. Kuyruğa alınan iletişim tüm karmaşıklığını ileti gönderme ve alma uygulamadan gizli.  
  
 Uyarılar hakkında bağlayıcı sıraya [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] içerir:  
  
-   Varsayılan olarak bağlayıcı sıraya çünkü tüm hizmet işlemleri tek yönlü olmalıdır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kuyrukları kullanma çift yönlü iletişimi desteklemez. İki yönlü iletişim örnek ([iki yönlü iletişim](../../../../docs/framework/wcf/samples/two-way-communication.md)) iki yönlü sözleşmeleri kuyrukları kullanma çift yönlü iletişimi uygulamak için nasıl kullanılacağı gösterilmektedir.  
  
-   Oluşturmak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] meta veri değişimi kullanan istemci gerektirdiğini hizmetine ek bir HTTP uç noktası doğrudan oluşturmak için sorgulanabilir şekilde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci ve uygun şekilde yapılandırmak için bağlama bilgileri elde sıraya alındı iletişim.  
  
-   Sıraya alınan bağlama, ek yapılandırma dışında göre [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gereklidir. Örneğin, <xref:System.ServiceModel.NetMsmqBinding> ile birlikte gelen sınıfı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yanı sıra bağlamalar yapılandırmak en düşük düzeyde Message Queuing (MSMQ) yapılandırma gerektirir.  
  
 Aşağıdaki bölümlerde ile birlikte gelen belirli sıraya alınan bağlamaları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], MSMQ üzerinde dayalı.  
  
### <a name="msmq"></a>MSMQ  
 Sıraya alınan aktarım [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ kendi kuyruğa alınan iletişim için kullanır.  
  
 MSMQ Windows ile isteğe bağlı bir bileşen olarak gelir ve bir NT hizmeti olarak çalışır. İletileri iletim sırası iletim ve bir hedef sıraya teslim yakalar. Böylece iletiler iletim kayboluyor değil MSMQ sırası yöneticilerini güvenilir ileti aktarma protokolü kullanır. Protokol, yerel ya da SOAP tabanlı gibi SOAP güvenilir ileti Protokolü (SRMP) olabilir.  
  
 MSMQ, işlem veya işlem olmayan sıralar olabilir. Bir işlem sırası, yakalanan ve bir işlem içinde teslim inceleyip işlemi sırasındaki depolanan iletilerine izin verir. İşlemsel bir sıraya gönderilen iletileri yalnızca bir kez sırada aktarılır. Geçici ve kalıcı iletilerini göndermek için işlemsel olmayan bir sıraya kullanabilirsiniz. İşlemsel olmayan bir sıraya gönderilen bir ileti hiçbir güvenilir aktarımı güvence taşımaz; Bu nedenle, iletileri kaybolmuş olabilir.  
  
 MSMQ kuyrukları Ayrıca Active Directory dizin hizmetine kayıtlı bir Windows kimlik bilgileriniz kullanılarak güvenli hale getirilebilir. MSMQ yüklerken, bir Windows etki alanı ağına parçası olarak bilgisayar gerektirir Active Directory Tümleştirme yükleyebilirsiniz.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] MSMQ bkz [yükleme Message Queuing (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md).  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 [ \<NetMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) sıraya alınan bağlama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] için iki sağlar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ kullanarak iletişim kurmak için uç noktaları. Bağlama, bu nedenle, MSMQ için belirli özellikleri sunar. Ancak, tüm MSMQ özellikleri ve Özellikler sunulan `NetMsmqBinding`. Sıkıştırma `NetMsmqBinding` en iyi bir müşterilerin çoğu yeterli bulmalıdır özellikler kümesi ile tasarlanmıştır.  
  
 `NetMsmqBinding` Bugüne kadarki özellikleri formunda bağlantılarına açıklanan çekirdek queuing kavramları bildirimleri. Bu özellikler için MSMQ sırayla aktarmak ve iletileri sunmak nasıl iletişim kurar. Özellik kategorileri tartışması aşağıdaki bölümlerde ' dir. Daha fazla bilgi için belirli özellikleri daha tamamen açıklayan kavramsal konulara bakın.  
  
#### <a name="exactlyonce-and-durable-properties"></a>ExactlyOnce ve dayanıklı özellikleri  
 `ExactlyOnce` Ve `Durable` özellikleri etkileyen iletiler sıralar arasında nasıl aktarılır:  
  
-   `ExactlyOnce`: Ayarlandığında `true` ileti teslim, değil yineleniyor olduğunu (varsayılan), sıraya alınan kanal sağlar. Ayrıca, ileti kaybı olmadığından sağlar. İleti teslim edilemez veya ileti teslim önce iletinin yaşam süresi oluşturmayı süresi, başarısız iletinin teslimat hatası nedeni ile birlikte bir sahipsiz sıraya kaydedilir. Ayarlandığında `false`, sıraya alınan kanal iletisi aktarmak için çaba yapar. Bu durumda, isteğe bağlı olarak sahipsiz sırayı seçebilirsiniz.  
  
-   `Durable:` Ayarlandığında `true` (varsayılan), MSMQ iletisini işlemi diskte depolar, sıraya alınan kanal sağlar. Bu nedenle, MSMQ hizmeti durdurun ve yeniden olsaydı, disk üzerindeki iletiler hedef sıra aktarılan veya hizmete teslim. Ayarlandığında `false`, iletiler volatile deposunda saklanır ve MSMQ hizmetini durdurup yeniden başlatarak üzerinde kaybolur.  
  
 İçin `ExactlyOnce` güvenilir bir aktarım MSMQ işlem sırası gerektirir. Ayrıca, MSMQ işlem kuyruktan okunmak üzere bir işlem gerektirir. Kullandığınızda, bu nedenle `NetMsmqBinding`, unutmayın bir işlem göndermek veya almak için gereken zaman iletileri `ExactlyOnce` ayarlanır `true`. Benzer şekilde, MSMQ ne zaman gibi en yüksek çaba güvence için işlem dışı sıra gerektirir `ExactlyOnce` olan `false` ve volatile ileti. Bu nedenle, ayarlarken `ExactlyOnce` için `false` veya için dayanıklı `false`, göndermek veya almak bir işlem kullanarak.  
  
> [!NOTE]
>  Doğru bir sıra (işlem veya işlem olmayan) bağlamaları ayarlarında temel alınarak oluşturulduğundan emin olun. Varsa `ExactlyOnce` olan `true`, bir işlem sırası kullanın; Aksi halde, işlemsel olmayan bir sıraya kullanın.  
  
#### <a name="dead-letter-queue-properties"></a>Sahipsiz Sıra özellikleri  
 Sahipsiz Sıra teslimi başarısız iletileri depolamak için kullanılır. Kullanıcı iletileri teslim edilemeyen sıranın dışında okur karşılayan mantığı yazabilirsiniz.  
  
 Birçok queuing sistemi için sistem genelinde bir sahipsiz sırayı sağlar. Bir sistem genelinde işlemsel olmayan eski ileti sırası işlem olmayan sıralar için teslim başarısız iletileri için ve bir sistem genelinde işlem eski ileti sırası işleme uygun sıralarda için teslim başarısız iletileri için MSMQ sağlar.  
  
 Birden çok istemci iletileri farklı bir hedef sıraya göndermek için MSMQ hizmeti paylaşıyorsanız, istemciler tarafından gönderilen tüm iletiler için aynı sahipsiz sırayı gidin. Bu her zaman tercih değildir. Daha iyi yalıtım [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve MSMQ [!INCLUDE[wv](../../../../includes/wv-md.md)] özel sahipsiz sırayı (veya uygulamaya özgü sahipsiz sırayı) sağlayan kullanıcı teslimi başarısız iletileri depolamak için belirtebilirsiniz. Bu nedenle, farklı istemciler aynı sahipsiz sırayı paylaşmayın.  
  
 Bağlama ilgilenilen iki özelliklere sahiptir:  
  
-   `DeadLetterQueue`: Bu özellik eski ileti sırası istenen olup olmadığını gösteren bir numaralandırma olur. Bir isteniyorsa numaralandırması sahipsiz sırayı türünü de içerir. Değerler `None`, `System`, ve `Custom`. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Bu özellikleri yorumu bkz [ileti aktarımı hatalarını işlemek için teslim edilemeyen iletiler sırası kullanma](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
  
-   `CustomDeadLetterQueue`: Bu özellik uygulamaya özgü sahipsiz sırayı Tekdüzen Kaynak Tanımlayıcısı (URI) adresidir. Bu gereklidir `DeadLetterQueue`.`Custom` seçilir.  
  
#### <a name="poison-message-handling-properties"></a>Zehirli ileti işleme özellikleri  
 Hizmet bir işlem altında hedef kuyruktan iletileri okuduğunda hizmet çeşitli nedenlerle iletiyi işlemek başarısız olabilir. İleti geri yeniden okumaya sıraya konur. Sürekli olarak, bir dizi poison ileti işleme başarısız iletilerle dağıtılacak bağlamasında özellikleri yapılandırılabilir. Dört özellikleri vardır: `ReceiveRetryCount`, `MaxRetryCycles`, `RetryCycleDelay`, ve `ReceiveErrorHandling`. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Bu özellikleri görmek [zehirli ileti işleme](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
#### <a name="security-properties"></a>Güvenlik özellikleri  
 Erişim denetim listeleri (ACL'ler) gibi MSMQ kendi güvenlik modeli, bulunan bir sıra kullanıma sunar. veya kimliği doğrulanmış iletilere gönderme. `NetMsmqBinding` Aktarım güvenlik ayarlarına bir parçası olarak bu güvenlik özellikleri sunar. Taşıma güvenliği bağlamasında iki özellik vardır: `MsmqAuthenticationMode` ve `MsmqProtectionLevel`. Bu özellikleri ayarlarında MSMQ nasıl yapılandırıldığına bağlıdır. Daha fazla bilgi için bkz: [taşıma güvenliği kullanarak iletileri güvenli hale getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
 Taşıma güvenliği ek olarak, gerçek SOAP iletisi kendisini ileti güvenliği kullanılarak güvenli hale getirilebilir. Daha fazla bilgi için bkz: [ileti güvenliği kullanarak iletileri güvenli hale getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md).  
  
 `MsmqTransportSecurity` Ayrıca iki özellikleri sunar `MsmqEncryptionAlgorithm` ve `MsmqHashAlgorithm`. İletilerin kuyruktan kuyruğa aktarımı şifreleme ve karma imzalarını seçme farklı algoritma numaralandırmalar bunlar.  
  
#### <a name="other-properties"></a>Diğer özellikler  
 Önceki özellikleri yanı sıra, bağlama Ekle sunulan diğer MSMQ özgü özellikler:  
  
-   `UseSourceJournal`: Bu kaynak günlük kaydı belirtmek için bir özelliği açıktır. Kaynak günlük kaydı başarıyla iletim sırasından aktarılan iletileri izler bir MSMQ özelliğidir.  
  
-   `UseMsmqTracing`: MSMQ izleme açık olduğunu belirtmek için bir özelliği. MSMQ İzleme Raporu iletilerini bir ileti bırakır veya bir makine MSMQ sıra yöneticisi barındırma sırasında her zaman bir rapor sırası gönderir.  
  
-   `QueueTransferProtocol`: Bir numaralandırma kuyruktan kuyruğa ileti aktarımlar için kullanılacak protokolü. MSMQ yerel sıra sıra Aktarım Protokolü ve SOAP Güvenilir Mesajlaşma Protokolü (SRMP) adlı bir SOAP tabanlı protokolü kullanır. SRMP HTTP aktarımı kuyruktan kuyruğa aktarımları için kullanılırken kullanılır. Kuyruktan kuyruğa aktarımları için HTTPS kullanan güvenli SRMP kullanılır.  
  
-   `UseActiveDirectory`: Active Directory sıra adres çözümlemesi için kullanılıp kullanılmayacağını belirtmek için bir Boole değeri. Varsayılan olarak, bu kapalıdır. Daha fazla bilgi için bkz: [hizmet uç noktaları ve kuyruk işleme](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 `MsmqIntegrationBinding` İstediğiniz kullanıldığında bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] C, C++, COM veya System.Messaging API'leri ile yazılmış varolan bir MSMQ uygulamayla iletişim kurmak için uç nokta.  
  
 Bağlama özellikleri aynıdır `NetMsmqBinding`. Ancak, aşağıdaki farkları Uygula:  
  
-   İçin işlem sözleşmesi `MsmqIntegrationBinding` tek bir parametre türü almak için sınırlı <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> burada tür parametresi, gövde türü.  
  
-   MSMQ yerel ileti özelliklerinin çoğunu açığa içinde <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> kullanmak için.  
  
-   Seri hale getirme ve seri durumdan çıkarma ileti gövdesinin yardımcı olmak için XML ve ActiveX gibi serileştiricileri verilmiştir.  
  
### <a name="sample-code"></a>Örnek kod  
 WCF yazma hakkında adım adım yönergeler için MSMQ kullanan hizmetler aşağıdaki konulara bakın:  
  
-   [Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
  
-   [Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
  
 WCF MSMQ kullanımını gösteren tamamlanmış kod örneği için aşağıdaki konulara bakın:  
  
-   [İşlem Gerçekleştirilmiş MSMQ Bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
  
-   [Geçici Kuyruğa Alınmış İletişim](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
  
-   [Teslim Edilemeyen İletiler Sırası](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
  
-   [Oturumlar ve Kuyruklar](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
  
-   [Çift Yönlü İletişim](../../../../docs/framework/wcf/samples/two-way-communication.md)  
  
-   [İşlem Yapılan Toplu İşlem](../../../../docs/framework/wcf/samples/transacted-batching.md)  
  
-   [SRMP](../../../../docs/framework/wcf/samples/srmp.md)  
  
-   [Message Queuing Üzerinden İleti Güvenliği](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmet Uç Noktaları ve Kuyruk İşleme](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)  
 [Kuyruğa Alınan Bir Uygulamayı Web'de Barındırma](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
