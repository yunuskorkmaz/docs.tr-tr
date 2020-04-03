---
title: 'Nasıl yapılır: Özel Bir WS-Metadata Değişimi Bağlaması Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: 6459e3f0cf0ab72af8027bd6802a0e7aa574aece
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635792"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="333cc-102">Nasıl yapılır: Özel Bir WS-Metadata Değişimi Bağlaması Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="333cc-102">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>

<span data-ttu-id="333cc-103">Bu makalede, özel bir WS-Meta veri değişimi bağlama yapılandırmak için nasıl açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="333cc-103">This article explains how to configure a custom WS-Metadata exchange binding.</span></span> <span data-ttu-id="333cc-104">Windows Communication Foundation (WCF) dört sistem tanımlı meta veri bağlaması içerir, ancak meta verileri istediğiniz bağlamayı kullanarak yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="333cc-104">Windows Communication Foundation (WCF) includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="333cc-105">Bu makalede, meta verileri kullanarak `wsHttpBinding`nasıl yayımlayacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="333cc-105">This article shows you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="333cc-106">Bu bağlama, meta verileri güvenli bir şekilde açığa çıkarma seçeneği sunar.</span><span class="sxs-lookup"><span data-stu-id="333cc-106">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="333cc-107">Bu makaledeki kod [Başlarken](../samples/getting-started-sample.md)dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="333cc-107">The code in this article is based on the [Getting Started](../samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="333cc-108">Yapılandırma dosyası kullanma</span><span class="sxs-lookup"><span data-stu-id="333cc-108">Using a configuration file</span></span>  
  
1. <span data-ttu-id="333cc-109">Hizmetin yapılandırma dosyasında, `serviceMetadata` etiketi içeren bir hizmet davranışı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="333cc-109">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. <span data-ttu-id="333cc-110">Bu `behaviorConfiguration` yeni davranışa başvuran hizmet etiketine bir öznitelik ekleyin:</span><span class="sxs-lookup"><span data-stu-id="333cc-110">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior" />
    ```  
  
3. <span data-ttu-id="333cc-111">Mex'i adres olarak, `wsHttpBinding` bağlama olarak ve <xref:System.ServiceModel.Description.IMetadataExchange> sözleşme olarak belirten bir meta veri bitiş noktası ekleyin:</span><span class="sxs-lookup"><span data-stu-id="333cc-111">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. <span data-ttu-id="333cc-112">Meta veri değişimi bitiş noktasının doğru çalıştığını doğrulamak için istemci yapılandırma dosyasına bir uç nokta etiketi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="333cc-112">To verify the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. <span data-ttu-id="333cc-113">İstemcinin Main() yönteminde, <xref:System.ServiceModel.Description.MetadataExchangeClient> yeni bir <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> örnek `true`oluşturun, <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> özelliğini döndürülen meta verilerin toplanması yoluyla , aramak ve sonra yinelemek için ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="333cc-113">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```csharp
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="333cc-114">Koda göre yapılandırma</span><span class="sxs-lookup"><span data-stu-id="333cc-114">Configuring by code</span></span>  
  
1. <span data-ttu-id="333cc-115">Bağlayıcı <xref:System.ServiceModel.WSHttpBinding> bir örnek oluşturun:</span><span class="sxs-lookup"><span data-stu-id="333cc-115">Create a <xref:System.ServiceModel.WSHttpBinding> binding instance:</span></span>  
  
    ```csharp  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. <span data-ttu-id="333cc-116">Bir <xref:System.ServiceModel.ServiceHost> örnek oluşturun:</span><span class="sxs-lookup"><span data-stu-id="333cc-116">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```csharp  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. <span data-ttu-id="333cc-117">Hizmet bitiş noktası ekleyin <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ve bir örnek ekleyin:</span><span class="sxs-lookup"><span data-stu-id="333cc-117">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. <span data-ttu-id="333cc-118">Daha önce <xref:System.ServiceModel.WSHttpBinding> oluşturulan belirterek bir meta veri değişimi bitiş noktası ekleyin:</span><span class="sxs-lookup"><span data-stu-id="333cc-118">Add a metadata exchange endpoint, specifying the <xref:System.ServiceModel.WSHttpBinding> created earlier:</span></span>  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. <span data-ttu-id="333cc-119">Meta veri alışverişi bitiş noktasının doğru çalıştığını doğrulamak için istemci yapılandırma dosyasına bir uç nokta etiketi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="333cc-119">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. <span data-ttu-id="333cc-120">İstemcinin Main() yönteminde, <xref:System.ServiceModel.Description.MetadataExchangeClient> yeni bir <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> örnek `true`oluşturun, <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> özelliği , arama ve döndürülen meta verilerin toplanması yoluyla yinelemek için ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="333cc-120">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```csharp  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="333cc-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="333cc-121">See also</span></span>

- [<span data-ttu-id="333cc-122">Meta Veri Yayımlama Davranışı</span><span class="sxs-lookup"><span data-stu-id="333cc-122">Metadata Publishing Behavior</span></span>](../samples/metadata-publishing-behavior.md)
- [<span data-ttu-id="333cc-123">Meta Verileri Alma</span><span class="sxs-lookup"><span data-stu-id="333cc-123">Retrieve Metadata</span></span>](../samples/retrieve-metadata.md)
- [<span data-ttu-id="333cc-124">Meta veriler</span><span class="sxs-lookup"><span data-stu-id="333cc-124">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="333cc-125">Meta Verileri Yayımlama</span><span class="sxs-lookup"><span data-stu-id="333cc-125">Publishing Metadata</span></span>](../feature-details/publishing-metadata.md)
- [<span data-ttu-id="333cc-126">Meta Veri Uç Noktalarını Yayımlama</span><span class="sxs-lookup"><span data-stu-id="333cc-126">Publishing Metadata Endpoints</span></span>](../publishing-metadata-endpoints.md)
