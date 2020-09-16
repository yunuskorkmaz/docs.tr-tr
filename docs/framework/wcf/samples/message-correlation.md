---
title: İleti Bağıntısı
ms.date: 03/30/2017
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
ms.openlocfilehash: c6c68ec36ecee294aa217f77f462dcea31f1e211
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557976"
---
# <a name="message-correlation"></a>İleti Bağıntısı

Bu örnek, bir Message Queuing (MSMQ) uygulamasının bir Windows Communication Foundation (WCF) hizmetine nasıl MSMQ iletisi gönderebileceğinizi ve iletilerin istek/yanıt senaryosunda gönderici ve alıcı uygulamaları arasında nasıl bağıntılı olduğunu gösterir. Bu örnek MsmqIntegrationBinding bağlamasını kullanır. Bu durumda hizmet, sıraya alınan iletileri alan hizmeti gözlemlemeye olanak sağlayan, kendinden konak bir konsol uygulamasıdır. k

 Hizmet gönderenden alınan iletiyi işler ve gönderene bir yanıt iletisi gönderir. Gönderen yanıtı, aldığı isteği ilk gönderdiği istek ile ilişkilendirir. `MessageID`İletinin ve `CorrelationID` Özellikleri, istek ve yanıt iletilerini ilişkilendirmek için kullanılır.

 `IOrderProcessor`Hizmet sözleşmesi, sıraya alma ile kullanılmak üzere uygun tek yönlü bir hizmet işlemi tanımlar. Bir MSMQ iletisinde eylem üst bilgisi yok, bu nedenle farklı MSMQ iletilerini işlem sözleşmelerine otomatik olarak eşlemek mümkün değildir. Bu nedenle, bu durumda yalnızca bir işlem sözleşmesi olabilir. Hizmette daha fazla işlem sözleşmesi tanımlamak istiyorsanız, uygulamanın hangi işlem sözleşmesinin gönderileceğine karar vermek için MSMQ iletisindeki hangi üstbilginin (örneğin, etiket veya correlationID) kullanılabileceği bilgisini sağlaması gerekir.

 MSMQ iletisi ayrıca, hangi üst bilgilerin işlem sözleşmesinin farklı parametreleriyle eşlendiği bilgisini içermez. Bu nedenle, işlem sözleşmesinde yalnızca bir parametre olabilir. Parametresi <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> , TEMELDEKI MSMQ iletisini içeren türüdür. Sınıftaki "T" türü, `MsmqMessage<T>` MSMQ ileti gövdesinde seri hale getirilen verileri temsil eder. Bu örnekte, `PurchaseOrder` tür MSMQ ileti gövdesinde serileştirilir.

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 Hizmet işlemi, satın alma siparişini işler ve hizmet konsolu penceresinde satın alma siparişinin içeriğini ve durumunu görüntüler. , <xref:System.ServiceModel.OperationBehaviorAttribute> İşlemi sıraya sahip bir işlemde Enlist olarak yapılandırır ve işlem geri döndüğünde işlemin tamamlandığını işaretler. , `PurchaseOrder` Hizmet tarafından işlenmesi gereken sipariş ayrıntılarını içerir.

```csharp
// Service class that implements the service contract.
public class OrderProcessorService : IOrderProcessor
{
   [OperationBehavior(TransactionScopeRequired = true,
          TransactionAutoComplete = true)]
   public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> ordermsg)
   {
       PurchaseOrder po = (PurchaseOrder)ordermsg.Body;
       Random statusIndexer = new Random();
       po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];
       Console.WriteLine("Processing {0} ", po);
       //Send a response to the client that the order has been received
         and is pending fullfillment.
       SendResponse(ordermsg);
    }

    private void SendResponse(MsmqMessage<PurchaseOrder> ordermsg)
    {
        OrderResponseClient client = new OrderResponseClient("OrderResponseEndpoint");

        //Set the correlation ID such that the client can correlate the response to the order.
        MsmqMessage<PurchaseOrder> orderResponsemsg = new MsmqMessage<PurchaseOrder>(ordermsg.Body);
        orderResponsemsg.CorrelationId = ordermsg.Id;
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            client.SendOrderResponse(orderResponsemsg);
            scope.Complete();
        }

        client.Close();
    }
}
```

 Hizmet, `OrderResponseClient` MSMQ iletisini sıraya göndermek için özel bir istemci kullanır. İletiyi alan ve işleyen uygulama bir WCF uygulaması değil bir MSMQ uygulaması olduğundan, iki uygulama arasında örtük bir hizmet sözleşmesi yoktur. Bu nedenle, Bu senaryodaki Svcutil.exe aracını kullanarak bir ara sunucu oluşturmuyoruz.

 Özel proxy temelde, `msmqIntegrationBinding` ileti göndermek için bağlamayı kullanan tüm WCF uygulamaları için aynıdır. Diğer proxy 'lerin aksine, bir dizi hizmet işlemi içermez. Yalnızca bir ileti gönder işlemidir.

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IOrderResponse
{

    [System.ServiceModel.OperationContractAttribute(IsOneWay = true, Action = "*")]
    void SendOrderResponse(MsmqMessage<PurchaseOrder> msg);
}

public partial class OrderResponseClient : System.ServiceModel.ClientBase<IOrderResponse>, IOrderResponse
{

    public OrderResponseClient()
    { }

    public OrderResponseClient(string configurationName)
        : base(configurationName)
    { }

    public OrderResponseClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)
        : base(binding, address)
    { }

    public void SendOrderResponse(MsmqMessage<PurchaseOrder> msg)
    {
        base.Channel.SendOrderResponse(msg);
    }
}
```

 Hizmet kendi kendine barındırılır. MSMQ tümleştirme taşıyıcısı kullanılırken kullanılan sıranın önceden oluşturulması gerekir. Bu, el ile veya kod aracılığıyla yapılabilir. Bu örnekte hizmet, <xref:System.Messaging> sıranın varlığını denetlemek ve gerekirse oluşturmak için kod içerir. Sıra adı yapılandırma dosyasından okundu.

```csharp
public static void Main()
{
       // Get the MSMQ queue name from application settings in configuration.
      string queueName =
                ConfigurationManager.AppSettings["orderQueueName"];
      // Create the transacted MSMQ queue if necessary.
      if (!MessageQueue.Exists(queueName))
                MessageQueue.Create(queueName, true);
     // Create a ServiceHost for the OrderProcessorService type.
     using (ServiceHost serviceHost = new
                   ServiceHost(typeof(OrderProcessorService)))
     {
            serviceHost.Open();
            // The service can now be accessed.
            Console.WriteLine("The service is ready.");
            Console.WriteLine("Press <ENTER> to terminate service.");
            Console.ReadLine();
            // Close the ServiceHost to shutdown the service.
            serviceHost.Close();
      }
}
```

 Sıra isteklerinin gönderildiği MSMQ kuyruğu, yapılandırma dosyasının appSettings bölümünde belirtilmiştir. İstemci ve hizmet uç noktaları, yapılandırma dosyasının System. serviceModel bölümünde tanımlanmıştır. Her ikisi de `msmqIntegrationbinding` bağlamayı belirtir.

```xml
<appSettings>
  <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>

<system.serviceModel>
  <client>
    <endpoint    name="OrderResponseEndpoint"
              address="msmq.formatname:DIRECT=OS:.\private$\OrderResponse"
              binding="msmqIntegrationBinding"
              bindingConfiguration="OrderProcessorBinding"
              contract="Microsoft.ServiceModel.Samples.IOrderResponse">
    </endpoint>
  </client>

  <services>
    <service
      name="Microsoft.ServiceModel.Samples.OrderProcessorService">
      <endpoint address="msmq.formatname:DIRECT=OS:.\private$\Orders"
                            binding="msmqIntegrationBinding"
                bindingConfiguration="OrderProcessorBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor">
      </endpoint>
    </service>
  </services>

  <bindings>
    <msmqIntegrationBinding>
      <binding name="OrderProcessorBinding" >
        <security mode="None" />
      </binding>
    </msmqIntegrationBinding>
  </bindings>

</system.serviceModel>
```

 İstemci uygulaması, <xref:System.Messaging> kuyruğa dayanıklı ve işlemsel bir ileti göndermek için kullanır. İletinin gövdesinde satınalma siparişi bulunur.

```csharp
static void PlaceOrder()
{
    //Connect to the queue
    MessageQueue orderQueue =
            new MessageQueue(
                    ConfigurationManager.AppSettings["orderQueueName"])
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

    Message msg = new Message();
    msg.UseDeadLetterQueue = true;
    msg.Body = po;

    //Create a transaction scope.
    using (TransactionScope scope = new
     TransactionScope(TransactionScopeOption.Required))
    {
        // Submit the purchase order.
        orderQueue.Send(msg, MessageQueueTransactionType.Automatic);
        // Complete the transaction.
        scope.Complete();
    }
    //Save the messageID for order response correlation.
    orderMessageID = msg.Id;
    Console.WriteLine("Placed the order, waiting for response...");
}
```

 Aşağıdaki örnek yapılandırmada gösterildiği gibi, sipariş yanıtlarının alındığı MSMQ kuyruğu yapılandırma dosyasının appSettings bölümünde belirtilmiştir.

> [!NOTE]
> Sıra adı, yerel bilgisayar için bir nokta (.) ve kendi yolunda ters eğik çizgi ayırıcılar kullanır. WCF uç noktası adresi bir MSMQ. formatname şeması belirtir ve yerel bilgisayar için "localhost" kullanır. Düzgün biçimlendirilmiş bir biçim adı, MSMQ yönergelerine göre URI 'deki MSMQ. formatname ' i izler.

```xml
<appSettings>
    <add key=" orderResponseQueueName" value=".\private$\Orders" />
</appSettings>
```

 İstemci uygulaması, `messageID` hizmetine gönderdiği sipariş isteği iletisini kaydeder ve hizmetten bir yanıt bekler. Bir yanıt kuyruğa ulaştığında, istemci, `correlationID` `messageID` istemcinin hizmete ilk olarak gönderdiği sipariş iletisini içeren ileti özelliğini kullanarak gönderdiği sipariş iletisiyle ilişkilendirir.

```csharp
static void DisplayOrderStatus()
{
    MessageQueue orderResponseQueue = new
     MessageQueue(ConfigurationManager.AppSettings
                  ["orderResponseQueueName"]);
    //Create a transaction scope.
    bool responseReceived = false;
    orderResponseQueue.MessageReadPropertyFilter.CorrelationId = true;
    while (!responseReceived)
    {
       Message responseMsg;
       using (TransactionScope scope2 = new
         TransactionScope(TransactionScopeOption.Required))
       {
          //Receive the Order Response message.
          responseMsg =
              orderResponseQueue.Receive
                   (MessageQueueTransactionType.Automatic);
          scope2.Complete();
     }
     responseMsg.Formatter = new
     System.Messaging.XmlMessageFormatter(new Type[] {
         typeof(PurchaseOrder) });
     PurchaseOrder responsepo = (PurchaseOrder)responseMsg.Body;
    //Check if the response is for the order placed.
    if (orderMessageID == responseMsg.CorrelationId)
    {
       responseReceived = true;
       Console.WriteLine("Status of current Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
    else
    {
       Console.WriteLine("Status of previous Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
  }
}
```

 Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencereleri içinde görüntülenir. Hizmetin istemciden ileti alacağını görebilir ve istemciye geri yanıt gönderir. İstemci, hizmetten alınan yanıtı görüntüler. Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.

> [!NOTE]
> Bu örnek Message Queuing (MSMQ) yüklemesini gerektirir. Ayrıca bkz. bölümünde MSMQ yükleme yönergelerine bakın.

## <a name="set-up-build-and-run-the-sample"></a>Örneği kurma, oluşturma ve çalıştırma

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Önce hizmet çalıştırıldığında, sıranın mevcut olduğundan emin olmak için kontrol edilir. Sıra yoksa, hizmet bir tane oluşturur. Kuyruğu oluşturmak için önce hizmeti çalıştırabilir veya MSMQ kuyruğu Yöneticisi aracılığıyla bir tane oluşturabilirsiniz. Windows 2008 ' de bir sıra oluşturmak için aşağıdaki adımları izleyin.

    1. Visual Studio 2012 ' de Sunucu Yöneticisi açın.

    2. **Özellikler** sekmesini genişletin.

    3. **Özel Ileti kuyrukları**' ne sağ tıklayıp **Yeni**, **özel kuyruk**' u seçin.

    4. **İşlem** kutusunu işaretleyin.

    5. `ServiceModelSamplesTransacted`Yeni kuyruğun adı olarak girin.

3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.

4. Örneği tek bilgisayarlı bir yapılandırmada çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.

## <a name="run-the-sample-across-computers"></a>Örneği bilgisayarlar arasında çalıştırma

1. Hizmet programı dosyalarını dile özgü klasörün altındaki \service\bin\ klasöründen hizmet bilgisayarına kopyalayın.

2. İstemci program dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci bilgisayara kopyalayın.

3. Client.exe.config dosyasında, Ordersıraadı ' nı "." yerine hizmet bilgisayar adını belirtecek şekilde değiştirin.

4. Service.exe.config dosyasında, istemci uç noktası adresini "." yerine istemci bilgisayar adını belirtecek şekilde değiştirin.

5. Hizmet bilgisayarında, bir komut isteminden Service.exe başlatın.

6. İstemci bilgisayarda, bir komut isteminden Client.exe başlatın.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`

## <a name="see-also"></a>Ayrıca bkz.

- [WCF'de Kuyruğa Alma](../feature-details/queuing-in-wcf.md)
- [Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))
