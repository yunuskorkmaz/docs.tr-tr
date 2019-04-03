---
title: Oturumlar ve Kuyruklar
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: 4aa8aea2e829f89714ad9fa946121d4ebab21c4c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814529"
---
# <a name="sessions-and-queues"></a><span data-ttu-id="b2e8e-102">Oturumlar ve Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="b2e8e-102">Sessions and Queues</span></span>
<span data-ttu-id="b2e8e-103">Bu örnek, göndermek ve bir dizi ilgili ileti kuyruğa alınan iletişim Message Queuing (MSMQ) aktarma üzerinden almak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-103">This sample demonstrates how to send and receive a set of related messages in queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="b2e8e-104">Bu örnekte `netMsmqBinding` bağlama.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="b2e8e-105">Hizmeti, sıraya alınan iletileri alma hizmeti gözlemleyin sağlamak için bir şirket içinde barındırılan bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-105">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2e8e-106">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b2e8e-107">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b2e8e-108">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b2e8e-109">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b2e8e-110">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 <span data-ttu-id="b2e8e-111">Kuyruğa alınan iletişim kullanarak bir kuyruk hizmetine istemci iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-111">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="b2e8e-112">Daha kesin bir istemci bir kuyruğa iletiler gönderir.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-112">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="b2e8e-113">Hizmet iletileri kuyruktan alır.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-113">The service receives messages from the queue.</span></span> <span data-ttu-id="b2e8e-114">Hizmet ve istemci bu nedenle, bir kuyruk kullanarak iletişim kurmak için aynı anda çalıştırılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-114">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="b2e8e-115">Bazı durumlarda, bir istemci, bir dizi bir grupta birbirleriyle ilişkili ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-115">Sometimes, a client sends a set of messages that are related to each other in a group.</span></span> <span data-ttu-id="b2e8e-116">İletileri birlikte ya da belirli bir sırayla işlenmesi gereken, bir kuyruk, bunları tek bir alıcı uygulama tarafından işlenmek arada gruplandırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-116">When messages must be processed together or in a specified order, a queue can be used to group them together, for processing by a single receiving application.</span></span> <span data-ttu-id="b2e8e-117">Bu bir sunucu grubu üzerinde birkaç alan uygulamalar vardır ve iletiler grubunu aynı alan bir uygulama tarafından işlendiğinden emin olmak için gerekli olduğunda özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-117">This is particularly important when there are several receiving applications on a group of servers and it is necessary to ensure that a group of messages is processed by the same receiving application.</span></span> <span data-ttu-id="b2e8e-118">Sıraya alınan oturumları, ilgili bir dizi tamamını aynı anda işlenen ileti alıp göndermek için kullanılan bir mekanizması mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-118">Queued sessions are a mechanism used to send and receive a related set of messages that must get processed all at once.</span></span> <span data-ttu-id="b2e8e-119">Sıraya alınan oturumları bu düzeni gösteren bir işlem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-119">Queued sessions require a transaction to exhibit this pattern.</span></span>  
  
 <span data-ttu-id="b2e8e-120">Bu örnekte istemci ileti sayısı oturum tek bir işlem kapsamı içindeki bir parçası olarak hizmetine gönderir.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-120">In the sample, the client sends a number of messages to the service as part of a session within the scope of a single transaction.</span></span>  
  
 <span data-ttu-id="b2e8e-121">Hizmet sözleşme `IOrderTaker`, kuyruklar ile kullanım için uygun olan bir tek yönlü hizmeti tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-121">The service contract is `IOrderTaker`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="b2e8e-122"><xref:System.ServiceModel.SessionMode> Aşağıda gösterilen sözleşmelerde kullanılan örnek kodu iletileri oturumun bir parçası olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-122">The <xref:System.ServiceModel.SessionMode> used in the contract shown in the following sample code indicates that the messages are part of the session.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface IOrderTaker  
{  
    [OperationContract(IsOneWay = true)]  
    void OpenPurchaseOrder(string customerId);  
  
    [OperationContract(IsOneWay = true)]  
    void AddProductLineItem(string productId, int quantity);  
  
    [OperationContract(IsOneWay = true)]  
    void EndPurchaseOrder();  
}  
```

 <span data-ttu-id="b2e8e-123">Hizmet, hizmet işlemleri ilk işlemin bir işlemde kaydeder ancak otomatik olarak hareket tamamlanmazsa şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-123">The service defines service operations in such a way that the first operation enlists in a transaction but does not automatically complete the transaction.</span></span> <span data-ttu-id="b2e8e-124">Sonraki işlemlerde de aynı işleme ancak otomatik olarak tamamlanmaz.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-124">Subsequent operations also enlist in the same transaction but do not automatically complete.</span></span> <span data-ttu-id="b2e8e-125">Oturumdaki son işlem, işlem otomatik olarak tamamlar.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-125">The last operation in the session automatically completes the transaction.</span></span> <span data-ttu-id="b2e8e-126">Bu nedenle, aynı işlem, hizmet sözleşmesindeki birkaç işlem çağrıları için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-126">Thus, the same transaction is used for several operation invocations in the service contract.</span></span> <span data-ttu-id="b2e8e-127">İşlemlerden birini bir özel durum, geri işlem yapar ve oturum geri sıraya konur.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-127">If any of the operations throw an exception, then the transaction rolls back and the session is put back into the queue.</span></span> <span data-ttu-id="b2e8e-128">Son işlem işlemin başarıyla tamamlanmasından sonra işlem taahhüt eder.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-128">Upon successful completion of the last operation, the transaction is committed.</span></span> <span data-ttu-id="b2e8e-129">Hizmeti kullandığı `PerSession` olarak <xref:System.ServiceModel.InstanceContextMode> service'nın aynı örneğine bir oturumdaki tüm iletileri almak için.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-129">The service uses `PerSession` as the <xref:System.ServiceModel.InstanceContextMode> to receive all messages in a session on the same instance of the service.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class OrderTakerService : IOrderTaker  
{  
    PurchaseOrder po;  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                 TransactionAutoComplete = false)]  
    public void OpenPurchaseOrder(string customerId)  
    {  
        Console.WriteLine("Creating purchase order");  
        po = new PurchaseOrder(customerId);  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                  TransactionAutoComplete = false)]  
    public void AddProductLineItem(string productId, int quantity)  
    {  
        po.AddProductLineItem(productId, quantity);  
        Console.WriteLine("Product " + productId + " quantity " +   
                            quantity + " added to purchase order");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                  TransactionAutoComplete = true)]  
    public void EndPurchaseOrder()  
    {  
       Console.WriteLine("Purchase Order Completed");  
       Console.WriteLine();  
       Console.WriteLine(po.ToString());  
    }  
}  
```

 <span data-ttu-id="b2e8e-130">Kendi kendine barındırılan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-130">The service is self hosted.</span></span> <span data-ttu-id="b2e8e-131">MSMQ taşıma kullanırken, kullanılan kuyruk önceden oluşturulmuş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-131">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="b2e8e-132">Bu, el ile veya kod aracılığıyla yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-132">This can be done manually or through code.</span></span> <span data-ttu-id="b2e8e-133">Bu örnekte, hizmeti içeren <xref:System.Messaging> sıranın varlığını denetlemek için kod ve, gerekirse oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-133">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="b2e8e-134">Kuyruk adı kullanılarak yapılandırma dosyasında okuma <xref:System.Configuration.ConfigurationManager.AppSettings%2A> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-134">The queue name is read from the configuration file using the <xref:System.Configuration.ConfigurationManager.AppSettings%2A> class.</span></span>  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderTakerService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderTakerService)))  
    {  
        // Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        // Close the ServiceHost to shutdown the service.  
        serviceHost.Close();   
    }  
}  
```

 <span data-ttu-id="b2e8e-135">MSMQ kuyruk adı, bir yapılandırma dosyasının appSettings bölümünde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="b2e8e-136">Hizmet için uç nokta yapılandırma dosyasının system.serviceModel bölümünde tanımlanan ve belirtir `netMsmqBinding` bağlama.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-136">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesSession" />  
</appSettings>  
  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      ...  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesSession"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
      ...  
    </service>  
  </services>  
  ...  
<system.serviceModel>  
```  
  
 <span data-ttu-id="b2e8e-137">İstemci işlem kapsamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-137">The client creates a transaction scope.</span></span> <span data-ttu-id="b2e8e-138">Oturum içindeki tüm iletileri burada tüm iletileri başarılı veya başarısız bir atomik birim olarak kabul edilmesi bu neden işlem kapsamında kuyruğa gönderilir.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-138">All messages in the session are sent to the queue within the transaction scope, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="b2e8e-139">İşlem çağırarak kararlıdır <xref:System.Transactions.TransactionScope.Complete%2A>.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-139">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A>.</span></span>  

```csharp
//Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    // Create a client with given client endpoint configuration.  
    OrderTakerClient client = new OrderTakerClient("OrderTakerEndpoint");  
    // Open a purchase order.  
    client.OpenPurchaseOrder("somecustomer.com");  
    Console.WriteLine("Purchase Order created");  
  
    // Add product line items.  
    Console.WriteLine("Adding 10 quantities of blue widget");  
    client.AddProductLineItem("Blue Widget", 10);  
  
    Console.WriteLine("Adding 23 quantities of red widget");  
    client.AddProductLineItem("Red Widget", 23);  
  
    // Close the purchase order.  
    Console.WriteLine("Closing the purchase order");  
    client.EndPurchaseOrder();  
  
    //Closing the client gracefully closes the connection and cleans up resources.  
    client.Close();                  
  
    // Complete the transaction.  
    scope.Complete();  
}  
```

> [!NOTE]
>  <span data-ttu-id="b2e8e-140">Yalnızca tek bir işlem için tüm iletiler oturumunda kullanabilirsiniz ve işlem yapmadan önce oturum içindeki tüm iletileri gönderilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-140">You can use only a single transaction for all messages in the session and all messages in the session must be sent before committing the transaction.</span></span> <span data-ttu-id="b2e8e-141">İstemci kapatma oturumu kapatır.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-141">Closing the client closes the session.</span></span> <span data-ttu-id="b2e8e-142">Bu nedenle, istemci tüm iletileri oturumda kuyruğa göndermek için işlem tamamlanmadan önce kapatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-142">Therefore, the client has to be closed before the transaction is completed to send all messages in the session to the queue.</span></span>  
  
 <span data-ttu-id="b2e8e-143">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hizmet ve istemci konsol pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-143">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="b2e8e-144">İstemciden hizmet alma iletileri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-144">You can see the service receive messages from the client.</span></span> <span data-ttu-id="b2e8e-145">Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-145">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="b2e8e-146">Sıraya alma kullanımda olduğundan, istemci ve hizmet aynı zamanda açık ve çalışıyor olması gerekmez, unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-146">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="b2e8e-147">İstemcisini çalıştıran da kapatın ve ardından hizmeti başlatın ve hala iletilerini alır.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-147">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>  
  
 <span data-ttu-id="b2e8e-148">İstemcide.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-148">On the client.</span></span>  
  
```  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="b2e8e-149">Hizmette.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-149">On the service.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Creating purchase order  
Product Blue Widget quantity 10 added to purchase order  
Product Red Widget quantity 23 added to purchase order  
Purchase Order Completed  
  
Purchase Order: 7c86fef0-2306-4c51-80e6-bcabcc1a6e5e  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 10 of Blue Widget @unit price: $2985  
                Order LineItem: 23 of Red Widget @unit price: $156  
        Total cost of this order: $33438  
        Order status: Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b2e8e-150">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b2e8e-150">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b2e8e-151">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b2e8e-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b2e8e-152">Çözüm C#, C++ veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b2e8e-152">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="b2e8e-153">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b2e8e-153">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="b2e8e-154">Varsayılan olarak <xref:System.ServiceModel.NetMsmqBinding>, aktarım güvenliği etkin.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="b2e8e-155">İki ilgili özellik yok MSMQ taşıma güvenlik yani <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ve <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` varsayılan olarak, kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-155">There are two relevant properties for MSMQ transport security namely, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="b2e8e-156">MSMQ imzalama özelliği ve kimlik doğrulaması sağlamak için bir etki alanının parçası olması gerekir ve MSMQ active directory tümleştirme seçeneği yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-156">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="b2e8e-157">Bu ölçütleri karşılamayan bir bilgisayarda bu örneği çalıştırmak, bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-157">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="b2e8e-158">Örnek, bir çalışma grubuna veya active directory tümleştirmesi olmadan alanına katılmış bir bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b2e8e-158">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="b2e8e-159">Bilgisayarınız bir etki alanının parçası değil veya yüklü active directory tümleştirmesi yok, aktarım güvenliği devre dışı kimlik doğrulama modu ve koruma düzeyi ayarlayarak kapatma `None` aşağıdaki örnek yapılandırmada gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-159">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <services>  
        <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
                 behaviorConfiguration="OrderTakerServiceBehavior">  
          <host>  
            <baseAddresses>  
              <add baseAddress=  
             "http://localhost:8000/ServiceModelSamples/service"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint  
              address=  
            "net.msmq://localhost/private/ServiceModelSamplesSession"  
              binding="netMsmqBinding"  
              bindingConfiguration="Binding1"  
           contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
          <!-- The mex endpoint is exposed at-->      
          <!--http://localhost:8000/ServiceModelSamples/service/mex. -->  
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
            <behavior name="OrderTakerServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2.  <span data-ttu-id="b2e8e-160">Örneği çalıştırmadan önce yapılandırma hem sunucu hem de istemci değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-160">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b2e8e-161">İçin güvenlik modunu ayarlama `None` ayarlamakla eşdeğerdir <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, ve `Message` güvenlik `None`.</span><span class="sxs-lookup"><span data-stu-id="b2e8e-161">Setting security mode to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
