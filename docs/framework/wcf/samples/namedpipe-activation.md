---
title: "NamedPipe Etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cf2ca3fb6cf7e17c0c27a4b03d7c61c86d6961a6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="namedpipe-activation"></a><span data-ttu-id="b8e4d-102">NamedPipe Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b8e4d-102">NamedPipe Activation</span></span>
<span data-ttu-id="b8e4d-103">Bu örnek adları Kanallar üzerinden iletişim kuran bir hizmeti etkinleştirmek için Windows İşlem Etkinleştirme Hizmeti (WAS) kullanan bir hizmet barındırma gösterir.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-103">This sample demonstrates hosting a service that uses Windows Process Activation Service (WAS) to activate a service that communicates over names pipes.</span></span> <span data-ttu-id="b8e4d-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) ve gerektirir [!INCLUDE[wv](../../../../includes/wv-md.md)] çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and requires [!INCLUDE[wv](../../../../includes/wv-md.md)] to run.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8e4d-105">Kurulum yordam ve yapılandırma yönergeleri Bu örneği için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b8e4d-106">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b8e4d-107">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b8e4d-108">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b8e4d-109">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`  
  
## <a name="sample-details"></a><span data-ttu-id="b8e4d-110">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="b8e4d-110">Sample Details</span></span>  
 <span data-ttu-id="b8e4d-111">Örnek, bir istemci konsol program (.exe) ve Windows İşlem Etkinleştirme Hizmetleri (WAS) tarafından etkinleştirilen bir çalışan işlemde barındırılan hizmet kitaplığı (.dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-111">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by the Windows Process Activation Services (WAS).</span></span> <span data-ttu-id="b8e4d-112">İstemci etkinliği konsol penceresinde görünür olur.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-112">Client activity is visible in the console window.</span></span>  
  
 <span data-ttu-id="b8e4d-113">Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-113">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="b8e4d-114">Anlaşma tarafından tanımlanan `ICalculator` matematik işlemleri kullanıma sunan arabirim (eklemek, çıkarma, çarpma ve bölme) aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-114">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="b8e4d-115">İstemci eş zamanlı istekleri için verilen matematik işlemi yapar ve hizmet uygulaması hesaplar ve uygun sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-115">The client makes synchronous requests to a given math operation and the service implementation calculates and returns the appropriate result.</span></span>  
  
```  
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
  
 <span data-ttu-id="b8e4d-116">Örnek bir değiştirilmiş kullanır `netNamedPipeBinding` hiçbir güvenlik ile bağlama.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-116">The sample uses a modified `netNamedPipeBinding` binding with no security.</span></span> <span data-ttu-id="b8e4d-117">Bağlama, istemci ve hizmet için yapılandırma dosyalarında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-117">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="b8e4d-118">Bağlama türü hizmeti için uç nokta öğesinin belirtilen `binding` özniteliği aşağıdaki örnek yapılandırmada gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-118">The binding type for the service is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
 <span data-ttu-id="b8e4d-119">Güvenli adlandırılmış kanal bağlama kullanmak istiyorsanız, istenen güvenlik ayarına sunucunun güvenlik modunu değiştirme ve svcutil.exe güncelleştirilmiş bir istemci yapılandırma dosyasını edinmek için istemcide yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-119">If you want use a secured named pipe binding, change the server's security mode to the desired security setting and run svcutil.exe again on the client to obtain an updated client configuration file.</span></span>  
  
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
        <!-- the mex endpoint is explosed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->  
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
  
 <span data-ttu-id="b8e4d-120">İstemcinin uç nokta bilgileri, aşağıdaki örnek kodda gösterildiği şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-120">The client’s endpoint information is configured as shown in the following sample code.</span></span>  
  
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
            Each property is configured with the default value.   -->  
  
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
  
 <span data-ttu-id="b8e4d-121">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b8e4d-122">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b8e4d-123">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="b8e4d-123">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b8e4d-124">Emin [!INCLUDE[iisver](../../../../includes/iisver-md.md)] yüklenir.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-124">Ensure that [!INCLUDE[iisver](../../../../includes/iisver-md.md)] is installed.</span></span> [!INCLUDE[iisver](../../../../includes/iisver-md.md)]<span data-ttu-id="b8e4d-125">WAS etkinleştirme için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-125"> is required for WAS activation.</span></span>  
  
2.  <span data-ttu-id="b8e4d-126">Gerçekleştirilen olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8e4d-126">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
     <span data-ttu-id="b8e4d-127">Ayrıca, yüklemelisiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP olmayan etkinleştirme bileşenleri:</span><span class="sxs-lookup"><span data-stu-id="b8e4d-127">In addition, you must install the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] non-HTTP activation components:</span></span>  
  
    1.  <span data-ttu-id="b8e4d-128">Gelen **Başlat** menüsünde seçin **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-128">From the **Start** menu, choose **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="b8e4d-129">Seçin **programlar ve Özellikler**.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-129">Select **Programs and Features**.</span></span>  
  
    3.  <span data-ttu-id="b8e4d-130">Tıklatın **açma veya kapatma Windows bileşenleri**.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-130">Click **Turn Windows Components on or Off**.</span></span>  
  
    4.  <span data-ttu-id="b8e4d-131">Genişletme **Microsoft .NET Framework 3.0** düğümü ve onay **Windows Communication Foundation HTTP olmayan etkinleştirme** özelliği.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-131">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>  
  
3.  <span data-ttu-id="b8e4d-132">Adlandırılmış kanal etkinleştirmeyi desteklemek için Windows İşlem Etkinleştirme Hizmeti'nı (WAS) yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-132">Configure the Windows Process Activation Service (WAS) to support named pipe activation.</span></span>  
  
     <span data-ttu-id="b8e4d-133">Kolaylık, aşağıdaki iki adımdan örnek dizininde bulunan AddNetPipeSiteBinding.cmd adlı bir toplu iş dosyası uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-133">As a convenience, the following two steps are implemented in a batch file called AddNetPipeSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="b8e4d-134">NET.pipe etkinleştirmeyi desteklemek için varsayılan Web sitesi ilk net.pipe protokole bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-134">To support net.pipe activation, the default Web site must first be bound to the net.pipe protocol.</span></span> <span data-ttu-id="b8e4d-135">Bu yapılabilir ile IIS 7.0 Yönetim araç takımı yüklü appcmd.exe kullanma.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-135">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="b8e4d-136">(Yönetici) yükseltilmiş komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-136">From an elevated (administrator) command prompt, run the following command.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.pipe',bindingInformation='*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="b8e4d-137">Bu komut, metnin tek bir satırdır.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-137">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="b8e4d-138">Bu komut net.pipe site bağlaması varsayılan Web sitesine ekler.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-138">This command adds a net.pipe site binding to the default Web site.</span></span>  
  
    2.  <span data-ttu-id="b8e4d-139">Bir sitedeki tüm uygulamaları ortak net.pipe bağlama paylaşmak rağmen her uygulama net.pipe desteğini ayrı ayrı etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-139">Although all applications within a site share a common net.pipe binding, each application can enable net.pipe support individually.</span></span> <span data-ttu-id="b8e4d-140">NET.pipe /servicemodelsamples uygulama için etkinleştirmek için yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-140">To enable net.pipe for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="b8e4d-141">Bu komut, metnin tek bir satırdır.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-141">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="b8e4d-142">Bu komut /servicemodelsamples uygulama tarafından http://localhost/servicemodelsamples ve net.tcp://localhost/servicemodelsamples kullanarak erişilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-142">This command enables the /servicemodelsamples application to be accessed using both http://localhost/servicemodelsamples and net.tcp://localhost/servicemodelsamples.</span></span>  
  
4.  <span data-ttu-id="b8e4d-143">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8e4d-143">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="b8e4d-144">Eklediğiniz net.pipe site bağlaması Bu örnek için kaldırın.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-144">Remove the net.pipe site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="b8e4d-145">Kolaylık, örnek dizininde bulunan RemoveNetPipeSiteBinding.cmd adlı bir toplu iş dosyasında aşağıdaki iki adımdan uygulanır:</span><span class="sxs-lookup"><span data-stu-id="b8e4d-145">As a convenience, the following two steps are implemented in a batch file called RemoveNetPipeSiteBinding.cmd located in the sample directory:</span></span>  
  
    1.  <span data-ttu-id="b8e4d-146">NET.TCP yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak etkin protokoller listesinden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-146">Remove net.tcp from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="b8e4d-147">Bu komut, tek satırlık metin girilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-147">This command must be entered as a single line of text.</span></span>  
  
    2.  <span data-ttu-id="b8e4d-148">Net.tcp site bağlaması, yükseltilmiş bir komut isteminden aşağıdaki komutu çalıştırarak kaldırın.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-148">Remove the net.tcp site binding by running the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="b8e4d-149">Bu komutu, içinde tek satırlık metin yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-149">This command must be typed in as a single line of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8e4d-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b8e4d-150">See Also</span></span>  
 [<span data-ttu-id="b8e4d-151">AppFabric barındırma ve kalıcılığı örnekleri</span><span class="sxs-lookup"><span data-stu-id="b8e4d-151">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
