---
title: Keşif Duyuruları ve Duyuru İstemcisi
ms.date: 03/30/2017
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
ms.openlocfilehash: c32aca5e6deab01423d61c516ee924d00bc041ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856606"
---
# <a name="discovery-announcements-and-announcement-client"></a><span data-ttu-id="077f3-102">Keşif Duyuruları ve Duyuru İstemcisi</span><span class="sxs-lookup"><span data-stu-id="077f3-102">Discovery Announcements and Announcement Client</span></span>
<span data-ttu-id="077f3-103">WCF bulma özelliği, kendi duyurmaktan mutluluk bileşenleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="077f3-103">The WCF discovery feature enables components to announce their availability.</span></span> <span data-ttu-id="077f3-104">Bunu yapmak için yapılandırılmışsa, bir hizmeti Merhaba ve Bye duyuruları gönderir.</span><span class="sxs-lookup"><span data-stu-id="077f3-104">If configured to do so, a service sends Hello and Bye announcements.</span></span> <span data-ttu-id="077f3-105">İstemciler veya diğer bileşenleri, böyle bir duyuru iletiler için dinleme yapan ve bunlar üzerinde harekete.</span><span class="sxs-lookup"><span data-stu-id="077f3-105">Clients or other components can listen for such announcement messages and act on them.</span></span> <span data-ttu-id="077f3-106">Bu, istemcilerin hizmetleri kullanan alternatif bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="077f3-106">This provides an alternative method for clients to be aware of services.</span></span> <span data-ttu-id="077f3-107">Duyuru işlevselliği birkaç kullanımı vardır, örneğin, hizmetleri girin ve bir ağ sık bırakın, duyuruları arama hizmetleri için daha iyi bir alternatif olabilir.</span><span class="sxs-lookup"><span data-stu-id="077f3-107">Announcement functionality has several uses, for example, if the services enter and leave a network frequently, announcements may be a better alternative than searching for services.</span></span> <span data-ttu-id="077f3-108">Bu yaklaşım ağ trafiği azaltılır ve duyuruları alındıktan hemen sonra istemci varlığı veya hizmetin ayrılma hakkında bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="077f3-108">With this approach, the network traffic is reduced and the client can learn about the presence or departure of the service as soon as announcements are received.</span></span>  
  
## <a name="discovery-announcements"></a><span data-ttu-id="077f3-109">Keşif duyuruları</span><span class="sxs-lookup"><span data-stu-id="077f3-109">Discovery Announcements</span></span>  
 <span data-ttu-id="077f3-110">Duyuruları için yapılandırılmış bir hizmet bir ağa katılır ve bulunabilir hale gelir, dinleme istemcilere, kullanılabilirlik Duyurusu Hello ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="077f3-110">When a service configured for announcements joins a network and becomes discoverable, it sends a Hello message announcing its availability to listening clients.</span></span> <span data-ttu-id="077f3-111">İletisini içeren bulma ilgili sözleşmesi, uç nokta adresi gibi hizmet hakkındaki bilgileri ve kapsamları.</span><span class="sxs-lookup"><span data-stu-id="077f3-111">The message contains discovery related information about the service, such as its contract, endpoint address and associated scopes.</span></span> <span data-ttu-id="077f3-112">Duyurunun ileti ile burada gönderilir belirtebilirsiniz <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="077f3-112">You can specify where the announcement message is sent with the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> class.</span></span> <span data-ttu-id="077f3-113">Duyuru uç nokta ise bir <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> Bye ve Hello uygun şekilde çok noktaya yayın veya tek noktaya yayın Duyurusu uç nokta ise belirtilen uç noktaya doğrudan iletiler gönderilir.</span><span class="sxs-lookup"><span data-stu-id="077f3-113">If the announcement endpoint is a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> then the Hello and Bye are multicast appropriately, or if the announcement endpoint is unicast, the messages are sent directly to the specified endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="077f3-114">Hizmet Konağı açar ve kapandığında duyuru gönderilir.</span><span class="sxs-lookup"><span data-stu-id="077f3-114">Announcements are sent when the service host opens and closes.</span></span> <span data-ttu-id="077f3-115">Bu çağrılar düzgün bitmeyebilir, duyuru yapılacak gönderilmemesi. Örneğin, Bye Duyurunun ileti gönderilmedi sonra hizmet hataları durumunda.</span><span class="sxs-lookup"><span data-stu-id="077f3-115">If these calls do not finish properly the announcement message may not be sent out. For example if the service faults, then the Bye announcement message is not sent.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="077f3-116">Seçtiğiniz her duyuruları göndermenizi sağlayan, duyuru işlevselliği özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="077f3-116">You can customize the announcement functionality, allowing you to send announcements whenever you choose.</span></span>  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="077f3-117">tanımlar <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> hizmetler ve istemcileri kolayca Merhaba ve Bye duyuruları göndermek için izin vermek için standart uç noktalar olarak.</span><span class="sxs-lookup"><span data-stu-id="077f3-117">defines the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> and <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> as standard endpoints to allow services and clients to easily send Hello and Bye announcements.</span></span>  
  
### <a name="announcements-on-the-service"></a><span data-ttu-id="077f3-118">Hizmet duyuruları</span><span class="sxs-lookup"><span data-stu-id="077f3-118">Announcements on the Service</span></span>  
 <span data-ttu-id="077f3-119">Duyurular göndermek üzere hizmetini yapılandırmak için Ekle bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> bir duyuru uç noktası ile.</span><span class="sxs-lookup"><span data-stu-id="077f3-119">To configure the service to send announcements, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> with an announcement endpoint.</span></span> <span data-ttu-id="077f3-120">Aşağıdaki örnekte, program aracılığıyla hizmet ana bilgisayarı için bu davranışı eklemek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="077f3-120">The following example shows how to programmatically add this behavior to the service host.</span></span> <span data-ttu-id="077f3-121">Bu örnekte `UdpAnnouncementEndpoint`, duyuruları bu standart bitiş noktası tarafından belirtilen bir konuma çok noktaya yayın anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="077f3-121">This example uses the `UdpAnnouncementEndpoint`, which implies that the announcements are multicast to a location specified by that standard endpoint.</span></span>  
  
```  
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```  
  
 <span data-ttu-id="077f3-122">Aşağıdaki örnekte gösterildiği gibi davranış yanı, yapılandırma dosyasında yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="077f3-122">The behavior can be configured in the configuration file as well, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="077f3-123">Önceki örneklerde otomatik olarak Duyurunun ileti göndermek için bir hizmet yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="077f3-123">The preceding examples configure a service to automatically send announcement messages.</span></span> <span data-ttu-id="077f3-124">Ayrıca Duyurusu iletileri açıkça kullanarak gönderebilirsiniz <xref:System.ServiceModel.Discovery.AnnouncementClient> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="077f3-124">You can also send announcement messages explicitly by using the <xref:System.ServiceModel.Discovery.AnnouncementClient> class.</span></span>  
  
### <a name="announcements-on-the-client"></a><span data-ttu-id="077f3-125">İstemci üzerindeki duyuruları</span><span class="sxs-lookup"><span data-stu-id="077f3-125">Announcements on the Client</span></span>  
 <span data-ttu-id="077f3-126">Bir istemci uygulaması Merhaba ve Bye iletileri yanıtlayıp abone için bir Duyurunun hizmeti ana bilgisayar <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> ve <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> olayları.</span><span class="sxs-lookup"><span data-stu-id="077f3-126">A client application must host an announcement service to respond to the Hello and Bye messages and subscribe to the <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> and <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> events.</span></span> <span data-ttu-id="077f3-127">Aşağıdaki örnek bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="077f3-127">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="077f3-128">Merhaba veya Bye bir ileti alındığında, uç nokta bulma meta veriler aracılığıyla erişebileceğiniz <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="077f3-128">When a Hello or Bye message is received, you can access the endpoint discovery metadata through <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> as shown in the following example.</span></span>  
  
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
