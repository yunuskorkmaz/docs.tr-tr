---
title: 'Nasıl yapılır: Özel Bir WS-Metadata Değişimi Bağlaması Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: 3d6f74d88dc9db775718c0098eccced4750d3b75
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184510"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="34741-102">Nasıl yapılır: Özel Bir WS-Metadata Değişimi Bağlaması Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="34741-102">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>
<span data-ttu-id="34741-103">Bu konu, özel bir WS-Metadata yapılandırma açıklayacak değişimi bağlaması.</span><span class="sxs-lookup"><span data-stu-id="34741-103">This topic will explain how to configure a custom WS-Metadata exchange binding.</span></span> <span data-ttu-id="34741-104">Windows Communication Foundation (WCF) dört sistem tarafından tanımlanan meta veri bağlamaları içerir, ancak meta veriler, istediğiniz herhangi bir bağlamayı kullanarak yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="34741-104">Windows Communication Foundation (WCF) includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="34741-105">Bu konuda, meta verileri kullanarak yayımlamak nasıl gösterilecektir `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="34741-105">This topic will show you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="34741-106">Bu bağlama, güvenli bir şekilde meta verileri kullanıma sunduğundan seçeneği sunar.</span><span class="sxs-lookup"><span data-stu-id="34741-106">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="34741-107">Bu makalede kod dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="34741-107">The code in this article is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="34741-108">Yapılandırma dosyası kullanma</span><span class="sxs-lookup"><span data-stu-id="34741-108">Using a configuration file</span></span>  
  
1.  <span data-ttu-id="34741-109">Hizmet yapılandırma dosyasında içeren bir hizmet davranışını ekleyin `serviceMetadata` etiketi:</span><span class="sxs-lookup"><span data-stu-id="34741-109">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  <span data-ttu-id="34741-110">Ekleme bir `behaviorConfiguration` özniteliği bu yeni davranış başvuran hizmet etiketi:</span><span class="sxs-lookup"><span data-stu-id="34741-110">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3.  <span data-ttu-id="34741-111">MEX adres olarak belirten bir meta veri uç noktası ekleme `wsHttpBinding` bağlama olarak ve <xref:System.ServiceModel.Description.IMetadataExchange> Sözleşme:</span><span class="sxs-lookup"><span data-stu-id="34741-111">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4.  <span data-ttu-id="34741-112">Meta veri değişimi uç noktası olduğunu doğrulamak için çalışma doğru bir uç nokta etiket eklemede istemci yapılandırma dosyasında:</span><span class="sxs-lookup"><span data-stu-id="34741-112">To verify the metadata exchange endpoint is working correctly add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5.  <span data-ttu-id="34741-113">Yeni bir istemcinin Main() yöntemi oluşturma <xref:System.ServiceModel.Description.MetadataExchangeClient> örnek olarak ayarlayın, <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> özelliğini `true`, çağrı <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> ve ardından döndürülen meta verileri koleksiyonu yineleme:</span><span class="sxs-lookup"><span data-stu-id="34741-113">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="34741-114">Kod ile yapılandırma</span><span class="sxs-lookup"><span data-stu-id="34741-114">Configuring by code</span></span>  
  
1.  <span data-ttu-id="34741-115">Oluşturma bir <xref:System.ServiceModel.WSHttpBinding> bağlama örneği:</span><span class="sxs-lookup"><span data-stu-id="34741-115">Create a <xref:System.ServiceModel.WSHttpBinding> binding instance:</span></span>  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2.  <span data-ttu-id="34741-116">Oluşturma bir <xref:System.ServiceModel.ServiceHost> örneği:</span><span class="sxs-lookup"><span data-stu-id="34741-116">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3.  <span data-ttu-id="34741-117">Hizmet uç noktası ekleme ve ekleme bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örneği:</span><span class="sxs-lookup"><span data-stu-id="34741-117">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4.  <span data-ttu-id="34741-118">Meta veri değişimi uç noktası ekleme belirtme <xref:System.ServiceModel.WSHttpBinding> daha önce oluşturulan:</span><span class="sxs-lookup"><span data-stu-id="34741-118">Add a metadata exchange endpoint, specifying the <xref:System.ServiceModel.WSHttpBinding> created earlier:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5.  <span data-ttu-id="34741-119">Meta veri değişimi uç noktası düzgün çalıştığını doğrulamak için istemci yapılandırma dosyasında bir bitiş etiketi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="34741-119">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6.  <span data-ttu-id="34741-120">Yeni bir istemcinin Main() yöntemi oluşturma <xref:System.ServiceModel.Description.MetadataExchangeClient> örnek olarak ayarlayın <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> özelliğini `true`, çağrı <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> ve ardından döndürülen meta verileri koleksiyonu yineleme:</span><span class="sxs-lookup"><span data-stu-id="34741-120">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="34741-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34741-121">See Also</span></span>  
 [<span data-ttu-id="34741-122">Meta Veri Yayımlama Davranışı</span><span class="sxs-lookup"><span data-stu-id="34741-122">Metadata Publishing Behavior</span></span>](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)  
 [<span data-ttu-id="34741-123">Meta Verileri Alma</span><span class="sxs-lookup"><span data-stu-id="34741-123">Retrieve Metadata</span></span>](../../../../docs/framework/wcf/samples/retrieve-metadata.md)  
 [<span data-ttu-id="34741-124">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="34741-124">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="34741-125">Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="34741-125">Publishing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)  
 [<span data-ttu-id="34741-126">Meta Veri Uç Noktalarını Yayımlama</span><span class="sxs-lookup"><span data-stu-id="34741-126">Publishing Metadata Endpoints</span></span>](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)
