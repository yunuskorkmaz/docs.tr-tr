---
title: Keşif Yönlendirme Hizmeti
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: f3ea32d10e27eceb3edcee8b6aeacbf9c5ebc6f1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96292655"
---
# <a name="discovery-router-service"></a><span data-ttu-id="0b7fb-102">Keşif Yönlendirme Hizmeti</span><span class="sxs-lookup"><span data-stu-id="0b7fb-102">Discovery Router Service</span></span>

<span data-ttu-id="0b7fb-103">Bu örnek, bulma iletilerinin başka bir uç noktaya nasıl iletileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-103">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="0b7fb-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="0b7fb-104">Demonstrates</span></span>  

 <span data-ttu-id="0b7fb-105">Bulma yönlendirmesi</span><span class="sxs-lookup"><span data-stu-id="0b7fb-105">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="0b7fb-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="0b7fb-106">Discussion</span></span>  

 <span data-ttu-id="0b7fb-107">Bulma yönlendirmesi, bir istemcinin proxy kullanarak hizmet arayan ve proxy 'nin böyle bir hizmetin farkında olduğu, ancak başka bir proxy 'nin bildiği bir senaryoda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-107">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="0b7fb-108">Bu proxy, bulma paketini bu istemciden ikinci proxy 'ye iletebilir.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-108">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="0b7fb-109">İkinci proxy hizmeti arayabilir ve özgün istemciye yanıtları döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-109">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="0b7fb-110">Bu örnekte, bir istemci bulma yönlendirme bileşenine bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-110">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="0b7fb-111">Bu ileti, bulma yönlendiricisinde belirli bir uç noktaya gönderilir.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-111">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="0b7fb-112">Yönlendirici daha sonra iletiyi bir UDP çok noktaya yayın uç noktasına iletir.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-112">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="0b7fb-113">Araştırma iletisi çok noktaya yayın uç noktasına gider ve bir UDP çok noktaya yayın adresini dinleyen bir hizmet, bu bulma yönlendiricisine yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-113">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="0b7fb-114">Bulma yönlendiricisi yanıtları toplar ve istemciye geri gönderir.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-114">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0b7fb-115">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="0b7fb-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0b7fb-116">Örneği derleyin.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-116">Build the sample.</span></span>  
  
2. <span data-ttu-id="0b7fb-117">DiscoveryRouter yürütülebilir dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-117">Run the DiscoveryRouter executable.</span></span>  
  
3. <span data-ttu-id="0b7fb-118">Hizmet yürütülebilir dosyasını yapı dizininden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-118">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="0b7fb-119">İstemci yürütülebilir dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-119">Run the client executable.</span></span> <span data-ttu-id="0b7fb-120">İstemcinin hizmeti konumlandırır olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-120">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0b7fb-121">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0b7fb-122">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0b7fb-123">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0b7fb-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0b7fb-124">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0b7fb-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
