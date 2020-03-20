---
title: UDP Taşıma Kullanarak Çok Noktaya Yayın Yapan Uygulamalar Oluşturma
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: 6825aaafe87ae362fd9266f7c7a82a36d054a69f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185250"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a>UDP Taşıma Kullanarak Çok Noktaya Yayın Yapan Uygulamalar Oluşturma
Çok noktaya yayın uygulamaları, bağlantı noktası oluşturmaya gerek kalmadan aynı anda çok sayıda alıcıya küçük iletiler gönderir. Bu tür uygulamaların vurgu güvenilirlik üzerinde hızdır. Başka bir deyişle, belirli bir iletinin gerçekten alındığından emin olmaktançok zamanında veri göndermek daha önemlidir. WCF artık <xref:System.ServiceModel.UdpBinding>multicasting uygulamaları kullanarak yazmayı destekler. Bu aktarım, bir hizmetin aynı anda birkaç istemciye küçük iletiler göndermesi gereken senaryolarda yararlıdır. Hisse senedi işaretçisi uygulaması böyle bir hizmete örnektir.  
  
## <a name="implementing-a-multicast-application"></a>Çok Noktaya Yayın Uygulaması Uygulama  
 Çok noktaya yayın uygulaması uygulamak için bir hizmet sözleşmesi tanımlayın ve çok noktaya yayın iletilerine yanıt vermesi gereken her yazılım bileşeni için hizmet sözleşmesini uygulayın. Örneğin, bir hisse senedi işaretleyici uygulaması bir hizmet sözleşmesi tanımlayabilir:  
  
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
  
 Çok noktaya yayın iletileri almak isteyen her uygulama, bu arabirimi ortaya çıkaran bir hizmeti barındırmalıdır.  Örneğin, çoklu noktaya yayın iletilerinin nasıl alındığını gösteren bir kod örneği aşağıda verilmiştir:  
  
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
  
 Uygulama, tüm hizmetlerin dinleyeceği UDP adresini belirtir. Yeni <xref:System.ServiceModel.ServiceHost> bir oluşturulur ve bir hizmet bitiş <xref:System.ServiceModel.UdpBinding>noktası . Daha <xref:System.ServiceModel.ServiceHost> sonra açılır ve gelen iletileri dinlemeye başlar.  
  
 Bu tür bir senaryoda, çok noktaya yayın yapan istemcidir. Doğru UDP adresinden dinleyen her hizmet çok noktaya yayın iletileri alır. Aşağıda, çok noktaya yayın iletileri gönderen bir istemci örneği verilmiştir:  
  
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
  
 Bu kod stok bilgileri oluşturur ve ardından doğru UDP adresini dinleyen hizmetleri çağırmak için çok noktaya yayın iletileri göndermek için hizmet sözleşmesi IStockTicker'ı kullanır.  
  
### <a name="udp-and-reliable-messaging"></a>UDP ve Güvenilir Mesajlaşma  
 UDP bağlama, UDP protokolünün hafif yapısı nedeniyle güvenilir iletileri desteklemez. İletilerin uzak bir bitiş noktası tarafından alındığını onaylamanız gerekiyorsa, HTTP veya TCP gibi güvenilir iletileri destekleyen bir aktarım kullanın. Güvenilir mesajlaşma hakkında daha fazla bilgi için bkz.https://go.microsoft.com/fwlink/?LinkId=231830  
  
### <a name="two-way-multicast-messaging"></a>İki Yönlü Çok Noktaya Yayın  
 Çok noktaya yayın iletileri genellikle tek yönlü olsa da, UdpBinding istek/yanıt iletisi alışverişini destekler. UDP aktarımını kullanarak gönderilen iletiler hem Gelen hem de To adresi içerir. Rotada kötü niyetle değiştirilebildiği için From adresi kullanılarak dikkatli olunmalıdır.  Adres aşağıdaki kod kullanılarak kontrol edilebilir:  
  
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
  
 Bu kod, Adres'in çok dökümlü bir adres olduğunu gösteren 0xE0 içerdiğini görmek için From adresinin ilk baytını denetler.  
  
### <a name="security-considerations"></a>Güvenlikle İlgili Dikkat Edilmesi Gerekenler  
 Çok noktaya yayın iletilerini dinlerken, yönlendiriciye çok noktaya yayın adresini dinlediğinizi bildiren bir ICMP paketi gönderilir. İzinleri olan yerel alt ağdaki herkes bu tür paketleri dinleyebilir ve hangi çok noktaya yayın adresini ve bağlantı noktasını dinlediğinizi belirleyebilir.  
  
 Gönderenin IP adresini herhangi bir güvenlik amacıyla kullanmayın. Bu bilgiler sahte olabilir ve bir uygulamanın yanlış makineye yanıt göndermesine neden olabilir. Bu tehdidi azaltmanın bir yolu ileti düzeyi güvenliğini sağlamaktır. Ağ düzeyinde IPSec (Internet Protocol Security) ve/veya NAP (Ağ Erişim Koruması) da kullanılabilir.
