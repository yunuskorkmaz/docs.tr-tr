---
title: Meta Veri Yayımlama Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: 3b3057d845ac37280ff46e6e15415758f1f0ba77
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714788"
---
# <a name="metadata-publishing-behavior"></a><span data-ttu-id="d9fcc-102">Meta Veri Yayımlama Davranışı</span><span class="sxs-lookup"><span data-stu-id="d9fcc-102">Metadata Publishing Behavior</span></span>
<span data-ttu-id="d9fcc-103">Meta veri yayımlama davranışı örneği, bir hizmetin meta veri yayımlama özelliklerinin nasıl kontrol leceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-103">The Metadata Publishing Behavior sample demonstrates how to control the metadata publishing features of a service.</span></span> <span data-ttu-id="d9fcc-104">Potansiyel olarak duyarlı hizmet meta verilerinin istenmeden açıklanmasını engellemek için Windows Communication Foundation (WCF) Hizmetleri için varsayılan yapılandırma, meta veri yayımlamayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-104">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="d9fcc-105">Bu davranış, varsayılan olarak güvenlidir, ancak hizmetin meta veri yayımlama davranışı yapılandırmada açıkça etkinleştirilmediği sürece hizmeti çağırmak için gereken istemci kodunu oluşturmak için bir meta veri alma aracı (Svcutil. exe gibi) kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-105">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d9fcc-106">Bu örnek, netlik açısından güvenli olmayan bir meta veri yayımlama uç noktasının nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-106">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="d9fcc-107">Bu uç noktalar, anonim olarak kimliği doğrulanmamış tüketiciler tarafından kullanılabilir ve bir hizmetin meta verilerinin genel olarak kapatılarak emin olmak için bu uç noktaların dağıtılmasından önce gerçekleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-107">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="d9fcc-108">Meta veri uç noktası güvenliğini sağlayan bir örnek için [özel güvenli meta veri uç noktası](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-108">See the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample for a sample that secures a metadata endpoint.</span></span>  
  
 <span data-ttu-id="d9fcc-109">Örnek, `ICalculator` hizmet sözleşmesini uygulayan [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-109">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="d9fcc-110">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-110">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9fcc-111">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d9fcc-112">Bir hizmetin meta verileri kullanıma sunmasına yönelik <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, hizmette yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-112">For a service to expose metadata, the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> must be configured on the service.</span></span> <span data-ttu-id="d9fcc-113">Bu davranış mevcut olduğunda, bir uç noktayı, <xref:System.ServiceModel.Description.IMetadataExchange> sözleşmesinin bir WS-MetadataExchange (MEX) protokolünün bir uygulama olarak kullanıma sunulacak şekilde yapılandırarak meta verileri yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-113">When this behavior is present, you can publish metadata by configuring an endpoint to expose the <xref:System.ServiceModel.Description.IMetadataExchange> contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="d9fcc-114">Kolaylık olması için, bu sözleşmeye "IMetadataExchange" kısaltılmış yapılandırma adı verildi.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-114">As a convenience, this contract has been given the abbreviated configuration name of "IMetadataExchange".</span></span> <span data-ttu-id="d9fcc-115">Bu örnek, güvenlik modu `None`olarak ayarlanan `wsHttpBinding` eşdeğer bir standart bağlama olan `mexHttpBinding`kullanır.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-115">This sample uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="d9fcc-116">Uç noktada "mex" göreli adresi kullanılır ve bu, hizmetler temel adresiyle çözümlenirse, `http://localhost/servicemodelsamples/service.svc/mex`uç nokta adresiyle sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-116">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of `http://localhost/servicemodelsamples/service.svc/mex`.</span></span> <span data-ttu-id="d9fcc-117">Davranış yapılandırması aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d9fcc-117">The following shows the behavior configuration:</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- The serviceMetadata behavior publishes metadata through   
           the IMetadataExchange contract. When this behavior is   
           present, you can expose this contract through an endpoint   
           as shown below. Setting httpGetEnabled to true publishes   
           the service's WSDL at the <baseaddress>?wsdl, for example,  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="d9fcc-118">Aşağıda, MEX uç noktası gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-118">The following shows the MEX endpoint.</span></span>  
  
```xml  
<!-- the MEX endpoint is exposed at   
     http://localhost/servicemodelsamples/service.svc/mex   
     To expose the IMetadataExchange contract, you   
     must enable the serviceMetadata behavior as demonstrated                           
     previously. -->  
<endpoint address="mex"  
          binding="mexHttpBinding"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="d9fcc-119">Bu örnek, <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliğini `true`olarak ayarlar ve bu da hizmetin meta verilerini HTTP GET kullanarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-119">This sample sets the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, which also exposes the service's metadata using HTTP GET.</span></span> <span data-ttu-id="d9fcc-120">HTTP GET metaveri uç noktasını etkinleştirmek için hizmetin bir HTTP temel adresi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-120">To enable an HTTP GET metadata endpoint, the service must have an HTTP base address.</span></span> <span data-ttu-id="d9fcc-121">Sorgu dizesi `?wsdl`, meta verilere erişmek için hizmetin temel adresinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-121">The query string `?wsdl` is used on the base address of the service to access the metadata.</span></span> <span data-ttu-id="d9fcc-122">Örneğin, hizmet için WSDL 'yi bir Web tarayıcısında görmek için `http://localhost/servicemodelsamples/service.svc?wsdl`adresini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-122">For example, to see the WSDL for the service in a Web browser you would use the address `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span> <span data-ttu-id="d9fcc-123">Alternatif olarak, <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> `true`ayarlayarak HTTPS üzerinden meta verileri açığa çıkarmak için bu davranışı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-123">Alternatively, you can use this behavior to expose metadata over HTTPS by setting <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> to `true`.</span></span> <span data-ttu-id="d9fcc-124">Bu bir HTTPS temel adresi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-124">This requires an HTTPS base address.</span></span>  
  
 <span data-ttu-id="d9fcc-125">Hizmetin MEX uç noktasına erişmek için, [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-125">To access the service's MEX endpoint use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 <span data-ttu-id="d9fcc-126">Bu, hizmetin meta verilerini temel alan bir istemci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-126">This generates a client based on the service's metadata.</span></span>  
  
 <span data-ttu-id="d9fcc-127">HTTP GET kullanarak hizmetin meta verilerine erişmek için tarayıcınızı `http://localhost/servicemodelsamples/service.svc?wsdl`üzerine getirin.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-127">To access the service's metadata using HTTP GET, point your browser to `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span>  
  
 <span data-ttu-id="d9fcc-128">Bu davranışı kaldırır ve hizmeti açmaya çalışırsanız bir özel durum alırsınız.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-128">If you remove this behavior and try to open the service you get an exception.</span></span> <span data-ttu-id="d9fcc-129">Bu hata, davranışı olmadan, `IMetadataExchange` sözleşmesiyle yapılandırılan uç noktanın hiçbir uygulamayla karşılaşmasından kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-129">This error occurs because without the behavior, the endpoint configured with the `IMetadataExchange` contract has no implementation.</span></span>  
  
 <span data-ttu-id="d9fcc-130">`HttpGetEnabled` `false`olarak ayarlarsanız, hizmetin meta verilerini görmek yerine Hesaplatorservice yardım sayfasını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-130">If you set `HttpGetEnabled` to `false`, you see the CalculatorService help page instead of seeing the service's metadata.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d9fcc-131">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="d9fcc-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d9fcc-132">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d9fcc-133">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d9fcc-134">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d9fcc-135">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d9fcc-136">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-136">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="d9fcc-137">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d9fcc-138">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d9fcc-138">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
