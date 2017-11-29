---
title: "MSMQ Etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
caps.latest.revision: "29"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 99fa5a5b76b90a6c16fa2bbd8ee11e91d77d47a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="msmq-activation"></a><span data-ttu-id="f8a84-102">MSMQ Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="f8a84-102">MSMQ Activation</span></span>
<span data-ttu-id="f8a84-103">Bu örnek, bir iletiyi kuyruktan okunur uygulamaların Windows İşlem Etkinleştirme Hizmeti (WAS) barındırmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f8a84-103">This sample demonstrates how to host applications in Windows Process Activation Service (WAS) that are read from a message queue.</span></span> <span data-ttu-id="f8a84-104">Bu örnekte `netMsmqBinding` ve dayanır [iki yönlü iletişim](../../../../docs/framework/wcf/samples/two-way-communication.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="f8a84-104">This sample uses the `netMsmqBinding` and is based on the [Two-Way Communication](../../../../docs/framework/wcf/samples/two-way-communication.md) sample.</span></span> <span data-ttu-id="f8a84-105">Bu durumda Web barındırdığı bir uygulama hizmetidir ve istemci kendiliğinden barındırılır ve gönderilen satınalma siparişi durumunu izlemek için konsola çıkarır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-105">The service in this case is a Web-hosted application and the client is self-hosted and outputs to the console to observe the status of purchase orders submitted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8a84-106">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8a84-107">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="f8a84-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f8a84-108">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f8a84-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  <span data-ttu-id="f8a84-109">\<InstallDrive >: \WF_WCF_Samples</span><span class="sxs-lookup"><span data-stu-id="f8a84-109">\<InstallDrive>:\WF_WCF_Samples</span></span>  
>   
>  <span data-ttu-id="f8a84-110">Bu dizin mevcut değilse, Git [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] HYPERLINK "http://go.microsoft.com/fwlink/?LinkId=150780" \t "_blank" ve [!INCLUDE[wf](../../../../includes/wf-md.md)] için örnekleri [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] tüm indirmek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="f8a84-110">If this directory does not exist, go to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] HYPERLINK "http://go.microsoft.com/fwlink/?LinkId=150780" \t "_blank"  and [!INCLUDE[wf](../../../../includes/wf-md.md)] Samples for [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] to download all [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f8a84-111">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f8a84-111">This sample is located in the following directory.</span></span>  
>   
>  <span data-ttu-id="f8a84-112">\<InstallDrive >: \Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span><span class="sxs-lookup"><span data-stu-id="f8a84-112">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span></span>  
  
 <span data-ttu-id="f8a84-113">Windows İşlem Etkinleştirme Hizmeti (WAS), yeni bir işlem etkinleştirme mekanizmasıdır için [!INCLUDE[lserver](../../../../includes/lserver-md.md)], daha önce yalnızca HTTP tabanlı uygulamalara HTTP olmayan protokolleri kullanan uygulamalar için kullanılabilen IIS benzeri özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8a84-113">Windows Process Activation Service (WAS), the new process activation mechanism for [!INCLUDE[lserver](../../../../includes/lserver-md.md)], provides IIS-like features that were previously only available to HTTP-based applications to applications that use non-HTTP protocols.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="f8a84-114">Dinleyici Bağdaştırıcısı arabirimi tarafından desteklenen HTTP olmayan protokolleri üzerinden alınan etkinleştirme isteklerini iletişim kurmak için kullandığı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]TCP, Adlandırılmış Kanallar ve MSMQ gibi.</span><span class="sxs-lookup"><span data-stu-id="f8a84-114"> uses the Listener Adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], such as TCP, Named Pipes, and MSMQ.</span></span> <span data-ttu-id="f8a84-115">HTTP olmayan protokolleri isteklerini almak için işlevselliği SMSvcHost.exe içinde çalışan yönetilen Windows Hizmetleri tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-115">The functionality for receiving requests over non-HTTP protocols is hosted by managed Windows services running in SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="f8a84-116">Sıradaki iletileri göre sıraya alınan uygulamaları Net.Msmq Dinleyici Bağdaştırıcısı hizmeti (NetMsmqActivator) etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="f8a84-116">The Net.Msmq Listener Adapter service (NetMsmqActivator) activates queued applications based on messages in the queue.</span></span>  
  
 <span data-ttu-id="f8a84-117">İstemci bir işlem kapsamı içinde hizmetinden satınalma siparişi gönderir.</span><span class="sxs-lookup"><span data-stu-id="f8a84-117">The client sends purchase orders to the service from within the scope of a transaction.</span></span> <span data-ttu-id="f8a84-118">Hizmet bir işlem içinde siparişleri alır ve bunları işler.</span><span class="sxs-lookup"><span data-stu-id="f8a84-118">The service receives the orders in a transaction and processes them.</span></span> <span data-ttu-id="f8a84-119">Hizmeti daha sonra geri sırasını durumunu istemcisiyle çağırır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-119">The service then calls back the client with the status of the order.</span></span> <span data-ttu-id="f8a84-120">Çift yönlü iletişimi kolaylaştırmak için istemci ve hizmet enqueue satınalma siparişi ve sipariş durumu sıralara kullanın.</span><span class="sxs-lookup"><span data-stu-id="f8a84-120">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="f8a84-121">Hizmet sözleşmesi `IOrderProcessor` queuing ile birlikte çalışan tek yönlü hizmet işlemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f8a84-121">The service contract `IOrderProcessor` defines the one-way service operations that work with queuing.</span></span> <span data-ttu-id="f8a84-122">Hizmet işlemini yanıt uç nokta sırasını durumları istemciye göndermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-122">The service operation uses the reply endpoint to send order statuses to the client.</span></span> <span data-ttu-id="f8a84-123">Yanıt uç noktanın, sipariş durumu istemciye göndermek için kullanılan sıra URI'sini adresidir.</span><span class="sxs-lookup"><span data-stu-id="f8a84-123">The reply endpoint's address is the URI of the queue used to send the order status back to the client.</span></span> <span data-ttu-id="f8a84-124">Uygulama işlem sırası bu sözleşmenin uygular.</span><span class="sxs-lookup"><span data-stu-id="f8a84-124">The order processing application implements this contract.</span></span>  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po,   
                                           string reportOrderStatusTo);  
}  
```  
  
 <span data-ttu-id="f8a84-125">İstemci tarafından belirtildiği için sipariş durumu gönderilecek yanıt sözleşmesi.</span><span class="sxs-lookup"><span data-stu-id="f8a84-125">The reply contract to send order status to is specified by the client.</span></span> <span data-ttu-id="f8a84-126">İstemci, sipariş durumu sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="f8a84-126">The client implements the order status contract.</span></span> <span data-ttu-id="f8a84-127">Hizmet, bu sözleşmenin oluşturulan istemci sipariş durumu istemciye göndermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-127">The service uses the generated client of this contract to send order status back to the client.</span></span>  
  
```csharp  
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```  
  
 <span data-ttu-id="f8a84-128">Hizmet işlemini gönderilen satın alma siparişi işler.</span><span class="sxs-lookup"><span data-stu-id="f8a84-128">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="f8a84-129"><xref:System.ServiceModel.OperationBehaviorAttribute> Otomatik kaydı kuyruk ve hizmet işleminin tamamlanması hareket otomatik tamamlama ileti almak için kullanılan işlem belirtmek üzere hizmet işlemi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-129">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in the transaction that is used to receive the message from the queue and automatic completion of the transaction on completion of the service operation.</span></span> <span data-ttu-id="f8a84-130">`Orders` Sınıfı, sipariş işleme işlevselliği yalıtır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-130">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="f8a84-131">Bu durumda, satın alma siparişi bir sözlüğe ekler.</span><span class="sxs-lookup"><span data-stu-id="f8a84-131">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="f8a84-132">Hizmet işlemi içinde kayıtlı işlem işlemlerinde kullanılabilir `Orders` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f8a84-132">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="f8a84-133">Sipariş durumu hakkında istemciye gönderilen satın alma siparişi işleme ek olarak hizmet işlemi yanıtlar.</span><span class="sxs-lookup"><span data-stu-id="f8a84-133">The service operation, in addition to processing the submitted purchase order, replies back to the client about the status of the order.</span></span>  
  
```csharp  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
        Console.WriteLine("Sending back order status information");  
        NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
        msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
        OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
        // please note that the same transaction that is used to dequeue purchase order is used  
        // to send back order status  
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
        {  
            client.OrderStatus(po.PONumber, po.Status);  
            scope.Complete();  
        }  
    }  
```  
  
 <span data-ttu-id="f8a84-134">Kullanılacak bağlama istemci, bir yapılandırma dosyası kullanarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="f8a84-134">The client binding to use is specified using a configuration file.</span></span>  
  
 <span data-ttu-id="f8a84-135">MSMQ kuyruk adı bir yapılandırma dosyasının appSettings bölümünde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f8a84-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="f8a84-136">Hizmeti için uç noktaya yapılandırma dosyası System.serviceModel bölümünde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-136">The endpoint for the service is defined in the System.serviceModel section of the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8a84-137">MSMQ sırası ad ve uç nokta adresi biraz farklı adresleme yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f8a84-137">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="f8a84-138">MSMQ kuyruk adı, ters eğik çizgi ayırıcıları yolundaki ve yerel bilgisayar için bir nokta (.) kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-138">The MSMQ queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="f8a84-139">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Uç noktası adresi bir net.msmq belirtir: şeması, "localhost" yerel bilgisayarda ve eğik, yolunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-139">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint address specifies a net.msmq: scheme, uses "localhost" for the local computer, and uses forward slashes in its path.</span></span> <span data-ttu-id="f8a84-140">Uzak bilgisayarda bulunan bir sıradan okumak için Değiştir "." ve "localhost" uzak bilgisayar adı.</span><span class="sxs-lookup"><span data-stu-id="f8a84-140">To read from a queue that is hosted on the remote computer, replace the "." and "localhost" to the remote computer name.</span></span>  
  
 <span data-ttu-id="f8a84-141">Sınıfın adını .svc dosyasıyla WAS hizmeti kodunda barındırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-141">A .svc file with the name of the class is used to host the service code in WAS.</span></span>  
  
 <span data-ttu-id="f8a84-142">Service.svc dosyası oluşturmak için bir yönergeyi içeren `OrderProcessorService`.</span><span class="sxs-lookup"><span data-stu-id="f8a84-142">The Service.svc file itself contains a directive to create the `OrderProcessorService`.</span></span>  
  
```xml  
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>  
```  
  
 <span data-ttu-id="f8a84-143">Service.svc dosya System.Transactions.dll yüklendiğinden emin olmak için bir derleme yönergesi de içerir.</span><span class="sxs-lookup"><span data-stu-id="f8a84-143">The Service.svc file also contains an assembly directive to ensure that System.Transactions.dll is loaded.</span></span>  
  
```xml  
<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>  
```  
  
 <span data-ttu-id="f8a84-144">İstemci bir işlem kapsamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f8a84-144">The client creates a transaction scope.</span></span> <span data-ttu-id="f8a84-145">Hizmet ile iletişim, burada tüm iletileri başarılı veya başarısız atomik bir birim olarak değerlendirilmesi için neden işlem kapsamı içinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="f8a84-145">Communication with the service takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="f8a84-146">İşlem çağırarak gerçekleştirilir `Complete` işlem kapsamında.</span><span class="sxs-lookup"><span data-stu-id="f8a84-146">The transaction is committed by calling `Complete` on the transaction scope.</span></span>  
  
```csharp  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
    // Open the ServiceHostBase to create listeners and start listening   
    // for order status messages.  
    serviceHost.Open();  
  
    // Create a proxy with given client endpoint configuration  
    OrderProcessorClient client = new OrderProcessorClient();  
  
    // Create the purchase order  
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
  
    //Create a transaction scope.  
    using (TransactionScope scope = new   
        TransactionScope(TransactionScopeOption.Required))  
    {  
        // Make a queued call to submit the purchase order  
        client.SubmitPurchaseOrder(po,   
       "net.msmq://localhost/private/ServiceModelSamplesOrder/OrderStatus");  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Closing the client gracefully closes the connection and cleans up   
    //resources  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHostBase to shutdown the service.  
    serviceHost.Close();  
    }  
```  
  
 <span data-ttu-id="f8a84-147">İstemci kodu uygulayan `IOrderStatus` hizmetinden sipariş durumunu almak sözleşme.</span><span class="sxs-lookup"><span data-stu-id="f8a84-147">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="f8a84-148">Bu durumda, sipariş durumu yazdırır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-148">In this case, it prints out the order status.</span></span>  
  
```csharp  
[ServiceBehavior]  
public class OrderStatusService : IOrderStatus  
{  
    [OperationBehavior(TransactionAutoComplete = true,   
                        TransactionScopeRequired = true)]  
    public void OrderStatus(string poNumber, string status)  
    {  
        Console.WriteLine("Status of order {0}:{1} ",   
                                         poNumber , status);  
    }  
}  
```  
  
 <span data-ttu-id="f8a84-149">Durum sırasını oluşturulan `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f8a84-149">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="f8a84-150">İstemci yapılandırması, aşağıdaki örnek yapılandırmada gösterildiği gibi sipariş durumu hizmeti barındırmak için sipariş durum hizmet yapılandırmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="f8a84-150">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
```csharp  
<appSettings>  
    <!-- use appSetting to configure MSMQ queue name -->  
    <add key="targetQueueName" value=".\private$\ServiceModelSamples/service.svc" />  
    <add key="responseQueueName" value=".\private$\ServiceModelSamples/OrderStatus" />  
  </appSettings>  
  
<system.serviceModel>  
  
    <services>  
      <service   
         name="Microsoft.ServiceModel.Samples.OrderStatusService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamples/OrderStatus"  
                  binding="netMsmqBinding"  
                  contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
      </service>  
    </services>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
                address="net.msmq://localhost/private/ServiceModelSamples/service.svc"   
                binding="netMsmqBinding"   
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
    </client>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="f8a84-151">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem sunucu hem de istemci konsol penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f8a84-151">When you run the sample, the client and service activities are displayed in both the server and client console windows.</span></span> <span data-ttu-id="f8a84-152">İstemciden iletilerini sunucu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8a84-152">You can see the server receive messages from the client.</span></span> <span data-ttu-id="f8a84-153">Her konsol penceresinde sunucu ve istemci kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f8a84-153">Press ENTER in each console window to shut down the server and client.</span></span>  
  
 <span data-ttu-id="f8a84-154">İstemci sunucu tarafından gönderilen sipariş durum bilgileri görüntüler:</span><span class="sxs-lookup"><span data-stu-id="f8a84-154">The client displays the order status information sent by the server:</span></span>  
  
```Output  
Press <ENTER> to terminate client.  
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f8a84-155">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="f8a84-155">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f8a84-156">Emin [!INCLUDE[iisver](../../../../includes/iisver-md.md)] WAS etkinleştirme için gerekli olduğundan, yüklenir.</span><span class="sxs-lookup"><span data-stu-id="f8a84-156">Ensure that [!INCLUDE[iisver](../../../../includes/iisver-md.md)] is installed, as it is required for WAS activation.</span></span>  
  
2.  <span data-ttu-id="f8a84-157">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f8a84-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span> <span data-ttu-id="f8a84-158">Ayrıca, yüklemelisiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP olmayan etkinleştirme bileşenleri:</span><span class="sxs-lookup"><span data-stu-id="f8a84-158">In addition, you must install the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] non-HTTP activation components:</span></span>  
  
    1.  <span data-ttu-id="f8a84-159">Gelen **Başlat** menüsünde seçin **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="f8a84-159">From the **Start** menu, choose **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="f8a84-160">Seçin **programlar ve Özellikler**.</span><span class="sxs-lookup"><span data-stu-id="f8a84-160">Select **Programs and Features**.</span></span>  
  
    3.  <span data-ttu-id="f8a84-161">Tıklatın **Windows özelliklerini aç veya Kapat**.</span><span class="sxs-lookup"><span data-stu-id="f8a84-161">Click **Turn Windows Features on or off**.</span></span>  
  
    4.  <span data-ttu-id="f8a84-162">Altında **Özellik Özeti**, tıklatın **Özellik Ekle**.</span><span class="sxs-lookup"><span data-stu-id="f8a84-162">Under **Features Summary**, click **Add Features**.</span></span>  
  
    5.  <span data-ttu-id="f8a84-163">Genişletme **Microsoft .NET Framework 3.0** düğümü ve onay **Windows Communication Foundation HTTP olmayan etkinleştirme** özelliği.</span><span class="sxs-lookup"><span data-stu-id="f8a84-163">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>  
  
3.  <span data-ttu-id="f8a84-164">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f8a84-164">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="f8a84-165">İstemci, bir komut penceresinde client.exe yürüterek çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f8a84-165">Run the client by executing client.exe from a command window.</span></span> <span data-ttu-id="f8a84-166">Bu sıranın oluşturur ve bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="f8a84-166">This creates the queue and sends a message to it.</span></span> <span data-ttu-id="f8a84-167">İleti okuma hizmet sonuçlarını görmek için çalıştıran istemci bırakın</span><span class="sxs-lookup"><span data-stu-id="f8a84-167">Leave the client running to see the result of the service reading the message</span></span>  
  
5.  <span data-ttu-id="f8a84-168">MSMQ Etkinleştirme hizmeti varsayılan olarak ağ hizmeti olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-168">The MSMQ activation service runs as Network Service by default.</span></span> <span data-ttu-id="f8a84-169">Bu nedenle, uygulamayı etkinleştirmek için kullanılan sıra olmalıdır almak ve ara ağ hizmeti için izinler.</span><span class="sxs-lookup"><span data-stu-id="f8a84-169">Therefore, the queue that is used to activate the application must have receive and peek permissions for Network Service.</span></span> <span data-ttu-id="f8a84-170">Bu, Message Queuing MMC kullanarak eklenebilir:</span><span class="sxs-lookup"><span data-stu-id="f8a84-170">This can be added by using the Message Queuing MMC:</span></span>  
  
    1.  <span data-ttu-id="f8a84-171">Gelen **Başlat** menüsünde tıklatın **çalıştırmak**, yazın `Compmgmt.msc` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f8a84-171">From the **Start** menu, click **Run**, then type `Compmgmt.msc` and press ENTER.</span></span>  
  
    2.  <span data-ttu-id="f8a84-172">Altında **hizmetler ve uygulamalar**, genişletin **Message Queuing**.</span><span class="sxs-lookup"><span data-stu-id="f8a84-172">Under **Services and Applications**, expand **Message Queuing**.</span></span>  
  
    3.  <span data-ttu-id="f8a84-173">Tıklatın **özel sıralar**.</span><span class="sxs-lookup"><span data-stu-id="f8a84-173">Click **Private Queues**.</span></span>  
  
    4.  <span data-ttu-id="f8a84-174">Sıranın (servicemodelsamples/Service.svc) sağ tıklatın ve seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="f8a84-174">Right-click the queue (servicemodelsamples/Service.svc) and choose **Properties**.</span></span>  
  
    5.  <span data-ttu-id="f8a84-175">Üzerinde **güvenlik** sekmesini tıklatın, **Ekle** gözlem verin ve alma izinleri ağ hizmeti için.</span><span class="sxs-lookup"><span data-stu-id="f8a84-175">On the **Security** tab, click **Add** and give peek and receive permissions to Network Service.</span></span>  
  
6.  <span data-ttu-id="f8a84-176">MSMQ etkinleştirmeyi desteklemek için Windows İşlem Etkinleştirme Hizmeti'nı (WAS) yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="f8a84-176">Configure the Windows Process Activation Service (WAS) to support MSMQ activation.</span></span>  
  
     <span data-ttu-id="f8a84-177">Kolaylık sağlamak üzere aşağıdaki adımları örnek dizininde bulunan AddMsmqSiteBinding.cmd adlı bir toplu iş dosyası uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-177">As a convenience, the following steps are implemented in a batch file called AddMsmqSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="f8a84-178">NET.MSMQ etkinleştirmeyi desteklemek için varsayılan Web sitesi ilk net.msmq protokole bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-178">To support net.msmq activation, the default Web site must first be bound to the net.msmq protocol.</span></span> <span data-ttu-id="f8a84-179">Bu yapılabilir ile yüklenen appcmd.exe kullanarak [!INCLUDE[iisver](../../../../includes/iisver-md.md)] yönetim araç takımı.</span><span class="sxs-lookup"><span data-stu-id="f8a84-179">This can be done using appcmd.exe, which is installed with the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] management toolset.</span></span> <span data-ttu-id="f8a84-180">(Yönetici) yükseltilmiş komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f8a84-180">From an elevated (administrator) command prompt, run the following command.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="f8a84-181">Bu komut, metnin tek bir satırdır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-181">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="f8a84-182">Bu komut net.msmq site bağlaması varsayılan Web sitesine ekler.</span><span class="sxs-lookup"><span data-stu-id="f8a84-182">This command adds a net.msmq site binding to the default Web site.</span></span>  
  
    2.  <span data-ttu-id="f8a84-183">Bir sitedeki tüm uygulamaları ortak net.msmq bağlama paylaşmak rağmen her uygulama net.msmq desteğini ayrı ayrı etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8a84-183">Although all applications within a site share a common net.msmq binding, each application can enable net.msmq support individually.</span></span> <span data-ttu-id="f8a84-184">NET.MSMQ /servicemodelsamples uygulama için etkinleştirmek için yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f8a84-184">To enable net.msmq for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="f8a84-185">Bu komut, metnin tek bir satırdır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-185">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="f8a84-186">Bu komut /servicemodelsamples uygulama tarafından http://localhost/servicemodelsamples ve net.msmq://localhost/servicemodelsamples kullanarak erişilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8a84-186">This command enables the /servicemodelsamples application to be accessed using http://localhost/servicemodelsamples and net.msmq://localhost/servicemodelsamples.</span></span>  
  
7.  <span data-ttu-id="f8a84-187">Daha önce yapmadıysanız, MSMQ Etkinleştirme hizmeti etkin olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f8a84-187">If you have not done so previously, ensure that the MSMQ activation service is enabled.</span></span> <span data-ttu-id="f8a84-188">Gelen **Başlat** menüsünde tıklatın **çalıştırmak**ve türü `Services.msc`.</span><span class="sxs-lookup"><span data-stu-id="f8a84-188">From the **Start** menu, click **Run**, and type `Services.msc`.</span></span> <span data-ttu-id="f8a84-189">İçin Hizmetler listesi arama **Net.Msmq dinleyici bağdaştırıcısı**.</span><span class="sxs-lookup"><span data-stu-id="f8a84-189">Search the list of services for the **Net.Msmq Listener Adapter**.</span></span> <span data-ttu-id="f8a84-190">Sağ tıklatıp **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="f8a84-190">Right-click and select **Properties**.</span></span> <span data-ttu-id="f8a84-191">Ayarlama **başlangıç türü** için **otomatik**, tıklatın **Uygula** tıklatıp **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="f8a84-191">Set the **Startup Type** to **Automatic**, click **Apply** and click the **Start** button.</span></span> <span data-ttu-id="f8a84-192">Bu adım yalnızca bir kez Net.Msmq Dinleyici Bağdaştırıcısı hizmeti ilk kullanımını önce yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-192">This step must only be done once prior to the first usage of the Net.Msmq Listener Adapter service.</span></span>  
  
8.  <span data-ttu-id="f8a84-193">Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f8a84-193">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="f8a84-194">Ayrıca, satın alma siparişi gönderirken sıranın URI'sini bilgisayar adını yansıtacak şekilde satın alma siparişi gönderen istemci kodu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f8a84-194">Additionally, change the code on the client that submits the purchase order to reflect the computer name in the URI of the queue when submitting the purchase order.</span></span> <span data-ttu-id="f8a84-195">Aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="f8a84-195">Use the following code:</span></span>  
  
    ```  
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");  
    ```  
  
9. <span data-ttu-id="f8a84-196">Eklediğiniz net.msmq site bağlaması Bu örnek için kaldırın.</span><span class="sxs-lookup"><span data-stu-id="f8a84-196">Remove the net.msmq site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="f8a84-197">Kolaylık sağlamak üzere aşağıdaki adımları örnek dizininde bulunan RemoveMsmqSiteBinding.cmd adlı bir toplu iş dosyasında uygulanır:</span><span class="sxs-lookup"><span data-stu-id="f8a84-197">As a convenience, the following steps are implemented in a batch file called RemoveMsmqSiteBinding.cmd located in the sample directory:</span></span>  
  
    1.  <span data-ttu-id="f8a84-198">NET.MSMQ yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak etkin protokoller listesinden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="f8a84-198">Remove net.msmq from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="f8a84-199">Bu komut, metnin tek bir satırdır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-199">This command is a single line of text.</span></span>  
  
    2.  <span data-ttu-id="f8a84-200">Net.msmq site bağlaması, yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak kaldırın.</span><span class="sxs-lookup"><span data-stu-id="f8a84-200">Remove the net.msmq site binding by running the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="f8a84-201">Bu komut, metnin tek bir satırdır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-201">This command is a single line of text.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="f8a84-202">Toplu iş dosyasını çalıştırarak .NET Framework sürüm 2.0 kullanarak çalışacak şekilde DefaultAppPool sıfırlanır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-202">Running the batch file will reset the DefaultAppPool to run using .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="f8a84-203">Varsayılan olarak `netMsmqBinding` bağlama taşıma, güvenlik etkindir.</span><span class="sxs-lookup"><span data-stu-id="f8a84-203">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="f8a84-204">İki özellik `MsmqAuthenticationMode` ve `MsmqProtectionLevel`, birlikte taşıma güvenliği türü belirlenemedi.</span><span class="sxs-lookup"><span data-stu-id="f8a84-204">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="f8a84-205">Varsayılan olarak kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`.</span><span class="sxs-lookup"><span data-stu-id="f8a84-205">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="f8a84-206">Kimlik doğrulaması ve imzalama özellik MSMQ için bir etki alanının parçası olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8a84-206">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="f8a84-207">Bu örnek, bir etki alanının parçası olmayan bir bilgisayarda çalıştırmak, şu hata alındı: "kullanıcının iç message queuing sertifikası yok".</span><span class="sxs-lookup"><span data-stu-id="f8a84-207">If you run this sample on a computer that is not part of a domain, the following error is received: "User's internal message queuing certificate does not exist".</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="f8a84-208">Örnek bir çalışma alanına katılmış bir bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f8a84-208">To run the sample on a computer joined to a workgroup</span></span>  
  
1.  <span data-ttu-id="f8a84-209">Bilgisayarınız bir etki alanının parçası değilse, taşıma güvenliği None aşağıdaki örnek yapılandırmada gösterildiği gibi kimlik doğrulama modu ve koruma düzeyi ayarlanarak açın.</span><span class="sxs-lookup"><span data-stu-id="f8a84-209">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to none as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding configurationName="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
2.  <span data-ttu-id="f8a84-210">Örneği çalıştırmadan önce hem sunucu hem de istemci yapılandırmasını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f8a84-210">Change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8a84-211">Ayarı `security mode` için `None` ayarına eşdeğerdir `MsmqAuthenticationMode`, `MsmqProtectionLevel` ve `Message` güvenlik `None`.</span><span class="sxs-lookup"><span data-stu-id="f8a84-211">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>  
  
3.  <span data-ttu-id="f8a84-212">Bir çalışma alanına katılmış bir bilgisayar etkinleştirme etkinleştirmek için etkinleştirme hizmeti ve çalışan işlemi (her ikisi için aynı olması gerekir) belirli bir kullanıcı hesabı ile çalıştırılmalıdır ve sıra ACL'ler belirli bir kullanıcı hesabı için olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f8a84-212">To enable activation in a computer joined to a workgroup, both the activation service and the worker process must be run with a specific user account (must be same for both) and the queue must have ACLs for the specific user account.</span></span>  
  
     <span data-ttu-id="f8a84-213">Çalışan işlemin altında çalıştığı kimliğini değiştirmek için:</span><span class="sxs-lookup"><span data-stu-id="f8a84-213">To change the identity that the worker process runs under:</span></span>  
  
    1.  <span data-ttu-id="f8a84-214">İnetmgr.exe'yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f8a84-214">Run Inetmgr.exe.</span></span>  
  
    2.  <span data-ttu-id="f8a84-215">Altında **uygulama havuzları**, sağ **AppPool** (genellikle **DefaultAppPool**) ve **uygulama havuzu Varsayılanlarını Ayarla...** .</span><span class="sxs-lookup"><span data-stu-id="f8a84-215">Under **Application Pools**, right-click the **AppPool** (typically **DefaultAppPool**) and choose **Set Application Pool Defaults…**.</span></span>  
  
    3.  <span data-ttu-id="f8a84-216">Belirli bir kullanıcı hesabı kullanmak için kimlik özelliklerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f8a84-216">Change the Identity properties to use the specific user account.</span></span>  
  
     <span data-ttu-id="f8a84-217">Etkinleştirme altında çalışacağı kimliği değiştirmek için:</span><span class="sxs-lookup"><span data-stu-id="f8a84-217">To change the identity that the Activation Service runs under:</span></span>  
  
    1.  <span data-ttu-id="f8a84-218">Services.msc dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f8a84-218">Run Services.msc.</span></span>  
  
    2.  <span data-ttu-id="f8a84-219">Sağ **Net.MsmqListener bağdaştırıcısı**ve seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="f8a84-219">Right-click the **Net.MsmqListener Adapter**, and choose **Properties**.</span></span>  
  
4.  <span data-ttu-id="f8a84-220">Hesabında değişiklik **oturum açma** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="f8a84-220">Change the account in the **LogOn** tab.</span></span>  
  
5.  <span data-ttu-id="f8a84-221">Bir çalışma grubunda, sınırsız belirteci kullanarak hizmet bir da çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8a84-221">In workgroup, the service must also run using an unrestricted token.</span></span> <span data-ttu-id="f8a84-222">Bunu yapmak için bir komut penceresinde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="f8a84-222">To do this, run the following in a command window:</span></span>  
  
    ```  
    sc sidtype netmsmqactivator unrestricted  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f8a84-223">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f8a84-223">See Also</span></span>  
 [<span data-ttu-id="f8a84-224">AppFabric barındırma ve kalıcılığı örnekleri</span><span class="sxs-lookup"><span data-stu-id="f8a84-224">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
