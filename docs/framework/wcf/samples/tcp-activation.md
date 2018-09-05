---
title: TCP Etkinleştirme
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: c10cc1edfb06d55fc8a59a32bf905c95b20a19dc
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43533610"
---
# <a name="tcp-activation"></a><span data-ttu-id="fe44c-102">TCP Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="fe44c-102">TCP Activation</span></span>
<span data-ttu-id="fe44c-103">Bu örnek net.tcp protokolü üzerinden iletişim kuran bir hizmeti etkinleştirmek için Windows İşlem Etkinleştirme Hizmetleri (WAS) kullanan bir hizmet barındırma gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe44c-103">This sample demonstrates hosting a service that uses Windows Process Activation Services (WAS) to activate a service that communicates over the net.tcp protocol.</span></span> <span data-ttu-id="fe44c-104">Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="fe44c-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe44c-105">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="fe44c-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fe44c-106">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="fe44c-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="fe44c-107">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fe44c-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fe44c-108">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="fe44c-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fe44c-109">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="fe44c-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`  
  
 <span data-ttu-id="fe44c-110">Örnek bir istemci konsol program (.exe) ve WAS tarafından etkinleştirilen bir çalışan işleminin barındırılan hizmet kitaplığı (.dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="fe44c-110">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by WAS.</span></span> <span data-ttu-id="fe44c-111">İstemci etkinliği konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="fe44c-111">Client activity is visible in the console window.</span></span>  
  
 <span data-ttu-id="fe44c-112">Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="fe44c-112">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="fe44c-113">Anlaşma tarafından tanımlanan `ICalculator` matematik işlemlerinden sunan arabirimi (ekleme, çıkarma, çarpma ve bölme), aşağıdaki örnek kodda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="fe44c-113">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code:</span></span>  
  
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
  
 <span data-ttu-id="fe44c-114">Hizmet uygulaması, hesaplar ve uygun sonucunu döndürür:</span><span class="sxs-lookup"><span data-stu-id="fe44c-114">The service implementation calculates and returns the appropriate result:</span></span>  
  
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
  
 <span data-ttu-id="fe44c-115">Örnek bir TCP bağlantı noktası paylaşımı etkin ve devre dışı güvenlikle bağlama net.tcp çeşidini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe44c-115">The sample uses a variant of the net.tcp binding with TCP port sharing enabled and security turned off.</span></span> <span data-ttu-id="fe44c-116">Güvenli bir TCP bağlaması kullanmak istiyorsanız, sunucunun güvenlik modu istediğiniz ayara değiştirin ve Svcutil.exe bir güncelleştirme istemci yapılandırma dosyası oluşturmak için istemcide yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fe44c-116">If you want to use a secured TCP binding, change the server's security mode to the desired setting and re-run Svcutil.exe on the client to generate an update client configuration file.</span></span>  
  
 <span data-ttu-id="fe44c-117">Aşağıdaki örnek, hizmet yapılandırmasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="fe44c-117">The following sample shows the configuration for the service:</span></span>  
  
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
  
 <span data-ttu-id="fe44c-118">Aşağıdaki örnek kodda gösterildiği gibi istemcinin uç nokta yapılandırılır:</span><span class="sxs-lookup"><span data-stu-id="fe44c-118">The client's endpoint is configured as shown in the following sample code:</span></span>  
  
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
  
 <span data-ttu-id="fe44c-119">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fe44c-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="fe44c-120">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fe44c-120">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fe44c-121">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="fe44c-121">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="fe44c-122">Emin [!INCLUDE[iisver](../../../../includes/iisver-md.md)] yüklenir.</span><span class="sxs-lookup"><span data-stu-id="fe44c-122">Ensure that [!INCLUDE[iisver](../../../../includes/iisver-md.md)] is installed.</span></span> [!INCLUDE[iisver](../../../../includes/iisver-md.md)]<span data-ttu-id="fe44c-123"> WAS etkinleştirme için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fe44c-123"> is required for WAS activation.</span></span>  
  
2.  <span data-ttu-id="fe44c-124">Gerçekleştirilen mutlaka [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fe44c-124">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
     <span data-ttu-id="fe44c-125">Ayrıca, WCF HTTP olmayan etkinleştirme bileşenlerini yüklemelisiniz:</span><span class="sxs-lookup"><span data-stu-id="fe44c-125">In addition, you must install the WCF non-HTTP activation components:</span></span>  
  
    1.  <span data-ttu-id="fe44c-126">Gelen **Başlat** menüsünde seçin **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="fe44c-126">From the **Start** menu, choose **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="fe44c-127">Seçin **programlar ve Özellikler**.</span><span class="sxs-lookup"><span data-stu-id="fe44c-127">Select **Programs and Features**.</span></span>  
  
    3.  <span data-ttu-id="fe44c-128">Tıklayın **Aç veya kapat Windows bileşenleri**.</span><span class="sxs-lookup"><span data-stu-id="fe44c-128">Click **Turn Windows Components on or Off**.</span></span>  
  
    4.  <span data-ttu-id="fe44c-129">Genişletin **Microsoft .NET Framework 3.0** düğüm ve onay **Windows Communication Foundation HTTP olmayan etkinleştirme** özelliği.</span><span class="sxs-lookup"><span data-stu-id="fe44c-129">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>  
  
3.  <span data-ttu-id="fe44c-130">WAS TCP etkinleştirilmesini destekleyecek şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="fe44c-130">Configure WAS to support TCP activation.</span></span>  
  
     <span data-ttu-id="fe44c-131">Bir kolaylık olarak örnek dizinde yer AddNetTcpSiteBinding.cmd adlı bir toplu iş dosyasında aşağıdaki iki adımı uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fe44c-131">As a convenience, the following two steps are implemented in a batch file called AddNetTcpSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="fe44c-132">NET.TCP etkinleştirmeyi desteklemek için varsayılan Web sitesi ilk net.tcp bağlantı noktasına bağlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe44c-132">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="fe44c-133">Bu yapılabilir, Internet Information Services 7.0 (IIS) Yönetimi araç takımıyla yüklenmeyen Appcmd.exe kullanarak.</span><span class="sxs-lookup"><span data-stu-id="fe44c-133">This can be done using Appcmd.exe, which is installed with the Internet Information Services 7.0 (IIS) management toolset.</span></span> <span data-ttu-id="fe44c-134">Bir düzey yönetici komut isteminden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="fe44c-134">From an administrator-level command prompt, run the following command:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!TIP]
        >  <span data-ttu-id="fe44c-135">Tek metin satırı komutudur.</span><span class="sxs-lookup"><span data-stu-id="fe44c-135">This command is a single line of text.</span></span> <span data-ttu-id="fe44c-136">Bu komut, varsayılan Web sitesine 808 tüm ana bilgisayar adına sahip numaralı TCP bağlantı noktasını dinleyen bir net.tcp site bağlaması ekler.</span><span class="sxs-lookup"><span data-stu-id="fe44c-136">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any hostname.</span></span>  
  
    2.  <span data-ttu-id="fe44c-137">Bir sitedeki tüm uygulamaları genel net.tcp bağlama paylaşsa da her uygulama net.tcp destek ayrı ayrı etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe44c-137">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="fe44c-138">NET.TCP /servicemodelsamples uygulamanın etkinleştirmek için bir yönetici düzeyinde komut isteminden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="fe44c-138">To enable net.tcp for the /servicemodelsamples application, run the following command from an administrator-level command prompt:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="fe44c-139">Tek metin satırı komutudur.</span><span class="sxs-lookup"><span data-stu-id="fe44c-139">This command is a single line of text.</span></span> <span data-ttu-id="fe44c-140">Bu komut, her ikisi de kullanılarak erişilecektir /servicemodelsamples uygulama etkinleştirir http://localhost/servicemodelsamples ve net.tcp://localhost/servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="fe44c-140">This command enables the /servicemodelsamples application to be accessed using both http://localhost/servicemodelsamples and net.tcp://localhost/servicemodelsamples.</span></span>  
  
4.  <span data-ttu-id="fe44c-141">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fe44c-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="fe44c-142">Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fe44c-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
     <span data-ttu-id="fe44c-143">Eklediğiniz net.tcp site bağlaması için bu örnek kaldırın.</span><span class="sxs-lookup"><span data-stu-id="fe44c-143">Remove the net.tcp site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="fe44c-144">Bir kolaylık olarak örnek dizinde yer RemoveNetTcpSiteBinding.cmd adlı bir toplu iş dosyasında aşağıdaki iki adımı uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fe44c-144">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="fe44c-145">NET.TCP, bir yönetici düzeyinde komut isteminden aşağıdaki komutu çalıştırarak etkin protokoller listesinden kaldırın:</span><span class="sxs-lookup"><span data-stu-id="fe44c-145">Remove net.tcp from the list of enabled protocols by running the following command from an administrator-level command prompt:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="fe44c-146">Bu komut, tek satırlık bir metin girilmelidir.</span><span class="sxs-lookup"><span data-stu-id="fe44c-146">This command must be entered as a single line of text.</span></span>  
  
    2.  <span data-ttu-id="fe44c-147">Net.tcp site bağlaması, bir yönetici düzeyinde komut isteminden aşağıdaki komutu çalıştırarak kaldırın:</span><span class="sxs-lookup"><span data-stu-id="fe44c-147">Remove the net.tcp site binding by running the following command from an administrator-level command prompt:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="fe44c-148">Bu komut, tek satırlık bir metin yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe44c-148">This command must be typed in as a single line of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe44c-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe44c-149">See Also</span></span>  
 [<span data-ttu-id="fe44c-150">AppFabric barındırma ve Kalıcılık örnekleri</span><span class="sxs-lookup"><span data-stu-id="fe44c-150">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
