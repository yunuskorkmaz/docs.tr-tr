---
title: WCF'de Kuyruğa Alma
ms.date: 03/30/2017
ms.assetid: e98d76ba-1acf-42cd-b137-0f8214661112
ms.openlocfilehash: 27c92b0f728b909de16a059485a38ff7fb0fb765
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913385"
---
# <a name="queuing-in-wcf"></a>WCF'de Kuyruğa Alma
Bu bölümde Windows Communication Foundation (WCF) ' de sıraya alınmış iletişimin nasıl kullanılacağı açıklanmaktadır.  
  
## <a name="queues-as-a-wcf-transport-binding"></a>WCF Aktarım bağlaması olarak kuyruklar  
 WCF 'de, sözleşmelerin ne değiştirildiğini belirtir. Sözleşmeler, işe bağımlı veya uygulamaya özel ileti değişimlerdir. Bağlamalarda ileti alışverişi yapmak için kullanılan mekanizma (veya "nasıl") belirtilir. WCF 'deki bağlamalar ileti değişimi ayrıntılarını kapsüller. Bu kişiler, kullanıcının taşımanın çeşitli yönlerini veya bağlamaların temsil ettiği Protokolü denetlemesini sağlamak için yapılandırma alt 'lerini kullanıma sunar. WCF 'de kuyruğa alma, birçok sıraya alma uygulaması için büyük bir avantaj olan diğer tüm aktarım bağlamaları gibi davranır. Günümüzde, birçok sıraya alma uygulaması diğer uzak yordam çağrısı (RPC) stili dağıtılan uygulamalardan farklı şekilde yazılmıştır, bu da izlemenizi ve bakımını zorlaştırır. WCF ile, dağıtılmış bir uygulama yazma stili çok aynıdır, daha kolay bir şekilde izlenmesini ve bakımını yapmayı kolaylaştırır. Üstelik, Exchange mekanizmasını iş mantığından ayrı olarak düzenleme, bu da aktarımı yapılandırmak veya uygulamaya özel kodu etkilemeden değişiklikler yapmak kolaydır. Aşağıdaki şekilde, bir WCF hizmeti ve bir istemcinin bir aktarım olarak MSMQ kullanan bir yapısı gösterilmektedir.  
  
 ![Kuyruğa alınmış uygulama diyagramı](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Dağıtılmış kuyruk-şekil")  
  
 Yukarıdaki şekilde görebileceğiniz gibi, istemci ve hizmet yalnızca uygulama semantiğini, yani, sözleşme ve uygulamayı tanımlamalıdır. Hizmet, tercih edilen ayarlarla sıraya alınmış bir bağlamayı yapılandırır. İstemci, hizmete bir WCF istemcisi oluşturmak ve hizmete ileti göndermek için kullanılacak bağlamaları açıklayan bir yapılandırma dosyası oluşturmak üzere [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kullanır. Bu nedenle, sıraya alınmış bir ileti göndermek için istemci bir WCF istemcisi başlatır ve üzerinde bir işlem çağırır. Bu, iletinin iletim kuyruğuna gönderilmesini ve hedef sıraya aktarılmasını sağlar. Sıraya alınan iletişimin tüm karmaşıklıkları, ileti gönderen ve alan uygulamadan gizlenir.  
  
 WCF 'de sıraya alınan bağlama hakkında uyarılar şunlardır:  
  
- WCF 'deki varsayılan sıraya alınmış bağlama kuyrukları kullanarak çift yönlü iletişimi desteklemediğinden tüm hizmet işlemleri tek yönlü olmalıdır. İki yönlü iletişim örneği ([Iki yönlü iletişim](../../../../docs/framework/wcf/samples/two-way-communication.md)) kuyrukları kullanarak çift yönlü iletişimi uygulamak için 2 1 yönlü sözleşmeleri nasıl kullanacağınızı gösterir.  
  
- Meta veri değişimi kullanan bir WCF istemcisi oluşturmak için, hizmette ek bir HTTP uç noktası gerekir, böylece doğrudan WCF istemcisini oluşturacak şekilde sorgulanabilir ve kuyruğa alınmış iletişimi uygun şekilde yapılandırmak için bağlama bilgilerini elde edebilirsiniz.  
  
- Sıraya alınan bağlamaya bağlı olarak, WCF dışında ek yapılandırma gerekir. Örneğin, <xref:System.ServiceModel.NetMsmqBinding> WCF ile birlikte gelen sınıf, bağlamaları yapılandırmanızı ve Message Queuing (MSMQ) en az yapılandırmayı gerektirir.  
  
 Aşağıdaki bölümlerde, MSMQ 'YU temel alan WCF ile birlikte gönderilen belirli sıraya alınmış bağlamalar açıklanır.  
  
### <a name="msmq"></a>MSMQ  
 WCF 'deki sıraya alınan aktarım, kuyruğa alınmış iletişimi için MSMQ kullanır.  
  
 MSMQ, Windows ile isteğe bağlı bir bileşen olarak gelir ve NT hizmeti olarak çalışır. İletim kuyruğuna iletim ve hedef sırada teslim için iletileri yakalar. MSMQ kuyruğu yöneticileri, iletilerin iletimde kaybedilmemesi için güvenilir bir ileti aktarımı Protokolü uygular. Protokol yerel veya SOAP tabanlı olabilir; örneğin SOAP güvenilir Ileti Protokolü (SRMP).  
  
 MSMQ 'da kuyruklar işlem veya işlem dışı olabilir. İşlemsel bir kuyruk, iletilerin bir işlem halinde yakalanıp teslim edilmesini ve sonra kuyrukta durda depolanmasını sağlar. İşlem kuyruğuna gönderilen iletiler, sırayla tam olarak bir kez aktarılır. Geçici ve dayanıklı iletileri göndermek için işlemsel olmayan bir kuyruk kullanabilirsiniz. İşlemsel olmayan bir sıraya gönderilen ileti, güvenilir aktarım kesintileri gerçekleştirmez; Bu nedenle iletiler kaybolabilir.  
  
 MSMQ kuyrukları, Active Directory dizin hizmetiyle kaydedilmiş bir Windows kimliği kullanılarak da güvenli hale getirilir. MSMQ yüklenirken, bilgisayarın bir Windows etki alanı ağının parçası olmasını gerektiren Active Directory tümleştirme yükleyebilirsiniz.  
  
 MSMQ hakkında daha fazla bilgi için bkz. [yükleme Message Queuing (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md).  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 NetMsmqBinding >, MSMQ kullanarak iletişim kurmak üzere iki WCF uç noktası için sağlanan sıraya alınmış bağlama WCF 'dir. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) Bu nedenle, bağlama, MSMQ 'ya özgü özellikleri gösterir. Ancak, tüm MSMQ özellikleri ve özellikleri içinde `NetMsmqBinding`gösterilmez. Compact `NetMsmqBinding` , çoğu müşterinin yeterince bulması gereken en uygun özellikler kümesiyle tasarlanmıştır.  
  
 , `NetMsmqBinding` Ana sıraya alınan temel sıraya alma kavramlarını, bu nedenle bağlamalardaki Özellikler biçiminde bildirimler. Bu özellikler sırasıyla MSMQ ile iletişim kurar ve iletileri nasıl aktaracağınızla iletişim kurabilir. Özellik kategorilerinin bir tartışması aşağıdaki bölümlerde verilmiştir. Daha fazla bilgi için, belirli özellikleri daha tamamen tanımlayan kavramsal konulara bakın.  
  
#### <a name="exactlyonce-and-durable-properties"></a>ExactlyOnce ve dayanıklı Özellikler  
 `ExactlyOnce` Ve`Durable` özellikleri, iletilerin kuyruklar arasında nasıl aktarılacağını etkiler:  
  
- `ExactlyOnce`: (Varsayılan) `true` olarak ayarlandığında, kuyruğa alınan kanal, teslim edildiğinde iletinin yinelenmemesini sağlar. Ayrıca iletinin kaybolmamasını de sağlar. İleti teslim edilemez veya ileti teslim edilmeden önce iletinin yaşam süresi dolarsa, teslim hatası nedeni ile birlikte başarısız ileti teslim edilemeyen bir sıraya kaydedilir. Olarak `false`ayarlandığında, kuyruğa alınan kanal iletiyi aktarma çabaları yapar. Bu durumda, isteğe bağlı olarak bir atılacak ileti sırası seçebilirsiniz.  
  
- `Durable:`(Varsayılan) `true` olarak ayarlandığında, sıraya alınan kanal MSMQ 'nun iletiyi diskte durda depoladığını sağlar. Bu nedenle, MSMQ hizmeti durdurulup yeniden başlatıldığında, diskteki iletiler hedef sıraya aktarılır veya hizmete teslim edilir. Olarak `false`ayarlandığında, iletiler geçici depoda depolanır ve MSMQ hizmetini durdurup yeniden başlatırken kaybedilir.  
  
 Güvenilir `ExactlyOnce` aktarım için, MSMQ kuyruğun işlem olmasını gerektirir. Ayrıca, MSMQ, işlem sırasından okumak için bir işlem gerektirir. Bu şekilde kullandığınızda `NetMsmqBinding`, olarak ayarlandığında `ExactlyOnce` `true`ileti göndermek veya almak için bir işlem gerektiğini unutmayın. Benzer şekilde, MSMQ, ne zaman `ExactlyOnce` ve geçici mesajlaşma için olduğu `false` gibi en iyi çaba kesintileri için kuyruğun işlem dışı olmasını gerektirir. Bu nedenle, `false` veya `ExactlyOnce` dayanıklı `false`olarak ayarlandığında, işlem kullanarak gönderilemez veya alamazsınız.  
  
> [!NOTE]
> Bağlamalardaki ayarlara bağlı olarak doğru sıranın (işlem veya işlem olmayan) oluşturulduğundan emin olun. `ExactlyOnce` İse`true`, bir işlem kuyruğu kullanın; Aksi takdirde, işlemsel olmayan bir kuyruk kullanın.  
  
#### <a name="dead-letter-queue-properties"></a>Atılacak ileti sırası özellikleri  
 Teslim edilemeyen iletileri depolamak için atılacak mektup kuyruğu kullanılır. Kullanıcı, iletileri atılacak ileti sırasından okuyan telafi mantığını yazabilir.  
  
 Birçok sıraya alma sistemi, sistem genelinde atılacak bir sıra için sağlanır. MSMQ, işlemsel olmayan sıralara teslim edilemeyen iletiler için sistem genelinde, işlem dışı bir atılacak ileti sırası ve işlem sıralarına teslim edilemeyen iletiler için sistem genelinde bir işlem atılacak mektup sırası sağlar.  
  
 Farklı hedef sıralara ileti gönderen birden çok istemci MSMQ hizmetini paylaşıyorsa, istemciler tarafından gönderilen tüm iletiler aynı atılacak ileti kuyruğuna gider. Bu her zaman tercih edilmez. ' Deki [!INCLUDE[wv](../../../../includes/wv-md.md)] WCF ve MSMQ, daha iyi yalıtım için kullanıcının teslim edilemeyen iletileri depolamak üzere belirtmesi için özel bir atılacak mektup kuyruğu (veya uygulamaya özel atılacak ileti sırası) sağlar. Bu nedenle, farklı istemciler aynı atılacak ileti sırasını paylaşmaz.  
  
 Bağlama, ilgilendiğiniz iki özelliğe sahiptir:  
  
- `DeadLetterQueue`: Bu özellik, atılacak bir sıra istenip istenmediğini belirten bir numaralandırmadır. Sabit Listesi istenirse, atılacak ileti sırası türünü de içerir. Değerleri `None`, `System`, ve `Custom`. Bu özelliklerin yorumu hakkında daha fazla bilgi için bkz. [Ileti aktarımı başarısızlıklarını işlemek Için atılacak Ileti kuyruklarını kullanma](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
  
- `CustomDeadLetterQueue`: Bu özellik, uygulamaya özel atılacak mektup sırasının Tekdüzen Kaynak tanımlayıcısı (URI) adresidir. Bu gereklidir `DeadLetterQueue`.`Custom` seçilir.  
  
#### <a name="poison-message-handling-properties"></a>Zarar Iletisi Işleme özellikleri  
 Hizmet bir işlem altındaki hedef sıradan iletileri okuduğunda, hizmet çeşitli nedenlerle iletiyi işleyemeyebilir. İleti daha sonra tekrar okumak üzere kuyruğa geri konur. Sürekli başarısız olan iletilerle uğraşmak için, bağlamada bir Poison-Message işleme özelliği yapılandırılabilir. `ReceiveRetryCount`Dört özellik vardır: `MaxRetryCycles` `RetryCycleDelay`,,, ve. `ReceiveErrorHandling` Bu özellikler hakkında daha fazla bilgi için bkz. [zehirli Ileti işleme](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
#### <a name="security-properties"></a>Güvenlik özellikleri  
 MSMQ, bir kuyruktaki erişim denetim listeleri (ACL 'Ler) veya kimliği doğrulanmış iletiler gönderme gibi kendi güvenlik modelini kullanıma sunar. , `NetMsmqBinding` Bu güvenlik özelliklerini taşıma güvenlik ayarlarının bir parçası olarak kullanıma sunar. Aktarım güvenliği için bağlamada iki özellik vardır: `MsmqAuthenticationMode` ve. `MsmqProtectionLevel` Bu özelliklerdeki ayarlar MSMQ 'nun nasıl yapılandırıldığına bağlıdır. Daha fazla bilgi için bkz. [Aktarım güvenliğini kullanarak Iletileri güvenli hale getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
 Aktarım güvenliğine ek olarak, gerçek SOAP iletisinin kendisi de ileti güvenliği kullanılarak güvenliği sağlanmış olabilir. Daha fazla bilgi için bkz. [Ileti güvenliği kullanarak Iletileri güvenli hale getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md).  
  
 `MsmqTransportSecurity`Ayrıca iki özelliği `MsmqEncryptionAlgorithm` `MsmqHashAlgorithm`de kullanıma sunar. Bunlar, iletilerin sıraya göre aktarım şifrelemesini ve imzaların karmasını seçmek için farklı algoritmaların numaralandırmalardır.  
  
#### <a name="other-properties"></a>Diğer özellikler  
 Önceki özelliklere ek olarak, bağlamada kullanıma sunulan diğer MSMQ 'ya özgü özellikler şunlardır:  
  
- `UseSourceJournal`: Kaynak günlüğünün açık olduğunu belirten bir özellik. Kaynak günlük kaydı, iletim sırasından başarıyla iletilmiş iletileri izlemeye devam eden bir MSMQ özelliğidir.  
  
- `UseMsmqTracing`: MSMQ izlemenin açık olduğunu belirten bir özellik. MSMQ izleme, bir ileti MSMQ kuyruğu Yöneticisi barındıran bir makineye ayrıldığında veya ulaştığında rapor kuyruğuna rapor iletileri gönderir.  
  
- `QueueTransferProtocol`: Kuyruk-kuyruk ileti aktarımları için kullanılacak protokol numaralandırması. MSMQ, yerel bir kuyruk-sıraya Aktarım Protokolü ve SOAP Güvenilir Mesajlaşma Protokolü (SRMP) adlı SOAP tabanlı bir protokol uygular. Queuequeue aktarımları için HTTP taşıması kullanılırken SRMP kullanılır. , Kuyruk-kuyruk aktarımları için HTTPS kullanılırken SRMP güvenli kullanılır.  
  
- `UseActiveDirectory`: Sıra adresi çözümlemesi için Active Directory kullanılması gerekip gerekmediğini belirten bir Boole değeri. Bu, varsayılan olarak kapalıdır. Daha fazla bilgi için bkz. [hizmet uç noktaları ve sıra adresleme](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 , Bir WCF uç noktasının C, C++, com veya System. Messaging API 'lerinde yazılmış mevcut bir MSMQ uygulamasıyla iletişim kurmasını istediğinizde kullanılır. `MsmqIntegrationBinding`  
  
 Bağlama özellikleri, ile `NetMsmqBinding`aynıdır. Ancak, aşağıdaki farklar geçerlidir:  
  
- İçin `MsmqIntegrationBinding` işlem sözleşmesinin, tür parametresinin gövde türü olduğu tek bir parametre türünde <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> alınması kısıtlıdır.  
  
- MSMQ yerel ileti özelliklerinin çoğu kullanım <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> için ' de kullanıma sunulur.  
  
- İleti gövdesinin serileştirilmesi ve serisini kaldırma konusunda yardımcı olmak için, XML ve ActiveX gibi serileştiriciler sağlanır.  
  
### <a name="sample-code"></a>Örnek Kod  
 MSMQ kullanan WCF hizmetleri yazma hakkında adım adım yönergeler için aşağıdaki konulara bakın:  
  
- [Nasıl yapılır: WCF uç noktaları ve Message Queuing uygulamalarla Exchange Iletileri](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
  
- [Nasıl yapılır: WCF uç noktaları ile sıraya alınan Iletileri değiştirme](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
  
 WCF 'de MSMQ kullanımını gösteren tamamlanmış bir kod örneği için aşağıdaki konulara bakın:  
  
- [İşlem Gerçekleştirilmiş MSMQ Bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
  
- [Geçici Kuyruğa Alınmış İletişim](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
  
- [Teslim Edilemeyen İletiler Sırası](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
  
- [Oturumlar ve Kuyruklar](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
  
- [Çift Yönlü İletişim](../../../../docs/framework/wcf/samples/two-way-communication.md) 
  
- [SRMP](../../../../docs/framework/wcf/samples/srmp.md)  
  
- [Message Queuing Üzerinden İleti Güvenliği](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet Uç Noktaları ve Kuyruk İşleme](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)
- [Kuyruğa Alınan Bir Uygulamayı Web'de Barındırma](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
