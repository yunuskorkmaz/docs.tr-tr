---
title: WCF Keşif Genel Bakış
ms.date: 03/30/2017
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
ms.openlocfilehash: 449d54e0dd1948885a7298fb4da46067de3eb9d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184208"
---
# <a name="wcf-discovery-overview"></a>WCF Keşif Genel Bakış
Discovery API'leri, WS-Discovery protokolünü kullanarak Web hizmetlerinin dinamik olarak yayımlanması ve keşfi için birleşik bir programlama modeli sağlar. Bu API'ler, hizmetlerin kendilerini ve istemcilerini yayımlayabilmeleri için yayımlanmış hizmetleri bulmalarına olanak sağlar. Bir hizmet keşfedilebilir hale getirildikten sonra, hizmet duyuru iletileri göndermenin yanı sıra keşif isteklerini dinleyebilir ve yanıtverebilir. Keşfedilebilir hizmetler, bir ağa gelişlerini duyurmak için Merhaba mesajları gönderebilir ve bir ağdan ayrıldıklarını duyurmak için Bye mesajları gönderebilir. Bir hizmeti bulmak için `Probe` istemciler, ağdaki hizmet sözleşmesi türü, anahtar kelimeler ve kapsam gibi belirli ölçütleri içeren bir istek gönderir. Hizmetler `Probe` isteği alır ve ölçütlerine uyup uymadığını belirler. Bir hizmet eşleşirse, hizmetle iletişim kurmak için gerekli bilgileri istemciye geri göndererek `ProbeMatch` yanıt verir. İstemciler, `Resolve` bitiş noktası adreslerini değiştirmiş olabilecek hizmetleri bulmalarına izin veren istekler de gönderebilir. Eşleşen hizmetler `Resolve` istemciye bir `ResolveMatch` ileti göndererek istekleri yanıtlar.  
  
## <a name="ad-hoc-and-managed-modes"></a>Ad-Hoc ve Yönetilen Modlar  
 Discovery API iki farklı modu destekler: Yönetilen ve Ad-Hoc. Yönetilen modda, kullanılabilir hizmetler hakkında bilgi tutan bir bulma proxy'si adı verilen merkezi bir sunucu vardır. Keşif proxy çeşitli şekillerde hizmetler hakkında bilgi ile doldurulabilir. Örneğin, hizmetler bulma proxy'sine başlatma sırasında duyuru iletileri gönderebilir veya proxy hangi hizmetlerin kullanılabilir olduğunu belirlemek için bir veritabanından veya yapılandırma dosyasından verileri okuyabilir. Keşif proxy'sinin nasıl doldurulur tamamen geliştiriciye bağlıdır. İstemciler kullanılabilir hizmetler hakkında bilgi almak için bulma proxy'sini kullanır. İstemci bir hizmeti aradığında, `Probe` bulma proxy'sine bir ileti gönderir ve proxy, bildiği hizmetlerden herhangi birinin istemcinin aradığı hizmetle eşleşip eşleşmediğini belirler. Eşleşmeler varsa, keşif proxy'si istemciye bir `ProbeMatch` yanıt gönderir. İstemci daha sonra proxy'den döndürülen hizmet bilgilerini kullanarak doğrudan hizmetle iletişim kurabilir. Yönetilen moduarkasındaki temel ilke, keşif isteklerinin tek bir yetkiliye, keşif proxy'sine tek tek bir şekilde gönderilmesidir. .NET Framework, kendi proxy'nizi oluşturmanıza olanak tanıyan önemli bileşenler içerir. İstemciler ve hizmetler proxy'yi birden çok yöntemle bulabilir:  
  
- Proxy geçici iletilere yanıt verebilir.  
  
- Proxy başlatma sırasında bir duyuru iletisi gönderebilir.  
  
- İstemciler ve hizmetler belirli bir iyi bilinen bitiş noktası aramak için yazılabilir.  
  
 Ad-Hoc modunda merkezi sunucu yoktur. Hizmet duyuruları ve istemci istekleri gibi tüm keşif iletileri çok noktaya yayın la gönderilir. Varsayılan olarak .NET Framework UDP protokolü üzerinden Ad-Hoc bulma desteği içerir. Örneğin, bir hizmet başlangıç'ta Merhaba duyurusu gönderecek şekilde yapılandırılırsa, bunu UDP protokolünü kullanarak tanınmış, çok noktaya yayın adresi üzerinden gönderir. Müşteriler aktif olarak bu duyurular için dinlemek ve buna göre bunları işlemek zorunda. İstemci bir `Probe` hizmet için ileti gönderdiğinde, çok noktaya yayın protokolü kullanılarak ağ üzerinden gönderilir. İsteğe sahip her hizmet, `Probe` iletideki ölçütlerle eşleşip eşleşmediğini belirler `ProbeMatch` ve hizmet `Probe` iletide belirtilen ölçütlerle eşleşirse doğrudan istemciye bir iletiyle yanıt verir.  
  
## <a name="benefits-of-using-wcf-discovery"></a>WCF Discovery Kullanmanın Faydaları  
 WCF Discovery, WS-Discovery protokolü kullanılarak uygulandığından, WS-Discovery'yi uygulayan diğer istemciler, hizmetler ve diğer kişilerle birlikte çalışabilir. WCF Discovery, varolan hizmetlerinize ve müşterilerinize Discovery işlevselliği eklemeyi kolaylaştıran mevcut WCF API'leri üzerine kuruludur. Hizmet bulunabilirliği uygulama yapılandırma ayarları aracılığıyla kolayca eklenebilir. Buna ek olarak, WCF Discovery ayrıca eş ağı, adlandırma bindirme ve HTTP gibi diğer aktarımlar üzerinde bulma protokolü nün kullanılmasını da destekler. WCF Discovery, bir keşif proxy'sinin kullanıldığı Yönetilen bir işlem modu için destek sağlar. İletiler tüm ağa çok noktaya yayın göndermek yerine doğrudan bulma proxy'sine gönderildiğinde bu ağ trafiğini azaltabilir. WCF Discovery, Web hizmetleriyle çalışırken daha fazla esneklik sağlar. Örneğin, istemciyi veya hizmeti yeniden yapılandırmak zorunda kalmadan bir hizmetin adresini değiştirebilirsiniz. İstemci hizmete erişmesi gerektiğinde, `Probe` bir `Find` istek aracılığıyla bir ileti verebilir ve hizmetin geçerli adresiyle yanıt vermesine bekleyebilir. WCF Discovery, istemcinin sözleşme türleri, bağlama öğeleri, ad alanı, kapsam ve anahtar kelimeler veya sürüm numaraları gibi farklı ölçütlere dayalı bir hizmeti aramasına olanak tanır. WCF Discovery çalışma zamanı ve tasarım zamanı bulma sağlar. Uygulamanıza keşif ekleme, hata toleransı ve otomatik yapılandırma gibi diğer senaryoları etkinleştirmek için kullanılabilir.  
  
## <a name="service-publication"></a>Hizmet Yayını  
 Bir hizmeti bulunabilir kılmak <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> için hizmet ana bilgisayara bir ekleme ve keşif iletilerinin nerede dinleneceğini belirtmek için bir keşif bitiş noktası nın eklenmesi gerekir. Aşağıdaki kod örneği, kendi kendine barındırılan bir hizmetin keşfedilebilir hale getirmek için nasıl değiştirilebileceği gösterilmektedir.  
  
```csharp  
Uri baseAddress = new Uri($"http://{System.Net.Dns.GetHostName()}:8000/discovery/scenarios/calculatorservice/{Guid.NewGuid().ToString()}/");

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
 Hizmetin <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> bulunabilmesi için bir hizmet açıklamasına bir örnek eklenmelidir. Hizmete keşif isteklerini nerede dinleyeceğini söylemek için servis ana bilgisayara bir <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> örnek eklenmelidir. Bu örnekte, <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> hizmetin UDP çok noktaya yayın aktarımı üzerinden keşif isteklerini dinlemesi gerektiğini belirtmek için bir (türetilmiş) <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>eklenir. Tüm <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> iletiler çok noktaya yayın bir şekilde gönderildiğinden, Ad-Hoc keşfi için kullanılır.  
  
## <a name="announcement"></a>Duyuru  
 Varsayılan olarak, hizmet yayını duyuru iletileri göndermez. Hizmet, duyuru iletileri gönderecek şekilde yapılandırılmalıdır. Bu, hizmeti keşif iletilerini dinlemekten ayrı olarak duyurabildiklerinden, hizmet yazarları için ek esneklik sağlar. Hizmet duyurusu, bir keşif proxy'si veya diğer hizmet kayıtlarıyla hizmetleri kaydetmek için bir mekanizma olarak da kullanılabilir. Aşağıdaki kod, bir UDP bağlama üzerinden duyuru iletileri göndermek için bir hizmetin nasıl yapılandırılabildiğini gösterir.  
  
```csharp  
Uri baseAddress = new Uri($"http://{System.Net.Dns.GetHostName()}:8000/discovery/scenarios/calculatorservice/{Guid.NewGuid().ToString()}/");

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    ServiceDiscoveryBehavior discoveryBehavior = new ServiceDiscoveryBehavior();
    serviceHost.Description.Behaviors.Add(discoveryBehavior);

    // Send announcements on UDP multicast transport
    discoveryBehavior.AnnouncementEndpoints.Add(
      new UdpAnnouncementEndpoint());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.Description.Endpoints.Add(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
## <a name="service-discovery"></a>Hizmet Bulma  
 İstemci uygulaması <xref:System.ServiceModel.Discovery.DiscoveryClient> hizmetleri bulmak için sınıfı kullanabilir. Geliştirici, nerede gönderileceği <xref:System.ServiceModel.Discovery.DiscoveryClient> `Probe` veya `Resolve` ileti gönderileceği belirtilen bir keşif bitiş noktasında geçen sınıfın bir örneğini oluşturur. İstemci <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> daha sonra bir <xref:System.ServiceModel.Discovery.FindCriteria> örnek içinde arama ölçütlerini belirten çağırır. Eşleşen hizmetler bulunursa, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> bir <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>koleksiyon döndürür. Aşağıdaki kod, yöntemin `Find` nasıl çağrılmasını ve sonra keşfedilen bir hizmete nasıl bağlanılmayı gösterir.  
  
```csharp  
class Client
{
    static EndpointAddress serviceAddress;
  
    static void Main()
    {  
        if (FindService())
        {
            InvokeService();
        }
    }  
  
    // ** DISCOVERY ** //  
    static bool FindService()  
    {  
        Console.WriteLine("\nFinding Calculator Service ..");  
        DiscoveryClient discoveryClient =
            new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
        Collection<EndpointDiscoveryMetadata> calculatorServices =
            (Collection<EndpointDiscoveryMetadata>)discoveryClient.Find(new FindCriteria(typeof(ICalculator))).Endpoints;  
  
        discoveryClient.Close();  
  
        if (calculatorServices.Count == 0)  
        {  
            Console.WriteLine("\nNo services are found.");  
            return false;  
        }  
        else  
        {  
            serviceAddress = calculatorServices[0].Address;  
            return true;  
        }  
    }  
  
    static void InvokeService()  
    {  
        Console.WriteLine("\nInvoking Calculator Service at {0}\n", serviceAddress);  
  
        // Create a client  
        CalculatorClient client = new CalculatorClient();  
        client.Endpoint.Address = serviceAddress;  
        client.Add(10,3);  
    }
}  
```  
  
## <a name="discovery-and-message-level-security"></a>Bulma ve İleti Düzeyi Güvenliği  
 İleti düzeyi güvenliğini kullanırken, hizmet <xref:System.ServiceModel.EndpointIdentity> bulma bitiş noktası ve <xref:System.ServiceModel.EndpointIdentity> istemci bulma bitiş noktası üzerinde bir eşleme belirtmek gerekir. İleti düzeyi güvenliği hakkında daha fazla bilgi için [İleti Güvenliği'ne](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)bakın.  
  
## <a name="discovery-and-web-hosted-services"></a>Bulma ve Web Barındırılan Hizmetler  
 WCF hizmetlerinin bulunabilmesi için çalışıyor olmaları gerekir. IIS veya WAS altında barındırılan WCF hizmetleri, IIS/WAS hizmete bağlı bir ileti alana kadar çalışmaz, bu nedenle varsayılan olarak bulunamazlar.  Web Tarafından Barındırılan hizmetleri keşfedilebilir hale getirmek için iki seçenek vardır:  
  
1. Windows Server AppFabric Otomatik Başlatma özelliğini kullanma  
  
2. Hizmet adına iletişim kurmak için bir keşif proxy'si kullanma  
  
 Windows Server AppFabric, herhangi bir ileti almadan önce bir hizmetin başlatılmasını sağlayacak bir Otomatik Başlatma özelliğine sahiptir. Bu Otomatik Başlatma kümesi yle, IIS/WAS barındırılan bir hizmet bulunabilir şekilde yapılandırılabilir. Otomatik Başlat özelliği hakkında daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/appfabric/ee677260(v=azure.10)) Otomatik Başlat özelliğini açmanın yanı sıra, hizmeti keşif için yapılandırmanız gerekir. Daha fazla bilgi için [bkz: Nasıl Yapılacağını: Bir WCF Hizmetine Keşfedilebilirlik Ve](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)Yapılandırma Dosyasında İstemci[Yapılandırma Bulma'](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md)yı Programlı bir şekilde ekleyin.  
  
 Bir keşif proxy'si, hizmet çalışmadığında WCF hizmeti adına iletişim kurmak için kullanılabilir. Proxy sonda için dinleyebilir veya iletileri çözebilir ve istemciye yanıt verebilir. İstemci daha sonra doğrudan hizmete ileti gönderebilir. İstemci hizmete bir ileti gönderdiğinde, iletiye yanıt vermek için anında yanıtlanır. Bir bulma proxy uygulama hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
  
> [!NOTE]
> WCF Discovery'nin düzgün çalışması için tüm NIC'lerin (Ağ Arabirimi Denetleyicisi) yalnızca 1 IP adresi olmalıdır.
