---
title: Windows Communication Foundation'dan İleti Kuyruğuna
ms.date: 03/30/2017
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
ms.openlocfilehash: 1551ab407049e871a9275d148b1c84dc2791ccad
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343395"
---
# <a name="windows-communication-foundation-to-message-queuing"></a><span data-ttu-id="5e15c-102">Windows Communication Foundation'dan İleti Kuyruğuna</span><span class="sxs-lookup"><span data-stu-id="5e15c-102">Windows Communication Foundation to Message Queuing</span></span>
<span data-ttu-id="5e15c-103">Bu örnek, bir Windows Communication Foundation (WCF) uygulaması bir Message Queuing (MSMQ) uygulaması için bir ileti nasıl gönderebileceğiniz gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5e15c-103">This sample demonstrates how a Windows Communication Foundation (WCF) application can send a message to a Message Queuing (MSMQ) application.</span></span> <span data-ttu-id="5e15c-104">Hizmeti, sıraya alınan iletileri alma hizmeti gözlemleyin sağlamak için bir şirket içinde barındırılan bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="5e15c-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span> <span data-ttu-id="5e15c-105">Hizmet ve istemci aynı anda çalıştırılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5e15c-105">The service and client do not have to be running at the same time.</span></span>

 <span data-ttu-id="5e15c-106">Hizmet iletileri kuyruktan alır ve siparişler işler.</span><span class="sxs-lookup"><span data-stu-id="5e15c-106">The service receives messages from the queue and processes orders.</span></span> <span data-ttu-id="5e15c-107">Hizmet, bir işlem kuyruğu oluşturur ve bir ileti alındı ileti işleyicisini, aşağıdaki örnek kodda gösterildiği gibi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5e15c-107">The service creates a transactional queue and sets up a message received message handler, as shown in the following sample code.</span></span>

```csharp
static void Main(string[] args)
{
    if (!MessageQueue.Exists(
              ConfigurationManager.AppSettings["queueName"]))
       MessageQueue.Create(
           ConfigurationManager.AppSettings["queueName"], true);
        //Connect to the queue
        MessageQueue Queue = new
    MessageQueue(ConfigurationManager.AppSettings["queueName"]);
    Queue.ReceiveCompleted +=
                 new ReceiveCompletedEventHandler(ProcessOrder);
    Queue.BeginReceive();
    Console.WriteLine("Order Service is running");
    Console.ReadLine();
}
```

 <span data-ttu-id="5e15c-108">Ne zaman bir ileti alındığında kuyrukta ileti işleyicisi `ProcessOrder` çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5e15c-108">When a message is received in the queue, the message handler `ProcessOrder` is invoked.</span></span>

```csharp
public static void ProcessOrder(Object source,
    ReceiveCompletedEventArgs asyncResult)
{
    try
    {
        // Connect to the queue.
        MessageQueue Queue = (MessageQueue)source;
        // End the asynchronous receive operation.
        System.Messaging.Message msg =
                     Queue.EndReceive(asyncResult.AsyncResult);
        msg.Formatter = new System.Messaging.XmlMessageFormatter(
                                new Type[] { typeof(PurchaseOrder) });
        PurchaseOrder po = (PurchaseOrder) msg.Body;
        Random statusIndexer = new Random();
        po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];
        Console.WriteLine("Processing {0} ", po);
        Queue.BeginReceive();
    }
    catch (System.Exception ex)
    {
        Console.WriteLine(ex.Message);
    }

}
```

 <span data-ttu-id="5e15c-109">Hizmet ayıklar `ProcessOrder` MSMQ İleti gövdesi ve sırayla işler.</span><span class="sxs-lookup"><span data-stu-id="5e15c-109">The service extracts the `ProcessOrder` from the MSMQ message body, and processes the order.</span></span>

 <span data-ttu-id="5e15c-110">MSMQ kuyruk adı, aşağıdaki örnek yapılandırmada gösterildiği gibi bir yapılandırma dosyasının appSettings bölümünde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="5e15c-110">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

> [!NOTE]
>  <span data-ttu-id="5e15c-111">Kuyruk adı, eğik çizgi ayırıcılar yolundaki ve yerel bilgisayar için bir nokta (.) kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e15c-111">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span>

 <span data-ttu-id="5e15c-112">İstemci, bir sipariş oluşturur ve aşağıdaki örnek kodda gösterildiği gibi bir işlem kapsamında satın alma siparişi gönderir.</span><span class="sxs-lookup"><span data-stu-id="5e15c-112">The client creates a purchase order and submits the purchase order within the scope of a transaction, as shown in the following sample code.</span></span>

```csharp
// Create the purchase order
PurchaseOrder po = new PurchaseOrder();
// Fill in the details
...

OrderProcessorClient client = new OrderProcessorClient("OrderResponseEndpoint");

MsmqMessage<PurchaseOrder> ordermsg = new MsmqMessage<PurchaseOrder>(po);
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{
    client.SubmitPurchaseOrder(ordermsg);
    scope.Complete();
}
Console.WriteLine("Order has been submitted:{0}", po);

//Closing the client gracefully closes the connection and cleans up resources
client.Close();
```

 <span data-ttu-id="5e15c-113">İstemci bir özel istemci sırayla MSMQ ileti sırasına göndermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e15c-113">The client uses a custom client in-order to send the MSMQ message to the queue.</span></span> <span data-ttu-id="5e15c-114">Alan ve iletiyi işleyen bir uygulama bir MSMQ uygulama ve WCF uygulaması olduğundan iki uygulama arasında örtük hizmet sözleşme yok.</span><span class="sxs-lookup"><span data-stu-id="5e15c-114">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="5e15c-115">Bu nedenle, bu senaryoda Svcutil.exe aracını kullanarak bir proxy oluşturamıyoruz.</span><span class="sxs-lookup"><span data-stu-id="5e15c-115">So, we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="5e15c-116">Özel istemci temel olarak kullanan tüm WCF uygulamaları aynı olduğundan `MsmqIntegration` ileti göndermek için bağlama.</span><span class="sxs-lookup"><span data-stu-id="5e15c-116">The custom client is essentially the same for all WCF applications that use the `MsmqIntegration` binding to send messages.</span></span> <span data-ttu-id="5e15c-117">Diğer istemcilerden farklı olarak, bir dizi hizmet işlemleri içermez.</span><span class="sxs-lookup"><span data-stu-id="5e15c-117">Unlike other clients, it does not include a range of service operations.</span></span> <span data-ttu-id="5e15c-118">Bir gönderme iletisi yalnızca işlemdir.</span><span class="sxs-lookup"><span data-stu-id="5e15c-118">It is a submit message operation only.</span></span>

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}

public partial class OrderProcessorClient : System.ServiceModel.ClientBase<IOrderProcessor>, IOrderProcessor
{
    public OrderProcessorClient(){}

    public OrderProcessorClient(string configurationName)
        : base(configurationName)
    { }

    public OrderProcessorClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)
        : base(binding, address)
    { }

    public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)
    {
        base.Channel.SubmitPurchaseOrder(msg);
    }
}
```

 <span data-ttu-id="5e15c-119">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hizmet ve istemci konsol pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5e15c-119">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="5e15c-120">İstemciden hizmet alma iletileri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e15c-120">You can see the service receive messages from the client.</span></span> <span data-ttu-id="5e15c-121">Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5e15c-121">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="5e15c-122">Sıraya alma kullanımda olduğundan, istemci ve hizmet aynı zamanda açık ve çalışıyor olması gerekmez, unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5e15c-122">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="5e15c-123">Örneğin, istemcisini çalıştıran, da kapatın ve ardından hizmeti başlatın ve hala iletileri alacaksınız.</span><span class="sxs-lookup"><span data-stu-id="5e15c-123">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

> [!NOTE]
>  <span data-ttu-id="5e15c-124">Bu örnek, Message Queuing yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5e15c-124">This sample requires the installation of Message Queuing.</span></span> <span data-ttu-id="5e15c-125">' Ndaki yükleme yönergelerine bakın [Message Queuing](https://go.microsoft.com/fwlink/?LinkId=94968).</span><span class="sxs-lookup"><span data-stu-id="5e15c-125">See the installation instructions in [Message Queuing](https://go.microsoft.com/fwlink/?LinkId=94968).</span></span>  
  
### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="5e15c-126">Kurulum, derleme ve örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5e15c-126">To setup, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5e15c-127">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5e15c-127">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5e15c-128">Hizmet ilk olarak çalıştırılırsa, sıranın mevcut olduğundan emin olun kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="5e15c-128">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="5e15c-129">Kuyruk yoksa, bir hizmeti oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="5e15c-129">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="5e15c-130">İlk sırayı oluşturmak için hizmet çalıştırabileceğiniz veya bir MSMQ Kuyruk Yöneticisi ile oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e15c-130">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="5e15c-131">Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="5e15c-131">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="5e15c-132">Visual Studio 2012'de Sunucu Yöneticisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="5e15c-132">Open Server Manager in Visual Studio 2012.</span></span>  
  
    2.  <span data-ttu-id="5e15c-133">Genişletin **özellikleri** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="5e15c-133">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="5e15c-134">Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.</span><span class="sxs-lookup"><span data-stu-id="5e15c-134">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="5e15c-135">Denetleme **işlem** kutusu.</span><span class="sxs-lookup"><span data-stu-id="5e15c-135">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="5e15c-136">Girin `ServiceModelSamplesTransacted` yeni Kuyruğun adı.</span><span class="sxs-lookup"><span data-stu-id="5e15c-136">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3. <span data-ttu-id="5e15c-137">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5e15c-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="5e15c-138">Tek bilgisayarlı yapılandırmada örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5e15c-138">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="5e15c-139">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5e15c-139">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="5e15c-140">Hizmet program dosyaları \service\bin\ klasöründen dile özgü klasörü altında hizmet bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="5e15c-140">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2. <span data-ttu-id="5e15c-141">İstemci program dosyaları \client\bin\ klasöründen dile özgü klasörünün altındaki istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="5e15c-141">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3. <span data-ttu-id="5e15c-142">Client.exe.config dosyasında yerine hizmeti bilgisayarın adını belirtmek için istemci uç nokta adresini Değiştir ".".</span><span class="sxs-lookup"><span data-stu-id="5e15c-142">In the Client.exe.config file, change the client endpoint address to specify the service computer name instead of ".".</span></span>  
  
4. <span data-ttu-id="5e15c-143">Hizmet bilgisayarda bir komut istemi'nden Service.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="5e15c-143">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5. <span data-ttu-id="5e15c-144">İstemci bilgisayarda bir komut istemi'nden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="5e15c-144">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5e15c-145">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="5e15c-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5e15c-146">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5e15c-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5e15c-147">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5e15c-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5e15c-148">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5e15c-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## <a name="see-also"></a><span data-ttu-id="5e15c-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e15c-149">See also</span></span>

- [<span data-ttu-id="5e15c-150">Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="5e15c-150">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [<span data-ttu-id="5e15c-151">Message Queuing</span><span class="sxs-lookup"><span data-stu-id="5e15c-151">Message Queuing</span></span>](https://go.microsoft.com/fwlink/?LinkId=94968)
