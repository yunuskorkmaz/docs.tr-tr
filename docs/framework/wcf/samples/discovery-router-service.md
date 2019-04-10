---
title: Keşif Yönlendirme Hizmeti
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 166f6b9d1055e36f987e6b9a81fe69dc8bd548b9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318773"
---
# <a name="discovery-router-service"></a><span data-ttu-id="ff906-102">Keşif Yönlendirme Hizmeti</span><span class="sxs-lookup"><span data-stu-id="ff906-102">Discovery Router Service</span></span>
<span data-ttu-id="ff906-103">Bu örnek, başka bir uç nokta bulma iletileri iletecek şekilde gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ff906-103">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="ff906-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="ff906-104">Demonstrates</span></span>  
 <span data-ttu-id="ff906-105">Bulma yönlendirme</span><span class="sxs-lookup"><span data-stu-id="ff906-105">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="ff906-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="ff906-106">Discussion</span></span>  
 <span data-ttu-id="ff906-107">Bulma yönlendirme, Ara sunucu kullanarak bir hizmet için bir istemci arıyor ve proxy böyle bir hizmet fark etmez, ancak başka bir proxy bildiği bir senaryoda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="ff906-107">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="ff906-108">Bu proxy, ikinci Ara sunucuya Bu istemciden bulma paket iletebilir.</span><span class="sxs-lookup"><span data-stu-id="ff906-108">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="ff906-109">İkinci proxy, hizmet için konum ve özgün istemciye bir yanıt döndürür.</span><span class="sxs-lookup"><span data-stu-id="ff906-109">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="ff906-110">Bu örnekte, bir istemci bir bulma yönlendirme bileşenin bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="ff906-110">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="ff906-111">Bu ileti, bulma yönlendiricisinde belirli bir uç noktasına gönderilir.</span><span class="sxs-lookup"><span data-stu-id="ff906-111">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="ff906-112">Yönlendirici, iletiyi daha sonra bir UDP olarak iletir. çok noktaya yayın bitiş noktası.</span><span class="sxs-lookup"><span data-stu-id="ff906-112">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="ff906-113">Araştırma iletisi ve çok noktaya yayın bitiş noktası ve bir UDP çok noktaya yayın üzerinde dinleyen bir hizmeti, bulma yönlendiriciye adresi yanıt gider.</span><span class="sxs-lookup"><span data-stu-id="ff906-113">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="ff906-114">Bulma yönlendirici yanıtları toplar ve bunları istemciye geri gönderir.</span><span class="sxs-lookup"><span data-stu-id="ff906-114">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ff906-115">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ff906-115">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ff906-116">Örneği derleyin.</span><span class="sxs-lookup"><span data-stu-id="ff906-116">Build the sample.</span></span>  
  
2. <span data-ttu-id="ff906-117">DiscoveryRouter yürütülebilir dosyayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ff906-117">Run the DiscoveryRouter executable.</span></span>  
  
3. <span data-ttu-id="ff906-118">Yürütülebilir hizmet oluşturma dizinden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ff906-118">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="ff906-119">İstemci yürütülebilir çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ff906-119">Run the client executable.</span></span> <span data-ttu-id="ff906-120">İstemci hizmeti bulduktan unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ff906-120">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ff906-121">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="ff906-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ff906-122">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ff906-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ff906-123">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ff906-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ff906-124">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ff906-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
