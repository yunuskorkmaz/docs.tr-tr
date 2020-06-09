---
title: 'Nasıl yapılır: WCF Web HTTP Programlama Modeli Kullanarak Rastgele Veriler Döndüren Bir Hizmet Oluşturma'
ms.date: 03/30/2017
ms.assetid: 0283955a-b4ae-458d-ad9e-6fbb6f529e3d
ms.openlocfilehash: 9753fbc9b333cb7e89ddc8dff030cb1f62ede23b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600367"
---
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a><span data-ttu-id="f6779-102">Nasıl yapılır: WCF Web HTTP Programlama Modeli Kullanarak Rastgele Veriler Döndüren Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f6779-102">How to: Create a Service That Returns Arbitrary Data Using The WCF Web HTTP Programming Model</span></span>
<span data-ttu-id="f6779-103">Bazen geliştiricilerin, bir hizmet işleminden verilerin nasıl döndürüldüğünden tam denetime sahip olmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6779-103">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="f6779-104">Bu durum, bir hizmet işleminin WCF tarafından desteklenmeyen bir biçimde veri döndürmesi gereken durumdur.</span><span class="sxs-lookup"><span data-stu-id="f6779-104">This is the case when a service operation must return data in a format not supported by WCF.</span></span> <span data-ttu-id="f6779-105">Bu konuda, bu tür bir hizmet oluşturmak için WCF WEB HTTP programlama modelinin kullanımı ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f6779-105">This topic discusses using the WCF WEB HTTP Programming Model to create such a service.</span></span> <span data-ttu-id="f6779-106">Bu hizmette bir akış döndüren bir işlem vardır.</span><span class="sxs-lookup"><span data-stu-id="f6779-106">This service has one operation that returns a stream.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="f6779-107">Hizmet sözleşmesini uygulamak için</span><span class="sxs-lookup"><span data-stu-id="f6779-107">To implement the service contract</span></span>  
  
1. <span data-ttu-id="f6779-108">Hizmet sözleşmesini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="f6779-108">Define the service contract.</span></span> <span data-ttu-id="f6779-109">Anlaşma çağrılır `IImageServer` ve `GetImage` döndüren bir yöntemi vardır <xref:System.IO.Stream> .</span><span class="sxs-lookup"><span data-stu-id="f6779-109">The contract is called `IImageServer` and has one method called `GetImage` that returns a <xref:System.IO.Stream>.</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     <span data-ttu-id="f6779-110">Yöntemi bir döndürdüğü için <xref:System.IO.Stream> , WCF işlemin hizmet işleminden döndürülen baytlar üzerinde tamamlanmamış bir denetime sahip olduğunu ve döndürülen verilere hiçbir biçimlendirme uygulanmadığından emin olur.</span><span class="sxs-lookup"><span data-stu-id="f6779-110">Because the method returns a <xref:System.IO.Stream>, WCF assumes that the operation has complete control over the bytes that are returned from the service operation and it applies no formatting to the data that is returned.</span></span>  
  
2. <span data-ttu-id="f6779-111">Hizmet sözleşmesini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f6779-111">Implement the service contract.</span></span> <span data-ttu-id="f6779-112">Sözleşmede yalnızca bir işlem () vardır `GetImage` .</span><span class="sxs-lookup"><span data-stu-id="f6779-112">The contract has only one operation (`GetImage`).</span></span> <span data-ttu-id="f6779-113">Bu yöntem bir bit eşlem üretir ve sonra <xref:System.IO.MemoryStream> . jpg biçiminde kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f6779-113">This method generates a bitmap and then save it to a <xref:System.IO.MemoryStream> in .jpg format.</span></span> <span data-ttu-id="f6779-114">İşlem daha sonra bu akışı çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6779-114">The operation then returns that stream to the caller.</span></span>  
  
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
  
     <span data-ttu-id="f6779-115">İkinci kodun son satırına dikkat edin:`WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span><span class="sxs-lookup"><span data-stu-id="f6779-115">Notice the second to last line of code: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span></span>  
  
     <span data-ttu-id="f6779-116">Bu, içerik türü üst bilgisini olarak ayarlar `"image/jpeg"` .</span><span class="sxs-lookup"><span data-stu-id="f6779-116">This sets the content type header to `"image/jpeg"`.</span></span> <span data-ttu-id="f6779-117">Bu örnek, bir. jpg dosyasının nasıl döndürülmesini gösterir, ancak herhangi bir biçimde gerekli olan herhangi bir veri türünü döndürecek şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f6779-117">Although this sample shows how to return a .jpg file, it can be modified to return any type of data that is required, in any format.</span></span> <span data-ttu-id="f6779-118">İşlemin verileri alması veya oluşturması ve sonra bir akışa yazması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6779-118">The operation must retrieve or generate the data and then write it to a stream.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="f6779-119">Hizmeti barındırmak için</span><span class="sxs-lookup"><span data-stu-id="f6779-119">To host the service</span></span>  
  
1. <span data-ttu-id="f6779-120">Hizmeti barındırmak için bir konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f6779-120">Create a console application to host the service.</span></span>  
  
    ```csharp
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }
    }  
    ```  
  
2. <span data-ttu-id="f6779-121">Yöntemi içindeki hizmetin temel adresini tutacak bir değişken oluşturun `Main` .</span><span class="sxs-lookup"><span data-stu-id="f6779-121">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```csharp
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. <span data-ttu-id="f6779-122">Hizmet <xref:System.ServiceModel.ServiceHost> sınıfını ve temel adresi belirten hizmet için bir örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f6779-122">Create a <xref:System.ServiceModel.ServiceHost> instance for the service specifying the service class and the base address.</span></span>  
  
    ```csharp
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4. <span data-ttu-id="f6779-123">Ve kullanarak bir uç nokta ekleyin <xref:System.ServiceModel.WebHttpBinding> <xref:System.ServiceModel.Description.WebHttpBehavior> .</span><span class="sxs-lookup"><span data-stu-id="f6779-123">Add an endpoint using the <xref:System.ServiceModel.WebHttpBinding> and the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. <span data-ttu-id="f6779-124">Hizmet konağını açın.</span><span class="sxs-lookup"><span data-stu-id="f6779-124">Open the service host.</span></span>  
  
    ```csharp  
    host.Open();  
    ```  
  
6. <span data-ttu-id="f6779-125">Hizmeti sonlandırmak için kullanıcının ENTER tuşuna basmasına kadar bekleyin.</span><span class="sxs-lookup"><span data-stu-id="f6779-125">Wait until the user presses ENTER to terminate the service.</span></span>  
  
    ```csharp
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a><span data-ttu-id="f6779-126">Internet Explorer 'ı kullanarak ham hizmeti çağırmak için</span><span class="sxs-lookup"><span data-stu-id="f6779-126">To call the raw service using Internet Explorer</span></span>  
  
1. <span data-ttu-id="f6779-127">Hizmeti çalıştırın, hizmetten aşağıdaki çıktıyı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6779-127">Run the service, you should see the following output from the service.</span></span> `Service is running Press ENTER to close the host`  
  
2. <span data-ttu-id="f6779-128">Internet Explorer 'ı açın ve yazın, `http://localhost:8000/Service/GetImage?width=50&height=40` ortadaki mavi bir diyagonal çizgi ile sarı bir dikdörtgen görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6779-128">Open Internet Explorer and type in `http://localhost:8000/Service/GetImage?width=50&height=40` you should see a yellow rectangle with a blue diagonal line through the center.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6779-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6779-129">Example</span></span>  
 <span data-ttu-id="f6779-130">Aşağıda, bu konunun kodun tamambir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f6779-130">The following is a complete listing of the code for this topic.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="f6779-131">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f6779-131">Compiling the Code</span></span>  
  
- <span data-ttu-id="f6779-132">Örnek kod başvurusu System. ServiceModel. dll ve System. ServiceModel. Web. dll ' i derlerken.</span><span class="sxs-lookup"><span data-stu-id="f6779-132">When compiling the sample code reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6779-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6779-133">See also</span></span>

- [<span data-ttu-id="f6779-134">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="f6779-134">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
