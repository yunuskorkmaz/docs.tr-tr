---
title: "Zaman uyumlu istemci yuvası kullanma"
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
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 03595539d825f26251a24fce33ede2552b79b38b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-a-synchronous-client-socket"></a>Zaman uyumlu istemci yuvası kullanma
Ağ işlemi tamamlanırken bir zaman uyumlu istemci yuva uygulama programı askıya alır. Zaman uyumlu yuva ağ yoğun olarak kullanılır, işlem için uygulamalar için uygun değildir, ancak basit ağ hizmetlerine erişim için diğer uygulamalar için etkinleştirebilirsiniz.  
  
 Veri göndermek için bir bayt dizisi birine geçirmek <xref:System.Net.Sockets.Socket> sınıfının gönderme veri yöntemleri (<xref:System.Net.Sockets.Socket.Send%2A> ve <xref:System.Net.Sockets.Socket.SendTo%2A>). Aşağıdaki örnekte bir dizeyi bir bayt dizisi kullanarak arabellek kodlar <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType> özelliği ve kullanarak ağ aygıtı için arabellek iletir **Gönder** yöntemi. **Gönder** yöntemi ağ cihazına gönderilen bayt sayısını döndürür.  
  
```vb  
Dim msg As Byte() = _  
    System.Text.Encoding.ASCII.GetBytes("This is a test.")  
Dim bytesSent As Integer = s.Send(msg)  
```  
  
```csharp  
byte[] msg = System.Text.Encoding.ASCII.GetBytes("This is a test");  
int bytesSent = s.Send(msg);  
```  
  
 **Gönder** yöntemi arabellekteki bayt kaldırır ve bunları ağ cihazına gönderilmek üzere ağ arabirimine sahip sıralar. Ağ arabirimi verileri hemen göndermek, ancak bağlantı normalde ile kapalı olduğu sürece, sonuç olarak, göndereceğiniz <xref:System.Net.Sockets.Socket.Shutdown%2A> yöntemi.  
  
 Bir ağ aygıtından veri almak için bir arabellek birine geçirmek **yuva** sınıfının aldığınız verilerinin yöntemleri (<xref:System.Net.Sockets.Socket.Receive%2A> ve <xref:System.Net.Sockets.Socket.ReceiveFrom%2A>). Bayt ağdan veya yuva kapatılana kadar alınana kadar zaman uyumlu yuva uygulama askıya alınır. Aşağıdaki örnek veri ağdan alır ve konsolda görüntülenir. Örneğin, ağdan gelen veriler ASCII kodlanmış metin olduğunu varsayar. **Alma** yöntemi ağdan alınan bayt sayısını döndürür.  
  
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
  
 Yuva artık gerekli olmadığında çağırarak serbest bırakmanız <xref:System.Net.Sockets.Socket.Shutdown%2A> yöntemi ve ardından çağırma **Kapat** yöntemi. Aşağıdaki örnek serbest bir **yuva**. <xref:System.Net.Sockets.SocketShutdown> Numaralandırma yuva gönderme, alma veya her ikisi için de kapatılıp kapatılmayacağını belirtmek sabitleri tanımlar.  
  
```vb  
s.Shutdown(SocketShutdown.Both)  
s.Close()  
```  
  
```csharp  
s.Shutdown(SocketShutdown.Both);  
s.Close();  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Zaman Uyumsuz İstemci Yuvası Kullanma](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [Yuvalarla Dinleme](../../../docs/framework/network-programming/listening-with-sockets.md)  
 [Zaman Uyumlu İstemci Yuvası Örneği](../../../docs/framework/network-programming/synchronous-client-socket-example.md)
