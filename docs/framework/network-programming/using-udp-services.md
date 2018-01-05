---
title: UDP Hizmetleri kullanma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 86f44c5aa4c744ab6966f0cb6b3834dd1f5f0f48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-udp-services"></a><span data-ttu-id="53c34-102">UDP Hizmetleri kullanma</span><span class="sxs-lookup"><span data-stu-id="53c34-102">Using UDP Services</span></span>
<span data-ttu-id="53c34-103"><xref:System.Net.Sockets.UdpClient> Sınıfı için UDP kullanan ağ hizmetleri ile iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="53c34-103">The <xref:System.Net.Sockets.UdpClient> class communicates with network services using UDP.</span></span> <span data-ttu-id="53c34-104">Özellikleri ve yöntemleri <xref:System.Net.Sockets.UdpClient> oluşturma ayrıntılarını soyut sınıf bir <xref:System.Net.Sockets.Socket> isteme ve UDP kullanarak veri almak için.</span><span class="sxs-lookup"><span data-stu-id="53c34-104">The properties and methods of the <xref:System.Net.Sockets.UdpClient> class abstract the details of creating a <xref:System.Net.Sockets.Socket> for requesting and receiving data using UDP.</span></span>  
  
 <span data-ttu-id="53c34-105">Kullanıcı Veri Birimi Protokolü (UDP) uzaktaki bir ana bilgisayara verileri sunmak için bir en iyi çaba sağlayan basit bir protokoldür.</span><span class="sxs-lookup"><span data-stu-id="53c34-105">User Datagram Protocol (UDP) is a simple protocol that makes a best effort to deliver data to a remote host.</span></span> <span data-ttu-id="53c34-106">Ancak, UDP protokolünü bağlantısız bir protokol olduğundan, uzak uç noktasına gönderilen UDP veri birimleri gelmesi garanti edilmez ve bunlar gönderilme sırayla gelmesi garanti.</span><span class="sxs-lookup"><span data-stu-id="53c34-106">However, because the UDP protocol is a connectionless protocol, UDP datagrams sent to the remote endpoint are not guaranteed to arrive, nor are they guaranteed to arrive in the same sequence in which they are sent.</span></span> <span data-ttu-id="53c34-107">Eksik, yinelenen ve sıra dışı veri birimi işlemek için UDP kullanan uygulamalar hazırlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="53c34-107">Applications that use UDP must be prepared to handle missing, duplicate, and out-of-sequence datagrams.</span></span>  
  
 <span data-ttu-id="53c34-108">UDP kullanan bir veri birimi göndermek için gereksinim duyduğunuz hizmeti ve hizmetin iletişim kurmak için kullandığı UDP bağlantı noktası numarası barındırma ağ aygıtı ağ adresini bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="53c34-108">To send a datagram using UDP, you must know the network address of the network device hosting the service you need and the UDP port number that the service uses to communicate.</span></span> <span data-ttu-id="53c34-109">Internet Atanmış Numaralar Yetkilisi (IANA) (www.iana.org/assignments/port-numbers bakın) ortak Hizmetleri için bağlantı noktası numaralarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="53c34-109">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (see www.iana.org/assignments/port-numbers).</span></span> <span data-ttu-id="53c34-110">IANA listede olmayan Hizmetleri bağlantı noktası numaraları 1024 65. 535'ı için aralığında olabilir.</span><span class="sxs-lookup"><span data-stu-id="53c34-110">Services not on the Iana list can have port numbers in the range 1,024 to 65,535.</span></span>  
  
 <span data-ttu-id="53c34-111">Özel ağ adresleri, IP tabanlı ağlarda UDP yayın iletileri desteklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="53c34-111">Special network addresses are used to support UDP broadcast messages on IP-based networks.</span></span> <span data-ttu-id="53c34-112">Aşağıdaki tartışma örnek olarak Internet'te kullanılan IP sürüm 4 Adres ailesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="53c34-112">The following discussion uses the IP version 4 address family used on the Internet as an example.</span></span>  
  
 <span data-ttu-id="53c34-113">IP sürüm 4 adresleri 32 bit bir ağ adresi belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="53c34-113">IP version 4 addresses use 32 bits to specify a network address.</span></span> <span data-ttu-id="53c34-114">Ağ maskesi 255.255.255.0 kullanarak C sınıfı adresleri için bu BITS dört sekizli ayrılır.</span><span class="sxs-lookup"><span data-stu-id="53c34-114">For class C addresses using a netmask of 255.255.255.0, these bits are separated into four octets.</span></span> <span data-ttu-id="53c34-115">Ondalık belirtildiğinde, dört sekizli 192.168.100.2 gibi bilinen noktalı dört gösterimini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="53c34-115">When expressed in decimal, the four octets form the familiar dotted-quad notation, such as 192.168.100.2.</span></span> <span data-ttu-id="53c34-116">İlk iki sekizli (Bu örnekte 192.168) ağ numarası form, üçüncü sekizli (100) alt ağı tanımlar ve son sekizli (2) ana bilgisayar tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="53c34-116">The first two octets (192.168 in this example) form the network number, the third octet (100) defines the subnet, and the final octet (2) is the host identifier.</span></span>  
  
 <span data-ttu-id="53c34-117">Bir veya 255.255.255.255, bir IP adresi tüm bit düzeyi ayarını sınırlı yayın adresi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="53c34-117">Setting all the bits of an IP address to one, or 255.255.255.255, forms the limited broadcast address.</span></span> <span data-ttu-id="53c34-118">UDP veri birimi bu adrese gönderdiği iletiyi yerel ağ kesimindeki herhangi bir ana sunar.</span><span class="sxs-lookup"><span data-stu-id="53c34-118">Sending a UDP datagram to this address delivers the message to any host on the local network segment.</span></span> <span data-ttu-id="53c34-119">Yönlendiriciler hiçbir zaman bu adrese gönderilen iletileri iletmek için yalnızca ağ kesimindeki ana yayın iletisi alırsınız.</span><span class="sxs-lookup"><span data-stu-id="53c34-119">Because routers never forward messages sent to this address, only hosts on the network segment receive the broadcast message.</span></span>  
  
 <span data-ttu-id="53c34-120">Yayınları belirli kısımlarını bir ağ için ana bilgisayar tanımlayıcısı tüm bitleri ayarlayarak yönlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="53c34-120">Broadcasts can be directed to specific portions of a network by setting all bits of the host identifier.</span></span> <span data-ttu-id="53c34-121">Örneğin, bir yayın 192.168.1 ile başlayan IP adresleri ile tanımlanan ağdaki tüm ana bilgisayarlara göndermek için 192.168.1.255 adresi kullanın.</span><span class="sxs-lookup"><span data-stu-id="53c34-121">For example, to send a broadcast to all hosts on the network identified by IP addresses starting with 192.168.1, use the address 192.168.1.255.</span></span>  
  
 <span data-ttu-id="53c34-122">Aşağıdaki kod örneğinde bir <xref:System.Net.Sockets.UdpClient> 192.168.1.255 11.000 bağlantı noktasında yönlendirme yapılan yayın adresine gönderilen UDP veri birimleri dinlemek için.</span><span class="sxs-lookup"><span data-stu-id="53c34-122">The following code example uses a <xref:System.Net.Sockets.UdpClient> to listen for UDP datagrams sent to the directed broadcast address 192.168.1.255 on port 11,000.</span></span> <span data-ttu-id="53c34-123">İstemci bir ileti dizesi alır ve ileti konsola yazar.</span><span class="sxs-lookup"><span data-stu-id="53c34-123">The client receives a message string and writes the message to the console.</span></span>  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class UDPListener  
   Private Const listenPort As Integer = 11000  
  
   Private Shared Sub StartListener()  
      Dim done As Boolean = False  
      Dim listener As New UdpClient(listenPort)  
      Dim groupEP As New IPEndPoint(IPAddress.Any, listenPort)  
      Try  
         While Not done  
            Console.WriteLine("Waiting for broadcast")  
            Dim bytes As Byte() = listener.Receive(groupEP)  
            Console.WriteLine("Received broadcast from {0} :", _  
                groupEP.ToString())   
            Console.WriteLine( _  
                Encoding.ASCII.GetString(bytes, 0, bytes.Length))  
            Console.WriteLine()  
         End While  
      Catch e As Exception  
         Console.WriteLine(e.ToString())  
      Finally  
         listener.Close()  
      End Try  
   End Sub 'StartListener  
  
   Public Shared Function Main() As Integer  
      StartListener()  
      Return 0  
   End Function 'Main  
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
        bool done = false;  
  
        UdpClient listener = new UdpClient(listenPort);  
        IPEndPoint groupEP = new IPEndPoint(IPAddress.Any,listenPort);  
  
        try   
        {  
            while (!done)   
            {  
                Console.WriteLine("Waiting for broadcast");  
                byte[] bytes = listener.Receive( ref groupEP);  
  
                Console.WriteLine("Received broadcast from {0} :\n {1}\n",  
                    groupEP.ToString(),  
                    Encoding.ASCII.GetString(bytes,0,bytes.Length));  
            }  
  
        }   
        catch (Exception e)   
        {  
            Console.WriteLine(e.ToString());  
        }  
        finally  
        {  
            listener.Close();  
        }  
    }  
  
    public static int Main()   
    {  
        StartListener();  
  
        return 0;  
    }  
}  
```  
  
 <span data-ttu-id="53c34-124">Aşağıdaki kod örneğinde bir <xref:System.Net.Sockets.UdpClient> bağlantı noktası 11.000 kullanarak yönlendirme yapılan yayın adresine için 192.168.1.255, UDP veri birimleri göndermek için.</span><span class="sxs-lookup"><span data-stu-id="53c34-124">The following code example uses a <xref:System.Net.Sockets.UdpClient> to send UDP datagrams to the directed broadcast address 192.168.1.255, using port 11,000.</span></span> <span data-ttu-id="53c34-125">İstemci komut satırında belirtilen ileti dizesi gönderir.</span><span class="sxs-lookup"><span data-stu-id="53c34-125">The client sends the message string specified on the command line.</span></span>  
  
```vb  
Imports System  
Imports System.Net  
Imports System.Net.Sockets  
Imports System.Text  
  
Public Class Program  
  
    Overloads Public Shared Function Main(args() As [String]) As Integer  
      Dim s As New Socket(AddressFamily.InterNetwork, SocketType.Dgram,  
          ProtocolType.Udp)  
      Dim broadcast As IPAddress = IPAddress.Parse("192.168.1.255")  
      Dim sendbuf As Byte() = Encoding.ASCII.GetBytes(args(0))  
      Dim ep As New IPEndPoint(broadcast, 11000)  
      s.SendTo(sendbuf, ep)  
      Console.WriteLine("Message sent to the broadcast address")  
   End Function 'Main  
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
        Socket s = new Socket(AddressFamily.InterNetwork, SocketType.Dgram,  
            ProtocolType.Udp);  
  
        IPAddress broadcast = IPAddress.Parse("192.168.1.255");  
  
        byte[] sendbuf = Encoding.ASCII.GetBytes(args[0]);  
        IPEndPoint ep = new IPEndPoint(broadcast, 11000);  
  
        s.SendTo(sendbuf, ep);  
  
        Console.WriteLine("Message sent to the broadcast address");  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="53c34-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="53c34-126">See Also</span></span>  
 <xref:System.Net.Sockets.UdpClient>  
 <xref:System.Net.IPAddress>  
 
