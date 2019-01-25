---
title: Windows Communication Foundation'dan İleti Kuyruğuna
ms.date: 03/30/2017
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
ms.openlocfilehash: abe033846aad061df2130f16f732215fb1416f1a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710527"
---
# <a name="windows-communication-foundation-to-message-queuing"></a>Windows Communication Foundation'dan İleti Kuyruğuna
Bu örnek, bir Windows Communication Foundation (WCF) uygulaması bir Message Queuing (MSMQ) uygulaması için bir ileti nasıl gönderebileceğiniz gösterilir. Hizmeti, sıraya alınan iletileri alma hizmeti gözlemleyin sağlamak için bir şirket içinde barındırılan bir konsol uygulamasıdır. Hizmet ve istemci aynı anda çalıştırılması gerekmez.

 Hizmet iletileri kuyruktan alır ve siparişler işler. Hizmet, bir işlem kuyruğu oluşturur ve bir ileti alındı ileti işleyicisini, aşağıdaki örnek kodda gösterildiği gibi ayarlar.

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

 Ne zaman bir ileti alındığında kuyrukta ileti işleyicisi `ProcessOrder` çağrılır.

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

 Hizmet ayıklar `ProcessOrder` MSMQ İleti gövdesi ve sırayla işler.

 MSMQ kuyruk adı, aşağıdaki örnek yapılandırmada gösterildiği gibi bir yapılandırma dosyasının appSettings bölümünde belirtilir.

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

> [!NOTE]
>  Kuyruk adı, eğik çizgi ayırıcılar yolundaki ve yerel bilgisayar için bir nokta (.) kullanır.

 İstemci, bir sipariş oluşturur ve aşağıdaki örnek kodda gösterildiği gibi bir işlem kapsamında satın alma siparişi gönderir.

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

 İstemci bir özel istemci sırayla MSMQ ileti sırasına göndermek için kullanır. Alan ve iletiyi işleyen bir uygulama bir MSMQ uygulama ve WCF uygulaması olduğundan iki uygulama arasında örtük hizmet sözleşme yok. Bu nedenle, bu senaryoda Svcutil.exe aracını kullanarak bir proxy oluşturamıyoruz.

 Özel istemci temel olarak kullanan tüm WCF uygulamaları aynı olduğundan `MsmqIntegration` ileti göndermek için bağlama. Diğer istemcilerden farklı olarak, bir dizi hizmet işlemleri içermez. Bir gönderme iletisi yalnızca işlemdir.

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

 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hizmet ve istemci konsol pencerelerinde görüntülenir. İstemciden hizmet alma iletileri görebilirsiniz. Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın. Sıraya alma kullanımda olduğundan, istemci ve hizmet aynı zamanda açık ve çalışıyor olması gerekmez, unutmayın. Örneğin, istemcisini çalıştıran, da kapatın ve ardından hizmeti başlatın ve hala iletileri alacaksınız.

> [!NOTE]
>  Bu örnek, Message Queuing yüklenmesini gerektirir. ' Ndaki yükleme yönergelerine bakın [Message Queuing](https://go.microsoft.com/fwlink/?LinkId=94968).  
  
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
  
3.  Client.exe.config dosyasında yerine hizmeti bilgisayarın adını belirtmek için istemci uç nokta adresini Değiştir ".".  
  
4.  Hizmet bilgisayarda bir komut istemi'nden Service.exe başlatın.  
  
5.  İstemci bilgisayarda bir komut istemi'nden Client.exe başlatın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: WCF uç noktaları ve ileti uygulamaları ile Exchange ileti](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [Message Queuing](https://go.microsoft.com/fwlink/?LinkId=94968)
