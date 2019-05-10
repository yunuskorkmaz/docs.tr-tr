---
title: İleti Aktarımı Hatalarını İşlemek için Teslim Edilemeyen İletiler Sırası Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9e891c6a-d960-45ea-904f-1a00e202d61a
ms.openlocfilehash: c83d48994c6038dfde67867a1766777c479c2169
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64637729"
---
# <a name="using-dead-letter-queues-to-handle-message-transfer-failures"></a>İleti Aktarımı Hatalarını İşlemek için Teslim Edilemeyen İletiler Sırası Kullanma
Kuyruğa alınmış iletiler teslim başarısız olabilir. Bu başarısız iletileri teslim edilemeyen kuyrukta kaydedilir. Ağ hataları, silinen bir kuyruk, dolu bir sıra, kimlik doğrulama hatası veya zamanında sunmak için bir hata gibi nedenlerle başarısız teslim neden olabilir.  
  
 Alıcı uygulama bunları zamanında kuyruktan okumaz, kuyruğa alınmış iletiler uzun süredir kuyrukta kalabilir. Bu davranış, zamana duyarlı iletileri için uygun olmayabilir. Zamana duyarlı iletilerin süreleri dolmadan önce ne kadar süreyle iletiler kuyrukta uygulanıp uygulanamayacağını gösterir sıraya alınan bağlamasında yaşam süresi (TTL) özelliği için bir zaman sahip. Süresi dolan iletileri eski ileti sırası adı verilen özel bir kuyruğa gönderilir. İleti kimlik doğrulama hatası nedeniyle veya bir kuyruk kotasını gibi başka nedenlerle de edilemeyen kuyrukta konulabilir.  
  
 Genel olarak, telafi mantığının hatası nedenleri ve eski ileti sırası iletileri okumak için uygulamalar yazın. Hatanın nedenini üzerinde ve telafi mantığının bağlıdır. Örneğin, kimlik doğrulama hatası olması durumunda, iletinin iliştirilmiş sertifika düzeltin ve iletisini yeniden gönder. Hedef kuyruğu kotası üst sınırına ulaşıldığından teslim başarısız olursa, kota sorun çözülmüş umuduyla teslimat yeniden çalıştırmayı deneyin.  
  
 Tüm başarısız iletileri bu sistemden depolandığı bir sistem genelinde eski ileti sırası en kuyruk sistemleri var. Message Queuing (MSMQ) iki sistem genelinde edilemeyen sağlar: işlem sırası ve depolayan bir işlem olmayan sistem genelinde geçerliliğini yitirmiş kuyruk teslim başarısız iletileri depolayan bir işlem sistem genelinde eski ileti sırası işlem olmayan sıraya teslim edilemedi iletileri. Ardından iki istemciler için iki farklı hizmet iletileri gönderen ve bu nedenle farklı kuyruklara wcf'de göndermek için aynı MSMQ hizmeti paylaşan, sistem edilemeyen kuyrukta iletileri bir karışımını olması mümkündür. Bu her zaman en uygun değildir. Bazı durumlarda (örneğin, güvenlik), başka bir istemcinin iletileri teslim edilemeyen kuyruktan okumak için bir istemci istemeyebilir. Paylaşılan bir eski ileti sırası, ayrıca, hangi fazla vakit pahalı olabilir eski ileti sırası iletilerin sayısına dayalı olarak gönderilen bir ileti bulmak için sırada göz atmak istemcileri gerektirir. Bu nedenle, wcf'de`NetMsmqBinding`, `MsmqIntegrationBinding,` ve üzerindeki [!INCLUDE[wv](../../../../includes/wv-md.md)] (bazen bir uygulamaya özgü eski ileti sırası adlandırılır) özel bir eski ileti sırası sağlayın.  
  
 Özel teslim edilemeyen kuyruğa ileti göndermek için aynı MSMQ hizmeti paylaşan istemciler arasında yalıtım sağlar.  
  
 Üzerinde [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)], Windows Communication Foundation (WCF) tüm kuyruğa alınan istemci uygulamaları için bir sistem genelinde eski ileti sırası sağlar. Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)], WCF, eski ileti sırası için her sıraya alınan istemci uygulaması sağlar.  
  
## <a name="specifying-use-of-the-dead-letter-queue"></a>Eski ileti sırası kullanımını belirtme  
 Gönderen uygulama sıra yöneticisinde bir teslim edilemeyen kuyruğudur. Bu aktarımı veya teslim başarısız olan veya süresi dolmuş olan iletileri depolar.  
  
 Bağlama aşağıdaki eski ileti sırası özelliklere sahiptir:  
  
- <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>  
  
- <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>  
  
## <a name="reading-messages-from-the-dead-letter-queue"></a>Teslim edilemeyen kuyruktan iletileri okuma  
 Geçerliliğini yitirmiş kuyruk iletileri okuyan bir uygulaması aşağıdaki küçük farklılıklar dışında bir uygulama kuyruktan okuyan bir WCF Hizmeti benzer:  
  
- Bir sistem işlem eski ileti sırası iletileri okumak için Tekdüzen Kaynak Tanımlayıcısı (URI) biçiminde olmalıdır: net.msmq://localhost/system$; DeadXact.  
  
- Bir sistem işlem olmayan eski ileti sırası iletileri okumak için URI biçiminde olmalıdır: net.msmq://localhost/system$; teslim edilemeyen iletiler.  
  
- Özel teslim edilemeyen kuyruktan iletileri okumak için URI form: net.msmq://localhost/private/ olmalıdır\<*özel dlq adı*> Burada *özel dlq adı* özel adı eski ileti sırası.  
  
 Adresi kuyruklara hakkında daha fazla bilgi için bkz. [hizmet uç noktaları ve kuyruk işleme](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
 WCF yığında alıcı adresi iletideki hizmet dinlediği adresleriyle eşleşir. Adreslerden biri eşleşirse ileti gönderilir; Aksi durumda, ileti değil gönderilir. Geçerliliğini yitirmiş kuyruk iletileri, genellikle hizmet ve eski ileti sırası hizmeti yönlendirildiği edilemeyen kuyruktan okunurken sorun olabilir. Bu nedenle, eski ileti kuyruktan okuma hizmet adresi filtresi yüklemeniz gerekir `ServiceBehavior` alıcıyı bağımsız olarak kuyruğundaki tüm iletileri eşleşmesi için yığın bildirir. Özellikle, eklemelisiniz bir `ServiceBehavior` ile <xref:System.ServiceModel.AddressFilterMode.Any> edilemeyen kuyruktan iletileri okuyan hizmet parametresi.  
  
## <a name="poison-message-handling-from-the-dead-letter-queue"></a>Zehirli ileti işleme eski ileti sırası  
 Zehirli ileti işleme edilemeyen, bazı koşullar ile kullanılabilir. Alt kuyruk sistem edilemeyen kuyruktan okurken sistem sıralarından oluşturulamıyor çünkü `ReceiveErrorHandling` ayarlanamıyor `Move`. Not özel teslim edilemeyen kuyruktan okuyorsanız, alt sıralar olabilir ve bu nedenle, `Move` zehirli ileti için geçerli bir eğilimi.  
  
 Zaman `ReceiveErrorHandling` ayarlanır `Reject`, zehirli ileti özel sahipsiz sıra okunurken sistem sahipsiz sıraya koyduğunuzda. İleti, sistem edilemeyen kuyruktan okuma, (Temizlenen) bırakılır. MSMQ düşme bir sistem edilemeyen kuyruktan bir reddetme (ileti temizler).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, geçerliliğini yitirmiş kuyruk oluşturma ve bunu süresi dolan iletileri işlemek için nasıl kullanılacağını gösterir. Örneğin, örnekte dayalı [nasıl yapılır: Exchange ileti WCF uç noktaları ile kuyruğa alınan](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md). Aşağıdaki örnek, sipariş işleme her uygulama için eski ileti sırası kullanan hizmet için istemci kodu yazma işlemi gösterilmektedir. Örnek ayrıca eski ileti sırası iletileri işlemek nasıl gösterir.  
  
 Her uygulama için bir sahipsiz sırayı belirten bir istemci için kod aşağıda verilmiştir.  
  
 [!code-csharp[S_DeadLetter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/client.cs#1)]
 [!code-vb[S_DeadLetter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/client.vb#1)]  
  
 İstemci yapılandırma dosyası için kodu verilmiştir.  

 Teslim edilemeyen bir kuyruktan ileti işleme bir hizmet için kod aşağıda verilmiştir.  
  
 [!code-csharp[S_DeadLetter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/dlservice.cs#3)]
 [!code-vb[S_DeadLetter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/dlservice.vb#3)]  
  
 Eski ileti sırası hizmeti yapılandırma dosyası için kodu verilmiştir.  

## <a name="see-also"></a>Ayrıca bkz.

- [Kuyruklara Genel Bakış](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Nasıl yapılır: WCF uç noktaları ile kuyruğa alınmış iletiler gönderip alır](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Zehirli İleti İşleme](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
