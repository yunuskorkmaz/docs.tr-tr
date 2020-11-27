---
title: Keşif Proxy'si Ekleme
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: ae003c89bb0f14623c5d31a1596533d821380336
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268306"
---
# <a name="implementing-a-discovery-proxy"></a><span data-ttu-id="442b2-102">Keşif Proxy'si Ekleme</span><span class="sxs-lookup"><span data-stu-id="442b2-102">Implementing a Discovery Proxy</span></span>

<span data-ttu-id="442b2-103">Bu bölümde, bulma proxy 'si uygulamak için gereken adımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="442b2-103">This section describes the steps required to implement a discovery proxy.</span></span> <span data-ttu-id="442b2-104">Bulma proxy 'si, bir hizmet deposu içeren tek başına hizmettir.</span><span class="sxs-lookup"><span data-stu-id="442b2-104">A discovery proxy is a standalone service that contains a repository of services.</span></span> <span data-ttu-id="442b2-105">İstemciler, proxy 'nin farkında olduğu keşfedilebilir hizmetleri bulmak için bir keşif proxy 'sini sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="442b2-105">Clients can query a discovery proxy to find discoverable services that the proxy is aware of.</span></span> <span data-ttu-id="442b2-106">Hizmetler ile bir ara sunucu nasıl doldurulur uygulayıcısı.</span><span class="sxs-lookup"><span data-stu-id="442b2-106">How a proxy is populated with services is up to the implementer.</span></span> <span data-ttu-id="442b2-107">Örneğin, bir bulma proxy 'si var olan bir hizmet deposuna bağlanabilir ve bu bilgileri bulunabilir hale getirebilir, bir yönetici bir ara sunucuya bulunabilir Hizmetleri eklemek için bir yönetim API 'SI kullanabilir veya bir keşif proxy, iç önbelleğini güncelleştirmek için duyuru işlevini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="442b2-107">For example, a discovery proxy can connect to an existing service repository and make that information discoverable, an administrator can use a management API to add discoverable services to a proxy, or a discovery proxy can use the announcement functionality to update its internal cache.</span></span>  
  
 <span data-ttu-id="442b2-108">WCF uygulama, kolayca bir proxy oluşturmanıza izin veren temel sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="442b2-108">The WCF implementation provides base classes that allow you to easily build a proxy.</span></span> <span data-ttu-id="442b2-109">Bu API 'Leri, mevcut deponuzda bir bulma proxy 'Si oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="442b2-109">You can utilize these APIs to build a Discovery Proxy on top of your existing repository.</span></span>  
  
 <span data-ttu-id="442b2-110">Burada uygulanan bulma proxy diğer tüm WCF Hizmetleri gibidir, bu da keşif proxy 'sini bulunabilir hale getirebilir ve istemcilerin uç noktalarını bulmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="442b2-110">The discovery proxy implemented here is like any other WCF services, in that you can also make the discovery proxy discoverable and have the clients locate its endpoints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="442b2-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="442b2-111">In This Section</span></span>  

 [<span data-ttu-id="442b2-112">Nasıl yapılır: Keşif Proxy'si Uygulama</span><span class="sxs-lookup"><span data-stu-id="442b2-112">How to: Implement a Discovery Proxy</span></span>](how-to-implement-a-discovery-proxy.md)  
 <span data-ttu-id="442b2-113">Bulma proxy 'sinin nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="442b2-113">Describes how to implement a discovery proxy.</span></span>  
  
 [<span data-ttu-id="442b2-114">Nasıl yapılır: Keşif Proxy'sine Kayıtlı Bir Bulunabilir Hizmet Ekleme</span><span class="sxs-lookup"><span data-stu-id="442b2-114">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](discoverable-service-that-registers-with-the-discovery-proxy.md)  
 <span data-ttu-id="442b2-115">Bulma proxy 'sine Kaydolmakta olan keşfedilebilir WCF hizmetinin nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="442b2-115">Describes how to implement a discoverable WCF service that registers with the discovery proxy.</span></span>  
  
 [<span data-ttu-id="442b2-116">Nasıl yapılır: Hizmet Bulmak için Keşif Proxy'si Kullanan Bir İstemci Uygulaması Kullanma</span><span class="sxs-lookup"><span data-stu-id="442b2-116">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)  
 <span data-ttu-id="442b2-117">Bir hizmeti aramak için bulma proxy 'sini kullanan bir WCF istemci uygulamasının nasıl uygulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="442b2-117">Describes how to implement a WCF client application that uses the discovery proxy to search for a service.</span></span>  
  
 [<span data-ttu-id="442b2-118">Nasıl yapılır: Keşif Proxy'sini Test Etme</span><span class="sxs-lookup"><span data-stu-id="442b2-118">How to: Test the Discovery Proxy</span></span>](how-to-test-the-discovery-proxy.md)  
 <span data-ttu-id="442b2-119">Önceki üç konuda yazılan kodun nasıl test edileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="442b2-119">Describes how to test the code written in the previous three topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="442b2-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="442b2-120">See also</span></span>

- [<span data-ttu-id="442b2-121">WCF Keşfetme</span><span class="sxs-lookup"><span data-stu-id="442b2-121">WCF Discovery</span></span>](wcf-discovery.md)
- [<span data-ttu-id="442b2-122">Nasıl yapılır: Bir WCF Hizmeti ve İstemcisine Programlı Bir Şekilde Keşfedilebilirlik Ekleme</span><span class="sxs-lookup"><span data-stu-id="442b2-122">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
