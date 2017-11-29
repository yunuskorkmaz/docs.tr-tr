---
title: "Keşif Proxy'si Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5ddea7bf69f697c5b9ecd9d41021bff2407522a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-a-discovery-proxy"></a><span data-ttu-id="728c1-102">Keşif Proxy'si Ekleme</span><span class="sxs-lookup"><span data-stu-id="728c1-102">Implementing a Discovery Proxy</span></span>
<span data-ttu-id="728c1-103">Bu bölüm, Keşif proxy'si uygulamak için gereken adımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="728c1-103">This section describes the steps required to implement a discovery proxy.</span></span> <span data-ttu-id="728c1-104">Keşif proxy'si bir depo hizmetleri içeren bir tek başına hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="728c1-104">A discovery proxy is a standalone service that contains a repository of services.</span></span> <span data-ttu-id="728c1-105">İstemciler, proxy farkındadır bulunabilirlik Hizmetleri bulmak için keşif proxy'si sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="728c1-105">Clients can query a discovery proxy to find discoverable services that the proxy is aware of.</span></span> <span data-ttu-id="728c1-106">Bir proxy sunucu hizmetleri ile nasıl doldurulur kadar uygulayan olur.</span><span class="sxs-lookup"><span data-stu-id="728c1-106">How a proxy is populated with services is up to the implementer.</span></span> <span data-ttu-id="728c1-107">Örneğin, Keşif proxy'si var olan bir hizmet deposuna bağlanmak ve bu bilgileri bulunabilir, yönetici bir proxy bulunabilir hizmet eklemek için yönetim API'si kullanabilir ya da keşif proxy'si duyuru işlevselliği kullanabilirsiniz yapın İç önbelleğini güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="728c1-107">For example, a discovery proxy can connect to an existing service repository and make that information discoverable, an administrator can use a management API to add discoverable services to a proxy, or a discovery proxy can use the announcement functionality to update its internal cache.</span></span>  
  
 <span data-ttu-id="728c1-108">WCF uygulaması, bir proxy kolayca oluşturmanıza olanak tanıyan temel sınıfları sağlar.</span><span class="sxs-lookup"><span data-stu-id="728c1-108">The WCF implementation provides base classes that allow you to easily build a proxy.</span></span> <span data-ttu-id="728c1-109">Varolan deponuz üstünde keşif proxy'si oluşturmak için bu API'leri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="728c1-109">You can utilize these APIs to build a Discovery Proxy on top of your existing repository.</span></span>  
  
 <span data-ttu-id="728c1-110">Ayrıca keşif proxy'si bulunabilir yapmak ve bitiş noktaları bulun istemcilerinin burada uygulandığı keşif proxy'si diğer WCF hizmetleri gibi olmamasıdır.</span><span class="sxs-lookup"><span data-stu-id="728c1-110">The discovery proxy implemented here is like any other WCF services, in that you can also make the discovery proxy discoverable and have the clients locate its endpoints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="728c1-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="728c1-111">In This Section</span></span>  
 [<span data-ttu-id="728c1-112">Nasıl yapılır: keşif proxy'si uygulama</span><span class="sxs-lookup"><span data-stu-id="728c1-112">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 <span data-ttu-id="728c1-113">Keşif proxy'si uygulama açıklar.</span><span class="sxs-lookup"><span data-stu-id="728c1-113">Describes how to implement a discovery proxy.</span></span>  
  
 [<span data-ttu-id="728c1-114">Nasıl yapılır: keşif proxy'sine kayıtlı bir bulunabilir hizmet ekleme</span><span class="sxs-lookup"><span data-stu-id="728c1-114">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 <span data-ttu-id="728c1-115">Bir bulunabilirlik uygulamak açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] keşif proxy'sine kayıtlı hizmet.</span><span class="sxs-lookup"><span data-stu-id="728c1-115">Describes how to implement a discoverable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that registers with the discovery proxy.</span></span>  
  
 [<span data-ttu-id="728c1-116">Nasıl yapılır: hizmet bulmak için keşif proxy'si kullanan bir istemci uygulaması kullanma</span><span class="sxs-lookup"><span data-stu-id="728c1-116">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 <span data-ttu-id="728c1-117">Nasıl uygulandığı açıklanır bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aramak için bir hizmet için keşif proxy'si kullanan istemci uygulaması.</span><span class="sxs-lookup"><span data-stu-id="728c1-117">Describes how to implement a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses the discovery proxy to search for a service.</span></span>  
  
 [<span data-ttu-id="728c1-118">Nasıl yapılır: keşif proxy'sini test etme</span><span class="sxs-lookup"><span data-stu-id="728c1-118">How to: Test the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 <span data-ttu-id="728c1-119">Önceki üç konularındaki yazılmış kodun test edileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="728c1-119">Describes how to test the code written in the previous three topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="728c1-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="728c1-120">See Also</span></span>  
 [<span data-ttu-id="728c1-121">WCF keşfetme</span><span class="sxs-lookup"><span data-stu-id="728c1-121">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 [<span data-ttu-id="728c1-122">Nasıl yapılır: program aracılığıyla bir WCF hizmeti ve istemci Keşfedilebilirlik ekleme</span><span class="sxs-lookup"><span data-stu-id="728c1-122">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
