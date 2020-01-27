---
title: Duyuru Örnekleri
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: c3824fb0dc7ab4169c309d1a5154127d6bc3b78f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747005"
---
# <a name="announcements-sample"></a>Duyuru Örnekleri

Bu örnek, bulma özelliğinin duyuru işlevselliğinin nasıl kullanılacağını gösterir. Duyurular, hizmetlerin hizmetle ilgili meta verileri içeren duyuru iletileri göndermesini sağlar. Varsayılan olarak, hizmet başlatıldığında bir Hello duyurusu gönderilir ve hizmet kapandığında bir bye duyurusu gönderilir. Bu duyurular çok noktaya yayın yapabilir veya noktadan noktaya gönderilebilir. Bu örnek iki proje hizmetinden ve istemcisinden oluşur.

## <a name="service"></a>Hizmet

Bu proje, şirket içinde barındırılan bir Hesaplayıcı hizmeti içerir. `Main` yönteminde bir hizmet ana bilgisayarı oluşturulur ve buna bir hizmet uç noktası eklenir. Sonra bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> oluşturulur. Duyuruları etkinleştirmek için <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>bir duyuru uç noktası eklenmelidir. Bu durumda, UDP çok noktaya yayın kullanan standart bir uç nokta, duyuru uç noktası olarak eklenir. Bu, duyuruları iyi bilinen bir UDP adresi üzerinden yayınlar.

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

Bu projede, istemcinin bir <xref:System.ServiceModel.Discovery.AnnouncementService>barındırdığını unutmayın. Ayrıca, iki temsilci olaylar ile kaydedilir. Bu olaylar, çevrimiçi ve çevrimdışı Duyurular alındığında istemcinin ne yaptığını belirler.

```csharp
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();

// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;
```

`OnOnlineEvent` ve `OnOfflineEvent` yöntemleri sırasıyla Merhaba ve bye bildiri iletilerini işler.

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

1. Bu örnek HTTP uç noktalarını kullanır ve bu örneği çalıştırmak için uygun URL ACL 'Leri eklenmelidir. Daha fazla bilgi için bkz. [http ve https yapılandırma](../feature-details/configuring-http-and-https.md). Yükseltilmiş bir ayrıcalıkta aşağıdaki komutu yürütmek uygun ACL 'Leri eklememelidir. Komutu olduğu gibi çalışmazsa, etki alanınızı ve Kullanıcı adınızı aşağıdaki bağımsız değişkenler için yerine koymak isteyebilirsiniz. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. Çözümü oluşturun.

3. Client. exe uygulamasını çalıştırın.

4. Service. exe uygulamasını çalıştırın. İstemcinin bir çevrimiçi duyuru aldığını aklınızda edin.

5. Service. exe uygulamasını kapatın. İstemcinin çevrimdışı bir duyuru aldığını aklınızda bırakın.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`
