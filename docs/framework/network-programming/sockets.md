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
ms.openlocfilehash: 468d8afc290d8e725deb13ba57dd990181ae4e19
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680500"
---
# <a name="sockets"></a>Yuva
<xref:System.Net.Sockets> Ad alanı, Windows yuva arabiriminin yönetilen bir uygulamasını içerir. Yer alan tüm diğer ağ erişim sınıfları <xref:System.Net> ad alanı, bu yuva uygulaması üzerinde oluşturulur.  
  
 .NET Framework <xref:System.Net.Sockets.Socket> sınıftır Winsock32 API'sı tarafından sağlanan yuva services yönetilen kod sürümü. Çoğu durumda **yuva** yöntemleri yalnızca sınıf yerel Win32 karşılıkları veri hazırlamak ve tüm gerekli güvenlik denetimlerini işleyecek.  
  
 **Yuva** sınıfı, zaman uyumlu ve zaman uyumsuz olmak üzere iki temel modlarını destekler. Zaman uyumlu modda ağ işlemleri gerçekleştirmek için işlevleri çağırır (gibi <xref:System.Net.Sockets.Socket.Send%2A> ve <xref:System.Net.Sockets.Socket.Receive%2A>) denetimi çağırma program döndürmeden önce işlemi tamamlanana kadar bekleyin. Zaman uyumsuz modda bu çağrılar hemen döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Yuva oluşturun](../../../docs/framework/network-programming/how-to-create-a-socket.md)

- [Uygulama Protokolleri Kullanma](../../../docs/framework/network-programming/using-application-protocols.md)
