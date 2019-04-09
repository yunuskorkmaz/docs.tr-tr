---
title: 'Nasıl yapılır: WebRequest sınıfını kullanarak veri gönderme'
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 456dbdab3070e88fe0bc6572c998ce54e3c19c00
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166962"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a><span data-ttu-id="58bdf-102">Nasıl yapılır: WebRequest sınıfını kullanarak veri gönderme</span><span class="sxs-lookup"><span data-stu-id="58bdf-102">How to: Send data by using the WebRequest class</span></span>
<span data-ttu-id="58bdf-103">Aşağıdaki yordam bir sunucuya veri göndermek için gereken adımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="58bdf-103">The following procedure describes the steps to send data to a server.</span></span> <span data-ttu-id="58bdf-104">Bu yordam, genellikle bir Web sayfasında veri göndermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58bdf-104">This procedure is commonly used to post data to a Web page.</span></span> 
  
## <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="58bdf-105">Bir konak sunucusuna veri göndermek için</span><span class="sxs-lookup"><span data-stu-id="58bdf-105">To send data to a host server</span></span>  
  
1.  <span data-ttu-id="58bdf-106">Oluşturma bir <xref:System.Net.WebRequest> çağırarak örneği <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> bir betik veya ASP.NET sayfası gibi bir kaynağın URI'sini ile verileri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="58bdf-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource, such as a script or ASP.NET page, that accepts data.</span></span> <span data-ttu-id="58bdf-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="58bdf-107">For example:</span></span> 
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="58bdf-108">.NET Framework türetilen protokole özgü sınıfların sağlar <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları ile başlayan bir URI'leri *http:*, *https:*, *ftp:* , ve *dosya:*.</span><span class="sxs-lookup"><span data-stu-id="58bdf-108">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>
    <span data-ttu-id="58bdf-109">Kümesi ya da okuma protokole özgü özellikleri gerekirse dönüştürmelisiniz, <xref:System.Net.WebRequest> veya <xref:System.Net.WebResponse> protokole özgü nesne türü için nesne.</span><span class="sxs-lookup"><span data-stu-id="58bdf-109">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="58bdf-110">Daha fazla bilgi için [takılabilir protokoller programlama](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="58bdf-110">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span> 
  
2.  <span data-ttu-id="58bdf-111">Size gereken tüm özellik değerlerini ayarlayın, `WebRequest` nesne.</span><span class="sxs-lookup"><span data-stu-id="58bdf-111">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="58bdf-112">Örneğin, kimlik doğrulamasını etkinleştirmek için ayarlanmış <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> örneğine özellik <xref:System.Net.NetworkCredential> sınıfı:</span><span class="sxs-lookup"><span data-stu-id="58bdf-112">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
3.  <span data-ttu-id="58bdf-113">Veri ile HTTP gibi bir istek gönderilmesine izin veren bir protokol yöntemini belirtin `POST` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="58bdf-113">Specify a protocol method that permits data to be sent with a request, such as the HTTP `POST` method:</span></span>  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4.  <span data-ttu-id="58bdf-114">Ayarlama <xref:System.Web.HttpRequest.ContentLength> özelliğini isteğinize dahil bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="58bdf-114">Set the <xref:System.Web.HttpRequest.ContentLength> property to the number of bytes you're including with your request.</span></span> <span data-ttu-id="58bdf-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="58bdf-115">For example:</span></span> 
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5.  <span data-ttu-id="58bdf-116">Ayarlama <xref:System.Web.HttpRequest.ContentType> özelliğini uygun bir değer.</span><span class="sxs-lookup"><span data-stu-id="58bdf-116">Set the <xref:System.Web.HttpRequest.ContentType> property to an appropriate value.</span></span> <span data-ttu-id="58bdf-117">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="58bdf-117">For example:</span></span>
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  <span data-ttu-id="58bdf-118">Get ayrı tutma çağırarak verileri istek akışı <xref:System.Net.WebRequest.GetRequestStream%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="58bdf-118">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span> <span data-ttu-id="58bdf-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="58bdf-119">For example:</span></span>
  
    ```csharp  
    Stream dataStream = request.GetRequestStream();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream()  
    ```  
  
7.  <span data-ttu-id="58bdf-120">Veri yazılan <xref:System.IO.Stream> tarafından döndürülen nesne `GetRequestStream` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="58bdf-120">Write the data to the <xref:System.IO.Stream> object returned by the `GetRequestStream` method.</span></span> <span data-ttu-id="58bdf-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="58bdf-121">For example:</span></span>
  
    ```csharp  
    dataStream.Write(byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write(byteArray, 0, byteArray.Length)  
    ```  
  
8.  <span data-ttu-id="58bdf-122">İstek akışı çağırarak kapatmak <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="58bdf-122">Close the request stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="58bdf-123">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="58bdf-123">For example:</span></span>
  
    ```csharp  
    dataStream.Close();  
    ```  
  
    ```vb  
    dataStream.Close()  
    ```  
  
9. <span data-ttu-id="58bdf-124">Çağırarak sunucuya istek göndermek <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="58bdf-124">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="58bdf-125">Bu yöntem sunucu yanıtını içeren bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="58bdf-125">This method returns an object containing the server's response.</span></span> <span data-ttu-id="58bdf-126">Döndürülen `WebResponse` nesnenin türü, isteğin URI düzeni tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="58bdf-126">The returned `WebResponse` object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="58bdf-127">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="58bdf-127">For example:</span></span>
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
10. <span data-ttu-id="58bdf-128">Özelliklerini erişebilir, `WebResponse` nesne veya protokole özgü özelliklerini okumak için bir protokole özgü örneğe dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="58bdf-128">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span> 

    <span data-ttu-id="58bdf-129">Örneğin, erişim HTTP'ye özgü özellikleri için <xref:System.Net.HttpWebResponse>, noktaya yayın, `WebResponse` nesnesini bir <xref:System.Net.HttpWebResponse> başvuru.</span><span class="sxs-lookup"><span data-stu-id="58bdf-129">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an <xref:System.Net.HttpWebResponse> reference.</span></span> <span data-ttu-id="58bdf-130">Aşağıdaki kod örneği, HTTP özgü görüntülenecek gösterilmektedir <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> Yanıtta gönderilen özelliği:</span><span class="sxs-lookup"><span data-stu-id="58bdf-130">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>
  
    ```csharp  
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);    
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. <span data-ttu-id="58bdf-131">Sunucu tarafından gönderilen yanıt verilerini içeren akış almak için arama <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> yöntemi, `WebResponse` nesne.</span><span class="sxs-lookup"><span data-stu-id="58bdf-131">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method of your `WebResponse` object.</span></span> <span data-ttu-id="58bdf-132">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="58bdf-132">For example:</span></span>
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
12. <span data-ttu-id="58bdf-133">Yanıt nesnesinden verileri okuduktan sonra ya da ile kapatmak <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> yöntemi veya kapanış yanıt akışı ile <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="58bdf-133">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="58bdf-134">Yanıt ya da akış kapatmayın, uygulamanızın sunucu bağlantılarını dışında çalıştırabilir ve ek istekleri işleyemediğinden haline gelir.</span><span class="sxs-lookup"><span data-stu-id="58bdf-134">If you don't close either the response or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="58bdf-135">Çünkü `WebResponse.Close` yöntem çağrılarını `Stream.Close` yanıtı kapatır, çağrı gerekli değildir `Close` nesnelerde yanıt ve akış bunu yaparsanız bu nedenle zararlı olmasa da.</span><span class="sxs-lookup"><span data-stu-id="58bdf-135">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="58bdf-136">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="58bdf-136">For example:</span></span>
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="58bdf-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="58bdf-137">Example</span></span>  
  
<span data-ttu-id="58bdf-138">Aşağıdaki kod örneği, bir web sunucusuna veri göndermek ve kendi yanıt verileri okumak gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="58bdf-138">The following code example shows how to send data to a web server and read the data in its response:</span></span>  

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a><span data-ttu-id="58bdf-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58bdf-139">See also</span></span>

- [<span data-ttu-id="58bdf-140">İnternet istekleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="58bdf-140">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="58bdf-141">Ağda akışları kullanma</span><span class="sxs-lookup"><span data-stu-id="58bdf-141">Using streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="58bdf-142">İnternet'e bir proxy üzerinden erişme</span><span class="sxs-lookup"><span data-stu-id="58bdf-142">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="58bdf-143">Veri isteme</span><span class="sxs-lookup"><span data-stu-id="58bdf-143">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="58bdf-144">Nasıl yapılır: WebRequest sınıfını kullanarak veri isteme</span><span class="sxs-lookup"><span data-stu-id="58bdf-144">How to: Request data by using the WebRequest class</span></span>](how-to-request-data-using-the-webrequest-class.md)
