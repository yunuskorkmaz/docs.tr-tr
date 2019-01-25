---
title: 'Nasıl yapılır: Yapılandırma özel bir WS-Metadata değişimi bağlaması'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: 4328306a6b67d2eac498ec48d1769bdf4bd5f81e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642470"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="7b0a5-102">Nasıl yapılır: Yapılandırma özel bir WS-Metadata değişimi bağlaması</span><span class="sxs-lookup"><span data-stu-id="7b0a5-102">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>
<span data-ttu-id="7b0a5-103">Bu konu, özel bir WS-Metadata yapılandırma açıklayacak değişimi bağlaması.</span><span class="sxs-lookup"><span data-stu-id="7b0a5-103">This topic will explain how to configure a custom WS-Metadata exchange binding.</span></span> <span data-ttu-id="7b0a5-104">Windows Communication Foundation (WCF) dört sistem tarafından tanımlanan meta veri bağlamaları içerir, ancak meta veriler, istediğiniz herhangi bir bağlamayı kullanarak yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b0a5-104">Windows Communication Foundation (WCF) includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="7b0a5-105">Bu konuda, meta verileri kullanarak yayımlamak nasıl gösterilecektir `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="7b0a5-105">This topic will show you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="7b0a5-106">Bu bağlama, güvenli bir şekilde meta verileri kullanıma sunduğundan seçeneği sunar.</span><span class="sxs-lookup"><span data-stu-id="7b0a5-106">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="7b0a5-107">Bu makalede kod dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="7b0a5-107">The code in this article is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="7b0a5-108">Yapılandırma dosyası kullanma</span><span class="sxs-lookup"><span data-stu-id="7b0a5-108">Using a configuration file</span></span>  
  
1.  <span data-ttu-id="7b0a5-109">Hizmet yapılandırma dosyasında içeren bir hizmet davranışını ekleyin `serviceMetadata` etiketi:</span><span class="sxs-lookup"><span data-stu-id="7b0a5-109">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  <span data-ttu-id="7b0a5-110">Ekleme bir `behaviorConfiguration` özniteliği bu yeni davranış başvuran hizmet etiketi:</span><span class="sxs-lookup"><span data-stu-id="7b0a5-110">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3.  <span data-ttu-id="7b0a5-111">MEX adres olarak belirten bir meta veri uç noktası ekleme `wsHttpBinding` bağlama olarak ve <xref:System.ServiceModel.Description.IMetadataExchange> Sözleşme:</span><span class="sxs-lookup"><span data-stu-id="7b0a5-111">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4.  <span data-ttu-id="7b0a5-112">Meta veri değişimi uç noktası olduğunu doğrulamak için çalışma doğru bir uç nokta etiket eklemede istemci yapılandırma dosyasında:</span><span class="sxs-lookup"><span data-stu-id="7b0a5-112">To verify the metadata exchange endpoint is working correctly add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5.  <span data-ttu-id="7b0a5-113">Yeni bir istemcinin Main() yöntemi oluşturma <xref:System.ServiceModel.Description.MetadataExchangeClient> örnek olarak ayarlayın, <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> özelliğini `true`, çağrı <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> ve ardından döndürülen meta verileri koleksiyonu yineleme:</span><span class="sxs-lookup"><span data-stu-id="7b0a5-113">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="7b0a5-114">Kod ile yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7b0a5-114">Configuring by code</span></span>  
  
1.  <span data-ttu-id="7b0a5-115">Oluşturma bir <xref:System.ServiceModel.WSHttpBinding> bağlama örneği:</span><span class="sxs-lookup"><span data-stu-id="7b0a5-115">Create a <xref:System.ServiceModel.WSHttpBinding> binding instance:</span></span>  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2.  <span data-ttu-id="7b0a5-116">Oluşturma bir <xref:System.ServiceModel.ServiceHost> örneği:</span><span class="sxs-lookup"><span data-stu-id="7b0a5-116">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3.  <span data-ttu-id="7b0a5-117">Hizmet uç noktası ekleme ve ekleme bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örneği:</span><span class="sxs-lookup"><span data-stu-id="7b0a5-117">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4.  <span data-ttu-id="7b0a5-118">Meta veri değişimi uç noktası ekleme belirtme <xref:System.ServiceModel.WSHttpBinding> daha önce oluşturulan:</span><span class="sxs-lookup"><span data-stu-id="7b0a5-118">Add a metadata exchange endpoint, specifying the <xref:System.ServiceModel.WSHttpBinding> created earlier:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5.  <span data-ttu-id="7b0a5-119">Meta veri değişimi uç noktası düzgün çalıştığını doğrulamak için istemci yapılandırma dosyasında bir bitiş etiketi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7b0a5-119">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6.  <span data-ttu-id="7b0a5-120">Yeni bir istemcinin Main() yöntemi oluşturma <xref:System.ServiceModel.Description.MetadataExchangeClient> örnek olarak ayarlayın <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> özelliğini `true`, çağrı <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> ve ardından döndürülen meta verileri koleksiyonu yineleme:</span><span class="sxs-lookup"><span data-stu-id="7b0a5-120">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7b0a5-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b0a5-121">See also</span></span>
- [<span data-ttu-id="7b0a5-122">Meta Veri Yayımlama Davranışı</span><span class="sxs-lookup"><span data-stu-id="7b0a5-122">Metadata Publishing Behavior</span></span>](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)
- [<span data-ttu-id="7b0a5-123">Meta Verileri Alma</span><span class="sxs-lookup"><span data-stu-id="7b0a5-123">Retrieve Metadata</span></span>](../../../../docs/framework/wcf/samples/retrieve-metadata.md)
- [<span data-ttu-id="7b0a5-124">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="7b0a5-124">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="7b0a5-125">Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="7b0a5-125">Publishing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)
- [<span data-ttu-id="7b0a5-126">Meta Veri Uç Noktalarını Yayımlama</span><span class="sxs-lookup"><span data-stu-id="7b0a5-126">Publishing Metadata Endpoints</span></span>](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)
