---
title: "WMI Sağlayıcısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
caps.latest.revision: "35"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7a0a64516bea4204eb782013e718c2fa26c6024b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="wmi-provider"></a><span data-ttu-id="95c74-102">WMI Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="95c74-102">WMI Provider</span></span>
<span data-ttu-id="95c74-103">Bu örnek veri toplamaya gösterilmiştir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Hizmetleri içinde yerleşik Windows Yönetim Araçları (WMI) sağlayıcısını kullanarak çalışma zamanında [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="95c74-103">This sample demonstrates how to gather data from [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="95c74-104">Ayrıca, bu örnek bir kullanıcı tanımlı WMI nesnesi için bir hizmet eklemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="95c74-104">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="95c74-105">Örnek için WMI sağlayıcısını etkinleştirir [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) ve veri toplamaya gösterilmiştir `ICalculator` çalışma zamanında hizmet.</span><span class="sxs-lookup"><span data-stu-id="95c74-105">The sample activates the WMI provider for the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="95c74-106">WMI, Web tabanlı Kuruluş Yönetimi'nin (WBEM) standart Microsoft uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="95c74-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="95c74-107">WMI SDK'sı hakkında daha fazla bilgi için bkz: [Windows Yönetim Araçları](https://msdn.microsoft.com/library/aa394582.aspx).</span><span class="sxs-lookup"><span data-stu-id="95c74-107">For more information about the WMI SDK, see [Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx).</span></span> <span data-ttu-id="95c74-108">WBEM nasıl uygulamaları dış Yönetim Araçları için Yönetim Araçları'nı kullanıma sunmak için bir endüstri standardıdır.</span><span class="sxs-lookup"><span data-stu-id="95c74-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="95c74-109">WMI sağlayıcısı, izleme çalışma zamanında bir WBEM uyumlu arabirimi aracılığıyla kullanıma sunan bir bileşen uygular.</span><span class="sxs-lookup"><span data-stu-id="95c74-109"> implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="95c74-110">Yönetim Araçları, çalışma zamanında arabirimi üzerinden hizmetlere bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="95c74-110">Management tools can connect to the services through the interface at runtime.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="95c74-111">adresler, bağlamalar, davranışları ve dinleyicileri gibi hizmetleri özniteliklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="95c74-111"> exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="95c74-112">Yerleşik WMI sağlayıcısı, uygulama yapılandırma dosyasında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="95c74-112">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="95c74-113">Bu yoluyla yapılır `wmiProviderEnabled` özniteliği [ \<Tanılama >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) içinde [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) bölümünde, aşağıdaki örnekte gösterildiği gibi yapılandırma:</span><span class="sxs-lookup"><span data-stu-id="95c74-113">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="95c74-114">Bu yapılandırma girdisi WMI arabirimini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="95c74-114">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="95c74-115">Yönetim uygulamaları artık bu arabirimi üzerinden bağlanır ve Yönetim Araçları'nı uygulamanın erişir.</span><span class="sxs-lookup"><span data-stu-id="95c74-115">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="95c74-116">Özel WMI nesnesi</span><span class="sxs-lookup"><span data-stu-id="95c74-116">Custom WMI Object</span></span>  
 <span data-ttu-id="95c74-117">Bir hizmet için WMI Nesne ekleme, kullanıcı tarafından tanımlanan bilgileri yerleşik WMI sağlayıcısı bilgilerle birlikte ortaya mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="95c74-117">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="95c74-118">Bu, Installutil.exe uygulamasını kullanarak WMI hizmetinin şema yayımlama tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="95c74-118">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="95c74-119">Bunun yanı sıra daha fazla ayrıntı için yönergeler konunun sonunda kurulum yönergelerini bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="95c74-119">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="95c74-120">WMI bilgilerine erişme</span><span class="sxs-lookup"><span data-stu-id="95c74-120">Accessing WMI Information</span></span>  
 <span data-ttu-id="95c74-121">WMI veri birçok farklı yolu erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="95c74-121">WMI data can be accessed many different ways.</span></span> <span data-ttu-id="95c74-122">Microsoft, komut dosyaları için WMI API'lerini sağlar [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] uygulamalar, C++ uygulamaları ve [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp).</span><span class="sxs-lookup"><span data-stu-id="95c74-122">Microsoft provides WMI APIs for scripts, [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] applications, C++ applications, and the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp).</span></span>  
  
 <span data-ttu-id="95c74-123">Bu örnek iki Java betiklerini kullanır: biri özellikleri ve kullanıcı tanımlı WMI verilerini görüntülemek için ikinci bazılarını yanı sıra bilgisayar üzerinde çalışan hizmetleri numaralandırılacak.</span><span class="sxs-lookup"><span data-stu-id="95c74-123">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="95c74-124">Betik WMI sağlayıcısına bir bağlantı açar, verileri ayrıştırır ve toplanan verileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="95c74-124">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="95c74-125">Çalışan bir örneğini oluşturmak için örnek Başlat bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="95c74-125">Start the sample to create a running instance of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="95c74-126">Hizmet çalışırken, komut istemine aşağıdaki komutu kullanarak her Java betiği çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="95c74-126">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="95c74-127">Komut dosyası hizmetinde bulunan araçları erişir ve şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="95c74-127">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="95c74-128">Ardından, kullanıcı tanımlı WMI verilerini görüntülemek için ikinci Java betiği çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="95c74-128">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="95c74-129">Komut dosyası, kullanıcı tanımlı araçları hizmetlerinde bulunan erişir ve şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="95c74-129">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="95c74-130">Çıkış bilgisayar üzerinde çalışan tek bir hizmet olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="95c74-130">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="95c74-131">Hizmet uygulayan bir uç noktasını kullanıma sunar `ICalculator` sözleşme.</span><span class="sxs-lookup"><span data-stu-id="95c74-131">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="95c74-132">Bitiş noktası tarafından uygulanan davranış ayarları ve bağlama Mesajlaşma yığınının ayrı ayrı öğeler toplamı olarak listelenir.</span><span class="sxs-lookup"><span data-stu-id="95c74-132">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="95c74-133">WMI, Yönetim Araçları'nı gösterme için sınırlı değildir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] altyapı.</span><span class="sxs-lookup"><span data-stu-id="95c74-133">WMI is not limited to exposing the management instrumentation of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure.</span></span> <span data-ttu-id="95c74-134">Uygulamanın kendi etki alanına özgü veri öğeleri aynı mekanizma getirebilir.</span><span class="sxs-lookup"><span data-stu-id="95c74-134">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="95c74-135">WMI, denetleme ve bir Web hizmeti denetimi için birleşik bir mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="95c74-135">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="95c74-136">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="95c74-136">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="95c74-137">Gerçekleştirilen olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="95c74-137">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="95c74-138">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="95c74-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="95c74-139">WMI hizmetleri şeması (InstallUtil.exe için varsayılan konumları olan "% WINDIR%\Microsoft.NET\Framework\v4.0.30319") InstallUtil.exe çalıştırarak barındırma dizinindeki service.dll dosyasını yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="95c74-139">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="95c74-140">Bu adım yalnızca service.dll dosyaya yapılan değişiklikler olduğunda yürütülmesi gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="95c74-140">This step only needs to be executed when changes have been made to the service.dll file.</span></span> <span data-ttu-id="95c74-141">Sağlama yönetim bilgilerini düzenleme uygulamaları tarafından daha fazla bilgi için bkz: "Nasıl için: yayımlama düzeni için WMI için bir izleme eklenmiş uygulamayı" bölümündeki http://msdn2.microsoft.com/library/ms186147.aspx.</span><span class="sxs-lookup"><span data-stu-id="95c74-141">For more information, see Providing Management Information by Instrumenting Applications at: http://msdn2.microsoft.com/library/ms186147.aspx in the "How To: Publish the Scheme to WMI for an Instrumented Application" section.</span></span>  
  
4.  <span data-ttu-id="95c74-142">Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="95c74-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="95c74-143">Yüklediyseniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET yükledikten sonra "%WINDIR%\ çalıştırmanız gerekebilir Microsoft.Net\Framework\v3.0\Windows iletişim Foundation\servicemodelreg.exe "- r - WMI nesnelerini yayınlamak için ASPNET hesabı izin vermek için x.</span><span class="sxs-lookup"><span data-stu-id="95c74-143">If you installed [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5.  <span data-ttu-id="95c74-144">WMI aracılığıyla komutları kullanarak ortaya örnek verileri görüntüleyin: `cscript EnumerateServices.js` veya `cscript EnumerateCustomObjects.js`.</span><span class="sxs-lookup"><span data-stu-id="95c74-144">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="95c74-145">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="95c74-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="95c74-146">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="95c74-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="95c74-147">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="95c74-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="95c74-148">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="95c74-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="95c74-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="95c74-149">See Also</span></span>  
 [<span data-ttu-id="95c74-150">AppFabric izleme örnekleri</span><span class="sxs-lookup"><span data-stu-id="95c74-150">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
