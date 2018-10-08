---
title: Windows Communication Foundation'a İleti Kuyruğa Alma
ms.date: 03/30/2017
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
ms.openlocfilehash: cbbbab700a6602fa02160733c383a0fcaa84297b
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850680"
---
# <a name="message-queuing-to-windows-communication-foundation"></a>Windows Communication Foundation'a İleti Kuyruğa Alma
Bu örnek, bir Message Queuing (MSMQ) uygulamasını bir Windows Communication Foundation (WCF) hizmetine bir MSMQ iletisinin nasıl gönderebileceğiniz gösterilir. Hizmeti, sıraya alınan iletileri alma hizmeti gözlemleyin sağlamak için bir şirket içinde barındırılan bir konsol uygulamasıdır.  
  
 Hizmet sözleşme `IOrderProcessor`, kuyruklar ile kullanım için uygun olan bir tek yönlü hizmeti tanımlar. Bir MSMQ iletisinin bir eylem üst bilgisi olmadığından, işlem sözleşmeleri farklı MSMQ iletileri otomatik olarak eşlemeye mümkün değildir. Bu nedenle, yalnızca bir işlem anlaşması olabilir. Hizmeti için birden fazla işlem anlaşması tanımlamak istiyorsanız, uygulamayı dağıtmak için hangi işlem anlaşması karar vermek için (örneğin, etiket veya Correlationıd) MSMQ iletisinin başlığında hangi kullanılabilir bilgi sağlamanız gerekir.
  
 MSMQ iletisinin hangi üstbilgileri da işlem anlaşması farklı parametrelerle eşlenir bilgi içermiyor. Parametre türüdür <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), temel alınan MSMQ iletisi içerir. ' % S'tür "T" içinde <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) sınıfı, MSMQ ileti gövdesine seri verileri temsil eder. Bu örnekte `PurchaseOrder` türü MSMQ ileti gövdesine seri.  
  
 Aşağıdaki örnek kod, sipariş işleme hizmeti, hizmet sözleşmesini gösterir.  

```csharp
// Define a service contract.
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 Kendi kendine barındırılan bir hizmettir. MSMQ kullanırken, kullanılan kuyruk önceden oluşturulmuş olması gerekir. Bu, el ile veya kod aracılığıyla yapılabilir. Bu örnekte, hizmet sırası varlığını denetler ve gerekirse oluşturur. Kuyruk adı yapılandırma dosyasından okunur.

```csharp
public static void Main()
{
    // Get the MSMQ queue name from the application settings in
    // configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];
    // Create the MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName, true);
    …
}
```

 Hizmet oluşturur ve açar bir <xref:System.ServiceModel.ServiceHost> için `OrderProcessorService`aşağıdaki örnek kodda gösterildiği gibi.

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
{
    serviceHost.Open();
    Console.WriteLine("The service is ready.");
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
    serviceHost.Close();
}
```

 MSMQ kuyruk adı, aşağıdaki örnek yapılandırmada gösterildiği gibi bir yapılandırma dosyasının appSettings bölümünde belirtilir.

> [!NOTE]
>  Kuyruk adı, eğik çizgi ayırıcılar yolundaki ve yerel bilgisayar için bir nokta (.) kullanır. WCF uç nokta adresini msmq.formatname düzenini belirtir ve yerel bilgisayar için localhost kullanır. Her MSMQ biçim yönergeleri ele alan adı için kuyruk adresini msmq.formatname düzeni izler.

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

 İstemci uygulama kullanan bir MSMQ uygulamasıdır <xref:System.Messaging.MessageQueue.Send%2A> aşağıdaki örnek kodda gösterildiği gibi kuyruğa, dayanıklı ve işlem tabanlı ileti göndermek için yöntemi.

```csharp
//Connect to the queue.
MessageQueue orderQueue = new MessageQueue(ConfigurationManager.AppSettings["orderQueueName"]);

// Create the purchase order.
PurchaseOrder po = new PurchaseOrder();
po.CustomerId = "somecustomer.com";
po.PONumber = Guid.NewGuid().ToString();

PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();
lineItem1.ProductId = "Blue Widget";
lineItem1.Quantity = 54;
lineItem1.UnitCost = 29.99F;

PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();
lineItem2.ProductId = "Red Widget";
lineItem2.Quantity = 890;
lineItem2.UnitCost = 45.89F;

po.orderLineItems = new PurchaseOrderLineItem[2];
po.orderLineItems[0] = lineItem1;
po.orderLineItems[1] = lineItem2;

// Submit the purchase order.
Message msg = new Message();
msg.Body = po;
//Create a transaction scope.
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{

    orderQueue.Send(msg, MessageQueueTransactionType.Automatic);
    // Complete the transaction.
    scope.Complete();

}
Console.WriteLine("Placed the order:{0}", po);
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hizmet ve istemci konsol pencerelerinde görüntülenir. İstemciden hizmet alma iletileri görebilirsiniz. Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın. Sıraya alma kullanımda olduğundan, istemci ve hizmet aynı zamanda açık ve çalışıyor olması gerekmez, unutmayın. Örneğin, istemcisini çalıştıran, da kapatın ve ardından hizmeti başlatın ve hala iletileri alacaksınız.

### <a name="to-setup-build-and-run-the-sample"></a>Kurulum, derleme ve örneği çalıştırmak için

1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  Hizmet ilk olarak çalıştırılırsa, sıranın mevcut olduğundan emin olun kontrol eder. Kuyruk yoksa, bir hizmeti oluşturacaksınız. İlk sırayı oluşturmak için hizmet çalıştırabileceğiniz veya bir MSMQ Kuyruk Yöneticisi ile oluşturabilirsiniz. Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.

    1.  Visual Studio 2012'de Sunucu Yöneticisi'ni açın.

    2.  Genişletin **özellikleri** sekmesi.

    3.  Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.

    4.  Denetleme **işlem** kutusu.

    5.  Girin `ServiceModelSamplesTransacted` yeni Kuyruğun adı.

3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).

4.  Tek bilgisayarlı yapılandırmada örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).

### <a name="to-run-the-sample-across-computers"></a>Bilgisayarlar arasında örneği çalıştırmak için

1.  Hizmet program dosyaları \service\bin\ klasöründen dile özgü klasörü altında hizmet bilgisayara kopyalayın.

2.  İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörünün altındaki istemci bilgisayara kopyalayın.

3.  Yerine hizmeti bilgisayarın adını belirtmek için orderQueueName Client.exe.config dosyasında değiştirme ".".

4.  Hizmet bilgisayarda bir komut istemi'nden Service.exe başlatın.

5.  İstemci bilgisayarda bir komut istemi'nden Client.exe başlatın.

> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF'de Kuyruklar](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [Message Queuing](https://go.microsoft.com/fwlink/?LinkId=94968)
