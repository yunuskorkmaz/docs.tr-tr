---
title: İşlem Gerçekleştirilmiş MSMQ Bağlama
ms.date: 03/30/2017
ms.assetid: 71f5cb8d-f1df-4e1e-b8a2-98e734a75c37
ms.openlocfilehash: 381304bcef40245bac882a4fe4ae18a6998665cf
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085098"
---
# <a name="transacted-msmq-binding"></a><span data-ttu-id="bfc7a-102">İşlem Gerçekleştirilmiş MSMQ Bağlama</span><span class="sxs-lookup"><span data-stu-id="bfc7a-102">Transacted MSMQ Binding</span></span>
<span data-ttu-id="bfc7a-103">Bu örnek, Message Queuing (MSMQ) kullanarak hizmetteki kuyruğa alınan iletişim gerçekleştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bfc7a-104">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="bfc7a-105">Kuyruğa alınan iletişim kullanarak bir kuyruk hizmetine istemci iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-105">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="bfc7a-106">Daha kesin bir istemci bir kuyruğa iletiler gönderir.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-106">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="bfc7a-107">Hizmet iletileri kuyruktan alır.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-107">The service receives messages from the queue.</span></span> <span data-ttu-id="bfc7a-108">Hizmet ve istemci, bu nedenle, bir kuyruk kullanarak iletişim kurmak için aynı anda çalıştırılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-108">The service and client, therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="bfc7a-109">İşlem, ileti göndermek ve almak için kullanıldığında, aslında iki ayrı işlem vardır.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-109">When transactions are used to send and receive messages, there are actually two separate transactions.</span></span> <span data-ttu-id="bfc7a-110">İstemci bir işlem kapsamı iletileri gönderdiğinde istemcinin ve istemci Kuyruk yöneticisi yerel bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-110">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="bfc7a-111">Hizmet işlem kapsamı içindeki iletileri aldığında, hizmet ve alıcı Kuyruk yöneticisi yerel bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-111">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="bfc7a-112">İstemciyi ve hizmeti aynı işlemde katılan değil olduğunu unutmamak çok önemlidir; Bunun yerine, farklı işlem işlemlerini (örneğin göndermek ve almak gibi) ile birlikte kuyruğa gerçekleştirirken kullandıkları.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-112">It is very important to remember that the client and the service are not participating in the same transaction; rather, they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>  
  
 <span data-ttu-id="bfc7a-113">Bu örnekte, istemci bir işlem kapsamında hizmetten toplu iletiler gönderir.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-113">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="bfc7a-114">Kuyruğa gönderilen iletiler, ardından hizmeti tarafından tanımlanan işlem kapsamında hizmeti tarafından alınır.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-114">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span>  
  
 <span data-ttu-id="bfc7a-115">Hizmet sözleşme `IOrderProcessor`aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-115">The service contract is `IOrderProcessor`, as shown in the following sample code.</span></span> <span data-ttu-id="bfc7a-116">Kuyruklar ile kullanım için uygun olan bir tek yönlü hizmeti arabirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-116">The interface defines a one-way service that is suitable for use with queues.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```

 <span data-ttu-id="bfc7a-117">Hizmet davranışı ile bir işlem davranışını tanımlar `TransactionScopeRequired` kümesine `true`.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-117">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="bfc7a-118">Bu, kuyruktan ileti almak için kullanılan aynı işlem kapsamı yöntemi tarafından erişilen tüm kaynak yöneticileri tarafından kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-118">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="bfc7a-119">Ayrıca, yöntem bir özel durum oluşturursa, kuyruğa ileti döndürülür garanti eder.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-119">It also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="bfc7a-120">Bu işlemi davranışı ayar olmadan sıraya alınan bir kanal iletiyi kuyruktan okumak için bir işlem oluşturur ve işlem başarısız olursa, ileti kaybolur şekilde gönderme önce otomatik olarak işlemeleri.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-120">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before dispatch such that if the operation fails, the message is lost.</span></span> <span data-ttu-id="bfc7a-121">İletiyi sıradan okumak için aşağıdaki kodda gösterildiği gibi kullanılan işlem listeleme hizmet işlemleri için en yaygın senaryodur bakın.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-121">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue, as demonstrated in the following code.</span></span>  

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

 <span data-ttu-id="bfc7a-122">Kendi kendine barındırılan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-122">The service is self hosted.</span></span> <span data-ttu-id="bfc7a-123">MSMQ taşıma kullanırken, kullanılan kuyruk önceden oluşturulmuş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-123">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="bfc7a-124">Bu, el ile veya kod aracılığıyla yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-124">This can be done manually or through code.</span></span> <span data-ttu-id="bfc7a-125">Bu örnekte, hizmet sıranın varlığını denetleyin ve henüz yoksa bir kuyruk oluşturmak için kod içerir.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-125">In this sample, the service contains code to check for the existence of the queue and create the queue if it does not exist.</span></span> <span data-ttu-id="bfc7a-126">Kuyruk adı yapılandırma dosyasından okunur.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-126">The queue name is read from the configuration file.</span></span> <span data-ttu-id="bfc7a-127">Tarafından kullanılan taban adresini [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proxy hizmeti oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-127">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  

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

 <span data-ttu-id="bfc7a-128">MSMQ kuyruk adı, aşağıdaki örnek yapılandırmada gösterildiği gibi bir yapılandırma dosyasının appSettings bölümünde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-128">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>  
  
```xml  
<appSettings>  
    <add key="queueName" value=".\private$\ServiceModelSamplesTransacted" />  
</appSettings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="bfc7a-129">Kuyruk adı bir nokta (.) yolundaki ters eğik çizgi ayırıcılar ve yerel bilgisayar için bir kuyruk kullanma oluştururken kullandığı <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-129">The queue name uses a dot (.) for the local computer and backslash separators in its path when creating the queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="bfc7a-130">Windows Communication Foundation (WCF) uç noktası net.msmq şeması ile kuyruk adresini kullanır, "localhost" yerel bilgisayarı belirtmek için kullanır ve kendi yolunda eğik kullanır.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-130">The Windows Communication Foundation (WCF) endpoint uses the queue address with net.msmq scheme, uses "localhost" to denote the local computer, and uses forward slashes in its path.</span></span>  
  
 <span data-ttu-id="bfc7a-131">İstemci işlem kapsamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-131">The client creates a transaction scope.</span></span> <span data-ttu-id="bfc7a-132">Kuyruk ile iletişimi, burada tüm iletileri kuyruğa gönderilir ya da hiçbiri iletilerin kuyruğa gönderilen bir atomik birim olarak kabul edilmesi bu neden işlemin kapsamı içinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-132">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="bfc7a-133">İşlem çağırarak kararlıdır <xref:System.Transactions.TransactionScope.Complete%2A> işlem kapsamı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-133">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>  

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

 <span data-ttu-id="bfc7a-134">İşlem çalıştığını doğrulamak için aşağıdaki örnek kodda gösterildiği gibi işlem kapsamı açıklama satırı yaparak istemci değiştirmek, çözümü yeniden oluşturun ve istemcisini çalıştıran.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-134">To verify that transactions are working, modify the client by commenting the transaction scope as shown in the following sample code, rebuild the solution, and run the client.</span></span>  

```csharp
//scope.Complete();  
```

 <span data-ttu-id="bfc7a-135">İşlem tamamlanmış sayılmaz olduğundan, iletileri kuyruğa gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-135">Because the transaction is not completed, the messages are not sent to the queue.</span></span>  
  
 <span data-ttu-id="bfc7a-136">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hizmet ve istemci konsol pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-136">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="bfc7a-137">İstemciden hizmet alma iletileri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-137">You can see the service receive messages from the client.</span></span> <span data-ttu-id="bfc7a-138">Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-138">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="bfc7a-139">Sıraya alma kullanımda olduğundan, istemci ve hizmet aynı zamanda açık ve çalışıyor olması gerekmez, unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-139">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="bfc7a-140">İstemcisini çalıştıran da kapatın ve ardından hizmeti başlatın ve hala iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-140">You can run the client, shut it down, and then start up the service and it still receives the messages.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bfc7a-141">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="bfc7a-141">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bfc7a-142">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bfc7a-142">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="bfc7a-143">Hizmet ilk olarak çalıştırılırsa, sıranın mevcut olduğundan emin olun kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-143">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="bfc7a-144">Kuyruk yoksa, bir hizmeti oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-144">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="bfc7a-145">İlk sırayı oluşturmak için hizmet çalıştırabileceğiniz veya bir MSMQ Kuyruk Yöneticisi ile oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-145">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="bfc7a-146">Windows 2008'de bir kuyruk oluşturmak için aşağıdaki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-146">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="bfc7a-147">Sunucu Yöneticisi'nde açın [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bfc7a-147">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="bfc7a-148">Genişletin **özellikleri** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-148">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="bfc7a-149">Sağ **özel ileti kuyrukları**seçip **yeni**, **özel sıra**.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-149">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="bfc7a-150">Denetleme **işlem** kutusu.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-150">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="bfc7a-151">Girin `ServiceModelSamplesTransacted` yeni Kuyruğun adı.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-151">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="bfc7a-152">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bfc7a-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="bfc7a-153">Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bfc7a-153">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="bfc7a-154">Varsayılan olarak <xref:System.ServiceModel.NetMsmqBinding>, aktarım güvenliği etkin.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="bfc7a-155">MSMQ taşıma güvenlik için iki ilgili özellik <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ve <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-155">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>.</span></span> <span data-ttu-id="bfc7a-156">Varsayılan olarak, kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-156">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="bfc7a-157">MSMQ imzalama özelliği ve kimlik doğrulaması sağlamak için bir etki alanının parçası olması gerekir ve MSMQ Active Directory Tümleştirme seçeneği yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-157">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the Active Directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="bfc7a-158">Bu ölçütleri karşılamayan bir bilgisayarda bu örneği çalıştırmak, bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-158">If you run this sample on a computer that does not satisfy these criteria, you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="bfc7a-159">Örnek, bir çalışma grubuna veya Active Directory Tümleştirmesi olmadan alanına katılmış bir bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="bfc7a-159">To run the sample on a computer joined to a workgroup or without Active Directory integration</span></span>  
  
1.  <span data-ttu-id="bfc7a-160">Bilgisayarınız bir etki alanının parçası değil veya yüklü Active Directory Tümleştirmesi yok, aktarım güvenliği devre dışı kimlik doğrulama modu ve koruma düzeyi ayarlayarak kapatma `None` aşağıdaki örnek yapılandırma kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-160">If your computer is not part of a domain or does not have Active Directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code.</span></span>  
  
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
  
2.  <span data-ttu-id="bfc7a-161">Örneği çalıştırmadan önce yapılandırma hem sunucu hem de istemci değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-161">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bfc7a-162">Ayarı `security``mode` için `None` ayarlamakla eşdeğerdir <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, ve `Message` güvenlik `None`.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-162">Setting `security``mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bfc7a-163">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-163">The samples may already be installed on your computer.</span></span> <span data-ttu-id="bfc7a-164">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-164">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bfc7a-165">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bfc7a-166">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-166">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Transacted`  
  
## <a name="see-also"></a><span data-ttu-id="bfc7a-167">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bfc7a-167">See Also</span></span>
