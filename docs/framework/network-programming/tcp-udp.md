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
# <a name="tcp-udp"></a>TCP-UDP
Uygulamalar, İletim Kontrol Protokolü (TCP) ve Kullanıcı Datagram Protokolü <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.TcpListener>(UDP) hizmetlerini , ve <xref:System.Net.Sockets.UdpClient> sınıflarla kullanabilir. Bu protokol sınıfları <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> sınıfın en üstünde inşa edilir ve veri aktarım ayrıntılarıdikkat çekmek.  
  
 Protokol sınıfları, durum bilgilerini koruma veya protokole özgü soketleri ayarlama ayrıntılarını bilme den ek yükü olmadan ağ hizmetlerine basit ve basit erişim sağlamak için **Soket** sınıfının eşzamanlı yöntemlerini kullanır. Eşzamanlı **Soket** yöntemlerini kullanmak <xref:System.Net.Sockets.NetworkStream> için, sınıf tarafından sağlanan eşzamanlı yöntemleri kullanabilirsiniz. Protokol sınıfları tarafından açığa çıkarılan **Soket** sınıfının özelliklerine erişmek için **Soket** sınıfını kullanmanız gerekir.  
  
 **TcpClient** ve **TcpListener,** **NetworkStream** sınıfını kullanarak ağı temsil ediyor. Ağ akışını <xref:System.Net.Sockets.TcpClient.GetStream%2A> döndürmek için yöntemi kullanırsınız ve ardından <xref:System.Net.Sockets.NetworkStream.Read%2A> akışı <xref:System.Net.Sockets.NetworkStream.Write%2A> ve yöntemleri çağırırsınız. **NetworkStream** protokol sınıfları'nın temel soketinin sahibi değildir, bu nedenle kapatmak soketi etkilemez.  
  
 **UdpClient** sınıfı, UDP veri gramını tutmak için bir dizi bayt kullanır. Verileri ağa <xref:System.Net.Sockets.UdpClient.Send%2A> göndermek için <xref:System.Net.Sockets.UdpClient.Receive%2A> yöntemi ve gelen bir datagram almak için yöntemi kullanırsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TCP Hizmetleri Kullanma](using-tcp-services.md)
- [UDP Hizmetleri Kullanma](using-udp-services.md)
- [Ağda Akışları Kullanma](using-streams-on-the-network.md)
- [Zaman Uyumsuz Sunucu Yuvası Kullanma](using-an-asynchronous-server-socket.md)
- [Zaman Uyumsuz İstemci Yuvası Kullanma](using-an-asynchronous-client-socket.md)
- [Uygulama Protokolleri Kullanma](using-application-protocols.md)
