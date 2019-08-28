---
title: Duyuru Örnekleri
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: 1acf51ebe36872424be1e0fdda65a7d18aa737f2
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045791"
---
# <a name="announcements-sample"></a>Duyuru Örnekleri

Bu örnek, bulma özelliğinin duyuru işlevselliğinin nasıl kullanılacağını gösterir. Duyurular, hizmetlerin hizmetle ilgili meta verileri içeren duyuru iletileri göndermesini sağlar. Varsayılan olarak, hizmet başlatıldığında bir Hello duyurusu gönderilir ve hizmet kapandığında bir bye duyurusu gönderilir. Bu duyurular çok noktaya yayın yapabilir veya noktadan noktaya gönderilebilir. Bu örnek iki proje hizmetinden ve istemcisinden oluşur.

## <a name="service"></a>Hizmet

Bu proje, şirket içinde barındırılan bir Hesaplayıcı hizmeti içerir. `Main` Yönteminde bir hizmet ana bilgisayarı oluşturulur ve buna bir hizmet uç noktası eklenir. Ardından, bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> oluşturulur. Duyuruları etkinleştirmek için, ' a bir duyuru uç noktası eklenmelidir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>. Bu durumda, UDP çok noktaya yayın kullanan standart bir uç nokta, duyuru uç noktası olarak eklenir. Bu, duyuruları iyi bilinen bir UDP adresi üzerinden yayınlar.

```csharp
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

Bu projede, istemcisinin bir <xref:System.ServiceModel.Discovery.AnnouncementService>barındırdığını unutmayın. Ayrıca, iki temsilci olaylar ile kaydedilir. Bu olaylar, çevrimiçi ve çevrimdışı Duyurular alındığında istemcinin ne yaptığını belirler.

```csharp
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();

// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;
```

`OnOnlineEvent` Ve`OnOfflineEvent` yöntemleri sırasıyla Merhaba ve bye bildiri iletilerini işler.

```csharp
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

1. Bu örnek HTTP uç noktalarını kullanır ve bu örneği çalıştırmak için uygun URL ACL 'Leri eklenmelidir. Ayrıntılar için bkz. [http ve https 'Yi yapılandırma](https://go.microsoft.com/fwlink/?LinkId=70353) . Yükseltilmiş bir ayrıcalıkta aşağıdaki komutu yürütmek uygun ACL 'Leri eklememelidir. Komutu olduğu gibi çalışmazsa, etki alanınızı ve Kullanıcı adınızı aşağıdaki bağımsız değişkenler için yerine koymak isteyebilirsiniz. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. Çözümü oluşturun.

3. Client. exe uygulamasını çalıştırın.

4. Service. exe uygulamasını çalıştırın. İstemcinin bir çevrimiçi duyuru aldığını aklınızda edin.

5. Service. exe uygulamasını kapatın. İstemcinin çevrimdışı bir duyuru aldığını aklınızda bırakın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`
