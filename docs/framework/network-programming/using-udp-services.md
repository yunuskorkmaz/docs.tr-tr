---
title: UDP Hizmetleri Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- protocols, UDP
- network resources, UDP
- requesting data from Internet, UDP
- UDP
- receiving data, UDP
- Internet, UDP
- broadcasting messages to multiple addresses
- data requests, UDP
- UdpClient class, about UdpClient class
- sending data, UDP
- application protocols, UDP
ms.assetid: d5c3477a-e798-454c-a890-738ba14c5707
ms.openlocfilehash: 477095ada6e44f66cbc60cd80375da9a87f38e39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180612"
---
# <a name="using-udp-services"></a><span data-ttu-id="2e6f4-102">UDP Hizmetleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="2e6f4-102">Using UDP Services</span></span>
<span data-ttu-id="2e6f4-103">Sınıf <xref:System.Net.Sockets.UdpClient> UDP kullanarak ağ hizmetleri ile iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-103">The <xref:System.Net.Sockets.UdpClient> class communicates with network services using UDP.</span></span> <span data-ttu-id="2e6f4-104"><xref:System.Net.Sockets.UdpClient> Sınıfın özellikleri ve yöntemleri UDP kullanarak <xref:System.Net.Sockets.Socket> veri istemek ve almak için oluşturma ayrıntılarını özetler.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-104">The properties and methods of the <xref:System.Net.Sockets.UdpClient> class abstract the details of creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using UDP.</span></span>

<span data-ttu-id="2e6f4-105">Kullanıcı Datagram Protokolü (UDP), uzak bir ana bilgisayara veri sağlamak için en iyi çabayı gösteren basit bir protokoldür.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-105">User Datagram Protocol (UDP) is a simple protocol that makes a best effort to deliver data to a remote host.</span></span> <span data-ttu-id="2e6f4-106">Ancak, UDP protokolü bağlantısız bir protokol olduğundan, uzak uç noktasına gönderilen UDP verigramlarının gelmesi garanti edilmez ve gönderildikleri sırayla ulaşmaları garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-106">However, because the UDP protocol is a connectionless protocol, UDP datagrams sent to the remote endpoint are not guaranteed to arrive, nor are they guaranteed to arrive in the same sequence in which they are sent.</span></span> <span data-ttu-id="2e6f4-107">UDP kullanan uygulamalar eksik, yinelenen ve sıra dışı veri gramlarını işlemek için hazırlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-107">Applications that use UDP must be prepared to handle missing, duplicate, and out-of-sequence datagrams.</span></span>

<span data-ttu-id="2e6f4-108">UDP kullanarak bir veri gramı göndermek için, gereksinim duyduğunuz hizmeti barındıran ağ aygıtının ağ adresini ve hizmetin iletişim kurmak için kullandığı UDP bağlantı noktası numarasını bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-108">To send a datagram using UDP, you must know the network address of the network device hosting the service you need and the UDP port number that the service uses to communicate.</span></span> <span data-ttu-id="2e6f4-109">Internet Atanmış Sayılar Yetkilisi (Iana), ortak hizmetler için bağlantı noktası numaralarını tanımlar (bkz. [Hizmet Adı ve Taşıma Protokolü Bağlantı Noktası Numarası Kayıt Defteri).](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)</span><span class="sxs-lookup"><span data-stu-id="2e6f4-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="2e6f4-110">Iana listesinde olmayan hizmetlerin bağlantı noktası numaraları 1.024 ile 65.535 arasında olabilir.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-110">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>

<span data-ttu-id="2e6f4-111">ÖZEL ağ adresleri, IP tabanlı ağlardaki UDP yayın iletilerini desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-111">Special network addresses are used to support UDP broadcast messages on IP-based networks.</span></span> <span data-ttu-id="2e6f4-112">Aşağıdaki tartışma, Internet'te kullanılan IP sürüm 4 adresi ailesini örnek olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-112">The following discussion uses the IP version 4 address family used on the Internet as an example.</span></span>

<span data-ttu-id="2e6f4-113">IP sürüm 4 adresleri bir ağ adresi belirtmek için 32 bit kullanır.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-113">IP version 4 addresses use 32 bits to specify a network address.</span></span> <span data-ttu-id="2e6f4-114">255.255.255.0 netmask kullanarak C sınıfı adresler için bu bitler dört sekizliye ayrılır.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-114">For class C addresses using a netmask of 255.255.255.0, these bits are separated into four octets.</span></span> <span data-ttu-id="2e6f4-115">Ondalık olarak ifade edildiğinde, dört sekizli 192.168.100.2 gibi tanıdık noktalı dörtlü gösterimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-115">When expressed in decimal, the four octets form the familiar dotted-quad notation, such as 192.168.100.2.</span></span> <span data-ttu-id="2e6f4-116">İlk iki sekizli (bu örnekte 192.168) ağ numarasını oluşturur, üçüncü sekizli (100) alt ağı tanımlar ve son sekizli (2) ana bilgisayar tanımlayıcısIdır.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-116">The first two octets (192.168 in this example) form the network number, the third octet (100) defines the subnet, and the final octet (2) is the host identifier.</span></span>

<span data-ttu-id="2e6f4-117">Bir IP adresinin tüm bitlerini bir veya 255.255.255.255 olarak ayarlamak sınırlı yayın adresini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-117">Setting all the bits of an IP address to one, or 255.255.255.255, forms the limited broadcast address.</span></span> <span data-ttu-id="2e6f4-118">Bu adrese bir UDP veri gramı göndermek, iletiyi yerel ağ segmentindeki herhangi bir ana bilgisayara gönderir.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-118">Sending a UDP datagram to this address delivers the message to any host on the local network segment.</span></span> <span data-ttu-id="2e6f4-119">Yönlendiriciler bu adrese gönderilen iletileri hiçbir zaman iletmediğinden, yayın iletisini yalnızca ağ segmentindeki ana bilgisayarlar alır.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-119">Because routers never forward messages sent to this address, only hosts on the network segment receive the broadcast message.</span></span>

<span data-ttu-id="2e6f4-120">Yayınlar, ana bilgisayar tanımlayıcısının tüm bitlerini ayarlayarak ağın belirli bölümlerine yönlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-120">Broadcasts can be directed to specific portions of a network by setting all bits of the host identifier.</span></span> <span data-ttu-id="2e6f4-121">Örneğin, 192.168.1 ile başlayan IP adresleri tarafından tanımlanan ağdaki tüm ana bilgisayarlara yayın göndermek için 192.168.1.255 adresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-121">For example, to send a broadcast to all hosts on the network identified by IP addresses starting with 192.168.1, use the address 192.168.1.255.</span></span>

<span data-ttu-id="2e6f4-122">Aşağıdaki kod örneği, <xref:System.Net.Sockets.UdpClient> bağlantı noktası 11.000'deki UDP verigramlarını dinlemek için bir örnek kullanır.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-122">The following code example uses a <xref:System.Net.Sockets.UdpClient> to listen for UDP datagrams on port 11,000.</span></span> <span data-ttu-id="2e6f4-123">İstemci bir ileti dizesi alır ve iletiyi konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-123">The client receives a message string and writes the message to the console.</span></span>

```vb
Imports System.Net
Imports System.Net.Sockets
Imports System.Text

Public Class UDPListener
   Private Const listenPort As Integer = 11000

   Private Shared Sub StartListener()
      Dim listener As New UdpClient(listenPort)
      Dim groupEP As New IPEndPoint(IPAddress.Any, listenPort)
      Try
         While True
            Console.WriteLine("Waiting for broadcast")
            Dim bytes As Byte() = listener.Receive(groupEP)
            Console.WriteLine("Received broadcast from {0} :", groupEP)
            Console.WriteLine(Encoding.ASCII.GetString(bytes, 0, bytes.Length))
         End While
      Catch e As SocketException
         Console.WriteLine(e)
      Finally
         listener.Close()
      End Try
   End Sub 'StartListener

   Public Shared Sub Main()
      StartListener()
   End Sub 'Main
End Class 'UDPListener
```

```csharp
using System;
using System.Net;
using System.Net.Sockets;
using System.Text;

public class UDPListener
{
    private const int listenPort = 11000;

    private static void StartListener()
    {
        UdpClient listener = new UdpClient(listenPort);
        IPEndPoint groupEP = new IPEndPoint(IPAddress.Any, listenPort);

        try
        {
            while (true)
            {
                Console.WriteLine("Waiting for broadcast");
                byte[] bytes = listener.Receive(ref groupEP);

                Console.WriteLine($"Received broadcast from {groupEP} :");
                Console.WriteLine($" {Encoding.ASCII.GetString(bytes, 0, bytes.Length)}");
            }
        }
        catch (SocketException e)
        {
            Console.WriteLine(e);
        }
        finally
        {
            listener.Close();
        }
    }

    public static void Main()
    {
        StartListener();
    }
}
```

<span data-ttu-id="2e6f4-124">Aşağıdaki kod örneği, <xref:System.Net.Sockets.Socket> 11.000 no'lu bağlantı noktasını kullanarak UDP veri gramlarını yönlendirilmiş yayın adresi 192.168.1.255'e göndermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-124">The following code example uses a <xref:System.Net.Sockets.Socket> to send UDP datagrams to the directed broadcast address 192.168.1.255, using port 11,000.</span></span> <span data-ttu-id="2e6f4-125">İstemci komut satırında belirtilen ileti dizesini gönderir.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-125">The client sends the message string specified on the command line.</span></span>

```vb
Imports System.Net
Imports System.Net.Sockets
Imports System.Text

Public Class Program
    Public Shared Sub Main(args() As [String])
      Dim s As New Socket(AddressFamily.InterNetwork, SocketType.Dgram, ProtocolType.Udp)
      Dim broadcast As IPAddress = IPAddress.Parse("192.168.1.255")
      Dim sendbuf As Byte() = Encoding.ASCII.GetBytes(args(0))
      Dim ep As New IPEndPoint(broadcast, 11000)
      s.SendTo(sendbuf, ep)
      Console.WriteLine("Message sent to the broadcast address")
   End Sub 'Main
End Class
```

```csharp
using System;
using System.Net;
using System.Net.Sockets;
using System.Text;

class Program
{
    static void Main(string[] args)
    {
        Socket s = new Socket(AddressFamily.InterNetwork, SocketType.Dgram, ProtocolType.Udp);

        IPAddress broadcast = IPAddress.Parse("192.168.1.255");

        byte[] sendbuf = Encoding.ASCII.GetBytes(args[0]);
        IPEndPoint ep = new IPEndPoint(broadcast, 11000);

        s.SendTo(sendbuf, ep);

        Console.WriteLine("Message sent to the broadcast address");
    }
}
```

## <a name="see-also"></a><span data-ttu-id="2e6f4-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e6f4-126">See also</span></span>

- <xref:System.Net.Sockets.UdpClient>
- <xref:System.Net.IPAddress>
