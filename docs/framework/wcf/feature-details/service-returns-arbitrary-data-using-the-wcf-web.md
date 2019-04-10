---
title: 'Nasıl yapılır: WCF Web HTTP Programlama Modeli Kullanarak Rastgele Veriler Döndüren Bir Hizmet Oluşturma'
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: 55fdc6824ab82bdf3b5913cd600815ed05bd909c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303927"
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a>Nasıl yapılır: WCF Web HTTP Programlama Modeli Kullanarak Rastgele Veriler Döndüren Bir Hizmet Oluşturma
Bazen geliştiriciler, veri hizmeti işleminden döndürülen nasıl tam denetimi olmalıdır. Bir hizmet işlemi WCF tarafından desteklenmeyen bir biçimde veri döndürmelidir olduğunda bu durum geçerlidir. Bu konuda, böyle bir hizmet oluşturmak için WCF WEB HTTP programlama modeli kullanarak anlatılmaktadır. Bu hizmet, bir akış döndüren tek bir işlem içerir.  
  
### <a name="to-implement-the-service-contract"></a>Hizmet sözleşmesini uygulama  
  
1. Hizmet sözleşmesini tanımlamaktır. Sözleşme adında `IImageServer` ve sahip bir yöntemi çağıran `GetImage` döndüren bir <xref:System.IO.Stream>.  
  
    ```  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     Yöntemin döndürdüğü için bir <xref:System.IO.Stream>, WCF işlemi hizmet işleminden döndürülen bayt üzerinde tam denetime sahip olduğunu varsayar ve biçimlendirmesi olmayan döndürülen veriler için geçerlidir.  
  
2. Hizmet sözleşmesini uygulama. Sözleşme yalnızca bir işlem var (`GetImage`). Bu yöntem bir bit eşlem oluşturur ve ardından kaydetmek bir <xref:System.IO.MemoryStream> .jpg biçiminde. İşlemi daha sonra bu çağırana döner.  
  
    ```  
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
  
     Son kod satırında ikinci dikkat edin: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`  
  
     Bu içerik türü üst bilgisi ayarlar `"image/jpeg"`. Bu örnek nasıl bir .jpg dosyasını döndürüleceğini gösterir, ancak herhangi bir türde, herhangi bir biçimde gereklidir veri döndürmek için değiştirilebilir. İşlemi almalı veya verileri oluşturmak ve sonra bunu bir akışa yazabilirsiniz.  
  
### <a name="to-host-the-service"></a>Ana bilgisayar hizmeti  
  
1. Hizmeti barındırmak için bir konsol uygulaması oluşturun.  
  
    ```  
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }   
    }  
    ```  
  
2. İçinde hizmet için temel adresini tutacak bir değişken oluşturma `Main` yöntemi.  
  
    ```  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. Oluşturma bir <xref:System.ServiceModel.ServiceHost> hizmet sınıfı ve taban adresi belirterek hizmet örneği.  
  
    ```  
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4. Kullanarak bir uç nokta ekleme <xref:System.ServiceModel.WebHttpBinding> ve <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
    ```  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. Hizmet ana bilgisayarı açın.  
  
    ```  
    host.Open()  
    ```  
  
6. Kullanıcı Hizmeti sonlandırmak için ENTER tuşuna bastığında kadar bekleyin.  
  
    ```  
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a>Internet Explorer'ı kullanarak ham hizmeti çağırmak için  
  
1. Hizmeti çalıştırmak, hizmetin aşağıdaki çıktısını görmeniz gerekir. `Service is running Press ENTER to close the host`  
  
2. Internet Explorer'ı açın ve yazın `http://localhost:8000/Service/GetImage?width=50&height=40` merkezi üzerinden çapraz mavi bir çizgi sarı bir dikdörtgen görmeniz gerekir.  
  
## <a name="example"></a>Örnek  
 Bu konu için kod tam listesi verilmiştir.  
  
```  
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
  
-   Örnek kod başvurusu System.ServiceModel.dll ve System.ServiceModel.Web.dll derlenirken.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
