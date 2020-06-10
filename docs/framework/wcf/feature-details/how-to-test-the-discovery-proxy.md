---
title: "Nasıl yapılır: Keşif Proxy'sini Test Etme"
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 78921d0a26f1116c87c2931b1472a161d6fed145
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592820"
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="1f955-102">Nasıl yapılır: Keşif Proxy'sini Test Etme</span><span class="sxs-lookup"><span data-stu-id="1f955-102">How to: Test the Discovery Proxy</span></span>
<span data-ttu-id="1f955-103">Bu, bulma proxy 'sinin nasıl uygulanacağını gösteren dört konulardan oluşan dördüncü bir değer.</span><span class="sxs-lookup"><span data-stu-id="1f955-103">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="1f955-104">Önceki konu başlığında [nasıl yapılır: bir hizmeti bulmak Için keşif proxy 'Si kullanan bir Istemci uygulaması](client-app-discovery-proxy-to-find-a-service.md)uygulama bir hizmet bulmak için keşif proxy 'si kullanan bir WCF istemci uygulaması uyguladıysanız ve ardından hizmeti çağırır.</span><span class="sxs-lookup"><span data-stu-id="1f955-104">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](client-app-discovery-proxy-to-find-a-service.md), you implemented a WCF client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="1f955-105">Bu konu, bulma proxy 'sinin, hizmetin ve istemci uygulamanın beklendiği gibi çalıştığını nasıl doğrulayabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="1f955-105">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="1f955-106">Keşif proxy 'sini çalıştırma</span><span class="sxs-lookup"><span data-stu-id="1f955-106">Run the Discovery Proxy</span></span>  
  
1. <span data-ttu-id="1f955-107">Yönetici olarak bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="1f955-107">Open a command prompt as an administrator.</span></span>  
  
2. <span data-ttu-id="1f955-108">Şöyle bir iletişim kutusu görebilirsiniz: Windows Güvenlik Duvarı 'nın bu programın bazı özelliklerini engellediği.</span><span class="sxs-lookup"><span data-stu-id="1f955-108">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="1f955-109">Bu iletiyi görürseniz, **Engellemeyi kaldır** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="1f955-109">If you see this message, click the **Unblock** button.</span></span>  
  
3. <span data-ttu-id="1f955-110">Komut istemi içinde, bulma proxy 'si olan DiscoveryProxy. exe ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1f955-110">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4. <span data-ttu-id="1f955-111">Uygulama şu metni görüntülemelidir: `Proxy started. Hit Enter to exit` .</span><span class="sxs-lookup"><span data-stu-id="1f955-111">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="1f955-112">Keşfedilebilir hizmeti çalıştırın</span><span class="sxs-lookup"><span data-stu-id="1f955-112">Run the Discoverable Service</span></span>  
  
1. <span data-ttu-id="1f955-113">Yönetici olarak bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="1f955-113">Open a command prompt as an administrator.</span></span>  
  
2. <span data-ttu-id="1f955-114">Komut istemi içinde Service. exe bulunabilir hizmetini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1f955-114">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3. <span data-ttu-id="1f955-115">DiscoveryProxy. exe şu metni görüntülemelidir: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span><span class="sxs-lookup"><span data-stu-id="1f955-115">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="1f955-116">Istemci uygulamasını çalıştırma</span><span class="sxs-lookup"><span data-stu-id="1f955-116">Run the Client Application</span></span>  
  
1. <span data-ttu-id="1f955-117">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="1f955-117">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="1f955-118">Komut istemi içinde Client. exe uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1f955-118">Within the command prompt, run the client.exe application.</span></span>  
  
3. <span data-ttu-id="1f955-119">Birkaç saniye sonra istemci uygulaması şu metni görüntüler: [hizmet uç noktası] bağlantısı.</span><span class="sxs-lookup"><span data-stu-id="1f955-119">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4. <span data-ttu-id="1f955-120">Service. exe ' nin ardından şu metni görüntülemesi gerekir: karşılama isteği alındı, yanıt vereceğim.</span><span class="sxs-lookup"><span data-stu-id="1f955-120">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5. <span data-ttu-id="1f955-121">Client. exe ' nin ardından şu metni görüntülemesi gerekir: Merhaba Istemci!</span><span class="sxs-lookup"><span data-stu-id="1f955-121">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="1f955-122">Uygulamaları kapatma</span><span class="sxs-lookup"><span data-stu-id="1f955-122">Shut Down the Applications</span></span>  
  
1. <span data-ttu-id="1f955-123">İstemci uygulamasını kapatın.</span><span class="sxs-lookup"><span data-stu-id="1f955-123">Shut down the client application.</span></span>  
  
2. <span data-ttu-id="1f955-124">Hizmeti kapatın.</span><span class="sxs-lookup"><span data-stu-id="1f955-124">Shut down the service.</span></span> <span data-ttu-id="1f955-125">Bulma proxy 'si şu metni görüntüler: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******` .</span><span class="sxs-lookup"><span data-stu-id="1f955-125">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3. <span data-ttu-id="1f955-126">Keşif proxy 'sini kapatın.</span><span class="sxs-lookup"><span data-stu-id="1f955-126">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f955-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f955-127">See also</span></span>

- [<span data-ttu-id="1f955-128">WCF Keşif Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1f955-128">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="1f955-129">Nasıl yapılır: Keşif Proxy'si Uygulama</span><span class="sxs-lookup"><span data-stu-id="1f955-129">How to: Implement a Discovery Proxy</span></span>](how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="1f955-130">Nasıl yapılır: Keşif Proxy'sine Kayıtlı Bir Bulunabilir Hizmet Ekleme</span><span class="sxs-lookup"><span data-stu-id="1f955-130">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="1f955-131">Nasıl yapılır: Hizmet Bulmak için Keşif Proxy'si Kullanan Bir İstemci Uygulaması Kullanma</span><span class="sxs-lookup"><span data-stu-id="1f955-131">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)
