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
# <a name="tcp-udp"></a>TCP-UDP
Uygulamalar <xref:System.Net.Sockets.TcpClient>,, <xref:System.Net.Sockets.TcpListener>ve <xref:System.Net.Sockets.UdpClient> sınıflarıyla iletim Denetim Protokolü (TCP) ve Kullanıcı Datagram Protokolü (UDP) hizmetlerini kullanabilir. Bu protokol sınıfları <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> sınıfının üzerine kurulmuştur ve veri aktarma ayrıntılarının ayrıntılarını alır.  
  
 Protokol sınıfları, durum bilgilerini koruma veya protokole özgü yuvaları ayarlama ayrıntılarını bilme olmadan ağ hizmetlerine basit ve kolay erişim sağlamak için **yuva** sınıfının zaman uyumlu yöntemlerini kullanır. Zaman uyumsuz **yuva** yöntemlerini kullanmak için, <xref:System.Net.Sockets.NetworkStream> sınıfı tarafından sağlanan zaman uyumsuz yöntemleri kullanabilirsiniz. Protokol sınıfları tarafından gösterilmeyen **yuva** sınıfının özelliklerine erişmek için **yuva** sınıfını kullanmanız gerekir.  
  
 **TcpClient** ve **TcpListener** , **NetworkStream** sınıfını kullanarak ağı temsil eder. Ağ akışını döndürmek <xref:System.Net.Sockets.TcpClient.GetStream%2A> için yöntemini kullanın ve ardından <xref:System.Net.Sockets.NetworkStream.Read%2A> akışın ve <xref:System.Net.Sockets.NetworkStream.Write%2A> yöntemlerini çağırabilirsiniz. **NetworkStream** , temel alınan yuvaya ait protokol sınıflarının sahibi değil, bu nedenle bunu kapatmak yuvayı etkilemez.  
  
 **UdpClient** sınıfı, UDP veri birimini tutmak için bir bayt dizisi kullanır. Verileri ağa göndermek <xref:System.Net.Sockets.UdpClient.Send%2A> için yöntemini <xref:System.Net.Sockets.UdpClient.Receive%2A> ve gelen bir veri birimini alma yöntemini kullanırsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TCP Hizmetleri Kullanma](using-tcp-services.md)
- [UDP Hizmetleri Kullanma](using-udp-services.md)
- [Ağda Akışları Kullanma](using-streams-on-the-network.md)
- [Zaman Uyumsuz Sunucu Yuvası Kullanma](using-an-asynchronous-server-socket.md)
- [Zaman Uyumsuz İstemci Yuvası Kullanma](using-an-asynchronous-client-socket.md)
- [Uygulama Protokolleri Kullanma](using-application-protocols.md)
