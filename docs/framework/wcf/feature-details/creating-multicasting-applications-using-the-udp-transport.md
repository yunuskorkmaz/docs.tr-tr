---
title: UDP Taşıma Kullanarak Çok Noktaya Yayın Yapan Uygulamalar Oluşturma
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: 40944129ce3b01d8422d5aba4cfbf913c56265ed
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144636"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a>UDP Taşıma Kullanarak Çok Noktaya Yayın Yapan Uygulamalar Oluşturma
Çok noktaya yayın uygulamaları, bağlantı noktası bağlantıları oluşturmak gerekmeden çok sayıda alıcıya aynı anda küçük iletiler gönderir. Bu tür uygulamaların vurgulaması, güvenilirlik üzerinde hızlanır. Diğer bir deyişle, belirli bir iletinin gerçekten alındığından emin olmak için verilerin zamanında gönderilmesi daha önemlidir. WCF artık kullanarak çok noktaya yayın uygulamaları yazmayı desteklemektedir <xref:System.ServiceModel.UdpBinding> . Bu aktarım, bir hizmetin bir dizi istemciye aynı anda küçük iletiler gönderebilmesi gereken senaryolarda yararlıdır. Bir stok şeridi uygulaması, bu tür bir hizmete örnektir.  
  
## <a name="implementing-a-multicast-application"></a>Çok noktaya yayın uygulaması uygulama  
 Bir çok noktaya yayın uygulaması uygulamak için, bir hizmet sözleşmesi tanımlayın ve çok noktaya yayın iletilerine yanıt vermesi gereken her yazılım bileşeni için hizmet sözleşmesini uygulayın. Örneğin, bir stok şeridi uygulaması bir hizmet sözleşmesini tanımlayabilir:  
  
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
  
 Çok noktaya yayın iletileri almak isteyen her uygulama, bu arabirimi kullanıma sunan bir hizmeti barındırmalıdır.  Örneğin, çok noktaya yayın iletilerinin nasıl alınacağını gösteren bir kod örneği aşağıda verilmiştir:  
  
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
  
 Uygulama, tüm hizmetlerin dinlediği UDP adresini belirtir. Yeni bir <xref:System.ServiceModel.ServiceHost> oluşturulur ve kullanılarak bir hizmet uç noktası gösterilir <xref:System.ServiceModel.UdpBinding> . <xref:System.ServiceModel.ServiceHost>Daha sonra açılır ve gelen iletileri dinlemeye başlayacaktır.  
  
 Bu tür bir senaryoda, gerçekte çok noktaya yayın iletilerini gönderen istemcdir. Doğru UDP adresini dinleyen her hizmet çok noktaya yayın iletilerini alır. Aşağıda çok noktaya yayın iletileri gönderen bir istemciye örnek verilmiştir:  
  
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
  
 Bu kod, stok bilgilerini oluşturur ve ardından doğru UDP adresinde dinleme yapan Hizmetleri çağırmak üzere çok noktaya yayın iletileri göndermek için ıtockticker hizmet sözleşmesini kullanır.  
  
### <a name="udp-and-reliable-messaging"></a>UDP ve güvenilir mesajlaşma  
  UDP bağlaması, UDP protokolünün hafif doğası nedeniyle güvenilir mesajlaşma özelliğini desteklemez. İletilerin uzak bir uç nokta tarafından alındığını onaylamanız gerekiyorsa, HTTP veya TCP gibi güvenilir mesajlaşmayı destekleyen bir aktarım kullanın. Güvenilir Mesajlaşma hakkında daha fazla bilgi için bkz <https://go.microsoft.com/fwlink/?LinkId=231830> ..  
  
### <a name="two-way-multicast-messaging"></a>İki yönlü çok noktaya yayın Iletisi  
 Çok noktaya yayın iletileri genellikle tek yönlü olsa da, UdpBinding istek/yanıt iletisi değişimini destekler. UDP taşıması kullanılarak gönderilen iletiler hem kimden hem de kime adresini içerir. Kimden adresi kötü amaçlı olarak değiştirilecekse, kimden adresini kullanırken dikkatli olunmalıdır.  Adres aşağıdaki kod kullanılarak denetlenebilir:  
  
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
  
 Bu kod, adresin çok noktaya yayın adresi olduğunu belirten 0xE0 içerip içermediğini görmek için kimden adresinin ilk baytını denetler.  
  
### <a name="security-considerations"></a>Güvenlikle İlgili Dikkat Edilmesi Gerekenler  
 Çok noktaya yayın iletilerini dinlerken, yönlendiriciye, çok noktaya yayın adresini dinlediğini bildiren bir ıCMP paketi gönderilir. Yerel alt ağ üzerindeki izinleri olan herkes bu paket türlerini dinleyebilir ve hangi çok noktaya yayın adresini ve hangi bağlantı noktasını dinleyeceğini belirleyebilir.  
  
 Tüm güvenlik amaçları için gönderenin IP adresini kullanmayın. Bu bilgiler sahte olabilir ve bir uygulamanın yanlış makineye yanıt göndermesini sağlayabilir. Bu tehdidi hafifletmek için bir yol ileti düzeyi güvenliği etkinleştirmektir. Ağ düzeyinde IPSec (Internet Protokolü güvenliği) ve/veya NAP (ağ erişim koruması) de kullanılabilir.
