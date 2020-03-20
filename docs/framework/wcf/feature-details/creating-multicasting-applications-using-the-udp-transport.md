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
# <a name="creating-multicasting-applications-using-the-udp-transport"></a><span data-ttu-id="cdcd0-102">UDP Taşıma Kullanarak Çok Noktaya Yayın Yapan Uygulamalar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cdcd0-102">Creating Multicasting Applications using the UDP Transport</span></span>
<span data-ttu-id="cdcd0-103">Çok noktaya yayın uygulamaları, bağlantı noktası oluşturmaya gerek kalmadan aynı anda çok sayıda alıcıya küçük iletiler gönderir.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-103">Multicasting applications send small messages to a large number of recipients at the same time without the need to establish point to point connections.</span></span> <span data-ttu-id="cdcd0-104">Bu tür uygulamaların vurgu güvenilirlik üzerinde hızdır.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-104">The emphasis of such applications is speed over reliability.</span></span> <span data-ttu-id="cdcd0-105">Başka bir deyişle, belirli bir iletinin gerçekten alındığından emin olmaktançok zamanında veri göndermek daha önemlidir.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-105">In other words, it is more important to send timely data than to ensure any specific message is actually received.</span></span> <span data-ttu-id="cdcd0-106">WCF artık <xref:System.ServiceModel.UdpBinding>multicasting uygulamaları kullanarak yazmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-106">WCF now supports writing multicasting applications using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="cdcd0-107">Bu aktarım, bir hizmetin aynı anda birkaç istemciye küçük iletiler göndermesi gereken senaryolarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-107">This transport is useful in scenarios where a service needs to send out small messages to a number of clients simultaneously.</span></span> <span data-ttu-id="cdcd0-108">Hisse senedi işaretçisi uygulaması böyle bir hizmete örnektir.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-108">A stock ticker application is an example of such a service.</span></span>  
  
## <a name="implementing-a-multicast-application"></a><span data-ttu-id="cdcd0-109">Çok Noktaya Yayın Uygulaması Uygulama</span><span class="sxs-lookup"><span data-stu-id="cdcd0-109">Implementing a Multicast Application</span></span>  
 <span data-ttu-id="cdcd0-110">Çok noktaya yayın uygulaması uygulamak için bir hizmet sözleşmesi tanımlayın ve çok noktaya yayın iletilerine yanıt vermesi gereken her yazılım bileşeni için hizmet sözleşmesini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-110">To implement a multicast application, define a service contract and for each software component that needs to respond to the multicast messages, implement the service contract.</span></span> <span data-ttu-id="cdcd0-111">Örneğin, bir hisse senedi işaretleyici uygulaması bir hizmet sözleşmesi tanımlayabilir:</span><span class="sxs-lookup"><span data-stu-id="cdcd0-111">For example, a stock ticker application might define a service contract:</span></span>  
  
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
  
 <span data-ttu-id="cdcd0-112">Çok noktaya yayın iletileri almak isteyen her uygulama, bu arabirimi ortaya çıkaran bir hizmeti barındırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-112">Each application that wants to receive multicast messages must host a service that exposes this interface.</span></span>  <span data-ttu-id="cdcd0-113">Örneğin, çoklu noktaya yayın iletilerinin nasıl alındığını gösteren bir kod örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cdcd0-113">For example, here is a code sample that illustrates how to receive multicast messages:</span></span>  
  
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
  
 <span data-ttu-id="cdcd0-114">Uygulama, tüm hizmetlerin dinleyeceği UDP adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-114">The application specifies the UDP address that all services will be listening on.</span></span> <span data-ttu-id="cdcd0-115">Yeni <xref:System.ServiceModel.ServiceHost> bir oluşturulur ve bir hizmet bitiş <xref:System.ServiceModel.UdpBinding>noktası .</span><span class="sxs-lookup"><span data-stu-id="cdcd0-115">A new <xref:System.ServiceModel.ServiceHost> is created and a service endpoint is exposed using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="cdcd0-116">Daha <xref:System.ServiceModel.ServiceHost> sonra açılır ve gelen iletileri dinlemeye başlar.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-116">The <xref:System.ServiceModel.ServiceHost> is then opened and will start listening for incoming messages.</span></span>  
  
 <span data-ttu-id="cdcd0-117">Bu tür bir senaryoda, çok noktaya yayın yapan istemcidir.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-117">In this type of a scenario it is the client that actually sends out multicast messages.</span></span> <span data-ttu-id="cdcd0-118">Doğru UDP adresinden dinleyen her hizmet çok noktaya yayın iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-118">Each service that is listening at the correct UDP address will receive the multicast messages.</span></span> <span data-ttu-id="cdcd0-119">Aşağıda, çok noktaya yayın iletileri gönderen bir istemci örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cdcd0-119">Here is an example of a client that sends out multicast messages:</span></span>  
  
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
  
 <span data-ttu-id="cdcd0-120">Bu kod stok bilgileri oluşturur ve ardından doğru UDP adresini dinleyen hizmetleri çağırmak için çok noktaya yayın iletileri göndermek için hizmet sözleşmesi IStockTicker'ı kullanır.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-120">This code generates stock information and then uses the service contract IStockTicker to send multicast messages to call services listening on the correct UDP address.</span></span>  
  
### <a name="udp-and-reliable-messaging"></a><span data-ttu-id="cdcd0-121">UDP ve Güvenilir Mesajlaşma</span><span class="sxs-lookup"><span data-stu-id="cdcd0-121">UDP and Reliable Messaging</span></span>  
 <span data-ttu-id="cdcd0-122">UDP bağlama, UDP protokolünün hafif yapısı nedeniyle güvenilir iletileri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-122">The UDP binding does not support reliable messaging because of the lightweight nature of the UDP protocol.</span></span> <span data-ttu-id="cdcd0-123">İletilerin uzak bir bitiş noktası tarafından alındığını onaylamanız gerekiyorsa, HTTP veya TCP gibi güvenilir iletileri destekleyen bir aktarım kullanın.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-123">If you need to confirm that messages are received by a remote endpoint, use a transport that supports reliable messaging like  HTTP or TCP.</span></span> <span data-ttu-id="cdcd0-124">Güvenilir mesajlaşma hakkında daha fazla bilgi için bkz.https://go.microsoft.com/fwlink/?LinkId=231830</span><span class="sxs-lookup"><span data-stu-id="cdcd0-124">For more information about reliable messaging see https://go.microsoft.com/fwlink/?LinkId=231830</span></span>  
  
### <a name="two-way-multicast-messaging"></a><span data-ttu-id="cdcd0-125">İki Yönlü Çok Noktaya Yayın</span><span class="sxs-lookup"><span data-stu-id="cdcd0-125">Two-way Multicast Messaging</span></span>  
 <span data-ttu-id="cdcd0-126">Çok noktaya yayın iletileri genellikle tek yönlü olsa da, UdpBinding istek/yanıt iletisi alışverişini destekler.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-126">While multicast messages are generally one-way, the UdpBinding does support request/reply message exchange.</span></span> <span data-ttu-id="cdcd0-127">UDP aktarımını kullanarak gönderilen iletiler hem Gelen hem de To adresi içerir.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-127">Messages sent using the UDP transport contain both a From and To address.</span></span> <span data-ttu-id="cdcd0-128">Rotada kötü niyetle değiştirilebildiği için From adresi kullanılarak dikkatli olunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-128">Care must be taken when using the From address as it could be maliciously changed en-route.</span></span>  <span data-ttu-id="cdcd0-129">Adres aşağıdaki kod kullanılarak kontrol edilebilir:</span><span class="sxs-lookup"><span data-stu-id="cdcd0-129">The address can be checked using the following code:</span></span>  
  
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
  
 <span data-ttu-id="cdcd0-130">Bu kod, Adres'in çok dökümlü bir adres olduğunu gösteren 0xE0 içerdiğini görmek için From adresinin ilk baytını denetler.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-130">This code checks the first byte of the From address to see if it contains 0xE0 which signifies that the address is a multi-cast address.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="cdcd0-131">Güvenlikle İlgili Dikkat Edilmesi Gerekenler</span><span class="sxs-lookup"><span data-stu-id="cdcd0-131">Security Considerations</span></span>  
 <span data-ttu-id="cdcd0-132">Çok noktaya yayın iletilerini dinlerken, yönlendiriciye çok noktaya yayın adresini dinlediğinizi bildiren bir ICMP paketi gönderilir.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-132">When listening for multicast messages an ICMP packet is sent to the router notifying it you are listening on the multicast address.</span></span> <span data-ttu-id="cdcd0-133">İzinleri olan yerel alt ağdaki herkes bu tür paketleri dinleyebilir ve hangi çok noktaya yayın adresini ve bağlantı noktasını dinlediğinizi belirleyebilir.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-133">Anyone on the local subnet who has permissions could listen for these types of packets and determine which multicast address and port you are listening on.</span></span>  
  
 <span data-ttu-id="cdcd0-134">Gönderenin IP adresini herhangi bir güvenlik amacıyla kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-134">Do not use the IP address of the sender for any security purposes.</span></span> <span data-ttu-id="cdcd0-135">Bu bilgiler sahte olabilir ve bir uygulamanın yanlış makineye yanıt göndermesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-135">This information can be spoofed and can cause an application to send responses to the wrong machine.</span></span> <span data-ttu-id="cdcd0-136">Bu tehdidi azaltmanın bir yolu ileti düzeyi güvenliğini sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-136">One way to mitigate this threat is to enable message level security.</span></span> <span data-ttu-id="cdcd0-137">Ağ düzeyinde IPSec (Internet Protocol Security) ve/veya NAP (Ağ Erişim Koruması) da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cdcd0-137">At the network level IPSec  (Internet Protocol Security) and/or NAP (Network Access Protection) could also be used.</span></span>
