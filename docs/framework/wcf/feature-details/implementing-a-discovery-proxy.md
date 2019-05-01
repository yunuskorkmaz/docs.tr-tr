---
title: Keşif Proxy'si Ekleme
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: 5d9296d8ba70d4c9e8d8339fa3a032d9c4c62826
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047067"
---
# <a name="implementing-a-discovery-proxy"></a><span data-ttu-id="b9e6f-102">Keşif Proxy'si Ekleme</span><span class="sxs-lookup"><span data-stu-id="b9e6f-102">Implementing a Discovery Proxy</span></span>
<span data-ttu-id="b9e6f-103">Bu bölümde, Keşif proxy'si uygulama için gereken adımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b9e6f-103">This section describes the steps required to implement a discovery proxy.</span></span> <span data-ttu-id="b9e6f-104">Keşif proxy'si bir depo hizmetleri içeren tek başına bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="b9e6f-104">A discovery proxy is a standalone service that contains a repository of services.</span></span> <span data-ttu-id="b9e6f-105">İstemciler, proxy farkındadır bulunabilirlik Hizmetleri bulmak için keşif proxy'si sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="b9e6f-105">Clients can query a discovery proxy to find discoverable services that the proxy is aware of.</span></span> <span data-ttu-id="b9e6f-106">Bir ara sunucu hizmetleri ile nasıl doldurulur kadar uygulayan olur.</span><span class="sxs-lookup"><span data-stu-id="b9e6f-106">How a proxy is populated with services is up to the implementer.</span></span> <span data-ttu-id="b9e6f-107">Örneğin, Keşif proxy'si mevcut bir hizmet depoya bağlanmak ve bu bilgileri bulunabilir, yönetici yönetim API'si için bir proxy bulunabilir hizmet eklemek için kullanabilirsiniz veya keşif proxy'si duyuru işlevini kullanabilirsiniz yapın İç önbelleğini güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="b9e6f-107">For example, a discovery proxy can connect to an existing service repository and make that information discoverable, an administrator can use a management API to add discoverable services to a proxy, or a discovery proxy can use the announcement functionality to update its internal cache.</span></span>  
  
 <span data-ttu-id="b9e6f-108">WCF uygulaması, bir proxy kolayca oluşturmanıza olanak tanıyan temel sınıfları sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9e6f-108">The WCF implementation provides base classes that allow you to easily build a proxy.</span></span> <span data-ttu-id="b9e6f-109">Keşif proxy'si mevcut deponuzda üzerine oluşturmak için bu API'leri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="b9e6f-109">You can utilize these APIs to build a Discovery Proxy on top of your existing repository.</span></span>  
  
 <span data-ttu-id="b9e6f-110">Ayrıca keşif proxy'si bulunabilir olmasını sağlayın ve kendi uç bulun istemciniz burada uygulanan keşif proxy'si diğer WCF hizmetleri gibi olmamasıdır.</span><span class="sxs-lookup"><span data-stu-id="b9e6f-110">The discovery proxy implemented here is like any other WCF services, in that you can also make the discovery proxy discoverable and have the clients locate its endpoints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b9e6f-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b9e6f-111">In This Section</span></span>  
 [<span data-ttu-id="b9e6f-112">Nasıl yapılır: Keşif proxy'si uygulama</span><span class="sxs-lookup"><span data-stu-id="b9e6f-112">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 <span data-ttu-id="b9e6f-113">Keşif proxy'si uygulama açıklar.</span><span class="sxs-lookup"><span data-stu-id="b9e6f-113">Describes how to implement a discovery proxy.</span></span>  
  
 [<span data-ttu-id="b9e6f-114">Nasıl yapılır: Keşif proxy'sine bir bulunabilir hizmet ekleme</span><span class="sxs-lookup"><span data-stu-id="b9e6f-114">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 <span data-ttu-id="b9e6f-115">Keşif proxy'sine kayıtlı bir bulunabilir WCF hizmet uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b9e6f-115">Describes how to implement a discoverable WCF service that registers with the discovery proxy.</span></span>  
  
 [<span data-ttu-id="b9e6f-116">Nasıl yapılır: Bir hizmet bulmak için keşif proxy'sini kullanan bir istemci uygulama</span><span class="sxs-lookup"><span data-stu-id="b9e6f-116">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 <span data-ttu-id="b9e6f-117">Bir hizmet için aranacak keşif proxy'sini kullanan bir WCF istemci uygulamanın nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b9e6f-117">Describes how to implement a WCF client application that uses the discovery proxy to search for a service.</span></span>  
  
 [<span data-ttu-id="b9e6f-118">Nasıl yapılır: Keşif proxy'sini test etme</span><span class="sxs-lookup"><span data-stu-id="b9e6f-118">How to: Test the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 <span data-ttu-id="b9e6f-119">Önceki üç konularındaki yazılmış kodu test açıklar.</span><span class="sxs-lookup"><span data-stu-id="b9e6f-119">Describes how to test the code written in the previous three topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9e6f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9e6f-120">See also</span></span>

- [<span data-ttu-id="b9e6f-121">WCF Bulma</span><span class="sxs-lookup"><span data-stu-id="b9e6f-121">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)
- [<span data-ttu-id="b9e6f-122">Nasıl yapılır: Bir WCF hizmeti ve istemci programlı bir şekilde Keşfedilebilirlik ekleme</span><span class="sxs-lookup"><span data-stu-id="b9e6f-122">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
