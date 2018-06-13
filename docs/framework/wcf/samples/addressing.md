---
title: Adres Ayarlama
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: 94ac903afb27f1b87f0ca8bf05cb891d0d9ee34c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502244"
---
# <a name="addressing"></a><span data-ttu-id="88a1a-102">Adres Ayarlama</span><span class="sxs-lookup"><span data-stu-id="88a1a-102">Addressing</span></span>
<span data-ttu-id="88a1a-103">Adresleme örnek çeşitli yönleri ve uç nokta adresleri özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="88a1a-103">The Addressing sample demonstrates various aspects and features of endpoint addresses.</span></span> <span data-ttu-id="88a1a-104">Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="88a1a-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="88a1a-105">Bu örnekte hizmet kendiliğinden barındırılır.</span><span class="sxs-lookup"><span data-stu-id="88a1a-105">In this sample the service is self-hosted.</span></span> <span data-ttu-id="88a1a-106">Hem hizmet hem de istemci konsol uygulamalardır.</span><span class="sxs-lookup"><span data-stu-id="88a1a-106">Both the service and the client are console applications.</span></span> <span data-ttu-id="88a1a-107">Hizmet mutlak bitiş noktası adreslerini birleşimini kullanarak birden çok uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="88a1a-107">The service defines multiple endpoints using a combination of relative and absolute endpoint addresses.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88a1a-108">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="88a1a-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="88a1a-109">Hizmet yapılandırma dosyası, bir taban adresi ve dört uç noktaları belirtir.</span><span class="sxs-lookup"><span data-stu-id="88a1a-109">The service configuration file specifies a base address and four endpoints.</span></span> <span data-ttu-id="88a1a-110">Aşağıdaki örnek yapılandırmada gösterildiği gibi ana bilgisayar/service/baseAddresses altında Ekle öğesini kullanarak taban adresi belirtildi.</span><span class="sxs-lookup"><span data-stu-id="88a1a-110">The base address is specified using the add element, under service/host/baseAddresses as demonstrated in the following sample configuration.</span></span>  
  
```xml  
<service name="Microsoft.ServiceModel.Samples.CalculatorService"  
         behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />  
    </baseAddresses>  
  </host>  
</service>  
```  
  
 <span data-ttu-id="88a1a-111">Aşağıdaki örnek yapılandırmada gösterilen ilk uç nokta tanımı taban adresini ve URI oluşturma kuralları aşağıdaki göreli adresi bileşimini uç nokta adresi gelir bir göreli adresi belirtir.</span><span class="sxs-lookup"><span data-stu-id="88a1a-111">The first endpoint definition shown in the following sample configuration specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of URI composition.</span></span>  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="88a1a-112">Bu durumda, göreli adresi boştur (""), uç nokta adresi taban adresi ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="88a1a-112">In this case, the relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="88a1a-113">Gerçek bitiş adresi http://localhost:8000/servicemodelsamples/service.</span><span class="sxs-lookup"><span data-stu-id="88a1a-113">The actual endpoint address is http://localhost:8000/servicemodelsamples/service.</span></span>  
  
 <span data-ttu-id="88a1a-114">İkinci uç nokta tanımı, ayrıca aşağıdaki örnek yapılandırmada gösterildiği gibi bir göreli adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="88a1a-114">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span>  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="88a1a-115">Göreli adresi "test", taban adresi eklenir.</span><span class="sxs-lookup"><span data-stu-id="88a1a-115">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="88a1a-116">Gerçek bitiş adresi http://localhost:8000/servicemodelsamples/service/test.</span><span class="sxs-lookup"><span data-stu-id="88a1a-116">The actual endpoint address is http://localhost:8000/servicemodelsamples/service/test.</span></span>  
  
 <span data-ttu-id="88a1a-117">Aşağıdaki örnek yapılandırmada gösterildiği gibi üçüncü uç nokta tanımı mutlak bir adres belirtir.</span><span class="sxs-lookup"><span data-stu-id="88a1a-117">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="88a1a-118">Temel adres adresi herhangi bir rol oynar.</span><span class="sxs-lookup"><span data-stu-id="88a1a-118">The base address plays no role in the address.</span></span> <span data-ttu-id="88a1a-119">Gerçek bitiş adresi http://localhost:8001/hello/servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="88a1a-119">The actual endpoint address is http://localhost:8001/hello/servicemodelsamples.</span></span>  
  
 <span data-ttu-id="88a1a-120">Mutlak bir adres ve farklı bir aktarım dördüncü uç noktası adresi belirtir — TCP.</span><span class="sxs-lookup"><span data-stu-id="88a1a-120">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="88a1a-121">Temel adres adresi herhangi bir rol oynar.</span><span class="sxs-lookup"><span data-stu-id="88a1a-121">The base address plays no role in the address.</span></span> <span data-ttu-id="88a1a-122">Gerçek bitiş adresini net.tcp://localhost olan: servicemodelsamples/9000/hizmet.</span><span class="sxs-lookup"><span data-stu-id="88a1a-122">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<!-- The absolute address specified, different transport: -->  
<!-- use the specified address, and ignore the base address. -->  
<!-- The endpoint address is -->  
<!-- net.tcp://localhost:9000/servicemodelsamples/service. -->  
<endpoint address=  
          "net.tcp://localhost:9000/servicemodelsamples/service"  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
</service>  
```  
  
 <span data-ttu-id="88a1a-123">İstemci dört hizmet uç noktalarına yalnızca biri erişir, ancak tüm dört kendi yapılandırma dosyasında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="88a1a-123">The client accesses just one of the four service endpoints, but all four are defined in its configuration file.</span></span> <span data-ttu-id="88a1a-124">Oluştururken istemci bir uç nokta seçer `CalculatorProxy` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="88a1a-124">The client selects an endpoint when it creates the `CalculatorProxy` object.</span></span> <span data-ttu-id="88a1a-125">Yapılandırma adı değiştirerek `CalculatorEndpoint1` aracılığıyla `CalculatorEndpoint4`, her bitiş noktalarının alıştırma yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88a1a-125">By changing the configuration name from `CalculatorEndpoint1` through `CalculatorEndpoint4`, you can exercise each of the endpoints.</span></span>  
  
 <span data-ttu-id="88a1a-126">Örneği çalıştırdığınızda, hizmet adı ve her biri kendi uç noktaları için sözleşme adı bağlama adresi numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="88a1a-126">When you run the sample, the service enumerates the address, binding name and contract name for each of its endpoints.</span></span> <span data-ttu-id="88a1a-127">Meta veri değişimi (MEX) uç noktası başka bir uç nokta ServiceHost'ın açısından olduğundan, listede görünür.</span><span class="sxs-lookup"><span data-stu-id="88a1a-127">The metadata exchange (MEX) endpoint is just another endpoint from the ServiceHost's perspective so it shows up in the list.</span></span>  
  
```  
Service endpoints:  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/test  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8001/hello/servicemodelsamples  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  net.tcp://localhost:9000/servicemodelsamples/service  
           binding:  NetTcpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/mex  
           binding:  MetadataExchangeHttpBinding  
           contract: IMetadataExchange  
  
The service is ready.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="88a1a-128">İstemci çalıştırdığınızda, işlem isteklerini ve yanıtlarını hem hizmet hem de istemci konsol pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="88a1a-128">When you run the client, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="88a1a-129">Her konsol penceresinde hizmet ve istemci kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="88a1a-129">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="88a1a-130">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="88a1a-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="88a1a-131">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="88a1a-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="88a1a-132">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="88a1a-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="88a1a-133">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="88a1a-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="88a1a-134">Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanırsanız, istemci kodu eşleşecek şekilde istemci yapılandırmasında uç nokta adı değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="88a1a-134">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="88a1a-135">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="88a1a-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="88a1a-136">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="88a1a-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="88a1a-137">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="88a1a-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="88a1a-138">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="88a1a-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
  
## <a name="see-also"></a><span data-ttu-id="88a1a-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="88a1a-139">See Also</span></span>
