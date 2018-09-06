---
title: Özel Demux
ms.date: 03/30/2017
ms.assetid: fc54065c-518e-4146-b24a-0fe00038bfa7
ms.openlocfilehash: 1542743a6e1658bad162d7ee9ca73e6b9b0444e2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732374"
---
# <a name="custom-demux"></a><span data-ttu-id="b4994-102">Özel Demux</span><span class="sxs-lookup"><span data-stu-id="b4994-102">Custom Demux</span></span>
<span data-ttu-id="b4994-103">Bu örnek, böylece Windows Communication Foundation (WCF) kullanan hizmetleri nasıl MSMQ İleti üstbilgileri için farklı hizmet işlemleri eşlenebilir gösterir <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> gösterildiği şekilde bir hizmet işlemi kullanarak sınırlı [ Message Queuing için Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) ve [Message Queuing Windows Communication Foundation'a](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b4994-103">This sample demonstrates how MSMQ message headers can be mapped to different service operations so that Windows Communication Foundation (WCF) services that use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> are not limited to using one service operation as demonstrated in the [Message Queuing to Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) and [Windows Communication Foundation to Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) samples.</span></span>  
  
 <span data-ttu-id="b4994-104">Bu örnekte, alan hizmet kuyruğa alınmış iletileri gözlemleyin sağlamak için şirket içinde barındırılan bir konsol uygulaması hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="b4994-104">The service in this sample is a self-hosted console application to enable you to observe the service that receives queued messages.</span></span>  
  
 <span data-ttu-id="b4994-105">Hizmet sözleşme `IOrderProcessor`ve Kuyruklar ile kullanım için uygun olan bir tek yönlü hizmeti tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b4994-105">The service contract is `IOrderProcessor`, and defines a one-way service that is suitable for use with queues.</span></span>  

```csharp
[ServiceContract]  
[KnownType(typeof(PurchaseOrder))]  
[KnownType(typeof(String))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Name = "SubmitPurchaseOrder")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
  
    [OperationContract(IsOneWay = true, Name = "CancelPurchaseOrder")]  
    void CancelPurchaseOrder(MsmqMessage<string> ponumber);  
}  
```

 <span data-ttu-id="b4994-106">Bir MSMQ iletisinin bir eylem üst bilgisi yok.</span><span class="sxs-lookup"><span data-stu-id="b4994-106">An MSMQ message does not have an Action header.</span></span> <span data-ttu-id="b4994-107">İşlem sözleşmeleri farklı MSMQ iletileri otomatik olarak eşlemeye mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="b4994-107">It is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="b4994-108">Bu nedenle, yalnızca bir işlem anlaşması olabilir.</span><span class="sxs-lookup"><span data-stu-id="b4994-108">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="b4994-109">Hizmet uygular bu sınırlamanın üstesinden gelmek için <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> yöntemi <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b4994-109">To overcome this limitation, the service implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> method of the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface.</span></span> <span data-ttu-id="b4994-110"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> Yöntemi bir özel hizmet işlemi için belirtilen bir üst bilgi iletisinin eşlemek bir hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4994-110">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> method enables the service to map a given header of the message to a particular service operation.</span></span> <span data-ttu-id="b4994-111">Bu örnekte, hizmet işlemleri için ileti etiketi üstbilgi eşlenir.</span><span class="sxs-lookup"><span data-stu-id="b4994-111">In this sample, the message's label header is mapped to the service operations.</span></span> <span data-ttu-id="b4994-112">`Name` Da işlem anlaşması parametresinin belirler hangi hizmet işlemi için belirli bir ileti etiket dağıtılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4994-112">The `Name` parameter of the operation contract determines which service operation must be dispatched for a given message label.</span></span> <span data-ttu-id="b4994-113">İleti etiketi başlığı "SubmitPurchaseOrder" içeriyorsa, örneğin, "SubmitPurchaseOrder" hizmet işlemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b4994-113">For example, if the message's label header contains "SubmitPurchaseOrder", the "SubmitPurchaseOrder" service operation is invoked.</span></span>  

```csharp
public class OperationSelector : IDispatchOperationSelector  
{  
    public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
    {  
        MsmqIntegrationMessageProperty property = MsmqIntegrationMessageProperty.Get(message);  
        return property.Label;  
    }  
}  
```

 <span data-ttu-id="b4994-114">Hizmet uygulamalıdır <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> yöntemi <xref:System.ServiceModel.Description.IContractBehavior> arabirimi aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="b4994-114">The service must implement the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> method of the <xref:System.ServiceModel.Description.IContractBehavior> interface as shown in the following sample code.</span></span> <span data-ttu-id="b4994-115">Bu özel geçerlidir `OperationSelector` hizmet framework gönderme çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="b4994-115">This applies the custom `OperationSelector` to the service framework dispatch runtime.</span></span>  

```csharp
void IContractBehavior.ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)  
{  
    dispatch.OperationSelector = new OperationSelector();  
}  
```

 <span data-ttu-id="b4994-116">Bir ileti dağıtıcısı kişinin geçmelidir <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> ClientRuntime için alma önce.</span><span class="sxs-lookup"><span data-stu-id="b4994-116">A message must pass through the dispatcher's <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> before getting to the OperationSelector.</span></span> <span data-ttu-id="b4994-117">Varsayılan olarak bir ileti reddedilir eylem hizmeti tarafından uygulanan herhangi bir sözleşme bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="b4994-117">By default a message is rejected if its action cannot be found on any contract implemented by the service.</span></span> <span data-ttu-id="b4994-118">Bu onay önlemek için biz uygulayan bir <xref:System.ServiceModel.Description.IEndpointBehavior> adlı `MatchAllFilterBehavior`, herhangi bir ileti geçişine izin veren `ContractFilter` uygulayarak <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> gibi.</span><span class="sxs-lookup"><span data-stu-id="b4994-118">To avoid this check, we implement an <xref:System.ServiceModel.Description.IEndpointBehavior> named `MatchAllFilterBehavior`, which allows any message to pass through the `ContractFilter` by applying the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> as follows.</span></span>  

```csharp
public void ApplyDispatchBehavior(ServiceEndpoint serviceEndpoint, EndpointDispatcher endpointDispatcher)  
{  
    endpointDispatcher.ContractFilter = new MatchAllMessageFilter();  
}  
```
  
 <span data-ttu-id="b4994-119">Hizmet tarafından bir ileti alındığında, uygun bir hizmet işlemi etiket üstbilgisi tarafından sağlanan bilgileri kullanarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="b4994-119">When a message is received by the service, the appropriate service operation is dispatched using the information provided by the label header.</span></span> <span data-ttu-id="b4994-120">İletisinin gövdesi seri durumdan bir `PurchaseOrder` aşağıdaki örnek kodda gösterildiği gibi nesne.</span><span class="sxs-lookup"><span data-stu-id="b4994-120">The body of the message is deserialized into a `PurchaseOrder` object, as shown in the following sample code.</span></span>  

```csharp
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
{  
    PurchaseOrder po = (PurchaseOrder)msg.Body;  
    Random statusIndexer = new Random();  
    po.Status = (OrderStates)statusIndexer.Next(3);  
    Console.WriteLine("Processing {0} ", po);  
}  
```

 <span data-ttu-id="b4994-121">Hizmet kendiliğinden barındırılır.</span><span class="sxs-lookup"><span data-stu-id="b4994-121">The service is self-hosted.</span></span> <span data-ttu-id="b4994-122">MSMQ kullanırken, kullanılan kuyruk önceden oluşturulmuş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4994-122">When using the MSMQ, the queue that is used must be created in advance.</span></span> <span data-ttu-id="b4994-123">Bu, el ile veya kod aracılığıyla yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4994-123">This can be done manually or through code.</span></span> <span data-ttu-id="b4994-124">Bu örnekte, hizmet sırası varlığını denetlemek için kod içeren ve kuyruk yoksa oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b4994-124">In this sample, the service contains code to check for the existence of the queue and creates it if the queue does not exist.</span></span> <span data-ttu-id="b4994-125">Kuyruk adı yapılandırma dosyasından okunur.</span><span class="sxs-lookup"><span data-stu-id="b4994-125">The queue name is read from the configuration file.</span></span>  

```csharp
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration  
    string queueName = ConfigurationManager.AppSettings["orderQueueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
    {                 
        ServiceEndpoint endpoint = serviceHost.Description.Endpoints[0];  
        endpoint.Behaviors.Add(new MatchAllFilterBehavior());  
  
        //Open the ServiceHost to create listeners and start listening for messages.  
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

 <span data-ttu-id="b4994-126">MSMQ kuyruk adı, bir yapılandırma dosyasının appSettings bölümünde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b4994-126">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4994-127">Kuyruk adı, eğik çizgi ayırıcılar yolundaki ve yerel bilgisayar için bir nokta (.) kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4994-127">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="b4994-128">WCF uç nokta adresini msmq.formatname düzenini belirtir ve yerel bilgisayar için localhost kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4994-128">The WCF endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="b4994-129">Düzen izleyen bir yönergeleri adresleme MSMQ biçim adına göre düzgün biçimlendirilmiş bir kuyruk adresidir.</span><span class="sxs-lookup"><span data-stu-id="b4994-129">What follows the scheme is a properly formatted queue address according to the MSMQ Format name addressing guidelines.</span></span>  
  
```xml  
<appSettings>  
    <!-- Use appSetting to configure the MSMQ queue name. -->  
    <add key="queueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="b4994-130">Bu örnek yüklenmesini gerektirir [Message Queuing](https://go.microsoft.com/fwlink/?LinkId=95143).</span><span class="sxs-lookup"><span data-stu-id="b4994-130">This sample requires the installation of [Message Queuing](https://go.microsoft.com/fwlink/?LinkId=95143).</span></span>  
  
 <span data-ttu-id="b4994-131">Hizmeti başlatın ve istemci çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b4994-131">Start the service and run the client.</span></span>  
  
 <span data-ttu-id="b4994-132">Aşağıdaki çıktı, istemcide görülür.</span><span class="sxs-lookup"><span data-stu-id="b4994-132">The following output is seen on the client.</span></span>  
  
```  
Placed the order:Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
Canceled the Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="b4994-133">Aşağıdaki çıktı, hizmette görülen gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4994-133">The following output must be seen on the service.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
Processing Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Shipped  
Purchase Order 28fc457a-1a56-4fe0-9dde-156965c21ed6 is canceled  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b4994-134">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b4994-134">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b4994-135">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b4994-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b4994-136">Hizmet ilk olarak çalıştırılırsa, sıranın mevcut olduğundan emin olun kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="b4994-136">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="b4994-137">Kuyruk yoksa, bir hizmeti oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="b4994-137">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="b4994-138">İlk sırayı oluşturmak için hizmet çalıştırabileceğiniz veya bir MSMQ Kuyruk Yöneticisi ile oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4994-138">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="b4994-139">Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="b4994-139">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="b4994-140">Sunucu Yöneticisi'nde açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b4994-140">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="b4994-141">Genişletin **özellikleri** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="b4994-141">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="b4994-142">Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.</span><span class="sxs-lookup"><span data-stu-id="b4994-142">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="b4994-143">Denetleme **işlem** kutusu.</span><span class="sxs-lookup"><span data-stu-id="b4994-143">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="b4994-144">Girin `ServiceModelSamplesTransacted` yeni Kuyruğun adı.</span><span class="sxs-lookup"><span data-stu-id="b4994-144">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="b4994-145">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b4994-145">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="b4994-146">Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b4994-146">To run the sample in a single- or cross- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="b4994-147">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b4994-147">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="b4994-148">Hizmet program dosyaları \service\bin\ klasöründen dile özgü klasörü altında hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="b4994-148">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="b4994-149">İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörünün altındaki istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="b4994-149">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="b4994-150">Yerine hizmeti bilgisayarın adını belirtmek için orderQueueName Client.exe.config dosyasında değiştirme ".".</span><span class="sxs-lookup"><span data-stu-id="b4994-150">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="b4994-151">Hizmet bilgisayarda bir komut istemi'nden Service.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="b4994-151">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="b4994-152">İstemci bilgisayarda bir komut istemi'nden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="b4994-152">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b4994-153">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="b4994-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b4994-154">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b4994-154">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b4994-155">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b4994-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b4994-156">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b4994-156">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\CustomDemux`  
  
## <a name="see-also"></a><span data-ttu-id="b4994-157">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b4994-157">See Also</span></span>  
 [<span data-ttu-id="b4994-158">WCF'de Kuyruğa Alma</span><span class="sxs-lookup"><span data-stu-id="b4994-158">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [<span data-ttu-id="b4994-159">Message Queuing</span><span class="sxs-lookup"><span data-stu-id="b4994-159">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=95143)
