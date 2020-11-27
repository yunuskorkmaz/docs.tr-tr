---
title: "Nasıl yapılır: Keşif Proxy'sini Test Etme"
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: b08e8561ceff9f0a427a9ea9acb2309772579853
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294670"
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="44e12-102">Nasıl yapılır: Keşif Proxy'sini Test Etme</span><span class="sxs-lookup"><span data-stu-id="44e12-102">How to: Test the Discovery Proxy</span></span>

<span data-ttu-id="44e12-103">Bu, bulma proxy 'sinin nasıl uygulanacağını gösteren dört konulardan oluşan dördüncü bir değer.</span><span class="sxs-lookup"><span data-stu-id="44e12-103">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="44e12-104">Önceki konu başlığında [nasıl yapılır: bir hizmeti bulmak Için keşif proxy 'Si kullanan bir Istemci uygulaması](client-app-discovery-proxy-to-find-a-service.md)uygulama bir hizmet bulmak için keşif proxy 'si kullanan bir WCF istemci uygulaması uyguladıysanız ve ardından hizmeti çağırır.</span><span class="sxs-lookup"><span data-stu-id="44e12-104">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](client-app-discovery-proxy-to-find-a-service.md), you implemented a WCF client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="44e12-105">Bu konu, bulma proxy 'sinin, hizmetin ve istemci uygulamanın beklendiği gibi çalıştığını nasıl doğrulayabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="44e12-105">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="44e12-106">Keşif proxy 'sini çalıştırma</span><span class="sxs-lookup"><span data-stu-id="44e12-106">Run the Discovery Proxy</span></span>  
  
1. <span data-ttu-id="44e12-107">Yönetici olarak bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="44e12-107">Open a command prompt as an administrator.</span></span>  
  
2. <span data-ttu-id="44e12-108">Şöyle bir iletişim kutusu görebilirsiniz: Windows Güvenlik Duvarı 'nın bu programın bazı özelliklerini engellediği.</span><span class="sxs-lookup"><span data-stu-id="44e12-108">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="44e12-109">Bu iletiyi görürseniz, **Engellemeyi kaldır** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="44e12-109">If you see this message, click the **Unblock** button.</span></span>  
  
3. <span data-ttu-id="44e12-110">Komut istemi içinde, DiscoveryProxy.exe bulma proxy 'sini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="44e12-110">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4. <span data-ttu-id="44e12-111">Uygulama şu metni görüntülemelidir: `Proxy started. Hit Enter to exit` .</span><span class="sxs-lookup"><span data-stu-id="44e12-111">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="44e12-112">Keşfedilebilir hizmeti çalıştırın</span><span class="sxs-lookup"><span data-stu-id="44e12-112">Run the Discoverable Service</span></span>  
  
1. <span data-ttu-id="44e12-113">Yönetici olarak bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="44e12-113">Open a command prompt as an administrator.</span></span>  
  
2. <span data-ttu-id="44e12-114">Komut istemi içinde Service.exe bulunabilir hizmeti çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="44e12-114">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3. <span data-ttu-id="44e12-115">DiscoveryProxy.exe şu metni görüntülemelidir: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span><span class="sxs-lookup"><span data-stu-id="44e12-115">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="44e12-116">Istemci uygulamasını çalıştırma</span><span class="sxs-lookup"><span data-stu-id="44e12-116">Run the Client Application</span></span>  
  
1. <span data-ttu-id="44e12-117">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="44e12-117">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="44e12-118">Komut istemi içinde client.exe uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="44e12-118">Within the command prompt, run the client.exe application.</span></span>  
  
3. <span data-ttu-id="44e12-119">Birkaç saniye sonra istemci uygulaması şu metni görüntüler: [hizmet uç noktası] bağlantısı.</span><span class="sxs-lookup"><span data-stu-id="44e12-119">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4. <span data-ttu-id="44e12-120">service.exe aşağıdaki metni görüntülemelidir: karşılama isteği alındı, yanıt vereceğim.</span><span class="sxs-lookup"><span data-stu-id="44e12-120">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5. <span data-ttu-id="44e12-121">client.exe aşağıdaki metni görüntülemelidir: Merhaba Istemci!</span><span class="sxs-lookup"><span data-stu-id="44e12-121">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="44e12-122">Uygulamaları kapatma</span><span class="sxs-lookup"><span data-stu-id="44e12-122">Shut Down the Applications</span></span>  
  
1. <span data-ttu-id="44e12-123">İstemci uygulamasını kapatın.</span><span class="sxs-lookup"><span data-stu-id="44e12-123">Shut down the client application.</span></span>  
  
2. <span data-ttu-id="44e12-124">Hizmeti kapatın.</span><span class="sxs-lookup"><span data-stu-id="44e12-124">Shut down the service.</span></span> <span data-ttu-id="44e12-125">Bulma proxy 'si şu metni görüntüler: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******` .</span><span class="sxs-lookup"><span data-stu-id="44e12-125">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3. <span data-ttu-id="44e12-126">Keşif proxy 'sini kapatın.</span><span class="sxs-lookup"><span data-stu-id="44e12-126">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44e12-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44e12-127">See also</span></span>

- [<span data-ttu-id="44e12-128">WCF Keşif Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="44e12-128">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="44e12-129">Nasıl yapılır: Keşif Proxy'si Uygulama</span><span class="sxs-lookup"><span data-stu-id="44e12-129">How to: Implement a Discovery Proxy</span></span>](how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="44e12-130">Nasıl yapılır: Keşif Proxy'sine Kayıtlı Bir Bulunabilir Hizmet Ekleme</span><span class="sxs-lookup"><span data-stu-id="44e12-130">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="44e12-131">Nasıl yapılır: Hizmet Bulmak için Keşif Proxy'si Kullanan Bir İstemci Uygulaması Kullanma</span><span class="sxs-lookup"><span data-stu-id="44e12-131">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)
