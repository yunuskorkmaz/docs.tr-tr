---
title: "İşlem Gerçekleştirilmiş MSMQ Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
caps.latest.revision: "50"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fd656bed608811a5a04a47849bf915f708a62a9d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="transacted-msmq-binding"></a><span data-ttu-id="06f01-102">İşlem Gerçekleştirilmiş MSMQ Bağlama</span><span class="sxs-lookup"><span data-stu-id="06f01-102">Transacted MSMQ Binding</span></span>
<span data-ttu-id="06f01-103">Bu örnek, Message Queuing (MSMQ) kullanarak hizmetteki kuyruğa alınan iletişim gerçekleştirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="06f01-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06f01-104">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="06f01-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="06f01-105">Kuyruğa alınan iletişim, istemci bir sıra kullanarak hizmeti ile iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="06f01-105">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="06f01-106">Daha hassas bir şekilde istemci kuyruğa ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="06f01-106">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="06f01-107">Hizmet kuyruktan iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="06f01-107">The service receives messages from the queue.</span></span> <span data-ttu-id="06f01-108">Hizmet ve istemci, bu nedenle, bir sıra kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="06f01-108">The service and client, therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="06f01-109">İleti gönderme ve alma için işlemleri kullanıldığında aslında iki ayrı işlemler vardır.</span><span class="sxs-lookup"><span data-stu-id="06f01-109">When transactions are used to send and receive messages, there are actually two separate transactions.</span></span> <span data-ttu-id="06f01-110">İstemci bir işlem kapsamı içinde iletileri gönderdiğinde, istemci ve istemci sıra yöneticisi yerel bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="06f01-110">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="06f01-111">Hizmet işlem kapsamı içinde ileti aldığında, hizmet ve alıcı sıra yöneticisi yerel bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="06f01-111">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="06f01-112">İstemci ve hizmet aynı işlemde yer almayan olduğunu unutmamak önemlidir; Bunun yerine, farklı işlemler işlemlerini (örneğin gönderme ve alma gibi) sıra ile gerçekleştirirken kullanıyordur.</span><span class="sxs-lookup"><span data-stu-id="06f01-112">It is very important to remember that the client and the service are not participating in the same transaction; rather, they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>  
  
 <span data-ttu-id="06f01-113">Bu örnekte, istemci bir işlem kapsamı içinde hizmetinden toplu iletiler gönderir.</span><span class="sxs-lookup"><span data-stu-id="06f01-113">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="06f01-114">Bu sıraya gönderilen iletileri sonra hizmet hizmet tarafından tanımlanan işlem kapsamı içinde tarafından alınır.</span><span class="sxs-lookup"><span data-stu-id="06f01-114">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span>  
  
 <span data-ttu-id="06f01-115">Hizmet sözleşme `IOrderProcessor`, aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="06f01-115">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span> <span data-ttu-id="06f01-116">Sıralar ile kullanım için uygun bir tek yönlü hizmet arabirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="06f01-116">The interface defines a one-way service that is suitable for use with queues.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```  
  
 <span data-ttu-id="06f01-117">Bir işlemi davranışı ile hizmet davranışını tanımlayan `TransactionScopeRequired` kümesine `true`.</span><span class="sxs-lookup"><span data-stu-id="06f01-117">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="06f01-118">Bu yöntem tarafından erişilen tüm kaynak yöneticileri kuyruktan ileti almak için kullanılan aynı işlem kapsamı kullandığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="06f01-118">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="06f01-119">Ayrıca, yöntemi bir özel durum oluşturursa ileti kuyruğuna döndürülür garanti eder.</span><span class="sxs-lookup"><span data-stu-id="06f01-119">It also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="06f01-120">Bu işlemi davranışı ayarı olmadan sıraya alınmış bir kanal iletiyi sıradan okumak için bir işlem oluşturur ve işlem başarısız olursa, ileti kaybolur şekilde, otomatik olarak gönderme önce kaydeder.</span><span class="sxs-lookup"><span data-stu-id="06f01-120">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before dispatch such that if the operation fails, the message is lost.</span></span> <span data-ttu-id="06f01-121">Aşağıdaki kodda gösterildiği gibi sıradan ileti okumak için kullanılır işlemdeki listeleme hizmet işlemleri için en yaygın senaryodur bakın.</span><span class="sxs-lookup"><span data-stu-id="06f01-121">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue, as demonstrated in the following code.</span></span>  
  
```  
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
  
 <span data-ttu-id="06f01-122">Kendi kendini barındırılan hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="06f01-122">The service is self hosted.</span></span> <span data-ttu-id="06f01-123">MSMQ taşıma kullanırken, sıranın kullanılan önceden oluşturulmuş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="06f01-123">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="06f01-124">Bu, el ile veya kod aracılığıyla yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="06f01-124">This can be done manually or through code.</span></span> <span data-ttu-id="06f01-125">Bu örnekte, hizmet sırası varlığını denetlemek ve henüz yoksa sırayı oluşturmak için kod içerir.</span><span class="sxs-lookup"><span data-stu-id="06f01-125">In this sample, the service contains code to check for the existence of the queue and create the queue if it does not exist.</span></span> <span data-ttu-id="06f01-126">Kuyruk adı yapılandırma dosyasından okunur.</span><span class="sxs-lookup"><span data-stu-id="06f01-126">The queue name is read from the configuration file.</span></span> <span data-ttu-id="06f01-127">Temel adres tarafından kullanılan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proxy hizmeti oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="06f01-127">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  
  
```  
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
  
 <span data-ttu-id="06f01-128">MSMQ kuyruk adı, aşağıdaki örnek yapılandırmada gösterildiği gibi bir yapılandırma dosyasının appSettings bölümünde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="06f01-128">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>  
  
```xml  
<appSettings>  
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />  
</appSettings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="06f01-129">Kuyruk adı bir nokta (.) yolundaki ters eğik çizgi ayırıcılar ve yerel bilgisayar için sıra kullanarak oluştururken kullandığı <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="06f01-129">The queue name uses a dot (.) for the local computer and backslash separators in its path when creating the queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="06f01-130">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Uç nokta sıra adresini kullanır yerel bilgisayarı belirtmek için "localhost" net.msmq şeması ile kullanır ve kullandığı yolundaki eğik.</span><span class="sxs-lookup"><span data-stu-id="06f01-130">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] endpoint uses the queue address with net.msmq scheme, uses "localhost" to denote the local computer, and uses forward slashes in its path.</span></span>  
  
 <span data-ttu-id="06f01-131">İstemci bir işlem kapsamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="06f01-131">The client creates a transaction scope.</span></span> <span data-ttu-id="06f01-132">Sıra ile iletişim, bu sıraya gönderilen tüm iletileri veya hiçbiri iletileri kuyruğa gönderilen olduğu atomik bir birim olarak kabul edilmesi neden işlem kapsamı içinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="06f01-132">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="06f01-133">İşlem çağırarak gerçekleştirilir <xref:System.Transactions.TransactionScope.Complete%2A> işlem kapsamında.</span><span class="sxs-lookup"><span data-stu-id="06f01-133">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>  
  
```  
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
  
 <span data-ttu-id="06f01-134">İşlemler çalıştığını doğrulamak için aşağıdaki örnek kodda gösterildiği gibi işlem kapsamı yorum istemci değiştirmek, çözümü yeniden derleyin ve istemci çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="06f01-134">To verify that transactions are working, modify the client by commenting the transaction scope as shown in the following sample code, rebuild the solution, and run the client.</span></span>  
  
```  
//scope.Complete();  
```  
  
 <span data-ttu-id="06f01-135">İşlem tamamlanmamış olduğundan, iletileri kuyruğa gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="06f01-135">Because the transaction is not completed, the messages are not sent to the queue.</span></span>  
  
 <span data-ttu-id="06f01-136">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="06f01-136">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="06f01-137">İstemci hizmeti alma iletileri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06f01-137">You can see the service receive messages from the client.</span></span> <span data-ttu-id="06f01-138">Her konsol penceresinde hizmet ve istemci kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="06f01-138">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="06f01-139">Queuing kullanımda olduğundan, istemci ve hizmet aynı anda açık ve çalışıyor olması sahip olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="06f01-139">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="06f01-140">İstemcisini çalıştıran, kapatmak ve hizmeti başlatın ve hala iletilerini alır.</span><span class="sxs-lookup"><span data-stu-id="06f01-140">You can run the client, shut it down, and then start up the service and it still receives the messages.</span></span>  
  
```  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="06f01-141">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="06f01-141">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="06f01-142">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="06f01-142">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="06f01-143">Hizmetin ilk olarak çalışıyorsa, sıranın var olduğundan emin olmak için kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="06f01-143">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="06f01-144">Hizmet sırası mevcut değilse oluşturur.</span><span class="sxs-lookup"><span data-stu-id="06f01-144">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="06f01-145">İlk sırayı oluşturmak için hizmet çalıştırabilirsiniz veya bir MSMQ sıra Yöneticisi aracılığıyla oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06f01-145">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="06f01-146">Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="06f01-146">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="06f01-147">Sunucu Yöneticisi'nde açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06f01-147">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="06f01-148">Genişletme **özellikleri** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="06f01-148">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="06f01-149">Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.</span><span class="sxs-lookup"><span data-stu-id="06f01-149">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="06f01-150">Denetleme **işlem** kutusu.</span><span class="sxs-lookup"><span data-stu-id="06f01-150">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="06f01-151">Girin `ServiceModelSamplesTransacted` yeni kuyruk adından farklı.</span><span class="sxs-lookup"><span data-stu-id="06f01-151">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="06f01-152">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="06f01-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="06f01-153">Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="06f01-153">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="06f01-154">Varsayılan olarak <xref:System.ServiceModel.NetMsmqBinding>, taşıma güvenliği etkindir.</span><span class="sxs-lookup"><span data-stu-id="06f01-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="06f01-155">MSMQ taşıma güvenliği için iki ilgili özellikler yok <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ve <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span><span class="sxs-lookup"><span data-stu-id="06f01-155">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span></span> <span data-ttu-id="06f01-156">Varsayılan olarak, kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`.</span><span class="sxs-lookup"><span data-stu-id="06f01-156">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="06f01-157">Bir etki alanının parçası olması gerekir ve kimlik doğrulaması ve imzalama özelliği, MSMQ için MSMQ Active Directory tümleştirme seçeneğini yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="06f01-157">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the Active Directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="06f01-158">Bu ölçütleri karşılayan olmayan bir bilgisayarda bu örneği çalıştırmak, bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="06f01-158">If you run this sample on a computer that does not satisfy these criteria, you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="06f01-159">Örnek bir çalışma grubu ya da Active Directory Tümleştirmesi olmadan alanına katılmış bir bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="06f01-159">To run the sample on a computer joined to a workgroup or without Active Directory integration</span></span>  
  
1.  <span data-ttu-id="06f01-160">Bilgisayarınız bir etki alanının parçası değil veya yüklü Active Directory Tümleştirmesi yok gerekirse kimlik doğrulama modu ve koruma düzeyini ayarlayarak taşıma güvenliği devre dışı bırakmak `None` aşağıdaki örnek yapılandırma kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="06f01-160">If your computer is not part of a domain or does not have Active Directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code.</span></span>  
  
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
          <!-- The mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex. -->  
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
  
2.  <span data-ttu-id="06f01-161">Örneği çalıştırmadan önce hem sunucu hem de istemci yapılandırmasına değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="06f01-161">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="06f01-162">Ayarı `security``mode` için `None` ayarına eşdeğerdir <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, ve `Message` güvenlik `None`.</span><span class="sxs-lookup"><span data-stu-id="06f01-162">Setting `security``mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="06f01-163">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="06f01-163">The samples may already be installed on your computer.</span></span> <span data-ttu-id="06f01-164">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="06f01-164">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="06f01-165">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="06f01-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="06f01-166">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="06f01-166">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`  
  
## <a name="see-also"></a><span data-ttu-id="06f01-167">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="06f01-167">See Also</span></span>
