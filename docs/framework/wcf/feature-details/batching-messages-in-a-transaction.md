---
title: Bir İşlemde Toplu İleti İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- batching messages [WCF]
ms.assetid: 53305392-e82e-4e89-aedc-3efb6ebcd28c
ms.openlocfilehash: 3b35d1de76587ce750bf73189eb37658c3d87a90
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593626"
---
# <a name="batching-messages-in-a-transaction"></a>Bir İşlemde Toplu İleti İşleme
Kuyruğa alınan uygulamalar, iletilerin doğruluğu ve güvenilir bir şekilde teslim edilmesini sağlamak için işlemleri kullanır. Ancak işlemler, pahalı işlemlerdir ve ileti verimini önemli ölçüde azaltabilir. İleti aktarım hızını artırmanın bir yolu, bir uygulamanın tek bir işlem içinde birden fazla iletiyi okumasını ve işlemesini kullanmaktır. Denge, performans ve kurtarma arasındadır: bir toplu işteki ileti sayısı arttıkça, işlemler geri alınırsa kurtarma işinin miktarı artar. İşlem ve oturumlardaki toplu işleme iletileri arasındaki farkı göz önünde bulundurulmamak önemlidir. *Oturum* , tek bir uygulama tarafından işlenen ve tek bir birim olarak yürütülen ilgili mesajların bir gruplandırmasıdır. Oturumlar genellikle ilgili bir grup ileti birlikte işlenmeli şekilde kullanılır. Bu, bir çevrimiçi alışveriş web sitesi örneğidir. *Toplu işlemler* , birden fazla ilişkisiz iletiyi ileti aktarım hızını arttırabileceğiniz bir şekilde işlemek için kullanılır. Oturumlar hakkında daha fazla bilgi için bkz. [bir oturumda sıraya alınmış Iletileri gruplandırma](grouping-queued-messages-in-a-session.md). Toplu işteki iletiler aynı zamanda tek bir uygulama tarafından işlenir ve tek bir birim olarak kaydedilir, ancak toplu işteki iletiler arasında hiçbir ilişki bulunmayabilir. İşlem içindeki iletileri toplu işleme, uygulamanın nasıl çalıştığını değiştirmayan bir iyileştirmedir.  
  
## <a name="entering-batching-mode"></a>Toplu Işleme moduna giriliyor  
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior>Uç nokta davranışı toplu işlemeyi denetler. Bu uç nokta davranışının bir hizmet uç noktasına eklenmesi, bir işlemdeki toplu iletilere Windows Communication Foundation (WCF) bildirir. Tüm iletiler bir işlem gerektirmez, bu nedenle yalnızca bir işlem gerektiren iletiler bir toplu işe konur ve yalnızca ile işaretlenmiş işlemlerden gönderilen iletiler `TransactionScopeRequired`  =  `true` `TransactionAutoComplete`  =  `true` bir toplu iş için kabul edilir. Hizmet sözleşmesindeki tüm işlemler ve ile işaretlenmişse `TransactionScopeRequired`  =  `false` `TransactionAutoComplete`  =  `false` , toplu işleme modu hiçbir şekilde girilmez.  
  
## <a name="committing-a-transaction"></a>Işlem yürütülüyor  
 Bir toplu işlem, aşağıdakilere göre kaydedilir:  
  
- `MaxBatchSize`. <xref:System.ServiceModel.Description.TransactedBatchingBehavior>Davranışın özelliği. Bu özellik bir toplu işe yerleştirilmiş en fazla ileti sayısını belirler. Bu sayıya ulaşıldığında, toplu iş kaydedilir. Bu değer katı bir sınır değildir, bu sayıda iletiyi almadan önce bir toplu işlem yürütmek mümkündür.  
  
- `Transaction Timeout`. İşlemin zaman aşımını yüzde 80 ' i geçtiğinde, toplu iş kaydedilir ve yeni bir toplu iş oluşturulur. Bu, bir işlemin tamamlanabilmesi için verilen sürenin yüzde 20 ' sini veya daha azını kalırsa toplu işin tamamlandığı anlamına gelir.  
  
- `TransactionScopeRequired`. Bir toplu ileti işlenirken, WCF bir tane bulursa, `TransactionScopeRequired`  =  `false` toplu işi kaydeder ve ve ile ilk iletinin alınması sırasında yeni bir toplu işi yeniden açar `TransactionScopeRequired`  =  `true` `TransactionAutoComplete`  =  `true` .  
  
- Kuyrukta daha fazla ileti yoksa, geçerli toplu işlem işlenir, ancak `MaxBatchSize` ulaşılmasa bile veya işlemin zaman aşımı süresinin yüzde 80 ' unun aşılmadığını belirtmez.  
  
## <a name="leaving-batching-mode"></a>Toplu Işleme modundan çıkma  
 Bir toplu işteki bir ileti işlemin iptal edilmesine neden oluyorsa, aşağıdaki adımlar oluşur:  
  
1. Tüm ileti toplu işi geri alınır.  
  
2. Okunan ileti sayısı en büyük toplu iş boyutunu iki kez aşana kadar iletiler bir kez okunabilir.  
  
3. Toplu işlem modu yeniden girildi.  
  
## <a name="choosing-the-batch-size"></a>Toplu Iş boyutunu seçme  
 Bir toplu işin boyutu uygulamaya bağımlıdır. Empırical yöntemi, uygulama için en iyi toplu iş boyutuna ulaşmanız için en iyi yoldur. Uygulamanızın gerçek dağıtım modeline göre boyutu seçmek için bir toplu iş boyutu seçerken unutmamak önemlidir. Örneğin, uygulamayı dağıttığınızda, uzak bir makinede bir SQL Server ve sırayı ve SQL Server 'ı kapsayan bir işlem gerekiyorsa, toplu iş boyutu bu tam yapılandırma çalıştırılarak en iyi şekilde belirlenir.  
  
## <a name="concurrency-and-batching"></a>Eşzamanlılık ve toplu Işleme  
 Aktarım hızını artırmak için aynı anda çok sayıda toplu işi de çalıştırabilirsiniz. ' De ayarı yaparak `ConcurrencyMode.Multiple` `ServiceBehaviorAttribute` , eşzamanlı toplu işlemeyi etkinleştirirsiniz.  
  
 *Hizmet azaltma* , hizmette kaç maksimum eşzamanlı çağrının kullanılabileceğini göstermek için kullanılan bir hizmet davranışıdır. Toplu işlem ile kullanıldığında, bu, kaç tane eşzamanlı toplu iş çalıştırılaacağına göre yorumlanır. Hizmet kısıtlaması ayarlanmamışsa, WCF varsayılan en fazla eşzamanlı olarak 16 ' ya çağrı yapar. Bu nedenle, varsayılan olarak toplu işlem davranışı eklendiyse, en fazla 16 toplu iş aynı anda etkin olabilir. Kapasiteniz temelinde hizmet azaltma ve toplu işleme ayarlamak en iyisidir. Örneğin, kuyruğun 100 iletisi varsa ve toplu iş 20 ' si isteniyorsa, aktarım hızına bağlı olarak 16 işlem etkin olabilir, çünkü işleme açık olmadan benzer. Bu nedenle, performans için ince ayar yaparken, eşzamanlı toplu işleme yok ya da doğru hizmet kısıtlama boyutuyla eşzamanlı toplu işleme sahip değil.  
  
## <a name="batching-and-multiple-endpoints"></a>Toplu işleme ve birden çok uç nokta  
 Bir uç nokta bir adresten ve sözleşmeden oluşur. Aynı bağlamayı paylaşan birden fazla uç nokta olabilir. İki uç noktanın aynı bağlamayı paylaşması ve Tekdüzen Kaynak tanımlayıcısı (URI) veya kuyruk adresi dinlemesi mümkündür. İki uç nokta aynı kuyruktan okunacağından ve her iki uç noktaya işlenen toplu işlem davranışı eklenirse, belirtilen toplu iş boyutlarında bir çakışma ortaya çıkabilir. Bu, iki işlem temelli toplu işlem davranışı arasında belirtilen en küçük toplu iş boyutu kullanılarak toplu işleme uygulayarak çözümlenir. Bu senaryoda, uç noktalardan biri işlenen toplu işleme belirtmezse her iki uç nokta de toplu işlem kullanmaz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `TransactedBatchingBehavior` bir yapılandırma dosyasında nasıl ekleneceğini gösterir.  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="TransactedBatchingBehavior"
              maxBatchSize="100" />
  </endpointBehaviors>
</behaviors>
```  
  
 Aşağıdaki örnek, içinde kodunun nasıl ekleneceğini gösterir <xref:System.ServiceModel.Description.TransactedBatchingBehavior> .  
  
```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
{
     ServiceEndpoint sep = ServiceHost.AddServiceEndpoint(typeof(IOrderProcessor), new NetMsmqBinding(), "net.msmq://localhost/private/ServiceModelSamplesTransacted");
     sep.Behaviors.Add(new TransactedBatchingBehavior(100));

     // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();
  
    // The service can now be accessed.
    Console.WriteLine("The service is ready.");
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.WriteLine();
    Console.ReadLine();
  
    // Close the ServiceHostB to shut down the service.
    serviceHost.Close();
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kuyruklar Genel Bakış](queues-overview.md)
- [WCF'de Kuyruğa Alma](queuing-in-wcf.md)
