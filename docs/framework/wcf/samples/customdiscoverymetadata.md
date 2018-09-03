---
title: CustomDiscoveryMetadata
ms.date: 03/30/2017
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
ms.openlocfilehash: 181910db3f1dd6da892f6ae2ddcbf7bd5859ff17
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43465583"
---
# <a name="customdiscoverymetadata"></a><span data-ttu-id="5d23d-102">CustomDiscoveryMetadata</span><span class="sxs-lookup"><span data-stu-id="5d23d-102">CustomDiscoveryMetadata</span></span>
<span data-ttu-id="5d23d-103">Bu örnek, bulma meta veriler hizmet tarafından sunulan bulunabilirlik bir uç nokta için özel XML meta veri eklemeye gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5d23d-103">This sample shows how to insert custom XML metadata into the discovery metadata for a discoverable endpoint exposed by a service.</span></span> <span data-ttu-id="5d23d-104">Örnek sonra nasıl bir istemci hizmeti için arama yapın ve bu özel verileri ayıklamak gösterir.</span><span class="sxs-lookup"><span data-stu-id="5d23d-104">The sample then shows how a client can search for the service and extract this custom data.</span></span> <span data-ttu-id="5d23d-105">Bu örnek, iki proje, hizmet ve istemci oluşur.</span><span class="sxs-lookup"><span data-stu-id="5d23d-105">This sample consists of two projects, service and client.</span></span>  
  
## <a name="service"></a><span data-ttu-id="5d23d-106">Hizmet</span><span class="sxs-lookup"><span data-stu-id="5d23d-106">Service</span></span>  
 <span data-ttu-id="5d23d-107">İçinde `main` yöntemi, örnek gösterir, bir nesne türü <xref:System.Xml.Linq.XElement> istenen alanları ile doldurulur ve eklendiğinden <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="5d23d-107">In the `main` method, the sample shows that an object of type <xref:System.Xml.Linq.XElement> is populated with the desired fields and is added to the <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>.</span></span> <span data-ttu-id="5d23d-108">Bu <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> için belirli bir uç noktası eklenir.</span><span class="sxs-lookup"><span data-stu-id="5d23d-108">This <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> is added to a particular endpoint.</span></span> <span data-ttu-id="5d23d-109">Belirli uç noktanın bulunduğunda bulma buraya eklenen özel verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="5d23d-109">When that particular endpoint is discovered, the discovery metadata contains the custom data that was added here.</span></span>  
  
## <a name="client"></a><span data-ttu-id="5d23d-110">İstemci</span><span class="sxs-lookup"><span data-stu-id="5d23d-110">Client</span></span>  
 <span data-ttu-id="5d23d-111">Örnek gösterir <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> üzerinde çağrılan yöntemi bir <xref:System.ServiceModel.Discovery.DiscoveryClient>.</span><span class="sxs-lookup"><span data-stu-id="5d23d-111">The sample shows the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method being called on a <xref:System.ServiceModel.Discovery.DiscoveryClient>.</span></span> <span data-ttu-id="5d23d-112">Ortaya çıkan <xref:System.ServiceModel.Discovery.FindResponse> ardından uygun ve beklenen XML öğeleri için sorgulanır.</span><span class="sxs-lookup"><span data-stu-id="5d23d-112">The resulting <xref:System.ServiceModel.Discovery.FindResponse> is then queried for the appropriate and expected XML elements.</span></span> <span data-ttu-id="5d23d-113">Bu öğeleri daha sonra konsola yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="5d23d-113">These elements are then printed to the console.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="5d23d-114">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="5d23d-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="5d23d-115">Proje çözümde yük [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ve projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="5d23d-115">Load the project solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="5d23d-116">İlk [çözüm temel dizini] \service\bin\debug içinde oluşturulan hizmet uygulamayı çalıştırın ve ardından [çözüm temel dizini] \Client\bin\debug içinde oluşturulan istemci uygulamasını çalıştırın</span><span class="sxs-lookup"><span data-stu-id="5d23d-116">First run the Service application, generated in [solution base directory]\service\bin\debug, and then run the Client application, generated in [solution base directory]\Client\bin\debug</span></span>  
  
3.  <span data-ttu-id="5d23d-117">Hizmetin çevrimiçi duruma, istemci hizmeti bulur ve meta veri uç noktasında yayımlanan yazdırır dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="5d23d-117">Note that the service comes online, the client locates the service and prints the metadata published in the endpoint.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5d23d-118">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="5d23d-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5d23d-119">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5d23d-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5d23d-120">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5d23d-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5d23d-121">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5d23d-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a><span data-ttu-id="5d23d-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d23d-122">See Also</span></span>
