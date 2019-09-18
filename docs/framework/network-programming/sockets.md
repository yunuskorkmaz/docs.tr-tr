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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047253"
---
# <a name="sockets"></a>Yuvalar
Ad <xref:System.Net.Sockets> alanı, Windows Sockets arabiriminin yönetilen bir uygulamasını içerir. Ad alanındaki diğer tüm ağ erişim sınıfları, <xref:System.Net> bu yuvalar uygulamasının üzerine kurulmuştur.  
  
 .NET Framework <xref:System.Net.Sockets.Socket> sınıfı, WinSock32 API 'si tarafından belirtilen yuva hizmetlerinin yönetilen kod sürümüdür. Çoğu durumda, **Socket** sınıfı yöntemleri yalnızca yerel Win32 karşılıklarına veri sıralamalarını ve gerekli güvenlik denetimlerini işlemelerini sağlamaktır.  
  
 **Yuva** sınıfı iki temel modu destekler, zaman uyumlu ve zaman uyumsuz. Zaman uyumlu modda, ağ işlemleri gerçekleştiren işlevlere yapılan çağrılar ( <xref:System.Net.Sockets.Socket.Send%2A> ve <xref:System.Net.Sockets.Socket.Receive%2A>gibi), çağıran programa denetim döndürmeden önce işlem tamamlanana kadar bekler. Zaman uyumsuz modda bu çağrılar hemen döndürülür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Yuva oluşturma](how-to-create-a-socket.md)

- [Uygulama Protokolleri Kullanma](using-application-protocols.md)
