---
title: MSMQ Etkinleştirme
ms.date: 03/30/2017
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
ms.openlocfilehash: 038f4d7e3d713cfe4134ea98f7858ef71f29bab4
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895244"
---
# <a name="msmq-activation"></a><span data-ttu-id="d5f83-102">MSMQ Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="d5f83-102">MSMQ Activation</span></span>

<span data-ttu-id="d5f83-103">Bu örnek, Windows Işlem etkinleştirme hizmeti 'nde (WAS) bir ileti sırasından okunan uygulamaların nasıl barındırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-103">This sample demonstrates how to host applications in Windows Process Activation Service (WAS) that are read from a message queue.</span></span> <span data-ttu-id="d5f83-104">Bu örnek, `netMsmqBinding` ve [iki yönlü iletişim](../../../../docs/framework/wcf/samples/two-way-communication.md) örneğine göre ' nı kullanır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-104">This sample uses the `netMsmqBinding` and is based on the [Two-Way Communication](../../../../docs/framework/wcf/samples/two-way-communication.md) sample.</span></span> <span data-ttu-id="d5f83-105">Bu durumda hizmet, Web 'de barındırılan bir uygulamadır ve istemci, gönderilen satın alma siparişlerinin durumunu gözlemleyecek şekilde kendi kendine barındırılır ve konsola çıkış verir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-105">The service in this case is a Web-hosted application and the client is self-hosted and outputs to the console to observe the status of purchase orders submitted.</span></span>

> [!NOTE]
> <span data-ttu-id="d5f83-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="d5f83-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="d5f83-107">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d5f83-108">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-108">Check for the following (default) directory before continuing.</span></span>
>
> <span data-ttu-id="d5f83-109">\<InstallDrive >: \WF_WCF_Samples</span><span class="sxs-lookup"><span data-stu-id="d5f83-109">\<InstallDrive>:\WF_WCF_Samples</span></span>
>
> <span data-ttu-id="d5f83-110">Bu dizin yoksa, tüm WCF ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all WCF and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d5f83-111">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d5f83-111">This sample is located in the following directory.</span></span>
>
> <span data-ttu-id="d5f83-112">\<InstallDrive >: \Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span><span class="sxs-lookup"><span data-stu-id="d5f83-112">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span></span>

<span data-ttu-id="d5f83-113">İçin [!INCLUDE[lserver](../../../../includes/lserver-md.md)]yeni işlem etkinleştirme mekanizması olan Windows işlem etkinleştirme hizmeti (was), daha önce HTTP tabanlı uygulamalar için yalnızca http olmayan protokolleri kullanan uygulamalara sunulan IIS benzeri özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5f83-113">Windows Process Activation Service (WAS), the new process activation mechanism for [!INCLUDE[lserver](../../../../includes/lserver-md.md)], provides IIS-like features that were previously only available to HTTP-based applications to applications that use non-HTTP protocols.</span></span> <span data-ttu-id="d5f83-114">Windows Communication Foundation (WCF), TCP, adlandırılmış kanallar ve MSMQ gibi WCF tarafından desteklenen HTTP olmayan protokoller üzerinden alınan etkinleştirme isteklerini iletmek için dinleyici bağdaştırıcısı arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-114">Windows Communication Foundation (WCF) uses the Listener Adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, Named Pipes, and MSMQ.</span></span> <span data-ttu-id="d5f83-115">HTTP olmayan protokoller üzerinden istek alma işlevselliği, SMSvcHost. exe ' de çalışan yönetilen Windows Hizmetleri tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-115">The functionality for receiving requests over non-HTTP protocols is hosted by managed Windows services running in SMSvcHost.exe.</span></span>

<span data-ttu-id="d5f83-116">Net. MSMQ dinleyicisi bağdaştırıcısı hizmeti (Netmsmqetkinleştirici) kuyruktaki iletileri temel alarak sıraya alınmış uygulamaları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-116">The Net.Msmq Listener Adapter service (NetMsmqActivator) activates queued applications based on messages in the queue.</span></span>

<span data-ttu-id="d5f83-117">İstemci, bir işlemin kapsamı içinde hizmete satın alma siparişleri gönderir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-117">The client sends purchase orders to the service from within the scope of a transaction.</span></span> <span data-ttu-id="d5f83-118">Hizmet, siparişleri bir işlem içinde alır ve işler.</span><span class="sxs-lookup"><span data-stu-id="d5f83-118">The service receives the orders in a transaction and processes them.</span></span> <span data-ttu-id="d5f83-119">Bu hizmet daha sonra istemciyi siparişin durumuyla geri çağırır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-119">The service then calls back the client with the status of the order.</span></span> <span data-ttu-id="d5f83-120">İki yönlü iletişimi kolaylaştırmak için, istemci ve hizmetin her ikisi de, satın alma siparişlerinin ve sipariş durumunun kuyruğa alınması için kuyrukları kullanır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-120">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>

<span data-ttu-id="d5f83-121">Hizmet sözleşmesi `IOrderProcessor` , sıraya alma ile çalışan tek yönlü hizmet işlemlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d5f83-121">The service contract `IOrderProcessor` defines the one-way service operations that work with queuing.</span></span> <span data-ttu-id="d5f83-122">Hizmet işlemi, istemciye sıra durumları göndermek için yanıt uç noktasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-122">The service operation uses the reply endpoint to send order statuses to the client.</span></span> <span data-ttu-id="d5f83-123">Yanıt uç noktasının adresi, sipariş durumunu istemciye geri göndermek için kullanılan kuyruğun URI 'sidir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-123">The reply endpoint's address is the URI of the queue used to send the order status back to the client.</span></span> <span data-ttu-id="d5f83-124">Sipariş işleme uygulaması bu sözleşmeyi uygular.</span><span class="sxs-lookup"><span data-stu-id="d5f83-124">The order processing application implements this contract.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po,
                                           string reportOrderStatusTo);
}
```

<span data-ttu-id="d5f83-125">Sıra durumunun gönderileceği yanıt sözleşmesi istemci tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-125">The reply contract to send order status to is specified by the client.</span></span> <span data-ttu-id="d5f83-126">İstemci sipariş durumu sözleşmesini uygular.</span><span class="sxs-lookup"><span data-stu-id="d5f83-126">The client implements the order status contract.</span></span> <span data-ttu-id="d5f83-127">Hizmet, sipariş durumunu istemciye geri göndermek için bu sözleşmenin oluşturulan istemcisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-127">The service uses the generated client of this contract to send order status back to the client.</span></span>

```csharp
[ServiceContract]
public interface IOrderStatus
{
    [OperationContract(IsOneWay = true)]
    void OrderStatus(string poNumber, string status);
}
```

<span data-ttu-id="d5f83-128">Hizmet işlemi gönderilen satın alma siparişini işler.</span><span class="sxs-lookup"><span data-stu-id="d5f83-128">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="d5f83-129">, <xref:System.ServiceModel.OperationBehaviorAttribute> Sıradaki iletiyi almak ve hizmet işleminin tamamlanmasından sonra işlemin otomatik olarak tamamlanması için kullanılan işlemde otomatik kayıt belirtmek üzere hizmet işlemine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-129">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in the transaction that is used to receive the message from the queue and automatic completion of the transaction on completion of the service operation.</span></span> <span data-ttu-id="d5f83-130">`Orders` Sınıfı sipariş işleme işlevselliğini Kapsüller.</span><span class="sxs-lookup"><span data-stu-id="d5f83-130">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="d5f83-131">Bu durumda, satın alma sırasını bir sözlüğe ekler.</span><span class="sxs-lookup"><span data-stu-id="d5f83-131">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="d5f83-132">İçindeki hizmet işleminin kayıtlı olduğu işlem, `Orders` sınıftaki işlemler için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-132">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>

<span data-ttu-id="d5f83-133">Hizmet işlemi, gönderilen satın alma siparişinin işlenmesine ek olarak, siparişin durumu hakkında istemciye geri yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-133">The service operation, in addition to processing the submitted purchase order, replies back to the client about the status of the order.</span></span>

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

<span data-ttu-id="d5f83-134">Kullanılacak istemci bağlaması bir yapılandırma dosyası kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-134">The client binding to use is specified using a configuration file.</span></span>

<span data-ttu-id="d5f83-135">MSMQ kuyruğu adı, yapılandırma dosyasının bir appSettings bölümünde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="d5f83-136">Hizmetin uç noktası, yapılandırma dosyasının System. serviceModel bölümünde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-136">The endpoint for the service is defined in the System.serviceModel section of the configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="d5f83-137">MSMQ kuyruğu adı ve uç nokta adresi biraz farklı adresleme kuralları kullanır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-137">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="d5f83-138">MSMQ sırası adı, yerel bilgisayar için bir nokta (.) ve kendi yolunda ters eğik çizgi ayırıcılar kullanır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-138">The MSMQ queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="d5f83-139">WCF uç nokta adresi bir net. MSMQ: Scheme belirtir, yerel bilgisayar için "localhost" kullanır ve yolunda eğik çizgi kullanır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-139">The WCF endpoint address specifies a net.msmq: scheme, uses "localhost" for the local computer, and uses forward slashes in its path.</span></span> <span data-ttu-id="d5f83-140">Uzak bilgisayarda barındırılan bir kuyruktan okumak için, "." ve "localhost" değerini uzak bilgisayar adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-140">To read from a queue that is hosted on the remote computer, replace the "." and "localhost" to the remote computer name.</span></span>

<span data-ttu-id="d5f83-141">WAS ' de hizmet kodunu barındırmak için sınıf adına sahip bir. svc dosyası kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-141">A .svc file with the name of the class is used to host the service code in WAS.</span></span>

<span data-ttu-id="d5f83-142">Service. svc dosyasının kendisi oluşturmak `OrderProcessorService`için bir yönerge içerir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-142">The Service.svc file itself contains a directive to create the `OrderProcessorService`.</span></span>

`<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>`

<span data-ttu-id="d5f83-143">Service. svc dosyası, System. Transactions. dll ' nin yüklü olduğundan emin olmak için bir derleme yönergesi de içerir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-143">The Service.svc file also contains an assembly directive to ensure that System.Transactions.dll is loaded.</span></span>

`<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>`

<span data-ttu-id="d5f83-144">İstemci bir işlem kapsamı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d5f83-144">The client creates a transaction scope.</span></span> <span data-ttu-id="d5f83-145">Hizmet ile iletişim, işlemin kapsamı içinde gerçekleşirken, tüm iletilerin başarılı veya başarısız olduğu atomik bir birim olarak işlenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="d5f83-145">Communication with the service takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="d5f83-146">İşlem, işlem kapsamında çağırarak `Complete` yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d5f83-146">The transaction is committed by calling `Complete` on the transaction scope.</span></span>

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

<span data-ttu-id="d5f83-147">İstemci kodu, hizmetten sipariş `IOrderStatus` durumunu almak için sözleşmeyi uygular.</span><span class="sxs-lookup"><span data-stu-id="d5f83-147">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="d5f83-148">Bu durumda, sipariş durumunu yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-148">In this case, it prints out the order status.</span></span>

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

<span data-ttu-id="d5f83-149">Sıra durumu kuyruğu `Main` yönteminde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d5f83-149">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="d5f83-150">İstemci yapılandırması, aşağıdaki örnek yapılandırmada gösterildiği gibi, sipariş durumu hizmetini barındıracak sıra durumu hizmeti yapılandırmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-150">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>

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

<span data-ttu-id="d5f83-151">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem sunucu hem de istemci konsol pencereleri içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-151">When you run the sample, the client and service activities are displayed in both the server and client console windows.</span></span> <span data-ttu-id="d5f83-152">İstemciden sunucudan ileti alın ' a bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5f83-152">You can see the server receive messages from the client.</span></span> <span data-ttu-id="d5f83-153">Sunucu ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d5f83-153">Press ENTER in each console window to shut down the server and client.</span></span>

<span data-ttu-id="d5f83-154">İstemci, sunucu tarafından gönderilen sıra durumu bilgilerini görüntüler:</span><span class="sxs-lookup"><span data-stu-id="d5f83-154">The client displays the order status information sent by the server:</span></span>

```console
Press <ENTER> to terminate client.
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d5f83-155">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="d5f83-155">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="d5f83-156">WAS etkinleştirmesi için gerekli olduğundan, IIS 7,0 ' nin yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d5f83-156">Ensure that IIS 7.0 is installed, as it is required for WAS activation.</span></span>

2. <span data-ttu-id="d5f83-157">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d5f83-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span> <span data-ttu-id="d5f83-158">Ayrıca, WCF HTTP olmayan etkinleştirme bileşenlerini yüklemelisiniz:</span><span class="sxs-lookup"><span data-stu-id="d5f83-158">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="d5f83-159">**Başlat** menüsünde, **Denetim Masası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-159">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="d5f83-160">**Programlar ve Özellikler '** i seçin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-160">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="d5f83-161">**Windows özelliklerini aç veya kapat**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5f83-161">Click **Turn Windows Features on or off**.</span></span>

    4. <span data-ttu-id="d5f83-162">**Özellikler Özeti**' nin altında **Özellik Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5f83-162">Under **Features Summary**, click **Add Features**.</span></span>

    5. <span data-ttu-id="d5f83-163">**Microsoft .NET Framework 3,0** düğümünü genişletin ve **Windows Communication Foundation HTTP olmayan etkinleştirme** özelliğini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-163">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="d5f83-164">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-164">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="d5f83-165">Bir komut penceresinden Client. exe ' yi yürüterek istemciyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d5f83-165">Run the client by executing client.exe from a command window.</span></span> <span data-ttu-id="d5f83-166">Bu, kuyruğu oluşturur ve ona bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-166">This creates the queue and sends a message to it.</span></span> <span data-ttu-id="d5f83-167">İletiyi okurken hizmetin sonucunu görmek için istemciyi çalışır durumda bırakın</span><span class="sxs-lookup"><span data-stu-id="d5f83-167">Leave the client running to see the result of the service reading the message</span></span>

5. <span data-ttu-id="d5f83-168">MSMQ etkinleştirme hizmeti varsayılan olarak ağ hizmeti olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-168">The MSMQ activation service runs as Network Service by default.</span></span> <span data-ttu-id="d5f83-169">Bu nedenle, uygulamayı etkinleştirmek için kullanılan sıranın ağ hizmeti için alma ve göz atma izinlerine sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-169">Therefore, the queue that is used to activate the application must have receive and peek permissions for Network Service.</span></span> <span data-ttu-id="d5f83-170">Bu, Message Queuing MMC kullanılarak eklenebilir:</span><span class="sxs-lookup"><span data-stu-id="d5f83-170">This can be added by using the Message Queuing MMC:</span></span>

    1. <span data-ttu-id="d5f83-171">**Başlat** menüsünde **Çalıştır**' a tıklayın ve yazın `Compmgmt.msc` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d5f83-171">From the **Start** menu, click **Run**, then type `Compmgmt.msc` and press ENTER.</span></span>

    2. <span data-ttu-id="d5f83-172">**Hizmetler ve uygulamalar**altında **Message Queuing**' ı genişletin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-172">Under **Services and Applications**, expand **Message Queuing**.</span></span>

    3. <span data-ttu-id="d5f83-173">**Özel kuyruklar**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5f83-173">Click **Private Queues**.</span></span>

    4. <span data-ttu-id="d5f83-174">Kuyruğa (servicemodelsamples/service. svc) sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-174">Right-click the queue (servicemodelsamples/Service.svc) and choose **Properties**.</span></span>

    5. <span data-ttu-id="d5f83-175">**Güvenlik** sekmesinde, **Ekle** ' ye tıklayın ve ağ hizmetine göz atma ve alma izinleri verin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-175">On the **Security** tab, click **Add** and give peek and receive permissions to Network Service.</span></span>

6. <span data-ttu-id="d5f83-176">Windows Işlem etkinleştirme hizmeti 'ni (WAS) MSMQ etkinleştirmesini destekleyecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="d5f83-176">Configure the Windows Process Activation Service (WAS) to support MSMQ activation.</span></span>

    <span data-ttu-id="d5f83-177">Kolaylık olması halinde, örnek dizinde bulunan AddMsmqSiteBinding. cmd adlı bir toplu iş dosyasında aşağıdaki adımlar uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-177">As a convenience, the following steps are implemented in a batch file called AddMsmqSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="d5f83-178">Net. MSMQ etkinleştirmesini desteklemek için, önce varsayılan Web sitesi önce net. MSMQ protokolüne bağlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-178">To support net.msmq activation, the default Web site must first be bound to the net.msmq protocol.</span></span> <span data-ttu-id="d5f83-179">Bu, IIS 7,0 yönetim araç takımı ile yüklenen appcmd. exe kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-179">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="d5f83-180">Yükseltilmiş (yönetici) komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d5f83-180">From an elevated (administrator) command prompt, run the following command.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']
        ```

        > [!NOTE]
        > <span data-ttu-id="d5f83-181">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-181">This command is a single line of text.</span></span>

        <span data-ttu-id="d5f83-182">Bu komut, varsayılan Web sitesine bir net. MSMQ site bağlaması ekler.</span><span class="sxs-lookup"><span data-stu-id="d5f83-182">This command adds a net.msmq site binding to the default Web site.</span></span>

    2. <span data-ttu-id="d5f83-183">Bir sitedeki tüm uygulamalar ortak bir net. MSMQ bağlamasını paylaşır, ancak her uygulama net. MSMQ desteğini tek tek etkinleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-183">Although all applications within a site share a common net.msmq binding, each application can enable net.msmq support individually.</span></span> <span data-ttu-id="d5f83-184">/Servicemodelsamples uygulaması için net. MSMQ ' yı etkinleştirmek için, yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d5f83-184">To enable net.msmq for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq
        ```

        > [!NOTE]
        > <span data-ttu-id="d5f83-185">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-185">This command is a single line of text.</span></span>

        <span data-ttu-id="d5f83-186">Bu komut, ve `http://localhost/servicemodelsamples` `net.msmq://localhost/servicemodelsamples`kullanarak/servicemodelsamples uygulamasına erişilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5f83-186">This command enables the /servicemodelsamples application to be accessed using `http://localhost/servicemodelsamples` and `net.msmq://localhost/servicemodelsamples`.</span></span>

7. <span data-ttu-id="d5f83-187">Daha önce yapmadıysanız, MSMQ etkinleştirme hizmeti 'nin etkinleştirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d5f83-187">If you have not done so previously, ensure that the MSMQ activation service is enabled.</span></span> <span data-ttu-id="d5f83-188">**Başlat** menüsünde **Çalıştır**' a tıklayın ve yazın `Services.msc`.</span><span class="sxs-lookup"><span data-stu-id="d5f83-188">From the **Start** menu, click **Run**, and type `Services.msc`.</span></span> <span data-ttu-id="d5f83-189">**Net. MSMQ dinleyicisi bağdaştırıcısı**için Hizmetler listesinde arama yapın.</span><span class="sxs-lookup"><span data-stu-id="d5f83-189">Search the list of services for the **Net.Msmq Listener Adapter**.</span></span> <span data-ttu-id="d5f83-190">Sağ tıklayın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-190">Right-click and select **Properties**.</span></span> <span data-ttu-id="d5f83-191">**Başlangıç türünü** **Otomatik**olarak ayarlayın, **Uygula** ' ya tıklayın ve **Başlat** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d5f83-191">Set the **Startup Type** to **Automatic**, click **Apply** and click the **Start** button.</span></span> <span data-ttu-id="d5f83-192">Bu adım yalnızca, net. MSMQ dinleyicisi bağdaştırıcısı hizmetinin ilk kullanımından önce bir kez yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-192">This step must only be done once prior to the first usage of the Net.Msmq Listener Adapter service.</span></span>

8. <span data-ttu-id="d5f83-193">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-193">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="d5f83-194">Ayrıca, satın alma siparişi gönderen istemcideki kodu, satın alma siparişi gönderilirken kuyruğun URI 'sindeki bilgisayar adını yansıtacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-194">Additionally, change the code on the client that submits the purchase order to reflect the computer name in the URI of the queue when submitting the purchase order.</span></span> <span data-ttu-id="d5f83-195">Aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="d5f83-195">Use the following code:</span></span>

    ```csharp
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");
    ```

9. <span data-ttu-id="d5f83-196">Bu örnek için eklemiş olduğunuz net. MSMQ site bağlamasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="d5f83-196">Remove the net.msmq site binding you added for this sample.</span></span>

    <span data-ttu-id="d5f83-197">Kolaylık olması açısından, aşağıdaki adımlar örnek dizinde bulunan RemoveMsmqSiteBinding. cmd adlı bir toplu iş dosyasında uygulanır:</span><span class="sxs-lookup"><span data-stu-id="d5f83-197">As a convenience, the following steps are implemented in a batch file called RemoveMsmqSiteBinding.cmd located in the sample directory:</span></span>

    1. <span data-ttu-id="d5f83-198">Yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak, etkin protokoller listesinden net. MSMQ ' yı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="d5f83-198">Remove net.msmq from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="d5f83-199">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-199">This command is a single line of text.</span></span>

    2. <span data-ttu-id="d5f83-200">Yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak net. MSMQ site bağlamasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="d5f83-200">Remove the net.msmq site binding by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']
        ```

        > [!NOTE]
        > <span data-ttu-id="d5f83-201">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-201">This command is a single line of text.</span></span>

    > [!WARNING]
    > <span data-ttu-id="d5f83-202">Toplu iş dosyasını çalıştırmak, .NET Framework sürüm 2,0 kullanılarak çalıştırılacak DefaultAppPool öğesini sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="d5f83-202">Running the batch file will reset the DefaultAppPool to run using .NET Framework version 2.0.</span></span>

<span data-ttu-id="d5f83-203">Varsayılan olarak, `netMsmqBinding` bağlama aktarımında güvenlik etkindir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-203">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="d5f83-204">İki özellik `MsmqAuthenticationMode` ve `MsmqProtectionLevel`, birlikte taşıma güvenliği türü belirlenir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-204">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="d5f83-205">Varsayılan olarak, kimlik doğrulama modu olarak `Windows` ayarlanır ve koruma düzeyi olarak `Sign`ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-205">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="d5f83-206">Kimlik doğrulama ve imzalama özelliğini sağlamak için MSMQ 'nun bir etki alanının parçası olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5f83-206">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="d5f83-207">Bu örneği bir etki alanının parçası olmayan bir bilgisayarda çalıştırırsanız, aşağıdaki hata alınır: "Kullanıcının iç Message Queuing sertifikası yok".</span><span class="sxs-lookup"><span data-stu-id="d5f83-207">If you run this sample on a computer that is not part of a domain, the following error is received: "User's internal message queuing certificate does not exist".</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="d5f83-208">Örneği çalışma grubuna katılmış bir bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="d5f83-208">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="d5f83-209">Bilgisayarınız bir etki alanının parçası değilse, aşağıdaki örnek yapılandırmada gösterildiği gibi kimlik doğrulama modu ve koruma düzeyini yok olarak ayarlayarak aktarım güvenliğini kapatın.</span><span class="sxs-lookup"><span data-stu-id="d5f83-209">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to none as shown in the following sample configuration.</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding configurationName="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

2. <span data-ttu-id="d5f83-210">Örneği çalıştırmadan önce hem sunucu hem de istemci üzerinde yapılandırmayı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-210">Change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d5f83-211">`security mode` Ayarı,`MsmqProtectionLevel` ayarına ve güvenliğineeşdeğerdir.`Message` `None` `MsmqAuthenticationMode` `None`</span><span class="sxs-lookup"><span data-stu-id="d5f83-211">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>

3. <span data-ttu-id="d5f83-212">Bir çalışma grubuna katılmış bir bilgisayarda etkinleştirmeyi etkinleştirmek için, hem etkinleştirme hizmeti hem de çalışan işleminin belirli bir kullanıcı hesabıyla çalıştırılması gerekir (her ikisi için de aynı olmalıdır) ve kuyruğun belirli kullanıcı hesabı için ACL 'Leri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-212">To enable activation in a computer joined to a workgroup, both the activation service and the worker process must be run with a specific user account (must be same for both) and the queue must have ACLs for the specific user account.</span></span>

     <span data-ttu-id="d5f83-213">Çalışan işleminin çalıştırıldığı kimliği değiştirmek için:</span><span class="sxs-lookup"><span data-stu-id="d5f83-213">To change the identity that the worker process runs under:</span></span>

    1. <span data-ttu-id="d5f83-214">Inetmgr. exe ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d5f83-214">Run Inetmgr.exe.</span></span>

    2. <span data-ttu-id="d5f83-215">**Uygulama havuzları**altında, **AppPool** öğesine sağ tıklayın (genellikle **DefaultAppPool**) ve **uygulama havuzu varsayılanlarını ayarla..** . seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-215">Under **Application Pools**, right-click the **AppPool** (typically **DefaultAppPool**) and choose **Set Application Pool Defaults…**.</span></span>

    3. <span data-ttu-id="d5f83-216">Kimlik özelliklerini belirli kullanıcı hesabını kullanacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-216">Change the Identity properties to use the specific user account.</span></span>

     <span data-ttu-id="d5f83-217">Etkinleştirme hizmetinin altında çalıştığı kimliği değiştirmek için:</span><span class="sxs-lookup"><span data-stu-id="d5f83-217">To change the identity that the Activation Service runs under:</span></span>

    1. <span data-ttu-id="d5f83-218">Services. msc dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d5f83-218">Run Services.msc.</span></span>

    2. <span data-ttu-id="d5f83-219">**Net. MsmqListener bağdaştırıcısını**sağ tıklatın ve **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-219">Right-click the **Net.MsmqListener Adapter**, and choose **Properties**.</span></span>

4. <span data-ttu-id="d5f83-220">Hesabı **oturum açma** sekmesinden değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d5f83-220">Change the account in the **LogOn** tab.</span></span>

5. <span data-ttu-id="d5f83-221">Çalışma grubunda, hizmet kısıtlanmamış bir belirteç kullanarak da çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d5f83-221">In workgroup, the service must also run using an unrestricted token.</span></span> <span data-ttu-id="d5f83-222">Bunu yapmak için, komut penceresinde aşağıdakileri çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="d5f83-222">To do this, run the following in a command window:</span></span>

    ```console
    sc sidtype netmsmqactivator unrestricted
    ```

## <a name="see-also"></a><span data-ttu-id="d5f83-223">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5f83-223">See also</span></span>

- [<span data-ttu-id="d5f83-224">AppFabric barındırma ve kalıcılık örnekleri</span><span class="sxs-lookup"><span data-stu-id="d5f83-224">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
