---
title: 'Nasıl yapılır: WebRequest sınıfını kullanarak veri gönderme'
description: .NET Framework WebRequest sınıfını kullanarak bir sunucuya veri gönderme hakkında bilgi edinin. Bu yordam yaygın olarak bir Web sayfasına veri göndermek için kullanılır.
ms.date: 03/25/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
ms.openlocfilehash: 4b353250fec778ee8b352f13de6d7faaf15c13ee
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502450"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a><span data-ttu-id="bb528-104">Nasıl yapılır: WebRequest sınıfını kullanarak veri gönderme</span><span class="sxs-lookup"><span data-stu-id="bb528-104">How to: Send data by using the WebRequest class</span></span>

<span data-ttu-id="bb528-105">Aşağıdaki yordam bir sunucusuna veri gönderme adımlarını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="bb528-105">The following procedure describes the steps to send data to a server.</span></span> <span data-ttu-id="bb528-106">Bu yordam yaygın olarak bir Web sayfasına veri göndermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bb528-106">This procedure is commonly used to post data to a Web page.</span></span>

## <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="bb528-107">Bir konak sunucusuna veri göndermek için</span><span class="sxs-lookup"><span data-stu-id="bb528-107">To send data to a host server</span></span>

1. <span data-ttu-id="bb528-108"><xref:System.Net.WebRequest> <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> Veri kabul eden bir betik veya ASP.NET sayfası gibi BIR kaynağın URI 'siyle çağırarak bir örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bb528-108">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource, such as a script or ASP.NET page, that accepts data.</span></span> <span data-ttu-id="bb528-109">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bb528-109">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > <span data-ttu-id="bb528-110">.NET Framework, <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> *http:*, *https:*, *FTP:* ve *Dosya:* ile başlayan URI 'ler için ve sınıflarından türetilmiş protokole özgü sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb528-110">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="bb528-111">Protokole özgü özellikleri ayarlamanız veya okumanız gerekiyorsa, <xref:System.Net.WebRequest> veya <xref:System.Net.WebResponse> nesnesini protokole özgü bir nesne türüne atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="bb528-111">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="bb528-112">Daha fazla bilgi için bkz. [takılabilir protokolleri programlama](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="bb528-112">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="bb528-113">Nesneniz için ihtiyacınız olan herhangi bir özellik değerini ayarlayın `WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="bb528-113">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="bb528-114">Örneğin, kimlik doğrulamasını etkinleştirmek için, <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> özelliğini sınıfının bir örneğine ayarlayın <xref:System.Net.NetworkCredential> :</span><span class="sxs-lookup"><span data-stu-id="bb528-114">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="bb528-115">HTTP yöntemi gibi bir istekle veri gönderilmesine izin veren bir protokol yöntemi belirtin `POST` :</span><span class="sxs-lookup"><span data-stu-id="bb528-115">Specify a protocol method that permits data to be sent with a request, such as the HTTP `POST` method:</span></span>

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. <span data-ttu-id="bb528-116">Özelliği, <xref:System.Web.HttpRequest.ContentLength> isteğinize dahil ettiğiniz bayt sayısına ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bb528-116">Set the <xref:System.Web.HttpRequest.ContentLength> property to the number of bytes you're including with your request.</span></span> <span data-ttu-id="bb528-117">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bb528-117">For example:</span></span>

    ```csharp
    request.ContentLength = byteArray.Length;
    ```

    ```vb
    request.ContentLength = byteArray.Length
    ```

5. <span data-ttu-id="bb528-118"><xref:System.Web.HttpRequest.ContentType>Özelliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="bb528-118">Set the <xref:System.Web.HttpRequest.ContentType> property to an appropriate value.</span></span> <span data-ttu-id="bb528-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bb528-119">For example:</span></span>

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. <span data-ttu-id="bb528-120">Yöntemini çağırarak istek verilerini tutan akışı alın <xref:System.Net.WebRequest.GetRequestStream%2A> .</span><span class="sxs-lookup"><span data-stu-id="bb528-120">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span> <span data-ttu-id="bb528-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bb528-121">For example:</span></span>

    ```csharp
    Stream dataStream = request.GetRequestStream();
    ```

    ```vb
    Dim dataStream As Stream = request.GetRequestStream()
    ```

7. <span data-ttu-id="bb528-122"><xref:System.IO.Stream>Yöntemi tarafından döndürülen nesneye verileri yazın `GetRequestStream` .</span><span class="sxs-lookup"><span data-stu-id="bb528-122">Write the data to the <xref:System.IO.Stream> object returned by the `GetRequestStream` method.</span></span> <span data-ttu-id="bb528-123">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bb528-123">For example:</span></span>

    ```csharp
    dataStream.Write(byteArray, 0, byteArray.Length);
    ```

    ```vb
    dataStream.Write(byteArray, 0, byteArray.Length)
    ```

8. <span data-ttu-id="bb528-124">Yöntemini çağırarak istek akışını kapatın <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="bb528-124">Close the request stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="bb528-125">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bb528-125">For example:</span></span>

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. <span data-ttu-id="bb528-126">Çağırarak isteği sunucuya gönderin <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="bb528-126">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bb528-127">Bu yöntem, sunucunun yanıtını içeren bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="bb528-127">This method returns an object containing the server's response.</span></span> <span data-ttu-id="bb528-128">Döndürülen `WebResponse` nesnenin türü, isteğin URI 'si düzenine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="bb528-128">The returned `WebResponse` object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="bb528-129">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bb528-129">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. <span data-ttu-id="bb528-130">`WebResponse`Bir protokole özgü özellikleri okumak için nesnenizin özelliklerine erişebilir veya protokole özgü bir örneğe çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb528-130">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="bb528-131">Örneğin, HTTP 'ye özgü özelliklerine erişmek için <xref:System.Net.HttpWebResponse> , `WebResponse` nesnenizin <xref:System.Net.HttpWebResponse> başvurusunu bir başvuruya atayın.</span><span class="sxs-lookup"><span data-stu-id="bb528-131">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an <xref:System.Net.HttpWebResponse> reference.</span></span> <span data-ttu-id="bb528-132">Aşağıdaki kod örneği, <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> bir Yanıt ile GÖNDERILEN http 'e özgü özelliğin nasıl görüntüleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="bb528-132">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)
    ```

11. <span data-ttu-id="bb528-133">Sunucu tarafından gönderilen yanıt verilerini içeren akışı almak için, <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> nesnenizin yöntemini çağırın `WebResponse` .</span><span class="sxs-lookup"><span data-stu-id="bb528-133">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method of your `WebResponse` object.</span></span> <span data-ttu-id="bb528-134">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bb528-134">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

12. <span data-ttu-id="bb528-135">Yanıt nesnesinden verileri okuduktan sonra, yöntemi ile kapatın <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> ya da yöntemi ile yanıt akışını kapatın <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="bb528-135">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="bb528-136">Yanıtı veya akışı kapatmazsanız, uygulamanızın sunucu bağlantısı tükenebilir ve ek istekleri işleyemez.</span><span class="sxs-lookup"><span data-stu-id="bb528-136">If you don't close either the response or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="bb528-137">`WebResponse.Close`Yöntemi `Stream.Close` yanıtı kapattığı zaman çağırdığı için, `Close` hem yanıt hem de akış nesnelerinde çağırmak gerekli değildir, ancak bunu zararlı değildir.</span><span class="sxs-lookup"><span data-stu-id="bb528-137">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="bb528-138">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bb528-138">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="bb528-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="bb528-139">Example</span></span>

<span data-ttu-id="bb528-140">Aşağıdaki örnek, bir Web sunucusuna nasıl veri gönderileceğini ve yanıttaki verileri nasıl okuyakullanacağınızı gösterir:</span><span class="sxs-lookup"><span data-stu-id="bb528-140">The following example shows how to send data to a web server and read the data in its response:</span></span>

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a><span data-ttu-id="bb528-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb528-141">See also</span></span>

- [<span data-ttu-id="bb528-142">İnternet istekleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="bb528-142">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="bb528-143">Ağda akışlar kullanma</span><span class="sxs-lookup"><span data-stu-id="bb528-143">Using streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="bb528-144">Bir ara sunucu üzerinden İnternet 'e erişme</span><span class="sxs-lookup"><span data-stu-id="bb528-144">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="bb528-145">Veri isteme</span><span class="sxs-lookup"><span data-stu-id="bb528-145">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="bb528-146">Nasıl yapılır: WebRequest sınıfını kullanarak veri ISTEME</span><span class="sxs-lookup"><span data-stu-id="bb528-146">How to: Request data by using the WebRequest class</span></span>](how-to-request-data-using-the-webrequest-class.md)
