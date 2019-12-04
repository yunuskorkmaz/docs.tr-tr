---
title: Teslim Edilemeyen İletiler Sırası
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: 70007289e457588e94128a573ced4b28e238acf4
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710883"
---
# <a name="dead-letter-queues"></a><span data-ttu-id="1b917-102">Teslim Edilemeyen İletiler Sırası</span><span class="sxs-lookup"><span data-stu-id="1b917-102">Dead Letter Queues</span></span>
<span data-ttu-id="1b917-103">Bu örnek, teslimin başarısız olduğu iletileri nasıl işleyeceğinizi ve işleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b917-103">This sample demonstrates how to handle and process messages that have failed delivery.</span></span> <span data-ttu-id="1b917-104">Bu [işlem, IŞLENEN MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örneğini temel alır.</span><span class="sxs-lookup"><span data-stu-id="1b917-104">It is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="1b917-105">Bu örnek `netMsmqBinding` bağlamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="1b917-105">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="1b917-106">Hizmet, sıraya alınan iletileri alma hizmetini gözlemlemeye olanak sağlayan, kendinden konak bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="1b917-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

> [!NOTE]
> <span data-ttu-id="1b917-107">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="1b917-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="1b917-108">Bu örnek, yalnızca [!INCLUDE[wv](../../../../includes/wv-md.md)]kullanılabilir olan her bir uygulama atılacak ileti sırasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b917-108">This sample demonstrates each application dead letter queue that is only available on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="1b917-109">Örnek, [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)]üzerinde MSMQ 3,0 için varsayılan sistem genelinde kuyrukları kullanacak şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1b917-109">The sample can be modified to use the default system-wide queues for MSMQ 3.0 on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)].</span></span>

 <span data-ttu-id="1b917-110">Sıraya alınmış iletişimde istemci, hizmet ile bir kuyruk kullanarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="1b917-110">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="1b917-111">Daha kesin olarak, istemci iletileri bir kuyruğa gönderir.</span><span class="sxs-lookup"><span data-stu-id="1b917-111">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="1b917-112">Hizmet kuyruktaki iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="1b917-112">The service receives messages from the queue.</span></span> <span data-ttu-id="1b917-113">Bu nedenle, hizmet ve istemci, bir kuyruk kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1b917-113">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="1b917-114">Kuyruğa alınan iletişim belirli bir miktarda devre dışı olabileceğinden, iletinin saati geçmiş olursa uygulamaya teslim edilmediğini sağlamak için ileti üzerinde bir yaşam süresi değeri ilişkilendirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b917-114">Because queued communication can involve a certain amount of dormancy, you may want to associate a time-to-live value on the message to ensure that the message does not get delivered to the application if it has gone past the time.</span></span> <span data-ttu-id="1b917-115">Ayrıca, bir iletinin teslim başarısız olup olmadığını bir uygulamanın bilgilendirilmesi gereken durumlar da vardır.</span><span class="sxs-lookup"><span data-stu-id="1b917-115">There are also cases, where an application must be informed whether a message failed delivery.</span></span> <span data-ttu-id="1b917-116">Bu durumların tümünde, iletideki yaşam süresi dolduğunda veya ileti teslimi başarısız olduğunda, ileti atılacak bir sıra kuyruğuna konur.</span><span class="sxs-lookup"><span data-stu-id="1b917-116">In all of these cases, such as when the time-to-live on the message has expired or the message failed delivery, the message is put in a dead letter queue.</span></span> <span data-ttu-id="1b917-117">Gönderen uygulama daha sonra teslim edilemeyen ileti sırasındaki iletileri okuyabilir ve başarısız teslimat nedenlerini düzeltmek ve iletiyi yeniden göndermek için hiçbir eylemde yer alan düzeltici eylemler gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="1b917-117">The sending application can then read the messages in the dead-letter queue and take corrective actions that range from no action to correcting the reasons for failed delivery and resending the message.</span></span>

 <span data-ttu-id="1b917-118">`NetMsmqBinding` bağlamasındaki atılacak mektup sırası aşağıdaki özelliklerde ifade edilir:</span><span class="sxs-lookup"><span data-stu-id="1b917-118">The dead-letter queue in the `NetMsmqBinding` binding is expressed in the following properties:</span></span>

- <span data-ttu-id="1b917-119">istemcinin gerektirdiği atılacak ileti sırası türünü ifade etmek için <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1b917-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> property to express the kind of dead-letter queue required by the client.</span></span> <span data-ttu-id="1b917-120">Bu numaralandırma aşağıdaki değerlere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="1b917-120">This enumeration has the following values:</span></span>

- <span data-ttu-id="1b917-121">`None`: istemci için atılacak ileti kuyruğu gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1b917-121">`None`: No dead-letter queue is required by the client.</span></span>

- <span data-ttu-id="1b917-122">`System`: sistem atılacak ileti sırası, ölü iletileri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b917-122">`System`: The system dead-letter queue is used to store dead messages.</span></span> <span data-ttu-id="1b917-123">Sistem atılacak ileti kuyruğu, bilgisayarda çalışan tüm uygulamalar tarafından paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="1b917-123">The system dead-letter queue is shared by all applications running on the computer.</span></span>

- <span data-ttu-id="1b917-124">`Custom`: <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> özelliği kullanılarak belirtilen özel bir atılacak mektup kuyruğu, ölü iletileri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b917-124">`Custom`: A custom dead-letter queue specified using the <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property is used to store dead messages.</span></span> <span data-ttu-id="1b917-125">Bu özellik yalnızca [!INCLUDE[wv](../../../../includes/wv-md.md)]kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1b917-125">This feature is only available on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="1b917-126">Bu, uygulamanın aynı bilgisayar üzerinde çalışan diğer uygulamalarla paylaşılması yerine kendi atılacak bir sıra kullanması gerektiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b917-126">This is used when the application must use its own dead letter queue instead of sharing it with other applications running on the same computer.</span></span>

- <span data-ttu-id="1b917-127">belirli bir kuyruğu, atılacak ileti sırası olarak kullanılacak şekilde ifade etmek için <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1b917-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property to express the specific queue to use as a dead-letter queue.</span></span> <span data-ttu-id="1b917-128">Bu yalnızca [!INCLUDE[wv](../../../../includes/wv-md.md)]kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1b917-128">This is available only in [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

 <span data-ttu-id="1b917-129">Bu örnekte, istemci, bir işlemin kapsamı içinde hizmete toplu bir ileti gönderir ve bu iletiler için "yaşam süresi" (yaklaşık 2 saniye) için rastgele bir düşük değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b917-129">In this sample, the client sends a batch of messages to the service from within the scope of a transaction and specifies an arbitrarily low value for "time-to-live" for these messages (about 2 seconds).</span></span> <span data-ttu-id="1b917-130">İstemci Ayrıca, kullanım dışı olan iletileri sıraya almak için kullanılacak özel bir atılacak mektup kuyruğu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b917-130">The client also specifies a custom dead-letter queue to use to enqueue the messages that have expired.</span></span>

 <span data-ttu-id="1b917-131">İstemci uygulaması, teslim edilemeyen ileti sırasındaki iletileri okuyabilir ve iletiyi göndermeyi yeniden deneyebilir ya da özgün iletinin atılacak ileti kuyruğuna yerleştirilmesine neden olan hatayı düzeltebilir ve iletiyi gönderebilirler.</span><span class="sxs-lookup"><span data-stu-id="1b917-131">The client application can read the messages in the dead-letter queue and either retry sending the message or correct the error that caused the original message to be placed in the dead-letter queue and send the message.</span></span> <span data-ttu-id="1b917-132">Örnekte istemci bir hata iletisi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1b917-132">In the sample, the client displays an error message.</span></span>

 <span data-ttu-id="1b917-133">Hizmet sözleşmesi aşağıdaki örnek kodda gösterildiği gibi `IOrderProcessor`.</span><span class="sxs-lookup"><span data-stu-id="1b917-133">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="1b917-134">Örnekteki hizmet kodu, [Işlem TEMELLI MSMQ bağlamadır](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="1b917-134">The service code in the sample is that of the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>

 <span data-ttu-id="1b917-135">Hizmet ile iletişim, bir işlemin kapsamı içinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="1b917-135">Communication with the service takes place within the scope of a transaction.</span></span> <span data-ttu-id="1b917-136">Hizmet kuyruktaki iletileri okur, işlemi gerçekleştirir ve sonra işlemin sonuçlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1b917-136">The service reads messages from the queue, performs the operation and then displays the results of the operation.</span></span> <span data-ttu-id="1b917-137">Uygulama, atılacak iletiler için atılacak mektup kuyruğu da oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1b917-137">The application also creates a dead-letter queue for dead-letter messages.</span></span>

```csharp
//The service contract is defined in generatedClient.cs, generated from the service by the svcutil tool.

//Client implementation code.
class Client
{
    static void Main()
    {
        // Get MSMQ queue name from app settings in configuration
        string deadLetterQueueName = ConfigurationManager.AppSettings["deadLetterQueueName"];

        // Create the transacted MSMQ queue for storing dead message if necessary.
        if (!MessageQueue.Exists(deadLetterQueueName))
            MessageQueue.Create(deadLetterQueueName, true);

        // Create a proxy with given client endpoint configuration
        OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");

        // Create the purchase order
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

        //Create a transaction scope.
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            // Make a queued call to submit the purchase order
            client.SubmitPurchaseOrder(po);
            // Complete the transaction.
            scope.Complete();
        }

        client.Close();

        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate client.");
        Console.ReadLine();
    }
}
```

 <span data-ttu-id="1b917-138">İstemcinin yapılandırması, iletinin hizmete ulaşması için kısa bir süre belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b917-138">The client's configuration specifies a short duration for the message to reach the service.</span></span> <span data-ttu-id="1b917-139">İleti belirtilen süre içinde iletilemez, iletinin süresi dolar ve atılacak ileti kuyruğuna taşınır.</span><span class="sxs-lookup"><span data-stu-id="1b917-139">If the message cannot be transmitted within the duration specified, the message expires and is moved to the dead-letter queue.</span></span>

> [!NOTE]
> <span data-ttu-id="1b917-140">İstemci, iletiyi belirtilen süre içinde hizmet kuyruğuna teslim etmek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="1b917-140">It is possible for the client to deliver the message to the service queue within the specified time.</span></span> <span data-ttu-id="1b917-141">İşlem sırasında atılacak ileti hizmetini gördiğinizden emin olmak için, hizmeti başlatmadan önce istemcisini çalıştırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="1b917-141">To ensure you see the dead-letter service in action, you should run the client before starting the service.</span></span> <span data-ttu-id="1b917-142">İleti zaman aşımına uğrar ve atılacak ileti hizmetine gönderilir.</span><span class="sxs-lookup"><span data-stu-id="1b917-142">The message times out and is delivered to the dead-letter service.</span></span>

 <span data-ttu-id="1b917-143">Uygulamanın, atılacak ileti sırası olarak hangi kuyruğun kullanılacağını tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b917-143">The application must define which queue to use as its dead-letter queue.</span></span> <span data-ttu-id="1b917-144">Hiçbir kuyruk belirtilmemişse, ölü iletileri sıraya almak için varsayılan sistem genelinde işlem atılacak ileti sırası kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b917-144">If no queue is specified, the default system-wide transactional dead-letter queue is used to queue dead messages.</span></span> <span data-ttu-id="1b917-145">Bu örnekte, istemci uygulaması kendi uygulama atılacak mektup sırasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b917-145">In this example, the client application specifies its own application dead-letter queue.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <!-- use appSetting to configure MSMQ Dead Letter queue name -->
    <add key="deadLetterQueueName" value=".\private$\ServiceModelSamplesOrdersAppDLQ"/>
  </appSettings>

  <system.serviceModel>
    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"
                binding="netMsmqBinding"
                bindingConfiguration="PerAppDLQBinding"
                contract="IOrderProcessor" />
    </client>

    <bindings>
      <netMsmqBinding>
        <binding name="PerAppDLQBinding"
                 deadLetterQueue="Custom"
                 customDeadLetterQueue="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"
                 timeToLive="00:00:02"/>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>

</configuration>
```

 <span data-ttu-id="1b917-146">Atılacak ileti hizmeti, iletileri atılacak ileti sırasından okur.</span><span class="sxs-lookup"><span data-stu-id="1b917-146">The dead-letter message service reads messages from the dead-letter queue.</span></span> <span data-ttu-id="1b917-147">Atılacak ileti hizmeti `IOrderProcessor` sözleşmesini uygular.</span><span class="sxs-lookup"><span data-stu-id="1b917-147">The dead-letter message service implements the `IOrderProcessor` contract.</span></span> <span data-ttu-id="1b917-148">Ancak, bu uygulama, siparişlerin işlenmesi için değildir.</span><span class="sxs-lookup"><span data-stu-id="1b917-148">Its implementation however is not to process orders.</span></span> <span data-ttu-id="1b917-149">Atılacak ileti hizmeti bir istemci hizmetidir ve siparişleri işleme olanağı yoktur.</span><span class="sxs-lookup"><span data-stu-id="1b917-149">The dead-letter message service is a client service and does not have the facility to process orders.</span></span>

> [!NOTE]
> <span data-ttu-id="1b917-150">Atılacak ileti sırası bir istemci kuyruğu ve istemci kuyruğu yöneticisinin yereldir.</span><span class="sxs-lookup"><span data-stu-id="1b917-150">The dead-letter queue is a client queue and is local to the client queue manager.</span></span>

 <span data-ttu-id="1b917-151">Atılacak ileti hizmeti uygulamasının bir ileti tesliminin başarısız olup olmadığını denetler ve düzeltici ölçüler alır.</span><span class="sxs-lookup"><span data-stu-id="1b917-151">The dead-letter message service implementation checks for the reason a message failed delivery and takes corrective measures.</span></span> <span data-ttu-id="1b917-152">İleti hatasının nedeni, <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> ve <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>olmak üzere iki numaralandırmalar halinde yakalanır.</span><span class="sxs-lookup"><span data-stu-id="1b917-152">The reason for a message failure is captured in two enumerations, <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> and <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span></span> <span data-ttu-id="1b917-153">Aşağıdaki örnek kodda gösterildiği gibi <xref:System.ServiceModel.OperationContext> <xref:System.ServiceModel.Channels.MsmqMessageProperty> alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1b917-153">You can retrieve the <xref:System.ServiceModel.Channels.MsmqMessageProperty> from the <xref:System.ServiceModel.OperationContext> as shown in the following sample code:</span></span>

```csharp
public void SubmitPurchaseOrder(PurchaseOrder po)
{
    Console.WriteLine("Submitting purchase order did not succeed ", po);
    MsmqMessageProperty mqProp =
                  OperationContext.Current.IncomingMessageProperties[
                  MsmqMessageProperty.Name] as MsmqMessageProperty;
    Console.WriteLine("Message Delivery Status: {0} ",
                                                mqProp.DeliveryStatus);
    Console.WriteLine("Message Delivery Failure: {0}",
                                               mqProp.DeliveryFailure);
    Console.WriteLine();
    …
}
```

 <span data-ttu-id="1b917-154">Atılacak ileti sırasındaki iletiler, iletiyi işleyen hizmete yönelik iletilerdir.</span><span class="sxs-lookup"><span data-stu-id="1b917-154">Messages in the dead-letter queue are messages that are addressed to the service that is processing the message.</span></span> <span data-ttu-id="1b917-155">Bu nedenle, atılacak ileti hizmeti sıradaki iletileri okuduğunda, Windows Communication Foundation (WCF) Kanal katmanı bitiş noktalarında uyuşmazlığını bulur ve iletiyi göndermez.</span><span class="sxs-lookup"><span data-stu-id="1b917-155">Therefore, when the dead-letter message service reads messages from the queue, the Windows Communication Foundation (WCF) channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="1b917-156">Bu durumda, ileti sipariş işleme hizmetine değinilmesi, ancak atılacak ileti hizmeti tarafından alınır.</span><span class="sxs-lookup"><span data-stu-id="1b917-156">In this case, the message is addressed to the order processing service but is received by the dead-letter message service.</span></span> <span data-ttu-id="1b917-157">Farklı bir uç noktaya yönelik bir ileti almak için, `ServiceBehavior`herhangi bir adresle eşleşecek bir adres filtresi belirtilir.</span><span class="sxs-lookup"><span data-stu-id="1b917-157">To receive a message that is addressed to a different endpoint, an address filter to match any address is specified in the `ServiceBehavior`.</span></span> <span data-ttu-id="1b917-158">Bu, atılacak ileti sırasından okunan iletileri başarıyla işlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1b917-158">This is required to successfully process messages that are read from the dead-letter queue.</span></span>

 <span data-ttu-id="1b917-159">Bu örnekte, hata nedeni iletinin zaman aşımına uğraması durumunda, atılacak ileti hizmeti iletiyi yeniden sonlandırır. Diğer tüm nedenlerden dolayı, aşağıdaki örnek kodda gösterildiği gibi teslim hatası görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="1b917-159">In this sample, the dead-letter message service resends the message if the reason for failure is that the message timed out. For all other reasons, it displays the delivery failure, as shown in the following sample code:</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Single, ConcurrencyMode=ConcurrencyMode.Single, AddressFilterMode=AddressFilterMode.Any)]
public class PurchaseOrderDLQService : IOrderProcessor
{
    OrderProcessorClient orderProcessorService;
    public PurchaseOrderDLQService()
    {
        orderProcessorService = new OrderProcessorClient("OrderProcessorEndpoint");
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Console.WriteLine("Submitting purchase order did not succeed ", po);
        MsmqMessageProperty mqProp = OperationContext.Current.IncomingMessageProperties[MsmqMessageProperty.Name] as MsmqMessageProperty;

        Console.WriteLine("Message Delivery Status: {0} ", mqProp.DeliveryStatus);
        Console.WriteLine("Message Delivery Failure: {0}", mqProp.DeliveryFailure);
        Console.WriteLine();

        // resend the message if timed out
        if (mqProp.DeliveryFailure == DeliveryFailure.ReachQueueTimeout ||
            mqProp.DeliveryFailure == DeliveryFailure.ReceiveTimeout)
        {
            // re-send
            Console.WriteLine("Purchase order Time To Live expired");
            Console.WriteLine("Trying to resend the message");

            // reuse the same transaction used to read the message from dlq to enqueue the message to app. queue
            orderProcessorService.SubmitPurchaseOrder(po);
            Console.WriteLine("Purchase order resent");
        }
    }

    // Host the service within this EXE console application.
    public static void Main()
    {
        // Create a ServiceHost for the PurchaseOrderDLQService type.
        using (ServiceHost serviceHost = new ServiceHost(typeof(PurchaseOrderDLQService)))
        {
            // Open the ServiceHostBase to create listeners and start listening for messages.
            serviceHost.Open();

            // The service can now be accessed.
            Console.WriteLine("The dead letter service is ready.");
            Console.WriteLine("Press <ENTER> to terminate service.");
            Console.WriteLine();
            Console.ReadLine();
        }
    }
}
```

 <span data-ttu-id="1b917-160">Aşağıdaki örnek, atılacak bir ileti için yapılandırmayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="1b917-160">The following sample shows the configuration for a dead-letter message:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.PurchaseOrderDLQService">
        <!-- Define NetMsmqEndpoint in this case, DLQ end point to read messages-->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesOrdersAppDLQ"
                  binding="netMsmqBinding"
                  bindingConfiguration="DefaultBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
      </service>
    </services>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                 address="net.msmq://localhost/private/ServiceModelSamplesDeadLetter"
                 binding="netMsmqBinding"
                 bindingConfiguration="SystemDLQBinding"
                 contract="IOrderProcessor" />
    </client>

    <bindings>
      <netMsmqBinding>
        <binding name="DefaultBinding" />
        <binding name="SystemDLQBinding"
                 deadLetterQueue="System"/>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="1b917-161">Örneği çalıştırırken, her uygulama için atılacak ileti sırasının nasıl çalıştığını görmek için çalıştırılacak 3 yürütülebilir dosya vardır; her uygulama için atılacak ileti sırasından okuyan ve iletiyi yeniden sonlandıran istemci, hizmet ve atılacak ileti hizmeti.</span><span class="sxs-lookup"><span data-stu-id="1b917-161">In running the sample, there are 3 executables to run to see how the dead-letter queue works for each application; the client, service and a dead-letter service that reads from the dead-letter queue for each application and resends the message to the service.</span></span> <span data-ttu-id="1b917-162">Hepsi konsol Windows 'da çıkışı olan konsol uygulamalardır.</span><span class="sxs-lookup"><span data-stu-id="1b917-162">All are console applications with output in console windows.</span></span>

> [!NOTE]
> <span data-ttu-id="1b917-163">Kuyruk kullanımda olduğundan, istemci ve hizmetin aynı anda çalışıyor olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="1b917-163">Because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="1b917-164">İstemcisini çalıştırabilir, kapatabilir ve ardından hizmeti başlatabilir ve yine de iletilerini alabilir.</span><span class="sxs-lookup"><span data-stu-id="1b917-164">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="1b917-165">Kuyruğun oluşturulabilmesi için hizmeti başlatmanız ve kapatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b917-165">You should start the service and shut it down so that the queue can be created.</span></span>

 <span data-ttu-id="1b917-166">İstemci çalıştırılırken, istemci şu iletiyi görüntüler:</span><span class="sxs-lookup"><span data-stu-id="1b917-166">When running the client, the client displays the message:</span></span>

```console
Press <ENTER> to terminate client.
```

 <span data-ttu-id="1b917-167">İstemci iletiyi gönderilmeye çalıştı, ancak kısa bir zaman aşımıyla, iletinin süresi doldu ve artık her uygulama için atılacak ileti kuyruğunda sıraya alındı.</span><span class="sxs-lookup"><span data-stu-id="1b917-167">The client attempted to send the message but with a short timeout, the message expired and is now queued in the dead-letter queue for each application.</span></span>

 <span data-ttu-id="1b917-168">Daha sonra iletiyi okuyan ve hata kodunu görüntüleyen ve iletiyi hizmete geri sonlandıran atılacak mektup hizmetini çalıştırırsınız.</span><span class="sxs-lookup"><span data-stu-id="1b917-168">You then run the dead-letter service, which reads the message and displays the error code and resends the message back to the service.</span></span>

```console
The dead letter service is ready.
Press <ENTER> to terminate service.

Submitting purchase order did not succeed
Message Delivery Status: InDoubt
Message Delivery Failure: ReachQueueTimeout

Purchase order Time To Live expired
Trying to resend the message
Purchase order resent
```

 <span data-ttu-id="1b917-169">Hizmet başlar ve sonra yeniden gönderilen iletiyi okur ve işler.</span><span class="sxs-lookup"><span data-stu-id="1b917-169">The service starts and then reads the resent message and processes it.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 97897eff-f926-4057-a32b-af8fb11b9bf9
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1b917-170">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="1b917-170">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="1b917-171">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="1b917-171">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="1b917-172">Önce hizmet çalıştırıldığında, sıranın mevcut olduğundan emin olmak için kontrol edilir.</span><span class="sxs-lookup"><span data-stu-id="1b917-172">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="1b917-173">Sıra yoksa, hizmet bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1b917-173">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="1b917-174">Kuyruğu oluşturmak için önce hizmeti çalıştırabilir veya MSMQ kuyruğu Yöneticisi aracılığıyla bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1b917-174">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="1b917-175">Windows 2008 ' de bir sıra oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="1b917-175">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="1b917-176">Visual Studio 2012 ' de Sunucu Yöneticisi açın.</span><span class="sxs-lookup"><span data-stu-id="1b917-176">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="1b917-177">**Özellikler** sekmesini genişletin.</span><span class="sxs-lookup"><span data-stu-id="1b917-177">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="1b917-178">**Özel Ileti kuyrukları**' ne sağ tıklayıp **Yeni**, **özel kuyruk**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="1b917-178">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="1b917-179">**İşlem** kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="1b917-179">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="1b917-180">Yeni kuyruğun adı olarak `ServiceModelSamplesTransacted` girin.</span><span class="sxs-lookup"><span data-stu-id="1b917-180">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="1b917-181">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="1b917-181">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="1b917-182">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için, localhost 'u bilgisayarın tam adıyla değiştirip [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="1b917-182">To run the sample in a single- or cross-computer configuration change queue names appropriately, replacing localhost with full name of the computer and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="1b917-183">Örneği çalışma grubuna katılmış bir bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="1b917-183">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="1b917-184">Bilgisayarınız bir etki alanının parçası değilse, aşağıdaki örnek yapılandırmada gösterildiği gibi kimlik doğrulama modu ve koruma düzeyini `None` olarak ayarlayarak aktarım güvenliğini kapatın:</span><span class="sxs-lookup"><span data-stu-id="1b917-184">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="1b917-185">Uç noktanın `bindingConfiguration` özniteliğini ayarlayarak, bitiş noktasının bağlama ile ilişkilendirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="1b917-185">Ensure the endpoint is associated with the binding by setting the endpoint's `bindingConfiguration` attribute.</span></span>

2. <span data-ttu-id="1b917-186">Örneği çalıştırmadan önce DeadLetterService, sunucu ve istemcideki yapılandırmayı değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="1b917-186">Ensure that you change the configuration on the DeadLetterService, server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1b917-187">`security mode` `None` ayarlanması `MsmqAuthenticationMode`, `MsmqProtectionLevel` ve `Message` güvenlik `None`ayarı ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="1b917-187">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>

## <a name="comments"></a><span data-ttu-id="1b917-188">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b917-188">Comments</span></span>
 <span data-ttu-id="1b917-189">`netMsmqBinding` bağlama taşıması ile varsayılan olarak güvenlik etkindir.</span><span class="sxs-lookup"><span data-stu-id="1b917-189">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="1b917-190">İki özellik, `MsmqAuthenticationMode` ve `MsmqProtectionLevel`birlikte taşıma güvenliği türünü belirleme.</span><span class="sxs-lookup"><span data-stu-id="1b917-190">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="1b917-191">Varsayılan olarak, kimlik doğrulama modu `Windows` olarak ayarlanır ve koruma düzeyi `Sign`olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1b917-191">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="1b917-192">Kimlik doğrulama ve imzalama özelliğini sağlamak için MSMQ 'nun bir etki alanının parçası olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b917-192">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="1b917-193">Bu örneği bir etki alanının parçası olmayan bir bilgisayarda çalıştırırsanız, şu hatayı alırsınız: "kullanıcının iç Message Queuing sertifikası yok".</span><span class="sxs-lookup"><span data-stu-id="1b917-193">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1b917-194">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="1b917-194">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1b917-195">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1b917-195">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="1b917-196">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="1b917-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1b917-197">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1b917-197">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
