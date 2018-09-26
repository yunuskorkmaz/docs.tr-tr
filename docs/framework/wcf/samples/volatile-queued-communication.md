---
title: Geçici Kuyruğa Alınmış İletişim
ms.date: 03/30/2017
ms.assetid: 0d012f64-51c7-41d0-8e18-c756f658ee3d
ms.openlocfilehash: 55c2b695cdc672216ef6a76bef55bc0d427336a0
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47204055"
---
# <a name="volatile-queued-communication"></a><span data-ttu-id="d2bad-102">Geçici Kuyruğa Alınmış İletişim</span><span class="sxs-lookup"><span data-stu-id="d2bad-102">Volatile Queued Communication</span></span>
<span data-ttu-id="d2bad-103">Bu örnek, Message Queuing (MSMQ) aktarma üzerinden geçici kuyruğa alınan iletişim gerçekleştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2bad-103">This sample demonstrates how to perform volatile queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="d2bad-104">Bu örnekte <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="d2bad-104">This sample uses <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="d2bad-105">Bu durumda, kuyruğa alınmış iletiler alma hizmeti gözlemleyin sağlamak için şirket içinde barındırılan bir konsol uygulaması hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="d2bad-105">The service in this case is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2bad-106">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="d2bad-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d2bad-107">Kuyruğa alınan iletişim kullanarak bir kuyruk hizmetine istemci iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="d2bad-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="d2bad-108">Daha kesin bir istemci bir kuyruğa iletiler gönderir.</span><span class="sxs-lookup"><span data-stu-id="d2bad-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="d2bad-109">Hizmet iletileri kuyruktan alır.</span><span class="sxs-lookup"><span data-stu-id="d2bad-109">The service receives messages from the queue.</span></span> <span data-ttu-id="d2bad-110">Hizmet ve istemci bu nedenle, bir kuyruk kullanarak iletişim kurmak için aynı anda çalıştırılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d2bad-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="d2bad-111">Hiçbir Güvenceleri içeren bir ileti gönderirken MSMQ yalnızca ileti aksine tam bir kez Güvenceleri ile burada MSMQ iletiyi teslim edildiğinden veya teslim edilemiyor, ileti teslim bilmenizi sağlar, sağlar sunmak için bir en iyi hale getirir.</span><span class="sxs-lookup"><span data-stu-id="d2bad-111">When you send a message with no assurances, MSMQ only makes a best effort to deliver the message, unlike with Exactly Once assurances where MSMQ ensures that the message gets delivered or, if it cannot be delivered, lets you know that the message cannot be delivered.</span></span>  
  
 <span data-ttu-id="d2bad-112">Belirli senaryolarda zamanında teslimat iletileri kaybetme değerinden daha önemli olduğunda, bir kuyruk hiçbir Güvenceleri içeren geçici bir ileti göndermek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2bad-112">In certain scenarios, you may want to send a volatile message with no assurances over a queue, when timely delivery is more important than losing messages.</span></span> <span data-ttu-id="d2bad-113">Volatile iletileri Kuyruk yöneticisi kilitlenmeleri sürdürmez.</span><span class="sxs-lookup"><span data-stu-id="d2bad-113">Volatile messages do not survive queue manager crashes.</span></span> <span data-ttu-id="d2bad-114">Bu nedenle sıra yöneticisini çökerse, geçici iletileri depolamak için kullanılan işlem olmayan sırasının devam eder ancak iletileri disk üzerinde değil depolanmadığından iletileri yapın.</span><span class="sxs-lookup"><span data-stu-id="d2bad-114">Therefore if the queue manager crashes, the non-transactional queue used to store volatile messages survives but the messages themselves do not because the messages are not stored on the disk.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2bad-115">MSMQ kullanarak bir işlem kapsamında hiçbir Güvenceleri geçici iletilerle gönderemez.</span><span class="sxs-lookup"><span data-stu-id="d2bad-115">You cannot send volatile messages with no assurances within the scope of a transaction using MSMQ.</span></span> <span data-ttu-id="d2bad-116">Ayrıca, geçici bir ileti göndermek için işlemsel olmayan bir sıraya oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2bad-116">You also must create a non-transactional queue to send volatile messages.</span></span>  
  
 <span data-ttu-id="d2bad-117">Bu hizmet sözleşme `IStockTicker` queuing ile kullanmak için en uygun tek yönlü hizmetler tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2bad-117">The service contract in this sample is `IStockTicker` that defines one-way services that are best suited for use with queuing.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IStockTicker  
{  
    [OperationContract(IsOneWay = true)]  
    void StockTick(string symbol, float price);  
}  
```

 <span data-ttu-id="d2bad-118">Hizmet işlemi borsa ve fiyat, aşağıdaki örnek kodda gösterildiği gibi görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="d2bad-118">The service operation displays the stock ticker symbol and price, as shown in the following sample code:</span></span>  
  
```csharp
public class StockTickerService : IStockTicker  
{  
    public void StockTick(string symbol, float price)  
    {  
        Console.WriteLine("Stock Tick {0}:{1} ", symbol, price);  
     }  
     …  
}  
```  
  
 <span data-ttu-id="d2bad-119">Kendi kendine barındırılan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="d2bad-119">The service is self hosted.</span></span> <span data-ttu-id="d2bad-120">MSMQ taşıma kullanırken, kullanılan kuyruk önceden oluşturulmuş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d2bad-120">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="d2bad-121">Bu, el ile veya kod aracılığıyla yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2bad-121">This can be done manually or through code.</span></span> <span data-ttu-id="d2bad-122">Bu örnekte, hizmet sıranın varlığını denetleyin ve gerekirse oluşturmak için kod içerir.</span><span class="sxs-lookup"><span data-stu-id="d2bad-122">In this sample, the service contains code to check for the existence of the queue and create it if required.</span></span> <span data-ttu-id="d2bad-123">Kuyruk adı yapılandırma dosyasından okunur.</span><span class="sxs-lookup"><span data-stu-id="d2bad-123">The queue name is read from the configuration file.</span></span> <span data-ttu-id="d2bad-124">Tarafından kullanılan taban adresini [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) proxy hizmeti için oluşturulacak.</span><span class="sxs-lookup"><span data-stu-id="d2bad-124">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy for the service.</span></span>  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName);  
  
    // Create a ServiceHost for the StockTickerService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(StockTickerService)))  
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

 <span data-ttu-id="d2bad-125">MSMQ kuyruk adı yapılandırma dosyasının appSettings bölümünde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="d2bad-125">The MSMQ queue name is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="d2bad-126">Hizmet için uç nokta yapılandırma dosyasının system.serviceModel bölümünde tanımlanan ve belirtir `netMsmqBinding` bağlama.</span><span class="sxs-lookup"><span data-stu-id="d2bad-126">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2bad-127">Kuyruk adı bir nokta (.) için yerel makine ve ters eğik çizgi ayırıcılar yolundaki bir kuyruk kullanma oluştururken kullandığı <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="d2bad-127">The queue name uses a dot (.) for the local machine and backslash separators in its path when creating a queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="d2bad-128">Windows Communication Foundation (WCF) uç nokta adresini belirten bir net.msmq: Düzen, eğik çizgi yolundaki ve yerel makine için "localhost" kullanır.</span><span class="sxs-lookup"><span data-stu-id="d2bad-128">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine and forward slashes in its path.</span></span>  
  
 <span data-ttu-id="d2bad-129">Güvenceleri ve dayanıklılık veya geçicilik iletilerinin de yapılandırmada belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="d2bad-129">The assurances and durability or volatility of messages are also specified in the configuration.</span></span>  
  
```xml  
<appSettings>  
  <!-- use appSetting to configure MSMQ queue name -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesVolatile" />  
</appSettings>  
  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.StockTickerService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
    ...  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"  
                binding="netMsmqBinding"  
                bindingConfiguration="volatileBinding"   
                contract="Microsoft.ServiceModel.Samples.IStockTicker" />  
    ...  
    </service>  
  </services>  
  
  <bindings>  
    <netMsmqBinding>  
      <binding name="volatileBinding"   
             durable="false"  
           exactlyOnce="false"/>  
    </netMsmqBinding>  
  </bindings>  
  ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="d2bad-130">Örnek, işlemsel olmayan bir sıraya kullanarak sıraya alınan iletileri gönderdiğinden, işlem yapılmış iletileri kuyruğa gönderilemez.</span><span class="sxs-lookup"><span data-stu-id="d2bad-130">Because the sample sends queued messages by using a non-transactional queue, transacted messages cannot be sent to the queue.</span></span>  

```csharp
// Create a client.  
Random r = new Random(137);  
  
StockTickerClient client = new StockTickerClient();  
  
float price = 43.23F;  
for (int i = 0; i < 10; i++)  
{  
    float increment = 0.01f * (r.Next(10));  
    client.StockTick("zzz" + i, price + increment);  
}  
  
//Closing the client gracefully cleans up resources.  
client.Close();  
```

 <span data-ttu-id="d2bad-131">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hizmet ve istemci konsol pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d2bad-131">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="d2bad-132">İstemciden hizmet alma iletileri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2bad-132">You can see the service receive messages from the client.</span></span> <span data-ttu-id="d2bad-133">Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d2bad-133">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="d2bad-134">Sıraya alma kullanımda olduğundan, istemci ve hizmet aynı zamanda açık ve çalışıyor olması gerekmez, unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d2bad-134">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="d2bad-135">İstemcisini çalıştıran da kapatın ve ardından hizmeti başlatın ve hala iletilerini alır.</span><span class="sxs-lookup"><span data-stu-id="d2bad-135">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Stock Tick zzz0:43.25  
Stock Tick zzz1:43.23  
Stock Tick zzz2:43.28  
Stock Tick zzz3:43.3  
Stock Tick zzz4:43.23  
Stock Tick zzz5:43.25  
Stock Tick zzz6:43.25  
Stock Tick zzz7:43.24  
Stock Tick zzz8:43.32  
Stock Tick zzz9:43.3  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d2bad-136">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d2bad-136">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d2bad-137">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d2bad-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d2bad-138">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d2bad-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d2bad-139">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d2bad-139">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="d2bad-140">Varsayılan olarak <xref:System.ServiceModel.NetMsmqBinding>, aktarım güvenliği etkin.</span><span class="sxs-lookup"><span data-stu-id="d2bad-140">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="d2bad-141">MSMQ taşıma güvenlik için iki testlerinizle ilgili olabilecek özellikler <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ve <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` varsayılan olarak, kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`.</span><span class="sxs-lookup"><span data-stu-id="d2bad-141">There are two pertinent properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="d2bad-142">MSMQ imzalama özelliği ve kimlik doğrulaması sağlamak için bir etki alanının parçası olması gerekir ve MSMQ active directory tümleştirme seçeneği yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="d2bad-142">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="d2bad-143">Bu ölçütleri karşılamayan bir bilgisayarda bu örneği çalıştırmak, bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="d2bad-143">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="d2bad-144">Örnek, bir çalışma grubuna veya active directory tümleştirmesi olmadan alanına katılmış bir bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="d2bad-144">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="d2bad-145">Bilgisayarınız bir etki alanının parçası değil veya yüklü active directory tümleştirmesi yok, aktarım güvenliği devre dışı kimlik doğrulama modu ve koruma düzeyi ayarlayarak kapatma `None` aşağıdaki örnek yapılandırma kodda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="d2bad-145">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code:</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <services>  
          <service name="Microsoft.ServiceModel.Samples.StockTickerService"  
                   behaviorConfiguration="StockTickerServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="volatileBinding"   
                      contract="Microsoft.ServiceModel.Samples.IStockTicker" />  
            <!-- the mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex -->  
            <endpoint address="mex"  
                      binding="mexHttpBinding"  
                      contract="IMetadataExchange" />  
  
          </service>  
        </services>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="volatileBinding"   
                  durable="false"  
                  exactlyOnce="false">  
              <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="StockTickerServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2.  <span data-ttu-id="d2bad-146">Örneği çalıştırmadan önce yapılandırma hem sunucu hem de istemci değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d2bad-146">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2bad-147">Ayarı `security mode` için `None` ayarlamakla eşdeğerdir <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, ve `Message` güvenlik `None`.</span><span class="sxs-lookup"><span data-stu-id="d2bad-147">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d2bad-148">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="d2bad-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d2bad-149">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d2bad-149">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d2bad-150">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d2bad-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d2bad-151">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d2bad-151">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Volatile`  
  
## <a name="see-also"></a><span data-ttu-id="d2bad-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d2bad-152">See Also</span></span>
