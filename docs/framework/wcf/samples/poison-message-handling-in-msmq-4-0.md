---
title: MSMQ 4.0'da Zehirli İleti İşleme
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: d0ddab7832e308336d5bfb1c5f75fd13fe63fe72
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="poison-message-handling-in-msmq-40"></a><span data-ttu-id="cba49-102">MSMQ 4.0'da Zehirli İleti İşleme</span><span class="sxs-lookup"><span data-stu-id="cba49-102">Poison Message Handling in MSMQ 4.0</span></span>
<span data-ttu-id="cba49-103">Bu örnek, bir hizmet olarak işleme zehir iletisi gerçekleştirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cba49-103">This sample demonstrates how to perform poison message handling in a service.</span></span> <span data-ttu-id="cba49-104">Bu örnek dayanır [işlem yapılan işlem MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="cba49-104">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="cba49-105">Bu örnekte `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="cba49-105">This sample uses the `netMsmqBinding`.</span></span> <span data-ttu-id="cba49-106">Hizmeti, sıraya alınan iletileri alma hizmeti izlemek etkinleştirmek için bir kendi kendini barındıran konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="cba49-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
 <span data-ttu-id="cba49-107">Kuyruğa alınan iletişim, istemci bir sıra kullanarak hizmeti ile iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="cba49-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="cba49-108">Daha hassas bir şekilde istemci kuyruğa ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="cba49-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="cba49-109">Hizmet kuyruktan iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="cba49-109">The service receives messages from the queue.</span></span> <span data-ttu-id="cba49-110">Hizmet ve istemci bu nedenle, bir sıra kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="cba49-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="cba49-111">Zararlı bir ileti, ileti okunurken hizmeti iletiyi işleyemediğinde kuyruktan art arda okunur ve bu nedenle altında ileti okuma işlemi sonlandırır bir iletidir.</span><span class="sxs-lookup"><span data-stu-id="cba49-111">A poison message is a message that is repeatedly read from a queue when the service reading the message cannot process the message and therefore terminates the transaction under which the message is read.</span></span> <span data-ttu-id="cba49-112">Böyle durumlarda, ileti yeniden denenir.</span><span class="sxs-lookup"><span data-stu-id="cba49-112">In such cases, the message is retried again.</span></span> <span data-ttu-id="cba49-113">İleti ile ilgili bir sorun varsa bu teorik olarak sonsuza kadar geçebilir.</span><span class="sxs-lookup"><span data-stu-id="cba49-113">This can theoretically go on forever if there is a problem with the message.</span></span> <span data-ttu-id="cba49-114">Sıradan Okuma ve hizmet işlemini çağırmak için işlemleri kullandığınızda yalnızca oluşabilir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cba49-114">Note that this can only occur when you use transactions to read from the queue and invoke the service operation.</span></span>  
  
 <span data-ttu-id="cba49-115">MSMQ sürümlerine göre NetMsmqBinding zarar iletileri tam algılanması için sınırlı algılama destekler.</span><span class="sxs-lookup"><span data-stu-id="cba49-115">Based on the version of MSMQ, the NetMsmqBinding supports limited detection to full detection of poison messages.</span></span> <span data-ttu-id="cba49-116">Ardından ileti zarar gibi algılandı sonra çeşitli yollarla işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="cba49-116">After the message has been detected as poisoned, then it can be handled in several ways.</span></span> <span data-ttu-id="cba49-117">Yeniden MSMQ sürümlerine göre NetMsmqBinding zarar iletileri tam işlenmesi için sınırlı işleme destekler.</span><span class="sxs-lookup"><span data-stu-id="cba49-117">Again, based on the version of MSMQ, the NetMsmqBinding supports limited handling to full handling of poison messages.</span></span>  
  
 <span data-ttu-id="cba49-118">Bu örnek sağlanan sınırlı zararlı tesislerde gösterilmektedir [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platform ve sağlanan tam zararlı tesis [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cba49-118">This sample illustrates the limited poison facilities provided on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wxp](../../../../includes/wxp-md.md)] platform and the full poison facilities provided on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="cba49-119">Her iki örneklerinde hedefi olan zehir iletisi dışarı Taşı kuyruğunu sonra zehir iletisi hizmeti tarafından hizmet başka bir kuyruğa.</span><span class="sxs-lookup"><span data-stu-id="cba49-119">In both samples, the objective is move the poison message out of the queue to another queue which then can be serviced by a poison message service.</span></span>  
  
## <a name="msmq-v40-poison-handling-sample"></a><span data-ttu-id="cba49-120">MSMQ v4.0 Poison örnek işleme</span><span class="sxs-lookup"><span data-stu-id="cba49-120">MSMQ v4.0 Poison Handling Sample</span></span>  
 <span data-ttu-id="cba49-121">İçinde [!INCLUDE[wv](../../../../includes/wv-md.md)], MSMQ zarar iletileri depolamak için kullanılan bir zarar alt sıra olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cba49-121">In [!INCLUDE[wv](../../../../includes/wv-md.md)], MSMQ provides a poison sub-queue facility that can be used to store poison messages.</span></span> <span data-ttu-id="cba49-122">Bu örneği kullanarak zarar iletileri postalarla en iyi uygulama gösterir [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cba49-122">This sample demonstrates the best practice of dealing with poison messages using [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>  
  
 <span data-ttu-id="cba49-123">Zehir iletisi algılama [!INCLUDE[wv](../../../../includes/wv-md.md)] oldukça karmaşık değil.</span><span class="sxs-lookup"><span data-stu-id="cba49-123">The poison message detection in [!INCLUDE[wv](../../../../includes/wv-md.md)] is quite sophisticated.</span></span> <span data-ttu-id="cba49-124">Algılama Yardım 3 özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="cba49-124">There are 3 properties that help with detection.</span></span> <span data-ttu-id="cba49-125"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> Sayıda belirli bir ileti kuyruktan yeniden okuma ve işleme için uygulama gönderilen.</span><span class="sxs-lookup"><span data-stu-id="cba49-125">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is number of times a given message is re-read from the queue and dispatched to the application for processing.</span></span> <span data-ttu-id="cba49-126">Bu geri sıraya ileti uygulamaya gönderilen olamaz veya uygulama işlem hizmet işlemini geri alır. geçirdiğinizde bir ileti kuyruktan yeniden okunur.</span><span class="sxs-lookup"><span data-stu-id="cba49-126">A message is re-read from the queue when it is put back into the queue because the message cannot be dispatched to the application or the application rolls back the transaction in the service operation.</span></span> <span data-ttu-id="cba49-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> yeniden deneme kuyruğuna ileti taşınır sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="cba49-127"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> is the number of times the message is moved to the retry queue.</span></span> <span data-ttu-id="cba49-128">Zaman <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> olan ulaşıldı, yeniden kuyruğa ileti taşınır.</span><span class="sxs-lookup"><span data-stu-id="cba49-128">When <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reached, the message is moved to the retry queue.</span></span> <span data-ttu-id="cba49-129">Özellik <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> geçmesi ileti taşınırken yeniden deneme sıradan geri ana sıranın zaman gecikmesi.</span><span class="sxs-lookup"><span data-stu-id="cba49-129">The property <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> is the time delay after which the message is moved from the retry queue back to the main queue.</span></span> <span data-ttu-id="cba49-130"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> 0 değerine sıfırlanır.</span><span class="sxs-lookup"><span data-stu-id="cba49-130">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reset to 0.</span></span> <span data-ttu-id="cba49-131">İleti yeniden denenir.</span><span class="sxs-lookup"><span data-stu-id="cba49-131">The message is tried again.</span></span> <span data-ttu-id="cba49-132">İleti okumak için tüm denemeleri başarısız, ileti zarar olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="cba49-132">If all attempts to read the message have failed, then the message is marked as poisoned.</span></span>  
  
 <span data-ttu-id="cba49-133">İleti zarar olarak işaretlendikten sonra ileti ile ayarlara göre dağıtılır <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="cba49-133">Once the message is marked as poisoned, the message is dealt with according to the settings in the <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeration.</span></span> <span data-ttu-id="cba49-134">Olası değerler yinelemek için:</span><span class="sxs-lookup"><span data-stu-id="cba49-134">To reiterate the possible values:</span></span>  
  
-   <span data-ttu-id="cba49-135">Hata (varsayılan): dinleyici ve ayrıca hizmet konağı alınmasını.</span><span class="sxs-lookup"><span data-stu-id="cba49-135">Fault (default): To fault the listener and also the service host.</span></span>  
  
-   <span data-ttu-id="cba49-136">Açılan: ileti bırakılamadı.</span><span class="sxs-lookup"><span data-stu-id="cba49-136">Drop: To drop the message.</span></span>  
  
-   <span data-ttu-id="cba49-137">Taşıma: ileti zehir iletisi alt sıraya taşınamadı.</span><span class="sxs-lookup"><span data-stu-id="cba49-137">Move: To move the message to the poison message sub-queue.</span></span> <span data-ttu-id="cba49-138">Bu değer yalnızca kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cba49-138">This value is available only on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>  
  
-   <span data-ttu-id="cba49-139">Reddetme: ileti reddetmek için gönderene ileti gönderme sahipsiz sıra.</span><span class="sxs-lookup"><span data-stu-id="cba49-139">Reject: To reject the message, sending the message back to the sender's dead-letter queue.</span></span> <span data-ttu-id="cba49-140">Bu değer yalnızca kullanılabilir [!INCLUDE[wv](../../../../includes/wv-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cba49-140">This value is available only on [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>  
  
 <span data-ttu-id="cba49-141">Örnek kullanarak gösterir `Move` zehir iletisi için eğilimi.</span><span class="sxs-lookup"><span data-stu-id="cba49-141">The sample demonstrates using the `Move` disposition for the poison message.</span></span> <span data-ttu-id="cba49-142">`Move` İletinin zararlı alt kuyruğuna Taşı neden olur.</span><span class="sxs-lookup"><span data-stu-id="cba49-142">`Move` causes the message to move to the poison sub-queue.</span></span>  
  
 <span data-ttu-id="cba49-143">Hizmet sözleşme `IOrderProcessor`, kuyruklar ile kullanım için uygun bir tek yönlü hizmet tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cba49-143">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```

 <span data-ttu-id="cba49-144">Hizmet işlemi, sipariş işleme bildiren bir ileti görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cba49-144">The service operation displays a message stating it is processing the order.</span></span> <span data-ttu-id="cba49-145">Zehir iletisi işlevselliğini göstermek için `SubmitPurchaseOrder` hizmet işlemi rastgele çağrılması hizmeti ile ilgili işlem geri almak için bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cba49-145">To demonstrate the poison message functionality, the `SubmitPurchaseOrder` service operation throws an exception to rollback the transaction on a random invocation of the service.</span></span> <span data-ttu-id="cba49-146">Bu iletinin kuyrukta geri yerleştirilecek neden olur.</span><span class="sxs-lookup"><span data-stu-id="cba49-146">This causes the message to be put back in the queue.</span></span> <span data-ttu-id="cba49-147">Sonunda iletisi poison işaretlenmiş.</span><span class="sxs-lookup"><span data-stu-id="cba49-147">Eventually the message is marked as poison.</span></span> <span data-ttu-id="cba49-148">Zehir iletisi zarar alt kuyruğuna taşımak için yapılandırmasını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cba49-148">The configuration is set to move the poison message to the poison sub-queue.</span></span>  

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

 <span data-ttu-id="cba49-149">Hizmet yapılandırması aşağıdaki zehirli ileti özellikleri içerir: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, ve `receiveErrorHandling` aşağıdaki yapılandırma dosyasında gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="cba49-149">The service configuration includes the following poison message properties: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, and `receiveErrorHandling` as shown in the following configuration file.</span></span>  
  
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
  
## <a name="processing-messages-from-the-poison-message-queue"></a><span data-ttu-id="cba49-150">Zehirli ileti kuyruktan iletileri işleme</span><span class="sxs-lookup"><span data-stu-id="cba49-150">Processing messages from the poison message queue</span></span>  
 <span data-ttu-id="cba49-151">Zehirli ileti hizmeti son zehirli ileti kuyruktan iletileri okur ve onları işler.</span><span class="sxs-lookup"><span data-stu-id="cba49-151">The poison message service reads messages from the final poison message queue and processes them.</span></span>  
  
 <span data-ttu-id="cba49-152">Zehirli ileti sıradaki iletiler zehir iletisi hizmet uç noktasından farklı olabilir iletisi işliyor hizmetine gönderilen iletiler ' dir.</span><span class="sxs-lookup"><span data-stu-id="cba49-152">Messages in the poison message queue are messages that are addressed to the service that is processing the message, which could be different from the poison message service endpoint.</span></span> <span data-ttu-id="cba49-153">Bu nedenle, zehirli ileti hizmeti kuyruktan iletileri okuduğunda WCF kanalı katman uyuşmazlığı uç noktalarını bulur ve ileti göndermez.</span><span class="sxs-lookup"><span data-stu-id="cba49-153">Therefore, when the poison message service reads messages from the queue, the WCF channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="cba49-154">Bu durumda, ileti hizmeti işlem sırasını ele ancak zehir iletisi hizmeti tarafından alınan.</span><span class="sxs-lookup"><span data-stu-id="cba49-154">In this case, the message is addressed to the order processing service but is being received by the poison message service.</span></span> <span data-ttu-id="cba49-155">İleti için farklı bir uç noktası ele olsa bile iletisini almaya devam etmek için biz eklemelisiniz bir `ServiceBehavior` eşleştirme ölçütü olduğu için ileti ele herhangi bir hizmet uç nokta eşleşecek şekilde filtre adreslere.</span><span class="sxs-lookup"><span data-stu-id="cba49-155">To continue to receive the message even if the message is addressed to a different endpoint, we must add a `ServiceBehavior` to filter addresses where the match criterion is to match any service endpoint the message is addressed to.</span></span> <span data-ttu-id="cba49-156">Bu, başarılı bir şekilde zehirli ileti kuyruğundan okumak iletileri işlemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cba49-156">This is required to successfully process messages that you read from the poison message queue.</span></span>  
  
 <span data-ttu-id="cba49-157">Zehir iletisi hizmet uygulaması kendi hizmet uygulaması çok benzer.</span><span class="sxs-lookup"><span data-stu-id="cba49-157">The poison message service implementation itself is very similar to the service implementation.</span></span> <span data-ttu-id="cba49-158">Sözleşme uygular ve siparişleri işler.</span><span class="sxs-lookup"><span data-stu-id="cba49-158">It implements the contract and processes the orders.</span></span> <span data-ttu-id="cba49-159">Kod örneği aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="cba49-159">The code example is as follows.</span></span>  

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

 <span data-ttu-id="cba49-160">Sipariş kuyruktan iletileri okur hizmeti işlem sırasını zehir iletisi hizmeti zararlı alt kuyruktan iletileri okur.</span><span class="sxs-lookup"><span data-stu-id="cba49-160">Unlike the order processing service that reads messages from the order queue, the poison message service reads messages from the poison sub-queue.</span></span> <span data-ttu-id="cba49-161">Zararlı sıranın ana sıranın alt bir sıra, "poison" olarak adlandırılır ve MSMQ tarafından otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cba49-161">The poison queue is a sub-queue of the main queue, is named "poison" and is automatically generated by MSMQ.</span></span> <span data-ttu-id="cba49-162">Erişmek için ana sıranın adından sağlayan bir ";" ve alt sıra adı, bu durumda-"Aşağıdaki örnek yapılandırmada gösterildiği gibi zararlı".</span><span class="sxs-lookup"><span data-stu-id="cba49-162">To access it, provide the main queue name followed by a ";" and the sub-queue name, in this case -"poison", as shown in the following sample configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cba49-163">MSMQ v3.0 örnek zararlı sıra adı yerine biz iletiye taşınmış sıranın alt bir sıra değil.</span><span class="sxs-lookup"><span data-stu-id="cba49-163">In the sample for MSMQ v3.0, the poison queue name is not a sub-queue, rather the queue that we moved the message to.</span></span>  
  
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
  
 <span data-ttu-id="cba49-164">Örneği çalıştırdığınızda, istemci, hizmet ve zehir iletisi hizmet etkinlikleri konsol pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cba49-164">When you run the sample, the client, service, and poison message service activities are displayed in console windows.</span></span> <span data-ttu-id="cba49-165">İstemci hizmeti alma iletileri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cba49-165">You can see the service receive messages from the client.</span></span> <span data-ttu-id="cba49-166">Her konsol penceresinde Hizmetleri'ni kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="cba49-166">Press ENTER in each console window to shut down the services.</span></span>  
  
 <span data-ttu-id="cba49-167">Hizmeti çalıştıran, sipariş işleme başlatır ve işlem sonlandırmak rastgele başlatır.</span><span class="sxs-lookup"><span data-stu-id="cba49-167">The service starts running, processing orders and at random starts to terminate processing.</span></span> <span data-ttu-id="cba49-168">İleti sırası işlediğinden gösteriyorsa, istemci hizmeti aslında bir ileti sonlandırıldı görene kadar başka bir iletiyi göndermeyi yeniden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cba49-168">If the message indicates it has processed the order, you can run the client again to send another message until you see the service has actually terminated a message.</span></span> <span data-ttu-id="cba49-169">Yapılandırılmış zararlı ayarlarına bağlı olarak, ileti, son zararlı kuyruğuna geçmeden önce işleme için bir kez denenir.</span><span class="sxs-lookup"><span data-stu-id="cba49-169">Based on the configured poison settings, the message is tried once for processing before moving it to the final poison queue.</span></span>  
  
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
  
 <span data-ttu-id="cba49-170">Zarar görmüş ileti zararlı kuyruktan okunmak üzere zehir iletisi hizmeti başlatın.</span><span class="sxs-lookup"><span data-stu-id="cba49-170">Start up the poison message service to read the poisoned message from the poison queue.</span></span> <span data-ttu-id="cba49-171">Bu örnekte, zehirli ileti hizmeti iletiyi okur ve işler.</span><span class="sxs-lookup"><span data-stu-id="cba49-171">In this example, the poison message service reads the message and processes it.</span></span> <span data-ttu-id="cba49-172">Sonlandırılacak ve zarar satın alma siparişi zehir iletisi hizmeti tarafından okunur görebilir.</span><span class="sxs-lookup"><span data-stu-id="cba49-172">You could see that the purchase order that was terminated and poisoned is read by the poison message service.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cba49-173">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="cba49-173">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="cba49-174">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cba49-174">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="cba49-175">Hizmetin ilk olarak çalışıyorsa, sıranın var olduğundan emin olmak için kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="cba49-175">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="cba49-176">Hizmet sırası mevcut değilse oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cba49-176">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="cba49-177">İlk sırayı oluşturmak için hizmet çalıştırabilirsiniz veya bir MSMQ sıra Yöneticisi aracılığıyla oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cba49-177">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="cba49-178">Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="cba49-178">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="cba49-179">Sunucu Yöneticisi'nde açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cba49-179">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="cba49-180">Genişletme **özellikleri** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="cba49-180">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="cba49-181">Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.</span><span class="sxs-lookup"><span data-stu-id="cba49-181">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="cba49-182">Denetleme **işlem** kutusu.</span><span class="sxs-lookup"><span data-stu-id="cba49-182">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="cba49-183">Girin `ServiceModelSamplesTransacted` yeni kuyruk adından farklı.</span><span class="sxs-lookup"><span data-stu-id="cba49-183">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="cba49-184">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cba49-184">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="cba49-185">Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin ve localhost yerine gerçek ana bilgisayar yansıtmak üzere sıra adları değiştirme [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cba49-185">To run the sample in a single- or cross-computer configuration, change the queue names to reflect the actual hostname instead of localhost and follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="cba49-186">Varsayılan olarak `netMsmqBinding` bağlama taşıma, güvenlik etkindir.</span><span class="sxs-lookup"><span data-stu-id="cba49-186">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="cba49-187">İki özellik `MsmqAuthenticationMode` ve `MsmqProtectionLevel`, birlikte taşıma güvenliği türü belirlenemedi.</span><span class="sxs-lookup"><span data-stu-id="cba49-187">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="cba49-188">Varsayılan olarak, kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`.</span><span class="sxs-lookup"><span data-stu-id="cba49-188">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="cba49-189">Kimlik doğrulaması ve imzalama özellik MSMQ için bir etki alanının parçası olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cba49-189">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="cba49-190">Bu örnek bir etki alanının parçası olmayan bir bilgisayarda çalıştırmanız gerekiyorsa aşağıdaki hata iletisini: "kullanıcının iç message queuing sertifikası yok".</span><span class="sxs-lookup"><span data-stu-id="cba49-190">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>  
  
#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="cba49-191">Örnek bir çalışma alanına katılmış bir bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="cba49-191">To run the sample on a computer joined to a workgroup</span></span>  
  
1.  <span data-ttu-id="cba49-192">Bilgisayarınız bir etki alanının parçası değilse, kimlik doğrulama modu ve koruma düzeyini ayarlayarak taşıma güvenliği devre dışı bırakma `None` aşağıdaki örnek yapılandırmada gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="cba49-192">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding name="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="cba49-193">Uç noktanın bindingConfiguration özniteliğini ayarlayarak uç nokta bağlama ile ilişkili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="cba49-193">Ensure the endpoint is associated with the binding by setting the endpoint's bindingConfiguration attribute.</span></span>  
  
2.  <span data-ttu-id="cba49-194">Örneği çalıştırmadan önce PoisonMessageServer, sunucu ve istemci yapılandırmasına değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="cba49-194">Ensure that you change the configuration on the PoisonMessageServer, server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cba49-195">Ayarı `security mode` için `None` ayarına eşdeğerdir `MsmqAuthenticationMode`, `MsmqProtectionLevel`, ve `Message` güvenlik `None`.</span><span class="sxs-lookup"><span data-stu-id="cba49-195">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel`, and `Message` security to `None`.</span></span>  
  
3.  <span data-ttu-id="cba49-196">İş Meta veri değişimi için sırayla biz http bağlama ile bir URL kaydedin.</span><span class="sxs-lookup"><span data-stu-id="cba49-196">In order for Meta Data Exchange to work, we register a URL with http binding.</span></span> <span data-ttu-id="cba49-197">Bu hizmet bir yükseltilmiş komut istemi penceresine çalıştırmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cba49-197">This requires that the service run in an elevated command window.</span></span> <span data-ttu-id="cba49-198">Aksi halde, bir özel durum gibi alın: işlenmeyen özel durum: System.ServiceModel.AddressAccessDeniedException: HTTP URL kaydedemedi http://+:8000/ServiceModelSamples/service/.</span><span class="sxs-lookup"><span data-stu-id="cba49-198">Otherwise, you get an exception such as: Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/.</span></span> <span data-ttu-id="cba49-199">İşleminizi bu ad alanına erişim hakları yok (bkz http://go.microsoft.com/fwlink/?LinkId=70353 Ayrıntılar için).</span><span class="sxs-lookup"><span data-stu-id="cba49-199">Your process does not have access rights to this namespace (see http://go.microsoft.com/fwlink/?LinkId=70353 for details).</span></span> <span data-ttu-id="cba49-200">System.Net.HttpListenerException--->: erişim reddedildi.</span><span class="sxs-lookup"><span data-stu-id="cba49-200">---> System.Net.HttpListenerException: Access is denied.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cba49-201">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="cba49-201">The samples may already be installed on your computer.</span></span> <span data-ttu-id="cba49-202">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="cba49-202">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cba49-203">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="cba49-203">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cba49-204">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="cba49-204">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`  
  
## <a name="see-also"></a><span data-ttu-id="cba49-205">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cba49-205">See Also</span></span>
