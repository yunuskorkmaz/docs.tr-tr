---
title: Bir İşlemde Toplu İleti İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- batching messages [WCF]
ms.assetid: 53305392-e82e-4e89-aedc-3efb6ebcd28c
ms.openlocfilehash: b0b189db8f51e0cccb6ee0516fc4cc53556ccf51
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174128"
---
# <a name="batching-messages-in-a-transaction"></a>Bir İşlemde Toplu İleti İşleme
Sıraya alınan uygulamaları, doğruluk ve iletilerin güvenilir teslim emin olmak için işlem kullanır. İşlem, ancak pahalı işlemlerdir ve ileti aktarım hızı önemli ölçüde azaltabilir. İleti işleme hızı artırmak için bir yol, okuma ve tek bir işlemde birden çok iletiyi bir uygulamaya sahip olmaktır. Performans ve kurtarma dengedir: toplu ileti sayısı arttıkça, bu nedenle gerekli işlemler geri alınacak olursa kurtarma iş yapar. Toplu işlem ve oturumları ileti işleme arasındaki farka dikkat edin önemlidir. A *oturumu* tek bir uygulama tarafından işlenen ve tek bir birim olarak kabul edilen ilgili iletiler bir gruplandırmasıdır. Oturumları ilgili iletiler grubunu birlikte işlenmesi gereken genel olarak kullanılır. Buna örnek olarak çevrimiçi bir alışveriş Web sitesidir. *Toplu* ilgisi olmayan iletileri arttıkça aktarım hızı ileti şekilde, birden fazla işlemek için kullanılır. Oturumlar hakkında daha fazla bilgi için bkz. [gruplandırma kuyruğa alınan iletileri bir oturumda](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md). Toplu iletiler de tek bir uygulama tarafından işlenen ve tek bir birim olarak kabul edilen, ancak toplu işlem iletileri arasında hiçbir ilişkisi olabilir. Bir işlemde toplu ileti işleme uygulamanın nasıl çalıştığını değişmez bir optimizasyondur.  
  
## <a name="entering-batching-mode"></a>Toplu işleme modu girme  
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior> Toplu işleme uç nokta davranışı denetimleri. Bu uç nokta davranışı hizmet uç noktası ekleme, bir işlemde toplu ileti için Windows Communication Foundation (WCF) bildirir. Bir işlem gerektiren yalnızca iletileri toplu işlemde yerleştirilir. Bu nedenle tüm iletileri bir işlem gerektirir ve ile işaretlenen işlemlerinden gönderilen yalnızca iletileri `TransactionScopeRequired`  =  `true` ve `TransactionAutoComplete`  =  `true` olan batch için kabul edilir. Tüm işlemleri hizmet sözleşmesi ile işaretlenip işaretlenmediğini `TransactionScopeRequired`  =  `false` ve `TransactionAutoComplete`  =  `false`, modu toplu işleme hiçbir zaman girildikten sonra.  
  
## <a name="committing-a-transaction"></a>Bir işlemi yürütülüyor  
 Toplu işlem taahhüt aşağıdakilere bağlıdır:  
  
-   `MaxBatchSize`biçimindeki telefon numarasıdır. Bir özelliği <xref:System.ServiceModel.Description.TransactedBatchingBehavior> davranışı. Bu özellik, bir toplu iş içine yerleştirilmesi iletileri maksimum sayısını belirler. Bu sayıya ulaşıldığında, toplu işlem taahhüt eder. Bu değeri kesin bir sınır değil, bu ileti sayısı almadan önce bir toplu iş yürütme mümkündür.  
  
-   `Transaction Timeout`biçimindeki telefon numarasıdır. İşlem zaman aşımı yüzde 80'i geçtikten sonra toplu işlem taahhüt eder ve yeni bir toplu iş oluşturulur. Yüzde 20, yani veya küçük bir hareketi tamamlamak verilen zaman olarak kalır, toplu işlem taahhüt eder.  
  
-   `TransactionScopeRequired`biçimindeki telefon numarasıdır. Toplu iletiler, WCF, içeren bulursa işlerken `TransactionScopeRequired`  =  `false`, toplu işleme ve ilk iletinin alınması üzerine yeni bir batch açana `TransactionScopeRequired`  =  `true` ve `TransactionAutoComplete`  = `true`.  
  
-   Daha fazla ileti kuyrukta kayıtlı sonra geçerli toplu kararlıdır bile `MaxBatchSize` değil ulaşıldı veya işlem zaman aşımı yüzde 80'i değil geçti.  
  
## <a name="leaving-batching-mode"></a>Toplu işleme modu çıkılıyor  
 Bir ileti bir toplu işlemin iptal etmek neden olursa, aşağıdaki adımlardan oluşur:  
  
1.  İletilerin toplu işin tamamını geri alınır.  
  
2.  İleti iki kez en yüksek toplu iş boyutu okuma ileti sayısını aşana kadar teker teker okunur.  
  
3.  Yeniden girilen toplu iş modu.  
  
## <a name="choosing-the-batch-size"></a>Toplu iş boyutu seçme  
 Bir toplu işin boyutunu uygulama bağımlıdır. Deneysel yöntemi, uygulama için bir en iyi toplu iş boyutu ulaşırsınız en iyi yoludur. Uygulamanızın gerçek dağıtım modeline göre boyutunu seçmek için bir toplu iş boyutu seçerken unutmamak önemlidir. Örneğin, uzak bir makine ve kuyruk kapsayan bir işlem üzerinde bir SQL server ve SQL server'ı gerekirse Uygulama dağıtırken, sonra toplu iş boyutu en iyi tam yapılandırmanın çalıştırarak belirlenir.  
  
## <a name="concurrency-and-batching"></a>Eşzamanlılık ve toplu işleme  
 Verimliliği artırmak için ayrıca birçok toplu eşzamanlı olarak çalıştırılmasını sağlayabilirsiniz. Ayarlayarak `ConcurrencyMode.Multiple` içinde `ServiceBehaviorAttribute`, eş zamanlı toplu işleme etkinleştirin.  
  
 *Hizmet azaltma* hizmette kaç tane maksimum eşzamanlı çağrı yapılabilmesi için göstermek için kullanılan bir hizmet davranışı. Birçok eş zamanlı toplu çalıştırılabilir nasıl toplu işlem ile kullanıldığında, bu yorumlanır. WCF Hizmeti azaltması ayarlanmazsa, 16 en fazla eşzamanlı çağrıların varsayılan olarak. Toplu işleme davranışı varsayılan olarak eklendiyse, bu nedenle, en fazla 16 toplu işlemler aynı anda etkin olabilir. Hizmet azaltma ayarlamak idealdir ve toplu işleme dayalı kapasite. İşleme bağlı olarak 16 işlemleri olabileceğinden, etkin, açık toplu işleme olmaması için benzer Örneğin, 100 iletileri kuyruğa varsa ve 20 toplu isteniyorsa, 16 ayarlamak en fazla eş zamanlı çağrılar sahip yararlı değil. Bu nedenle, performans için düzenine ince ayar yaparken ya eşzamanlı toplu işleme sahip ya da eşzamanlı doğru hizmet kısıtlama boyutuyla toplu işleme sahip.  
  
## <a name="batching-and-multiple-endpoints"></a>Toplu işleme ve birden fazla uç noktası  
 Bir uç nokta bir adresi ve bir sözleşme oluşur. Aynı bağlama paylaşan birden fazla uç nokta olabilir. Aynı bağlama paylaşmak ve Tekdüzen Kaynak Tanımlayıcısı (URI) veya kuyruk adresini dinlemek iki uç nokta için mümkündür. İki uç nokta aynı sıra okunurken ve hizmetteki ise davranışı toplu işleme, her iki uç noktaları, belirtilen boyutlarını meydana gelebilecek toplu işlemdeki bir çakışma eklenir. Bu, iki işlenen toplu işlem davranışları arasında belirtilen en az bir toplu iş boyutu kullanarak toplu işleme uygulayarak çözülür. Uç noktalardan biri işlenen toplu işleme belirtmiyor Bu senaryoda, ardından her iki bitiş toplu işleme kullanmanız gerekir değil.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl belirtileceğini gösterir `TransactedBatchingBehavior` bir yapılandırma dosyası.  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="TransactedBatchingBehavior"
              maxBatchSize="100" />
  </endpointBehaviors>
</behaviors>
```  
  
 Aşağıdaki örnek nasıl belirtileceğini gösterir <xref:System.ServiceModel.Description.TransactedBatchingBehavior> kod.  
  
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

- [Kuyruklar Genel Bakış](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [WCF'de Kuyruğa Alma](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
