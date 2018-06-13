---
title: Yapılandırma Temelli Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 21bb762e-c43e-4b0c-887b-5e434d665838
ms.openlocfilehash: 3ac4edd2a51e4ed8a5c0b7e73d7d1afa31334c33
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809920"
---
# <a name="configuration-based-activation"></a><span data-ttu-id="1e706-102">Yapılandırma Temelli Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1e706-102">Configuration-Based Activation</span></span>
<span data-ttu-id="1e706-103">Bu örnek, bir .svc dosya gerek kalmadan Windows Communication Foundation (WCF) hizmetlerini etkinleştirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1e706-103">This sample demonstrates how to activate Windows Communication Foundation (WCF) services without requiring a .svc file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1e706-104">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="1e706-104">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1e706-105">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1e706-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1e706-106">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="1e706-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1e706-107">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1e706-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\ConfigBasedActivation`  
  
## <a name="sample-details"></a><span data-ttu-id="1e706-108">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="1e706-108">Sample Details</span></span>  
 <span data-ttu-id="1e706-109">Bu örnekte, istemci WCF test istemcisi ve IIS'de barındırılan hizmetindeki.</span><span class="sxs-lookup"><span data-stu-id="1e706-109">In this sample, the client is the WCF test client and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e706-110">Kurulum ve yapılandırma yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="1e706-110">The setup and build instructions for this sample are located at the end of this topic.</span></span>  
  
### <a name="activation-of-services-without-requiring-a-svc-file"></a><span data-ttu-id="1e706-111">.Svc dosya gerektirmeden hizmetlerin etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1e706-111">Activation of services without requiring a .svc file</span></span>  
 <span data-ttu-id="1e706-112">İçinde [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], .svc dosyasındaki bir hizmeti etkinleştirmek için gerekli.</span><span class="sxs-lookup"><span data-stu-id="1e706-112">In [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], a .svc file was required for activating a service.</span></span> <span data-ttu-id="1e706-113">Ek dosya dağıtılması ve uygulamayı ile birlikte saklanır için gerekli olduğu için bu ek yönetim yükünü neden oldu.</span><span class="sxs-lookup"><span data-stu-id="1e706-113">This caused additional management overhead, because an additional file was required to be deployed and maintained along with the application.</span></span> <span data-ttu-id="1e706-114">Sürümü ile [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], etkinleştirme bileşenleri uygulama yapılandırma dosyası kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="1e706-114">With the release of [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], the activation components can be configured using the application configuration file.</span></span>  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]<span data-ttu-id="1e706-115"> Yeni bir yapılandırma öğesi sunar (<xref:System.ServiceModel.Configuration.ServiceActivationElement>), <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> uygulama yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="1e706-115"> introduces a new configuration element (<xref:System.ServiceModel.Configuration.ServiceActivationElement>), in the <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> of the application configuration file.</span></span> <span data-ttu-id="1e706-116"><xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> Koleksiyonu aşağıdaki kod örneğinde gösterildiği gibi etkinleştirmek için hizmetler koleksiyonu kabul eder.</span><span class="sxs-lookup"><span data-stu-id="1e706-116">The <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> collection accepts a collection of services to activate, as shown in the following code example.</span></span>  
  
```xml  
<serviceActivations>  
   <add relativeAddress="Calculator.svc" service="Microsoft.ServiceModel.Samples.CalculatorService" />  
  
<serviceActivations>  
```  
  
 <span data-ttu-id="1e706-117">Yapmak için gözlem yapılandırma .svc dosyalarını yapılandırma için çok benzer görünüyor.</span><span class="sxs-lookup"><span data-stu-id="1e706-117">The observation to make is the configuration looks very similar to the configuration of .svc files.</span></span> <span data-ttu-id="1e706-118">Eklenen ek bir özniteliktir `relativeAddress` hizmetinin adresini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e706-118">An additional attribute that is introduced is the `relativeAddress` that provides the address of the service.</span></span> <span data-ttu-id="1e706-119">Göreli Ayrıca hizmet için sanal yolu adresidir.</span><span class="sxs-lookup"><span data-stu-id="1e706-119">The relative address is also the virtual path for the service.</span></span> <span data-ttu-id="1e706-120">Dosyadan Web.config dosyası ana bilgisayarı alır `virtualPath` konumu, ana bilgisayar, yoksa kendi üst klasörü özyinelemeli olarak arar.</span><span class="sxs-lookup"><span data-stu-id="1e706-120">The host retrieves the Web.config file of the file from the `virtualPath` location, if present; otherwise the host searches its parent folder recursively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e706-121">Bu örnek, IIS'de işleve barındırma gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1e706-121">This sample requires hosting in IIS to function.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="1e706-122">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="1e706-122">To use this sample</span></span>  
  
1.  <span data-ttu-id="1e706-123">Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], Service.csproj dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="1e706-123">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the Service.csproj file.</span></span>  
  
2.  <span data-ttu-id="1e706-124">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1e706-124">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="1e706-125">Hizmet WCFTestClient.exe çalıştırarak sınayın.</span><span class="sxs-lookup"><span data-stu-id="1e706-125">Test the service by running WCFTestClient.exe.</span></span>  
  
4.  <span data-ttu-id="1e706-126">Kullanarak [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="1e706-126">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], navigate to the %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE folder.</span></span>  
  
5.  <span data-ttu-id="1e706-127">WcfTestClient.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1e706-127">Run WcfTestClient.exe.</span></span>  
  
6.  <span data-ttu-id="1e706-128">Hizmetinin MEX adresi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1e706-128">Set the MEX address of the service.</span></span>  
  
7.  <span data-ttu-id="1e706-129">Hizmet adresini ayarlamak için CTRL + SHIFT + A basın.</span><span class="sxs-lookup"><span data-stu-id="1e706-129">Press CTRL+SHIFT+A to set the service address.</span></span>  
  
8.  <span data-ttu-id="1e706-130">Adres kümesine http://localhost/ServiceModelSamples/Calculator.svc.</span><span class="sxs-lookup"><span data-stu-id="1e706-130">Set the address to http://localhost/ServiceModelSamples/Calculator.svc.</span></span>  
  
9. <span data-ttu-id="1e706-131">Gerçekleştirmek `Add` işlemi.</span><span class="sxs-lookup"><span data-stu-id="1e706-131">Perform the `Add` operation.</span></span> <span data-ttu-id="1e706-132">Değeri ayarlayın `n1` 10 ve ayarlanmış değeri parametresi `n2` 15 parametresi.</span><span class="sxs-lookup"><span data-stu-id="1e706-132">Set value on the `n1` parameter to 10 and set value on the `n2` parameter to 15.</span></span>  
  
10. <span data-ttu-id="1e706-133">Tuşuna **çağırma**.</span><span class="sxs-lookup"><span data-stu-id="1e706-133">Press **Invoke**.</span></span>  
  
     <span data-ttu-id="1e706-134">Beklenen sonucu 25'tir.</span><span class="sxs-lookup"><span data-stu-id="1e706-134">The expected result is 25.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1e706-135">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="1e706-135">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1e706-136">Gerçekleştirilen mutlaka [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1e706-136">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="1e706-137">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1e706-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="1e706-138">IIS ServiceModelSamples uygulamada ayarlamak için Setup.bat çalıştırmak sonra çözüm oluşturulmadı.</span><span class="sxs-lookup"><span data-stu-id="1e706-138">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS.</span></span> <span data-ttu-id="1e706-139">ServiceModelSamples dizini artık bir IIS uygulaması olarak görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="1e706-139">The ServiceModelSamples directory should now appear as an IIS Application.</span></span>  
  
4.  <span data-ttu-id="1e706-140">Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1e706-140">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e706-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1e706-141">See Also</span></span>  
 [<span data-ttu-id="1e706-142">AppFabric barındırma ve kalıcılığı örnekleri</span><span class="sxs-lookup"><span data-stu-id="1e706-142">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
