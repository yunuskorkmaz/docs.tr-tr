---
title: Bir İşlemde Toplu İleti İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- batching messages [WCF]
ms.assetid: 53305392-e82e-4e89-aedc-3efb6ebcd28c
ms.openlocfilehash: be9661525c960ae558d21b05781007b81b8a3f56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185445"
---
# <a name="batching-messages-in-a-transaction"></a>Bir İşlemde Toplu İleti İşleme
Sıraya alınan uygulamalar, iletilerin doğruluğunu ve güvenilir bir şekilde teslim edilmesini sağlamak için hareketleri kullanır. Ancak işlemler pahalı işlemlerdir ve ileti iş bilgilerini önemli ölçüde azaltabilir. İleti bilgisini geliştirmenin bir yolu, bir uygulamanın tek bir işlem içinde birden çok iletiyi okumasını ve işlemesini sağlamaktır. Dengeleme performans ve kurtarma arasındadır: toplu işteki ileti sayısı arttıkça, hareketler geri alınırsa gerekli kurtarma çalışması miktarı da artar. İletileri bir işlemde toplu olarak gruplandırma ile oturumlar arasındaki farkı not etmek önemlidir. *Oturum,* tek bir uygulama tarafından işlenen ve tek bir birim olarak işlenen ilgili iletilerin gruplandırmasıdır. Oturumlar genellikle ilgili iletiler grubu birlikte işlenmesi gerektiğinde kullanılır. Bunun bir örneği bir online alışveriş Web sitesidir. *Toplu iş,* birden çok ilgisiz iletiyi ileti alım sını artıran bir şekilde işlemek için kullanılır. Oturumlar hakkında daha fazla bilgi için, [Oturumda Sıraya Alınan İletileri Gruplandırma'ya](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)bakın. Toplu işteki iletiler de tek bir uygulama tarafından işlenir ve tek bir birim olarak işlenir, ancak toplu işteki iletiler arasında ilişki olmayabilir. İletileri bir işlemde toplu olarak gruplandırmak, uygulamanın çalışma şeklini değiştirmeyen bir optimizasyondur.  
  
## <a name="entering-batching-mode"></a>Toplu İşlem Moduna Girme  
 Uç <xref:System.ServiceModel.Description.TransactedBatchingBehavior> nokta davranışı toplu işlemi denetler. Bu son nokta davranışını bir hizmet bitiş noktasına eklemek, Windows Communication Foundation'a (WCF) bir işlemdeki toplu iletilere bildirir. Tüm iletiler bir hareket gerektirmez, bu nedenle yalnızca bir hareket gerektiren iletiler toplu iş `TransactionScopeRequired`  =  `true` haline `TransactionAutoComplete`  =  `true` yerleştirilir ve yalnızca işlemlerden gönderilen iletiler toplu iş için işaretlenir ve kabul edilir. Hizmet `TransactionScopeRequired`  =  `false` sözleşmesindeki tüm işlemler işaretlenirse ve `TransactionAutoComplete`  =  `false`,toplu işlem modu na girilir.  
  
## <a name="committing-a-transaction"></a>İşlem Gerçekleştirme  
 Toplu işlem aşağıdakilere göre işlenir:  
  
- `MaxBatchSize`. Davranışın <xref:System.ServiceModel.Description.TransactedBatchingBehavior> bir özelliği. Bu özellik, toplu iş haline yerleştirilen en fazla ileti sayısını belirler. Bu sayıya ulaşıldığında, toplu iş işlenir. Bu değer sıkı bir sınır değildir, bu sayıda ileti almadan önce bir toplu iş işlemek mümkündür.  
  
- `Transaction Timeout`. İşlemin zaman aşımının yüzde 80'i geçtikten sonra, toplu iş işlenir ve yeni bir toplu iş oluşturulur. Bu, bir işlemin tamamlanması için verilen sürenin yüzde 20'si veya daha azı kalırsa, toplu iş işleminin işlendiği anlamına gelir.  
  
- `TransactionScopeRequired`. Bir ileti toplu işlemini işlerken, WCF `TransactionScopeRequired`  =  `false`bir tane bulursa, toplu iş yapar `TransactionScopeRequired`  =  `true` ve ilk iletinin `TransactionAutoComplete`  =  `true`alındığı ilk toplu iş ve .  
  
- Sırada başka ileti yoksa, ulaşılamasa veya işlemin zaman `MaxBatchSize` aşımının yüzde 80'i geçmemiş olsa bile geçerli toplu iş işlenir.  
  
## <a name="leaving-batching-mode"></a>Toplu İşlem Modundan Çıkma  
 Toplu iş teki bir ileti işlemin iptaline neden oluyorsa, aşağıdaki adımlar oluşur:  
  
1. İletilerin tüm toplu geri alınır.  
  
2. İletiler, okunan ileti sayısı en fazla toplu iş boyutunun iki katını aşana kadar teker teker okunur.  
  
3. Toplu iş modu yeniden girilir.  
  
## <a name="choosing-the-batch-size"></a>Toplu İşlem Boyutunu Seçme  
 Toplu iş boyutu uygulamaya bağlıdır. Ampirik yöntem uygulama için en uygun toplu iş boyutuna ulaşmanın en iyi yoludur. Uygulamanızın gerçek dağıtım modeline göre boyutu seçmek için bir toplu iş boyutu seçerken hatırlamanız önemlidir. Örneğin, uygulamayı dağıtırken, uzak bir makinede bir SQL sunucusuna ve kuyruğa ve SQL sunucusuna yayılan bir işlem gerekiyorsa, toplu iş boyutu en iyi bu tam yapılandırmayı çalıştırarak belirlenir.  
  
## <a name="concurrency-and-batching"></a>Eşzamanlılık ve Toplu İşlem  
 İş bilgililiği artırmak için, aynı anda birçok toplu iş çalıştırabilirsiniz. `ServiceBehaviorAttribute`Ayarlayarak, `ConcurrencyMode.Multiple` eşzamanlı toplu işlemi etkinleştirin.  
  
 *Hizmet azaltma,* hizmette kaç tane en fazla eşzamanlı arama yapılabilir olduğunu belirtmek için kullanılan bir hizmet davranışıdır. Toplu işlerle birlikte kullanıldığında, bu işlem kaç eşzamanlı toplu iş çalıştırılabildiği olarak yorumlanır. Hizmet azaltma ayarlı değilse, WCF varsayılan olarak en fazla eşzamanlı aramaları 16'ya çağırır. Bu nedenle, toplu işleme davranışı varsayılan olarak eklendiyse, aynı anda en fazla 16 toplu iş etkin olabilir. Kapasitenize göre hizmet azaltma ve toplu işlemi ayarlamak en iyisidir. Örneğin, kuyruğda 100 ileti varsa ve toplu işlem isteniyorsa, en fazla eşzamanlı çağrının 16 olarak ayarlanmış olması yararlı değildir, çünkü iş bölümüne bağlı olarak 16 işlem etkin olabilir ve toplu işlemin açık olmamasına benzer. Bu nedenle, performans için ince ayar yaparken, eşzamanlı toplu işlem yok veya doğru servis azaltma boyutuyla eşzamanlı toplu işlem yapın.  
  
## <a name="batching-and-multiple-endpoints"></a>Toplu İşlem ve Çoklu Uç Noktaları  
 Bitiş noktası bir adres ve sözleşmeden oluşur. Aynı bağlamayı paylaşan birden çok uç nokta olabilir. İki uç noktanın aynı bağlamayı paylaşması ve Tek düzen Kaynak Tanımlayıcısı'nı (URI) veya sıra adresini dinlemesi mümkündür. İki uç nokta aynı satırdan okunuyorsa ve her iki uç noktaya da işleyen toplu işleme davranışı eklenirse, belirtilen toplu iş boyutlarında bir çakışma ortaya çıkabilir. Bu, iki işlenmiş toplu işlem davranışı arasında belirtilen en az toplu iş boyutu kullanılarak toplu iş uygulayarak çözülür. Bu senaryoda, uç noktalardan biri işleyen toplu işlemi belirtmezse, her iki uç nokta toplu işleme kullanmaz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, yapılandırma `TransactedBatchingBehavior` dosyasında nasıl belirtilenler gösterilmektedir.  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="TransactedBatchingBehavior"
              maxBatchSize="100" />
  </endpointBehaviors>
</behaviors>
```  
  
 Aşağıdaki örnekte kod nasıl <xref:System.ServiceModel.Description.TransactedBatchingBehavior> belirtilir gösterilmektedir.  
  
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
