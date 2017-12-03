---
title: "Keşif Duyuruları ve Duyuru İstemcisi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a6da9c2e251a6592bb0af039d552d02e7e4fd3fd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="discovery-announcements-and-announcement-client"></a><span data-ttu-id="791ce-102">Keşif Duyuruları ve Duyuru İstemcisi</span><span class="sxs-lookup"><span data-stu-id="791ce-102">Discovery Announcements and Announcement Client</span></span>
<span data-ttu-id="791ce-103">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Bulma özelliği kendi kullanıma sunulduğunu duyurmaktan bileşenleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="791ce-103">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] discovery feature enables components to announce their availability.</span></span> <span data-ttu-id="791ce-104">Bunu yapmak için yapılandırılmışsa, bir hizmet Hello ve Bye Duyurular gönderir.</span><span class="sxs-lookup"><span data-stu-id="791ce-104">If configured to do so, a service sends Hello and Bye announcements.</span></span> <span data-ttu-id="791ce-105">İstemcileri veya diğer bileşenleri, bu tür duyuru iletiler için dinleme ve bunlar üzerinde hareket.</span><span class="sxs-lookup"><span data-stu-id="791ce-105">Clients or other components can listen for such announcement messages and act on them.</span></span> <span data-ttu-id="791ce-106">Bu, istemcilerin hizmetlerin farkında olması alternatif bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="791ce-106">This provides an alternative method for clients to be aware of services.</span></span> <span data-ttu-id="791ce-107">Duyuru işlevselliği birkaç kullanımı vardır, örneğin, hizmetleri girin ve bir ağ sık bırakırsanız duyuruları arama hizmetleri için daha iyi bir alternatif olabilir.</span><span class="sxs-lookup"><span data-stu-id="791ce-107">Announcement functionality has several uses, for example, if the services enter and leave a network frequently, announcements may be a better alternative than searching for services.</span></span> <span data-ttu-id="791ce-108">Bu yaklaşım ağ trafiği azaltılır ve duyuruları alınan hemen istemci varlığının veya hizmetin ayrılma hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="791ce-108">With this approach, the network traffic is reduced and the client can learn about the presence or departure of the service as soon as announcements are received.</span></span>  
  
## <a name="discovery-announcements"></a><span data-ttu-id="791ce-109">Keşif duyuruları</span><span class="sxs-lookup"><span data-stu-id="791ce-109">Discovery Announcements</span></span>  
 <span data-ttu-id="791ce-110">Duyuruları için yapılandırılmış bir hizmeti bir ağ birleştirir ve bulunabilirlik olur, kendi kullanılabilirlik dinleme istemcilere Duyurusu Hello ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="791ce-110">When a service configured for announcements joins a network and becomes discoverable, it sends a Hello message announcing its availability to listening clients.</span></span> <span data-ttu-id="791ce-111">İleti içerir bulma ilgili hizmet sözleşmesi, uç nokta adresi gibi ilgili bilgileri ve kapsamları.</span><span class="sxs-lookup"><span data-stu-id="791ce-111">The message contains discovery related information about the service, such as its contract, endpoint address and associated scopes.</span></span> <span data-ttu-id="791ce-112">Duyuru iletisi ile gönderilen burada belirtebilirsiniz <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="791ce-112">You can specify where the announcement message is sent with the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> class.</span></span> <span data-ttu-id="791ce-113">Duyuru uç nokta ise bir <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> Hello ve Bye uygun şekilde çok noktaya yayın veya tek noktaya yayın duyuruyu uç nokta ise, belirtilen uç noktası doğrudan iletileri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="791ce-113">If the announcement endpoint is a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> then the Hello and Bye are multicast appropriately, or if the announcement endpoint is unicast, the messages are sent directly to the specified endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="791ce-114">Hizmet Konağı açar ve kapandığında duyuruları gönderilir.</span><span class="sxs-lookup"><span data-stu-id="791ce-114">Announcements are sent when the service host opens and closes.</span></span> <span data-ttu-id="791ce-115">Bu çağrı düzgün son değil, duyuru iletisi gönderilmemesi. Hizmet hataları Bye Duyurunun ileti gönderilmedi sonra Örneğin.</span><span class="sxs-lookup"><span data-stu-id="791ce-115">If these calls do not finish properly the announcement message may not be sent out. For example if the service faults, then the Bye announcement message is not sent.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="791ce-116">Seçtiğiniz her duyuruları göndermenizi sağlayan duyuru işlevselliği özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="791ce-116">You can customize the announcement functionality, allowing you to send announcements whenever you choose.</span></span>  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="791ce-117">tanımlar <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> hizmetler ve kolayca Hello ve Bye duyuruları göndermek için istemcileri izin vermek için standart uç noktaları olarak.</span><span class="sxs-lookup"><span data-stu-id="791ce-117"> defines the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> and <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> as standard endpoints to allow services and clients to easily send Hello and Bye announcements.</span></span>  
  
### <a name="announcements-on-the-service"></a><span data-ttu-id="791ce-118">Hizmette duyuruları</span><span class="sxs-lookup"><span data-stu-id="791ce-118">Announcements on the Service</span></span>  
 <span data-ttu-id="791ce-119">Duyurular göndermek üzere hizmetini yapılandırmak için ekleyin bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> bir duyuru uç noktası ile.</span><span class="sxs-lookup"><span data-stu-id="791ce-119">To configure the service to send announcements, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> with an announcement endpoint.</span></span> <span data-ttu-id="791ce-120">Aşağıdaki örnek programlı olarak bu davranış hizmet ana bilgisayara nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="791ce-120">The following example shows how to programmatically add this behavior to the service host.</span></span> <span data-ttu-id="791ce-121">Bu örnekte `UdpAnnouncementEndpoint`, duyuruları standart bu bitiş noktası tarafından belirtilen bir konuma çok noktaya yayın anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="791ce-121">This example uses the `UdpAnnouncementEndpoint`, which implies that the announcements are multicast to a location specified by that standard endpoint.</span></span>  
  
```  
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```  
  
 <span data-ttu-id="791ce-122">Aşağıdaki örnekte gösterildiği gibi davranış yanı, yapılandırma dosyasında yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="791ce-122">The behavior can be configured in the configuration file as well, as shown in the following example.</span></span>  
  
```xml  
<services>
  <service behaviorConfiguration="CalculatorBehavior" name="Microsoft.Samples.Discovery.CalculatorService">
    <!--Add Discovery Endpoint-->
    <endpoint name="udpDiscoveryEpt" kind="udpDiscoveryEndpoint" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorBehavior">
      <!--Add Discovery behavior-->
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
 <span data-ttu-id="791ce-123">Önceki örneklerde otomatik olarak duyuru iletileri göndermek üzere bir hizmetini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="791ce-123">The preceding examples configure a service to automatically send announcement messages.</span></span> <span data-ttu-id="791ce-124">Ayrıca duyuru iletileri açıkça kullanarak gönderebilirsiniz <xref:System.ServiceModel.Discovery.AnnouncementClient> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="791ce-124">You can also send announcement messages explicitly by using the <xref:System.ServiceModel.Discovery.AnnouncementClient> class.</span></span>  
  
### <a name="announcements-on-the-client"></a><span data-ttu-id="791ce-125">İstemci üzerinde duyuruları</span><span class="sxs-lookup"><span data-stu-id="791ce-125">Announcements on the Client</span></span>  
 <span data-ttu-id="791ce-126">Bir istemci uygulaması Hello ve Bye iletileri yanıtlayın ve abone olmak üzere bir duyuru hizmet ana bilgisayar <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> ve <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> olaylar.</span><span class="sxs-lookup"><span data-stu-id="791ce-126">A client application must host an announcement service to respond to the Hello and Bye messages and subscribe to the <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> and <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> events.</span></span> <span data-ttu-id="791ce-127">Aşağıdaki örnek bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="791ce-127">The following example shows how to do this.</span></span>  
  
```  
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();
  
// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;
  
// Create ServiceHost for the AnnouncementService
using (ServiceHost announcementServiceHost = new ServiceHost(announcementService))
{  
    // Listen for the announcements sent over UDP multicast
    announcementServiceHost.AddServiceEndpoint(new UdpAnnouncementEndpoint());
    announcementServiceHost.Open();
  
    Console.WriteLine("Press <ENTER> to terminate.");
    Console.ReadLine();
}  
```  
  
 <span data-ttu-id="791ce-128">Merhaba veya Bye bir ileti alındığında, uç nokta bulma meta veriler üzerinden erişebilirsiniz <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="791ce-128">When a Hello or Bye message is received, you can access the endpoint discovery metadata through <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> as shown in the following example.</span></span>  
  
```  
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine("Received an online announcement from {0}", 
e.EndpointDiscoveryMetadata.Address);
}

static void OnOfflineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine("Received an offline announcement from {0}", 
e.EndpointDiscoveryMetadata.Address);
}
```
