---
title: 'Nasıl yapılır: WebRequest sınıfını kullanarak veri isteme'
ms.date: 03/30/2017
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 8928ce8790f58b6920c16cbfd9fc8d9aa6644a44
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47197831"
---
# <a name="how-to-request-data-using-the-webrequest-class"></a>Nasıl yapılır: WebRequest sınıfını kullanarak veri isteme
Aşağıdaki yordamda, bir kaynak, örneğin, bir sunucudan istemek için kullanılan adımlarla, bir Web sayfası veya dosya açıklanmaktadır. Kaynak URI tarafından tanımlanması gerekir.  
  
### <a name="to-request-data-from-a-host-server"></a>Bir konak sunucusundan veri istemek için  
  
1.  Oluşturma bir <xref:System.Net.WebRequest> çağırarak örneği <xref:System.Net.WebRequest.Create%2A> kaynağın URI'sini ile.  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  .NET Framework türetilen protokole özgü sınıfların sağlar **WebRequest** ve **WebResponse** ile başlayan bir URI'leri için "http:", "https:''," ftp: ", ve" dosya: ". Diğer protokoller kullanarak kaynaklara erişmeye öğesinden türetilen protokole özgü sınıfların uygulamalıdır **WebRequest** ve **WebResponse**. Daha fazla bilgi için [takılabilir protokoller programlama](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .  
  
2.  Size gereken tüm özellik değerlerini ayarlamak **WebRequest**. Örneğin, kimlik doğrulamasını etkinleştirmek için ayarlanmış **kimlik bilgilerini** örneğine özellik <xref:System.Net.NetworkCredential> sınıfı.  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     Çoğu durumda **WebRequest** sınıfı, veri almak yeterli. Ancak, protokole özgü özelliklerini ayarlamak gerekiyorsa dönüştürmelisiniz **WebRequest** protokole özgü türü. Örneğin, erişim HTTP'ye özgü özellikleri için <xref:System.Net.HttpWebRequest>, noktaya yayın **WebRequest** için bir **HttpWebRequest** başvuru. Aşağıdaki kod örneği, HTTP özgü ayarlanacak gösterilmektedir <xref:System.Net.HttpWebRequest.UserAgent%2A> özelliği.  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  Sunucuya istek göndermek için arama <xref:System.Net.HttpWebRequest.GetResponse%2A>. Gerçek türü döndürülen **WebResponse** nesne, istenen URI'nin şeması tarafından belirlenir.  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  İle tamamladıktan sonra bir <xref:System.Net.WebResponse> nesne kapatmalısınız bunu çağırarak <xref:System.Net.WebResponse.Close%2A> yöntemi. Yanıt nesneden yanıt akışına edindiğiniz, alternatif olarak, akış çağırarak kapatabilirsiniz <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yöntemi. Yanıt ya da akış kapatmazsanız uygulamanız bağlantılar dışında sunucuya çalıştırın ve ek istekleri işleyemediğinden haline gelir.  
  
4.  Özelliklerini erişebileceğiniz **WebResponse** veya dönüştürme **WebResponse** protokole özgü özelliklerini okumak için bir protokole özgü örneğine. Örneğin, erişim HTTP'ye özgü özellikleri için <xref:System.Net.HttpWebResponse>, noktaya yayın **WebResponse** için bir **HttpWebResponse** başvuru. Aşağıdaki kod örneği, yanıtta gönderilen durum bilgilerini görüntülemek gösterilmektedir.  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  Sunucu tarafından gönderilen yanıt verilerini içeren akış almak için kullanın <xref:System.Net.HttpWebResponse.GetResponseStream%2A> yöntemi **WebResponse**.  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  Yanıttan verileri okuduktan sonra ya da yanıt akışı kullanılarak kapatmalısınız **Stream.Close** yöntemi veya yanıtı kullanma Kapat **WebResponse.Close** yöntemi. Bu çağrı gerekli değildir **Kapat** yanıt akışında yöntemi ve **WebResponse**, ancak bunu yaparsanız bu nedenle zararlı. **WebResponse.Close** çağrıları **Stream.Close** yanıt kapatırken.  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a>Örnek  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestGetExample  
    {  
        public static void Main()  
        {  
            // Create a request for the URL.   
            WebRequest request = WebRequest.Create(  
              "http://www.contoso.com/default.html");  
            // If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials;  
            // Get the response.  
            WebResponse response = request.GetResponse();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            Stream dataStream = response.GetResponseStream();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader(dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd();  
            // Display the content.  
            Console.WriteLine(responseFromServer);  
            // Clean up the streams and the response.  
            reader.Close();  
            response.Close();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Net  
Imports System.Text  
Namespace Examples.System.Net  
    Public Class WebRequestGetExample  
  
        Public Shared Sub Main()  
            ' Create a request for the URL.   
            Dim request As WebRequest = _  
              WebRequest.Create("http://www.contoso.com/default.html")  
            ' If required by the server, set the credentials.  
            request.Credentials = CredentialCache.DefaultCredentials  
            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
            ' Get the stream containing content returned by the server.  
            Dim dataStream As Stream = response.GetResponseStream()  
            ' Open the stream using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  
            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  
            ' Clean up the streams and the response.  
            reader.Close()  
            response.Close()  
        End Sub   
    End Class   
End Namespace  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İnternet İstekleri Oluşturma](../../../docs/framework/network-programming/creating-internet-requests.md)  
 [Ağda Akışları Kullanma](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [Ara Sunucu Üzerinden İnternet Erişimi](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Veri İsteme](../../../docs/framework/network-programming/requesting-data.md)  
 [Nasıl yapılır: WebRequest Sınıfını Kullanarak Veri Gönderme](../../../docs/framework/network-programming/how-to-send-data-using-the-webrequest-class.md)
