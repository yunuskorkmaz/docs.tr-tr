---
description: 'Daha fazla bilgi edinin: bulma yönlendirici hizmeti'
title: Keşif Yönlendirme Hizmeti
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: f5fa4cd19758bef0b867fafc5af4b9cf6df27028
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726721"
---
# <a name="discovery-router-service"></a><span data-ttu-id="1574c-103">Keşif Yönlendirme Hizmeti</span><span class="sxs-lookup"><span data-stu-id="1574c-103">Discovery Router Service</span></span>

<span data-ttu-id="1574c-104">Bu örnek, bulma iletilerinin başka bir uç noktaya nasıl iletileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="1574c-104">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="1574c-105">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="1574c-105">Demonstrates</span></span>  

 <span data-ttu-id="1574c-106">Bulma yönlendirmesi</span><span class="sxs-lookup"><span data-stu-id="1574c-106">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="1574c-107">Tartışma</span><span class="sxs-lookup"><span data-stu-id="1574c-107">Discussion</span></span>  

 <span data-ttu-id="1574c-108">Bulma yönlendirmesi, bir istemcinin proxy kullanarak hizmet arayan ve proxy 'nin böyle bir hizmetin farkında olduğu, ancak başka bir proxy 'nin bildiği bir senaryoda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1574c-108">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="1574c-109">Bu proxy, bulma paketini bu istemciden ikinci proxy 'ye iletebilir.</span><span class="sxs-lookup"><span data-stu-id="1574c-109">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="1574c-110">İkinci proxy hizmeti arayabilir ve özgün istemciye yanıtları döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="1574c-110">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="1574c-111">Bu örnekte, bir istemci bulma yönlendirme bileşenine bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="1574c-111">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="1574c-112">Bu ileti, bulma yönlendiricisinde belirli bir uç noktaya gönderilir.</span><span class="sxs-lookup"><span data-stu-id="1574c-112">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="1574c-113">Yönlendirici daha sonra iletiyi bir UDP çok noktaya yayın uç noktasına iletir.</span><span class="sxs-lookup"><span data-stu-id="1574c-113">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="1574c-114">Araştırma iletisi çok noktaya yayın uç noktasına gider ve bir UDP çok noktaya yayın adresini dinleyen bir hizmet, bu bulma yönlendiricisine yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="1574c-114">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="1574c-115">Bulma yönlendiricisi yanıtları toplar ve istemciye geri gönderir.</span><span class="sxs-lookup"><span data-stu-id="1574c-115">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1574c-116">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="1574c-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1574c-117">Örneği derleyin.</span><span class="sxs-lookup"><span data-stu-id="1574c-117">Build the sample.</span></span>  
  
2. <span data-ttu-id="1574c-118">DiscoveryRouter yürütülebilir dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1574c-118">Run the DiscoveryRouter executable.</span></span>  
  
3. <span data-ttu-id="1574c-119">Hizmet yürütülebilir dosyasını yapı dizininden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1574c-119">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="1574c-120">İstemci yürütülebilir dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1574c-120">Run the client executable.</span></span> <span data-ttu-id="1574c-121">İstemcinin hizmeti konumlandırır olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1574c-121">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1574c-122">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="1574c-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1574c-123">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1574c-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1574c-124">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1574c-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1574c-125">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1574c-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
