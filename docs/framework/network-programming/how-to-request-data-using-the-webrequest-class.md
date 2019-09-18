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
ms.openlocfilehash: e670a2a503ce704eff847e9e0b3ee340ab52fe62
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048160"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a>Nasıl yapılır: WebRequest sınıfını kullanarak veri isteme

Aşağıdaki yordam bir sunucudan bir Web sayfası veya dosya gibi bir kaynak isteme adımlarını açıklamaktadır. Kaynağın bir URI ile tanımlanması gerekir.

## <a name="to-request-data-from-a-host-server"></a>Bir konak sunucusundan veri istemek için

1. Bir kaynağın <xref:System.Net.WebRequest> URI 'siyle çağırarak <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> bir örnek oluşturun. Örneğin:

    ```csharp
    WebRequest request = WebRequest.Create("https://docs.microsoft.com");
    ```

    ```vb
    Dim request as WebRequest = WebRequest.Create("https://docs.microsoft.com")
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

3. Çağırarak <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>isteği sunucuya gönderin. Bu yöntem, sunucunun yanıtını içeren bir nesne döndürür. Döndürülen <xref:System.Net.WebResponse> nesnenin türü, isteğin URI 'si düzenine göre belirlenir. Örneğin:

    ```csharp
    WebResponse response = request.GetResponse();
    ```

    ```vb
    Dim response As WebResponse = request.GetResponse()
    ```

4. Bir protokole özgü özellikleri okumak için `WebResponse` nesnenizin özelliklerine erişebilir veya protokole özgü bir örneğe çevirebilirsiniz.

    Örneğin, http 'ye özgü özelliklerine <xref:System.Net.HttpWebResponse>erişmek için, `WebResponse` nesnenizin başvurusunu bir `HttpWebResponse` başvuruya atayın. Aşağıdaki kod örneği, bir Yanıt ile gönderilen http 'e özgü <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> özelliğin nasıl görüntüleneceğini göstermektedir:

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

6. Yanıt nesnesinden verileri okuduktan sonra, <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> yöntemi ile kapatın ya da <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yöntemi ile yanıt akışını kapatın. Yanıt nesnesini veya akışı kapatmazsanız, uygulamanız sunucu bağlantılarının tükenebilir ve ek istekleri işleyemez. Yöntemi yanıtı kapattığı zaman `Stream.Close` çağırdığı için, hem yanıt hem de akış nesnelerinde çağırmak `Close` gerekli değildir, ancak bunu zararlı değildir. `WebResponse.Close` Örneğin:

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
