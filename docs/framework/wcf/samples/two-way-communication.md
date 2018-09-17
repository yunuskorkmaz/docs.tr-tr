---
title: Çift Yönlü İletişim
ms.date: 03/30/2017
ms.assetid: fb64192d-b3ea-4e02-9fb3-46a508d26c60
ms.openlocfilehash: 319b63ff1eefdab4c23932294c3f1970f204601e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45674162"
---
# <a name="two-way-communication"></a><span data-ttu-id="29dba-102">Çift Yönlü İletişim</span><span class="sxs-lookup"><span data-stu-id="29dba-102">Two-Way Communication</span></span>
<span data-ttu-id="29dba-103">Bu örnek, MSMQ kuyruğa alınan hizmetteki iki yönlü iletişim gerçekleştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="29dba-103">This sample demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span> <span data-ttu-id="29dba-104">Bu örnekte `netMsmqBinding` bağlama.</span><span class="sxs-lookup"><span data-stu-id="29dba-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="29dba-105">Bu durumda, kuyruğa alınmış iletiler alma hizmeti gözlemleyin olanak tanıyan bir şirket içinde barındırılan bir konsol uygulaması hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="29dba-105">In this case, the service is a self-hosted console application that allows you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29dba-106">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="29dba-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="29dba-107">Bu örnek dayanır [işlem temelli MSMQ bağlama](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="29dba-107">This sample is based on the [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
 <span data-ttu-id="29dba-108">Kuyruğa alınan iletişim kullanarak bir kuyruk hizmetine istemci iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="29dba-108">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="29dba-109">İstemci bir kuyruğa ileti gönderir ve hizmet iletileri kuyruktan alır.</span><span class="sxs-lookup"><span data-stu-id="29dba-109">The client sends messages to a queue, and the service receives messages from the queue.</span></span> <span data-ttu-id="29dba-110">Hizmet ve istemci bu nedenle, bir kuyruk kullanarak iletişim kurmak için aynı anda çalıştırılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="29dba-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="29dba-111">Bu örnek 2 yönlü iletişimi kuyruklarını kullanan gösterir.</span><span class="sxs-lookup"><span data-stu-id="29dba-111">This sample demonstrates 2-way communication using queues.</span></span> <span data-ttu-id="29dba-112">İstemci, sıradan bir işlem kapsamında satın alma siparişleri gönderir.</span><span class="sxs-lookup"><span data-stu-id="29dba-112">The client sends purchase orders to the queue from within the scope of a transaction.</span></span> <span data-ttu-id="29dba-113">Hizmet siparişleri alır, sipariş işleme ve daha sonra geri istemci siparişin durumunu içeren bir işlem kapsamındaki sırasından çağırır.</span><span class="sxs-lookup"><span data-stu-id="29dba-113">The service receives the orders, processes the order and then calls back the client with the status of the order from the queue within the scope of a transaction.</span></span> <span data-ttu-id="29dba-114">İki yönlü iletişimi kolaylaştırmak için kuyruğa satın alma siparişleri ve sipariş durumu sıralara istemciyi ve hizmeti kullanın.</span><span class="sxs-lookup"><span data-stu-id="29dba-114">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="29dba-115">Hizmet sözleşmesi `IOrderProcessor` queuing kullanımını uygun bir tek yönlü hizmet işlemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="29dba-115">The service contract `IOrderProcessor` defines one-way service operations that suit the use of queuing.</span></span> <span data-ttu-id="29dba-116">Hizmet işlemi için sipariş durumları göndermek için kullanılacak yanıt uç nokta içerir.</span><span class="sxs-lookup"><span data-stu-id="29dba-116">The service operation includes the reply endpoint to use to send the order statuses to.</span></span> <span data-ttu-id="29dba-117">Sıranın URI'sini sipariş durumunun istemciye geri gönderilecek yanıt uç noktadır.</span><span class="sxs-lookup"><span data-stu-id="29dba-117">The reply endpoint is the URI of the queue to send the order status back to the client.</span></span> <span data-ttu-id="29dba-118">Uygulama işleme sırası, bu sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="29dba-118">The order processing application implements this contract.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po, string   
                                  reportOrderStatusTo);  
}
```
  
 <span data-ttu-id="29dba-119">Sipariş durumu gönderilecek yanıt anlaşması, istemci tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="29dba-119">The reply contract to send order status is specified by the client.</span></span> <span data-ttu-id="29dba-120">Sipariş durumu sözleşme istemciye uygular.</span><span class="sxs-lookup"><span data-stu-id="29dba-120">The client implements the order status contract.</span></span> <span data-ttu-id="29dba-121">Hizmet, bu sözleşmenin oluşturulan proxy siparişinizin durumu istemciye geri göndermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="29dba-121">The service uses the generated proxy of this contract to send order status back to the client.</span></span>  

```csharp
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```

 <span data-ttu-id="29dba-122">Hizmet işlemi gönderilen satın alma siparişi işler.</span><span class="sxs-lookup"><span data-stu-id="29dba-122">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="29dba-123"><xref:System.ServiceModel.OperationBehaviorAttribute> İşlem tamamlandığında hizmet işleminin otomatik tamamlama ve kuyruk iletiyi almak için kullanılan bir işlemde otomatik kaydı belirtmek için hizmet işlemi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="29dba-123">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in a transaction that is used to receive the message from the queue and automatic completion of transactions on completion of the service operation.</span></span> <span data-ttu-id="29dba-124">`Orders` Sınıfı sipariş işleme işlevselliğini kapsüller.</span><span class="sxs-lookup"><span data-stu-id="29dba-124">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="29dba-125">Bu durumda, satın alma siparişi bir sözlüğe ekler.</span><span class="sxs-lookup"><span data-stu-id="29dba-125">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="29dba-126">Hizmet işlemi kayıtlı işlem işlemlerinde kullanılabilir `Orders` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="29dba-126">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="29dba-127">Siparişin durumunu istemciye gönderilen satın alma siparişi işleme ek olarak hizmet işlemi yanıtlar.</span><span class="sxs-lookup"><span data-stu-id="29dba-127">The service operation, in addition to processing the submitted purchase order, replies back to the client on the status of the order.</span></span>  

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

 <span data-ttu-id="29dba-128">MSMQ kuyruk adı, bir yapılandırma dosyasının appSettings bölümünde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="29dba-128">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="29dba-129">Hizmet için uç nokta yapılandırma dosyasının System.ServiceModel bölümünde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="29dba-129">The endpoint for the service is defined in the System.ServiceModel section of the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29dba-130">MSMQ kuyruk adı ve uç nokta adresi adresleme biraz farklı kuralları kullanın.</span><span class="sxs-lookup"><span data-stu-id="29dba-130">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="29dba-131">MSMQ kuyruk adı yerel makine ve ters eğik çizgi ayırıcılar yolundaki bir nokta (.) kullanır.</span><span class="sxs-lookup"><span data-stu-id="29dba-131">The MSMQ queue name uses a dot (.) for the local machine and backslash separators in its path.</span></span> <span data-ttu-id="29dba-132">Windows Communication Foundation (WCF) uç nokta adresini belirten bir net.msmq: şeması, "localhost" için yerel makine ve eğik kendi yolu kullanır.</span><span class="sxs-lookup"><span data-stu-id="29dba-132">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine, and uses forward slashes in its path.</span></span> <span data-ttu-id="29dba-133">Uzak makinede barındırılan bir kuyruktan okunur değiştirin "." ve "localhost" uzak makine adı.</span><span class="sxs-lookup"><span data-stu-id="29dba-133">To read from a queue that is hosted on the remote machine, replace the "." and "localhost" to the remote machine name.</span></span>  
  
 <span data-ttu-id="29dba-134">Kendi kendine barındırılan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="29dba-134">The service is self hosted.</span></span> <span data-ttu-id="29dba-135">MSMQ taşıma kullanırken, kullanılan kuyruk önceden oluşturulmuş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="29dba-135">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="29dba-136">Bu, el ile veya kod aracılığıyla yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="29dba-136">This can be done manually or through code.</span></span> <span data-ttu-id="29dba-137">Bu örnekte, hizmet sırası varlığını denetler ve, gerekirse oluşturur.</span><span class="sxs-lookup"><span data-stu-id="29dba-137">In this sample, the service checks for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="29dba-138">Kuyruk adı yapılandırma dosyasından okunur.</span><span class="sxs-lookup"><span data-stu-id="29dba-138">The queue name is read from the configuration file.</span></span> <span data-ttu-id="29dba-139">Tarafından kullanılan taban adresini [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proxy hizmeti oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="29dba-139">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy to the service.</span></span>  

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

 <span data-ttu-id="29dba-140">İstemci, bir işlem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="29dba-140">The client creates a transaction.</span></span> <span data-ttu-id="29dba-141">Kuyruk ile iletişimi, burada tüm iletileri başarılı veya başarısız bir atomik birim olarak kabul edilmesi bu neden işlemin kapsamı içinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="29dba-141">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span>  

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

 <span data-ttu-id="29dba-142">İstemci kodu uygulayan `IOrderStatus` siparişinizin durumu hizmetinden almak üzere sözleşme.</span><span class="sxs-lookup"><span data-stu-id="29dba-142">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="29dba-143">Bu durumda, siparişinizin durumu yazdırır.</span><span class="sxs-lookup"><span data-stu-id="29dba-143">In this case, it prints out the order status.</span></span>  

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

 <span data-ttu-id="29dba-144">Durum sırasını oluşturulan `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="29dba-144">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="29dba-145">Aşağıdaki örnek yapılandırmada gösterildiği gibi istemci yapılandırması sipariş durumu hizmeti barındırmak için sipariş durumu hizmeti yapılandırması içerir.</span><span class="sxs-lookup"><span data-stu-id="29dba-145">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="29dba-146">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hizmet ve istemci konsol pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="29dba-146">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="29dba-147">İstemciden hizmet alma iletileri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29dba-147">You can see the service receive messages from the client.</span></span> <span data-ttu-id="29dba-148">Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="29dba-148">Press ENTER in each console window to shut down the service and client.</span></span>  
  
 <span data-ttu-id="29dba-149">Hizmet satın alma siparişi bilgileri görüntüler ve sipariş durumunun durumu sırasını geri gönderdiği gösterir.</span><span class="sxs-lookup"><span data-stu-id="29dba-149">The service displays the purchase order information and indicates it is sending back the order status to the order status queue.</span></span>  
  
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
  
 <span data-ttu-id="29dba-150">İstemci, hizmet tarafından gönderilen sipariş durumu bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="29dba-150">The client displays the order status information sent by the service.</span></span>  
  
```  
Press <ENTER> to terminate client.  
Status of order 124a1f69-3699-4b16-9bcc-43147a8756fc:Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="29dba-151">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="29dba-151">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="29dba-152">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="29dba-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="29dba-153">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="29dba-153">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="29dba-154">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="29dba-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="29dba-155">Bu örnek için yapılandırmayı yeniden üretmek için Svcutil.exe kullanma, uç nokta adları istemci kodu eşleştirilecek istemci yapılandırmasında değişiklik emin olun.</span><span class="sxs-lookup"><span data-stu-id="29dba-155">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint names in the client configuration to match the client code.</span></span>  
  
 <span data-ttu-id="29dba-156">Varsayılan olarak <xref:System.ServiceModel.NetMsmqBinding>, aktarım güvenliği etkin.</span><span class="sxs-lookup"><span data-stu-id="29dba-156">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="29dba-157">MSMQ taşıma güvenlik için iki ilgili özellik <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ve <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` varsayılan olarak, kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`.</span><span class="sxs-lookup"><span data-stu-id="29dba-157">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="29dba-158">MSMQ imzalama özelliği ve kimlik doğrulaması sağlamak için bir etki alanının parçası olması gerekir ve MSMQ active directory tümleştirme seçeneği yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="29dba-158">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="29dba-159">Bu ölçütleri karşılamayan bir bilgisayarda bu örneği çalıştırmak, bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="29dba-159">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="29dba-160">Örnek, bir çalışma grubuna veya active directory tümleştirmesi olmadan alanına katılmış bir bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="29dba-160">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="29dba-161">Bilgisayarınız bir etki alanının parçası değil veya yüklü active directory tümleştirmesi yok, aktarım güvenliği devre dışı kimlik doğrulama modu ve koruma düzeyi ayarlayarak kapatma `None` aşağıdaki örnek yapılandırmada gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="29dba-161">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
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
  
2.  <span data-ttu-id="29dba-162">Bir istemci yapılandırması için güvenlik kapatma aşağıdakileri oluşturur:</span><span class="sxs-lookup"><span data-stu-id="29dba-162">Turning off security for a client configuration generates the following:</span></span>  
  
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
  
3.  <span data-ttu-id="29dba-163">Bu örnek bir bağlama oluşturur `OrderProcessorService`.</span><span class="sxs-lookup"><span data-stu-id="29dba-163">The service for this sample creates a binding in the `OrderProcessorService`.</span></span> <span data-ttu-id="29dba-164">Güvenlik modu ayarlamak için bağlama örneği sonra bir kod satırını ekleyin `None`.</span><span class="sxs-lookup"><span data-stu-id="29dba-164">Add a line of code after the binding is instantiated to set the security mode to `None`.</span></span>  
  
    ```csharp
    NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
    msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
    ```  
  
4.  <span data-ttu-id="29dba-165">Örneği çalıştırmadan önce yapılandırma hem sunucu hem de istemci değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="29dba-165">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="29dba-166">Ayarı `security mode` için `None` ayarlamakla eşdeğerdir <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> veya `Message` güvenlik `None`.</span><span class="sxs-lookup"><span data-stu-id="29dba-166">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> or `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="29dba-167">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="29dba-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="29dba-168">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="29dba-168">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="29dba-169">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="29dba-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="29dba-170">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="29dba-170">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Binding\Net\MSMQ\Two-Way`  
  
## <a name="see-also"></a><span data-ttu-id="29dba-171">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="29dba-171">See Also</span></span>
