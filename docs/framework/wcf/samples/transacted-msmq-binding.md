---
description: 'Daha fazla bilgi edinin: Işlem temelli MSMQ bağlama'
title: İşlem Gerçekleştirilmiş MSMQ Bağlama
ms.date: 03/30/2017
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
ms.openlocfilehash: 17fdcdb169c9e57c1a95d5aea4c79654e3739664
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668539"
---
# <a name="transacted-msmq-binding"></a><span data-ttu-id="91e13-103">İşlem Gerçekleştirilmiş MSMQ Bağlama</span><span class="sxs-lookup"><span data-stu-id="91e13-103">Transacted MSMQ Binding</span></span>

<span data-ttu-id="91e13-104">Bu örnek, Message Queuing (MSMQ) kullanılarak işlenen sıraya alınmış iletişimin nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="91e13-104">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ).</span></span>

> [!NOTE]
> <span data-ttu-id="91e13-105">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="91e13-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="91e13-106">Sıraya alınmış iletişimde istemci, hizmet ile bir kuyruk kullanarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="91e13-106">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="91e13-107">Daha kesin olarak, istemci iletileri bir kuyruğa gönderir.</span><span class="sxs-lookup"><span data-stu-id="91e13-107">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="91e13-108">Hizmet kuyruktaki iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="91e13-108">The service receives messages from the queue.</span></span> <span data-ttu-id="91e13-109">Bu nedenle, hizmet ve istemcinin bir kuyruk kullanarak iletişim kurmak için aynı anda çalışması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="91e13-109">The service and client, therefore, do not have to be running at the same time to communicate using a queue.</span></span>

<span data-ttu-id="91e13-110">İletileri göndermek ve almak için işlemler kullanıldığında, aslında iki ayrı işlem vardır.</span><span class="sxs-lookup"><span data-stu-id="91e13-110">When transactions are used to send and receive messages, there are actually two separate transactions.</span></span> <span data-ttu-id="91e13-111">İstemci bir işlemin kapsamı içinde ileti gönderdiğinde, işlem istemciye ve istemci kuyruğu yöneticisine yereldir.</span><span class="sxs-lookup"><span data-stu-id="91e13-111">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="91e13-112">Hizmet, işlem kapsamındaki iletileri aldığında işlem, hizmete ve alma kuyruğu Yöneticisi 'ne yereldir.</span><span class="sxs-lookup"><span data-stu-id="91e13-112">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="91e13-113">İstemcinin ve hizmetin aynı işleme katılmadığından emin olmak çok önemlidir; Bunun yerine, kuyrukla birlikte işlemlerini gerçekleştirirken farklı işlemler (örneğin, gönder ve Al) kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="91e13-113">It is very important to remember that the client and the service are not participating in the same transaction; rather, they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>

<span data-ttu-id="91e13-114">Bu örnekte, istemci, bir işlemin kapsamı içinde hizmete bir toplu işlem iletisi gönderir.</span><span class="sxs-lookup"><span data-stu-id="91e13-114">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="91e13-115">Kuyruğa gönderilen iletiler daha sonra hizmet tarafından tanımlanan işlem kapsamı içinde hizmet tarafından alınır.</span><span class="sxs-lookup"><span data-stu-id="91e13-115">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span>

<span data-ttu-id="91e13-116">Hizmet sözleşmesi `IOrderProcessor` Aşağıdaki örnek kodda gösterildiği gibi olur.</span><span class="sxs-lookup"><span data-stu-id="91e13-116">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span> <span data-ttu-id="91e13-117">Arabirim, kuyruklarla kullanım için uygun olan tek yönlü bir hizmeti tanımlar.</span><span class="sxs-lookup"><span data-stu-id="91e13-117">The interface defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

<span data-ttu-id="91e13-118">Hizmet davranışı, olarak ayarlanmış bir işlem davranışını tanımlar `TransactionScopeRequired` `true` .</span><span class="sxs-lookup"><span data-stu-id="91e13-118">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="91e13-119">Bu, sıradan iletiyi almak için kullanılan aynı işlem kapsamının, yöntemi tarafından erişilen herhangi bir kaynak yöneticisi tarafından kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="91e13-119">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="91e13-120">Ayrıca Yöntem bir özel durum oluşturursa, iletinin kuyruğa döndürüldüğünden de garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="91e13-120">It also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="91e13-121">Bu işlem davranışını ayarlamadan, kuyruğa alınmış bir kanal iletiyi kuyruktan okumak için bir işlem oluşturur ve işlem başarısız olursa ileti kaybedildiğinden göndermeden önce otomatik olarak işleme konur.</span><span class="sxs-lookup"><span data-stu-id="91e13-121">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before dispatch such that if the operation fails, the message is lost.</span></span> <span data-ttu-id="91e13-122">En yaygın senaryo, aşağıdaki kodda gösterildiği gibi sıradan iletiyi okumak için kullanılan işlemde listeleme için hizmet işlemlerine yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="91e13-122">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue, as demonstrated in the following code.</span></span>

```csharp
 // This service class that implements the service contract.
 // This added code writes output to the console window.
 public class OrderProcessorService : IOrderProcessor
 {
     [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
     public void SubmitPurchaseOrder(PurchaseOrder po)
     {
         Orders.Add(po);
         Console.WriteLine("Processing {0} ", po);
     }
  …
}
```

<span data-ttu-id="91e13-123">Hizmet kendi kendine barındırılır.</span><span class="sxs-lookup"><span data-stu-id="91e13-123">The service is self hosted.</span></span> <span data-ttu-id="91e13-124">MSMQ aktarımını kullanırken kullanılan kuyruğun önceden oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="91e13-124">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="91e13-125">Bu, el ile veya kod aracılığıyla yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="91e13-125">This can be done manually or through code.</span></span> <span data-ttu-id="91e13-126">Bu örnekte hizmet, sıranın varlığını denetlemek ve yoksa kuyruğu oluşturmak için kod içerir.</span><span class="sxs-lookup"><span data-stu-id="91e13-126">In this sample, the service contains code to check for the existence of the queue and create the queue if it does not exist.</span></span> <span data-ttu-id="91e13-127">Sıra adı yapılandırma dosyasından okundu.</span><span class="sxs-lookup"><span data-stu-id="91e13-127">The queue name is read from the configuration file.</span></span> <span data-ttu-id="91e13-128">Temel adres, [ServiceModel meta veri yardımcı programı Aracı (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından hizmete proxy 'yi oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="91e13-128">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>

```csharp
// Host the service within this EXE console application.
public static void Main()
{
    // Get the MSMQ queue name from appSettings in configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];

    // Create the transacted MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName, true);

    // Create a ServiceHost for the OrderProcessorService type.
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
    {
        // Open the ServiceHost to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHost to shut down the service.
        serviceHost.Close();
    }
}
```

<span data-ttu-id="91e13-129">MSMQ kuyruğu adı, aşağıdaki örnek yapılandırmada gösterildiği gibi, yapılandırma dosyasının bir appSettings bölümünde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="91e13-129">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />
</appSettings>
```

> [!NOTE]
> <span data-ttu-id="91e13-130">Kuyruk adı, kullanarak kuyruğu oluştururken Yerel bilgisayar ve ters eğik çizgi ayırıcıları için bir nokta (.) kullanır <xref:System.Messaging> .</span><span class="sxs-lookup"><span data-stu-id="91e13-130">The queue name uses a dot (.) for the local computer and backslash separators in its path when creating the queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="91e13-131">Windows Communication Foundation (WCF) uç noktası, net. MSMQ şeması ile kuyruk adresini kullanır, yerel bilgisayarı belirtmek için "localhost" kullanır ve yolunda eğik çizgi kullanır.</span><span class="sxs-lookup"><span data-stu-id="91e13-131">The Windows Communication Foundation (WCF) endpoint uses the queue address with net.msmq scheme, uses "localhost" to denote the local computer, and uses forward slashes in its path.</span></span>

<span data-ttu-id="91e13-132">İstemci bir işlem kapsamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="91e13-132">The client creates a transaction scope.</span></span> <span data-ttu-id="91e13-133">Kuyrukla iletişim, işlemin kapsamı içinde gerçekleşirken, tüm iletilerin sıraya gönderildiği veya hiçbir iletinin sıraya gönderilmediği atomik bir birim olarak işlenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="91e13-133">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="91e13-134">İşlem, işlem kapsamında çağırarak yürütülür <xref:System.Transactions.TransactionScope.Complete%2A> .</span><span class="sxs-lookup"><span data-stu-id="91e13-134">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>

```csharp
// Create a client.
OrderProcessorClient client = new OrderProcessorClient();

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

// Create a transaction scope.
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
{
    // Make a queued call to submit the purchase order.
    client.SubmitPurchaseOrder(po);
    // Complete the transaction.
    scope.Complete();
}

// Closing the client gracefully closes the connection and cleans up resources.
client.Close();

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

<span data-ttu-id="91e13-135">İşlemlerin çalıştığını doğrulamak için, aşağıdaki örnek kodda gösterildiği gibi işlem kapsamını inceleyerek istemciyi değiştirin, çözümü yeniden derleyin ve istemciyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="91e13-135">To verify that transactions are working, modify the client by commenting the transaction scope as shown in the following sample code, rebuild the solution, and run the client.</span></span>

```csharp
//scope.Complete();
```

<span data-ttu-id="91e13-136">İşlem tamamlanmadığı için iletiler kuyruğa gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="91e13-136">Because the transaction is not completed, the messages are not sent to the queue.</span></span>

<span data-ttu-id="91e13-137">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencereleri içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="91e13-137">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="91e13-138">Hizmetin istemciden ileti alacağını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91e13-138">You can see the service receive messages from the client.</span></span> <span data-ttu-id="91e13-139">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="91e13-139">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="91e13-140">Kuyruk kullanımda olduğu için istemci ve hizmetin aynı anda çalışmaya ve çalışır durumda olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="91e13-140">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="91e13-141">İstemcisini çalıştırabilir, kapatabilir ve ardından hizmeti başlatabilir ve iletileri almaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91e13-141">You can run the client, shut it down, and then start up the service and it still receives the messages.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 7b31ce51-ae7c-4def-9b8b-617e4288eafd
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="91e13-142">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="91e13-142">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="91e13-143">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="91e13-143">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="91e13-144">Önce hizmet çalıştırıldığında, sıranın mevcut olduğundan emin olmak için kontrol edilir.</span><span class="sxs-lookup"><span data-stu-id="91e13-144">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="91e13-145">Sıra yoksa, hizmet bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="91e13-145">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="91e13-146">Kuyruğu oluşturmak için önce hizmeti çalıştırabilir veya MSMQ kuyruğu Yöneticisi aracılığıyla bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91e13-146">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="91e13-147">Windows 2008 ' de bir sıra oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="91e13-147">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="91e13-148">Visual Studio 2012 ' de Sunucu Yöneticisi açın.</span><span class="sxs-lookup"><span data-stu-id="91e13-148">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="91e13-149">**Özellikler** sekmesini genişletin.</span><span class="sxs-lookup"><span data-stu-id="91e13-149">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="91e13-150">**Özel Ileti kuyrukları**' ne sağ tıklayıp **Yeni**, **özel kuyruk**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="91e13-150">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="91e13-151">**İşlem** kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="91e13-151">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="91e13-152">`ServiceModelSamplesTransacted`Yeni kuyruğun adı olarak girin.</span><span class="sxs-lookup"><span data-stu-id="91e13-152">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="91e13-153">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="91e13-153">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="91e13-154">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="91e13-154">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

<span data-ttu-id="91e13-155">Varsayılan olarak, <xref:System.ServiceModel.NetMsmqBinding> taşıma güvenliği etkindir.</span><span class="sxs-lookup"><span data-stu-id="91e13-155">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="91e13-156">MSMQ taşıma güvenliği için iki ilgili özellik vardır <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ve <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> .</span><span class="sxs-lookup"><span data-stu-id="91e13-156">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span></span> <span data-ttu-id="91e13-157">Varsayılan olarak, kimlik doğrulama modu olarak ayarlanır `Windows` ve koruma düzeyi olarak ayarlanır `Sign` .</span><span class="sxs-lookup"><span data-stu-id="91e13-157">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="91e13-158">MSMQ için kimlik doğrulama ve imzalama özelliğini sağlamak üzere, bir etki alanının parçası olması ve MSMQ için Active Directory tümleştirme seçeneğinin yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="91e13-158">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the Active Directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="91e13-159">Bu örneği bu ölçütlere uygun olmayan bir bilgisayarda çalıştırırsanız bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="91e13-159">If you run this sample on a computer that does not satisfy these criteria, you receive an error.</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="91e13-160">Örneği bir çalışma grubuna katılmış veya Active Directory tümleştirme olmadan bir bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="91e13-160">To run the sample on a computer joined to a workgroup or without Active Directory integration</span></span>

1. <span data-ttu-id="91e13-161">Bilgisayarınız bir etki alanının parçası değilse veya Active Directory tümleştirme yüklü değilse, `None` Aşağıdaki örnek yapılandırma kodunda gösterildiği gibi olarak kimlik doğrulama modu ve koruma düzeyini ayarlayarak aktarım güvenliğini kapatın.</span><span class="sxs-lookup"><span data-stu-id="91e13-161">If your computer is not part of a domain or does not have Active Directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code.</span></span>

    ```xml
    <system.serviceModel>
      <services>
        <service name="Microsoft.ServiceModel.Samples.OrderProcessorService"
                 behaviorConfiguration="OrderProcessorServiceBehavior">
          <host>
            <baseAddresses>
              <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
            </baseAddresses>
          </host>
          <!-- Define NetMsmqEndpoint. -->
          <endpoint
              address="net.msmq://localhost/private/ServiceModelSamplesTransacted"
              binding="netMsmqBinding"
              bindingConfiguration="Binding1"
           contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
          <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
          <endpoint address="mex"
                    binding="mexHttpBinding"
                    contract="IMetadataExchange" />
        </service>
      </services>

      <bindings>
        <netMsmqBinding>
          <binding name="Binding1">
            <security mode="None" />
          </binding>
        </netMsmqBinding>
      </bindings>

        <behaviors>
          <serviceBehaviors>
            <behavior name="OrderProcessorServiceBehavior">
              <serviceMetadata httpGetEnabled="True"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>

      </system.serviceModel>
    ```

2. <span data-ttu-id="91e13-162">Örneği çalıştırmadan önce hem sunucu hem de istemci üzerinde yapılandırmayı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="91e13-162">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="91e13-163">Ayarı `security mode` `None` <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> , <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> ve güvenlik ayarlarına eşdeğerdir `Message` `None` .</span><span class="sxs-lookup"><span data-stu-id="91e13-163">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="91e13-164">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="91e13-164">The samples may already be installed on your computer.</span></span> <span data-ttu-id="91e13-165">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="91e13-165">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="91e13-166">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="91e13-166">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="91e13-167">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="91e13-167">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`
