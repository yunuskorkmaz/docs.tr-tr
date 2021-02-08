---
description: 'Daha fazla bilgi edinin: WCF bulgu genel bakış'
title: WCF Keşif Genel Bakış
ms.date: 03/30/2017
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
ms.openlocfilehash: d6acfb86ce0961ea7fbfba7695bece067e3dcec2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779653"
---
# <a name="wcf-discovery-overview"></a><span data-ttu-id="35881-103">WCF Keşif Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="35881-103">WCF Discovery Overview</span></span>

<span data-ttu-id="35881-104">Bulma API 'Leri, WS-Discovery protokolü kullanılarak dinamik yayımlama ve Web Hizmetleri bulma için Birleşik bir programlama modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="35881-104">The Discovery APIs provide a unified programming model for the dynamic publication and discovery of Web services using the WS-Discovery protocol.</span></span> <span data-ttu-id="35881-105">Bu API 'Ler, hizmetlerin kendilerini ve istemcileri yayımlanmış Hizmetleri bulmak için yayımlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="35881-105">These APIs allow services to publish themselves and clients to find published services.</span></span> <span data-ttu-id="35881-106">Bir hizmet bulunabilir hale getirildikten sonra hizmet, duyuru iletileri gönderebilir ve bulma isteklerini dinleyebilir ve bunlara yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="35881-106">Once a service is made discoverable, the service has the ability to send announcement messages as well as listen for and respond to discovery requests.</span></span> <span data-ttu-id="35881-107">Keşfedilebilir hizmetler, bir ağ üzerinden bir ağı duyurmak üzere bir ağ ve Bye iletileri üzerinde gelişmelerini duyurmak için Merhaba iletiler gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="35881-107">Discoverable services can send Hello messages to announce their arrival on a network and Bye messages to announce their departure from a network.</span></span> <span data-ttu-id="35881-108">İstemcileri, bir hizmeti bulmak için `Probe` ağ üzerinde hizmet sözleşmesi türü, anahtar sözcükler ve kapsam gibi belirli ölçütler içeren bir istek gönderir.</span><span class="sxs-lookup"><span data-stu-id="35881-108">To find a service, clients send a `Probe` request that contains specific criteria such as service contract type, keywords, and scope on the network.</span></span> <span data-ttu-id="35881-109">Hizmetler, `Probe` isteği alır ve ölçütlere göre eşleşip eşleşmediğine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="35881-109">Services receive the `Probe` request and determine whether they match the criteria.</span></span> <span data-ttu-id="35881-110">Bir hizmet eşleşiyorsa, `ProbeMatch` hizmetle iletişim kurmak için gereken bilgilerle istemciye geri ileti göndererek yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="35881-110">If a service matches, it responds by sending a `ProbeMatch` message back to the client with the information necessary to contact the service.</span></span> <span data-ttu-id="35881-111">İstemciler ayrıca `Resolve` , kendi uç nokta adreslerini değiştirmiş olabilecek Hizmetleri bulmasına izin veren istekleri de gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="35881-111">Clients can also send `Resolve` requests that allow them to find services that may have changed their endpoint address.</span></span> <span data-ttu-id="35881-112">Eşleşen Hizmetler `Resolve` istemciye geri ileti göndererek isteklere yanıt verir `ResolveMatch` .</span><span class="sxs-lookup"><span data-stu-id="35881-112">Matching services respond to `Resolve` requests by sending a `ResolveMatch` message back to the client.</span></span>  
  
## <a name="ad-hoc-and-managed-modes"></a><span data-ttu-id="35881-113">Geçici ve yönetilen modlar</span><span class="sxs-lookup"><span data-stu-id="35881-113">Ad-Hoc and Managed Modes</span></span>  

 <span data-ttu-id="35881-114">Keşif API 'SI iki farklı modu destekler: yönetilen ve geçici.</span><span class="sxs-lookup"><span data-stu-id="35881-114">The Discovery API supports two different modes: Managed and Ad-Hoc.</span></span> <span data-ttu-id="35881-115">Yönetilen modda, kullanılabilir hizmetler hakkında bilgi tutan bulma proxy 'si adlı merkezi bir sunucu vardır.</span><span class="sxs-lookup"><span data-stu-id="35881-115">In Managed mode there is a centralized server called a discovery proxy that maintains information about available services.</span></span> <span data-ttu-id="35881-116">Keşif proxy 'si, hizmetler hakkında çeşitli yollarla doldurulmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="35881-116">The discovery proxy can be populated with information about services in a variety of ways.</span></span> <span data-ttu-id="35881-117">Örneğin, hizmetler bulma proxy 'sine başlama sırasında duyuru iletileri gönderebilir veya proxy, hangi hizmetlerin kullanılabilir olduğunu belirlemek için bir veritabanından veya bir yapılandırma dosyasından verileri okuyabilir.</span><span class="sxs-lookup"><span data-stu-id="35881-117">For example, services can send announcement messages during start up to the discovery proxy or the proxy may read data from a database or a configuration file to determine what services are available.</span></span> <span data-ttu-id="35881-118">Bulma proxy 'sinin nasıl doldurulduğu, geliştiriciye tamamen tamamen yapılır.</span><span class="sxs-lookup"><span data-stu-id="35881-118">How the discovery proxy is populated is completely up to the developer.</span></span> <span data-ttu-id="35881-119">İstemciler, kullanılabilir hizmetler hakkında bilgi almak için bulma proxy 'sini kullanır.</span><span class="sxs-lookup"><span data-stu-id="35881-119">Clients use the discovery proxy to retrieve information about available services.</span></span> <span data-ttu-id="35881-120">Bir istemci bir hizmeti aradığında `Probe` , bulma proxy 'sine bir ileti gönderir ve proxy, istemci tarafından aranan hizmetlerden herhangi birinin aradığı hizmetle eşleşip eşleşmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="35881-120">When a client searches for a service it sends a `Probe` message to the discovery proxy and the proxy determines whether any of the services it knows about match the service the client is searching for.</span></span> <span data-ttu-id="35881-121">Eşleşmeler varsa bulma proxy 'si istemciye bir yanıt gönderir `ProbeMatch` .</span><span class="sxs-lookup"><span data-stu-id="35881-121">If there are matches the discovery proxy sends a `ProbeMatch` response back to the client.</span></span> <span data-ttu-id="35881-122">İstemci daha sonra doğrudan proxy 'den döndürülen hizmet bilgilerini kullanarak hizmetle iletişim kurabilirler.</span><span class="sxs-lookup"><span data-stu-id="35881-122">The client can then contact the service directly using the service information returned from the proxy.</span></span> <span data-ttu-id="35881-123">Yönetilen modun arkasındaki anahtar ilkesi, bulma isteklerinin tek bir yetkiliye, bulma proxy 'sine yönelik bir tek noktaya gönderildiği bir şekilde gönderilir.</span><span class="sxs-lookup"><span data-stu-id="35881-123">The key principle behind Managed mode is that the discovery requests are sent in a unicast manner to one authority, the discovery proxy.</span></span> <span data-ttu-id="35881-124">.NET Framework kendi ara sunucusunu oluşturmanıza izin veren anahtar bileşenleri içerir.</span><span class="sxs-lookup"><span data-stu-id="35881-124">The .NET Framework contains key components that allow you to build your own proxy.</span></span> <span data-ttu-id="35881-125">İstemciler ve hizmetler Proxy 'yi birden çok yöntemle bulabilir:</span><span class="sxs-lookup"><span data-stu-id="35881-125">Clients and services can locate the proxy by multiple methods:</span></span>  
  
- <span data-ttu-id="35881-126">Proxy, geçici iletilere yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="35881-126">The proxy can respond to ad-hoc messages.</span></span>  
  
- <span data-ttu-id="35881-127">Proxy, başlangıç sırasında bir duyuru iletisi gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="35881-127">The proxy can send an announcement message during start up.</span></span>  
  
- <span data-ttu-id="35881-128">İstemciler ve hizmetler, iyi bilinen belirli bir uç noktayı aramak için yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="35881-128">Clients and services can be written to look for a specific well-known endpoint.</span></span>  
  
 <span data-ttu-id="35881-129">Geçici modda, merkezi sunucu yoktur.</span><span class="sxs-lookup"><span data-stu-id="35881-129">In Ad-Hoc mode, there is no centralized server.</span></span> <span data-ttu-id="35881-130">Hizmet duyuruları ve istemci istekleri gibi tüm bulma iletileri çok noktaya yayın biçiminde gönderilir.</span><span class="sxs-lookup"><span data-stu-id="35881-130">All discovery messages such as service announcements and client requests are sent in a multicast fashion.</span></span> <span data-ttu-id="35881-131">Varsayılan olarak .NET Framework, UDP protokolü üzerinden geçici bulma desteği içerir.</span><span class="sxs-lookup"><span data-stu-id="35881-131">By default the .NET Framework contains support for Ad-Hoc discovery over the UDP protocol.</span></span> <span data-ttu-id="35881-132">Örneğin, bir hizmet başlangıç sırasında bir Hello duyurusu gönderecek şekilde yapılandırıldıysa, UDP protokolünü kullanarak iyi bilinen bir çok noktaya yayın adresi üzerinden gönderilir.</span><span class="sxs-lookup"><span data-stu-id="35881-132">For example, if a service is configured to send out a Hello announcement on start up, it sends it out over a well-known, multicast address using the UDP protocol.</span></span> <span data-ttu-id="35881-133">İstemcilerin bu duyuruları etkin bir şekilde dinlemek ve uygun şekilde işlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="35881-133">Clients have to actively listen for these announcements and process them accordingly.</span></span> <span data-ttu-id="35881-134">İstemci `Probe` bir hizmet için bir ileti gönderdiğinde çok noktaya yayın protokolü kullanılarak ağ üzerinden gönderilir.</span><span class="sxs-lookup"><span data-stu-id="35881-134">When a client sends a `Probe` message for a service it is sent over the network using a multicast protocol.</span></span> <span data-ttu-id="35881-135">İsteği alan her hizmet, iletideki ölçütlerle eşleşip eşleşmediğini belirler `Probe` ve `ProbeMatch` hizmet iletide belirtilen ölçütlerle eşleşiyorsa istemciye doğrudan bir iletiyle yanıt verir `Probe` .</span><span class="sxs-lookup"><span data-stu-id="35881-135">Each service that receives the request determines whether it matches the criteria in the `Probe` message and responds directly to the client with a `ProbeMatch` message if the service matches the criteria specified in the `Probe` message.</span></span>  
  
## <a name="benefits-of-using-wcf-discovery"></a><span data-ttu-id="35881-136">WCF bulmayı kullanmanın avantajları</span><span class="sxs-lookup"><span data-stu-id="35881-136">Benefits of Using WCF Discovery</span></span>  

 <span data-ttu-id="35881-137">WCF bulma WS-Discovery protokol kullanılarak uygulandığından, WS-Discovery uygulayan diğer istemcilerle, hizmetlerle ve proxy 'lerde birlikte çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="35881-137">Because WCF Discovery is implemented using the WS-Discovery protocol it is interoperable with other clients, services, and proxies that implement WS-Discovery as well.</span></span> <span data-ttu-id="35881-138">WCF bulma, mevcut WCF API 'Leri üzerine kurulmuştur. Bu, mevcut hizmet ve istemcilerinize bulma işlevselliği eklemenizi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="35881-138">WCF Discovery is built upon the existing WCF APIs, which makes it easy to add Discovery functionality to your existing services and clients.</span></span> <span data-ttu-id="35881-139">Hizmet bulunabilirliği, uygulama yapılandırma ayarları aracılığıyla kolayca eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="35881-139">Service discoverability can be easily added through the application configuration settings.</span></span> <span data-ttu-id="35881-140">Ayrıca, WCF bulma Ayrıca, Eş ağ, adlandırma kaplaması ve HTTP gibi diğer aktarımlara yönelik bulma protokolünü de destekler.</span><span class="sxs-lookup"><span data-stu-id="35881-140">In addition, WCF Discovery also supports using the discovery protocol over other transports such as peer net, naming overlay, and HTTP.</span></span> <span data-ttu-id="35881-141">WCF bulma, bir bulma proxy 'sinin kullanıldığı yönetilen işlem modu için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="35881-141">WCF Discovery provides support for a Managed mode of operation where a discovery proxy is used.</span></span> <span data-ttu-id="35881-142">Bu, iletiler tüm ağa çok noktaya yayın iletileri göndermek yerine doğrudan bulma proxy 'sine gönderildiğinde ağ trafiğini azaltabilir.</span><span class="sxs-lookup"><span data-stu-id="35881-142">This can reduce network traffic as messages are sent directly to the discovery proxy instead of sending multicast messages to the entire network.</span></span> <span data-ttu-id="35881-143">WCF bulma ayrıca Web hizmetleriyle çalışırken daha fazla esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="35881-143">WCF Discovery also allows for more flexibility when working with Web services.</span></span> <span data-ttu-id="35881-144">Örneğin, istemciyi veya hizmeti yeniden yapılandırmak zorunda kalmadan bir hizmetin adresini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35881-144">For example, you can change the address of a service without having to reconfigure the client or the service.</span></span> <span data-ttu-id="35881-145">Bir istemcinin hizmete erişmesi gerektiğinde, `Probe` bir istek aracılığıyla bir ileti verebilir `Find` ve hizmetin geçerli adresiyle yanıt vermesini bekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="35881-145">When a client must access the service it can issue a `Probe` message through a `Find` request and expect the service to respond with its current address.</span></span> <span data-ttu-id="35881-146">WCF bulma, bir istemcinin sözleşme türleri, bağlama öğeleri, ad alanı, kapsam ve anahtar sözcükler ya da sürüm numaraları gibi farklı ölçütlere göre bir hizmet aramasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="35881-146">WCF Discovery allows a client to search for a service based on different criteria including contract types, binding elements, namespace, scope, and keywords or version numbers.</span></span> <span data-ttu-id="35881-147">WCF bulma çalışma zamanı ve tasarım zamanı bulmayı mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="35881-147">WCF Discovery enables runtime and design time discovery.</span></span> <span data-ttu-id="35881-148">Uygulamanıza bulma eklemek, hata toleransı ve otomatik yapılandırma gibi diğer senaryolara olanak tanımak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="35881-148">Adding discovery to your application can be used to enable other scenarios such as fault tolerance and auto configuration.</span></span>  
  
## <a name="service-publication"></a><span data-ttu-id="35881-149">Hizmet yayını</span><span class="sxs-lookup"><span data-stu-id="35881-149">Service Publication</span></span>  

 <span data-ttu-id="35881-150">Bir hizmeti bulunabilir hale getirmek için, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> hizmet ana bilgisayarına eklenmelidir ve bulma iletilerinin nerede dinleneceğini belirtmek için bir bulma uç noktası eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="35881-150">To make a service discoverable, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> must be added to the service host and a discovery endpoint must be added to specify where to listen for discovery messages.</span></span> <span data-ttu-id="35881-151">Aşağıdaki kod örneği, kendi kendine barındırılan bir hizmetin bulunabilir hale getirmek için nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="35881-151">The following code example shows how a self-hosted service can be modified to make it discoverable.</span></span>  
  
```csharp  
Uri baseAddress = new Uri($"http://{System.Net.Dns.GetHostName()}:8000/discovery/scenarios/calculatorservice/{Guid.NewGuid().ToString()}/");

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
  
 <span data-ttu-id="35881-152"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>Hizmetin keşfedilmesini sağlamak için bir hizmet açıklamasına bir örnek eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="35881-152">A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance must be added to a service description for the service to be discoverable.</span></span> <span data-ttu-id="35881-153">Hizmeti <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> bulma isteklerinin nerede dinleneceğini bildirmek için hizmet ana bilgisayarına bir örnek eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="35881-153">A <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance must be added to the service host to tell the service where to listen for discovery requests.</span></span> <span data-ttu-id="35881-154">Bu örnekte, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> hizmetin UDP çok noktaya yayın aktarımı üzerinden bulma isteklerini dinlemesi gerektiğini belirtmek için bir (öğesinden türetilmiş) bir () eklenir.</span><span class="sxs-lookup"><span data-stu-id="35881-154">In this example, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (which is derived from <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) is added to specify that the service should listen for discovery requests over the UDP multicast transport.</span></span> <span data-ttu-id="35881-155">, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Tüm iletiler çok noktaya yayın düzeyinde gönderildiğinden, geçici bulma için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="35881-155">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is used for Ad-Hoc discovery because all messages are sent in a multicast fashion.</span></span>  
  
## <a name="announcement"></a><span data-ttu-id="35881-156">Duyuru</span><span class="sxs-lookup"><span data-stu-id="35881-156">Announcement</span></span>  

 <span data-ttu-id="35881-157">Varsayılan olarak, hizmet yayını duyuru iletileri göndermez.</span><span class="sxs-lookup"><span data-stu-id="35881-157">By default, service publication does not send out announcement messages.</span></span> <span data-ttu-id="35881-158">Hizmetin duyuru iletileri gönderecek şekilde yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="35881-158">The service must be configured to send out announcement messages.</span></span> <span data-ttu-id="35881-159">Bu, hizmeti bulma iletilerini dinlemeden ayrı olarak duyurabileceğinden, hizmet yazarları için ek esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="35881-159">This provides additional flexibility for service writers because they can announce the service separately from listening for discovery messages.</span></span> <span data-ttu-id="35881-160">Hizmet duyurusu Ayrıca, Hizmetleri bulma proxy 'si veya diğer hizmet kayıt defterlerine kaydetme mekanizması olarak da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="35881-160">Service announcement can also be used as a mechanism for registering services with a discovery proxy or other service registries.</span></span> <span data-ttu-id="35881-161">Aşağıdaki kod, bir hizmetin UDP bağlama üzerinden duyuru iletileri göndermek için nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="35881-161">The following code shows how to configure a service to send announcement messages over a UDP binding.</span></span>  
  
```csharp  
Uri baseAddress = new Uri($"http://{System.Net.Dns.GetHostName()}:8000/discovery/scenarios/calculatorservice/{Guid.NewGuid().ToString()}/");

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    ServiceDiscoveryBehavior discoveryBehavior = new ServiceDiscoveryBehavior();
    serviceHost.Description.Behaviors.Add(discoveryBehavior);

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
  
## <a name="service-discovery"></a><span data-ttu-id="35881-162">Hizmet Bulma</span><span class="sxs-lookup"><span data-stu-id="35881-162">Service Discovery</span></span>  

 <span data-ttu-id="35881-163">İstemci uygulaması, <xref:System.ServiceModel.Discovery.DiscoveryClient> Hizmetleri bulmak için sınıfını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="35881-163">A client application can use the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to find services.</span></span> <span data-ttu-id="35881-164">Geliştirici, <xref:System.ServiceModel.Discovery.DiscoveryClient> ' ın nereye gönderileceğini belirten bir bulma uç noktasında geçen sınıfının bir örneğini oluşturur `Probe` `Resolve` .</span><span class="sxs-lookup"><span data-stu-id="35881-164">The developer creates an instance of the <xref:System.ServiceModel.Discovery.DiscoveryClient> class that passes in a discovery endpoint that specifies where to send `Probe` or `Resolve` messages.</span></span> <span data-ttu-id="35881-165">İstemci daha sonra <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> bir örnek içinde arama ölçütlerini belirten çağırır <xref:System.ServiceModel.Discovery.FindCriteria> .</span><span class="sxs-lookup"><span data-stu-id="35881-165">The client then calls <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> that specifies search criteria within a <xref:System.ServiceModel.Discovery.FindCriteria> instance.</span></span> <span data-ttu-id="35881-166">Eşleşen hizmetler bulunursa, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> bir koleksiyonu döndürür <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> .</span><span class="sxs-lookup"><span data-stu-id="35881-166">If matching services are found, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> returns a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>.</span></span> <span data-ttu-id="35881-167">Aşağıdaki kod, yönteminin nasıl çağrılacağını `Find` ve sonra keşfedilen bir hizmete nasıl bağlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="35881-167">The following code shows how to call the `Find` method and then connect to a discovered service.</span></span>  
  
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
  
## <a name="discovery-and-message-level-security"></a><span data-ttu-id="35881-168">Bulma ve Ileti düzeyi güvenliği</span><span class="sxs-lookup"><span data-stu-id="35881-168">Discovery and Message Level Security</span></span>  

 <span data-ttu-id="35881-169">İleti düzeyinde güvenlik kullanırken, <xref:System.ServiceModel.EndpointIdentity> hizmet bulma uç noktasında ve <xref:System.ServiceModel.EndpointIdentity> istemci bulma uç noktasında eşleşen bir değer belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="35881-169">When using message level security it is necessary to specify an <xref:System.ServiceModel.EndpointIdentity> on the service discovery endpoint and a matching <xref:System.ServiceModel.EndpointIdentity> on the client discovery endpoint.</span></span> <span data-ttu-id="35881-170">İleti düzeyi güvenliği hakkında daha fazla bilgi için bkz. [Ileti güvenliği](message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="35881-170">For more information about message level security, see [Message Security](message-security-in-wcf.md).</span></span>  
  
## <a name="discovery-and-web-hosted-services"></a><span data-ttu-id="35881-171">Bulma ve Web 'de barındırılan hizmetler</span><span class="sxs-lookup"><span data-stu-id="35881-171">Discovery and Web Hosted Services</span></span>  

 <span data-ttu-id="35881-172">WCF hizmetlerinin keşfedilmesini sağlamak için bunların çalışıyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="35881-172">In order for WCF services to be discoverable they must be running.</span></span> <span data-ttu-id="35881-173">IIS 'de barındırılan WCF Hizmetleri, IIS/hizmet için bir ileti alana bağlanana kadar çalıştırılmadığından, varsayılan olarak keşfedilemez.</span><span class="sxs-lookup"><span data-stu-id="35881-173">WCF services hosted under IIS or WAS do not run until IIS/WAS receives a message bound for the service, so they cannot be discoverable by default.</span></span>  <span data-ttu-id="35881-174">Web-Hosted hizmetlerini bulunabilir hale getirmek için iki seçenek vardır:</span><span class="sxs-lookup"><span data-stu-id="35881-174">There are two options for making Web-Hosted services discoverable:</span></span>  
  
1. <span data-ttu-id="35881-175">Windows Server AppFabric otomatik başlatma özelliğini kullanın</span><span class="sxs-lookup"><span data-stu-id="35881-175">Use the Windows Server AppFabric Auto-Start feature</span></span>  
  
2. <span data-ttu-id="35881-176">Hizmet adına iletişim kurmak için bir bulma proxy 'si kullanın</span><span class="sxs-lookup"><span data-stu-id="35881-176">Use a discovery proxy to communicate on behalf of the service</span></span>  
  
 <span data-ttu-id="35881-177">Windows Server AppFabric, herhangi bir ileti alınmadan önce bir hizmetin başlatılmasını sağlayacak bir otomatik başlatma özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="35881-177">Windows Server AppFabric has an Auto-Start feature that will allow a service to be started before receiving any messages.</span></span> <span data-ttu-id="35881-178">Bu otomatik başlatma kümesiyle, bir IIS/WAS barındırılan hizmeti bulunabilir olacak şekilde yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="35881-178">With this Auto-Start set, an IIS/WAS hosted service can be configured to be discoverable.</span></span> <span data-ttu-id="35881-179">Otomatik başlatma özelliği hakkında daha fazla bilgi için bkz. [Windows Server AppFabric otomatik başlatma özelliği](/previous-versions/appfabric/ee677260(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="35881-179">For more information about the Auto-Start feature see, [Windows Server AppFabric Auto-Start Feature](/previous-versions/appfabric/ee677260(v=azure.10)).</span></span> <span data-ttu-id="35881-180">Otomatik başlatma özelliğini açma ile birlikte, hizmeti bulma için yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="35881-180">Along with turning on the Auto-Start feature, you must configure the service for discovery.</span></span> <span data-ttu-id="35881-181">Daha fazla bilgi için bkz. [nasıl yapılır: program aracılığıyla BIR WCF hizmetine bulunabilirliği ekleme ve Istemci](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[yapılandırma dosyasında bulmayı yapılandırma](configuring-discovery-in-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="35881-181">For more information, see [How to: Programmatically Add Discoverability to a WCF Service and Client](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[Configuring Discovery in a Configuration File](configuring-discovery-in-a-configuration-file.md).</span></span>  
  
 <span data-ttu-id="35881-182">Bulma proxy 'si, hizmet çalışmadığı zaman WCF hizmeti adına iletişim kurmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="35881-182">A discovery proxy can be used to communicate on behalf of the WCF service when the service is not running.</span></span> <span data-ttu-id="35881-183">Proxy, araştırmayı dinleyebilir veya iletileri çözümleyebilir ve istemciye yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="35881-183">The proxy can listen for probe or resolve messages and respond to the client.</span></span> <span data-ttu-id="35881-184">İstemci daha sonra iletileri doğrudan hizmete gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="35881-184">The client can then send messages directly to the service.</span></span> <span data-ttu-id="35881-185">İstemci hizmete bir ileti gönderdiğinde, iletiye yanıt vermek için örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="35881-185">When the client sends a message to the service it will be instantiated to respond to the message.</span></span> <span data-ttu-id="35881-186">Bulma proxy 'si uygulama hakkında daha fazla bilgi için bkz. [bulma proxy 'Si uygulama](implementing-a-discovery-proxy.md).</span><span class="sxs-lookup"><span data-stu-id="35881-186">For more information about implementing a discovery proxy see, [Implementing a Discovery Proxy](implementing-a-discovery-proxy.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35881-187">WCF bulmanın düzgün çalışması için tüm NIC 'ler (ağ arabirim denetleyicisi) yalnızca 1 IP adresine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="35881-187">For WCF Discovery to work correctly, all NICs (Network Interface Controller) should only have 1 IP address.</span></span>
