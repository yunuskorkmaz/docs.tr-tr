---
title: Keşif Proxy'si Ekleme
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: 0c7086e0eecea6cc2d7494d6afda0abf056ba758
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492225"
---
# <a name="implementing-a-discovery-proxy"></a><span data-ttu-id="73024-102">Keşif Proxy'si Ekleme</span><span class="sxs-lookup"><span data-stu-id="73024-102">Implementing a Discovery Proxy</span></span>
<span data-ttu-id="73024-103">Bu bölüm, Keşif proxy'si uygulamak için gereken adımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="73024-103">This section describes the steps required to implement a discovery proxy.</span></span> <span data-ttu-id="73024-104">Keşif proxy'si bir depo hizmetleri içeren bir tek başına hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="73024-104">A discovery proxy is a standalone service that contains a repository of services.</span></span> <span data-ttu-id="73024-105">İstemciler, proxy farkındadır bulunabilirlik Hizmetleri bulmak için keşif proxy'si sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="73024-105">Clients can query a discovery proxy to find discoverable services that the proxy is aware of.</span></span> <span data-ttu-id="73024-106">Bir proxy sunucu hizmetleri ile nasıl doldurulur kadar uygulayan olur.</span><span class="sxs-lookup"><span data-stu-id="73024-106">How a proxy is populated with services is up to the implementer.</span></span> <span data-ttu-id="73024-107">Örneğin, Keşif proxy'si var olan bir hizmet deposuna bağlanmak ve bu bilgileri bulunabilir, yönetici bir proxy bulunabilir hizmet eklemek için yönetim API'si kullanabilir ya da keşif proxy'si duyuru işlevselliği kullanabilirsiniz yapın İç önbelleğini güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="73024-107">For example, a discovery proxy can connect to an existing service repository and make that information discoverable, an administrator can use a management API to add discoverable services to a proxy, or a discovery proxy can use the announcement functionality to update its internal cache.</span></span>  
  
 <span data-ttu-id="73024-108">WCF uygulaması, bir proxy kolayca oluşturmanıza olanak tanıyan temel sınıfları sağlar.</span><span class="sxs-lookup"><span data-stu-id="73024-108">The WCF implementation provides base classes that allow you to easily build a proxy.</span></span> <span data-ttu-id="73024-109">Varolan deponuz üstünde keşif proxy'si oluşturmak için bu API'leri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="73024-109">You can utilize these APIs to build a Discovery Proxy on top of your existing repository.</span></span>  
  
 <span data-ttu-id="73024-110">Ayrıca keşif proxy'si bulunabilir yapmak ve bitiş noktaları bulun istemcilerinin burada uygulandığı keşif proxy'si diğer WCF hizmetleri gibi olmamasıdır.</span><span class="sxs-lookup"><span data-stu-id="73024-110">The discovery proxy implemented here is like any other WCF services, in that you can also make the discovery proxy discoverable and have the clients locate its endpoints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="73024-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="73024-111">In This Section</span></span>  
 [<span data-ttu-id="73024-112">Nasıl yapılır: Keşif Proxy'si Uygulama</span><span class="sxs-lookup"><span data-stu-id="73024-112">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 <span data-ttu-id="73024-113">Keşif proxy'si uygulama açıklar.</span><span class="sxs-lookup"><span data-stu-id="73024-113">Describes how to implement a discovery proxy.</span></span>  
  
 [<span data-ttu-id="73024-114">Nasıl yapılır: Keşif Proxy'sine Kayıtlı Bir Bulunabilir Hizmet Ekleme</span><span class="sxs-lookup"><span data-stu-id="73024-114">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 <span data-ttu-id="73024-115">Keşif proxy'sine kayıtlı bir bulunabilir WCF hizmet uygulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="73024-115">Describes how to implement a discoverable WCF service that registers with the discovery proxy.</span></span>  
  
 [<span data-ttu-id="73024-116">Nasıl yapılır: Hizmet Bulmak için Keşif Proxy'si Kullanan Bir İstemci Uygulaması Kullanma</span><span class="sxs-lookup"><span data-stu-id="73024-116">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 <span data-ttu-id="73024-117">Bir hizmet için aramak için keşif proxy'si kullanan bir WCF istemci uygulamasını gerçekleştirme açıklar.</span><span class="sxs-lookup"><span data-stu-id="73024-117">Describes how to implement a WCF client application that uses the discovery proxy to search for a service.</span></span>  
  
 [<span data-ttu-id="73024-118">Nasıl yapılır: Keşif Proxy'sini Test Etme</span><span class="sxs-lookup"><span data-stu-id="73024-118">How to: Test the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 <span data-ttu-id="73024-119">Önceki üç konularındaki yazılmış kodun test edileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="73024-119">Describes how to test the code written in the previous three topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73024-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="73024-120">See Also</span></span>  
 [<span data-ttu-id="73024-121">WCF Bulma</span><span class="sxs-lookup"><span data-stu-id="73024-121">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 [<span data-ttu-id="73024-122">Nasıl yapılır: Bir WCF Hizmeti ve İstemcisine Programlı Bir Şekilde Keşfedilebilirlik Ekleme</span><span class="sxs-lookup"><span data-stu-id="73024-122">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
