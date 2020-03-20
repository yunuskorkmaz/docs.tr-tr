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
# <a name="handling-errors"></a><span data-ttu-id="998da-102">Hataları İşleme</span><span class="sxs-lookup"><span data-stu-id="998da-102">Handling Errors</span></span>

<span data-ttu-id="998da-103">Ve <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> sınıflar hem sistem özel durumlarını (örneğin) <xref:System.ArgumentException>hem de <xref:System.Net.WebException> Web'e <xref:System.Net.WebRequest.GetResponse%2A> özgü özel özel durumları (yöntem tarafından atılan) atar.</span><span class="sxs-lookup"><span data-stu-id="998da-103">The <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes throw both system exceptions (such as <xref:System.ArgumentException>) and Web-specific exceptions (which are <xref:System.Net.WebException> thrown by the <xref:System.Net.WebRequest.GetResponse%2A> method).</span></span>  
  
<span data-ttu-id="998da-104">Her **WebException** <xref:System.Net.WebException.Status%2A> numaralandırma bir <xref:System.Net.WebExceptionStatus> değer içeren bir özellik içerir.</span><span class="sxs-lookup"><span data-stu-id="998da-104">Each **WebException** includes a <xref:System.Net.WebException.Status%2A> property that contains a value from the <xref:System.Net.WebExceptionStatus> enumeration.</span></span> <span data-ttu-id="998da-105">Oluşan hatayı belirlemek için **Durum** özelliğini inceleyebilir ve hatayı gidermek için uygun adımları atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="998da-105">You can examine the **Status** property to determine the error that occurred and take the proper steps to resolve the error.</span></span>  
  
<span data-ttu-id="998da-106">Aşağıdaki **tabloda Durum** özelliği için olası değerler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="998da-106">The following table describes the possible values for the **Status** property.</span></span>  
  
|<span data-ttu-id="998da-107">Durum</span><span class="sxs-lookup"><span data-stu-id="998da-107">Status</span></span>|<span data-ttu-id="998da-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="998da-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="998da-109">ConnectFailure</span><span class="sxs-lookup"><span data-stu-id="998da-109">ConnectFailure</span></span>|<span data-ttu-id="998da-110">Uzak hizmet, aktarım düzeyinde bağlantı kuramadı.</span><span class="sxs-lookup"><span data-stu-id="998da-110">The remote service could not be contacted at the transport level.</span></span>|  
|<span data-ttu-id="998da-111">Bağlantı Kapalı</span><span class="sxs-lookup"><span data-stu-id="998da-111">ConnectionClosed</span></span>|<span data-ttu-id="998da-112">Bağlantı zamanından önce kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="998da-112">The connection was closed prematurely.</span></span>|  
|<span data-ttu-id="998da-113">KeepAliveFailure</span><span class="sxs-lookup"><span data-stu-id="998da-113">KeepAliveFailure</span></span>|<span data-ttu-id="998da-114">Sunucu, Canlı Kal üstbilgi kümesiyle yapılan bir bağlantıyı kapattı.</span><span class="sxs-lookup"><span data-stu-id="998da-114">The server closed a connection made with the Keep-alive header set.</span></span>|  
|<span data-ttu-id="998da-115">Ad Çözümleme Hatası</span><span class="sxs-lookup"><span data-stu-id="998da-115">NameResolutionFailure</span></span>|<span data-ttu-id="998da-116">Ad hizmeti ana bilgisayar adını çözümlemedi.</span><span class="sxs-lookup"><span data-stu-id="998da-116">The name service could not resolve the host name.</span></span>|  
|<span data-ttu-id="998da-117">ProtokolHatası</span><span class="sxs-lookup"><span data-stu-id="998da-117">ProtocolError</span></span>|<span data-ttu-id="998da-118">Sunucudan alınan yanıt tamamlandı, ancak protokol düzeyinde bir hata belirtildi.</span><span class="sxs-lookup"><span data-stu-id="998da-118">The response received from the server was complete but indicated an error at the protocol level.</span></span>|  
|<span data-ttu-id="998da-119">Alma Hatası</span><span class="sxs-lookup"><span data-stu-id="998da-119">ReceiveFailure</span></span>|<span data-ttu-id="998da-120">Uzak sunucudan tam bir yanıt alınmadı.</span><span class="sxs-lookup"><span data-stu-id="998da-120">A complete response was not received from the remote server.</span></span>|  
|<span data-ttu-id="998da-121">İstekİptal edildi</span><span class="sxs-lookup"><span data-stu-id="998da-121">RequestCanceled</span></span>|<span data-ttu-id="998da-122">İstek iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="998da-122">The request was canceled.</span></span>|  
|<span data-ttu-id="998da-123">Güvenli Kanal Hatası</span><span class="sxs-lookup"><span data-stu-id="998da-123">SecureChannelFailure</span></span>|<span data-ttu-id="998da-124">Güvenli bir kanal bağlantısında bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="998da-124">An error occurred in a secure channel link.</span></span>|  
|<span data-ttu-id="998da-125">SendFailure</span><span class="sxs-lookup"><span data-stu-id="998da-125">SendFailure</span></span>|<span data-ttu-id="998da-126">Uzak sunucuya tam bir istek gönderilemedi.</span><span class="sxs-lookup"><span data-stu-id="998da-126">A complete request could not be sent to the remote server.</span></span>|  
|<span data-ttu-id="998da-127">ServerProtocolViolation</span><span class="sxs-lookup"><span data-stu-id="998da-127">ServerProtocolViolation</span></span>|<span data-ttu-id="998da-128">Sunucu yanıtı geçerli bir HTTP yanıtı değildi.</span><span class="sxs-lookup"><span data-stu-id="998da-128">The server response was not a valid HTTP response.</span></span>|  
|<span data-ttu-id="998da-129">Başarılı</span><span class="sxs-lookup"><span data-stu-id="998da-129">Success</span></span>|<span data-ttu-id="998da-130">Hiçbir hata yla karşılaşılmamada.</span><span class="sxs-lookup"><span data-stu-id="998da-130">No error was encountered.</span></span>|  
|<span data-ttu-id="998da-131">Zaman aşımı</span><span class="sxs-lookup"><span data-stu-id="998da-131">Timeout</span></span>|<span data-ttu-id="998da-132">İstek için zaman belirleme kümesi içinde yanıt alınmadı.</span><span class="sxs-lookup"><span data-stu-id="998da-132">No response was received within the time-out set for the request.</span></span>|  
|<span data-ttu-id="998da-133">Güven Hatası</span><span class="sxs-lookup"><span data-stu-id="998da-133">TrustFailure</span></span>|<span data-ttu-id="998da-134">Sunucu sertifikası doğrulanamadı.</span><span class="sxs-lookup"><span data-stu-id="998da-134">A server certificate could not be validated.</span></span>|  
|<span data-ttu-id="998da-135">MesajUzunluğuLimitAşıldı</span><span class="sxs-lookup"><span data-stu-id="998da-135">MessageLengthLimitExceeded</span></span>|<span data-ttu-id="998da-136">İstek gönderirken veya sunucudan yanıt alırken belirtilen sınırı aşan bir ileti alındı.</span><span class="sxs-lookup"><span data-stu-id="998da-136">A message was received that exceeded the specified limit when sending a request or receiving a response from the server.</span></span>|  
|<span data-ttu-id="998da-137">Beklemede</span><span class="sxs-lookup"><span data-stu-id="998da-137">Pending</span></span>|<span data-ttu-id="998da-138">Dahili bir eşzamanlı istek beklemede.</span><span class="sxs-lookup"><span data-stu-id="998da-138">An internal asynchronous request is pending.</span></span>|  
|<span data-ttu-id="998da-139">Boru Hattı Arıza</span><span class="sxs-lookup"><span data-stu-id="998da-139">PipelineFailure</span></span>|<span data-ttu-id="998da-140">Bu değer .NET Framework altyapısını destekler ve doğrudan kodunuzda kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="998da-140">This value supports the .NET Framework infrastructure and is not intended to be used directly in your code.</span></span>|  
|<span data-ttu-id="998da-141">ProxyNameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="998da-141">ProxyNameResolutionFailure</span></span>|<span data-ttu-id="998da-142">Ad çözümleyici hizmeti proxy ana bilgisayar adını çözemedi.</span><span class="sxs-lookup"><span data-stu-id="998da-142">The name resolver service could not resolve the proxy host name.</span></span>|  
|<span data-ttu-id="998da-143">UnknownError</span><span class="sxs-lookup"><span data-stu-id="998da-143">UnknownError</span></span>|<span data-ttu-id="998da-144">Bilinmeyen türde bir özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="998da-144">An exception of unknown type has occurred.</span></span>|  
  
<span data-ttu-id="998da-145">**Durum** özelliği **WebExceptionStatus.ProtocolError**olduğunda, sunucudan yanıt içeren bir **WebResponse** kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="998da-145">When the **Status** property is **WebExceptionStatus.ProtocolError**, a **WebResponse** that contains the response from the server is available.</span></span> <span data-ttu-id="998da-146">Bu yanıtı, protokol hatasının gerçek kaynağını belirlemek için inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="998da-146">You can examine this response to determine the actual source of the protocol error.</span></span>  
  
<span data-ttu-id="998da-147">Aşağıdaki örnek, bir **WebException'ı**nasıl yakalayacaklarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="998da-147">The following example shows how to catch a **WebException**.</span></span>  
  
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
  
<span data-ttu-id="998da-148">Windows yuvasında <xref:System.Net.Sockets.Socket> hatalar <xref:System.Net.Sockets.SocketException> oluştuğunda sınıf atışını kullanan uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="998da-148">Applications that use the <xref:System.Net.Sockets.Socket> class throw <xref:System.Net.Sockets.SocketException> when errors occur on the Windows socket.</span></span> <span data-ttu-id="998da-149">, <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.TcpListener>ve <xref:System.Net.Sockets.UdpClient> sınıflar **Soket** sınıfının üstüne inşa edilir ve **SocketExceptions** atmak da.</span><span class="sxs-lookup"><span data-stu-id="998da-149">The <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes are built on top of the **Socket** class and throw **SocketExceptions** as well.</span></span>  
  
<span data-ttu-id="998da-150">**SocketException** atıldığında, **SocketException** sınıfı <xref:System.Net.Sockets.SocketException.ErrorCode%2A> özelliği oluşan son işletim sistemi soketi hatasına ayarlar.</span><span class="sxs-lookup"><span data-stu-id="998da-150">When a **SocketException** is thrown, the **SocketException** class sets the <xref:System.Net.Sockets.SocketException.ErrorCode%2A> property to the last operating system socket error that occurred.</span></span> <span data-ttu-id="998da-151">Soket hata kodları hakkında daha fazla bilgi için MSDN'deki Winsock 2.0 API hata kodu belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="998da-151">For more information about socket error codes, see the Winsock 2.0 API error code documentation in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="998da-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="998da-152">See also</span></span>

- [<span data-ttu-id="998da-153">.NET'te özel durumları işleme ve atma</span><span class="sxs-lookup"><span data-stu-id="998da-153">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="998da-154">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="998da-154">Requesting Data</span></span>](requesting-data.md)
