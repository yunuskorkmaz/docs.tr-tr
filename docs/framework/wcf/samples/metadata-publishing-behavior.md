---
description: 'Daha fazla bilgi edinin: meta veri yayımlama davranışı'
title: Meta Veri Yayımlama Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: 13e52e5f2a8d301eac3100cbf2350cc5a089aa34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752250"
---
# <a name="metadata-publishing-behavior"></a><span data-ttu-id="41e51-103">Meta Veri Yayımlama Davranışı</span><span class="sxs-lookup"><span data-stu-id="41e51-103">Metadata Publishing Behavior</span></span>

<span data-ttu-id="41e51-104">Meta veri yayımlama davranışı örneği, bir hizmetin meta veri yayımlama özelliklerinin nasıl kontrol leceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="41e51-104">The Metadata Publishing Behavior sample demonstrates how to control the metadata publishing features of a service.</span></span> <span data-ttu-id="41e51-105">Potansiyel olarak duyarlı hizmet meta verilerinin istenmeden açıklanmasını engellemek için Windows Communication Foundation (WCF) Hizmetleri için varsayılan yapılandırma, meta veri yayımlamayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="41e51-105">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="41e51-106">Bu davranış, varsayılan olarak güvenlidir, ancak hizmetin meta veri yayımlama davranışı yapılandırmada açıkça etkinleştirilmediği sürece hizmeti çağırmak için gereken istemci kodunu oluşturmak için bir meta veri alma aracı (Svcutil.exe gibi) kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="41e51-106">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="41e51-107">Bu örnek, netlik açısından güvenli olmayan bir meta veri yayımlama uç noktasının nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="41e51-107">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="41e51-108">Bu uç noktalar, anonim olarak kimliği doğrulanmamış tüketiciler tarafından kullanılabilir ve bir hizmetin meta verilerinin genel olarak kapatılarak emin olmak için bu uç noktaların dağıtılmasından önce gerçekleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="41e51-108">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="41e51-109">Meta veri uç noktası güvenliğini sağlayan bir örnek için [özel güvenli meta veri uç noktası](custom-secure-metadata-endpoint.md) örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="41e51-109">See the [Custom Secure Metadata Endpoint](custom-secure-metadata-endpoint.md) sample for a sample that secures a metadata endpoint.</span></span>  
  
 <span data-ttu-id="41e51-110">Örnek, hizmet sözleşmesini uygulayan [kullanmaya](getting-started-sample.md)Başlarken ' i temel alır `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="41e51-110">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="41e51-111">Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="41e51-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41e51-112">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="41e51-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="41e51-113">Meta verileri kullanıma sunmasına yönelik bir hizmetin, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> hizmette yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="41e51-113">For a service to expose metadata, the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> must be configured on the service.</span></span> <span data-ttu-id="41e51-114">Bu davranış mevcut olduğunda, bir uç noktayı, <xref:System.ServiceModel.Description.IMetadataExchange> sözleşmeyi bir WS-MetadataExchange (MEX) protokolünün bir uygulama olarak kullanıma sunmak üzere yapılandırarak meta verileri yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41e51-114">When this behavior is present, you can publish metadata by configuring an endpoint to expose the <xref:System.ServiceModel.Description.IMetadataExchange> contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="41e51-115">Kolaylık olması için, bu sözleşmeye "IMetadataExchange" kısaltılmış yapılandırma adı verildi.</span><span class="sxs-lookup"><span data-stu-id="41e51-115">As a convenience, this contract has been given the abbreviated configuration name of "IMetadataExchange".</span></span> <span data-ttu-id="41e51-116">Bu örnek, `mexHttpBinding` `wsHttpBinding` güvenlik modu olarak ayarlanmış olan öğesine eşdeğer bir standart bağlama olan öğesini kullanır `None` .</span><span class="sxs-lookup"><span data-stu-id="41e51-116">This sample uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="41e51-117">Uç noktada "mex" göreli adresi kullanılır. bu durum, hizmet tabanı adresine karşı çözümlenirse, bir uç nokta adresinde oluşur `http://localhost/servicemodelsamples/service.svc/mex` .</span><span class="sxs-lookup"><span data-stu-id="41e51-117">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of `http://localhost/servicemodelsamples/service.svc/mex`.</span></span> <span data-ttu-id="41e51-118">Davranış yapılandırması aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="41e51-118">The following shows the behavior configuration:</span></span>  
  
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
  
 <span data-ttu-id="41e51-119">Aşağıda, MEX uç noktası gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="41e51-119">The following shows the MEX endpoint.</span></span>  
  
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
  
 <span data-ttu-id="41e51-120">Bu örnek, <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliğini olarak ayarlar `true` ve bu da hizmetin meta VERILERINI http get kullanarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="41e51-120">This sample sets the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, which also exposes the service's metadata using HTTP GET.</span></span> <span data-ttu-id="41e51-121">HTTP GET metaveri uç noktasını etkinleştirmek için hizmetin bir HTTP temel adresi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="41e51-121">To enable an HTTP GET metadata endpoint, the service must have an HTTP base address.</span></span> <span data-ttu-id="41e51-122">Sorgu dizesi, `?wsdl` meta verilere erişmek için hizmetin temel adresinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="41e51-122">The query string `?wsdl` is used on the base address of the service to access the metadata.</span></span> <span data-ttu-id="41e51-123">Örneğin, hizmet için WSDL 'yi bir Web tarayıcısında görmek için adresini kullanmanız gerekir `http://localhost/servicemodelsamples/service.svc?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="41e51-123">For example, to see the WSDL for the service in a Web browser you would use the address `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span> <span data-ttu-id="41e51-124">Alternatif olarak, ' ı ' e ayarlayarak HTTPS üzerinden meta verileri açığa çıkarmak için bu davranışı kullanabilirsiniz <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> `true` .</span><span class="sxs-lookup"><span data-stu-id="41e51-124">Alternatively, you can use this behavior to expose metadata over HTTPS by setting <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> to `true`.</span></span> <span data-ttu-id="41e51-125">Bu bir HTTPS temel adresi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="41e51-125">This requires an HTTPS base address.</span></span>  
  
 <span data-ttu-id="41e51-126">Hizmetin MEX uç noktasına erişmek için, [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="41e51-126">To access the service's MEX endpoint use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 <span data-ttu-id="41e51-127">Bu, hizmetin meta verilerini temel alan bir istemci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41e51-127">This generates a client based on the service's metadata.</span></span>  
  
 <span data-ttu-id="41e51-128">HTTP GET kullanarak hizmetin meta verilerine erişmek için tarayıcınızı üzerine gelin `http://localhost/servicemodelsamples/service.svc?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="41e51-128">To access the service's metadata using HTTP GET, point your browser to `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span>  
  
 <span data-ttu-id="41e51-129">Bu davranışı kaldırır ve hizmeti açmaya çalışırsanız bir özel durum alırsınız.</span><span class="sxs-lookup"><span data-stu-id="41e51-129">If you remove this behavior and try to open the service you get an exception.</span></span> <span data-ttu-id="41e51-130">Bu hata, davranışı olmadan yapılandırılan bitiş noktasının `IMetadataExchange` hiçbir uygulamaya sahip olmadığı için oluşur.</span><span class="sxs-lookup"><span data-stu-id="41e51-130">This error occurs because without the behavior, the endpoint configured with the `IMetadataExchange` contract has no implementation.</span></span>  
  
 <span data-ttu-id="41e51-131">`HttpGetEnabled`Olarak ayarlarsanız `false` , hizmetin meta verilerini görmek yerine hesaplatorservıce yardım sayfasını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="41e51-131">If you set `HttpGetEnabled` to `false`, you see the CalculatorService help page instead of seeing the service's metadata.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="41e51-132">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="41e51-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="41e51-133">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="41e51-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="41e51-134">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="41e51-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="41e51-135">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="41e51-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="41e51-136">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="41e51-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="41e51-137">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="41e51-137">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="41e51-138">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="41e51-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="41e51-139">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="41e51-139">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
