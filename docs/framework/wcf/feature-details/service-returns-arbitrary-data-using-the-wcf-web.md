---
title: 'Nasıl yapılır: WCF Web HTTP Programlama Modeli Kullanarak Rastgele Veriler Döndüren Bir Hizmet Oluşturma'
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: 55fdc6824ab82bdf3b5913cd600815ed05bd909c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747855"
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a><span data-ttu-id="ec114-102">Nasıl yapılır: WCF Web HTTP Programlama Modeli Kullanarak Rastgele Veriler Döndüren Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ec114-102">How to: Create a Service That Returns Arbitrary Data Using The WCF Web HTTP Programming Model</span></span>
<span data-ttu-id="ec114-103">Bazen geliştiriciler, veri hizmeti işleminden döndürülen nasıl tam denetimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ec114-103">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="ec114-104">Bir hizmet işlemi WCF tarafından desteklenmeyen bir biçimde veri döndürmelidir olduğunda bu durum geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ec114-104">This is the case when a service operation must return data in a format not supported by WCF.</span></span> <span data-ttu-id="ec114-105">Bu konuda, böyle bir hizmet oluşturmak için WCF WEB HTTP programlama modeli kullanarak anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ec114-105">This topic discusses using the WCF WEB HTTP Programming Model to create such a service.</span></span> <span data-ttu-id="ec114-106">Bu hizmet, bir akış döndüren tek bir işlem içerir.</span><span class="sxs-lookup"><span data-stu-id="ec114-106">This service has one operation that returns a stream.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="ec114-107">Hizmet sözleşmesini uygulama</span><span class="sxs-lookup"><span data-stu-id="ec114-107">To implement the service contract</span></span>  
  
1. <span data-ttu-id="ec114-108">Hizmet sözleşmesini tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="ec114-108">Define the service contract.</span></span> <span data-ttu-id="ec114-109">Sözleşme adında `IImageServer` ve sahip bir yöntemi çağıran `GetImage` döndüren bir <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="ec114-109">The contract is called `IImageServer` and has one method called `GetImage` that returns a <xref:System.IO.Stream>.</span></span>  
  
    ```  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     <span data-ttu-id="ec114-110">Yöntemin döndürdüğü için bir <xref:System.IO.Stream>, WCF işlemi hizmet işleminden döndürülen bayt üzerinde tam denetime sahip olduğunu varsayar ve biçimlendirmesi olmayan döndürülen veriler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ec114-110">Because the method returns a <xref:System.IO.Stream>, WCF assumes that the operation has complete control over the bytes that are returned from the service operation and it applies no formatting to the data that is returned.</span></span>  
  
2. <span data-ttu-id="ec114-111">Hizmet sözleşmesini uygulama.</span><span class="sxs-lookup"><span data-stu-id="ec114-111">Implement the service contract.</span></span> <span data-ttu-id="ec114-112">Sözleşme yalnızca bir işlem var (`GetImage`).</span><span class="sxs-lookup"><span data-stu-id="ec114-112">The contract has only one operation (`GetImage`).</span></span> <span data-ttu-id="ec114-113">Bu yöntem bir bit eşlem oluşturur ve ardından kaydetmek bir <xref:System.IO.MemoryStream> .jpg biçiminde.</span><span class="sxs-lookup"><span data-stu-id="ec114-113">This method generates a bitmap and then save it to a <xref:System.IO.MemoryStream> in .jpg format.</span></span> <span data-ttu-id="ec114-114">İşlemi daha sonra bu çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="ec114-114">The operation then returns that stream to the caller.</span></span>  
  
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
  
     <span data-ttu-id="ec114-115">Son kod satırında ikinci dikkat edin: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span><span class="sxs-lookup"><span data-stu-id="ec114-115">Notice the second to last line of code: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span></span>  
  
     <span data-ttu-id="ec114-116">Bu içerik türü üst bilgisi ayarlar `"image/jpeg"`.</span><span class="sxs-lookup"><span data-stu-id="ec114-116">This sets the content type header to `"image/jpeg"`.</span></span> <span data-ttu-id="ec114-117">Bu örnek nasıl bir .jpg dosyasını döndürüleceğini gösterir, ancak herhangi bir türde, herhangi bir biçimde gereklidir veri döndürmek için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ec114-117">Although this sample shows how to return a .jpg file, it can be modified to return any type of data that is required, in any format.</span></span> <span data-ttu-id="ec114-118">İşlemi almalı veya verileri oluşturmak ve sonra bunu bir akışa yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec114-118">The operation must retrieve or generate the data and then write it to a stream.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="ec114-119">Ana bilgisayar hizmeti</span><span class="sxs-lookup"><span data-stu-id="ec114-119">To host the service</span></span>  
  
1. <span data-ttu-id="ec114-120">Hizmeti barındırmak için bir konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ec114-120">Create a console application to host the service.</span></span>  
  
    ```  
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }   
    }  
    ```  
  
2. <span data-ttu-id="ec114-121">İçinde hizmet için temel adresini tutacak bir değişken oluşturma `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ec114-121">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. <span data-ttu-id="ec114-122">Oluşturma bir <xref:System.ServiceModel.ServiceHost> hizmet sınıfı ve taban adresi belirterek hizmet örneği.</span><span class="sxs-lookup"><span data-stu-id="ec114-122">Create a <xref:System.ServiceModel.ServiceHost> instance for the service specifying the service class and the base address.</span></span>  
  
    ```  
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4. <span data-ttu-id="ec114-123">Kullanarak bir uç nokta ekleme <xref:System.ServiceModel.WebHttpBinding> ve <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="ec114-123">Add an endpoint using the <xref:System.ServiceModel.WebHttpBinding> and the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. <span data-ttu-id="ec114-124">Hizmet ana bilgisayarı açın.</span><span class="sxs-lookup"><span data-stu-id="ec114-124">Open the service host.</span></span>  
  
    ```  
    host.Open()  
    ```  
  
6. <span data-ttu-id="ec114-125">Kullanıcı Hizmeti sonlandırmak için ENTER tuşuna bastığında kadar bekleyin.</span><span class="sxs-lookup"><span data-stu-id="ec114-125">Wait until the user presses ENTER to terminate the service.</span></span>  
  
    ```  
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a><span data-ttu-id="ec114-126">Internet Explorer'ı kullanarak ham hizmeti çağırmak için</span><span class="sxs-lookup"><span data-stu-id="ec114-126">To call the raw service using Internet Explorer</span></span>  
  
1. <span data-ttu-id="ec114-127">Hizmeti çalıştırmak, hizmetin aşağıdaki çıktısını görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec114-127">Run the service, you should see the following output from the service.</span></span> `Service is running Press ENTER to close the host`  
  
2. <span data-ttu-id="ec114-128">Internet Explorer'ı açın ve yazın `http://localhost:8000/Service/GetImage?width=50&height=40` merkezi üzerinden çapraz mavi bir çizgi sarı bir dikdörtgen görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec114-128">Open Internet Explorer and type in `http://localhost:8000/Service/GetImage?width=50&height=40` you should see a yellow rectangle with a blue diagonal line through the center.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec114-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec114-129">Example</span></span>  
 <span data-ttu-id="ec114-130">Bu konu için kod tam listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ec114-130">The following is a complete listing of the code for this topic.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="ec114-131">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ec114-131">Compiling the Code</span></span>  
  
- <span data-ttu-id="ec114-132">Örnek kod başvurusu System.ServiceModel.dll ve System.ServiceModel.Web.dll derlenirken.</span><span class="sxs-lookup"><span data-stu-id="ec114-132">When compiling the sample code reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec114-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec114-133">See also</span></span>

- [<span data-ttu-id="ec114-134">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="ec114-134">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
