---
title: TCP-UDP
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
ms.openlocfilehash: d35278ab7feb42453b5a0adbc86c47b7ac3ff5ca
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047107"
---
# <a name="tcp-udp"></a><span data-ttu-id="c918b-102">TCP-UDP</span><span class="sxs-lookup"><span data-stu-id="c918b-102">TCP-UDP</span></span>
<span data-ttu-id="c918b-103">Uygulamalar <xref:System.Net.Sockets.TcpClient>,, <xref:System.Net.Sockets.TcpListener>ve <xref:System.Net.Sockets.UdpClient> sınıflarıyla iletim Denetim Protokolü (TCP) ve Kullanıcı Datagram Protokolü (UDP) hizmetlerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="c918b-103">Applications can use Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) services with the <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes.</span></span> <span data-ttu-id="c918b-104">Bu protokol sınıfları <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> sınıfının üzerine kurulmuştur ve veri aktarma ayrıntılarının ayrıntılarını alır.</span><span class="sxs-lookup"><span data-stu-id="c918b-104">These protocol classes are built on top of the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class and take care of the details of transferring data.</span></span>  
  
 <span data-ttu-id="c918b-105">Protokol sınıfları, durum bilgilerini koruma veya protokole özgü yuvaları ayarlama ayrıntılarını bilme olmadan ağ hizmetlerine basit ve kolay erişim sağlamak için **yuva** sınıfının zaman uyumlu yöntemlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c918b-105">The protocol classes use the synchronous methods of the **Socket** class to provide simple and straightforward access to network services without the overhead of maintaining state information or knowing the details of setting up protocol-specific sockets.</span></span> <span data-ttu-id="c918b-106">Zaman uyumsuz **yuva** yöntemlerini kullanmak için, <xref:System.Net.Sockets.NetworkStream> sınıfı tarafından sağlanan zaman uyumsuz yöntemleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c918b-106">To use asynchronous **Socket** methods, you can use the asynchronous methods supplied by the <xref:System.Net.Sockets.NetworkStream> class.</span></span> <span data-ttu-id="c918b-107">Protokol sınıfları tarafından gösterilmeyen **yuva** sınıfının özelliklerine erişmek için **yuva** sınıfını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c918b-107">To access features of the **Socket** class not exposed by the protocol classes, you must use the **Socket** class.</span></span>  
  
 <span data-ttu-id="c918b-108">**TcpClient** ve **TcpListener** , **NetworkStream** sınıfını kullanarak ağı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c918b-108">**TcpClient** and **TcpListener** represent the network using the **NetworkStream** class.</span></span> <span data-ttu-id="c918b-109">Ağ akışını döndürmek <xref:System.Net.Sockets.TcpClient.GetStream%2A> için yöntemini kullanın ve ardından <xref:System.Net.Sockets.NetworkStream.Read%2A> akışın ve <xref:System.Net.Sockets.NetworkStream.Write%2A> yöntemlerini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c918b-109">You use the <xref:System.Net.Sockets.TcpClient.GetStream%2A> method to return the network stream, and then call the stream's <xref:System.Net.Sockets.NetworkStream.Read%2A> and <xref:System.Net.Sockets.NetworkStream.Write%2A> methods.</span></span> <span data-ttu-id="c918b-110">**NetworkStream** , temel alınan yuvaya ait protokol sınıflarının sahibi değil, bu nedenle bunu kapatmak yuvayı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="c918b-110">The **NetworkStream** does not own the protocol classes' underlying socket, so closing it does not affect the socket.</span></span>  
  
 <span data-ttu-id="c918b-111">**UdpClient** sınıfı, UDP veri birimini tutmak için bir bayt dizisi kullanır.</span><span class="sxs-lookup"><span data-stu-id="c918b-111">The **UdpClient** class uses an array of bytes to hold the UDP datagram.</span></span> <span data-ttu-id="c918b-112">Verileri ağa göndermek <xref:System.Net.Sockets.UdpClient.Send%2A> için yöntemini <xref:System.Net.Sockets.UdpClient.Receive%2A> ve gelen bir veri birimini alma yöntemini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c918b-112">You use the <xref:System.Net.Sockets.UdpClient.Send%2A> method to send the data to the network and the <xref:System.Net.Sockets.UdpClient.Receive%2A> method to receive an incoming datagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c918b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c918b-113">See also</span></span>

- [<span data-ttu-id="c918b-114">TCP Hizmetleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="c918b-114">Using TCP Services</span></span>](using-tcp-services.md)
- [<span data-ttu-id="c918b-115">UDP Hizmetleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="c918b-115">Using UDP Services</span></span>](using-udp-services.md)
- [<span data-ttu-id="c918b-116">Ağda Akışları Kullanma</span><span class="sxs-lookup"><span data-stu-id="c918b-116">Using Streams on the Network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="c918b-117">Zaman Uyumsuz Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="c918b-117">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="c918b-118">Zaman Uyumsuz İstemci Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="c918b-118">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="c918b-119">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="c918b-119">Using Application Protocols</span></span>](using-application-protocols.md)
