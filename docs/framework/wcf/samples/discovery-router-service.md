---
title: Keşif Yönlendirme Hizmeti
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 09309b23d2a3cc672811c2f617e6fb81a2b4e021
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74712282"
---
# <a name="discovery-router-service"></a><span data-ttu-id="2c49b-102">Keşif Yönlendirme Hizmeti</span><span class="sxs-lookup"><span data-stu-id="2c49b-102">Discovery Router Service</span></span>
<span data-ttu-id="2c49b-103">Bu örnek, bulma iletilerinin başka bir uç noktaya nasıl iletileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2c49b-103">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="2c49b-104">Gösterir</span><span class="sxs-lookup"><span data-stu-id="2c49b-104">Demonstrates</span></span>  
 <span data-ttu-id="2c49b-105">Bulma yönlendirmesi</span><span class="sxs-lookup"><span data-stu-id="2c49b-105">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="2c49b-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="2c49b-106">Discussion</span></span>  
 <span data-ttu-id="2c49b-107">Bulma yönlendirmesi, bir istemcinin proxy kullanarak hizmet arayan ve proxy 'nin böyle bir hizmetin farkında olduğu, ancak başka bir proxy 'nin bildiği bir senaryoda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="2c49b-107">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="2c49b-108">Bu proxy, bulma paketini bu istemciden ikinci proxy 'ye iletebilir.</span><span class="sxs-lookup"><span data-stu-id="2c49b-108">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="2c49b-109">İkinci proxy hizmeti arayabilir ve özgün istemciye yanıtları döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="2c49b-109">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="2c49b-110">Bu örnekte, bir istemci bulma yönlendirme bileşenine bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="2c49b-110">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="2c49b-111">Bu ileti, bulma yönlendiricisinde belirli bir uç noktaya gönderilir.</span><span class="sxs-lookup"><span data-stu-id="2c49b-111">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="2c49b-112">Yönlendirici daha sonra iletiyi bir UDP çok noktaya yayın uç noktasına iletir.</span><span class="sxs-lookup"><span data-stu-id="2c49b-112">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="2c49b-113">Araştırma iletisi çok noktaya yayın uç noktasına gider ve bir UDP çok noktaya yayın adresini dinleyen bir hizmet, bu bulma yönlendiricisine yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="2c49b-113">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="2c49b-114">Bulma yönlendiricisi yanıtları toplar ve istemciye geri gönderir.</span><span class="sxs-lookup"><span data-stu-id="2c49b-114">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2c49b-115">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="2c49b-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2c49b-116">Örneği oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2c49b-116">Build the sample.</span></span>  
  
2. <span data-ttu-id="2c49b-117">DiscoveryRouter yürütülebilir dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2c49b-117">Run the DiscoveryRouter executable.</span></span>  
  
3. <span data-ttu-id="2c49b-118">Hizmet yürütülebilir dosyasını yapı dizininden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2c49b-118">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="2c49b-119">İstemci yürütülebilir dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2c49b-119">Run the client executable.</span></span> <span data-ttu-id="2c49b-120">İstemcinin hizmeti konumlandırır olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2c49b-120">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2c49b-121">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="2c49b-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2c49b-122">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="2c49b-122">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="2c49b-123">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="2c49b-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2c49b-124">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="2c49b-124">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
