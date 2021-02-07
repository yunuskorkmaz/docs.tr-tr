---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: özel bir WS-Metadata Exchange bağlaması yapılandırma'
title: 'Nasıl yapılır: Özel Bir WS-Metadata Değişimi Bağlaması Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: ae9d1932e7539d25c117a98bd130d1def8e691fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743739"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="f16f7-103">Nasıl yapılır: Özel Bir WS-Metadata Değişimi Bağlaması Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f16f7-103">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>

<span data-ttu-id="f16f7-104">Bu makalede, özel bir WS-Metadata Exchange bağlamasının nasıl yapılandırılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f16f7-104">This article explains how to configure a custom WS-Metadata exchange binding.</span></span> <span data-ttu-id="f16f7-105">Windows Communication Foundation (WCF), sistem tarafından tanımlanan dört meta veri bağlaması içerir, ancak istediğiniz bağlamayı kullanarak meta verileri yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f16f7-105">Windows Communication Foundation (WCF) includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="f16f7-106">Bu makalede, kullanarak meta verilerin nasıl yayımlanacağı gösterilmektedir `wsHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="f16f7-106">This article shows you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="f16f7-107">Bu bağlama, meta verileri güvenli bir şekilde gösterme seçeneği sunar.</span><span class="sxs-lookup"><span data-stu-id="f16f7-107">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="f16f7-108">Bu makaledeki kod, [Başlarken](../samples/getting-started-sample.md)' i temel alır.</span><span class="sxs-lookup"><span data-stu-id="f16f7-108">The code in this article is based on the [Getting Started](../samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="f16f7-109">Yapılandırma dosyası kullanma</span><span class="sxs-lookup"><span data-stu-id="f16f7-109">Using a configuration file</span></span>  
  
1. <span data-ttu-id="f16f7-110">Hizmetin yapılandırma dosyasında, etiketi içeren bir hizmet davranışı ekleyin `serviceMetadata` :</span><span class="sxs-lookup"><span data-stu-id="f16f7-110">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. <span data-ttu-id="f16f7-111">`behaviorConfiguration`Hizmet etiketine bu yeni davranışa başvuran bir öznitelik ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f16f7-111">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior" />
    ```  
  
3. <span data-ttu-id="f16f7-112">Adres olarak MEX, `wsHttpBinding` bağlama olarak ve sözleşme olarak belirten bir meta veri uç noktası ekleyin <xref:System.ServiceModel.Description.IMetadataExchange> :</span><span class="sxs-lookup"><span data-stu-id="f16f7-112">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. <span data-ttu-id="f16f7-113">Meta veri değişimi uç noktasının düzgün çalıştığını doğrulamak için, istemci yapılandırma dosyasına bir uç nokta etiketi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f16f7-113">To verify the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. <span data-ttu-id="f16f7-114">İstemcinin Main () yönteminde, yeni bir örnek oluşturun, <xref:System.ServiceModel.Description.MetadataExchangeClient> <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> özelliğini olarak ayarlayın `true` , çağırın <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> ve ardından döndürülen meta veri koleksiyonunu yineleyin:</span><span class="sxs-lookup"><span data-stu-id="f16f7-114">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```csharp
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="f16f7-115">Kodla yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f16f7-115">Configuring by code</span></span>  
  
1. <span data-ttu-id="f16f7-116"><xref:System.ServiceModel.WSHttpBinding>Bağlama örneği oluştur:</span><span class="sxs-lookup"><span data-stu-id="f16f7-116">Create a <xref:System.ServiceModel.WSHttpBinding> binding instance:</span></span>  
  
    ```csharp  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. <span data-ttu-id="f16f7-117">Örnek oluşturun <xref:System.ServiceModel.ServiceHost> :</span><span class="sxs-lookup"><span data-stu-id="f16f7-117">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```csharp  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. <span data-ttu-id="f16f7-118">Hizmet uç noktası ekleyin ve bir <xref:System.ServiceModel.Description.ServiceMetadataBehavior> örnek ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f16f7-118">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. <span data-ttu-id="f16f7-119">Daha önce oluşturulmuş bir meta veri değişimi uç noktası ekleyin <xref:System.ServiceModel.WSHttpBinding> :</span><span class="sxs-lookup"><span data-stu-id="f16f7-119">Add a metadata exchange endpoint, specifying the <xref:System.ServiceModel.WSHttpBinding> created earlier:</span></span>  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. <span data-ttu-id="f16f7-120">Meta veri değişimi uç noktasının düzgün çalıştığını doğrulamak için, istemci yapılandırma dosyasına bir uç nokta etiketi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f16f7-120">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. <span data-ttu-id="f16f7-121">İstemcinin Main () yönteminde, yeni bir örnek oluşturun, <xref:System.ServiceModel.Description.MetadataExchangeClient> <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> özelliğini olarak ayarlayın `true` , çağırın <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> ve ardından döndürülen meta veri koleksiyonu aracılığıyla yineleyin:</span><span class="sxs-lookup"><span data-stu-id="f16f7-121">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```csharp  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f16f7-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f16f7-122">See also</span></span>

- [<span data-ttu-id="f16f7-123">Meta Veri Yayımlama Davranışı</span><span class="sxs-lookup"><span data-stu-id="f16f7-123">Metadata Publishing Behavior</span></span>](../samples/metadata-publishing-behavior.md)
- [<span data-ttu-id="f16f7-124">Meta Verileri Alma</span><span class="sxs-lookup"><span data-stu-id="f16f7-124">Retrieve Metadata</span></span>](../samples/retrieve-metadata.md)
- [<span data-ttu-id="f16f7-125">Meta veri</span><span class="sxs-lookup"><span data-stu-id="f16f7-125">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="f16f7-126">Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="f16f7-126">Publishing Metadata</span></span>](../feature-details/publishing-metadata.md)
- [<span data-ttu-id="f16f7-127">Meta Veri Uç Noktalarını Yayımlama</span><span class="sxs-lookup"><span data-stu-id="f16f7-127">Publishing Metadata Endpoints</span></span>](../publishing-metadata-endpoints.md)
