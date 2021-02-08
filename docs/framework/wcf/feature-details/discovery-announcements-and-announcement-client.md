---
description: 'Daha fazla bilgi edinin: bulma duyuruları ve duyuru Istemcisi'
title: Keşif Duyuruları ve Duyuru İstemcisi
ms.date: 03/30/2017
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
ms.openlocfilehash: 2076b4dbdc57bd3de47fccdb4a51ef9e6fc48366
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802976"
---
# <a name="discovery-announcements-and-announcement-client"></a><span data-ttu-id="7ff2f-103">Keşif Duyuruları ve Duyuru İstemcisi</span><span class="sxs-lookup"><span data-stu-id="7ff2f-103">Discovery Announcements and Announcement Client</span></span>

<span data-ttu-id="7ff2f-104">WCF bulma özelliği, bileşenlerin kullanılabilirliğini duyurmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ff2f-104">The WCF discovery feature enables components to announce their availability.</span></span> <span data-ttu-id="7ff2f-105">Bunu yapmak için yapılandırıldıysa, bir hizmet Hello ve bye duyuruları gönderir.</span><span class="sxs-lookup"><span data-stu-id="7ff2f-105">If configured to do so, a service sends Hello and Bye announcements.</span></span> <span data-ttu-id="7ff2f-106">İstemciler veya diğer bileşenler bu tür duyuru iletilerini dinleyebilir ve üzerinde işlem yapabilir.</span><span class="sxs-lookup"><span data-stu-id="7ff2f-106">Clients or other components can listen for such announcement messages and act on them.</span></span> <span data-ttu-id="7ff2f-107">Bu, istemcilerin hizmetlerden haberdar olması için alternatif bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ff2f-107">This provides an alternative method for clients to be aware of services.</span></span> <span data-ttu-id="7ff2f-108">Duyuru işlevselliğinin birçok kullanımı vardır. Örneğin, hizmetler bir ağı girip bir kez daha bırakıyorsanız, Duyurular hizmetler aranırken daha iyi bir alternatif olabilir.</span><span class="sxs-lookup"><span data-stu-id="7ff2f-108">Announcement functionality has several uses, for example, if the services enter and leave a network frequently, announcements may be a better alternative than searching for services.</span></span> <span data-ttu-id="7ff2f-109">Bu yaklaşımda, ağ trafiği azalır ve istemci, Duyurular alındıktan hemen sonra, hizmetin varlığı veya ayrılış hakkında bilgi alabilir.</span><span class="sxs-lookup"><span data-stu-id="7ff2f-109">With this approach, the network traffic is reduced and the client can learn about the presence or departure of the service as soon as announcements are received.</span></span>

## <a name="discovery-announcements"></a><span data-ttu-id="7ff2f-110">Keşif Duyuruları</span><span class="sxs-lookup"><span data-stu-id="7ff2f-110">Discovery Announcements</span></span>

<span data-ttu-id="7ff2f-111">Duyurular için yapılandırılmış bir hizmet bir ağa katıldığında ve bulunabilir hale geldiğinde, istemcileri dinlemek için kullanılabilirliğini duyuran bir Hello iletisi gönderir.</span><span class="sxs-lookup"><span data-stu-id="7ff2f-111">When a service configured for announcements joins a network and becomes discoverable, it sends a Hello message announcing its availability to listening clients.</span></span> <span data-ttu-id="7ff2f-112">İleti, hizmet hakkında, sözleşme, uç nokta adresi ve ilişkili kapsamlar gibi bulma ile ilgili bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="7ff2f-112">The message contains discovery related information about the service, such as its contract, endpoint address and associated scopes.</span></span> <span data-ttu-id="7ff2f-113">Duyuru iletisinin sınıf ile nereye gönderileceğini belirtebilirsiniz <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="7ff2f-113">You can specify where the announcement message is sent with the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> class.</span></span> <span data-ttu-id="7ff2f-114">Duyuru uç noktası bir ise, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> Merhaba ve bye çok noktaya yayın ise veya duyuru uç noktası tek noktaya ise, iletiler doğrudan belirtilen uç noktaya gönderilir.</span><span class="sxs-lookup"><span data-stu-id="7ff2f-114">If the announcement endpoint is a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> then the Hello and Bye are multicast appropriately, or if the announcement endpoint is unicast, the messages are sent directly to the specified endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="7ff2f-115">Duyurular, hizmet ana bilgisayarı açılıp kapandığında gönderilir.</span><span class="sxs-lookup"><span data-stu-id="7ff2f-115">Announcements are sent when the service host opens and closes.</span></span> <span data-ttu-id="7ff2f-116">Bu çağrılar düzgün tamamlanmazsa, duyuru iletisi gönderilemeyebilir. Örneğin, hizmet hataları varsa, Bye duyuru iletisi gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="7ff2f-116">If these calls do not finish properly the announcement message may not be sent out. For example if the service faults, then the Bye announcement message is not sent.</span></span>

> [!TIP]
> <span data-ttu-id="7ff2f-117">Duyuru işlevini özelleştirerek, her seçerken Duyurular göndermenize olanak sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ff2f-117">You can customize the announcement functionality, allowing you to send announcements whenever you choose.</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="7ff2f-118"><xref:System.ServiceModel.Discovery.AnnouncementEndpoint> <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> hizmetlerin ve Istemcilerin kolayca Hello ve bye duyuruları göndermesini sağlamak için ve standart uç noktaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7ff2f-118">defines the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> and <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> as standard endpoints to allow services and clients to easily send Hello and Bye announcements.</span></span>

### <a name="announcements-on-the-service"></a><span data-ttu-id="7ff2f-119">Hizmette Duyurular</span><span class="sxs-lookup"><span data-stu-id="7ff2f-119">Announcements on the Service</span></span>

<span data-ttu-id="7ff2f-120">Hizmeti Duyurular gönderecek şekilde yapılandırmak için bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> duyuru uç noktası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7ff2f-120">To configure the service to send announcements, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> with an announcement endpoint.</span></span> <span data-ttu-id="7ff2f-121">Aşağıdaki örnek, bu davranışın hizmet ana bilgisayarına programlı bir şekilde nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ff2f-121">The following example shows how to programmatically add this behavior to the service host.</span></span> <span data-ttu-id="7ff2f-122">Bu örnek, `UdpAnnouncementEndpoint` bildirilerinin çok noktaya yayın olduğunu belirten, bu standart uç nokta tarafından belirtilen bir konuma kadar olan öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7ff2f-122">This example uses the `UdpAnnouncementEndpoint`, which implies that the announcements are multicast to a location specified by that standard endpoint.</span></span>

```csharp
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```

<span data-ttu-id="7ff2f-123">Aşağıdaki örnekte gösterildiği gibi, davranış yapılandırma dosyasında da yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="7ff2f-123">The behavior can be configured in the configuration file as well, as shown in the following example.</span></span>

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

<span data-ttu-id="7ff2f-124">Yukarıdaki örneklerde, bir hizmet otomatik olarak duyuru iletileri gönderecek şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="7ff2f-124">The preceding examples configure a service to automatically send announcement messages.</span></span> <span data-ttu-id="7ff2f-125">Ayrıca, sınıfını kullanarak bildiri iletilerini açıkça de gönderebilirsiniz <xref:System.ServiceModel.Discovery.AnnouncementClient> .</span><span class="sxs-lookup"><span data-stu-id="7ff2f-125">You can also send announcement messages explicitly by using the <xref:System.ServiceModel.Discovery.AnnouncementClient> class.</span></span>

### <a name="announcements-on-the-client"></a><span data-ttu-id="7ff2f-126">Istemcideki Duyurular</span><span class="sxs-lookup"><span data-stu-id="7ff2f-126">Announcements on the Client</span></span>

<span data-ttu-id="7ff2f-127">İstemci uygulaması, Merhaba ve bye iletilerine yanıt vermek ve ve olaylarına abone olmak için bir duyuru hizmeti barındırmalıdır <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> .</span><span class="sxs-lookup"><span data-stu-id="7ff2f-127">A client application must host an announcement service to respond to the Hello and Bye messages and subscribe to the <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> and <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> events.</span></span> <span data-ttu-id="7ff2f-128">Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7ff2f-128">The following example shows how to do this.</span></span>

```csharp
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

<span data-ttu-id="7ff2f-129">Bir Hello veya bye iletisi alındığında, <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> Aşağıdaki örnekte gösterildiği gibi, uç nokta bulgu meta verilerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ff2f-129">When a Hello or Bye message is received, you can access the endpoint discovery metadata through <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> as shown in the following example.</span></span>

```csharp
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
