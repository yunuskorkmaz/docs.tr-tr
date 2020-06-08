---
title: 'Nasıl Yapılır: Yuva Oluşturma'
description: Uzak cihazlarla iletişim kurmak için bir yuva başlatmayı öğrenin. Adres ailesini, yuva türünü ve protokol türünü belirtmek için yuva sınıfını kullanın.
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
ms.openlocfilehash: 1d56ddea721b54192a7dd47d144b6c41bbb9a5d7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502554"
---
# <a name="how-to-create-a-socket"></a>Nasıl Yapılır: Yuva Oluşturma
Uzak cihazlarla iletişim kurmak üzere bir yuva kullanabilmeniz için, yuva protokol ve ağ adresi bilgileriyle başlatılmalıdır. Sınıfına yönelik oluşturucunun, <xref:System.Net.Sockets.Socket> bağlantı kurmak için yuvanın kullandığı adres ailesini, yuva türünü ve protokol türünü belirten parametreleri vardır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Internet gibi TCP/IP tabanlı bir ağda iletişim kurmak için kullanılabilecek bir yuva oluşturur.  
  
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
  
 <xref:System.Net.Sockets.AddressFamily>Sabit listesi, ağ adreslerini çözümlemek Için **yuva** sınıfı tarafından kullanılan standart adres aileleri belirtir (örneğin, **AddressFamily. ıNTERNETWORK** üyesi, IP sürüm 4 adres ailesini belirtir).  
  
 <xref:System.Net.Sockets.SocketType>Numaralandırma, yuva türünü belirtir (örneğin, **SocketType. Stream** üyesi, akış denetimiyle veri gönderme ve alma için standart bir yuva gösterir).  
  
 <xref:System.Net.Sockets.ProtocolType>Sabit listesi, **yuvada** iletişim kurulurken kullanılacak ağ protokolünü belirtir (örneğin, **ProtocolType. TCP** , yuvanın TCP kullandığını gösterir; **ProtocolType. UDP** , yuvanın UDP kullandığını gösterir.  
  
 Bir **yuva** oluşturulduktan sonra, uzak bir uç noktaya bağlantı başlatabilir veya uzak cihazlardan gelen bağlantıları alabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemci Yuvaları Kullanma](using-client-sockets.md)
- [Yuvalarla Dinleme](listening-with-sockets.md)
