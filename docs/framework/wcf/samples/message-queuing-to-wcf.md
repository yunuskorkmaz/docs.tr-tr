---
title: Windows Communication Foundation'a İleti Kuyruğa Alma
ms.date: 03/30/2017
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
ms.openlocfilehash: cbbbab700a6602fa02160733c383a0fcaa84297b
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850680"
---
# <a name="message-queuing-to-windows-communication-foundation"></a><span data-ttu-id="03c32-102">Windows Communication Foundation'a İleti Kuyruğa Alma</span><span class="sxs-lookup"><span data-stu-id="03c32-102">Message Queuing to Windows Communication Foundation</span></span>
<span data-ttu-id="03c32-103">Bu örnek, bir Message Queuing (MSMQ) uygulamasını bir Windows Communication Foundation (WCF) hizmetine bir MSMQ iletisinin nasıl gönderebileceğiniz gösterilir.</span><span class="sxs-lookup"><span data-stu-id="03c32-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="03c32-104">Hizmeti, sıraya alınan iletileri alma hizmeti gözlemleyin sağlamak için bir şirket içinde barındırılan bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="03c32-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
 <span data-ttu-id="03c32-105">Hizmet sözleşme `IOrderProcessor`, kuyruklar ile kullanım için uygun olan bir tek yönlü hizmeti tanımlar.</span><span class="sxs-lookup"><span data-stu-id="03c32-105">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="03c32-106">Bir MSMQ iletisinin bir eylem üst bilgisi olmadığından, işlem sözleşmeleri farklı MSMQ iletileri otomatik olarak eşlemeye mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="03c32-106">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="03c32-107">Bu nedenle, yalnızca bir işlem anlaşması olabilir.</span><span class="sxs-lookup"><span data-stu-id="03c32-107">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="03c32-108">Hizmeti için birden fazla işlem anlaşması tanımlamak istiyorsanız, uygulamayı dağıtmak için hangi işlem anlaşması karar vermek için (örneğin, etiket veya Correlationıd) MSMQ iletisinin başlığında hangi kullanılabilir bilgi sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="03c32-108">If you want to define more than one operation contract for the service, the application must provide information as to which header in the MSMQ message (for example, the label or correlationID) can be used to decide which operation contract to dispatch.</span></span>
  
 <span data-ttu-id="03c32-109">MSMQ iletisinin hangi üstbilgileri da işlem anlaşması farklı parametrelerle eşlenir bilgi içermiyor.</span><span class="sxs-lookup"><span data-stu-id="03c32-109">The MSMQ message does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="03c32-110">Parametre türüdür <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), temel alınan MSMQ iletisi içerir.</span><span class="sxs-lookup"><span data-stu-id="03c32-110">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), which contains the underlying MSMQ message.</span></span> <span data-ttu-id="03c32-111">' % S'tür "T" içinde <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) sınıfı, MSMQ ileti gövdesine seri verileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="03c32-111">The type "T" in the <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="03c32-112">Bu örnekte `PurchaseOrder` türü MSMQ ileti gövdesine seri.</span><span class="sxs-lookup"><span data-stu-id="03c32-112">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>  
  
 <span data-ttu-id="03c32-113">Aşağıdaki örnek kod, sipariş işleme hizmeti, hizmet sözleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="03c32-113">The following sample code shows the service contract of the order processing service.</span></span>  

```csharp
// Define a service contract.
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 <span data-ttu-id="03c32-114">Kendi kendine barındırılan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="03c32-114">The service is self hosted.</span></span> <span data-ttu-id="03c32-115">MSMQ kullanırken, kullanılan kuyruk önceden oluşturulmuş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="03c32-115">When using MSMQ, the queue used must be created in advance.</span></span> <span data-ttu-id="03c32-116">Bu, el ile veya kod aracılığıyla yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="03c32-116">This can be done manually or through code.</span></span> <span data-ttu-id="03c32-117">Bu örnekte, hizmet sırası varlığını denetler ve gerekirse oluşturur.</span><span class="sxs-lookup"><span data-stu-id="03c32-117">In this sample, the service checks for the existence of the queue and creates it if required.</span></span> <span data-ttu-id="03c32-118">Kuyruk adı yapılandırma dosyasından okunur.</span><span class="sxs-lookup"><span data-stu-id="03c32-118">The queue name is read from the configuration file.</span></span>

```csharp
public static void Main()
{
    // Get the MSMQ queue name from the application settings in
    // configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];
    // Create the MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName, true);
    …
}
```

 <span data-ttu-id="03c32-119">Hizmet oluşturur ve açar bir <xref:System.ServiceModel.ServiceHost> için `OrderProcessorService`aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="03c32-119">The service creates and opens a <xref:System.ServiceModel.ServiceHost> for the `OrderProcessorService`, as shown in the following sample code.</span></span>

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
{
    serviceHost.Open();
    Console.WriteLine("The service is ready.");
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
    serviceHost.Close();
}
```

 <span data-ttu-id="03c32-120">MSMQ kuyruk adı, aşağıdaki örnek yapılandırmada gösterildiği gibi bir yapılandırma dosyasının appSettings bölümünde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="03c32-120">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
>  <span data-ttu-id="03c32-121">Kuyruk adı, eğik çizgi ayırıcılar yolundaki ve yerel bilgisayar için bir nokta (.) kullanır.</span><span class="sxs-lookup"><span data-stu-id="03c32-121">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="03c32-122">WCF uç nokta adresini msmq.formatname düzenini belirtir ve yerel bilgisayar için localhost kullanır.</span><span class="sxs-lookup"><span data-stu-id="03c32-122">The WCF endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="03c32-123">Her MSMQ biçim yönergeleri ele alan adı için kuyruk adresini msmq.formatname düzeni izler.</span><span class="sxs-lookup"><span data-stu-id="03c32-123">The address of the queue for each MSMQ Format Name addressing guidelines follows the msmq.formatname scheme.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="03c32-124">İstemci uygulama kullanan bir MSMQ uygulamasıdır <xref:System.Messaging.MessageQueue.Send%2A> aşağıdaki örnek kodda gösterildiği gibi kuyruğa, dayanıklı ve işlem tabanlı ileti göndermek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="03c32-124">The client application is an MSMQ application that uses the <xref:System.Messaging.MessageQueue.Send%2A> method to send a durable and transactional message to the queue, as shown in the following sample code.</span></span>

```csharp
//Connect to the queue.
MessageQueue orderQueue = new MessageQueue(ConfigurationManager.AppSettings["orderQueueName"]);

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

// Submit the purchase order.
Message msg = new Message();
msg.Body = po;
//Create a transaction scope.
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{

    orderQueue.Send(msg, MessageQueueTransactionType.Automatic);
    // Complete the transaction.
    scope.Complete();

}
Console.WriteLine("Placed the order:{0}", po);
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

 <span data-ttu-id="03c32-125">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hizmet ve istemci konsol pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="03c32-125">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="03c32-126">İstemciden hizmet alma iletileri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c32-126">You can see the service receive messages from the client.</span></span> <span data-ttu-id="03c32-127">Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="03c32-127">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="03c32-128">Sıraya alma kullanımda olduğundan, istemci ve hizmet aynı zamanda açık ve çalışıyor olması gerekmez, unutmayın.</span><span class="sxs-lookup"><span data-stu-id="03c32-128">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="03c32-129">Örneğin, istemcisini çalıştıran, da kapatın ve ardından hizmeti başlatın ve hala iletileri alacaksınız.</span><span class="sxs-lookup"><span data-stu-id="03c32-129">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="03c32-130">Kurulum, derleme ve örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="03c32-130">To setup, build, and run the sample</span></span>

1.  <span data-ttu-id="03c32-131">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="03c32-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2.  <span data-ttu-id="03c32-132">Hizmet ilk olarak çalıştırılırsa, sıranın mevcut olduğundan emin olun kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="03c32-132">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="03c32-133">Kuyruk yoksa, bir hizmeti oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="03c32-133">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="03c32-134">İlk sırayı oluşturmak için hizmet çalıştırabileceğiniz veya bir MSMQ Kuyruk Yöneticisi ile oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c32-134">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="03c32-135">Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="03c32-135">Follow these steps to create a queue in Windows 2008.</span></span>

    1.  <span data-ttu-id="03c32-136">Visual Studio 2012'de Sunucu Yöneticisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="03c32-136">Open Server Manager in Visual Studio 2012.</span></span>

    2.  <span data-ttu-id="03c32-137">Genişletin **özellikleri** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="03c32-137">Expand the **Features** tab.</span></span>

    3.  <span data-ttu-id="03c32-138">Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.</span><span class="sxs-lookup"><span data-stu-id="03c32-138">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4.  <span data-ttu-id="03c32-139">Denetleme **işlem** kutusu.</span><span class="sxs-lookup"><span data-stu-id="03c32-139">Check the **Transactional** box.</span></span>

    5.  <span data-ttu-id="03c32-140">Girin `ServiceModelSamplesTransacted` yeni Kuyruğun adı.</span><span class="sxs-lookup"><span data-stu-id="03c32-140">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3.  <span data-ttu-id="03c32-141">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="03c32-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4.  <span data-ttu-id="03c32-142">Tek bilgisayarlı yapılandırmada örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="03c32-142">To run the sample in a single- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="03c32-143">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="03c32-143">To run the sample across computers</span></span>

1.  <span data-ttu-id="03c32-144">Hizmet program dosyaları \service\bin\ klasöründen dile özgü klasörü altında hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="03c32-144">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2.  <span data-ttu-id="03c32-145">İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörünün altındaki istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="03c32-145">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3.  <span data-ttu-id="03c32-146">Yerine hizmeti bilgisayarın adını belirtmek için orderQueueName Client.exe.config dosyasında değiştirme ".".</span><span class="sxs-lookup"><span data-stu-id="03c32-146">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4.  <span data-ttu-id="03c32-147">Hizmet bilgisayarda bir komut istemi'nden Service.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="03c32-147">On the service computer, launch Service.exe from a command prompt.</span></span>

5.  <span data-ttu-id="03c32-148">İstemci bilgisayarda bir komut istemi'nden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="03c32-148">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="03c32-149">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="03c32-149">The samples may already be installed on your computer.</span></span> <span data-ttu-id="03c32-150">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="03c32-150">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="03c32-151">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="03c32-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="03c32-152">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="03c32-152">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`  
  
## <a name="see-also"></a><span data-ttu-id="03c32-153">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="03c32-153">See Also</span></span>  
 [<span data-ttu-id="03c32-154">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="03c32-154">Queues in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="03c32-155">Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="03c32-155">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [<span data-ttu-id="03c32-156">Message Queuing</span><span class="sxs-lookup"><span data-stu-id="03c32-156">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=94968)
