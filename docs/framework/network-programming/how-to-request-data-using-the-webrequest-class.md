---
title: 'Nasıl kullanılır: WebRequest sınıfını kullanarak veri isteme'
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
ms.openlocfilehash: e670a2a503ce704eff847e9e0b3ee340ab52fe62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048160"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a><span data-ttu-id="8c2b9-102">Nasıl kullanılır: WebRequest sınıfını kullanarak veri isteme</span><span class="sxs-lookup"><span data-stu-id="8c2b9-102">How to: Request data by using the WebRequest class</span></span>

<span data-ttu-id="8c2b9-103">Aşağıdaki yordam, bir sunucudan Web sayfası veya dosya gibi bir kaynak istemek için adımları açıklar.</span><span class="sxs-lookup"><span data-stu-id="8c2b9-103">The following procedure describes the steps to request a resource, such as a Web page or a file, from a server.</span></span> <span data-ttu-id="8c2b9-104">Kaynak bir URI tarafından tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8c2b9-104">The resource must be identified by a URI.</span></span>

## <a name="to-request-data-from-a-host-server"></a><span data-ttu-id="8c2b9-105">Ana bilgisayar sunucusundan veri istemek için</span><span class="sxs-lookup"><span data-stu-id="8c2b9-105">To request data from a host server</span></span>

1. <span data-ttu-id="8c2b9-106">Kaynağın <xref:System.Net.WebRequest> URI'si ile arayarak <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> bir örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8c2b9-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> with the URI of a resource.</span></span> <span data-ttu-id="8c2b9-107">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8c2b9-107">For example:</span></span>

    ```csharp
    WebRequest request = WebRequest.Create("https://docs.microsoft.com");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("https://docs.microsoft.com")
    ```

    > [!NOTE]
    > <span data-ttu-id="8c2b9-108">.NET <xref:System.Net.WebRequest> Framework http ile başlayan URI'ler için ve <xref:System.Net.WebResponse> sınıflardan türetilen protokole özgü sınıflar *sağlar:*, *https:*, *ftp:*, ve *dosya:*.</span><span class="sxs-lookup"><span data-stu-id="8c2b9-108">The .NET Framework provides protocol-specific classes derived from the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes for URIs that begin with *http:*, *https:*, *ftp:*, and *file:*.</span></span>

    <span data-ttu-id="8c2b9-109">Protokole özgü özellikleri ayarlamanız veya okumanız gerekiyorsa, <xref:System.Net.WebResponse> nesnenizi veya nesnenizi protokole özgü bir nesne türüne dökmeniz <xref:System.Net.WebRequest> gerekir.</span><span class="sxs-lookup"><span data-stu-id="8c2b9-109">If you need to set or read protocol-specific properties, you must cast your <xref:System.Net.WebRequest> or <xref:System.Net.WebResponse> object to a protocol-specific object type.</span></span> <span data-ttu-id="8c2b9-110">Daha fazla bilgi için [takılabilir Programlama protokollerine](programming-pluggable-protocols.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8c2b9-110">For more information, see [Programming pluggable protocols](programming-pluggable-protocols.md).</span></span>

2. <span data-ttu-id="8c2b9-111">Nesnenizde `WebRequest` gereksinim duyduğunuz özellik değerlerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8c2b9-111">Set any property values that you need in your `WebRequest` object.</span></span> <span data-ttu-id="8c2b9-112">Örneğin, kimlik doğrulamasını etkinleştirmek <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> için özelliği <xref:System.Net.NetworkCredential> sınıfın bir örneğine ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="8c2b9-112">For example, to enable authentication, set the <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> property to an instance of the <xref:System.Net.NetworkCredential> class:</span></span>

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. <span data-ttu-id="8c2b9-113">Arayarak isteği sunucuya <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>gönderin.</span><span class="sxs-lookup"><span data-stu-id="8c2b9-113">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8c2b9-114">Bu yöntem, sunucunun yanıtını içeren bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="8c2b9-114">This method returns an object containing the server's response.</span></span> <span data-ttu-id="8c2b9-115">Döndürülen <xref:System.Net.WebResponse> nesnenin türü, isteğin URI düzenine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="8c2b9-115">The returned <xref:System.Net.WebResponse> object's type is determined by the scheme of the request's URI.</span></span> <span data-ttu-id="8c2b9-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8c2b9-116">For example:</span></span>

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. <span data-ttu-id="8c2b9-117">Nesnenizin `WebResponse` özelliklerine erişebilir veya protokole özgü özellikleri okumak için protokole özgü bir örneğe atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c2b9-117">You can access the properties of your `WebResponse` object or cast it to a protocol-specific instance to read protocol-specific properties.</span></span>

    <span data-ttu-id="8c2b9-118">Örneğin, HTTP'ye özgü özelliklere <xref:System.Net.HttpWebResponse>erişmek için `WebResponse` nesnenizi `HttpWebResponse` bir başvuruya döküm.</span><span class="sxs-lookup"><span data-stu-id="8c2b9-118">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast your `WebResponse` object to an `HttpWebResponse` reference.</span></span> <span data-ttu-id="8c2b9-119">Aşağıdaki kod örneği, yanıtla gönderilen <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> HTTP'ye özgü özelliğin nasıl görüntülenebildiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="8c2b9-119">The following code example shows how to display the HTTP-specific <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> property sent with a response:</span></span>

    ```csharp
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)
    ```

5. <span data-ttu-id="8c2b9-120">Sunucu tarafından gönderilen yanıt verilerini içeren akışı <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> almak için yöntemi arayın.</span><span class="sxs-lookup"><span data-stu-id="8c2b9-120">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8c2b9-121">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8c2b9-121">For example:</span></span>

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

6. <span data-ttu-id="8c2b9-122">Yanıt nesnesinden gelen verileri okuduktan sonra, <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> yöntemle kapatın veya <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yöntemle yanıt akışını kapatın.</span><span class="sxs-lookup"><span data-stu-id="8c2b9-122">After you've read the data from the response object, either close it with the <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> method or close the response stream with the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8c2b9-123">Yanıt nesnesini veya akışı kapatmazsanız, uygulamanız sunucu bağlantıları tükenebilir ve ek istekleri işleyemez hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="8c2b9-123">If you don't close either the response object or the stream, your application can run out of server connections and become unable to process additional requests.</span></span> <span data-ttu-id="8c2b9-124">Yöntem `WebResponse.Close` yanıtı `Stream.Close` kapattığında aradığından, bunu yapmak zararlı olmasa `Close` da hem yanıtı hem de akış nesnelerini çağırmak gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="8c2b9-124">Because the `WebResponse.Close` method calls `Stream.Close` when it closes the response, it's not necessary to call `Close` on both the response and stream objects, although doing so isn't harmful.</span></span> <span data-ttu-id="8c2b9-125">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8c2b9-125">For example:</span></span>

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a><span data-ttu-id="8c2b9-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="8c2b9-126">Example</span></span>

<span data-ttu-id="8c2b9-127">Aşağıdaki kod örneği, bir web sunucusuna nasıl istek oluşturulup yanıttaki verileri nasıl okuyabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8c2b9-127">The following code example shows how to create a request to a web server and read the data in its response:</span></span>

[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a><span data-ttu-id="8c2b9-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c2b9-128">See also</span></span>

- [<span data-ttu-id="8c2b9-129">Internet istekleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="8c2b9-129">Creating internet requests</span></span>](creating-internet-requests.md)
- [<span data-ttu-id="8c2b9-130">Ağdaki Akışları Kullanma</span><span class="sxs-lookup"><span data-stu-id="8c2b9-130">Using Streams on the network</span></span>](using-streams-on-the-network.md)
- [<span data-ttu-id="8c2b9-131">Bir proxy üzerinden internete erişim</span><span class="sxs-lookup"><span data-stu-id="8c2b9-131">Accessing the internet through a proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="8c2b9-132">Veri isteme</span><span class="sxs-lookup"><span data-stu-id="8c2b9-132">Requesting data</span></span>](requesting-data.md)
- [<span data-ttu-id="8c2b9-133">Nasıl kullanılır: WebRequest sınıfını kullanarak veri gönderme</span><span class="sxs-lookup"><span data-stu-id="8c2b9-133">How to: Send data by using the WebRequest class</span></span>](how-to-send-data-using-the-webrequest-class.md)
