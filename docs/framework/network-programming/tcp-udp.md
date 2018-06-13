---
title: TCP UDP
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 30630f397d491a6a5f251ddac14a4db90e53b999
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394611"
---
# <a name="tcp-udp"></a>TCP UDP
Uygulamalar, İletim Denetimi Protokolü (TCP) ve kullanıcı veri birimi Protokolü (UDP) Hizmetleri ile kullanabileceğiniz <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, ve <xref:System.Net.Sockets.UdpClient> sınıfları. Bu protocol sınıflar üstünde oluşturulan <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> sınıf ve veri aktarma ayrıntılarını dikkatli olun.  
  
 Zaman uyumlu yöntemleri Protokolü sınıfları kullanan **yuva** durumu bilgilerini yönetmek veya ayarlama ayrıntılarını bilmek yükü olmadan Ağ Hizmetleri basit ve kolay erişim sağlamak için sınıfı protokole özgü yuva. Zaman uyumsuz kullanılacak **yuva** yöntemleri tarafından sağlanan zaman uyumsuz yöntemleri kullanabilir <xref:System.Net.Sockets.NetworkStream> sınıfı. Erişim özelliklerine **yuva** Protokolü sınıfları tarafından gösterilmeyen sınıfı kullanmalısınız **yuva** sınıfı.  
  
 **TcpClient** ve **TcpListener** kullanarak ağ temsil **NetworkStream** sınıfı. Kullandığınız <xref:System.Net.Sockets.TcpClient.GetStream%2A> ağ akışı dönüp akışın çağırmak için yöntemi <xref:System.Net.Sockets.NetworkStream.Read%2A> ve <xref:System.Net.Sockets.NetworkStream.Write%2A> yöntemleri. **NetworkStream** kapatma yuva etkilemesini protocol sınıflar temel yuva, kendisine ait değil.  
  
 **UdpClient** sınıfı UDP veri birimi tutacak bir bayt dizisi kullanır. Kullandığınız <xref:System.Net.Sockets.UdpClient.Send%2A> ağa veri göndermek için yöntem ve <xref:System.Net.Sockets.UdpClient.Receive%2A> gelen bir veri biriminde almaya yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TCP Hizmetleri Kullanma](../../../docs/framework/network-programming/using-tcp-services.md)  
 [UDP Hizmetleri Kullanma](../../../docs/framework/network-programming/using-udp-services.md)  
 [Ağda Akışları Kullanma](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [Zaman Uyumsuz Sunucu Yuvası Kullanma](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [Zaman Uyumsuz İstemci Yuvası Kullanma](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [Uygulama Protokolleri Kullanma](../../../docs/framework/network-programming/using-application-protocols.md)
