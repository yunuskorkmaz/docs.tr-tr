---
title: Oturumlar ve Kuyruklar
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: 8a342b185c7965e9ee0ff9941a09e00fc392ad4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144105"
---
# <a name="sessions-and-queues"></a><span data-ttu-id="4f1fb-102">Oturumlar ve Kuyruklar</span><span class="sxs-lookup"><span data-stu-id="4f1fb-102">Sessions and Queues</span></span>
<span data-ttu-id="4f1fb-103">Bu örnek, İleti Queuing (MSMQ) aktarımı üzerinden sıraya alınan iletişimde ilgili iletilerin nasıl gönderilip alınılsüreceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-103">This sample demonstrates how to send and receive a set of related messages in queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="4f1fb-104">Bu örnek `netMsmqBinding` bağlama kullanır.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="4f1fb-105">Hizmet, sıraya alınan iletileri alan hizmeti gözlemlemenizi sağlayan, kendi kendine barındırılan bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-105">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f1fb-106">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4f1fb-107">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4f1fb-108">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4f1fb-109">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4f1fb-110">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 <span data-ttu-id="4f1fb-111">Sıralı iletişimde, istemci bir sıra kullanarak hizmete iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-111">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="4f1fb-112">Daha doğrusu, istemci sıraya ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-112">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="4f1fb-113">Hizmet, kuyruktan iletiler alır.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-113">The service receives messages from the queue.</span></span> <span data-ttu-id="4f1fb-114">Bu nedenle, hizmet ve istemci, bir sıra kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-114">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="4f1fb-115">Bazen, istemci bir grupta birbiriyle ilişkili bir dizi ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-115">Sometimes, a client sends a set of messages that are related to each other in a group.</span></span> <span data-ttu-id="4f1fb-116">İletilerin birlikte veya belirli bir sırada işlenmesi gerektiğinde, tek bir alıcı uygulama tarafından işlenmek üzere onları gruplandırmak için bir kuyruk kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-116">When messages must be processed together or in a specified order, a queue can be used to group them together, for processing by a single receiving application.</span></span> <span data-ttu-id="4f1fb-117">Bu, özellikle bir sunucu grubunda birden fazla uygulama aldığında önemlidir ve bir ileti grubunun aynı alıcı uygulama tarafından işlendiğinden emin olmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-117">This is particularly important when there are several receiving applications on a group of servers and it is necessary to ensure that a group of messages is processed by the same receiving application.</span></span> <span data-ttu-id="4f1fb-118">Sıralanan oturumlar, aynı anda işlenmesi gereken ilgili ileti kümesini göndermek ve almak için kullanılan bir mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-118">Queued sessions are a mechanism used to send and receive a related set of messages that must get processed all at once.</span></span> <span data-ttu-id="4f1fb-119">Sıralanmış oturumlar, bu deseni sergilemek için bir hareket gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-119">Queued sessions require a transaction to exhibit this pattern.</span></span>  
  
 <span data-ttu-id="4f1fb-120">Örnekte, istemci tek bir işlem kapsamında bir oturumun parçası olarak hizmete bir dizi ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-120">In the sample, the client sends a number of messages to the service as part of a session within the scope of a single transaction.</span></span>  
  
 <span data-ttu-id="4f1fb-121">Hizmet sözleşmesi, `IOrderTaker`kuyruklarla kullanıma uygun tek yönlü bir hizmeti tanımlayan sözleşmedir.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-121">The service contract is `IOrderTaker`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="4f1fb-122">Aşağıdaki <xref:System.ServiceModel.SessionMode> örnek kodda gösterilen sözleşmede kullanılan iletilerin oturumun bir parçası olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-122">The <xref:System.ServiceModel.SessionMode> used in the contract shown in the following sample code indicates that the messages are part of the session.</span></span>  

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

 <span data-ttu-id="4f1fb-123">Hizmet, hizmet işlemlerini, ilk işlemin bir harekette kaydedilen, ancak hareketi otomatik olarak tamamlamayan şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-123">The service defines service operations in such a way that the first operation enlists in a transaction but does not automatically complete the transaction.</span></span> <span data-ttu-id="4f1fb-124">Sonraki işlemler de aynı işlem de kaydolmak, ancak otomatik olarak tamamlanmaz.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-124">Subsequent operations also enlist in the same transaction but do not automatically complete.</span></span> <span data-ttu-id="4f1fb-125">Oturumdaki son işlem işlemi otomatik olarak tamamlar.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-125">The last operation in the session automatically completes the transaction.</span></span> <span data-ttu-id="4f1fb-126">Bu nedenle, aynı işlem hizmet sözleşmesinde çeşitli işlem çağrıları için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-126">Thus, the same transaction is used for several operation invocations in the service contract.</span></span> <span data-ttu-id="4f1fb-127">İşlemlerden herhangi biri özel durum atarsa, işlem geri alınır ve oturum sıraya geri alınır.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-127">If any of the operations throw an exception, then the transaction rolls back and the session is put back into the queue.</span></span> <span data-ttu-id="4f1fb-128">Son işlemin başarıyla tamamlanmasından sonra, işlem yapılır.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-128">Upon successful completion of the last operation, the transaction is committed.</span></span> <span data-ttu-id="4f1fb-129">Hizmet, `PerSession` bir <xref:System.ServiceModel.InstanceContextMode> oturumdaki tüm iletileri hizmetin aynı örneğinde almak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-129">The service uses `PerSession` as the <xref:System.ServiceModel.InstanceContextMode> to receive all messages in a session on the same instance of the service.</span></span>  

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

 <span data-ttu-id="4f1fb-130">Hizmet kendi kendine barındırılır.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-130">The service is self hosted.</span></span> <span data-ttu-id="4f1fb-131">MSMQ aktarımını kullanırken, kullanılan sıra önceden oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-131">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="4f1fb-132">Bu el ile veya kod yoluyla yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-132">This can be done manually or through code.</span></span> <span data-ttu-id="4f1fb-133">Bu örnekte, hizmet <xref:System.Messaging> sıranın varlığını denetlemek için kod içerir ve gerekirse bunu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-133">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="4f1fb-134">Sıra adı <xref:System.Configuration.ConfigurationManager.AppSettings%2A> sınıfı kullanarak yapılandırma dosyasından okunur.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-134">The queue name is read from the configuration file using the <xref:System.Configuration.ConfigurationManager.AppSettings%2A> class.</span></span>  

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

 <span data-ttu-id="4f1fb-135">MSMQ sıra adı yapılandırma dosyasının bir uygulama Ayarları bölümünde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="4f1fb-136">Hizmetin bitiş noktası yapılandırma dosyasının system.serviceModel bölümünde tanımlanır ve bağlamayı `netMsmqBinding` belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-136">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>  
  
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
  
 <span data-ttu-id="4f1fb-137">İstemci bir hareket kapsamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-137">The client creates a transaction scope.</span></span> <span data-ttu-id="4f1fb-138">Oturumdaki tüm iletiler işlem kapsamı içinde kuyruğa gönderilir ve tüm iletilerin başarılı veya başarısız olduğu bir atomik birim olarak ele alınmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-138">All messages in the session are sent to the queue within the transaction scope, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="4f1fb-139">Hareket arayarak <xref:System.Transactions.TransactionScope.Complete%2A>işlenir.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-139">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A>.</span></span>  

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
> <span data-ttu-id="4f1fb-140">Oturumdaki tüm iletiler için yalnızca tek bir işlem kullanabilirsiniz ve işlem gerçekleştirmeden önce oturumdaki tüm iletilerin gönderilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-140">You can use only a single transaction for all messages in the session and all messages in the session must be sent before committing the transaction.</span></span> <span data-ttu-id="4f1fb-141">İstemciyi kapatmak oturumu kapatır.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-141">Closing the client closes the session.</span></span> <span data-ttu-id="4f1fb-142">Bu nedenle, oturumdaki tüm iletileri sıraya göndermek için işlem tamamlanmadan önce istemcinin kapatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-142">Therefore, the client has to be closed before the transaction is completed to send all messages in the session to the queue.</span></span>  
  
 <span data-ttu-id="4f1fb-143">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsolu pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-143">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="4f1fb-144">Hizmetin istemciden ileti aldığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-144">You can see the service receive messages from the client.</span></span> <span data-ttu-id="4f1fb-145">Hizmeti ve istemciyi kapatmak için her konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-145">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="4f1fb-146">Kuyruk kullanımda olduğundan, istemci ve hizmetin aynı anda çalışır durumda olması gerekmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-146">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="4f1fb-147">İstemciyi çalıştırabilir, kapatabilir ve sonra hizmeti başlatabilir ve yine de iletilerini alır.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-147">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>  
  
 <span data-ttu-id="4f1fb-148">Müşteriye.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-148">On the client.</span></span>  
  
```console  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="4f1fb-149">Serviste.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-149">On the service.</span></span>  
  
```console  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4f1fb-150">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="4f1fb-150">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4f1fb-151">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4f1fb-152">Çözümün C#, C++veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation Örneklerini Oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-152">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="4f1fb-153">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-153">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="4f1fb-154">Varsayılan olarak <xref:System.ServiceModel.NetMsmqBinding>, aktarım güvenliği etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="4f1fb-155">MSMQ aktarım güvenliği için iki <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ilgili <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` özellik vardır, yani, ve `Windows` varsayılan olarak, kimlik `Sign`doğrulama modu ayarlanır ve koruma düzeyi .</span><span class="sxs-lookup"><span data-stu-id="4f1fb-155">There are two relevant properties for MSMQ transport security namely, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="4f1fb-156">MSMQ'nun kimlik doğrulama ve imzalama özelliğini sağlaması için bir etki alanının parçası olması ve MSMQ için etkin dizin tümleştirme seçeneğinin yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-156">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="4f1fb-157">Bu örneği bu ölçütleri karşılamayan bir bilgisayarda çalıştırıyorsanız bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-157">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="4f1fb-158">Bir çalışma grubuna katılan veya etkin dizin tümleştirmesi olmayan bir bilgisayarda örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="4f1fb-158">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1. <span data-ttu-id="4f1fb-159">Bilgisayarınız bir etki alanının parçası değilse veya etkin dizin tümleştirmesi yüklü değilse, kimlik doğrulama `None` modunu ve koruma düzeyini aşağıdaki örnek yapılandırmada gösterildiği gibi ayarlayarak aktarım güvenliğini kapatın.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-159">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration.</span></span>  
  
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
  
2. <span data-ttu-id="4f1fb-160">Örneği çalıştırmadan önce hem sunucuda hem de istemcide yapılandırmayı değiştirdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-160">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4f1fb-161">Güvenlik modunu `None` ayarla, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>ayara `Message` ve `None`güvenlik 'e eşittir.</span><span class="sxs-lookup"><span data-stu-id="4f1fb-161">Setting security mode to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
