---
title: WCF'de Kuyruğa Alma
ms.date: 03/30/2017
ms.assetid: e98d76ba-1acf-42cd-b137-0f8214661112
ms.openlocfilehash: 7f0a6700dba8eb844cc471704095b29c2a2c7937
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="queuing-in-wcf"></a>WCF'de Kuyruğa Alma
Bu bölüm, Windows Communication Foundation (WCF) kuyruğa alınan iletişim kullanmayı açıklar.  
  
## <a name="queues-as-a-wcf-transport-binding"></a>Bağlama sırası bir WCF olarak taşıma  
 WCF içinde ne alınıp sözleşmeleri belirtin. Sözleşmelerin iş bağımlı veya uygulamaya özel ileti alışverişlerinde durumda. İleti değiş tokuşu için kullanılan mekanizma (veya "nasıl") bağlamalar belirtildi. WCF bağlamaları ileti değişimi ayrıntılarını kapsüller. Bunlar kullanıcının aktarım veya bağlamaları temsil Protokolü çeşitli yönlerini denetlemek yapılandırma düğmelerini kullanıma sunar. WCF'de kuyruğa alma, çok sayıda kuyruğa alma uygulamaları için büyük bir avantajı herhangi diğer aktarım bağlama gibi değerlendirilir. Bugün, çok sayıda kuyruğa alma uygulamaları diğer uzak yordam çağrısı (RPC) farklı şekilde yazılır-stil dağıtılan uygulamalar izleyin ve sürdürmek daha zor hale getirme. WCF ile dağıtılmış bir uygulamayı yazma stili çok izleyin ve bakımını kolaylaştırır aynıdır. Ayrıca, iş mantığı ayrı olarak Exchange'den mekanizması çıkışı Finansman tarafından taşıma yapılandırmak veya uygulamanın belirli bir kod etkilemeden değişiklik daha kolay olur. Aşağıdaki şekilde bir WCF hizmeti ve bir taşıma olarak MSMQ kullanan istemci yapısını gösterilmektedir.  
  
 ![Sıraya alınan uygulama diyagramı](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "dağıtılmış-sıra-Şekil")  
  
 Önceki rakamdan görüldüğü gibi istemci ve hizmet yalnızca uygulama semantiğini, diğer bir deyişle, sözleşme ve uygulama tanımlamanız gerekir. Hizmet bir sıralı bağlama ile tercih edilen ayarları yapılandırır. İstemcinin kullandığı [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmetine bir WCF istemcisi oluşturmak için ve hizmete iletileri göndermek için kullanılacak bağlamaları açıklayan bir yapılandırma dosyası oluşturmak için. Bu nedenle, sıraya alınan ileti göndermek için istemci bir WCF istemcisi oluşturur ve bunu üzerinde bir işlemi çağırır. Bu ileti iletim kuyruğuna gönderilen ve hedef sıra aktarılan neden olur. Kuyruğa alınan iletişim tüm karmaşıklığını ileti gönderme ve alma uygulamadan gizli.  
  
 Wcf'de kuyruğa alınan bağlama hakkında uyarılar şunları içerir:  
  
-   WCF'de bağlama varsayılan sıraya çünkü işlemlerini tek yönlü olmalıdır tüm Hizmet Kuyrukları kullanma çift yönlü iletişimi desteklemez. İki yönlü iletişim örnek ([iki yönlü iletişim](../../../../docs/framework/wcf/samples/two-way-communication.md)) iki yönlü sözleşmeleri kuyrukları kullanma çift yönlü iletişimi uygulamak için nasıl kullanılacağı gösterilmektedir.  
  
-   WCF istemcisi oluşturma ve kuyruğa alınan iletişim uygun şekilde yapılandırmak için bağlama bilgilerini elde etmek için doğrudan sorgulanabilir bir WCF oluşturmak için meta veri değişimi kullanan istemci hizmeti hakkında ek bir HTTP uç noktası gerektirir.  
  
-   Üzerinde sıraya alınan bağlama bağlı olarak, WCF dışında ek yapılandırma gerekli değildir. Örneğin, <xref:System.ServiceModel.NetMsmqBinding> WCF ile birlikte gelen sınıfı yanı sıra bağlamalar yapılandırmak en düşük düzeyde Message Queuing (MSMQ) yapılandırma gerektirir.  
  
 Aşağıdaki bölümlerde MSMQ üzerinde temel WCF ile birlikte gelen belirli sıraya alınan bağlamaları açıklanmaktadır.  
  
### <a name="msmq"></a>MSMQ  
 WCF'de sıraya alınan aktarım MSMQ kendi kuyruğa alınan iletişim için kullanır.  
  
 MSMQ Windows ile isteğe bağlı bir bileşen olarak gelir ve bir NT hizmeti olarak çalışır. İletileri iletim sırası iletim ve bir hedef sıraya teslim yakalar. Böylece iletiler iletim kayboluyor değil MSMQ sırası yöneticilerini güvenilir ileti aktarma protokolü kullanır. Protokol, yerel ya da SOAP tabanlı gibi SOAP güvenilir ileti Protokolü (SRMP) olabilir.  
  
 MSMQ, işlem veya işlem olmayan sıralar olabilir. Bir işlem sırası, yakalanan ve bir işlem içinde teslim inceleyip işlemi sırasındaki depolanan iletilerine izin verir. İşlemsel bir sıraya gönderilen iletileri yalnızca bir kez sırada aktarılır. Geçici ve kalıcı iletilerini göndermek için işlemsel olmayan bir sıraya kullanabilirsiniz. İşlemsel olmayan bir sıraya gönderilen bir ileti hiçbir güvenilir aktarımı güvence taşımaz; Bu nedenle, iletileri kaybolmuş olabilir.  
  
 MSMQ kuyrukları Ayrıca Active Directory dizin hizmetine kayıtlı bir Windows kimlik bilgileriniz kullanılarak güvenli hale getirilebilir. MSMQ yüklerken, bir Windows etki alanı ağına parçası olarak bilgisayar gerektirir Active Directory Tümleştirme yükleyebilirsiniz.  
  
 MSMQ hakkında daha fazla bilgi için bkz: [yükleme Message Queuing (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md).  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 [ \<NetMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) WCF sağlar MSMQ kullanarak iletişim kurmak iki WCF uç noktaları için sıraya alınan bağlama. Bağlama, bu nedenle, MSMQ için belirli özellikleri sunar. Ancak, tüm MSMQ özellikleri ve Özellikler sunulan `NetMsmqBinding`. Sıkıştırma `NetMsmqBinding` en iyi bir müşterilerin çoğu yeterli bulmalıdır özellikler kümesi ile tasarlanmıştır.  
  
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
  
 Birden çok istemci iletileri farklı bir hedef sıraya göndermek için MSMQ hizmeti paylaşıyorsanız, istemciler tarafından gönderilen tüm iletiler için aynı sahipsiz sırayı gidin. Bu her zaman tercih değildir. WCF ve MSMQ daha iyi yalıtım [!INCLUDE[wv](../../../../includes/wv-md.md)] özel sahipsiz sırayı (veya uygulamaya özgü sahipsiz sırayı) sağlamak kullanıcı teslimi başarısız iletileri depolamak için belirtebilirsiniz. Bu nedenle, farklı istemciler aynı sahipsiz sırayı paylaşmayın.  
  
 Bağlama ilgilenilen iki özelliklere sahiptir:  
  
-   `DeadLetterQueue`: Bu özellik eski ileti sırası istenen olup olmadığını gösteren bir numaralandırma olur. Bir isteniyorsa numaralandırması sahipsiz sırayı türünü de içerir. Değerler `None`, `System`, ve `Custom`. Bu özellikleri yorumu hakkında daha fazla bilgi için bkz: [ileti aktarımı hatalarını işlemek için teslim edilemeyen iletiler sırası kullanma](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
  
-   `CustomDeadLetterQueue`: Bu özellik uygulamaya özgü sahipsiz sırayı Tekdüzen Kaynak Tanımlayıcısı (URI) adresidir. Bu gereklidir `DeadLetterQueue`.`Custom` seçilir.  
  
#### <a name="poison-message-handling-properties"></a>Zehirli ileti işleme özellikleri  
 Hizmet bir işlem altında hedef kuyruktan iletileri okuduğunda hizmet çeşitli nedenlerle iletiyi işlemek başarısız olabilir. İleti geri yeniden okumaya sıraya konur. Sürekli olarak, bir dizi poison ileti işleme başarısız iletilerle dağıtılacak bağlamasında özellikleri yapılandırılabilir. Dört özellikleri vardır: `ReceiveRetryCount`, `MaxRetryCycles`, `RetryCycleDelay`, ve `ReceiveErrorHandling`. Bu özellikler hakkında daha fazla bilgi için bkz: [zehirli ileti işleme](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
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
 `MsmqIntegrationBinding` C, C++, COM veya System.Messaging API'leri ile yazılmış varolan bir MSMQ uygulamasıyla iletişim kurmak için bir WCF uç noktası istediğinizde kullanılır.  
  
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
