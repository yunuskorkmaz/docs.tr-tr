---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: WCF Web HTTP programlama modelini kullanarak rastgele veriler döndüren bir hizmet oluşturma'
title: 'Nasıl yapılır: WCF Web HTTP Programlama Modeli Kullanarak Rastgele Veriler Döndüren Bir Hizmet Oluşturma'
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: aeb03e0dad6c63c463db419027f5556922b2f160
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793538"
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a>Nasıl yapılır: WCF Web HTTP Programlama Modeli Kullanarak Rastgele Veriler Döndüren Bir Hizmet Oluşturma

Bazen geliştiricilerin, bir hizmet işleminden verilerin nasıl döndürüldüğünden tam denetime sahip olmaları gerekir. Bu durum, bir hizmet işleminin WCF tarafından desteklenmeyen bir biçimde veri döndürmesi gereken durumdur. Bu konuda, bu tür bir hizmet oluşturmak için WCF WEB HTTP programlama modelinin kullanımı ele alınmaktadır. Bu hizmette bir akış döndüren bir işlem vardır.  
  
### <a name="to-implement-the-service-contract"></a>Hizmet sözleşmesini uygulamak için  
  
1. Hizmet sözleşmesini tanımlayın. Anlaşma çağrılır `IImageServer` ve `GetImage` döndüren bir yöntemi vardır <xref:System.IO.Stream> .  
  
    ```csharp  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     Yöntemi bir döndürdüğü için <xref:System.IO.Stream> , WCF işlemin hizmet işleminden döndürülen baytlar üzerinde tamamlanmamış bir denetime sahip olduğunu ve döndürülen verilere hiçbir biçimlendirme uygulanmadığından emin olur.  
  
2. Hizmet sözleşmesini uygulayın. Sözleşmede yalnızca bir işlem () vardır `GetImage` . Bu yöntem bir bit eşlem üretir ve sonra <xref:System.IO.MemoryStream> . jpg biçiminde kaydeder. İşlem daha sonra bu akışı çağırana döndürür.  
  
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
  
     İkinci kodun son satırına dikkat edin: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`  
  
     Bu, içerik türü üst bilgisini olarak ayarlar `"image/jpeg"` . Bu örnek, bir. jpg dosyasının nasıl döndürülmesini gösterir, ancak herhangi bir biçimde gerekli olan herhangi bir veri türünü döndürecek şekilde değiştirilebilir. İşlemin verileri alması veya oluşturması ve sonra bir akışa yazması gerekir.  
  
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
  
3. Hizmet <xref:System.ServiceModel.ServiceHost> sınıfını ve temel adresi belirten hizmet için bir örnek oluşturun.  
  
    ```csharp
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4. Ve kullanarak bir uç nokta ekleyin <xref:System.ServiceModel.WebHttpBinding> <xref:System.ServiceModel.Description.WebHttpBehavior> .  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. Hizmet konağını açın.  
  
    ```csharp  
    host.Open();  
    ```  
  
6. Hizmeti sonlandırmak için kullanıcının ENTER tuşuna basmasına kadar bekleyin.  
  
    ```csharp
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a>Internet Explorer 'ı kullanarak ham hizmeti çağırmak için  
  
1. Hizmeti çalıştırın, hizmetten aşağıdaki çıktıyı görmeniz gerekir. `Service is running Press ENTER to close the host`  
  
2. Internet Explorer 'ı açın ve yazın, `http://localhost:8000/Service/GetImage?width=50&height=40` ortadaki mavi bir diyagonal çizgi ile sarı bir dikdörtgen görmeniz gerekir.  
  
## <a name="example"></a>Örnek  

 Aşağıda, bu konunun kodun tamambir listesi verilmiştir.  
  
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
  
- Örnek kod başvurusunu derlerken System.ServiceModel.dll ve System.ServiceModel.Web.dll.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Web HTTP Programlama Modeli](wcf-web-http-programming-model.md)
