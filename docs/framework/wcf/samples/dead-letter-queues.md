---
title: Teslim Edilemeyen İletiler Sırası
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: c6b3f059f1a1b11825b595346ed47f6a498078f1
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582612"
---
# <a name="dead-letter-queues"></a><span data-ttu-id="d62fa-102">Teslim Edilemeyen İletiler Sırası</span><span class="sxs-lookup"><span data-stu-id="d62fa-102">Dead Letter Queues</span></span>
<span data-ttu-id="d62fa-103">Bu örnek ve teslim başarısız olmuş bir iletiyi işlemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="d62fa-103">This sample demonstrates how to handle and process messages that have failed delivery.</span></span> <span data-ttu-id="d62fa-104">Dayanır [işlem temelli MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="d62fa-104">It is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="d62fa-105">Bu örnekte `netMsmqBinding` bağlama.</span><span class="sxs-lookup"><span data-stu-id="d62fa-105">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="d62fa-106">Hizmeti, sıraya alınan iletileri alma hizmeti gözlemleyin sağlamak için bir şirket içinde barındırılan bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="d62fa-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

> [!NOTE]
>  <span data-ttu-id="d62fa-107">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="d62fa-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!NOTE]
>  <span data-ttu-id="d62fa-108">Bu örnek yalnızca üzerinde kullanılabilir olan her uygulama geçerliliğini yitirmiş kuyruk gösterir [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d62fa-108">This sample demonstrates each application dead letter queue that is only available on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="d62fa-109">Örnek, varsayılan sistem genelinde kuyruklar için MSMQ 3.0 kullanmak üzere değiştirilebilir [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d62fa-109">The sample can be modified to use the default system-wide queues for MSMQ 3.0 on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)].</span></span>

 <span data-ttu-id="d62fa-110">Kuyruğa alınan iletişim kullanarak bir kuyruk hizmetine istemci iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="d62fa-110">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="d62fa-111">Daha kesin bir istemci bir kuyruğa iletiler gönderir.</span><span class="sxs-lookup"><span data-stu-id="d62fa-111">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="d62fa-112">Hizmet iletileri kuyruktan alır.</span><span class="sxs-lookup"><span data-stu-id="d62fa-112">The service receives messages from the queue.</span></span> <span data-ttu-id="d62fa-113">Hizmet ve istemci bu nedenle, bir kuyruk kullanarak iletişim kurmak için aynı anda çalıştırılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d62fa-113">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="d62fa-114">Kuyruğa alınan iletişim belirli bir miktarda dormancy içerebildiğinden, bir yaşam süresi değerini zamanından daha sonradır geçti, ileti uygulamaya teslim değil emin olmak için iletide ilişkilendirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d62fa-114">Because queued communication can involve a certain amount of dormancy, you may want to associate a time-to-live value on the message to ensure that the message does not get delivered to the application if it has gone past the time.</span></span> <span data-ttu-id="d62fa-115">Durumda, burada bir uygulama bir ileti teslim başarısız olup olmadığını bilgilendirilmesi gerekir vardır.</span><span class="sxs-lookup"><span data-stu-id="d62fa-115">There are also cases, where an application must be informed whether a message failed delivery.</span></span> <span data-ttu-id="d62fa-116">Bu durumların tümünde gibi zaman yaşam iletideki süresi doldu veya iletinin teslim başarısız, ileti sahipsiz sıraya konur.</span><span class="sxs-lookup"><span data-stu-id="d62fa-116">In all of these cases, such as when the time-to-live on the message has expired or the message failed delivery, the message is put in a dead letter queue.</span></span> <span data-ttu-id="d62fa-117">Gönderen uygulamayı iletileri teslim edilemeyen okuyabilir ve herhangi bir eylemi başarısız teslim nedenlerle düzeltme ve ileti yeniden gönderme aralığı düzeltme girişimlerinde bulunun.</span><span class="sxs-lookup"><span data-stu-id="d62fa-117">The sending application can then read the messages in the dead-letter queue and take corrective actions that range from no action to correcting the reasons for failed delivery and resending the message.</span></span>

 <span data-ttu-id="d62fa-118">Teslim edilemeyen kuyrukta `NetMsmqBinding` bağlama şu özelliklerde ifade edilir:</span><span class="sxs-lookup"><span data-stu-id="d62fa-118">The dead-letter queue in the `NetMsmqBinding` binding is expressed in the following properties:</span></span>

-   <span data-ttu-id="d62fa-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> Gerekli istemci tarafından eski ileti sırası türünü express özellik.</span><span class="sxs-lookup"><span data-stu-id="d62fa-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> property to express the kind of dead-letter queue required by the client.</span></span> <span data-ttu-id="d62fa-120">Bu numaralandırma aşağıdaki değerlere sahip:</span><span class="sxs-lookup"><span data-stu-id="d62fa-120">This enumeration has the following values:</span></span>

-   <span data-ttu-id="d62fa-121">`None`: Hiçbir eski ileti sırası istemci tarafından gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d62fa-121">`None`: No dead-letter queue is required by the client.</span></span>

-   <span data-ttu-id="d62fa-122">`System`: Sistem eski ileti sırası ölü iletileri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d62fa-122">`System`: The system dead-letter queue is used to store dead messages.</span></span> <span data-ttu-id="d62fa-123">Sistem eski ileti sırası bilgisayarda çalışan tüm uygulamalar tarafından paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="d62fa-123">The system dead-letter queue is shared by all applications running on the computer.</span></span>

-   <span data-ttu-id="d62fa-124">`Custom`Kullanarak belirtilen özel eski ileti sırası <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> özelliği ölü iletileri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d62fa-124">`Custom`: A custom dead-letter queue specified using the <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property is used to store dead messages.</span></span> <span data-ttu-id="d62fa-125">Bu özellik yalnızca üzerinde kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d62fa-125">This feature is only available on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="d62fa-126">Aynı bilgisayarda çalışan diğer uygulamalarla paylaşmak yerine, uygulamanın kendi geçerliliğini yitirmiş kuyruk kullanmanız gerekir, bu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d62fa-126">This is used when the application must use its own dead letter queue instead of sharing it with other applications running on the same computer.</span></span>

-   <span data-ttu-id="d62fa-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> belirli bir kuyruğa atılacak kullanmak için express özellik.</span><span class="sxs-lookup"><span data-stu-id="d62fa-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property to express the specific queue to use as a dead-letter queue.</span></span> <span data-ttu-id="d62fa-128">Bu yalnızca kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d62fa-128">This is available only in [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

 <span data-ttu-id="d62fa-129">Bu örnekte, istemci bir işlem kapsamında hizmetten toplu iletiler gönderir ve "zaman yaşam" Bu iletileri (yaklaşık 2 saniye) için rastgele düşük bir değer belirtir.</span><span class="sxs-lookup"><span data-stu-id="d62fa-129">In this sample, the client sends a batch of messages to the service from within the scope of a transaction and specifies an arbitrarily low value for "time-to-live" for these messages (about 2 seconds).</span></span> <span data-ttu-id="d62fa-130">İstemci Ayrıca, süresi dolan iletileri kuyruğa kullanmak için özel bir sahipsiz sırayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="d62fa-130">The client also specifies a custom dead-letter queue to use to enqueue the messages that have expired.</span></span>

 <span data-ttu-id="d62fa-131">İstemci uygulama, sahipsiz sırayı ve ileti göndermek ya da yeniden deneme iletileri okumak veya özgün iletinin teslim edilemeyen sırasına ve ileti göndermek neden olan hatayı düzeltin.</span><span class="sxs-lookup"><span data-stu-id="d62fa-131">The client application can read the messages in the dead-letter queue and either retry sending the message or correct the error that caused the original message to be placed in the dead-letter queue and send the message.</span></span> <span data-ttu-id="d62fa-132">Bu örnekte, istemci bir hata iletisi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d62fa-132">In the sample, the client displays an error message.</span></span>

 <span data-ttu-id="d62fa-133">Hizmet sözleşme `IOrderProcessor`aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="d62fa-133">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="d62fa-134">Hizmet kod budur [işlem temelli MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="d62fa-134">The service code in the sample is that of the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>

 <span data-ttu-id="d62fa-135">Hizmet ile iletişim bir işlem kapsamında gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d62fa-135">Communication with the service takes place within the scope of a transaction.</span></span> <span data-ttu-id="d62fa-136">Hizmet iletileri kuyruktan okuyan işlemi gerçekleştirir ve işlemin sonuçları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d62fa-136">The service reads messages from the queue, performs the operation and then displays the results of the operation.</span></span> <span data-ttu-id="d62fa-137">Uygulama eski ileti sırası için teslim edilemeyen iletiler de oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d62fa-137">The application also creates a dead-letter queue for dead-letter messages.</span></span>

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

 <span data-ttu-id="d62fa-138">İstemcinin yapılandırma hizmete erişmek ileti için kısa bir süre belirtir.</span><span class="sxs-lookup"><span data-stu-id="d62fa-138">The client's configuration specifies a short duration for the message to reach the service.</span></span> <span data-ttu-id="d62fa-139">Belirtilen süre içinde ileti iletilemedi, ileti süresi dolmadan ve eski ileti sırası için taşınır.</span><span class="sxs-lookup"><span data-stu-id="d62fa-139">If the message cannot be transmitted within the duration specified, the message expires and is moved to the dead-letter queue.</span></span>

> [!NOTE]
>  <span data-ttu-id="d62fa-140">Bu, istemcinin belirtilen süre içinde hizmet kuyruğa ileti teslim mümkündür.</span><span class="sxs-lookup"><span data-stu-id="d62fa-140">It is possible for the client to deliver the message to the service queue within the specified time.</span></span> <span data-ttu-id="d62fa-141">Teslim edilemeyen Hizmeti'ni çalışırken görmek emin olmak için İstemci Hizmeti başlatmadan önce çalıştırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="d62fa-141">To ensure you see the dead-letter service in action, you should run the client before starting the service.</span></span> <span data-ttu-id="d62fa-142">İleti zaman aşımına uğrar ve edilemeyen hizmete teslim edilir.</span><span class="sxs-lookup"><span data-stu-id="d62fa-142">The message times out and is delivered to the dead-letter service.</span></span>

 <span data-ttu-id="d62fa-143">Uygulama, eski ileti sırası kullanmak için hangi sıranın tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d62fa-143">The application must define which queue to use as its dead-letter queue.</span></span> <span data-ttu-id="d62fa-144">Sıra belirtilmezse, varsayılan sistem genelinde işlem eski ileti sırası eski iletilerin sıraya almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d62fa-144">If no queue is specified, the default system-wide transactional dead-letter queue is used to queue dead messages.</span></span> <span data-ttu-id="d62fa-145">Bu örnekte, istemci uygulamayı kendi uygulama sahipsiz sırayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="d62fa-145">In this example, the client application specifies its own application dead-letter queue.</span></span>

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

 <span data-ttu-id="d62fa-146">Teslim edilemeyen mesaj servisi iletileri teslim edilemeyen kuyruktaki iletileri okur.</span><span class="sxs-lookup"><span data-stu-id="d62fa-146">The dead-letter message service reads messages from the dead-letter queue.</span></span> <span data-ttu-id="d62fa-147">Edilemeyen mesaj hizmeti uygulayan `IOrderProcessor` sözleşme.</span><span class="sxs-lookup"><span data-stu-id="d62fa-147">The dead-letter message service implements the `IOrderProcessor` contract.</span></span> <span data-ttu-id="d62fa-148">Uygulaması ancak değil işlem siparişlere.</span><span class="sxs-lookup"><span data-stu-id="d62fa-148">Its implementation however is not to process orders.</span></span> <span data-ttu-id="d62fa-149">Teslim edilemeyen mesaj servisi siparişleri işleme olanağı yok ve bir istemci hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="d62fa-149">The dead-letter message service is a client service and does not have the facility to process orders.</span></span>

> [!NOTE]
>  <span data-ttu-id="d62fa-150">Eski ileti sırası istemci kuyruk ve istemci Kuyruk yöneticisi için yereldir.</span><span class="sxs-lookup"><span data-stu-id="d62fa-150">The dead-letter queue is a client queue and is local to the client queue manager.</span></span>

 <span data-ttu-id="d62fa-151">Bir ileti teslimi ve gerçekleştirilen işlemlerin düzeltici önlemleri başarısız oldu. nedeni edilemeyen mesaj hizmeti uygulaması denetler.</span><span class="sxs-lookup"><span data-stu-id="d62fa-151">The dead-letter message service implementation checks for the reason a message failed delivery and takes corrective measures.</span></span> <span data-ttu-id="d62fa-152">Bir ileti başarısızlık iki numaralandırmalara yakalanan <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> ve <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span><span class="sxs-lookup"><span data-stu-id="d62fa-152">The reason for a message failure is captured in two enumerations, <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> and <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span></span> <span data-ttu-id="d62fa-153">Alabileceğiniz <xref:System.ServiceModel.Channels.MsmqMessageProperty> gelen <xref:System.ServiceModel.OperationContext> aşağıdaki örnek kodda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="d62fa-153">You can retrieve the <xref:System.ServiceModel.Channels.MsmqMessageProperty> from the <xref:System.ServiceModel.OperationContext> as shown in the following sample code:</span></span>

```csharp
public void SubmitPurchaseOrder(PurchaseOrder po)
{
    Console.WriteLine("Submitting purchase order did not succed ", po);
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

 <span data-ttu-id="d62fa-154">Geçerliliğini yitirmiş kuyruk iletilerindeki iletiyi işlemeyi hizmetine gönderilen iletileri ' dir.</span><span class="sxs-lookup"><span data-stu-id="d62fa-154">Messages in the dead-letter queue are messages that are addressed to the service that is processing the message.</span></span> <span data-ttu-id="d62fa-155">Bu nedenle, kuyruktan iletileri teslim edilemeyen mesaj servisi okur, Windows Communication Foundation (WCF) kanal katmanını uyuşmazlığı uç noktaların bulur ve ileti göndermez.</span><span class="sxs-lookup"><span data-stu-id="d62fa-155">Therefore, when the dead-letter message service reads messages from the queue, the Windows Communication Foundation (WCF) channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="d62fa-156">Bu durumda, ileti işleme hizmeti siparişin ele ancak edilemeyen mesaj hizmeti tarafından alındı.</span><span class="sxs-lookup"><span data-stu-id="d62fa-156">In this case, the message is addressed to the order processing service but is received by the dead-letter message service.</span></span> <span data-ttu-id="d62fa-157">Farklı bir uç noktasına yönelik bir ileti almak için bir adres filtresi eşleşen herhangi bir adres için belirtilen `ServiceBehavior`.</span><span class="sxs-lookup"><span data-stu-id="d62fa-157">To receive a message that is addressed to a different endpoint, an address filter to match any address is specified in the `ServiceBehavior`.</span></span> <span data-ttu-id="d62fa-158">Bu, başarılı bir şekilde teslim edilemeyen kuyruktan okunmak iletilerini işlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d62fa-158">This is required to successfully process messages that are read from the dead-letter queue.</span></span>

 <span data-ttu-id="d62fa-159">Başarısızlık nedeni bu örnekte, zaman aşımına uğradı ileti iletinin teslim edilemeyen mesaj servisi beşe. Diğer nedenlerle, aşağıdaki örnek kodda gösterildiği gibi teslim hatası gösterir:</span><span class="sxs-lookup"><span data-stu-id="d62fa-159">In this sample, the dead-letter message service resends the message if the reason for failure is that the message timed out. For all other reasons, it displays the delivery failure, as shown in the following sample code:</span></span>

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

 <span data-ttu-id="d62fa-160">Aşağıdaki örnek, bir edilemeyen mesaj yapılandırmasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="d62fa-160">The following sample shows the configuration for a dead-letter message:</span></span>

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

 <span data-ttu-id="d62fa-161">Çalışan örnek eski ileti sırası her uygulama için nasıl çalıştığını görmek için çalıştırmayı 3 yürütülebilir dosyaları vardır; İstemci, hizmeti ve her uygulama için teslim edilemeyen kuyruktan okuyan ve hizmete ileti beşe edilemeyen hizmet.</span><span class="sxs-lookup"><span data-stu-id="d62fa-161">In running the sample, there are 3 executables to run to see how the dead-letter queue works for each application; the client, service and a dead-letter service that reads from the dead-letter queue for each application and resends the message to the service.</span></span> <span data-ttu-id="d62fa-162">Konsol uygulamaları windows konsol çıkışında ile tümü.</span><span class="sxs-lookup"><span data-stu-id="d62fa-162">All are console applications with output in console windows.</span></span>

> [!NOTE]
>  <span data-ttu-id="d62fa-163">Sıraya alma kullanımda olduğundan, istemci ve hizmet aynı zamanda açık ve çalışıyor olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d62fa-163">Because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="d62fa-164">İstemcisini çalıştıran da kapatın ve ardından hizmeti başlatın ve hala iletilerini alır.</span><span class="sxs-lookup"><span data-stu-id="d62fa-164">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="d62fa-165">Hizmeti başlatın ve böylece kuyruğa oluşturulabilir kapatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d62fa-165">You should start the service and shut it down so that the queue can be created.</span></span>

 <span data-ttu-id="d62fa-166">İstemci, istemci çalıştırırken, ileti görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="d62fa-166">When running the client, the client displays the message:</span></span>

```
Press <ENTER> to terminate client.
```

 <span data-ttu-id="d62fa-167">İletiyi göndermek istemci çalıştı ancak kısa bir zaman aşımı iletisi süresi doldu ve artık her uygulama için eski ileti sırası olarak sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="d62fa-167">The client attempted to send the message but with a short timeout, the message expired and is now queued in the dead-letter queue for each application.</span></span>

 <span data-ttu-id="d62fa-168">İletiyi okur ve görüntüler hata kodu ve ileti hizmet beşe edilemeyen hizmet çalıştırılacaktır.</span><span class="sxs-lookup"><span data-stu-id="d62fa-168">You then run the dead-letter service, which reads the message and displays the error code and resends the message back to the service.</span></span>

```
The dead letter service is ready.
Press <ENTER> to terminate service.

Submitting purchase order did not succeed
Message Delivery Status: InDoubt
Message Delivery Failure: ReachQueueTimeout

Purchase order Time To Live expired
Trying to resend the message
Purchase order resent
```

 <span data-ttu-id="d62fa-169">Hizmet başlar ve ardından yakın iletiyi okur ve işler.</span><span class="sxs-lookup"><span data-stu-id="d62fa-169">The service starts and then reads the resent message and processes it.</span></span>

```
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

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d62fa-170">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d62fa-170">To set up, build, and run the sample</span></span>

1.  <span data-ttu-id="d62fa-171">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d62fa-171">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2.  <span data-ttu-id="d62fa-172">Hizmet ilk olarak çalıştırılırsa, sıranın mevcut olduğundan emin olun kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="d62fa-172">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="d62fa-173">Kuyruk yoksa, bir hizmeti oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="d62fa-173">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="d62fa-174">İlk sırayı oluşturmak için hizmet çalıştırabileceğiniz veya bir MSMQ Kuyruk Yöneticisi ile oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d62fa-174">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="d62fa-175">Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="d62fa-175">Follow these steps to create a queue in Windows 2008.</span></span>

    1.  <span data-ttu-id="d62fa-176">Visual Studio 2012'de Sunucu Yöneticisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="d62fa-176">Open Server Manager in Visual Studio 2012.</span></span>

    2.  <span data-ttu-id="d62fa-177">Genişletin **özellikleri** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="d62fa-177">Expand the **Features** tab.</span></span>

    3.  <span data-ttu-id="d62fa-178">Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.</span><span class="sxs-lookup"><span data-stu-id="d62fa-178">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4.  <span data-ttu-id="d62fa-179">Denetleme **işlem** kutusu.</span><span class="sxs-lookup"><span data-stu-id="d62fa-179">Check the **Transactional** box.</span></span>

    5.  <span data-ttu-id="d62fa-180">Girin `ServiceModelSamplesTransacted` yeni Kuyruğun adı.</span><span class="sxs-lookup"><span data-stu-id="d62fa-180">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3.  <span data-ttu-id="d62fa-181">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d62fa-181">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4.  <span data-ttu-id="d62fa-182">Örnek tek veya çoklu bilgisayar yapılandırma değişikliği kuyrukta adları uygun şekilde, localhost bilgisayarın tam adıyla değiştirerek çalıştırıp yönergeleri [WindowsCommunicationFoundationörnekleriniçalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d62fa-182">To run the sample in a single- or cross-computer configuration change queue names appropriately, replacing localhost with full name of the computer and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="d62fa-183">Örneği için bir çalışma alanına katılmış bir bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="d62fa-183">To run the sample on a computer joined to a workgroup</span></span>

1.  <span data-ttu-id="d62fa-184">Bilgisayarınız bir etki alanının parçası değilse, kimlik doğrulama modu ve koruma düzeyi ayarlayarak aktarım güvenliği devre dışı kapatma `None` aşağıdaki örnek yapılandırmada gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="d62fa-184">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="d62fa-185">Uç nokta bağlamayla ilişkili uç noktanın ayarlayarak olduğundan emin olun `bindingConfiguration` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d62fa-185">Ensure the endpoint is associated with the binding by setting the endpoint's `bindingConfiguration` attribute.</span></span>

2.  <span data-ttu-id="d62fa-186">Örneği çalıştırmadan önce DeadLetterService, sunucu ve istemci üzerindeki yapılandırmayı değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d62fa-186">Ensure that you change the configuration on the DeadLetterService, server and the client before you run the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="d62fa-187">Ayarı `security mode` için `None` ayarlamakla eşdeğerdir `MsmqAuthenticationMode`, `MsmqProtectionLevel` ve `Message` güvenlik `None`.</span><span class="sxs-lookup"><span data-stu-id="d62fa-187">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>

## <a name="comments"></a><span data-ttu-id="d62fa-188">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d62fa-188">Comments</span></span>
 <span data-ttu-id="d62fa-189">Varsayılan olarak `netMsmqBinding` bağlama taşıma, güvenlik etkin.</span><span class="sxs-lookup"><span data-stu-id="d62fa-189">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="d62fa-190">İki özellik `MsmqAuthenticationMode` ve `MsmqProtectionLevel`, birlikte aktarım güvenliği türünü belirleyin.</span><span class="sxs-lookup"><span data-stu-id="d62fa-190">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="d62fa-191">Varsayılan kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`.</span><span class="sxs-lookup"><span data-stu-id="d62fa-191">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="d62fa-192">Kimlik doğrulama ve imzalama özelliği sağlamak MSMQ için bir etki alanının parçası olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d62fa-192">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="d62fa-193">Bu örnek, bir etki alanının parçası olmayan bir bilgisayar üzerinde çalıştırırsanız, aşağıdaki hatayı alırsınız: "kullanıcının iç message queuing sertifika mevcut değil".</span><span class="sxs-lookup"><span data-stu-id="d62fa-193">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="d62fa-194">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="d62fa-194">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d62fa-195">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d62fa-195">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d62fa-196">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d62fa-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d62fa-197">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d62fa-197">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
  
## <a name="see-also"></a><span data-ttu-id="d62fa-198">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d62fa-198">See Also</span></span>
