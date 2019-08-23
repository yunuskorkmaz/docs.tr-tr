---
title: Windows Communication Foundation'dan İleti Kuyruğuna
ms.date: 03/30/2017
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
ms.openlocfilehash: 083e652a0924ffed272387a4974ec600073cef2f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966729"
---
# <a name="windows-communication-foundation-to-message-queuing"></a>Windows Communication Foundation'dan İleti Kuyruğuna
Bu örnek, bir Windows Communication Foundation (WCF) uygulamasının bir Message Queuing (MSMQ) uygulamasına nasıl ileti gönderebileceğinizi gösterir. Hizmet, sıraya alınan iletileri alma hizmetini gözlemlemeye olanak sağlayan, kendinden konak bir konsol uygulamasıdır. Hizmetin ve istemcinin aynı anda çalışıyor olması gerekmez.

 Hizmet kuyruk ve işlem siparişlerinden iletileri alır. Hizmet bir işlem kuyruğu oluşturur ve aşağıdaki örnek kodda gösterildiği gibi ileti alma iletisi işleyicisini ayarlar.

```csharp
static void Main(string[] args)
{
    if (!MessageQueue.Exists(
              ConfigurationManager.AppSettings["queueName"]))
       MessageQueue.Create(
           ConfigurationManager.AppSettings["queueName"], true);
        //Connect to the queue
        MessageQueue Queue = new
    MessageQueue(ConfigurationManager.AppSettings["queueName"]);
    Queue.ReceiveCompleted +=
                 new ReceiveCompletedEventHandler(ProcessOrder);
    Queue.BeginReceive();
    Console.WriteLine("Order Service is running");
    Console.ReadLine();
}
```

 Kuyrukta bir ileti alındığında ileti işleyicisi `ProcessOrder` çağrılır.

```csharp
public static void ProcessOrder(Object source,
    ReceiveCompletedEventArgs asyncResult)
{
    try
    {
        // Connect to the queue.
        MessageQueue Queue = (MessageQueue)source;
        // End the asynchronous receive operation.
        System.Messaging.Message msg =
                     Queue.EndReceive(asyncResult.AsyncResult);
        msg.Formatter = new System.Messaging.XmlMessageFormatter(
                                new Type[] { typeof(PurchaseOrder) });
        PurchaseOrder po = (PurchaseOrder) msg.Body;
        Random statusIndexer = new Random();
        po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];
        Console.WriteLine("Processing {0} ", po);
        Queue.BeginReceive();
    }
    catch (System.Exception ex)
    {
        Console.WriteLine(ex.Message);
    }

}
```

 Hizmet MSMQ ileti gövdesinden ayıklar `ProcessOrder` ve siparişi işler.

 MSMQ kuyruğu adı, aşağıdaki örnek yapılandırmada gösterildiği gibi, yapılandırma dosyasının bir appSettings bölümünde belirtilmiştir.

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

> [!NOTE]
> Sıra adı, yerel bilgisayar için bir nokta (.) ve kendi yolunda ters eğik çizgi ayırıcılar kullanır.

 İstemci bir satınalma siparişi oluşturur ve aşağıdaki örnek kodda gösterildiği gibi, satın alma sırasını bir işlemin kapsamı içinde gönderir.

```csharp
// Create the purchase order
PurchaseOrder po = new PurchaseOrder();
// Fill in the details
...

OrderProcessorClient client = new OrderProcessorClient("OrderResponseEndpoint");

MsmqMessage<PurchaseOrder> ordermsg = new MsmqMessage<PurchaseOrder>(po);
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{
    client.SubmitPurchaseOrder(ordermsg);
    scope.Complete();
}
Console.WriteLine("Order has been submitted:{0}", po);

//Closing the client gracefully closes the connection and cleans up resources
client.Close();
```

 İstemci, MSMQ iletisini sıraya göndermek için özel bir istemci sırayla kullanır. İletiyi alan ve işleyen uygulama bir WCF uygulaması değil bir MSMQ uygulaması olduğundan, iki uygulama arasında örtük bir hizmet sözleşmesi yoktur. Bu nedenle, bu senaryoda Svcutil. exe aracını kullanarak bir ara sunucu oluşturmuyoruz.

 Özel istemci temelde, ileti göndermek için `MsmqIntegration` bağlamayı kullanan tüm WCF uygulamaları için aynıdır. Diğer istemcilerin aksine, bir dizi hizmet işlemi içermez. Yalnızca bir ileti gönder işlemidir.

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}

public partial class OrderProcessorClient : System.ServiceModel.ClientBase<IOrderProcessor>, IOrderProcessor
{
    public OrderProcessorClient(){}

    public OrderProcessorClient(string configurationName)
        : base(configurationName)
    { }

    public OrderProcessorClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)
        : base(binding, address)
    { }

    public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)
    {
        base.Channel.SubmitPurchaseOrder(msg);
    }
}
```

 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencereleri içinde görüntülenir. Hizmetin istemciden ileti alacağını görebilirsiniz. Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın. Kuyruk kullanımda olduğu için istemci ve hizmetin aynı anda çalışmaya ve çalışır durumda olmadığından emin olun. Örneğin, istemcisini çalıştırabilir, kapatabilir ve ardından hizmeti başlatabilir ve yine de iletilerini alabilir.

> [!NOTE]
> Bu örnek Message Queuing yüklenmesini gerektirir. [Message Queuing](https://go.microsoft.com/fwlink/?LinkId=94968)'teki yükleme yönergelerine bakın.  
  
### <a name="to-setup-build-and-run-the-sample"></a>Örneği kurmak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Önce hizmet çalıştırıldığında, sıranın mevcut olduğundan emin olmak için kontrol edilir. Sıra yoksa, hizmet bir tane oluşturur. Kuyruğu oluşturmak için önce hizmeti çalıştırabilir veya MSMQ kuyruğu Yöneticisi aracılığıyla bir tane oluşturabilirsiniz. Windows 2008 ' de bir sıra oluşturmak için aşağıdaki adımları izleyin.  
  
    1. Visual Studio 2012 ' de Sunucu Yöneticisi açın.  
  
    2. **Özellikler** sekmesini genişletin.  
  
    3. **Özel Ileti kuyrukları**' ne sağ tıklayıp **Yeni**, **özel kuyruk**' u seçin.  
  
    4. **İşlem** kutusunu işaretleyin.  
  
    5. Yeni `ServiceModelSamplesTransacted` kuyruğun adı olarak girin.  
  
3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
4. Örneği tek bilgisayarlı bir yapılandırmada çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
### <a name="to-run-the-sample-across-computers"></a>Örneği bilgisayarlar arasında çalıştırmak için  
  
1. Hizmet programı dosyalarını dile özgü klasörün altındaki \service\bin\ klasöründen hizmet bilgisayarına kopyalayın.  
  
2. İstemci program dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci bilgisayara kopyalayın.  
  
3. Client. exe. config dosyasında, istemci uç noktası adresini "." yerine hizmet bilgisayar adını belirtecek şekilde değiştirin.  
  
4. Hizmet bilgisayarında, bir komut isteminden Service. exe ' yi başlatın.  
  
5. İstemci bilgisayarda, bir komut isteminden Client. exe ' yi başlatın.  
  
> [!IMPORTANT]
>  Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: WCF uç noktaları ve Message Queuing uygulamalarla Exchange Iletileri](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [Message Queuing](https://go.microsoft.com/fwlink/?LinkId=94968)
