---
title: "Nasıl yapılır: bir yuva oluşturun"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- Networking
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- Socket class, creating sockets
- Network Resources
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- sockets, creating
ms.assetid: c64a049c-5981-43bc-a2dc-1851473589c7
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 721839e0e27682477f7ba3739d3c666208fae417
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-socket"></a>Nasıl yapılır: bir yuva oluşturun
Uzak aygıtlarıyla iletişim kurmak için bir yuva kullanmadan önce yuva protokolünü ve ağ adresi bilgilerini ile başlatılması gerekir. Oluşturucusu <xref:System.Net.Sockets.Socket> sınıfı Adres ailesi, yuva türü ve yuva bağlantı kurmak için kullandığı protokol türü belirtin parametreleri sahiptir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Internet gibi IP tabanlı bir ağda iletişim kurmak için kullanılan bir yuva oluşturur.  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 UDP yerine TCP kullanmak için aşağıdaki örnekte olduğu gibi protokol türü değiştirin:  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <xref:System.Net.Sockets.AddressFamily> Numaralandırmasını belirtir tarafından kullanılan standart adres ailesi **yuva** ağ adresleri çözümleyecek şekilde sınıfı (örneğin, **AddressFamily.InterNetwork** üye IP belirtir sürüm 4 Adres ailesi).  
  
 <xref:System.Net.Sockets.SocketType> Numaralandırma yuva türünü belirtir (örneğin, **SocketType.Stream** üye akış denetimi ile veri gönderme ve alma için standart bir yuva gösterir).  
  
 <xref:System.Net.Sockets.ProtocolType> Numaralandırmasını belirtir üzerinde iletişim kurarken kullanması için Ağ Protokolü **yuva** (örneğin, **ProtocolType.Tcp** yuva TCP; kullandığını gösterir **ProtocolType.Udp** yuva UDP kullandığını gösterir).  
  
 Sonra bir **yuva** olan oluşturulmuş, uzak uç nokta için bir bağlantı başlatmak veya uzak bağlantıları almasını.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İstemci yuvaları kullanma](../../../docs/framework/network-programming/using-client-sockets.md)  
 [Yuva başına dinleme](../../../docs/framework/network-programming/listening-with-sockets.md)
