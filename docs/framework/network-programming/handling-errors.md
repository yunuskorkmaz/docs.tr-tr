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
ms.openlocfilehash: 26e2a25855485bdd19d30e8497d0f75b7d4432e0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097167"
---
# <a name="handling-errors"></a><span data-ttu-id="eb334-102">Hataları İşleme</span><span class="sxs-lookup"><span data-stu-id="eb334-102">Handling Errors</span></span>
<span data-ttu-id="eb334-103"><xref:System.Net.WebRequest> Ve <xref:System.Net.WebResponse> sınıflar her iki sistem özel durumlarını throw (gibi <xref:System.ArgumentException>) ve Web özel durumlar (hangi <xref:System.Net.WebException> tarafından oluşturulan <xref:System.Net.WebRequest.GetResponse%2A> yöntemi).</span><span class="sxs-lookup"><span data-stu-id="eb334-103">The <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes throw both system exceptions (such as <xref:System.ArgumentException>) and Web-specific exceptions (which are <xref:System.Net.WebException> thrown by the <xref:System.Net.WebRequest.GetResponse%2A> method).</span></span>  
  
 <span data-ttu-id="eb334-104">Her **WebException** içeren bir <xref:System.Net.WebException.Status%2A> arasında bir değer içeren özellik <xref:System.Net.WebExceptionStatus> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="eb334-104">Each **WebException** includes a <xref:System.Net.WebException.Status%2A> property that contains a value from the <xref:System.Net.WebExceptionStatus> enumeration.</span></span> <span data-ttu-id="eb334-105">İnceleyebilirsiniz **durumu** özelliği oluşan hata belirlemek ve hatayı gidermek için uygun adımları atın.</span><span class="sxs-lookup"><span data-stu-id="eb334-105">You can examine the **Status** property to determine the error that occurred and take the proper steps to resolve the error.</span></span>  
  
 <span data-ttu-id="eb334-106">Aşağıdaki tabloda olası değerleri açıklanmaktadır **durumu** özelliği.</span><span class="sxs-lookup"><span data-stu-id="eb334-106">The following table describes the possible values for the **Status** property.</span></span>  
  
|<span data-ttu-id="eb334-107">Durum</span><span class="sxs-lookup"><span data-stu-id="eb334-107">Status</span></span>|<span data-ttu-id="eb334-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb334-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="eb334-109">ConnectFailure</span><span class="sxs-lookup"><span data-stu-id="eb334-109">ConnectFailure</span></span>|<span data-ttu-id="eb334-110">Uzak Hizmet taşıma düzeyinde kurulamadı.</span><span class="sxs-lookup"><span data-stu-id="eb334-110">The remote service could not be contacted at the transport level.</span></span>|  
|<span data-ttu-id="eb334-111">ConnectionClosed</span><span class="sxs-lookup"><span data-stu-id="eb334-111">ConnectionClosed</span></span>|<span data-ttu-id="eb334-112">Bağlantıyı erken sonlandırdı.</span><span class="sxs-lookup"><span data-stu-id="eb334-112">The connection was closed prematurely.</span></span>|  
|<span data-ttu-id="eb334-113">KeepAliveFailure</span><span class="sxs-lookup"><span data-stu-id="eb334-113">KeepAliveFailure</span></span>|<span data-ttu-id="eb334-114">Sunucu Keep-alive üst bilgisi kümesiyle yapılan bağlantı kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="eb334-114">The server closed a connection made with the Keep-alive header set.</span></span>|  
|<span data-ttu-id="eb334-115">NameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="eb334-115">NameResolutionFailure</span></span>|<span data-ttu-id="eb334-116">Ad hizmeti konak adı çözümlenemedi.</span><span class="sxs-lookup"><span data-stu-id="eb334-116">The name service could not resolve the host name.</span></span>|  
|<span data-ttu-id="eb334-117">ProtocolError</span><span class="sxs-lookup"><span data-stu-id="eb334-117">ProtocolError</span></span>|<span data-ttu-id="eb334-118">Sunucudan alınan yanıtı tamamlandı ancak protokol düzeyinde bir hata gösterilir.</span><span class="sxs-lookup"><span data-stu-id="eb334-118">The response received from the server was complete but indicated an error at the protocol level.</span></span>|  
|<span data-ttu-id="eb334-119">ReceiveFailure</span><span class="sxs-lookup"><span data-stu-id="eb334-119">ReceiveFailure</span></span>|<span data-ttu-id="eb334-120">Uzak sunucudan tam yanıtı alınmadı.</span><span class="sxs-lookup"><span data-stu-id="eb334-120">A complete response was not received from the remote server.</span></span>|  
|<span data-ttu-id="eb334-121">RequestCanceled</span><span class="sxs-lookup"><span data-stu-id="eb334-121">RequestCanceled</span></span>|<span data-ttu-id="eb334-122">İstek iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="eb334-122">The request was canceled.</span></span>|  
|<span data-ttu-id="eb334-123">SecureChannelFailure</span><span class="sxs-lookup"><span data-stu-id="eb334-123">SecureChannelFailure</span></span>|<span data-ttu-id="eb334-124">Güvenli kanal bağlantısında hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="eb334-124">An error occurred in a secure channel link.</span></span>|  
|<span data-ttu-id="eb334-125">SendFailure</span><span class="sxs-lookup"><span data-stu-id="eb334-125">SendFailure</span></span>|<span data-ttu-id="eb334-126">Uzak sunucuya tam bir istek gönderilemedi.</span><span class="sxs-lookup"><span data-stu-id="eb334-126">A complete request could not be sent to the remote server.</span></span>|  
|<span data-ttu-id="eb334-127">ServerProtocolViolation</span><span class="sxs-lookup"><span data-stu-id="eb334-127">ServerProtocolViolation</span></span>|<span data-ttu-id="eb334-128">Sunucu yanıtı geçerli bir HTTP yanıt değildi.</span><span class="sxs-lookup"><span data-stu-id="eb334-128">The server response was not a valid HTTP response.</span></span>|  
|<span data-ttu-id="eb334-129">Başarılı</span><span class="sxs-lookup"><span data-stu-id="eb334-129">Success</span></span>|<span data-ttu-id="eb334-130">Herhangi bir hata ile karşılaşıldı.</span><span class="sxs-lookup"><span data-stu-id="eb334-130">No error was encountered.</span></span>|  
|<span data-ttu-id="eb334-131">zaman aşımı</span><span class="sxs-lookup"><span data-stu-id="eb334-131">Timeout</span></span>|<span data-ttu-id="eb334-132">İçin isteği zaman aşımı içinde yanıt alınmadı.</span><span class="sxs-lookup"><span data-stu-id="eb334-132">No response was received within the time-out set for the request.</span></span>|  
|<span data-ttu-id="eb334-133">TrustFailure</span><span class="sxs-lookup"><span data-stu-id="eb334-133">TrustFailure</span></span>|<span data-ttu-id="eb334-134">Bir sunucu sertifikası doğrulanamadı.</span><span class="sxs-lookup"><span data-stu-id="eb334-134">A server certificate could not be validated.</span></span>|  
|<span data-ttu-id="eb334-135">MessageLengthLimitExceeded</span><span class="sxs-lookup"><span data-stu-id="eb334-135">MessageLengthLimitExceeded</span></span>|<span data-ttu-id="eb334-136">Bir isteği gönderirken belirtilen sınırı aşan bir ileti alındı veya bir yanıt sunucudan alma.</span><span class="sxs-lookup"><span data-stu-id="eb334-136">A message was received that exceeded the specified limit when sending a request or receiving a response from the server.</span></span>|  
|<span data-ttu-id="eb334-137">Bekleniyor</span><span class="sxs-lookup"><span data-stu-id="eb334-137">Pending</span></span>|<span data-ttu-id="eb334-138">İç zaman uyumsuz isteği bekliyor.</span><span class="sxs-lookup"><span data-stu-id="eb334-138">An internal asynchronous request is pending.</span></span>|  
|<span data-ttu-id="eb334-139">PipelineFailure</span><span class="sxs-lookup"><span data-stu-id="eb334-139">PipelineFailure</span></span>|<span data-ttu-id="eb334-140">Bu değer .NET Framework altyapısını destekler ve doğrudan kodunuzda kullanılması amaçlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="eb334-140">This value supports the .NET Framework infrastructure and is not intended to be used directly in your code.</span></span>|  
|<span data-ttu-id="eb334-141">ProxyNameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="eb334-141">ProxyNameResolutionFailure</span></span>|<span data-ttu-id="eb334-142">Ad çözümleyici hizmetini proxy konak adı çözümlenemedi.</span><span class="sxs-lookup"><span data-stu-id="eb334-142">The name resolver service could not resolve the proxy host name.</span></span>|  
|<span data-ttu-id="eb334-143">Başvuruları</span><span class="sxs-lookup"><span data-stu-id="eb334-143">UnknownError</span></span>|<span data-ttu-id="eb334-144">Bilinmeyen türde bir özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="eb334-144">An exception of unknown type has occurred.</span></span>|  
  
 <span data-ttu-id="eb334-145">Zaman **durumu** özelliği **WebExceptionStatus.ProtocolError**, **WebResponse** sunucu yanıtı içeren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb334-145">When the **Status** property is **WebExceptionStatus.ProtocolError**, a **WebResponse** that contains the response from the server is available.</span></span> <span data-ttu-id="eb334-146">Protokol hatası gerçek kaynağını belirlemek için bu yanıtı inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb334-146">You can examine this response to determine the actual source of the protocol error.</span></span>  
  
 <span data-ttu-id="eb334-147">Aşağıdaki örnek catch gösterilmiştir bir **WebException**.</span><span class="sxs-lookup"><span data-stu-id="eb334-147">The following example shows how to catch a **WebException**.</span></span>  
  
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
  
 <span data-ttu-id="eb334-148">Kullanan uygulamalar <xref:System.Net.Sockets.Socket> sınıfı throw <xref:System.Net.Sockets.SocketException> hataları Windows yuva olduğunda.</span><span class="sxs-lookup"><span data-stu-id="eb334-148">Applications that use the <xref:System.Net.Sockets.Socket> class throw <xref:System.Net.Sockets.SocketException> when errors occur on the Windows socket.</span></span> <span data-ttu-id="eb334-149"><xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, Ve <xref:System.Net.Sockets.UdpClient> sınıfları üst kısmındaki yerleşiktir **yuva** sınıfı ve throw **SocketExceptions** de.</span><span class="sxs-lookup"><span data-stu-id="eb334-149">The <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes are built on top of the **Socket** class and throw **SocketExceptions** as well.</span></span>  
  
 <span data-ttu-id="eb334-150">Olduğunda bir **SocketException** oluşturulur, **SocketException** sınıf kümelerini <xref:System.Net.Sockets.SocketException.ErrorCode%2A> özelliğini gerçekleşen son işletim sistemi Yuva hatası.</span><span class="sxs-lookup"><span data-stu-id="eb334-150">When a **SocketException** is thrown, the **SocketException** class sets the <xref:System.Net.Sockets.SocketException.ErrorCode%2A> property to the last operating system socket error that occurred.</span></span> <span data-ttu-id="eb334-151">Yuva hata kodları hakkında daha fazla bilgi için MSDN'de Winsock 2.0 API'sine hata kodu belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="eb334-151">For more information about socket error codes, see the Winsock 2.0 API error code documentation in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb334-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb334-152">See also</span></span>

- [<span data-ttu-id="eb334-153">Özel durum işleme temelleri</span><span class="sxs-lookup"><span data-stu-id="eb334-153">Exception Handling Fundamentals</span></span>](../../../docs/standard/exceptions/exception-handling-fundamentals.md)
- [<span data-ttu-id="eb334-154">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="eb334-154">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
