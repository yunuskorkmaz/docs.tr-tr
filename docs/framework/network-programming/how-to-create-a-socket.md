---
title: 'Nasıl Yapılır: Yuva Oluşturma'
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
ms.openlocfilehash: e71e7e235048361580c65bdb551919fe3038130b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180832"
---
# <a name="how-to-create-a-socket"></a>Nasıl Yapılır: Yuva Oluşturma
Uzak aygıtlarla iletişim kurmak için bir soket kullanabilmek için önce, soketin protokol ve ağ adresi bilgileriyle başlatılması gerekir. Sınıfın oluşturucusu, yuvanın <xref:System.Net.Sockets.Socket> bağlantı yapmak için kullandığı adres ailesini, yuva türünü ve protokol türünü belirten parametrelere sahiptir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Internet gibi TCP/IP tabanlı bir ağda iletişim kurmak için kullanılabilecek bir Soket oluşturur.  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 TCP yerine UDP kullanmak için, aşağıdaki örnekte olduğu gibi protokol türünü değiştirin:  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 Numaralandırma, <xref:System.Net.Sockets.AddressFamily> **soket** sınıfı tarafından ağ adreslerini çözmek için kullanılan standart adres ailelerini belirtir (örneğin, **AddressFamily.InterNetwork** üyesi IP sürüm 4 adres ailesini belirtir).  
  
 Numaralandırma <xref:System.Net.Sockets.SocketType> soket türünü belirtir (örneğin, **SocketType.Stream** üyesi akış denetimi ile veri göndermek ve almak için standart bir soket gösterir).  
  
 Numaralandırma, <xref:System.Net.Sockets.ProtocolType> **Soket** üzerinde iletişim kurarken kullanılacak ağ protokolünü belirtir (örneğin, **ProtocolType.Tcp** soketin TCP kullandığını gösterir; **ProtocolType.Udp** soketin UDP kullandığını gösterir).  
  
 Bir **Soket** oluşturulduktan sonra, uzak bir uç noktaya bağlantı başlatabilir veya uzak aygıtlardan bağlantı alabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemci Yuvaları Kullanma](using-client-sockets.md)
- [Yuvalarla Dinleme](listening-with-sockets.md)
