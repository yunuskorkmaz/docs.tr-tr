---
title: 'Nasıl yapılır: WCF REST Programlama Modeli Kullanarak Rastgele Verileri Kabul Eden Bir Hizmet Oluşturma'
ms.date: 03/30/2017
ms.assetid: e566c15a-b600-4e4a-be3a-4af43e767dae
ms.openlocfilehash: d908651f7815c102b45ea106f5bec4c07d869950
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601341"
---
# <a name="how-to-create-a-service-that-accepts-arbitrary-data-using-the-wcf-rest-programming-model"></a>Nasıl yapılır: WCF REST Programlama Modeli Kullanarak Rastgele Verileri Kabul Eden Bir Hizmet Oluşturma
Bazen geliştiricilerin, bir hizmet işleminden verilerin nasıl döndürüldüğünden tam denetime sahip olmaları gerekir. Bu durum, bir hizmet işleminin verileri desteklenmeyen bir biçimde döndürmesi gereken bir biçimde (WCF), bu durumdur. Bu konuda, rastgele veri alan bir hizmet oluşturmak için WCF REST programlama modelinin kullanımı ele alınmaktadır.  
  
### <a name="to-implement-the-service-contract"></a>Hizmet sözleşmesini uygulamak için  
  
1. Hizmet sözleşmesini tanımlayın. Rastgele verileri alan işlem türünde bir parametreye sahip olmalıdır <xref:System.IO.Stream> . Ayrıca, bu parametre isteğin gövdesinde geçirilen tek parametre olmalıdır. Bu örnekte açıklanan işlem de bir filename parametresi alır. Bu parametre isteğin URL 'SI içinde geçirilir. İçinde bir parametre belirterek parametrenin URL içinde geçtiğini belirtebilirsiniz <xref:System.UriTemplate> <xref:System.ServiceModel.Web.WebInvokeAttribute> . Bu durumda, bu yöntemi çağırmak için kullanılan URI "UploadFile/some-filename" içinde sona erer. URI şablonunun "{filename}" kısmı, işlem için dosya adı parametresinin işlemi çağırmak için kullanılan URI içinde geçtiğini belirtir.  
  
    ```csharp  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2. Hizmet sözleşmesini uygulayın. Sözleşmede bir `UploadFile` akışta rastgele veri dosyası alan yalnızca bir yöntemi vardır. Bu işlem, okunan bayt sayısını sayarak akışı okur ve sonra dosya adını ve okunan bayt sayısını görüntüler.  
  
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
  
### <a name="to-host-the-service"></a>Hizmeti barındırmak için  
  
1. Hizmeti barındırmak için bir konsol uygulaması oluşturun.  
  
    ```csharp  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
    ```  
  
2. Yöntemi içindeki hizmetin temel adresini tutacak bir değişken oluşturun `Main` .  
  
    ```csharp  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. Hizmet <xref:System.ServiceModel.ServiceHost> sınıfı ve temel adresi belirten bir örnek oluşturun.  
  
    ```csharp  
    ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
    ```  
  
4. , Ve sözleşmesini belirten bir uç nokta ekleyin <xref:System.ServiceModel.WebHttpBinding> <xref:System.ServiceModel.Description.WebHttpBehavior> .  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. Hizmet konağını açın. Hizmet artık istekleri almaya hazırdır.  
  
    ```csharp  
    host.Open();  
    Console.WriteLine("Host opened");  
    ```  
  
### <a name="to-call-the-service-programmatically"></a>Hizmeti programlı olarak çağırmak için  
  
1. <xref:System.Net.HttpWebRequest>Hizmeti çağırmak için kullanılan URI ile bir oluşturun. Bu kodda, temel adres ile birleştirilir `"/UploadFile/Text"` . `"UploadFile"`URI 'nin bölümü çağrılacak işlemi belirtir. `"Test.txt"`URI 'nin bölümü, işleme geçirilecek filename parametresini belirtir `UploadFile` . Bu öğelerin her ikisi de <xref:System.UriTemplate> işlem sözleşmesine uygulanan ile eşlenir.  
  
    ```csharp  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
    ```  
  
2. <xref:System.Net.HttpWebRequest.Method%2A> <xref:System.Net.HttpWebRequest> `POST` Ve <xref:System.Net.HttpWebRequest.ContentType%2A> özelliğinin özelliğini olarak ayarlayın `"text/plain"` . Bu, hizmete kodun veri gönderdiğini ve verilerin düz metin olduğunu söyler.  
  
    ```csharp  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3. <xref:System.Net.HttpWebRequest.GetRequestStream%2A>İstek akışını almak için çağrısı yapın, gönderecek verileri oluşturun, bu verileri istek akışına yazın ve akışı kapatın.  
  
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
  
4. <xref:System.Net.HttpWebRequest.GetResponse%2A>Yanıt verilerini çağırarak ve konsola görüntüleyerek hizmetten gelen yanıtı alın.  
  
    ```csharp  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
    ```  
  
5. Hizmet konağını kapatın.  
  
    ```csharp  
    host.Close();  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıda bu örnek için kodun tamamen bir listesi verilmiştir.  
  
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
  
- System. ServiceModel. dll ve System. ServiceModel. Web. dll kod başvurusunu derlerken  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UriTemplate ve UriTemplateTable](uritemplate-and-uritemplatetable.md)
- [WCF Web HTTP Programlama Modeli](wcf-web-http-programming-model.md)
- [WCF Web HTTP Programlama Modeli Genel Bakış](wcf-web-http-programming-model-overview.md)
