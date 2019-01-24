---
title: "Nasıl yapılır: Keşif proxy'sini test etme"
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 3c159481813266386706b34d172bbf9614a8253d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590519"
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="b0eea-102">Nasıl yapılır: Keşif proxy'sini test etme</span><span class="sxs-lookup"><span data-stu-id="b0eea-102">How to: Test the Discovery Proxy</span></span>
<span data-ttu-id="b0eea-103">Keşif proxy'si uygulama gösteren dördüncü dört konuları budur.</span><span class="sxs-lookup"><span data-stu-id="b0eea-103">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="b0eea-104">Önceki konu [nasıl yapılır: Bir hizmet bulmak için keşif proxy'sini kullanan bir istemci uygulaması yürütürsünüz](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), Keşif proxy'si hizmet bulmak için kullanır ve ardından hizmeti çağıran bir WCF istemci uygulaması uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b0eea-104">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), you implemented a WCF client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="b0eea-105">Bu konu, beklendiği gibi keşif proxy'si, hizmet ve istemci uygulama iş doğrulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="b0eea-105">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="b0eea-106">Keşif proxy'si çalıştırın</span><span class="sxs-lookup"><span data-stu-id="b0eea-106">Run the Discovery Proxy</span></span>  
  
1.  <span data-ttu-id="b0eea-107">Yönetici olarak bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="b0eea-107">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="b0eea-108">Bildiren bir iletişim kutusu görebilirsiniz: Windows Güvenlik Duvarı, bazı özellikler bu programın engelledi.</span><span class="sxs-lookup"><span data-stu-id="b0eea-108">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="b0eea-109">Bu iletiyi görüyorsanız tıklayın **Engellemeyi Kaldır** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="b0eea-109">If you see this message, click the **Unblock** button.</span></span>  
  
3.  <span data-ttu-id="b0eea-110">İçinde komut isteminde, Keşif proxy'si DiscoveryProxy.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b0eea-110">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4.  <span data-ttu-id="b0eea-111">Uygulama aşağıdaki metni görüntülenmelidir: `Proxy started. Hit Enter to exit`.</span><span class="sxs-lookup"><span data-stu-id="b0eea-111">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="b0eea-112">Bulunabilir hizmet çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b0eea-112">Run the Discoverable Service</span></span>  
  
1.  <span data-ttu-id="b0eea-113">Yönetici olarak bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="b0eea-113">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="b0eea-114">İçinde komut isteminde, Service.exe bulunabilir hizmet çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b0eea-114">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3.  <span data-ttu-id="b0eea-115">Aşağıdaki metni DiscoveryProxy.exe görüntülenmelidir: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span><span class="sxs-lookup"><span data-stu-id="b0eea-115">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="b0eea-116">İstemci uygulamasını çalıştırın</span><span class="sxs-lookup"><span data-stu-id="b0eea-116">Run the Client Application</span></span>  
  
1.  <span data-ttu-id="b0eea-117">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="b0eea-117">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="b0eea-118">Komut istemi içinde client.exe uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b0eea-118">Within the command prompt, run the client.exe application.</span></span>  
  
3.  <span data-ttu-id="b0eea-119">Birkaç saniye sonra istemci uygulama, aşağıdaki metni görüntüler: [Hizmet uç noktası için] bağlanılıyor.</span><span class="sxs-lookup"><span data-stu-id="b0eea-119">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4.  <span data-ttu-id="b0eea-120">Service.exe, ardından aşağıdaki metni görüntülenmelidir: Alınan istek Karşılama, ı yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="b0eea-120">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5.  <span data-ttu-id="b0eea-121">Client.exe sonra aşağıdaki metni görüntülenir: İstemci Merhaba!</span><span class="sxs-lookup"><span data-stu-id="b0eea-121">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="b0eea-122">Uygulamaları kapatın</span><span class="sxs-lookup"><span data-stu-id="b0eea-122">Shut Down the Applications</span></span>  
  
1.  <span data-ttu-id="b0eea-123">İstemci uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="b0eea-123">Shut down the client application.</span></span>  
  
2.  <span data-ttu-id="b0eea-124">Hizmeti kapat.</span><span class="sxs-lookup"><span data-stu-id="b0eea-124">Shut down the service.</span></span> <span data-ttu-id="b0eea-125">Keşif proxy'si aşağıdaki metni görüntüler: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span><span class="sxs-lookup"><span data-stu-id="b0eea-125">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3.  <span data-ttu-id="b0eea-126">Keşif proxy'si kapatın.</span><span class="sxs-lookup"><span data-stu-id="b0eea-126">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0eea-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0eea-127">See also</span></span>
- [<span data-ttu-id="b0eea-128">WCF Bulmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b0eea-128">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="b0eea-129">Nasıl yapılır: Keşif proxy'si uygulama</span><span class="sxs-lookup"><span data-stu-id="b0eea-129">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="b0eea-130">Nasıl yapılır: Keşif proxy'sine bir bulunabilir hizmet ekleme</span><span class="sxs-lookup"><span data-stu-id="b0eea-130">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="b0eea-131">Nasıl yapılır: Bir hizmet bulmak için keşif proxy'sini kullanan bir istemci uygulama</span><span class="sxs-lookup"><span data-stu-id="b0eea-131">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
