---
title: Meta Veri Yayımlama Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: dade6d1a53fd99b994fb3c027db4e51392bfdcda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144402"
---
# <a name="metadata-publishing-behavior"></a><span data-ttu-id="8a4e3-102">Meta Veri Yayımlama Davranışı</span><span class="sxs-lookup"><span data-stu-id="8a4e3-102">Metadata Publishing Behavior</span></span>
<span data-ttu-id="8a4e3-103">Meta veri yayımlama davranışı örneği, bir hizmetin meta veri yayımlama özelliklerinin nasıl denetlenir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-103">The Metadata Publishing Behavior sample demonstrates how to control the metadata publishing features of a service.</span></span> <span data-ttu-id="8a4e3-104">Potansiyel olarak hassas hizmet meta verilerinin kasıtsız olarak açıklanmasını önlemek için, Windows Communication Foundation (WCF) hizmetleri için varsayılan yapılandırma meta veri yayımlamayı devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-104">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="8a4e3-105">Bu davranış varsayılan olarak güvenlidir, ancak hizmetin meta veri yayımlama davranışı yapılandırmada açıkça etkinleştirilmediği sürece hizmeti çağırmak için gereken istemci kodunu oluşturmak için bir meta veri alma aracını (Svcutil.exe gibi) kullanamayacağınız anlamına da gelir.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-105">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8a4e3-106">Bu örnek, açıklık için güvenli olmayan bir meta veri yayımlama bitiş noktasının nasıl oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-106">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="8a4e3-107">Bu tür uç noktalar anonim kimliği doğrulanmamış tüketiciler için kullanılabilir ve bir hizmetin meta verilerinin herkese açık olarak ifşa edilmesinin uygun olduğundan emin olmak için bu uç noktaları dağıtmadan önce dikkatli olunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-107">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="8a4e3-108">Meta [veri](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) bitiş noktasını güvence altına alan bir örnek için Özel Güvenli Meta Veri Bitiş Noktası örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-108">See the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample for a sample that secures a metadata endpoint.</span></span>  
  
 <span data-ttu-id="8a4e3-109">Örnek, hizmet sözleşmesini uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) `ICalculator` dayanır.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-109">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="8a4e3-110">Bu örnekte, istemci bir konsol uygulamasıdır (.exe) ve hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-110">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a4e3-111">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8a4e3-112">Bir hizmetin meta verileri <xref:System.ServiceModel.Description.ServiceMetadataBehavior> açığa çıkarabilmesi için, hizmet üzerinde yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-112">For a service to expose metadata, the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> must be configured on the service.</span></span> <span data-ttu-id="8a4e3-113">Bu davranış söz konusu olduğunda, <xref:System.ServiceModel.Description.IMetadataExchange> sözleşmeyi ws-MetadataExchange (MEX) protokolünün bir uygulaması olarak ortaya çıkarmak için bir bitiş noktası yapılandırarak meta verileri yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-113">When this behavior is present, you can publish metadata by configuring an endpoint to expose the <xref:System.ServiceModel.Description.IMetadataExchange> contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="8a4e3-114">Kolaylık sağlamak amacıyla, bu sözleşmeye "IMetadataExchange" kısaltma yapılandırma adı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-114">As a convenience, this contract has been given the abbreviated configuration name of "IMetadataExchange".</span></span> <span data-ttu-id="8a4e3-115">Bu `mexHttpBinding`örnek, güvenlik modu ile eşdeğer `wsHttpBinding` bir kolaylık standart bağlama `None`kullanır.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-115">This sample uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="8a4e3-116">Uç noktada "mex"in göreceli bir adresi kullanılır ve hizmetler temel adresine karşı çözüldüğünde `http://localhost/servicemodelsamples/service.svc/mex`bir bitiş noktası adresi .</span><span class="sxs-lookup"><span data-stu-id="8a4e3-116">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of `http://localhost/servicemodelsamples/service.svc/mex`.</span></span> <span data-ttu-id="8a4e3-117">Aşağıdaki davranış yapılandırmasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="8a4e3-117">The following shows the behavior configuration:</span></span>  
  
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
  
 <span data-ttu-id="8a4e3-118">Aşağıdaki MEX bitiş noktasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-118">The following shows the MEX endpoint.</span></span>  
  
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
  
 <span data-ttu-id="8a4e3-119">Bu örnek <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> `true`özelliği , http GET kullanarak hizmetin meta verilerini de ortaya çıkaran olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-119">This sample sets the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, which also exposes the service's metadata using HTTP GET.</span></span> <span data-ttu-id="8a4e3-120">HTTP GET meta veri bitiş noktasını etkinleştirmek için hizmetin bir HTTP temel adresi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-120">To enable an HTTP GET metadata endpoint, the service must have an HTTP base address.</span></span> <span data-ttu-id="8a4e3-121">Sorgu dizesi, `?wsdl` meta verilere erişmek için hizmetin temel adresinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-121">The query string `?wsdl` is used on the base address of the service to access the metadata.</span></span> <span data-ttu-id="8a4e3-122">Örneğin, bir Web tarayıcısında hizmet için WSDL görmek için `http://localhost/servicemodelsamples/service.svc?wsdl`adresi kullanmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-122">For example, to see the WSDL for the service in a Web browser you would use the address `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span> <span data-ttu-id="8a4e3-123">Alternatif olarak, bu davranışı, https üzerinden meta <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> verileri `true`' ye ayarlayarak ortaya çıkarmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-123">Alternatively, you can use this behavior to expose metadata over HTTPS by setting <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> to `true`.</span></span> <span data-ttu-id="8a4e3-124">Bunun için bir HTTPS temel adresi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-124">This requires an HTTPS base address.</span></span>  
  
 <span data-ttu-id="8a4e3-125">Hizmetin MEX bitiş noktasına erişmek için [ServiceModel Metadata Utility Tool 'u (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-125">To access the service's MEX endpoint use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 <span data-ttu-id="8a4e3-126">Bu, hizmetin meta verilerine dayalı bir istemci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-126">This generates a client based on the service's metadata.</span></span>  
  
 <span data-ttu-id="8a4e3-127">HTTP GET'i kullanarak hizmetin meta verilerine `http://localhost/servicemodelsamples/service.svc?wsdl`erişmek için tarayıcınızı ' a' ya yönlendirin.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-127">To access the service's metadata using HTTP GET, point your browser to `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span>  
  
 <span data-ttu-id="8a4e3-128">Bu davranışı kaldırır ve hizmeti açmaya çalışırsanız bir özel durum elde elabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-128">If you remove this behavior and try to open the service you get an exception.</span></span> <span data-ttu-id="8a4e3-129">Bu hata, davranış olmadan, sözleşmeyle yapılandırılan `IMetadataExchange` bitiş noktasının uygulaması olmadığından oluşur.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-129">This error occurs because without the behavior, the endpoint configured with the `IMetadataExchange` contract has no implementation.</span></span>  
  
 <span data-ttu-id="8a4e3-130">`false`Ayarlarsanız, `HttpGetEnabled` hizmetin meta verilerini görmek yerine Hesap Makinesi Hizmeti yardım sayfasını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-130">If you set `HttpGetEnabled` to `false`, you see the CalculatorService help page instead of seeing the service's metadata.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8a4e3-131">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="8a4e3-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8a4e3-132">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8a4e3-133">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="8a4e3-134">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8a4e3-135">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8a4e3-136">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8a4e3-137">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8a4e3-138">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="8a4e3-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
