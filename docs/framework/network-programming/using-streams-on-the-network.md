---
title: Ağda Akışları Kullanma
description: .NET Framework, ağ kaynaklarını akışlar olarak temsil eder. NetworkStream sınıfı, ağ kaynaklarıyla kullanılmak üzere Stream sınıfını uygular.
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
ms.openlocfilehash: f8d35b43c9b46a77bfd0c78f7d0118093b6fe824
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501982"
---
# <a name="using-streams-on-the-network"></a>Ağda Akışları Kullanma
Ağ kaynakları .NET Framework akışlar olarak temsil edilir. Akışları genel olarak düşünerek, .NET Framework aşağıdaki özellikleri sunar:  
  
- Web verilerini göndermenin ve almanın yaygın bir yolu. Dosyanın gerçek içerikleri ne olursa olsun — HTML, XML veya başka bir şey — uygulamanız, <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType> <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType> veri göndermek ve almak için kullanır.  
  
- .NET Framework içindeki akışlarla uyumluluk. Akışlar, işlemek için zengin bir altyapıyı içeren .NET Framework boyunca kullanılır. Örneğin, <xref:System.IO.FileStream> <xref:System.Net.Sockets.NetworkStream> yalnızca akışı başlatacak olan kodun yalnızca birkaç satırını değiştirerek, bir ' dan veri okumak için bir uygulamayı bir ' dan okuyabilirsiniz. **NetworkStream** sınıfı ve diğer akışlar arasındaki önemli farklılıklar, **NetworkStream** 'in aranabilir olmadığı, <xref:System.Net.Sockets.NetworkStream.CanSeek%2A> özelliğin her zaman **false**döndüğü ve <xref:System.Net.Sockets.NetworkStream.Seek%2A> ve <xref:System.Net.Sockets.NetworkStream.Position%2A> yöntemlerinin bir oluşturması <xref:System.NotSupportedException> .  
  
- Verilerin ulaştığı gibi işlenmesi. Akışlar, uygulamanızın bir veri kümesinin tamamını indirilmesini beklemek yerine, ağ üzerinden gelen verilere erişim sağlar.  
  
 <xref:System.Net.Sockets>Ad alanı, **NetworkStream** <xref:System.IO.Stream> sınıfı özel olarak ağ kaynaklarıyla kullanılmak üzere uygulayan bir NetworkStream sınıfı içerir. <xref:System.Net.Sockets>Ad alanındaki sınıflar, akışları temsil etmek Için **NetworkStream** sınıfını kullanır.  
  
 Döndürülen akışı kullanarak ağa veri göndermek için, üzerinde öğesini çağırın <xref:System.Net.WebRequest.GetRequestStream%2A> <xref:System.Net.WebRequest> . **WebRequest** , istek üst bilgilerini sunucuya gönderir; ardından <xref:System.IO.Stream.BeginWrite%2A> , <xref:System.IO.Stream.EndWrite%2A> döndürülen akışta, veya yöntemini çağırarak ağ kaynağına veri gönderebilirsiniz <xref:System.IO.Stream.Write%2A> . HTTP gibi bazı protokoller, verileri göndermeden önce protokole özgü özellikler ayarlamanız gerekebilir. Aşağıdaki kod örneğinde, veri göndermek için HTTP 'ye özgü özelliklerin nasıl ayarlanacağı gösterilmektedir. Değişkenin `sendData` gönderileceği verileri içerdiğini ve değişkenin `sendLength` gönderileceği verilerin bayt sayısını olduğunu varsayar.  
  
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
  
 Ağdan veri almak için ' i arayın <xref:System.Net.WebResponse.GetResponseStream%2A> <xref:System.Net.WebResponse> . Ardından <xref:System.IO.Stream.BeginRead%2A> , <xref:System.IO.Stream.EndRead%2A> döndürülen akışta, veya yöntemini çağırarak ağ kaynağından verileri okuyabilirsiniz <xref:System.IO.Stream.Read%2A> .  
  
 Ağ kaynaklarından akışlar kullanırken, aşağıdaki noktaları göz önünde bulundurun:  
  
- **NetworkStream** sınıfı akıştaki konumu Değiştirelemediğinden **CanSeek** özelliği her zaman **false** değerini döndürür. **Seek** ve **Position** yöntemleri **NotSupportedException**oluşturur.  
  
- **WebRequest** ve **WebResponse**kullandığınızda, **GetResponseStream** çağrılırken oluşturulan akış örnekleri salt okunurdur ve **GetRequestStream** çağrılırken oluşturulan akış örnekleri salt yazılır.  
  
- <xref:System.IO.StreamReader>Kodlamayı daha kolay hale getirmek için sınıfını kullanın. Aşağıdaki kod örneği bir **Web YANıTıNDAN** ASCII kodlamalı bir akış okumak Için bir **StreamReader** kullanır (örnek, istek oluşturmayı göstermez).  
  
- Ağ kaynaklarının kullanılabilir olup olmadığını **GetResponse** çağrısı engelleyebilir. Ve yöntemleriyle zaman uyumsuz bir istek kullanmayı göz önünde bulundurmanız gerekir <xref:System.Net.WebRequest.BeginGetResponse%2A> <xref:System.Net.WebRequest.EndGetResponse%2A> .  
  
- Sunucu bağlantısı oluşturulurken **GetRequestStream** çağrısı engelleyebilirler. Ve yöntemleriyle akış için zaman uyumsuz bir istek kullanmayı göz önünde bulundurmanız <xref:System.Net.WebRequest.BeginGetRequestStream%2A> gerekir <xref:System.Net.WebRequest.EndGetRequestStream%2A> .  
  
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
