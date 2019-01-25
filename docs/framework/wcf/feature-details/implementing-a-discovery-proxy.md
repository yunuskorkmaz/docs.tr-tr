---
title: Keşif Proxy'si Ekleme
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: f2f687912b966b03c17206f369b46ffd28d019d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634525"
---
# <a name="implementing-a-discovery-proxy"></a><span data-ttu-id="8a401-102">Keşif Proxy'si Ekleme</span><span class="sxs-lookup"><span data-stu-id="8a401-102">Implementing a Discovery Proxy</span></span>
<span data-ttu-id="8a401-103">Bu bölümde, Keşif proxy'si uygulama için gereken adımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8a401-103">This section describes the steps required to implement a discovery proxy.</span></span> <span data-ttu-id="8a401-104">Keşif proxy'si bir depo hizmetleri içeren tek başına bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="8a401-104">A discovery proxy is a standalone service that contains a repository of services.</span></span> <span data-ttu-id="8a401-105">İstemciler, proxy farkındadır bulunabilirlik Hizmetleri bulmak için keşif proxy'si sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="8a401-105">Clients can query a discovery proxy to find discoverable services that the proxy is aware of.</span></span> <span data-ttu-id="8a401-106">Bir ara sunucu hizmetleri ile nasıl doldurulur kadar uygulayan olur.</span><span class="sxs-lookup"><span data-stu-id="8a401-106">How a proxy is populated with services is up to the implementer.</span></span> <span data-ttu-id="8a401-107">Örneğin, Keşif proxy'si mevcut bir hizmet depoya bağlanmak ve bu bilgileri bulunabilir, yönetici yönetim API'si için bir proxy bulunabilir hizmet eklemek için kullanabilirsiniz veya keşif proxy'si duyuru işlevini kullanabilirsiniz yapın İç önbelleğini güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="8a401-107">For example, a discovery proxy can connect to an existing service repository and make that information discoverable, an administrator can use a management API to add discoverable services to a proxy, or a discovery proxy can use the announcement functionality to update its internal cache.</span></span>  
  
 <span data-ttu-id="8a401-108">WCF uygulaması, bir proxy kolayca oluşturmanıza olanak tanıyan temel sınıfları sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a401-108">The WCF implementation provides base classes that allow you to easily build a proxy.</span></span> <span data-ttu-id="8a401-109">Keşif proxy'si mevcut deponuzda üzerine oluşturmak için bu API'leri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8a401-109">You can utilize these APIs to build a Discovery Proxy on top of your existing repository.</span></span>  
  
 <span data-ttu-id="8a401-110">Ayrıca keşif proxy'si bulunabilir olmasını sağlayın ve kendi uç bulun istemciniz burada uygulanan keşif proxy'si diğer WCF hizmetleri gibi olmamasıdır.</span><span class="sxs-lookup"><span data-stu-id="8a401-110">The discovery proxy implemented here is like any other WCF services, in that you can also make the discovery proxy discoverable and have the clients locate its endpoints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8a401-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8a401-111">In This Section</span></span>  
 [<span data-ttu-id="8a401-112">Nasıl yapılır: Keşif proxy'si uygulama</span><span class="sxs-lookup"><span data-stu-id="8a401-112">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 <span data-ttu-id="8a401-113">Keşif proxy'si uygulama açıklar.</span><span class="sxs-lookup"><span data-stu-id="8a401-113">Describes how to implement a discovery proxy.</span></span>  
  
 [<span data-ttu-id="8a401-114">Nasıl yapılır: Keşif proxy'sine bir bulunabilir hizmet ekleme</span><span class="sxs-lookup"><span data-stu-id="8a401-114">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 <span data-ttu-id="8a401-115">Keşif proxy'sine kayıtlı bir bulunabilir WCF hizmet uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8a401-115">Describes how to implement a discoverable WCF service that registers with the discovery proxy.</span></span>  
  
 [<span data-ttu-id="8a401-116">Nasıl yapılır: Bir hizmet bulmak için keşif proxy'sini kullanan bir istemci uygulama</span><span class="sxs-lookup"><span data-stu-id="8a401-116">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 <span data-ttu-id="8a401-117">Bir hizmet için aranacak keşif proxy'sini kullanan bir WCF istemci uygulamanın nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8a401-117">Describes how to implement a WCF client application that uses the discovery proxy to search for a service.</span></span>  
  
 [<span data-ttu-id="8a401-118">Nasıl yapılır: Keşif proxy'sini test etme</span><span class="sxs-lookup"><span data-stu-id="8a401-118">How to: Test the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 <span data-ttu-id="8a401-119">Önceki üç konularındaki yazılmış kodu test açıklar.</span><span class="sxs-lookup"><span data-stu-id="8a401-119">Describes how to test the code written in the previous three topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a401-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a401-120">See also</span></span>
- [<span data-ttu-id="8a401-121">WCF Bulma</span><span class="sxs-lookup"><span data-stu-id="8a401-121">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)
- [<span data-ttu-id="8a401-122">Nasıl yapılır: Bir WCF hizmeti ve istemci programlı bir şekilde Keşfedilebilirlik ekleme</span><span class="sxs-lookup"><span data-stu-id="8a401-122">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
