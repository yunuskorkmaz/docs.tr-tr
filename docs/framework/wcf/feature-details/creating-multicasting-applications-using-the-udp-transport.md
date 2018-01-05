---
title: "UDP Taşıma Kullanarak Çok Noktaya Yayın Yapan Uygulamalar Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57c30c8b6b381be931789f3f64cbd26943bb2b34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a><span data-ttu-id="f2bb5-102">UDP Taşıma Kullanarak Çok Noktaya Yayın Yapan Uygulamalar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f2bb5-102">Creating Multicasting Applications using the UDP Transport</span></span>
<span data-ttu-id="f2bb5-103">Çok noktaya yayın uygulamalar, noktadan noktaya bağlantılar kurmak zorunda kalmadan aynı anda çok sayıda alıcı küçük iletileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-103">Multicasting applications send small messages to a large number of recipients at the same time without the need to establish point to point connections.</span></span> <span data-ttu-id="f2bb5-104">Bu tür uygulamalar Vurgu güvenilirlik hızıdır.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-104">The emphasis of such applications is speed over reliability.</span></span> <span data-ttu-id="f2bb5-105">Diğer bir deyişle, belirli bir ileti gerçekte buluttaki sağlamak üzere daha güncel veri göndermek daha önemlidir.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-105">In other words, it is more important to send timely data than to ensure any specific message is actually received.</span></span> <span data-ttu-id="f2bb5-106">WCF artık destekliyor kullanarak çok noktaya yayın uygulamaları yazma <xref:System.ServiceModel.UdpBinding>.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-106">WCF now supports writing multicasting applications using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="f2bb5-107">Bu aktarma, burada bir hizmet küçük iletilerini istemci sayısı için aynı anda göndermesi gerekir senaryolarda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-107">This transport is useful in scenarios where a service needs to send out small messages to a number of clients simultaneously.</span></span> <span data-ttu-id="f2bb5-108">Bu tür bir hizmet örneği bir borsa uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-108">A stock ticker application is an example of such a service.</span></span>  
  
## <a name="implementing-a-multicast-application"></a><span data-ttu-id="f2bb5-109">Çok noktaya yayın uygulaması gerçekleştirilmesinin</span><span class="sxs-lookup"><span data-stu-id="f2bb5-109">Implementing a Multicast Application</span></span>  
 <span data-ttu-id="f2bb5-110">Bir çok noktaya yayın uygulaması uygulamak için çok noktaya yayın iletileri için yanıt vermesi her yazılım bileşeni için hizmet sözleşmesini uygulama ve hizmet sözleşmesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-110">To implement a multicast application, define a service contract and for each software component that needs to respond to the multicast messages, implement the service contract.</span></span> <span data-ttu-id="f2bb5-111">Örneğin, bir bandı uygulaması bir hizmet sözleşmesini tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f2bb5-111">For example, a stock ticker application might define a service contract:</span></span>  
  
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
  
 <span data-ttu-id="f2bb5-112">Çok noktaya yayın iletileri almak istediği her bir uygulama bu arabirimi kullanıma sunan bir hizmet ana bilgisayar gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-112">Each application that wants to receive multicast messages must host a service that exposes this interface.</span></span>  <span data-ttu-id="f2bb5-113">Örneğin, çok noktaya yayın ileti alma gösteren bir kod örneği şöyledir:</span><span class="sxs-lookup"><span data-stu-id="f2bb5-113">For example, here is a code sample that illustrates how to receive multicast messages:</span></span>  
  
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
  
 <span data-ttu-id="f2bb5-114">Uygulamanın tüm hizmetlerin dinlediği UDP adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-114">The application specifies the UDP address that all services will be listening on.</span></span> <span data-ttu-id="f2bb5-115">Yeni bir <xref:System.ServiceModel.ServiceHost> oluşturulur ve bir hizmet uç noktası kullanılarak kullanıma sunulan <xref:System.ServiceModel.UdpBinding>.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-115">A new <xref:System.ServiceModel.ServiceHost> is created and a service endpoint is exposed using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="f2bb5-116"><xref:System.ServiceModel.ServiceHost> Daha sonra açılır ve gelen iletiler için dinleme başlar.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-116">The <xref:System.ServiceModel.ServiceHost> is then opened and will start listening for incoming messages.</span></span>  
  
 <span data-ttu-id="f2bb5-117">Bu tür bir senaryosu, gerçekte çok noktaya yayın iletileri gönderen istemcidir.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-117">In this type of a scenario it is the client that actually sends out multicast messages.</span></span> <span data-ttu-id="f2bb5-118">Doğru UDP adresinde dinleme her hizmet çok noktaya yayın iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-118">Each service that is listening at the correct UDP address will receive the multicast messages.</span></span> <span data-ttu-id="f2bb5-119">Çok noktaya yayın iletilerini gönderme bir istemcinin bir örneği burada verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f2bb5-119">Here is an example of a client that sends out multicast messages:</span></span>  
  
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
  
 <span data-ttu-id="f2bb5-120">Bu kod hisse bilgilerini oluşturur ve doğru UDP adresini dinlemesini Hizmetleri çağırmak için çok noktaya yayın iletileri göndermek için hizmet sözleşmesini IStockTicker kullanır.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-120">This code generates stock information and then uses the service contract IStockTicker to send multicast messages to call services listening on the correct UDP address.</span></span>  
  
### <a name="udp-and-reliable-messaging"></a><span data-ttu-id="f2bb5-121">UDP ve güvenilir Mesajlaşma</span><span class="sxs-lookup"><span data-stu-id="f2bb5-121">UDP and Reliable Messaging</span></span>  
 <span data-ttu-id="f2bb5-122">UDP bağlama UDP protokolünü basit gereği güvenilir Mesajlaşma desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-122">The UDP binding does not support reliable messaging because of the lightweight nature of the UDP protocol.</span></span> <span data-ttu-id="f2bb5-123">İleti uzak uç noktası tarafından alındığında onaylamanız gerekir, örneğin HTTP veya TCP güvenilir Mesajlaşma destekleyen bir taşıma kullanın.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-123">If you need to confirm that messages are received by a remote endpoint, use a transport that supports reliable messaging like  HTTP or TCP.</span></span> <span data-ttu-id="f2bb5-124">Http://go.microsoft.com/fwlink/?LinkId=231830 güvenilir Mesajlaşma hakkında daha fazla bilgi için bkz:</span><span class="sxs-lookup"><span data-stu-id="f2bb5-124">For more information about reliable messaging see http://go.microsoft.com/fwlink/?LinkId=231830</span></span>  
  
### <a name="two-way-multicast-messaging"></a><span data-ttu-id="f2bb5-125">İki yönlü çok noktaya yayın iletileri</span><span class="sxs-lookup"><span data-stu-id="f2bb5-125">Two-way Multicast Messaging</span></span>  
 <span data-ttu-id="f2bb5-126">Çok noktaya yayın iletileri genellikle tek yönlü olsa da, UdpBinding istek/yanıt iletisi exchange desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-126">While multicast messages are generally one-way, the UdpBinding does support request/reply message exchange.</span></span> <span data-ttu-id="f2bb5-127">UDP taşıma kullanarak gönderilen iletileri içeren iki From ve adresine.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-127">Messages sent using the UDP transport contain both a From and To address.</span></span> <span data-ttu-id="f2bb5-128">Kötü amaçlı olarak olabileceğinden KİMDEN adresini kullanarak tr yol değiştiğinde dikkatli olunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-128">Care must be taken when using the From address as it could be maliciously changed en-route.</span></span>  <span data-ttu-id="f2bb5-129">Aşağıdaki kodu kullanarak adresi denetlenebilir:</span><span class="sxs-lookup"><span data-stu-id="f2bb5-129">The address can be checked using the following code:</span></span>  
  
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
  
 <span data-ttu-id="f2bb5-130">Bu kod adresi çok noktaya yayın adresi olduğunu belirten 0xE0 içerip içermediğini Kimden adresinin ilk baytını denetler.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-130">This code checks the first byte of the From address to see if it contains 0xE0 which signifies that the address is a multi-cast address.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="f2bb5-131">Güvenlik Değerlendirmeleri</span><span class="sxs-lookup"><span data-stu-id="f2bb5-131">Security Considerations</span></span>  
 <span data-ttu-id="f2bb5-132">Çok noktaya yayın iletileri için dinlerken, yönlendirici, çok noktaya yayın adresi dinleyen bildiren bir ICMP paketi gönderilir.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-132">When listening for multicast messages an ICMP packet is sent to the router notifying it you are listening on the multicast address.</span></span> <span data-ttu-id="f2bb5-133">Herkes izinlere sahip olan yerel alt ağda, bu paket türleri için dinleme ve hangi çok noktaya yayın adresi ve bağlantı noktası üzerinde dinleyen belirleyin.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-133">Anyone on the local subnet who has permissions could listen for these types of packets and determine which multicast address and port you are listening on.</span></span>  
  
 <span data-ttu-id="f2bb5-134">Gönderenin IP adresi tüm güvenlik amaçlar için kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-134">Do not use the IP address of the sender for any security purposes.</span></span> <span data-ttu-id="f2bb5-135">Bu bilgileri sahte ve yanlış makine yanıtları göndermek bir uygulama neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-135">This information can be spoofed and can cause an application to send responses to the wrong machine.</span></span> <span data-ttu-id="f2bb5-136">Bu tehdidi azaltmak için bir ileti düzeyi güvenliği etkinleştirmek için yoludur.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-136">One way to mitigate this threat is to enable message level security.</span></span> <span data-ttu-id="f2bb5-137">Ağ düzeyinde IPSec (Internet Protokolü güvenliği) ve/veya NAP (Ağ Erişim Koruması) de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f2bb5-137">At the network level IPSec  (Internet Protocol Security) and/or NAP (Network Access Protection) could also be used.</span></span>
