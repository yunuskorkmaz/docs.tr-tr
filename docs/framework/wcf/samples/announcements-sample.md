---
title: Duyuru Örnekleri
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: a82056844c9ec8f77bce4b0adec481a025894d1f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43749268"
---
# <a name="announcements-sample"></a>Duyuru Örnekleri
Bu örnek bulma özelliğinin duyuru işlevini nasıl kullanacağınızı gösterir. Duyurular hizmeti hakkında meta veriler içeren bir Duyurunun ileti göndermek için izin verin. Varsayılan olarak, hizmet başlatıldığı ve hizmet kapatıldığında bye duyuru gönderilir hello duyuru gönderilir. Bu duyurular çok noktaya yayın veya noktadan noktaya gönderilebilir. Bu örnek, iki proje hizmeti ve istemci oluşur.  
  
## <a name="service"></a>Hizmet  
 Bu proje, şirket içinde barındırılan hesaplayıcı hizmet içerir. İçinde `Main` yöntemi, bir hizmet konağı oluşturulur ve bir hizmet uç noktası eklenir. Ardından, bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> oluşturulur. Duyurular etkinleştirmek için bir Duyurunun bitiş noktası eklenmelidir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>. Bu durumda UDP çok noktaya yayın kullanarak bir standart uç nokta duyuru uç noktası olarak eklenir. Bu, iyi bilinen bir UDP adresi duyurularını yayınlar.  
  
```  
Uri baseAddress = new Uri("http://localhost:8000/" + Guid.NewGuid().ToString());  
  
// Create a ServiceHost for the CalculatorService type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
{  
     serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new WSHttpBinding(), String.Empty);  
  
     ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();  
  
     // Announce the availability of the service over UDP multicast  
    serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());  
  
    // Make the service discoverable over UDP multicast.  
    serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);                  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    serviceHost.Open();  
    // ...  
}  
```  
  
## <a name="client"></a>İstemci  
 Bu projede unutmayın istemci konakları bir <xref:System.ServiceModel.Discovery.AnnouncementService>. Ayrıca, iki temsilci olduğunda olayları ile kaydedilir. Bu olayları, istemcinin çevrimiçi ve çevrimdışı duyuruları alındığında ne yaptığını gerektirir.  
  
```  
// Create an AnnouncementService instance  
AnnouncementService announcementService = new AnnouncementService();  
  
// Subscribe the announcement events  
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;  
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;  
```  
  
 `OnOnlineEvent` Ve `OnOfflineEvent` yöntemleri işleyen Merhaba ve bye duyuru iletileri sırasıyla.  
  
```  
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)  
{  
    Console.WriteLine();              
    Console.WriteLine("Received an online announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);  
PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);  
}  
  
static void OnOfflineEvent(object sender, AnnouncementEventArgs e)  
{  
    Console.WriteLine();  
    Console.WriteLine("Received an offline announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);  
            PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);  
}  
```  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Bu örnek HTTP uç noktaları kullanır ve bu örnek, uygun URL ACL çalıştırmak için bkz: eklenmelidir [yapılandırma HTTP ve HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) Ayrıntılar için. Aşağıdaki komut bir yükseltilmiş ayrıcalık yürütme uygun ACL'lerin eklemeniz gerekir. Olduğu gibi bir komut çalışmazsa, aşağıdaki bağımsız değişkenler yerine etki alanı ve kullanıcı adı isteyebilirsiniz. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Çözümü oluşturun.  
  
3.  Client.exe uygulamayı çalıştırın.  
  
4.  Service.exe uygulamayı çalıştırın. İstemci çevrimiçi duyuruyu alır unutmayın.  
  
5.  Service.exe uygulamayı kapatın. Not istemci çevrimdışı duyuruyu alır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`  
  
## <a name="see-also"></a>Ayrıca Bkz.
