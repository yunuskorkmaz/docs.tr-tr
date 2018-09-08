---
title: WCF Keşif Genel Bakış
ms.date: 03/30/2017
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
ms.openlocfilehash: 24d758502e360a8368be25c506b8648b12a3eb20
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44173080"
---
# <a name="wcf-discovery-overview"></a>WCF Keşif Genel Bakış
Bulma API'ları dinamik yayını ve Web Hizmetleri için WS bulma protokolünü kullanarak bulma için birleşik bir programlama modeli sağlar. Bu API'leri, kendileri ve yayımlanan hizmetleri bulmak için istemcileri yayımlamak hizmetleri sağlar. Bir hizmet bulunabilirlik yapıldıktan sonra hizmet Duyurunun ileti gönderme yanı sıra dinler ve keşif istekleri'özelliğine sahiptir. Bulunabilirlik Hizmetleri, ağ üzerinde kendi varış duyurmaktan Karışılama iletileri ve kendi kalkış ağdan duyurmaktan Bye iletileri gönderebilir. Bir hizmet bulmak için istemcilerin gönderdiği bir `Probe` hizmet sözleşme türü, anahtar sözcükleri ve ağ üzerinde kapsamı gibi belirli ölçütleri içeren istek. Hizmetleri almak `Probe` istemek ve ölçütlerle eşleşen olup olmadığını belirler. Bir hizmet eşleşirse, göndererek yanıt bir `ProbeMatch` istemcisine hizmetiyle bağlantı kurmak gereken bilgileri ile ileti. İstemciler ayrıca gönderebilir `Resolve` kendi uç nokta adresi değişmiş olan hizmetleri bulmak izin istekleri. Eşleşen Hizmetleri yanıt için `Resolve` göndererek istekleri bir `ResolveMatch` istemcisine ileti.  
  
## <a name="ad-hoc-and-managed-modes"></a>Geçici ve yönetilen modları  
 Bulma API iki farklı modunu destekler: yönetilen ve geçici. Yönetilen modda kullanılabilir hizmetleri hakkında bilgileri tutan keşif proxy'si olarak adlandırılan bir merkezi sunucu yok. Keşif proxy'si çeşitli şekillerde hizmetlerimizle ilgili bilgi doldurulabilir. Örneğin, hizmetleri keşif proxy'si kadar başlangıç sırasında duyuru iletileri gönderebilir veya bir veritabanını veya yapılandırma dosyasını hangi hizmetlerin kullanılabildiğini belirlemenize proxy veri okuyabilirsiniz. Keşif proxy'si nasıl doldurulur tamamen geliştiricisi kadar kadar. İstemcilerin kullanılabilir hizmetleri hakkında bilgi almak için keşif proxy'si kullanın. Bir istemci arandığında bir hizmet için gönderen bir `Probe` bulma proxy ve proxy ileti bilir hakkında hizmetlerinden herhangi birinin istemci arıyor hizmet eşleşip eşleşmediğini belirler. Keşif proxy gönderir eşleşme varsa bir `ProbeMatch` istemcisine geri yanıt. İstemci sonra proxy sunucudan döndürülen hizmet bilgilerini kullanarak doğrudan hizmet başvurabilirsiniz. Anahtar yönetilen modu arkasındaki bir yetkilisi, Keşif proxy'si tek noktaya yayın şekilde bulma isteği gönderilir ilkesidir. .NET Framework kendi proxy oluşturmanıza olanak tanıyan anahtar bileşenleri içerir. Proxy, istemciler ve hizmetler tarafından birden çok yöntem bulabilirsiniz:  
  
-   Proxy geçici iletilere yanıt verebilir.  
  
-   Proxy bir duyuru başlatma sırasında gönderebilirsiniz.  
  
-   İstemciler ve hizmetler için belirli ve iyi bilinen bir uç aramak için yazılabilir.  
  
 Geçici modunda merkezi sunucusu yok. Çok noktaya yayın biçimde hizmet duyuruları ve istemci istekleri gibi tüm bulma iletileri gönderilir. Varsayılan olarak .NET Framework UDP protokolü üzerinden geçici bulma desteği içerir. Bir hizmet başlangıcı'te bir Merhaba duyurudan göndermek için yapılandırılmışsa, örneğin, bu, UDP protokolünü kullanan bir bilinen, çok noktaya yayın adresi gönderir. İstemciler, etkin bir şekilde bu Duyurular için dinleme ve bunları uygun şekilde işlemek zorunda. Bir istemci gönderdiğinde bir `Probe` bir hizmet için ileti çok noktaya yayın protokolü kullanarak ağ üzerinden gönderilir. İsteği aldığında her hizmet ölçütler eşleşip eşleşmediğini belirler `Probe` iletisi ve doğrudan istemciye yanıt veren bir `ProbeMatch` hizmet içinde belirtilen ölçütlerle eşleşmesi durumunda ileti `Probe` ileti.  
  
## <a name="benefits-of-using-wcf-discovery"></a>WCF bulma kullanmanın avantajları  
 WCF bulma uygulandığından WS bulma protokolünü kullanarak diğer istemciler, hizmetleri ve WS-bulma de uygulama proxy'si ile birlikte çalışabilir. WCF bulma, bulma işlevleri, mevcut hizmet ve istemcileri eklemek kolaylaştıran var olan WCF API'leri üzerinde oluşturulmuştur. Hizmet bulunabilirliği, uygulama yapılandırma ayarları'nda kolayca eklenebilir. Ayrıca, WCF bulma ayrıca eş net adlandırma katmana ve HTTP gibi diğer taşımalar üzerinden Bulma Protokolü kullanarak destekler. WCF bulma işlemi keşif proxy'si kullanıldığı bir yönetilen modu için destek sağlar. Tüm ağ için çok noktaya yayın iletileri göndermek yerine doğrudan keşif proxy'si iletilerinin gönderildiği gibi bu ağ trafiğini azaltabilir. WCF bulma daha fazla esneklik için Web services ile çalışırken de sağlar. Örneğin, istemci veya hizmetini yeniden yapılandırmanız gerekmeden hizmetin adres değiştirebilirsiniz. Bir istemci sorun hizmet erişmesi gerektiğinde bir `Probe` üzerinden ileti bir `Find` istemek ve hizmet, geçerli bir adres ile yanıt bekler. WCF bulma, bir hizmet anlaşması türleri, bağlama öğeleri, ad alanı, kapsam ve anahtar sözcükler veya sürüm numaraları gibi farklı ölçütlere göre aramak bir istemci sağlar. WCF bulma, çalışma zamanı ve tasarım zamanı bulma olanağı sağlar. Uygulamanıza ekleme bulma, hataya dayanıklılık ve otomatik yapılandırma gibi diğer senaryoları etkinleştirmek için kullanılabilir.  
  
## <a name="service-publication"></a>Hizmet yayımı  
 Bir hizmet bulunabilir, yapmak için bir <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> eklenmelidir bulma iletileri dinlemek yeri belirtmek için hizmet ana bilgisayarı ve bir bulma uç noktası eklenmelidir. Aşağıdaki kod örneği, şirket içinde barındırılan bir hizmet bulunabilir hale getirmek için nasıl değiştirilebilir gösterir.  
  
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
  
 A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> örneği, hizmetin bulunabilir olması bir hizmet açıklaması eklenmelidir. A <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> örneği için hizmet bulma isteklerini dinlemek yeri bildirme hizmet konak eklenmesi gerekir. Bu örnekte, bir <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (türetilen <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) hizmet bulma istekleri için UDP üzerinden dinleme yapması gerektiğini belirtmek için eklenen çok noktaya yayın taşıma. <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Tüm iletileri bir çok noktaya yayın biçimde gönderildiğinden geçici bulmak için kullanılır.  
  
## <a name="announcement"></a>Duyuru  
 Varsayılan olarak, hizmet yayımı duyuru iletilerini göndermez. Hizmet, duyuru iletilerini göndermek için yapılandırılmalıdır. Hizmet bulma iletiler için dinleme listesinden duyurmaktan çünkü bu hizmeti yazıcıları için daha fazla esneklik sağlar. Hizmet duyuru Hizmetleri keşif proxy'si veya diğer hizmet kayıt defterleri ile kaydetmek için bir mekanizma olarak da kullanılabilir. Aşağıdaki kod, bir UDP bağlama üzerinden Duyurunun ileti göndermek için bir hizmet yapılandırma işlemi gösterilmektedir.  
  
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
 Bir istemci uygulaması kullanabilirsiniz <xref:System.ServiceModel.Discovery.DiscoveryClient> Hizmetleri bulmak için sınıf. Geliştirici bir örneğini oluşturur <xref:System.ServiceModel.Discovery.DiscoveryClient> nereye gönderileceğini belirtir bulma uç noktası geçirir sınıfı `Probe` veya `Resolve` iletileri. Ardından istemci çağrıları <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> içinde arama ölçütlerini belirten bir <xref:System.ServiceModel.Discovery.FindCriteria> örneği. Eşleşen Hizmetleri bulunursa <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> koleksiyonunu döndürür <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>. Aşağıdaki kod nasıl çağrılacağını gösterir `Find` yöntemi ve ardından bulunan bir hizmete bağlanabilir.  
  
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
 İleti düzeyi güvenlik kullanılırken belirtmek gerekmez, bir <xref:System.ServiceModel.EndpointIdentity> hizmet bulma uç noktası ile eşleşen bir üzerinde <xref:System.ServiceModel.EndpointIdentity> istemci bulma uç noktası üzerinde. İleti düzeyi güvenliği hakkında daha fazla bilgi için bkz: [ileti güvenliği](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
## <a name="discovery-and-web-hosted-services"></a>Bulma ve Web Hizmetleri barındırılan  
 Sırayla bulunabilir olması WCF hizmetleri için bunlar çalıştırılması gerekir. IIS kadar IIS ya da WAS çalıştırmayın altında barındırılan WCF hizmetleri / WAS hizmeti için bu nedenle varsayılan olarak bulunabilir olamaz bağlı bir ileti alır.  Web barındırılan hizmetler bulunabilir olmasını sağlama için iki seçenek vardır:  
  
1.  Windows Server AppFabric otomatik başlatma özelliğini kullanma  
  
2.  Hizmet adına iletişim kurmak için keşif proxy'si kullanın  
  
 Windows Server AppFabric iletileri almadan önce başlatılması için bir hizmet sağlayacak bir otomatik başlatma özelliği vardır. Bu otomatik başlatma ile ayarlayın, bir IIS / WAS barındırılan hizmeti bulunabilir olması için yapılandırılabilir. Otomatik başlatma özelliği bakın hakkında daha fazla bilgi için [Windows Server AppFabric otomatik başlatma özelliği](https://go.microsoft.com/fwlink/?LinkId=205545). Otomatik başlatma özelliği etkinleştirme yanı sıra, hizmet bulma için yapılandırmanız gerekir. Daha fazla bilgi için [nasıl yapılır: program aracılığıyla ekleme bulunabilirliği bir WCF hizmeti ve istemci](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[yapılandırma dosyasındaki yapılandırma bulma](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).  
  
 Keşif proxy'si hizmeti çalışmadığı zaman WCF hizmeti adına iletişim için kullanılabilir. Proxy için yoklama dinleme veya iletileri çözmek ve istemci taleplerine yanıt. İstemci, sonra iletileri doğrudan hizmetine gönderebilir. İstemci hizmete bir ileti gönderdiğinde iletiye yanıt vermek için örneği oluşturulur. Keşif proxy bkz uygulama hakkında daha fazla bilgi için [keşif proxy'si ekleme](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).  
  
> [!NOTE]
>  WCF bulma'nın düzgün çalışması için tüm NIC'ler (ağ arabirimi denetleyicisi) yalnızca 1 IP adresi olmalıdır.
