---
title: Yuvalar
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
ms.openlocfilehash: cffad6b4677a880bd63f5ae0232c639f7a262c59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047253"
---
# <a name="sockets"></a>Yuvalar
Ad <xref:System.Net.Sockets> alanı, Windows Soketleri arabiriminin yönetilen bir uygulamasını içerir. <xref:System.Net> Ad alanındaki diğer tüm ağ erişim sınıfları, soketlerin bu uygulamasının üzerine inşa edilmiştir.  
  
 .NET Framework <xref:System.Net.Sockets.Socket> sınıfı, Winsock32 API tarafından sağlanan soket hizmetlerinin yönetilen kodlu bir sürümüdür. Çoğu durumda, **Socket** sınıfı yöntemleri verileri yalnızca yerel Win32 muadillerine göre yönetir ve gerekli güvenlik denetimlerini işler.  
  
 **Soket** sınıfı senkron ve eşzamanlı olmak üzere iki temel modu destekler. Senkron modda, ağ işlemleri gerçekleştiren işlevlere <xref:System.Net.Sockets.Socket.Send%2A> (örneğin ve) <xref:System.Net.Sockets.Socket.Receive%2A>arama programına denetimi döndürmeden önce işlem tamamlanana kadar bekler. Eşzamanlı modda, bu çağrılar hemen geri döner.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Yuva Oluşturma](how-to-create-a-socket.md)

- [Uygulama Protokolleri Kullanma](using-application-protocols.md)
