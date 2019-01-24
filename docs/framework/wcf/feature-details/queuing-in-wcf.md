---
title: WCF'de Kuyruğa Alma
ms.date: 03/30/2017
ms.assetid: e98d76ba-1acf-42cd-b137-0f8214661112
ms.openlocfilehash: fcdd38cf02157829bdc476cc289ea89ff8767487
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559478"
---
# <a name="queuing-in-wcf"></a>WCF'de Kuyruğa Alma
Bu bölümde, Windows Communication Foundation (WCF) kuyruğa alınan iletişim kullanmayı açıklar.  
  
## <a name="queues-as-a-wcf-transport-binding"></a>Bağlama sırası olarak bir WCF aktarma  
 WCF'de, anlaşmalar ne değiştirilen belirtin. Sözleşmelerin iş bağımlı veya uygulamaya özel ileti alışverişlerinde durumda. İleti değişimi için kullanılan mekanizma (veya "nasıl") bağlamalar belirtildi. WCF bağlamaları ileti alışverişi ayrıntılarını kapsüller. Bunlar, yapılandırma düğmelerini taşıma veya bağlamaları temsil Protokolü çeşitli yönlerini denetlemek kullanıcı için ortaya çıkarır. WCF'de kuyruğa alma, çok sayıda kuyruğa alma uygulamaları için büyük bir avantaj herhangi diğer aktarım bağlama gibi değerlendirilir. Günümüzde, çok sayıda kuyruğa alma uygulamaları diğer uzak yordam çağrısı (RPC) farklı yazılır-style dağıtılmış uygulamalar, izleyin ve korumak daha zor hale getirme. WCF ile dağıtılmış bir uygulama yazma stili çok, izleyin ve bakımını kolaylaştırır aynıdır. Ayrıca, iş mantığı ayrı olarak Exchange'den mekanizmasını kullanıma hesaba katarak tarafından taşıma yapılandırmak veya özel uygulama kodunu etkilemeden değişiklik yapmak daha kolay olur. Aşağıdaki şekilde, bir WCF hizmeti ve istemci aktarım olarak MSMQ kullanarak yapısı gösterilmektedir.  
  
 ![Uygulama diyagramı kuyruğa](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "dağıtılmış-kuyruk-Şekil")  
  
 Önceki şekilden görebileceğiniz gibi istemci ve hizmet, yalnızca uygulama semantiği, diğer bir deyişle, sözleşme ve uygulama tanımlamanız gerekir. Hizmet, kuyruğa alınmış bir bağlama ile tercih edilen ayarları yapılandırır. İstemcinin kullandığı [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmetine bir WCF istemcisi oluşturma ve hizmete ileti göndermek için kullanılacak bağlamaları tanımlayan bir yapılandırma dosyası oluşturmak için. Bu nedenle, kuyruğa alınmış ileti göndermek için istemci bir WCF istemcisi oluşturur ve bir işlem başlatır. Bu iletinin iletimini kuyruğa gönderilen ve hedef kuyruğa aktarılan neden olur. Kuyruğa alınan iletişim karmaşıklığını ileti gönderme ve alma uygulamaya ait gizli.  
  
 Wcf'de kuyruğa alınmış bağlama hakkında uyarılar şunlardır:  
  
-   Varsayılan bağlama WCF'de kuyruğa alınan işlemler tek yönlü olması gerekir, çünkü tüm servis kuyruklarını kullanarak çift yönlü iletişimi desteklemez. İki yönlü iletişim örnek ([iki yönlü iletişimi](../../../../docs/framework/wcf/samples/two-way-communication.md)) kuyruklarını kullanarak çift yönlü iletişim uygulamak için iki yönlü sözleşmeler kullanılması gösterilmektedir.  
  
-   Bir WCF oluşturmak için WCF istemcisi oluşturma ve kuyruğa alınan iletişim uygun şekilde yapılandırmak için bağlama bilgilerini elde etmek için doğrudan sorgulanabilir böylece meta veri değişimi kullanarak istemci hizmeti hakkında ek bir HTTP uç noktası gerektirir.  
  
-   Üzerinde sıraya alınan bağlama bağlı olarak, WCF dışında ek bir yapılandırma gereklidir. Örneğin, <xref:System.ServiceModel.NetMsmqBinding> WCF ile birlikte gelen sınıfı yanı sıra bağlamalarını yapılandırmak için en düşük düzeyde Message Queuing (MSMQ) yapılandırma gerektirir.  
  
 Aşağıdaki bölümlerde, MSMQ üzerinde temel WCF ile birlikte gelen belirli sıraya alınan bağlamaları açıklanmaktadır.  
  
### <a name="msmq"></a>MSMQ  
 Wcf'de kuyruğa alınmış taşıma, kuyruğa alınan iletişim için MSMQ kullanır.  
  
 MSMQ Windows ile isteğe bağlı bir bileşen olarak gelir ve bir NT hizmeti olarak çalışır. Bu ileti hedef sıra teslimi ve iletim sırasındaki iletim için yakalar. Böylece iletiler iletim kaybolmaz MSMQ sırası yöneticilerini güvenilir ileti aktarım protokolü kullanır. Protokol, yerel ya da SOAP tabanlı gibi SOAP Güvenilir İletisi Protokolü (SRMP) olabilir.  
  
 MSMQ, işlem ya da işlem olmayan sıralar olabilir. Bir işlem sırası, yakalanan ve teslim işlem ve büyük bir kuyrukta depolanan iletilerine izin verir. İşlem kuyruğa gönderilen iletilerin tam bir kez sırayla aktarılır. Hem geçici hem de dayanıklı ileti göndermek için işlemsel olmayan bir kuyruk kullanabilirsiniz. Bir işlem olmayan kuyruğuna gönderilen ileti, herhangi bir Güvenilir Aktarım Güvenceleri içermez; Bu nedenle, iletileri kaybolmuş olabilir.  
  
 MSMQ kuyruk aynı zamanda Active Directory dizin hizmetine kayıtlı bir Windows kimliği kullanılarak güvenli hale getirilebilir. MSMQ yüklerken, Active Directory Tümleştirmesi, bilgisayarın Windows etki alanı ağın parçası olmasını gerektiren yükleyebilirsiniz.  
  
 MSMQ hakkında daha fazla bilgi için bkz: [yükleme Message Queuing (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md).  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 [ \<NetMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) WCF sağlar MSMQ kullanarak iletişim kurmak iki WCF uç noktaları için sıraya alınan bağlamadır. Bağlama, bu nedenle, MSMQ için belirli özellikleri sunar. Ancak, tüm MSMQ özellikleri ve özellikleri sunulan `NetMsmqBinding`. Sıkıştırma `NetMsmqBinding` en uygun müşterilerin çoğu yeterli bulmalısınız özellikler kümesini ile tasarlanmıştır.  
  
 `NetMsmqBinding` Şimdiye kadarki özellikleri biçiminde bağlamalarda ele sıraya alma kavramları bildirimleri. Bu özellikler için MSMQ sırayla aktarmak ve iletileri ulaştırmak nasıl iletişim kurar. Aşağıdaki bölümlerde özellik kategorileri hakkında ayrıntılı bilgi var. Daha fazla bilgi için daha eksiksiz özgü özellikleri açıklayan kavramsal konulara bakın.  
  
#### <a name="exactlyonce-and-durable-properties"></a>ExactlyOnce ve dayanıklı özellikleri  
 `ExactlyOnce` Ve `Durable` özellikler, ileti kuyrukları arasında nasıl aktarıldığı etkiler:  
  
-   `ExactlyOnce`: Ayarlandığında `true` (varsayılan), ileti teslim ise değil yineleniyor, kuyruğa alınmış kanal sağlar. Ayrıca, ileti kaybolmaz sağlar. İleti teslim ya da ileti yaşam süresi için ileti teslim önce sona edilemeyen kuyrukta başarısız iletinin teslim hatanın nedenini birlikte kaydedilir. Ayarlandığında `false`, kuyruğa alınmış kanal ileti aktarım için çaba yapar. Bu durumda, eski ileti sırası isteğe bağlı olarak seçebilirsiniz.  
  
-   `Durable:` Ayarlandığında `true` (varsayılan), MSMQ İleti arızaya diskte depolar, kuyruğa alınmış kanal sağlar. Bu nedenle, MSMQ hizmeti durdurun ve yeniden başlatmak için olsaydı, iletileri disk için hedef sıra aktarılan veya hizmete teslim. Ayarlandığında `false`, iletileri geçici deposunda depolanır ve MSMQ hizmeti durdurup yeniden üzerinde kaybolur.  
  
 İçin `ExactlyOnce` Güvenilir Aktarım MSMQ kuyruk işlem gerektirir. Ayrıca, MSMQ işlem kuyruktan okunmak üzere bir işlem gerektirir. Bu nedenle, kullandığınız zaman `NetMsmqBinding`, unutmayın iletileri ne zaman gönderileceği ve alınacağı bir işlem gereklidir `ExactlyOnce` ayarlanır `true`. Benzer şekilde, MSMQ kuyruk ne zaman gibi en yüksek çaba Güvenceleri için işlem olmayan gerektirir `ExactlyOnce` olduğu `false` ve volatile Mesajlaşma için. Bu nedenle, ayarlarken `ExactlyOnce` için `false` veya için dayanıklı `false`, gönderdiğiniz veya bir işlem kullanarak alırsınız.  
  
> [!NOTE]
>  Doğru bir sıra (işlem veya işlem olmayan) bağlamaları ayarlarında temel alınarak oluşturulduğundan emin olun. Varsa `ExactlyOnce` olduğu `true`, işlem sırasını kullanın; Aksi takdirde, işlemsel olmayan bir kuyruk kullanın.  
  
#### <a name="dead-letter-queue-properties"></a>Eski ileti sırası özellikleri  
 Eski ileti sırası teslim başarısız iletileri depolamak için kullanılır. Kullanıcı eski ileti sırası iletileri okuyan telafi mantığı yazabilirsiniz.  
  
 Sistem genelinde eski ileti sırası için birçok queuing sistemi sağlar. Bir sistem genelinde işlem olmayan eski ileti sırası işlem olmayan sıralara teslim başarısız iletiler için ve bir sistem genelinde işlem eski ileti sırası işleme uygun sıralarda teslim başarısız iletiler için MSMQ sağlar.  
  
 Birden çok istemci farklı bir hedef sıralara ileti göndermek için MSMQ hizmeti paylaşıyorsanız, istemciler tarafından gönderilen tüm iletiler için aynı eski ileti sırası gidin. Bu her zaman tercih değildir. Daha iyi yalıtım, WCF ve MSMQ [!INCLUDE[wv](../../../../includes/wv-md.md)] özel eski ileti sırası (veya uygulamaya özgü eski ileti sırası) sağlayan kullanıcı teslim başarısız iletileri depolamak için belirtebilirsiniz. Bu nedenle, farklı istemciler aynı eski ileti sırası paylaşmayın.  
  
 Bağlama, ilgilenilen iki özelliğe sahiptir:  
  
-   `DeadLetterQueue`: Bu özellik eski ileti sırası istemediğini gösteren bir sabit listesidir. Bir istenirse numaralandırma eski ileti sırası türünü de içerir. Değerler `None`, `System`, ve `Custom`. Bu özelliklerin yorumlama hakkında daha fazla bilgi için bkz. [ileti aktarımı hatalarını işlemek için teslim edilemeyen kuyrukları kullanma](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
  
-   `CustomDeadLetterQueue`: Bu özellik uygulamaya özgü eski ileti sırası Tekdüzen Kaynak Tanımlayıcısı (URI) adresidir. Bu gerekli ise `DeadLetterQueue`.`Custom` seçilir.  
  
#### <a name="poison-message-handling-properties"></a>Zehirli ileti işleme özellikleri  
 Hizmet, bir işlem altında hedef kuyruktan iletileri okuduğunda, hizmet çeşitli nedenlerle iletiyi işlemek başarısız olabilir. İleti geri yeniden okumak için sıraya konur. Bir dizi poison ileti işleme tekrar tekrar başarısız iletileri ile dağıtılacak bağlama özellikleri yapılandırılabilir. Dört özellik vardır: `ReceiveRetryCount`, `MaxRetryCycles`, `RetryCycleDelay`, ve `ReceiveErrorHandling`. Bu özellikler hakkında daha fazla bilgi için bkz. [zehirli ileti işleme](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
#### <a name="security-properties"></a>Güvenlik özellikleri  
 Erişim denetim listeleri (ACL'ler) gibi MSMQ kendi güvenlik modeli, bir kuyruğa kullanıma sunar. veya kimliği doğrulanmış iletiler gönderme. `NetMsmqBinding` Taşıma güvenlik ayarlarını bir parçası olarak bu güvenlik özellikleri sunar. Aktarım güvenliği'ni bağlamasında iki özellik vardır: `MsmqAuthenticationMode` ve `MsmqProtectionLevel`. Bu özellikleri'ndeki ayarlar, MSMQ nasıl yapılandırıldığına bağlıdır. Daha fazla bilgi için [aktarım güvenliği kullanarak iletileri güvenli hale getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
 Aktarım güvenliği yanı sıra gerçek SOAP iletisi kendisi ileti güvenliği kullanılarak güvenli hale getirilebilir. Daha fazla bilgi için [ileti Güveliği kullanarak iletileri güvenli hale getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md).  
  
 `MsmqTransportSecurity` Ayrıca iki özellik sunan `MsmqEncryptionAlgorithm` ve `MsmqHashAlgorithm`. Bu, sabit listeleri için ileti kuyruğu kuyruk aktarım şifreleme ve imzalarını karma seçmek için farklı algoritma vardır.  
  
#### <a name="other-properties"></a>Diğer özellikler  
 Önceki özelliklerine ek olarak, bağlama Ekle kullanıma sunulan diğer MSMQ özgü özellikler:  
  
-   `UseSourceJournal`: Bu kaynak günlük kaydı belirtmek için bir özelliği etkinleştirilir. Kaynak günlük kaydı başarıyla iletim sırasından gönderilen iletileri izlemek bir MSMQ özelliğidir.  
  
-   `UseMsmqTracing`: MSMQ izleme açık olduğunu belirtmek için bir özellik. MSMQ izleme, bir rapor kuyruğa bir ileti ayrıldığında ya da bir MSMQ Kuyruk Yöneticisi'ni barındıran bir makinenin ulaşan her zaman rapor iletileri gönderir.  
  
-   `QueueTransferProtocol`: Kuyruk kuyruk iletisi aktarımlar için kullanılacak protokolü numaralandırması. MSMQ yerel kuyruk sırası Aktarım Protokolü ve SOAP Güvenilir Mesajlaşma Protokolü (SRMP) adlı bir SOAP tabanlı Protokolü uygular. Kuyruk sırası aktarımları için HTTP aktarımı kullanarak SRMP kullanılır. Kuyruk sırası aktarımları için HTTPS kullanan güvenli SRMP kullanılır.  
  
-   `UseActiveDirectory`: Active Directory kuyruk adres çözümlemesi için kullanılıp kullanılmayacağını belirten bir Boole değeri. Varsayılan olarak, bu kapalıdır. Daha fazla bilgi için [hizmet uç noktaları ve kuyruk işleme](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 `MsmqIntegrationBinding` C, C++, COM veya System.Messaging API'leri ile yazılmış mevcut bir MSMQ uygulamasıyla iletişim kurmak için WCF uç noktasını istediğinizde kullanılır.  
  
 Bağlama özellikleri aynıdır `NetMsmqBinding`. Ancak, aşağıdaki farklar geçerlidir:  
  
-   İşlem anlaşması için `MsmqIntegrationBinding` türünde tek bir parametre almak için kısıtlı <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> gövde türü olduğu tür parametresi.  
  
-   MSMQ yerel ileti özelliklerinin çoğunu içinde sunulur <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> kullanmak için.  
  
-   Serileştirme ve seri durumundan çıkarma ileti gövdesi ile yardımcı olmak için seri hale getiricileri genişletme XML ve ActiveX gibi sağlanır.  
  
### <a name="sample-code"></a>Örnek Kod  
 WCF yazmaya yönelik adım adım yönergeler için MSMQ kullanan hizmetler aşağıdaki konulara bakın:  
  
-   [Nasıl yapılır: WCF uç noktaları ve ileti uygulamaları ile Exchange ileti](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
  
-   [Nasıl yapılır: WCF uç noktaları ile kuyruğa alınmış iletiler gönderip alır](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
  
 Wcf'de MSMQ kullanımını gösteren tamamlanmış kod örneği için aşağıdaki konulara bakın:  
  
-   [İşlem Gerçekleştirilmiş MSMQ Bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
  
-   [Geçici Kuyruğa Alınmış İletişim](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
  
-   [Teslim Edilemeyen İletiler Sırası](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
  
-   [Oturumlar ve Kuyruklar](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
  
-   [Çift Yönlü İletişim](../../../../docs/framework/wcf/samples/two-way-communication.md) 
  
-   [SRMP](../../../../docs/framework/wcf/samples/srmp.md)  
  
-   [Message Queuing Üzerinden İleti Güvenliği](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hizmet Uç Noktaları ve Kuyruk İşleme](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)
- [Kuyruğa Alınan Bir Uygulamayı Web'de Barındırma](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
