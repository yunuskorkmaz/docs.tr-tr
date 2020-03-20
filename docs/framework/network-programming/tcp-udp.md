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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047107"
---
# <a name="tcp-udp"></a><span data-ttu-id="211ed-102">TCP-UDP</span><span class="sxs-lookup"><span data-stu-id="211ed-102">TCP-UDP</span></span>
<span data-ttu-id="211ed-103">Uygulamalar, İletim Kontrol Protokolü (TCP) ve Kullanıcı Datagram Protokolü <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.TcpListener>(UDP) hizmetlerini , ve <xref:System.Net.Sockets.UdpClient> sınıflarla kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="211ed-103">Applications can use Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) services with the <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes.</span></span> <span data-ttu-id="211ed-104">Bu protokol sınıfları <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> sınıfın en üstünde inşa edilir ve veri aktarım ayrıntılarıdikkat çekmek.</span><span class="sxs-lookup"><span data-stu-id="211ed-104">These protocol classes are built on top of the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class and take care of the details of transferring data.</span></span>  
  
 <span data-ttu-id="211ed-105">Protokol sınıfları, durum bilgilerini koruma veya protokole özgü soketleri ayarlama ayrıntılarını bilme den ek yükü olmadan ağ hizmetlerine basit ve basit erişim sağlamak için **Soket** sınıfının eşzamanlı yöntemlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="211ed-105">The protocol classes use the synchronous methods of the **Socket** class to provide simple and straightforward access to network services without the overhead of maintaining state information or knowing the details of setting up protocol-specific sockets.</span></span> <span data-ttu-id="211ed-106">Eşzamanlı **Soket** yöntemlerini kullanmak <xref:System.Net.Sockets.NetworkStream> için, sınıf tarafından sağlanan eşzamanlı yöntemleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="211ed-106">To use asynchronous **Socket** methods, you can use the asynchronous methods supplied by the <xref:System.Net.Sockets.NetworkStream> class.</span></span> <span data-ttu-id="211ed-107">Protokol sınıfları tarafından açığa çıkarılan **Soket** sınıfının özelliklerine erişmek için **Soket** sınıfını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="211ed-107">To access features of the **Socket** class not exposed by the protocol classes, you must use the **Socket** class.</span></span>  
  
 <span data-ttu-id="211ed-108">**TcpClient** ve **TcpListener,** **NetworkStream** sınıfını kullanarak ağı temsil ediyor.</span><span class="sxs-lookup"><span data-stu-id="211ed-108">**TcpClient** and **TcpListener** represent the network using the **NetworkStream** class.</span></span> <span data-ttu-id="211ed-109">Ağ akışını <xref:System.Net.Sockets.TcpClient.GetStream%2A> döndürmek için yöntemi kullanırsınız ve ardından <xref:System.Net.Sockets.NetworkStream.Read%2A> akışı <xref:System.Net.Sockets.NetworkStream.Write%2A> ve yöntemleri çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="211ed-109">You use the <xref:System.Net.Sockets.TcpClient.GetStream%2A> method to return the network stream, and then call the stream's <xref:System.Net.Sockets.NetworkStream.Read%2A> and <xref:System.Net.Sockets.NetworkStream.Write%2A> methods.</span></span> <span data-ttu-id="211ed-110">**NetworkStream** protokol sınıfları'nın temel soketinin sahibi değildir, bu nedenle kapatmak soketi etkilemez.</span><span class="sxs-lookup"><span data-stu-id="211ed-110">The **NetworkStream** does not own the protocol classes' underlying socket, so closing it does not affect the socket.</span></span>  
  
 <span data-ttu-id="211ed-111">**UdpClient** sınıfı, UDP veri gramını tutmak için bir dizi bayt kullanır.</span><span class="sxs-lookup"><span data-stu-id="211ed-111">The **UdpClient** class uses an array of bytes to hold the UDP datagram.</span></span> <span data-ttu-id="211ed-112">Verileri ağa <xref:System.Net.Sockets.UdpClient.Send%2A> göndermek için <xref:System.Net.Sockets.UdpClient.Receive%2A> yöntemi ve gelen bir datagram almak için yöntemi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="211ed-112">You use the <xref:System.Net.Sockets.UdpClient.Send%2A> method to send the data to the network and the <xref:System.Net.Sockets.UdpClient.Receive%2A> method to receive an incoming datagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="211ed-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="211ed-113">See also</span></span>

- [<span data-ttu-id="211ed-114">TCP Hizmetleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="211ed-114">Using TCP Services</span></span>](using-tcp-services.md)
- [<span data-ttu-id="211ed-115">UDP Hizmetleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="211ed-115">Using UDP Services</span></span>](using-udp-services.md)
- [<span data-ttu-id="211ed-116">Ağda Akışları Kullanma</span><span class="sxs-lookup"><span data-stu-id="211ed-116">Using Streams on the Network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="211ed-117">Zaman Uyumsuz Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="211ed-117">Using an Asynchronous Server Socket</span></span>](using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="211ed-118">Zaman Uyumsuz İstemci Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="211ed-118">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="211ed-119">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="211ed-119">Using Application Protocols</span></span>](using-application-protocols.md)
