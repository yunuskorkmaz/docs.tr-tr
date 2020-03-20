---
title: Teslim Edilemeyen İletiler Sırası
ms.date: 03/30/2017
ms.assetid: ff664f33-ad02-422c-9041-bab6d993f9cc
ms.openlocfilehash: eab1c52f4d0b3d0f82cf561a9478ea8233598e1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144954"
---
# <a name="dead-letter-queues"></a><span data-ttu-id="5b9b8-102">Teslim Edilemeyen İletiler Sırası</span><span class="sxs-lookup"><span data-stu-id="5b9b8-102">Dead Letter Queues</span></span>
<span data-ttu-id="5b9b8-103">Bu örnek, teslimbaşarısız olan iletilerin nasıl işleyeceğini ve işleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-103">This sample demonstrates how to handle and process messages that have failed delivery.</span></span> <span data-ttu-id="5b9b8-104">[İşlenmiş MSMQ Bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örneğine dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-104">It is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="5b9b8-105">Bu örnek `netMsmqBinding` bağlama kullanır.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-105">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="5b9b8-106">Hizmet, sıraya alınan iletileri alan hizmeti gözlemlemenizi sağlayan, kendi kendine barındırılan bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

> [!NOTE]
> <span data-ttu-id="5b9b8-107">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="5b9b8-108">Bu örnek, yalnızca Windows Vista'da kullanılabilen her uygulama ölü harf sıranı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-108">This sample demonstrates each application dead letter queue that is only available on Windows Vista.</span></span> <span data-ttu-id="5b9b8-109">Örnek, Windows Server 2003 ve Windows XP'de MSMQ 3.0 için varsayılan sistem çapındaki kuyrukları kullanacak şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-109">The sample can be modified to use the default system-wide queues for MSMQ 3.0 on Windows Server 2003 and Windows XP.</span></span>

 <span data-ttu-id="5b9b8-110">Sıralı iletişimde, istemci bir sıra kullanarak hizmete iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-110">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="5b9b8-111">Daha doğrusu, istemci sıraya ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-111">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="5b9b8-112">Hizmet, kuyruktan iletiler alır.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-112">The service receives messages from the queue.</span></span> <span data-ttu-id="5b9b8-113">Bu nedenle, hizmet ve istemci, bir sıra kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-113">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="5b9b8-114">Sıralı iletişim belirli bir miktarda uyku damıtma içerebileceğinden, iletinin zaman geçtiyse uygulamaya teslim edilmediğinden emin olmak için iletide bir zaman-canlı değeri ilişkilendirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-114">Because queued communication can involve a certain amount of dormancy, you may want to associate a time-to-live value on the message to ensure that the message does not get delivered to the application if it has gone past the time.</span></span> <span data-ttu-id="5b9b8-115">Ayrıca, bir uygulamanın iletinin teslimde başarısız olup olmadığı konusunda bilgilendirilmeleri gereken durumlar da vardır.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-115">There are also cases, where an application must be informed whether a message failed delivery.</span></span> <span data-ttu-id="5b9b8-116">İletide yayınlanacak zaman dolduğunda veya ileti nin teslimi başarısız olduğunda, ileti nin ölü harf kuyruğuna konması gibi tüm bu gibi durumlarda.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-116">In all of these cases, such as when the time-to-live on the message has expired or the message failed delivery, the message is put in a dead letter queue.</span></span> <span data-ttu-id="5b9b8-117">Gönderme uygulaması daha sonra ölü harf kuyruğundaki iletileri okuyabilir ve hiçbir eylemden başarısız teslimin nedenlerini düzeltmeye ve iletiyi yeniden göndermeye kadar değişen düzeltici eylemlerde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-117">The sending application can then read the messages in the dead-letter queue and take corrective actions that range from no action to correcting the reasons for failed delivery and resending the message.</span></span>

 <span data-ttu-id="5b9b8-118">`NetMsmqBinding` Bağlamadaki ölü harf sırası aşağıdaki özelliklerle ifade edilir:</span><span class="sxs-lookup"><span data-stu-id="5b9b8-118">The dead-letter queue in the `NetMsmqBinding` binding is expressed in the following properties:</span></span>

- <span data-ttu-id="5b9b8-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>istemci tarafından gerekli ölü harf sırası türünü ifade etmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-119"><xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A> property to express the kind of dead-letter queue required by the client.</span></span> <span data-ttu-id="5b9b8-120">Bu numaralandırma aşağıdaki değerlere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5b9b8-120">This enumeration has the following values:</span></span>

- <span data-ttu-id="5b9b8-121">`None`: İstemci tarafından ölü harf sırası gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-121">`None`: No dead-letter queue is required by the client.</span></span>

- <span data-ttu-id="5b9b8-122">`System`: Sistem ölü harf sırası ölü iletileri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-122">`System`: The system dead-letter queue is used to store dead messages.</span></span> <span data-ttu-id="5b9b8-123">Sistem ölü harf sırası bilgisayarda çalışan tüm uygulamalar tarafından paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-123">The system dead-letter queue is shared by all applications running on the computer.</span></span>

- <span data-ttu-id="5b9b8-124">`Custom`: Ölü iletileri depolamak <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> için özelliği kullanarak belirtilen özel bir ölü harf sırası kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-124">`Custom`: A custom dead-letter queue specified using the <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property is used to store dead messages.</span></span> <span data-ttu-id="5b9b8-125">Bu özellik yalnızca Windows Vista'da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-125">This feature is only available on Windows Vista.</span></span> <span data-ttu-id="5b9b8-126">Bu, uygulamanın aynı bilgisayarda çalışan diğer uygulamalarla paylaşmak yerine kendi ölü harf sırasını kullanması gerektiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-126">This is used when the application must use its own dead letter queue instead of sharing it with other applications running on the same computer.</span></span>

- <span data-ttu-id="5b9b8-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>ölü harf sırası olarak kullanılacak belirli sırayı ifade etme özelliği.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-127"><xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A> property to express the specific queue to use as a dead-letter queue.</span></span> <span data-ttu-id="5b9b8-128">Bu yalnızca Windows Vista'da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-128">This is available only in Windows Vista.</span></span>

 <span data-ttu-id="5b9b8-129">Bu örnekte, istemci bir işlem kapsamından hizmete bir toplu ileti gönderir ve bu iletiler için "canlı kullanım süresi" için rasgele düşük bir değer belirtir (yaklaşık 2 saniye).</span><span class="sxs-lookup"><span data-stu-id="5b9b8-129">In this sample, the client sends a batch of messages to the service from within the scope of a transaction and specifies an arbitrarily low value for "time-to-live" for these messages (about 2 seconds).</span></span> <span data-ttu-id="5b9b8-130">İstemci ayrıca, süresi dolmuş iletileri sıraya girmek için kullanılacak özel bir ölü harf kuyruğu da belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-130">The client also specifies a custom dead-letter queue to use to enqueue the messages that have expired.</span></span>

 <span data-ttu-id="5b9b8-131">İstemci uygulaması ölü harf kuyruğundaki iletileri okuyabilir ve iletiyi yeniden göndermeyi deneyebilir veya özgün iletinin ölü harf kuyruğuna yerleştirilmesine ve iletiyi göndermesine neden olan hatayı düzeltebilir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-131">The client application can read the messages in the dead-letter queue and either retry sending the message or correct the error that caused the original message to be placed in the dead-letter queue and send the message.</span></span> <span data-ttu-id="5b9b8-132">Örnekte, istemci bir hata iletisi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-132">In the sample, the client displays an error message.</span></span>

 <span data-ttu-id="5b9b8-133">Hizmet sözleşmesi, `IOrderProcessor`aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-133">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="5b9b8-134">Örnekteki hizmet [kodu, İşlenmiş MSMQ Bağlama'ya](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)ait.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-134">The service code in the sample is that of the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>

 <span data-ttu-id="5b9b8-135">Hizmetle iletişim bir işlem kapsamında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-135">Communication with the service takes place within the scope of a transaction.</span></span> <span data-ttu-id="5b9b8-136">Hizmet kuyruktaki iletileri okur, işlemi gerçekleştirir ve ardından işlemin sonuçlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-136">The service reads messages from the queue, performs the operation and then displays the results of the operation.</span></span> <span data-ttu-id="5b9b8-137">Uygulama ayrıca ölü harfli iletiler için ölü harf sırası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-137">The application also creates a dead-letter queue for dead-letter messages.</span></span>

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

 <span data-ttu-id="5b9b8-138">İstemcinin yapılandırması, iletinin hizmete ulaşması için kısa bir süre belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-138">The client's configuration specifies a short duration for the message to reach the service.</span></span> <span data-ttu-id="5b9b8-139">İleti belirtilen süre içinde iletilemiyorsa, iletinin süresi doluyor ve ölü harf sırasına taşınır.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-139">If the message cannot be transmitted within the duration specified, the message expires and is moved to the dead-letter queue.</span></span>

> [!NOTE]
> <span data-ttu-id="5b9b8-140">İstemcinin iletiyi belirtilen süre içinde servis kuyruğuna teslim etmesi mümkündür.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-140">It is possible for the client to deliver the message to the service queue within the specified time.</span></span> <span data-ttu-id="5b9b8-141">Ölü harf hizmetini iş başında gördüğünüzden emin olmak için, hizmeti başlatmadan önce istemciyi çalıştırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-141">To ensure you see the dead-letter service in action, you should run the client before starting the service.</span></span> <span data-ttu-id="5b9b8-142">İleti zaman ları dışarı ve ölü harf servisine teslim edilir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-142">The message times out and is delivered to the dead-letter service.</span></span>

 <span data-ttu-id="5b9b8-143">Uygulama, ölü harf sırası olarak hangi sıranın kullanılacağını tanımlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-143">The application must define which queue to use as its dead-letter queue.</span></span> <span data-ttu-id="5b9b8-144">Sıra belirtilmemişse, varsayılan sistem genelinde ki işlem li harf sırası ölü iletileri sıraya almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-144">If no queue is specified, the default system-wide transactional dead-letter queue is used to queue dead messages.</span></span> <span data-ttu-id="5b9b8-145">Bu örnekte, istemci uygulaması kendi uygulama ölü harf sırasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-145">In this example, the client application specifies its own application dead-letter queue.</span></span>

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

 <span data-ttu-id="5b9b8-146">Ölü harfli ileti hizmeti, ölü harf kuyruğundan gelen iletileri okur.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-146">The dead-letter message service reads messages from the dead-letter queue.</span></span> <span data-ttu-id="5b9b8-147">Ölü harfli ileti hizmeti `IOrderProcessor` sözleşmeyi uygular.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-147">The dead-letter message service implements the `IOrderProcessor` contract.</span></span> <span data-ttu-id="5b9b8-148">Ancak uygulanması siparişleri işlemek değildir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-148">Its implementation however is not to process orders.</span></span> <span data-ttu-id="5b9b8-149">Ölü harfileti hizmeti bir istemci hizmetidir ve siparişleri işleme imla sıyrık ları yoktur.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-149">The dead-letter message service is a client service and does not have the facility to process orders.</span></span>

> [!NOTE]
> <span data-ttu-id="5b9b8-150">Ölü harf sırası bir istemci sırasıdır ve istemci sıra yöneticisi için yereldir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-150">The dead-letter queue is a client queue and is local to the client queue manager.</span></span>

 <span data-ttu-id="5b9b8-151">Ölü harfli ileti hizmeti uygulaması, iletinin teslimi başarısız olmasının nedenini denetler ve düzeltici önlemler alır.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-151">The dead-letter message service implementation checks for the reason a message failed delivery and takes corrective measures.</span></span> <span data-ttu-id="5b9b8-152">İleti başarısızlığının nedeni iki sayısallandırmada yakalanır <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> ve <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-152">The reason for a message failure is captured in two enumerations, <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryFailure%2A> and <xref:System.ServiceModel.Channels.MsmqMessageProperty.DeliveryStatus%2A>.</span></span> <span data-ttu-id="5b9b8-153">Aşağıdaki örnek <xref:System.ServiceModel.Channels.MsmqMessageProperty> kodda <xref:System.ServiceModel.OperationContext> gösterildiği gibi alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5b9b8-153">You can retrieve the <xref:System.ServiceModel.Channels.MsmqMessageProperty> from the <xref:System.ServiceModel.OperationContext> as shown in the following sample code:</span></span>

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

 <span data-ttu-id="5b9b8-154">Ölü harf kuyruğundaki iletiler, iletiyi işleyen hizmete gönderilen iletilerdir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-154">Messages in the dead-letter queue are messages that are addressed to the service that is processing the message.</span></span> <span data-ttu-id="5b9b8-155">Bu nedenle, ölü harfileti hizmeti kuyruktaki iletileri okuduğunda, Windows Communication Foundation (WCF) kanal katmanı uyuşmazlığı uç noktalarda bulur ve iletiyi göndermez.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-155">Therefore, when the dead-letter message service reads messages from the queue, the Windows Communication Foundation (WCF) channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="5b9b8-156">Bu durumda, ileti sipariş işleme hizmetine yöneliktir, ancak ölü harf iletisi hizmeti tarafından alınır.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-156">In this case, the message is addressed to the order processing service but is received by the dead-letter message service.</span></span> <span data-ttu-id="5b9b8-157">Farklı bir uç noktaya yönelik bir ileti almak için, herhangi bir adresle `ServiceBehavior`eşleşen bir adres filtresi .</span><span class="sxs-lookup"><span data-stu-id="5b9b8-157">To receive a message that is addressed to a different endpoint, an address filter to match any address is specified in the `ServiceBehavior`.</span></span> <span data-ttu-id="5b9b8-158">Bu, ölü harf kuyruğundan okunan iletileri başarıyla işlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-158">This is required to successfully process messages that are read from the dead-letter queue.</span></span>

 <span data-ttu-id="5b9b8-159">Bu örnekte, başarısız olmasının nedeni iletinin zaman lanmış olmasıysa, ölü harf iletisi hizmeti iletiyi yeniden gönderir. Diğer tüm nedenlerle, aşağıdaki örnek kodda gösterildiği gibi teslim hatasını görüntüler:</span><span class="sxs-lookup"><span data-stu-id="5b9b8-159">In this sample, the dead-letter message service resends the message if the reason for failure is that the message timed out. For all other reasons, it displays the delivery failure, as shown in the following sample code:</span></span>

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

 <span data-ttu-id="5b9b8-160">Aşağıdaki örnek, ölü harfli ileti yapılandırmasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5b9b8-160">The following sample shows the configuration for a dead-letter message:</span></span>

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

 <span data-ttu-id="5b9b8-161">Örneği çalıştıran, ölü harf sırasının her uygulama için nasıl çalıştığını görmek için çalıştırılabilen 3 yürütülebilir vardır; istemci, hizmet ve her uygulama için ölü harf kuyruğundan okuyan ve iletiyi hizmete yeniden gönderen bir ölü harf hizmeti.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-161">In running the sample, there are 3 executables to run to see how the dead-letter queue works for each application; the client, service and a dead-letter service that reads from the dead-letter queue for each application and resends the message to the service.</span></span> <span data-ttu-id="5b9b8-162">Tüm konsol pencerelerinde çıkış ile konsol uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-162">All are console applications with output in console windows.</span></span>

> [!NOTE]
> <span data-ttu-id="5b9b8-163">Kuyruk kullanımda olduğundan, istemci ve hizmetin aynı anda çalışır durumda olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-163">Because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="5b9b8-164">İstemciyi çalıştırabilir, kapatabilir ve sonra hizmeti başlatabilir ve yine de iletilerini alır.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-164">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="5b9b8-165">Sıranın oluşturulabilmesi için hizmeti başlatıp kapatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-165">You should start the service and shut it down so that the queue can be created.</span></span>

 <span data-ttu-id="5b9b8-166">İstemciyi çalıştırırken, istemci iletiyi görüntüler:</span><span class="sxs-lookup"><span data-stu-id="5b9b8-166">When running the client, the client displays the message:</span></span>

```console
Press <ENTER> to terminate client.
```

 <span data-ttu-id="5b9b8-167">İstemci iletiyi göndermeyi denedi, ancak kısa bir zaman aşımıyla iletinin süresi doldu ve artık her uygulama için ölü harf kuyruğunda sıraya girdi.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-167">The client attempted to send the message but with a short timeout, the message expired and is now queued in the dead-letter queue for each application.</span></span>

 <span data-ttu-id="5b9b8-168">Daha sonra, iletiyi okuyan ve hata kodunu görüntüleyen ve iletiyi hizmete geri gönderen ölü harf li servisini çalıştırırsınız.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-168">You then run the dead-letter service, which reads the message and displays the error code and resends the message back to the service.</span></span>

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

 <span data-ttu-id="5b9b8-169">Hizmet başlar ve sonra dargın iletiyi okur ve işler.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-169">The service starts and then reads the resent message and processes it.</span></span>

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

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5b9b8-170">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5b9b8-170">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="5b9b8-171">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-171">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="5b9b8-172">Önce hizmet çalıştırılırsa, sıranın mevcut olduğundan emin olmak için denetler.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-172">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="5b9b8-173">Sıra yoksa, hizmet bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-173">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="5b9b8-174">Sırayı oluşturmak için önce hizmeti çalıştırabilir veya MSMQ Sıra Yöneticisi aracılığıyla bir hizmet oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-174">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="5b9b8-175">Windows 2008'de bir sıra oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-175">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="5b9b8-176">Visual Studio 2012'de Sunucu Yöneticisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-176">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="5b9b8-177">**Özellikler** sekmesini genişletin.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-177">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="5b9b8-178">Özel **İleti Kuyrukları'nı**sağ tıklatın ve **Yeni**, **Özel Sıra'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-178">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="5b9b8-179">**İşlem** kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-179">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="5b9b8-180">Yeni `ServiceModelSamplesTransacted` sıranın adı olarak girin.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-180">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="5b9b8-181">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-181">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="5b9b8-182">Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak için sıra adlarını uygun şekilde değiştirin, localhost'u bilgisayarın tam adı ile değiştirin ve [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-182">To run the sample in a single- or cross-computer configuration change queue names appropriately, replacing localhost with full name of the computer and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="5b9b8-183">Bir çalışma grubuna katılan bir bilgisayarda örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5b9b8-183">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="5b9b8-184">Bilgisayarınız bir etki alanının parçası değilse, kimlik doğrulama modunu ve koruma `None` düzeyini aşağıdaki örnek yapılandırmada gösterildiği gibi ayarlayarak aktarım güvenliğini kapatın:</span><span class="sxs-lookup"><span data-stu-id="5b9b8-184">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="5b9b8-185">Bitiş noktasının özniteliğini ayarlayarak bitiş noktasının `bindingConfiguration` bağlamayla ilişkili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-185">Ensure the endpoint is associated with the binding by setting the endpoint's `bindingConfiguration` attribute.</span></span>

2. <span data-ttu-id="5b9b8-186">Örneği çalıştırmadan önce DeadLetterService, sunucu ve istemcideki yapılandırmayı değiştirdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-186">Ensure that you change the configuration on the DeadLetterService, server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5b9b8-187">`None` Ayar `security mode` ayarı `MsmqAuthenticationMode` `MsmqProtectionLevel` ve `Message` güvenlik ' `None`e eşittir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-187">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>

## <a name="comments"></a><span data-ttu-id="5b9b8-188">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="5b9b8-188">Comments</span></span>
 <span data-ttu-id="5b9b8-189">`netMsmqBinding` Varsayılan olarak bağlama aktarımı ile güvenlik etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-189">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="5b9b8-190">İki özellik `MsmqAuthenticationMode` `MsmqProtectionLevel`ve birlikte aktarım güvenlik türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-190">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="5b9b8-191">Varsayılan olarak kimlik doğrulama modu `Windows` ayarlanır ve koruma `Sign`düzeyi .</span><span class="sxs-lookup"><span data-stu-id="5b9b8-191">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="5b9b8-192">MSMQ'nun kimlik doğrulama ve imzalama özelliğini sağlaması için, bir etki alanının parçası olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-192">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="5b9b8-193">Bu örneği etki alanının parçası olmayan bir bilgisayarda çalıştırıyorsanız, aşağıdaki hatayı alırsınız: "Kullanıcının iç ileti sıraya alma sertifikası yok".</span><span class="sxs-lookup"><span data-stu-id="5b9b8-193">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b9b8-194">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-194">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5b9b8-195">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-195">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5b9b8-196">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5b9b8-197">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="5b9b8-197">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\DeadLetter`  
