---
title: Hataları işleme
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8020a92345ba85a99c0b46b2d4247d677defd054
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="handling-errors"></a>Hataları işleme
<xref:System.Net.WebRequest> Ve <xref:System.Net.WebResponse> sınıfları throw her iki sistem özel durumları (gibi <xref:System.ArgumentException>) ve Web özel durumlar (hangi <xref:System.Net.WebException> tarafından oluşturulan <xref:System.Net.WebRequest.GetResponse%2A> yöntemi).  
  
 Her **WebException** içeren bir <xref:System.Net.WebException.Status%2A> arasında bir değer içeren özelliği <xref:System.Net.WebExceptionStatus> numaralandırması. İnceleyebilirsiniz **durum** özelliğini oluşan hata belirlemek ve sorunu çözümlemek için ilgili uygun adımları gerçekleştirin.  
  
 Aşağıdaki tabloda olası değerleri açıklanmaktadır **durum** özelliği.  
  
|Durum|Açıklama|  
|------------|-----------------|  
|ConnectFailure|Uzak Hizmet aktarım düzeyinde bağlantı kurulamadı.|  
|ConnectionClosed|Bağlantıyı erken sonlandırdı.|  
|KeepAliveFailure|Sunucu tutma üstbilgi kümesi ile yapılan bir bağlantı kapatıldı.|  
|NameResolutionFailure|Ad Hizmeti ana bilgisayar adı çözümlenemedi.|  
|ProtocolError|Sunucudan alınan yanıt tamamlandı ancak protokol düzeyinde bir hata gösterilir.|  
|ReceiveFailure|Tam bir yanıt Uzak sunucudan alınmadı.|  
|RequestCanceled|İstek iptal edildi.|  
|SecureChannelFailure|Güvenli kanal bağlantıdaki bir hata oluştu.|  
|SendFailure|Uzak sunucuya tam bir istek gönderilemedi.|  
|ServerProtocolViolation|Sunucu yanıtı geçerli bir HTTP yanıt değildi.|  
|Başarılı|Hiçbir hatayla karşılaşıldı.|  
|Zaman aşımı|İstek için ayarlanmış zaman aşımı içinde yanıt alındı.|  
|TrustFailure|Bir sunucu sertifikası doğrulanamadı.|  
|MessageLengthLimitExceeded|Bir isteği gönderirken belirtilen sınırı aşan bir ileti alındı veya bir yanıt sunucudan alınıyor.|  
|Bekleniyor|İç zaman uyumsuz isteği bekliyor.|  
|PipelineFailure|Bu değer .NET Framework altyapısını destekler ve doğrudan kodunuzda kullanılmak üzere tasarlanmamıştır.|  
|ProxyNameResolutionFailure|Ad Çözümleyici hizmeti proxy konak adı çözümlenemedi.|  
|Başvuruları|Bilinmeyen türde bir özel durum oluştu.|  
  
 Zaman **durum** özelliği **WebExceptionStatus.ProtocolError**, **WebResponse** sunucudan gelen yanıtı içeren kullanılabilir. Protokol hatası gerçek kaynağını belirlemek için bu yanıt inceleyebilirsiniz.  
  
 Aşağıdaki örnek catch gösterilmektedir bir **WebException**.  
  
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
  
 Kullanan uygulamalar <xref:System.Net.Sockets.Socket> sınıfı throw <xref:System.Net.Sockets.SocketException> hataları Windows yuvada olduğunda. <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, Ve <xref:System.Net.Sockets.UdpClient> sınıfları üstünde yerleşiktir **yuva** sınıfı ve throw **SocketExceptions** de.  
  
 Zaman bir **SocketException** oluşturulur, **SocketException** sınıf kümeleri <xref:System.Net.Sockets.SocketException.ErrorCode%2A> oluştu son işletim sistemi Yuva hatası özelliğine. Yuva hata kodları hakkında daha fazla bilgi için MSDN'de Winsock 2.0 API hata kodu belgelerine bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel durum işleme temelleri](../../../docs/standard/exceptions/exception-handling-fundamentals.md)  
 [Veri İsteme](../../../docs/framework/network-programming/requesting-data.md)
