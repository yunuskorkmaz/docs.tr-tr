---
title: Ağda akışları kullanma
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1157fd8772546a1e34343bcf05ac40ca8ad592a5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47080987"
---
# <a name="using-streams-on-the-network"></a>Ağda akışları kullanma
Ağ kaynaklarını .NET Framework akışları olarak temsil edilir. .NET Framework akışları genel düşünerek, aşağıdaki özellikleri sunar:  
  
-   Web veri göndermek ve almak için yaygın bir yolu. Hangi gerçek dosyasının içeriğini — HTML, XML veya başka bir şey — uygulamanızın kullanacağı <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> ve <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> veri göndermek ve almak için.  
  
-   Arasında .NET Framework akışları ile uyumluluk. Akışları bunları işlemesi için zengin bir altyapı olan .NET Framework boyunca kullanılır. XML verileri okuyan bir uygulama gibi değiştirebileceğiniz bir <xref:System.IO.FileStream> verileri okumak için bir <xref:System.Net.Sockets.NetworkStream> bunun yerine, akışı başlatmak yalnızca birkaç satır kod ile değiştirme. Arasındaki temel farklar **NetworkStream** sınıfı ve diğer akışlar olduğundan, **NetworkStream** aranabilir, değil <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> özelliği her zaman döndürür **false**ve <xref:System.Net.Sockets.NetworkStream.Seek%2A> ve <xref:System.Net.Sockets.NetworkStream.Position%2A> yöntemleri throw bir <xref:System.NotSupportedException>.  
  
-   Verilerin işlenmesini ulaşır. Uygulamanızı bir bütün indirilmesi için veri kümesi beklenecek zorlamak yerine ağ ulaştıkça akışları verilere erişim sağlar.  
  
 <xref:System.Net.Sockets> Ad alanı içeren bir **NetworkStream** uygulayan sınıf <xref:System.IO.Stream> ağ kaynakları ile kullanılmak üzere özel olarak sınıf. Sınıflar <xref:System.Net.Sockets> ad **NetworkStream** akışları temsil eden sınıf.  
  
 Döndürülen akışa kullanarak ağa veri göndermek için arama <xref:System.Net.WebRequest.GetRequestStream%2A> üzerinde <xref:System.Net.WebRequest>. **WebRequest** sunucuya; istek üst bilgilerini gönderir, ardından çağırarak ağ kaynağına veri gönderebilir <xref:System.IO.Stream.BeginWrite%2A>, <xref:System.IO.Stream.EndWrite%2A>, veya <xref:System.IO.Stream.Write%2A> döndürülen akışa yöntemi. HTTP gibi bazı protokoller, verileri göndermeden önce protokole özgü özelliklerini ayarlamak gerektirebilir. Aşağıdaki kod örneği, veri göndermek için HTTP özel özelliklerin nasıl ayarlanacağını gösterir. Olduğunu varsayar değişkeni `sendData` gönderilecek verileri içeren değişken `sendLength` gönderilecek verileri baytlık sayısıdır.  
  
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
  
 Ağ üzerinden veri almak için çağrı <xref:System.Net.WebResponse.GetResponseStream%2A> üzerinde <xref:System.Net.WebResponse>. Çağırarak verileri ağ kaynak ardından okuyabilir <xref:System.IO.Stream.BeginRead%2A>, <xref:System.IO.Stream.EndRead%2A>, veya <xref:System.IO.Stream.Read%2A> döndürülen akışa yöntemi.  
  
 Ağ kaynaklarını akışlardan kullanırken aşağıdaki noktaları göz önünde bulundurun:  
  
-   **CanSeek** özelliği her zaman döndürür **false** beri **NetworkStream** sınıfı, akışta konumu değiştirilemez. **Arama** ve **konumu** yöntemleri throw bir **NotSupportedException**.  
  
-   Kullanırken **WebRequest** ve **WebResponse**, akış çağrılarak oluşturulan örnekleri **GetResponseStream** salt okunurdur ve bunların akışını çağrılarakoluşturulanörnekleri **GetRequestStream** salt yazılır.  
  
-   Kullanım <xref:System.IO.StreamReader> kodlama daha kolay hale getirmek için sınıf. Aşağıdaki kod örneğinde bir **StreamReader** ASCII kodlamalı bir akıştan okumak için bir **WebResponse** (örneğin isteği oluşturma göstermez).  
  
-   Çağrı **GetResponse yanıtına** ağ kaynaklarını kullanılabilir durumda değilse, engelleyebilirsiniz. Zaman uyumsuz bir istekle kullanmayı düşünmeniz gerekir <xref:System.Net.WebRequest.BeginGetResponse%2A> ve <xref:System.Net.WebRequest.EndGetResponse%2A> yöntemleri.  
  
-   Çağrı **GetRequestStream** sunucusuyla bağlantı oluşturulurken engelleyebilirsiniz. Sahip akış için bir zaman uyumsuz istek kullanmayı düşünmeniz gerekir <xref:System.Net.WebRequest.BeginGetRequestStream%2A> ve <xref:System.Net.WebRequest.EndGetRequestStream%2A> yöntemleri.  
  
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
 [Nasıl yapılır: WebRequest Sınıfını Kullanarak Veri İsteme](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)  
 [Veri İsteme](../../../docs/framework/network-programming/requesting-data.md)
