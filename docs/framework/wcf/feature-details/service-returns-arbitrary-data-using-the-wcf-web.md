---
title: 'Nasıl yapılır: WCF Web HTTP Programlama Modeli Kullanarak Rastgele Veriler Döndüren Bir Hizmet Oluşturma'
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: c85ab6725876a2d523a18c817ce3fd89f0d2285a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184479"
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a>Nasıl yapılır: WCF Web HTTP Programlama Modeli Kullanarak Rastgele Veriler Döndüren Bir Hizmet Oluşturma
Bazen geliştiriciler, verilerin bir hizmet işleminden nasıl döndürüldüğü konusunda tam denetime sahip olmalıdır. Bu durum, bir hizmet işleminin WCF tarafından desteklenmeyen bir biçimde veri döndürmesi gerektiği durumdur. Bu konu, böyle bir hizmet oluşturmak için WCF WEB HTTP Programlama Modeli kullanarak tartışır. Bu hizmet, bir akışı döndüren bir işlem vardır.  
  
### <a name="to-implement-the-service-contract"></a>Hizmet sözleşmesini uygulamak için  
  
1. Hizmet sözleşmesini tanımlayın. Sözleşme denir `IImageServer` ve bir ' `GetImage` döndürür denilen bir <xref:System.IO.Stream>yöntem vardır.  
  
    ```csharp  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     Yöntem bir <xref:System.IO.Stream>döndürdüğünden, WCF, işletmek, hizmet işletmesinden döndürülen baytlar üzerinde tam denetime sahip olduğunu ve iade edilen verilere biçimlendirme uygulamazığını varsayar.  
  
2. Hizmet sözleşmesini uygulayın. Sözleşmenin yalnızca bir`GetImage`işlemi vardır ( ). Bu yöntem bir bit eşlemi oluşturur <xref:System.IO.MemoryStream> ve sonra onu .jpg formatında bir biçime kaydeder. İşlem daha sonra bu akışı arayana döndürür.  
  
    ```csharp
    public class Service : IImageServer
    {
        public Stream GetImage(int width, int height)
        {
            Bitmap bitmap = new Bitmap(width, height);
            for (int i = 0; i < bitmap.Width; i++)
            {
                for (int j = 0; j < bitmap.Height; j++)
                {
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);
                }
            }
            MemoryStream ms = new MemoryStream();
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);
            ms.Position = 0;
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";
            return ms;
        }
    }
    ```  
  
     Kodun ikinci ve son satırına dikkat edin:`WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`  
  
     Bu, içerik türü üstbilgisini `"image/jpeg"`. Bu örnek bir .jpg dosyasının nasıl döndürüleceğini gösterse de, herhangi bir biçimde gerekli olan her türlü veriyi döndürmek için değiştirilebilir. İşlem, verileri almalı veya oluşturmalı ve sonra bir akışa yazmalıdır.  
  
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
  
2. `Main` Yöntem içinde hizmetin temel adresini tutmak için bir değişken oluşturun.  
  
    ```csharp
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. Hizmet <xref:System.ServiceModel.ServiceHost> sınıfını ve temel adresi belirten hizmet için bir örnek oluşturun.  
  
    ```csharp
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4. ve kullanarak bir <xref:System.ServiceModel.WebHttpBinding> bitiş <xref:System.ServiceModel.Description.WebHttpBehavior>noktası ekleyin.  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. Servis ana bilgisayarını açın.  
  
    ```csharp  
    host.Open();  
    ```  
  
6. Kullanıcı hizmeti sonlandırmak için ENTER tuşuna basana kadar bekleyin.  
  
    ```csharp
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a>Internet Explorer kullanarak ham hizmeti aramak için  
  
1. Hizmeti çalıştırın, hizmetten aşağıdaki çıktıyı görmeniz gerekir. `Service is running Press ENTER to close the host`  
  
2. Internet Explorer'ı `http://localhost:8000/Service/GetImage?width=50&height=40` açın ve ortasın asıması mavi çapraz çizgili sarı bir dikdörtgen görmeniz gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıda, bu konu için kodun tam bir listesi vettir.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.ServiceModel;  
using System.ServiceModel.Web;  
using System.ServiceModel.Description;  
using System.IO;  
using System.Drawing;  
  
namespace RawImageService  
{  
    // Define the service contract  
    [ServiceContract]  
    public interface IImageServer  
    {  
        [WebGet]  
        Stream GetImage(int width, int height);  
    }  
  
    // implement the service contract  
    public class Service : IImageServer  
    {  
        public Stream GetImage(int width, int height)  
        {  
            // Although this method returns a jpeg, it can be  
            // modified to return any data you want within the stream  
            Bitmap bitmap = new Bitmap(width, height);  
            for (int i = 0; i < bitmap.Width; i++)  
            {  
                for (int j = 0; j < bitmap.Height; j++)  
                {  
                    bitmap.SetPixel(i, j, (Math.Abs(i - j) < 2) ? Color.Blue : Color.Yellow);  
                }  
            }  
            MemoryStream ms = new MemoryStream();  
            bitmap.Save(ms, System.Drawing.Imaging.ImageFormat.Jpeg);  
            ms.Position = 0;  
            WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";  
            return ms;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
            ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
            host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            host.Open();  
            Console.WriteLine("Service is running");  
            Console.Write("Press ENTER to close the host");  
            Console.ReadLine();  
            host.Close();  
  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Örnek kod referans System.ServiceModel.dll ve System.ServiceModel.Web.dll derlenirken.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
