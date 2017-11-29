---
title: "Ağda akışlarını kullanma"
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
- requesting data from Internet, streams
- Networking
- response to Internet request, streams
- network resources, stream capabilities
- receiving data, stream capabilities
- Network Resources
- sending data, stream capabilities
- downloading Internet resources, streams
- streams, capabilities
- Internet, streams
- streams
ms.assetid: 02b05fba-7235-45ce-94e5-060436ee0875
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f9e011b304a7f6c7d0d07761677c0368efcfcf4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-streams-on-the-network"></a>Ağda akışlarını kullanma
Ağ kaynakları .NET Framework akışları olarak temsil edilir. .NET Framework akışları genel düşünerek, aşağıdaki özellikleri sunar:  
  
-   Web veri göndermek ve almak için genel bir yöntem. Ne olursa olsun gerçek dosyasının içeriğini — HTML, XML veya başka bir şey — uygulamanız kullanacak <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> ve <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> veri göndermek ve almak için.  
  
-   .NET Framework üzerinde akışları ile uyumluluk. Akışlar, bunları işlemek için zengin bir altyapı olan .NET Framework boyunca kullanılır. Örneğin, XML veri okuyan bir uygulama değiştirebilirsiniz bir <xref:System.IO.FileStream> verileri okumak için bir <xref:System.Net.Sockets.NetworkStream> yerine akış başlatmak yalnızca birkaç satır kod değiştirmek. Arasındaki temel farklılıklar **NetworkStream** sınıfı ve diğer akışlar olan, **NetworkStream** aranabilir, değil <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> özelliği her zaman döndürür **yanlış**ve <xref:System.Net.Sockets.NetworkStream.Seek%2A> ve <xref:System.Net.Sockets.NetworkStream.Position%2A> yöntemleri throw bir <xref:System.NotSupportedException>.  
  
-   Verilerinin işlenmesini ulaşır. Bütün bir veri indirilmesi kümesi için beklenecek uygulamanızı zorlama yerine ağ ulaştığında akışları verilere erişim sağlar.  
  
 <xref:System.Net.Sockets> Ad alanı içeren bir **NetworkStream** uygulayan sınıf <xref:System.IO.Stream> ağ kaynakları ile kullanılmak üzere özel olarak sınıfı. Sınıfları <xref:System.Net.Sockets> ad alanı kullanım **NetworkStream** akışları temsil eden sınıf.  
  
 Döndürülen akışa kullanarak ağa veri göndermek için arama <xref:System.Net.WebRequest.GetRequestStream%2A> üzerinde <xref:System.Net.WebRequest>. **WebRequest** istek üstbilgileri sunucuya; gönderir sonra çağırarak ağ kaynağına veri gönderebilir <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, veya <xref:System.IO.Stream.Write%2A> döndürülen akışa yöntemi. HTTP gibi bazı protokoller, veri göndermeden önce protokole özgü özelliklerini ayarlamak gerektirebilir. Aşağıdaki kod örneğinde veri göndermek için HTTP özgü özelliklerin nasıl ayarlanacağını gösterir. Varsayılmaktadır değişkeni `sendData` içeren gönderilecek veriler ve değişken `sendLength` göndermek için veri baytı sayısı.  
  
```csharp  
HttpWebRequest request =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
request.Method = "POST";  
request.ContentLength = sendLength;  
try  
{  
   Stream sendStream = request.GetRequestStream();  
   sendStream.Write(sendData,0,sendLength);  
   sendStream.Close();  
}  
catch  
{  
   // Handle errors . . .  
}  
```  
  
```vb  
Dim request As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
request.Method = "POST"  
request.ContentLength = sendLength  
Try  
   Dim sendStream As Stream = request.GetRequestStream()  
   sendStream.Write(sendData, 0, sendLength)  
   sendStream.Close()  
Catch  
   ' Handle errors . . .  
End Try  
```  
  
 Ağ üzerinden veri almak için arama <xref:System.Net.WebResponse.GetResponseStream%2A> üzerinde <xref:System.Net.WebResponse>. Çağırarak verileri ağ kaynak grubundan sonra okuyabilir <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, veya <xref:System.IO.Stream.Read%2A> döndürülen akışa yöntemi.  
  
 Ağ kaynakları akışlardan kullanırken aşağıdaki noktaları göz önünde bulundurun:  
  
-   **CanSeek** özelliği her zaman döndürür **false** beri **NetworkStream** sınıfı akış konumda değiştiremiyor. **Seek** ve **konumu** yöntemleri throw bir **NotSupportedException**.  
  
-   Kullandığınızda **WebRequest** ve **WebResponse**, akış çağrılarak oluşturulan örnekleri **GetResponseStream** salt okunurdur ve akışını çağrılarakoluşturulanörnekleri **GetRequestStream** salt yazılır.  
  
-   Kullanım <xref:System.IO.StreamReader> daha kolay kodlama yapmak için sınıf. Aşağıdaki kod örneğinde bir **StreamReader** ASCII kodlu bir akıştan okumak için bir **WebResponse** (örneğin isteği oluşturma göstermiyor).  
  
-   Çağrı **GetResponse** ağ kaynaklarına yoksa engelleyebilirsiniz. Zaman uyumsuz isteği ile kullanmayı düşünmelisiniz <xref:System.Net.WebRequest.BeginGetResponse%2A> ve <xref:System.Net.WebRequest.EndGetResponse%2A> yöntemleri.  
  
-   Çağrı **GetRequestStream** sunucuya bağlantı oluşturulurken engelleyebilirsiniz. Zaman uyumsuz isteği olan akış için kullanmayı düşünmelisiniz <xref:System.Net.WebRequest.BeginGetRequestStream%2A> ve <xref:System.Net.WebRequest.EndGetRequestStream%2A> yöntemleri.  
  
```csharp  
// Create a response object.  
WebResponse response = request.GetResponse();  
// Get a readable stream from the server.  
StreamReader sr =   
   new StreamReader(response.GetResponseStream(), Encoding.ASCII);  
// Use the stream. Remember when you are through with the stream to close it.  
sr.Close();  
```  
  
```vb  
' Create a response object.  
Dim response As WebResponse = request.GetResponse()  
' Get a readable stream from the server.  
Dim sr As _   
   New StreamReader(response.GetResponseStream(), Encoding.ASCII)  
' Use the stream. Remember when you are through with the stream to close it.  
sr.Close()  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: İstek WebRequest sınıfı kullanarak verileri](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)  
 [İstekte bulunan verileri](../../../docs/framework/network-programming/requesting-data.md)
