---
title: 'Nasıl yapılır: Yuva oluşturma'
ms.date: 03/30/2017
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
ms.openlocfilehash: 2c3bfb6435901ac8154bc801ae2a420b252d5849
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50202269"
---
# <a name="how-to-create-a-socket"></a>Nasıl yapılır: Yuva oluşturma
Yuvanın uzak cihazlarla iletişim kurmak için bir yuva kullanmadan önce protokolü ve ağ adresi bilgilerini başlatılması gerekir. Oluşturucusu <xref:System.Net.Sockets.Socket> sınıfı Adres ailesi, yuva türünü ve yuva bağlantı kurmak için kullandığı protokol türü parametresi vardır.  
  
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
  
 UDP, TCP yerine kullanmak için aşağıdaki örnekte olduğu gibi bir protokol türü değiştirin:  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <xref:System.Net.Sockets.AddressFamily> Numaralandırması tarafından kullanılan standart adres ailesi belirtir **yuva** ağ adreslerini çözümlemeye sınıfı (örneğin, **AddressFamily.InterNetwork** üye IP belirtir sürüm 4 Adres ailesi).  
  
 <xref:System.Net.Sockets.SocketType> Numaralandırma yuva türünü belirtir (örneğin, **SocketType.Stream** üye akış denetimi ile veri gönderme ve alma için standart bir yuva gösterir).  
  
 <xref:System.Net.Sockets.ProtocolType> Numaralandırma üzerinde iletişim kurarken kullanılacak ağ protokolü belirtir **yuva** (örneğin, **ProtocolType.Tcp** yuva TCP; kullandığını gösterir **ProtocolType.Udp** yuva UDP kullandığını gösterir).  
  
 Sonra bir **yuva** olan oluşturulmuş, uzak uç noktası için bir bağlantı başlatmak veya uzak bağlantıları alabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İstemci Yuvaları Kullanma](../../../docs/framework/network-programming/using-client-sockets.md)  
 [Yuvalarla Dinleme](../../../docs/framework/network-programming/listening-with-sockets.md)
