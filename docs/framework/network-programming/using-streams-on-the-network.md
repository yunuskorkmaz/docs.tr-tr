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
ms.openlocfilehash: aa3fc56dc461d4fe22e2ff391f3561d8834128d8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046872"
---
# <a name="using-streams-on-the-network"></a>Ağda Akışları Kullanma
Ağ kaynakları .NET Framework akışlar olarak temsil edilir. Akışları genel olarak düşünerek, .NET Framework aşağıdaki özellikleri sunar:  
  
- Web verilerini göndermenin ve almanın yaygın bir yolu. Dosyanın gerçek içerikleri ne olursa olsun — HTML, XML veya başka bir şey — uygulamanız, veri göndermek ve <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> almak <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> için kullanır.  
  
- .NET Framework içindeki akışlarla uyumluluk. Akışlar, işlemek için zengin bir altyapıyı içeren .NET Framework boyunca kullanılır. Örneğin, yalnızca akışı başlatacak olan kodun yalnızca birkaç satırını değiştirerek, bir ' <xref:System.IO.FileStream> dan veri <xref:System.Net.Sockets.NetworkStream> okumak için bir uygulamayı bir ' dan okuyabilirsiniz. **NetworkStream** sınıfı ve diğer akışlar arasındaki önemli farklılıklar, **NetworkStream** 'in aranabilir olmadığı, <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> <xref:System.Net.Sockets.NetworkStream.Seek%2A> özelliğin her zaman **false**döndüğü ve ve <xref:System.Net.Sockets.NetworkStream.Position%2A> yöntemlerinin bir <xref:System.NotSupportedException>.  
  
- Verilerin ulaştığı gibi işlenmesi. Akışlar, uygulamanızın bir veri kümesinin tamamını indirilmesini beklemek yerine, ağ üzerinden gelen verilere erişim sağlar.  
  
 Ad <xref:System.Net.Sockets> alanı, <xref:System.IO.Stream> sınıfı özel olarak ağ kaynaklarıyla kullanılmak üzere uygulayan bir **NetworkStream** sınıfı içerir. Ad alanındaki sınıflar, akışları temsil etmek için NetworkStream sınıfını kullanır. <xref:System.Net.Sockets>  
  
 Döndürülen akışı kullanarak ağa veri göndermek için, <xref:System.Net.WebRequest.GetRequestStream%2A> <xref:System.Net.WebRequest>üzerinde öğesini çağırın. **WebRequest** , istek üst bilgilerini sunucuya gönderir; ardından <xref:System.IO.Stream.BeginWrite%2A>, döndürülen akışta, <xref:System.IO.Stream.EndWrite%2A>veya <xref:System.IO.Stream.Write%2A> yöntemini çağırarak ağ kaynağına veri gönderebilirsiniz. HTTP gibi bazı protokoller, verileri göndermeden önce protokole özgü özellikler ayarlamanız gerekebilir. Aşağıdaki kod örneğinde, veri göndermek için HTTP 'ye özgü özelliklerin nasıl ayarlanacağı gösterilmektedir. Değişkenin `sendData` gönderileceği verileri içerdiğini ve değişkenin `sendLength` gönderileceği verilerin bayt sayısını olduğunu varsayar.  
  
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
  
 Ağdan veri almak için ' i arayın <xref:System.Net.WebResponse.GetResponseStream%2A>. <xref:System.Net.WebResponse> Ardından <xref:System.IO.Stream.BeginRead%2A>, döndürülen akışta, <xref:System.IO.Stream.EndRead%2A>veya <xref:System.IO.Stream.Read%2A> yöntemini çağırarak ağ kaynağından verileri okuyabilirsiniz.  
  
 Ağ kaynaklarından akışlar kullanırken, aşağıdaki noktaları göz önünde bulundurun:  
  
- **NetworkStream** sınıfı akıştaki konumu Değiştirelemediğinden **CanSeek** özelliği her zaman **false** değerini döndürür. **Seek** ve **Position** yöntemleri **NotSupportedException**oluşturur.  
  
- **WebRequest** ve **WebResponse**kullandığınızda, **GetResponseStream** çağrılırken oluşturulan akış örnekleri salt okunurdur ve **GetRequestStream** çağrılırken oluşturulan akış örnekleri salt yazılır.  
  
- Kodlamayı daha kolay hale getirmek için sınıfınıkullanın.<xref:System.IO.StreamReader> Aşağıdaki kod örneği bir **Web YANıTıNDAN** ASCII kodlamalı bir akış okumak Için bir **StreamReader** kullanır (örnek, istek oluşturmayı göstermez).  
  
- Ağ kaynaklarının kullanılabilir olup olmadığını **GetResponse** çağrısı engelleyebilir. <xref:System.Net.WebRequest.BeginGetResponse%2A> Ve<xref:System.Net.WebRequest.EndGetResponse%2A> yöntemleriyle zaman uyumsuz bir istek kullanmayı göz önünde bulundurmanız gerekir.  
  
- Sunucu bağlantısı oluşturulurken **GetRequestStream** çağrısı engelleyebilirler. <xref:System.Net.WebRequest.BeginGetRequestStream%2A> Ve<xref:System.Net.WebRequest.EndGetRequestStream%2A> yöntemleriyle akış için zaman uyumsuz bir istek kullanmayı göz önünde bulundurmanız gerekir.  
  
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

- [Nasıl yapılır: WebRequest sınıfını kullanarak veri isteme](how-to-request-data-using-the-webrequest-class.md)
- [Veri İsteme](requesting-data.md)
