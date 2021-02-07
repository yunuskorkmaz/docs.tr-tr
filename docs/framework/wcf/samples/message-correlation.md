---
description: 'Daha fazla bilgi edinin: Ileti bağıntısı'
title: İleti Bağıntısı
ms.date: 03/30/2017
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
ms.openlocfilehash: e38e2e8d6936132e165fd3372ac57fef27240d1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704036"
---
# <a name="message-correlation"></a><span data-ttu-id="f8741-103">İleti Bağıntısı</span><span class="sxs-lookup"><span data-stu-id="f8741-103">Message Correlation</span></span>

<span data-ttu-id="f8741-104">Bu örnek, bir Message Queuing (MSMQ) uygulamasının bir Windows Communication Foundation (WCF) hizmetine nasıl MSMQ iletisi gönderebileceğinizi ve iletilerin istek/yanıt senaryosunda gönderici ve alıcı uygulamaları arasında nasıl bağıntılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8741-104">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service and how messages can be correlated between sender and receiver applications in a request/response scenario.</span></span> <span data-ttu-id="f8741-105">Bu örnek MsmqIntegrationBinding bağlamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8741-105">This sample uses the msmqIntegrationBinding binding.</span></span> <span data-ttu-id="f8741-106">Bu durumda hizmet, sıraya alınan iletileri alan hizmeti gözlemlemeye olanak sağlayan, kendinden konak bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="f8741-106">The service in this case is a self-hosted console application to allow you to observe the service that receives queued messages.</span></span> <span data-ttu-id="f8741-107">k</span><span class="sxs-lookup"><span data-stu-id="f8741-107">k</span></span>

 <span data-ttu-id="f8741-108">Hizmet gönderenden alınan iletiyi işler ve gönderene bir yanıt iletisi gönderir.</span><span class="sxs-lookup"><span data-stu-id="f8741-108">The service processes the message received from the sender and sends a response message back to the sender.</span></span> <span data-ttu-id="f8741-109">Gönderen yanıtı, aldığı isteği ilk gönderdiği istek ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="f8741-109">The sender correlates the response it received to the request it sent originally.</span></span> <span data-ttu-id="f8741-110">`MessageID`İletinin ve `CorrelationID` Özellikleri, istek ve yanıt iletilerini ilişkilendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f8741-110">The `MessageID` and `CorrelationID` properties of the message are used to correlate the request and response messages.</span></span>

 <span data-ttu-id="f8741-111">`IOrderProcessor`Hizmet sözleşmesi, sıraya alma ile kullanılmak üzere uygun tek yönlü bir hizmet işlemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f8741-111">The `IOrderProcessor` service contract defines a one-way service operation that is suitable for use with queuing.</span></span> <span data-ttu-id="f8741-112">Bir MSMQ iletisinde eylem üst bilgisi yok, bu nedenle farklı MSMQ iletilerini işlem sözleşmelerine otomatik olarak eşlemek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="f8741-112">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="f8741-113">Bu nedenle, bu durumda yalnızca bir işlem sözleşmesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="f8741-113">Therefore, there can be only one operation contract in this case.</span></span> <span data-ttu-id="f8741-114">Hizmette daha fazla işlem sözleşmesi tanımlamak istiyorsanız, uygulamanın hangi işlem sözleşmesinin gönderileceğine karar vermek için MSMQ iletisindeki hangi üstbilginin (örneğin, etiket veya correlationID) kullanılabileceği bilgisini sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8741-114">If you want to define more operation contracts in the service, the application must provide information as to which header in the MSMQ message (for example, the label, or correlationID) can be used to decide which operation contract to dispatch.</span></span>

 <span data-ttu-id="f8741-115">MSMQ iletisi ayrıca, hangi üst bilgilerin işlem sözleşmesinin farklı parametreleriyle eşlendiği bilgisini içermez.</span><span class="sxs-lookup"><span data-stu-id="f8741-115">The MSMQ message also does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="f8741-116">Bu nedenle, işlem sözleşmesinde yalnızca bir parametre olabilir.</span><span class="sxs-lookup"><span data-stu-id="f8741-116">Therefore, there can be only one parameter in the operation contract.</span></span> <span data-ttu-id="f8741-117">Parametresi <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> , TEMELDEKI MSMQ iletisini içeren türüdür.</span><span class="sxs-lookup"><span data-stu-id="f8741-117">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, which contains the underlying MSMQ message.</span></span> <span data-ttu-id="f8741-118">Sınıftaki "T" türü, `MsmqMessage<T>` MSMQ ileti gövdesinde seri hale getirilen verileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f8741-118">The type "T" in the `MsmqMessage<T>` class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="f8741-119">Bu örnekte, `PurchaseOrder` tür MSMQ ileti gövdesinde serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="f8741-119">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 <span data-ttu-id="f8741-120">Hizmet işlemi, satın alma siparişini işler ve hizmet konsolu penceresinde satın alma siparişinin içeriğini ve durumunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f8741-120">The service operation processes the purchase order and displays the contents of the purchase order and its status in the service console window.</span></span> <span data-ttu-id="f8741-121">, <xref:System.ServiceModel.OperationBehaviorAttribute> İşlemi sıraya sahip bir işlemde Enlist olarak yapılandırır ve işlem geri döndüğünde işlemin tamamlandığını işaretler.</span><span class="sxs-lookup"><span data-stu-id="f8741-121">The <xref:System.ServiceModel.OperationBehaviorAttribute> configures the operation to enlist in a transaction with the queue and to mark the transaction complete when the operation returns.</span></span> <span data-ttu-id="f8741-122">, `PurchaseOrder` Hizmet tarafından işlenmesi gereken sipariş ayrıntılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="f8741-122">The `PurchaseOrder` contains the order details that must be processed by the service.</span></span>

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

 <span data-ttu-id="f8741-123">Hizmet, `OrderResponseClient` MSMQ iletisini sıraya göndermek için özel bir istemci kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8741-123">The service uses a custom client `OrderResponseClient` to send the MSMQ message to the queue.</span></span> <span data-ttu-id="f8741-124">İletiyi alan ve işleyen uygulama bir WCF uygulaması değil bir MSMQ uygulaması olduğundan, iki uygulama arasında örtük bir hizmet sözleşmesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f8741-124">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="f8741-125">Bu nedenle, Bu senaryodaki Svcutil.exe aracını kullanarak bir ara sunucu oluşturmuyoruz.</span><span class="sxs-lookup"><span data-stu-id="f8741-125">So we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="f8741-126">Özel proxy temelde, `msmqIntegrationBinding` ileti göndermek için bağlamayı kullanan tüm WCF uygulamaları için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f8741-126">The custom proxy is essentially the same for all WCF applications that use the `msmqIntegrationBinding` binding to send messages.</span></span> <span data-ttu-id="f8741-127">Diğer proxy 'lerin aksine, bir dizi hizmet işlemi içermez.</span><span class="sxs-lookup"><span data-stu-id="f8741-127">Unlike other proxies, it does not include a range of service operations.</span></span> <span data-ttu-id="f8741-128">Yalnızca bir ileti gönder işlemidir.</span><span class="sxs-lookup"><span data-stu-id="f8741-128">It is a submit message operation only.</span></span>

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

 <span data-ttu-id="f8741-129">Hizmet kendi kendine barındırılır.</span><span class="sxs-lookup"><span data-stu-id="f8741-129">The service is self hosted.</span></span> <span data-ttu-id="f8741-130">MSMQ tümleştirme taşıyıcısı kullanılırken kullanılan sıranın önceden oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8741-130">When using the MSMQ integration transport, the queue used must be created in advance.</span></span> <span data-ttu-id="f8741-131">Bu, el ile veya kod aracılığıyla yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="f8741-131">This can be done manually or through code.</span></span> <span data-ttu-id="f8741-132">Bu örnekte hizmet, <xref:System.Messaging> sıranın varlığını denetlemek ve gerekirse oluşturmak için kod içerir.</span><span class="sxs-lookup"><span data-stu-id="f8741-132">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and create it if necessary.</span></span> <span data-ttu-id="f8741-133">Sıra adı yapılandırma dosyasından okundu.</span><span class="sxs-lookup"><span data-stu-id="f8741-133">The queue name is read from the configuration file.</span></span>

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

 <span data-ttu-id="f8741-134">Sıra isteklerinin gönderildiği MSMQ kuyruğu, yapılandırma dosyasının appSettings bölümünde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f8741-134">The MSMQ queue to which the order requests are sent is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="f8741-135">İstemci ve hizmet uç noktaları, yapılandırma dosyasının System. serviceModel bölümünde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f8741-135">The client and service endpoints are defined in the system.serviceModel section of the configuration file.</span></span> <span data-ttu-id="f8741-136">Her ikisi de `msmqIntegrationbinding` bağlamayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8741-136">Both specify the `msmqIntegrationbinding` binding.</span></span>

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

 <span data-ttu-id="f8741-137">İstemci uygulaması, <xref:System.Messaging> kuyruğa dayanıklı ve işlemsel bir ileti göndermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8741-137">The client application uses <xref:System.Messaging> to send a durable and transactional message to the queue.</span></span> <span data-ttu-id="f8741-138">İletinin gövdesinde satınalma siparişi bulunur.</span><span class="sxs-lookup"><span data-stu-id="f8741-138">The message's body contains the purchase order.</span></span>

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

 <span data-ttu-id="f8741-139">Aşağıdaki örnek yapılandırmada gösterildiği gibi, sipariş yanıtlarının alındığı MSMQ kuyruğu yapılandırma dosyasının appSettings bölümünde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f8741-139">The MSMQ queue from which the order responses are received is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="f8741-140">Sıra adı, yerel bilgisayar için bir nokta (.) ve kendi yolunda ters eğik çizgi ayırıcılar kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8741-140">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="f8741-141">WCF uç noktası adresi bir MSMQ. formatname şeması belirtir ve yerel bilgisayar için "localhost" kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8741-141">The WCF endpoint address specifies a msmq.formatname scheme, and uses "localhost" for the local computer.</span></span> <span data-ttu-id="f8741-142">Düzgün biçimlendirilmiş bir biçim adı, MSMQ yönergelerine göre URI 'deki MSMQ. formatname ' i izler.</span><span class="sxs-lookup"><span data-stu-id="f8741-142">A properly formed format name follows msmq.formatname in the URI according to MSMQ guidelines.</span></span>

```xml
<appSettings>
    <add key=" orderResponseQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="f8741-143">İstemci uygulaması, `messageID` hizmetine gönderdiği sipariş isteği iletisini kaydeder ve hizmetten bir yanıt bekler.</span><span class="sxs-lookup"><span data-stu-id="f8741-143">The client application saves the `messageID` of the order request message that it sends to the service and waits for a response from the service.</span></span> <span data-ttu-id="f8741-144">Bir yanıt kuyruğa ulaştığında, istemci, `correlationID` `messageID` istemcinin hizmete ilk olarak gönderdiği sipariş iletisini içeren ileti özelliğini kullanarak gönderdiği sipariş iletisiyle ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="f8741-144">Once a response arrives in the queue the client correlates it with the order message it sent using the `correlationID` property of the message, which contains the `messageID` of the order message that the client sent to the service originally.</span></span>

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

 <span data-ttu-id="f8741-145">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencereleri içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f8741-145">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="f8741-146">Hizmetin istemciden ileti alacağını görebilir ve istemciye geri yanıt gönderir.</span><span class="sxs-lookup"><span data-stu-id="f8741-146">You can see the service receive messages from the client and sends a response back to the client.</span></span> <span data-ttu-id="f8741-147">İstemci, hizmetten alınan yanıtı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f8741-147">The client displays the response received from the service.</span></span> <span data-ttu-id="f8741-148">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f8741-148">Press ENTER in each console window to shut down the service and client.</span></span>

> [!NOTE]
> <span data-ttu-id="f8741-149">Bu örnek Message Queuing (MSMQ) yüklemesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f8741-149">This sample requires the installation of Message Queuing (MSMQ).</span></span> <span data-ttu-id="f8741-150">Ayrıca bkz. bölümünde MSMQ yükleme yönergelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="f8741-150">See the MSMQ installation instructions in the See Also section.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="f8741-151">Örneği kurma, oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="f8741-151">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="f8741-152">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="f8741-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="f8741-153">Önce hizmet çalıştırıldığında, sıranın mevcut olduğundan emin olmak için kontrol edilir.</span><span class="sxs-lookup"><span data-stu-id="f8741-153">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="f8741-154">Sıra yoksa, hizmet bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f8741-154">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="f8741-155">Kuyruğu oluşturmak için önce hizmeti çalıştırabilir veya MSMQ kuyruğu Yöneticisi aracılığıyla bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8741-155">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="f8741-156">Windows 2008 ' de bir sıra oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="f8741-156">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="f8741-157">Visual Studio 2012 ' de Sunucu Yöneticisi açın.</span><span class="sxs-lookup"><span data-stu-id="f8741-157">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="f8741-158">**Özellikler** sekmesini genişletin.</span><span class="sxs-lookup"><span data-stu-id="f8741-158">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="f8741-159">**Özel Ileti kuyrukları**' ne sağ tıklayıp **Yeni**, **özel kuyruk**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="f8741-159">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="f8741-160">**İşlem** kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="f8741-160">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="f8741-161">`ServiceModelSamplesTransacted`Yeni kuyruğun adı olarak girin.</span><span class="sxs-lookup"><span data-stu-id="f8741-161">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="f8741-162">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="f8741-162">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="f8741-163">Örneği tek bilgisayarlı bir yapılandırmada çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="f8741-163">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="run-the-sample-across-computers"></a><span data-ttu-id="f8741-164">Örneği bilgisayarlar arasında çalıştırma</span><span class="sxs-lookup"><span data-stu-id="f8741-164">Run the sample across computers</span></span>

1. <span data-ttu-id="f8741-165">Hizmet programı dosyalarını dile özgü klasörün altındaki \service\bin\ klasöründen hizmet bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f8741-165">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="f8741-166">İstemci program dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="f8741-166">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="f8741-167">Client.exe.config dosyasında, Ordersıraadı ' nı "." yerine hizmet bilgisayar adını belirtecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f8741-167">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="f8741-168">Service.exe.config dosyasında, istemci uç noktası adresini "." yerine istemci bilgisayar adını belirtecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f8741-168">In the Service.exe.config file, change the client endpoint address to specify the client computer name instead of ".".</span></span>

5. <span data-ttu-id="f8741-169">Hizmet bilgisayarında, bir komut isteminden Service.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="f8741-169">On the service computer, launch Service.exe from a command prompt.</span></span>

6. <span data-ttu-id="f8741-170">İstemci bilgisayarda, bir komut isteminden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="f8741-170">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f8741-171">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="f8741-171">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f8741-172">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f8741-172">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="f8741-173">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f8741-173">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f8741-174">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f8741-174">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`

## <a name="see-also"></a><span data-ttu-id="f8741-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8741-175">See also</span></span>

- [<span data-ttu-id="f8741-176">WCF'de Kuyruğa Alma</span><span class="sxs-lookup"><span data-stu-id="f8741-176">Queuing in WCF</span></span>](../feature-details/queuing-in-wcf.md)
- <span data-ttu-id="f8741-177">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="f8741-177">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span></span>
