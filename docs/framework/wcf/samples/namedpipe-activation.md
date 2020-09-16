---
title: NamedPipe Etkinleştirme
ms.date: 03/30/2017
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
ms.openlocfilehash: 56775842a742d0c6b07c6870bfce524ed1d275fa
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556108"
---
# <a name="namedpipe-activation"></a><span data-ttu-id="7b9cc-102">NamedPipe Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="7b9cc-102">NamedPipe Activation</span></span>

<span data-ttu-id="7b9cc-103">Bu örnekte, ad kanalları üzerinden iletişim kuran bir hizmeti etkinleştirmek için Windows Işlem etkinleştirme hizmeti (WAS) kullanan bir hizmetin barındırılması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-103">This sample demonstrates hosting a service that uses Windows Process Activation Service (WAS) to activate a service that communicates over names pipes.</span></span> <span data-ttu-id="7b9cc-104">Bu örnek [Başlarken](getting-started-sample.md) ' e dayalıdır ve Windows Vista 'nın çalışmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-104">This sample is based on the [Getting Started](getting-started-sample.md) and requires Windows Vista to run.</span></span>

> [!NOTE]
> <span data-ttu-id="7b9cc-105">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7b9cc-106">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7b9cc-107">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="7b9cc-108">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7b9cc-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7b9cc-109">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`

## <a name="sample-details"></a><span data-ttu-id="7b9cc-110">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7b9cc-110">Sample Details</span></span>

<span data-ttu-id="7b9cc-111">Örnek, bir istemci konsol programından (. exe) ve Windows Işlem etkinleştirme Hizmetleri (WAS) tarafından etkinleştirilen bir çalışan işleminde barındırılan bir hizmet kitaplığından (. dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-111">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by the Windows Process Activation Services (WAS).</span></span> <span data-ttu-id="7b9cc-112">İstemci etkinliği konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-112">Client activity is visible in the console window.</span></span>

<span data-ttu-id="7b9cc-113">Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-113">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="7b9cc-114">Sözleşme, `ICalculator` Aşağıdaki örnek kodda gösterildiği gibi matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) sunan arabirim tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-114">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code.</span></span>

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

<span data-ttu-id="7b9cc-115">İstemci belirli bir matematik işlemine zaman uyumlu istekler yapar ve hizmet uygulamasını hesaplar ve ilgili sonucu döndürür.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-115">The client makes synchronous requests to a given math operation and the service implementation calculates and returns the appropriate result.</span></span>

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

<span data-ttu-id="7b9cc-116">Örnek, bir `netNamedPipeBinding` güvenlik olmadan değiştirilmiş bağlamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-116">The sample uses a modified `netNamedPipeBinding` binding with no security.</span></span> <span data-ttu-id="7b9cc-117">Bağlama, istemci ve hizmet için yapılandırma dosyalarında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-117">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="7b9cc-118">Hizmetin bağlama türü, `binding` Aşağıdaki örnek yapılandırmada gösterildiği gibi Endpoint öğesinin özniteliğinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-118">The binding type for the service is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>

<span data-ttu-id="7b9cc-119">Güvenli adlandırılmış kanal bağlamayı kullanmak istiyorsanız, sunucunun güvenlik modunu istediğiniz güvenlik ayarıyla değiştirin ve güncelleştirilmiş bir istemci yapılandırma dosyası almak için istemcide svcutil.exe yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-119">If you want use a secured named pipe binding, change the server's security mode to the desired security setting and run svcutil.exe again on the client to obtain an updated client configuration file.</span></span>

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

<span data-ttu-id="7b9cc-120">İstemcinin uç nokta bilgileri aşağıdaki örnek kodda gösterildiği gibi yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-120">The client’s endpoint information is configured as shown in the following sample code.</span></span>

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

<span data-ttu-id="7b9cc-121">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7b9cc-122">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-122">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7b9cc-123">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="7b9cc-123">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="7b9cc-124">IIS 7,0 'nin yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-124">Ensure that IIS 7.0 is installed.</span></span> <span data-ttu-id="7b9cc-125">WAS etkinleştirmesi için IIS 7,0 gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-125">IIS 7.0 is required for WAS activation.</span></span>

2. <span data-ttu-id="7b9cc-126">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-126">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="7b9cc-127">Ayrıca, WCF HTTP olmayan etkinleştirme bileşenlerini yüklemelisiniz:</span><span class="sxs-lookup"><span data-stu-id="7b9cc-127">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="7b9cc-128">**Başlat** menüsünde, **Denetim Masası**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-128">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="7b9cc-129">**Programlar ve Özellikler '** i seçin.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-129">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="7b9cc-130">**Windows bileşenlerini aç veya kapat**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-130">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="7b9cc-131">**Microsoft .NET Framework 3,0** düğümünü genişletin ve **Windows Communication Foundation HTTP olmayan etkinleştirme** özelliğini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-131">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="7b9cc-132">Windows Işlem etkinleştirme hizmeti 'ni (WAS) adlandırılmış kanal etkinleştirmesini destekleyecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-132">Configure the Windows Process Activation Service (WAS) to support named pipe activation.</span></span>

    <span data-ttu-id="7b9cc-133">Kolaylık olması halinde, örnek dizinde bulunan AddNetPipeSiteBinding. cmd adlı bir toplu iş dosyasında aşağıdaki iki adım uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-133">As a convenience, the following two steps are implemented in a batch file called AddNetPipeSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="7b9cc-134">Net. pipe etkinleştirmesini desteklemek için, önce varsayılan Web sitesinin net. pipe protokolüne bağlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-134">To support net.pipe activation, the default Web site must first be bound to the net.pipe protocol.</span></span> <span data-ttu-id="7b9cc-135">Bu, IIS 7,0 yönetim araç takımı ile yüklenen appcmd.exe kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-135">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="7b9cc-136">Yükseltilmiş (yönetici) komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-136">From an elevated (administrator) command prompt, run the following command.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="7b9cc-137">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-137">This command is a single line of text.</span></span>

        <span data-ttu-id="7b9cc-138">Bu komut, varsayılan Web sitesine bir net. pipe site bağlaması ekler.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-138">This command adds a net.pipe site binding to the default Web site.</span></span>

    2. <span data-ttu-id="7b9cc-139">Bir sitedeki tüm uygulamalar ortak bir net. pipe bağlamasını paylaşır, ancak her uygulama net. pipe desteğini tek tek etkinleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-139">Although all applications within a site share a common net.pipe binding, each application can enable net.pipe support individually.</span></span> <span data-ttu-id="7b9cc-140">/Servicemodelsamples uygulamasının net. pipe ' ı etkinleştirmek için, yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-140">To enable net.pipe for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe
        ```

        > [!NOTE]
        > <span data-ttu-id="7b9cc-141">Bu komut, tek satırlık bir metin.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-141">This command is a single line of text.</span></span>

        <span data-ttu-id="7b9cc-142">Bu komut, hem hem de kullanılarak/servicemodelsamples uygulamasına erişilmesini sağlar `http://localhost/servicemodelsamples` `net.tcp://localhost/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="7b9cc-142">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="7b9cc-143">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-143">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

5. <span data-ttu-id="7b9cc-144">Bu örnek için eklemiş olduğunuz net. pipe site bağlamasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-144">Remove the net.pipe site binding you added for this sample.</span></span>

    <span data-ttu-id="7b9cc-145">Kolaylık olması için aşağıdaki iki adım örnek dizinde yer alan RemoveNetPipeSiteBinding. cmd adlı bir toplu iş dosyasında uygulanır:</span><span class="sxs-lookup"><span data-stu-id="7b9cc-145">As a convenience, the following two steps are implemented in a batch file called RemoveNetPipeSiteBinding.cmd located in the sample directory:</span></span>

    1. <span data-ttu-id="7b9cc-146">Yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak, etkin protokoller listesinden net. TCP ' i kaldırın.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-146">Remove net.tcp from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="7b9cc-147">Bu komut tek satırlık bir metin olarak girilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-147">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="7b9cc-148">Yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak net. TCP site bağlamasını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-148">Remove the net.tcp site binding by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="7b9cc-149">Bu komutun tek satırlık bir metin olarak yazılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-149">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b9cc-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b9cc-150">See also</span></span>

- <span data-ttu-id="7b9cc-151">[AppFabric barındırma ve kalıcılık örnekleri](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="7b9cc-151">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
