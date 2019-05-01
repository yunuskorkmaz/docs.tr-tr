---
title: "Nasıl yapılır: Keşif Proxy'sini Test Etme"
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 856b86241299585b80d58c6d37582463736a5935
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972919"
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="36b58-102">Nasıl yapılır: Keşif Proxy'sini Test Etme</span><span class="sxs-lookup"><span data-stu-id="36b58-102">How to: Test the Discovery Proxy</span></span>
<span data-ttu-id="36b58-103">Keşif proxy'si uygulama gösteren dördüncü dört konuları budur.</span><span class="sxs-lookup"><span data-stu-id="36b58-103">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="36b58-104">Önceki konu [nasıl yapılır: Bir hizmet bulmak için keşif proxy'sini kullanan bir istemci uygulaması yürütürsünüz](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), Keşif proxy'si hizmet bulmak için kullanır ve ardından hizmeti çağıran bir WCF istemci uygulaması uygulanır.</span><span class="sxs-lookup"><span data-stu-id="36b58-104">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), you implemented a WCF client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="36b58-105">Bu konu, beklendiği gibi keşif proxy'si, hizmet ve istemci uygulama iş doğrulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="36b58-105">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="36b58-106">Keşif proxy'si çalıştırın</span><span class="sxs-lookup"><span data-stu-id="36b58-106">Run the Discovery Proxy</span></span>  
  
1. <span data-ttu-id="36b58-107">Yönetici olarak bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="36b58-107">Open a command prompt as an administrator.</span></span>  
  
2. <span data-ttu-id="36b58-108">Bildiren bir iletişim kutusu görebilirsiniz: Windows Güvenlik Duvarı, bazı özellikler bu programın engelledi.</span><span class="sxs-lookup"><span data-stu-id="36b58-108">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="36b58-109">Bu iletiyi görüyorsanız tıklayın **Engellemeyi Kaldır** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="36b58-109">If you see this message, click the **Unblock** button.</span></span>  
  
3. <span data-ttu-id="36b58-110">İçinde komut isteminde, Keşif proxy'si DiscoveryProxy.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="36b58-110">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4. <span data-ttu-id="36b58-111">Uygulama aşağıdaki metni görüntülenmelidir: `Proxy started. Hit Enter to exit`.</span><span class="sxs-lookup"><span data-stu-id="36b58-111">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="36b58-112">Bulunabilir hizmet çalıştırma</span><span class="sxs-lookup"><span data-stu-id="36b58-112">Run the Discoverable Service</span></span>  
  
1. <span data-ttu-id="36b58-113">Yönetici olarak bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="36b58-113">Open a command prompt as an administrator.</span></span>  
  
2. <span data-ttu-id="36b58-114">İçinde komut isteminde, Service.exe bulunabilir hizmet çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="36b58-114">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3. <span data-ttu-id="36b58-115">Aşağıdaki metni DiscoveryProxy.exe görüntülenmelidir: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span><span class="sxs-lookup"><span data-stu-id="36b58-115">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="36b58-116">İstemci uygulamasını çalıştırın</span><span class="sxs-lookup"><span data-stu-id="36b58-116">Run the Client Application</span></span>  
  
1. <span data-ttu-id="36b58-117">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="36b58-117">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="36b58-118">Komut istemi içinde client.exe uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="36b58-118">Within the command prompt, run the client.exe application.</span></span>  
  
3. <span data-ttu-id="36b58-119">Birkaç saniye sonra istemci uygulama, aşağıdaki metni görüntüler: [Hizmet uç noktası için] bağlanılıyor.</span><span class="sxs-lookup"><span data-stu-id="36b58-119">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4. <span data-ttu-id="36b58-120">Service.exe, ardından aşağıdaki metni görüntülenmelidir: Alınan istek Karşılama, ı yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="36b58-120">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5. <span data-ttu-id="36b58-121">Client.exe sonra aşağıdaki metni görüntülenir: İstemci Merhaba!</span><span class="sxs-lookup"><span data-stu-id="36b58-121">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="36b58-122">Uygulamaları kapatın</span><span class="sxs-lookup"><span data-stu-id="36b58-122">Shut Down the Applications</span></span>  
  
1. <span data-ttu-id="36b58-123">İstemci uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="36b58-123">Shut down the client application.</span></span>  
  
2. <span data-ttu-id="36b58-124">Hizmeti kapat.</span><span class="sxs-lookup"><span data-stu-id="36b58-124">Shut down the service.</span></span> <span data-ttu-id="36b58-125">Keşif proxy'si aşağıdaki metni görüntüler: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span><span class="sxs-lookup"><span data-stu-id="36b58-125">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3. <span data-ttu-id="36b58-126">Keşif proxy'si kapatın.</span><span class="sxs-lookup"><span data-stu-id="36b58-126">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36b58-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36b58-127">See also</span></span>

- [<span data-ttu-id="36b58-128">WCF Bulmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="36b58-128">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="36b58-129">Nasıl yapılır: Keşif proxy'si uygulama</span><span class="sxs-lookup"><span data-stu-id="36b58-129">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="36b58-130">Nasıl yapılır: Keşif proxy'sine bir bulunabilir hizmet ekleme</span><span class="sxs-lookup"><span data-stu-id="36b58-130">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="36b58-131">Nasıl yapılır: Bir hizmet bulmak için keşif proxy'sini kullanan bir istemci uygulama</span><span class="sxs-lookup"><span data-stu-id="36b58-131">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
