---
title: "Nasıl yapılır: WCF Web HTTP Programlama Modeli Kullanarak Rastgele Veriler Döndüren Bir Hizmet Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 829e9f2bcf909bee41f53b4b7cabbb0803e77963
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a>Nasıl yapılır: WCF Web HTTP Programlama Modeli Kullanarak Rastgele Veriler Döndüren Bir Hizmet Oluşturma
Bazen geliştiriciler, veriler bir hizmeti işleminin nasıl döndürülür, tam denetimi olmalıdır. Bir hizmet işlemi tarafından desteklenmeyen bir biçimde veri döndürmesi gerekir, bu durumda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Bu konuda ele alınmıştır kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WEB HTTP programlama gibi bir hizmet oluşturmak için modeli. Bu hizmet bir akış döndüren bir işlemi var.  
  
### <a name="to-implement-the-service-contract"></a>Hizmet sözleşmesini uygulama  
  
1.  Hizmet sözleşmesi tanımlayın. Sözleşme adında `IImageServer` ve sahip bir yöntem çağırdı `GetImage` döndüren bir <xref:System.IO.Stream>.  
  
    ```  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     Yöntemin döndürdüğü için bir <xref:System.IO.Stream>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] varsayar işlemi hizmet işleminden döndürülen bayt tam denetime sahiptir ve hiçbir geri döndürülen verileri biçimlendirme uygular.  
  
2.  Hizmet sözleşmesini uygulama. Sözleşme yalnızca bir işlem var (`GetImage`). Bu yöntem bir bit eşlem oluşturur ve ardından kaydetmesi bir <xref:System.IO.MemoryStream> .jpg biçiminde. İşlemi daha sonra bu akış çağırana döndürür.  
  
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
  
     Kodu son satırının ikinci dikkat edin:`WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`  
  
     Bu içerik türü üstbilgisini ayarlar `"image/jpeg"`. Bu örnek nasıl bir .jpg dosyası döndürüleceğini gösterir, ancak herhangi bir türde, herhangi bir biçimde gerekli olan verileri döndürmek için değiştirilebilir. İşlemi almalı veya verileri oluşturmak ve ardından bir akışa yazın.  
  
### <a name="to-host-the-service"></a>Ana bilgisayar hizmeti  
  
1.  Hizmet barındırmak için bir konsol uygulaması oluşturun.  
  
    ```  
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }   
    }  
    ```  
  
2.  Temel adres için hizmet içinde tutmak için bir değişken oluşturun `Main` yöntemi.  
  
    ```  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3.  Oluşturma bir <xref:System.ServiceModel.ServiceHost> hizmet sınıf ve taban adresi belirtme hizmet örneği.  
  
    ```  
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4.  Kullanarak bir uç nokta ekleme <xref:System.ServiceModel.WebHttpBinding> ve <xref:System.ServiceModel.Description.WebHttpBehavior>.  
  
    ```  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5.  Hizmet ana bilgisayarı açın.  
  
    ```  
    host.Open()  
    ```  
  
6.  Kullanıcının hizmet sonlandırmak için ENTER tuşuna bastığında kadar bekleyin.  
  
    ```  
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a>Internet Explorer kullanarak ham hizmetini çağırmak için  
  
1.  Hizmetini çalıştırmak, hizmet aşağıdaki çıktısını görmeniz gerekir. `Service is running Press ENTER to close the host`  
  
2.  Internet Explorer'ı açın ve yazın `http://localhost:8000/Service/GetImage?width=50&height=40` mavi bir çapraz çizgi merkezi aracılığıyla sarı bir dikdörtgen görmeniz gerekir.  
  
## <a name="example"></a>Örnek  
 Bu konuda kodunu tam bir listesi verilmiştir.  
  
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
  
-   Örnek kod başvurusu System.ServiceModel.dll ve System.ServiceModel.Web.dll derlerken.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Web HTTP Programlama Modeli](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
