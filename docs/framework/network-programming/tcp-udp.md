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
ms.openlocfilehash: e074a487c39dfaf1c4704f9dadf7ed8e430fb630
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172555"
---
# <a name="tcp-udp"></a><span data-ttu-id="e0028-102">TCP-UDP</span><span class="sxs-lookup"><span data-stu-id="e0028-102">TCP-UDP</span></span>
<span data-ttu-id="e0028-103">Uygulamalar, İletim Denetimi Protokolü (TCP) ve kullanıcı veri birimi Protokolü (UDP) Hizmetleri ile kullanabileceğiniz <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, ve <xref:System.Net.Sockets.UdpClient> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="e0028-103">Applications can use Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) services with the <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes.</span></span> <span data-ttu-id="e0028-104">Bu protokol sınıfların üstünde oluşturulan <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> sınıfı ve veri aktarımı işlemlerinin ayrıntılarını ele ilgileniriz.</span><span class="sxs-lookup"><span data-stu-id="e0028-104">These protocol classes are built on top of the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class and take care of the details of transferring data.</span></span>  
  
 <span data-ttu-id="e0028-105">Zaman uyumlu yöntemlerini Protokolü sınıfları kullanması **yuva** sade ve durum bilgilerini korumak veya ayarlamaya ilişkin ayrıntılar bilerek ek yükü olmadan ağ hizmetlerine erişim sağlamak için sınıfı protokole özgü yuva.</span><span class="sxs-lookup"><span data-stu-id="e0028-105">The protocol classes use the synchronous methods of the **Socket** class to provide simple and straightforward access to network services without the overhead of maintaining state information or knowing the details of setting up protocol-specific sockets.</span></span> <span data-ttu-id="e0028-106">Zaman uyumsuz kullanılacak **yuva** yöntemleri tarafından sağlanan zaman uyumsuz yöntemler kullanabilir <xref:System.Net.Sockets.NetworkStream> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e0028-106">To use asynchronous **Socket** methods, you can use the asynchronous methods supplied by the <xref:System.Net.Sockets.NetworkStream> class.</span></span> <span data-ttu-id="e0028-107">Erişim özelliklerine **yuva** sınıf Protokolü sınıfları tarafından sunulmadığından kullanmalısınız **yuva** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e0028-107">To access features of the **Socket** class not exposed by the protocol classes, you must use the **Socket** class.</span></span>  
  
 <span data-ttu-id="e0028-108">**TcpClient** ve **TcpListener** kullanarak ağ temsil **NetworkStream** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e0028-108">**TcpClient** and **TcpListener** represent the network using the **NetworkStream** class.</span></span> <span data-ttu-id="e0028-109">Kullandığınız <xref:System.Net.Sockets.TcpClient.GetStream%2A> ağ akışı dönün ve ardından akışın çağırmak için yöntem <xref:System.Net.Sockets.NetworkStream.Read%2A> ve <xref:System.Net.Sockets.NetworkStream.Write%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="e0028-109">You use the <xref:System.Net.Sockets.TcpClient.GetStream%2A> method to return the network stream, and then call the stream's <xref:System.Net.Sockets.NetworkStream.Read%2A> and <xref:System.Net.Sockets.NetworkStream.Write%2A> methods.</span></span> <span data-ttu-id="e0028-110">**NetworkStream** yuva kapatma etkilemez şekilde Protokolü sınıfların temel alınan yuva sahibi değildir.</span><span class="sxs-lookup"><span data-stu-id="e0028-110">The **NetworkStream** does not own the protocol classes' underlying socket, so closing it does not affect the socket.</span></span>  
  
 <span data-ttu-id="e0028-111">**UdpClient** sınıfı UDP veri birimi tutmak için bayt dizisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e0028-111">The **UdpClient** class uses an array of bytes to hold the UDP datagram.</span></span> <span data-ttu-id="e0028-112">Kullandığınız <xref:System.Net.Sockets.UdpClient.Send%2A> yöntemi ağa veri göndermek ve <xref:System.Net.Sockets.UdpClient.Receive%2A> gelen bir veri birimi almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e0028-112">You use the <xref:System.Net.Sockets.UdpClient.Send%2A> method to send the data to the network and the <xref:System.Net.Sockets.UdpClient.Receive%2A> method to receive an incoming datagram.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0028-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0028-113">See also</span></span>

- [<span data-ttu-id="e0028-114">TCP Hizmetleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="e0028-114">Using TCP Services</span></span>](../../../docs/framework/network-programming/using-tcp-services.md)
- [<span data-ttu-id="e0028-115">UDP Hizmetleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="e0028-115">Using UDP Services</span></span>](../../../docs/framework/network-programming/using-udp-services.md)
- [<span data-ttu-id="e0028-116">Ağda Akışları Kullanma</span><span class="sxs-lookup"><span data-stu-id="e0028-116">Using Streams on the Network</span></span>](../../../docs/framework/network-programming/using-streams-on-the-network.md)
- [<span data-ttu-id="e0028-117">Zaman Uyumsuz Sunucu Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="e0028-117">Using an Asynchronous Server Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)
- [<span data-ttu-id="e0028-118">Zaman Uyumsuz İstemci Yuvası Kullanma</span><span class="sxs-lookup"><span data-stu-id="e0028-118">Using an Asynchronous Client Socket</span></span>](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="e0028-119">Uygulama Protokolleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="e0028-119">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
