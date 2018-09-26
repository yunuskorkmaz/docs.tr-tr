---
title: 'Nasıl yapılır: WebRequest sınıfını kullanarak veri isteme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- downloading Internet resources, steps
- requesting data from Internet, steps
- WebRequest class, receiving data
- receiving data, using WebRequest class
- Internet, requesting data
ms.assetid: 368b8d0f-dc5e-4469-a8b8-b2adbf5dd800
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 8928ce8790f58b6920c16cbfd9fc8d9aa6644a44
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47197831"
---
# <a name="how-to-request-data-using-the-webrequest-class"></a><span data-ttu-id="2625e-102">Nasıl yapılır: WebRequest sınıfını kullanarak veri isteme</span><span class="sxs-lookup"><span data-stu-id="2625e-102">How to: Request Data Using the WebRequest Class</span></span>
<span data-ttu-id="2625e-103">Aşağıdaki yordamda, bir kaynak, örneğin, bir sunucudan istemek için kullanılan adımlarla, bir Web sayfası veya dosya açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2625e-103">The following procedure describes the steps used to request a resource from a server, for example, a Web page or file.</span></span> <span data-ttu-id="2625e-104">Kaynak URI tarafından tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2625e-104">The resource must be identified by a URI.</span></span>  
  
### <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="2625e-105">Bir konak sunucusundan veri istemek için</span><span class="sxs-lookup"><span data-stu-id="2625e-105">To request data from a host server</span></span>  
  
1.  <span data-ttu-id="2625e-106">Oluşturma bir <xref:System.Net.WebRequest> çağırarak örneği <xref:System.Net.WebRequest.Create%2A> kaynağın URI'sini ile.</span><span class="sxs-lookup"><span data-stu-id="2625e-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A> with the URI of the resource.</span></span>  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="2625e-107">.NET Framework türetilen protokole özgü sınıfların sağlar **WebRequest** ve **WebResponse** ile başlayan bir URI'leri için "http:", "https:''," ftp: ", ve" dosya: ".</span><span class="sxs-lookup"><span data-stu-id="2625e-107">The .NET Framework provides protocol-specific classes derived from **WebRequest** and **WebResponse** for URIs that begin with "http:", "https:'', "ftp:", and "file:".</span></span> <span data-ttu-id="2625e-108">Diğer protokoller kullanarak kaynaklara erişmeye öğesinden türetilen protokole özgü sınıfların uygulamalıdır **WebRequest** ve **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="2625e-108">To access resources using other protocols, you must implement protocol-specific classes that derive from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="2625e-109">Daha fazla bilgi için [takılabilir protokoller programlama](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span><span class="sxs-lookup"><span data-stu-id="2625e-109">For more information, see [Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span></span>  
  
2.  <span data-ttu-id="2625e-110">Size gereken tüm özellik değerlerini ayarlamak **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="2625e-110">Set any property values that you need in the **WebRequest**.</span></span> <span data-ttu-id="2625e-111">Örneğin, kimlik doğrulamasını etkinleştirmek için ayarlanmış **kimlik bilgilerini** örneğine özellik <xref:System.Net.NetworkCredential> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2625e-111">For example, to enable authentication, set the **Credentials** property to an instance of the <xref:System.Net.NetworkCredential> class.</span></span>  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     <span data-ttu-id="2625e-112">Çoğu durumda **WebRequest** sınıfı, veri almak yeterli.</span><span class="sxs-lookup"><span data-stu-id="2625e-112">In most cases, the **WebRequest** class is sufficient to receive data.</span></span> <span data-ttu-id="2625e-113">Ancak, protokole özgü özelliklerini ayarlamak gerekiyorsa dönüştürmelisiniz **WebRequest** protokole özgü türü.</span><span class="sxs-lookup"><span data-stu-id="2625e-113">However, if you need to set protocol-specific properties, you must cast the **WebRequest** to the protocol-specific type.</span></span> <span data-ttu-id="2625e-114">Örneğin, erişim HTTP'ye özgü özellikleri için <xref:System.Net.HttpWebRequest>, noktaya yayın **WebRequest** için bir **HttpWebRequest** başvuru.</span><span class="sxs-lookup"><span data-stu-id="2625e-114">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebRequest>, cast the **WebRequest** to an **HttpWebRequest** reference.</span></span> <span data-ttu-id="2625e-115">Aşağıdaki kod örneği, HTTP özgü ayarlanacak gösterilmektedir <xref:System.Net.HttpWebRequest.UserAgent%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="2625e-115">The following code example shows how to set the HTTP-specific <xref:System.Net.HttpWebRequest.UserAgent%2A> property.</span></span>  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  <span data-ttu-id="2625e-116">Sunucuya istek göndermek için arama <xref:System.Net.HttpWebRequest.GetResponse%2A>.</span><span class="sxs-lookup"><span data-stu-id="2625e-116">To send the request to the server, call <xref:System.Net.HttpWebRequest.GetResponse%2A>.</span></span> <span data-ttu-id="2625e-117">Gerçek türü döndürülen **WebResponse** nesne, istenen URI'nin şeması tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="2625e-117">The actual type of the returned **WebResponse** object is determined by the scheme of the requested URI.</span></span>  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="2625e-118">İle tamamladıktan sonra bir <xref:System.Net.WebResponse> nesne kapatmalısınız bunu çağırarak <xref:System.Net.WebResponse.Close%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2625e-118">After you are finished with a <xref:System.Net.WebResponse> object, you must close it by calling the <xref:System.Net.WebResponse.Close%2A> method.</span></span> <span data-ttu-id="2625e-119">Yanıt nesneden yanıt akışına edindiğiniz, alternatif olarak, akış çağırarak kapatabilirsiniz <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2625e-119">Alternatively, if you have gotten the response stream from the response object, you can close the stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2625e-120">Yanıt ya da akış kapatmazsanız uygulamanız bağlantılar dışında sunucuya çalıştırın ve ek istekleri işleyemediğinden haline gelir.</span><span class="sxs-lookup"><span data-stu-id="2625e-120">If you do not close either the response or the stream, your application can run out of connections to the server and become unable to process additional requests.</span></span>  
  
4.  <span data-ttu-id="2625e-121">Özelliklerini erişebileceğiniz **WebResponse** veya dönüştürme **WebResponse** protokole özgü özelliklerini okumak için bir protokole özgü örneğine.</span><span class="sxs-lookup"><span data-stu-id="2625e-121">You can access the properties of the **WebResponse** or cast the **WebResponse** to a protocol-specific instance to read protocol-specific properties.</span></span> <span data-ttu-id="2625e-122">Örneğin, erişim HTTP'ye özgü özellikleri için <xref:System.Net.HttpWebResponse>, noktaya yayın **WebResponse** için bir **HttpWebResponse** başvuru.</span><span class="sxs-lookup"><span data-stu-id="2625e-122">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast the **WebResponse** to a **HttpWebResponse** reference.</span></span> <span data-ttu-id="2625e-123">Aşağıdaki kod örneği, yanıtta gönderilen durum bilgilerini görüntülemek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2625e-123">The following code example shows how to display the status information sent with a response.</span></span>  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  <span data-ttu-id="2625e-124">Sunucu tarafından gönderilen yanıt verilerini içeren akış almak için kullanın <xref:System.Net.HttpWebResponse.GetResponseStream%2A> yöntemi **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="2625e-124">To get the stream containing response data sent by the server, use the <xref:System.Net.HttpWebResponse.GetResponseStream%2A> method of the **WebResponse**.</span></span>  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  <span data-ttu-id="2625e-125">Yanıttan verileri okuduktan sonra ya da yanıt akışı kullanılarak kapatmalısınız **Stream.Close** yöntemi veya yanıtı kullanma Kapat **WebResponse.Close** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2625e-125">After reading the data from the response, you must either close the response stream using the **Stream.Close** method or close the response using the **WebResponse.Close** method.</span></span> <span data-ttu-id="2625e-126">Bu çağrı gerekli değildir **Kapat** yanıt akışında yöntemi ve **WebResponse**, ancak bunu yaparsanız bu nedenle zararlı.</span><span class="sxs-lookup"><span data-stu-id="2625e-126">It is not necessary to call the **Close** method on both the response stream and the **WebResponse**, but doing so is not harmful.</span></span> <span data-ttu-id="2625e-127">**WebResponse.Close** çağrıları **Stream.Close** yanıt kapatırken.</span><span class="sxs-lookup"><span data-stu-id="2625e-127">**WebResponse.Close** calls **Stream.Close** when closing the response.</span></span>  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="2625e-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="2625e-128">Example</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestGetExample  
    {  
        public static void Main()  
        {  
            // Create a request for the URL.   
            WebRequest request = WebRequest.Create(  
              "http://www.contoso.com/default.html");  
            // If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials;  
            // Get the response.  
            WebResponse response = request.GetResponse();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            Stream dataStream = response.GetResponseStream();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader(dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd();  
            // Display the content.  
            Console.WriteLine(responseFromServer);  
            // Clean up the streams and the response.  
            reader.Close();  
            response.Close();  
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
    Public Class WebRequestGetExample  
  
        Public Shared Sub Main()  
            ' Create a request for the URL.   
            Dim request As WebRequest = _  
              WebRequest.Create("http://www.contoso.com/default.html")  
            ' If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials  
            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
            ' Get the stream containing content returned by the server.  
            Dim dataStream As Stream = response.GetResponseStream()  
            ' Open the stream using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  
            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  
            ' Clean up the streams and the response.  
            reader.Close()  
            response.Close()  
        End Sub   
    End Class   
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="2625e-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2625e-129">See Also</span></span>  
 [<span data-ttu-id="2625e-130">İnternet İstekleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2625e-130">Creating Internet Requests</span></span>](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [<span data-ttu-id="2625e-131">Ağda Akışları Kullanma</span><span class="sxs-lookup"><span data-stu-id="2625e-131">Using Streams on the Network</span></span>](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [<span data-ttu-id="2625e-132">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="2625e-132">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="2625e-133">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="2625e-133">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)  
 [<span data-ttu-id="2625e-134">Nasıl yapılır: WebRequest Sınıfını Kullanarak Veri Gönderme</span><span class="sxs-lookup"><span data-stu-id="2625e-134">How to: Send Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-send-data-using-the-webrequest-class.md)
