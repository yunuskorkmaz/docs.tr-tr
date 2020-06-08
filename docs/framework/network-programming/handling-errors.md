---
title: Hataları İşleme
description: WebRequest ve WebResponse tarafından oluşturulan sistem ve Web 'e özel özel durumlar hakkında bilgi edinin. Sorunu anlamak ve çözmek için Status özelliğini kullanın.
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
ms.openlocfilehash: 786b2bd8bc4d1b394bcfe920053b2f4f55d1cdea
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502580"
---
# <a name="handling-errors"></a><span data-ttu-id="cf7c9-104">Hataları İşleme</span><span class="sxs-lookup"><span data-stu-id="cf7c9-104">Handling Errors</span></span>

<span data-ttu-id="cf7c9-105"><xref:System.Net.WebRequest>Ve <xref:System.Net.WebResponse> sınıfları hem sistem özel durumlarını (gibi) hem de <xref:System.ArgumentException> Web 'e özel özel durumları ( <xref:System.Net.WebException> yöntemi tarafından oluşturulan) oluşturur <xref:System.Net.WebRequest.GetResponse%2A> .</span><span class="sxs-lookup"><span data-stu-id="cf7c9-105">The <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes throw both system exceptions (such as <xref:System.ArgumentException>) and Web-specific exceptions (which are <xref:System.Net.WebException> thrown by the <xref:System.Net.WebRequest.GetResponse%2A> method).</span></span>  
  
<span data-ttu-id="cf7c9-106">Her **WebException** <xref:System.Net.WebException.Status%2A> , Numaralandırmadaki bir değer içeren bir özelliği içerir <xref:System.Net.WebExceptionStatus> .</span><span class="sxs-lookup"><span data-stu-id="cf7c9-106">Each **WebException** includes a <xref:System.Net.WebException.Status%2A> property that contains a value from the <xref:System.Net.WebExceptionStatus> enumeration.</span></span> <span data-ttu-id="cf7c9-107">**Durum** özelliğini inceleyerek oluşan hatayı belirleyebilir ve hatayı çözümlemek için doğru adımları uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-107">You can examine the **Status** property to determine the error that occurred and take the proper steps to resolve the error.</span></span>  
  
<span data-ttu-id="cf7c9-108">Aşağıdaki tabloda **durum** özelliği için olası değerler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-108">The following table describes the possible values for the **Status** property.</span></span>  
  
|<span data-ttu-id="cf7c9-109">Durum</span><span class="sxs-lookup"><span data-stu-id="cf7c9-109">Status</span></span>|<span data-ttu-id="cf7c9-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf7c9-110">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="cf7c9-111">ConnectFailure</span><span class="sxs-lookup"><span data-stu-id="cf7c9-111">ConnectFailure</span></span>|<span data-ttu-id="cf7c9-112">Uzak hizmete Aktarım düzeyinde iletişim kurulamadı.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-112">The remote service could not be contacted at the transport level.</span></span>|  
|<span data-ttu-id="cf7c9-113">ConnectionClosed</span><span class="sxs-lookup"><span data-stu-id="cf7c9-113">ConnectionClosed</span></span>|<span data-ttu-id="cf7c9-114">Bağlantı zamanından önce kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-114">The connection was closed prematurely.</span></span>|  
|<span data-ttu-id="cf7c9-115">KeepAliveFailure</span><span class="sxs-lookup"><span data-stu-id="cf7c9-115">KeepAliveFailure</span></span>|<span data-ttu-id="cf7c9-116">Sunucu, etkin tut üst bilgi kümesiyle yapılan bir bağlantıyı kapattı.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-116">The server closed a connection made with the Keep-alive header set.</span></span>|  
|<span data-ttu-id="cf7c9-117">NameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="cf7c9-117">NameResolutionFailure</span></span>|<span data-ttu-id="cf7c9-118">Ad hizmeti, ana bilgisayar adını çözümleyemedi.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-118">The name service could not resolve the host name.</span></span>|  
|<span data-ttu-id="cf7c9-119">ProtocolError</span><span class="sxs-lookup"><span data-stu-id="cf7c9-119">ProtocolError</span></span>|<span data-ttu-id="cf7c9-120">Sunucudan alınan yanıt tamamlanmıştır, ancak protokol düzeyinde bir hata belirtti.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-120">The response received from the server was complete but indicated an error at the protocol level.</span></span>|  
|<span data-ttu-id="cf7c9-121">ReceiveFailure</span><span class="sxs-lookup"><span data-stu-id="cf7c9-121">ReceiveFailure</span></span>|<span data-ttu-id="cf7c9-122">Uzak sunucudan bir bütün yanıt alınmadı.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-122">A complete response was not received from the remote server.</span></span>|  
|<span data-ttu-id="cf7c9-123">Requestiptal edildi</span><span class="sxs-lookup"><span data-stu-id="cf7c9-123">RequestCanceled</span></span>|<span data-ttu-id="cf7c9-124">İstek iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-124">The request was canceled.</span></span>|  
|<span data-ttu-id="cf7c9-125">SecureChannelFailure</span><span class="sxs-lookup"><span data-stu-id="cf7c9-125">SecureChannelFailure</span></span>|<span data-ttu-id="cf7c9-126">Güvenli kanal bağlantısında bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-126">An error occurred in a secure channel link.</span></span>|  
|<span data-ttu-id="cf7c9-127">SendFailure</span><span class="sxs-lookup"><span data-stu-id="cf7c9-127">SendFailure</span></span>|<span data-ttu-id="cf7c9-128">Uzak sunucuya komple bir istek gönderilemedi.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-128">A complete request could not be sent to the remote server.</span></span>|  
|<span data-ttu-id="cf7c9-129">Serverprotocolihlaline</span><span class="sxs-lookup"><span data-stu-id="cf7c9-129">ServerProtocolViolation</span></span>|<span data-ttu-id="cf7c9-130">Sunucu yanıtı geçerli bir HTTP yanıtı değildi.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-130">The server response was not a valid HTTP response.</span></span>|  
|<span data-ttu-id="cf7c9-131">Başarılı</span><span class="sxs-lookup"><span data-stu-id="cf7c9-131">Success</span></span>|<span data-ttu-id="cf7c9-132">Hatayla karşılaşılmadı.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-132">No error was encountered.</span></span>|  
|<span data-ttu-id="cf7c9-133">Zaman aşımı</span><span class="sxs-lookup"><span data-stu-id="cf7c9-133">Timeout</span></span>|<span data-ttu-id="cf7c9-134">İstek için zaman aşımı kümesi içinde yanıt alınmadı.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-134">No response was received within the time-out set for the request.</span></span>|  
|<span data-ttu-id="cf7c9-135">TrustFailure hatası</span><span class="sxs-lookup"><span data-stu-id="cf7c9-135">TrustFailure</span></span>|<span data-ttu-id="cf7c9-136">Sunucu sertifikası doğrulanamadı.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-136">A server certificate could not be validated.</span></span>|  
|<span data-ttu-id="cf7c9-137">Messagelengthlimitexceıbaşında</span><span class="sxs-lookup"><span data-stu-id="cf7c9-137">MessageLengthLimitExceeded</span></span>|<span data-ttu-id="cf7c9-138">İstek gönderilirken veya sunucudan yanıt alındığında belirtilen sınırı aşan bir ileti alındı.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-138">A message was received that exceeded the specified limit when sending a request or receiving a response from the server.</span></span>|  
|<span data-ttu-id="cf7c9-139">Beklemede</span><span class="sxs-lookup"><span data-stu-id="cf7c9-139">Pending</span></span>|<span data-ttu-id="cf7c9-140">İç zaman uyumsuz istek bekleniyor.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-140">An internal asynchronous request is pending.</span></span>|  
|<span data-ttu-id="cf7c9-141">PipelineFailure</span><span class="sxs-lookup"><span data-stu-id="cf7c9-141">PipelineFailure</span></span>|<span data-ttu-id="cf7c9-142">Bu değer .NET Framework altyapısını destekler ve doğrudan kodunuzda kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-142">This value supports the .NET Framework infrastructure and is not intended to be used directly in your code.</span></span>|  
|<span data-ttu-id="cf7c9-143">ProxyNameResolutionFailure</span><span class="sxs-lookup"><span data-stu-id="cf7c9-143">ProxyNameResolutionFailure</span></span>|<span data-ttu-id="cf7c9-144">Ad çözümleyici Hizmeti, proxy ana bilgisayar adını çözümleyemedi.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-144">The name resolver service could not resolve the proxy host name.</span></span>|  
|<span data-ttu-id="cf7c9-145">UnknownError</span><span class="sxs-lookup"><span data-stu-id="cf7c9-145">UnknownError</span></span>|<span data-ttu-id="cf7c9-146">Bilinmeyen türde bir özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-146">An exception of unknown type has occurred.</span></span>|  
  
<span data-ttu-id="cf7c9-147">**Status** özelliği **WebExceptionStatus. ProtocolError**olduğunda, sunucudan gelen yanıtı içeren bir **WebResponse** kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-147">When the **Status** property is **WebExceptionStatus.ProtocolError**, a **WebResponse** that contains the response from the server is available.</span></span> <span data-ttu-id="cf7c9-148">Protokol hatasının gerçek kaynağını öğrenmek için bu yanıtı inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-148">You can examine this response to determine the actual source of the protocol error.</span></span>  
  
<span data-ttu-id="cf7c9-149">Aşağıdaki örnek, bir **WebException**nasıl yakalandığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-149">The following example shows how to catch a **WebException**.</span></span>  
  
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
  
<span data-ttu-id="cf7c9-150">Sınıfını kullanan uygulamalar <xref:System.Net.Sockets.Socket> <xref:System.Net.Sockets.SocketException> , Windows yuvasında hata oluştuğunda oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-150">Applications that use the <xref:System.Net.Sockets.Socket> class throw <xref:System.Net.Sockets.SocketException> when errors occur on the Windows socket.</span></span> <span data-ttu-id="cf7c9-151"><xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener> Ve <xref:System.Net.Sockets.UdpClient> sınıfları **yuva** sınıfının üzerine kurulmuştur ve **SocketExceptions** de oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-151">The <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, and <xref:System.Net.Sockets.UdpClient> classes are built on top of the **Socket** class and throw **SocketExceptions** as well.</span></span>  
  
<span data-ttu-id="cf7c9-152">Bir **SocketException** oluşturulduğunda, **SocketException** sınıfı <xref:System.Net.Sockets.SocketException.ErrorCode%2A> özelliği, gerçekleşen son işletim sistemi yuva hatası olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-152">When a **SocketException** is thrown, the **SocketException** class sets the <xref:System.Net.Sockets.SocketException.ErrorCode%2A> property to the last operating system socket error that occurred.</span></span> <span data-ttu-id="cf7c9-153">Yuva hata kodları hakkında daha fazla bilgi için MSDN 'de Winsock 2,0 API hata kodu belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-153">For more information about socket error codes, see the Winsock 2.0 API error code documentation in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf7c9-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf7c9-154">See also</span></span>

- [<span data-ttu-id="cf7c9-155">.NET 'te özel durumları işleme ve atma</span><span class="sxs-lookup"><span data-stu-id="cf7c9-155">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="cf7c9-156">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="cf7c9-156">Requesting Data</span></span>](requesting-data.md)
