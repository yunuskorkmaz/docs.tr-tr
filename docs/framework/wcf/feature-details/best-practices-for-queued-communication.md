---
title: Kuyruğa Alınan İletişim için En İyi Uygulamalar
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], best practices
- best practices [WCF], queued communication
ms.assetid: 446a6383-cae3-4338-b193-a33c14a49948
ms.openlocfilehash: b2f64faab6df678182fb39174c8a558b298a8748
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584976"
---
# <a name="best-practices-for-queued-communication"></a>Kuyruğa Alınan İletişim için En İyi Uygulamalar
Bu konu, Windows Communication Foundation (WCF) kuyruğa alınan iletişim için önerilen yöntemler sağlar. Aşağıdaki bölümlerde, önerilen uygulamaların bir senaryo açısından ele alınmıştır.  
  
## <a name="fast-best-effort-queued-messaging"></a>Hızlı, en yüksek çaba ileti kuyruğa alındı  
 İleti kuyruğa ayrımı sağlar gerektiren senaryolar ve hızlı, yüksek performanslı en yüksek çaba Güvenceleri ile Mesajlaşma için işlem olmayan bir kuyruk kullanın ve ayarlama <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> özelliğini `false`.  
  
 Ayrıca, disk yazmalarının ayarlayarak bir ücret değil seçebileceğiniz <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> özelliğini `false`.  
  
 Güvenlik, performans üzerinde etkilere sahiptir. Daha fazla bilgi için [performansla ilgili önemli noktalar](../../../../docs/framework/wcf/feature-details/performance-considerations.md).  
  
## <a name="reliable-end-to-end-queued-messaging"></a>Güvenilir uçtan uca ileti kuyruğa alındı  
 Aşağıdaki bölümlerde, uçtan uca güvenilir Mesajlaşma gerektiren senaryolar için önerilen yöntemler açıklanmaktadır.  
  
### <a name="basic-reliable-transfer"></a>Temel Güvenilir Aktarım  
 Uçtan uca güvenilirlik için ayarlanmış <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> özelliğini `true` aktarımı emin olmak için. <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> Özelliği ayarlanabilir `true` veya `false` gereksinimlerinize bağlı olarak (varsayılan değer `true`). Genellikle, <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> özelliği `true` uçtan uca güvenilirlik bir parçası olarak. Güvenlik aşılması bir performans maliyeti, ancak ileti dayanıklı yapar ve böylece bir kuyruk Yöneticisi bir çökme gerçekleşirse ileti kaybolur değil.  
  
### <a name="use-of-transactions"></a>İşlem kullanımı  
 Uçtan uca güvenilirlik sağlamak için işlem kullanmanız gerekir. `ExactlyOnce` Güvenceleri yalnızca iletileri hedef sıraya teslim edilmesini sağlayın. İleti alındığından emin olmak için işlemleri kullanma. Hizmetin kilitlenmesi durumunda işlemler olmadan teslim edilmekte olduğu ancak gerçekten uygulamaya teslim ileti kaybedersiniz.  
  
### <a name="use-of-dead-letter-queues"></a>Edilemeyen kullanımı  
 Edilemeyen bir iletinin hedef sıraya teslim başarısız olursa bildirim aldığından emin olun. Sistem tarafından sağlanan eski ileti sırası veya özel bir eski ileti sırası kullanabilirsiniz. Tek bir eski ileti sırası bir uygulamaya teslim edilemeyen iletiler göndermenize olanak sağladığından genel olarak, özel bir sahipsiz sırayı kullanarak en iyisidir. Aksi takdirde, sistem üzerinde çalışan tüm uygulamalar için ortaya çıkan tüm teslim edilemeyen iletiler tek kuyruğuna teslim edilir. Ardından, her bir uygulama yine de bu uygulamayla ilgili atılacak iletiler bulmak için eski ileti sırası aramanız gerekir. Bazı durumlarda, bir özel sahipsiz sırayı kullanarak MSMQ 3.0 kullanırken olduğu gibi uygun değil.  
  
 Geçerliliğini yitirmiş kuyruk uçtan uca güvenilir iletişim için kapatma önerilmez.  
  
 Daha fazla bilgi için [kullanarak edilemeyen ileti aktarımı hatalarını işlemek için](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).  
  
### <a name="use-of-poison-message-handling"></a>Poison ileti işleme kullanımı  
 Poison ileti işleme için işlem iletileri hatadan kurtarmak yeteneği sağlar.  
  
 Poison ileti işleme özelliğini kullanırken, emin <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> özelliği, uygun değere ayarlanır. Bu ayarın <xref:System.ServiceModel.ReceiveErrorHandling.Drop> verilere kaybolmuş anlamına gelir. Öte yandan, ayar <xref:System.ServiceModel.ReceiveErrorHandling.Fault> hizmet ana bilgisayarı, zehirli ileti algıladığında hataları. MSMQ 3.0 kullanan <xref:System.ServiceModel.ReceiveErrorHandling.Fault> zehirli ileti dışına taşımak ve veri kaybını önlemek için en iyi seçenektir. MSMQ 4. 0'da da kullanarak <xref:System.ServiceModel.ReceiveErrorHandling.Move> önerilen yaklaşımdır. <xref:System.ServiceModel.ReceiveErrorHandling.Move> Hizmet yeni iletileri işlemeye devam edebilmesi sıradaki zarar görmüş bir ileti taşır. Poison message hizmeti daha sonra ayrı ayrı zehirli ileti işleyebilir.  
  
 Daha fazla bilgi için [zehirli ileti işleme](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
## <a name="achieving-high-throughput"></a>Yüksek verimlilik elde etmeye  
 Tek bir uç nokta üzerinde yüksek performans sağlamak için aşağıdakileri kullanın:  
  
- İşlem yapılan toplu işlem. İşlenen toplu işleme, çok sayıda ileti tek bir işlemde okuyabilmelerini sağlar. Bu işlem yürütmeleri genel performansı artırmak, en iyi duruma getirir. Toplu işleme maliyeti, tek bir iletide bir yığın içindeki bir hata oluşması sonra toplu işin tamamını geri alınır ve iletileri işlenen teker teker yeniden toplu güvenlidir kadar olması gerekiyorsa. Toplu işlem sırasında katılan diğer kaynak yöneticileri olduğunda özellikle sistem performansını artırmak için tercih edilen yol, bu nedenle çoğu durumda, zehirli iletiler nadir rastlanır. Daha fazla bilgi için [bir işlemde toplu ileti](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md).  
  
- Eşzamanlılık. Eşzamanlılık verimliliğini artırır, ancak eşzamanlılık çakışması paylaşılan kaynaklar için de etkiler. Daha fazla bilgi için [eşzamanlılık](../../../../docs/framework/wcf/samples/concurrency.md).  
  
- Azaltma. En iyi performans için dağıtıcı ardışık düzeninde iletilerin sayısını azaltma. Bunu yapmak nasıl bir örnek için bkz [azaltma](../../../../docs/framework/wcf/samples/throttling.md).  
  
 Toplu işlem kullanırken, eşzamanlılık ve azaltma için eş zamanlı toplu Çevir dikkat edin.  
  
 Daha yüksek performans ve kullanılabilirlik elde etmek için bir kuyruktan okunur WCF hizmetleri grubu kullanın. Bu, bu hizmetlerin tümü aynı sözleşme aynı uç noktayı kullanıma gerektirir. Grup yaklaşım, bir dizi hizmet tüm sağladığından iletileri oranları yüksek üretim uygulamaları için en iyi çalışır aynı kuyruktan okunur.  
  
 Grupları kullanırken, MSMQ 3.0 uzak işlem temelli okuma desteklemediğini unutmayın. MSMQ 4.0 uzak işlem temelli okuma desteklemiyor.  
  
 Daha fazla bilgi için [bir işlemde toplu ileti](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md) ve [Windows Vista, Windows Server 2003 ve Windows XP sıraya alma özelliği arasındaki farklar](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).  
  
## <a name="queuing-with-unit-of-work-semantics"></a>İş semantiği birimle sıraya alma  
 Bazı senaryolarda, kuyruktaki iletiler grubunu ilgili ve bu nedenle, bu iletileri sıralama önemlidir. Böyle senaryolarda, tek bir birim olarak birlikte ilgili iletiler grubunu işlem: yok veya tüm iletileri başarıyla işlendi. Bu davranışı uygulamak kuyruklarla oturumları kullanın.  
  
 Daha fazla bilgi için [gruplandırma kuyruğa alınan iletileri bir oturumda](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md).  
  
## <a name="correlating-request-reply-messages"></a>İstek-yanıt iletilerini ilişkilendirme  
 Bazı senaryolarda kuyrukları tek yönlü genellikle olsa da, daha önce gönderilen bir istek aldı. bir Yanıtla ilişkilendirmek isteyebilirsiniz. Bu tür bağıntı ihtiyacınız varsa bağıntı bilgi iletisi içeren kendi SOAP ileti üst bilgisi geçerli önerilir. Genellikle, bu üst bilgi iletisi gönderen ekler ve böylece gönderenin bağıntı bilgilerini içeren gönderenin ileti üst bilgisi alıcı iletiyi işlemeyi ve yeniden bir yanıt kuyruğu üzerinde yeni bir ileti ile yanıt ekler İstek iletisi ile yanıt iletisi tanımlayın.  
  
## <a name="integrating-with-non-wcf-applications"></a>WCF olmayan uygulamaları ile tümleştirme  
 Kullanım `MsmqIntegrationBinding` WCF hizmetleri veya istemciler olmayan WCF hizmetleri veya istemcileri ile tümleştirdiğinizde. WCF olmayan uygulama MSMQ uygulamanın System.Messaging, COM +, Visual Basic veya C++ kullanılarak yazılmış olabilir.  
  
 Kullanırken `MsmqIntegrationBinding`, şunlara dikkat edin:  
  
- Bir WCF ileti gövdesi bir MSMQ İleti gövdesi ile aynı değil. Sıraya alınan bir bağlamayı kullanarak bir WCF ileti gönderirken, WCF ileti gövdesi içinde bir MSMQ iletisinin yerleştirilir. Bu ek bilgileri oblivious MSMQ altyapısıdır; Bu, yalnızca MSMQ iletiyi görür.  
  
- `MsmqIntegrationBinding` popüler serileştirme türlerini destekler. Genel iletinin gövde türü serileştirme türü temel alarak <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, farklı tür parametreleri alır. Örneğin, <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.ByteArray> gerektirir `MsmqMessage\<byte[]>` ve <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.Stream> gerektirir `MsmqMessage<Stream>`.  
  
- XML serileştirme ile bilinen türü kullanarak belirtebilirsiniz `KnownTypes` özniteliği [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesi XML ileti seri durumdan nasıl belirlemek için kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF'de Kuyruğa Alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [Nasıl yapılır: WCF uç noktaları ile kuyruğa alınmış iletiler gönderip alır](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Nasıl yapılır: WCF uç noktaları ve ileti uygulamaları ile Exchange ileti](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [Oturumda Kuyruğa Alınmış İletileri Gruplandırma](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)
- [Bir İşlemde Toplu İleti İşleme](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)
- [İleti Aktarımı Hatalarını İşlemek için Teslim Edilemeyen İletiler Sırası Kullanma](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)
- [Zehirli İleti İşleme](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
- [Windows Vista, Windows Server 2003 ve Windows XP'de Kuyruğa Alma Özelliği Arasındaki Farklar](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)
- [Aktarım Güvenliği Kullanarak İletileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)
- [İleti Güveliği Kullanarak İletileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)
- [Kuyruğa Alınan İletilerde Sorun Giderme](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)
