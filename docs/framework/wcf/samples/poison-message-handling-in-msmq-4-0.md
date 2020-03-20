---
title: MSMQ 4.0'da Zehirli İleti İşleme
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: 4b662094923c85e825edcc9025a73f1a1b42cb9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144246"
---
# <a name="poison-message-handling-in-msmq-40"></a><span data-ttu-id="19d7d-102">MSMQ 4.0'da Zehirli İleti İşleme</span><span class="sxs-lookup"><span data-stu-id="19d7d-102">Poison Message Handling in MSMQ 4.0</span></span>
<span data-ttu-id="19d7d-103">Bu örnek, bir hizmette zehirli ileti işlemenin nasıl gerçekleştirilgösterdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-103">This sample demonstrates how to perform poison message handling in a service.</span></span> <span data-ttu-id="19d7d-104">Bu [örnek, Transacted MSMQ Bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örneğine dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="19d7d-104">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="19d7d-105">Bu örnek `netMsmqBinding`te .</span><span class="sxs-lookup"><span data-stu-id="19d7d-105">This sample uses the `netMsmqBinding`.</span></span> <span data-ttu-id="19d7d-106">Hizmet, sıraya alınan iletileri alan hizmeti gözlemlemenizi sağlayan, kendi kendine barındırılan bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="19d7d-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="19d7d-107">Sıralı iletişimde, istemci bir sıra kullanarak hizmete iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="19d7d-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="19d7d-108">Daha doğrusu, istemci sıraya ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="19d7d-109">Hizmet, kuyruktan iletiler alır.</span><span class="sxs-lookup"><span data-stu-id="19d7d-109">The service receives messages from the queue.</span></span> <span data-ttu-id="19d7d-110">Bu nedenle, hizmet ve istemci, bir sıra kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="19d7d-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="19d7d-111">Zehirli ileti, iletiyi okuyan hizmet iletiyi işleyemediğinde ve bu nedenle iletinin okunduğu işlemi sonlandırdığinde, bir kuyruktan sürekli olarak okunan iletidir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-111">A poison message is a message that is repeatedly read from a queue when the service reading the message cannot process the message and therefore terminates the transaction under which the message is read.</span></span> <span data-ttu-id="19d7d-112">Bu gibi durumlarda, ileti yeniden denendir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-112">In such cases, the message is retried again.</span></span> <span data-ttu-id="19d7d-113">İletiyle ilgili bir sorun varsa, bu teorik olarak sonsuza kadar devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-113">This can theoretically go on forever if there is a problem with the message.</span></span> <span data-ttu-id="19d7d-114">Bu yalnızca kuyruktan okumak ve hizmet işlemini çağırmak için hareketleri kullandığınızda oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-114">This can only occur when you use transactions to read from the queue and invoke the service operation.</span></span>

 <span data-ttu-id="19d7d-115">MSMQ sürümüne dayanarak, NetMsmqBinding zehirli mesajların tam tespiti için sınırlı algılama destekler.</span><span class="sxs-lookup"><span data-stu-id="19d7d-115">Based on the version of MSMQ, the NetMsmqBinding supports limited detection to full detection of poison messages.</span></span> <span data-ttu-id="19d7d-116">İleti nin zehirlendiği tespit edildikten sonra, çeşitli şekillerde ele alınabilir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-116">After the message has been detected as poisoned, then it can be handled in several ways.</span></span> <span data-ttu-id="19d7d-117">Yine, MSMQ sürümüne dayalı, NetMsmqBinding zehirli mesajların tam işleme sınırlı işleme destekler.</span><span class="sxs-lookup"><span data-stu-id="19d7d-117">Again, based on the version of MSMQ, the NetMsmqBinding supports limited handling to full handling of poison messages.</span></span>

 <span data-ttu-id="19d7d-118">Bu örnek, Windows Server 2003 ve Windows XP platformunda sağlanan sınırlı zehir lenme olanaklarını ve Windows Vista'da sağlanan tam zehir lenme olanaklarını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-118">This sample illustrates the limited poison facilities provided on Windows Server 2003 and Windows XP platform and the full poison facilities provided on Windows Vista.</span></span> <span data-ttu-id="19d7d-119">Her iki örnekte de amaç, zehir iletisini sıranın dışına başka bir sıraya taşımaktır.</span><span class="sxs-lookup"><span data-stu-id="19d7d-119">In both samples, the objective is to move the poison message out of the queue to another queue.</span></span> <span data-ttu-id="19d7d-120">Bu sıra daha sonra bir zehirli ileti hizmeti tarafından servis edilebilir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-120">That queue can then be serviced by a poison message service.</span></span>

## <a name="msmq-v40-poison-handling-sample"></a><span data-ttu-id="19d7d-121">MSMQ v4.0 Zehir İşleme Örneği</span><span class="sxs-lookup"><span data-stu-id="19d7d-121">MSMQ v4.0 Poison Handling Sample</span></span>
 <span data-ttu-id="19d7d-122">Windows Vista'da, MSMQ zehirli iletileri depolamak için kullanılabilecek bir zehirli alt sıra olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="19d7d-122">In Windows Vista, MSMQ provides a poison subqueue facility that can be used to store poison messages.</span></span> <span data-ttu-id="19d7d-123">Bu örnek, Windows Vista kullanarak zehirli iletilerle başa çıkmanın en iyi uygulamalarını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-123">This sample demonstrates the best practice of dealing with poison messages using Windows Vista.</span></span>

 <span data-ttu-id="19d7d-124">Windows Vista'daki zehirli ileti algılama sı sofistikedir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-124">The poison message detection in Windows Vista is sophisticated.</span></span> <span data-ttu-id="19d7d-125">Algılamaya yardımcı olan 3 özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="19d7d-125">There are 3 properties that help with detection.</span></span> <span data-ttu-id="19d7d-126">Belirli <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> bir iletinin kuyruktan yeniden okunması ve işleme için uygulamaya gönderilmesi sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="19d7d-126">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is number of times a given message is re-read from the queue and dispatched to the application for processing.</span></span> <span data-ttu-id="19d7d-127">İleti uygulamaya gönderilemediği için sıraya geri konulduğunda bir ileti kuyruktan yeniden okunur veya uygulama hizmet işleminde hareketi geri alır.</span><span class="sxs-lookup"><span data-stu-id="19d7d-127">A message is re-read from the queue when it is put back into the queue because the message cannot be dispatched to the application or the application rolls back the transaction in the service operation.</span></span> <span data-ttu-id="19d7d-128"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>iletinin yeniden deneme kuyruğuna kaç kez taşındığıdır.</span><span class="sxs-lookup"><span data-stu-id="19d7d-128"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> is the number of times the message is moved to the retry queue.</span></span> <span data-ttu-id="19d7d-129"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Erişildiğinde, ileti yeniden deneme sırasına taşınır.</span><span class="sxs-lookup"><span data-stu-id="19d7d-129">When <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reached, the message is moved to the retry queue.</span></span> <span data-ttu-id="19d7d-130"><xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> Özellik, iletinin yeniden deneme kuyruğundan ana kuyruğa geri taşındığı zaman gecikmesidir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-130">The property <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> is the time delay after which the message is moved from the retry queue back to the main queue.</span></span> <span data-ttu-id="19d7d-131">Sıfırlanır <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> 0.0.'dır.</span><span class="sxs-lookup"><span data-stu-id="19d7d-131">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reset to 0.</span></span> <span data-ttu-id="19d7d-132">İleti yeniden denendi.</span><span class="sxs-lookup"><span data-stu-id="19d7d-132">The message is tried again.</span></span> <span data-ttu-id="19d7d-133">İletiyi okumaya yönelik tüm denemeler başarısız olduysa, ileti zehirli olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-133">If all attempts to read the message have failed, then the message is marked as poisoned.</span></span>

 <span data-ttu-id="19d7d-134">İleti zehirli olarak işaretlendikten sonra, ileti numaralandırmadaki <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> ayarlara göre ele alınır.</span><span class="sxs-lookup"><span data-stu-id="19d7d-134">Once the message is marked as poisoned, the message is dealt with according to the settings in the <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeration.</span></span> <span data-ttu-id="19d7d-135">Olası değerleri yinelemek için:</span><span class="sxs-lookup"><span data-stu-id="19d7d-135">To reiterate the possible values:</span></span>

- <span data-ttu-id="19d7d-136">Hata (varsayılan): Dinleyiciyi ve hizmet ana bilgisayarını hata etmek.</span><span class="sxs-lookup"><span data-stu-id="19d7d-136">Fault (default): To fault the listener and also the service host.</span></span>

- <span data-ttu-id="19d7d-137">Bırak: İletiyi bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="19d7d-137">Drop: To drop the message.</span></span>

- <span data-ttu-id="19d7d-138">Taşı: İletiyi zehirli ileti alt sırasına taşımak için.</span><span class="sxs-lookup"><span data-stu-id="19d7d-138">Move: To move the message to the poison message subqueue.</span></span> <span data-ttu-id="19d7d-139">Bu değer yalnızca Windows Vista'da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-139">This value is available only on Windows Vista.</span></span>

- <span data-ttu-id="19d7d-140">Reddet: İletiyi reddetmek ve iletiyi gönderenin ölü harf kuyruğuna geri göndermek.</span><span class="sxs-lookup"><span data-stu-id="19d7d-140">Reject: To reject the message, sending the message back to the sender's dead-letter queue.</span></span> <span data-ttu-id="19d7d-141">Bu değer yalnızca Windows Vista'da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-141">This value is available only on Windows Vista.</span></span>

 <span data-ttu-id="19d7d-142">Örnek, zehir mesajının eğiliminin `Move` kullanılmasını gösteriyor.</span><span class="sxs-lookup"><span data-stu-id="19d7d-142">The sample demonstrates using the `Move` disposition for the poison message.</span></span> <span data-ttu-id="19d7d-143">`Move`iletinin zehirli alt sıraya taşınmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="19d7d-143">`Move` causes the message to move to the poison subqueue.</span></span>

 <span data-ttu-id="19d7d-144">Hizmet sözleşmesi, `IOrderProcessor`kuyruklarla kullanıma uygun tek yönlü bir hizmeti tanımlayan sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-144">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="19d7d-145">Hizmet işlemi, siparişi işlettiğini belirten bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="19d7d-145">The service operation displays a message stating it is processing the order.</span></span> <span data-ttu-id="19d7d-146">Zehir iletisi işlevselliğini `SubmitPurchaseOrder` göstermek için, hizmet işlemi, hizmetin rasgele bir çağırması üzerine hareketi geri almak için bir özel durum atar.</span><span class="sxs-lookup"><span data-stu-id="19d7d-146">To demonstrate the poison message functionality, the `SubmitPurchaseOrder` service operation throws an exception to roll back the transaction on a random invocation of the service.</span></span> <span data-ttu-id="19d7d-147">Bu, iletinin sıraya geri konmasını neden olur.</span><span class="sxs-lookup"><span data-stu-id="19d7d-147">This causes the message to be put back in the queue.</span></span> <span data-ttu-id="19d7d-148">Sonunda mesaj zehir olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-148">Eventually the message is marked as poison.</span></span> <span data-ttu-id="19d7d-149">Yapılandırma, zehir iletisini zehir alt sırasına taşımak için ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="19d7d-149">The configuration is set to move the poison message to the poison subqueue.</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    static Random r = new Random(137);

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {

        int randomNumber = r.Next(10);

        if (randomNumber % 2 == 0)
        {
            Orders.Add(po);
            Console.WriteLine("Processing {0} ", po);
        }
        else
        {
            Console.WriteLine("Aborting transaction, cannot process purchase order: " + po.PONumber);
            Console.WriteLine();
            throw new Exception("Cannot process purchase order: " + po.PONumber);
        }
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted");
    }

    // Host the service within this EXE console application.
    public static void Main()
    {
        // Get MSMQ queue name from app settings in configuration.
        string queueName = ConfigurationManager.AppSettings["queueName"];

        // Create the transacted MSMQ queue if necessary.
        if (!System.Messaging.MessageQueue.Exists(queueName))
            System.Messaging.MessageQueue.Create(queueName, true);

        // Get the base address that is used to listen for WS-MetaDataExchange requests.
        // This is useful to generate a proxy for the client.
        string baseAddress = ConfigurationManager.AppSettings["baseAddress"];

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService), new Uri(baseAddress));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        // Open the ServiceHostBase to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        if(serviceHost.State != CommunicationState.Faulted) {
            serviceHost.Close();
        }

    }
}
```

 <span data-ttu-id="19d7d-150">Hizmet yapılandırması aşağıdaki zehirli ileti `receiveRetryCount` `maxRetryCycles`özelliklerini `retryCycleDelay`içerir: , , ve `receiveErrorHandling` aşağıdaki yapılandırma dosyasında gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="19d7d-150">The service configuration includes the following poison message properties: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, and `receiveErrorHandling` as shown in the following configuration file.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesPoison" />
    <add key="baseAddress" value="http://localhost:8000/orderProcessor/poisonSample"/>
  </appSettings>
  <system.serviceModel>
    <services>
      <service
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison"
                  binding="netMsmqBinding"
                  bindingConfiguration="PoisonBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
      </service>
    </services>

    <bindings>
      <netMsmqBinding>
        <binding name="PoisonBinding"
                 receiveRetryCount="0"
                 maxRetryCycles="1"
                 retryCycleDelay="00:00:05"
                 receiveErrorHandling="Move">
        </binding>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

## <a name="processing-messages-from-the-poison-message-queue"></a><span data-ttu-id="19d7d-151">Zehirli ileti kuyruğundaki iletileri işleme</span><span class="sxs-lookup"><span data-stu-id="19d7d-151">Processing messages from the poison message queue</span></span>
 <span data-ttu-id="19d7d-152">Zehirli ileti hizmeti son zehirli ileti kuyruğundaki iletileri okur ve işler.</span><span class="sxs-lookup"><span data-stu-id="19d7d-152">The poison message service reads messages from the final poison message queue and processes them.</span></span>

 <span data-ttu-id="19d7d-153">Zehirli ileti kuyruğundaki iletiler, iletiyi işleyen hizmete yönlendirilen ve zehirli ileti hizmeti bitiş noktasından farklı olabilecek iletilerdir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-153">Messages in the poison message queue are messages that are addressed to the service that is processing the message, which could be different from the poison message service endpoint.</span></span> <span data-ttu-id="19d7d-154">Bu nedenle, zehirli ileti hizmeti kuyruktaki iletileri okuduğunda, WCF kanal katmanı bitiş noktalarındaki uyumsuzluğu bulur ve iletiyi göndermez.</span><span class="sxs-lookup"><span data-stu-id="19d7d-154">Therefore, when the poison message service reads messages from the queue, the WCF channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="19d7d-155">Bu durumda, ileti sipariş işleme hizmetine yöneliktir, ancak zehirli ileti hizmeti tarafından alınır.</span><span class="sxs-lookup"><span data-stu-id="19d7d-155">In this case, the message is addressed to the order processing service but is being received by the poison message service.</span></span> <span data-ttu-id="19d7d-156">İleti farklı bir bitiş noktasına yönlendirilse bile iletiyi almaya `ServiceBehavior` devam etmek için, iletinin adreslendiği herhangi bir hizmet bitiş noktasıyla eşleşecek şekilde eşleşmek için filtre adreslerine bir eklememiz gerekir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-156">To continue to receive the message even if the message is addressed to a different endpoint, we must add a `ServiceBehavior` to filter addresses where the match criterion is to match any service endpoint the message is addressed to.</span></span> <span data-ttu-id="19d7d-157">Bu, zehirli ileti kuyruğundan okuduğunuz iletileri başarıyla işlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-157">This is required to successfully process messages that you read from the poison message queue.</span></span>

 <span data-ttu-id="19d7d-158">Zehirli ileti hizmeti uygulamasının kendisi hizmet uygulamasına çok benzer.</span><span class="sxs-lookup"><span data-stu-id="19d7d-158">The poison message service implementation itself is very similar to the service implementation.</span></span> <span data-ttu-id="19d7d-159">Sözleşmeyi uygular ve emirleri işler.</span><span class="sxs-lookup"><span data-stu-id="19d7d-159">It implements the contract and processes the orders.</span></span> <span data-ttu-id="19d7d-160">Kod örneği aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-160">The code example is as follows.</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
[ServiceBehavior(AddressFilterMode=AddressFilterMode.Any)]
public class OrderProcessorService : IOrderProcessor
{
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted...exiting app");
        Environment.Exit(1);
    }

    // Host the service within this EXE console application.
    public static void Main()
    {

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The poison message service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHostBase to shutdown the service.
        if(serviceHost.State != CommunicationState.Faulted)
        {
            serviceHost.Close();
        }
    }
```

 <span data-ttu-id="19d7d-161">Sipariş kuyruğundan iletileri okuyan sipariş işleme hizmetinin aksine, zehirli ileti hizmeti zehirli alt sıradaki iletileri okur.</span><span class="sxs-lookup"><span data-stu-id="19d7d-161">Unlike the order processing service that reads messages from the order queue, the poison message service reads messages from the poison subqueue.</span></span> <span data-ttu-id="19d7d-162">Zehir sırası ana sıranın bir alt sırasıdır, "zehir" olarak adlandırılır ve msmq tarafından otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="19d7d-162">The poison queue is a subqueue of the main queue, is named "poison" and is automatically generated by MSMQ.</span></span> <span data-ttu-id="19d7d-163">Erişmek için, aşağıdaki örnek yapılandırmada gösterildiği gibi, bu durumda -"zehir" ve ardından gelen ana sıra adını ";" ve alt sıra adını sağlayın.</span><span class="sxs-lookup"><span data-stu-id="19d7d-163">To access it, provide the main queue name followed by a ";" and the subqueue name, in this case -"poison", as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="19d7d-164">MSMQ v3.0 için örnekte, zehir sıraadı bir alt sıra değil, daha çok iletiyi taşıdığımız sıradır.</span><span class="sxs-lookup"><span data-stu-id="19d7d-164">In the sample for MSMQ v3.0, the poison queue name is not a sub-queue, rather the queue that we moved the message to.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison;poison"
                  binding="netMsmqBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" >
        </endpoint>
      </service>
    </services>

  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="19d7d-165">Örneği çalıştırdığınızda, istemci, hizmet ve zehirli ileti hizmeti etkinlikleri konsol pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-165">When you run the sample, the client, service, and poison message service activities are displayed in console windows.</span></span> <span data-ttu-id="19d7d-166">Hizmetin istemciden ileti aldığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19d7d-166">You can see the service receive messages from the client.</span></span> <span data-ttu-id="19d7d-167">Hizmetleri kapatmak için her konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="19d7d-167">Press ENTER in each console window to shut down the services.</span></span>

 <span data-ttu-id="19d7d-168">Hizmet çalışmaya, siparişleri işlemeye ve rasgele işleme sonlandırmaya başlar başlar.</span><span class="sxs-lookup"><span data-stu-id="19d7d-168">The service starts running, processing orders and at random starts to terminate processing.</span></span> <span data-ttu-id="19d7d-169">İleti siparişi işlettiğini gösteriyorsa, hizmetin bir iletiyi gerçekten sonlandırdığını görene kadar istemciyi başka bir ileti göndermek için yeniden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19d7d-169">If the message indicates it has processed the order, you can run the client again to send another message until you see the service has actually terminated a message.</span></span> <span data-ttu-id="19d7d-170">Yapılandırılan zehir ayarlarına bağlı olarak, ileti son zehir kuyruğuna taşımadan önce bir kez işlenmek üzere denendi.</span><span class="sxs-lookup"><span data-stu-id="19d7d-170">Based on the configured poison settings, the message is tried once for processing before moving it to the final poison queue.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 0f063b71-93e0-42a1-aa3b-bca6c7a89546
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Processing Purchase Order: 5ef9a4fa-5a30-4175-b455-2fb1396095fa
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Aborting transaction, cannot process purchase order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
```

 <span data-ttu-id="19d7d-171">Zehir kuyruğundan zehirli mesajı okumak için zehir mesajı servisini başlatın.</span><span class="sxs-lookup"><span data-stu-id="19d7d-171">Start up the poison message service to read the poisoned message from the poison queue.</span></span> <span data-ttu-id="19d7d-172">Bu örnekte, zehirli ileti hizmeti iletiyi okur ve işler.</span><span class="sxs-lookup"><span data-stu-id="19d7d-172">In this example, the poison message service reads the message and processes it.</span></span> <span data-ttu-id="19d7d-173">Sonlandırılan ve zehirlenen satın alma siparişinin zehirli mesaj servisi tarafından okunduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19d7d-173">You could see that the purchase order that was terminated and poisoned is read by the poison message service.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="19d7d-174">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="19d7d-174">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="19d7d-175">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="19d7d-175">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="19d7d-176">Önce hizmet çalıştırılırsa, sıranın mevcut olduğundan emin olmak için denetler.</span><span class="sxs-lookup"><span data-stu-id="19d7d-176">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="19d7d-177">Sıra yoksa, hizmet bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="19d7d-177">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="19d7d-178">Sırayı oluşturmak için önce hizmeti çalıştırabilir veya MSMQ Sıra Yöneticisi aracılığıyla bir hizmet oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19d7d-178">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="19d7d-179">Windows 2008'de bir sıra oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="19d7d-179">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="19d7d-180">Visual Studio 2012'de Sunucu Yöneticisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="19d7d-180">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="19d7d-181">**Özellikler** sekmesini genişletin.</span><span class="sxs-lookup"><span data-stu-id="19d7d-181">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="19d7d-182">Özel **İleti Kuyrukları'nı**sağ tıklatın ve **Yeni**, **Özel Sıra'yı**seçin.</span><span class="sxs-lookup"><span data-stu-id="19d7d-182">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="19d7d-183">**İşlem** kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="19d7d-183">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="19d7d-184">Yeni `ServiceModelSamplesTransacted` sıranın adı olarak girin.</span><span class="sxs-lookup"><span data-stu-id="19d7d-184">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="19d7d-185">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="19d7d-185">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="19d7d-186">Örneği tek veya çapraz bilgisayar yapılandırmasında çalıştırmak için, sıra adlarını localhost yerine gerçek ana bilgisayar adını yansıtacak şekilde değiştirin ve [Windows Communication Foundation Samples'i çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="19d7d-186">To run the sample in a single- or cross-computer configuration, change the queue names to reflect the actual hostname instead of localhost and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

 <span data-ttu-id="19d7d-187">`netMsmqBinding` Varsayılan olarak bağlama aktarımı ile güvenlik etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-187">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="19d7d-188">İki özellik `MsmqAuthenticationMode` `MsmqProtectionLevel`ve birlikte aktarım güvenlik türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="19d7d-188">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="19d7d-189">Varsayılan olarak, kimlik doğrulama modu `Windows` ayarlanır ve koruma `Sign`düzeyi .</span><span class="sxs-lookup"><span data-stu-id="19d7d-189">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="19d7d-190">MSMQ'nun kimlik doğrulama ve imzalama özelliğini sağlaması için, bir etki alanının parçası olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-190">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="19d7d-191">Bu örneği etki alanının parçası olmayan bir bilgisayarda çalıştırıyorsanız, aşağıdaki hatayı alırsınız: "Kullanıcının iç ileti sıraya alma sertifikası yok".</span><span class="sxs-lookup"><span data-stu-id="19d7d-191">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="19d7d-192">Bir çalışma grubuna katılan bir bilgisayarda örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="19d7d-192">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="19d7d-193">Bilgisayarınız bir etki alanının parçası değilse, kimlik doğrulama modunu ve koruma `None` düzeyini aşağıdaki örnek yapılandırmada gösterildiği gibi ayarlayarak aktarım güvenliğini kapatın:</span><span class="sxs-lookup"><span data-stu-id="19d7d-193">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="19d7d-194">Bitiş noktasının bağlamaYapılandırma özniteliğini ayarlayarak bitiş noktasının bağlamayla ilişkili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="19d7d-194">Ensure the endpoint is associated with the binding by setting the endpoint's bindingConfiguration attribute.</span></span>

2. <span data-ttu-id="19d7d-195">Örneği çalıştırmadan önce PoisonMessageServer, sunucu ve istemcideki yapılandırmayı değiştirdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="19d7d-195">Ensure that you change the configuration on the PoisonMessageServer, server, and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="19d7d-196">`None` Ayar, `security mode` ayarına `MsmqAuthenticationMode` `MsmqProtectionLevel`ve `Message` güvenlik `None`'e eşittir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-196">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel`, and `Message` security to `None`.</span></span>  
  
3. <span data-ttu-id="19d7d-197">Meta Veri Alışverişi'nin çalışması için http binding içeren bir URL kaydettiriyoruz.</span><span class="sxs-lookup"><span data-stu-id="19d7d-197">In order for Meta Data Exchange to work, we register a URL with http binding.</span></span> <span data-ttu-id="19d7d-198">Bu, hizmetin yükseltilmiş bir komut penceresinde çalışmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-198">This requires that the service run in an elevated command window.</span></span> <span data-ttu-id="19d7d-199">Aksi takdirde, gibi bir `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`özel durum olsun: .</span><span class="sxs-lookup"><span data-stu-id="19d7d-199">Otherwise, you get an exception such as: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="19d7d-200">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="19d7d-200">The samples may already be installed on your computer.</span></span> <span data-ttu-id="19d7d-201">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="19d7d-201">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="19d7d-202">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="19d7d-202">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="19d7d-203">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="19d7d-203">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
