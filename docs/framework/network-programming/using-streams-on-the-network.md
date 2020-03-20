---
title: Ağda Akışları Kullanma
ms.date: 03/30/2017
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
ms.openlocfilehash: 7d5a2e3eec9b49731a09f6eb41a8d8500a59b45c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180619"
---
# <a name="using-streams-on-the-network"></a>Ağda Akışları Kullanma
Ağ kaynakları .NET Framework'de akış olarak temsil edilir. Akışları genel olarak işleyerek,.NET Framework aşağıdaki özellikleri sunar:  
  
- Web verilerini göndermenin ve almanın yaygın bir yolu. Dosyanın gerçek içeriği ne olursa olsun - HTML, XML <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> veya <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> başka bir şey - uygulamanızı kullanır ve veri göndermek ve almak için.  
  
- .NET Framework'deki akışlarla uyumluluk. Akışlar, bunları işlemek için zengin bir altyapıya sahip olan .NET Framework boyunca kullanılır. Örneğin, a'dan <xref:System.IO.FileStream> okunacak verilerden <xref:System.Net.Sockets.NetworkStream> XML verilerini okuyan bir uygulamayı, akışı başlatmayı yalnızca birkaç kod satırını değiştirerek değiştirebilirsiniz. **NetworkStream** sınıfı ve diğer akışlar arasındaki en büyük farklar **NetworkStream** <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> aranmaz, özellik <xref:System.Net.Sockets.NetworkStream.Seek%2A> her zaman <xref:System.NotSupportedException> **yanlış**döndürür ve ve <xref:System.Net.Sockets.NetworkStream.Position%2A> yöntemleri atmak bir .  
  
- Verilerin geldiği gibi işlenmesi. Akışlar, uygulamanızı tüm veri kümesinin indirilmesi için beklemeye zorlamak yerine, ağdan gelen verilere erişim sağlar.  
  
 Ad <xref:System.Net.Sockets> alanı, <xref:System.IO.Stream> sınıfı ağ kaynaklarıyla kullanılmak üzere özel olarak uygulayan bir **NetworkStream** sınıfı içerir. Ad alanındaki sınıflar akışları temsil etmek için Ağ Akışı sınıfını kullanır. **NetworkStream** <xref:System.Net.Sockets>  
  
 Döndürülen akışı kullanarak ağa veri göndermek <xref:System.Net.WebRequest.GetRequestStream%2A> için. <xref:System.Net.WebRequest> **WebRequest** sunucuya istek üstbilgilerini gönderir; ardından, döndürülen akıştaki <xref:System.IO.Stream.BeginWrite%2A>" veya <xref:System.IO.Stream.EndWrite%2A> <xref:System.IO.Stream.Write%2A> yöntemi" çağırarak ağ kaynağına veri gönderebilirsiniz. HTTP gibi bazı protokoller, veri göndermeden önce protokole özgü özellikler ayarlamanızı gerektirebilir. Aşağıdaki kod örneği, veri göndermek için HTTP'ye özgü özelliklerin nasıl ayarlanır olduğunu gösterir. Değişkenin `sendData` gönderilecek verileri içerdiğini ve değişkenin `sendLength` gönderilecek bayt veri sayısı olduğunu varsayar.  
  
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
  
 Ağdan veri almak için, <xref:System.Net.WebResponse.GetResponseStream%2A> <xref:System.Net.WebResponse> Daha sonra, döndürülen akıştaki <xref:System.IO.Stream.BeginRead%2A>" <xref:System.IO.Stream.EndRead%2A>veya <xref:System.IO.Stream.Read%2A> yöntemi" çağırarak ağ kaynağındaki verileri okuyabilirsiniz.  
  
 Ağ kaynaklarından gelen akışları kullanırken aşağıdaki noktaları aklınızda bulundurun:  
  
- **Ağ Akışı** sınıfı akıştaki konumu değiştiremediğinden **CanSeek** özelliği her zaman **yanlış** döndürür. **Arama** ve **Konum** yöntemleri **NotSupportedException**atar.  
  
- **WebRequest** ve **WebResponse'u**kullandığınızda, **GetResponseStream'i** arayarak oluşturulan akış örnekleri salt okunur ve **GetRequestStream'i** arayarak oluşturulan akış örnekleri yalnızca yazmadır.  
  
- Kodlamayı <xref:System.IO.StreamReader> kolaylaştırmak için sınıfı kullanın. Aşağıdaki kod örneği, **Bir WebResponse'dan** ASCII kodlanmış bir akışı okumak için bir **StreamReader** kullanır (örnek, isteği oluşturmayı göstermez).  
  
- Ağ kaynakları yoksa **GetResponse** çağrısı engellenebilir. <xref:System.Net.WebRequest.BeginGetResponse%2A> Senvel ve <xref:System.Net.WebRequest.EndGetResponse%2A> yöntemlerle bir asynchronous istek kullanmayı düşünmelisiniz.  
  
- Sunucuya bağlantı oluşturulurken **GetRequestStream'e** çağrı engellenebilir. Akış ve <xref:System.Net.WebRequest.BeginGetRequestStream%2A> <xref:System.Net.WebRequest.EndGetRequestStream%2A> yöntemlerle asenkron bir istek kullanmayı düşünmelisiniz.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: WebRequest Sınıfını Kullanarak Veri İsteme](how-to-request-data-using-the-webrequest-class.md)
- [Veri İsteme](requesting-data.md)
