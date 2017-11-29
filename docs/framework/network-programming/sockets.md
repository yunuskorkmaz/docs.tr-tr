---
title: Yuva
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: de5778e398a9a7205e99cc810d0b672ac247da08
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="sockets"></a>Yuva
<xref:System.Net.Sockets> Ad alanı, yönetilen bir uygulama Windows Sockets arabirimi içerir. Tüm diğer ağ erişim sınıfları <xref:System.Net> ad alanı, bu yuva uygulama üstünde yerleşiktir.  
  
 .NET Framework <xref:System.Net.Sockets.Socket> Winsock32 API'si tarafından sağlanan yuva services yönetilen kod sürümü bir sınıftır. Çoğu durumda, **yuva** yöntemleri yalnızca sınıf yerel Win32 dekiler verileri sıralama ve tüm gerekli güvenlik denetimlerini tanıtıcı.  
  
 **Yuva** sınıfı, zaman uyumlu ve zaman uyumsuz olmak üzere iki temel modunu destekler. Ağ işlemlerini gerçekleştirme işlevleri için zaman uyumlu modda çağıran (gibi <xref:System.Net.Sockets.Socket.Send%2A> ve <xref:System.Net.Sockets.Socket.Receive%2A>) denetimi çağıran program döndürmeden önce işlemi tamamlanana dek bekleyin. Zaman uyumsuz modda çağrıları, hemen döndürülür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: bir yuva oluşturun](../../../docs/framework/network-programming/how-to-create-a-socket.md)  
    
 [Uygulama protokolleri kullanma](../../../docs/framework/network-programming/using-application-protocols.md)
