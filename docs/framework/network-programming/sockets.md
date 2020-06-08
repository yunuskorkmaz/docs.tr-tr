---
title: Yuvalar
description: WinSock32 API 'SI tarafından sunulan yuva hizmetlerinin yönetilen kod sürümü olan .NET Framework yuva sınıfı hakkında bilgi edinin.
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
ms.openlocfilehash: b44409a0fafc770625be55881ccef3b57045acef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502138"
---
# <a name="sockets"></a>Yuvalar
<xref:System.Net.Sockets>Ad alanı, Windows Sockets arabiriminin yönetilen bir uygulamasını içerir. Ad alanındaki diğer tüm ağ erişim sınıfları, <xref:System.Net> Bu yuvalar uygulamasının üzerine kurulmuştur.  
  
 .NET Framework <xref:System.Net.Sockets.Socket> sınıfı, WinSock32 API 'si tarafından belirtilen yuva hizmetlerinin yönetilen kod sürümüdür. Çoğu durumda, **Socket** sınıfı yöntemleri yalnızca yerel Win32 karşılıklarına veri sıralamalarını ve gerekli güvenlik denetimlerini işlemelerini sağlamaktır.  
  
 **Yuva** sınıfı iki temel modu destekler, zaman uyumlu ve zaman uyumsuz. Zaman uyumlu modda, ağ işlemleri gerçekleştiren işlevlere yapılan çağrılar ( <xref:System.Net.Sockets.Socket.Send%2A> ve gibi), <xref:System.Net.Sockets.Socket.Receive%2A> çağıran programa denetim döndürmeden önce işlem tamamlanana kadar bekler. Zaman uyumsuz modda bu çağrılar hemen döndürülür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Yuva Oluşturma](how-to-create-a-socket.md)

- [Uygulama Protokolleri Kullanma](using-application-protocols.md)
