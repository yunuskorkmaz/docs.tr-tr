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
# <a name="how-to-send-data-by-using-the-webrequest-class"></a>Nasıl yapılır: WebRequest sınıfını kullanarak veri gönderme

Aşağıdaki yordam bir sunucusuna veri gönderme adımlarını açıklamaktadır. Bu yordam yaygın olarak bir Web sayfasına veri göndermek için kullanılır.

## <a name="to-send-data-to-a-host-server"></a>Bir konak sunucusuna veri göndermek için

1. Veri kabul <xref:System.Net.WebRequest> eden bir betik <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> veya ASP.NET sayfası gibi bir kaynağın URI 'siyle çağırarak bir örnek oluşturun. Örneğin:

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > .NET Framework <xref:System.Net.WebRequest> , *http:* , *https:* , *FTP:* ve <xref:System.Net.WebResponse> *Dosya:* ile başlayan URI 'ler için ve sınıflarından türetilmiş protokole özgü sınıflar sağlar.

    Protokole özgü özellikleri ayarlamanız veya okumanız gerekiyorsa, <xref:System.Net.WebRequest> veya <xref:System.Net.WebResponse> nesnesini protokole özgü bir nesne türüne atamalısınız. Daha fazla bilgi için bkz. [takılabilir protokolleri programlama](programming-pluggable-protocols.md).

2. `WebRequest` Nesneniz için ihtiyacınız olan herhangi bir özellik değerini ayarlayın. Örneğin, kimlik doğrulamasını etkinleştirmek için, <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> özelliğini <xref:System.Net.NetworkCredential> sınıfının bir örneğine ayarlayın:

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. HTTP `POST` yöntemi gibi bir istekle veri gönderilmesine izin veren bir protokol yöntemi belirtin:

    ```csharp
    request.Method = "POST";
    ```

    ```vb
    request.Method = "POST"
    ```

4. Özelliği, <xref:System.Web.HttpRequest.ContentLength> isteğinize dahil ettiğiniz bayt sayısına ayarlayın. Örneğin:

    ```csharp
    request.ContentLength = byteArray.Length;
    ```

    ```vb
    request.ContentLength = byteArray.Length
    ```

5. <xref:System.Web.HttpRequest.ContentType> Özelliği uygun bir değere ayarlayın. Örneğin:

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. <xref:System.Net.WebRequest.GetRequestStream%2A> Yöntemini çağırarak istek verilerini tutan akışı alın. Örneğin:

    ```csharp
    Stream dataStream = request.GetRequestStream();
    ```

    ```vb
    Dim dataStream As Stream = request.GetRequestStream()
    ```

7. Yöntemi tarafından döndürülen <xref:System.IO.Stream> nesneye verileri yazın. `GetRequestStream` Örneğin:

    ```csharp
    dataStream.Write(byteArray, 0, byteArray.Length);
    ```

    ```vb
    dataStream.Write(byteArray, 0, byteArray.Length)
    ```

8. <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> Yöntemini çağırarak istek akışını kapatın. Örneğin:

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. Çağırarak <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>isteği sunucuya gönderin. Bu yöntem, sunucunun yanıtını içeren bir nesne döndürür. Döndürülen `WebResponse` nesnenin türü, isteğin URI 'si düzenine göre belirlenir. Örneğin:

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. Bir protokole özgü özellikleri okumak için `WebResponse` nesnenizin özelliklerine erişebilir veya protokole özgü bir örneğe çevirebilirsiniz.

    Örneğin, http 'ye özgü özelliklerine <xref:System.Net.HttpWebResponse>erişmek için, `WebResponse` nesnenizin başvurusunu bir <xref:System.Net.HttpWebResponse> başvuruya atayın. Aşağıdaki kod örneği, bir Yanıt ile gönderilen http 'e özgü <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> özelliğin nasıl görüntüleneceğini göstermektedir:

    ```csharp
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)
    ```

11. Sunucu tarafından gönderilen yanıt verilerini içeren akışı almak için, <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> `WebResponse` nesnenizin yöntemini çağırın. Örneğin:

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

12. Yanıt nesnesinden verileri okuduktan sonra, <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> yöntemi ile kapatın ya da <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yöntemi ile yanıt akışını kapatın. Yanıtı veya akışı kapatmazsanız, uygulamanızın sunucu bağlantısı tükenebilir ve ek istekleri işleyemez. Yöntemi yanıtı kapattığı zaman `Stream.Close` çağırdığı için, hem yanıt hem de akış nesnelerinde çağırmak `Close` gerekli değildir, ancak bunu zararlı değildir. `WebResponse.Close` Örneğin:

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir Web sunucusuna nasıl veri gönderileceğini ve yanıttaki verileri nasıl okuyakullanacağınızı gösterir:

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [İnternet istekleri oluşturma](creating-internet-requests.md)
- [Ağda akışlar kullanma](using-streams-on-the-network.md)
- [Bir ara sunucu üzerinden İnternet 'e erişme](accessing-the-internet-through-a-proxy.md)
- [Veri isteme](requesting-data.md)
- [Nasıl yapılır: WebRequest sınıfını kullanarak veri isteme](how-to-request-data-using-the-webrequest-class.md)
