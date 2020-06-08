---
title: UDP Hizmetleri Kullanma
description: UdpClient sınıfı, .NET Framework UDP kullanarak veri istemek ve almak için bir yuva oluşturmak üzere ayrıntıları soyutlar.
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
ms.openlocfilehash: 4c2e88492f737800151d30097719d7d011054a5e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501956"
---
# <a name="use-udp-services"></a><span data-ttu-id="ef006-103">UDP hizmetlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="ef006-103">Use UDP services</span></span>

<span data-ttu-id="ef006-104"><xref:System.Net.Sockets.UdpClient>Sınıfı, UDP kullanarak ağ hizmetleriyle iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="ef006-104">The <xref:System.Net.Sockets.UdpClient> class communicates with network services using UDP.</span></span> <span data-ttu-id="ef006-105">Sınıfının özellikleri ve yöntemleri, <xref:System.Net.Sockets.UdpClient> <xref:System.Net.Sockets.Socket> UDP kullanarak veri istemek ve almak için oluşturma ayrıntılarını soyutlar.</span><span class="sxs-lookup"><span data-stu-id="ef006-105">The properties and methods of the <xref:System.Net.Sockets.UdpClient> class abstract the details of creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using UDP.</span></span>

<span data-ttu-id="ef006-106">Kullanıcı veri birimi Protokolü (UDP), uzak bir konağa veri teslim etmeyi en iyi şekilde kolaylaştıran bir basit protokoldür.</span><span class="sxs-lookup"><span data-stu-id="ef006-106">User Datagram Protocol (UDP) is a simple protocol that makes a best effort to deliver data to a remote host.</span></span> <span data-ttu-id="ef006-107">Bununla birlikte, UDP protokolü bağlantısız bir protokol olduğundan, uzak uç noktaya gönderilen UDP veri birimlerinin gelmesi garanti edilmez, ne de gönderildikleri sırada gelmesi garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="ef006-107">However, because the UDP protocol is a connectionless protocol, UDP datagrams sent to the remote endpoint are not guaranteed to arrive, nor are they guaranteed to arrive in the same sequence in which they are sent.</span></span> <span data-ttu-id="ef006-108">UDP kullanan uygulamalar eksik, yinelenen ve dizi dışı datagramları işleyecek şekilde hazırlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef006-108">Applications that use UDP must be prepared to handle missing, duplicate, and out-of-sequence datagrams.</span></span>

<span data-ttu-id="ef006-109">UDP kullanarak bir veri birimi göndermek için, ihtiyacınız olan hizmeti barındıran ağ cihazının ağ adresini ve hizmetin iletişim kurmak için kullandığı UDP bağlantı noktası numarasını bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef006-109">To send a datagram using UDP, you must know the network address of the network device hosting the service you need and the UDP port number that the service uses to communicate.</span></span> <span data-ttu-id="ef006-110">Internet atanmış numaralar yetkilisi (ıANA), ortak hizmetler için bağlantı noktası numaralarını tanımlar (bkz. [hizmet adı ve Aktarım Protokolü bağlantı noktası numarası kayıt defteri](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span><span class="sxs-lookup"><span data-stu-id="ef006-110">The Internet Assigned Numbers Authority (IANA) defines port numbers for common services (see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="ef006-111">IANA listesinde bulunmayan hizmetler 1.024-65.535 aralığında bağlantı noktası numaralarına sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="ef006-111">Services not on the IANA list can have port numbers in the range 1,024 to 65,535.</span></span>

<span data-ttu-id="ef006-112">Özel ağ adresleri IP tabanlı ağlardaki UDP yayın iletilerini desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef006-112">Special network addresses are used to support UDP broadcast messages on IP-based networks.</span></span> <span data-ttu-id="ef006-113">Aşağıdaki tartışmada, Internet üzerinde kullanılan IP sürüm 4 adres ailesi bir örnek olarak kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ef006-113">The following discussion uses the IP version 4 address family used on the Internet as an example.</span></span>

<span data-ttu-id="ef006-114">IP sürüm 4 adresleri bir ağ adresi belirtmek için 32 bit kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef006-114">IP version 4 addresses use 32 bits to specify a network address.</span></span> <span data-ttu-id="ef006-115">255.255.255.0 ağ maskesini kullanan sınıf C adresleri için, bu bitler dört sekizlik ile ayrılır.</span><span class="sxs-lookup"><span data-stu-id="ef006-115">For class C addresses using a netmask of 255.255.255.0, these bits are separated into four octets.</span></span> <span data-ttu-id="ef006-116">Ondalık olarak ifade edildiğinde, dört sekizli, 192.168.100.2 gibi tanıdık noktalı dörtlü gösterimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ef006-116">When expressed in decimal, the four octets form the familiar dotted-quad notation, such as 192.168.100.2.</span></span> <span data-ttu-id="ef006-117">İlk iki sekizli (Bu örnekteki 192,168) ağ numarasını, üçüncü sekizli (100) alt ağı tanımlar ve son sekizli (2) konak tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="ef006-117">The first two octets (192.168 in this example) form the network number, the third octet (100) defines the subnet, and the final octet (2) is the host identifier.</span></span>

<span data-ttu-id="ef006-118">Bir IP adresinin tüm bitlerini bir veya 255.255.255.255 olarak ayarlamak, sınırlı yayın adresini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ef006-118">Setting all the bits of an IP address to one, or 255.255.255.255, forms the limited broadcast address.</span></span> <span data-ttu-id="ef006-119">Bu adrese bir UDP veri birimi gönderilmesi, iletiyi yerel ağ kesimindeki herhangi bir konağa gönderir.</span><span class="sxs-lookup"><span data-stu-id="ef006-119">Sending a UDP datagram to this address delivers the message to any host on the local network segment.</span></span> <span data-ttu-id="ef006-120">Yönlendiriciler bu adrese gönderilen iletileri hiçbir şekilde iletmediği için, yalnızca ağ kesimindeki konaklar yayın iletisini alır.</span><span class="sxs-lookup"><span data-stu-id="ef006-120">Because routers never forward messages sent to this address, only hosts on the network segment receive the broadcast message.</span></span>

<span data-ttu-id="ef006-121">Yayınlar, ana bilgisayar tanımlayıcısının tüm bitlerini ayarlayarak bir ağın belirli bölümlerine yönlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ef006-121">Broadcasts can be directed to specific portions of a network by setting all bits of the host identifier.</span></span> <span data-ttu-id="ef006-122">Örneğin, 192.168.1 ile başlayan IP adresleri tarafından tanımlanan ağdaki tüm konaklara bir yayın göndermek için 192.168.1.255 aralığındaki adresini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef006-122">For example, to send a broadcast to all hosts on the network identified by IP addresses starting with 192.168.1, use the address 192.168.1.255.</span></span>

<span data-ttu-id="ef006-123">Aşağıdaki kod örneği, <xref:System.Net.Sockets.UdpClient> bağlantı noktası 11.000 ' DEKI UDP datagramları dinlemek için bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef006-123">The following code example uses a <xref:System.Net.Sockets.UdpClient> to listen for UDP datagrams on port 11,000.</span></span> <span data-ttu-id="ef006-124">İstemci bir ileti dizesi alır ve iletiyi konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="ef006-124">The client receives a message string and writes the message to the console.</span></span>

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

<span data-ttu-id="ef006-125">Aşağıdaki kod örneği, <xref:System.Net.Sockets.Socket> 11.000 numaralı bağlantı noktasını kullanarak 192.168.1.255 aralığındaki yönlendirilmiş yayın ADRESINE UDP veri birimleri göndermek için bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef006-125">The following code example uses a <xref:System.Net.Sockets.Socket> to send UDP datagrams to the directed broadcast address 192.168.1.255, using port 11,000.</span></span> <span data-ttu-id="ef006-126">İstemci, komut satırında belirtilen ileti dizesini gönderir.</span><span class="sxs-lookup"><span data-stu-id="ef006-126">The client sends the message string specified on the command line.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ef006-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef006-127">See also</span></span>

- <xref:System.Net.Sockets.UdpClient>
- <xref:System.Net.IPAddress>
