---
title: CustomDiscoveryMetadata
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5b3272b642a04821d8343cae776e48f90d266cfe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="customdiscoverymetadata"></a><span data-ttu-id="cba1a-102">CustomDiscoveryMetadata</span><span class="sxs-lookup"><span data-stu-id="cba1a-102">CustomDiscoveryMetadata</span></span>
<span data-ttu-id="cba1a-103">Bu örnek, bulma meta veri hizmeti tarafından sunulan bulunabilirlik bir uç nokta için özel XML meta verileri takın gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cba1a-103">This sample shows how to insert custom XML metadata into the discovery metadata for a discoverable endpoint exposed by a service.</span></span> <span data-ttu-id="cba1a-104">Örnek sonra nasıl bir istemci hizmeti için arama yapın ve bu özel veri ayıklamak gösterir.</span><span class="sxs-lookup"><span data-stu-id="cba1a-104">The sample then shows how a client can search for the service and extract this custom data.</span></span> <span data-ttu-id="cba1a-105">Bu örnek iki proje, hizmet ve istemci oluşur.</span><span class="sxs-lookup"><span data-stu-id="cba1a-105">This sample consists of two projects, service and client.</span></span>  
  
## <a name="service"></a><span data-ttu-id="cba1a-106">Hizmet</span><span class="sxs-lookup"><span data-stu-id="cba1a-106">Service</span></span>  
 <span data-ttu-id="cba1a-107">İçinde `main` yöntemi, örnek gösterilmektedir türünde bir nesne <xref:System.Xml.Linq.XElement> istenen alanları ile doldurulur ve eklenir <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="cba1a-107">In the `main` method, the sample shows that an object of type <xref:System.Xml.Linq.XElement> is populated with the desired fields and is added to the <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>.</span></span> <span data-ttu-id="cba1a-108">Bu <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> için özel bir uç nokta eklenir.</span><span class="sxs-lookup"><span data-stu-id="cba1a-108">This <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> is added to a particular endpoint.</span></span> <span data-ttu-id="cba1a-109">Bu belirli uç bulunduğunda bulma meta verileri buraya eklenen özel verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="cba1a-109">When that particular endpoint is discovered, the discovery metadata contains the custom data that was added here.</span></span>  
  
## <a name="client"></a><span data-ttu-id="cba1a-110">İstemci</span><span class="sxs-lookup"><span data-stu-id="cba1a-110">Client</span></span>  
 <span data-ttu-id="cba1a-111">Örnek gösterir <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> üzerinde çağrılan yöntemi bir <xref:System.ServiceModel.Discovery.DiscoveryClient>.</span><span class="sxs-lookup"><span data-stu-id="cba1a-111">The sample shows the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method being called on a <xref:System.ServiceModel.Discovery.DiscoveryClient>.</span></span> <span data-ttu-id="cba1a-112">Elde edilen <xref:System.ServiceModel.Discovery.FindResponse> ardından uygun ve beklenen XML öğeleri için sorgulanır.</span><span class="sxs-lookup"><span data-stu-id="cba1a-112">The resulting <xref:System.ServiceModel.Discovery.FindResponse> is then queried for the appropriate and expected XML elements.</span></span> <span data-ttu-id="cba1a-113">Bu öğelerden sonra konsola yazdırılır.</span><span class="sxs-lookup"><span data-stu-id="cba1a-113">These elements are then printed to the console.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="cba1a-114">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="cba1a-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="cba1a-115">Proje çözümde yük [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ve projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="cba1a-115">Load the project solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="cba1a-116">İlk [çözüm temel dizin] \service\bin\debug içinde oluşturulan hizmet uygulamayı çalıştırın ve ardından [çözüm temel dizin] \Client\bin\debug oluşturulan istemci uygulaması çalıştırın</span><span class="sxs-lookup"><span data-stu-id="cba1a-116">First run the Service application, generated in [solution base directory]\service\bin\debug, and then run the Client application, generated in [solution base directory]\Client\bin\debug</span></span>  
  
3.  <span data-ttu-id="cba1a-117">Hizmetin çevrimiçi olduğunu, istemci hizmeti bulur ve meta veri uç yayımlanan yazdırır dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="cba1a-117">Note that the service comes online, the client locates the service and prints the metadata published in the endpoint.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cba1a-118">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="cba1a-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cba1a-119">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="cba1a-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cba1a-120">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="cba1a-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cba1a-121">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="cba1a-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a><span data-ttu-id="cba1a-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cba1a-122">See Also</span></span>
