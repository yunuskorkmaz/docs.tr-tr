---
title: Keşif Duyuruları ve Duyuru İstemcisi
ms.date: 03/30/2017
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
ms.openlocfilehash: 4ad0b3ea5c257fa3117c426391bd59ad7b560d4f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040176"
---
# <a name="discovery-announcements-and-announcement-client"></a>Keşif Duyuruları ve Duyuru İstemcisi

WCF bulma özelliği, bileşenlerin kullanılabilirliğini duyurmalarını sağlar. Bunu yapmak için yapılandırıldıysa, bir hizmet Hello ve bye duyuruları gönderir. İstemciler veya diğer bileşenler bu tür duyuru iletilerini dinleyebilir ve üzerinde işlem yapabilir. Bu, istemcilerin hizmetlerden haberdar olması için alternatif bir yöntem sağlar. Duyuru işlevselliğinin birçok kullanımı vardır. Örneğin, hizmetler bir ağı girip bir kez daha bırakıyorsanız, Duyurular hizmetler aranırken daha iyi bir alternatif olabilir. Bu yaklaşımda, ağ trafiği azalır ve istemci, Duyurular alındıktan hemen sonra, hizmetin varlığı veya ayrılış hakkında bilgi alabilir.

## <a name="discovery-announcements"></a>Keşif Duyuruları

Duyurular için yapılandırılmış bir hizmet bir ağa katıldığında ve bulunabilir hale geldiğinde, istemcileri dinlemek için kullanılabilirliğini duyuran bir Hello iletisi gönderir. İleti, hizmet hakkında, sözleşme, uç nokta adresi ve ilişkili kapsamlar gibi bulma ile ilgili bilgileri içerir. Duyuru iletisinin <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> sınıf ile nereye gönderileceğini belirtebilirsiniz. Duyuru uç noktası bir <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> ise, Merhaba ve bye çok noktaya yayın ise veya duyuru uç noktası tek noktaya ise, iletiler doğrudan belirtilen uç noktaya gönderilir.

> [!NOTE]
> Duyurular, hizmet ana bilgisayarı açılıp kapandığında gönderilir. Bu çağrılar düzgün tamamlanmazsa, duyuru iletisi gönderilemeyebilir. Örneğin, hizmet hataları varsa, Bye duyuru iletisi gönderilmez.

> [!TIP]
> Duyuru işlevini özelleştirerek, her seçerken Duyurular göndermenize olanak sağlayabilirsiniz.

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]hizmetlerin ve istemcilerin <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> kolayca Hello ve bye duyuruları göndermesini sağlamak için vestandartuçnoktalarıtanımlar.<xref:System.ServiceModel.Discovery.AnnouncementEndpoint>

### <a name="announcements-on-the-service"></a>Hizmette Duyurular

Hizmeti Duyurular gönderecek şekilde yapılandırmak için bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> duyuru uç noktası ekleyin. Aşağıdaki örnek, bu davranışın hizmet ana bilgisayarına programlı bir şekilde nasıl ekleneceğini gösterir. Bu örnek, bildirilerinin `UdpAnnouncementEndpoint`çok noktaya yayın olduğunu belirten, bu standart uç nokta tarafından belirtilen bir konuma kadar olan öğesini kullanır.

```csharp
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```

Aşağıdaki örnekte gösterildiği gibi, davranış yapılandırma dosyasında da yapılandırılabilir.

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

Yukarıdaki örneklerde, bir hizmet otomatik olarak duyuru iletileri gönderecek şekilde yapılandırılır. Ayrıca, <xref:System.ServiceModel.Discovery.AnnouncementClient> sınıfını kullanarak bildiri iletilerini açıkça de gönderebilirsiniz.

### <a name="announcements-on-the-client"></a>Istemcideki Duyurular

İstemci uygulaması, Merhaba ve bye iletilerine yanıt vermek ve <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> ve <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> olaylarına abone olmak için bir duyuru hizmeti barındırmalıdır. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.

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

Bir Hello veya bye iletisi alındığında, aşağıdaki örnekte gösterildiği <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> gibi, uç nokta bulgu meta verilerine erişebilirsiniz.

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
