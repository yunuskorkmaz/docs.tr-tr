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
ms.openlocfilehash: 2467b289df7a0361b51ad91d4458d32742c42275
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040824"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a><span data-ttu-id="def6a-102">Nasıl yapılır: WebRequest sınıfını kullanarak veri gönderme</span><span class="sxs-lookup"><span data-stu-id="def6a-102">How to: Send data by using the WebRequest class</span></span>

<span data-ttu-id="def6a-103">Aşağıdaki yordam bir sunucusuna veri gönderme adımlarını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="def6a-103">The following procedure describes the steps to send data to a server.</span></span> <span data-ttu-id="def6a-104">Bu yordam yaygın olarak bir Web sayfasına veri göndermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="def6a-104">This procedure is commonly used to post data to a Web page.</span></span>

## <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="def6a-105">Bir konak sunucusuna veri göndermek için</span><span class="sxs-lookup"><span data-stu-id="def6a-105">To send data to a host server</span></span>

1. <span data-ttu-id="def6a-106">Veri kabul <xref:System.Net.WebRequest> eden bir betik <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> veya ASP.NET sayfası gibi bir kaynağın URI 'siyle çağırarak bir örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="def6a-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource, such as a script or ASP.NET page, that accepts data.</span></span> <span data-ttu-id="def6a-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="def6a-107">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > <span data-ttu-id="def6a-108">.NET Framework <xref:System.Net.WebRequest> , *http:* , *https:* , *FTP:* ve <xref:System.Net.WebResponse> *Dosya:* ile başlayan URI 'ler için ve sınıflarından türetilmiş protokole özgü sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="def6a-108">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="def6a-109">Protokole özgü özellikleri ayarlamanız veya okumanız gerekiyorsa, <xref:System.Net.WebRequest> veya <xref:System.Net.WebResponse> nesnesini protokole özgü bir nesne türüne atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="def6a-109">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="def6a-110">Daha fazla bilgi için bkz. [takılabilir protokolleri programlama](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="def6a-110">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="def6a-111">`WebRequest` Nesneniz için ihtiyacınız olan herhangi bir özellik değerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="def6a-111">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="def6a-112">Örneğin, kimlik doğrulamasını etkinleştirmek için, <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> özelliğini <xref:System.Net.NetworkCredential> sınıfının bir örneğine ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="def6a-112">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="def6a-113">HTTP `POST` yöntemi gibi bir istekle veri gönderilmesine izin veren bir protokol yöntemi belirtin:</span><span class="sxs-lookup"><span data-stu-id="def6a-113">Specify a protocol method that permits data to be sent with a request, such as the HTTP `POST` method:</span></span>

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. <span data-ttu-id="def6a-114">Özelliği, <xref:System.Web.HttpRequest.ContentLength> isteğinize dahil ettiğiniz bayt sayısına ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="def6a-114">Set the <xref:System.Web.HttpRequest.ContentLength> property to the number of bytes you're including with your request.</span></span> <span data-ttu-id="def6a-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="def6a-115">For example:</span></span>

    ```csharp
    request.ContentLength = byteArray.Length;
    ```

    ```vb
    request.ContentLength = byteArray.Length
    ```

5. <span data-ttu-id="def6a-116"><xref:System.Web.HttpRequest.ContentType> Özelliği uygun bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="def6a-116">Set the <xref:System.Web.HttpRequest.ContentType> property to an appropriate value.</span></span> <span data-ttu-id="def6a-117">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="def6a-117">For example:</span></span>

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. <span data-ttu-id="def6a-118"><xref:System.Net.WebRequest.GetRequestStream%2A> Yöntemini çağırarak istek verilerini tutan akışı alın.</span><span class="sxs-lookup"><span data-stu-id="def6a-118">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span> <span data-ttu-id="def6a-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="def6a-119">For example:</span></span>

    ```csharp
    Stream dataStream = request.GetRequestStream();
    ```

    ```vb
    Dim dataStream As Stream = request.GetRequestStream()
    ```

7. <span data-ttu-id="def6a-120">Yöntemi tarafından döndürülen <xref:System.IO.Stream> nesneye verileri yazın. `GetRequestStream`</span><span class="sxs-lookup"><span data-stu-id="def6a-120">Write the data to the <xref:System.IO.Stream> object returned by the `GetRequestStream` method.</span></span> <span data-ttu-id="def6a-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="def6a-121">For example:</span></span>

    ```csharp
    dataStream.Write(byteArray, 0, byteArray.Length);
    ```

    ```vb
    dataStream.Write(byteArray, 0, byteArray.Length)
    ```

8. <span data-ttu-id="def6a-122"><xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> Yöntemini çağırarak istek akışını kapatın.</span><span class="sxs-lookup"><span data-stu-id="def6a-122">Close the request stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="def6a-123">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="def6a-123">For example:</span></span>

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. <span data-ttu-id="def6a-124">Çağırarak <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>isteği sunucuya gönderin.</span><span class="sxs-lookup"><span data-stu-id="def6a-124">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="def6a-125">Bu yöntem, sunucunun yanıtını içeren bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="def6a-125">This method returns an object containing the server's response.</span></span> <span data-ttu-id="def6a-126">Döndürülen `WebResponse` nesnenin türü, isteğin URI 'si düzenine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="def6a-126">The returned `WebResponse` object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="def6a-127">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="def6a-127">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. <span data-ttu-id="def6a-128">Bir protokole özgü özellikleri okumak için `WebResponse` nesnenizin özelliklerine erişebilir veya protokole özgü bir örneğe çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="def6a-128">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="def6a-129">Örneğin, http 'ye özgü özelliklerine <xref:System.Net.HttpWebResponse>erişmek için, `WebResponse` nesnenizin başvurusunu bir <xref:System.Net.HttpWebResponse> başvuruya atayın.</span><span class="sxs-lookup"><span data-stu-id="def6a-129">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an <xref:System.Net.HttpWebResponse> reference.</span></span> <span data-ttu-id="def6a-130">Aşağıdaki kod örneği, bir Yanıt ile gönderilen http 'e özgü <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> özelliğin nasıl görüntüleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="def6a-130">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)
    ```

11. <span data-ttu-id="def6a-131">Sunucu tarafından gönderilen yanıt verilerini içeren akışı almak için, <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> `WebResponse` nesnenizin yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="def6a-131">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method of your `WebResponse` object.</span></span> <span data-ttu-id="def6a-132">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="def6a-132">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

12. <span data-ttu-id="def6a-133">Yanıt nesnesinden verileri okuduktan sonra, <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> yöntemi ile kapatın ya da <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yöntemi ile yanıt akışını kapatın.</span><span class="sxs-lookup"><span data-stu-id="def6a-133">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="def6a-134">Yanıtı veya akışı kapatmazsanız, uygulamanızın sunucu bağlantısı tükenebilir ve ek istekleri işleyemez.</span><span class="sxs-lookup"><span data-stu-id="def6a-134">If you don't close either the response or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="def6a-135">Yöntemi yanıtı kapattığı zaman `Stream.Close` çağırdığı için, hem yanıt hem de akış nesnelerinde çağırmak `Close` gerekli değildir, ancak bunu zararlı değildir. `WebResponse.Close`</span><span class="sxs-lookup"><span data-stu-id="def6a-135">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="def6a-136">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="def6a-136">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="def6a-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="def6a-137">Example</span></span>

<span data-ttu-id="def6a-138">Aşağıdaki örnek, bir Web sunucusuna nasıl veri gönderileceğini ve yanıttaki verileri nasıl okuyakullanacağınızı gösterir:</span><span class="sxs-lookup"><span data-stu-id="def6a-138">The following example shows how to send data to a web server and read the data in its response:</span></span>

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a><span data-ttu-id="def6a-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="def6a-139">See also</span></span>

- [<span data-ttu-id="def6a-140">İnternet istekleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="def6a-140">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="def6a-141">Ağda akışlar kullanma</span><span class="sxs-lookup"><span data-stu-id="def6a-141">Using streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="def6a-142">Bir ara sunucu üzerinden İnternet 'e erişme</span><span class="sxs-lookup"><span data-stu-id="def6a-142">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="def6a-143">Veri isteme</span><span class="sxs-lookup"><span data-stu-id="def6a-143">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="def6a-144">Nasıl yapılır: WebRequest sınıfını kullanarak veri isteme</span><span class="sxs-lookup"><span data-stu-id="def6a-144">How to: Request data by using the WebRequest class</span></span>](how-to-request-data-using-the-webrequest-class.md)
