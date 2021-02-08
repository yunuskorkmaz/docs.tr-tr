---
description: 'Hakkında daha fazla bilgi edinin: Message Queuing Windows Communication Foundation'
title: Windows Communication Foundation'dan İleti Kuyruğuna
ms.date: 03/30/2017
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
ms.openlocfilehash: ef4fe5f23b4ce462b13e12b706a3a72225a74f8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798192"
---
# <a name="windows-communication-foundation-to-message-queuing"></a><span data-ttu-id="4dddb-103">Windows Communication Foundation'dan İleti Kuyruğuna</span><span class="sxs-lookup"><span data-stu-id="4dddb-103">Windows Communication Foundation to Message Queuing</span></span>

<span data-ttu-id="4dddb-104">Bu örnek, bir Windows Communication Foundation (WCF) uygulamasının bir Message Queuing (MSMQ) uygulamasına nasıl ileti gönderebileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="4dddb-104">This sample demonstrates how a Windows Communication Foundation (WCF) application can send a message to a Message Queuing (MSMQ) application.</span></span> <span data-ttu-id="4dddb-105">Hizmet, sıraya alınan iletileri alma hizmetini gözlemlemeye olanak sağlayan, kendinden konak bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="4dddb-105">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span> <span data-ttu-id="4dddb-106">Hizmetin ve istemcinin aynı anda çalışıyor olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4dddb-106">The service and client do not have to be running at the same time.</span></span>

 <span data-ttu-id="4dddb-107">Hizmet kuyruk ve işlem siparişlerinden iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="4dddb-107">The service receives messages from the queue and processes orders.</span></span> <span data-ttu-id="4dddb-108">Hizmet bir işlem kuyruğu oluşturur ve aşağıdaki örnek kodda gösterildiği gibi ileti alma iletisi işleyicisini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4dddb-108">The service creates a transactional queue and sets up a message received message handler, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="4dddb-109">Kuyrukta bir ileti alındığında ileti işleyicisi `ProcessOrder` çağrılır.</span><span class="sxs-lookup"><span data-stu-id="4dddb-109">When a message is received in the queue, the message handler `ProcessOrder` is invoked.</span></span>

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

 <span data-ttu-id="4dddb-110">Hizmet `ProcessOrder` MSMQ ileti gövdesinden ayıklar ve siparişi işler.</span><span class="sxs-lookup"><span data-stu-id="4dddb-110">The service extracts the `ProcessOrder` from the MSMQ message body, and processes the order.</span></span>

 <span data-ttu-id="4dddb-111">MSMQ kuyruğu adı, aşağıdaki örnek yapılandırmada gösterildiği gibi, yapılandırma dosyasının bir appSettings bölümünde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4dddb-111">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

> [!NOTE]
> <span data-ttu-id="4dddb-112">Sıra adı, yerel bilgisayar için bir nokta (.) ve kendi yolunda ters eğik çizgi ayırıcılar kullanır.</span><span class="sxs-lookup"><span data-stu-id="4dddb-112">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span>

 <span data-ttu-id="4dddb-113">İstemci bir satınalma siparişi oluşturur ve aşağıdaki örnek kodda gösterildiği gibi, satın alma sırasını bir işlemin kapsamı içinde gönderir.</span><span class="sxs-lookup"><span data-stu-id="4dddb-113">The client creates a purchase order and submits the purchase order within the scope of a transaction, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="4dddb-114">İstemci, MSMQ iletisini sıraya göndermek için özel bir istemci sırayla kullanır.</span><span class="sxs-lookup"><span data-stu-id="4dddb-114">The client uses a custom client in-order to send the MSMQ message to the queue.</span></span> <span data-ttu-id="4dddb-115">İletiyi alan ve işleyen uygulama bir WCF uygulaması değil bir MSMQ uygulaması olduğundan, iki uygulama arasında örtük bir hizmet sözleşmesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="4dddb-115">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="4dddb-116">Bu nedenle, Bu senaryodaki Svcutil.exe aracını kullanarak bir ara sunucu oluşturmuyoruz.</span><span class="sxs-lookup"><span data-stu-id="4dddb-116">So, we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="4dddb-117">Özel istemci temelde, `MsmqIntegration` ileti göndermek için bağlamayı kullanan tüm WCF uygulamaları için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="4dddb-117">The custom client is essentially the same for all WCF applications that use the `MsmqIntegration` binding to send messages.</span></span> <span data-ttu-id="4dddb-118">Diğer istemcilerin aksine, bir dizi hizmet işlemi içermez.</span><span class="sxs-lookup"><span data-stu-id="4dddb-118">Unlike other clients, it does not include a range of service operations.</span></span> <span data-ttu-id="4dddb-119">Yalnızca bir ileti gönder işlemidir.</span><span class="sxs-lookup"><span data-stu-id="4dddb-119">It is a submit message operation only.</span></span>

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

 <span data-ttu-id="4dddb-120">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencereleri içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4dddb-120">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="4dddb-121">Hizmetin istemciden ileti alacağını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4dddb-121">You can see the service receive messages from the client.</span></span> <span data-ttu-id="4dddb-122">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4dddb-122">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="4dddb-123">Kuyruk kullanımda olduğu için istemci ve hizmetin aynı anda çalışmaya ve çalışır durumda olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="4dddb-123">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="4dddb-124">Örneğin, istemcisini çalıştırabilir, kapatabilir ve ardından hizmeti başlatabilir ve yine de iletilerini alabilir.</span><span class="sxs-lookup"><span data-stu-id="4dddb-124">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

> [!NOTE]
> <span data-ttu-id="4dddb-125">Bu örnek Message Queuing yüklenmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4dddb-125">This sample requires the installation of Message Queuing.</span></span> <span data-ttu-id="4dddb-126">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))'teki yükleme yönergelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="4dddb-126">See the installation instructions in [Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85)).</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="4dddb-127">Örneği kurma, oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="4dddb-127">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="4dddb-128">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="4dddb-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="4dddb-129">Önce hizmet çalıştırıldığında, sıranın mevcut olduğundan emin olmak için kontrol edilir.</span><span class="sxs-lookup"><span data-stu-id="4dddb-129">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="4dddb-130">Sıra yoksa, hizmet bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4dddb-130">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="4dddb-131">Kuyruğu oluşturmak için önce hizmeti çalıştırabilir veya MSMQ kuyruğu Yöneticisi aracılığıyla bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4dddb-131">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="4dddb-132">Windows 2008 ' de bir sıra oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="4dddb-132">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="4dddb-133">Visual Studio 2012 ' de Sunucu Yöneticisi açın.</span><span class="sxs-lookup"><span data-stu-id="4dddb-133">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="4dddb-134">**Özellikler** sekmesini genişletin.</span><span class="sxs-lookup"><span data-stu-id="4dddb-134">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="4dddb-135">**Özel ileti sıraları**' na sağ tıklayın ve ardından **Yeni**  >  **özel kuyruk**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="4dddb-135">Right-click **Private Message Queues**, and then select **New** > **Private Queue**.</span></span>

    4. <span data-ttu-id="4dddb-136">**İşlem** kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="4dddb-136">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="4dddb-137">`ServiceModelSamplesTransacted`Yeni kuyruğun adı olarak girin.</span><span class="sxs-lookup"><span data-stu-id="4dddb-137">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="4dddb-138">Çözümün C# veya Visual Basic sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="4dddb-138">To build the C# or Visual Basic edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="4dddb-139">Örneği tek bilgisayarlı bir yapılandırmada çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="4dddb-139">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="run-the-sample-across-computers"></a><span data-ttu-id="4dddb-140">Örneği bilgisayarlar arasında çalıştırma</span><span class="sxs-lookup"><span data-stu-id="4dddb-140">Run the sample across computers</span></span>

1. <span data-ttu-id="4dddb-141">Hizmet programı dosyalarını dile özgü klasörün altındaki \service\bin\ klasöründen hizmet bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="4dddb-141">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="4dddb-142">İstemci program dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="4dddb-142">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="4dddb-143">Client.exe.config dosyasında, istemci uç noktası adresini "." yerine hizmet bilgisayar adını belirtecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4dddb-143">In the Client.exe.config file, change the client endpoint address to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="4dddb-144">Hizmet bilgisayarında, bir komut isteminden Service.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="4dddb-144">On the service computer, launch Service.exe from a command prompt.</span></span>

5. <span data-ttu-id="4dddb-145">İstemci bilgisayarda, bir komut isteminden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="4dddb-145">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4dddb-146">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="4dddb-146">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4dddb-147">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4dddb-147">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="4dddb-148">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4dddb-148">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4dddb-149">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="4dddb-149">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`

## <a name="see-also"></a><span data-ttu-id="4dddb-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4dddb-150">See also</span></span>

- [<span data-ttu-id="4dddb-151">Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="4dddb-151">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- <span data-ttu-id="4dddb-152">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="4dddb-152">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span></span>
