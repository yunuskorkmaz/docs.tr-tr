---
title: 'Nasıl yapılır: WCF REST Programlama Modeli Kullanarak Rastgele Verileri Kabul Eden Bir Hizmet Oluşturma'
ms.date: 03/30/2017
ms.assetid: e566c15a-b600-4e4a-be3a-4af43e767dae
ms.openlocfilehash: d7da3a5c6dd4f04c4d902dab9c2dff40413ddd20
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857342"
---
# <a name="how-to-create-a-service-that-accepts-arbitrary-data-using-the-wcf-rest-programming-model"></a>Nasıl yapılır: WCF REST Programlama Modeli Kullanarak Rastgele Verileri Kabul Eden Bir Hizmet Oluşturma
Bazen geliştiriciler, veri hizmeti işleminden döndürülen nasıl tam denetimi olmalıdır. Bir hizmet işlemi, verileri bir biçimde byWCF desteklenmiyor döndürmelidir olduğunda bu durum geçerlidir. Bu konuda, rastgele verileri alan bir hizmet oluşturmak için WCF REST programlama modeli kullanarak anlatılmaktadır.  
  
### <a name="to-implement-the-service-contract"></a>Hizmet sözleşmesini uygulama  
  
1. Hizmet sözleşmesini tanımlamaktır. Rastgele veri aldığında işlem türünde bir parametresi olmalıdır <xref:System.IO.Stream>. Ayrıca, bu parametre istek gövdesinde geçirilen tek parametresi olması gerekir. Bu örnekte açıklanan işlem, ayrıca bir filename parametresi alır. Bu parametre, istek URL'si içinde iletilir. Parametre URL'sini belirterek geçirilen belirtebileceğiniz bir <xref:System.UriTemplate> içinde <xref:System.ServiceModel.Web.WebInvokeAttribute>. URI çağırmak için kullanılan bu durumda bu yöntem, "UploadFile/bazı-dosya adı" sona erer. URI şablonu "{filename}" kısmı, işlemi için dosya adı parametresi işlemi çağırmak için kullanılan URI içinde geçirildiğini belirtir.  
  
    ```csharp  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2. Hizmet sözleşmesini uygulama. Sözleşme yalnızca bir yöntem olan `UploadFile` , rastgele veriler dosyası bir akışa alır. İşlemin bayt sayısını sayma stream okuyun ve ardından dosya adı ve okunan bayt sayısını görüntüler okur.  
  
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
  
1. Hizmeti barındırmak için bir konsol uygulaması oluşturun.  
  
    ```csharp  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
    ```  
  
2. İçinde hizmet için temel adresini tutacak bir değişken oluşturma `Main` yöntemi.  
  
    ```csharp  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. Oluşturma bir <xref:System.ServiceModel.ServiceHost> hizmet sınıfı ve taban adresini belirten bir hizmet örneği.  
  
    ```csharp  
    ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
    ```  
  
4. Sözleşme belirten bir uç nokta ekleyin <xref:System.ServiceModel.WebHttpBinding>, ve <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. Hizmet ana bilgisayarı açın. Hizmet isteklerini almak artık hazırdır.  
  
    ```csharp  
    host.Open();  
    Console.WriteLine("Host opened");  
    ```  
  
### <a name="to-call-the-service-programmatically"></a>Program aracılığıyla hizmeti çağırmak için  
  
1. Oluşturma bir <xref:System.Net.HttpWebRequest> hizmeti çağırmak için kullanılan URI ile. Bu kodda, temel adresi ile birleştirilir `"/UploadFile/Text"`. `"UploadFile"` URI kısmı aranacak işlem belirtir. `"Test.txt"` URI kısmı belirtir geçirilecek filename parametresi `UploadFile` işlemi. Bu öğelerinin her ikisini de eşlemek <xref:System.UriTemplate> da işlem anlaşması için uygulanır.  
  
    ```csharp  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
    ```  
  
2. Ayarlama <xref:System.Net.HttpWebRequest.Method%2A> özelliği <xref:System.Net.HttpWebRequest> için `POST` ve <xref:System.Net.HttpWebRequest.ContentType%2A> özelliğini `"text/plain"`. Bu kod, veri göndermek ve bu veriler düz metin olarak yapılır hizmet bildirir.  
  
    ```csharp  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3. Çağrı <xref:System.Net.HttpWebRequest.GetRequestStream%2A> İstek akışını almak için veri göndermek, bu veri isteği akışa yazmak ve akış Kapat oluşturun.  
  
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
  
4. Çağırarak hizmetten yanıt alma <xref:System.Net.HttpWebRequest.GetResponse%2A> ve konsola yanıt verileri görüntüler.  
  
    ```csharp  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
    ```  
  
5. Hizmet ana bilgisayarını kapatın.  
  
    ```csharp  
    host.Close();  
    ```  
  
## <a name="example"></a>Örnek  
 Bu örnek için kod tam listesi verilmiştir.  
  
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
  
- Kod başvurusu System.ServiceModel.dll ve System.ServiceModel.Web.dll derlenirken  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UriTemplate ve UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)
- [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [WCF Web HTTP Programlama Modeli Genel Bakış](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
