---
title: "Nasıl yapılır: WCF REST Programlama Modeli Kullanarak Rastgele Verileri Kabul Eden Bir Hizmet Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e566c15a-b600-4e4a-be3a-4af43e767dae
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 170149f5a6c495b3f22b9fd30f79ecdda87789b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-service-that-accepts-arbitrary-data-using-the-wcf-rest-programming-model"></a>Nasıl yapılır: WCF REST Programlama Modeli Kullanarak Rastgele Verileri Kabul Eden Bir Hizmet Oluşturma
Bazen geliştiriciler, veriler bir hizmeti işleminin nasıl döndürülür, tam denetimi olmalıdır. Bir hizmet işlemi tarafından desteklenmeyen bir biçimde veri döndürmesi gerekir, bu durumda[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Bu konuda ele alınmıştır kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] rastgele verileri alan bir hizmet oluşturmak için REST programlama modeli.  
  
### <a name="to-implement-the-service-contract"></a>Hizmet sözleşmesini uygulama  
  
1.  Hizmet sözleşmesi tanımlayın. Rastgele verileri alan işlem türünün bir parametresi olmalıdır <xref:System.IO.Stream>. Ayrıca, bu parametre istek gövdesinde geçirilen yalnızca parametresi olmalıdır. Bu örnekte açıklanan işlemi aynı zamanda bir filename parametresi alır. Bu parametre istek URL'si içinde geçirilir. Parametre içinde URL belirterek geçirilen belirtebilirsiniz bir <xref:System.UriTemplate> içinde <xref:System.ServiceModel.Web.WebInvokeAttribute>. URI çağırmak için kullanılan bu durumda, "UploadFile/bazı-dosya adı" Bu yöntem sona erer. URI şablonunu "{filename}" bölümünü filename parametresi işlemi için işlem çağırmak için kullanılan URI içinde geçirilir belirtir.  
  
    ```csharp  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2.  Hizmet sözleşmesini uygulama. Yalnızca bir yöntemi, sözleşmenin sahip `UploadFile` , rastgele verilerin dosyasını bir akışa alır. İşlemi okur bayt sayısı sayım akış okuyun ve dosya adını ve okunan bayt sayısını görüntüler.  
  
    ```csharp  
    public class RawDataService : IReceiveData  
    {  
        public void UploadFile(string fileName, Stream fileContents)  
        {  
            byte[] buffer = new byte[10000];  
            int bytesRead, totalBytesRead = 0;  
            do  
            {  
                bytesRead = fileContents.Read(buffer, 0, buffer.Length);  
                totalBytesRead += bytesRead;  
            } while (bytesRead > 0);  
            Console.WriteLine("Service: Received file {0} with {1} bytes", fileName, totalBytesRead);  
        }  
    }  
    ```  
  
### <a name="to-host-the-service"></a>Ana bilgisayar hizmeti  
  
1.  Hizmet barındırmak için bir konsol uygulaması oluşturun.  
  
    ```csharp  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
    ```  
  
2.  Temel adres için hizmet içinde tutmak için bir değişken oluşturun `Main` yöntemi.  
  
    ```csharp  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3.  Oluşturma bir <xref:System.ServiceModel.ServiceHost> hizmet sınıf ve taban adresi belirtir hizmet örneği.  
  
    ```csharp  
    ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
    ```  
  
4.  Sözleşmeyi belirten bir uç nokta ekleyin <xref:System.ServiceModel.WebHttpBinding>, ve <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5.  Hizmet ana bilgisayarı açın. Hizmet isteklerini almak artık hazırdır.  
  
    ```csharp  
    host.Open();  
    Console.WriteLine("Host opened");  
    ```  
  
### <a name="to-call-the-service-programmatically"></a>Hizmeti program aracılığıyla çağırmak için  
  
1.  Oluşturma bir <xref:System.Net.HttpWebRequest> hizmetini çağırmak için kullanılan URI ile. Bu kodda taban adresi ile birleştirilir `"/UploadFile/Text"`. `"UploadFile"` URI bölümünü çağırmak için işlemi belirtir. `"Test.txt"` URI bölümünü belirtir geçirilecek filename parametresi `UploadFile` işlemi. Bu öğelerinin her ikisini de Eşle <xref:System.UriTemplate> işlemi sözleşmenin uygulanır.  
  
    ```csharp  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
    ```  
  
2.  Ayarlama <xref:System.Net.HttpWebRequest.Method%2A> özelliği <xref:System.Net.HttpWebRequest> için `POST` ve <xref:System.Net.HttpWebRequest.ContentType%2A> özelliğine `"text/plain"`. Bu hizmet kod veri gönderme ve bu verileri düz metin olarak olduğunu bildirir.  
  
    ```csharp  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3.  Çağrı <xref:System.Net.HttpWebRequest.GetRequestStream%2A> istek akışı almak için verileri göndermek, bu veri isteği akışa yazmak ve akış kapatmak oluşturun.  
  
    ```csharp  
    Stream reqStream = req.GetRequestStream();  
    byte[] fileToSend = new byte[12345];  
    for (int i = 0; i < fileToSend.Length; i++)  
       {  
           fileToSend[i] = (byte)('a' + (i % 26));  
       }  
    reqStream.Write(fileToSend, 0, fileToSend.Length);  
    reqStream.Close();  
    ```  
  
4.  Çağırarak hizmetinden yanıt Al <xref:System.Net.HttpWebRequest.GetResponse%2A> ve konsola yanıt verilerini görüntüler.  
  
    ```csharp  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
    ```  
  
5.  Hizmet ana bilgisayarını kapatın.  
  
    ```csharp  
    host.Close();  
    ```  
  
## <a name="example"></a>Örnek  
 Bu örnek kodu tam bir listesi verilmiştir.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.ServiceModel;  
using System.ServiceModel.Web;  
using System.ServiceModel.Description;  
using System.IO;  
using System.Net;  
  
namespace ReceiveRawData  
{  
    [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    public class RawDataService : IReceiveData  
    {  
        public void UploadFile(string fileName, Stream fileContents)  
        {  
            byte[] buffer = new byte[10000];  
            int bytesRead, totalBytesRead = 0;  
            do  
            {  
                bytesRead = fileContents.Read(buffer, 0, buffer.Length);  
                totalBytesRead += bytesRead;  
            } while (bytesRead > 0);  
            Console.WriteLine("Service: Received file {0} with {1} bytes", fileName, totalBytesRead);  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
            ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
            host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            host.Open();  
            Console.WriteLine("Host opened");  
  
            HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
            req.Method = "POST";  
            req.ContentType = "text/plain";  
            Stream reqStream = req.GetRequestStream();  
            byte[] fileToSend = new byte[12345];  
            for (int i = 0; i < fileToSend.Length; i++)  
            {  
                fileToSend[i] = (byte)('a' + (i % 26));  
            }  
            reqStream.Write(fileToSend, 0, fileToSend.Length);  
            reqStream.Close();  
            HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
            Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
            host.Close();  
  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Kod başvurusu System.ServiceModel.dll ve System.ServiceModel.Web.dll derlerken  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UriTemplate ve UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
 [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [WCF Web HTTP Programlama Modeli Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
