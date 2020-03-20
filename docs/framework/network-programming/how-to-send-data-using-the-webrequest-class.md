---
title: 'Nasıl kullanılır: WebRequest sınıfını kullanarak veri gönderme'
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 2467b289df7a0361b51ad91d4458d32742c42275
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70040824"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a><span data-ttu-id="0d489-102">Nasıl kullanılır: WebRequest sınıfını kullanarak veri gönderme</span><span class="sxs-lookup"><span data-stu-id="0d489-102">How to: Send data by using the WebRequest class</span></span>

<span data-ttu-id="0d489-103">Aşağıdaki yordam, bir sunucuya veri gönderme adımlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0d489-103">The following procedure describes the steps to send data to a server.</span></span> <span data-ttu-id="0d489-104">Bu yordam genellikle bir Web sayfasına veri göndermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0d489-104">This procedure is commonly used to post data to a Web page.</span></span>

## <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="0d489-105">Ana bilgisayar sunucusuna veri göndermek için</span><span class="sxs-lookup"><span data-stu-id="0d489-105">To send data to a host server</span></span>

1. <span data-ttu-id="0d489-106">Verileri <xref:System.Net.WebRequest> kabul eden <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> komut dosyası veya ASP.NET sayfası gibi bir kaynağın URI'si ile arayarak bir örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0d489-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource, such as a script or ASP.NET page, that accepts data.</span></span> <span data-ttu-id="0d489-107">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d489-107">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > <span data-ttu-id="0d489-108">.NET <xref:System.Net.WebRequest> Framework http ile başlayan URI'ler için ve <xref:System.Net.WebResponse> sınıflardan türetilen protokole özgü sınıflar *sağlar:*, *https:*, *ftp:*, ve *dosya:*.</span><span class="sxs-lookup"><span data-stu-id="0d489-108">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="0d489-109">Protokole özgü özellikleri ayarlamanız veya okumanız gerekiyorsa, <xref:System.Net.WebResponse> nesnenizi veya nesnenizi protokole özgü bir nesne türüne dökmeniz <xref:System.Net.WebRequest> gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d489-109">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="0d489-110">Daha fazla bilgi için [takılabilir Programlama protokollerine](programming-pluggable-protocols.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="0d489-110">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="0d489-111">Nesnenizde `WebRequest` gereksinim duyduğunuz özellik değerlerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0d489-111">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="0d489-112">Örneğin, kimlik doğrulamasını etkinleştirmek <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> için özelliği <xref:System.Net.NetworkCredential> sınıfın bir örneğine ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="0d489-112">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="0d489-113">Http `POST` yöntemi gibi bir istekle veri gönderilmesine izin veren bir protokol yöntemi belirtin:</span><span class="sxs-lookup"><span data-stu-id="0d489-113">Specify a protocol method that permits data to be sent with a request, such as the HTTP `POST` method:</span></span>

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. <span data-ttu-id="0d489-114"><xref:System.Web.HttpRequest.ContentLength> Özelliği, isteğiniz için dahil ettiğiniz bayt sayısına ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0d489-114">Set the <xref:System.Web.HttpRequest.ContentLength> property to the number of bytes you're including with your request.</span></span> <span data-ttu-id="0d489-115">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d489-115">For example:</span></span>

    ```csharp
    request.ContentLength = byteArray.Length;
    ```

    ```vb
    request.ContentLength = byteArray.Length
    ```

5. <span data-ttu-id="0d489-116"><xref:System.Web.HttpRequest.ContentType> Özelliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0d489-116">Set the <xref:System.Web.HttpRequest.ContentType> property to an appropriate value.</span></span> <span data-ttu-id="0d489-117">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d489-117">For example:</span></span>

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. <span data-ttu-id="0d489-118"><xref:System.Net.WebRequest.GetRequestStream%2A> Yöntemi arayarak istek verilerini tutan akışı alın.</span><span class="sxs-lookup"><span data-stu-id="0d489-118">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span> <span data-ttu-id="0d489-119">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d489-119">For example:</span></span>

    ```csharp
    Stream dataStream = request.GetRequestStream();
    ```

    ```vb
    Dim dataStream As Stream = request.GetRequestStream()
    ```

7. <span data-ttu-id="0d489-120">Yöntemi yle <xref:System.IO.Stream> `GetRequestStream` döndürülen nesneye verileri yazın.</span><span class="sxs-lookup"><span data-stu-id="0d489-120">Write the data to the <xref:System.IO.Stream> object returned by the `GetRequestStream` method.</span></span> <span data-ttu-id="0d489-121">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d489-121">For example:</span></span>

    ```csharp
    dataStream.Write(byteArray, 0, byteArray.Length);
    ```

    ```vb
    dataStream.Write(byteArray, 0, byteArray.Length)
    ```

8. <span data-ttu-id="0d489-122"><xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> Yöntemi çağırarak istek akışını kapatın.</span><span class="sxs-lookup"><span data-stu-id="0d489-122">Close the request stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0d489-123">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d489-123">For example:</span></span>

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. <span data-ttu-id="0d489-124">Arayarak isteği sunucuya <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>gönderin.</span><span class="sxs-lookup"><span data-stu-id="0d489-124">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0d489-125">Bu yöntem, sunucunun yanıtını içeren bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="0d489-125">This method returns an object containing the server's response.</span></span> <span data-ttu-id="0d489-126">Döndürülen `WebResponse` nesnenin türü, isteğin URI düzenine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="0d489-126">The returned `WebResponse` object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="0d489-127">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d489-127">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. <span data-ttu-id="0d489-128">Nesnenizin `WebResponse` özelliklerine erişebilir veya protokole özgü özellikleri okumak için protokole özgü bir örneğe atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d489-128">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="0d489-129">Örneğin, HTTP'ye özgü özelliklere <xref:System.Net.HttpWebResponse>erişmek için `WebResponse` nesnenizi <xref:System.Net.HttpWebResponse> bir başvuruya döküm.</span><span class="sxs-lookup"><span data-stu-id="0d489-129">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an <xref:System.Net.HttpWebResponse> reference.</span></span> <span data-ttu-id="0d489-130">Aşağıdaki kod örneği, yanıtla gönderilen <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> HTTP'ye özgü özelliğin nasıl görüntülenebildiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="0d489-130">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)
    ```

11. <span data-ttu-id="0d489-131">Sunucu tarafından gönderilen yanıt verilerini içeren akışı <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> almak için `WebResponse` nesnenizin yöntemini arayın.</span><span class="sxs-lookup"><span data-stu-id="0d489-131">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method of your `WebResponse` object.</span></span> <span data-ttu-id="0d489-132">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d489-132">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

12. <span data-ttu-id="0d489-133">Yanıt nesnesinden gelen verileri okuduktan sonra, <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> yöntemle kapatın veya <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yöntemle yanıt akışını kapatın.</span><span class="sxs-lookup"><span data-stu-id="0d489-133">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0d489-134">Yanıtı veya akışı kapatmazsanız, uygulamanızın sunucu bağlantıları tükenebilir ve ek istekleri işleyemez hale gelir.</span><span class="sxs-lookup"><span data-stu-id="0d489-134">If you don't close either the response or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="0d489-135">Yöntem `WebResponse.Close` yanıtı `Stream.Close` kapattığında aradığından, bunu yapmak zararlı olmasa `Close` da hem yanıtı hem de akış nesnelerini çağırmak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="0d489-135">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="0d489-136">Örnek:</span><span class="sxs-lookup"><span data-stu-id="0d489-136">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="0d489-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="0d489-137">Example</span></span>

<span data-ttu-id="0d489-138">Aşağıdaki örnek, bir web sunucusuna nasıl veri gönderilebildiğini ve yanıtındaki verileri nasıl okuyup okunduğunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="0d489-138">The following example shows how to send data to a web server and read the data in its response:</span></span>

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a><span data-ttu-id="0d489-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d489-139">See also</span></span>

- [<span data-ttu-id="0d489-140">Internet istekleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="0d489-140">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="0d489-141">Ağdaki akışları kullanma</span><span class="sxs-lookup"><span data-stu-id="0d489-141">Using streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="0d489-142">Bir proxy üzerinden internete erişim</span><span class="sxs-lookup"><span data-stu-id="0d489-142">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="0d489-143">Veri isteme</span><span class="sxs-lookup"><span data-stu-id="0d489-143">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="0d489-144">Nasıl kullanılır: WebRequest sınıfını kullanarak veri isteme</span><span class="sxs-lookup"><span data-stu-id="0d489-144">How to: Request data by using the WebRequest class</span></span>](how-to-request-data-using-the-webrequest-class.md)
