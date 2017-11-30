---
title: "Nasıl yapılır: Özel Bir WS-Metadata Değişimi Bağlaması Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4202c0471c681257fa1ab1153d363e59615e10c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="75a1f-102">Nasıl yapılır: Özel Bir WS-Metadata Değişimi Bağlaması Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="75a1f-102">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>
<span data-ttu-id="75a1f-103">Bu konuda özel bir WS-Metadata yapılandırmak nasıl anlatılmıştır değişimi bağlaması.</span><span class="sxs-lookup"><span data-stu-id="75a1f-103">This topic will explain how to configure a custom WS-Metadata exchange binding.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="75a1f-104">dört sistem tanımlı meta veri bağlaması içeriyor ancak istediğiniz herhangi bir bağlamayı kullanarak meta verilerini yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="75a1f-104"> includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="75a1f-105">Bu konuda meta verileri kullanarak yayımlamak nasıl yapacağınızı gösterir `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="75a1f-105">This topic will show you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="75a1f-106">Bu bağlama meta verileri güvenli bir şekilde gösterme seçeneği sunar.</span><span class="sxs-lookup"><span data-stu-id="75a1f-106">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="75a1f-107">Bu makaledeki kod dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="75a1f-107">The code in this article is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="75a1f-108">Bir yapılandırma dosyası kullanma</span><span class="sxs-lookup"><span data-stu-id="75a1f-108">Using a configuration file</span></span>  
  
1.  <span data-ttu-id="75a1f-109">Hizmet yapılandırma dosyasında içeren bir hizmet davranışı eklemek `serviceMetadata` etiketi:</span><span class="sxs-lookup"><span data-stu-id="75a1f-109">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  <span data-ttu-id="75a1f-110">Ekleme bir `behaviorConfiguration` özniteliği bu yeni davranış başvuran hizmet etiketi:</span><span class="sxs-lookup"><span data-stu-id="75a1f-110">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3.  <span data-ttu-id="75a1f-111">MEX adresi olarak belirten bir meta veri uç noktası ekleme `wsHttpBinding` bağlama ve <xref:System.ServiceModel.Description.IMetadataExchange> Sözleşme:</span><span class="sxs-lookup"><span data-stu-id="75a1f-111">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4.  <span data-ttu-id="75a1f-112">Meta veri exchange uç noktası doğrulamak için çalışma doğru bir uç nokta etiketi ekleyin istemci yapılandırma dosyasında:</span><span class="sxs-lookup"><span data-stu-id="75a1f-112">To verify the metadata exchange endpoint is working correctly add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5.  <span data-ttu-id="75a1f-113">İstemcinin Main() yöntemi yeni bir oluşturun <xref:System.ServiceModel.Description.MetadataExchangeClient> örneği, Ayarla kendi <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> özelliğine `true`, çağrı <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> ve daha sonra döndürülen meta veri toplulukta tekrarlama:</span><span class="sxs-lookup"><span data-stu-id="75a1f-113">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="75a1f-114">Koduna göre yapılandırma</span><span class="sxs-lookup"><span data-stu-id="75a1f-114">Configuring by code</span></span>  
  
1.  <span data-ttu-id="75a1f-115">Oluşturma bir <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> bağlama örneği:</span><span class="sxs-lookup"><span data-stu-id="75a1f-115">Create a <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> binding instance:</span></span>  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2.  <span data-ttu-id="75a1f-116">Oluşturma bir <xref:System.ServiceModel.ServiceHost> örneği:</span><span class="sxs-lookup"><span data-stu-id="75a1f-116">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3.  <span data-ttu-id="75a1f-117">Hizmet uç noktası ekleyin ve ekleyin bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örneği:</span><span class="sxs-lookup"><span data-stu-id="75a1f-117">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4.  <span data-ttu-id="75a1f-118">Bir meta veri exchange uç nokta ekleme belirtme <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> daha önce oluşturduğunuz:</span><span class="sxs-lookup"><span data-stu-id="75a1f-118">Add a metadata exchange endpoint, specifying the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> created earlier:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5.  <span data-ttu-id="75a1f-119">Meta veri exchange uç noktası düzgün çalıştığını doğrulamak için istemci yapılandırma dosyasında bir bitiş etiketi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="75a1f-119">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6.  <span data-ttu-id="75a1f-120">İstemcinin Main() yöntemi yeni bir oluşturun <xref:System.ServiceModel.Description.MetadataExchangeClient> örneği, Ayarla <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> özelliğine `true`, çağrı <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> ve daha sonra döndürülen meta veri toplulukta tekrarlama:</span><span class="sxs-lookup"><span data-stu-id="75a1f-120">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="75a1f-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="75a1f-121">See Also</span></span>  
 [<span data-ttu-id="75a1f-122">Meta veri yayımlama davranışı</span><span class="sxs-lookup"><span data-stu-id="75a1f-122">Metadata Publishing Behavior</span></span>](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)  
 [<span data-ttu-id="75a1f-123">Meta veri alma</span><span class="sxs-lookup"><span data-stu-id="75a1f-123">Retrieve Metadata</span></span>](../../../../docs/framework/wcf/samples/retrieve-metadata.md)  
 [<span data-ttu-id="75a1f-124">Meta veriler</span><span class="sxs-lookup"><span data-stu-id="75a1f-124">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="75a1f-125">Meta veri yayımlama</span><span class="sxs-lookup"><span data-stu-id="75a1f-125">Publishing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)  
 [<span data-ttu-id="75a1f-126">Yayımlama meta veri uç noktaları</span><span class="sxs-lookup"><span data-stu-id="75a1f-126">Publishing Metadata Endpoints</span></span>](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)
