---
title: Windows Communication Foundation'dan İleti Kuyruğuna
ms.date: 03/30/2017
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
ms.openlocfilehash: a6e322936740f7d88d30b9a205ac937a807bedc1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552933"
---
# <a name="windows-communication-foundation-to-message-queuing"></a><span data-ttu-id="55ca9-102">Windows Communication Foundation'dan İleti Kuyruğuna</span><span class="sxs-lookup"><span data-stu-id="55ca9-102">Windows Communication Foundation to Message Queuing</span></span>

<span data-ttu-id="55ca9-103">Bu örnek, bir Windows Communication Foundation (WCF) uygulamasının bir Message Queuing (MSMQ) uygulamasına nasıl ileti gönderebileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="55ca9-103">This sample demonstrates how a Windows Communication Foundation (WCF) application can send a message to a Message Queuing (MSMQ) application.</span></span> <span data-ttu-id="55ca9-104">Hizmet, sıraya alınan iletileri alma hizmetini gözlemlemeye olanak sağlayan, kendinden konak bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="55ca9-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span> <span data-ttu-id="55ca9-105">Hizmetin ve istemcinin aynı anda çalışıyor olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="55ca9-105">The service and client do not have to be running at the same time.</span></span>

 <span data-ttu-id="55ca9-106">Hizmet kuyruk ve işlem siparişlerinden iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="55ca9-106">The service receives messages from the queue and processes orders.</span></span> <span data-ttu-id="55ca9-107">Hizmet bir işlem kuyruğu oluşturur ve aşağıdaki örnek kodda gösterildiği gibi ileti alma iletisi işleyicisini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="55ca9-107">The service creates a transactional queue and sets up a message received message handler, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="55ca9-108">Kuyrukta bir ileti alındığında ileti işleyicisi `ProcessOrder` çağrılır.</span><span class="sxs-lookup"><span data-stu-id="55ca9-108">When a message is received in the queue, the message handler `ProcessOrder` is invoked.</span></span>

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

 <span data-ttu-id="55ca9-109">Hizmet `ProcessOrder` MSMQ ileti gövdesinden ayıklar ve siparişi işler.</span><span class="sxs-lookup"><span data-stu-id="55ca9-109">The service extracts the `ProcessOrder` from the MSMQ message body, and processes the order.</span></span>

 <span data-ttu-id="55ca9-110">MSMQ kuyruğu adı, aşağıdaki örnek yapılandırmada gösterildiği gibi, yapılandırma dosyasının bir appSettings bölümünde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="55ca9-110">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

> [!NOTE]
> <span data-ttu-id="55ca9-111">Sıra adı, yerel bilgisayar için bir nokta (.) ve kendi yolunda ters eğik çizgi ayırıcılar kullanır.</span><span class="sxs-lookup"><span data-stu-id="55ca9-111">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span>

 <span data-ttu-id="55ca9-112">İstemci bir satınalma siparişi oluşturur ve aşağıdaki örnek kodda gösterildiği gibi, satın alma sırasını bir işlemin kapsamı içinde gönderir.</span><span class="sxs-lookup"><span data-stu-id="55ca9-112">The client creates a purchase order and submits the purchase order within the scope of a transaction, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="55ca9-113">İstemci, MSMQ iletisini sıraya göndermek için özel bir istemci sırayla kullanır.</span><span class="sxs-lookup"><span data-stu-id="55ca9-113">The client uses a custom client in-order to send the MSMQ message to the queue.</span></span> <span data-ttu-id="55ca9-114">İletiyi alan ve işleyen uygulama bir WCF uygulaması değil bir MSMQ uygulaması olduğundan, iki uygulama arasında örtük bir hizmet sözleşmesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="55ca9-114">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="55ca9-115">Bu nedenle, Bu senaryodaki Svcutil.exe aracını kullanarak bir ara sunucu oluşturmuyoruz.</span><span class="sxs-lookup"><span data-stu-id="55ca9-115">So, we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="55ca9-116">Özel istemci temelde, `MsmqIntegration` ileti göndermek için bağlamayı kullanan tüm WCF uygulamaları için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="55ca9-116">The custom client is essentially the same for all WCF applications that use the `MsmqIntegration` binding to send messages.</span></span> <span data-ttu-id="55ca9-117">Diğer istemcilerin aksine, bir dizi hizmet işlemi içermez.</span><span class="sxs-lookup"><span data-stu-id="55ca9-117">Unlike other clients, it does not include a range of service operations.</span></span> <span data-ttu-id="55ca9-118">Yalnızca bir ileti gönder işlemidir.</span><span class="sxs-lookup"><span data-stu-id="55ca9-118">It is a submit message operation only.</span></span>

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

 <span data-ttu-id="55ca9-119">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencereleri içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="55ca9-119">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="55ca9-120">Hizmetin istemciden ileti alacağını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55ca9-120">You can see the service receive messages from the client.</span></span> <span data-ttu-id="55ca9-121">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="55ca9-121">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="55ca9-122">Kuyruk kullanımda olduğu için istemci ve hizmetin aynı anda çalışmaya ve çalışır durumda olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="55ca9-122">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="55ca9-123">Örneğin, istemcisini çalıştırabilir, kapatabilir ve ardından hizmeti başlatabilir ve yine de iletilerini alabilir.</span><span class="sxs-lookup"><span data-stu-id="55ca9-123">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

> [!NOTE]
> <span data-ttu-id="55ca9-124">Bu örnek Message Queuing yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="55ca9-124">This sample requires the installation of Message Queuing.</span></span> <span data-ttu-id="55ca9-125">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))'teki yükleme yönergelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="55ca9-125">See the installation instructions in [Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85)).</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="55ca9-126">Örneği kurma, oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="55ca9-126">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="55ca9-127">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="55ca9-127">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="55ca9-128">Önce hizmet çalıştırıldığında, sıranın mevcut olduğundan emin olmak için kontrol edilir.</span><span class="sxs-lookup"><span data-stu-id="55ca9-128">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="55ca9-129">Sıra yoksa, hizmet bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="55ca9-129">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="55ca9-130">Kuyruğu oluşturmak için önce hizmeti çalıştırabilir veya MSMQ kuyruğu Yöneticisi aracılığıyla bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55ca9-130">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="55ca9-131">Windows 2008 ' de bir sıra oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="55ca9-131">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="55ca9-132">Visual Studio 2012 ' de Sunucu Yöneticisi açın.</span><span class="sxs-lookup"><span data-stu-id="55ca9-132">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="55ca9-133">**Özellikler** sekmesini genişletin.</span><span class="sxs-lookup"><span data-stu-id="55ca9-133">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="55ca9-134">**Özel ileti sıraları**' na sağ tıklayın ve ardından **Yeni**  >  **özel kuyruk**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="55ca9-134">Right-click **Private Message Queues**, and then select **New** > **Private Queue**.</span></span>

    4. <span data-ttu-id="55ca9-135">**İşlem** kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="55ca9-135">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="55ca9-136">`ServiceModelSamplesTransacted`Yeni kuyruğun adı olarak girin.</span><span class="sxs-lookup"><span data-stu-id="55ca9-136">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="55ca9-137">Çözümün C# veya Visual Basic sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="55ca9-137">To build the C# or Visual Basic edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="55ca9-138">Örneği tek bilgisayarlı bir yapılandırmada çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="55ca9-138">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="run-the-sample-across-computers"></a><span data-ttu-id="55ca9-139">Örneği bilgisayarlar arasında çalıştırma</span><span class="sxs-lookup"><span data-stu-id="55ca9-139">Run the sample across computers</span></span>

1. <span data-ttu-id="55ca9-140">Hizmet programı dosyalarını dile özgü klasörün altındaki \service\bin\ klasöründen hizmet bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="55ca9-140">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="55ca9-141">İstemci program dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="55ca9-141">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="55ca9-142">Client.exe.config dosyasında, istemci uç noktası adresini "." yerine hizmet bilgisayar adını belirtecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="55ca9-142">In the Client.exe.config file, change the client endpoint address to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="55ca9-143">Hizmet bilgisayarında, bir komut isteminden Service.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="55ca9-143">On the service computer, launch Service.exe from a command prompt.</span></span>

5. <span data-ttu-id="55ca9-144">İstemci bilgisayarda, bir komut isteminden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="55ca9-144">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="55ca9-145">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="55ca9-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="55ca9-146">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="55ca9-146">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="55ca9-147">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="55ca9-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="55ca9-148">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="55ca9-148">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`

## <a name="see-also"></a><span data-ttu-id="55ca9-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55ca9-149">See also</span></span>

- [<span data-ttu-id="55ca9-150">Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="55ca9-150">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- <span data-ttu-id="55ca9-151">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="55ca9-151">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span></span>
