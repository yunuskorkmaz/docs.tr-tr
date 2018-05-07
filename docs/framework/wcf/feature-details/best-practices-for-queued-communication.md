---
title: Kuyruğa Alınan İletişim için En İyi Uygulamalar
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], best practices
- best practices [WCF], queued communication
ms.assetid: 446a6383-cae3-4338-b193-a33c14a49948
ms.openlocfilehash: b54569ad3d11c3b9b1b96e2738bdf0582b63b0b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="best-practices-for-queued-communication"></a>Kuyruğa Alınan İletişim için En İyi Uygulamalar
Bu konu, kuyruğa alınan iletişim Windows Communication Foundation (WCF) için önerilen yöntemler sağlar. Aşağıdaki bölümlerde bir senaryo açısından önerilen yöntemler açıklanmaktadır.  
  
## <a name="fast-best-effort-queued-messaging"></a>Hızlı ve en yüksek çaba ileti kuyruğa  
 İleti kuyruğa ayrımı sağlar gerektiren senaryolar ve hızlı, yüksek performanslı en yüksek çaba çıkışların ile Mesajlaşma, işlemsel olmayan bir sıraya kullanın ve ayarlayın <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> özelliğine `false`.  
  
 Ayrıca, disk yazma işlemleri maliyetini ayarlayarak tabi değil seçebileceğiniz <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> özelliğine `false`.  
  
 Güvenlik, performans üzerinde etkilere sahiptir. Daha fazla bilgi için bkz: [başarım düşünceleri](../../../../docs/framework/wcf/feature-details/performance-considerations.md).  
  
## <a name="reliable-end-to-end-queued-messaging"></a>Güvenilir uçtan uca ileti kuyruğa alındı  
 Aşağıdaki bölümler, uçtan uca güvenilir Mesajlaşma gerektiren senaryolar için önerilen uygulamaları açıklamaktadır.  
  
### <a name="basic-reliable-transfer"></a>Temel güvenilir aktarımı  
 Uçtan uca güvenilirlik için ayarlanmış <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> özelliğine `true` aktarım sağlamak için. <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> Özelliği ayarlanabilir `true` veya `false` gereksinimlerinize bağlı olarak (varsayılan `true`). Genellikle, <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> özelliği ayarlanmış `true` uçtan uca güvenilirlik bir parçası olarak. Güvenlik aşılması performans maliyeti, ancak sıra yöneticisi çökme gerçekleşirse ileti kayıp olmaması ileti dayanıklı hale getirir.  
  
### <a name="use-of-transactions"></a>İşlemleri kullanma  
 İşlemler, uçtan uca güvenilirlik sağlamak için kullanmalısınız. `ExactlyOnce` çıkışların yalnızca iletileri hedef sıraya teslim edilir emin olun. İleti alındığında emin olmak için işlemleri kullanın. Hizmetin çökmesi durumunda işlemler olmadan teslim edilmekte olduğu, ancak gerçekte uygulamaya teslim ileti kaybedersiniz.  
  
### <a name="use-of-dead-letter-queues"></a>Teslim edilemeyen iletiler sırası kullanma  
 Teslim edilemeyen iletiler sırası hedef sıraya teslim edilmesi bir ileti başarısız olursa bildirim aldığından emin olun. Sistem tarafından sağlanan sahipsiz sırayı veya özel bir sahipsiz sırayı kullanabilirsiniz. Tek bir sahipsiz sıraya içine bir uygulamadan teslim edilemeyen iletiler göndermenize olanak sağladığından genel olarak, özel bir sahipsiz sırayı kullanarak en iyisidir. Aksi takdirde, sistem üzerinde çalışan tüm uygulamaları için ortaya çıkan tüm teslim edilemeyen iletiler tek bir sıraya teslim edilir. Ardından, her uygulama yine de bu uygulamayla ilgili teslim edilemeyen iletiler bulmak için sahipsiz sırayı aramanız gerekir. Bazı durumlarda, özel bir sahipsiz sırayı kullanarak MSMQ 3.0 kullanırken gibi uygun değildir.  
  
 Sıralarındaki uçtan uca güvenilir iletişim için kapatma önerilmez.  
  
 Daha fazla bilgi için bkz: [ileti aktarımı hatalarını işlemek için teslim edilemeyen iletiler sırası kullanma](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).  
  
### <a name="use-of-poison-message-handling"></a>Poison ileti işleme kullanımı  
 Poison ileti işleme işlem iletileri hatasından kurtarma olanağı sağlar.  
  
 Poison ileti işleme özelliğini kullanırken emin <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> özelliğini uygun değere ayarlayın. Ayar <xref:System.ServiceModel.ReceiveErrorHandling.Drop> veriler kaybolur anlamına gelir. Diğer taraftan, ayarı <xref:System.ServiceModel.ReceiveErrorHandling.Fault> zararlı bir ileti algıladığında hizmet konağı hataları. MSMQ 3.0 kullanılarak <xref:System.ServiceModel.ReceiveErrorHandling.Fault> veri kaybını önlemek ve zararlı ileti dışına taşımak için en iyi seçenektir. MSMQ 4. 0'da da kullanarak <xref:System.ServiceModel.ReceiveErrorHandling.Move> önerilen yaklaşımdır. <xref:System.ServiceModel.ReceiveErrorHandling.Move> Hizmet yeni iletileri işlemeye devam edebilmek için sıradaki zarar görmüş bir ileti taşır. Poison ileti hizmeti zehir iletisi sonra ayrı olarak işleyebilir.  
  
 Daha fazla bilgi için bkz: [zehirli ileti işleme](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
## <a name="achieving-high-throughput"></a>Yüksek verimlilik elde  
 Tek bir uç noktada yüksek verimlilik elde etmek için aşağıdakileri kullanın:  
  
-   İşlem yapılan toplu işlem. İşlenen toplu iş çok sayıda ileti tek bir işlemde okuyabilmelerini sağlar. Bu işlem yürütme, genel performansı artırma en iyi duruma getirir. Toplu işleme maliyetini bir yığın içindeki tek bir ileti hata oluşuyor sonra toplu işlemin tamamını geri alınır ve iletileri işlenen teker teker yeniden toplu güvenlidir kadar olması gerekiyorsa olmasıdır. Çoğu durumda, toplu işleme özellikle işlemde diğer kaynak yöneticileri olduğunda sistem performansını artırmak için tercih edilen yöntem olmasını zarar iletileri seyrek, kullanılır. Daha fazla bilgi için bkz: [bir işlemde toplu ileti](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md).  
  
-   Eşzamanlılık. Eşzamanlılık verimliliğini artırır, ancak eşzamanlılık paylaşılan kaynakları için Çekişme de etkiler. Daha fazla bilgi için bkz: [eşzamanlılık](../../../../docs/framework/wcf/samples/concurrency.md).  
  
-   Azaltma. En iyi performans için ileti dağıtıcısı ardışık düzeninde sayısını azaltma. Bunun nasıl yapılacağı örneği için bkz: [azaltma](../../../../docs/framework/wcf/samples/throttling.md).  
  
 Toplu işleme kullanırken, eşzamanlılık ve azaltma için eş zamanlı toplu Çevir unutmayın.  
  
 Daha yüksek performans ve kullanılabilirlik elde etmek için bir grubu kuyruktan okunmak WCF hizmetleri kullanın. Bu, tüm bu hizmetleri aynı sözleşme aynı uç noktada kullanıma gerektirir. Grup yaklaşım iletileri yüksek üretim oranları tüm hizmetlerin sayısı sağladığından olan uygulamalar için en iyi çalışır aynı kuyruktan okuyun.  
  
 Grupları kullanırken, MSMQ 3.0 uzak işlem temelli okuma desteklemediğini unutmayın. MSMQ 4.0 uzaktan hizmetteki okuma desteklemiyor.  
  
 Daha fazla bilgi için bkz: [bir işlemde toplu ileti](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md) ve [Queuing özelliği Windows Vista, Windows Server 2003 ve Windows XP arasındaki farklar](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).  
  
## <a name="queuing-with-unit-of-work-semantics"></a>İş semantiği birimle queuing  
 Bazı senaryolarda iletiler bir kuyrukta grubunu ilgili olabilir ve bu nedenle, bu iletilerin sıralama önemlidir. Bu senaryolarda, ilgili iletiler birlikte tek bir birim olarak bir grup işlem: tüm iletileri başarıyla işlendi ya da yok. Bu tür davranış uygulamak için kuyruklarla oturumları kullanın.  
  
 Daha fazla bilgi için bkz: [gruplandırma sıraya alınan iletileri bir oturumda](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md).  
  
## <a name="correlating-request-reply-messages"></a>İstek-yanıt iletilerini ilişkilendirme  
 Kuyruklar genellikle tek yönlü olmakla birlikte, bazı senaryolarda daha önce gönderilen bir istek aldı bir Yanıtla ilişkilendirmek isteyebilirsiniz. Bu tür bağıntı gerektiriyorsa, iletinin bağıntı bilgilerle içeren kendi SOAP iletisi üstbilgisi uygulamanız önerilir. Genellikle, bu iletiyi başlığıyla gönderen ekler ve iletiyi işlemeyi ve yanıt sırası üzerinde yeni bir ileti ile geri yanıtlama alıcı, böylece gönderenin bağıntı bilgilerini içeren gönderenin ileti üstbilgisi ekler İstek iletisi yanıt iletisiyle tanımlayın.  
  
## <a name="integrating-with-non-wcf-applications"></a>WCF olmayan uygulamaları ile tümleştirme  
 Kullanım `MsmqIntegrationBinding` WCF hizmetleri veya istemcileri olmayan WCF hizmetleri veya istemcileri ile tümleştirdiğinizde. WCF olmayan uygulama System.Messaging, COM +, Visual Basic ya da C++ kullanılarak yazılmış bir MSMQ uygulama olabilir.  
  
 Kullanırken `MsmqIntegrationBinding`, aşağıdakilere dikkat edin:  
  
-   WCF ileti gövdesi MSMQ İleti gövdesi aynı değil. Sıraya alınan bağlama kullanarak bir WCF ileti gönderirken, WCF ileti gövdesi içinde MSMQ iletisi yerleştirilir. Bu ek bilgiler oblivious MSMQ altyapısıdır; yalnızca MSMQ iletisi görür.  
  
-   `MsmqIntegrationBinding` popüler serileştirme türlerini destekler. Genel ileti gövdesi türü seri hale getirme türüne göre <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, farklı tür parametreleri alır. Örneğin, <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.ByteArray> gerektirir `MsmqMessage\<byte[]>` ve <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.Stream> gerektirir `MsmqMessage<Stream>`.  
  
-   XML serileştirilmesi ile bilinen türü kullanılarak belirtebilirsiniz `KnownTypes` özniteliği [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) sonra XML iletisini seri durumdan nasıl belirlemek için kullanılan öğesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF'de Kuyruğa Alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [Oturumda Kuyruğa Alınmış İletileri Gruplandırma](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 [Bir İşlemde Toplu İleti İşleme](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 [İleti Aktarımı Hatalarını İşlemek için Teslim Edilemeyen İletiler Sırası Kullanma](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 [Zehirli İleti İşleme](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 [Windows Vista, Windows Server 2003 ve Windows XP'de Kuyruğa Alma Özelliği Arasındaki Farklar](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 [Aktarım Güvenliği Kullanarak İletileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 [İleti Güveliği Kullanarak İletileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 [Kuyruğa Alınan İletilerde Sorun Giderme](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)
