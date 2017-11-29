---
title: "Geçici Kuyruğa Alınmış İletişim"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d012f64-51c7-41d0-8e18-c756f658ee3d
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a7e6bb57245e9877fe337b86a03565d0197b0084
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="volatile-queued-communication"></a><span data-ttu-id="d5623-102">Geçici Kuyruğa Alınmış İletişim</span><span class="sxs-lookup"><span data-stu-id="d5623-102">Volatile Queued Communication</span></span>
<span data-ttu-id="d5623-103">Bu örnek, Message Queuing (MSMQ) aktarımı üzerinden geçici kuyruğa alınan iletişim gerçekleştirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d5623-103">This sample demonstrates how to perform volatile queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="d5623-104">Bu örnekte <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="d5623-104">This sample uses <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="d5623-105">Bu durumda, sıraya alınan iletileri alma hizmeti izlemek etkinleştirmek için bir kendi kendini barındıran konsol uygulaması hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="d5623-105">The service in this case is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5623-106">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="d5623-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d5623-107">Kuyruğa alınan iletişim, istemci bir sıra kullanarak hizmeti ile iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="d5623-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="d5623-108">Daha hassas bir şekilde istemci kuyruğa ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="d5623-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="d5623-109">Hizmet kuyruktan iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="d5623-109">The service receives messages from the queue.</span></span> <span data-ttu-id="d5623-110">Hizmet ve istemci bu nedenle, bir sıra kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d5623-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="d5623-111">Hiçbir garanti vermediğini içeren bir ileti gönderirken MSMQ yalnızca ileti aksine tam olarak bir kez çıkışların ile burada MSMQ İleti teslim veya teslim edilmemesi durumunda, ileti teslim bilmenizi sağlar, sağlar teslim etmek için en iyi çaba hale getirir.</span><span class="sxs-lookup"><span data-stu-id="d5623-111">When you send a message with no assurances, MSMQ only makes a best effort to deliver the message, unlike with Exactly Once assurances where MSMQ ensures that the message gets delivered or, if it cannot be delivered, lets you know that the message cannot be delivered.</span></span>  
  
 <span data-ttu-id="d5623-112">Belirli senaryolarda zamanında teslim iletileri kaybetme değerinden daha önemli olduğu durumlarda bir kuyruk hiçbir garanti vermediğini içeren geçici bir ileti göndermek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5623-112">In certain scenarios, you may want to send a volatile message with no assurances over a queue, when timely delivery is more important than losing messages.</span></span> <span data-ttu-id="d5623-113">Volatile iletileri sıra yöneticisi çökme (Crash) varlığını sürdürmesini değil.</span><span class="sxs-lookup"><span data-stu-id="d5623-113">Volatile messages do not survive queue manager crashes.</span></span> <span data-ttu-id="d5623-114">Bu nedenle sıra yöneticisini çökerse volatile iletileri depolamak için kullanılan işlem dışı sırası devam eder ancak iletileri disk üzerinde değil depolanmadığından iletilerini kendileri yapın.</span><span class="sxs-lookup"><span data-stu-id="d5623-114">Therefore if the queue manager crashes, the non-transactional queue used to store volatile messages survives but the messages themselves do not because the messages are not stored on the disk.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5623-115">MSMQ kullanarak bir işlem kapsamı içinde hiçbir garanti vermediğini ile volatile iletiler gönderemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5623-115">You cannot send volatile messages with no assurances within the scope of a transaction using MSMQ.</span></span> <span data-ttu-id="d5623-116">Volatile iletileri göndermek için işlemsel olmayan bir sıraya da oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5623-116">You also must create a non-transactional queue to send volatile messages.</span></span>  
  
 <span data-ttu-id="d5623-117">Bu örnekte service sözleşmedir `IStockTicker` queuing ile kullanmak için en uygun tek yönlü hizmetler tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d5623-117">The service contract in this sample is `IStockTicker` that defines one-way services that are best suited for use with queuing.</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IStockTicker  
{  
    [OperationContract(IsOneWay = true)]  
    void StockTick(string symbol, float price);  
}  
```  
  
 <span data-ttu-id="d5623-118">Aşağıdaki örnek kodda gösterildiği gibi borsa ve fiyat, hizmet işlemi görüntüler:</span><span class="sxs-lookup"><span data-stu-id="d5623-118">The service operation displays the stock ticker symbol and price, as shown in the following sample code:</span></span>  
  
```  
public class StockTickerService : IStockTicker  
{  
    public void StockTick(string symbol, float price)  
    {  
        Console.WriteLine("Stock Tick {0}:{1} ", symbol, price);  
     }  
     …  
}  
```  
  
 <span data-ttu-id="d5623-119">Kendi kendini barındırılan hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="d5623-119">The service is self hosted.</span></span> <span data-ttu-id="d5623-120">MSMQ taşıma kullanırken, sıranın kullanılan önceden oluşturulmuş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5623-120">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="d5623-121">Bu, el ile veya kod aracılığıyla yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5623-121">This can be done manually or through code.</span></span> <span data-ttu-id="d5623-122">Bu örnekte, hizmet sırası varlığını denetlemek ve gerekirse oluşturmak için kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="d5623-122">In this sample, the service contains code to check for the existence of the queue and create it if required.</span></span> <span data-ttu-id="d5623-123">Kuyruk adı yapılandırma dosyasından okunur.</span><span class="sxs-lookup"><span data-stu-id="d5623-123">The queue name is read from the configuration file.</span></span> <span data-ttu-id="d5623-124">Temel adres tarafından kullanılan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmeti için proxy oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="d5623-124">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy for the service.</span></span>  
  
```  
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
  
 <span data-ttu-id="d5623-125">Yapılandırma dosyasının appSettings bölümünde belirtilen MSMQ sırası adı.</span><span class="sxs-lookup"><span data-stu-id="d5623-125">The MSMQ queue name is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="d5623-126">Hizmeti için uç noktaya yapılandırma dosyası system.serviceModel bölümünde tanımlanan ve belirten `netMsmqBinding` bağlama.</span><span class="sxs-lookup"><span data-stu-id="d5623-126">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5623-127">Kuyruk adı bir nokta (.) için yerel makine ve eğik çizgi ayırıcıları yolundaki kullanarak bir sıra oluştururken kullandığı <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="d5623-127">The queue name uses a dot (.) for the local machine and backslash separators in its path when creating a queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="d5623-128">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Uç noktası adresi bir net.msmq belirtir: Düzen, LocalMachine ve eğik yolundaki "localhost" kullanır.</span><span class="sxs-lookup"><span data-stu-id="d5623-128">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine and forward slashes in its path.</span></span>  
  
 <span data-ttu-id="d5623-129">Çıkışların ve dayanıklılık veya iletilerinin volatilite de yapılandırmada belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="d5623-129">The assurances and durability or volatility of messages are also specified in the configuration.</span></span>  
  
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
  
 <span data-ttu-id="d5623-130">Örnek, işlemsel olmayan bir sıraya kullanarak sıraya alınan iletileri gönderdiğinden, işlenen iletiler sıraya gönderilemez.</span><span class="sxs-lookup"><span data-stu-id="d5623-130">Because the sample sends queued messages by using a non-transactional queue, transacted messages cannot be sent to the queue.</span></span>  
  
```  
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
  
 <span data-ttu-id="d5623-131">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d5623-131">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="d5623-132">İstemci hizmeti alma iletileri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5623-132">You can see the service receive messages from the client.</span></span> <span data-ttu-id="d5623-133">Her konsol penceresinde hizmet ve istemci kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d5623-133">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="d5623-134">Queuing kullanımda olduğundan, istemci ve hizmet aynı anda açık ve çalışıyor olması sahip olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d5623-134">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="d5623-135">İstemcisini çalıştıran, kapatmak ve hizmeti başlatın ve hala kendi iletilerini alır.</span><span class="sxs-lookup"><span data-stu-id="d5623-135">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d5623-136">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="d5623-136">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d5623-137">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d5623-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d5623-138">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d5623-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d5623-139">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d5623-139">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="d5623-140">Varsayılan olarak <xref:System.ServiceModel.NetMsmqBinding>, taşıma güvenliği etkindir.</span><span class="sxs-lookup"><span data-stu-id="d5623-140">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="d5623-141">MSMQ taşıma güvenliği için iki ilgili özellikler yok <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ve <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` varsayılan olarak, kimlik doğrulama modu ayarlamak `Windows` ve koruma düzeyini ayarlamak `Sign`.</span><span class="sxs-lookup"><span data-stu-id="d5623-141">There are two pertinent properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="d5623-142">Bir etki alanının parçası olması gerekir ve kimlik doğrulaması ve imzalama özelliği, MSMQ için MSMQ active directory tümleştirme seçeneğini yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5623-142">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="d5623-143">Bu ölçütleri karşılayan olmayan bir bilgisayarda bu örnek çalıştırırsanız, bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="d5623-143">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="d5623-144">Örnek bir çalışma grubu ya da active directory tümleştirmesi olmadan alanına katılmış bir bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="d5623-144">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="d5623-145">Bilgisayarınız bir etki alanının parçası değil veya yüklü active directory tümleştirmesi yok gerekirse kimlik doğrulama modu ve koruma düzeyini ayarlayarak taşıma güvenliği devre dışı bırakmak `None` aşağıdaki örnek yapılandırma kodda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="d5623-145">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code:</span></span>  
  
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
  
2.  <span data-ttu-id="d5623-146">Örneği çalıştırmadan önce hem sunucu hem de istemci yapılandırmasına değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d5623-146">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d5623-147">Ayarı `security mode` için `None` ayarına eşdeğerdir <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, ve `Message` güvenlik `None`.</span><span class="sxs-lookup"><span data-stu-id="d5623-147">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d5623-148">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="d5623-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d5623-149">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d5623-149">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d5623-150">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d5623-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d5623-151">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d5623-151">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Volatile`  
  
## <a name="see-also"></a><span data-ttu-id="d5623-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d5623-152">See Also</span></span>
