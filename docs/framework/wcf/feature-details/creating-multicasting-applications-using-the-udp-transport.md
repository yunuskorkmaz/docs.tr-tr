---
title: UDP Taşıma Kullanarak Çok Noktaya Yayın Yapan Uygulamalar Oluşturma
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: b65a277b6e76767d1e3bfdbebbac5051759986e0
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241859"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a>UDP Taşıma Kullanarak Çok Noktaya Yayın Yapan Uygulamalar Oluşturma
Çok noktaya yayın uygulamaları, noktadan noktaya bağlantılar kurmak zorunda kalmadan aynı anda çok sayıda alıcı küçük iletileri gönderir. Bu tür uygulamaların Vurgu güvenilirlik hızıdır. Diğer bir deyişle, belirli bir ileti gerçekten alındığında olmak üzere daha güncel veri göndermek daha önemlidir. WCF destekler kullanarak çok noktaya yayın uygulamaları yazma <xref:System.ServiceModel.UdpBinding>. Bu aktarım nerede küçük iletilerini istemci sayısı için aynı anda göndermek için bir hizmet gerektiği senaryolarda yararlıdır. Bir bandı uygulama, böyle bir hizmet örneğidir.  
  
## <a name="implementing-a-multicast-application"></a>Bir çok noktaya yayın uygulaması gerçekleştirilmesinin  
 Çok noktaya yayın bir uygulama için bir hizmet sözleşmesini tanımlama ve çok noktaya yayın iletileri cevaplayin gereken her yazılım bileşeni için hizmet sözleşmesini uygulama. Örneğin, bir bandı uygulama hizmet sözleşmesini tanımlayabilir:  
  
```csharp
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
  
 Çok noktaya yayın iletileri almak istediği her bir uygulama bu arabirimi kullanıma sunan bir hizmet ana bilgisayar gerekir.  Örneğin, çok noktaya yayın ileti alma gösteren kod örneği aşağıdadır:  
  
```csharp
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
  
 Uygulama, tüm hizmetlerin dinlediği UDP adresini belirtir. Yeni bir <xref:System.ServiceModel.ServiceHost> oluşturulur ve bir hizmet uç noktası kullanılarak açığa çıkarılır <xref:System.ServiceModel.UdpBinding>. <xref:System.ServiceModel.ServiceHost> Daha sonra açılır ve gelen iletiler için dinleme başlar.  
  
 Bu tür bir senaryo bu gerçekte çok noktaya yayın iletileri gönderen istemcisidir. Doğru UDP adreste dinleme yaptığı her bir hizmet çok noktaya yayın iletileri alır. Çok noktaya yayın iletileri gönderen bir istemci bir örnek aşağıda verilmiştir:  
  
```csharp
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
    Console.WriteLine($"sent stock info at {DateTime.Now}");
    // Wait for one second before sending another update
    System.Threading.Thread.Sleep(new TimeSpan(0, 0, 1));
}
```  
  
 Bu kod, stok bilgilerini oluşturur ve ardından doğru UDP adresinde dinlemeye hizmetlerini çağırmak için çok noktaya yayın iletileri göndermek için hizmet sözleşmesi IStockTicker kullanır.  
  
### <a name="udp-and-reliable-messaging"></a>UDP ve güvenilir Mesajlaşma  
 Güvenilir Mesajlaşma basit UDP protokolünü yapısı nedeniyle UDP bağlamayı desteklemez. İleti bir uzaktan bitiş noktası tarafından alındığında doğrulamanız gerekirse, HTTP veya TCP gibi güvenilir Mesajlaşma destekleyen bir aktarım kullanın. Güvenilir Mesajlaşma bakın hakkında daha fazla bilgi için https://go.microsoft.com/fwlink/?LinkId=231830  
  
### <a name="two-way-multicast-messaging"></a>İki yönlü çok noktaya yayın iletileri  
 Çok noktaya yayın iletileri genellikle tek yönlü olsa da, istek/yanıt iletisi exchange UdpBinding desteklemiyor. UDP taşıma kullanarak gönderilen iletileri içeren iki From adresine. Kötü amaçlı olarak olabileceğinden Kimden adresi kullanarak tr-route değiştirildiğinde dikkatli olunması gerekir.  Aşağıdaki kodu kullanarak adresi denetlenebilir:  
  
```csharp
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
  
 Bu kod, adresi çok noktaya yayın adresi olduğunu belirten 0xE0 içerip içermediğini görmek için Kimden adresi'nin ilk baytı denetler.  
  
### <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
 Çok noktaya yayın iletileri için dinlerken, yönlendirici, çok noktaya yayın adresinde dinleyen bildiren bir ICMP paketi gönderilir. İzinlerine sahip yerel alt ağdaki herhangi biri, bu paket türleri için dinleme ve hangi çok noktaya yayın adresi ve bağlantı noktası üzerinde dinleyen belirleyin.  
  
 Gönderenin IP adresi, tüm güvenlik amaçlar için kullanmayın. Bu bilgiler, sahte ve yanlış makineye yanıtlar göndermek bir uygulamanın neden olabilir. Bu tehdidi azaltmaya yollarından biri, ileti düzeyi güvenliği etkinleştirmektir. Ağ düzeyinde IPSec (Internet Protokolü güvenliği) ve/veya NAP (Ağ Erişim Koruması) de kullanılabilir.
