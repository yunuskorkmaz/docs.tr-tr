---
title: Yapılandırma Temelli Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 21bb762e-c43e-4b0c-887b-5e434d665838
ms.openlocfilehash: e016dffdaf93b222c1fd2380bfa175256b009068
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43742322"
---
# <a name="configuration-based-activation"></a><span data-ttu-id="cca4b-102">Yapılandırma Temelli Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="cca4b-102">Configuration-Based Activation</span></span>
<span data-ttu-id="cca4b-103">Bu örnek, bir .svc dosya gerek kalmadan Windows Communication Foundation (WCF) hizmetlerini etkinleştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="cca4b-103">This sample demonstrates how to activate Windows Communication Foundation (WCF) services without requiring a .svc file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cca4b-104">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="cca4b-104">The samples may already be installed on your computer.</span></span> <span data-ttu-id="cca4b-105">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="cca4b-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cca4b-106">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="cca4b-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cca4b-107">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="cca4b-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\ConfigBasedActivation`  
  
## <a name="sample-details"></a><span data-ttu-id="cca4b-108">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="cca4b-108">Sample Details</span></span>  
 <span data-ttu-id="cca4b-109">Bu örnekte istemci WCF test istemcisi ve IIS'de barındırılan hizmet.</span><span class="sxs-lookup"><span data-stu-id="cca4b-109">In this sample, the client is the WCF test client and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cca4b-110">Bu örnek için Kurulum ve yapılandırma yönergeleri Bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="cca4b-110">The setup and build instructions for this sample are located at the end of this topic.</span></span>  
  
### <a name="activation-of-services-without-requiring-a-svc-file"></a><span data-ttu-id="cca4b-111">.Svc dosya gerektirmeden hizmetlerin etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="cca4b-111">Activation of services without requiring a .svc file</span></span>  
 <span data-ttu-id="cca4b-112">İçinde [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], bir hizmeti etkinleştirme için gerekli .svc dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="cca4b-112">In [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], a .svc file was required for activating a service.</span></span> <span data-ttu-id="cca4b-113">Ek dosya dağıtılması ve uygulama ile birlikte korunur için gerekli olduğu için bu ek yönetim yükünü neden oldu.</span><span class="sxs-lookup"><span data-stu-id="cca4b-113">This caused additional management overhead, because an additional file was required to be deployed and maintained along with the application.</span></span> <span data-ttu-id="cca4b-114">Sürümüyle [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], etkinleştirme bileşenlerini, uygulama yapılandırma dosyası kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="cca4b-114">With the release of [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], the activation components can be configured using the application configuration file.</span></span>  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]<span data-ttu-id="cca4b-115"> Yeni bir yapılandırma öğesi sunar (<xref:System.ServiceModel.Configuration.ServiceActivationElement>), <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> uygulama yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="cca4b-115"> introduces a new configuration element (<xref:System.ServiceModel.Configuration.ServiceActivationElement>), in the <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> of the application configuration file.</span></span> <span data-ttu-id="cca4b-116"><xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> Koleksiyonu aşağıdaki kod örneğinde gösterildiği gibi hizmetleri etkinleştirmek için koleksiyonu kabul eder.</span><span class="sxs-lookup"><span data-stu-id="cca4b-116">The <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> collection accepts a collection of services to activate, as shown in the following code example.</span></span>  
  
```xml  
<serviceActivations>  
   <add relativeAddress="Calculator.svc" service="Microsoft.ServiceModel.Samples.CalculatorService" />  
  
<serviceActivations>  
```  
  
 <span data-ttu-id="cca4b-117">Yapılandırma .svc dosyalarını yapılandırmanız için çok benzer görünür hale getirmek için gözlem olur.</span><span class="sxs-lookup"><span data-stu-id="cca4b-117">The observation to make is the configuration looks very similar to the configuration of .svc files.</span></span> <span data-ttu-id="cca4b-118">Sunulan ek bir özniteliktir `relativeAddress` hizmetinin adresini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cca4b-118">An additional attribute that is introduced is the `relativeAddress` that provides the address of the service.</span></span> <span data-ttu-id="cca4b-119">Hizmetin göreli adresini de hizmet için sanal yolu var.</span><span class="sxs-lookup"><span data-stu-id="cca4b-119">The relative address is also the virtual path for the service.</span></span> <span data-ttu-id="cca4b-120">Dosyadan Web.config dosyasına ana bilgisayar alır `virtualPath` konumu, konak değişkenidir; Aksi takdirde, üst klasörü yinelemeli olarak arar.</span><span class="sxs-lookup"><span data-stu-id="cca4b-120">The host retrieves the Web.config file of the file from the `virtualPath` location, if present; otherwise the host searches its parent folder recursively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cca4b-121">Bu örnek, IIS'de işleve barındırma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="cca4b-121">This sample requires hosting in IIS to function.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="cca4b-122">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="cca4b-122">To use this sample</span></span>  
  
1.  <span data-ttu-id="cca4b-123">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], Service.csproj dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="cca4b-123">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the Service.csproj file.</span></span>  
  
2.  <span data-ttu-id="cca4b-124">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="cca4b-124">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="cca4b-125">Hizmet WCFTestClient.exe çalıştırarak test edin.</span><span class="sxs-lookup"><span data-stu-id="cca4b-125">Test the service by running WCFTestClient.exe.</span></span>  
  
4.  <span data-ttu-id="cca4b-126">Kullanarak [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="cca4b-126">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], navigate to the %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE folder.</span></span>  
  
5.  <span data-ttu-id="cca4b-127">WcfTestClient.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cca4b-127">Run WcfTestClient.exe.</span></span>  
  
6.  <span data-ttu-id="cca4b-128">MEX adresa hizmetinin ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cca4b-128">Set the MEX address of the service.</span></span>  
  
7.  <span data-ttu-id="cca4b-129">Hizmet adresinin ayarlamak için CTRL + SHIFT + A tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="cca4b-129">Press CTRL+SHIFT+A to set the service address.</span></span>  
  
8.  <span data-ttu-id="cca4b-130">Adresini http://localhost/ServiceModelSamples/Calculator.svc.</span><span class="sxs-lookup"><span data-stu-id="cca4b-130">Set the address to http://localhost/ServiceModelSamples/Calculator.svc.</span></span>  
  
9. <span data-ttu-id="cca4b-131">Gerçekleştirmek `Add` işlemi.</span><span class="sxs-lookup"><span data-stu-id="cca4b-131">Perform the `Add` operation.</span></span> <span data-ttu-id="cca4b-132">Değer kümesi üzerinde `n1` parametresini 10 ve ayarlanan değere `n2` 15 parametresi.</span><span class="sxs-lookup"><span data-stu-id="cca4b-132">Set value on the `n1` parameter to 10 and set value on the `n2` parameter to 15.</span></span>  
  
10. <span data-ttu-id="cca4b-133">Tuşuna **çağırma**.</span><span class="sxs-lookup"><span data-stu-id="cca4b-133">Press **Invoke**.</span></span>  
  
     <span data-ttu-id="cca4b-134">Beklenen sonuç 25'tir.</span><span class="sxs-lookup"><span data-stu-id="cca4b-134">The expected result is 25.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cca4b-135">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="cca4b-135">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="cca4b-136">Gerçekleştirilen mutlaka [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cca4b-136">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="cca4b-137">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cca4b-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="cca4b-138">IIS ServiceModelSamples uygulamada ayarlamak için Setup.bat çalıştırma sonra çözümü oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="cca4b-138">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS.</span></span> <span data-ttu-id="cca4b-139">ServiceModelSamples dizin artık IIS uygulaması olarak görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="cca4b-139">The ServiceModelSamples directory should now appear as an IIS Application.</span></span>  
  
4.  <span data-ttu-id="cca4b-140">Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cca4b-140">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cca4b-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cca4b-141">See Also</span></span>  
 [<span data-ttu-id="cca4b-142">AppFabric barındırma ve Kalıcılık örnekleri</span><span class="sxs-lookup"><span data-stu-id="cca4b-142">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
