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
ms.openlocfilehash: 1d8f501e90f3942bbfd95fc06e9fdd79d8f6430e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642535"
---
# <a name="how-to-request-data-by-using-the-webrequest-class"></a>Nasıl yapılır: WebRequest sınıfını kullanarak veri isteme
Aşağıdaki yordamda, bir Web sayfası veya bir dosya gibi bir kaynak sunucudan istemek için adımlar açıklanmaktadır. Kaynak URI tarafından tanımlanması gerekir.  
  
## <a name="to-request-data-from-a-host-server"></a>Bir konak sunucusundan veri istemek için  
  
1. Oluşturma bir <xref:System.Net.WebRequest> çağırarak örneği <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> bir kaynağın URI'sini ile. Örneğin: 
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/default.html");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/default.html")  
    ```  
  
    > [!NOTE]
    > .NET Framework türetilen protokole özgü sınıfların sağlar <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları ile başlayan bir URI'leri *http:*, *https:*, *ftp:* , ve *dosya:*.
    Kümesi ya da okuma protokole özgü özellikleri gerekirse dönüştürmelisiniz, <xref:System.Net.WebRequest> veya <xref:System.Net.WebResponse> protokole özgü nesne türü için nesne. Daha fazla bilgi için [takılabilir protokoller programlama](programming-pluggable-protocols.md). 
  
2. Size gereken tüm özellik değerlerini ayarlayın, `WebRequest` nesne. Örneğin, kimlik doğrulamasını etkinleştirmek için ayarlanmış <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> örneğine özellik <xref:System.Net.NetworkCredential> sınıfı:  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
3. Çağırarak sunucuya istek göndermek <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>. Bu yöntem sunucu yanıtını içeren bir nesne döndürür. Döndürülen <xref:System.Net.WebResponse> nesnenin türü, isteğin URI düzeni tarafından belirlenir. Örneğin:
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
4. Özelliklerini erişebilir, `WebResponse` nesne veya protokole özgü özelliklerini okumak için bir protokole özgü örneğe dönüştürün. 

    Örneğin, erişim HTTP'ye özgü özellikleri için <xref:System.Net.HttpWebResponse>, noktaya yayın, `WebResponse` nesnesini bir `HttpWebResponse` başvuru. Aşağıdaki kod örneği, HTTP özgü görüntülenecek gösterilmektedir <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> Yanıtta gönderilen özelliği:
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5. Sunucu tarafından gönderilen yanıt verilerini içeren akış almak için arama <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> yöntemi. Örneğin:  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6. Yanıt nesnesinden verileri okuduktan sonra ya da ile kapatmak <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> yöntemi veya kapanış yanıt akışı ile <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yöntemi. Yanıt nesnesini ya da akış kapatmayın, uygulamanızın sunucu bağlantılarını dışında çalıştırabilir ve ek istekleri işleyemediğinden haline gelir. Çünkü `WebResponse.Close` yöntem çağrılarını `Stream.Close` yanıtı kapatır, çağrı gerekli değildir `Close` nesnelerde yanıt ve akış bunu yaparsanız bu nedenle zararlı olmasa da. Örneğin:
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a>Örnek  

Aşağıdaki kod örneği, bir web sunucusu için bir istek oluşturun ve kendi yanıt verileri okumak gösterilmektedir:  
  
[!code-csharp[RequestDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/RequestDataUsingWebRequest/cs/WebRequestGetExample.cs)]
[!code-vb[RequestDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/RequestDataUsingWebRequest/vb/WebRequestGetExample.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [İnternet istekleri oluşturma](creating-internet-requests.md)
- [Ağda akışları kullanma](using-streams-on-the-network.md)
- [İnternet'e bir proxy üzerinden erişme](accessing-the-internet-through-a-proxy.md)
- [Veri isteme](requesting-data.md)
- [Nasıl yapılır: WebRequest sınıfını kullanarak veri gönderme](how-to-send-data-using-the-webrequest-class.md)
