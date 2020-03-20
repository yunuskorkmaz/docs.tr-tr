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
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a><span data-ttu-id="15d1a-102">Nasıl yapılır: WCF Web HTTP Programlama Modeli Kullanarak Rastgele Veriler Döndüren Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="15d1a-102">How to: Create a Service That Returns Arbitrary Data Using The WCF Web HTTP Programming Model</span></span>
<span data-ttu-id="15d1a-103">Bazen geliştiriciler, verilerin bir hizmet işleminden nasıl döndürüldüğü konusunda tam denetime sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="15d1a-103">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="15d1a-104">Bu durum, bir hizmet işleminin WCF tarafından desteklenmeyen bir biçimde veri döndürmesi gerektiği durumdur.</span><span class="sxs-lookup"><span data-stu-id="15d1a-104">This is the case when a service operation must return data in a format not supported by WCF.</span></span> <span data-ttu-id="15d1a-105">Bu konu, böyle bir hizmet oluşturmak için WCF WEB HTTP Programlama Modeli kullanarak tartışır.</span><span class="sxs-lookup"><span data-stu-id="15d1a-105">This topic discusses using the WCF WEB HTTP Programming Model to create such a service.</span></span> <span data-ttu-id="15d1a-106">Bu hizmet, bir akışı döndüren bir işlem vardır.</span><span class="sxs-lookup"><span data-stu-id="15d1a-106">This service has one operation that returns a stream.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="15d1a-107">Hizmet sözleşmesini uygulamak için</span><span class="sxs-lookup"><span data-stu-id="15d1a-107">To implement the service contract</span></span>  
  
1. <span data-ttu-id="15d1a-108">Hizmet sözleşmesini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="15d1a-108">Define the service contract.</span></span> <span data-ttu-id="15d1a-109">Sözleşme denir `IImageServer` ve bir ' `GetImage` döndürür denilen bir <xref:System.IO.Stream>yöntem vardır.</span><span class="sxs-lookup"><span data-stu-id="15d1a-109">The contract is called `IImageServer` and has one method called `GetImage` that returns a <xref:System.IO.Stream>.</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     <span data-ttu-id="15d1a-110">Yöntem bir <xref:System.IO.Stream>döndürdüğünden, WCF, işletmek, hizmet işletmesinden döndürülen baytlar üzerinde tam denetime sahip olduğunu ve iade edilen verilere biçimlendirme uygulamazığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="15d1a-110">Because the method returns a <xref:System.IO.Stream>, WCF assumes that the operation has complete control over the bytes that are returned from the service operation and it applies no formatting to the data that is returned.</span></span>  
  
2. <span data-ttu-id="15d1a-111">Hizmet sözleşmesini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="15d1a-111">Implement the service contract.</span></span> <span data-ttu-id="15d1a-112">Sözleşmenin yalnızca bir`GetImage`işlemi vardır ( ).</span><span class="sxs-lookup"><span data-stu-id="15d1a-112">The contract has only one operation (`GetImage`).</span></span> <span data-ttu-id="15d1a-113">Bu yöntem bir bit eşlemi oluşturur <xref:System.IO.MemoryStream> ve sonra onu .jpg formatında bir biçime kaydeder.</span><span class="sxs-lookup"><span data-stu-id="15d1a-113">This method generates a bitmap and then save it to a <xref:System.IO.MemoryStream> in .jpg format.</span></span> <span data-ttu-id="15d1a-114">İşlem daha sonra bu akışı arayana döndürür.</span><span class="sxs-lookup"><span data-stu-id="15d1a-114">The operation then returns that stream to the caller.</span></span>  
  
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
  
     <span data-ttu-id="15d1a-115">Kodun ikinci ve son satırına dikkat edin:`WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span><span class="sxs-lookup"><span data-stu-id="15d1a-115">Notice the second to last line of code: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span></span>  
  
     <span data-ttu-id="15d1a-116">Bu, içerik türü üstbilgisini `"image/jpeg"`.</span><span class="sxs-lookup"><span data-stu-id="15d1a-116">This sets the content type header to `"image/jpeg"`.</span></span> <span data-ttu-id="15d1a-117">Bu örnek bir .jpg dosyasının nasıl döndürüleceğini gösterse de, herhangi bir biçimde gerekli olan her türlü veriyi döndürmek için değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="15d1a-117">Although this sample shows how to return a .jpg file, it can be modified to return any type of data that is required, in any format.</span></span> <span data-ttu-id="15d1a-118">İşlem, verileri almalı veya oluşturmalı ve sonra bir akışa yazmalıdır.</span><span class="sxs-lookup"><span data-stu-id="15d1a-118">The operation must retrieve or generate the data and then write it to a stream.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="15d1a-119">Hizmeti barındırmak için</span><span class="sxs-lookup"><span data-stu-id="15d1a-119">To host the service</span></span>  
  
1. <span data-ttu-id="15d1a-120">Hizmeti barındırmak için bir konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="15d1a-120">Create a console application to host the service.</span></span>  
  
    ```csharp
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }
    }  
    ```  
  
2. <span data-ttu-id="15d1a-121">`Main` Yöntem içinde hizmetin temel adresini tutmak için bir değişken oluşturun.</span><span class="sxs-lookup"><span data-stu-id="15d1a-121">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```csharp
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. <span data-ttu-id="15d1a-122">Hizmet <xref:System.ServiceModel.ServiceHost> sınıfını ve temel adresi belirten hizmet için bir örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="15d1a-122">Create a <xref:System.ServiceModel.ServiceHost> instance for the service specifying the service class and the base address.</span></span>  
  
    ```csharp
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4. <span data-ttu-id="15d1a-123">ve kullanarak bir <xref:System.ServiceModel.WebHttpBinding> bitiş <xref:System.ServiceModel.Description.WebHttpBehavior>noktası ekleyin.</span><span class="sxs-lookup"><span data-stu-id="15d1a-123">Add an endpoint using the <xref:System.ServiceModel.WebHttpBinding> and the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. <span data-ttu-id="15d1a-124">Servis ana bilgisayarını açın.</span><span class="sxs-lookup"><span data-stu-id="15d1a-124">Open the service host.</span></span>  
  
    ```csharp  
    host.Open();  
    ```  
  
6. <span data-ttu-id="15d1a-125">Kullanıcı hizmeti sonlandırmak için ENTER tuşuna basana kadar bekleyin.</span><span class="sxs-lookup"><span data-stu-id="15d1a-125">Wait until the user presses ENTER to terminate the service.</span></span>  
  
    ```csharp
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a><span data-ttu-id="15d1a-126">Internet Explorer kullanarak ham hizmeti aramak için</span><span class="sxs-lookup"><span data-stu-id="15d1a-126">To call the raw service using Internet Explorer</span></span>  
  
1. <span data-ttu-id="15d1a-127">Hizmeti çalıştırın, hizmetten aşağıdaki çıktıyı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="15d1a-127">Run the service, you should see the following output from the service.</span></span> `Service is running Press ENTER to close the host`  
  
2. <span data-ttu-id="15d1a-128">Internet Explorer'ı `http://localhost:8000/Service/GetImage?width=50&height=40` açın ve ortasın asıması mavi çapraz çizgili sarı bir dikdörtgen görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="15d1a-128">Open Internet Explorer and type in `http://localhost:8000/Service/GetImage?width=50&height=40` you should see a yellow rectangle with a blue diagonal line through the center.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15d1a-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="15d1a-129">Example</span></span>  
 <span data-ttu-id="15d1a-130">Aşağıda, bu konu için kodun tam bir listesi vettir.</span><span class="sxs-lookup"><span data-stu-id="15d1a-130">The following is a complete listing of the code for this topic.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="15d1a-131">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="15d1a-131">Compiling the Code</span></span>  
  
- <span data-ttu-id="15d1a-132">Örnek kod referans System.ServiceModel.dll ve System.ServiceModel.Web.dll derlenirken.</span><span class="sxs-lookup"><span data-stu-id="15d1a-132">When compiling the sample code reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15d1a-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15d1a-133">See also</span></span>

- [<span data-ttu-id="15d1a-134">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="15d1a-134">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
