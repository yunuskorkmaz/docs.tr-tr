---
title: WMI Sağlayıcısı
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 04fdbb7efcae6fdbb78f467352e6106ac5218799
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183197"
---
# <a name="wmi-provider"></a><span data-ttu-id="11e60-102">WMI Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="11e60-102">WMI Provider</span></span>
<span data-ttu-id="11e60-103">Bu örnek, WCF'de yerleşik olan Windows Yönetim Araçları (WMI) sağlayıcısını kullanarak çalışma zamanında Windows Communication Foundation (WCF) hizmetlerinden nasıl veri toplanacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="11e60-103">This sample demonstrates how to gather data from Windows Communication Foundation (WCF) services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into WCF.</span></span> <span data-ttu-id="11e60-104">Ayrıca, bu örnek, bir hizmete kullanıcı tanımlı WMI nesnesi nasıl ekleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="11e60-104">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="11e60-105">Örnek, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) için WMI sağlayıcısını etkinleştirir ve çalışma `ICalculator` zamanında hizmetten nasıl veri toplanacaklarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="11e60-105">The sample activates the WMI provider for the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="11e60-106">WMI, Microsoft'un Web Tabanlı Kurumsal Yönetim (WBEM) standardını uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="11e60-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="11e60-107">WMI SDK hakkında daha fazla bilgi için [Windows Management Instrumentation'a](/windows/desktop/WmiSdk/wmi-start-page)bakın.</span><span class="sxs-lookup"><span data-stu-id="11e60-107">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="11e60-108">WBEM, uygulamaların yönetim araçlarını dış yönetim araçlarına nasıl maruz bıraktamaları için bir endüstri standardıdır.</span><span class="sxs-lookup"><span data-stu-id="11e60-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="11e60-109">WCF, WBEM uyumlu bir arayüz aracılığıyla çalışma zamanında enstrümantasyonu ortaya çıkaran bir bileşen olan bir WMI sağlayıcısı uygular.</span><span class="sxs-lookup"><span data-stu-id="11e60-109">WCF implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="11e60-110">Yönetim araçları, çalışma zamanında arabirim üzerinden hizmetlere bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="11e60-110">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="11e60-111">WCF, adresler, bağlamalar, davranışlar ve dinleyiciler gibi hizmetlerin özniteliklerini ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="11e60-111">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="11e60-112">Yerleşik WMI sağlayıcısı uygulamanın yapılandırma dosyasında etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="11e60-112">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="11e60-113">Bu, aşağıdaki `wmiProviderEnabled` örnek yapılandırmada gösterildiği gibi, [ \<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) bölümündeki [ \<>tanılama](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) özelliği ile yapılır:</span><span class="sxs-lookup"><span data-stu-id="11e60-113">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="11e60-114">Bu yapılandırma girişi bir WMI arabirimini ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="11e60-114">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="11e60-115">Yönetim uygulamaları artık bu arayüz üzerinden bağlanabilir ve uygulamanın yönetim enstrümantasyonuna erişebilir.</span><span class="sxs-lookup"><span data-stu-id="11e60-115">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="11e60-116">Özel WMI Nesnesi</span><span class="sxs-lookup"><span data-stu-id="11e60-116">Custom WMI Object</span></span>  
 <span data-ttu-id="11e60-117">Bir hizmete WMI nesneleri eklemek, yerleşik WMI sağlayıcı bilgileriyle birlikte kullanıcı tanımlı bilgileri ortaya çıkarmasını mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="11e60-117">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="11e60-118">Bu, Installutil.exe uygulamasını kullanarak hizmetin şemasını WMI'ye yayımlayarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="11e60-118">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="11e60-119">Bunu gerçekleştirmek için talimatlar, daha fazla ayrıntı ile birlikte konunun sonunda kurulum talimatları bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="11e60-119">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="11e60-120">WMI Bilgilerine Erişim</span><span class="sxs-lookup"><span data-stu-id="11e60-120">Accessing WMI Information</span></span>  

<span data-ttu-id="11e60-121">WMI verilerine birçok farklı şekilde erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="11e60-121">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="11e60-122">Microsoft komut dosyaları, Visual Basic uygulamaları, C++ uygulamaları ve .NET Framework için WMI API'leri sağlar.</span><span class="sxs-lookup"><span data-stu-id="11e60-122">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="11e60-123">Daha fazla bilgi için [WMI kullanma'ya](/windows/desktop/wmisdk/using-wmi)bakın.</span><span class="sxs-lookup"><span data-stu-id="11e60-123">For more information, see [Using WMI](/windows/desktop/wmisdk/using-wmi).</span></span>
  
 <span data-ttu-id="11e60-124">Bu örnekte iki Java komut dosyası kullanılır: biri bilgisayarda çalışan hizmetleri bazı özellikleriyle birlikte, ikincisi de kullanıcı tarafından tanımlanan WMI verilerini görüntülemek için sıralamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="11e60-124">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="11e60-125">Komut dosyası WMI sağlayıcısına bir bağlantı açar, verileri parses ve toplanan verileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="11e60-125">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="11e60-126">Bir WCF hizmetinin çalışan bir örneğini oluşturmak için örneği başlatın.</span><span class="sxs-lookup"><span data-stu-id="11e60-126">Start the sample to create a running instance of a WCF service.</span></span> <span data-ttu-id="11e60-127">Hizmet çalışırken, komut isteminde aşağıdaki komutu kullanarak her Java komut dosyasını çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="11e60-127">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```console  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="11e60-128">Komut dosyası, hizmette bulunan enstrümantasyona erişir ve aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="11e60-128">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
```console  
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
  
 <span data-ttu-id="11e60-129">Ardından, kullanıcı tanımlı WMI verilerini görüntülemek için ikinci Java Komut Dosyasını çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="11e60-129">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```console  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="11e60-130">Komut dosyası, hizmetlerde bulunan kullanıcı tanımlı enstrümantasyona erişir ve aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="11e60-130">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```console
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="11e60-131">Çıktı, bilgisayarda çalışan tek bir hizmet olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="11e60-131">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="11e60-132">Hizmet, sözleşmeyi `ICalculator` uygulayan bir bitiş noktasını ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="11e60-132">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="11e60-133">Bitiş noktası tarafından uygulanan davranış ve bağlama ayarları, ileti yığınının tek tek öğelerinin toplamı olarak listelenir.</span><span class="sxs-lookup"><span data-stu-id="11e60-133">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="11e60-134">WMI, WCF altyapısının yönetim enstrümantasyonunu ortaya çıkarmakla sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="11e60-134">WMI is not limited to exposing the management instrumentation of the WCF infrastructure.</span></span> <span data-ttu-id="11e60-135">Uygulama, aynı mekanizma aracılığıyla kendi etki alanına özgü veri öğelerini ortaya çıkarabilir.</span><span class="sxs-lookup"><span data-stu-id="11e60-135">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="11e60-136">WMI, bir Web hizmetinin denetimi ve denetimi için birleşik bir mekanizmadır.</span><span class="sxs-lookup"><span data-stu-id="11e60-136">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="11e60-137">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="11e60-137">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="11e60-138">[Windows Communication Foundation Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi sağlayın.</span><span class="sxs-lookup"><span data-stu-id="11e60-138">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="11e60-139">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="11e60-139">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="11e60-140">InstallUtil.exe için varsayılan konumlar barındırma dizinindeki service.dll dosyasında InstallUtil.exe 'yi çalıştırarak hizmetleri schema'yı WMI'ye yayımlayın (InstallUtil.exe için varsayılan konumlar "%WINDIR%\Microsoft.NET\Framework\v4.0.30319"dur).</span><span class="sxs-lookup"><span data-stu-id="11e60-140">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="11e60-141">Bu adımın yalnızca service.dll dosyasında değişiklikler yapıldığında yürütülmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="11e60-141">This step only needs to be executed when changes have been made to the service.dll file.</span></span>
  
4. <span data-ttu-id="11e60-142">Örneği tek veya bilgisayar lar arası yapılandırmada çalıştırmak [için, Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="11e60-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="11e60-143">wcf'yi ASP.NET yükledikten sonra yüklediyseniz,%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x ASPNET hesabına WMI nesnelerini yayımlama izni vermek için.</span><span class="sxs-lookup"><span data-stu-id="11e60-143">If you installed WCF after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5. <span data-ttu-id="11e60-144">WMI aracılığıyla yüzeye çıkan örnekteki verileri komutları kullanarak görüntüleyin: `cscript EnumerateServices.js` veya `cscript EnumerateCustomObjects.js`.</span><span class="sxs-lookup"><span data-stu-id="11e60-144">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="11e60-145">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="11e60-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="11e60-146">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="11e60-146">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="11e60-147">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="11e60-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="11e60-148">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="11e60-148">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="11e60-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11e60-149">See also</span></span>

- <span data-ttu-id="11e60-150">[AppFabric İzleme Örnekleri](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="11e60-150">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
