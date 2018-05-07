---
title: WCF Keşif Genel Bakış
ms.date: 03/30/2017
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
ms.openlocfilehash: c01ded15b3284058d7c5678409936e51fce1ea5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="wcf-discovery-overview"></a>WCF Keşif Genel Bakış
Bulma API'ları dinamik yayını ve bulma WS bulma protokolünü kullanarak bir Web Hizmetleri için birleşik bir programlama modeli sağlar. Bu API'leri kendilerini ve yayımlanan hizmetleri bulmak için istemcileri yayımlamak hizmetler sağlar. Bir hizmet bulunabilirlik sağlandıktan sonra hizmet duyuru iletileri gönderme yanı sıra dinler ve bulma isteklerine yanıt özelliğine sahiptir. Bulunabilirlik Hizmetleri Ağ üzerinde kendi varış duyurmaktan Merhaba iletileri ve bunların ayrılma ağdan duyurmaktan Bye iletileri gönderebilir. Bir hizmet bulmak için istemcilerin gönderdiği bir `Probe` hizmet sözleşmesi türü, anahtar sözcükleri ve ağ üzerindeki kapsamı gibi belirli bir ölçüte içeren isteği. Hizmetleri almak `Probe` istemek ve ölçütlerle eşleştiğini belirlemek. Bir hizmet eşleşirse, göndererek yanıt bir `ProbeMatch` hizmetiyle iletişim için gereken bilgiler ile istemciye ileti. İstemcileri de gönderebilirler `Resolve` bunları kendi uç noktası adresi değişmiş olabilir Hizmetleri bulmak izin istekleri. Eşleşen Hizmetleri yanıt için `Resolve` göndererek isteklerini bir `ResolveMatch` istemciye ileti.  
  
## <a name="ad-hoc-and-managed-modes"></a>Geçici ve yönetilen modları  
 Bulma APİ'si iki farklı modlarını destekler: yönetilen ve geçici. Yönetilen modunda kullanılabilir hizmetler hakkında bilgileri tutan keşif proxy'si olarak adlandırılan bir merkezi sunucu yok. Keşif proxy'si çeşitli şekillerde hizmetleri hakkında bilgi ile doldurulabilir. Örneğin, hizmetleri keşif proxy'si kadar başlangıç sırasında duyuru iletiler gönderebilir veya bir veritabanı ya da hangi hizmetlerin kullanılabilir olduğunu belirlemek için bir yapılandırma dosyasını proxy veri okuyabilirsiniz. Keşif proxy'si nasıl doldurulur tamamen kadar geliştiricisi değildir. İstemciler kullanılabilir hizmetler hakkında bilgi almak için keşif proxy'si kullanın. Ne zaman bir istemci arar bir hizmet için bu gönderir bir `Probe` keşif proxy'si ve proxy iletiye belirler bilir hakkında hizmetlerden herhangi biri için istemci arama hizmeti eşleşip eşleşmediğini. Keşif proxy gönderir eşleşme varsa bir `ProbeMatch` istemcisine geri yanıt. İstemci ardından kullanarak doğrudan proxy sunucudan döndürülen hizmet bilgileri hizmet başvurabilirsiniz. Anahtar yönetilen modu arkasında bulma istekleri bir yetkilisi, Keşif proxy'si için bir tek noktaya yayın şekilde gönderilir ilkesidir. .NET Framework kendi proxy oluşturmanıza olanak sağlayan anahtar bileşenleri içerir. İstemcileri ve Hizmetleri proxy birden çok yöntemlerle bulabilirsiniz:  
  
-   Proxy geçici iletilere yanıt verebilir.  
  
-   Proxy bir duyuru iletisi başlatma sırasında gönderebilirsiniz.  
  
-   İstemciler ve hizmetler için belirli bir iyi bilinen uç aramak için yazılabilir.  
  
 Geçici modunda merkezi sunucusu yok. Tüm bulma iletileri hizmet duyuruları ve istemci istekleri gibi bir çok noktaya yayın şekilde gönderilir. Varsayılan olarak .NET Framework UDP protokolü üzerinden geçici bulma için destek içerir. Bir hizmeti başlatma üzerinde Hello duyuru göndermek için yapılandırılmışsa, örneğin, bunu, UDP protokolünü kullanarak bir iyi bilinen, çok noktaya yayın adresi gönderir. İstemcilerini etkin şekilde bu duyuruları için dinleme ve buna göre işlem gerekmez. Bir istemci gönderdiğinde bir `Probe` ileti bir hizmet için çok noktaya yayın protokolü kullanarak ağ üzerinden gönderilir. İsteği alır her hizmet ölçütler eşleşip eşleşmediğini belirler `Probe` iletisi ve istemci ile doğrudan yanıtlaması bir `ProbeMatch` hizmet belirtilen ölçütlere uyuyorsa ileti `Probe` ileti.  
  
## <a name="benefits-of-using-wcf-discovery"></a>WCF keşif kullanmanın yararları  
 WCF keşif WS bulma protokolünü kullanılarak uygulanan çünkü diğer istemciler, hizmetleri ve WS-bulma de uygulama proxy'si ile birlikte çalışabilir. WCF keşif bulma işlevselliği, mevcut hizmetler ve istemcileri eklemek kolay hale getiren var olan WCF API'leri, bağlı yerleşik olarak bulunur. Hizmet bulunabilirliği kolayca uygulama yapılandırma ayarları'nda eklenebilir. Ayrıca, WCF bulma ayrıca eş net, adlandırma katmana ve HTTP gibi diğer taşımaları üzerinden Bulma Protokolü kullanarak destekler. WCF bulma işlemi keşif proxy'si kullanıldığı bir yönetilen modu için destek sağlar. Tüm ağ için çok noktaya yayın iletileri göndermek yerine doğrudan keşif proxy'si iletilerinin gönderildiği gibi bu ağ trafiğini azaltabilir. WCF keşif daha fazla esneklik için Web services ile çalışırken de sağlar. Örneğin, istemci veya hizmeti yeniden yapılandırmak zorunda kalmadan bir hizmet adresini değiştirebilirsiniz. Bir istemci sorun hizmet erişmesi gerektiğinde bir `Probe` aracılığıyla ileti bir `Find` istemek ve geçerli adresiyle yanıt hizmete bekler. WCF keşif sözleşme türleri, bağlama öğeleri, ad alanı, kapsam ve anahtar sözcükleri veya sürüm numaraları gibi farklı ölçütleri temel alarak bir hizmet aramak bir istemcinin sağlar. WCF keşif çalışma zamanı ve tasarım zamanı bulma sağlar. Uygulamanıza ekleme bulma, hata toleransı ve otomatik yapılandırması gibi diğer senaryoları etkinleştirmek için kullanılabilir.  
  
## <a name="service-publication"></a>Hizmet yayımı  
 Bir hizmet bulunabilir, duruma getirmek için bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> eklenmelidir bulma iletiler için dinleme konumu belirtmek için hizmet ana bilgisayarı ve bir bulma uç noktası eklenmelidir. Aşağıdaki kod örneğinde, kendini barındıran hizmet bulunabilir duruma getirmek için nasıl değiştirilebilir gösterir.  
  
```csharp  
Uri baseAddress = new Uri(string.Format("http://{0}:8000/discovery/scenarios/calculatorservice/{1}/",  
        System.Net.Dns.GetHostName(), Guid.NewGuid().ToString()));

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
  
 A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> örneği bulunabilir hizmet için bir hizmet açıklama eklenmelidir. A <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> örneği, hizmet bulma isteklerini dinlemek nereye bildirmek için hizmet konağı eklenmelidir. Bu örnekte, bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (türetilen <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) hizmet bulma istekleri için UDP üzerinden dinleme yapması gerektiğini belirtmek için eklenen çok noktaya yayın taşıma. <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Tüm iletileri çok noktaya yayın bir biçimde gönderildiğinden geçici bulmak için kullanılır.  
  
## <a name="announcement"></a>Duyuru  
 Varsayılan olarak, hizmet yayımı duyuru iletilerini göndermez. Hizmetin, duyuru iletilerini göndermek için yapılandırılmalıdır. Ayrı olarak bulma iletiler için dinleme hizmetinin Duyurusu çünkü bu hizmeti yazıcıları için ek esneklik sağlar. Hizmet duyuru Hizmetleri keşif proxy'si veya diğer hizmet kayıt defterleri ile kaydettirmek için bir mekanizma olarak da kullanılabilir. Aşağıdaki kod bir UDP bağlama üzerinden duyuru iletileri göndermek için bir hizmeti yapılandırmak nasıl gösterir.  
  
```csharp  
Uri baseAddress = new Uri(string.Format("http://{0}:8000/discovery/scenarios/calculatorservice/{1}/",
        System.Net.Dns.GetHostName(), Guid.NewGuid().ToString()));

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    ServiceDiscoveryBehavior discoveryBehavior = new ServiceDiscoveryBehavior();
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

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
  
## <a name="service-discovery"></a>Hizmet bulma  
 Bir istemci uygulaması kullanabilir <xref:System.ServiceModel.Discovery.DiscoveryClient> Hizmetleri bulmak için sınıf. Geliştirici bir örneğini oluşturur <xref:System.ServiceModel.Discovery.DiscoveryClient> nereye gönderileceğini belirten bir bulma uç noktası geçirir sınıfı `Probe` veya `Resolve` iletileri. İstemci ardından çağırır <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> içinde arama ölçütlerini belirtir bir <xref:System.ServiceModel.Discovery.FindCriteria> örneği. Eşleşen Hizmetleri bulunursa, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> koleksiyonunu döndürür <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Aşağıdaki kod nasıl çağrılacağını gösterir `Find` yöntemi ve bulunan bir hizmetine bağlanın.  
  
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
  
## <a name="discovery-and-message-level-security"></a>Bulma ve ileti düzeyi güvenliği  
 İleti düzeyi güvenlik kullanılırken belirtmek için gerekli bir <xref:System.ServiceModel.EndpointIdentity> hizmet bulma uç noktası ve eşleşen bir <xref:System.ServiceModel.EndpointIdentity> istemci bulma uç. İleti düzeyi güvenliği hakkında daha fazla bilgi için bkz: [ileti güvenliği](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
## <a name="discovery-and-web-hosted-services"></a>Bulma ve Web Hizmetleri barındırılan  
 WCF hizmetleri bulunabilir sırayla bunlar çalıştırması gerekir. IIS kadar IIS ya da WAS çalıştırmayın altında barındırılan WCF hizmetleri / olan hizmet için varsayılan olarak bulunabilirlik olamaz bağlı bir ileti alır.  Web barındırılan hizmetleri bulunabilir yapmak için iki seçenek vardır:  
  
1.  Windows Server AppFabric otomatik başlatma özelliğini kullanma  
  
2.  Adına hizmeti iletişim kurmak için keşif proxy'si kullanın  
  
 Windows Server AppFabric iletileri almadan önce başlatılması bir hizmet sağlayacak bir otomatik başlatma özelliği vardır. Bu otomatik başlatma olan ayarlayın, bir IIS / barındırılan WAS hizmeti bulunabilir olarak yapılandırılabilir. Otomatik başlatma özelliği bakın hakkında daha fazla bilgi için [Windows Server AppFabric otomatik başlatma özelliği](http://go.microsoft.com/fwlink/?LinkId=205545). Otomatik başlatma özelliğini kapatma yanı sıra, hizmet bulma için yapılandırmanız gerekir. Daha fazla bilgi için bkz: [nasıl yapılır: program aracılığıyla eklemek bulunabilirliği bir WCF hizmeti ve istemci](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[yapılandırma bulma yapılandırma dosyasında](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).  
  
 Keşif proxy'si hizmeti çalışmadığı zaman adına WCF Hizmeti iletişim kurmak için kullanılabilir. Proxy için yoklama dinleme veya iletileri çözün ve istemci yanıt. İstemci, ardından doğrudan hizmet iletileri gönderebilir. İstemci hizmete bir ileti gönderdiğinde iletisinde örneği. Keşif proxy bakın, uygulama hakkında daha fazla bilgi için [keşif proxy'si ekleme](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).  
  
> [!NOTE]
>  WCF keşif'ın düzgün çalışması tüm NIC'ler (ağ arabirimi denetleyicisinin) yalnızca 1 IP adresi olmalıdır.
