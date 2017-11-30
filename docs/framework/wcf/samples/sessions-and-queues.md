---
title: Oturumlar ve Kuyruklar
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
caps.latest.revision: "27"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dffee557bea81c769038729a60b9d270f0f28c6b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="sessions-and-queues"></a><span data-ttu-id="40c3c-102">Oturumlar ve Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="40c3c-102">Sessions and Queues</span></span>
<span data-ttu-id="40c3c-103">Bu örnek, gönderip bir dizi ilgili ileti kuyruğa alınan iletişim Message Queuing (MSMQ) aktarımı üzerinden gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="40c3c-103">This sample demonstrates how to send and receive a set of related messages in queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="40c3c-104">Bu örnekte `netMsmqBinding` bağlama.</span><span class="sxs-lookup"><span data-stu-id="40c3c-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="40c3c-105">Hizmeti, sıraya alınan iletileri alma hizmeti izlemek etkinleştirmek için bir kendi kendini barındıran konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="40c3c-105">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40c3c-106">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="40c3c-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="40c3c-107">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="40c3c-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="40c3c-108">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="40c3c-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="40c3c-109">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="40c3c-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="40c3c-110">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="40c3c-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 <span data-ttu-id="40c3c-111">Kuyruğa alınan iletişim, istemci bir sıra kullanarak hizmeti ile iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="40c3c-111">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="40c3c-112">Daha hassas bir şekilde istemci kuyruğa ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="40c3c-112">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="40c3c-113">Hizmet kuyruktan iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="40c3c-113">The service receives messages from the queue.</span></span> <span data-ttu-id="40c3c-114">Hizmet ve istemci bu nedenle, bir sıra kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="40c3c-114">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="40c3c-115">Bazı durumlarda, bir istemci bir dizi birbirlerine bir grupta ilişkili ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="40c3c-115">Sometimes, a client sends a set of messages that are related to each other in a group.</span></span> <span data-ttu-id="40c3c-116">İletiler birlikte ya da belirli bir sırada işlenmesi gereken, bir sıra bunları, tek bir alıcı uygulaması tarafından işlenmek gruplamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="40c3c-116">When messages must be processed together or in a specified order, a queue can be used to group them together, for processing by a single receiving application.</span></span> <span data-ttu-id="40c3c-117">Bu bir sunucu grubu üzerinde birkaç alıcı uygulamalar vardır ve iletileri bir grup aynı alıcı uygulama tarafından işlendiğinden emin olmak için gerekli olduğunda özellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="40c3c-117">This is particularly important when there are several receiving applications on a group of servers and it is necessary to ensure that a group of messages is processed by the same receiving application.</span></span> <span data-ttu-id="40c3c-118">Sıraya alınan oturumları ilgili bir dizi tümünü bir defada işlenen ileti alıp göndermek için kullanılan bir sistemdir.</span><span class="sxs-lookup"><span data-stu-id="40c3c-118">Queued sessions are a mechanism used to send and receive a related set of messages that must get processed all at once.</span></span> <span data-ttu-id="40c3c-119">Sıraya alınan oturumları bu deseni göstermesi için bir işlem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="40c3c-119">Queued sessions require a transaction to exhibit this pattern.</span></span>  
  
 <span data-ttu-id="40c3c-120">Örnekte, istemci hizmet tek bir işlem kapsamı içinde oturumun bir parçası olarak çeşitli iletiler gönderir.</span><span class="sxs-lookup"><span data-stu-id="40c3c-120">In the sample, the client sends a number of messages to the service as part of a session within the scope of a single transaction.</span></span>  
  
 <span data-ttu-id="40c3c-121">Hizmet sözleşme `IOrderTaker`, kuyruklar ile kullanım için uygun bir tek yönlü hizmet tanımlar.</span><span class="sxs-lookup"><span data-stu-id="40c3c-121">The service contract is `IOrderTaker`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="40c3c-122"><xref:System.ServiceModel.SessionMode> Aşağıda gösterildiği sözleşmelerde kullanılan örnek kod iletileri oturumunun parçası olan gösterir.</span><span class="sxs-lookup"><span data-stu-id="40c3c-122">The <xref:System.ServiceModel.SessionMode> used in the contract shown in the following sample code indicates that the messages are part of the session.</span></span>  
  
```  
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
  
 <span data-ttu-id="40c3c-123">Hizmetin hizmet işlemleri ilk işlem işlemde kaydeder ancak otomatik olarak hareket tamamlanmazsa bir şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="40c3c-123">The service defines service operations in such a way that the first operation enlists in a transaction but does not automatically complete the transaction.</span></span> <span data-ttu-id="40c3c-124">Ayrıca sonraki işlemleri aynı işlemde listeleme ancak otomatik olarak tamamlanmaz.</span><span class="sxs-lookup"><span data-stu-id="40c3c-124">Subsequent operations also enlist in the same transaction but do not automatically complete.</span></span> <span data-ttu-id="40c3c-125">Son işlem oturumda işlem otomatik olarak tamamlar.</span><span class="sxs-lookup"><span data-stu-id="40c3c-125">The last operation in the session automatically completes the transaction.</span></span> <span data-ttu-id="40c3c-126">Bu nedenle, aynı işlem hizmet sözleşmesinde birkaç işlem çağrıları için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40c3c-126">Thus, the same transaction is used for several operation invocations in the service contract.</span></span> <span data-ttu-id="40c3c-127">İşlemlerden birini bir özel durum, işlem geri alınır ve oturum geri sıraya konur.</span><span class="sxs-lookup"><span data-stu-id="40c3c-127">If any of the operations throw an exception, then the transaction rolls back and the session is put back into the queue.</span></span> <span data-ttu-id="40c3c-128">Son işlemi başarıyla tamamlandıktan sonra işlemin taahhüt eder.</span><span class="sxs-lookup"><span data-stu-id="40c3c-128">Upon successful completion of the last operation, the transaction is committed.</span></span> <span data-ttu-id="40c3c-129">Hizmet kullandığı `PerSession` olarak <xref:System.ServiceModel.InstanceContextMode> aynı hizmet örneği üzerinde bir oturumdaki tüm iletileri almak için.</span><span class="sxs-lookup"><span data-stu-id="40c3c-129">The service uses `PerSession` as the <xref:System.ServiceModel.InstanceContextMode> to receive all messages in a session on the same instance of the service.</span></span>  
  
```  
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
  
 <span data-ttu-id="40c3c-130">Kendi kendini barındırılan hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="40c3c-130">The service is self hosted.</span></span> <span data-ttu-id="40c3c-131">MSMQ taşıma kullanırken, sıranın kullanılan önceden oluşturulmuş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="40c3c-131">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="40c3c-132">Bu, el ile veya kod aracılığıyla yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="40c3c-132">This can be done manually or through code.</span></span> <span data-ttu-id="40c3c-133">Bu örnekte, hizmeti içeren <xref:System.Messaging> sıranın varlığını denetlemek için kod ve, gerekirse oluşturur.</span><span class="sxs-lookup"><span data-stu-id="40c3c-133">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="40c3c-134">Kuyruk adı kullanarak yapılandırma dosyası okunduğu <xref:System.Configuration.ConfigurationManager.AppSettings%2A> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="40c3c-134">The queue name is read from the configuration file using the <xref:System.Configuration.ConfigurationManager.AppSettings%2A> class.</span></span>  
  
```  
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
  
 <span data-ttu-id="40c3c-135">MSMQ kuyruk adı bir yapılandırma dosyasının appSettings bölümünde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="40c3c-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="40c3c-136">Hizmeti için uç noktaya yapılandırma dosyası system.serviceModel bölümünde tanımlanan ve belirten `netMsmqBinding` bağlama.</span><span class="sxs-lookup"><span data-stu-id="40c3c-136">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>  
  
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
  
 <span data-ttu-id="40c3c-137">İstemci bir işlem kapsamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="40c3c-137">The client creates a transaction scope.</span></span> <span data-ttu-id="40c3c-138">Oturumdaki tüm iletilerin sıra burada tüm iletileri başarılı veya başarısız atomik bir birim olarak değerlendirilmesi için neden işlem kapsamı içinde gönderilir.</span><span class="sxs-lookup"><span data-stu-id="40c3c-138">All messages in the session are sent to the queue within the transaction scope, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="40c3c-139">İşlem çağırarak gerçekleştirilir <xref:System.Transactions.TransactionScope.Complete%2A>.</span><span class="sxs-lookup"><span data-stu-id="40c3c-139">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A>.</span></span>  
  
```  
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
>  <span data-ttu-id="40c3c-140">Oturumdaki tüm iletilerin işlem gerçekleştirmeden önce gönderilmesine ve yalnızca tek bir işlem oturumda tüm iletiler için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40c3c-140">You can use only a single transaction for all messages in the session and all messages in the session must be sent before committing the transaction.</span></span> <span data-ttu-id="40c3c-141">İstemci kapatma oturumunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="40c3c-141">Closing the client closes the session.</span></span> <span data-ttu-id="40c3c-142">Bu nedenle, istemci tüm iletileri oturumda kuyruğa göndermek için işlem tamamlanmadan önce kapatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="40c3c-142">Therefore, the client has to be closed before the transaction is completed to send all messages in the session to the queue.</span></span>  
  
 <span data-ttu-id="40c3c-143">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="40c3c-143">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="40c3c-144">İstemci hizmeti alma iletileri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40c3c-144">You can see the service receive messages from the client.</span></span> <span data-ttu-id="40c3c-145">Her konsol penceresinde hizmet ve istemci kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="40c3c-145">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="40c3c-146">Queuing kullanımda olduğundan, istemci ve hizmet aynı anda açık ve çalışıyor olması sahip olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="40c3c-146">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="40c3c-147">İstemcisini çalıştıran, kapatmak ve hizmeti başlatın ve hala kendi iletilerini alır.</span><span class="sxs-lookup"><span data-stu-id="40c3c-147">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>  
  
 <span data-ttu-id="40c3c-148">İstemci üzerinde.</span><span class="sxs-lookup"><span data-stu-id="40c3c-148">On the client.</span></span>  
  
```  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="40c3c-149">Hizmette.</span><span class="sxs-lookup"><span data-stu-id="40c3c-149">On the service.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="40c3c-150">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="40c3c-150">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="40c3c-151">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="40c3c-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="40c3c-152">C#, C++, Visual Basic .NET edition çözümü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="40c3c-152">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="40c3c-153">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="40c3c-153">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="40c3c-154">Varsayılan olarak <xref:System.ServiceModel.NetMsmqBinding>, taşıma güvenliği etkindir.</span><span class="sxs-lookup"><span data-stu-id="40c3c-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="40c3c-155">İki ilgili özellikler yok MSMQ taşıma güvenliği için ayrıca <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ve <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` varsayılan olarak, kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`.</span><span class="sxs-lookup"><span data-stu-id="40c3c-155">There are two relevant properties for MSMQ transport security namely, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="40c3c-156">Bir etki alanının parçası olması gerekir ve kimlik doğrulaması ve imzalama özelliği, MSMQ için MSMQ active directory tümleştirme seçeneğini yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="40c3c-156">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="40c3c-157">Bu ölçütleri karşılayan olmayan bir bilgisayarda bu örnek çalıştırırsanız, bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="40c3c-157">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="40c3c-158">Örnek bir çalışma grubu ya da active directory tümleştirmesi olmadan alanına katılmış bir bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="40c3c-158">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="40c3c-159">Bilgisayarınız bir etki alanının parçası değil veya yüklü active directory tümleştirmesi yok gerekirse kimlik doğrulama modu ve koruma düzeyini ayarlayarak taşıma güvenliği devre dışı bırakmak `None` aşağıdaki örnek yapılandırmada gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="40c3c-159">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration.</span></span>  
  
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
  
2.  <span data-ttu-id="40c3c-160">Örneği çalıştırmadan önce hem sunucu hem de istemci yapılandırmasına değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="40c3c-160">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="40c3c-161">İçin güvenlik modunu ayarlama `None` ayarına eşdeğerdir <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, ve `Message` güvenlik `None`.</span><span class="sxs-lookup"><span data-stu-id="40c3c-161">Setting security mode to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c3c-162">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40c3c-162">See Also</span></span>
