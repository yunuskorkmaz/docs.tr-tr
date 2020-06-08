---
title: 'Nasıl yapılır: WebRequest sınıfını kullanarak veri ISTEME'
description: .NET Framework Web sayfası veya dosya gibi bir kaynağı sunucudan WebRequest sınıfını kullanarak bir sunucudan isteme hakkında bilgi edinin.
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
ms.openlocfilehash: 5dcc1a7dad226288e3f74969b86e2dd457c0eed0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502476"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a>Nasıl yapılır: WebRequest sınıfını kullanarak veri ISTEME

Aşağıdaki yordam bir sunucudan bir Web sayfası veya dosya gibi bir kaynak isteme adımlarını açıklamaktadır. Kaynağın bir URI ile tanımlanması gerekir.

## <a name="to-request-data-from-a-host-server"></a>Bir konak sunucusundan veri istemek için

1. <xref:System.Net.WebRequest> <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> BIR kaynağın URI 'siyle çağırarak bir örnek oluşturun. Örneğin:

    ```csharp
    WebRequest request = WebRequest.Create("https://docs.microsoft.com");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("https://docs.microsoft.com")
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

3. Çağırarak isteği sunucuya gönderin <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> . Bu yöntem, sunucunun yanıtını içeren bir nesne döndürür. Döndürülen <xref:System.Net.WebResponse> nesnenin türü, isteğin URI 'si düzenine göre belirlenir. Örneğin:

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. `WebResponse`Bir protokole özgü özellikleri okumak için nesnenizin özelliklerine erişebilir veya protokole özgü bir örneğe çevirebilirsiniz.

    Örneğin, HTTP 'ye özgü özelliklerine erişmek için <xref:System.Net.HttpWebResponse> , `WebResponse` nesnenizin `HttpWebResponse` başvurusunu bir başvuruya atayın. Aşağıdaki kod örneği, <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> bir Yanıt ile GÖNDERILEN http 'e özgü özelliğin nasıl görüntüleneceğini göstermektedir:

    ```csharp
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);
    ```

    ```vb
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)
    ```

5. Sunucu tarafından gönderilen yanıt verilerini içeren akışı almak için <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> yöntemini çağırın. Örneğin:

    ```csharp
    Stream dataStream = response.GetResponseStream();
    ```

    ```vb
    Dim dataStream As Stream = response.GetResponseStream()
    ```

6. Yanıt nesnesinden verileri okuduktan sonra, yöntemi ile kapatın <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> ya da yöntemi ile yanıt akışını kapatın <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> . Yanıt nesnesini veya akışı kapatmazsanız, uygulamanız sunucu bağlantılarının tükenebilir ve ek istekleri işleyemez. `WebResponse.Close`Yöntemi `Stream.Close` yanıtı kapattığı zaman çağırdığı için, `Close` hem yanıt hem de akış nesnelerinde çağırmak gerekli değildir, ancak bunu zararlı değildir. Örneğin:

    ```csharp
    response.Close();
    ```

    ```vb
    response.Close()
    ```

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, bir Web sunucusuna nasıl istek oluşturulacağını ve yanıttaki verileri nasıl okuyakullanacağınızı gösterir:

[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [İnternet istekleri oluşturma](creating-internet-requests.md)
- [Ağda akışlar kullanma](using-streams-on-the-network.md)
- [Bir ara sunucu üzerinden İnternet 'e erişme](accessing-the-internet-through-a-proxy.md)
- [Veri isteme](requesting-data.md)
- [Nasıl yapılır: WebRequest sınıfını kullanarak veri gönderme](how-to-send-data-using-the-webrequest-class.md)
