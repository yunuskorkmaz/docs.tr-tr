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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 36003933a9fb49fe4fe4f0b677ee584066d415ac
ms.sourcegitcommit: ea1fd4ff4c36169fc722ef263e24884c5cd431a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2017
---
# <a name="discovery-announcements-and-announcement-client"></a>Keşif Duyuruları ve Duyuru İstemcisi
[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Bulma özelliği kendi kullanıma sunulduğunu duyurmaktan bileşenleri sağlar. Bunu yapmak için yapılandırılmışsa, bir hizmet Hello ve Bye Duyurular gönderir. İstemcileri veya diğer bileşenleri, bu tür duyuru iletiler için dinleme ve bunlar üzerinde hareket. Bu, istemcilerin hizmetlerin farkında olması alternatif bir yöntem sağlar. Duyuru işlevselliği birkaç kullanımı vardır, örneğin, hizmetleri girin ve bir ağ sık bırakırsanız duyuruları arama hizmetleri için daha iyi bir alternatif olabilir. Bu yaklaşım ağ trafiği azaltılır ve duyuruları alınan hemen istemci varlığının veya hizmetin ayrılma hakkında bilgi edinebilirsiniz.  
  
## <a name="discovery-announcements"></a>Keşif duyuruları  
 Duyuruları için yapılandırılmış bir hizmeti bir ağ birleştirir ve bulunabilirlik olur, kendi kullanılabilirlik dinleme istemcilere Duyurusu Hello ileti gönderir. İleti içerir bulma ilgili hizmet sözleşmesi, uç nokta adresi gibi ilgili bilgileri ve kapsamları. Duyuru iletisi ile gönderilen burada belirtebilirsiniz <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> sınıfı. Duyuru uç nokta ise bir <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> Hello ve Bye uygun şekilde çok noktaya yayın veya tek noktaya yayın duyuruyu uç nokta ise, belirtilen uç noktası doğrudan iletileri gönderilir.  
  
> [!NOTE]
>  Hizmet Konağı açar ve kapandığında duyuruları gönderilir. Bu çağrı düzgün son değil, duyuru iletisi gönderilmemesi. Hizmet hataları Bye Duyurunun ileti gönderilmedi sonra Örneğin.  
  
> [!TIP]
>  Seçtiğiniz her duyuruları göndermenizi sağlayan duyuru işlevselliği özelleştirebilirsiniz.  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]tanımlar <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> ve <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> hizmetler ve kolayca Hello ve Bye duyuruları göndermek için istemcileri izin vermek için standart uç noktaları olarak.  
  
### <a name="announcements-on-the-service"></a>Hizmette duyuruları  
 Duyurular göndermek üzere hizmetini yapılandırmak için ekleyin bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> bir duyuru uç noktası ile. Aşağıdaki örnek programlı olarak bu davranış hizmet ana bilgisayara nasıl ekleneceğini gösterir. Bu örnekte `UdpAnnouncementEndpoint`, duyuruları standart bu bitiş noktası tarafından belirtilen bir konuma çok noktaya yayın anlamına gelir.  
  
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
  
 Önceki örneklerde otomatik olarak duyuru iletileri göndermek üzere bir hizmetini yapılandırın. Ayrıca duyuru iletileri açıkça kullanarak gönderebilirsiniz <xref:System.ServiceModel.Discovery.AnnouncementClient> sınıfı.  
  
### <a name="announcements-on-the-client"></a>İstemci üzerinde duyuruları  
 Bir istemci uygulaması Hello ve Bye iletileri yanıtlayın ve abone olmak üzere bir duyuru hizmet ana bilgisayar <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> ve <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> olaylar. Aşağıdaki örnek bunun nasıl yapılacağı gösterilmektedir.  
  
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
  
 Merhaba veya Bye bir ileti alındığında, uç nokta bulma meta veriler üzerinden erişebilirsiniz <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> aşağıdaki örnekte gösterildiği gibi.  
  
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
