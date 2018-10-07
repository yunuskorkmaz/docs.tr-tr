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
ms.openlocfilehash: b3e39b952b37f70513b3a84ce6b6059b85e01c28
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845469"
---
# <a name="tcp-udp"></a>TCP UDP
Uygulamalar, İletim Denetimi Protokolü (TCP) ve kullanıcı veri birimi Protokolü (UDP) Hizmetleri ile kullanabileceğiniz <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, ve <xref:System.Net.Sockets.UdpClient> sınıfları. Bu protokol sınıfların üstünde oluşturulan <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> sınıfı ve veri aktarımı işlemlerinin ayrıntılarını ele ilgileniriz.  
  
 Zaman uyumlu yöntemlerini Protokolü sınıfları kullanması **yuva** sade ve durum bilgilerini korumak veya ayarlamaya ilişkin ayrıntılar bilerek ek yükü olmadan ağ hizmetlerine erişim sağlamak için sınıfı protokole özgü yuva. Zaman uyumsuz kullanılacak **yuva** yöntemleri tarafından sağlanan zaman uyumsuz yöntemler kullanabilir <xref:System.Net.Sockets.NetworkStream> sınıfı. Erişim özelliklerine **yuva** sınıf Protokolü sınıfları tarafından sunulmadığından kullanmalısınız **yuva** sınıfı.  
  
 **TcpClient** ve **TcpListener** kullanarak ağ temsil **NetworkStream** sınıfı. Kullandığınız <xref:System.Net.Sockets.TcpClient.GetStream%2A> ağ akışı dönün ve ardından akışın çağırmak için yöntem <xref:System.Net.Sockets.NetworkStream.Read%2A> ve <xref:System.Net.Sockets.NetworkStream.Write%2A> yöntemleri. **NetworkStream** yuva kapatma etkilemez şekilde Protokolü sınıfların temel alınan yuva sahibi değildir.  
  
 **UdpClient** sınıfı UDP veri birimi tutmak için bayt dizisini kullanır. Kullandığınız <xref:System.Net.Sockets.UdpClient.Send%2A> yöntemi ağa veri göndermek ve <xref:System.Net.Sockets.UdpClient.Receive%2A> gelen bir veri birimi almak için yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TCP Hizmetleri Kullanma](../../../docs/framework/network-programming/using-tcp-services.md)  
 [UDP Hizmetleri Kullanma](../../../docs/framework/network-programming/using-udp-services.md)  
 [Ağda Akışları Kullanma](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [Zaman Uyumsuz Sunucu Yuvası Kullanma](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [Zaman Uyumsuz İstemci Yuvası Kullanma](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [Uygulama Protokolleri Kullanma](../../../docs/framework/network-programming/using-application-protocols.md)
