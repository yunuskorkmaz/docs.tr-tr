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
# <a name="how-to-request-data-by-using-the-webrequest-class"></a>Nasıl kullanılır: WebRequest sınıfını kullanarak veri isteme

Aşağıdaki yordam, bir sunucudan Web sayfası veya dosya gibi bir kaynak istemek için adımları açıklar. Kaynak bir URI tarafından tanımlanmalıdır.

## <a name="to-request-data-from-a-host-server"></a>Ana bilgisayar sunucusundan veri istemek için

1. Kaynağın <xref:System.Net.WebRequest> URI'si ile arayarak <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> bir örnek oluşturun. Örnek:

    ```csharp
    WebRequest request = WebRequest.Create("https://docs.microsoft.com");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("https://docs.microsoft.com")
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

3. Arayarak isteği sunucuya <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>gönderin. Bu yöntem, sunucunun yanıtını içeren bir nesne döndürür. Döndürülen <xref:System.Net.WebResponse> nesnenin türü, isteğin URI düzenine göre belirlenir. Örnek:

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. Nesnenizin `WebResponse` özelliklerine erişebilir veya protokole özgü özellikleri okumak için protokole özgü bir örneğe atabilirsiniz.

    Örneğin, HTTP'ye özgü özelliklere <xref:System.Net.HttpWebResponse>erişmek için `WebResponse` nesnenizi `HttpWebResponse` bir başvuruya döküm. Aşağıdaki kod örneği, yanıtla gönderilen <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> HTTP'ye özgü özelliğin nasıl görüntülenebildiğini gösterir:

    ```csharp
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)
    ```

5. Sunucu tarafından gönderilen yanıt verilerini içeren akışı <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> almak için yöntemi arayın. Örnek:

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

6. Yanıt nesnesinden gelen verileri okuduktan sonra, <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> yöntemle kapatın veya <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yöntemle yanıt akışını kapatın. Yanıt nesnesini veya akışı kapatmazsanız, uygulamanız sunucu bağlantıları tükenebilir ve ek istekleri işleyemez hale gelebilir. Yöntem `WebResponse.Close` yanıtı `Stream.Close` kapattığında aradığından, bunu yapmak zararlı olmasa `Close` da hem yanıtı hem de akış nesnelerini çağırmak gerekli değildir. Örnek:

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, bir web sunucusuna nasıl istek oluşturulup yanıttaki verileri nasıl okuyabilirsiniz:

[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Internet istekleri oluşturma](creating-internet-requests.md)
- [Ağdaki Akışları Kullanma](using-streams-on-the-network.md)
- [Bir proxy üzerinden internete erişim](accessing-the-internet-through-a-proxy.md)
- [Veri isteme](requesting-data.md)
- [Nasıl kullanılır: WebRequest sınıfını kullanarak veri gönderme](how-to-send-data-using-the-webrequest-class.md)
