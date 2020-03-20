---
title: Adres Ayarlama
ms.date: 03/30/2017
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
ms.openlocfilehash: 4403ac2bf8e0e5193006f6ec19b24a9bcb00bf35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183971"
---
# <a name="addressing"></a><span data-ttu-id="cb412-102">Adres Ayarlama</span><span class="sxs-lookup"><span data-stu-id="cb412-102">Addressing</span></span>
<span data-ttu-id="cb412-103">Adresleme örneği, uç nokta adreslerinin çeşitli yönlerini ve özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb412-103">The Addressing sample demonstrates various aspects and features of endpoint addresses.</span></span> <span data-ttu-id="cb412-104">Örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb412-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="cb412-105">Bu örnekte hizmet kendi kendine barındırılır.</span><span class="sxs-lookup"><span data-stu-id="cb412-105">In this sample the service is self-hosted.</span></span> <span data-ttu-id="cb412-106">Hem hizmet hem de istemci konsol uygulamalarıdır.</span><span class="sxs-lookup"><span data-stu-id="cb412-106">Both the service and the client are console applications.</span></span> <span data-ttu-id="cb412-107">Hizmet, göreli ve mutlak uç nokta adreslerinin bir birleşimini kullanarak birden çok uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cb412-107">The service defines multiple endpoints using a combination of relative and absolute endpoint addresses.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb412-108">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="cb412-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="cb412-109">Hizmet yapılandırma dosyası nda bir temel adres ve dört uç nokta belirtilir.</span><span class="sxs-lookup"><span data-stu-id="cb412-109">The service configuration file specifies a base address and four endpoints.</span></span> <span data-ttu-id="cb412-110">Temel adres, aşağıdaki örnek yapılandırmada gösterildiği gibi hizmet/ana bilgisayar/baseAddresss altında ekle öğesi kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="cb412-110">The base address is specified using the add element, under service/host/baseAddresses as demonstrated in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="cb412-111">Aşağıdaki örnek yapılandırmada gösterilen ilk uç nokta tanımı göreceli bir adres belirtir, bu da bitiş noktası adresinin temel adres ile URI kompozisyonunun kurallarını izleyen göreli adresin birleşimi olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cb412-111">The first endpoint definition shown in the following sample configuration specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of URI composition.</span></span>  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="cb412-112">Bu durumda, göreli adres boş (""), bu nedenle bitiş noktası adresi temel adresle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="cb412-112">In this case, the relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="cb412-113">Gerçek bitiş noktası `http://localhost:8000/servicemodelsamples/service`adresi .</span><span class="sxs-lookup"><span data-stu-id="cb412-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>
  
 <span data-ttu-id="cb412-114">İkinci uç nokta tanımı, aşağıdaki örnek yapılandırmada gösterildiği gibi göreli bir adres de belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb412-114">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span>  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="cb412-115">Göreli adres, "test", temel adrese eklenir.</span><span class="sxs-lookup"><span data-stu-id="cb412-115">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="cb412-116">Gerçek bitiş noktası `http://localhost:8000/servicemodelsamples/service/test`adresi .</span><span class="sxs-lookup"><span data-stu-id="cb412-116">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>
  
 <span data-ttu-id="cb412-117">Üçüncü uç nokta tanımı, aşağıdaki örnek yapılandırmada gösterildiği gibi mutlak bir adres belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb412-117">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="cb412-118">Temel adres adreste hiçbir rol oynamaz.</span><span class="sxs-lookup"><span data-stu-id="cb412-118">The base address plays no role in the address.</span></span> <span data-ttu-id="cb412-119">Gerçek bitiş noktası `http://localhost:8001/hello/servicemodelsamples`adresi .</span><span class="sxs-lookup"><span data-stu-id="cb412-119">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>
  
 <span data-ttu-id="cb412-120">Dördüncü uç nokta adresi mutlak bir adres ve farklı bir aktarım belirtir—TCP.</span><span class="sxs-lookup"><span data-stu-id="cb412-120">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="cb412-121">Temel adres adreste hiçbir rol oynamaz.</span><span class="sxs-lookup"><span data-stu-id="cb412-121">The base address plays no role in the address.</span></span> <span data-ttu-id="cb412-122">Gerçek bitiş noktası `net.tcp://localhost:9000/servicemodelsamples/service`adresi .</span><span class="sxs-lookup"><span data-stu-id="cb412-122">The actual endpoint address is `net.tcp://localhost:9000/servicemodelsamples/service`.</span></span>
  
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
  
 <span data-ttu-id="cb412-123">İstemci dört hizmet uç noktasından yalnızca birine erişir, ancak dördü de yapılandırma dosyasında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="cb412-123">The client accesses just one of the four service endpoints, but all four are defined in its configuration file.</span></span> <span data-ttu-id="cb412-124">İstemci `CalculatorProxy` nesneyi oluştururken bir bitiş noktası seçer.</span><span class="sxs-lookup"><span data-stu-id="cb412-124">The client selects an endpoint when it creates the `CalculatorProxy` object.</span></span> <span data-ttu-id="cb412-125">Yapılandırma adını `CalculatorEndpoint1` buradan `CalculatorEndpoint4`değiştirerek, uç noktaların her birini egzersiz yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb412-125">By changing the configuration name from `CalculatorEndpoint1` through `CalculatorEndpoint4`, you can exercise each of the endpoints.</span></span>  
  
 <span data-ttu-id="cb412-126">Örneği çalıştırdığınızda, hizmet, bitiş noktalarının her biri için adresi, bağlama adını ve sözleşme adını diziler.</span><span class="sxs-lookup"><span data-stu-id="cb412-126">When you run the sample, the service enumerates the address, binding name and contract name for each of its endpoints.</span></span> <span data-ttu-id="cb412-127">Meta veri değişimi (MEX) bitiş noktası, ServiceHost'un bakış açısından yalnızca başka bir bitiş noktasıdır, bu nedenle listede gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb412-127">The metadata exchange (MEX) endpoint is just another endpoint from the ServiceHost's perspective so it shows up in the list.</span></span>  
  
```console  
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
  
 <span data-ttu-id="cb412-128">İstemciyi çalıştırdığınızda, işlem istekleri ve yanıtları hem hizmet hem de istemci konsolu pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cb412-128">When you run the client, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="cb412-129">Hizmeti ve istemciyi kapatmak için her konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="cb412-129">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cb412-130">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="cb412-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="cb412-131">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="cb412-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="cb412-132">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="cb412-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="cb412-133">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="cb412-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="cb412-134">Bu örnek için yapılandırmayı yeniden oluşturmak için Svcutil.exe kullanıyorsanız, istemci yapılandırmasındaki uç nokta adını istemci koduyla eşleşecek şekilde değiştirdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="cb412-134">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cb412-135">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="cb412-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cb412-136">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="cb412-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="cb412-137">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="cb412-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cb412-138">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb412-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
