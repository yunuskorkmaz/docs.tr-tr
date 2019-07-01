---
title: NamedPipe Etkinleştirme
ms.date: 03/30/2017
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
ms.openlocfilehash: a7d940d6be56160945ca0f8697361314af96bc0b
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487545"
---
# <a name="namedpipe-activation"></a><span data-ttu-id="eb5d0-102">NamedPipe Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="eb5d0-102">NamedPipe Activation</span></span>

<span data-ttu-id="eb5d0-103">Bu örnek adları Kanallar üzerinden iletişim kuran bir hizmeti etkinleştirmek için Windows İşlem Etkinleştirme Hizmeti (WAS) kullanan bir hizmet barındırma gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-103">This sample demonstrates hosting a service that uses Windows Process Activation Service (WAS) to activate a service that communicates over names pipes.</span></span> <span data-ttu-id="eb5d0-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) ve gerektiren [!INCLUDE[wv](../../../../includes/wv-md.md)] çalıştırılacak.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and requires [!INCLUDE[wv](../../../../includes/wv-md.md)] to run.</span></span>

> [!NOTE]
> <span data-ttu-id="eb5d0-105">Bu örnek için Kurulum yordamı ve derleme yönergeleri Bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eb5d0-106">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="eb5d0-107">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="eb5d0-108">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="eb5d0-109">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`

## <a name="sample-details"></a><span data-ttu-id="eb5d0-110">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="eb5d0-110">Sample Details</span></span>

<span data-ttu-id="eb5d0-111">Örnek bir istemci konsol program (.exe) ve Windows İşlem Etkinleştirme Hizmetleri (WAS) tarafından etkin bir çalışan işleminin barındırılan hizmet kitaplığı (.dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-111">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by the Windows Process Activation Services (WAS).</span></span> <span data-ttu-id="eb5d0-112">İstemci etkinliği konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-112">Client activity is visible in the console window.</span></span>

<span data-ttu-id="eb5d0-113">Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-113">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="eb5d0-114">Anlaşma tarafından tanımlanan `ICalculator` matematik işlemlerinden sunan arabirimi (ekleme, çıkarma, çarpma ve bölme), aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-114">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="eb5d0-115">İstemci bir verilen matematik işlemi için zaman uyumlu istekleri yapar ve hizmet uygulaması hesaplar ve uygun sonucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-115">The client makes synchronous requests to a given math operation and the service implementation calculates and returns the appropriate result.</span></span>

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

<span data-ttu-id="eb5d0-116">Örnek bir değiştirilen kullanır `netNamedPipeBinding` ile güvenlik bağlama.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-116">The sample uses a modified `netNamedPipeBinding` binding with no security.</span></span> <span data-ttu-id="eb5d0-117">İstemci ve hizmet yapılandırma dosyalarında bağlama belirtildi.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-117">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="eb5d0-118">Bağlama türü için hizmet uç noktası öğenin belirtilen `binding` özniteliği aşağıdaki örnek yapılandırmada gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-118">The binding type for the service is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>

<span data-ttu-id="eb5d0-119">Güvenli bir adlandırılmış kanal bağlama kullanmak istiyorsanız, istenen güvenlik sunucunun güvenlik modunu değiştirin ve svcutil.exe güncelleştirilmiş bir istemci yapılandırma dosyası almak için istemcide yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-119">If you want use a secured named pipe binding, change the server's security mode to the desired security setting and run svcutil.exe again on the client to obtain an updated client configuration file.</span></span>

```xml
<system.serviceModel>
        <services>
            <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">

        <!-- This endpoint is exposed at the base address provided by host: net.pipe://localhost/servicemodelsamples/service.svc  -->
        <endpoint address=""
                  binding="netNamedPipeBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexNamedPipeBinding"
                  contract="IMetadataExchange" />
      </service>
        </services>
        <bindings>
            <netNamedPipeBinding>
                <binding name="Binding1" >
                    <security mode = "None">
                    </security>
                </binding >
            </netNamedPipeBinding>
        </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

<span data-ttu-id="eb5d0-120">İstemcinin uç nokta bilgileri, aşağıdaki örnek kodda gösterildiği şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-120">The client’s endpoint information is configured as shown in the following sample code.</span></span>

```xml
<system.serviceModel>

    <client>
      <endpoint name=""
                          address="net.pipe://localhost/servicemodelsamples/service.svc"
                          binding="netNamedPipeBinding"
                          bindingConfiguration="Binding1"
                          contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>

    <bindings>

      <!--  Following is the expanded configuration section for a NetNamedPipeBinding.
            Each property is configured with the default value. -->

      <netNamedPipeBinding>
        <binding name="Binding1"
                         maxBufferSize="65536"
                         maxConnections="10">
          <security mode = "None">
          </security>
        </binding >

      </netNamedPipeBinding>
    </bindings>

  </system.serviceModel>
```

<span data-ttu-id="eb5d0-121">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="eb5d0-122">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-122">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="eb5d0-123">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="eb5d0-123">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="eb5d0-124">IIS 7. 0'ın yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-124">Ensure that IIS 7.0 is installed.</span></span> <span data-ttu-id="eb5d0-125">WAS etkinleştirme için IIS 7.0 gereklidir.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-125">IIS 7.0 is required for WAS activation.</span></span>

2. <span data-ttu-id="eb5d0-126">Gerçekleştirdiğiniz olun [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-126">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="eb5d0-127">Ayrıca, WCF HTTP olmayan etkinleştirme bileşenlerini yüklemelisiniz:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-127">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="eb5d0-128">Gelen **Başlat** menüsünde seçin **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-128">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="eb5d0-129">Seçin **programlar ve Özellikler**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-129">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="eb5d0-130">Tıklayın **Aç veya kapat Windows bileşenleri**.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-130">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="eb5d0-131">Genişletin **Microsoft .NET Framework 3.0** düğüm ve onay **Windows Communication Foundation HTTP olmayan etkinleştirme** özelliği.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-131">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="eb5d0-132">Adlandırılmış kanal etkinleştirmeyi desteklemek için Windows İşlem Etkinleştirme Hizmeti'nı (WAS) yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-132">Configure the Windows Process Activation Service (WAS) to support named pipe activation.</span></span>

    <span data-ttu-id="eb5d0-133">Bir kolaylık olarak örnek dizinde yer AddNetPipeSiteBinding.cmd adlı bir toplu iş dosyasında aşağıdaki iki adımı uygulanır.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-133">As a convenience, the following two steps are implemented in a batch file called AddNetPipeSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="eb5d0-134">NET.pipe etkinleştirmeyi desteklemek için varsayılan Web sitesi ilk net.pipe protokole bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-134">To support net.pipe activation, the default Web site must first be bound to the net.pipe protocol.</span></span> <span data-ttu-id="eb5d0-135">Bu yapılabilir, IIS 7.0 Yönetim araç takımıyla yüklenmeyen appcmd.exe kullanarak.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-135">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="eb5d0-136">(Yönetici) yükseltilmiş komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-136">From an elevated (administrator) command prompt, run the following command.</span></span>

        ```
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="eb5d0-137">Tek metin satırı komutudur.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-137">This command is a single line of text.</span></span>

        <span data-ttu-id="eb5d0-138">Bu komut, varsayılan Web sitesine net.pipe site bağlaması ekler.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-138">This command adds a net.pipe site binding to the default Web site.</span></span>

    2. <span data-ttu-id="eb5d0-139">Bir sitedeki tüm uygulamaları genel net.pipe bağlama paylaşsa da her uygulama net.pipe destek ayrı ayrı etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-139">Although all applications within a site share a common net.pipe binding, each application can enable net.pipe support individually.</span></span> <span data-ttu-id="eb5d0-140">/Servicemodelsamples uygulamanın NET.pipe etkinleştirmek için yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-140">To enable net.pipe for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>

        ```
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe
        ```

        > [!NOTE]
        > <span data-ttu-id="eb5d0-141">Tek metin satırı komutudur.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-141">This command is a single line of text.</span></span>

        <span data-ttu-id="eb5d0-142">Bu komut, her ikisi de kullanılarak erişilecektir /servicemodelsamples uygulama etkinleştirir `http://localhost/servicemodelsamples` ve `net.tcp://localhost/servicemodelsamples`.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-142">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="eb5d0-143">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="eb5d0-143">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

5. <span data-ttu-id="eb5d0-144">Eklediğiniz net.pipe site bağlaması için bu örnek kaldırın.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-144">Remove the net.pipe site binding you added for this sample.</span></span>

    <span data-ttu-id="eb5d0-145">Bir kolaylık olarak örnek dizinde yer RemoveNetPipeSiteBinding.cmd adlı bir toplu iş dosyasında aşağıdaki iki adımı uygulanır:</span><span class="sxs-lookup"><span data-stu-id="eb5d0-145">As a convenience, the following two steps are implemented in a batch file called RemoveNetPipeSiteBinding.cmd located in the sample directory:</span></span>

    1. <span data-ttu-id="eb5d0-146">NET.TCP, yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak etkin protokoller listesinden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-146">Remove net.tcp from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>

        ```
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="eb5d0-147">Bu komut, tek satırlık bir metin girilmelidir.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-147">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="eb5d0-148">Net.tcp site bağlaması, yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak kaldırın.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-148">Remove the net.tcp site binding by running the following command from an elevated command prompt.</span></span>

        ```
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="eb5d0-149">Bu komut, tek satırlık bir metin yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-149">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb5d0-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb5d0-150">See also</span></span>

- <span data-ttu-id="eb5d0-151">[AppFabric barındırma ve Kalıcılık örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="eb5d0-151">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
