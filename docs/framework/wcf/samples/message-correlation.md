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
# <a name="message-correlation"></a><span data-ttu-id="9f321-102">İleti Bağıntısı</span><span class="sxs-lookup"><span data-stu-id="9f321-102">Message Correlation</span></span>

<span data-ttu-id="9f321-103">Bu örnek, bir Message Queuing (MSMQ) uygulamasının bir Windows Communication Foundation (WCF) hizmetine nasıl MSMQ iletisi gönderebileceğinizi ve iletilerin istek/yanıt senaryosunda gönderici ve alıcı uygulamaları arasında nasıl bağıntılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f321-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service and how messages can be correlated between sender and receiver applications in a request/response scenario.</span></span> <span data-ttu-id="9f321-104">Bu örnek MsmqIntegrationBinding bağlamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="9f321-104">This sample uses the msmqIntegrationBinding binding.</span></span> <span data-ttu-id="9f321-105">Bu durumda hizmet, sıraya alınan iletileri alan hizmeti gözlemlemeye olanak sağlayan, kendinden konak bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="9f321-105">The service in this case is a self-hosted console application to allow you to observe the service that receives queued messages.</span></span> <span data-ttu-id="9f321-106">k</span><span class="sxs-lookup"><span data-stu-id="9f321-106">k</span></span>

 <span data-ttu-id="9f321-107">Hizmet gönderenden alınan iletiyi işler ve gönderene bir yanıt iletisi gönderir.</span><span class="sxs-lookup"><span data-stu-id="9f321-107">The service processes the message received from the sender and sends a response message back to the sender.</span></span> <span data-ttu-id="9f321-108">Gönderen yanıtı, aldığı isteği ilk gönderdiği istek ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="9f321-108">The sender correlates the response it received to the request it sent originally.</span></span> <span data-ttu-id="9f321-109">`MessageID`İletinin ve `CorrelationID` Özellikleri, istek ve yanıt iletilerini ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9f321-109">The `MessageID` and `CorrelationID` properties of the message are used to correlate the request and response messages.</span></span>

 <span data-ttu-id="9f321-110">`IOrderProcessor`Hizmet sözleşmesi, sıraya alma ile kullanılmak üzere uygun tek yönlü bir hizmet işlemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9f321-110">The `IOrderProcessor` service contract defines a one-way service operation that is suitable for use with queuing.</span></span> <span data-ttu-id="9f321-111">Bir MSMQ iletisinde eylem üst bilgisi yok, bu nedenle farklı MSMQ iletilerini işlem sözleşmelerine otomatik olarak eşlemek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="9f321-111">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="9f321-112">Bu nedenle, bu durumda yalnızca bir işlem sözleşmesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="9f321-112">Therefore, there can be only one operation contract in this case.</span></span> <span data-ttu-id="9f321-113">Hizmette daha fazla işlem sözleşmesi tanımlamak istiyorsanız, uygulamanın hangi işlem sözleşmesinin gönderileceğine karar vermek için MSMQ iletisindeki hangi üstbilginin (örneğin, etiket veya correlationID) kullanılabileceği bilgisini sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f321-113">If you want to define more operation contracts in the service, the application must provide information as to which header in the MSMQ message (for example, the label, or correlationID) can be used to decide which operation contract to dispatch.</span></span>

 <span data-ttu-id="9f321-114">MSMQ iletisi ayrıca, hangi üst bilgilerin işlem sözleşmesinin farklı parametreleriyle eşlendiği bilgisini içermez.</span><span class="sxs-lookup"><span data-stu-id="9f321-114">The MSMQ message also does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="9f321-115">Bu nedenle, işlem sözleşmesinde yalnızca bir parametre olabilir.</span><span class="sxs-lookup"><span data-stu-id="9f321-115">Therefore, there can be only one parameter in the operation contract.</span></span> <span data-ttu-id="9f321-116">Parametresi <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> , TEMELDEKI MSMQ iletisini içeren türüdür.</span><span class="sxs-lookup"><span data-stu-id="9f321-116">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, which contains the underlying MSMQ message.</span></span> <span data-ttu-id="9f321-117">Sınıftaki "T" türü, `MsmqMessage<T>` MSMQ ileti gövdesinde seri hale getirilen verileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9f321-117">The type "T" in the `MsmqMessage<T>` class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="9f321-118">Bu örnekte, `PurchaseOrder` tür MSMQ ileti gövdesinde serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="9f321-118">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 <span data-ttu-id="9f321-119">Hizmet işlemi, satın alma siparişini işler ve hizmet konsolu penceresinde satın alma siparişinin içeriğini ve durumunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9f321-119">The service operation processes the purchase order and displays the contents of the purchase order and its status in the service console window.</span></span> <span data-ttu-id="9f321-120">, <xref:System.ServiceModel.OperationBehaviorAttribute> İşlemi sıraya sahip bir işlemde Enlist olarak yapılandırır ve işlem geri döndüğünde işlemin tamamlandığını işaretler.</span><span class="sxs-lookup"><span data-stu-id="9f321-120">The <xref:System.ServiceModel.OperationBehaviorAttribute> configures the operation to enlist in a transaction with the queue and to mark the transaction complete when the operation returns.</span></span> <span data-ttu-id="9f321-121">, `PurchaseOrder` Hizmet tarafından işlenmesi gereken sipariş ayrıntılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="9f321-121">The `PurchaseOrder` contains the order details that must be processed by the service.</span></span>

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

 <span data-ttu-id="9f321-122">Hizmet, `OrderResponseClient` MSMQ iletisini sıraya göndermek için özel bir istemci kullanır.</span><span class="sxs-lookup"><span data-stu-id="9f321-122">The service uses a custom client `OrderResponseClient` to send the MSMQ message to the queue.</span></span> <span data-ttu-id="9f321-123">İletiyi alan ve işleyen uygulama bir WCF uygulaması değil bir MSMQ uygulaması olduğundan, iki uygulama arasında örtük bir hizmet sözleşmesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9f321-123">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="9f321-124">Bu nedenle, Bu senaryodaki Svcutil.exe aracını kullanarak bir ara sunucu oluşturmuyoruz.</span><span class="sxs-lookup"><span data-stu-id="9f321-124">So we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="9f321-125">Özel proxy temelde, `msmqIntegrationBinding` ileti göndermek için bağlamayı kullanan tüm WCF uygulamaları için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="9f321-125">The custom proxy is essentially the same for all WCF applications that use the `msmqIntegrationBinding` binding to send messages.</span></span> <span data-ttu-id="9f321-126">Diğer proxy 'lerin aksine, bir dizi hizmet işlemi içermez.</span><span class="sxs-lookup"><span data-stu-id="9f321-126">Unlike other proxies, it does not include a range of service operations.</span></span> <span data-ttu-id="9f321-127">Yalnızca bir ileti gönder işlemidir.</span><span class="sxs-lookup"><span data-stu-id="9f321-127">It is a submit message operation only.</span></span>

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

 <span data-ttu-id="9f321-128">Hizmet kendi kendine barındırılır.</span><span class="sxs-lookup"><span data-stu-id="9f321-128">The service is self hosted.</span></span> <span data-ttu-id="9f321-129">MSMQ tümleştirme taşıyıcısı kullanılırken kullanılan sıranın önceden oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f321-129">When using the MSMQ integration transport, the queue used must be created in advance.</span></span> <span data-ttu-id="9f321-130">Bu, el ile veya kod aracılığıyla yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="9f321-130">This can be done manually or through code.</span></span> <span data-ttu-id="9f321-131">Bu örnekte hizmet, <xref:System.Messaging> sıranın varlığını denetlemek ve gerekirse oluşturmak için kod içerir.</span><span class="sxs-lookup"><span data-stu-id="9f321-131">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and create it if necessary.</span></span> <span data-ttu-id="9f321-132">Sıra adı yapılandırma dosyasından okundu.</span><span class="sxs-lookup"><span data-stu-id="9f321-132">The queue name is read from the configuration file.</span></span>

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

 <span data-ttu-id="9f321-133">Sıra isteklerinin gönderildiği MSMQ kuyruğu, yapılandırma dosyasının appSettings bölümünde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9f321-133">The MSMQ queue to which the order requests are sent is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="9f321-134">İstemci ve hizmet uç noktaları, yapılandırma dosyasının System. serviceModel bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9f321-134">The client and service endpoints are defined in the system.serviceModel section of the configuration file.</span></span> <span data-ttu-id="9f321-135">Her ikisi de `msmqIntegrationbinding` bağlamayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f321-135">Both specify the `msmqIntegrationbinding` binding.</span></span>

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

 <span data-ttu-id="9f321-136">İstemci uygulaması, <xref:System.Messaging> kuyruğa dayanıklı ve işlemsel bir ileti göndermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="9f321-136">The client application uses <xref:System.Messaging> to send a durable and transactional message to the queue.</span></span> <span data-ttu-id="9f321-137">İletinin gövdesinde satınalma siparişi bulunur.</span><span class="sxs-lookup"><span data-stu-id="9f321-137">The message's body contains the purchase order.</span></span>

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

 <span data-ttu-id="9f321-138">Aşağıdaki örnek yapılandırmada gösterildiği gibi, sipariş yanıtlarının alındığı MSMQ kuyruğu yapılandırma dosyasının appSettings bölümünde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9f321-138">The MSMQ queue from which the order responses are received is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="9f321-139">Sıra adı, yerel bilgisayar için bir nokta (.) ve kendi yolunda ters eğik çizgi ayırıcılar kullanır.</span><span class="sxs-lookup"><span data-stu-id="9f321-139">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="9f321-140">WCF uç noktası adresi bir MSMQ. formatname şeması belirtir ve yerel bilgisayar için "localhost" kullanır.</span><span class="sxs-lookup"><span data-stu-id="9f321-140">The WCF endpoint address specifies a msmq.formatname scheme, and uses "localhost" for the local computer.</span></span> <span data-ttu-id="9f321-141">Düzgün biçimlendirilmiş bir biçim adı, MSMQ yönergelerine göre URI 'deki MSMQ. formatname ' i izler.</span><span class="sxs-lookup"><span data-stu-id="9f321-141">A properly formed format name follows msmq.formatname in the URI according to MSMQ guidelines.</span></span>

```xml
<appSettings>
    <add key=" orderResponseQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="9f321-142">İstemci uygulaması, `messageID` hizmetine gönderdiği sipariş isteği iletisini kaydeder ve hizmetten bir yanıt bekler.</span><span class="sxs-lookup"><span data-stu-id="9f321-142">The client application saves the `messageID` of the order request message that it sends to the service and waits for a response from the service.</span></span> <span data-ttu-id="9f321-143">Bir yanıt kuyruğa ulaştığında, istemci, `correlationID` `messageID` istemcinin hizmete ilk olarak gönderdiği sipariş iletisini içeren ileti özelliğini kullanarak gönderdiği sipariş iletisiyle ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="9f321-143">Once a response arrives in the queue the client correlates it with the order message it sent using the `correlationID` property of the message, which contains the `messageID` of the order message that the client sent to the service originally.</span></span>

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

 <span data-ttu-id="9f321-144">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencereleri içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9f321-144">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="9f321-145">Hizmetin istemciden ileti alacağını görebilir ve istemciye geri yanıt gönderir.</span><span class="sxs-lookup"><span data-stu-id="9f321-145">You can see the service receive messages from the client and sends a response back to the client.</span></span> <span data-ttu-id="9f321-146">İstemci, hizmetten alınan yanıtı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9f321-146">The client displays the response received from the service.</span></span> <span data-ttu-id="9f321-147">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="9f321-147">Press ENTER in each console window to shut down the service and client.</span></span>

> [!NOTE]
> <span data-ttu-id="9f321-148">Bu örnek Message Queuing (MSMQ) yüklemesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9f321-148">This sample requires the installation of Message Queuing (MSMQ).</span></span> <span data-ttu-id="9f321-149">Ayrıca bkz. bölümünde MSMQ yükleme yönergelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="9f321-149">See the MSMQ installation instructions in the See Also section.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="9f321-150">Örneği kurma, oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="9f321-150">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="9f321-151">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9f321-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="9f321-152">Önce hizmet çalıştırıldığında, sıranın mevcut olduğundan emin olmak için kontrol edilir.</span><span class="sxs-lookup"><span data-stu-id="9f321-152">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="9f321-153">Sıra yoksa, hizmet bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9f321-153">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="9f321-154">Kuyruğu oluşturmak için önce hizmeti çalıştırabilir veya MSMQ kuyruğu Yöneticisi aracılığıyla bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f321-154">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="9f321-155">Windows 2008 ' de bir sıra oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="9f321-155">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="9f321-156">Visual Studio 2012 ' de Sunucu Yöneticisi açın.</span><span class="sxs-lookup"><span data-stu-id="9f321-156">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="9f321-157">**Özellikler** sekmesini genişletin.</span><span class="sxs-lookup"><span data-stu-id="9f321-157">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="9f321-158">**Özel Ileti kuyrukları**' ne sağ tıklayıp **Yeni**, **özel kuyruk**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="9f321-158">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="9f321-159">**İşlem** kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="9f321-159">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="9f321-160">`ServiceModelSamplesTransacted`Yeni kuyruğun adı olarak girin.</span><span class="sxs-lookup"><span data-stu-id="9f321-160">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="9f321-161">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="9f321-161">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="9f321-162">Örneği tek bilgisayarlı bir yapılandırmada çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="9f321-162">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="run-the-sample-across-computers"></a><span data-ttu-id="9f321-163">Örneği bilgisayarlar arasında çalıştırma</span><span class="sxs-lookup"><span data-stu-id="9f321-163">Run the sample across computers</span></span>

1. <span data-ttu-id="9f321-164">Hizmet programı dosyalarını dile özgü klasörün altındaki \service\bin\ klasöründen hizmet bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="9f321-164">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="9f321-165">İstemci program dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="9f321-165">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="9f321-166">Client.exe.config dosyasında, Ordersıraadı ' nı "." yerine hizmet bilgisayar adını belirtecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9f321-166">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="9f321-167">Service.exe.config dosyasında, istemci uç noktası adresini "." yerine istemci bilgisayar adını belirtecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9f321-167">In the Service.exe.config file, change the client endpoint address to specify the client computer name instead of ".".</span></span>

5. <span data-ttu-id="9f321-168">Hizmet bilgisayarında, bir komut isteminden Service.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="9f321-168">On the service computer, launch Service.exe from a command prompt.</span></span>

6. <span data-ttu-id="9f321-169">İstemci bilgisayarda, bir komut isteminden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="9f321-169">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9f321-170">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="9f321-170">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9f321-171">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9f321-171">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="9f321-172">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9f321-172">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9f321-173">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9f321-173">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`

## <a name="see-also"></a><span data-ttu-id="9f321-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f321-174">See also</span></span>

- [<span data-ttu-id="9f321-175">WCF'de Kuyruğa Alma</span><span class="sxs-lookup"><span data-stu-id="9f321-175">Queuing in WCF</span></span>](../feature-details/queuing-in-wcf.md)
- <span data-ttu-id="9f321-176">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="9f321-176">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span></span>
