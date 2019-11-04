---
title: Hataları İşleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, WebRequest and WebResponse classes exceptions
- Status property
- WebExceptions class, about WebExceptions class
- Timeout enumeration member
- ConnectFailure enumeration member
- TrustFailure enumeration member
- WebRequest class, exceptions
- requesting data from Internet, error handling
- Success enumeration member
- receiving data, errors
- ProtocolError enumeration member
- downloading Internet resources, error handling
- WebResponse class, exceptions
- SendFailure enumeration member
- errors [.NET Framework], WebRequest and WebResponse classes exceptions
- sending data, errors
- response to Internet request, error handling
- NameResolutionFailure enumeration member
- KeepAliveFailure enumeration member
- network resources, WebRequest and WebResponse classes exceptions
- RequestCanceled enumeration member
- ReceiveFailure enumeration member
- ServerProtocolViolation enumeration member
- ConnectionClosed enumeration member
- SecureChannelFailure enumeration member
ms.assetid: 657141cd-5cf5-4fdb-a4b2-4c040eba84b5
ms.openlocfilehash: 7084c4579dd5fca0075c7516754195f7cea9e27c
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458044"
---
# <a name="handling-errors"></a>Hataları İşleme

<xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları sistem özel durumlarını (<xref:System.ArgumentException>gibi) ve Web 'e özgü özel durumları (<xref:System.Net.WebRequest.GetResponse%2A> yöntemi tarafından oluşturulan <xref:System.Net.WebException>) oluşturur.  
  
Her **WebException** , <xref:System.Net.WebExceptionStatus> numaralandırmasından bir değer içeren bir <xref:System.Net.WebException.Status%2A> özelliği içerir. **Durum** özelliğini inceleyerek oluşan hatayı belirleyebilir ve hatayı çözümlemek için doğru adımları uygulayabilirsiniz.  
  
Aşağıdaki tabloda **durum** özelliği için olası değerler açıklanmaktadır.  
  
|Durum|Açıklama|  
|------------|-----------------|  
|ConnectFailure|Uzak hizmete Aktarım düzeyinde iletişim kurulamadı.|  
|ConnectionClosed|Bağlantı zamanından önce kapatıldı.|  
|KeepAliveFailure|Sunucu, etkin tut üst bilgi kümesiyle yapılan bir bağlantıyı kapattı.|  
|NameResolutionFailure|Ad hizmeti, ana bilgisayar adını çözümleyemedi.|  
|ProtocolError|Sunucudan alınan yanıt tamamlanmıştır, ancak protokol düzeyinde bir hata belirtti.|  
|ReceiveFailure|Uzak sunucudan bir bütün yanıt alınmadı.|  
|Requestiptal edildi|İstek iptal edildi.|  
|SecureChannelFailure|Güvenli kanal bağlantısında bir hata oluştu.|  
|SendFailure|Uzak sunucuya komple bir istek gönderilemedi.|  
|Serverprotocolihlaline|Sunucu yanıtı geçerli bir HTTP yanıtı değildi.|  
|Başarılı|Hatayla karşılaşılmadı.|  
|aş|İstek için zaman aşımı kümesi içinde yanıt alınmadı.|  
|TrustFailure hatası|Sunucu sertifikası doğrulanamadı.|  
|Messagelengthlimitexceıbaşında|İstek gönderilirken veya sunucudan yanıt alındığında belirtilen sınırı aşan bir ileti alındı.|  
|Bekleniyor|İç zaman uyumsuz istek bekleniyor.|  
|PipelineFailure|Bu değer .NET Framework altyapısını destekler ve doğrudan kodunuzda kullanılmaya yönelik değildir.|  
|ProxyNameResolutionFailure|Ad çözümleyici Hizmeti, proxy ana bilgisayar adını çözümleyemedi.|  
|UnknownError|Bilinmeyen türde bir özel durum oluştu.|  
  
**Status** özelliği **WebExceptionStatus. ProtocolError**olduğunda, sunucudan gelen yanıtı içeren bir **WebResponse** kullanılabilir. Protokol hatasının gerçek kaynağını öğrenmek için bu yanıtı inceleyebilirsiniz.  
  
Aşağıdaki örnek, bir **WebException**nasıl yakalandığı gösterilmektedir.  
  
```csharp  
try   
{  
    // Create a request instance.  
    WebRequest myRequest =   
    WebRequest.Create("http://www.contoso.com");  
    // Get the response.  
    WebResponse myResponse = myRequest.GetResponse();  
    //Get a readable stream from the server.   
    Stream sr = myResponse.GetResponseStream();  
  
    //Read from the stream and write any data to the console.  
    bytesread = sr.Read( myBuffer, 0, length);  
    while( bytesread > 0 )   
    {  
        for (int i=0; i<bytesread; i++) {  
            Console.Write( "{0}", myBuffer[i]);  
        }  
        Console.WriteLine();  
        bytesread = sr.Read( myBuffer, 0, length);  
    }  
    sr.Close();  
    myResponse.Close();  
}  
catch (WebException webExcp)   
{  
    // If you reach this point, an exception has been caught.  
    Console.WriteLine("A WebException has been caught.");  
    // Write out the WebException message.  
    Console.WriteLine(webExcp.ToString());  
    // Get the WebException status code.  
    WebExceptionStatus status =  webExcp.Status;  
    // If status is WebExceptionStatus.ProtocolError,   
    //   there has been a protocol error and a WebResponse   
    //   should exist. Display the protocol error.  
    if (status == WebExceptionStatus.ProtocolError) {  
        Console.Write("The server returned protocol error ");  
        // Get HttpWebResponse so that you can check the HTTP status code.  
        HttpWebResponse httpResponse = (HttpWebResponse)webExcp.Response;  
        Console.WriteLine((int)httpResponse.StatusCode + " - "  
           + httpResponse.StatusCode);  
    }  
}  
catch (Exception e)   
{  
    // Code to catch other exceptions goes here.  
}  
```  
  
```vb  
Try  
    ' Create a request instance.  
    Dim myRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
    ' Get the response.  
    Dim myResponse As WebResponse = myRequest.GetResponse()  
    'Get a readable stream from the server.   
    Dim sr As Stream = myResponse.GetResponseStream()  
  
    Dim i As Integer      
    'Read from the stream and write any data to the console.  
    bytesread = sr.Read(myBuffer, 0, length)  
    While bytesread > 0  
        For i = 0 To bytesread - 1  
            Console.Write("{0}", myBuffer(i))  
        Next i  
        Console.WriteLine()  
        bytesread = sr.Read(myBuffer, 0, length)  
    End While  
    sr.Close()  
    myResponse.Close()  
Catch webExcp As WebException  
    ' If you reach this point, an exception has been caught.  
    Console.WriteLine("A WebException has been caught.")  
    ' Write out the WebException message.  
    Console.WriteLine(webExcp.ToString())  
    ' Get the WebException status code.  
    Dim status As WebExceptionStatus = webExcp.Status  
    ' If status is WebExceptionStatus.ProtocolError,   
    '   there has been a protocol error and a WebResponse   
    '   should exist. Display the protocol error.  
    If status = WebExceptionStatus.ProtocolError Then  
        Console.Write("The server returned protocol error ")  
        ' Get HttpWebResponse so that you can check the HTTP status code.  
        Dim httpResponse As HttpWebResponse = _  
           CType(webExcp.Response, HttpWebResponse)  
        Console.WriteLine(CInt(httpResponse.StatusCode).ToString() & _  
           " - " & httpResponse.StatusCode.ToString())  
    End If  
Catch e As Exception  
    ' Code to catch other exceptions goes here.  
End Try  
```  
  
<xref:System.Net.Sockets.Socket> sınıfını kullanan uygulamalar, Windows yuvasında hata oluştuğunda <xref:System.Net.Sockets.SocketException> oluşturur. <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>ve <xref:System.Net.Sockets.UdpClient> sınıfları **yuva** sınıfının üzerine kurulmuştur ve **SocketExceptions** de oluşturur.  
  
Bir **SocketException** oluşturulduğunda, **socketexception** sınıfı <xref:System.Net.Sockets.SocketException.ErrorCode%2A> özelliğini gerçekleşen son işletim sistemi yuva hatası olarak ayarlar. Yuva hata kodları hakkında daha fazla bilgi için MSDN 'de Winsock 2,0 API hata kodu belgelerine bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET 'te özel durumları işleme ve atma](../../standard/exceptions/index.md)
- [Veri İsteme](requesting-data.md)
