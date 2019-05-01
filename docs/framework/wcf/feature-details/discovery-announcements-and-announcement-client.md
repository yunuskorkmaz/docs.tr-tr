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
# <a name="discovery-announcements-and-announcement-client"></a>Keşif Duyuruları ve Duyuru İstemcisi
WCF bulma özelliği, kendi duyurmaktan mutluluk bileşenleri sağlar. Bunu yapmak için yapılandırılmışsa, bir hizmeti Merhaba ve Bye duyuruları gönderir. İstemciler veya diğer bileşenleri, böyle bir duyuru iletiler için dinleme yapan ve bunlar üzerinde harekete. Bu, istemcilerin hizmetleri kullanan alternatif bir yöntem sağlar. Duyuru işlevselliği birkaç kullanımı vardır, örneğin, hizmetleri girin ve bir ağ sık bırakın, duyuruları arama hizmetleri için daha iyi bir alternatif olabilir. Bu yaklaşım ağ trafiği azaltılır ve duyuruları alındıktan hemen sonra istemci varlığı veya hizmetin ayrılma hakkında bilgi edinebilirsiniz.  
  
## <a name="discovery-announcements"></a>Keşif duyuruları  
 Duyuruları için yapılandırılmış bir hizmet bir ağa katılır ve bulunabilir hale gelir, dinleme istemcilere, kullanılabilirlik Duyurusu Hello ileti gönderir. İletisini içeren bulma ilgili sözleşmesi, uç nokta adresi gibi hizmet hakkındaki bilgileri ve kapsamları. Duyurunun ileti ile burada gönderilir belirtebilirsiniz <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> sınıfı. Duyuru uç nokta ise bir <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> Bye ve Hello uygun şekilde çok noktaya yayın veya tek noktaya yayın Duyurusu uç nokta ise belirtilen uç noktaya doğrudan iletiler gönderilir.  
  
> [!NOTE]
>  Hizmet Konağı açar ve kapandığında duyuru gönderilir. Bu çağrılar düzgün bitmeyebilir, duyuru yapılacak gönderilmemesi. Örneğin, Bye Duyurunun ileti gönderilmedi sonra hizmet hataları durumunda.  
  
> [!TIP]
>  Seçtiğiniz her duyuruları göndermenizi sağlayan, duyuru işlevselliği özelleştirebilirsiniz.  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] tanımlar <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> hizmetler ve istemcileri kolayca Merhaba ve Bye duyuruları göndermek için izin vermek için standart uç noktalar olarak.  
  
### <a name="announcements-on-the-service"></a>Hizmet duyuruları  
 Duyurular göndermek üzere hizmetini yapılandırmak için Ekle bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> bir duyuru uç noktası ile. Aşağıdaki örnekte, program aracılığıyla hizmet ana bilgisayarı için bu davranışı eklemek gösterilmektedir. Bu örnekte `UdpAnnouncementEndpoint`, duyuruları bu standart bitiş noktası tarafından belirtilen bir konuma çok noktaya yayın anlamına gelir.  
  
```  
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```  
  
 Aşağıdaki örnekte gösterildiği gibi davranış yanı, yapılandırma dosyasında yapılandırılabilir.  
  
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
  
 Önceki örneklerde otomatik olarak Duyurunun ileti göndermek için bir hizmet yapılandırın. Ayrıca Duyurusu iletileri açıkça kullanarak gönderebilirsiniz <xref:System.ServiceModel.Discovery.AnnouncementClient> sınıfı.  
  
### <a name="announcements-on-the-client"></a>İstemci üzerindeki duyuruları  
 Bir istemci uygulaması Merhaba ve Bye iletileri yanıtlayıp abone için bir Duyurunun hizmeti ana bilgisayar <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> ve <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> olayları. Aşağıdaki örnek bunun nasıl yapılacağı gösterilmektedir.  
  
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
  
 Merhaba veya Bye bir ileti alındığında, uç nokta bulma meta veriler aracılığıyla erişebileceğiniz <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> aşağıdaki örnekte gösterildiği gibi.  
  
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
