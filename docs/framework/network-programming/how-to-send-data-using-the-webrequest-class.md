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
# <a name="how-to-send-data-by-using-the-webrequest-class"></a>Nasıl yapılır: WebRequest sınıfını kullanarak veri gönderme

Aşağıdaki yordam bir sunucusuna veri gönderme adımlarını açıklamaktadır. Bu yordam yaygın olarak bir Web sayfasına veri göndermek için kullanılır.

## <a name="to-send-data-to-a-host-server"></a>Bir konak sunucusuna veri göndermek için

1. <xref:System.Net.WebRequest> <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> Veri kabul eden bir betik veya ASP.NET sayfası gibi BIR kaynağın URI 'siyle çağırarak bir örnek oluşturun. Örneğin:

    ```csharp
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")
    ```

    > [!NOTE]
    > .NET Framework, <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> *http:*, *https:*, *FTP:* ve *Dosya:* ile başlayan URI 'ler için ve sınıflarından türetilmiş protokole özgü sınıflar sağlar.

    Protokole özgü özellikleri ayarlamanız veya okumanız gerekiyorsa, <xref:System.Net.WebRequest> veya <xref:System.Net.WebResponse> nesnesini protokole özgü bir nesne türüne atamalısınız. Daha fazla bilgi için bkz. [takılabilir protokolleri programlama](programming-pluggable-protocols.md).

2. Nesneniz için ihtiyacınız olan herhangi bir özellik değerini ayarlayın `WebRequest` . Örneğin, kimlik doğrulamasını etkinleştirmek için, <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> özelliğini sınıfının bir örneğine ayarlayın <xref:System.Net.NetworkCredential> :

    ```csharp
    request.Credentials = CredentialCache.DefaultCredentials;
    ```

    ```vb
    request.Credentials = CredentialCache.DefaultCredentials
    ```

3. HTTP yöntemi gibi bir istekle veri gönderilmesine izin veren bir protokol yöntemi belirtin `POST` :

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

5. <xref:System.Web.HttpRequest.ContentType>Özelliği uygun bir değere ayarlayın. Örneğin:

    ```csharp
    request.ContentType = "application/x-www-form-urlencoded";
    ```

    ```vb
    request.ContentType = "application/x-www-form-urlencoded"
    ```

6. Yöntemini çağırarak istek verilerini tutan akışı alın <xref:System.Net.WebRequest.GetRequestStream%2A> . Örneğin:

    ```csharp
    Stream dataStream = request.GetRequestStream();
    ```

    ```vb
    Dim dataStream As Stream = request.GetRequestStream()
    ```

7. <xref:System.IO.Stream>Yöntemi tarafından döndürülen nesneye verileri yazın `GetRequestStream` . Örneğin:

    ```csharp
    dataStream.Write(byteArray, 0, byteArray.Length);
    ```

    ```vb
    dataStream.Write(byteArray, 0, byteArray.Length)
    ```

8. Yöntemini çağırarak istek akışını kapatın <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> . Örneğin:

    ```csharp
    dataStream.Close();
    ```

    ```vb
    dataStream.Close()
    ```

9. Çağırarak isteği sunucuya gönderin <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> . Bu yöntem, sunucunun yanıtını içeren bir nesne döndürür. Döndürülen `WebResponse` nesnenin türü, isteğin URI 'si düzenine göre belirlenir. Örneğin:

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

10. `WebResponse`Bir protokole özgü özellikleri okumak için nesnenizin özelliklerine erişebilir veya protokole özgü bir örneğe çevirebilirsiniz.

    Örneğin, HTTP 'ye özgü özelliklerine erişmek için <xref:System.Net.HttpWebResponse> , `WebResponse` nesnenizin <xref:System.Net.HttpWebResponse> başvurusunu bir başvuruya atayın. Aşağıdaki kod örneği, <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> bir Yanıt ile GÖNDERILEN http 'e özgü özelliğin nasıl görüntüleneceğini göstermektedir:

    ```csharp
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)
    ```

11. Sunucu tarafından gönderilen yanıt verilerini içeren akışı almak için, <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> nesnenizin yöntemini çağırın `WebResponse` . Örneğin:

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

12. Yanıt nesnesinden verileri okuduktan sonra, yöntemi ile kapatın <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> ya da yöntemi ile yanıt akışını kapatın <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> . Yanıtı veya akışı kapatmazsanız, uygulamanızın sunucu bağlantısı tükenebilir ve ek istekleri işleyemez. `WebResponse.Close`Yöntemi `Stream.Close` yanıtı kapattığı zaman çağırdığı için, `Close` hem yanıt hem de akış nesnelerinde çağırmak gerekli değildir, ancak bunu zararlı değildir. Örneğin:

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
- [Nasıl yapılır: WebRequest sınıfını kullanarak veri ISTEME](how-to-request-data-using-the-webrequest-class.md)
