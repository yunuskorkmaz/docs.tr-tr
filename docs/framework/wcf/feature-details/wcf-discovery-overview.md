---
title: WCF Keşif Genel Bakış
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c0ac6cec6a86b431d71534880f1a883d648c4332
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="wcf-discovery-overview"></a><span data-ttu-id="5fd90-102">WCF Keşif Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5fd90-102">WCF Discovery Overview</span></span>
<span data-ttu-id="5fd90-103">Bulma API'ları dinamik yayını ve bulma WS bulma protokolünü kullanarak bir Web Hizmetleri için birleşik bir programlama modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fd90-103">The Discovery APIs provide a unified programming model for the dynamic publication and discovery of Web services using the WS-Discovery protocol.</span></span> <span data-ttu-id="5fd90-104">Bu API'leri kendilerini ve yayımlanan hizmetleri bulmak için istemcileri yayımlamak hizmetler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fd90-104">These APIs allow services to publish themselves and clients to find published services.</span></span> <span data-ttu-id="5fd90-105">Bir hizmet bulunabilirlik sağlandıktan sonra hizmet duyuru iletileri gönderme yanı sıra dinler ve bulma isteklerine yanıt özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-105">Once a service is made discoverable, the service has the ability to send announcement messages as well as listen for and respond to discovery requests.</span></span> <span data-ttu-id="5fd90-106">Bulunabilirlik Hizmetleri Ağ üzerinde kendi varış duyurmaktan Merhaba iletileri ve bunların ayrılma ağdan duyurmaktan Bye iletileri gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-106">Discoverable services can send Hello messages to announce their arrival on a network and Bye messages to announce their departure from a network.</span></span> <span data-ttu-id="5fd90-107">Bir hizmet bulmak için istemcilerin gönderdiği bir `Probe` hizmet sözleşmesi türü, anahtar sözcükleri ve ağ üzerindeki kapsamı gibi belirli bir ölçüte içeren isteği.</span><span class="sxs-lookup"><span data-stu-id="5fd90-107">To find a service, clients send a `Probe` request that contains specific criteria such as service contract type, keywords, and scope on the network.</span></span> <span data-ttu-id="5fd90-108">Hizmetleri almak `Probe` istemek ve ölçütlerle eşleştiğini belirlemek.</span><span class="sxs-lookup"><span data-stu-id="5fd90-108">Services receive the `Probe` request and determine whether they match the criteria.</span></span> <span data-ttu-id="5fd90-109">Bir hizmet eşleşirse, göndererek yanıt bir `ProbeMatch` hizmetiyle iletişim için gereken bilgiler ile istemciye ileti.</span><span class="sxs-lookup"><span data-stu-id="5fd90-109">If a service matches, it responds by sending a `ProbeMatch` message back to the client with the information necessary to contact the service.</span></span> <span data-ttu-id="5fd90-110">İstemcileri de gönderebilirler `Resolve` bunları kendi uç noktası adresi değişmiş olabilir Hizmetleri bulmak izin istekleri.</span><span class="sxs-lookup"><span data-stu-id="5fd90-110">Clients can also send `Resolve` requests that allow them to find services that may have changed their endpoint address.</span></span> <span data-ttu-id="5fd90-111">Eşleşen Hizmetleri yanıt için `Resolve` göndererek isteklerini bir `ResolveMatch` istemciye ileti.</span><span class="sxs-lookup"><span data-stu-id="5fd90-111">Matching services respond to `Resolve` requests by sending a `ResolveMatch` message back to the client.</span></span>  
  
## <a name="ad-hoc-and-managed-modes"></a><span data-ttu-id="5fd90-112">Geçici ve yönetilen modları</span><span class="sxs-lookup"><span data-stu-id="5fd90-112">Ad-Hoc and Managed Modes</span></span>  
 <span data-ttu-id="5fd90-113">Bulma APİ'si iki farklı modlarını destekler: yönetilen ve geçici.</span><span class="sxs-lookup"><span data-stu-id="5fd90-113">The Discovery API supports two different modes: Managed and Ad-Hoc.</span></span> <span data-ttu-id="5fd90-114">Yönetilen modunda kullanılabilir hizmetler hakkında bilgileri tutan keşif proxy'si olarak adlandırılan bir merkezi sunucu yok.</span><span class="sxs-lookup"><span data-stu-id="5fd90-114">In Managed mode there is a centralized server called a discovery proxy that maintains information about available services.</span></span> <span data-ttu-id="5fd90-115">Keşif proxy'si çeşitli şekillerde hizmetleri hakkında bilgi ile doldurulabilir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-115">The discovery proxy can be populated with information about services in a variety of ways.</span></span> <span data-ttu-id="5fd90-116">Örneğin, hizmetleri keşif proxy'si kadar başlangıç sırasında duyuru iletiler gönderebilir veya bir veritabanı ya da hangi hizmetlerin kullanılabilir olduğunu belirlemek için bir yapılandırma dosyasını proxy veri okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fd90-116">For example, services can send announcement messages during start up to the discovery proxy or the proxy may read data from a database or a configuration file to determine what services are available.</span></span> <span data-ttu-id="5fd90-117">Keşif proxy'si nasıl doldurulur tamamen kadar geliştiricisi değildir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-117">How the discovery proxy is populated is completely up to the developer.</span></span> <span data-ttu-id="5fd90-118">İstemciler kullanılabilir hizmetler hakkında bilgi almak için keşif proxy'si kullanın.</span><span class="sxs-lookup"><span data-stu-id="5fd90-118">Clients use the discovery proxy to retrieve information about available services.</span></span> <span data-ttu-id="5fd90-119">Ne zaman bir istemci arar bir hizmet için bu gönderir bir `Probe` keşif proxy'si ve proxy iletiye belirler bilir hakkında hizmetlerden herhangi biri için istemci arama hizmeti eşleşip eşleşmediğini.</span><span class="sxs-lookup"><span data-stu-id="5fd90-119">When a client searches for a service it sends a `Probe` message to the discovery proxy and the proxy determines whether any of the services it knows about match the service the client is searching for.</span></span> <span data-ttu-id="5fd90-120">Keşif proxy gönderir eşleşme varsa bir `ProbeMatch` istemcisine geri yanıt.</span><span class="sxs-lookup"><span data-stu-id="5fd90-120">If there are matches the discovery proxy sends a `ProbeMatch` response back to the client.</span></span> <span data-ttu-id="5fd90-121">İstemci ardından kullanarak doğrudan proxy sunucudan döndürülen hizmet bilgileri hizmet başvurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fd90-121">The client can then contact the service directly using the service information returned from the proxy.</span></span> <span data-ttu-id="5fd90-122">Anahtar yönetilen modu arkasında bulma istekleri bir yetkilisi, Keşif proxy'si için bir tek noktaya yayın şekilde gönderilir ilkesidir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-122">The key principle behind Managed mode is that the discovery requests are sent in a unicast manner to one authority, the discovery proxy.</span></span> <span data-ttu-id="5fd90-123">.NET Framework kendi proxy oluşturmanıza olanak sağlayan anahtar bileşenleri içerir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-123">The .NET Framework contains key components that allow you to build your own proxy.</span></span> <span data-ttu-id="5fd90-124">İstemcileri ve Hizmetleri proxy birden çok yöntemlerle bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5fd90-124">Clients and services can locate the proxy by multiple methods:</span></span>  
  
-   <span data-ttu-id="5fd90-125">Proxy geçici iletilere yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-125">The proxy can respond to ad-hoc messages.</span></span>  
  
-   <span data-ttu-id="5fd90-126">Proxy bir duyuru iletisi başlatma sırasında gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fd90-126">The proxy can send an announcement message during start up.</span></span>  
  
-   <span data-ttu-id="5fd90-127">İstemciler ve hizmetler için belirli bir iyi bilinen uç aramak için yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-127">Clients and services can be written to look for a specific well-known endpoint.</span></span>  
  
 <span data-ttu-id="5fd90-128">Geçici modunda merkezi sunucusu yok.</span><span class="sxs-lookup"><span data-stu-id="5fd90-128">In Ad-Hoc mode, there is no centralized server.</span></span> <span data-ttu-id="5fd90-129">Tüm bulma iletileri hizmet duyuruları ve istemci istekleri gibi bir çok noktaya yayın şekilde gönderilir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-129">All discovery messages such as service announcements and client requests are sent in a multicast fashion.</span></span> <span data-ttu-id="5fd90-130">Varsayılan olarak .NET Framework UDP protokolü üzerinden geçici bulma için destek içerir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-130">By default the .NET Framework contains support for Ad-Hoc discovery over the UDP protocol.</span></span> <span data-ttu-id="5fd90-131">Bir hizmeti başlatma üzerinde Hello duyuru göndermek için yapılandırılmışsa, örneğin, bunu, UDP protokolünü kullanarak bir iyi bilinen, çok noktaya yayın adresi gönderir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-131">For example, if a service is configured to send out a Hello announcement on start up, it sends it out over a well-known, multicast address using the UDP protocol.</span></span> <span data-ttu-id="5fd90-132">İstemcilerini etkin şekilde bu duyuruları için dinleme ve buna göre işlem gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5fd90-132">Clients have to actively listen for these announcements and process them accordingly.</span></span> <span data-ttu-id="5fd90-133">Bir istemci gönderdiğinde bir `Probe` ileti bir hizmet için çok noktaya yayın protokolü kullanarak ağ üzerinden gönderilir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-133">When a client sends a `Probe` message for a service it is sent over the network using a multicast protocol.</span></span> <span data-ttu-id="5fd90-134">İsteği alır her hizmet ölçütler eşleşip eşleşmediğini belirler `Probe` iletisi ve istemci ile doğrudan yanıtlaması bir `ProbeMatch` hizmet belirtilen ölçütlere uyuyorsa ileti `Probe` ileti.</span><span class="sxs-lookup"><span data-stu-id="5fd90-134">Each service that receives the request determines whether it matches the criteria in the `Probe` message and responds directly to the client with a `ProbeMatch` message if the service matches the criteria specified in the `Probe` message.</span></span>  
  
## <a name="benefits-of-using-wcf-discovery"></a><span data-ttu-id="5fd90-135">WCF keşif kullanmanın yararları</span><span class="sxs-lookup"><span data-stu-id="5fd90-135">Benefits of Using WCF Discovery</span></span>  
 <span data-ttu-id="5fd90-136">WCF keşif WS bulma protokolünü kullanılarak uygulanan çünkü diğer istemciler, hizmetleri ve WS-bulma de uygulama proxy'si ile birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-136">Because WCF Discovery is implemented using the WS-Discovery protocol it is interoperable with other clients, services, and proxies that implement WS-Discovery as well.</span></span> <span data-ttu-id="5fd90-137">WCF keşif bulma işlevselliği, mevcut hizmetler ve istemcileri eklemek kolay hale getiren var olan WCF API'leri, bağlı yerleşik olarak bulunur.</span><span class="sxs-lookup"><span data-stu-id="5fd90-137">WCF Discovery is built upon the existing WCF APIs, which makes it easy to add Discovery functionality to your existing services and clients.</span></span> <span data-ttu-id="5fd90-138">Hizmet bulunabilirliği kolayca uygulama yapılandırma ayarları'nda eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-138">Service discoverability can be easily added through the application configuration settings.</span></span> <span data-ttu-id="5fd90-139">Ayrıca, WCF bulma ayrıca eş net, adlandırma katmana ve HTTP gibi diğer taşımaları üzerinden Bulma Protokolü kullanarak destekler.</span><span class="sxs-lookup"><span data-stu-id="5fd90-139">In addition, WCF Discovery also supports using the discovery protocol over other transports such as peer net, naming overlay, and HTTP.</span></span> <span data-ttu-id="5fd90-140">WCF bulma işlemi keşif proxy'si kullanıldığı bir yönetilen modu için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fd90-140">WCF Discovery provides support for a Managed mode of operation where a discovery proxy is used.</span></span> <span data-ttu-id="5fd90-141">Tüm ağ için çok noktaya yayın iletileri göndermek yerine doğrudan keşif proxy'si iletilerinin gönderildiği gibi bu ağ trafiğini azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-141">This can reduce network traffic as messages are sent directly to the discovery proxy instead of sending multicast messages to the entire network.</span></span> <span data-ttu-id="5fd90-142">WCF keşif daha fazla esneklik için Web services ile çalışırken de sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fd90-142">WCF Discovery also allows for more flexibility when working with Web services.</span></span> <span data-ttu-id="5fd90-143">Örneğin, istemci veya hizmeti yeniden yapılandırmak zorunda kalmadan bir hizmet adresini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fd90-143">For example, you can change the address of a service without having to reconfigure the client or the service.</span></span> <span data-ttu-id="5fd90-144">Bir istemci sorun hizmet erişmesi gerektiğinde bir `Probe` aracılığıyla ileti bir `Find` istemek ve geçerli adresiyle yanıt hizmete bekler.</span><span class="sxs-lookup"><span data-stu-id="5fd90-144">When a client must access the service it can issue a `Probe` message through a `Find` request and expect the service to respond with its current address.</span></span> <span data-ttu-id="5fd90-145">WCF keşif sözleşme türleri, bağlama öğeleri, ad alanı, kapsam ve anahtar sözcükleri veya sürüm numaraları gibi farklı ölçütleri temel alarak bir hizmet aramak bir istemcinin sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fd90-145">WCF Discovery allows a client to search for a service based on different criteria including contract types, binding elements, namespace, scope, and keywords or version numbers.</span></span> <span data-ttu-id="5fd90-146">WCF keşif çalışma zamanı ve tasarım zamanı bulma sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fd90-146">WCF Discovery enables runtime and design time discovery.</span></span> <span data-ttu-id="5fd90-147">Uygulamanıza ekleme bulma, hata toleransı ve otomatik yapılandırması gibi diğer senaryoları etkinleştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-147">Adding discovery to your application can be used to enable other scenarios such as fault tolerance and auto configuration.</span></span>  
  
## <a name="service-publication"></a><span data-ttu-id="5fd90-148">Hizmet yayımı</span><span class="sxs-lookup"><span data-stu-id="5fd90-148">Service Publication</span></span>  
 <span data-ttu-id="5fd90-149">Bir hizmet bulunabilir, duruma getirmek için bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> eklenmelidir bulma iletiler için dinleme konumu belirtmek için hizmet ana bilgisayarı ve bir bulma uç noktası eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-149">To make a service discoverable, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> must be added to the service host and a discovery endpoint must be added to specify where to listen for discovery messages.</span></span> <span data-ttu-id="5fd90-150">Aşağıdaki kod örneğinde, kendini barındıran hizmet bulunabilir duruma getirmek için nasıl değiştirilebilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-150">The following code example shows how a self-hosted service can be modified to make it discoverable.</span></span>  
  
```csharp  
Uri baseAddress = new Uri(string.Format("http://{0}:8000/discovery/scenarios/calculatorservice/{1}/",  
        System.Net.Dns.GetHostName(), Guid.NewGuid().ToString()));

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
 <span data-ttu-id="5fd90-151">A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> örneği bulunabilir hizmet için bir hizmet açıklama eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-151">A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance must be added to a service description for the service to be discoverable.</span></span> <span data-ttu-id="5fd90-152">A <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> örneği, hizmet bulma isteklerini dinlemek nereye bildirmek için hizmet konağı eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-152">A <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance must be added to the service host to tell the service where to listen for discovery requests.</span></span> <span data-ttu-id="5fd90-153">Bu örnekte, bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (türetilen <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) hizmet bulma istekleri için UDP üzerinden dinleme yapması gerektiğini belirtmek için eklenen çok noktaya yayın taşıma.</span><span class="sxs-lookup"><span data-stu-id="5fd90-153">In this example, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (which is derived from <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) is added to specify that the service should listen for discovery requests over the UDP multicast transport.</span></span> <span data-ttu-id="5fd90-154"><xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Tüm iletileri çok noktaya yayın bir biçimde gönderildiğinden geçici bulmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5fd90-154">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is used for Ad-Hoc discovery because all messages are sent in a multicast fashion.</span></span>  
  
## <a name="announcement"></a><span data-ttu-id="5fd90-155">Duyuru</span><span class="sxs-lookup"><span data-stu-id="5fd90-155">Announcement</span></span>  
 <span data-ttu-id="5fd90-156">Varsayılan olarak, hizmet yayımı duyuru iletilerini göndermez.</span><span class="sxs-lookup"><span data-stu-id="5fd90-156">By default, service publication does not send out announcement messages.</span></span> <span data-ttu-id="5fd90-157">Hizmetin, duyuru iletilerini göndermek için yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5fd90-157">The service must be configured to send out announcement messages.</span></span> <span data-ttu-id="5fd90-158">Ayrı olarak bulma iletiler için dinleme hizmetinin Duyurusu çünkü bu hizmeti yazıcıları için ek esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fd90-158">This provides additional flexibility for service writers because they can announce the service separately from listening for discovery messages.</span></span> <span data-ttu-id="5fd90-159">Hizmet duyuru Hizmetleri keşif proxy'si veya diğer hizmet kayıt defterleri ile kaydettirmek için bir mekanizma olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-159">Service announcement can also be used as a mechanism for registering services with a discovery proxy or other service registries.</span></span> <span data-ttu-id="5fd90-160">Aşağıdaki kod bir UDP bağlama üzerinden duyuru iletileri göndermek için bir hizmeti yapılandırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-160">The following code shows how to configure a service to send announcement messages over a UDP binding.</span></span>  
  
```csharp  
Uri baseAddress = new Uri(string.Format("http://{0}:8000/discovery/scenarios/calculatorservice/{1}/",
        System.Net.Dns.GetHostName(), Guid.NewGuid().ToString()));

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    ServiceDiscoveryBehavior discoveryBehavior = new ServiceDiscoveryBehavior();
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

    // Send announcements on UDP multicast transport
    discoveryBehavior.AnnouncementEndpoints.Add(
      new UdpAnnouncementEndpoint());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.Description.Endpoints.Add(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
## <a name="service-discovery"></a><span data-ttu-id="5fd90-161">Hizmet bulma</span><span class="sxs-lookup"><span data-stu-id="5fd90-161">Service Discovery</span></span>  
 <span data-ttu-id="5fd90-162">Bir istemci uygulaması kullanabilir <xref:System.ServiceModel.Discovery.DiscoveryClient> Hizmetleri bulmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="5fd90-162">A client application can use the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to find services.</span></span> <span data-ttu-id="5fd90-163">Geliştirici bir örneğini oluşturur <xref:System.ServiceModel.Discovery.DiscoveryClient> nereye gönderileceğini belirten bir bulma uç noktası geçirir sınıfı `Probe` veya `Resolve` iletileri.</span><span class="sxs-lookup"><span data-stu-id="5fd90-163">The developer creates an instance of the <xref:System.ServiceModel.Discovery.DiscoveryClient> class that passes in a discovery endpoint that specifies where to send `Probe` or `Resolve` messages.</span></span> <span data-ttu-id="5fd90-164">İstemci ardından çağırır <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> içinde arama ölçütlerini belirtir bir <xref:System.ServiceModel.Discovery.FindCriteria> örneği.</span><span class="sxs-lookup"><span data-stu-id="5fd90-164">The client then calls <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> that specifies search criteria within a <xref:System.ServiceModel.Discovery.FindCriteria> instance.</span></span> <span data-ttu-id="5fd90-165">Eşleşen Hizmetleri bulunursa, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> koleksiyonunu döndürür <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>.</span><span class="sxs-lookup"><span data-stu-id="5fd90-165">If matching services are found, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> returns a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>.</span></span> <span data-ttu-id="5fd90-166">Aşağıdaki kod nasıl çağrılacağını gösterir `Find` yöntemi ve bulunan bir hizmetine bağlanın.</span><span class="sxs-lookup"><span data-stu-id="5fd90-166">The following code shows how to call the `Find` method and then connect to a discovered service.</span></span>  
  
```csharp  
class Client
{
    static EndpointAddress serviceAddress;
  
    static void Main()
    {  
        if (FindService()) 
        {
            InvokeService();
        }
    }  
  
    // ** DISCOVERY ** //  
    static bool FindService()  
    {  
        Console.WriteLine("\nFinding Calculator Service ..");  
        DiscoveryClient discoveryClient =   
            new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
        Collection<EndpointDiscoveryMetadata> calculatorServices =   
            (Collection<EndpointDiscoveryMetadata>)discoveryClient.Find(new FindCriteria(typeof(ICalculator))).Endpoints;  
  
        discoveryClient.Close();  
  
        if (calculatorServices.Count == 0)  
        {  
            Console.WriteLine("\nNo services are found.");  
            return false;  
        }  
        else  
        {  
            serviceAddress = calculatorServices[0].Address;  
            return true;  
        }  
    }  
  
    static void InvokeService()  
    {  
        Console.WriteLine("\nInvoking Calculator Service at {0}\n", serviceAddress);  
  
        // Create a client  
        CalculatorClient client = new CalculatorClient();  
        client.Endpoint.Address = serviceAddress;  
        client.Add(10,3);  
    }
}  
```  
  
## <a name="discovery-and-message-level-security"></a><span data-ttu-id="5fd90-167">Bulma ve ileti düzeyi güvenliği</span><span class="sxs-lookup"><span data-stu-id="5fd90-167">Discovery and Message Level Security</span></span>  
 <span data-ttu-id="5fd90-168">İleti düzeyi güvenlik kullanılırken belirtmek için gerekli bir <xref:System.ServiceModel.EndpointIdentity> hizmet bulma uç noktası ve eşleşen bir <xref:System.ServiceModel.EndpointIdentity> istemci bulma uç.</span><span class="sxs-lookup"><span data-stu-id="5fd90-168">When using message level security it is necessary to specify an <xref:System.ServiceModel.EndpointIdentity> on the service discovery endpoint and a matching <xref:System.ServiceModel.EndpointIdentity> on the client discovery endpoint.</span></span> <span data-ttu-id="5fd90-169">İleti düzeyi güvenliği hakkında daha fazla bilgi için bkz: [ileti güvenliği](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="5fd90-169">For more information about message level security, see [Message Security](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span></span>  
  
## <a name="discovery-and-web-hosted-services"></a><span data-ttu-id="5fd90-170">Bulma ve Web Hizmetleri barındırılan</span><span class="sxs-lookup"><span data-stu-id="5fd90-170">Discovery and Web Hosted Services</span></span>  
 <span data-ttu-id="5fd90-171">WCF hizmetleri bulunabilir sırayla bunlar çalıştırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-171">In order for WCF services to be discoverable they must be running.</span></span> <span data-ttu-id="5fd90-172">IIS kadar IIS ya da WAS çalıştırmayın altında barındırılan WCF hizmetleri / olan hizmet için varsayılan olarak bulunabilirlik olamaz bağlı bir ileti alır.</span><span class="sxs-lookup"><span data-stu-id="5fd90-172">WCF services hosted under IIS or WAS do not run until IIS/WAS receives a message bound for the service, so they cannot be discoverable by default.</span></span>  <span data-ttu-id="5fd90-173">Web barındırılan hizmetleri bulunabilir yapmak için iki seçenek vardır:</span><span class="sxs-lookup"><span data-stu-id="5fd90-173">There are two options for making Web-Hosted services discoverable:</span></span>  
  
1.  <span data-ttu-id="5fd90-174">Windows Server AppFabric otomatik başlatma özelliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="5fd90-174">Use the Windows Server AppFabric Auto-Start feature</span></span>  
  
2.  <span data-ttu-id="5fd90-175">Adına hizmeti iletişim kurmak için keşif proxy'si kullanın</span><span class="sxs-lookup"><span data-stu-id="5fd90-175">Use a discovery proxy to communicate on behalf of the service</span></span>  
  
 <span data-ttu-id="5fd90-176">Windows Server AppFabric iletileri almadan önce başlatılması bir hizmet sağlayacak bir otomatik başlatma özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="5fd90-176">Windows Server AppFabric has an Auto-Start feature that will allow a service to be started before receiving any messages.</span></span> <span data-ttu-id="5fd90-177">Bu otomatik başlatma olan ayarlayın, bir IIS / barındırılan WAS hizmeti bulunabilir olarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-177">With this Auto-Start set, an IIS/WAS hosted service can be configured to be discoverable.</span></span> <span data-ttu-id="5fd90-178">Otomatik başlatma özelliği bakın hakkında daha fazla bilgi için [Windows Server AppFabric otomatik başlatma özelliği](http://go.microsoft.com/fwlink/?LinkId=205545).</span><span class="sxs-lookup"><span data-stu-id="5fd90-178">For more information about the Auto-Start feature see, [Windows Server AppFabric Auto-Start Feature](http://go.microsoft.com/fwlink/?LinkId=205545).</span></span> <span data-ttu-id="5fd90-179">Otomatik başlatma özelliğini kapatma yanı sıra, hizmet bulma için yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-179">Along with turning on the Auto-Start feature, you must configure the service for discovery.</span></span> <span data-ttu-id="5fd90-180">Daha fazla bilgi için bkz: [nasıl yapılır: program aracılığıyla eklemek bulunabilirliği bir WCF hizmeti ve istemci](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[yapılandırma bulma yapılandırma dosyasında](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="5fd90-180">For more information, see [How to: Programmatically Add Discoverability to a WCF Service and Client](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[Configuring Discovery in a Configuration File](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).</span></span>  
  
 <span data-ttu-id="5fd90-181">Keşif proxy'si hizmeti çalışmadığı zaman adına WCF Hizmeti iletişim kurmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-181">A discovery proxy can be used to communicate on behalf of the WCF service when the service is not running.</span></span> <span data-ttu-id="5fd90-182">Proxy için yoklama dinleme veya iletileri çözün ve istemci yanıt.</span><span class="sxs-lookup"><span data-stu-id="5fd90-182">The proxy can listen for probe or resolve messages and respond to the client.</span></span> <span data-ttu-id="5fd90-183">İstemci, ardından doğrudan hizmet iletileri gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="5fd90-183">The client can then send messages directly to the service.</span></span> <span data-ttu-id="5fd90-184">İstemci hizmete bir ileti gönderdiğinde iletisinde örneği.</span><span class="sxs-lookup"><span data-stu-id="5fd90-184">When the client sends a message to the service it will be instantiated to respond to the message.</span></span> <span data-ttu-id="5fd90-185">Keşif proxy bakın, uygulama hakkında daha fazla bilgi için [keşif proxy'si ekleme](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).</span><span class="sxs-lookup"><span data-stu-id="5fd90-185">For more information about implementing a discovery proxy see, [Implementing a Discovery Proxy](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5fd90-186">WCF keşif'ın düzgün çalışması tüm NIC'ler (ağ arabirimi denetleyicisinin) yalnızca 1 IP adresi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5fd90-186">For WCF Discovery to work correctly, all NICs (Network Interface Controller) should only have 1 IP address.</span></span>
