---
description: 'Hakkında daha fazla bilgi edinin: UDP taşıma kullanarak çok noktaya yayın uygulamaları oluşturma'
title: UDP Taşıma Kullanarak Çok Noktaya Yayın Yapan Uygulamalar Oluşturma
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: cea76bc1256d52dabebe525b0fdd8b64c08f9e7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705167"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a><span data-ttu-id="5a232-103">UDP Taşıma Kullanarak Çok Noktaya Yayın Yapan Uygulamalar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5a232-103">Creating Multicasting Applications using the UDP Transport</span></span>

<span data-ttu-id="5a232-104">Çok noktaya yayın uygulamaları, bağlantı noktası bağlantıları oluşturmak gerekmeden çok sayıda alıcıya aynı anda küçük iletiler gönderir.</span><span class="sxs-lookup"><span data-stu-id="5a232-104">Multicasting applications send small messages to a large number of recipients at the same time without the need to establish point to point connections.</span></span> <span data-ttu-id="5a232-105">Bu tür uygulamaların vurgulaması, güvenilirlik üzerinde hızlanır.</span><span class="sxs-lookup"><span data-stu-id="5a232-105">The emphasis of such applications is speed over reliability.</span></span> <span data-ttu-id="5a232-106">Diğer bir deyişle, belirli bir iletinin gerçekten alındığından emin olmak için verilerin zamanında gönderilmesi daha önemlidir.</span><span class="sxs-lookup"><span data-stu-id="5a232-106">In other words, it is more important to send timely data than to ensure any specific message is actually received.</span></span> <span data-ttu-id="5a232-107">WCF artık kullanarak çok noktaya yayın uygulamaları yazmayı desteklemektedir <xref:System.ServiceModel.UdpBinding> .</span><span class="sxs-lookup"><span data-stu-id="5a232-107">WCF now supports writing multicasting applications using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="5a232-108">Bu aktarım, bir hizmetin bir dizi istemciye aynı anda küçük iletiler gönderebilmesi gereken senaryolarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="5a232-108">This transport is useful in scenarios where a service needs to send out small messages to a number of clients simultaneously.</span></span> <span data-ttu-id="5a232-109">Bir stok şeridi uygulaması, bu tür bir hizmete örnektir.</span><span class="sxs-lookup"><span data-stu-id="5a232-109">A stock ticker application is an example of such a service.</span></span>  
  
## <a name="implementing-a-multicast-application"></a><span data-ttu-id="5a232-110">Çok noktaya yayın uygulaması uygulama</span><span class="sxs-lookup"><span data-stu-id="5a232-110">Implementing a Multicast Application</span></span>  

 <span data-ttu-id="5a232-111">Bir çok noktaya yayın uygulaması uygulamak için, bir hizmet sözleşmesi tanımlayın ve çok noktaya yayın iletilerine yanıt vermesi gereken her yazılım bileşeni için hizmet sözleşmesini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="5a232-111">To implement a multicast application, define a service contract and for each software component that needs to respond to the multicast messages, implement the service contract.</span></span> <span data-ttu-id="5a232-112">Örneğin, bir stok şeridi uygulaması bir hizmet sözleşmesini tanımlayabilir:</span><span class="sxs-lookup"><span data-stu-id="5a232-112">For example, a stock ticker application might define a service contract:</span></span>  
  
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
  
 <span data-ttu-id="5a232-113">Çok noktaya yayın iletileri almak isteyen her uygulama, bu arabirimi kullanıma sunan bir hizmeti barındırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5a232-113">Each application that wants to receive multicast messages must host a service that exposes this interface.</span></span>  <span data-ttu-id="5a232-114">Örneğin, çok noktaya yayın iletilerinin nasıl alınacağını gösteren bir kod örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5a232-114">For example, here is a code sample that illustrates how to receive multicast messages:</span></span>  
  
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
  
 <span data-ttu-id="5a232-115">Uygulama, tüm hizmetlerin dinlediği UDP adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5a232-115">The application specifies the UDP address that all services will be listening on.</span></span> <span data-ttu-id="5a232-116">Yeni bir <xref:System.ServiceModel.ServiceHost> oluşturulur ve kullanılarak bir hizmet uç noktası gösterilir <xref:System.ServiceModel.UdpBinding> .</span><span class="sxs-lookup"><span data-stu-id="5a232-116">A new <xref:System.ServiceModel.ServiceHost> is created and a service endpoint is exposed using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="5a232-117"><xref:System.ServiceModel.ServiceHost>Daha sonra açılır ve gelen iletileri dinlemeye başlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="5a232-117">The <xref:System.ServiceModel.ServiceHost> is then opened and will start listening for incoming messages.</span></span>  
  
 <span data-ttu-id="5a232-118">Bu tür bir senaryoda, gerçekte çok noktaya yayın iletilerini gönderen istemcdir.</span><span class="sxs-lookup"><span data-stu-id="5a232-118">In this type of a scenario it is the client that actually sends out multicast messages.</span></span> <span data-ttu-id="5a232-119">Doğru UDP adresini dinleyen her hizmet çok noktaya yayın iletilerini alır.</span><span class="sxs-lookup"><span data-stu-id="5a232-119">Each service that is listening at the correct UDP address will receive the multicast messages.</span></span> <span data-ttu-id="5a232-120">Aşağıda çok noktaya yayın iletileri gönderen bir istemciye örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5a232-120">Here is an example of a client that sends out multicast messages:</span></span>  
  
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
  
 <span data-ttu-id="5a232-121">Bu kod, stok bilgilerini oluşturur ve ardından doğru UDP adresinde dinleme yapan Hizmetleri çağırmak üzere çok noktaya yayın iletileri göndermek için ıtockticker hizmet sözleşmesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5a232-121">This code generates stock information and then uses the service contract IStockTicker to send multicast messages to call services listening on the correct UDP address.</span></span>  
  
### <a name="udp-and-reliable-messaging"></a><span data-ttu-id="5a232-122">UDP ve güvenilir mesajlaşma</span><span class="sxs-lookup"><span data-stu-id="5a232-122">UDP and Reliable Messaging</span></span>  

  <span data-ttu-id="5a232-123">UDP bağlaması, UDP protokolünün hafif doğası nedeniyle güvenilir mesajlaşma özelliğini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="5a232-123">The UDP binding does not support reliable messaging because of the lightweight nature of the UDP protocol.</span></span> <span data-ttu-id="5a232-124">İletilerin uzak bir uç nokta tarafından alındığını onaylamanız gerekiyorsa, HTTP veya TCP gibi güvenilir mesajlaşmayı destekleyen bir aktarım kullanın.</span><span class="sxs-lookup"><span data-stu-id="5a232-124">If you need to confirm that messages are received by a remote endpoint, use a transport that supports reliable messaging like  HTTP or TCP.</span></span> <span data-ttu-id="5a232-125">Güvenilir Mesajlaşma hakkında daha fazla bilgi için bkz <https://go.microsoft.com/fwlink/?LinkId=231830> ..</span><span class="sxs-lookup"><span data-stu-id="5a232-125">For more information about reliable messaging, see <https://go.microsoft.com/fwlink/?LinkId=231830>.</span></span>  
  
### <a name="two-way-multicast-messaging"></a><span data-ttu-id="5a232-126">İki yönlü çok noktaya yayın Iletisi</span><span class="sxs-lookup"><span data-stu-id="5a232-126">Two-way Multicast Messaging</span></span>  

 <span data-ttu-id="5a232-127">Çok noktaya yayın iletileri genellikle tek yönlü olsa da, UdpBinding istek/yanıt iletisi değişimini destekler.</span><span class="sxs-lookup"><span data-stu-id="5a232-127">While multicast messages are generally one-way, the UdpBinding does support request/reply message exchange.</span></span> <span data-ttu-id="5a232-128">UDP taşıması kullanılarak gönderilen iletiler hem kimden hem de kime adresini içerir.</span><span class="sxs-lookup"><span data-stu-id="5a232-128">Messages sent using the UDP transport contain both a From and To address.</span></span> <span data-ttu-id="5a232-129">Kimden adresi kötü amaçlı olarak değiştirilecekse, kimden adresini kullanırken dikkatli olunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5a232-129">Care must be taken when using the From address as it could be maliciously changed en-route.</span></span>  <span data-ttu-id="5a232-130">Adres aşağıdaki kod kullanılarak denetlenebilir:</span><span class="sxs-lookup"><span data-stu-id="5a232-130">The address can be checked using the following code:</span></span>  
  
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
  
 <span data-ttu-id="5a232-131">Bu kod, adresin çok noktaya yayın adresi olduğunu belirten 0xE0 içerip içermediğini görmek için kimden adresinin ilk baytını denetler.</span><span class="sxs-lookup"><span data-stu-id="5a232-131">This code checks the first byte of the From address to see if it contains 0xE0 which signifies that the address is a multi-cast address.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="5a232-132">Güvenlikle İlgili Dikkat Edilmesi Gerekenler</span><span class="sxs-lookup"><span data-stu-id="5a232-132">Security Considerations</span></span>  

 <span data-ttu-id="5a232-133">Çok noktaya yayın iletilerini dinlerken, yönlendiriciye, çok noktaya yayın adresini dinlediğini bildiren bir ıCMP paketi gönderilir.</span><span class="sxs-lookup"><span data-stu-id="5a232-133">When listening for multicast messages an ICMP packet is sent to the router notifying it you are listening on the multicast address.</span></span> <span data-ttu-id="5a232-134">Yerel alt ağ üzerindeki izinleri olan herkes bu paket türlerini dinleyebilir ve hangi çok noktaya yayın adresini ve hangi bağlantı noktasını dinleyeceğini belirleyebilir.</span><span class="sxs-lookup"><span data-stu-id="5a232-134">Anyone on the local subnet who has permissions could listen for these types of packets and determine which multicast address and port you are listening on.</span></span>  
  
 <span data-ttu-id="5a232-135">Tüm güvenlik amaçları için gönderenin IP adresini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="5a232-135">Do not use the IP address of the sender for any security purposes.</span></span> <span data-ttu-id="5a232-136">Bu bilgiler sahte olabilir ve bir uygulamanın yanlış makineye yanıt göndermesini sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="5a232-136">This information can be spoofed and can cause an application to send responses to the wrong machine.</span></span> <span data-ttu-id="5a232-137">Bu tehdidi hafifletmek için bir yol ileti düzeyi güvenliği etkinleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="5a232-137">One way to mitigate this threat is to enable message level security.</span></span> <span data-ttu-id="5a232-138">Ağ düzeyinde IPSec (Internet Protokolü güvenliği) ve/veya NAP (ağ erişim koruması) de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5a232-138">At the network level IPSec  (Internet Protocol Security) and/or NAP (Network Access Protection) could also be used.</span></span>
