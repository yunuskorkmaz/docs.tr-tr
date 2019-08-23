---
title: Keşif Duyuruları ve Duyuru İstemcisi
ms.date: 03/30/2017
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
ms.openlocfilehash: 74362343dc1fd5df6d1b91537f7fed5bc08f8fe0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968823"
---
# <a name="discovery-announcements-and-announcement-client"></a><span data-ttu-id="6b978-102">Keşif Duyuruları ve Duyuru İstemcisi</span><span class="sxs-lookup"><span data-stu-id="6b978-102">Discovery Announcements and Announcement Client</span></span>
<span data-ttu-id="6b978-103">WCF bulma özelliği, bileşenlerin kullanılabilirliğini duyurmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b978-103">The WCF discovery feature enables components to announce their availability.</span></span> <span data-ttu-id="6b978-104">Bunu yapmak için yapılandırıldıysa, bir hizmet Hello ve bye duyuruları gönderir.</span><span class="sxs-lookup"><span data-stu-id="6b978-104">If configured to do so, a service sends Hello and Bye announcements.</span></span> <span data-ttu-id="6b978-105">İstemciler veya diğer bileşenler bu tür duyuru iletilerini dinleyebilir ve üzerinde işlem yapabilir.</span><span class="sxs-lookup"><span data-stu-id="6b978-105">Clients or other components can listen for such announcement messages and act on them.</span></span> <span data-ttu-id="6b978-106">Bu, istemcilerin hizmetlerden haberdar olması için alternatif bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="6b978-106">This provides an alternative method for clients to be aware of services.</span></span> <span data-ttu-id="6b978-107">Duyuru işlevselliğinin birçok kullanımı vardır. Örneğin, hizmetler bir ağı girip bir kez daha bırakıyorsanız, Duyurular hizmetler aranırken daha iyi bir alternatif olabilir.</span><span class="sxs-lookup"><span data-stu-id="6b978-107">Announcement functionality has several uses, for example, if the services enter and leave a network frequently, announcements may be a better alternative than searching for services.</span></span> <span data-ttu-id="6b978-108">Bu yaklaşımda, ağ trafiği azalır ve istemci, Duyurular alındıktan hemen sonra, hizmetin varlığı veya ayrılış hakkında bilgi alabilir.</span><span class="sxs-lookup"><span data-stu-id="6b978-108">With this approach, the network traffic is reduced and the client can learn about the presence or departure of the service as soon as announcements are received.</span></span>  
  
## <a name="discovery-announcements"></a><span data-ttu-id="6b978-109">Keşif Duyuruları</span><span class="sxs-lookup"><span data-stu-id="6b978-109">Discovery Announcements</span></span>  
 <span data-ttu-id="6b978-110">Duyurular için yapılandırılmış bir hizmet bir ağa katıldığında ve bulunabilir hale geldiğinde, istemcileri dinlemek için kullanılabilirliğini duyuran bir Hello iletisi gönderir.</span><span class="sxs-lookup"><span data-stu-id="6b978-110">When a service configured for announcements joins a network and becomes discoverable, it sends a Hello message announcing its availability to listening clients.</span></span> <span data-ttu-id="6b978-111">İleti, hizmet hakkında, sözleşme, uç nokta adresi ve ilişkili kapsamlar gibi bulma ile ilgili bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="6b978-111">The message contains discovery related information about the service, such as its contract, endpoint address and associated scopes.</span></span> <span data-ttu-id="6b978-112">Duyuru iletisinin <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> sınıf ile nereye gönderileceğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b978-112">You can specify where the announcement message is sent with the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> class.</span></span> <span data-ttu-id="6b978-113">Duyuru uç noktası bir <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> ise, Merhaba ve bye çok noktaya yayın ise veya duyuru uç noktası tek noktaya ise, iletiler doğrudan belirtilen uç noktaya gönderilir.</span><span class="sxs-lookup"><span data-stu-id="6b978-113">If the announcement endpoint is a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> then the Hello and Bye are multicast appropriately, or if the announcement endpoint is unicast, the messages are sent directly to the specified endpoint.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6b978-114">Duyurular, hizmet ana bilgisayarı açılıp kapandığında gönderilir.</span><span class="sxs-lookup"><span data-stu-id="6b978-114">Announcements are sent when the service host opens and closes.</span></span> <span data-ttu-id="6b978-115">Bu çağrılar düzgün tamamlanmazsa, duyuru iletisi gönderilemeyebilir. Örneğin, hizmet hataları varsa, Bye duyuru iletisi gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="6b978-115">If these calls do not finish properly the announcement message may not be sent out. For example if the service faults, then the Bye announcement message is not sent.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="6b978-116">Duyuru işlevini özelleştirerek, her seçerken Duyurular göndermenize olanak sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b978-116">You can customize the announcement functionality, allowing you to send announcements whenever you choose.</span></span>  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="6b978-117">hizmetlerin ve istemcilerin <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> kolayca Hello ve bye duyuruları göndermesini sağlamak için vestandartuçnoktalarıtanımlar.<xref:System.ServiceModel.Discovery.AnnouncementEndpoint></span><span class="sxs-lookup"><span data-stu-id="6b978-117">defines the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> and <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> as standard endpoints to allow services and clients to easily send Hello and Bye announcements.</span></span>  
  
### <a name="announcements-on-the-service"></a><span data-ttu-id="6b978-118">Hizmette Duyurular</span><span class="sxs-lookup"><span data-stu-id="6b978-118">Announcements on the Service</span></span>  
 <span data-ttu-id="6b978-119">Hizmeti Duyurular gönderecek şekilde yapılandırmak için bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> duyuru uç noktası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6b978-119">To configure the service to send announcements, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> with an announcement endpoint.</span></span> <span data-ttu-id="6b978-120">Aşağıdaki örnek, bu davranışın hizmet ana bilgisayarına programlı bir şekilde nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b978-120">The following example shows how to programmatically add this behavior to the service host.</span></span> <span data-ttu-id="6b978-121">Bu örnek, bildirilerinin `UdpAnnouncementEndpoint`çok noktaya yayın olduğunu belirten, bu standart uç nokta tarafından belirtilen bir konuma kadar olan öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6b978-121">This example uses the `UdpAnnouncementEndpoint`, which implies that the announcements are multicast to a location specified by that standard endpoint.</span></span>  
  
```  
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```  
  
 <span data-ttu-id="6b978-122">Aşağıdaki örnekte gösterildiği gibi, davranış yapılandırma dosyasında da yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="6b978-122">The behavior can be configured in the configuration file as well, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="6b978-123">Yukarıdaki örneklerde, bir hizmet otomatik olarak duyuru iletileri gönderecek şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="6b978-123">The preceding examples configure a service to automatically send announcement messages.</span></span> <span data-ttu-id="6b978-124">Ayrıca, <xref:System.ServiceModel.Discovery.AnnouncementClient> sınıfını kullanarak bildiri iletilerini açıkça de gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b978-124">You can also send announcement messages explicitly by using the <xref:System.ServiceModel.Discovery.AnnouncementClient> class.</span></span>  
  
### <a name="announcements-on-the-client"></a><span data-ttu-id="6b978-125">Istemcideki Duyurular</span><span class="sxs-lookup"><span data-stu-id="6b978-125">Announcements on the Client</span></span>  
 <span data-ttu-id="6b978-126">İstemci uygulaması, Merhaba ve bye iletilerine yanıt vermek ve <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> ve <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> olaylarına abone olmak için bir duyuru hizmeti barındırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6b978-126">A client application must host an announcement service to respond to the Hello and Bye messages and subscribe to the <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> and <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> events.</span></span> <span data-ttu-id="6b978-127">Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6b978-127">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="6b978-128">Bir Hello veya bye iletisi alındığında, aşağıdaki örnekte gösterildiği <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> gibi, uç nokta bulgu meta verilerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b978-128">When a Hello or Bye message is received, you can access the endpoint discovery metadata through <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> as shown in the following example.</span></span>  
  
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
