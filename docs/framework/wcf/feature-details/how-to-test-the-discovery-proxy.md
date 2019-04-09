---
title: "Nasıl yapılır: Keşif Proxy'sini Test Etme"
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 13d2e8ca46e634e3b27c8eb967d89d860df1c72d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176286"
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="a86b8-102">Nasıl yapılır: Keşif Proxy'sini Test Etme</span><span class="sxs-lookup"><span data-stu-id="a86b8-102">How to: Test the Discovery Proxy</span></span>
<span data-ttu-id="a86b8-103">Keşif proxy'si uygulama gösteren dördüncü dört konuları budur.</span><span class="sxs-lookup"><span data-stu-id="a86b8-103">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="a86b8-104">Önceki konu [nasıl yapılır: Bir hizmet bulmak için keşif proxy'sini kullanan bir istemci uygulaması yürütürsünüz](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), Keşif proxy'si hizmet bulmak için kullanır ve ardından hizmeti çağıran bir WCF istemci uygulaması uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a86b8-104">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), you implemented a WCF client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="a86b8-105">Bu konu, beklendiği gibi keşif proxy'si, hizmet ve istemci uygulama iş doğrulamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="a86b8-105">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="a86b8-106">Keşif proxy'si çalıştırın</span><span class="sxs-lookup"><span data-stu-id="a86b8-106">Run the Discovery Proxy</span></span>  
  
1.  <span data-ttu-id="a86b8-107">Yönetici olarak bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="a86b8-107">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="a86b8-108">Bildiren bir iletişim kutusu görebilirsiniz: Windows Güvenlik Duvarı, bazı özellikler bu programın engelledi.</span><span class="sxs-lookup"><span data-stu-id="a86b8-108">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="a86b8-109">Bu iletiyi görüyorsanız tıklayın **Engellemeyi Kaldır** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a86b8-109">If you see this message, click the **Unblock** button.</span></span>  
  
3.  <span data-ttu-id="a86b8-110">İçinde komut isteminde, Keşif proxy'si DiscoveryProxy.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a86b8-110">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4.  <span data-ttu-id="a86b8-111">Uygulama aşağıdaki metni görüntülenmelidir: `Proxy started. Hit Enter to exit`.</span><span class="sxs-lookup"><span data-stu-id="a86b8-111">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="a86b8-112">Bulunabilir hizmet çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a86b8-112">Run the Discoverable Service</span></span>  
  
1.  <span data-ttu-id="a86b8-113">Yönetici olarak bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="a86b8-113">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="a86b8-114">İçinde komut isteminde, Service.exe bulunabilir hizmet çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a86b8-114">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3.  <span data-ttu-id="a86b8-115">Aşağıdaki metni DiscoveryProxy.exe görüntülenmelidir: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span><span class="sxs-lookup"><span data-stu-id="a86b8-115">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="a86b8-116">İstemci uygulamasını çalıştırın</span><span class="sxs-lookup"><span data-stu-id="a86b8-116">Run the Client Application</span></span>  
  
1.  <span data-ttu-id="a86b8-117">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="a86b8-117">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="a86b8-118">Komut istemi içinde client.exe uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a86b8-118">Within the command prompt, run the client.exe application.</span></span>  
  
3.  <span data-ttu-id="a86b8-119">Birkaç saniye sonra istemci uygulama, aşağıdaki metni görüntüler: [Hizmet uç noktası için] bağlanılıyor.</span><span class="sxs-lookup"><span data-stu-id="a86b8-119">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4.  <span data-ttu-id="a86b8-120">Service.exe, ardından aşağıdaki metni görüntülenmelidir: Alınan istek Karşılama, ı yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="a86b8-120">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5.  <span data-ttu-id="a86b8-121">Client.exe sonra aşağıdaki metni görüntülenir: İstemci Merhaba!</span><span class="sxs-lookup"><span data-stu-id="a86b8-121">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="a86b8-122">Uygulamaları kapatın</span><span class="sxs-lookup"><span data-stu-id="a86b8-122">Shut Down the Applications</span></span>  
  
1.  <span data-ttu-id="a86b8-123">İstemci uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="a86b8-123">Shut down the client application.</span></span>  
  
2.  <span data-ttu-id="a86b8-124">Hizmeti kapat.</span><span class="sxs-lookup"><span data-stu-id="a86b8-124">Shut down the service.</span></span> <span data-ttu-id="a86b8-125">Keşif proxy'si aşağıdaki metni görüntüler: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span><span class="sxs-lookup"><span data-stu-id="a86b8-125">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3.  <span data-ttu-id="a86b8-126">Keşif proxy'si kapatın.</span><span class="sxs-lookup"><span data-stu-id="a86b8-126">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a86b8-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a86b8-127">See also</span></span>

- [<span data-ttu-id="a86b8-128">WCF Keşif Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a86b8-128">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="a86b8-129">Nasıl yapılır: Keşif Proxy'si Uygulama</span><span class="sxs-lookup"><span data-stu-id="a86b8-129">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="a86b8-130">Nasıl yapılır: Keşif Proxy'sine Kayıtlı Bir Bulunabilir Hizmet Ekleme</span><span class="sxs-lookup"><span data-stu-id="a86b8-130">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="a86b8-131">Nasıl yapılır: Hizmet Bulmak için Keşif Proxy'si Kullanan Bir İstemci Uygulaması Kullanma</span><span class="sxs-lookup"><span data-stu-id="a86b8-131">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
