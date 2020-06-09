---
title: İşlem Gerçekleştirilmiş MSMQ Bağlama
ms.date: 03/30/2017
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
ms.openlocfilehash: fa53099caba144f321698f180fe18f7614a1fa64
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596571"
---
# <a name="transacted-msmq-binding"></a><span data-ttu-id="23211-102">İşlem Gerçekleştirilmiş MSMQ Bağlama</span><span class="sxs-lookup"><span data-stu-id="23211-102">Transacted MSMQ Binding</span></span>

<span data-ttu-id="23211-103">Bu örnek, Message Queuing (MSMQ) kullanılarak işlenen sıraya alınmış iletişimin nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="23211-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ).</span></span>

> [!NOTE]
> <span data-ttu-id="23211-104">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="23211-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="23211-105">Sıraya alınmış iletişimde istemci, hizmet ile bir kuyruk kullanarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="23211-105">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="23211-106">Daha kesin olarak, istemci iletileri bir kuyruğa gönderir.</span><span class="sxs-lookup"><span data-stu-id="23211-106">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="23211-107">Hizmet kuyruktaki iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="23211-107">The service receives messages from the queue.</span></span> <span data-ttu-id="23211-108">Bu nedenle, hizmet ve istemcinin bir kuyruk kullanarak iletişim kurmak için aynı anda çalışması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="23211-108">The service and client, therefore, do not have to be running at the same time to communicate using a queue.</span></span>

<span data-ttu-id="23211-109">İletileri göndermek ve almak için işlemler kullanıldığında, aslında iki ayrı işlem vardır.</span><span class="sxs-lookup"><span data-stu-id="23211-109">When transactions are used to send and receive messages, there are actually two separate transactions.</span></span> <span data-ttu-id="23211-110">İstemci bir işlemin kapsamı içinde ileti gönderdiğinde, işlem istemciye ve istemci kuyruğu yöneticisine yereldir.</span><span class="sxs-lookup"><span data-stu-id="23211-110">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="23211-111">Hizmet, işlem kapsamındaki iletileri aldığında işlem, hizmete ve alma kuyruğu Yöneticisi 'ne yereldir.</span><span class="sxs-lookup"><span data-stu-id="23211-111">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="23211-112">İstemcinin ve hizmetin aynı işleme katılmadığından emin olmak çok önemlidir; Bunun yerine, kuyrukla birlikte işlemlerini gerçekleştirirken farklı işlemler (örneğin, gönder ve Al) kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="23211-112">It is very important to remember that the client and the service are not participating in the same transaction; rather, they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>

<span data-ttu-id="23211-113">Bu örnekte, istemci, bir işlemin kapsamı içinde hizmete bir toplu işlem iletisi gönderir.</span><span class="sxs-lookup"><span data-stu-id="23211-113">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="23211-114">Kuyruğa gönderilen iletiler daha sonra hizmet tarafından tanımlanan işlem kapsamı içinde hizmet tarafından alınır.</span><span class="sxs-lookup"><span data-stu-id="23211-114">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span>

<span data-ttu-id="23211-115">Hizmet sözleşmesi `IOrderProcessor` Aşağıdaki örnek kodda gösterildiği gibi olur.</span><span class="sxs-lookup"><span data-stu-id="23211-115">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span> <span data-ttu-id="23211-116">Arabirim, kuyruklarla kullanım için uygun olan tek yönlü bir hizmeti tanımlar.</span><span class="sxs-lookup"><span data-stu-id="23211-116">The interface defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

<span data-ttu-id="23211-117">Hizmet davranışı, olarak ayarlanmış bir işlem davranışını tanımlar `TransactionScopeRequired` `true` .</span><span class="sxs-lookup"><span data-stu-id="23211-117">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="23211-118">Bu, sıradan iletiyi almak için kullanılan aynı işlem kapsamının, yöntemi tarafından erişilen herhangi bir kaynak yöneticisi tarafından kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="23211-118">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="23211-119">Ayrıca Yöntem bir özel durum oluşturursa, iletinin kuyruğa döndürüldüğünden de garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="23211-119">It also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="23211-120">Bu işlem davranışını ayarlamadan, kuyruğa alınmış bir kanal iletiyi kuyruktan okumak için bir işlem oluşturur ve işlem başarısız olursa ileti kaybedildiğinden göndermeden önce otomatik olarak işleme konur.</span><span class="sxs-lookup"><span data-stu-id="23211-120">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before dispatch such that if the operation fails, the message is lost.</span></span> <span data-ttu-id="23211-121">En yaygın senaryo, aşağıdaki kodda gösterildiği gibi sıradan iletiyi okumak için kullanılan işlemde listeleme için hizmet işlemlerine yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="23211-121">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue, as demonstrated in the following code.</span></span>

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

<span data-ttu-id="23211-122">Hizmet kendi kendine barındırılır.</span><span class="sxs-lookup"><span data-stu-id="23211-122">The service is self hosted.</span></span> <span data-ttu-id="23211-123">MSMQ aktarımını kullanırken kullanılan kuyruğun önceden oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="23211-123">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="23211-124">Bu, el ile veya kod aracılığıyla yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="23211-124">This can be done manually or through code.</span></span> <span data-ttu-id="23211-125">Bu örnekte hizmet, sıranın varlığını denetlemek ve yoksa kuyruğu oluşturmak için kod içerir.</span><span class="sxs-lookup"><span data-stu-id="23211-125">In this sample, the service contains code to check for the existence of the queue and create the queue if it does not exist.</span></span> <span data-ttu-id="23211-126">Sıra adı yapılandırma dosyasından okundu.</span><span class="sxs-lookup"><span data-stu-id="23211-126">The queue name is read from the configuration file.</span></span> <span data-ttu-id="23211-127">Temel adres, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından hizmete proxy oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="23211-127">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>

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

<span data-ttu-id="23211-128">MSMQ kuyruğu adı, aşağıdaki örnek yapılandırmada gösterildiği gibi, yapılandırma dosyasının bir appSettings bölümünde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="23211-128">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />
</appSettings>
```

> [!NOTE]
> <span data-ttu-id="23211-129">Kuyruk adı, kullanarak kuyruğu oluştururken Yerel bilgisayar ve ters eğik çizgi ayırıcıları için bir nokta (.) kullanır <xref:System.Messaging> .</span><span class="sxs-lookup"><span data-stu-id="23211-129">The queue name uses a dot (.) for the local computer and backslash separators in its path when creating the queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="23211-130">Windows Communication Foundation (WCF) uç noktası, net. MSMQ şeması ile kuyruk adresini kullanır, yerel bilgisayarı belirtmek için "localhost" kullanır ve yolunda eğik çizgi kullanır.</span><span class="sxs-lookup"><span data-stu-id="23211-130">The Windows Communication Foundation (WCF) endpoint uses the queue address with net.msmq scheme, uses "localhost" to denote the local computer, and uses forward slashes in its path.</span></span>

<span data-ttu-id="23211-131">İstemci bir işlem kapsamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="23211-131">The client creates a transaction scope.</span></span> <span data-ttu-id="23211-132">Kuyrukla iletişim, işlemin kapsamı içinde gerçekleşirken, tüm iletilerin sıraya gönderildiği veya hiçbir iletinin sıraya gönderilmediği atomik bir birim olarak işlenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="23211-132">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="23211-133">İşlem, işlem kapsamında çağırarak yürütülür <xref:System.Transactions.TransactionScope.Complete%2A> .</span><span class="sxs-lookup"><span data-stu-id="23211-133">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>

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

<span data-ttu-id="23211-134">İşlemlerin çalıştığını doğrulamak için, aşağıdaki örnek kodda gösterildiği gibi işlem kapsamını inceleyerek istemciyi değiştirin, çözümü yeniden derleyin ve istemciyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="23211-134">To verify that transactions are working, modify the client by commenting the transaction scope as shown in the following sample code, rebuild the solution, and run the client.</span></span>

```csharp
//scope.Complete();
```

<span data-ttu-id="23211-135">İşlem tamamlanmadığı için iletiler kuyruğa gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="23211-135">Because the transaction is not completed, the messages are not sent to the queue.</span></span>

<span data-ttu-id="23211-136">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencereleri içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="23211-136">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="23211-137">Hizmetin istemciden ileti alacağını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23211-137">You can see the service receive messages from the client.</span></span> <span data-ttu-id="23211-138">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="23211-138">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="23211-139">Kuyruk kullanımda olduğu için istemci ve hizmetin aynı anda çalışmaya ve çalışır durumda olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="23211-139">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="23211-140">İstemcisini çalıştırabilir, kapatabilir ve ardından hizmeti başlatabilir ve iletileri almaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23211-140">You can run the client, shut it down, and then start up the service and it still receives the messages.</span></span>

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

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="23211-141">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="23211-141">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="23211-142">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="23211-142">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="23211-143">Önce hizmet çalıştırıldığında, sıranın mevcut olduğundan emin olmak için kontrol edilir.</span><span class="sxs-lookup"><span data-stu-id="23211-143">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="23211-144">Sıra yoksa, hizmet bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="23211-144">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="23211-145">Kuyruğu oluşturmak için önce hizmeti çalıştırabilir veya MSMQ kuyruğu Yöneticisi aracılığıyla bir tane oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23211-145">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="23211-146">Windows 2008 ' de bir sıra oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="23211-146">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="23211-147">Visual Studio 2012 ' de Sunucu Yöneticisi açın.</span><span class="sxs-lookup"><span data-stu-id="23211-147">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="23211-148">**Özellikler** sekmesini genişletin.</span><span class="sxs-lookup"><span data-stu-id="23211-148">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="23211-149">**Özel Ileti kuyrukları**' ne sağ tıklayıp **Yeni**, **özel kuyruk**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="23211-149">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="23211-150">**İşlem** kutusunu işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="23211-150">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="23211-151">`ServiceModelSamplesTransacted`Yeni kuyruğun adı olarak girin.</span><span class="sxs-lookup"><span data-stu-id="23211-151">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="23211-152">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="23211-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="23211-153">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="23211-153">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

<span data-ttu-id="23211-154">Varsayılan olarak, <xref:System.ServiceModel.NetMsmqBinding> taşıma güvenliği etkindir.</span><span class="sxs-lookup"><span data-stu-id="23211-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="23211-155">MSMQ taşıma güvenliği için iki ilgili özellik vardır <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ve <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> .</span><span class="sxs-lookup"><span data-stu-id="23211-155">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span></span> <span data-ttu-id="23211-156">Varsayılan olarak, kimlik doğrulama modu olarak ayarlanır `Windows` ve koruma düzeyi olarak ayarlanır `Sign` .</span><span class="sxs-lookup"><span data-stu-id="23211-156">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="23211-157">MSMQ için kimlik doğrulama ve imzalama özelliğini sağlamak üzere, bir etki alanının parçası olması ve MSMQ için Active Directory tümleştirme seçeneğinin yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="23211-157">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the Active Directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="23211-158">Bu örneği bu ölçütlere uygun olmayan bir bilgisayarda çalıştırırsanız bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="23211-158">If you run this sample on a computer that does not satisfy these criteria, you receive an error.</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="23211-159">Örneği bir çalışma grubuna katılmış veya Active Directory tümleştirme olmadan bir bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="23211-159">To run the sample on a computer joined to a workgroup or without Active Directory integration</span></span>

1. <span data-ttu-id="23211-160">Bilgisayarınız bir etki alanının parçası değilse veya Active Directory tümleştirme yüklü değilse, `None` Aşağıdaki örnek yapılandırma kodunda gösterildiği gibi olarak kimlik doğrulama modu ve koruma düzeyini ayarlayarak aktarım güvenliğini kapatın.</span><span class="sxs-lookup"><span data-stu-id="23211-160">If your computer is not part of a domain or does not have Active Directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code.</span></span>

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

2. <span data-ttu-id="23211-161">Örneği çalıştırmadan önce hem sunucu hem de istemci üzerinde yapılandırmayı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="23211-161">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="23211-162">Ayarı `security mode` `None` <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> , <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> ve güvenlik ayarlarına eşdeğerdir `Message` `None` .</span><span class="sxs-lookup"><span data-stu-id="23211-162">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="23211-163">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="23211-163">The samples may already be installed on your computer.</span></span> <span data-ttu-id="23211-164">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="23211-164">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="23211-165">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="23211-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="23211-166">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="23211-166">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`
