---
title: "Nasıl yapılır: WebRequest sınıfı kullanarak veri gönderme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: b4cc524b3b3c1dbe42f3fe3926ed44c1e917e871
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-send-data-using-the-webrequest-class"></a>Nasıl yapılır: WebRequest sınıfı kullanarak veri gönderme
Aşağıdaki yordamda bir sunucuya veri göndermek için kullanılan adımlar açıklanmaktadır. Bu yordam, genellikle bir Web sayfasında veri göndermek için kullanılır.  
  
### <a name="to-send-data-to-a-host-server"></a>Bir ana bilgisayar sunucusuna veri göndermek için  
  
1.  Oluşturma bir <xref:System.Net.WebRequest> çağırarak örneği <xref:System.Net.WebRequest.Create%2A> verileri, örneğin kabul kaynak, bir komut dosyası veya ASP.NET sayfası URI ile.  
  
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
  
     Çoğu durumda, **WebRequest** örneğinin kendisi veri göndermek yeterli. Protokole özgü özelliklerini ayarlamak ihtiyacınız varsa, ancak atamalısınız **WebRequest** protokole özgü türü. Örneğin, erişim HTTP özgü özellikleri için <xref:System.Net.HttpWebRequest>, noktaya yayın **WebRequest** için bir **HttpWebRequest** başvuru. Aşağıdaki kod örneğinde HTTP özgü ayarlanacağı gösterilmiştir <xref:System.Net.HttpWebRequest.UserAgent%2A> özelliği.  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  HTTP gibi bir istekle gönderilmesi için veri izin veren bir protokol yöntemini belirtin **POST** yöntemi.  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4.  Ayarlama **ContentLength** özelliği.  
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5.  Ayarlama **ContentType** uygun bir değere özelliği.  
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  Get ayrı tutma çağırarak veri istek akışı <xref:System.Net.WebRequest.GetRequestStream%2A> yöntemi.  
  
    ```csharp  
    Stream dataStream = request.GetRequestStream ();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream ()  
    ```  
  
7.  Veri yazma <xref:System.IO.Stream> bu yöntem tarafından döndürülen nesne.  
  
    ```csharp  
    dataStream.Write (byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write (byteArray, 0, byteArray.Length)  
    ```  
  
8.  İstek akışı çağırarak kapatmak **Stream.Close** yöntemi.  
  
    ```csharp  
    dataStream.Close ();  
    ```  
  
    ```vb  
    dataStream.Close ()  
    ```  
  
9. Çağırarak sunucuya istek göndermek <xref:System.Net.WebRequest.GetResponse%2A>. Bu yöntem, sunucu yanıtı içeren bir nesne döndürür. Döndürülen <xref:System.Net.WebResponse> nesnenin türü, isteğin URI düzeni tarafından belirlenir.  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  İle tamamladıktan sonra bir <xref:System.Net.WebResponse> nesne kapatmalısınız onu çağırarak <xref:System.Net.WebResponse.Close%2A> yöntemi. Yanıt akışı yanıt nesnesinden getirildiğini, alternatif olarak, akış çağırarak kapatabilirsiniz <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> yöntemi. Yanıt veya akış kapatmazsanız uygulamanızı sunucuya bağlantıları dışında çalıştırın ve ek istekleri işleyemiyor haline gelir.  
  
10. Özelliklerini erişebilirsiniz **WebResponse** veya cast **WebResponse** bir protokole özgü örneğine protokole özgü özellikleri okunamıyor. Örneğin, erişim HTTP özgü özellikleri için <xref:System.Net.HttpWebResponse>, noktaya yayın **WebResponse** için bir **HttpWebResponse** başvuru.  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. Sunucu tarafından gönderilen yanıtı verilerini içeren akışı almak için arama <xref:System.Net.WebResponse.GetResponseStream%2A> yöntemi **WebResponse**.  
  
    ```csharp  
    Stream data = response.GetResponseStream;  
    ```  
  
    ```vb  
    Dim data As Stream = response.GetResponseStream  
    ```  
  
12. Veri gelen yanıt okunduktan sonra ya da yanıt akışı kullanarak kapatmanız gerekir **Stream.Close** yöntemi veya yanıt kullanarak Kapat **WebResponse.Close** yöntemi. Bu çağrı gerekli değildir **Kapat** yanıt akışına yöntemi ve **WebResponse**, ancak bunun nedenle zararlı.  
  
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
    public class WebRequestPostExample  
    {  
        public static void Main ()  
        {  
            // Create a request using a URL that can receive a post.   
            WebRequest request = WebRequest.Create ("http://www.contoso.com/PostAccepter.aspx ");  
            // Set the Method property of the request to POST.  
            request.Method = "POST";  
            // Create POST data and convert it to a byte array.  
            string postData = "This is a test that posts this string to a Web server.";  
            byte[] byteArray = Encoding.UTF8.GetBytes (postData);  
            // Set the ContentType property of the WebRequest.  
            request.ContentType = "application/x-www-form-urlencoded";  
            // Set the ContentLength property of the WebRequest.  
            request.ContentLength = byteArray.Length;  
            // Get the request stream.  
            Stream dataStream = request.GetRequestStream ();  
            // Write the data to the request stream.  
            dataStream.Write (byteArray, 0, byteArray.Length);  
            // Close the Stream object.  
            dataStream.Close ();  
            // Get the response.  
            WebResponse response = request.GetResponse ();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream ();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader (dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd ();  
            // Display the content.  
            Console.WriteLine (responseFromServer);  
            // Clean up the streams.  
            reader.Close ();  
            dataStream.Close ();  
            response.Close ();  
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
    Public Class WebRequestPostExample  
  
        Public Shared Sub Main()  
            ' Create a request using a URL that can receive a post.   
            Dim request As WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx ")  
            ' Set the Method property of the request to POST.  
            request.Method = "POST"  
            ' Create POST data and convert it to a byte array.  
            Dim postData As String = "This is a test that posts this string to a Web server."  
            Dim byteArray As Byte() = Encoding.UTF8.GetBytes(postData)  
            ' Set the ContentType property of the WebRequest.  
            request.ContentType = "application/x-www-form-urlencoded"  
            ' Set the ContentLength property of the WebRequest.  
            request.ContentLength = byteArray.Length  
            ' Get the request stream.  
            Dim dataStream As Stream = request.GetRequestStream()  
            ' Write the data to the request stream.  
            dataStream.Write(byteArray, 0, byteArray.Length)  
            ' Close the Stream object.  
            dataStream.Close()  
            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
            ' Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream()  
            ' Open the stream using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  
            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  
            ' Clean up the streams.  
            reader.Close()  
            dataStream.Close()  
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
 [Nasıl yapılır: WebRequest Sınıfını Kullanarak Veri İsteme](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)
