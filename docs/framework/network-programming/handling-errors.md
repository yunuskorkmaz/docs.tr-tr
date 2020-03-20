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
ms.openlocfilehash: f5be5d8e14d7aa2d98009fc10c9cce314e745ed1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180865"
---
# <a name="handling-errors"></a>Hataları İşleme

Ve <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> sınıflar hem sistem özel durumlarını (örneğin) <xref:System.ArgumentException>hem de <xref:System.Net.WebException> Web'e <xref:System.Net.WebRequest.GetResponse%2A> özgü özel özel durumları (yöntem tarafından atılan) atar.  
  
Her **WebException** <xref:System.Net.WebException.Status%2A> numaralandırma bir <xref:System.Net.WebExceptionStatus> değer içeren bir özellik içerir. Oluşan hatayı belirlemek için **Durum** özelliğini inceleyebilir ve hatayı gidermek için uygun adımları atabilirsiniz.  
  
Aşağıdaki **tabloda Durum** özelliği için olası değerler açıklanmaktadır.  
  
|Durum|Açıklama|  
|------------|-----------------|  
|ConnectFailure|Uzak hizmet, aktarım düzeyinde bağlantı kuramadı.|  
|Bağlantı Kapalı|Bağlantı zamanından önce kapatıldı.|  
|KeepAliveFailure|Sunucu, Canlı Kal üstbilgi kümesiyle yapılan bir bağlantıyı kapattı.|  
|Ad Çözümleme Hatası|Ad hizmeti ana bilgisayar adını çözümlemedi.|  
|ProtokolHatası|Sunucudan alınan yanıt tamamlandı, ancak protokol düzeyinde bir hata belirtildi.|  
|Alma Hatası|Uzak sunucudan tam bir yanıt alınmadı.|  
|İstekİptal edildi|İstek iptal edildi.|  
|Güvenli Kanal Hatası|Güvenli bir kanal bağlantısında bir hata oluştu.|  
|SendFailure|Uzak sunucuya tam bir istek gönderilemedi.|  
|ServerProtocolViolation|Sunucu yanıtı geçerli bir HTTP yanıtı değildi.|  
|Başarılı|Hiçbir hata yla karşılaşılmamada.|  
|Zaman aşımı|İstek için zaman belirleme kümesi içinde yanıt alınmadı.|  
|Güven Hatası|Sunucu sertifikası doğrulanamadı.|  
|MesajUzunluğuLimitAşıldı|İstek gönderirken veya sunucudan yanıt alırken belirtilen sınırı aşan bir ileti alındı.|  
|Beklemede|Dahili bir eşzamanlı istek beklemede.|  
|Boru Hattı Arıza|Bu değer .NET Framework altyapısını destekler ve doğrudan kodunuzda kullanılmak üzere tasarlanmamıştır.|  
|ProxyNameResolutionFailure|Ad çözümleyici hizmeti proxy ana bilgisayar adını çözemedi.|  
|UnknownError|Bilinmeyen türde bir özel durum oluştu.|  
  
**Durum** özelliği **WebExceptionStatus.ProtocolError**olduğunda, sunucudan yanıt içeren bir **WebResponse** kullanılabilir. Bu yanıtı, protokol hatasının gerçek kaynağını belirlemek için inceleyebilirsiniz.  
  
Aşağıdaki örnek, bir **WebException'ı**nasıl yakalayacaklarını gösterir.  
  
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
  
Windows yuvasında <xref:System.Net.Sockets.Socket> hatalar <xref:System.Net.Sockets.SocketException> oluştuğunda sınıf atışını kullanan uygulamalar. , <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.TcpListener>ve <xref:System.Net.Sockets.UdpClient> sınıflar **Soket** sınıfının üstüne inşa edilir ve **SocketExceptions** atmak da.  
  
**SocketException** atıldığında, **SocketException** sınıfı <xref:System.Net.Sockets.SocketException.ErrorCode%2A> özelliği oluşan son işletim sistemi soketi hatasına ayarlar. Soket hata kodları hakkında daha fazla bilgi için MSDN'deki Winsock 2.0 API hata kodu belgelerine bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET'te özel durumları işleme ve atma](../../standard/exceptions/index.md)
- [Veri İsteme](requesting-data.md)
