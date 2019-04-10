---
title: MSMQ 4.0'da Zehirli İleti İşleme
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: b4711d344a6ce08adc6e993c19f2c3d97f56e7b4
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316472"
---
# <a name="poison-message-handling-in-msmq-40"></a><span data-ttu-id="ee6c8-102">MSMQ 4.0'da Zehirli İleti İşleme</span><span class="sxs-lookup"><span data-stu-id="ee6c8-102">Poison Message Handling in MSMQ 4.0</span></span>
<span data-ttu-id="ee6c8-103">Bu örnek, zehirli ileti bir hizmet olarak işleme gerçekleştirmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-103">This sample demonstrates how to perform poison message handling in a service.</span></span> <span data-ttu-id="ee6c8-104">Bu örnek dayanır [işlem temelli MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-104">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="ee6c8-105">Bu örnekte `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-105">This sample uses the `netMsmqBinding`.</span></span> <span data-ttu-id="ee6c8-106">Hizmeti, sıraya alınan iletileri alma hizmeti gözlemleyin sağlamak için bir şirket içinde barındırılan bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="ee6c8-107">Kuyruğa alınan iletişim kullanarak bir kuyruk hizmetine istemci iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="ee6c8-108">Daha kesin bir istemci bir kuyruğa iletiler gönderir.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="ee6c8-109">Hizmet iletileri kuyruktan alır.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-109">The service receives messages from the queue.</span></span> <span data-ttu-id="ee6c8-110">Hizmet ve istemci bu nedenle, bir kuyruk kullanarak iletişim kurmak için aynı anda çalıştırılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="ee6c8-111">Zehirli ileti, ileti okuma hizmeti iletiyi işlerken art arda bir kuyruktan okunur ve bu nedenle altında ileti okuma işlemi sonlandıran bir iletidir.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-111">A poison message is a message that is repeatedly read from a queue when the service reading the message cannot process the message and therefore terminates the transaction under which the message is read.</span></span> <span data-ttu-id="ee6c8-112">Bu gibi durumlarda, ileti yeniden denenir.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-112">In such cases, the message is retried again.</span></span> <span data-ttu-id="ee6c8-113">İletiyle ilgili bir sorun varsa bu teorik olarak süresiz geçebilir.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-113">This can theoretically go on forever if there is a problem with the message.</span></span> <span data-ttu-id="ee6c8-114">Kuyruktan okunmak ve hizmet işlemini çağırmak için işlemleri kullandığınızda yalnızca oluşabilir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-114">Note that this can only occur when you use transactions to read from the queue and invoke the service operation.</span></span>

 <span data-ttu-id="ee6c8-115">MSMQ sürümüne bağlı olarak, tam zehirli iletilerin algılanması için sınırlı algılama NetMsmqBinding destekler.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-115">Based on the version of MSMQ, the NetMsmqBinding supports limited detection to full detection of poison messages.</span></span> <span data-ttu-id="ee6c8-116">Ardından iletiyi zarar olarak algılandı sonra birkaç şekilde işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-116">After the message has been detected as poisoned, then it can be handled in several ways.</span></span> <span data-ttu-id="ee6c8-117">Yeniden MSMQ sürümüne bağlı olarak, NetMsmqBinding zehirli iletilerin tam işleme için sınırlı işlemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-117">Again, based on the version of MSMQ, the NetMsmqBinding supports limited handling to full handling of poison messages.</span></span>

 <span data-ttu-id="ee6c8-118">Bu örnek sağlanan sınırlı zehirli özelliklerini göstermektedir [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platform ve sağlanan tam zehirli tesis [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ee6c8-118">This sample illustrates the limited poison facilities provided on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platform and the full poison facilities provided on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="ee6c8-119">Her iki örneklerinde hedefi olan zehirli ileti dışarı Taşı sırasına ardından zehirli ileti hizmeti tarafından hizmet başka bir kuyruk için.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-119">In both samples, the objective is move the poison message out of the queue to another queue which then can be serviced by a poison message service.</span></span>

## <a name="msmq-v40-poison-handling-sample"></a><span data-ttu-id="ee6c8-120">MSMQ v4.0 Poison örnek işleme</span><span class="sxs-lookup"><span data-stu-id="ee6c8-120">MSMQ v4.0 Poison Handling Sample</span></span>
 <span data-ttu-id="ee6c8-121">İçinde [!INCLUDE[wv](../../../../includes/wv-md.md)], MSMQ zehirli iletileri depolamak için kullanılan bir zehirli alt kuyruk olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-121">In [!INCLUDE[wv](../../../../includes/wv-md.md)], MSMQ provides a poison sub-queue facility that can be used to store poison messages.</span></span> <span data-ttu-id="ee6c8-122">Bu örnek, en iyi zehirli iletileri kullanarak uğraşmanızı gösterir [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ee6c8-122">This sample demonstrates the best practice of dealing with poison messages using [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

 <span data-ttu-id="ee6c8-123">Zehirli ileti algılama [!INCLUDE[wv](../../../../includes/wv-md.md)] oldukça karmaşık olduğundan.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-123">The poison message detection in [!INCLUDE[wv](../../../../includes/wv-md.md)] is quite sophisticated.</span></span> <span data-ttu-id="ee6c8-124">Yardımcı algılama 3 özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-124">There are 3 properties that help with detection.</span></span> <span data-ttu-id="ee6c8-125"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Sayıda belirli bir ileti kuyruktan yeniden okuma ve işleme uygulamaya gönderilen.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-125">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is number of times a given message is re-read from the queue and dispatched to the application for processing.</span></span> <span data-ttu-id="ee6c8-126">Bunu yeniden kuyruğa ileti uygulamaya dağıtılamaz veya uygulama hizmeti işleminin geri işlem yapar çünkü alınan olduğunda yeniden bir ileti kuyruktan okunur.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-126">A message is re-read from the queue when it is put back into the queue because the message cannot be dispatched to the application or the application rolls back the transaction in the service operation.</span></span> <xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> <span data-ttu-id="ee6c8-127">yeniden deneme kuyruğa ileti taşınır sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-127">is the number of times the message is moved to the retry queue.</span></span> <span data-ttu-id="ee6c8-128">Zaman <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> olan üst sınıra ulaşıldı, yeniden deneme kuyruğa ileti taşınır.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-128">When <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reached, the message is moved to the retry queue.</span></span> <span data-ttu-id="ee6c8-129">Özellik <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> sonra iletiyi taşındıysa yeniden deneme kuyruktan geri ana kuyruğa zaman gecikmesi.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-129">The property <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> is the time delay after which the message is moved from the retry queue back to the main queue.</span></span> <span data-ttu-id="ee6c8-130"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> 0 değerine sıfırlanır.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-130">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reset to 0.</span></span> <span data-ttu-id="ee6c8-131">İleti yeniden denenir.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-131">The message is tried again.</span></span> <span data-ttu-id="ee6c8-132">İleti okumak için tüm denemeler başarısız olursa, ileti zarar olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-132">If all attempts to read the message have failed, then the message is marked as poisoned.</span></span>

 <span data-ttu-id="ee6c8-133">İleti zarar olarak işaretlendikten sonra ileti ile ayarlarına göre dağıtılır <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-133">Once the message is marked as poisoned, the message is dealt with according to the settings in the <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeration.</span></span> <span data-ttu-id="ee6c8-134">Olası değerler yinelemek için:</span><span class="sxs-lookup"><span data-stu-id="ee6c8-134">To reiterate the possible values:</span></span>

-   <span data-ttu-id="ee6c8-135">Hata (varsayılan): Hata dinleyicisi ve ayrıca hizmet ana bilgisayarı için.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-135">Fault (default): To fault the listener and also the service host.</span></span>

-   <span data-ttu-id="ee6c8-136">Açılır: İleti bırakmak.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-136">Drop: To drop the message.</span></span>

-   <span data-ttu-id="ee6c8-137">Taşı: Zehirli ileti alt kuyruğa ileti taşımak için.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-137">Move: To move the message to the poison message sub-queue.</span></span> <span data-ttu-id="ee6c8-138">Bu değer yalnızca kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ee6c8-138">This value is available only on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

-   <span data-ttu-id="ee6c8-139">Reddetme: İletiyi gönderenin eski ileti sırası geri gönderme, ileti reddetmek için.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-139">Reject: To reject the message, sending the message back to the sender's dead-letter queue.</span></span> <span data-ttu-id="ee6c8-140">Bu değer yalnızca kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ee6c8-140">This value is available only on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

 <span data-ttu-id="ee6c8-141">Örnek kullanmayı gösterir `Move` zehirli ileti için değerlendirme.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-141">The sample demonstrates using the `Move` disposition for the poison message.</span></span> `Move` <span data-ttu-id="ee6c8-142">zehirli alt kuyruğuna Taşı iletiyi neden olur.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-142">causes the message to move to the poison sub-queue.</span></span>

 <span data-ttu-id="ee6c8-143">Hizmet sözleşme `IOrderProcessor`, kuyruklar ile kullanım için uygun olan bir tek yönlü hizmeti tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-143">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="ee6c8-144">Hizmet işlemi, sipariş işleme bildiren bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-144">The service operation displays a message stating it is processing the order.</span></span> <span data-ttu-id="ee6c8-145">Zehirli ileti işlevselliğini göstermek için `SubmitPurchaseOrder` hizmet işlemi hizmeti rastgele bir çağrıda işlem geri alınacak bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-145">To demonstrate the poison message functionality, the `SubmitPurchaseOrder` service operation throws an exception to rollback the transaction on a random invocation of the service.</span></span> <span data-ttu-id="ee6c8-146">Bu iletinin geri sıraya koymak neden olur.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-146">This causes the message to be put back in the queue.</span></span> <span data-ttu-id="ee6c8-147">Sonuçta ileti zarar işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-147">Eventually the message is marked as poison.</span></span> <span data-ttu-id="ee6c8-148">Yapılandırma, zehirli ileti zehirli alt kuyruğuna Taşı şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-148">The configuration is set to move the poison message to the poison sub-queue.</span></span>

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

 <span data-ttu-id="ee6c8-149">Hizmet yapılandırması aşağıdaki zehirli ileti özellikleri içerir: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, ve `receiveErrorHandling` aşağıdaki yapılandırma dosyasında gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-149">The service configuration includes the following poison message properties: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, and `receiveErrorHandling` as shown in the following configuration file.</span></span>

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

## <a name="processing-messages-from-the-poison-message-queue"></a><span data-ttu-id="ee6c8-150">Zehirli ileti kuyruktan iletileri işleme</span><span class="sxs-lookup"><span data-stu-id="ee6c8-150">Processing messages from the poison message queue</span></span>
 <span data-ttu-id="ee6c8-151">Zehirli ileti hizmet son zehirli ileti kuyruktan iletileri okuyan ve işler.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-151">The poison message service reads messages from the final poison message queue and processes them.</span></span>

 <span data-ttu-id="ee6c8-152">Zehirli ileti kuyruğu iletilerinde zehirli ileti hizmet uç noktasından farklı iletisi işliyor hizmete gönderilen iletileri ' dir.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-152">Messages in the poison message queue are messages that are addressed to the service that is processing the message, which could be different from the poison message service endpoint.</span></span> <span data-ttu-id="ee6c8-153">Bu nedenle, zehirli ileti hizmet iletileri kuyruktan okuyan, WCF kanal katmanını uyuşmazlığı uç noktaların bulur ve bu iletiyi göndermez.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-153">Therefore, when the poison message service reads messages from the queue, the WCF channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="ee6c8-154">Bu durumda, ileti işleme hizmeti siparişin ele ancak zehirli ileti hizmet tarafından alınan.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-154">In this case, the message is addressed to the order processing service but is being received by the poison message service.</span></span> <span data-ttu-id="ee6c8-155">İleti farklı bir uç noktaya yönelik bile iletiyi almaya devam etmek biz eklemelisiniz bir `ServiceBehavior` filtre adreslerine eşleştirme ölçütü olduğu ileti ele alınan herhangi bir hizmet uç noktası eşleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-155">To continue to receive the message even if the message is addressed to a different endpoint, we must add a `ServiceBehavior` to filter addresses where the match criterion is to match any service endpoint the message is addressed to.</span></span> <span data-ttu-id="ee6c8-156">Bu, başarılı bir şekilde zehirli ileti kuyruktan okunmak iletilerini işlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-156">This is required to successfully process messages that you read from the poison message queue.</span></span>

 <span data-ttu-id="ee6c8-157">Zehirli ileti hizmet uygulaması kendi hizmet uygulaması için çok benzer.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-157">The poison message service implementation itself is very similar to the service implementation.</span></span> <span data-ttu-id="ee6c8-158">Bu sözleşme uygular ve siparişleri işler.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-158">It implements the contract and processes the orders.</span></span> <span data-ttu-id="ee6c8-159">Kod örneği aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-159">The code example is as follows.</span></span>

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

 <span data-ttu-id="ee6c8-160">Sipariş işleme sırası kuyruktan iletileri okuyan hizmet, zehirli ileti hizmeti zehirli alt kuyruktan iletileri okur.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-160">Unlike the order processing service that reads messages from the order queue, the poison message service reads messages from the poison sub-queue.</span></span> <span data-ttu-id="ee6c8-161">Zehirli sıranın "poison" adlı bir alt kuyruk ana sıranın ve MSMQ tarafından otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-161">The poison queue is a sub-queue of the main queue, is named "poison" and is automatically generated by MSMQ.</span></span> <span data-ttu-id="ee6c8-162">Erişmek için ana kuyruk adından sağlayan bir ";" ve alt kuyruk adı, bu durumda-"Aşağıdaki örnek yapılandırmada gösterildiği zehirli".</span><span class="sxs-lookup"><span data-stu-id="ee6c8-162">To access it, provide the main queue name followed by a ";" and the sub-queue name, in this case -"poison", as shown in the following sample configuration.</span></span>

> [!NOTE]
>  <span data-ttu-id="ee6c8-163">MSMQ v3.0 örnek zehirli kuyruk adı yerine iletiye geçtiğimizi kuyruk bir alt kuyruk değil.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-163">In the sample for MSMQ v3.0, the poison queue name is not a sub-queue, rather the queue that we moved the message to.</span></span>

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

 <span data-ttu-id="ee6c8-164">Örneği çalıştırdığınızda, konsol pencerelerinde istemci, hizmet ve zehirli ileti hizmet etkinlikleri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-164">When you run the sample, the client, service, and poison message service activities are displayed in console windows.</span></span> <span data-ttu-id="ee6c8-165">İstemciden hizmet alma iletileri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-165">You can see the service receive messages from the client.</span></span> <span data-ttu-id="ee6c8-166">Her konsol penceresi Hizmetleri kapatılmaya için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-166">Press ENTER in each console window to shut down the services.</span></span>

 <span data-ttu-id="ee6c8-167">Hizmet çalışıyor, sipariş işleme başlar ve işlemesini sonlandırmak rastgele başlatır.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-167">The service starts running, processing orders and at random starts to terminate processing.</span></span> <span data-ttu-id="ee6c8-168">İleti sırası işlediği gösteriyorsa, istemci hizmeti aslında bir ileti sonlandırıldı görene kadar başka bir iletiyi göndermeyi yeniden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-168">If the message indicates it has processed the order, you can run the client again to send another message until you see the service has actually terminated a message.</span></span> <span data-ttu-id="ee6c8-169">Yapılandırılmış zehirli ayarlarına bağlı olarak, ileti son zehirli kuyruğa geçmeden önce işleme için bir kez denenir.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-169">Based on the configured poison settings, the message is tried once for processing before moving it to the final poison queue.</span></span>

```
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

 <span data-ttu-id="ee6c8-170">Zehirli kuyruktan zehirlenmiş iletiyi okumak için zehirli ileti hizmet başlatın.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-170">Start up the poison message service to read the poisoned message from the poison queue.</span></span> <span data-ttu-id="ee6c8-171">Bu örnekte, zehirli ileti hizmeti iletiyi okur ve işler.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-171">In this example, the poison message service reads the message and processes it.</span></span> <span data-ttu-id="ee6c8-172">Sonlandırılacak ve zarar satınalma siparişi zehirli ileti hizmet tarafından okunur görebilir.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-172">You could see that the purchase order that was terminated and poisoned is read by the poison message service.</span></span>

```
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

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ee6c8-173">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ee6c8-173">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="ee6c8-174">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee6c8-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="ee6c8-175">Hizmet ilk olarak çalıştırılırsa, sıranın mevcut olduğundan emin olun kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-175">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="ee6c8-176">Kuyruk yoksa, bir hizmeti oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-176">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="ee6c8-177">İlk sırayı oluşturmak için hizmet çalıştırabileceğiniz veya bir MSMQ Kuyruk Yöneticisi ile oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-177">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="ee6c8-178">Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-178">Follow these steps to create a queue in Windows 2008.</span></span>

    1.  <span data-ttu-id="ee6c8-179">Visual Studio 2012'de Sunucu Yöneticisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-179">Open Server Manager in Visual Studio 2012.</span></span>

    2.  <span data-ttu-id="ee6c8-180">Genişletin **özellikleri** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-180">Expand the **Features** tab.</span></span>

    3.  <span data-ttu-id="ee6c8-181">Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-181">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4.  <span data-ttu-id="ee6c8-182">Denetleme **işlem** kutusu.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-182">Check the **Transactional** box.</span></span>

    5.  <span data-ttu-id="ee6c8-183">Girin `ServiceModelSamplesTransacted` yeni Kuyruğun adı.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-183">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="ee6c8-184">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee6c8-184">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="ee6c8-185">Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin ve localhost yerine sunucunun gerçek ana bilgisayar'ı yansıtmak için kuyruk adları değiştirme [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee6c8-185">To run the sample in a single- or cross-computer configuration, change the queue names to reflect the actual hostname instead of localhost and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

 <span data-ttu-id="ee6c8-186">Varsayılan olarak `netMsmqBinding` bağlama taşıma, güvenlik etkin.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-186">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="ee6c8-187">İki özellik `MsmqAuthenticationMode` ve `MsmqProtectionLevel`, birlikte aktarım güvenliği türünü belirleyin.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-187">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="ee6c8-188">Varsayılan olarak, kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-188">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="ee6c8-189">Kimlik doğrulama ve imzalama özelliği sağlamak MSMQ için bir etki alanının parçası olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-189">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="ee6c8-190">Bir etki alanının parçası olmayan bir bilgisayarda bu örneği çalıştırmak, şu hatayı alırsınız: "Kullanıcının iç message queuing sertifikası yok".</span><span class="sxs-lookup"><span data-stu-id="ee6c8-190">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="ee6c8-191">Örneği için bir çalışma alanına katılmış bir bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ee6c8-191">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="ee6c8-192">Bilgisayarınız bir etki alanının parçası değilse, kimlik doğrulama modu ve koruma düzeyi ayarlayarak aktarım güvenliği devre dışı kapatma `None` aşağıdaki örnek yapılandırmada gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="ee6c8-192">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="ee6c8-193">Uç noktanın bindingConfiguration özniteliğini ayarlayarak uç nokta bağlama ile ilişkili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-193">Ensure the endpoint is associated with the binding by setting the endpoint's bindingConfiguration attribute.</span></span>

2. <span data-ttu-id="ee6c8-194">Örneği çalıştırmadan önce PoisonMessageServer, sunucu ve istemci üzerindeki yapılandırmayı değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-194">Ensure that you change the configuration on the PoisonMessageServer, server and the client before you run the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="ee6c8-195">Ayarı `security mode` için `None` ayarlamakla eşdeğerdir `MsmqAuthenticationMode`, `MsmqProtectionLevel`, ve `Message` güvenlik `None`.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-195">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel`, and `Message` security to `None`.</span></span>  
  
3. <span data-ttu-id="ee6c8-196">Sırayla çalışması Meta veri değişimi için size bir URL http bağlaması ile kaydedin.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-196">In order for Meta Data Exchange to work, we register a URL with http binding.</span></span> <span data-ttu-id="ee6c8-197">Bu, hizmetin bir yükseltilmiş komut istemi penceresine çalıştırmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-197">This requires that the service run in an elevated command window.</span></span> <span data-ttu-id="ee6c8-198">Aksi takdirde, bir özel durum gibi alın: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-198">Otherwise, you get an exception such as: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ee6c8-199">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ee6c8-200">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ee6c8-201">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ee6c8-202">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ee6c8-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`