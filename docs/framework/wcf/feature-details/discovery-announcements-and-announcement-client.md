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
# <a name="discovery-announcements-and-announcement-client"></a>Keşif Duyuruları ve Duyuru İstemcisi

WCF bulma özelliği, bileşenlerin kullanılabilirliğini duyurmalarını sağlar. Bunu yapmak için yapılandırıldıysa, bir hizmet Hello ve bye duyuruları gönderir. İstemciler veya diğer bileşenler bu tür duyuru iletilerini dinleyebilir ve üzerinde işlem yapabilir. Bu, istemcilerin hizmetlerden haberdar olması için alternatif bir yöntem sağlar. Duyuru işlevselliğinin birçok kullanımı vardır. Örneğin, hizmetler bir ağı girip bir kez daha bırakıyorsanız, Duyurular hizmetler aranırken daha iyi bir alternatif olabilir. Bu yaklaşımda, ağ trafiği azalır ve istemci, Duyurular alındıktan hemen sonra, hizmetin varlığı veya ayrılış hakkında bilgi alabilir.

## <a name="discovery-announcements"></a>Keşif Duyuruları

Duyurular için yapılandırılmış bir hizmet bir ağa katıldığında ve bulunabilir hale geldiğinde, istemcileri dinlemek için kullanılabilirliğini duyuran bir Hello iletisi gönderir. İleti, hizmet hakkında, sözleşme, uç nokta adresi ve ilişkili kapsamlar gibi bulma ile ilgili bilgileri içerir. Duyuru iletisinin sınıf ile nereye gönderileceğini belirtebilirsiniz <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> . Duyuru uç noktası bir ise, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> Merhaba ve bye çok noktaya yayın ise veya duyuru uç noktası tek noktaya ise, iletiler doğrudan belirtilen uç noktaya gönderilir.

> [!NOTE]
> Duyurular, hizmet ana bilgisayarı açılıp kapandığında gönderilir. Bu çağrılar düzgün tamamlanmazsa, duyuru iletisi gönderilemeyebilir. Örneğin, hizmet hataları varsa, Bye duyuru iletisi gönderilmez.

> [!TIP]
> Duyuru işlevini özelleştirerek, her seçerken Duyurular göndermenize olanak sağlayabilirsiniz.

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<xref:System.ServiceModel.Discovery.AnnouncementEndpoint> <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> hizmetlerin ve Istemcilerin kolayca Hello ve bye duyuruları göndermesini sağlamak için ve standart uç noktaları tanımlar.

### <a name="announcements-on-the-service"></a>Hizmette Duyurular

Hizmeti Duyurular gönderecek şekilde yapılandırmak için bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> duyuru uç noktası ekleyin. Aşağıdaki örnek, bu davranışın hizmet ana bilgisayarına programlı bir şekilde nasıl ekleneceğini gösterir. Bu örnek, `UdpAnnouncementEndpoint` bildirilerinin çok noktaya yayın olduğunu belirten, bu standart uç nokta tarafından belirtilen bir konuma kadar olan öğesini kullanır.

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

Yukarıdaki örneklerde, bir hizmet otomatik olarak duyuru iletileri gönderecek şekilde yapılandırılır. Ayrıca, sınıfını kullanarak bildiri iletilerini açıkça de gönderebilirsiniz <xref:System.ServiceModel.Discovery.AnnouncementClient> .

### <a name="announcements-on-the-client"></a>Istemcideki Duyurular

İstemci uygulaması, Merhaba ve bye iletilerine yanıt vermek ve ve olaylarına abone olmak için bir duyuru hizmeti barındırmalıdır <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> . Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.

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

Bir Hello veya bye iletisi alındığında, <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> Aşağıdaki örnekte gösterildiği gibi, uç nokta bulgu meta verilerine erişebilirsiniz.

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
