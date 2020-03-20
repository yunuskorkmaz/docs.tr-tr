---
title: WCF'de Kuyruğa Alma
ms.date: 03/30/2017
ms.assetid: e98d76ba-1acf-42cd-b137-0f8214661112
ms.openlocfilehash: e6608a3d556b546660be904eb8c853243e833d2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184557"
---
# <a name="queuing-in-wcf"></a>WCF'de Kuyruğa Alma
Bu bölümde, Windows Communication Foundation 'da (WCF) sıraya girilen iletişimin nasıl kullanılacağı açıklanmaktadır.  
  
## <a name="queues-as-a-wcf-transport-binding"></a>WCF aktarım bağlama olarak kuyruklar  
 WCF'de, sözleşmeler nelerin değiş tokuş edildiğini belirtir. Sözleşmeler, işletmeye bağlı veya uygulamaya özgü ileti alışverişidir. İleti alışverişinde kullanılan mekanizma (veya "nasıl") bağlamalarda belirtilir. WCF'deki ciltler ileti alışverişinin ayrıntılarını kapsüller. Kullanıcının aktarımın veya bağlamaların temsil ettiği protokolün çeşitli yönlerini denetlemesi için yapılandırma düğümlerini ortaya çıkarırlar. WCF'de kuyruk, birçok kuyruk uygulaması için büyük bir avantaj olan diğer aktarım bağlama gibi ele alınarak işlem yapılır. Günümüzde, birçok kuyruk uygulaması diğer uzak yordam çağrısı (RPC) tarzı dağıtılmış uygulamalardan farklı olarak yazılır ve bu da takip etmeyi ve bakımını zorlaştırır. WCF ile dağıtılmış bir uygulama yazma stili çok aynıdır, bu da takip etmeyi ve bakımını kolaylaştırır. Ayrıca, değişim mekanizmasını iş mantığından ayrı olarak hesaba katarak, taşımayı yapılandırmak veya uygulamaya özel kodu etkilemeden değişiklik yapmak daha kolaydır. Aşağıdaki şekil, msmq'yi aktarım olarak kullanan bir WCF hizmetinin ve istemcinin yapısını göstermektedir.  
  
 ![Sıralı Uygulama Diyagramı](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Dağıtılmış Sıra-Şekil")  
  
 Bir önceki şekilde de görebileceğiniz gibi, istemci ve hizmet yalnızca uygulama semantiklerini, yani sözleşmeyi ve uygulamayı tanımlamalıdır. Hizmet, tercih edilen ayarlarla sıralı bir bağlamayı yapılandırır. İstemci [ServiceModel Metadata Utility Tool 'u (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmete bir WCF istemcisi oluşturmak ve hizmete ileti göndermek için kullanılacak bağlamaları açıklayan bir yapılandırma dosyası oluşturmak için kullanır. Böylece, sıraya alınan bir ileti göndermek için istemci bir WCF istemcisini anında anında alır ve bu iletiye bir işlem çağırır. Bu, iletinin iletim kuyruğuna gönderilmesine ve hedef sıraya aktarılmasına neden olur. Sıralı iletişimin tüm karmaşıklığı, ileti gönderen ve alan uygulamadan gizlenir.  
  
 WCF'de sıraya alınma yla ilgili uyarılar şunlardır:  
  
- WCF'de varsayılan sıraya alınma sırası kuyrukları kullanarak çift yönlü iletişimi desteklemediği için tüm hizmet işlemleri tek yönlü olmalıdır. İki yönlü iletişim örneği[(İki Yönlü İletişim),](../../../../docs/framework/wcf/samples/two-way-communication.md)kuyrukları kullanarak çift yönlü iletişimi uygulamak için iki tek yönlü sözleşmenin nasıl kullanılacağını gösterir.  
  
- Meta veri alışverişini kullanarak bir WCF istemcisi oluşturmak için, wcf istemcisini oluşturmak ve sıraya alınan iletişimi uygun şekilde yapılandırmak için bağlayıcı bilgiler elde etmek için doğrudan sorgulanabilmesi için hizmette ek bir HTTP bitiş noktası gerekir.  
  
- Sıralanan bağlamaya bağlı olarak, WCF dışında ekstra yapılandırma gereklidir. Örneğin, WCF ile gönderilen <xref:System.ServiceModel.NetMsmqBinding> sınıf, bağlamaları yapılandırmanın yanı sıra Ileti Sıralamasını (MSMQ) en az yapılandırmanızı gerektirir.  
  
 Aşağıdaki bölümler, MsMQ'ya dayalı WCF ile gönderilen belirli sıralı bağlamaları açıklar.  
  
### <a name="msmq"></a>MSMQ  
 WCF'de sıralanmış aktarım, sıraya girilen iletişim için MSMQ kullanır.  
  
 MSMQ, Windows ile isteğe bağlı bir bileşen olarak çalışır ve NT hizmeti olarak çalışır. İleti, iletim kuyruğunda iletim ve hedef sırada teslim için iletileri yakalar. MSMQ sıra yöneticileri, iletilerin iletimde kaybolmaması için güvenilir bir ileti aktarım protokolü uygular. Protokol, SOAP Güvenilir İleti Protokolü (SRMP) gibi yerel veya SABUN tabanlı olabilir.  
  
 MSMQ'da kuyruklar işlemsel veya işlem dışı olabilir. İşlem sırası iletilerin bir işlemde yakalanmasını ve teslim edilmesini ve ardından kuyrukta uzun süre depolanabilir. Hareket kuyruğuna gönderilen iletiler sırayla tam olarak bir kez aktarılır. Hem geçici hem de dayanıklı iletiler göndermek için işlem dışı bir kuyruk kullanabilirsiniz. İşlem dışı bir kuyruğa gönderilen ileti güvenilir aktarım güvencesi taşımaz; böylece iletiler kaybolabilir.  
  
 MSMQ kuyrukları, Active Directory directory hizmetine kayıtlı bir Windows kimliği kullanılarak da güvenli hale alınabilir. MSMQ'yu yüklerken, bilgisayarın bir Windows etki alanı ağının parçası olmasını gerektiren Active Directory tümleştirmesini yükleyebilirsiniz.  
  
 MSMQ hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
  
### <a name="netmsmqbinding"></a>Netmsmqbinding  
 netMsmqBinding>, WCF'nin MSMQ kullanarak iletişim kurmak için iki WCF uç noktası sağladığı sıraya bağlı dır. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) Bu nedenle, bağlama, MSMQ'ya özgü özellikleri ortaya çıkarır. Ancak, tüm MSMQ özellikleri ve özellikleri. `NetMsmqBinding` Kompakt, `NetMsmqBinding` çoğu müşterinin yeterli bulması gereken en uygun özelliklerle tasarlanmıştır.  
  
 Şimdiye `NetMsmqBinding` kadar ciltler üzerinde özellikleri şeklinde tartışılan temel kuyruk kavramları tezahürleri. Bu özellikler, sırayla, iletilerin nasıl aktarılabildiğini ve iletilir gibi MSMQ'ya iletilir. Özellik kategorilerinin tartışılması aşağıdaki bölümlerde yer almaktadır. Daha fazla bilgi için, belirli özellikleri daha tam olarak açıklayan kavramsal konulara bakın.  
  
#### <a name="exactlyonce-and-durable-properties"></a>ExactlyOnce ve Dayanıklı Özellikleri  
 Ve `ExactlyOnce` `Durable` özellikleri, iletilerin sıralar arasında nasıl aktarıldığını etkiler:  
  
- `ExactlyOnce`: `true` (Varsayılan) olarak ayarlandığında, sıralanan kanal teslim edilirse iletinin yineleninmemesini sağlar. Ayrıca iletinin kaybolmamasını da sağlar. İleti teslim edilemiyorsa veya ileti teslim edilmeden önce Zaman-İkinci İletinin süresi doluyorsa, başarısız ileti nin yanı sıra teslim hatası nedeni ölü harf kuyruğuna kaydedilir. `false`Ayarlandığında, sıralanan kanal iletiyi aktarmak için çaba gösterir. Bu durumda, isteğe bağlı olarak ölü harf sırası seçebilirsiniz.  
  
- `Durable:``true` (Varsayılan) olarak ayarlandığında, sıralanan kanal MSMQ'nun iletiyi diskte uzun bir şekilde depolarmasını sağlar. Böylece, MSMQ hizmeti durdurulup yeniden başlatılırsa, diskteki iletiler hedef sıraya aktarılır veya hizmete teslim edilir. `false`Ayarlandığında, iletiler geçici depoda depolanır ve MSMQ hizmetini durdurma ve yeniden başlatma da kaybolur.  
  
 Güvenilir `ExactlyOnce` aktarım için MSMQ sıranın işlemsel olmasını gerektirir. Ayrıca, MSMQ bir işlem kuyruğundan okumak için bir hareket gerektirir. Bu nedenle, bir `NetMsmqBinding`hareket in ' olarak ayarlandığında ileti `ExactlyOnce` göndermek veya `true`almak için gerekli olduğunu unutmayın. Benzer şekilde, MSMQ, sıranın ne zaman `ExactlyOnce` `false` olduğu ve geçici iletiler gibi en iyi çaba güvencesi için işlem amaçlı olmamasını gerektirir. Bu nedenle, `ExactlyOnce` `false` bir işlemi `false`ayarlarken veya buna dayanıklı yken, bir hareketi kullanarak gönderemezsiniz veya alamazsınız.  
  
> [!NOTE]
> Bağlamadaki ayarlara göre doğru sıranın (işlemsel veya işlem dışı) oluşturulduğundan emin olun. `ExactlyOnce` Ise, `true`bir işlem sırası kullanın; aksi takdirde, işlem dışı bir sıra kullanın.  
  
#### <a name="dead-letter-queue-properties"></a>Ölü Harf Sıra Özellikleri  
 Ölü harf sırası, teslim başarısız iletileri depolamak için kullanılır. Kullanıcı, ölü harf kuyruğundan iletileri okuyan telafi mantığı yazabilir.  
  
 Birçok kuyruk sistemi, sistem çapında ölü harf sırası sağlar. MSMQ, işlem dışı kuyruklara teslim ivedilik etmeyen iletiler için sistem genelinde işlem dışı bir ölü harf sırası ve işlem kuyruklarına teslim ilerleyen iletiler için sistem genelinde işlemsel ölü harf kuyruğu sağlar.  
  
 Farklı hedef kuyruklara ileti gönderen birden çok istemci MSMQ hizmetini paylaşıyorsa, istemciler tarafından gönderilen tüm iletiler aynı ölü harf kuyruğuna gider. Bu her zaman tercih edilmez. Daha iyi yalıtım için, Windows Vista'daki WCF ve MSMQ, kullanıcının teslimde başarısız olan iletileri depolamak için belirtebileceği özel bir ölü harf sırası (veya uygulamaya özgü ölü harf sırası) sağlar. Bu nedenle, farklı istemciler aynı ölü harf sırasını paylaşmaz.  
  
 Bağlamanın iki ilgi özelliği vardır:  
  
- `DeadLetterQueue`: Bu özellik, ölü harf sırası nın istenip istenmediğini gösteren bir numaralandırmadır. Numaralandırma, istenirse ölü harf sırası türünü de içerir. Değerler `None`, `System`ve `Custom`. Bu özelliklerin yorumlanması hakkında daha fazla bilgi için, [İleti Aktarım Hatalarını Işlemek için Ölü Harf Kuyrukları Kullanma bölümüne](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md) bakın  
  
- `CustomDeadLetterQueue`: Bu özellik, uygulamaya özgü ölü harf sırasının Tekdüzen Kaynak Tanımlayıcısı (URI) adresidir. Bu, eğer `DeadLetterQueue`gereklidir.`Custom` seçilir.  
  
#### <a name="poison-message-handling-properties"></a>Zehirli İleti İşleme özellikleri  
 Hizmet bir hareket altında hedef sıradaki iletileri okuduğunda, hizmet çeşitli nedenlerle iletiyi işleyebilir. İleti daha sonra yeniden okunmak üzere kuyruğa geri konur. Sürekli olarak başarısız olan iletilerle başa çıkmak için, bir dizi zehirli ileti işleme özelliği bağlamada yapılandırılabilir. Dört özelliği `ReceiveRetryCount`vardır: `MaxRetryCycles` `RetryCycleDelay`, `ReceiveErrorHandling`, , ve . Bu özellikler hakkında daha fazla bilgi için [Poison Message Handling'e](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)bakın.  
  
#### <a name="security-properties"></a>Güvenlik Özellikleri  
 MSMQ, bir kuyruğa erişim denetim listeleri (ALA)veya kimlik doğrulaması iletileri gönderme gibi kendi güvenlik modelini ortaya çıkarır. Bu `NetMsmqBinding` güvenlik özelliklerini aktarım güvenlik ayarlarının bir parçası olarak ortaya çıkarır. Aktarım güvenliği için bağlamada iki `MsmqAuthenticationMode` `MsmqProtectionLevel`özellik vardır: ve. Bu özelliklerdeki ayarlar, MSMQ'nun nasıl yapılandırıldığına bağlıdır. Daha fazla bilgi için, [Aktarım Güvenliğini Kullanarak İletileri Güvence Altına Alma'ya](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)bakın.  
  
 Aktarım güvenliğine ek olarak, gerçek SOAP iletisinin kendisi ileti güvenliği kullanılarak güvenli hale alınabilir. Daha fazla bilgi için İleti [güvenliğini kullanarak İletileri Güvence Altına Alma'ya](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)bakın.  
  
 `MsmqTransportSecurity`ayrıca iki özelliği `MsmqEncryptionAlgorithm` ortaya `MsmqHashAlgorithm`çıkarır ve . Bunlar, iletilerin sıraya aktarım şifrelemesi ve imzaların karma hale getirmesi için seçilecek farklı algoritmaların sayısaldır.  
  
#### <a name="other-properties"></a>Diğer Özellikler  
 Önceki özelliklere ek olarak, bağlamada açığa çıkan diğer MSMQ özelliği ne kadar dır:  
  
- `UseSourceJournal`: Kaynak günlüğünün açık olduğunu gösteren bir özellik. Kaynak günlüğe aktarma, iletim kuyruğundan başarıyla iletilen iletileri izleyen bir MSMQ özelliğidir.  
  
- `UseMsmqTracing`: MSMQ izlemenin açık olduğunu gösteren bir özellik. MSMQ izleme, bir ileti her ayrıldığında veya MSMQ sıra yöneticisi barındıran bir makineye geldiğinde rapor kuyruğuna rapor iletileri gönderir.  
  
- `QueueTransferProtocol`: Sıraya sıralı ileti aktarımları için kullanılacak protokolün numaralandırması. MSMQ, yerel bir sıra-sıra aktarım protokolü ve SOAP Güvenilir İleti Protokolü (SRMP) adı verilen SOAP tabanlı bir protokol uygular. SRMP, sıraya sıraak aktarımlar için HTTP aktarımLarını kullanırken kullanılır. Kuyruk-sıra aktarımları için HTTPS kullanırken SRMP secure kullanılır.  
  
- `UseActiveDirectory`: Etkin Dizin'in sıra adresi çözümü için kullanılıp kullanılmayacağını belirtmek için bir Boolean değeri. Varsayılan olarak, bu kapalıdır. Daha fazla bilgi için [Hizmet Bitiş Noktaları ve Sıra Adresleme'ye](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)bakın.  
  
### <a name="msmqintegrationbinding"></a>Msmqıntegrationbinding  
 C, `MsmqIntegrationBinding` C++, COM veya System.Messaging API'lerinde yazılmış varolan bir MSMQ uygulamasıyla iletişim kurmak için wcf bitiş noktası istediğinizde kullanılır.  
  
 Bağlama özellikleri `NetMsmqBinding`. Ancak, aşağıdaki farklar geçerlidir:  
  
- İşlem `MsmqIntegrationBinding` sözleşmesi, tür parametresi gövde türü <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> olduğu tek bir tür parametresi alarak sınırlıdır.  
  
- MSMQ yerel ileti özelliklerinin <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> çoğu kullanımda ortaya çıkarır.  
  
- İleti gövdesinin serileştirilmesi ve deserializasyonuna yardımcı olmak için XML ve ActiveX gibi serializerler sağlanır.  
  
### <a name="sample-code"></a>Örnek Kod  
 MSMQ kullanan WCF hizmetlerinin nasıl yazılacağına ilişkin adım adım talimatlar için aşağıdaki konulara bakın:  
  
- [Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
  
- [Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
  
 WCF'de MSMQ kullanımını gösteren tamamlanmış bir kod örneği için aşağıdaki konulara bakın:  
  
- [İşlem Gerçekleştirilmiş MSMQ Bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
  
- [Geçici Kuyruğa Alınmış İletişim](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
  
- [Teslim Edilemeyen İletiler Sırası](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
  
- [Oturumlar ve Kuyruklar](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
  
- [Çift Yönlü İletişim](../../../../docs/framework/wcf/samples/two-way-communication.md)
  
- [SRMP](../../../../docs/framework/wcf/samples/srmp.md)  
  
- [İleti Kuyruğa Alma ile İleti Güvenliği](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmet Uç Noktaları ve Kuyruk İşleme](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)
- [Kuyruğa Alınan Bir Uygulamayı Web'de Barındırma](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
