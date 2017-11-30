---
title: TCP UDP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 04a3bb1c7499a60175aaaa9715e780ea5ddceb31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="tcp-udp"></a>TCP UDP
Uygulamalar, İletim Denetimi Protokolü (TCP) ve kullanıcı veri birimi Protokolü (UDP) Hizmetleri ile kullanabileceğiniz <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, ve <xref:System.Net.Sockets.UdpClient> sınıfları. Bu protocol sınıflar üstünde oluşturulan <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> sınıf ve veri aktarma ayrıntılarını dikkatli olun.  
  
 Zaman uyumlu yöntemleri Protokolü sınıfları kullanan **yuva** durumu bilgilerini yönetmek veya ayarlama ayrıntılarını bilmek yükü olmadan Ağ Hizmetleri basit ve kolay erişim sağlamak için sınıfı protokole özgü yuva. Zaman uyumsuz kullanılacak **yuva** yöntemleri tarafından sağlanan zaman uyumsuz yöntemleri kullanabilir <xref:System.Net.Sockets.NetworkStream> sınıfı. Erişim özelliklerine **yuva** Protokolü sınıfları tarafından gösterilmeyen sınıfı kullanmalısınız **yuva** sınıfı.  
  
 **TcpClient** ve **TcpListener** kullanarak ağ temsil **NetworkStream** sınıfı. Kullandığınız <xref:System.Net.Sockets.TcpClient.GetStream%2A> ağ akışı dönüp akışın çağırmak için yöntemi <xref:System.Net.Sockets.NetworkStream.Read%2A> ve <xref:System.Net.Sockets.NetworkStream.Write%2A> yöntemleri. **NetworkStream** kapatma yuva etkilemesini protocol sınıflar temel yuva, kendisine ait değil.  
  
 **UdpClient** sınıfı UDP veri birimi tutacak bir bayt dizisi kullanır. Kullandığınız <xref:System.Net.Sockets.UdpClient.Send%2A> ağa veri göndermek için yöntem ve <xref:System.Net.Sockets.UdpClient.Receive%2A> gelen bir veri biriminde almaya yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TCP Hizmetleri kullanma](../../../docs/framework/network-programming/using-tcp-services.md)  
 [UDP Hizmetleri kullanma](../../../docs/framework/network-programming/using-udp-services.md)  
 [Ağda akışlarını kullanma](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [Zaman uyumsuz Server yuva kullanma](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [Zaman uyumsuz istemci yuvası kullanma](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [Uygulama protokolleri kullanma](../../../docs/framework/network-programming/using-application-protocols.md)
