---
title: Zaman Uyumlu İstemci Yuvası Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- synchronous client sockets
- Socket class, synchronous client sockets
- receiving data, sockets
- sockets, synchronous client sockets
- protocols, sockets
- Internet, sockets
- client sockets
ms.assetid: 945d00c6-7202-466c-9df9-140b84156d43
ms.openlocfilehash: fdecd18dc5975cd469e49de0eb0b55081e738cd8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047068"
---
# <a name="using-a-synchronous-client-socket"></a>Zaman Uyumlu İstemci Yuvası Kullanma
Ağ işlemi tamamlanırken, zaman uyumlu bir istemci yuvası uygulama programını askıya alır. Zaman uyumlu yuvalar, ağ işlemleri için yoğun olarak kullanılan uygulamalar için uygun değildir, ancak diğer uygulamalar için ağ hizmetlerine basit erişimi etkinleştirebilir.  
  
 Veri göndermek için, <xref:System.Net.Sockets.Socket> sınıfın Send-Data yöntemlerinden birine bir bayt dizisi geçirin (<xref:System.Net.Sockets.Socket.Send%2A> ve <xref:System.Net.Sockets.Socket.SendTo%2A>). Aşağıdaki örnek, <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> özelliğini kullanarak bir dizeyi bir bayt dizisi arabelleğine kodluyor ve sonra **Send** metodunu kullanarak arabelleği ağ cihazına iletir. **Send** yöntemi, ağ cihazına gönderilen bayt sayısını döndürür.  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 **Send** yöntemi arabellekteki baytları kaldırır ve ağ cihazına gönderilmek üzere ağ arabirimiyle sıralar. Ağ arabirimi, verileri hemen gönderemeyebilir, ancak bağlantı, normal şekilde <xref:System.Net.Sockets.Socket.Shutdown%2A> yöntemle kapandığı sürece, bu işlemi sonunda gönderir.  
  
 Bir ağ aygıtından veri almak için, **yuva** sınıfının Receive-Data yöntemlerinden birine bir arabellek geçirin (<xref:System.Net.Sockets.Socket.Receive%2A> ve <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>). Zaman uyumlu yuvalar, ağdan bayt alınana veya yuva kapatılıncaya kadar uygulamayı askıya alır. Aşağıdaki örnek, ağdan verileri alır ve sonra konsolunda görüntüler. Örnek, ağdan gelen verilerin ASCII kodlamalı metin olduğunu varsayar. **Receive** yöntemi ağdan alınan bayt sayısını döndürür.  
  
```vb  
Dim bytes(1024) As Byte  
Dim bytesRec = s.Receive(bytes)  
Console.WriteLine("Echoed text = {0}", _  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec))  
```  
  
```csharp  
byte[] bytes = new byte[1024];  
int bytesRec = s.Receive(bytes);  
Console.WriteLine("Echoed text = {0}",  
    System.Text.Encoding.ASCII.GetString(bytes, 0, bytesRec));  
```  
  
 Yuva artık gerekli olmadığında, <xref:System.Net.Sockets.Socket.Shutdown%2A> yöntemini çağırarak ve sonra **Close** metodunu çağırarak onu serbest bırakmanız gerekir. Aşağıdaki örnek bir **yuva**yayınlar. <xref:System.Net.Sockets.SocketShutdown> Sabit listesi, yuvanın gönderme, alma için veya her ikisi için de kapatılıp kapatılmayacağını belirten sabitleri tanımlar.  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Zaman Uyumsuz İstemci Yuvası Kullanma](using-an-asynchronous-client-socket.md)
- [Yuvalarla Dinleme](listening-with-sockets.md)
- [Zaman Uyumlu İstemci Yuvası Örneği](synchronous-client-socket-example.md)
