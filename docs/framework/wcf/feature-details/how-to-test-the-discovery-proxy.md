---
title: "Nasıl yapılır: Keşif Proxy'sini Test Etme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55a7fe72b34fc8c099d921e7e295c184817825a3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="d3a7a-102">Nasıl yapılır: Keşif Proxy'sini Test Etme</span><span class="sxs-lookup"><span data-stu-id="d3a7a-102">How to: Test the Discovery Proxy</span></span>
<span data-ttu-id="d3a7a-103">Keşif proxy'si uygulama gösteren dördüncü dört konuların budur.</span><span class="sxs-lookup"><span data-stu-id="d3a7a-103">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="d3a7a-104">Önceki konusunda [nasıl yapılır: hizmet bulmak için keşif proxy'si kullanan bir istemci uygulaması yürütürsünüz](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), uygulanan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet bulmak için keşif proxy'si kullanan ve daha sonra çağırır istemci uygulaması hizmet.</span><span class="sxs-lookup"><span data-stu-id="d3a7a-104">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), you implemented a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="d3a7a-105">Bu konu, Keşif proxy'si, hizmet ve istemci uygulaması iş beklendiği gibi doğrulayın açıklar.</span><span class="sxs-lookup"><span data-stu-id="d3a7a-105">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="d3a7a-106">Keşif proxy'si çalıştırın</span><span class="sxs-lookup"><span data-stu-id="d3a7a-106">Run the Discovery Proxy</span></span>  
  
1.  <span data-ttu-id="d3a7a-107">Komut istemini yönetici olarak açın.</span><span class="sxs-lookup"><span data-stu-id="d3a7a-107">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="d3a7a-108">Bildiren bir iletişim kutusu görebilirsiniz: Windows Güvenlik Duvarı, bu programın bazı özellikler engelledi.</span><span class="sxs-lookup"><span data-stu-id="d3a7a-108">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="d3a7a-109">Bu iletiyi görürseniz, tıklatın **Engellemeyi Kaldır** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="d3a7a-109">If you see this message, click the **Unblock** button.</span></span>  
  
3.  <span data-ttu-id="d3a7a-110">Komut istemi içinde keşif proxy'si, DiscoveryProxy.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d3a7a-110">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4.  <span data-ttu-id="d3a7a-111">Uygulama aşağıdaki metni görüntülenmelidir: `Proxy started. Hit Enter to exit`.</span><span class="sxs-lookup"><span data-stu-id="d3a7a-111">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="d3a7a-112">Bulunabilir hizmet çalıştırın</span><span class="sxs-lookup"><span data-stu-id="d3a7a-112">Run the Discoverable Service</span></span>  
  
1.  <span data-ttu-id="d3a7a-113">Komut istemini yönetici olarak açın.</span><span class="sxs-lookup"><span data-stu-id="d3a7a-113">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="d3a7a-114">Komut istemi içinde Service.exe bulunabilir hizmet çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d3a7a-114">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3.  <span data-ttu-id="d3a7a-115">Aşağıdaki metni DiscoveryProxy.exe görüntülenmelidir: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span><span class="sxs-lookup"><span data-stu-id="d3a7a-115">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="d3a7a-116">İstemci uygulaması çalıştırın</span><span class="sxs-lookup"><span data-stu-id="d3a7a-116">Run the Client Application</span></span>  
  
1.  <span data-ttu-id="d3a7a-117">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="d3a7a-117">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="d3a7a-118">Komut istemi içinde client.exe uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d3a7a-118">Within the command prompt, run the client.exe application.</span></span>  
  
3.  <span data-ttu-id="d3a7a-119">Birkaç saniye sonra istemci uygulaması aşağıdaki metni görüntüler: [hizmet uç noktası] bağlanma.</span><span class="sxs-lookup"><span data-stu-id="d3a7a-119">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4.  <span data-ttu-id="d3a7a-120">Service.exe sonra aşağıdaki metni görüntülenmelidir: isteği alındı selamlama, ı yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="d3a7a-120">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5.  <span data-ttu-id="d3a7a-121">Client.exe sonra aşağıdaki metni görüntülenmelidir: Hello istemci!</span><span class="sxs-lookup"><span data-stu-id="d3a7a-121">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="d3a7a-122">Uygulamaları kapatın</span><span class="sxs-lookup"><span data-stu-id="d3a7a-122">Shut Down the Applications</span></span>  
  
1.  <span data-ttu-id="d3a7a-123">İstemci uygulamasını kapatın.</span><span class="sxs-lookup"><span data-stu-id="d3a7a-123">Shut down the client application.</span></span>  
  
2.  <span data-ttu-id="d3a7a-124">Hizmetini kapatın.</span><span class="sxs-lookup"><span data-stu-id="d3a7a-124">Shut down the service.</span></span> <span data-ttu-id="d3a7a-125">Aşağıdaki metin keşif proxy'si görüntüler: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span><span class="sxs-lookup"><span data-stu-id="d3a7a-125">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3.  <span data-ttu-id="d3a7a-126">Keşif proxy'si kapatın.</span><span class="sxs-lookup"><span data-stu-id="d3a7a-126">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3a7a-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d3a7a-127">See Also</span></span>  
 [<span data-ttu-id="d3a7a-128">WCF keşif genel bakış</span><span class="sxs-lookup"><span data-stu-id="d3a7a-128">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="d3a7a-129">Nasıl yapılır: keşif proxy'si uygulama</span><span class="sxs-lookup"><span data-stu-id="d3a7a-129">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [<span data-ttu-id="d3a7a-130">Nasıl yapılır: keşif proxy'sine kayıtlı bir bulunabilir hizmet ekleme</span><span class="sxs-lookup"><span data-stu-id="d3a7a-130">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 [<span data-ttu-id="d3a7a-131">Nasıl yapılır: hizmet bulmak için keşif proxy'si kullanan bir istemci uygulaması kullanma</span><span class="sxs-lookup"><span data-stu-id="d3a7a-131">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
