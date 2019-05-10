---
title: MSMQ Etkinleştirme
ms.date: 03/30/2017
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
ms.openlocfilehash: 925148c4bd084f843f125ab9e851a5404bbe4b89
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664804"
---
# <a name="msmq-activation"></a><span data-ttu-id="4e085-102">MSMQ Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="4e085-102">MSMQ Activation</span></span>
<span data-ttu-id="4e085-103">Bu örnek, bir ileti kuyruktan okunmak uygulamaların Windows İşlem Etkinleştirme Hizmeti (WAS) barındırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="4e085-103">This sample demonstrates how to host applications in Windows Process Activation Service (WAS) that are read from a message queue.</span></span> <span data-ttu-id="4e085-104">Bu örnekte `netMsmqBinding` ve dayanır [iki yönlü iletişimi](../../../../docs/framework/wcf/samples/two-way-communication.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="4e085-104">This sample uses the `netMsmqBinding` and is based on the [Two-Way Communication](../../../../docs/framework/wcf/samples/two-way-communication.md) sample.</span></span> <span data-ttu-id="4e085-105">Bu durumda Web barındırılan bir uygulama hizmetidir ve istemci kendiliğinden barındırılır ve gönderilen satın alma siparişleri durumunu izlemek için konsola çıkışı.</span><span class="sxs-lookup"><span data-stu-id="4e085-105">The service in this case is a Web-hosted application and the client is self-hosted and outputs to the console to observe the status of purchase orders submitted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e085-106">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="4e085-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e085-107">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="4e085-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4e085-108">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4e085-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  <span data-ttu-id="4e085-109">\<InstallDrive>:\WF_WCF_Samples</span><span class="sxs-lookup"><span data-stu-id="4e085-109">\<InstallDrive>:\WF_WCF_Samples</span></span>  
>   
>  <span data-ttu-id="4e085-110">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm WCF indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="4e085-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all WCF and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4e085-111">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="4e085-111">This sample is located in the following directory.</span></span>  
>   
>  <span data-ttu-id="4e085-112">\<Installdrive >: \Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span><span class="sxs-lookup"><span data-stu-id="4e085-112">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span></span>  
  
 <span data-ttu-id="4e085-113">Windows İşlem Etkinleştirme Hizmeti (WAS), yeni işlem etkinleştirme mekanizması [!INCLUDE[lserver](../../../../includes/lserver-md.md)], daha önce yalnızca HTTP tabanlı uygulamalara HTTP olmayan protokolleri kullanan uygulamalar için kullanılabilen IIS gibi özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e085-113">Windows Process Activation Service (WAS), the new process activation mechanism for [!INCLUDE[lserver](../../../../includes/lserver-md.md)], provides IIS-like features that were previously only available to HTTP-based applications to applications that use non-HTTP protocols.</span></span> <span data-ttu-id="4e085-114">Windows Communication Foundation (WCF), MSMQ TCP ve adlandırılmış kanallar gibi bir WCF tarafından desteklenen HTTP olmayan protokolleri üzerinden alınan etkinleştirme isteklerini iletmek için dinleyici bağdaştırıcı arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4e085-114">Windows Communication Foundation (WCF) uses the Listener Adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, Named Pipes, and MSMQ.</span></span> <span data-ttu-id="4e085-115">HTTP olmayan protokolleri üzerinden isteklerini almak için işlevselliği, SMSvcHost.exe içinde çalışan yönetilen Windows Hizmetleri tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="4e085-115">The functionality for receiving requests over non-HTTP protocols is hosted by managed Windows services running in SMSvcHost.exe.</span></span>  
  
 <span data-ttu-id="4e085-116">(NetMsmqActivator) Net.Msmq dinleyici bağdaştırıcı hizmeti, iletileri sıraya göre kuyruğa alınmış uygulamaları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="4e085-116">The Net.Msmq Listener Adapter service (NetMsmqActivator) activates queued applications based on messages in the queue.</span></span>  
  
 <span data-ttu-id="4e085-117">İstemci hizmetinden bir işlem kapsamında satın alma siparişleri gönderir.</span><span class="sxs-lookup"><span data-stu-id="4e085-117">The client sends purchase orders to the service from within the scope of a transaction.</span></span> <span data-ttu-id="4e085-118">Hizmet, bir işlemde siparişleri alır ve işler.</span><span class="sxs-lookup"><span data-stu-id="4e085-118">The service receives the orders in a transaction and processes them.</span></span> <span data-ttu-id="4e085-119">Hizmet daha sonra siparişin durumunu istemcisiyle geri çağırır.</span><span class="sxs-lookup"><span data-stu-id="4e085-119">The service then calls back the client with the status of the order.</span></span> <span data-ttu-id="4e085-120">İki yönlü iletişimi kolaylaştırmak için kuyruğa satın alma siparişleri ve sipariş durumu sıralara istemciyi ve hizmeti kullanın.</span><span class="sxs-lookup"><span data-stu-id="4e085-120">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>  
  
 <span data-ttu-id="4e085-121">Hizmet sözleşmesi `IOrderProcessor` queuing ile birlikte çalışan tek yönlü hizmet işlemleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4e085-121">The service contract `IOrderProcessor` defines the one-way service operations that work with queuing.</span></span> <span data-ttu-id="4e085-122">Hizmet işlemi yanıt uç nokta sırasını durumları istemciye göndermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="4e085-122">The service operation uses the reply endpoint to send order statuses to the client.</span></span> <span data-ttu-id="4e085-123">Yanıt uç noktasının, sipariş durumunun istemciye geri göndermek için kullanılan kuyruk URI'sini adresidir.</span><span class="sxs-lookup"><span data-stu-id="4e085-123">The reply endpoint's address is the URI of the queue used to send the order status back to the client.</span></span> <span data-ttu-id="4e085-124">Uygulama işleme sırası, bu sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="4e085-124">The order processing application implements this contract.</span></span>  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po,   
                                           string reportOrderStatusTo);  
}  
```  
  
 <span data-ttu-id="4e085-125">Sipariş durumu için belirtilen istemci tarafından gönderilecek yanıt anlaşması.</span><span class="sxs-lookup"><span data-stu-id="4e085-125">The reply contract to send order status to is specified by the client.</span></span> <span data-ttu-id="4e085-126">Sipariş durumu sözleşme istemciye uygular.</span><span class="sxs-lookup"><span data-stu-id="4e085-126">The client implements the order status contract.</span></span> <span data-ttu-id="4e085-127">Hizmet, bu sözleşmenin oluşturulan istemci siparişinizin durumu istemciye geri göndermek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="4e085-127">The service uses the generated client of this contract to send order status back to the client.</span></span>  
  
```csharp  
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```  
  
 <span data-ttu-id="4e085-128">Hizmet işlemi gönderilen satın alma siparişi işler.</span><span class="sxs-lookup"><span data-stu-id="4e085-128">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="4e085-129"><xref:System.ServiceModel.OperationBehaviorAttribute> Otomatik kayıt hizmeti işleminin tamamlanması hareket otomatik tamamlama ve kuyruk iletiyi almak için kullanılan işlem belirtmek için hizmet işlemi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4e085-129">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in the transaction that is used to receive the message from the queue and automatic completion of the transaction on completion of the service operation.</span></span> <span data-ttu-id="4e085-130">`Orders` Sınıfı sipariş işleme işlevselliğini kapsüller.</span><span class="sxs-lookup"><span data-stu-id="4e085-130">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="4e085-131">Bu durumda, satın alma siparişi bir sözlüğe ekler.</span><span class="sxs-lookup"><span data-stu-id="4e085-131">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="4e085-132">Hizmet işlemi kayıtlı işlem işlemlerinde kullanılabilir `Orders` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4e085-132">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>  
  
 <span data-ttu-id="4e085-133">Siparişin durumunu istemciye gönderilen satın alma siparişi işleme ek olarak hizmet işlemi yanıtlar.</span><span class="sxs-lookup"><span data-stu-id="4e085-133">The service operation, in addition to processing the submitted purchase order, replies back to the client about the status of the order.</span></span>  
  
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
}
```  
  
 <span data-ttu-id="4e085-134">Kullanılacak bağlama istemci, bir yapılandırma dosyası kullanarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="4e085-134">The client binding to use is specified using a configuration file.</span></span>  
  
 <span data-ttu-id="4e085-135">MSMQ kuyruk adı, bir yapılandırma dosyasının appSettings bölümünde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="4e085-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="4e085-136">Hizmet için uç nokta yapılandırma dosyasının System.serviceModel bölümünde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4e085-136">The endpoint for the service is defined in the System.serviceModel section of the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e085-137">MSMQ kuyruk adı ve uç nokta adresi adresleme biraz farklı kuralları kullanın.</span><span class="sxs-lookup"><span data-stu-id="4e085-137">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="4e085-138">MSMQ kuyruk adı, eğik çizgi ayırıcılar yolundaki ve yerel bilgisayar için bir nokta (.) kullanır.</span><span class="sxs-lookup"><span data-stu-id="4e085-138">The MSMQ queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="4e085-139">Bir net.msmq WCF uç nokta adresini belirtir: düzeni, "localhost" yerel bilgisayarı ve eğik kendi yolunda kullanır.</span><span class="sxs-lookup"><span data-stu-id="4e085-139">The WCF endpoint address specifies a net.msmq: scheme, uses "localhost" for the local computer, and uses forward slashes in its path.</span></span> <span data-ttu-id="4e085-140">Uzak bilgisayarda barındırılan bir kuyruktan okunur değiştirin "." ve "localhost" uzak bilgisayar adı.</span><span class="sxs-lookup"><span data-stu-id="4e085-140">To read from a queue that is hosted on the remote computer, replace the "." and "localhost" to the remote computer name.</span></span>  
  
 <span data-ttu-id="4e085-141">Bir sınıfın adını .svc dosyasıyla WAS hizmeti kodunda barındırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4e085-141">A .svc file with the name of the class is used to host the service code in WAS.</span></span>  
  
 <span data-ttu-id="4e085-142">Service.svc dosyası oluşturmak için bir yönergeyi içeren `OrderProcessorService`.</span><span class="sxs-lookup"><span data-stu-id="4e085-142">The Service.svc file itself contains a directive to create the `OrderProcessorService`.</span></span>  
  
```svc
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>  
```  
  
 <span data-ttu-id="4e085-143">Service.svc dosya System.Transactions.dll yüklendiğinden emin olmak için bir derleme yönergesi de içerir.</span><span class="sxs-lookup"><span data-stu-id="4e085-143">The Service.svc file also contains an assembly directive to ensure that System.Transactions.dll is loaded.</span></span>  
  
```svc  
<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>  
```  
  
 <span data-ttu-id="4e085-144">İstemci işlem kapsamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4e085-144">The client creates a transaction scope.</span></span> <span data-ttu-id="4e085-145">Hizmeti ile iletişimi, burada tüm iletileri başarılı veya başarısız bir atomik birim olarak kabul edilmesi bu neden işlemin kapsamı içinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="4e085-145">Communication with the service takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="4e085-146">İşlem çağırarak kararlıdır `Complete` işlem kapsamı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="4e085-146">The transaction is committed by calling `Complete` on the transaction scope.</span></span>  
  
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
  
 <span data-ttu-id="4e085-147">İstemci kodu uygulayan `IOrderStatus` siparişinizin durumu hizmetinden almak üzere sözleşme.</span><span class="sxs-lookup"><span data-stu-id="4e085-147">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="4e085-148">Bu durumda, siparişinizin durumu yazdırır.</span><span class="sxs-lookup"><span data-stu-id="4e085-148">In this case, it prints out the order status.</span></span>  
  
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
  
 <span data-ttu-id="4e085-149">Durum sırasını oluşturulan `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4e085-149">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="4e085-150">Aşağıdaki örnek yapılandırmada gösterildiği gibi istemci yapılandırması sipariş durumu hizmeti barındırmak için sipariş durumu hizmeti yapılandırması içerir.</span><span class="sxs-lookup"><span data-stu-id="4e085-150">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>  
  
```xml  
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
  
 <span data-ttu-id="4e085-151">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem sunucu hem de istemci konsol penceresi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4e085-151">When you run the sample, the client and service activities are displayed in both the server and client console windows.</span></span> <span data-ttu-id="4e085-152">Sunucunun istemciden iletilerini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e085-152">You can see the server receive messages from the client.</span></span> <span data-ttu-id="4e085-153">Her konsol penceresi sunucu ve istemci kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4e085-153">Press ENTER in each console window to shut down the server and client.</span></span>  
  
 <span data-ttu-id="4e085-154">İstemci, sunucu tarafından gönderilen sipariş durumu bilgilerini görüntüler:</span><span class="sxs-lookup"><span data-stu-id="4e085-154">The client displays the order status information sent by the server:</span></span>  
  
```console  
Press <ENTER> to terminate client.  
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4e085-155">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="4e085-155">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4e085-156">Emin [!INCLUDE[iisver](../../../../includes/iisver-md.md)] WAS etkinleştirme için gerekli olduğu gibi yüklenir.</span><span class="sxs-lookup"><span data-stu-id="4e085-156">Ensure that [!INCLUDE[iisver](../../../../includes/iisver-md.md)] is installed, as it is required for WAS activation.</span></span>  
  
2. <span data-ttu-id="4e085-157">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e085-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span> <span data-ttu-id="4e085-158">Ayrıca, WCF HTTP olmayan etkinleştirme bileşenlerini yüklemelisiniz:</span><span class="sxs-lookup"><span data-stu-id="4e085-158">In addition, you must install the WCF non-HTTP activation components:</span></span>  
  
    1. <span data-ttu-id="4e085-159">Gelen **Başlat** menüsünde seçin **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="4e085-159">From the **Start** menu, choose **Control Panel**.</span></span>  
  
    2. <span data-ttu-id="4e085-160">Seçin **programlar ve Özellikler**.</span><span class="sxs-lookup"><span data-stu-id="4e085-160">Select **Programs and Features**.</span></span>  
  
    3. <span data-ttu-id="4e085-161">Tıklayın **Windows özelliklerini aç veya Kapat**.</span><span class="sxs-lookup"><span data-stu-id="4e085-161">Click **Turn Windows Features on or off**.</span></span>  
  
    4. <span data-ttu-id="4e085-162">Altında **özellikler özeti**, tıklayın **Özellik Ekle**.</span><span class="sxs-lookup"><span data-stu-id="4e085-162">Under **Features Summary**, click **Add Features**.</span></span>  
  
    5. <span data-ttu-id="4e085-163">Genişletin **Microsoft .NET Framework 3.0** düğüm ve onay **Windows Communication Foundation HTTP olmayan etkinleştirme** özelliği.</span><span class="sxs-lookup"><span data-stu-id="4e085-163">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>  
  
3. <span data-ttu-id="4e085-164">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e085-164">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="4e085-165">İstemci, bir komut penceresinden client.exe yürüterek çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4e085-165">Run the client by executing client.exe from a command window.</span></span> <span data-ttu-id="4e085-166">Bu, bir sıra oluşturur ve ona bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="4e085-166">This creates the queue and sends a message to it.</span></span> <span data-ttu-id="4e085-167">İleti okuma hizmet sonucunu görmek için çalıştıran istemci bırakın</span><span class="sxs-lookup"><span data-stu-id="4e085-167">Leave the client running to see the result of the service reading the message</span></span>  
  
5. <span data-ttu-id="4e085-168">MSMQ Etkinleştirme hizmeti varsayılan olarak ağ hizmeti olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="4e085-168">The MSMQ activation service runs as Network Service by default.</span></span> <span data-ttu-id="4e085-169">Bu nedenle, uygulamayı etkinleştirmek için kullanılan kuyruk olmalıdır alır ve ağ hizmeti için izinleri göz at.</span><span class="sxs-lookup"><span data-stu-id="4e085-169">Therefore, the queue that is used to activate the application must have receive and peek permissions for Network Service.</span></span> <span data-ttu-id="4e085-170">Bu, Message Queuing MMC kullanarak eklenebilir:</span><span class="sxs-lookup"><span data-stu-id="4e085-170">This can be added by using the Message Queuing MMC:</span></span>  
  
    1. <span data-ttu-id="4e085-171">Gelen **Başlat** menüsünde tıklatın **çalıştırmak**, yazın `Compmgmt.msc` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4e085-171">From the **Start** menu, click **Run**, then type `Compmgmt.msc` and press ENTER.</span></span>  
  
    2. <span data-ttu-id="4e085-172">Altında **hizmetler ve uygulamalar**, genişletme **Message Queuing**.</span><span class="sxs-lookup"><span data-stu-id="4e085-172">Under **Services and Applications**, expand **Message Queuing**.</span></span>  
  
    3. <span data-ttu-id="4e085-173">Tıklayın **özel sıralar**.</span><span class="sxs-lookup"><span data-stu-id="4e085-173">Click **Private Queues**.</span></span>  
  
    4. <span data-ttu-id="4e085-174">' % S'sıra (servicemodelsamples/Service.svc) sağ tıklatın ve seçin **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="4e085-174">Right-click the queue (servicemodelsamples/Service.svc) and choose **Properties**.</span></span>  
  
    5. <span data-ttu-id="4e085-175">Üzerinde **güvenlik** sekmesinde **Ekle** gözlem verin ve alma izinleri ağ hizmeti için.</span><span class="sxs-lookup"><span data-stu-id="4e085-175">On the **Security** tab, click **Add** and give peek and receive permissions to Network Service.</span></span>  
  
6. <span data-ttu-id="4e085-176">MSMQ etkinleştirmeyi desteklemek için Windows İşlem Etkinleştirme Hizmeti'nı (WAS) yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="4e085-176">Configure the Windows Process Activation Service (WAS) to support MSMQ activation.</span></span>  
  
     <span data-ttu-id="4e085-177">Kolaylık, örnek dizininde AddMsmqSiteBinding.cmd adlı bir toplu iş dosyasında aşağıdaki adımlar uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4e085-177">As a convenience, the following steps are implemented in a batch file called AddMsmqSiteBinding.cmd located in the sample directory.</span></span>  
  
    1. <span data-ttu-id="4e085-178">NET.MSMQ etkinleştirmeyi desteklemek için varsayılan Web sitesi ilk net.msmq protokole bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4e085-178">To support net.msmq activation, the default Web site must first be bound to the net.msmq protocol.</span></span> <span data-ttu-id="4e085-179">Bu yapılabilir ile birlikte yüklenen appcmd.exe kullanarak [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Yönetimi araç.</span><span class="sxs-lookup"><span data-stu-id="4e085-179">This can be done using appcmd.exe, which is installed with the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] management toolset.</span></span> <span data-ttu-id="4e085-180">(Yönetici) yükseltilmiş komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4e085-180">From an elevated (administrator) command prompt, run the following command.</span></span>  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="4e085-181">Tek metin satırı komutudur.</span><span class="sxs-lookup"><span data-stu-id="4e085-181">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="4e085-182">Bu komut, varsayılan Web sitesine net.msmq site bağlaması ekler.</span><span class="sxs-lookup"><span data-stu-id="4e085-182">This command adds a net.msmq site binding to the default Web site.</span></span>  
  
    2. <span data-ttu-id="4e085-183">Bir sitedeki tüm uygulamaları genel net.msmq bağlama paylaşsa da her uygulama net.msmq destek ayrı ayrı etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4e085-183">Although all applications within a site share a common net.msmq binding, each application can enable net.msmq support individually.</span></span> <span data-ttu-id="4e085-184">/Servicemodelsamples uygulamanın NET.MSMQ etkinleştirmek için yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4e085-184">To enable net.msmq for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="4e085-185">Tek metin satırı komutudur.</span><span class="sxs-lookup"><span data-stu-id="4e085-185">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="4e085-186">Bu komut kullanılarak erişilecektir /servicemodelsamples uygulamayı etkinleştirir `http://localhost/servicemodelsamples` ve `net.msmq://localhost/servicemodelsamples`.</span><span class="sxs-lookup"><span data-stu-id="4e085-186">This command enables the /servicemodelsamples application to be accessed using `http://localhost/servicemodelsamples` and `net.msmq://localhost/servicemodelsamples`.</span></span>
  
7. <span data-ttu-id="4e085-187">Daha önce yapmadıysanız, MSMQ Etkinleştirme Hizmeti'nın etkin olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4e085-187">If you have not done so previously, ensure that the MSMQ activation service is enabled.</span></span> <span data-ttu-id="4e085-188">Gelen **Başlat** menüsünde tıklatın **çalıştırın**ve türü `Services.msc`.</span><span class="sxs-lookup"><span data-stu-id="4e085-188">From the **Start** menu, click **Run**, and type `Services.msc`.</span></span> <span data-ttu-id="4e085-189">Arama için Hizmetler listesi **Net.Msmq dinleyici bağdaştırıcısı**.</span><span class="sxs-lookup"><span data-stu-id="4e085-189">Search the list of services for the **Net.Msmq Listener Adapter**.</span></span> <span data-ttu-id="4e085-190">Sağ tıklayıp **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="4e085-190">Right-click and select **Properties**.</span></span> <span data-ttu-id="4e085-191">Ayarlama **başlangıç türü** için **otomatik**, tıklayın **Uygula** tıklatıp **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="4e085-191">Set the **Startup Type** to **Automatic**, click **Apply** and click the **Start** button.</span></span> <span data-ttu-id="4e085-192">Bu adım yalnızca bir kez Net.Msmq dinleyici bağdaştırıcı hizmeti ilk kullanımlar yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4e085-192">This step must only be done once prior to the first usage of the Net.Msmq Listener Adapter service.</span></span>  
  
8. <span data-ttu-id="4e085-193">Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e085-193">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="4e085-194">Ayrıca, satın alma siparişi gönderirken URİ'sini sıra bilgisayar adını yansıtacak şekilde satınalma siparişi gönderen istemci kodu değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4e085-194">Additionally, change the code on the client that submits the purchase order to reflect the computer name in the URI of the queue when submitting the purchase order.</span></span> <span data-ttu-id="4e085-195">Aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="4e085-195">Use the following code:</span></span>  
  
    ```csharp  
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");  
    ```  
  
9. <span data-ttu-id="4e085-196">Eklediğiniz net.msmq site bağlaması için bu örnek kaldırın.</span><span class="sxs-lookup"><span data-stu-id="4e085-196">Remove the net.msmq site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="4e085-197">Kolaylık, örnek dizininde RemoveMsmqSiteBinding.cmd adlı bir toplu iş dosyasında aşağıdaki adımlar uygulanır:</span><span class="sxs-lookup"><span data-stu-id="4e085-197">As a convenience, the following steps are implemented in a batch file called RemoveMsmqSiteBinding.cmd located in the sample directory:</span></span>  
  
    1. <span data-ttu-id="4e085-198">NET.MSMQ yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak etkin protokoller listesinden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="4e085-198">Remove net.msmq from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="4e085-199">Tek metin satırı komutudur.</span><span class="sxs-lookup"><span data-stu-id="4e085-199">This command is a single line of text.</span></span>  
  
    2. <span data-ttu-id="4e085-200">Net.msmq site bağlaması, yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak kaldırın.</span><span class="sxs-lookup"><span data-stu-id="4e085-200">Remove the net.msmq site binding by running the following command from an elevated command prompt.</span></span>  
  
        ```console  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="4e085-201">Tek metin satırı komutudur.</span><span class="sxs-lookup"><span data-stu-id="4e085-201">This command is a single line of text.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="4e085-202">Toplu iş dosyasını çalıştırarak .NET Framework sürüm 2.0 kullanarak çalışacak şekilde DefaultAppPool sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="4e085-202">Running the batch file will reset the DefaultAppPool to run using .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="4e085-203">Varsayılan olarak `netMsmqBinding` bağlama taşıma, güvenlik etkin.</span><span class="sxs-lookup"><span data-stu-id="4e085-203">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="4e085-204">İki özellik `MsmqAuthenticationMode` ve `MsmqProtectionLevel`, birlikte aktarım güvenliği türünü belirleyin.</span><span class="sxs-lookup"><span data-stu-id="4e085-204">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="4e085-205">Varsayılan kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`.</span><span class="sxs-lookup"><span data-stu-id="4e085-205">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="4e085-206">Kimlik doğrulama ve imzalama özelliği sağlamak MSMQ için bir etki alanının parçası olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4e085-206">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="4e085-207">Bu örnek, bir etki alanının parçası olmayan bir bilgisayar üzerinde çalıştırırsanız, aşağıdaki hata alınır: "Kullanıcının iç message queuing sertifikası yok".</span><span class="sxs-lookup"><span data-stu-id="4e085-207">If you run this sample on a computer that is not part of a domain, the following error is received: "User's internal message queuing certificate does not exist".</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="4e085-208">Örneği için bir çalışma alanına katılmış bir bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="4e085-208">To run the sample on a computer joined to a workgroup</span></span>  
  
1. <span data-ttu-id="4e085-209">Bilgisayarınız bir etki alanının parçası değilse, hiçbiri aşağıdaki örnek yapılandırmada gösterildiği gibi kimlik doğrulama modu ve koruma düzeyi ayarlayarak aktarım güvenliği devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="4e085-209">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to none as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding configurationName="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
2. <span data-ttu-id="4e085-210">Örneği çalıştırmadan önce hem sunucu hem de istemci yapılandırmasını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4e085-210">Change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4e085-211">Ayarı `security mode` için `None` ayarlamakla eşdeğerdir `MsmqAuthenticationMode`, `MsmqProtectionLevel` ve `Message` güvenlik `None`.</span><span class="sxs-lookup"><span data-stu-id="4e085-211">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>  
  
3. <span data-ttu-id="4e085-212">Bir çalışma alanına katılmış bir bilgisayar etkinleştirmesi için hem Etkinleştirme hizmeti hem de çalışan işlemi (her ikisi için aynı olmalıdır) belirli bir kullanıcı hesabı ile çalıştırılmalıdır ve kuyruk ACL'leri belirli bir kullanıcı hesabı için olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4e085-212">To enable activation in a computer joined to a workgroup, both the activation service and the worker process must be run with a specific user account (must be same for both) and the queue must have ACLs for the specific user account.</span></span>  
  
     <span data-ttu-id="4e085-213">Altında çalışan işlemini çalıştıran kimliği değiştirmek için:</span><span class="sxs-lookup"><span data-stu-id="4e085-213">To change the identity that the worker process runs under:</span></span>  
  
    1. <span data-ttu-id="4e085-214">Inetmgr.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4e085-214">Run Inetmgr.exe.</span></span>  
  
    2. <span data-ttu-id="4e085-215">Altında **uygulama havuzları**, sağ **AppPool** (genellikle **DefaultAppPool**) ve **uygulama havuzu Varsayılanlarını Ayarla...** .</span><span class="sxs-lookup"><span data-stu-id="4e085-215">Under **Application Pools**, right-click the **AppPool** (typically **DefaultAppPool**) and choose **Set Application Pool Defaults…**.</span></span>  
  
    3. <span data-ttu-id="4e085-216">Belirli bir kullanıcı hesabını kullanmak üzere kimlik özelliklerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4e085-216">Change the Identity properties to use the specific user account.</span></span>  
  
     <span data-ttu-id="4e085-217">Etkinleştirme altında çalışacağı kimliği değiştirmek için:</span><span class="sxs-lookup"><span data-stu-id="4e085-217">To change the identity that the Activation Service runs under:</span></span>  
  
    1. <span data-ttu-id="4e085-218">Services.msc dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4e085-218">Run Services.msc.</span></span>  
  
    2. <span data-ttu-id="4e085-219">Sağ **Net.MsmqListener bağdaştırıcısı**ve **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="4e085-219">Right-click the **Net.MsmqListener Adapter**, and choose **Properties**.</span></span>  
  
4. <span data-ttu-id="4e085-220">Hesabında değişiklik **oturum açma** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="4e085-220">Change the account in the **LogOn** tab.</span></span>  
  
5. <span data-ttu-id="4e085-221">Bir çalışma grubunda hizmeti sınırsız bir belirteç kullanarak da çalıştırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4e085-221">In workgroup, the service must also run using an unrestricted token.</span></span> <span data-ttu-id="4e085-222">Bunu yapmak için bir komut penceresinde aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="4e085-222">To do this, run the following in a command window:</span></span>  
  
    ```console  
    sc sidtype netmsmqactivator unrestricted  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4e085-223">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e085-223">See also</span></span>

- [<span data-ttu-id="4e085-224">AppFabric barındırma ve Kalıcılık örnekleri</span><span class="sxs-lookup"><span data-stu-id="4e085-224">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
