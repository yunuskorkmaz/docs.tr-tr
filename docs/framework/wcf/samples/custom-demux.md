---
title: Özel Demux
ms.date: 03/30/2017
ms.assetid: fc54065c-518e-4146-b24a-0fe00038bfa7
ms.openlocfilehash: e88672f152b87740feef1345b3eac213916a1527
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="custom-demux"></a><span data-ttu-id="10bff-102">Özel Demux</span><span class="sxs-lookup"><span data-stu-id="10bff-102">Custom Demux</span></span>
<span data-ttu-id="10bff-103">Böylece Windows Communication Foundation (WCF) kullanan hizmetleri nasıl MSMQ ileti üstbilgilerini farklı hizmet işlemleri eşlenebilir. Bu örneği gösterir <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> örnekte gösterildiği gibi bir hizmet işlemi kullanmaya sınırlı değildir [ Message Queuing için Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) ve [Message Queuing için Windows Communication Foundation](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) örnekleri.</span><span class="sxs-lookup"><span data-stu-id="10bff-103">This sample demonstrates how MSMQ message headers can be mapped to different service operations so that Windows Communication Foundation (WCF) services that use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> are not limited to using one service operation as demonstrated in the [Message Queuing to Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) and [Windows Communication Foundation to Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) samples.</span></span>  
  
 <span data-ttu-id="10bff-104">Bu örnekte, alan hizmetini sıraya alınan iletileri gözlemleyin sağlamak için bir kendi kendini barındıran konsol uygulaması hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="10bff-104">The service in this sample is a self-hosted console application to enable you to observe the service that receives queued messages.</span></span>  
  
 <span data-ttu-id="10bff-105">Hizmet sözleşme `IOrderProcessor`ve Kuyruklar ile kullanım için uygun bir tek yönlü hizmet tanımlar.</span><span class="sxs-lookup"><span data-stu-id="10bff-105">The service contract is `IOrderProcessor`, and defines a one-way service that is suitable for use with queues.</span></span>  

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

 <span data-ttu-id="10bff-106">MSMQ iletisine bir eylem üstbilgisi yok.</span><span class="sxs-lookup"><span data-stu-id="10bff-106">An MSMQ message does not have an Action header.</span></span> <span data-ttu-id="10bff-107">Farklı MSMQ iletileri işlemi sözleşmeleri için otomatik olarak eşlemeye mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="10bff-107">It is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="10bff-108">Bu nedenle, yalnızca bir işlem sözleşmesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="10bff-108">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="10bff-109">Hizmet Implements bu sınırlamanın üstesinden gelmek için <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> yöntemi <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="10bff-109">To overcome this limitation, the service implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> method of the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface.</span></span> <span data-ttu-id="10bff-110"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> Yöntemi, belirli bir hizmet işlemi için belirtilen bir iletinin üstbilgisi eşlemek hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="10bff-110">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> method enables the service to map a given header of the message to a particular service operation.</span></span> <span data-ttu-id="10bff-111">Bu örnekte, ileti etiketi üstbilgi Hizmet işlemlerini eşlenir.</span><span class="sxs-lookup"><span data-stu-id="10bff-111">In this sample, the message's label header is mapped to the service operations.</span></span> <span data-ttu-id="10bff-112">`Name` İşlemi sözleşme parametresinin belirler hangi hizmet işlemi belirli bir ileti etiketi dağıtılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="10bff-112">The `Name` parameter of the operation contract determines which service operation must be dispatched for a given message label.</span></span> <span data-ttu-id="10bff-113">Örneğin, "SubmitPurchaseOrder" İleti etiketi üstbilgi içeriyorsa, "SubmitPurchaseOrder" hizmet işlemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="10bff-113">For example, if the message's label header contains "SubmitPurchaseOrder", the "SubmitPurchaseOrder" service operation is invoked.</span></span>  

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

 <span data-ttu-id="10bff-114">Hizmet uygulamalıdır <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> yöntemi <xref:System.ServiceModel.Description.IContractBehavior> arabirimi aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="10bff-114">The service must implement the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> method of the <xref:System.ServiceModel.Description.IContractBehavior> interface as shown in the following sample code.</span></span> <span data-ttu-id="10bff-115">Bu özel geçerlidir `OperationSelector` hizmet framework gönderme çalışma zamanının.</span><span class="sxs-lookup"><span data-stu-id="10bff-115">This applies the custom `OperationSelector` to the service framework dispatch runtime.</span></span>  

```csharp
void IContractBehavior.ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)  
{  
    dispatch.OperationSelector = new OperationSelector();  
}  
```

 <span data-ttu-id="10bff-116">Bir ileti dağıtıcısı kişinin geçmelidir <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> ClientRuntime alma önce.</span><span class="sxs-lookup"><span data-stu-id="10bff-116">A message must pass through the dispatcher's <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> before getting to the OperationSelector.</span></span> <span data-ttu-id="10bff-117">Varsayılan olarak bir ileti reddedilir eylemi hizmeti tarafından uygulanan herhangi bir sözleşme bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="10bff-117">By default a message is rejected if its action cannot be found on any contract implemented by the service.</span></span> <span data-ttu-id="10bff-118">Bu onay önlemek için biz uygulayan bir <xref:System.ServiceModel.Description.IEndpointBehavior> adlı `MatchAllFilterBehavior`, herhangi bir iletisi geçişine izin veren `ContractFilter` uygulayarak <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> gibi.</span><span class="sxs-lookup"><span data-stu-id="10bff-118">To avoid this check, we implement an <xref:System.ServiceModel.Description.IEndpointBehavior> named `MatchAllFilterBehavior`, which allows any message to pass through the `ContractFilter` by applying the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> as follows.</span></span>  

```csharp
public void ApplyDispatchBehavior(ServiceEndpoint serviceEndpoint, EndpointDispatcher endpointDispatcher)  
{  
    endpointDispatcher.ContractFilter = new MatchAllMessageFilter();  
}  
```
  
 <span data-ttu-id="10bff-119">Bir ileti hizmeti tarafından alındığında, uygun hizmet işlemi etiket üstbilgisi tarafından sağlanan bilgileri kullanarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="10bff-119">When a message is received by the service, the appropriate service operation is dispatched using the information provided by the label header.</span></span> <span data-ttu-id="10bff-120">İleti gövdesi içine seri durumdan bir `PurchaseOrder` , aşağıdaki örnek kodda gösterildiği gibi nesne.</span><span class="sxs-lookup"><span data-stu-id="10bff-120">The body of the message is deserialized into a `PurchaseOrder` object, as shown in the following sample code.</span></span>  

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

 <span data-ttu-id="10bff-121">Hizmet kendiliğinden barındırılır.</span><span class="sxs-lookup"><span data-stu-id="10bff-121">The service is self-hosted.</span></span> <span data-ttu-id="10bff-122">MSMQ kullanırken, sıranın kullanılan önceden oluşturulmuş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="10bff-122">When using the MSMQ, the queue that is used must be created in advance.</span></span> <span data-ttu-id="10bff-123">Bu, el ile veya kod aracılığıyla yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="10bff-123">This can be done manually or through code.</span></span> <span data-ttu-id="10bff-124">Bu örnek, hizmet sıranın varlığını denetlemek için kod içerir ve sıra yoksa oluşturur.</span><span class="sxs-lookup"><span data-stu-id="10bff-124">In this sample, the service contains code to check for the existence of the queue and creates it if the queue does not exist.</span></span> <span data-ttu-id="10bff-125">Kuyruk adı yapılandırma dosyasından okunur.</span><span class="sxs-lookup"><span data-stu-id="10bff-125">The queue name is read from the configuration file.</span></span>  

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

 <span data-ttu-id="10bff-126">MSMQ kuyruk adı bir yapılandırma dosyasının appSettings bölümünde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="10bff-126">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10bff-127">Kuyruk adı, ters eğik çizgi ayırıcıları yolundaki ve yerel bilgisayar için bir nokta (.) kullanır.</span><span class="sxs-lookup"><span data-stu-id="10bff-127">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="10bff-128">WCF uç noktası adresi msmq.formatname düzeni belirtir ve yerel bilgisayar için localhost kullanır.</span><span class="sxs-lookup"><span data-stu-id="10bff-128">The WCF endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="10bff-129">Düzeni izleyen bir yönergeleri adresleme MSMQ biçim adı göre düzgün biçimlendirilmiş sıra adresidir.</span><span class="sxs-lookup"><span data-stu-id="10bff-129">What follows the scheme is a properly formatted queue address according to the MSMQ Format name addressing guidelines.</span></span>  
  
```xml  
<appSettings>  
    <!-- Use appSetting to configure the MSMQ queue name. -->  
    <add key="queueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="10bff-130">Bu örnek yüklenmesini gerektirir [Message Queuing](http://go.microsoft.com/fwlink/?LinkId=95143).</span><span class="sxs-lookup"><span data-stu-id="10bff-130">This sample requires the installation of [Message Queuing](http://go.microsoft.com/fwlink/?LinkId=95143).</span></span>  
  
 <span data-ttu-id="10bff-131">Hizmeti başlatmak ve istemci çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="10bff-131">Start the service and run the client.</span></span>  
  
 <span data-ttu-id="10bff-132">Aşağıdaki çıkış istemcide görülür.</span><span class="sxs-lookup"><span data-stu-id="10bff-132">The following output is seen on the client.</span></span>  
  
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
  
 <span data-ttu-id="10bff-133">Aşağıdaki çıkış hizmette görülen gerekir.</span><span class="sxs-lookup"><span data-stu-id="10bff-133">The following output must be seen on the service.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="10bff-134">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="10bff-134">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="10bff-135">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="10bff-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="10bff-136">Hizmetin ilk olarak çalışıyorsa, sıranın var olduğundan emin olmak için kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="10bff-136">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="10bff-137">Hizmet sırası mevcut değilse oluşturur.</span><span class="sxs-lookup"><span data-stu-id="10bff-137">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="10bff-138">İlk sırayı oluşturmak için hizmet çalıştırabilirsiniz veya bir MSMQ sıra Yöneticisi aracılığıyla oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10bff-138">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="10bff-139">Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="10bff-139">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="10bff-140">Sunucu Yöneticisi'nde açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="10bff-140">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="10bff-141">Genişletme **özellikleri** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="10bff-141">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="10bff-142">Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.</span><span class="sxs-lookup"><span data-stu-id="10bff-142">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="10bff-143">Denetleme **işlem** kutusu.</span><span class="sxs-lookup"><span data-stu-id="10bff-143">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="10bff-144">Girin `ServiceModelSamplesTransacted` yeni kuyruk adından farklı.</span><span class="sxs-lookup"><span data-stu-id="10bff-144">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="10bff-145">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="10bff-145">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="10bff-146">Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="10bff-146">To run the sample in a single- or cross- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="10bff-147">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="10bff-147">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="10bff-148">Hizmet program dosyalarını dile özgü klasörü altındaki \service\bin\ klasöründen hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="10bff-148">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="10bff-149">İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörü altında istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="10bff-149">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="10bff-150">Hizmet bilgisayar adı yerine belirtmek için orderQueueName Client.exe.config dosyasında değiştirmek ".".</span><span class="sxs-lookup"><span data-stu-id="10bff-150">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="10bff-151">Hizmet bilgisayarda bir komut isteminden Service.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="10bff-151">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="10bff-152">İstemci bilgisayarda bir komut isteminden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="10bff-152">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="10bff-153">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="10bff-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="10bff-154">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="10bff-154">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="10bff-155">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="10bff-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="10bff-156">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="10bff-156">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\CustomDemux`  
  
## <a name="see-also"></a><span data-ttu-id="10bff-157">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="10bff-157">See Also</span></span>  
 [<span data-ttu-id="10bff-158">WCF'de Kuyruğa Alma</span><span class="sxs-lookup"><span data-stu-id="10bff-158">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [<span data-ttu-id="10bff-159">Message Queuing</span><span class="sxs-lookup"><span data-stu-id="10bff-159">Message Queuing</span></span>](http://go.microsoft.com/fwlink/?LinkId=95143)
