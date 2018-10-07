---
title: WMI Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 7947d9a1bedfe7a2a550a7b4d52b3cf5a8f40126
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48839404"
---
# <a name="wmi-provider"></a><span data-ttu-id="2ea71-102">WMI Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="2ea71-102">WMI Provider</span></span>
<span data-ttu-id="2ea71-103">Bu örnek, WCF yerleşik Windows Yönetim Araçları (WMI) sağlayıcısını kullanarak çalışma zamanında Windows Communication Foundation (WCF) hizmetlerden veri toplamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ea71-103">This sample demonstrates how to gather data from Windows Communication Foundation (WCF) services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into WCF.</span></span> <span data-ttu-id="2ea71-104">Ayrıca, bu örnek, bir kullanıcı tanımlı WMI nesnesi için bir hizmet eklemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ea71-104">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="2ea71-105">Örnek için WMI sağlayıcısını etkinleştirir [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) ve veri toplamaya gösterilmiştir `ICalculator` zamanında hizmet.</span><span class="sxs-lookup"><span data-stu-id="2ea71-105">The sample activates the WMI provider for the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="2ea71-106">WMI Web tabanlı kuruluş yönetimi (WBEM) standart Microsoft uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="2ea71-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="2ea71-107">WMI SDK'sı hakkında daha fazla bilgi için bkz. [Windows Yönetim Araçları'nı](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="2ea71-107">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="2ea71-108">WBEM, uygulamaları dış Yönetim Araçları için Yönetim Araçları'nı nasıl kullanıma için standart bir endüstri standardıdır.</span><span class="sxs-lookup"><span data-stu-id="2ea71-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="2ea71-109">WCF izleme çalışma zamanında bir WBEM uyumlu arabirimi üzerinden kullanıma sunan bir bileşen bir WMI sağlayıcısını uygular.</span><span class="sxs-lookup"><span data-stu-id="2ea71-109">WCF implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="2ea71-110">Yönetim Araçları hizmetler zamanında arabirimi aracılığıyla bağlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ea71-110">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="2ea71-111">WCF hizmetleri adresler, bağlamalar, davranışları ve dinleyicileri gibi öznitelikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ea71-111">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="2ea71-112">Yerleşik WMI sağlayıcısı, uygulamanın yapılandırma dosyasında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2ea71-112">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="2ea71-113">Bu yoluyla yapılır `wmiProviderEnabled` özniteliği [ \<Tanılama >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) içinde [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) bölümünde, aşağıdaki örnekte gösterildiği gibi yapılandırma:</span><span class="sxs-lookup"><span data-stu-id="2ea71-113">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="2ea71-114">Bu yapılandırma girişi WMI arabirimini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="2ea71-114">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="2ea71-115">Yönetim uygulamaları artık bu arabirimi üzerinden bağlanabilir ve Yönetim Araçları uygulamanın erişim.</span><span class="sxs-lookup"><span data-stu-id="2ea71-115">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="2ea71-116">Özel WMI nesnesi</span><span class="sxs-lookup"><span data-stu-id="2ea71-116">Custom WMI Object</span></span>  
 <span data-ttu-id="2ea71-117">WMI nesnelerini bir hizmete ekleme yerleşik WMI sağlayıcısı bilgileriyle birlikte kullanıcı tarafından tanımlanan bilgileri açığa çıkarmak mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="2ea71-117">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="2ea71-118">Bu, Installutil.exe uygulamayı kullanarak hizmet şeması için WMI yayımlayarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2ea71-118">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="2ea71-119">Bunun yanı sıra daha fazla ayrıntı için yönergeler konunun sonunda kurulum yönergelerini bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="2ea71-119">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="2ea71-120">WMI bilgilerine erişme</span><span class="sxs-lookup"><span data-stu-id="2ea71-120">Accessing WMI Information</span></span>  
 <span data-ttu-id="2ea71-121">WMI verilerini birçok farklı yolu erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="2ea71-121">WMI data can be accessed many different ways.</span></span> <span data-ttu-id="2ea71-122">Microsoft, betikleri, Visual Basic uygulamaları, C++ uygulamaları için WMI API'lerini sağlar ve [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp).</span><span class="sxs-lookup"><span data-stu-id="2ea71-122">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp).</span></span>  
  
 <span data-ttu-id="2ea71-123">Bu örnek iki Java betiklerini kullanır: biri yanı sıra bazı kendi özellikleri ve kullanıcı tanımlı WMI verilerini görüntülemek için ikinci bir bilgisayar üzerinde çalışan hizmetleri listeleme.</span><span class="sxs-lookup"><span data-stu-id="2ea71-123">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="2ea71-124">Betik, WMI sağlayıcısı bir bağlantı açar, verilerini ayrıştırır ve toplanan verileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2ea71-124">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="2ea71-125">Bir WCF hizmeti çalışan bir örneğini oluşturmak için örneği başlatır.</span><span class="sxs-lookup"><span data-stu-id="2ea71-125">Start the sample to create a running instance of a WCF service.</span></span> <span data-ttu-id="2ea71-126">Hizmet çalışırken, komut isteminde aşağıdaki komutu kullanarak her Java betiği çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="2ea71-126">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="2ea71-127">Betik, hizmette bulunan izleme erişir ve aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2ea71-127">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
```  
Microsoft (R) Windows Script Host Version 5.6  
Copyright © Microsoft Corporation 1996-2001. All rights reserved.  
  
1 service(s) found.  
|-PID:           5776  
|-DistinguishedName:  CalculatorService@http://localhost/ServiceModelSamples/service.svc  
|-Endpoints:     1 endpoints  
  |-CalculatorService.ICalculator@http://localhost/ServiceModelSamples/service.svc  
    |-Address:                        http://localhost/ServiceModelSamples/service.svc  
    |-CounterInstanceName:  
    |-AddressHeaders:                 0  
    |-ContractType:                   Contract.Name='ICalculator'  
    |-BindingElements:                4 bindings  
      |-BindingElements[0]  
        |-Type:                       TransactionFlowBindingElement  
      |-BindingElements[1]  
        |-Type:                       SymmetricSecurityBindingElement  
      |-BindingElements[2]  
        |-Type:                       TextMessageEncodingBindingElement  
        |-MaxReadPoolSize:            64  
        |-MaxWritePoolSize:           16  
      |-BindingElements[3]  
        |-Type:                       HttpTransportBindingElement  
        |-ManualAddressing:           false  
        |-MaxBufferSize:              65536  
        |-AllowCookies:               false  
        |-AuthenticationScheme:       Anonymous  
        |-BypassProxyOnLocal:         false  
        |-HostNameComparisonMode:     StrongWildcard  
        |-ProxyAddress:               null  
        |-ProxyAuthenticationScheme:  Anonymous  
        |-Realm:  
        |-TransferMode:               Buffered  
        |-UseDefaultWebProxy:         true  
|-Behaviors:     5 behaviors  
      |-Behavior[0]  
      |-Type:                       ServiceBehaviorAttribute  
        |-AddressFilterMode:               Exact  
        |-AutomaticSessionShutdown:        true  
        |-ConcurrencyMode:                 Single  
        |-IncludeExceptionDetailInFaults:  false  
        |-InstanceContextMode:             PerSession  
        |-TransactionIsolationLevel:       Unspecified  
        |-TransactionTimeout:              null  
        |-ValidateMustUnderstand:          true  
      |-Behavior[1]  
      |-Type:                       AspNetCompatibilityRequirementsAttribute  
      |-Behavior[2]  
      |-Type:                       ServiceDebugBehavior  
      |-Behavior[3]  
      |-Type:                       ServiceAuthorizationBehavior  
      |-Behavior[4]  
      |-Type:                       Behavior  
```  
  
 <span data-ttu-id="2ea71-128">Ardından, kullanıcı tanımlı WMI verilerini görüntülemek için ikinci Java betiği çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="2ea71-128">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="2ea71-129">Betik ve hizmetlerde yer alan kullanıcı tanımlı araçları erişir ve aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2ea71-129">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="2ea71-130">Çıktı bilgisayar üzerinde çalışan tek bir hizmet olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ea71-130">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="2ea71-131">Hizmet uygulayan bir uç noktasını kullanıma sunar. `ICalculator` sözleşme.</span><span class="sxs-lookup"><span data-stu-id="2ea71-131">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="2ea71-132">Bitiş noktası tarafından uygulanan ayarları davranış ve bağlama Mesajlaşma yığını tek tek öğelerine toplamı olarak listelenir.</span><span class="sxs-lookup"><span data-stu-id="2ea71-132">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="2ea71-133">WMI WCF altyapısının Yönetim Araçları'nı kullanıma sunmak için sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="2ea71-133">WMI is not limited to exposing the management instrumentation of the WCF infrastructure.</span></span> <span data-ttu-id="2ea71-134">Uygulama kendi etki alanına özgü veri öğelerini aynı bir mekanizma aracılığıyla kullanıma sunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ea71-134">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="2ea71-135">WMI, inceleme ve Denetim Web hizmetinin birleşik bir mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="2ea71-135">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2ea71-136">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="2ea71-136">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2ea71-137">Gerçekleştirdiğiniz olun [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2ea71-137">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="2ea71-138">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2ea71-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="2ea71-139">WMI hizmetleri şeması (InstallUtil.exe varsayılan konumları, "% WINDIR%\Microsoft.NET\Framework\v4.0.30319" dır) InstallUtil.exe çalıştırarak barındırma dizininde service.dll dosyasını yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="2ea71-139">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="2ea71-140">Bu adım yalnızca service.dll dosyasına değişiklikler yapıldığında yürütülmesi gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="2ea71-140">This step only needs to be executed when changes have been made to the service.dll file.</span></span>
  
4.  <span data-ttu-id="2ea71-141">Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2ea71-141">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ea71-142">WCF ASP.NET'ı yükledikten sonra yüklerseniz, "%WINDIR%\ çalıştırmanız gerekebilir Microsoft.Net\Framework\v3.0\Windows iletişimi Foundation\servicemodelreg.exe "- r - WMI Nesne yayımlamak için ASP.NET hesabı izin vermek için x.</span><span class="sxs-lookup"><span data-stu-id="2ea71-142">If you installed WCF after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5.  <span data-ttu-id="2ea71-143">WMI aracılığıyla komutları kullanarak ortaya örnekten verileri görüntüleme: `cscript EnumerateServices.js` veya `cscript EnumerateCustomObjects.js`.</span><span class="sxs-lookup"><span data-stu-id="2ea71-143">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2ea71-144">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="2ea71-144">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2ea71-145">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="2ea71-145">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2ea71-146">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="2ea71-146">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2ea71-147">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="2ea71-147">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="2ea71-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2ea71-148">See Also</span></span>  
 [<span data-ttu-id="2ea71-149">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="2ea71-149">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
