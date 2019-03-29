---
title: 'Nasıl yapılır: WebRequest sınıfını kullanarak veri isteme'
ms.date: 03/21/2019
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
ms.openlocfilehash: 1b71327d007e66cc217f6d69e11122c481e5118f
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634043"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a><span data-ttu-id="cea58-102">Nasıl yapılır: WebRequest sınıfını kullanarak veri isteme</span><span class="sxs-lookup"><span data-stu-id="cea58-102">How to: Request data by using the WebRequest class</span></span>
<span data-ttu-id="cea58-103">Aşağıdaki yordamda, bir Web sayfası veya bir dosya gibi bir kaynak sunucudan istemek için adımlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cea58-103">The following procedure describes the steps to request a resource, such as a Web page or a file, from a server.</span></span> <span data-ttu-id="cea58-104">Kaynak URI tarafından tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cea58-104">The resource must be identified by a URI.</span></span>  
  
## <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="cea58-105">Bir konak sunucusundan veri istemek için</span><span class="sxs-lookup"><span data-stu-id="cea58-105">To request data from a host server</span></span>  
  
1.  <span data-ttu-id="cea58-106">Oluşturma bir <xref:System.Net.WebRequest> çağırarak örneği <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> bir kaynağın URI'sini ile.</span><span class="sxs-lookup"><span data-stu-id="cea58-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource.</span></span> <span data-ttu-id="cea58-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="cea58-107">For example:</span></span> 
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/default.html");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/default.html")  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="cea58-108">.NET Framework türetilen protokole özgü sınıfların sağlar <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları ile başlayan bir URI'leri *http:*, *https:*, *ftp:* , ve *dosya:*.</span><span class="sxs-lookup"><span data-stu-id="cea58-108">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>
    <span data-ttu-id="cea58-109">Kümesi ya da okuma protokole özgü özellikleri gerekirse dönüştürmelisiniz, <xref:System.Net.WebRequest> veya <xref:System.Net.WebResponse> protokole özgü nesne türü için nesne.</span><span class="sxs-lookup"><span data-stu-id="cea58-109">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="cea58-110">Daha fazla bilgi için [takılabilir protokoller programlama](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="cea58-110">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span> 
  
2.  <span data-ttu-id="cea58-111">Size gereken tüm özellik değerlerini ayarlayın, `WebRequest` nesne.</span><span class="sxs-lookup"><span data-stu-id="cea58-111">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="cea58-112">Örneğin, kimlik doğrulamasını etkinleştirmek için ayarlanmış <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> örneğine özellik <xref:System.Net.NetworkCredential> sınıfı:</span><span class="sxs-lookup"><span data-stu-id="cea58-112">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
3.  <span data-ttu-id="cea58-113">Çağırarak sunucuya istek göndermek <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cea58-113">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cea58-114">Bu yöntem sunucu yanıtını içeren bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="cea58-114">This method returns an object containing the server's response.</span></span> <span data-ttu-id="cea58-115">Döndürülen <xref:System.Net.WebResponse> nesnenin türü, isteğin URI düzeni tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="cea58-115">The returned <xref:System.Net.WebResponse> object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="cea58-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="cea58-116">For example:</span></span>
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
4.  <span data-ttu-id="cea58-117">Özelliklerini erişebilir, `WebResponse` nesne veya protokole özgü özelliklerini okumak için bir protokole özgü örneğe dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="cea58-117">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span> 

    <span data-ttu-id="cea58-118">Örneğin, erişim HTTP'ye özgü özellikleri için <xref:System.Net.HttpWebResponse>, noktaya yayın, `WebResponse` nesnesini bir `HttpWebResponse` başvuru.</span><span class="sxs-lookup"><span data-stu-id="cea58-118">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an `HttpWebResponse` reference.</span></span> <span data-ttu-id="cea58-119">Aşağıdaki kod örneği, HTTP özgü görüntülenecek gösterilmektedir <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> Yanıtta gönderilen özelliği:</span><span class="sxs-lookup"><span data-stu-id="cea58-119">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  <span data-ttu-id="cea58-120">Sunucu tarafından gönderilen yanıt verilerini içeren akış almak için arama <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cea58-120">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cea58-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="cea58-121">For example:</span></span>  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  <span data-ttu-id="cea58-122">Yanıt nesnesinden verileri okuduktan sonra ya da ile kapatmak <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> yöntemi veya kapanış yanıt akışı ile <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cea58-122">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cea58-123">Yanıt nesnesini ya da akış kapatmayın, uygulamanızın sunucu bağlantılarını dışında çalıştırabilir ve ek istekleri işleyemediğinden haline gelir.</span><span class="sxs-lookup"><span data-stu-id="cea58-123">If you don't close either the response object or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="cea58-124">Çünkü `WebResponse.Close` yöntem çağrılarını `Stream.Close` yanıtı kapatır, çağrı gerekli değildir `Close` nesnelerde yanıt ve akış bunu yaparsanız bu nedenle zararlı olmasa da.</span><span class="sxs-lookup"><span data-stu-id="cea58-124">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="cea58-125">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="cea58-125">For example:</span></span>
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="cea58-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="cea58-126">Example</span></span>  

<span data-ttu-id="cea58-127">Aşağıdaki kod örneği, bir web sunucusu için bir istek oluşturun ve kendi yanıt verileri okumak gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="cea58-127">The following code example shows how to create a request to a web server and read the data in its response:</span></span>  
  
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
            // Open the stream by using a StreamReader for easy access.  
            StreamReader reader = new StreamReader(dataStream);  

            // Read the content.  
            string responseFromServer = reader.ReadToEnd();  
            // Display the content.  
            Console.WriteLine(responseFromServer);  

            // Clean up the response.  
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
            ' Open the stream by using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  

            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  

            ' Clean up the response.  
            reader.Close()  
            response.Close() 

        End Sub   

    End Class  
 
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="cea58-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cea58-128">See also</span></span>
- [<span data-ttu-id="cea58-129">İnternet istekleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="cea58-129">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="cea58-130">Ağda akışları kullanma</span><span class="sxs-lookup"><span data-stu-id="cea58-130">Using Streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="cea58-131">İnternet'e bir proxy üzerinden erişme</span><span class="sxs-lookup"><span data-stu-id="cea58-131">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="cea58-132">Veri isteme</span><span class="sxs-lookup"><span data-stu-id="cea58-132">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="cea58-133">Nasıl yapılır: WebRequest sınıfını kullanarak veri gönderme</span><span class="sxs-lookup"><span data-stu-id="cea58-133">How to: Send data by using the WebRequest class</span></span>](how-to-send-data-using-the-webrequest-class.md)
