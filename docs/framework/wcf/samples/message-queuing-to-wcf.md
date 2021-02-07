---
description: 'Hakkında daha fazla bilgi edinin: Windows Communication Foundation Message Queuing'
title: Windows Communication Foundation'a İleti Kuyruğa Alma
ms.date: 03/30/2017
ms.assetid: 6d718eb0-9f61-4653-8a75-d2dac8fb3520
ms.openlocfilehash: 53c535379584bcb8fa50d1b550f87ea7acc15175
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704010"
---
# <a name="message-queuing-to-windows-communication-foundation"></a><span data-ttu-id="15a88-103">Windows Communication Foundation'a İleti Kuyruğa Alma</span><span class="sxs-lookup"><span data-stu-id="15a88-103">Message Queuing to Windows Communication Foundation</span></span>

<span data-ttu-id="15a88-104">Bu örnek, bir Message Queuing (MSMQ) uygulamasının bir Windows Communication Foundation (WCF) hizmetine nasıl MSMQ iletisi gönderebileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="15a88-104">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="15a88-105">Hizmet, sıraya alınan iletileri alma hizmetini gözlemlemeye olanak sağlayan, kendinden konak bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="15a88-105">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="15a88-106">Hizmet sözleşmesi, `IOrderProcessor` kuyruklarla birlikte kullanılmak üzere uygun tek yönlü bir hizmeti tanımlar.</span><span class="sxs-lookup"><span data-stu-id="15a88-106">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="15a88-107">Bir MSMQ iletisinde eylem üst bilgisi yok, bu nedenle farklı MSMQ iletilerini işlem sözleşmelerine otomatik olarak eşlemek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="15a88-107">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="15a88-108">Bu nedenle, yalnızca bir işlem sözleşmesi olabilir.</span><span class="sxs-lookup"><span data-stu-id="15a88-108">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="15a88-109">Hizmet için birden fazla işlem sözleşmesi tanımlamak istiyorsanız, uygulamanın hangi işlem sözleşmesinin gönderileceğine karar vermek için MSMQ iletisindeki (örneğin, etiket veya correlationID) hangi üstbilginin kullanılabileceğini belirlemek üzere bilgi sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="15a88-109">If you want to define more than one operation contract for the service, the application must provide information as to which header in the MSMQ message (for example, the label or correlationID) can be used to decide which operation contract to dispatch.</span></span>

 <span data-ttu-id="15a88-110">MSMQ iletisi, hangi üst bilgilerin işlem sözleşmesinin farklı parametreleriyle eşlendiği bilgisini içermez.</span><span class="sxs-lookup"><span data-stu-id="15a88-110">The MSMQ message does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="15a88-111">Parametresi <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> `MsmqMessage<T>` , temeldeki MSMQ iletisini içeren türündedir ().</span><span class="sxs-lookup"><span data-stu-id="15a88-111">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`), which contains the underlying MSMQ message.</span></span> <span data-ttu-id="15a88-112">() Sınıfındaki "T" türü <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> , `MsmqMessage<T>` MSMQ ileti gövdesinde seri hale getirilen verileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="15a88-112">The type "T" in the <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>(`MsmqMessage<T>`) class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="15a88-113">Bu örnekte, `PurchaseOrder` tür MSMQ ileti gövdesinde serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="15a88-113">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>

 <span data-ttu-id="15a88-114">Aşağıdaki örnek kod, sipariş işleme hizmetinin hizmet sözleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="15a88-114">The following sample code shows the service contract of the order processing service.</span></span>

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

 <span data-ttu-id="15a88-115">Hizmet kendi kendine barındırılır.</span><span class="sxs-lookup"><span data-stu-id="15a88-115">The service is self hosted.</span></span> <span data-ttu-id="15a88-116">MSMQ kullanılırken kullanılan kuyruğun önceden oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="15a88-116">When using MSMQ, the queue used must be created in advance.</span></span> <span data-ttu-id="15a88-117">Bu, el ile veya kod aracılığıyla yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="15a88-117">This can be done manually or through code.</span></span> <span data-ttu-id="15a88-118">Bu örnekte hizmet, sıranın varlığını denetler ve gerekirse oluşturur.</span><span class="sxs-lookup"><span data-stu-id="15a88-118">In this sample, the service checks for the existence of the queue and creates it if required.</span></span> <span data-ttu-id="15a88-119">Sıra adı yapılandırma dosyasından okundu.</span><span class="sxs-lookup"><span data-stu-id="15a88-119">The queue name is read from the configuration file.</span></span>

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

 <span data-ttu-id="15a88-120">Hizmeti, <xref:System.ServiceModel.ServiceHost> `OrderProcessorService` Aşağıdaki örnek kodda gösterildiği gibi, için bir için oluşturur ve açar.</span><span class="sxs-lookup"><span data-stu-id="15a88-120">The service creates and opens a <xref:System.ServiceModel.ServiceHost> for the `OrderProcessorService`, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="15a88-121">MSMQ kuyruğu adı, aşağıdaki örnek yapılandırmada gösterildiği gibi, yapılandırma dosyasının bir appSettings bölümünde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="15a88-121">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="15a88-122">Sıra adı, yerel bilgisayar için bir nokta (.) ve kendi yolunda ters eğik çizgi ayırıcılar kullanır.</span><span class="sxs-lookup"><span data-stu-id="15a88-122">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="15a88-123">WCF uç noktası adresi bir MSMQ. formatname şemasını belirtir ve yerel bilgisayar için localhost kullanır.</span><span class="sxs-lookup"><span data-stu-id="15a88-123">The WCF endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="15a88-124">Her MSMQ Format adı adresleme Kılavuzu için kuyruğun adresi MSMQ. formatname düzenini izler.</span><span class="sxs-lookup"><span data-stu-id="15a88-124">The address of the queue for each MSMQ Format Name addressing guidelines follows the msmq.formatname scheme.</span></span>

```xml
<appSettings>
    <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="15a88-125">İstemci uygulaması, <xref:System.Messaging.MessageQueue.Send%2A> Aşağıdaki örnek kodda gösterildiği gibi, sıraya dayanıklı ve işlemsel bir ileti göndermek için yöntemini kullanan BIR MSMQ uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="15a88-125">The client application is an MSMQ application that uses the <xref:System.Messaging.MessageQueue.Send%2A> method to send a durable and transactional message to the queue, as shown in the following sample code.</span></span>

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

 <span data-ttu-id="15a88-126">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencereleri içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="15a88-126">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="15a88-127">Hizmetin istemciden ileti alacağını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15a88-127">You can see the service receive messages from the client.</span></span> <span data-ttu-id="15a88-128">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="15a88-128">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="15a88-129">Kuyruk kullanımda olduğu için istemci ve hizmetin aynı anda çalışmaya ve çalışır durumda olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="15a88-129">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="15a88-130">Örneğin, istemcisini çalıştırabilir, kapatabilir ve ardından hizmeti başlatabilir ve yine de iletilerini alabilir.</span><span class="sxs-lookup"><span data-stu-id="15a88-130">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="15a88-131">Örneği kurma, oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="15a88-131">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="15a88-132">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="15a88-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="15a88-133">Önce hizmet çalıştırıldığında, sıranın mevcut olduğundan emin olmak için kontrol edilir.</span><span class="sxs-lookup"><span data-stu-id="15a88-133">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="15a88-134">Sıra yoksa, hizmet bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="15a88-134">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="15a88-135">Kuyruğu oluşturmak için önce hizmeti çalıştırabilir veya MSMQ kuyruğu Yöneticisi aracılığıyla bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15a88-135">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="15a88-136">Windows 2008 ' de bir sıra oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="15a88-136">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="15a88-137">Visual Studio 2012 ' de Sunucu Yöneticisi açın.</span><span class="sxs-lookup"><span data-stu-id="15a88-137">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="15a88-138">**Özellikler** sekmesini genişletin.</span><span class="sxs-lookup"><span data-stu-id="15a88-138">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="15a88-139">**Özel Ileti kuyrukları**' ne sağ tıklayıp **Yeni**, **özel kuyruk**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="15a88-139">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="15a88-140">**İşlem** kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="15a88-140">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="15a88-141">`ServiceModelSamplesTransacted`Yeni kuyruğun adı olarak girin.</span><span class="sxs-lookup"><span data-stu-id="15a88-141">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="15a88-142">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="15a88-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="15a88-143">Örneği tek bilgisayarlı bir yapılandırmada çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="15a88-143">To run the sample in a single- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="run-the-sample-across-computers"></a><span data-ttu-id="15a88-144">Örneği bilgisayarlar arasında çalıştırma</span><span class="sxs-lookup"><span data-stu-id="15a88-144">Run the sample across computers</span></span>

1. <span data-ttu-id="15a88-145">Hizmet programı dosyalarını dile özgü klasörün altındaki \service\bin\ klasöründen hizmet bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="15a88-145">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="15a88-146">İstemci program dosyalarını dile özgü klasörün altındaki \client\bin\ klasöründen istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="15a88-146">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="15a88-147">Client.exe.config dosyasında, Ordersıraadı ' nı "." yerine hizmet bilgisayar adını belirtecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="15a88-147">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="15a88-148">Hizmet bilgisayarında, bir komut isteminden Service.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="15a88-148">On the service computer, launch Service.exe from a command prompt.</span></span>

5. <span data-ttu-id="15a88-149">İstemci bilgisayarda, bir komut isteminden Client.exe başlatın.</span><span class="sxs-lookup"><span data-stu-id="15a88-149">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="15a88-150">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="15a88-150">The samples may already be installed on your computer.</span></span> <span data-ttu-id="15a88-151">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="15a88-151">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="15a88-152">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="15a88-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="15a88-153">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="15a88-153">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MsmqToWcf`

## <a name="see-also"></a><span data-ttu-id="15a88-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15a88-154">See also</span></span>

- [<span data-ttu-id="15a88-155">WCF'de Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="15a88-155">Queues in WCF</span></span>](../feature-details/queues-in-wcf.md)
- [<span data-ttu-id="15a88-156">Nasıl yapılır: WCF Uç Noktaları ve İleti Kuyruğa Alma Uygulamaları ile İleti Alma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="15a88-156">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- <span data-ttu-id="15a88-157">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="15a88-157">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span></span>
