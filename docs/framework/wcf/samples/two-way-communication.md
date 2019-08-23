---
title: Çift Yönlü İletişim
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 297e9af98f6fe39fb2cca4b5d0350c293177b173
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941004"
---
# <a name="two-way-communication"></a><span data-ttu-id="ce578-102">Çift Yönlü İletişim</span><span class="sxs-lookup"><span data-stu-id="ce578-102">Two-Way Communication</span></span>
<span data-ttu-id="ce578-103">Bu örnek, MSMQ üzerinden işlem temelli iki yönlü sıraya alınmış iletişimin nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce578-103">This sample demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span> <span data-ttu-id="ce578-104">Bu örnek, `netMsmqBinding` bağlamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="ce578-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="ce578-105">Bu durumda hizmet, sıraya alınan iletileri alma hizmetinin gözlemlebilmenizi sağlayan, kendine barındırılan bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="ce578-105">In this case, the service is a self-hosted console application that allows you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce578-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="ce578-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ce578-107">Bu örnek, [IŞLENEN MSMQ bağlamasını](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)temel alır.</span><span class="sxs-lookup"><span data-stu-id="ce578-107">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
 <span data-ttu-id="ce578-108">Sıraya alınmış iletişimde istemci, hizmet ile bir kuyruk kullanarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="ce578-108">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="ce578-109">İstemci bir kuyruğa ileti gönderir ve hizmet kuyruktan iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="ce578-109">The client sends messages to a queue, and the service receives messages from the queue.</span></span> <span data-ttu-id="ce578-110">Bu nedenle, hizmet ve istemci, bir kuyruk kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ce578-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="ce578-111">Bu örnek, kuyrukları kullanarak 2 yönlü iletişimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce578-111">This sample demonstrates 2-way communication using queues.</span></span> <span data-ttu-id="ce578-112">İstemci, bir işlemin kapsamındaki satınalma emirlerini kuyruğa gönderir.</span><span class="sxs-lookup"><span data-stu-id="ce578-112">The client sends purchase orders to the queue from within the scope of a transaction.</span></span> <span data-ttu-id="ce578-113">Hizmet siparişleri alır, sırayı işler ve sonra bir işlemin kapsamındaki sıradaki sıra durumuyla istemciyi geri çağırır.</span><span class="sxs-lookup"><span data-stu-id="ce578-113">The service receives the orders, processes the order and then calls back the client with the status of the order from the queue within the scope of a transaction.</span></span> <span data-ttu-id="ce578-114">İki yönlü iletişimi kolaylaştırmak için, istemci ve hizmetin her ikisi de, satın alma siparişlerinin ve sipariş durumunun kuyruğa alınması için kuyrukları kullanır.</span><span class="sxs-lookup"><span data-stu-id="ce578-114">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="ce578-115">Hizmet sözleşmesi `IOrderProcessor` , sıraya alma işlemini kullanan tek yönlü hizmet işlemlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ce578-115">The service contract `IOrderProcessor` defines one-way service operations that suit the use of queuing.</span></span> <span data-ttu-id="ce578-116">Hizmet işlemi, sipariş durumlarını göndermek için kullanılacak yanıt uç noktasını içerir.</span><span class="sxs-lookup"><span data-stu-id="ce578-116">The service operation includes the reply endpoint to use to send the order statuses to.</span></span> <span data-ttu-id="ce578-117">Yanıt uç noktası, sipariş durumunun istemciye geri gönderilmesi için kuyruğun URI 'sidir.</span><span class="sxs-lookup"><span data-stu-id="ce578-117">The reply endpoint is the URI of the queue to send the order status back to the client.</span></span> <span data-ttu-id="ce578-118">Sipariş işleme uygulaması bu sözleşmeyi uygular.</span><span class="sxs-lookup"><span data-stu-id="ce578-118">The order processing application implements this contract.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string   
                                  reportOrderStatusTo);  
}
```
  
 <span data-ttu-id="ce578-119">Sıra durumunu göndermek için gereken yanıt sözleşmesi, istemci tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="ce578-119">The reply contract to send order status is specified by the client.</span></span> <span data-ttu-id="ce578-120">İstemci sipariş durumu sözleşmesini uygular.</span><span class="sxs-lookup"><span data-stu-id="ce578-120">The client implements the order status contract.</span></span> <span data-ttu-id="ce578-121">Hizmet, sipariş durumunu istemciye geri göndermek için bu sözleşmenin oluşturulan ara sunucusunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="ce578-121">The service uses the generated proxy of this contract to send order status back to the client.</span></span>  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 <span data-ttu-id="ce578-122">Hizmet işlemi gönderilen satın alma siparişini işler.</span><span class="sxs-lookup"><span data-stu-id="ce578-122">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="ce578-123">, <xref:System.ServiceModel.OperationBehaviorAttribute> Kuyruktan ileti almak ve hizmet işleminin tamamlanmasından sonra işlemlerin otomatik olarak tamamlanması için kullanılan bir işlemde otomatik kayıt belirtmek üzere hizmet işlemine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ce578-123">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in a transaction that is used to receive the message from the queue and automatic completion of transactions on completion of the service operation.</span></span> <span data-ttu-id="ce578-124">`Orders` Sınıfı sipariş işleme işlevselliğini Kapsüller.</span><span class="sxs-lookup"><span data-stu-id="ce578-124">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="ce578-125">Bu durumda, satın alma sırasını bir sözlüğe ekler.</span><span class="sxs-lookup"><span data-stu-id="ce578-125">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="ce578-126">İçindeki hizmet işleminin kayıtlı olduğu işlem, `Orders` sınıftaki işlemler için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ce578-126">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="ce578-127">Hizmet işlemi, gönderilen satın alma siparişinin işlenmesine ek olarak, siparişin durumunda istemciye geri yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="ce578-127">The service operation, in addition to processing the submitted purchase order, replies back to the client on the status of the order.</span></span>  

```csharp
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
{  
    Orders.Add(po);  
    Console.WriteLine("Processing {0} ", po);  
    Console.WriteLine("Sending back order status information");  
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding("ClientCallbackBinding");  
    OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
  
    // Please note that the same transaction that is used to dequeue the purchase order is used  
    // to send back order status.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        client.OrderStatus(po.PONumber, po.Status);  
        scope.Complete();  
    }  
    //Close the client.  
    client.Close();  
}  
```

 <span data-ttu-id="ce578-128">MSMQ kuyruğu adı, yapılandırma dosyasının bir appSettings bölümünde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ce578-128">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="ce578-129">Hizmetin uç noktası, yapılandırma dosyasının System. ServiceModel bölümünde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ce578-129">The endpoint for the service is defined in the System.ServiceModel section of the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce578-130">MSMQ kuyruğu adı ve uç nokta adresi biraz farklı adresleme kuralları kullanır.</span><span class="sxs-lookup"><span data-stu-id="ce578-130">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="ce578-131">MSMQ sırası adı, yerel makine için bir nokta (.) ve kendi yolunda ters eğik çizgi ayırıcılar kullanır.</span><span class="sxs-lookup"><span data-stu-id="ce578-131">The MSMQ queue name uses a dot (.) for the local machine and backslash separators in its path.</span></span> <span data-ttu-id="ce578-132">Windows Communication Foundation (WCF) uç noktası adresi bir net. MSMQ: Scheme belirtir, yerel makine için "localhost" kullanır ve yolunda eğik çizgi kullanır.</span><span class="sxs-lookup"><span data-stu-id="ce578-132">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine, and uses forward slashes in its path.</span></span> <span data-ttu-id="ce578-133">Uzak makinede barındırılan bir kuyruktan okumak için, "." ve "localhost" değerini uzak makine adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ce578-133">To read from a queue that is hosted on the remote machine, replace the "." and "localhost" to the remote machine name.</span></span>  
  
 <span data-ttu-id="ce578-134">Hizmet kendi kendine barındırılır.</span><span class="sxs-lookup"><span data-stu-id="ce578-134">The service is self hosted.</span></span> <span data-ttu-id="ce578-135">MSMQ aktarımını kullanırken kullanılan kuyruğun önceden oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ce578-135">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="ce578-136">Bu, el ile veya kod aracılığıyla yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="ce578-136">This can be done manually or through code.</span></span> <span data-ttu-id="ce578-137">Bu örnekte hizmet, sıranın varlığını denetler ve gerekirse oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ce578-137">In this sample, the service checks for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="ce578-138">Sıra adı yapılandırma dosyasından okundu.</span><span class="sxs-lookup"><span data-stu-id="ce578-138">The queue name is read from the configuration file.</span></span> <span data-ttu-id="ce578-139">Temel adres, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından hizmete proxy oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ce578-139">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from appSettings in configuration.  
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
    }  
}  
```

 <span data-ttu-id="ce578-140">İstemci bir işlem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ce578-140">The client creates a transaction.</span></span> <span data-ttu-id="ce578-141">Kuyrukla iletişim, işlemin kapsamı içinde gerçekleşirken, tüm iletilerin başarılı veya başarısız olduğu atomik bir birim olarak işlenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="ce578-141">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span>  

```csharp
// Create a ServiceHost for the OrderStatus service type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
  
    // Open the ServiceHostBase to create listeners and start listening for order status messages.  
    serviceHost.Open();  
  
    // Create the purchase order.  
    ...  
  
    // Create a client with given client endpoint configuration.  
    OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
    //Create a transaction scope.  
    using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
    {  
        string hostName = Dns.GetHostName();  
  
        // Make a queued call to submit the purchase order.  
        client.SubmitPurchaseOrder(po, "net.msmq://" + hostName + "/private/ServiceModelSamplesTwo-way/OrderStatus");  
  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Close down the client.  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHost to shutdown the service.  
    serviceHost.Close();  
}  
```

 <span data-ttu-id="ce578-142">İstemci kodu, hizmetten sipariş `IOrderStatus` durumunu almak için sözleşmeyi uygular.</span><span class="sxs-lookup"><span data-stu-id="ce578-142">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="ce578-143">Bu durumda, sipariş durumunu yazdırır.</span><span class="sxs-lookup"><span data-stu-id="ce578-143">In this case, it prints out the order status.</span></span>  

```csharp
[ServiceBehavior]  
public class OrderStatusService : IOrderStatus  
{  
    [OperationBehavior(TransactionAutoComplete = true,   
                        TransactionScopeRequired = true)]  
    public void OrderStatus(string poNumber, string status)  
    {  
        Console.WriteLine("Status of order {0}:{1} ", poNumber ,   
                                                           status);  
    }  
}  
```

 <span data-ttu-id="ce578-144">Sıra durumu kuyruğu `Main` yönteminde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ce578-144">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="ce578-145">İstemci yapılandırması, aşağıdaki örnek yapılandırmada gösterildiği gibi, sipariş durumu hizmetini barındıracak sıra durumu hizmeti yapılandırmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="ce578-145">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
</appSettings>  
  
<system.serviceModel>  
  
  <services>  
    <service   
       name="Microsoft.ServiceModel.Samples.OrderStatusService">  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
    </service>  
  </services>  
  
  <client>  
    <!-- Define NetMsmqEndpoint -->  
    <endpoint name="OrderProcessorEndpoint"  
              address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"   
              binding="netMsmqBinding"   
              contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
  </client>  
  
</system.serviceModel>  
```  
  
 <span data-ttu-id="ce578-146">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencereleri içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ce578-146">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="ce578-147">Hizmetin istemciden ileti alacağını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce578-147">You can see the service receive messages from the client.</span></span> <span data-ttu-id="ce578-148">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="ce578-148">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="ce578-149">Hizmet, satın alma siparişi bilgilerini görüntüler ve sipariş durumunu sipariş durumu kuyruğuna geri gönderdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce578-149">The service displays the purchase order information and indicates it is sending back the order status to the order status queue.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Processing Purchase Order: 124a1f69-3699-4b16-9bcc-43147a8756fc  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
  
Sending back order status information  
```  
  
 <span data-ttu-id="ce578-150">İstemci, hizmet tarafından gönderilen sıra durumu bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ce578-150">The client displays the order status information sent by the service.</span></span>  
  
```  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ce578-151">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ce578-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ce578-152">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ce578-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ce578-153">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="ce578-153">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ce578-154">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="ce578-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ce578-155">Bu örneğe yönelik yapılandırmayı yeniden oluşturmak için Svcutil. exe ' yi kullanırsanız, istemci yapılandırmasındaki uç nokta adlarını istemci koduyla eşleşecek şekilde değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ce578-155">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint names in the client configuration to match the client code.</span></span>  
  
 <span data-ttu-id="ce578-156">Varsayılan <xref:System.ServiceModel.NetMsmqBinding>olarak, taşıma güvenliği etkindir.</span><span class="sxs-lookup"><span data-stu-id="ce578-156">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="ce578-157"><xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> MSMQ aktarım güvenliği için iki ilgili özellik vardır ve `.` <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> varsayılan olarak, kimlik doğrulama modu olarak `Windows` ayarlanır ve koruma düzeyi olarak `Sign`ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ce578-157">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="ce578-158">Kimlik doğrulama ve imzalama özelliğini sağlamak için MSMQ için, bir etki alanının parçası olması ve MSMQ için Active Directory tümleştirme seçeneğinin yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ce578-158">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="ce578-159">Bu örneği bu ölçütlere uygun olmayan bir bilgisayarda çalıştırırsanız bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="ce578-159">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="ce578-160">Örneği bir çalışma grubuna katılmış veya Active Directory Tümleştirmesi olmadan bir bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ce578-160">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1. <span data-ttu-id="ce578-161">Bilgisayarınız bir etki alanının parçası değilse veya Active Directory Tümleştirmesi yüklü değilse, kimlik doğrulama modunu ve koruma düzeyini `None` aşağıdaki örnek yapılandırmada gösterildiği gibi olarak ayarlayarak aktarım güvenliğini kapatın:</span><span class="sxs-lookup"><span data-stu-id="ce578-161">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
    ```xml  
    <configuration>  
  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderProcessor" />  
      </appSettings>  
  
      <system.serviceModel>  
        <services>  
          <service   
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding"   
                      contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          </service>  
        </services>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
2. <span data-ttu-id="ce578-162">İstemci yapılandırması için güvenliği kapatmak aşağıdakileri oluşturur:</span><span class="sxs-lookup"><span data-stu-id="ce578-162">Turning off security for a client configuration generates the following:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <appSettings>  
        <!-- Use appSetting to configure MSMQ queue name. -->  
        <add key="queueName" value=".\private$\ServiceModelSamplesTwo-way/OrderStatus" />  
      </appSettings>  
  
      <system.serviceModel>  
  
        <services>  
          <service   
             name="Microsoft.ServiceModel.Samples.OrderStatusService">  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderStatus"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="TransactedBinding" contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
          </service>  
        </services>  
  
        <client>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint name="OrderProcessorEndpoint"  
                    address="net.msmq://localhost/private/ServiceModelSamplesTwo-way/OrderProcessor"   
                    binding="netMsmqBinding"   
                    bindingConfiguration="TransactedBinding"  
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
        </client>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="TransactedBinding" >  
             <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
      </system.serviceModel>  
  
    </configuration>  
    ```  
  
3. <span data-ttu-id="ce578-163">Bu örnek için hizmeti, `OrderProcessorService`içinde bir bağlama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ce578-163">The service for this sample creates a binding in the `OrderProcessorService`.</span></span> <span data-ttu-id="ce578-164">Güvenlik modunu olarak `None`ayarlamak için bağlama örneği oluşturulduktan sonra bir kod satırı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ce578-164">Add a line of code after the binding is instantiated to set the security mode to `None`.</span></span>  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4. <span data-ttu-id="ce578-165">Örneği çalıştırmadan önce hem sunucu hem de istemci üzerinde yapılandırmayı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ce578-165">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ce578-166">`security mode` Ayarı,<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> ayarına veya Güvenliğeeşdeğerdir.`Message` `None` <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> `None`</span><span class="sxs-lookup"><span data-stu-id="ce578-166">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> or `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ce578-167">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="ce578-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ce578-168">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ce578-168">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ce578-169">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="ce578-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ce578-170">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ce578-170">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
