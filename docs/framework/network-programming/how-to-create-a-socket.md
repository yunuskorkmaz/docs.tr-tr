---
title: 'Nasıl yapılır: Yuva Oluşturma'
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
ms.openlocfilehash: 54706293784d77e535cac582c99b1dd21a12e380
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048379"
---
# <a name="how-to-create-a-socket"></a>Nasıl yapılır: Yuva Oluşturma
Uzak cihazlarla iletişim kurmak üzere bir yuva kullanabilmeniz için, yuva protokol ve ağ adresi bilgileriyle başlatılmalıdır. <xref:System.Net.Sockets.Socket> Sınıfına yönelik oluşturucunun, bağlantı kurmak için yuvanın kullandığı adres ailesini, yuva türünü ve protokol türünü belirten parametreleri vardır.  
  
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
  
 Sabit listesi, ağ adreslerini çözümlemek için **yuva** sınıfı tarafından kullanılan standart adres aileleri belirtir (örneğin, **AddressFamily. InterNetwork** üyesi, IP sürüm 4 adres ailesini belirtir). <xref:System.Net.Sockets.AddressFamily>  
  
 Numaralandırma, yuva türünü belirtir (örneğin, **SocketType. Stream** üyesi, akış denetimiyle veri gönderme ve alma için standart bir yuva gösterir). <xref:System.Net.Sockets.SocketType>  
  
 Sabit listesi, **yuvada** iletişim kurulurken kullanılacak ağ protokolünü belirtir (örneğin, **ProtocolType. TCP** , yuvanın TCP kullandığını gösterir; <xref:System.Net.Sockets.ProtocolType> **ProtocolType. UDP** , yuvanın UDP kullandığını gösterir.  
  
 Bir **yuva** oluşturulduktan sonra, uzak bir uç noktaya bağlantı başlatabilir veya uzak cihazlardan gelen bağlantıları alabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemci Yuvaları Kullanma](using-client-sockets.md)
- [Yuvalarla Dinleme](listening-with-sockets.md)
