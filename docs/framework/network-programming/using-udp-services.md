---
title: UDP Hizmetleri kullanma
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
ms.openlocfilehash: f89a0ad79dbf46c6d75d56106ad05a683482a501
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511611"
---
# <a name="using-udp-services"></a><span data-ttu-id="e1f6e-102">UDP Hizmetleri kullanma</span><span class="sxs-lookup"><span data-stu-id="e1f6e-102">Using UDP Services</span></span>
<span data-ttu-id="e1f6e-103"><xref:System.Net.Sockets.UdpClient> Sınıfı UDP kullanarak Ağ Hizmetleri ile iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-103">The <xref:System.Net.Sockets.UdpClient> class communicates with network services using UDP.</span></span> <span data-ttu-id="e1f6e-104">Özellikleri ve yöntemleri <xref:System.Net.Sockets.UdpClient> oluşturma ayrıntıları soyut sınıf bir <xref:System.Net.Sockets.Socket> istemek ve UDP kullanarak verileri alma.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-104">The properties and methods of the <xref:System.Net.Sockets.UdpClient> class abstract the details of creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using UDP.</span></span>

<span data-ttu-id="e1f6e-105">Kullanıcı Veri Birimi Protokolü (UDP), uzak bir konağa verileri sunmak için bir en iyi hale getiren basit bir protokoldür.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-105">User Datagram Protocol (UDP) is a simple protocol that makes a best effort to deliver data to a remote host.</span></span> <span data-ttu-id="e1f6e-106">Ancak, bağlantısız bir protokol UDP protokolünü olduğundan, uzak uç noktaya gönderdi UDP veri birimi ulşamasını garanti değil ya da, bunlar gönderildiği sırada ulşamasını garanti.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-106">However, because the UDP protocol is a connectionless protocol, UDP datagrams sent to the remote endpoint are not guaranteed to arrive, nor are they guaranteed to arrive in the same sequence in which they are sent.</span></span> <span data-ttu-id="e1f6e-107">UDP kullanan uygulamalar, eksik, yinelenen ve sıra dışı veri birimi işlemek için hazırlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-107">Applications that use UDP must be prepared to handle missing, duplicate, and out-of-sequence datagrams.</span></span>

<span data-ttu-id="e1f6e-108">Bir veri biriminde UDP kullanarak göndermek için barındırma hizmeti ve hizmetin iletişim kurmak için kullandığı UDP bağlantı noktası numarasını ağ cihaz ağ adresini bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-108">To send a datagram using UDP, you must know the network address of the network device hosting the service you need and the UDP port number that the service uses to communicate.</span></span> <span data-ttu-id="e1f6e-109">Ortak Hizmetleri için bağlantı noktası numaralarını Internet Atanmış Numaralar Yetkilisi (IANA) tanımlar (bkz [hizmet adını ve Aktarım Protokolü bağlantı noktası numarasını kayıt defteri](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span><span class="sxs-lookup"><span data-stu-id="e1f6e-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="e1f6e-110">IANA listede olmayan Hizmetleri bağlantı noktası numaraları için 1024 65,535 aralığında olabilir.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-110">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>

<span data-ttu-id="e1f6e-111">Özel ağ adresleri, IP tabanlı ağlarda UDP yayın iletilerini desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-111">Special network addresses are used to support UDP broadcast messages on IP-based networks.</span></span> <span data-ttu-id="e1f6e-112">Aşağıdaki tartışma örnek olarak Internet'te kullanılan IP sürüm 4 Adres ailesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-112">The following discussion uses the IP version 4 address family used on the Internet as an example.</span></span>

<span data-ttu-id="e1f6e-113">IP sürüm 4 adresleri 32 bit bir ağ adresi belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-113">IP version 4 addresses use 32 bits to specify a network address.</span></span> <span data-ttu-id="e1f6e-114">Bir ağ maskesi 255.255.255.0 kullanarak sınıfı C adres için bu bit dört sekizlik tabanda ayrılır.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-114">For class C addresses using a netmask of 255.255.255.0, these bits are separated into four octets.</span></span> <span data-ttu-id="e1f6e-115">Ondalık olarak belirtildiğinde, dört sekizlik tabanda 192.168.100.2 gibi tanıdık dört noktalı gösterimde oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-115">When expressed in decimal, the four octets form the familiar dotted-quad notation, such as 192.168.100.2.</span></span> <span data-ttu-id="e1f6e-116">İlk iki sekizlik tabanda (Bu örnekte 192.168) ağ sayısı form, üçüncü sekizli (100) alt ağı tanımlar ve son sekizli (2) konak tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-116">The first two octets (192.168 in this example) form the network number, the third octet (100) defines the subnet, and the final octet (2) is the host identifier.</span></span>

<span data-ttu-id="e1f6e-117">Bir veya 255.255.255.255, tüm bit'leri bir IP adresi ayarlama sınırlı yayın adresini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-117">Setting all the bits of an IP address to one, or 255.255.255.255, forms the limited broadcast address.</span></span> <span data-ttu-id="e1f6e-118">Bu adrese bir UDP veri birimi gönderme yerel ağ kesimindeki tüm Konaklara iletiyi teslim eder.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-118">Sending a UDP datagram to this address delivers the message to any host on the local network segment.</span></span> <span data-ttu-id="e1f6e-119">Yönlendiriciler hiçbir zaman bu adrese gönderilen iletileri iletmek için yalnızca ağ kesimindeki ana yayın iletisi alırsınız.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-119">Because routers never forward messages sent to this address, only hosts on the network segment receive the broadcast message.</span></span>

<span data-ttu-id="e1f6e-120">Yayınları tüm bitlerinin ana tanımlayıcısının ayarlayarak bir ağ belirli kısımlarını yönlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-120">Broadcasts can be directed to specific portions of a network by setting all bits of the host identifier.</span></span> <span data-ttu-id="e1f6e-121">Örneğin, bir yayın 192.168.1 ile başlangıç IP adresi ile tanımlanan ağdaki tüm konaklar göndermek üzere 192.168.1.255 aralığındaki adresi kullanın.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-121">For example, to send a broadcast to all hosts on the network identified by IP addresses starting with 192.168.1, use the address 192.168.1.255.</span></span>

<span data-ttu-id="e1f6e-122">Aşağıdaki kod örneğinde bir <xref:System.Net.Sockets.UdpClient> UDP veri birimi 11.000 numaralı bağlantı noktasında dinleyecek şekilde.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-122">The following code example uses a <xref:System.Net.Sockets.UdpClient> to listen for UDP datagrams on port 11,000.</span></span> <span data-ttu-id="e1f6e-123">İstemci, bir ileti dizesi alır ve ileti konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-123">The client receives a message string and writes the message to the console.</span></span>

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

<span data-ttu-id="e1f6e-124">Aşağıdaki kod örneğinde bir <xref:System.Net.Sockets.Socket> 11.000 numaralı bağlantı noktasını kullanan yayın adresine için 192.168.1.255 aralığındaki, UDP veri birimi göndermek için.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-124">The following code example uses a <xref:System.Net.Sockets.Socket> to send UDP datagrams to the directed broadcast address 192.168.1.255, using port 11,000.</span></span> <span data-ttu-id="e1f6e-125">İstemci, komut satırında belirtilen ileti dizesi gönderir.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-125">The client sends the message string specified on the command line.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e1f6e-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1f6e-126">See also</span></span>
- <xref:System.Net.Sockets.UdpClient>
- <xref:System.Net.IPAddress>
