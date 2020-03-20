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
# <a name="how-to-send-data-by-using-the-webrequest-class"></a>Nasıl kullanılır: WebRequest sınıfını kullanarak veri gönderme

Aşağıdaki yordam, bir sunucuya veri gönderme adımlarını açıklar. Bu yordam genellikle bir Web sayfasına veri göndermek için kullanılır.

## <a name="to-send-data-to-a-host-server"></a>Ana bilgisayar sunucusuna veri göndermek için

1. Verileri <xref:System.Net.WebRequest> kabul eden <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> komut dosyası veya ASP.NET sayfası gibi bir kaynağın URI'si ile arayarak bir örnek oluşturun. Örnek:

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > .NET <xref:System.Net.WebRequest> Framework http ile başlayan URI'ler için ve <xref:System.Net.WebResponse> sınıflardan türetilen protokole özgü sınıflar *sağlar:*, *https:*, *ftp:*, ve *dosya:*.

    Protokole özgü özellikleri ayarlamanız veya okumanız gerekiyorsa, <xref:System.Net.WebResponse> nesnenizi veya nesnenizi protokole özgü bir nesne türüne dökmeniz <xref:System.Net.WebRequest> gerekir. Daha fazla bilgi için [takılabilir Programlama protokollerine](programming-pluggable-protocols.md)bakın.

2. Nesnenizde `WebRequest` gereksinim duyduğunuz özellik değerlerini ayarlayın. Örneğin, kimlik doğrulamasını etkinleştirmek <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> için özelliği <xref:System.Net.NetworkCredential> sınıfın bir örneğine ayarlayın:

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. Http `POST` yöntemi gibi bir istekle veri gönderilmesine izin veren bir protokol yöntemi belirtin:

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. <xref:System.Web.HttpRequest.ContentLength> Özelliği, isteğiniz için dahil ettiğiniz bayt sayısına ayarlayın. Örnek:

    ```csharp
    request.ContentLength = byteArray.Length;
    ```

    ```vb
    request.ContentLength = byteArray.Length
    ```

5. <xref:System.Web.HttpRequest.ContentType> Özelliği uygun bir değere ayarlayın. Örnek:

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. <xref:System.Net.WebRequest.GetRequestStream%2A> Yöntemi arayarak istek verilerini tutan akışı alın. Örnek:

    ```csharp
    Stream dataStream = request.GetRequestStream();
    ```

    ```vb
    Dim dataStream As Stream = request.GetRequestStream()
    ```

7. Yöntemi yle <xref:System.IO.Stream> `GetRequestStream` döndürülen nesneye verileri yazın. Örnek:

    ```csharp
    dataStream.Write(byteArray, 0, byteArray.Length);
    ```

    ```vb
    dataStream.Write(byteArray, 0, byteArray.Length)
    ```

8. <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> Yöntemi çağırarak istek akışını kapatın. Örnek:

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. Arayarak isteği sunucuya <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>gönderin. Bu yöntem, sunucunun yanıtını içeren bir nesne döndürür. Döndürülen `WebResponse` nesnenin türü, isteğin URI düzenine göre belirlenir. Örnek:

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. Nesnenizin `WebResponse` özelliklerine erişebilir veya protokole özgü özellikleri okumak için protokole özgü bir örneğe atabilirsiniz.

    Örneğin, HTTP'ye özgü özelliklere <xref:System.Net.HttpWebResponse>erişmek için `WebResponse` nesnenizi <xref:System.Net.HttpWebResponse> bir başvuruya döküm. Aşağıdaki kod örneği, yanıtla gönderilen <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> HTTP'ye özgü özelliğin nasıl görüntülenebildiğini gösterir:

    ```csharp
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)
    ```

11. Sunucu tarafından gönderilen yanıt verilerini içeren akışı <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> almak için `WebResponse` nesnenizin yöntemini arayın. Örnek:

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

12. Yanıt nesnesinden gelen verileri okuduktan sonra, <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> yöntemle kapatın veya <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yöntemle yanıt akışını kapatın. Yanıtı veya akışı kapatmazsanız, uygulamanızın sunucu bağlantıları tükenebilir ve ek istekleri işleyemez hale gelir. Yöntem `WebResponse.Close` yanıtı `Stream.Close` kapattığında aradığından, bunu yapmak zararlı olmasa `Close` da hem yanıtı hem de akış nesnelerini çağırmak gerekli değildir. Örnek:

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir web sunucusuna nasıl veri gönderilebildiğini ve yanıtındaki verileri nasıl okuyup okunduğunu gösterir:

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Internet istekleri oluşturma](creating-internet-requests.md)
- [Ağdaki akışları kullanma](using-streams-on-the-network.md)
- [Bir proxy üzerinden internete erişim](accessing-the-internet-through-a-proxy.md)
- [Veri isteme](requesting-data.md)
- [Nasıl kullanılır: WebRequest sınıfını kullanarak veri isteme](how-to-request-data-using-the-webrequest-class.md)
