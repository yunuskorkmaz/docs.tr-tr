---
title: Kuyruğa Alınan İletişim için En İyi Uygulamalar
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], best practices
- best practices [WCF], queued communication
ms.assetid: 446a6383-cae3-4338-b193-a33c14a49948
ms.openlocfilehash: af9ed7d64a60042297e071262be7610c4d791a51
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601354"
---
# <a name="best-practices-for-queued-communication"></a>Kuyruğa Alınan İletişim için En İyi Uygulamalar
Bu konu, Windows Communication Foundation (WCF) ' de sıraya alınmış iletişim için önerilen uygulamaları sağlar. Aşağıdaki bölümlerde senaryo açısından önerilen uygulamalar ele alınmaktadır.  
  
## <a name="fast-best-effort-queued-messaging"></a>Hızlı, En Iyi performans sıraya alınmış mesajlaşma  
 Sıraya alınan mesajlaşma 'nın sağladığı ve hızlı, yüksek performanslı mesajlaşma sağlayan ve en iyi çaba düzeyi olan, işlemsel olmayan bir kuyruk kullanan ve özelliği olarak ayarlanmış olan senaryolar için <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> `false` .  
  
 Ayrıca, özelliğini olarak ayarlayarak disk yazma maliyetlerine yönelik bir ücret ödemeniz gerekmez <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> `false` .  
  
 Güvenliğin performansı üzerinde etkileri vardır. Daha fazla bilgi için bkz. [performans konuları](performance-considerations.md).  
  
## <a name="reliable-end-to-end-queued-messaging"></a>Güvenli uçtan uca sıraya alınmış mesajlaşma  
 Aşağıdaki bölümlerde uçtan uca güvenilir mesajlaşma gerektiren senaryolar için önerilen uygulamalar açıklanır.  
  
### <a name="basic-reliable-transfer"></a>Temel güvenilir aktarım  
 Uçtan uca güvenilirlik için, <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> `true` aktarımı sağlamak üzere özelliğini olarak ayarlayın. <xref:System.ServiceModel.MsmqBindingBase.Durable%2A>Özelliği `true` `false` gereksinimlerinize göre veya gereksinimlerinize göre ayarlanabilir (varsayılan değer `true` ). Genellikle, <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> özelliği `true` uçtan uca güvenilirliğin parçası olarak olarak ayarlanır. Bu bir performans maliyetlidir, ancak kuyruk yöneticisi kilitlenirse iletinin kaybolmaması için iletiyi sürekli hale getirir.  
  
### <a name="use-of-transactions"></a>Işlemlerin kullanımı  
 Uçtan uca güvenilirlik sağlamak için işlemleri kullanmanız gerekir. `ExactlyOnce`yalnızca iletilerin hedef sıraya teslim edilmesini sağlar. İletinin alındığından emin olmak için işlemleri kullanın. İşlem olmadan, hizmet çöktüğünde, teslim edilen ancak uygulamaya teslim edilen iletiyi kaybedersiniz.  
  
### <a name="use-of-dead-letter-queues"></a>Atılacak Ileti sıralarının kullanımı  
 Atılacak ileti sıraları, bir iletinin hedef sıraya teslim edilemezse haberdar olmanızı sağlar. Sistem tarafından belirtilen atılacak ileti sırasını veya özel bir atılacak ileti sırasını kullanabilirsiniz. Genel olarak, özel bir atılacak mektup sırasının kullanılması en iyisidir çünkü bir uygulamadan gelen atılacak iletileri tek bir atılacak ileti kuyruğuna göndermenizi sağlar. Aksi takdirde, sistemde çalışan tüm uygulamalar için oluşan tüm atılacak iletiler tek bir sıraya teslim edilir. Daha sonra her bir uygulama, bu uygulamayla ilgili atılacak ileti iletilerini bulmak için atılacak ileti kuyruğu ' nu aramalıdır. Bazen, MSMQ 3,0 kullanırken olduğu gibi özel bir atılacak mektup sırasının kullanılması uygulanamaz.  
  
 Uçtan uca güvenilir iletişim için atılacak ileti sıralarının kapatılması önerilmez.  
  
 Daha fazla bilgi için bkz. [Ileti aktarımı başarısızlıklarını işlemek Için atılacak Ileti sıralarını kullanma](using-dead-letter-queues-to-handle-message-transfer-failures.md).  
  
### <a name="use-of-poison-message-handling"></a>Zehirli Ileti Işleme kullanımı  
 Zehirli ileti işleme, iletileri işleme başarısızlığından kurtarma olanağı sağlar.  
  
 Zarar iletisi işleme özelliğini kullanırken, <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> özelliğinin uygun değere ayarlandığından emin olun. <xref:System.ServiceModel.ReceiveErrorHandling.Drop>Verilerin kaybedildiği anlamına gelir. Öte yandan, <xref:System.ServiceModel.ReceiveErrorHandling.Fault> bir zarar iletisi algıladığında hizmet ana bilgisayarının hatalarını hatalara göre ayarlama. MSMQ 3,0 kullanarak, <xref:System.ServiceModel.ReceiveErrorHandling.Fault> veri kaybını önlemek ve zarar iletisini bu şekilde taşımak için en iyi seçenektir. MSMQ 4,0 kullanarak <xref:System.ServiceModel.ReceiveErrorHandling.Move> Önerilen yaklaşım önerilir. <xref:System.ServiceModel.ReceiveErrorHandling.Move>Hizmetin yeni iletileri işlemeye devam edebilmesi için, zarar görmüş bir iletiyi kuyruktan taşımış şekilde taşıyabilirsiniz. Poison-Message hizmeti daha sonra zarar iletisini ayrı olarak işleyebilir.  
  
 Daha fazla bilgi için bkz. [zehirli Ileti işleme](poison-message-handling.md).  
  
## <a name="achieving-high-throughput"></a>Yüksek verim elde etmek  
 Tek bir uç noktada yüksek performans elde etmek için aşağıdakileri kullanın:  
  
- İşlem temelli toplu işleme. İşlem temelli toplu işlem, birçok iletinin tek bir işlemde okunmamasını sağlar. Bu işlem, genel performansı artırarak işlem yürütmelerini iyileştirir. Toplu işlemin maliyeti, bir yığın içindeki tek bir iletide bir hata oluşursa, tüm toplu işin geri alınması ve iletilerin bir kez toplu iş için güvenli olana kadar tek tek işlenmesi gerekir. Çoğu durumda, zarar iletileri nadir olur, bu nedenle işlem, özellikle işleme katılan diğer kaynak yöneticileriniz olduğunda sistem performansını artırmanın tercih edilen yoludur. Daha fazla bilgi için bkz. [işlem Içindeki Iletileri toplu işleme](batching-messages-in-a-transaction.md).  
  
- Zamanlı. Eşzamanlılık aktarım hızını artırır, ancak eşzamanlılık, paylaşılan kaynaklara çekişmeyi de etkiler. Daha fazla bilgi için bkz. [eşzamanlılık](../samples/concurrency.md).  
  
- YAVAŞLATMA. En iyi performans için, dağıtıcı işlem hattındaki ileti sayısını azaltma. Bunun nasıl yapılacağı hakkında bir örnek için bkz. [azaltma](../samples/throttling.md).  
  
 Toplu işleme kullanılırken eşzamanlılık ve azaltma 'nın eşzamanlı toplu işlemlere çevirduğuna dikkat edin.  
  
 Daha yüksek aktarım hızı ve kullanılabilirlik elde etmek için, kuyruktan okuyan bir grup WCF hizmetini kullanın. Bu, tüm bu hizmetlerin aynı bir uç noktada aynı sözleşmeyi kullanıma sunmasına gerek duyar. Grup yaklaşımı, çok sayıda hizmetin aynı kuyruktan okunmasını sağladığından yüksek üretim fiyatları olan uygulamalar için en iyi şekilde kullanılır.  
  
 Grupları kullanırken, MSMQ 3,0 'nin uzaktan işlenen okumaları desteklemediğini unutmayın. MSMQ 4,0, uzaktan işlenen okumaları destekler.  
  
 Daha fazla bilgi için bkz. [Windows Vista, Windows Server 2003 ve WINDOWS XP 'de kuyruğa alma özelliklerinde](diff-in-queue-in-vista-server-2003-windows-xp.md) [Iletileri bir işlemde toplu işleme](batching-messages-in-a-transaction.md) ve farklar.  
  
## <a name="queuing-with-unit-of-work-semantics"></a>Çalışma birimi semantiğinin kuyruğa alınması  
 Bazı senaryolarda bir kuyruktaki bir ileti grubu ilgili olabilir ve bu nedenle, bu mesajların sıralaması önemli olur. Bu tür senaryolarda, bir grup ilişkili iletiyi tek bir birim olarak işleyin: tüm iletiler başarıyla işlenir ya da hiçbiri yoktur. Bu tür davranışları uygulamak için, kuyruklar ile oturum kullanın.  
  
 Daha fazla bilgi için bkz. [bir oturumda sıraya alınmış Iletileri gruplandırma](grouping-queued-messages-in-a-session.md).  
  
## <a name="correlating-request-reply-messages"></a>Istek-yanıt Iletilerini ilişkilendirme  
 Kuyruklar genellikle tek yönlü olsa da, bazı senaryolarda, daha önce gönderilen bir istek için alınan bir yanıtı ilişkilendirmek isteyebilirsiniz. Bu tür bağıntıya ihtiyacınız varsa, ileti ile bağıntı bilgilerini içeren kendi SOAP ileti üst bilgisini uygulamanız önerilir. Genellikle Gönderen bu üstbilgiyi ileti ile iliştirir ve alıcıyı bir yanıt kuyruğu üzerinde iletiyi işleyerek ve yeni bir iletiyle yeniden yanıtlayarak, gönderenin, istek iletisiyle yanıt iletisini tanımlayabilmesi için bağıntı bilgilerini içeren ileti üst bilgisini iliştirir.  
  
## <a name="integrating-with-non-wcf-applications"></a>WCF olmayan uygulamalarla tümleştirme  
 WCF `MsmqIntegrationBinding` hizmetlerini veya ISTEMCILERI WCF olmayan hizmetler veya istemcilerle tümleştirdiğinizde kullanın. WCF olmayan uygulama, System. Messaging, COM+, Visual Basic veya C++ kullanılarak yazılmış bir MSMQ uygulaması olabilir.  
  
 Kullanırken `MsmqIntegrationBinding` , aşağıdakilere dikkat edin:  
  
- Bir WCF ileti gövdesi, MSMQ ileti gövdesi ile aynı değildir. Bir WCF iletisini sıraya alınmış bağlamayı kullanarak gönderirken, WCF ileti gövdesi bir MSMQ iletisinin içine yerleştirilir. MSMQ altyapısı, bu ek bilgiler için zorunluluvou olur; yalnızca MSMQ iletisini görür.  
  
- `MsmqIntegrationBinding`Popüler serileştirme türlerini destekler. Serileştirme türüne dayalı olarak, genel iletinin gövde türü, <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> farklı tür parametreleri alır. Örneğin, <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.ByteArray> `MsmqMessage\<byte[]>` ve <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.Stream> gerektirir `MsmqMessage<Stream>` .  
  
- XML serileştirme ile, `KnownTypes` [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) XML iletisinin serisini kaldırma hakkında daha sonra kullanılan öğesindeki özniteliğini kullanarak bilinen türü belirtebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF'de Kuyruğa Alma](queuing-in-wcf.md)
- [Nasıl yapılır: WCF Uç Noktaları ile Kuyruğa Alınan İletileri Gönderme ve Alma](how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [Oturumda Kuyruğa Alınmış İletileri Gruplandırma](grouping-queued-messages-in-a-session.md)
- [Bir İşlemde Toplu İleti İşleme](batching-messages-in-a-transaction.md)
- [İleti Aktarımı Hatalarını İşlemek için Teslim Edilemeyen İletiler Sırası Kullanma](using-dead-letter-queues-to-handle-message-transfer-failures.md)
- [Zehirli İleti İşleme](poison-message-handling.md)
- [Windows Vista, Windows Server 2003 ve Windows XP'de Kuyruğa Alma Özelliği Arasındaki Farklar](diff-in-queue-in-vista-server-2003-windows-xp.md)
- [Taşıma Güveliği Kullanarak İletileri Güvenli Hale Getirme](securing-messages-using-transport-security.md)
- [İleti Güveliği Kullanarak İletileri Güvenli Hale Getirme](securing-messages-using-message-security.md)
- [Kuyruğa Alınan İletilerde Sorun Giderme](troubleshooting-queued-messaging.md)
