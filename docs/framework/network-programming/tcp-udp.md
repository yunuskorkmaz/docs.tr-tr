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
ms.openlocfilehash: ae6d2f9ced2235aa1b9b8fada8064d7e4be970a0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502099"
---
# <a name="tcp-udp"></a>TCP-UDP
Uygulamalar <xref:System.Net.Sockets.TcpClient> ,, ve sınıflarıyla Iletim Denetim Protokolü (TCP) ve Kullanıcı Datagram Protokolü (UDP) hizmetlerini kullanabilir <xref:System.Net.Sockets.TcpListener> <xref:System.Net.Sockets.UdpClient> . Bu protokol sınıfları sınıfının üzerine kurulmuştur <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> ve veri aktarma ayrıntılarının ayrıntılarını alır.  
  
 Protokol sınıfları, durum bilgilerini koruma veya protokole özgü yuvaları ayarlama ayrıntılarını bilme olmadan ağ hizmetlerine basit ve kolay erişim sağlamak için **yuva** sınıfının zaman uyumlu yöntemlerini kullanır. Zaman uyumsuz **yuva** yöntemlerini kullanmak için, sınıfı tarafından sağlanan zaman uyumsuz yöntemleri kullanabilirsiniz <xref:System.Net.Sockets.NetworkStream> . Protokol sınıfları tarafından gösterilmeyen **yuva** sınıfının özelliklerine erişmek için **yuva** sınıfını kullanmanız gerekir.  
  
 **TcpClient** ve **TcpListener** , **NetworkStream** sınıfını kullanarak ağı temsil eder. <xref:System.Net.Sockets.TcpClient.GetStream%2A>Ağ akışını döndürmek için yöntemini kullanın ve ardından akışın <xref:System.Net.Sockets.NetworkStream.Read%2A> ve <xref:System.Net.Sockets.NetworkStream.Write%2A> yöntemlerini çağırabilirsiniz. **NetworkStream** , temel alınan yuvaya ait protokol sınıflarının sahibi değil, bu nedenle bunu kapatmak yuvayı etkilemez.  
  
 **UdpClient** sınıfı, UDP veri birimini tutmak için bir bayt dizisi kullanır. <xref:System.Net.Sockets.UdpClient.Send%2A>Verileri ağa göndermek için yöntemini ve <xref:System.Net.Sockets.UdpClient.Receive%2A> gelen bir veri birimini alma yöntemini kullanırsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TCP Hizmetleri Kullanma](using-tcp-services.md)
- [UDP Hizmetleri Kullanma](using-udp-services.md)
- [Ağda Akışları Kullanma](using-streams-on-the-network.md)
- [Zaman Uyumsuz Sunucu Yuvası Kullanma](using-an-asynchronous-server-socket.md)
- [Zaman Uyumsuz İstemci Yuvası Kullanma](using-an-asynchronous-client-socket.md)
- [Uygulama Protokolleri Kullanma](using-application-protocols.md)
