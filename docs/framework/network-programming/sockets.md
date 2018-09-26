---
title: Yuva
ms.date: 03/30/2017
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- Windows Sockets
- sockets, about sockets
- Socket class, about Socket class
- sockets
- requesting data from Internet, sockets
- network, sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 10d22735-bd37-42c1-a2be-c1932f979a7d
author: mcleblanc
ms.author: markl
ms.openlocfilehash: ce7ded81ad23c2df55afa9360435e8391fea7a63
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47176831"
---
# <a name="sockets"></a>Yuva
<xref:System.Net.Sockets> Ad alanı, Windows yuva arabiriminin yönetilen bir uygulamasını içerir. Yer alan tüm diğer ağ erişim sınıfları <xref:System.Net> ad alanı, bu yuva uygulaması üzerinde oluşturulur.  
  
 .NET Framework <xref:System.Net.Sockets.Socket> sınıftır Winsock32 API'sı tarafından sağlanan yuva services yönetilen kod sürümü. Çoğu durumda **yuva** yöntemleri yalnızca sınıf yerel Win32 karşılıkları veri hazırlamak ve tüm gerekli güvenlik denetimlerini işleyecek.  
  
 **Yuva** sınıfı, zaman uyumlu ve zaman uyumsuz olmak üzere iki temel modlarını destekler. Zaman uyumlu modda ağ işlemleri gerçekleştirmek için işlevleri çağırır (gibi <xref:System.Net.Sockets.Socket.Send%2A> ve <xref:System.Net.Sockets.Socket.Receive%2A>) denetimi çağırma program döndürmeden önce işlemi tamamlanana kadar bekleyin. Zaman uyumsuz modda bu çağrılar hemen döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl Yapılır: Yuva Oluşturma](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
    
 [Uygulama Protokolleri Kullanma](../../../docs/framework/network-programming/using-application-protocols.md)
