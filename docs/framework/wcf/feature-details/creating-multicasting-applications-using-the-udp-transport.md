---
title: UDP Taşıma Kullanarak Çok Noktaya Yayın Yapan Uygulamalar Oluşturma
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: 84b36029416a66ef03768aed7d0c789a41eed8ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490431"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a>UDP Taşıma Kullanarak Çok Noktaya Yayın Yapan Uygulamalar Oluşturma
Çok noktaya yayın uygulamalar, noktadan noktaya bağlantılar kurmak zorunda kalmadan aynı anda çok sayıda alıcı küçük iletileri gönderir. Bu tür uygulamalar Vurgu güvenilirlik hızıdır. Diğer bir deyişle, belirli bir ileti gerçekte buluttaki sağlamak üzere daha güncel veri göndermek daha önemlidir. WCF artık destekliyor kullanarak çok noktaya yayın uygulamaları yazma <xref:System.ServiceModel.UdpBinding>. Bu aktarma, burada bir hizmet küçük iletilerini istemci sayısı için aynı anda göndermesi gerekir senaryolarda kullanışlıdır. Bu tür bir hizmet örneği bir borsa uygulamasıdır.  
  
## <a name="implementing-a-multicast-application"></a>Çok noktaya yayın uygulaması gerçekleştirilmesinin  
 Bir çok noktaya yayın uygulaması uygulamak için çok noktaya yayın iletileri için yanıt vermesi her yazılım bileşeni için hizmet sözleşmesini uygulama ve hizmet sözleşmesi tanımlayın. Örneğin, bir bandı uygulaması bir hizmet sözleşmesini tanımlayabilirsiniz:  
  
```  
// Shared contracts between the client and the service  
[ServiceContract]
interface IStockTicker
{
    [OperationContract(IsOneWay = true)]
    void SendStockInfo(StockInfo[] stockInfo);
}

[DataContract]
class StockInfo
{
    [DataMember]
    public string Symbol;

    [DataMember]
    public float Price;

    public StockInfo(string symbol, float price)
    {
        this.Symbol = symbol;
        this.Price = price;
    }
}
```  
  
 Çok noktaya yayın iletileri almak istediği her bir uygulama bu arabirimi kullanıma sunan bir hizmet ana bilgisayar gerekir.  Örneğin, çok noktaya yayın ileti alma gösteren bir kod örneği şöyledir:  
  
```  
// Service Address
string serviceAddress = "soap.udp://224.0.0.1:40000";
// Binding
UdpBinding myBinding = new UdpBinding();
// Host
ServiceHost host = new ServiceHost(typeof(StockTickerService), new Uri(serviceAddress));
// Add service endpoint
host.AddServiceEndpoint(typeof(IStockTicker), myBinding, string.Empty);
// Openup the service host
host.Open();

Console.WriteLine("Start receiving stock information");
Console.ReadLine();
```  
  
 Uygulamanın tüm hizmetlerin dinlediği UDP adresini belirtir. Yeni bir <xref:System.ServiceModel.ServiceHost> oluşturulur ve bir hizmet uç noktası kullanılarak kullanıma sunulan <xref:System.ServiceModel.UdpBinding>. <xref:System.ServiceModel.ServiceHost> Daha sonra açılır ve gelen iletiler için dinleme başlar.  
  
 Bu tür bir senaryosu, gerçekte çok noktaya yayın iletileri gönderen istemcidir. Doğru UDP adresinde dinleme her hizmet çok noktaya yayın iletileri alır. Çok noktaya yayın iletilerini gönderme bir istemcinin bir örneği burada verilmiştir:  
  
```  
// Multicast Address
string serviceAddress = "soap.udp://224.0.0.1:40000";

// Binding
UdpBinding myBinding = new UdpBinding();

// Channel factory
ChannelFactory<IStockTicker> factory 
    = new ChannelFactory<IStockTicker>(myBinding,
                new EndpointAddress(serviceAddress));

// Call service
IStockTicker proxy = factory.CreateChannel();

while (true)
{
    // This will continue to mulicast stock information
    proxy.SendStockInfo(GetStockInfo());
    Console.WriteLine(String.Format("sent stock info at {0}", DateTime.Now));
    // Wait for one second before sending another update
    System.Threading.Thread.Sleep(new TimeSpan(0, 0, 1));
}
```  
  
 Bu kod hisse bilgilerini oluşturur ve doğru UDP adresini dinlemesini Hizmetleri çağırmak için çok noktaya yayın iletileri göndermek için hizmet sözleşmesini IStockTicker kullanır.  
  
### <a name="udp-and-reliable-messaging"></a>UDP ve güvenilir Mesajlaşma  
 UDP bağlama UDP protokolünü basit gereği güvenilir Mesajlaşma desteklemez. İleti uzak uç noktası tarafından alındığında onaylamanız gerekir, örneğin HTTP veya TCP güvenilir Mesajlaşma destekleyen bir taşıma kullanın. Güvenilir Mesajlaşma bakın hakkında daha fazla bilgi için http://go.microsoft.com/fwlink/?LinkId=231830  
  
### <a name="two-way-multicast-messaging"></a>İki yönlü çok noktaya yayın iletileri  
 Çok noktaya yayın iletileri genellikle tek yönlü olsa da, UdpBinding istek/yanıt iletisi exchange desteklemiyor. UDP taşıma kullanarak gönderilen iletileri içeren iki From ve adresine. Kötü amaçlı olarak olabileceğinden KİMDEN adresini kullanarak tr yol değiştiğinde dikkatli olunması gerekir.  Aşağıdaki kodu kullanarak adresi denetlenebilir:  
  
```  
if (address.AddressFamily == AddressFamily.InterNetwork)
{
    // IPv4
    byte[] addressBytes = address.GetAddressBytes();
    return ((addressBytes[0] & 0xE0) == 0xE0);
}
else
{
    // IPv6
    return address.IsIPv6Multicast;
}
```  
  
 Bu kod adresi çok noktaya yayın adresi olduğunu belirten 0xE0 içerip içermediğini Kimden adresinin ilk baytını denetler.  
  
### <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
 Çok noktaya yayın iletileri için dinlerken, yönlendirici, çok noktaya yayın adresi dinleyen bildiren bir ICMP paketi gönderilir. Herkes izinlere sahip olan yerel alt ağda, bu paket türleri için dinleme ve hangi çok noktaya yayın adresi ve bağlantı noktası üzerinde dinleyen belirleyin.  
  
 Gönderenin IP adresi tüm güvenlik amaçlar için kullanmayın. Bu bilgileri sahte ve yanlış makine yanıtları göndermek bir uygulama neden olabilir. Bu tehdidi azaltmak için bir ileti düzeyi güvenliği etkinleştirmek için yoludur. Ağ düzeyinde IPSec (Internet Protokolü güvenliği) ve/veya NAP (Ağ Erişim Koruması) de kullanılabilir.
