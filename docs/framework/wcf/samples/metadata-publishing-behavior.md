---
title: Meta Veri Yayımlama Davranışı
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: 547ff9fcaca8b9af7a7559a11ef4c4a8b5996174
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33505527"
---
# <a name="metadata-publishing-behavior"></a><span data-ttu-id="6ea3c-102">Meta Veri Yayımlama Davranışı</span><span class="sxs-lookup"><span data-stu-id="6ea3c-102">Metadata Publishing Behavior</span></span>
<span data-ttu-id="6ea3c-103">Meta veri yayımlama davranışı örneği, bir hizmetin meta veri yayımlama özelliklerini denetlemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-103">The Metadata Publishing Behavior sample demonstrates how to control the metadata publishing features of a service.</span></span> <span data-ttu-id="6ea3c-104">Olası hassas hizmeti meta verilerin yanlışlıkla açığa çıkmasını önlemek için meta veri yayımlama Windows Communication Foundation (WCF) hizmetlerini için varsayılan yapılandırmayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-104">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="6ea3c-105">Bu davranışı varsayılan olarak güvenlidir, ancak ayrıca bir meta veri kullanamayacağı anlamına gelir (örneğin, Svcutil.exe) aracı hizmetin meta veri yayımlama davranışı açıkça yapılandırmasında etkinleştirilmediği sürece hizmetini çağırmak için gerekli istemci kodu oluşturmak üzere, içe.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-105">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6ea3c-106">Daha anlaşılır olması için bu örnek nasıl güvenli meta veri yayımlama uç noktası oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-106">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="6ea3c-107">Bu tür uç noktaları anonim kimlik doğrulamasız tüketicilere potansiyel olarak kullanılabilir ve bakım gibi uç noktaları dağıtmadan önce genel olarak disclosing bir hizmetin meta veri uygun olduğundan emin olmak için izlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-107">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="6ea3c-108">Bkz: [özel güvenli meta veri uç noktasının](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) bir meta veri uç noktası güvenli hale getiren bir örnek için örnek.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-108">See the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample for a sample that secures a metadata endpoint.</span></span>  
  
 <span data-ttu-id="6ea3c-109">Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), hangi uygulayan `ICalculator` hizmet sözleşme.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-109">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="6ea3c-110">Bu örnekte, istemci bir konsol uygulaması (.exe) ve Internet Information Services (IIS) tarafından barındırılan hizmetindeki.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-110">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ea3c-111">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="6ea3c-112">Meta veri, kullanıma sunmak bir hizmet için <xref:System.ServiceModel.Description.ServiceMetadataBehavior> hizmette yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-112">For a service to expose metadata, the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> must be configured on the service.</span></span> <span data-ttu-id="6ea3c-113">Bu davranış bulunduğunda kullanıma sunmak için bir uç nokta yapılandırarak meta verileri yayımlayabilirsiniz <xref:System.ServiceModel.Description.IMetadataExchange> WS-MetadataExchange (MEX) Protokolü uygulaması olarak sözleşme.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-113">When this behavior is present, you can publish metadata by configuring an endpoint to expose the <xref:System.ServiceModel.Description.IMetadataExchange> contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="6ea3c-114">Kolaylık, bu sözleşme "IMetadataExchange" kısaltılmış yapılandırma adı verilmedi.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-114">As a convenience, this contract has been given the abbreviated configuration name of "IMetadataExchange".</span></span> <span data-ttu-id="6ea3c-115">Bu örnekte `mexHttpBinding`, kolaylık sağlamak amacıyla bağlaması standart olduğu eşdeğerdir `wsHttpBinding` kümesine güvenlik moduyla `None`.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-115">This sample uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="6ea3c-116">"Mex" göreli adresidir kullanılan uç, hangi olduğunda çözülmüş temel Hizmetleri karşı adresi sonuçları bir uç nokta adresi http://localhost/servicemodelsamples/service.svc/mex.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-116">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of http://localhost/servicemodelsamples/service.svc/mex.</span></span> <span data-ttu-id="6ea3c-117">Aşağıdaki davranış yapılandırmasını gösterir:</span><span class="sxs-lookup"><span data-stu-id="6ea3c-117">The following shows the behavior configuration:</span></span>  
  
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
  
 <span data-ttu-id="6ea3c-118">Aşağıdaki MEX bitiş noktası gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-118">The following shows the MEX endpoint.</span></span>  
  
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
  
 <span data-ttu-id="6ea3c-119">Bu örnek ayarlar <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> özelliğine `true`, hangi ayrıca sunan HTTP GET kullanarak hizmetin meta verileri.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-119">This sample sets the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, which also exposes the service's metadata using HTTP GET.</span></span> <span data-ttu-id="6ea3c-120">Bir HTTP GET meta veri uç noktasının etkinleştirmek için hizmeti bir HTTP temel adresi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-120">To enable an HTTP GET metadata endpoint, the service must have an HTTP base address.</span></span> <span data-ttu-id="6ea3c-121">Sorgu dizesi `?wsdl` hizmetinin temel adresini meta verilerine erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-121">The query string `?wsdl` is used on the base address of the service to access the metadata.</span></span> <span data-ttu-id="6ea3c-122">Örneğin, bir Web tarayıcısı hizmetinde WSDL görmek için adresi kullanırsınız http://localhost/servicemodelsamples/service.svc?wsdl.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-122">For example, to see the WSDL for the service in a Web browser you would use the address http://localhost/servicemodelsamples/service.svc?wsdl.</span></span> <span data-ttu-id="6ea3c-123">Alternatif olarak, meta veri ayarlayarak HTTPS üzerinden kullanıma sunmak için bu davranış kullanabilirsiniz <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> için `true`.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-123">Alternatively, you can use this behavior to expose metadata over HTTPS by setting <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> to `true`.</span></span> <span data-ttu-id="6ea3c-124">Bu bir HTTPS temel adresi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-124">This requires an HTTPS base address.</span></span>  
  
 <span data-ttu-id="6ea3c-125">Hizmetin MEX uç noktası kullan erişmek için [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6ea3c-125">To access the service's MEX endpoint use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 <span data-ttu-id="6ea3c-126">Bu hizmetin meta verileri temel alarak istemci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-126">This generates a client based on the service's metadata.</span></span>  
  
 <span data-ttu-id="6ea3c-127">HTTP GET kullanarak hizmetin meta verilerine erişmek için tarayıcınızı noktası http://localhost/servicemodelsamples/service.svc?wsdl.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-127">To access the service's metadata using HTTP GET, point your browser to http://localhost/servicemodelsamples/service.svc?wsdl.</span></span>  
  
 <span data-ttu-id="6ea3c-128">Bu davranış kaldırırsanız ve hizmet açmaya çalıştığınızda bir özel durum alın.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-128">If you remove this behavior and try to open the service you get an exception.</span></span> <span data-ttu-id="6ea3c-129">Davranış uç nokta ile yapılandırılmış. Bu hata oluşur `IMetadataExchange` sözleşme hiçbir uygulama vardır.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-129">This error occurs because without the behavior, the endpoint configured with the `IMetadataExchange` contract has no implementation.</span></span>  
  
 <span data-ttu-id="6ea3c-130">Ayarlarsanız `HttpGetEnabled` için `false`, hizmetin meta verileri görmesini yerine CalculatorService yardım sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-130">If you set `HttpGetEnabled` to `false`, you see the CalculatorService help page instead of seeing the service's metadata.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6ea3c-131">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="6ea3c-131">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6ea3c-132">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6ea3c-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="6ea3c-133">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6ea3c-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="6ea3c-134">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6ea3c-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6ea3c-135">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6ea3c-136">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6ea3c-137">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6ea3c-138">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
  
## <a name="see-also"></a><span data-ttu-id="6ea3c-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6ea3c-139">See Also</span></span>
