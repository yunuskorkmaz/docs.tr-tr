---
title: "TCP Etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 25dc9f7e09b4761dd1232700f43019c8ee51f0e2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="tcp-activation"></a><span data-ttu-id="7810f-102">TCP Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="7810f-102">TCP Activation</span></span>
<span data-ttu-id="7810f-103">Bu örnek net.tcp protokolü üzerinden iletişim kuran bir hizmeti etkinleştirmek için Windows İşlem Etkinleştirme Hizmetleri (WAS) kullanan bir hizmet barındırma gösterir.</span><span class="sxs-lookup"><span data-stu-id="7810f-103">This sample demonstrates hosting a service that uses Windows Process Activation Services (WAS) to activate a service that communicates over the net.tcp protocol.</span></span> <span data-ttu-id="7810f-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="7810f-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7810f-105">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="7810f-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7810f-106">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="7810f-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7810f-107">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7810f-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7810f-108">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7810f-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7810f-109">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7810f-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`  
  
 <span data-ttu-id="7810f-110">Örnek, bir istemci konsol program (.exe) ve WAS tarafından etkinleştirilen bir çalışan işlemde barındırılan hizmet kitaplığı (.dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="7810f-110">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by WAS.</span></span> <span data-ttu-id="7810f-111">İstemci etkinliği konsol penceresinde görünür olur.</span><span class="sxs-lookup"><span data-stu-id="7810f-111">Client activity is visible in the console window.</span></span>  
  
 <span data-ttu-id="7810f-112">Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="7810f-112">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="7810f-113">Anlaşma tarafından tanımlanan `ICalculator` matematik işlemleri kullanıma sunan arabirim (eklemek, çıkarma, çarpma ve bölme) aşağıdaki örnek kodda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="7810f-113">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code:</span></span>  
  
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
  
 <span data-ttu-id="7810f-114">Hizmet uygulaması hesaplar ve uygun sonucu döndürür:</span><span class="sxs-lookup"><span data-stu-id="7810f-114">The service implementation calculates and returns the appropriate result:</span></span>  
  
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
  
 <span data-ttu-id="7810f-115">Örnek bir TCP bağlantı noktası paylaşımı etkin ve devre dışı güvenlik bağlama net.tcp türevi kullanır.</span><span class="sxs-lookup"><span data-stu-id="7810f-115">The sample uses a variant of the net.tcp binding with TCP port sharing enabled and security turned off.</span></span> <span data-ttu-id="7810f-116">Güvenli TCP bağlaması kullanmak istiyorsanız, istenen ayara sunucunun güvenlik modunu değiştirme ve Svcutil.exe bir güncelleştirme istemci yapılandırma dosyası oluşturmak için istemcide yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7810f-116">If you want to use a secured TCP binding, change the server's security mode to the desired setting and re-run Svcutil.exe on the client to generate an update client configuration file.</span></span>  
  
 <span data-ttu-id="7810f-117">Aşağıdaki örnek, hizmet yapılandırmasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="7810f-117">The following sample shows the configuration for the service:</span></span>  
  
```xml  
<system.serviceModel>  
  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by host: net.tcp://localhost/servicemodelsamples/service.svc  -->  
        <endpoint binding="netTcpBinding" bindingConfiguration="PortSharingBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is explosed at net.tcp://localhost/servicemodelsamples/service.svc/mex -->  
        <endpoint address="mex"  
                  binding="mexTcpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="PortSharingBinding" portSharingEnabled="true">  
          <security mode="None" />  
        </binding>  
      </netTcpBinding>  
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
  
 <span data-ttu-id="7810f-118">İstemcinin uç noktası, aşağıdaki örnek kodda gösterildiği gibi yapılandırılır:</span><span class="sxs-lookup"><span data-stu-id="7810f-118">The client's endpoint is configured as shown in the following sample code:</span></span>  
  
```xml  
<system.serviceModel>  
    <bindings>  
        <netTcpBinding>  
          <binding name="NetTcpBinding_ICalculator">  
            <security mode="None"/>  
          </binding>  
        </netTcpBinding>  
    </bindings>  
    <client>  
        <endpoint address="net.tcp://localhost/servicemodelsamples/service.svc"  
            binding="netTcpBinding" bindingConfiguration="NetTcpBinding_ICalculator"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" name="NetTcpBinding_ICalculator" />  
    </client>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="7810f-119">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7810f-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7810f-120">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="7810f-120">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7810f-121">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="7810f-121">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7810f-122">Emin [!INCLUDE[iisver](../../../../includes/iisver-md.md)] yüklenir.</span><span class="sxs-lookup"><span data-stu-id="7810f-122">Ensure that [!INCLUDE[iisver](../../../../includes/iisver-md.md)] is installed.</span></span> [!INCLUDE[iisver](../../../../includes/iisver-md.md)]<span data-ttu-id="7810f-123">WAS etkinleştirme için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7810f-123"> is required for WAS activation.</span></span>  
  
2.  <span data-ttu-id="7810f-124">Gerçekleştirilen mutlaka [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7810f-124">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
     <span data-ttu-id="7810f-125">Ayrıca, yüklemelisiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] HTTP olmayan etkinleştirme bileşenleri:</span><span class="sxs-lookup"><span data-stu-id="7810f-125">In addition, you must install the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] non-HTTP activation components:</span></span>  
  
    1.  <span data-ttu-id="7810f-126">Gelen **Başlat** menüsünde seçin **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="7810f-126">From the **Start** menu, choose **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="7810f-127">Seçin **programlar ve Özellikler**.</span><span class="sxs-lookup"><span data-stu-id="7810f-127">Select **Programs and Features**.</span></span>  
  
    3.  <span data-ttu-id="7810f-128">Tıklatın **açma veya kapatma Windows bileşenleri**.</span><span class="sxs-lookup"><span data-stu-id="7810f-128">Click **Turn Windows Components on or Off**.</span></span>  
  
    4.  <span data-ttu-id="7810f-129">Genişletme **Microsoft .NET Framework 3.0** düğümü ve onay **Windows Communication Foundation HTTP olmayan etkinleştirme** özelliği.</span><span class="sxs-lookup"><span data-stu-id="7810f-129">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>  
  
3.  <span data-ttu-id="7810f-130">WAS TCP etkinleştirilmesini destekleyecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="7810f-130">Configure WAS to support TCP activation.</span></span>  
  
     <span data-ttu-id="7810f-131">Kolaylık, aşağıdaki iki adımdan örnek dizininde bulunan AddNetTcpSiteBinding.cmd adlı bir toplu iş dosyası uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7810f-131">As a convenience, the following two steps are implemented in a batch file called AddNetTcpSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="7810f-132">NET.TCP etkinleştirmeyi desteklemek için varsayılan Web sitesi ilk net.tcp bağlantı noktasına bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7810f-132">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="7810f-133">Bu yapılabilir Internet Information Services 7.0 (IIS) yönetim araç takımı ile yüklü Appcmd.exe kullanma.</span><span class="sxs-lookup"><span data-stu-id="7810f-133">This can be done using Appcmd.exe, which is installed with the Internet Information Services 7.0 (IIS) management toolset.</span></span> <span data-ttu-id="7810f-134">Bir yönetici düzeyi komut isteminden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7810f-134">From an administrator-level command prompt, run the following command:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!TIP]
        >  <span data-ttu-id="7810f-135">Bu komut, metnin tek bir satırdır.</span><span class="sxs-lookup"><span data-stu-id="7810f-135">This command is a single line of text.</span></span> <span data-ttu-id="7810f-136">Bu komut, tüm ana bilgisayar adı ile 808 numaralı TCP bağlantı noktasını dinleme varsayılan Web sitesine net.tcp site bağlaması ekler.</span><span class="sxs-lookup"><span data-stu-id="7810f-136">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any hostname.</span></span>  
  
    2.  <span data-ttu-id="7810f-137">Bir sitedeki tüm uygulamaları ortak net.tcp bağlama paylaşmak rağmen her uygulama net.tcp desteğini ayrı ayrı etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7810f-137">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="7810f-138">NET.TCP /servicemodelsamples uygulama için etkinleştirmek için bir yönetici düzeyi komut isteminden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7810f-138">To enable net.tcp for the /servicemodelsamples application, run the following command from an administrator-level command prompt:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="7810f-139">Bu komut, metnin tek bir satırdır.</span><span class="sxs-lookup"><span data-stu-id="7810f-139">This command is a single line of text.</span></span> <span data-ttu-id="7810f-140">Bu komut /servicemodelsamples uygulama tarafından http://localhost/servicemodelsamples ve net.tcp://localhost/servicemodelsamples kullanarak erişilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7810f-140">This command enables the /servicemodelsamples application to be accessed using both http://localhost/servicemodelsamples and net.tcp://localhost/servicemodelsamples.</span></span>  
  
4.  <span data-ttu-id="7810f-141">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7810f-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="7810f-142">Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7810f-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
     <span data-ttu-id="7810f-143">Eklediğiniz net.tcp site bağlaması Bu örnek için kaldırın.</span><span class="sxs-lookup"><span data-stu-id="7810f-143">Remove the net.tcp site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="7810f-144">Kolaylık, aşağıdaki iki adımdan örnek dizininde bulunan RemoveNetTcpSiteBinding.cmd adlı bir toplu iş dosyası uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7810f-144">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="7810f-145">NET.TCP etkin protokoller listesinden bir yönetici düzeyi komut isteminden aşağıdaki komutu çalıştırarak kaldırın:</span><span class="sxs-lookup"><span data-stu-id="7810f-145">Remove net.tcp from the list of enabled protocols by running the following command from an administrator-level command prompt:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="7810f-146">Bu komut, tek satırlık metin girilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7810f-146">This command must be entered as a single line of text.</span></span>  
  
    2.  <span data-ttu-id="7810f-147">Net.tcp site bağlaması, bir yönetici düzeyi komut isteminden aşağıdaki komutu çalıştırarak kaldırın:</span><span class="sxs-lookup"><span data-stu-id="7810f-147">Remove the net.tcp site binding by running the following command from an administrator-level command prompt:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="7810f-148">Bu komutu, içinde tek satırlık metin yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7810f-148">This command must be typed in as a single line of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7810f-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7810f-149">See Also</span></span>  
 [<span data-ttu-id="7810f-150">AppFabric barındırma ve kalıcılığı örnekleri</span><span class="sxs-lookup"><span data-stu-id="7810f-150">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
