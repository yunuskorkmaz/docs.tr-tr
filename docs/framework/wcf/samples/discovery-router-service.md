---
title: "Keşif Yönlendirme Hizmeti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ec96a4c318b7f9994f04bf2e4dfc6209cadda29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="discovery-router-service"></a><span data-ttu-id="06277-102">Keşif Yönlendirme Hizmeti</span><span class="sxs-lookup"><span data-stu-id="06277-102">Discovery Router Service</span></span>
<span data-ttu-id="06277-103">Bu örnek, başka bir uç nokta bulma iletilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="06277-103">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="06277-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="06277-104">Demonstrates</span></span>  
 <span data-ttu-id="06277-105">Keşif yönlendirme</span><span class="sxs-lookup"><span data-stu-id="06277-105">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="06277-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="06277-106">Discussion</span></span>  
 <span data-ttu-id="06277-107">Keşif yönlendirme, bir istemci bir proxy kullanarak bir hizmet için arıyor ve proxy bu tür bir hizmet farkında değildir, ancak başka bir proxy bilir bir senaryoda yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="06277-107">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="06277-108">Bu proxy bulma paketi Bu istemciden ikinci proxy sunucusuna iletebilir.</span><span class="sxs-lookup"><span data-stu-id="06277-108">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="06277-109">İkinci proxy hizmeti için konum ve özgün istemci yanıtlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="06277-109">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="06277-110">Bu örnekte, bir istemci bir bulma yönlendirme bileşenine bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="06277-110">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="06277-111">Bu ileti bulma yönlendirici belirli bir noktadaki gönderilir.</span><span class="sxs-lookup"><span data-stu-id="06277-111">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="06277-112">Yönlendirici, iletiyi daha sonra bir UDP iletir. çok noktaya yayın bitiş noktası.</span><span class="sxs-lookup"><span data-stu-id="06277-112">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="06277-113">Yoklama iletisi çok noktaya yayın bitiş noktası ve UDP çok noktaya yayın üzerinde dinleyen bir hizmeti adresi o bulma yönlendiriciye yanıt gider.</span><span class="sxs-lookup"><span data-stu-id="06277-113">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="06277-114">Bulma yönlendirici yanıtları toplar ve bunları istemciye geri gönderir.</span><span class="sxs-lookup"><span data-stu-id="06277-114">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="06277-115">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="06277-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="06277-116">Örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="06277-116">Build the sample.</span></span>  
  
2.  <span data-ttu-id="06277-117">DiscoveryRouter yürütülebilir dosyayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="06277-117">Run the DiscoveryRouter executable.</span></span>  
  
3.  <span data-ttu-id="06277-118">Hizmeti yürütülebilir dosyası derleme dizininden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="06277-118">Run the service executable from the build directory.</span></span>  
  
4.  <span data-ttu-id="06277-119">İstemci yürütülebilir çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="06277-119">Run the client executable.</span></span> <span data-ttu-id="06277-120">İstemci hizmeti bulur unutmayın.</span><span class="sxs-lookup"><span data-stu-id="06277-120">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="06277-121">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="06277-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="06277-122">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="06277-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="06277-123">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="06277-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="06277-124">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="06277-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
