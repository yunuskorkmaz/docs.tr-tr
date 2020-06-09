---
title: Geçici Kuyruğa Alınmış İletişim
ms.date: 03/30/2017
ms.assetid: 0d012f64-51c7-41d0-8e18-c756f658ee3d
ms.openlocfilehash: a9f7e8a96fd293c7f87cc19846a42a42f28de288
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602353"
---
# <a name="volatile-queued-communication"></a><span data-ttu-id="65204-102">Geçici Kuyruğa Alınmış İletişim</span><span class="sxs-lookup"><span data-stu-id="65204-102">Volatile Queued Communication</span></span>

<span data-ttu-id="65204-103">Bu örnek, Message Queuing (MSMQ) taşıması üzerinden geçici sıraya alınmış iletişimin nasıl gerçekleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="65204-103">This sample demonstrates how to perform volatile queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="65204-104">Bu örnek kullanır <xref:System.ServiceModel.NetMsmqBinding> .</span><span class="sxs-lookup"><span data-stu-id="65204-104">This sample uses <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="65204-105">Bu durumda hizmet, sıraya alınan iletileri alma hizmetini gözlemlemeye olanak sağlayan, kendine barındırılan bir konsol uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="65204-105">The service in this case is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

> [!NOTE]
> <span data-ttu-id="65204-106">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="65204-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="65204-107">Sıraya alınmış iletişimde istemci, hizmet ile bir kuyruk kullanarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="65204-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="65204-108">Daha kesin olarak, istemci iletileri bir kuyruğa gönderir.</span><span class="sxs-lookup"><span data-stu-id="65204-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="65204-109">Hizmet kuyruktaki iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="65204-109">The service receives messages from the queue.</span></span> <span data-ttu-id="65204-110">Bu nedenle, hizmet ve istemci, bir kuyruk kullanarak iletişim kurmak için aynı anda çalışıyor olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="65204-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

<span data-ttu-id="65204-111">Herhangi bir bilgi sahibi olmadan bir ileti gönderdiğinizde, MSMQ yalnızca iletiyi teslim etmek için en iyi çaba, MSMQ 'nun iletinin teslim edilmesini sağlayan veya teslim edileyemediği durumlarda iletinin teslim edilemez olduğunu bilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="65204-111">When you send a message with no assurances, MSMQ only makes a best effort to deliver the message, unlike with Exactly Once assurances where MSMQ ensures that the message gets delivered or, if it cannot be delivered, lets you know that the message cannot be delivered.</span></span>

<span data-ttu-id="65204-112">Belirli senaryolarda, bir kuyruk üzerinden hiçbir zaman daha önemli olan bir geçici ileti göndermek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65204-112">In certain scenarios, you may want to send a volatile message with no assurances over a queue, when timely delivery is more important than losing messages.</span></span> <span data-ttu-id="65204-113">Geçici iletiler, kuyruk yöneticisi kilitlenmelerinden devam etmez.</span><span class="sxs-lookup"><span data-stu-id="65204-113">Volatile messages do not survive queue manager crashes.</span></span> <span data-ttu-id="65204-114">Bu nedenle, kuyruk yöneticisi kilitlenirse, geçici iletileri daha fazla saklamak için kullanılan işlem dışı sıra, iletiler diskte depolanmadığı için ileti kendileri değildir.</span><span class="sxs-lookup"><span data-stu-id="65204-114">Therefore if the queue manager crashes, the non-transactional queue used to store volatile messages survives but the messages themselves do not because the messages are not stored on the disk.</span></span>

> [!NOTE]
> <span data-ttu-id="65204-115">MSMQ kullanarak bir işlemin kapsamı içinde hiçbir ölçü olmadan geçici iletiler gönderemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="65204-115">You cannot send volatile messages with no assurances within the scope of a transaction using MSMQ.</span></span> <span data-ttu-id="65204-116">Ayrıca geçici iletiler göndermek için işlemsel olmayan bir sıra oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="65204-116">You also must create a non-transactional queue to send volatile messages.</span></span>

<span data-ttu-id="65204-117">Bu örnekteki hizmet sözleşmesi, `IStockTicker` sıraya alma ile kullanım için en uygun olan tek yönlü hizmetleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="65204-117">The service contract in this sample is `IStockTicker` that defines one-way services that are best suited for use with queuing.</span></span>

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IStockTicker
{
    [OperationContract(IsOneWay = true)]
    void StockTick(string symbol, float price);
}
```

<span data-ttu-id="65204-118">Hizmet işlemi, aşağıdaki örnek kodda gösterildiği gibi hisse senedi bandı sembolünü ve fiyatını görüntüler:</span><span class="sxs-lookup"><span data-stu-id="65204-118">The service operation displays the stock ticker symbol and price, as shown in the following sample code:</span></span>

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

<span data-ttu-id="65204-119">Hizmet kendi kendine barındırılır.</span><span class="sxs-lookup"><span data-stu-id="65204-119">The service is self hosted.</span></span> <span data-ttu-id="65204-120">MSMQ aktarımını kullanırken kullanılan kuyruğun önceden oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="65204-120">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="65204-121">Bu, el ile veya kod aracılığıyla yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="65204-121">This can be done manually or through code.</span></span> <span data-ttu-id="65204-122">Bu örnekte hizmet, sıranın varlığını denetlemek ve gerekirse oluşturmak için kod içerir.</span><span class="sxs-lookup"><span data-stu-id="65204-122">In this sample, the service contains code to check for the existence of the queue and create it if required.</span></span> <span data-ttu-id="65204-123">Sıra adı yapılandırma dosyasından okundu.</span><span class="sxs-lookup"><span data-stu-id="65204-123">The queue name is read from the configuration file.</span></span> <span data-ttu-id="65204-124">Temel adres, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tarafından hizmete yönelik proxy oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="65204-124">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy for the service.</span></span>

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

<span data-ttu-id="65204-125">MSMQ kuyruğu adı, yapılandırma dosyasının appSettings bölümünde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="65204-125">The MSMQ queue name is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="65204-126">Hizmetin uç noktası, yapılandırma dosyasının System. serviceModel bölümünde tanımlanır ve `netMsmqBinding` bağlamayı belirtir.</span><span class="sxs-lookup"><span data-stu-id="65204-126">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>

> [!NOTE]
> <span data-ttu-id="65204-127">Kuyruk adı, kullanarak bir kuyruk oluştururken yerel makine ve ters eğik çizgi ayırıcıları için bir nokta (.) kullanır <xref:System.Messaging> .</span><span class="sxs-lookup"><span data-stu-id="65204-127">The queue name uses a dot (.) for the local machine and backslash separators in its path when creating a queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="65204-128">Windows Communication Foundation (WCF) uç noktası adresi bir net. MSMQ: Scheme belirtir, yerel makine için "localhost" kullanır ve yolunda eğik çizgiler kullanır.</span><span class="sxs-lookup"><span data-stu-id="65204-128">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine and forward slashes in its path.</span></span>

<span data-ttu-id="65204-129">Yapılandırmada Ayrıca, bir veya daha fazla ileti de belirtilir.</span><span class="sxs-lookup"><span data-stu-id="65204-129">The assurances and durability or volatility of messages are also specified in the configuration.</span></span>

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

<span data-ttu-id="65204-130">Örnek, işlem olmayan bir sıra kullanarak sıraya alınmış iletiler gönderdiğinden, işlem temelli iletiler kuyruğa gönderilemez.</span><span class="sxs-lookup"><span data-stu-id="65204-130">Because the sample sends queued messages by using a non-transactional queue, transacted messages cannot be sent to the queue.</span></span>

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

<span data-ttu-id="65204-131">Örneği çalıştırdığınızda, istemci ve hizmet etkinlikleri hem hizmet hem de istemci konsol pencereleri içinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="65204-131">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="65204-132">Hizmetin istemciden ileti alacağını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65204-132">You can see the service receive messages from the client.</span></span> <span data-ttu-id="65204-133">Hizmeti ve istemciyi kapatmak için her bir konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="65204-133">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="65204-134">Kuyruk kullanımda olduğu için istemci ve hizmetin aynı anda çalışmaya ve çalışır durumda olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="65204-134">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="65204-135">İstemcisini çalıştırabilir, kapatabilir ve ardından hizmeti başlatabilir ve yine de iletilerini alabilir.</span><span class="sxs-lookup"><span data-stu-id="65204-135">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>

```console
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

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="65204-136">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="65204-136">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="65204-137">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="65204-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="65204-138">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="65204-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="65204-139">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="65204-139">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

<span data-ttu-id="65204-140">Varsayılan olarak, <xref:System.ServiceModel.NetMsmqBinding> taşıma güvenliği etkindir.</span><span class="sxs-lookup"><span data-stu-id="65204-140">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="65204-141">MSMQ aktarım güvenliği için iki ilgili özellik vardır <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> ve <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` Varsayılan olarak, kimlik doğrulama modu olarak ayarlanır `Windows` ve koruma düzeyi olarak ayarlanır `Sign` .</span><span class="sxs-lookup"><span data-stu-id="65204-141">There are two pertinent properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="65204-142">Kimlik doğrulama ve imzalama özelliğini sağlamak için MSMQ için, bir etki alanının parçası olması ve MSMQ için Active Directory tümleştirme seçeneğinin yüklü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="65204-142">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="65204-143">Bu örneği bu ölçütlere uygun olmayan bir bilgisayarda çalıştırırsanız bir hata alırsınız.</span><span class="sxs-lookup"><span data-stu-id="65204-143">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="65204-144">Örneği bir çalışma grubuna katılmış veya Active Directory Tümleştirmesi olmadan bir bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="65204-144">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>

1. <span data-ttu-id="65204-145">Bilgisayarınız bir etki alanının parçası değilse veya Active Directory Tümleştirmesi yüklü değilse, `None` Aşağıdaki örnek yapılandırma kodunda gösterildiği gibi olarak kimlik doğrulama modu ve koruma düzeyini ayarlayarak aktarım güvenliğini kapatın:</span><span class="sxs-lookup"><span data-stu-id="65204-145">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code:</span></span>

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
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
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

2. <span data-ttu-id="65204-146">Örneği çalıştırmadan önce hem sunucu hem de istemci üzerinde yapılandırmayı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="65204-146">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="65204-147">Ayarı `security mode` `None` <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> , <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> ve güvenlik ayarlarına eşdeğerdir `Message` `None` .</span><span class="sxs-lookup"><span data-stu-id="65204-147">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="65204-148">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="65204-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="65204-149">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="65204-149">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="65204-150">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="65204-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="65204-151">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="65204-151">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Volatile`
