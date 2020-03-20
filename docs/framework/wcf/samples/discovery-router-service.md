---
title: Keşif Yönlendirme Hizmeti
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 149dd69cdd1972465f4b7cb48ab657492d3f21d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183722"
---
# <a name="discovery-router-service"></a><span data-ttu-id="10c6f-102">Keşif Yönlendirme Hizmeti</span><span class="sxs-lookup"><span data-stu-id="10c6f-102">Discovery Router Service</span></span>
<span data-ttu-id="10c6f-103">Bu örnek, keşif iletilerinin başka bir uç noktaya nasıl iletilenin nasıl gösterildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="10c6f-103">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="10c6f-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="10c6f-104">Demonstrates</span></span>  
 <span data-ttu-id="10c6f-105">Keşif Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="10c6f-105">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="10c6f-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="10c6f-106">Discussion</span></span>  
 <span data-ttu-id="10c6f-107">Bulma yönlendirme, istemcinin proxy kullanarak bir hizmet aradığı ve proxy'nin böyle bir hizmetten habersiz olduğu, ancak başka bir proxy bildiği bir senaryoda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="10c6f-107">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="10c6f-108">Bu proxy, bulma paketini bu istemciden ikinci proxy'ye iletebilir.</span><span class="sxs-lookup"><span data-stu-id="10c6f-108">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="10c6f-109">İkinci proxy hizmeti arar ve yanıtları özgün istemciye döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="10c6f-109">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="10c6f-110">Bu örnekte, istemci bir bulma yönlendirme bileşenine bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="10c6f-110">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="10c6f-111">Bu ileti, bulma yönlendiricisindeki belirli bir bitiş noktasına gönderilir.</span><span class="sxs-lookup"><span data-stu-id="10c6f-111">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="10c6f-112">Yönlendirici daha sonra iletiyi UDP çok noktaya yayın ucuna ileter.</span><span class="sxs-lookup"><span data-stu-id="10c6f-112">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="10c6f-113">Sonda iletisi çok noktaya yayın ucuna gider ve UDP çok noktaya yayın adresini dinleyen bir hizmet bu keşif yönlendiricisine yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="10c6f-113">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="10c6f-114">Bulma yönlendiricisi yanıtları toplar ve istemciye geri gönderir.</span><span class="sxs-lookup"><span data-stu-id="10c6f-114">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="10c6f-115">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="10c6f-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="10c6f-116">Örneği derleyin.</span><span class="sxs-lookup"><span data-stu-id="10c6f-116">Build the sample.</span></span>  
  
2. <span data-ttu-id="10c6f-117">DiscoveryRouter çalıştırılabilir çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="10c6f-117">Run the DiscoveryRouter executable.</span></span>  
  
3. <span data-ttu-id="10c6f-118">Yapı dizininden çalıştırılabilen hizmeti çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="10c6f-118">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="10c6f-119">İstemciyi çalıştırılabilir çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="10c6f-119">Run the client executable.</span></span> <span data-ttu-id="10c6f-120">İstemcinin hizmeti bulup bulmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="10c6f-120">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="10c6f-121">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="10c6f-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="10c6f-122">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="10c6f-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="10c6f-123">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="10c6f-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="10c6f-124">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="10c6f-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
