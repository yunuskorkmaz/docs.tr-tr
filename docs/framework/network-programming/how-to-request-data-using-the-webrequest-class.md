---
title: 'Nasıl yapılır: İstek WebRequest sınıfı kullanarak verileri'
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
manager: markl
ms.openlocfilehash: e02ad4772d3ba84a2735a2e146a9979862d75989
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397721"
---
# <a name="how-to-request-data-using-the-webrequest-class"></a><span data-ttu-id="9658f-102">Nasıl yapılır: İstek WebRequest sınıfı kullanarak verileri</span><span class="sxs-lookup"><span data-stu-id="9658f-102">How to: Request Data Using the WebRequest Class</span></span>
<span data-ttu-id="9658f-103">Aşağıdaki yordam, örneğin, bir sunucudan bir kaynak istemek için kullanılan adımlar, bir Web sayfasına veya dosya açıklar.</span><span class="sxs-lookup"><span data-stu-id="9658f-103">The following procedure describes the steps used to request a resource from a server, for example, a Web page or file.</span></span> <span data-ttu-id="9658f-104">Kaynak bir URI tarafından tanımlanan gerekir.</span><span class="sxs-lookup"><span data-stu-id="9658f-104">The resource must be identified by a URI.</span></span>  
  
### <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="9658f-105">Bir ana bilgisayar sunucusundan veri istemek için</span><span class="sxs-lookup"><span data-stu-id="9658f-105">To request data from a host server</span></span>  
  
1.  <span data-ttu-id="9658f-106">Oluşturma bir <xref:System.Net.WebRequest> çağırarak örneği <xref:System.Net.WebRequest.Create%2A> kaynak URI'si ile.</span><span class="sxs-lookup"><span data-stu-id="9658f-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A> with the URI of the resource.</span></span>  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="9658f-107">.NET Framework türetilmiş protokole özgü sınıflar sağlar **WebRequest** ve **WebResponse** ile başlayan URI için "http:", "https:''," ftp: ", ve" dosya: ".</span><span class="sxs-lookup"><span data-stu-id="9658f-107">The .NET Framework provides protocol-specific classes derived from **WebRequest** and **WebResponse** for URIs that begin with "http:", "https:'', "ftp:", and "file:".</span></span> <span data-ttu-id="9658f-108">Diğer protokolleri kullanan kaynaklara erişmek için öğesinden türetilen protokole özgü sınıflar uygulamalıdır **WebRequest** ve **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="9658f-108">To access resources using other protocols, you must implement protocol-specific classes that derive from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="9658f-109">Daha fazla bilgi için bkz: [programlama Takılabilir Protokol](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span><span class="sxs-lookup"><span data-stu-id="9658f-109">For more information, see [Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span></span>  
  
2.  <span data-ttu-id="9658f-110">Gereksinim duyduğunuz tüm özellik değerlerini ayarlar **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="9658f-110">Set any property values that you need in the **WebRequest**.</span></span> <span data-ttu-id="9658f-111">Örneğin, kimlik doğrulamasını etkinleştirmek için ayarlar **kimlik bilgileri** örneği özelliğine <xref:System.Net.NetworkCredential> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9658f-111">For example, to enable authentication, set the **Credentials** property to an instance of the <xref:System.Net.NetworkCredential> class.</span></span>  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     <span data-ttu-id="9658f-112">Çoğu durumda, **WebRequest** sınıftır verileri almak yeterli.</span><span class="sxs-lookup"><span data-stu-id="9658f-112">In most cases, the **WebRequest** class is sufficient to receive data.</span></span> <span data-ttu-id="9658f-113">Protokole özgü özelliklerini ayarlamak ihtiyacınız varsa, ancak atamalısınız **WebRequest** protokole özgü türü.</span><span class="sxs-lookup"><span data-stu-id="9658f-113">However, if you need to set protocol-specific properties, you must cast the **WebRequest** to the protocol-specific type.</span></span> <span data-ttu-id="9658f-114">Örneğin, erişim HTTP özgü özellikleri için <xref:System.Net.HttpWebRequest>, noktaya yayın **WebRequest** için bir **HttpWebRequest** başvuru.</span><span class="sxs-lookup"><span data-stu-id="9658f-114">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebRequest>, cast the **WebRequest** to an **HttpWebRequest** reference.</span></span> <span data-ttu-id="9658f-115">Aşağıdaki kod örneğinde HTTP özgü ayarlanacağı gösterilmiştir <xref:System.Net.HttpWebRequest.UserAgent%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="9658f-115">The following code example shows how to set the HTTP-specific <xref:System.Net.HttpWebRequest.UserAgent%2A> property.</span></span>  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  <span data-ttu-id="9658f-116">Sunucuya istek göndermek için çağrı <xref:System.Net.HttpWebRequest.GetResponse%2A>.</span><span class="sxs-lookup"><span data-stu-id="9658f-116">To send the request to the server, call <xref:System.Net.HttpWebRequest.GetResponse%2A>.</span></span> <span data-ttu-id="9658f-117">Döndürülen gerçek türünü **WebResponse** nesne, istenen URI düzeni tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="9658f-117">The actual type of the returned **WebResponse** object is determined by the scheme of the requested URI.</span></span>  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="9658f-118">İle tamamladıktan sonra bir <xref:System.Net.WebResponse> nesne kapatmalısınız onu çağırarak <xref:System.Net.WebResponse.Close%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9658f-118">After you are finished with a <xref:System.Net.WebResponse> object, you must close it by calling the <xref:System.Net.WebResponse.Close%2A> method.</span></span> <span data-ttu-id="9658f-119">Yanıt akışı yanıt nesnesinden getirildiğini, alternatif olarak, akış çağırarak kapatabilirsiniz <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9658f-119">Alternatively, if you have gotten the response stream from the response object, you can close the stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9658f-120">Yanıt veya akış kapatmazsanız uygulamanızı sunucuya bağlantıları dışında çalıştırın ve ek istekleri işleyemiyor haline gelir.</span><span class="sxs-lookup"><span data-stu-id="9658f-120">If you do not close either the response or the stream, your application can run out of connections to the server and become unable to process additional requests.</span></span>  
  
4.  <span data-ttu-id="9658f-121">Özelliklerini erişebilirsiniz **WebResponse** veya cast **WebResponse** bir protokole özgü örneğine protokole özgü özellikleri okunamıyor.</span><span class="sxs-lookup"><span data-stu-id="9658f-121">You can access the properties of the **WebResponse** or cast the **WebResponse** to a protocol-specific instance to read protocol-specific properties.</span></span> <span data-ttu-id="9658f-122">Örneğin, erişim HTTP özgü özellikleri için <xref:System.Net.HttpWebResponse>, noktaya yayın **WebResponse** için bir **HttpWebResponse** başvuru.</span><span class="sxs-lookup"><span data-stu-id="9658f-122">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast the **WebResponse** to a **HttpWebResponse** reference.</span></span> <span data-ttu-id="9658f-123">Aşağıdaki kod örneği ile bir yanıt gönderdi durum bilgilerini görüntülemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="9658f-123">The following code example shows how to display the status information sent with a response.</span></span>  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  <span data-ttu-id="9658f-124">Sunucu tarafından gönderilen yanıtı verilerini içeren akışı almak için <xref:System.Net.HttpWebResponse.GetResponseStream%2A> yöntemi **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="9658f-124">To get the stream containing response data sent by the server, use the <xref:System.Net.HttpWebResponse.GetResponseStream%2A> method of the **WebResponse**.</span></span>  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  <span data-ttu-id="9658f-125">Veri gelen yanıt okunduktan sonra ya da yanıt akışı kullanarak kapatmanız gerekir **Stream.Close** yöntemi veya yanıt kullanarak Kapat **WebResponse.Close** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9658f-125">After reading the data from the response, you must either close the response stream using the **Stream.Close** method or close the response using the **WebResponse.Close** method.</span></span> <span data-ttu-id="9658f-126">Bu çağrı gerekli değildir **Kapat** yanıt akışına yöntemi ve **WebResponse**, ancak bunun nedenle zararlı.</span><span class="sxs-lookup"><span data-stu-id="9658f-126">It is not necessary to call the **Close** method on both the response stream and the **WebResponse**, but doing so is not harmful.</span></span> <span data-ttu-id="9658f-127">**WebResponse.Close** çağrıları **Stream.Close** yanıt kapatırken.</span><span class="sxs-lookup"><span data-stu-id="9658f-127">**WebResponse.Close** calls **Stream.Close** when closing the response.</span></span>  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="9658f-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="9658f-128">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9658f-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9658f-129">See Also</span></span>  
 [<span data-ttu-id="9658f-130">İnternet İstekleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9658f-130">Creating Internet Requests</span></span>](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [<span data-ttu-id="9658f-131">Ağda Akışları Kullanma</span><span class="sxs-lookup"><span data-stu-id="9658f-131">Using Streams on the Network</span></span>](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [<span data-ttu-id="9658f-132">Ara Sunucu Üzerinden İnternet Erişimi</span><span class="sxs-lookup"><span data-stu-id="9658f-132">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="9658f-133">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="9658f-133">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)  
 [<span data-ttu-id="9658f-134">Nasıl yapılır: WebRequest Sınıfını Kullanarak Veri Gönderme</span><span class="sxs-lookup"><span data-stu-id="9658f-134">How to: Send Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-send-data-using-the-webrequest-class.md)
