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
ms.openlocfilehash: 456dbdab3070e88fe0bc6572c998ce54e3c19c00
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166962"
---
# <a name="how-to-send-data-by-using-the-webrequest-class"></a>Nasıl yapılır: WebRequest sınıfını kullanarak veri gönderme
Aşağıdaki yordam bir sunucuya veri göndermek için gereken adımları açıklar. Bu yordam, genellikle bir Web sayfasında veri göndermek için kullanılır. 
  
## <a name="to-send-data-to-a-host-server"></a>Bir konak sunucusuna veri göndermek için  
  
1.  Oluşturma bir <xref:System.Net.WebRequest> çağırarak örneği <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> bir betik veya ASP.NET sayfası gibi bir kaynağın URI'sini ile verileri kabul eder. Örneğin: 
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx")  
    ```  
  
    > [!NOTE]
    > .NET Framework türetilen protokole özgü sınıfların sağlar <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıfları ile başlayan bir URI'leri *http:*, *https:*, *ftp:* , ve *dosya:*.
    Kümesi ya da okuma protokole özgü özellikleri gerekirse dönüştürmelisiniz, <xref:System.Net.WebRequest> veya <xref:System.Net.WebResponse> protokole özgü nesne türü için nesne. Daha fazla bilgi için [takılabilir protokoller programlama](programming-pluggable-protocols.md). 
  
2.  Size gereken tüm özellik değerlerini ayarlayın, `WebRequest` nesne. Örneğin, kimlik doğrulamasını etkinleştirmek için ayarlanmış <xref:System.Net.WebRequest.Credentials%2A?displayProperty=nameWithType> örneğine özellik <xref:System.Net.NetworkCredential> sınıfı:
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
3.  Veri ile HTTP gibi bir istek gönderilmesine izin veren bir protokol yöntemini belirtin `POST` yöntemi:  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4.  Ayarlama <xref:System.Web.HttpRequest.ContentLength> özelliğini isteğinize dahil bayt sayısı. Örneğin: 
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5.  Ayarlama <xref:System.Web.HttpRequest.ContentType> özelliğini uygun bir değer. Örneğin:
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  Get ayrı tutma çağırarak verileri istek akışı <xref:System.Net.WebRequest.GetRequestStream%2A> yöntemi. Örneğin:
  
    ```csharp  
    Stream dataStream = request.GetRequestStream();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream()  
    ```  
  
7.  Veri yazılan <xref:System.IO.Stream> tarafından döndürülen nesne `GetRequestStream` yöntemi. Örneğin:
  
    ```csharp  
    dataStream.Write(byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write(byteArray, 0, byteArray.Length)  
    ```  
  
8.  İstek akışı çağırarak kapatmak <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yöntemi. Örneğin:
  
    ```csharp  
    dataStream.Close();  
    ```  
  
    ```vb  
    dataStream.Close()  
    ```  
  
9. Çağırarak sunucuya istek göndermek <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType>. Bu yöntem sunucu yanıtını içeren bir nesne döndürür. Döndürülen `WebResponse` nesnenin türü, isteğin URI düzeni tarafından belirlenir. Örneğin:
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
10. Özelliklerini erişebilir, `WebResponse` nesne veya protokole özgü özelliklerini okumak için bir protokole özgü örneğe dönüştürün. 

    Örneğin, erişim HTTP'ye özgü özellikleri için <xref:System.Net.HttpWebResponse>, noktaya yayın, `WebResponse` nesnesini bir <xref:System.Net.HttpWebResponse> başvuru. Aşağıdaki kod örneği, HTTP özgü görüntülenecek gösterilmektedir <xref:System.Net.HttpWebResponse.StatusDescription%2A?displayProperty=nameWithType> Yanıtta gönderilen özelliği:
  
    ```csharp  
    Console.WriteLine(((HttpWebResponse)response).StatusDescription);    
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. Sunucu tarafından gönderilen yanıt verilerini içeren akış almak için arama <xref:System.Net.WebResponse.GetResponseStream%2A?displayProperty=nameWithType> yöntemi, `WebResponse` nesne. Örneğin:
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
12. Yanıt nesnesinden verileri okuduktan sonra ya da ile kapatmak <xref:System.Net.WebResponse.Close%2A?displayProperty=nameWithType> yöntemi veya kapanış yanıt akışı ile <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yöntemi. Yanıt ya da akış kapatmayın, uygulamanızın sunucu bağlantılarını dışında çalıştırabilir ve ek istekleri işleyemediğinden haline gelir. Çünkü `WebResponse.Close` yöntem çağrılarını `Stream.Close` yanıtı kapatır, çağrı gerekli değildir `Close` nesnelerde yanıt ve akış bunu yaparsanız bu nedenle zararlı olmasa da. Örneğin:
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a>Örnek  
  
Aşağıdaki kod örneği, bir web sunucusuna veri göndermek ve kendi yanıt verileri okumak gösterilmektedir:  

[!code-csharp[SendDataUsingWebRequest](../../../samples/snippets/csharp/VS_Snippets_Network/SendDataUsingWebRequest/cs/WebRequestPostExample.cs)]
[!code-vb[SendDataUsingWebRequest](../../../samples/snippets/visualbasic/VS_Snippets_Network/SendDataUsingWebRequest/vb/WebRequestPostExample.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [İnternet istekleri oluşturma](creating-internet-requests.md)
- [Ağda akışları kullanma](using-streams-on-the-network.md)
- [İnternet'e bir proxy üzerinden erişme](accessing-the-internet-through-a-proxy.md)
- [Veri isteme](requesting-data.md)
- [Nasıl yapılır: WebRequest sınıfını kullanarak veri isteme](how-to-request-data-using-the-webrequest-class.md)
