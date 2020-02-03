---
title: Windows Communication Foundation'a İleti Kuyruğa Alma
ms.date: 03/30/2017
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
ms.openlocfilehash: 541ea23e6748242db57661ceda8e1fedecb66884
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747124"
---
# <a name="message-queuing-to-windows-communication-foundation"></a><span data-ttu-id="683d0-102">Windows Communication Foundation'a İleti Kuyruğa Alma</span><span class="sxs-lookup"><span data-stu-id="683d0-102">Message Queuing to Windows Communication Foundation</span></span>

<span data-ttu-id="683d0-103">Bu örnek, bir Message Queuing (MSMQ) uygulamasının bir Windows Communication Foundation (WCF) hizmetine nasıl MSMQ iletisi gönderebileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="683d0-103">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="683d0-104">Hizmet, sıraya alınan iletileri alma hizmetini gözlemlemeye olanak sağlayan, kendinden konak bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="683d0-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="683d0-105">Hizmet sözleşmesi, kuyruklarla birlikte kullanılmak üzere uygun tek yönlü bir hizmeti tanımlayan `IOrderProcessor`.</span><span class="sxs-lookup"><span data-stu-id="683d0-105">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="683d0-106">Bir MSMQ iletisinde eylem üst bilgisi yok, bu nedenle farklı MSMQ iletilerini işlem sözleşmelerine otomatik olarak eşlemek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="683d0-106">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="683d0-107">Bu nedenle, yalnızca bir işlem sözleşmesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="683d0-107">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="683d0-108">Hizmet için birden fazla işlem sözleşmesi tanımlamak istiyorsanız, uygulamanın hangi işlem sözleşmesinin gönderileceğine karar vermek için MSMQ iletisindeki (örneğin, etiket veya correlationID) hangi üstbilginin kullanılabileceğini belirlemek üzere bilgi sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="683d0-108">If you want to define more than one operation contract for the service, the application must provide information as to which header in the MSMQ message (for example, the label or correlationID) can be used to decide which operation contract to dispatch.</span></span>

 <span data-ttu-id="683d0-109">MSMQ iletisi, hangi üst bilgilerin işlem sözleşmesinin farklı parametreleriyle eşlendiği bilgisini içermez.</span><span class="sxs-lookup"><span data-stu-id="683d0-109">The MSMQ message does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="683d0-110">Parametresi, temeldeki MSMQ iletisini içeren <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) türündedir.</span><span class="sxs-lookup"><span data-stu-id="683d0-110">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), which contains the underlying MSMQ message.</span></span> <span data-ttu-id="683d0-111"><xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) sınıfındaki "T" türü, MSMQ ileti gövdesinde seri hale getirilen verileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="683d0-111">The type "T" in the <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="683d0-112">Bu örnekte, `PurchaseOrder` türü MSMQ ileti gövdesinde serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="683d0-112">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>

 <span data-ttu-id="683d0-113">Aşağıdaki örnek kod, sipariş işleme hizmetinin hizmet sözleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="683d0-113">The following sample code shows the service contract of the order processing service.</span></span>

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

 <span data-ttu-id="683d0-114">Hizmet kendi kendine barındırılır.</span><span class="sxs-lookup"><span data-stu-id="683d0-114">The service is self hosted.</span></span> <span data-ttu-id="683d0-115">MSMQ kullanılırken kullanılan kuyruğun önceden oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="683d0-115">When using MSMQ, the queue used must be created in advance.</span></span> <span data-ttu-id="683d0-116">Bu, el ile veya kod aracılığıyla yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="683d0-116">This can be done manually or through code.</span></span> <span data-ttu-id="683d0-117">Bu örnekte hizmet, sıranın varlığını denetler ve gerekirse oluşturur.</span><span class="sxs-lookup"><span data-stu-id="683d0-117">In this sample, the service checks for the existence of the queue and creates it if required.</span></span> <span data-ttu-id="683d0-118">Sıra adı yapılandırma dosyasından okundu.</span><span class="sxs-lookup"><span data-stu-id="683d0-118">The queue name is read from the configuration file.</span></span>

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

 <span data-ttu-id="683d0-119">Hizmet, aşağıdaki örnek kodda gösterildiği gibi, `OrderProcessorService`için bir <xref:System.ServiceModel.ServiceHost> oluşturur ve açar.</span><span class="sxs-lookup"><span data-stu-id="683d0-119">The service creates and opens a <xref:System.ServiceModel.ServiceHost> for the `OrderProcessorService`, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="683d0-120">MSMQ kuyruğu adı, aşağıdaki örnek yapılandırmada gösterildiği gibi, yapılandırma dosyasının bir appSettings bölümünde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="683d0-120">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="683d0-121">Sıra adı, yerel bilgisayar için bir nokta (.) ve kendi yolunda ters eğik çizgi ayırıcılar kullanır.</span><span class="sxs-lookup"><span data-stu-id="683d0-121">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="683d0-122">WCF uç noktası adresi bir MSMQ. formatname şemasını belirtir ve yerel bilgisayar için localhost kullanır.</span><span class="sxs-lookup"><span data-stu-id="683d0-122">The WCF endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="683d0-123">Her MSMQ Format adı adresleme Kılavuzu için kuyruğun adresi MSMQ. formatname düzenini izler.</span><span class="sxs-lookup"><span data-stu-id="683d0-123">The address of the queue for each MSMQ Format Name addressing guidelines follows the msmq.formatname scheme.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="683d0-124">İstemci uygulaması, aşağıdaki örnek kodda gösterildiği gibi, sıraya dayanıklı ve işlemsel bir ileti göndermek için <xref:System.Messaging.MessageQueue.Send%2A> yöntemini kullanan bir MSMQ uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="683d0-124">The client application is an MSMQ application that uses the <xref:System.Messaging.MessageQueue.Send%2A> method to send a durable and transactional message to the queue, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="683d0-125">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencereleri içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="683d0-125">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="683d0-126">Hizmetin istemciden ileti alacağını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="683d0-126">You can see the service receive messages from the client.</span></span> <span data-ttu-id="683d0-127">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="683d0-127">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="683d0-128">Kuyruk kullanımda olduğu için istemci ve hizmetin aynı anda çalışmaya ve çalışır durumda olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="683d0-128">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="683d0-129">Örneğin, istemcisini çalıştırabilir, kapatabilir ve ardından hizmeti başlatabilir ve yine de iletilerini alabilir.</span><span class="sxs-lookup"><span data-stu-id="683d0-129">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="683d0-130">Örneği kurma, oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="683d0-130">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="683d0-131">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="683d0-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="683d0-132">Önce hizmet çalıştırıldığında, sıranın mevcut olduğundan emin olmak için kontrol edilir.</span><span class="sxs-lookup"><span data-stu-id="683d0-132">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="683d0-133">Sıra yoksa, hizmet bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="683d0-133">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="683d0-134">Kuyruğu oluşturmak için önce hizmeti çalıştırabilir veya MSMQ kuyruğu Yöneticisi aracılığıyla bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="683d0-134">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="683d0-135">Windows 2008 ' de bir sıra oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="683d0-135">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="683d0-136">Visual Studio 2012 ' de Sunucu Yöneticisi açın.</span><span class="sxs-lookup"><span data-stu-id="683d0-136">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="683d0-137">**Özellikler** sekmesini genişletin.</span><span class="sxs-lookup"><span data-stu-id="683d0-137">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="683d0-138">**Özel Ileti kuyrukları**' ne sağ tıklayıp **Yeni**, **özel kuyruk**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="683d0-138">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="683d0-139">**İşlem** kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="683d0-139">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="683d0-140">Yeni kuyruğun adı olarak `ServiceModelSamplesTransacted` girin.</span><span class="sxs-lookup"><span data-stu-id="683d0-140">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="683d0-141">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="683d0-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="683d0-142">Örneği tek bilgisayarlı bir yapılandırmada çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="683d0-142">To run the sample in a single- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

## <a name="run-the-sample-across-computers"></a><span data-ttu-id="683d0-143">Örneği bilgisayarlar arasında çalıştırma</span><span class="sxs-lookup"><span data-stu-id="683d0-143">Run the sample across computers</span></span>

1. <span data-ttu-id="683d0-144">Hizmet programı dosyalarını dile özgü klasörün altındaki \service\bin\ klasöründen hizmet bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="683d0-144">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="683d0-145">İstemci program dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="683d0-145">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="683d0-146">Client. exe. config dosyasında, Ordersıraadı ' nı "." yerine hizmet bilgisayar adını belirtecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="683d0-146">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="683d0-147">Hizmet bilgisayarında, bir komut isteminden Service. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="683d0-147">On the service computer, launch Service.exe from a command prompt.</span></span>

5. <span data-ttu-id="683d0-148">İstemci bilgisayarda, bir komut isteminden Client. exe ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="683d0-148">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="683d0-149">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="683d0-149">The samples may already be installed on your computer.</span></span> <span data-ttu-id="683d0-150">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="683d0-150">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="683d0-151">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="683d0-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="683d0-152">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="683d0-152">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`

## <a name="see-also"></a><span data-ttu-id="683d0-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="683d0-153">See also</span></span>

- [<span data-ttu-id="683d0-154">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="683d0-154">Queues in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="683d0-155">Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="683d0-155">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- <span data-ttu-id="683d0-156">[Message Queuing](https://docs.microsoft.com/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="683d0-156">[Message Queuing](https://docs.microsoft.com/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span></span>
