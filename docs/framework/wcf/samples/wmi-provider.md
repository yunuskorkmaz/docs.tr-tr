---
title: WMI Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 89e2d370919519953e714cb0d0020587b3f53c9d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038511"
---
# <a name="wmi-provider"></a><span data-ttu-id="fc5ad-102">WMI Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="fc5ad-102">WMI Provider</span></span>
<span data-ttu-id="fc5ad-103">Bu örnek, WCF 'de yerleşik olarak bulunan Windows Yönetim Araçları (WMI) sağlayıcısını kullanarak çalışma zamanında Windows Communication Foundation (WCF) hizmetlerinden nasıl veri toplanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-103">This sample demonstrates how to gather data from Windows Communication Foundation (WCF) services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into WCF.</span></span> <span data-ttu-id="fc5ad-104">Ayrıca, bu örnek, bir hizmete Kullanıcı tanımlı WMI nesnesinin nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-104">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="fc5ad-105">Örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) için WMI sağlayıcısını etkinleştirir ve çalışma zamanında `ICalculator` hizmetten nasıl veri toplanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-105">The sample activates the WMI provider for the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="fc5ad-106">WMI, Microsoft 'un web tabanlı kuruluş yönetimi (WBEM) standardı uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="fc5ad-107">WMI SDK hakkında daha fazla bilgi için bkz. [Windows Yönetim Araçları](/windows/desktop/WmiSdk/wmi-start-page).</span><span class="sxs-lookup"><span data-stu-id="fc5ad-107">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="fc5ad-108">WBEM, uygulamaların yönetim araçları 'nı dış yönetim araçlarına nasıl sergilekullandığını gösteren bir sektör standardıdır.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="fc5ad-109">WCF, bir WBEM uyumlu arabirim aracılığıyla çalışma zamanında izleme sunan bir bileşen olan WMI sağlayıcısını uygular.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-109">WCF implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="fc5ad-110">Yönetim Araçları, çalışma zamanında arabirim aracılığıyla hizmetlere bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-110">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="fc5ad-111">WCF, adresler, bağlamalar, davranışlar ve dinleyicileri gibi hizmetlerin özniteliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-111">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="fc5ad-112">Yerleşik WMI sağlayıcısı, uygulamanın yapılandırma dosyasında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-112">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="fc5ad-113">Bu, aşağıdaki örnek yapılandırmada `wmiProviderEnabled` gösterildiği gibi [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) bölümündeki [ \<Tanılama >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) özniteliği aracılığıyla yapılır:</span><span class="sxs-lookup"><span data-stu-id="fc5ad-113">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="fc5ad-114">Bu yapılandırma girişi bir WMI arabirimi sunar.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-114">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="fc5ad-115">Yönetim uygulamaları artık bu arabirimden bağlanabilir ve uygulamanın yönetim araçlarına erişebilir.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-115">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="fc5ad-116">Özel WMI nesnesi</span><span class="sxs-lookup"><span data-stu-id="fc5ad-116">Custom WMI Object</span></span>  
 <span data-ttu-id="fc5ad-117">WMI nesnelerini bir hizmete eklemek, yerleşik WMI sağlayıcısı bilgileriyle birlikte Kullanıcı tanımlı bilgilerin açığa çıkarmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-117">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="fc5ad-118">Bu, InstallUtil. exe uygulaması kullanılarak hizmetin şeması WMI 'ye yayınlanarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-118">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="fc5ad-119">Bunu gerçekleştirmeye yönelik yönergeler, konunun sonundaki Kurulum yönergelerindeki daha ayrıntılı bilgi bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-119">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="fc5ad-120">WMI bilgilerine erişme</span><span class="sxs-lookup"><span data-stu-id="fc5ad-120">Accessing WMI Information</span></span>  
 <span data-ttu-id="fc5ad-121">WMI verilerine birçok farklı şekilde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-121">WMI data can be accessed many different ways.</span></span> <span data-ttu-id="fc5ad-122">Microsoft, betikler, Visual Basic uygulamalar, C++ uygulamalar ve .NET Framework Için WMI API 'leri sağlar (https://docs.microsoft.com/windows/desktop/wmisdk/using-wmi).</span><span class="sxs-lookup"><span data-stu-id="fc5ad-122">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework (https://docs.microsoft.com/windows/desktop/wmisdk/using-wmi).</span></span>  
  
 <span data-ttu-id="fc5ad-123">Bu örnek iki Java komut dosyası kullanır: biri bilgisayarda çalışan hizmetleri, bazı özellikleriyle birlikte, Kullanıcı tanımlı WMI verilerini görüntülemek için ikincisini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-123">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="fc5ad-124">Betik, WMI sağlayıcısına bir bağlantı açar, verileri ayrıştırır ve toplanan verileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-124">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="fc5ad-125">WCF hizmetinin çalışan bir örneğini oluşturmak için örneği başlatın.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-125">Start the sample to create a running instance of a WCF service.</span></span> <span data-ttu-id="fc5ad-126">Hizmet çalışırken, komut isteminde aşağıdaki komutu kullanarak her bir Java betiğini çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="fc5ad-126">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="fc5ad-127">Betik, hizmette bulunan izleme erişimine erişir ve aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fc5ad-127">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="fc5ad-128">Sonra, Kullanıcı tanımlı WMI verilerini göstermek için ikinci Java betiğini çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="fc5ad-128">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="fc5ad-129">Betik, hizmetlerde bulunan Kullanıcı tanımlı izleme erişimine erişir ve aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fc5ad-129">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="fc5ad-130">Çıktı, bilgisayarda çalışan tek bir hizmet olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-130">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="fc5ad-131">Hizmet, `ICalculator` sözleşmeyi uygulayan bir uç noktayı kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-131">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="fc5ad-132">Uç nokta tarafından uygulanan davranışın ve bağlamanın ayarları, mesajlaşma yığınındaki bireysel öğelerin toplamı olarak listelenir.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-132">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="fc5ad-133">WMI, WCF altyapısının yönetim araçlarını açığa çıkarmak için sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-133">WMI is not limited to exposing the management instrumentation of the WCF infrastructure.</span></span> <span data-ttu-id="fc5ad-134">Uygulama, kendi etki alanına özgü veri öğelerini aynı mekanizmaya göre kullanıma sunabilir.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-134">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="fc5ad-135">WMI, bir Web hizmeti denetimi ve denetimi için Birleşik bir mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-135">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fc5ad-136">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fc5ad-136">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="fc5ad-137">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-137">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fc5ad-138">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="fc5ad-139">InstallUtil. exe ' yi çalıştırarak (InstallUtil. exe için varsayılan konumlar "%WINDIR%\Microsoft.NET\Framework\v4.0.30319"), barındırma dizinindeki Service. dll dosyasında, hizmet şemasını WMI 'ya yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-139">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="fc5ad-140">Bu adımın yalnızca Service. dll dosyasında değişiklik yapıldığında yürütülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-140">This step only needs to be executed when changes have been made to the service.dll file.</span></span>
  
4. <span data-ttu-id="fc5ad-141">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-141">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="fc5ad-142">ASP.NET yükledikten sonra WCF 'yi yüklediyseniz, "% WINDIR% \ öğesini çalıştırmanız gerekebilir Microsoft. Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe "-r-x" ASPNET hesabına WMI nesneleri yayımlama izni vermek için.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-142">If you installed WCF after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5. <span data-ttu-id="fc5ad-143">Komutları kullanarak WMI üzerinden ortaya çıkacak örnekteki verileri görüntüleyin: `cscript EnumerateServices.js` veya. `cscript EnumerateCustomObjects.js`</span><span class="sxs-lookup"><span data-stu-id="fc5ad-143">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fc5ad-144">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-144">The samples may already be installed on your computer.</span></span> <span data-ttu-id="fc5ad-145">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-145">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="fc5ad-146">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-146">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fc5ad-147">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-147">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="fc5ad-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc5ad-148">See also</span></span>

- [<span data-ttu-id="fc5ad-149">AppFabric Izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="fc5ad-149">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
