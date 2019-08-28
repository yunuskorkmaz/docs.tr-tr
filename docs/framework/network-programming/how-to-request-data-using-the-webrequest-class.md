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
ms.openlocfilehash: eb38a95891afaf4cab98e43a250b67823fa5eb24
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040880"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a><span data-ttu-id="35d52-102">Nasıl yapılır: WebRequest sınıfını kullanarak veri isteme</span><span class="sxs-lookup"><span data-stu-id="35d52-102">How to: Request data by using the WebRequest class</span></span>

<span data-ttu-id="35d52-103">Aşağıdaki yordam bir sunucudan bir Web sayfası veya dosya gibi bir kaynak isteme adımlarını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="35d52-103">The following procedure describes the steps to request a resource, such as a Web page or a file, from a server.</span></span> <span data-ttu-id="35d52-104">Kaynağın bir URI ile tanımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="35d52-104">The resource must be identified by a URI.</span></span>

## <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="35d52-105">Bir konak sunucusundan veri istemek için</span><span class="sxs-lookup"><span data-stu-id="35d52-105">To request data from a host server</span></span>

1. <span data-ttu-id="35d52-106">Bir kaynağın <xref:System.Net.WebRequest> URI 'siyle çağırarak <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> bir örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="35d52-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource.</span></span> <span data-ttu-id="35d52-107">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="35d52-107">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/default.html");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/default.html")
    ```

    > [!NOTE]
    > <span data-ttu-id="35d52-108">.NET Framework <xref:System.Net.WebRequest> , *http:* , *https:* , *FTP:* ve <xref:System.Net.WebResponse> *Dosya:* ile başlayan URI 'ler için ve sınıflarından türetilmiş protokole özgü sınıflar sağlar.</span><span class="sxs-lookup"><span data-stu-id="35d52-108">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="35d52-109">Protokole özgü özellikleri ayarlamanız veya okumanız gerekiyorsa, <xref:System.Net.WebRequest> veya <xref:System.Net.WebResponse> nesnesini protokole özgü bir nesne türüne atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="35d52-109">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="35d52-110">Daha fazla bilgi için bkz. [takılabilir protokolleri programlama](programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="35d52-110">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="35d52-111">`WebRequest` Nesneniz için ihtiyacınız olan herhangi bir özellik değerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="35d52-111">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="35d52-112">Örneğin, kimlik doğrulamasını etkinleştirmek için, <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> özelliğini <xref:System.Net.NetworkCredential> sınıfının bir örneğine ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="35d52-112">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="35d52-113">Çağırarak <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>isteği sunucuya gönderin.</span><span class="sxs-lookup"><span data-stu-id="35d52-113">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="35d52-114">Bu yöntem, sunucunun yanıtını içeren bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="35d52-114">This method returns an object containing the server's response.</span></span> <span data-ttu-id="35d52-115">Döndürülen <xref:System.Net.WebResponse> nesnenin türü, isteğin URI 'si düzenine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="35d52-115">The returned <xref:System.Net.WebResponse> object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="35d52-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="35d52-116">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. <span data-ttu-id="35d52-117">Bir protokole özgü özellikleri okumak için `WebResponse` nesnenizin özelliklerine erişebilir veya protokole özgü bir örneğe çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35d52-117">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="35d52-118">Örneğin, http 'ye özgü özelliklerine <xref:System.Net.HttpWebResponse>erişmek için, `WebResponse` nesnenizin başvurusunu bir `HttpWebResponse` başvuruya atayın.</span><span class="sxs-lookup"><span data-stu-id="35d52-118">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an `HttpWebResponse` reference.</span></span> <span data-ttu-id="35d52-119">Aşağıdaki kod örneği, bir Yanıt ile gönderilen http 'e özgü <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> özelliğin nasıl görüntüleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="35d52-119">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)
    ```

5. <span data-ttu-id="35d52-120">Sunucu tarafından gönderilen yanıt verilerini içeren akışı almak için <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="35d52-120">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="35d52-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="35d52-121">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

6. <span data-ttu-id="35d52-122">Yanıt nesnesinden verileri okuduktan sonra, <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> yöntemi ile kapatın ya da <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yöntemi ile yanıt akışını kapatın.</span><span class="sxs-lookup"><span data-stu-id="35d52-122">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="35d52-123">Yanıt nesnesini veya akışı kapatmazsanız, uygulamanız sunucu bağlantılarının tükenebilir ve ek istekleri işleyemez.</span><span class="sxs-lookup"><span data-stu-id="35d52-123">If you don't close either the response object or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="35d52-124">Yöntemi yanıtı kapattığı zaman `Stream.Close` çağırdığı için, hem yanıt hem de akış nesnelerinde çağırmak `Close` gerekli değildir, ancak bunu zararlı değildir. `WebResponse.Close`</span><span class="sxs-lookup"><span data-stu-id="35d52-124">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="35d52-125">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="35d52-125">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="35d52-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="35d52-126">Example</span></span>

<span data-ttu-id="35d52-127">Aşağıdaki kod örneği, bir Web sunucusuna nasıl istek oluşturulacağını ve yanıttaki verileri nasıl okuyakullanacağınızı gösterir:</span><span class="sxs-lookup"><span data-stu-id="35d52-127">The following code example shows how to create a request to a web server and read the data in its response:</span></span>

[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a><span data-ttu-id="35d52-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35d52-128">See also</span></span>

- [<span data-ttu-id="35d52-129">İnternet istekleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="35d52-129">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="35d52-130">Ağda akışlar kullanma</span><span class="sxs-lookup"><span data-stu-id="35d52-130">Using Streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="35d52-131">Bir ara sunucu üzerinden İnternet 'e erişme</span><span class="sxs-lookup"><span data-stu-id="35d52-131">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="35d52-132">Veri isteme</span><span class="sxs-lookup"><span data-stu-id="35d52-132">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="35d52-133">Nasıl yapılır: WebRequest sınıfını kullanarak veri gönderme</span><span class="sxs-lookup"><span data-stu-id="35d52-133">How to: Send data by using the WebRequest class</span></span>](how-to-send-data-using-the-webrequest-class.md)
