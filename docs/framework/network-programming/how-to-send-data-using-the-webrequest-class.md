---
title: 'Nasıl yapılır: WebRequest sınıfını kullanarak veri gönderme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: dac372ce4f9da99b91b6f8d140d69ce9f1238f30
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562910"
---
# <a name="how-to-send-data-using-the-webrequest-class"></a><span data-ttu-id="043ac-102">Nasıl yapılır: WebRequest sınıfını kullanarak veri gönderme</span><span class="sxs-lookup"><span data-stu-id="043ac-102">How to: Send Data Using the WebRequest Class</span></span>
<span data-ttu-id="043ac-103">Aşağıdaki yordam bir sunucuya veri göndermek için kullanılan adımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="043ac-103">The following procedure describes the steps used to send data to a server.</span></span> <span data-ttu-id="043ac-104">Bu yordam, genellikle bir Web sayfasında veri göndermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="043ac-104">This procedure is commonly used to post data to a Web page.</span></span>  
  
### <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="043ac-105">Bir konak sunucusuna veri göndermek için</span><span class="sxs-lookup"><span data-stu-id="043ac-105">To send data to a host server</span></span>  
  
1.  <span data-ttu-id="043ac-106">Oluşturma bir <xref:System.Net.WebRequest> çağırarak örneği <xref:System.Net.WebRequest.Create%2A> verileri, örneğin kabul kaynak, bir komut dosyası veya ASP.NET sayfası URI'yı içeren.</span><span class="sxs-lookup"><span data-stu-id="043ac-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A> with the URI of the resource that accepts data, for example, a script or ASP.NET page.</span></span>  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="043ac-107">.NET Framework türetilen protokole özgü sınıfların sağlar **WebRequest** ve **WebResponse** ile başlayan bir URI'leri için "http:", "https:''," ftp: ", ve" dosya: ".</span><span class="sxs-lookup"><span data-stu-id="043ac-107">The .NET Framework provides protocol-specific classes derived from **WebRequest** and **WebResponse** for URIs that begin with "http:", "https:'', "ftp:", and "file:".</span></span> <span data-ttu-id="043ac-108">Diğer protokoller kullanarak kaynaklara erişmeye öğesinden türetilen protokole özgü sınıfların uygulamalıdır **WebRequest** ve **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="043ac-108">To access resources using other protocols, you must implement protocol-specific classes that derive from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="043ac-109">Daha fazla bilgi için [takılabilir protokoller programlama](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span><span class="sxs-lookup"><span data-stu-id="043ac-109">For more information, see [Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span></span>  
  
2.  <span data-ttu-id="043ac-110">Size gereken tüm özellik değerlerini ayarlamak **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="043ac-110">Set any property values that you need in the **WebRequest**.</span></span> <span data-ttu-id="043ac-111">Örneğin, kimlik doğrulamasını etkinleştirmek için ayarlanmış **kimlik bilgilerini** örneğine özellik <xref:System.Net.NetworkCredential> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="043ac-111">For example, to enable authentication, set the **Credentials** property to an instance of the <xref:System.Net.NetworkCredential> class.</span></span>  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     <span data-ttu-id="043ac-112">Çoğu durumda **WebRequest** örnek kendi veri göndermek yeterli.</span><span class="sxs-lookup"><span data-stu-id="043ac-112">In most cases, the **WebRequest** instance itself is sufficient to send data.</span></span> <span data-ttu-id="043ac-113">Ancak, protokole özgü özelliklerini ayarlamak gerekiyorsa dönüştürmelisiniz **WebRequest** protokole özgü türü.</span><span class="sxs-lookup"><span data-stu-id="043ac-113">However, if you need to set protocol-specific properties, you must cast the **WebRequest** to the protocol-specific type.</span></span> <span data-ttu-id="043ac-114">Örneğin, erişim HTTP'ye özgü özellikleri için <xref:System.Net.HttpWebRequest>, noktaya yayın **WebRequest** için bir **HttpWebRequest** başvuru.</span><span class="sxs-lookup"><span data-stu-id="043ac-114">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebRequest>, cast the **WebRequest** to an **HttpWebRequest** reference.</span></span> <span data-ttu-id="043ac-115">Aşağıdaki kod örneği, HTTP özgü ayarlanacak gösterilmektedir <xref:System.Net.HttpWebRequest.UserAgent%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="043ac-115">The following code example shows how to set the HTTP-specific <xref:System.Net.HttpWebRequest.UserAgent%2A> property.</span></span>  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  <span data-ttu-id="043ac-116">Veri ile HTTP gibi bir istek gönderilmesine izin veren bir protokol yöntemini belirtin **POST** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="043ac-116">Specify a protocol method that permits data to be sent with a request, such as the HTTP **POST** method.</span></span>  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4.  <span data-ttu-id="043ac-117">Ayarlama **ContentLength** özelliği.</span><span class="sxs-lookup"><span data-stu-id="043ac-117">Set the **ContentLength** property.</span></span>  
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5.  <span data-ttu-id="043ac-118">Ayarlama **ContentType** özelliğini uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="043ac-118">Set the **ContentType** property to an appropriate value.</span></span>  
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  <span data-ttu-id="043ac-119">Get ayrı tutma çağırarak verileri istek akışı <xref:System.Net.WebRequest.GetRequestStream%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="043ac-119">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span>  
  
    ```csharp  
    Stream dataStream = request.GetRequestStream ();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream ()  
    ```  
  
7.  <span data-ttu-id="043ac-120">Veri yazılan <xref:System.IO.Stream> bu yöntem tarafından döndürülen nesne.</span><span class="sxs-lookup"><span data-stu-id="043ac-120">Write the data to the <xref:System.IO.Stream> object returned by this method.</span></span>  
  
    ```csharp  
    dataStream.Write (byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write (byteArray, 0, byteArray.Length)  
    ```  
  
8.  <span data-ttu-id="043ac-121">İstek akışı çağırarak kapatmak **Stream.Close** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="043ac-121">Close the request stream by calling the **Stream.Close** method.</span></span>  
  
    ```csharp  
    dataStream.Close ();  
    ```  
  
    ```vb  
    dataStream.Close ()  
    ```  
  
9. <span data-ttu-id="043ac-122">Çağırarak sunucuya istek göndermek <xref:System.Net.WebRequest.GetResponse%2A>.</span><span class="sxs-lookup"><span data-stu-id="043ac-122">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A>.</span></span> <span data-ttu-id="043ac-123">Bu yöntem sunucu yanıtını içeren bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="043ac-123">This method returns an object containing the server's response.</span></span> <span data-ttu-id="043ac-124">Döndürülen <xref:System.Net.WebResponse> nesnenin türü, isteğin URI düzeni tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="043ac-124">The returned <xref:System.Net.WebResponse> object's type is determined by the scheme of the request's URI.</span></span>  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="043ac-125">İle tamamladıktan sonra bir <xref:System.Net.WebResponse> nesne kapatmalısınız bunu çağırarak <xref:System.Net.WebResponse.Close%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="043ac-125">After you are finished with a <xref:System.Net.WebResponse> object, you must close it by calling the <xref:System.Net.WebResponse.Close%2A> method.</span></span> <span data-ttu-id="043ac-126">Yanıt nesneden yanıt akışına edindiğiniz, alternatif olarak, akış çağırarak kapatabilirsiniz <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="043ac-126">Alternatively, if you have gotten the response stream from the response object, you can close the stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="043ac-127">Yanıt veya akış kapatmazsanız uygulamanız bağlantılar dışında sunucuya çalıştırın ve ek istekleri işleyemediğinden haline gelir.</span><span class="sxs-lookup"><span data-stu-id="043ac-127">If you do not close the response or the stream, your application can run out of connections to the server and become unable to process additional requests.</span></span>  
  
10. <span data-ttu-id="043ac-128">Özelliklerini erişebileceğiniz **WebResponse** veya dönüştürme **WebResponse** protokole özgü özelliklerini okumak için bir protokole özgü örneğine.</span><span class="sxs-lookup"><span data-stu-id="043ac-128">You can access the properties of the **WebResponse** or cast the **WebResponse** to a protocol-specific instance to read protocol-specific properties.</span></span> <span data-ttu-id="043ac-129">Örneğin, erişim HTTP'ye özgü özellikleri için <xref:System.Net.HttpWebResponse>, noktaya yayın **WebResponse** için bir **HttpWebResponse** başvuru.</span><span class="sxs-lookup"><span data-stu-id="043ac-129">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast the **WebResponse** to an **HttpWebResponse** reference.</span></span>  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. <span data-ttu-id="043ac-130">Sunucu tarafından gönderilen yanıt verilerini içeren akış almak için arama <xref:System.Net.WebResponse.GetResponseStream%2A> yöntemi **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="043ac-130">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A> method of the **WebResponse**.</span></span>  
  
    ```csharp  
    Stream data = response.GetResponseStream;  
    ```  
  
    ```vb  
    Dim data As Stream = response.GetResponseStream  
    ```  
  
12. <span data-ttu-id="043ac-131">Yanıttan verileri okuduktan sonra ya da yanıt akışı kullanılarak kapatmalısınız **Stream.Close** yöntemi veya yanıtı kullanma Kapat **WebResponse.Close** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="043ac-131">After reading the data from the response, you must either close the response stream using the **Stream.Close** method or close the response using the **WebResponse.Close** method.</span></span> <span data-ttu-id="043ac-132">Bu çağrı gerekli değildir **Kapat** yanıt akışında yöntemi ve **WebResponse**, ancak bunu yaparsanız bu nedenle zararlı.</span><span class="sxs-lookup"><span data-stu-id="043ac-132">It is not necessary to call the **Close** method on both the response stream and the **WebResponse**, but doing so is not harmful.</span></span>  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="043ac-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="043ac-133">Example</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestPostExample  
    {  
        public static void Main ()  
        {  
            // Create a request using a URL that can receive a post.   
            WebRequest request = WebRequest.Create ("http://www.contoso.com/PostAccepter.aspx ");  
            // Set the Method property of the request to POST.  
            request.Method = "POST";  
            // Create POST data and convert it to a byte array.  
            string postData = "This is a test that posts this string to a Web server.";  
            byte[] byteArray = Encoding.UTF8.GetBytes (postData);  
            // Set the ContentType property of the WebRequest.  
            request.ContentType = "application/x-www-form-urlencoded";  
            // Set the ContentLength property of the WebRequest.  
            request.ContentLength = byteArray.Length;  
            // Get the request stream.  
            Stream dataStream = request.GetRequestStream ();  
            // Write the data to the request stream.  
            dataStream.Write (byteArray, 0, byteArray.Length);  
            // Close the Stream object.  
            dataStream.Close ();  
            // Get the response.  
            WebResponse response = request.GetResponse ();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream ();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader (dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd ();  
            // Display the content.  
            Console.WriteLine (responseFromServer);  
            // Clean up the streams.  
            reader.Close ();  
            dataStream.Close ();  
            response.Close ();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Net  
Imports System.Text  
Namespace Examples.System.Net  
    Public Class WebRequestPostExample  
  
        Public Shared Sub Main()  
            ' Create a request using a URL that can receive a post.   
            Dim request As WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx ")  
            ' Set the Method property of the request to POST.  
            request.Method = "POST"  
            ' Create POST data and convert it to a byte array.  
            Dim postData As String = "This is a test that posts this string to a Web server."  
            Dim byteArray As Byte() = Encoding.UTF8.GetBytes(postData)  
            ' Set the ContentType property of the WebRequest.  
            request.ContentType = "application/x-www-form-urlencoded"  
            ' Set the ContentLength property of the WebRequest.  
            request.ContentLength = byteArray.Length  
            ' Get the request stream.  
            Dim dataStream As Stream = request.GetRequestStream()  
            ' Write the data to the request stream.  
            dataStream.Write(byteArray, 0, byteArray.Length)  
            ' Close the Stream object.  
            dataStream.Close()  
            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
            ' Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream()  
            ' Open the stream using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  
            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  
            ' Clean up the streams.  
            reader.Close()  
            dataStream.Close()  
            response.Close()  
        End Sub  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="043ac-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="043ac-134">See also</span></span>
- [<span data-ttu-id="043ac-135">İnternet İstekleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="043ac-135">Creating Internet Requests</span></span>](../../../docs/framework/network-programming/creating-internet-requests.md)
- [<span data-ttu-id="043ac-136">Ağda Akışları Kullanma</span><span class="sxs-lookup"><span data-stu-id="043ac-136">Using Streams on the Network</span></span>](../../../docs/framework/network-programming/using-streams-on-the-network.md)
- [<span data-ttu-id="043ac-137">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="043ac-137">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="043ac-138">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="043ac-138">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
- [<span data-ttu-id="043ac-139">Nasıl yapılır: WebRequest sınıfını kullanarak veri isteme</span><span class="sxs-lookup"><span data-stu-id="043ac-139">How to: Request Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)
