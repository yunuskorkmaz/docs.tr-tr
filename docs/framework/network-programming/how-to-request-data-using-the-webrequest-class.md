---
title: 'Nasıl yapılır: İstek WebRequest sınıfı kullanarak verileri'
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
manager: markl
ms.openlocfilehash: e02ad4772d3ba84a2735a2e146a9979862d75989
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-request-data-using-the-webrequest-class"></a>Nasıl yapılır: İstek WebRequest sınıfı kullanarak verileri
Aşağıdaki yordam, örneğin, bir sunucudan bir kaynak istemek için kullanılan adımlar, bir Web sayfasına veya dosya açıklar. Kaynak bir URI tarafından tanımlanan gerekir.  
  
### <a name="to-request-data-from-a-host-server"></a>Bir ana bilgisayar sunucusundan veri istemek için  
  
1.  Oluşturma bir <xref:System.Net.WebRequest> çağırarak örneği <xref:System.Net.WebRequest.Create%2A> kaynak URI'si ile.  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  .NET Framework türetilmiş protokole özgü sınıflar sağlar **WebRequest** ve **WebResponse** ile başlayan URI için "http:", "https:''," ftp: ", ve" dosya: ". Diğer protokolleri kullanan kaynaklara erişmek için öğesinden türetilen protokole özgü sınıflar uygulamalıdır **WebRequest** ve **WebResponse**. Daha fazla bilgi için bkz: [programlama Takılabilir Protokol](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .  
  
2.  Gereksinim duyduğunuz tüm özellik değerlerini ayarlar **WebRequest**. Örneğin, kimlik doğrulamasını etkinleştirmek için ayarlar **kimlik bilgileri** örneği özelliğine <xref:System.Net.NetworkCredential> sınıfı.  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     Çoğu durumda, **WebRequest** sınıftır verileri almak yeterli. Protokole özgü özelliklerini ayarlamak ihtiyacınız varsa, ancak atamalısınız **WebRequest** protokole özgü türü. Örneğin, erişim HTTP özgü özellikleri için <xref:System.Net.HttpWebRequest>, noktaya yayın **WebRequest** için bir **HttpWebRequest** başvuru. Aşağıdaki kod örneğinde HTTP özgü ayarlanacağı gösterilmiştir <xref:System.Net.HttpWebRequest.UserAgent%2A> özelliği.  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  Sunucuya istek göndermek için çağrı <xref:System.Net.HttpWebRequest.GetResponse%2A>. Döndürülen gerçek türünü **WebResponse** nesne, istenen URI düzeni tarafından belirlenir.  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  İle tamamladıktan sonra bir <xref:System.Net.WebResponse> nesne kapatmalısınız onu çağırarak <xref:System.Net.WebResponse.Close%2A> yöntemi. Yanıt akışı yanıt nesnesinden getirildiğini, alternatif olarak, akış çağırarak kapatabilirsiniz <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yöntemi. Yanıt veya akış kapatmazsanız uygulamanızı sunucuya bağlantıları dışında çalıştırın ve ek istekleri işleyemiyor haline gelir.  
  
4.  Özelliklerini erişebilirsiniz **WebResponse** veya cast **WebResponse** bir protokole özgü örneğine protokole özgü özellikleri okunamıyor. Örneğin, erişim HTTP özgü özellikleri için <xref:System.Net.HttpWebResponse>, noktaya yayın **WebResponse** için bir **HttpWebResponse** başvuru. Aşağıdaki kod örneği ile bir yanıt gönderdi durum bilgilerini görüntülemek nasıl gösterir.  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response,HttpWebResponse).StatusDescription)  
    ```  
  
5.  Sunucu tarafından gönderilen yanıtı verilerini içeren akışı almak için <xref:System.Net.HttpWebResponse.GetResponseStream%2A> yöntemi **WebResponse**.  
  
    ```csharp  
    Stream dataStream = response.GetResponseStream();  
    ```  
  
    ```vb  
    Dim dataStream As Stream = response.GetResponseStream()  
    ```  
  
6.  Veri gelen yanıt okunduktan sonra ya da yanıt akışı kullanarak kapatmanız gerekir **Stream.Close** yöntemi veya yanıt kullanarak Kapat **WebResponse.Close** yöntemi. Bu çağrı gerekli değildir **Kapat** yanıt akışına yöntemi ve **WebResponse**, ancak bunun nedenle zararlı. **WebResponse.Close** çağrıları **Stream.Close** yanıt kapatırken.  
  
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
