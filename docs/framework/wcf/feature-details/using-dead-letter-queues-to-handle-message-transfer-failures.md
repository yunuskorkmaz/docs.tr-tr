---
title: İleti Aktarımı Hatalarını İşlemek için Teslim Edilemeyen İletiler Sırası Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9e891c6a-d960-45ea-904f-1a00e202d61a
ms.openlocfilehash: 0be22fa1e81c85d82494bc4b93468a18f05d6423
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345567"
---
# <a name="using-dead-letter-queues-to-handle-message-transfer-failures"></a>İleti Aktarımı Hatalarını İşlemek için Teslim Edilemeyen İletiler Sırası Kullanma
Sıraya alınan iletiler teslim başarısız olabilir. Bu başarısız iletiler, teslim edilemeyen bir sıraya kaydedilir. Başarısız teslimat, ağ hataları, silinen bir kuyruk, tam sıra, kimlik doğrulama hatası veya zaman içinde teslim etme hatası gibi nedenlerle neden olabilir.  
  
 Alınan uygulama, zaman zaman bir süre sonra kuyruktan okunmayan sırada, sıradaki iletiler kuyrukta kalabilirler. Bu davranış zamana duyarlı iletiler için uygun olmayabilir. Zamana duyarlı iletiler, sıradaki bağlamada ayarlanan yaşam süresi (TTL) özelliğine sahiptir ve bu, iletilerin süresi dolmadan önce kuyrukta ne kadar süreyle kalabileceğini gösterir. Süre dolmayan iletiler, teslim edilemeyen ileti sırası adlı özel bir kuyruğa gönderilir. Ayrıca iletiler, bir kuyruk kotasının aşılması veya kimlik doğrulama hatası nedeniyle diğer nedenlerden dolayı atılacak bir sıraya alınabilir.  
  
 Genellikle, uygulamalar teslim edilemeyen ileti sırasından ve hata nedenlerinden iletileri okumak için maaş mantığı yazar. Dengeleme mantığı, hatanın nedenine bağlıdır. Örneğin, kimlik doğrulama hatası durumunda iletiyle bağlantılı sertifikayı düzeltebilir ve iletiyi yeniden gönderebilirsiniz. Hedef kuyruk kotasına ulaşıldığından, teslim başarısız olursa, kota sorununun çözümlendiğini umuyoruz.  
  
 Çoğu sıraya alma sisteminde, bu sistemdeki tüm başarısız iletilerin depolandığı sistem genelinde bir atılacak ileti sırası vardır. Message Queuing (MSMQ), iki sistem genelinde atılacak ileti sırası sağlar: işlem kuyruğuna teslim edilemeyen iletileri ve depolama olmayan sistem genelinde bir atılacak ileti kuyruğunu depolayan, sistem genelinde özel bir atılacak mektup kuyruğu işlemsel olmayan sıraya teslim edilemedi iletileri. İki istemci iki farklı hizmete ileti gönderiyorsa ve bu nedenle WCF 'deki farklı kuyruklar, göndermek için aynı MSMQ hizmetini paylaşılıyorsa, sistem teslim edilemeyen ileti kuyruğunda ileti karışımı olması mümkündür. Bu her zaman en uygun değildir. Birkaç durumda (güvenlik, örneğin), bir istemcinin eski ileti sırasından başka bir istemcinin iletilerini okumasını istemeyebilirsiniz. Paylaşılan bir atılacak ileti sırası, istemcilerin gönderdikleri bir iletiyi bulmak için kuyruğa gözatmasını ve teslim edilemeyen ileti sırasındaki ileti sayısına bağlı olarak yüksek maliyetli olabilecek bir şekilde canlı olarak yapılmasını gerektirir. Bu nedenle, WCF`NetMsmqBinding`, Windows Vista 'da `MsmqIntegrationBinding,` ve MSMQ özel bir atılacak ileti sırası (bazen uygulamaya özel atılacak mektup kuyruğu olarak adlandırılır) sağlar.  
  
 Özel atılacak mektup kuyruğu, iletileri göndermek için aynı MSMQ hizmetini paylaşan istemciler arasında yalıtım sağlar.  
  
 Windows Server 2003 ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)]Windows Communication Foundation (WCF), tüm sıraya alınmış istemci uygulamaları için sistem genelinde bir atılacak ileti sırası sağlar. Windows Vista 'da WCF, her kuyruğa alınan istemci uygulaması için atılacak bir sıra sağlar.  
  
## <a name="specifying-use-of-the-dead-letter-queue"></a>Atılacak Ileti sırasının kullanımını belirtme  
 Teslim edilemeyen bir sıra, gönderen uygulamanın kuyruk yöneticisidir. Bu, zaman aşımına uğradı veya başarısız aktarım ya da teslim olan iletileri depolar.  
  
 Bağlama, aşağıdaki atılacak ileti sırası özelliklerine sahiptir:  
  
- <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>  
  
- <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>  
  
## <a name="reading-messages-from-the-dead-letter-queue"></a>Iletileri atılacak ileti sırasından okuma  
 Eski bir ileti sırasından gelen iletileri okuyan bir uygulama, aşağıdaki küçük farklılıklar dışında bir uygulama kuyruğundan okuyan bir WCF hizmetine benzerdir:  
  
- Sistem işlem dışı ileti sırasından iletileri okumak için Tekdüzen Kaynak tanımlayıcısı (URI) şu biçimde olmalıdır: net. MSMQ://localhost/System $;D Eadxyasası.  
  
- Bir sistem işlem dışı teslim edilemeyen ileti sırasından iletileri okumak için URI şu biçimde olmalıdır: net. MSMQ://localhost/System $;D eadLetter.  
  
- Özel bir atılacak ileti sırasından iletileri okumak için URI şu biçimde olmalıdır: net. MSMQ://localhost/private/\<*Custom-DLQ-name*>; burada *Custom-DLQ-Name* özel atılacak ileti sırasının adıdır.  
  
 Kuyrukların nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [hizmet uç noktaları ve sıra adresleme](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
 Alıcının WCF yığını, hizmetin iletideki adresle dinlediği adreslerle eşleşir. Adresler eşleşiyorsa ileti gönderilir; Aksi takdirde ileti gönderilir. Bu, atılacak ileti sırasındaki iletiler genellikle teslim edilemeyen ileti sırası hizmetine değil hizmete değinilmesi nedeniyle, atılacak ileti sırasından okurken soruna neden olabilir. Bu nedenle, atılacak ileti sırasından okuma hizmeti, yığının, kümeden bağımsız olarak kuyruktaki tüm iletilerle eşleşmesini sağlayan bir adres filtresi `ServiceBehavior` yüklemelidir. Özellikle, teslim edilemeyen ileti sırasındaki iletileri okumak için <xref:System.ServiceModel.AddressFilterMode.Any> parametresine sahip bir `ServiceBehavior` eklemeniz gerekir.  
  
## <a name="poison-message-handling-from-the-dead-letter-queue"></a>Atılacak Ileti sırasından zarar Iletisi Işleme  
 Zarar iletisi işleme, bazı koşullarla, atılacak ileti sıralarında kullanılabilir. Sistem kuyruklarından alt kuyruklar oluşturamadığı için, sistem atılacak ileti sırasından okurken `ReceiveErrorHandling` `Move`olarak ayarlanamaz. Özel bir teslim edilemeyen ileti sırasından okuyorsanız, alt kuyruklara sahip olabilirsiniz ve bu nedenle `Move`, zarar iletisi için geçerli bir değerlendirme olduğunu unutmayın.  
  
 `ReceiveErrorHandling` `Reject`olarak ayarlandığında, özel geçersiz ileti sırasından okurken, zarar iletisi sistem atılacak ileti kuyruğuna konur. Sistem teslim edilemeyen ileti sırasından okurken ileti bırakılır (temizlendi). MSMQ 'da bir sistem atılacak ileti sırasından reddetme, iletiyi bırakır (temizler).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir atılacak ileti sırasının nasıl oluşturulduğunu ve süre sonu iletileri işlemek için nasıl kullanılacağını gösterir. Örnek, [nasıl yapılır: WCF uç noktaları Ile sıraya alınmış Iletileri Exchange ile](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)ilgili örneğe dayanır. Aşağıdaki örnek, her bir uygulama için bir atılacak ileti sırası kullanan sipariş işleme hizmetine istemci kodunun nasıl yazılacağını gösterir. Örnek ayrıca, teslim edilemeyen ileti sırasından iletileri nasıl işleyeceğini gösterir.  
  
 Aşağıda, her bir uygulama için atılacak ileti sırası belirten bir istemcinin kodu verilmiştir.  
  
 [!code-csharp[S_DeadLetter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/client.cs#1)]
 [!code-vb[S_DeadLetter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/client.vb#1)]  
  
 İstemci yapılandırma dosyasının kodu aşağıda verilmiştir.  

 Aşağıda, bir hizmet işlem iletilerinin atılacak ileti sırasından kodu verilmiştir.  
  
 [!code-csharp[S_DeadLetter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/dlservice.cs#3)]
 [!code-vb[S_DeadLetter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/dlservice.vb#3)]  
  
 Aşağıda, atılacak ileti sırası hizmeti yapılandırma dosyasının kodu verilmiştir.  

## <a name="see-also"></a>Ayrıca bkz.

- [Kuyruklara Genel Bakış](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Zehirli İleti İşleme](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
