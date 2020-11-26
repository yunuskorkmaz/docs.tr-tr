---
title: TCP-UDP
description: TcpClient, TcpListener ve Udpistemci sınıflarının TCP ve UDP hizmetlerini nasıl işleyeceğini öğrenin ve bu, .NET Framework veri aktarımının ayrıntılarını ele alır.
ms.date: 03/30/2017
helpviewer_keywords:
- protocols, TCP/UDP
- network resources, TCP/UDP
- sending data, TCP/UDP
- TCP/UDP
- TcpClient class, about TcpClient class
- application protocols, TCP/UDP
- receiving data, TCP/UDP
- TcpListener class, about TcpListener class
- Socket class, about Socket class
- UDP
- data requests, TCP/UDP
- requesting data from Internet, TCP/UDP
- Internet, TCP/UDP
ms.assetid: df29b4b0-49e8-4923-82b9-13150dfc40f5
ms.openlocfilehash: b5b8b5cb3ce38fcff9115b2f9acf23fc5a970adf
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239452"
---
# <a name="tcp-udp"></a><span data-ttu-id="1cf17-103">TCP-UDP</span><span class="sxs-lookup"><span data-stu-id="1cf17-103">TCP-UDP</span></span>

<span data-ttu-id="1cf17-104">Uygulamalar <xref:System.Net.Sockets.TcpClient> ,, ve sınıflarıyla Iletim Denetim Protokolü (TCP) ve Kullanıcı Datagram Protokolü (UDP) hizmetlerini kullanabilir <xref:System.Net.Sockets.TcpListener> <xref:System.Net.Sockets.UdpClient> .</span><span class="sxs-lookup"><span data-stu-id="1cf17-104">Applications can use Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) services with the <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes.</span></span> <span data-ttu-id="1cf17-105">Bu protokol sınıfları sınıfının üzerine kurulmuştur <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> ve veri aktarma ayrıntılarının ayrıntılarını alır.</span><span class="sxs-lookup"><span data-stu-id="1cf17-105">These protocol classes are built on top of the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class and take care of the details of transferring data.</span></span>  
  
 <span data-ttu-id="1cf17-106">Protokol sınıfları, durum bilgilerini koruma veya protokole özgü yuvaları ayarlama ayrıntılarını bilme olmadan ağ hizmetlerine basit ve kolay erişim sağlamak için **yuva** sınıfının zaman uyumlu yöntemlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1cf17-106">The protocol classes use the synchronous methods of the **Socket** class to provide simple and straightforward access to network services without the overhead of maintaining state information or knowing the details of setting up protocol-specific sockets.</span></span> <span data-ttu-id="1cf17-107">Zaman uyumsuz **yuva** yöntemlerini kullanmak için, sınıfı tarafından sağlanan zaman uyumsuz yöntemleri kullanabilirsiniz <xref:System.Net.Sockets.NetworkStream> .</span><span class="sxs-lookup"><span data-stu-id="1cf17-107">To use asynchronous **Socket** methods, you can use the asynchronous methods supplied by the <xref:System.Net.Sockets.NetworkStream> class.</span></span> <span data-ttu-id="1cf17-108">Protokol sınıfları tarafından gösterilmeyen **yuva** sınıfının özelliklerine erişmek için **yuva** sınıfını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1cf17-108">To access features of the **Socket** class not exposed by the protocol classes, you must use the **Socket** class.</span></span>  
  
 <span data-ttu-id="1cf17-109">**TcpClient** ve **TcpListener** , **NetworkStream** sınıfını kullanarak ağı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1cf17-109">**TcpClient** and **TcpListener** represent the network using the **NetworkStream** class.</span></span> <span data-ttu-id="1cf17-110"><xref:System.Net.Sockets.TcpClient.GetStream%2A>Ağ akışını döndürmek için yöntemini kullanın ve ardından akışın <xref:System.Net.Sockets.NetworkStream.Read%2A> ve <xref:System.Net.Sockets.NetworkStream.Write%2A> yöntemlerini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cf17-110">You use the <xref:System.Net.Sockets.TcpClient.GetStream%2A> method to return the network stream, and then call the stream's <xref:System.Net.Sockets.NetworkStream.Read%2A> and <xref:System.Net.Sockets.NetworkStream.Write%2A> methods.</span></span> <span data-ttu-id="1cf17-111">**NetworkStream** , temel alınan yuvaya ait protokol sınıflarının sahibi değil, bu nedenle bunu kapatmak yuvayı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="1cf17-111">The **NetworkStream** does not own the protocol classes' underlying socket, so closing it does not affect the socket.</span></span>  
  
 <span data-ttu-id="1cf17-112">**UdpClient** sınıfı, UDP veri birimini tutmak için bir bayt dizisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="1cf17-112">The **UdpClient** class uses an array of bytes to hold the UDP datagram.</span></span> <span data-ttu-id="1cf17-113"><xref:System.Net.Sockets.UdpClient.Send%2A>Verileri ağa göndermek için yöntemini ve <xref:System.Net.Sockets.UdpClient.Receive%2A> gelen bir veri birimini alma yöntemini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="1cf17-113">You use the <xref:System.Net.Sockets.UdpClient.Send%2A> method to send the data to the network and the <xref:System.Net.Sockets.UdpClient.Receive%2A> method to receive an incoming datagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cf17-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1cf17-114">See also</span></span>

- [<span data-ttu-id="1cf17-115">TCP Hizmetleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="1cf17-115">Using TCP Services</span></span>](using-tcp-services.md)
- [<span data-ttu-id="1cf17-116">UDP Hizmetleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="1cf17-116">Using UDP Services</span></span>](using-udp-services.md)
- [<span data-ttu-id="1cf17-117">Ağda Akışları Kullanma</span><span class="sxs-lookup"><span data-stu-id="1cf17-117">Using Streams on the Network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="1cf17-118">Zaman Uyumsuz Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="1cf17-118">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="1cf17-119">Zaman Uyumsuz İstemci Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="1cf17-119">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="1cf17-120">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="1cf17-120">Using Application Protocols</span></span>](using-application-protocols.md)
