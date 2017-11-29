---
title: "Duyuru Örnekleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 05e2c45b66f92229877ac3ec867da9b71cd4156a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="announcements-sample"></a>Duyuru Örnekleri
Bu örnek duyuru işlevselliğinin bulma özelliğinin nasıl kullanılacağını gösterir. Duyurular, hizmet hakkındaki meta verileri içeren duyuru iletilerini göndermek hizmetler sağlar. Varsayılan olarak, hizmet başlatıldığında ve hizmet kapatıldığında bye duyuru gönderilen hello duyuru gönderilir. Noktadan noktaya gönderilen veya bu Duyurular çok noktaya yayın olabilir. Bu örnek iki proje hizmet ve istemci oluşur.  
  
## <a name="service"></a>Hizmet  
 Bu proje bir kendi kendini barındıran hesaplayıcı hizmeti içerir. İçinde `Main` yöntemi, bir hizmet ana bilgisayarı oluşturulur ve hizmet uç noktası için eklenir. Ardından, bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> oluşturulur. Duyurular etkinleştirmek için bir duyuru uç noktası eklenmelidir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>. Bu durumda çok noktaya yayın UDP kullanan standart bir uç nokta duyuru uç noktası olarak eklenir. Bu, iyi bilinen bir UDP adresi duyuruları yayınlar.  
  
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
 Bu projede unutmayın istemci konakları bir <xref:System.ServiceModel.Discovery.AnnouncementService>. Ayrıca, iki temsilciler olayı kaydedilir. Bu olaylar, çevrimiçi ve çevrimdışı duyuruları alındığında istemcinin ne yaptığını dikte.  
  
```  
// Create an AnnouncementService instance  
AnnouncementService announcementService = new AnnouncementService();  
  
// Subscribe the announcement events  
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;  
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;  
```  
  
 `OnOnlineEvent` Ve `OnOfflineEvent` yöntemlerini işlemek hello ve bye duyuru iletileri sırasıyla.  
  
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
  
1.  Bu örnek HTTP uç noktaları kullanır ve bu örnek, uygun URL ACL çalıştırmak için bkz: eklenmelidir [yapılandırma HTTP ve HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) Ayrıntılar için. Aşağıdaki komutu yükseltilmiş ayrıcalık yürütme uygun ACL'ler eklemeniz gerekir. Komut olduğu gibi çalışmazsa, etki alanı ve kullanıcı adı şu bağımsız değişkenleri yerine isteyebilirsiniz. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Çözümü oluşturun.  
  
3.  Client.exe uygulamayı çalıştırın.  
  
4.  Service.exe uygulamayı çalıştırın. İstemci çevrimiçi duyuru alır unutmayın.  
  
5.  Service.exe uygulamayı kapatın. Not istemci çevrimdışı duyuru alır.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`  
  
## <a name="see-also"></a>Ayrıca Bkz.
