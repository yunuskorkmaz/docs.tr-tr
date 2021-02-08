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
# <a name="how-to-create-a-service-that-returns-arbitrary-data-using-the-wcf-web-http-programming-model"></a><span data-ttu-id="57edb-103">Nasıl yapılır: WCF Web HTTP Programlama Modeli Kullanarak Rastgele Veriler Döndüren Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="57edb-103">How to: Create a Service That Returns Arbitrary Data Using The WCF Web HTTP Programming Model</span></span>

<span data-ttu-id="57edb-104">Bazen geliştiricilerin, bir hizmet işleminden verilerin nasıl döndürüldüğünden tam denetime sahip olmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="57edb-104">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="57edb-105">Bu durum, bir hizmet işleminin WCF tarafından desteklenmeyen bir biçimde veri döndürmesi gereken durumdur.</span><span class="sxs-lookup"><span data-stu-id="57edb-105">This is the case when a service operation must return data in a format not supported by WCF.</span></span> <span data-ttu-id="57edb-106">Bu konuda, bu tür bir hizmet oluşturmak için WCF WEB HTTP programlama modelinin kullanımı ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="57edb-106">This topic discusses using the WCF WEB HTTP Programming Model to create such a service.</span></span> <span data-ttu-id="57edb-107">Bu hizmette bir akış döndüren bir işlem vardır.</span><span class="sxs-lookup"><span data-stu-id="57edb-107">This service has one operation that returns a stream.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="57edb-108">Hizmet sözleşmesini uygulamak için</span><span class="sxs-lookup"><span data-stu-id="57edb-108">To implement the service contract</span></span>  
  
1. <span data-ttu-id="57edb-109">Hizmet sözleşmesini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="57edb-109">Define the service contract.</span></span> <span data-ttu-id="57edb-110">Anlaşma çağrılır `IImageServer` ve `GetImage` döndüren bir yöntemi vardır <xref:System.IO.Stream> .</span><span class="sxs-lookup"><span data-stu-id="57edb-110">The contract is called `IImageServer` and has one method called `GetImage` that returns a <xref:System.IO.Stream>.</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IImageServer  
        {  
            [WebGet]  
            Stream GetImage(int width, int height);  
        }  
    ```  
  
     <span data-ttu-id="57edb-111">Yöntemi bir döndürdüğü için <xref:System.IO.Stream> , WCF işlemin hizmet işleminden döndürülen baytlar üzerinde tamamlanmamış bir denetime sahip olduğunu ve döndürülen verilere hiçbir biçimlendirme uygulanmadığından emin olur.</span><span class="sxs-lookup"><span data-stu-id="57edb-111">Because the method returns a <xref:System.IO.Stream>, WCF assumes that the operation has complete control over the bytes that are returned from the service operation and it applies no formatting to the data that is returned.</span></span>  
  
2. <span data-ttu-id="57edb-112">Hizmet sözleşmesini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="57edb-112">Implement the service contract.</span></span> <span data-ttu-id="57edb-113">Sözleşmede yalnızca bir işlem () vardır `GetImage` .</span><span class="sxs-lookup"><span data-stu-id="57edb-113">The contract has only one operation (`GetImage`).</span></span> <span data-ttu-id="57edb-114">Bu yöntem bir bit eşlem üretir ve sonra <xref:System.IO.MemoryStream> . jpg biçiminde kaydeder.</span><span class="sxs-lookup"><span data-stu-id="57edb-114">This method generates a bitmap and then save it to a <xref:System.IO.MemoryStream> in .jpg format.</span></span> <span data-ttu-id="57edb-115">İşlem daha sonra bu akışı çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="57edb-115">The operation then returns that stream to the caller.</span></span>  
  
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
  
     <span data-ttu-id="57edb-116">İkinci kodun son satırına dikkat edin: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span><span class="sxs-lookup"><span data-stu-id="57edb-116">Notice the second to last line of code: `WebOperationContext.Current.OutgoingResponse.ContentType = "image/jpeg";`</span></span>  
  
     <span data-ttu-id="57edb-117">Bu, içerik türü üst bilgisini olarak ayarlar `"image/jpeg"` .</span><span class="sxs-lookup"><span data-stu-id="57edb-117">This sets the content type header to `"image/jpeg"`.</span></span> <span data-ttu-id="57edb-118">Bu örnek, bir. jpg dosyasının nasıl döndürülmesini gösterir, ancak herhangi bir biçimde gerekli olan herhangi bir veri türünü döndürecek şekilde değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="57edb-118">Although this sample shows how to return a .jpg file, it can be modified to return any type of data that is required, in any format.</span></span> <span data-ttu-id="57edb-119">İşlemin verileri alması veya oluşturması ve sonra bir akışa yazması gerekir.</span><span class="sxs-lookup"><span data-stu-id="57edb-119">The operation must retrieve or generate the data and then write it to a stream.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="57edb-120">Hizmeti barındırmak için</span><span class="sxs-lookup"><span data-stu-id="57edb-120">To host the service</span></span>  
  
1. <span data-ttu-id="57edb-121">Hizmeti barındırmak için bir konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="57edb-121">Create a console application to host the service.</span></span>  
  
    ```csharp
    class Program  
    {  
        static void Main(string[] args)  
        {  
        }
    }  
    ```  
  
2. <span data-ttu-id="57edb-122">Yöntemi içindeki hizmetin temel adresini tutacak bir değişken oluşturun `Main` .</span><span class="sxs-lookup"><span data-stu-id="57edb-122">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```csharp
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. <span data-ttu-id="57edb-123">Hizmet <xref:System.ServiceModel.ServiceHost> sınıfını ve temel adresi belirten hizmet için bir örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="57edb-123">Create a <xref:System.ServiceModel.ServiceHost> instance for the service specifying the service class and the base address.</span></span>  
  
    ```csharp
    ServiceHost host = new ServiceHost(typeof(Service), new Uri(baseAddress));  
    ```  
  
4. <span data-ttu-id="57edb-124">Ve kullanarak bir uç nokta ekleyin <xref:System.ServiceModel.WebHttpBinding> <xref:System.ServiceModel.Description.WebHttpBehavior> .</span><span class="sxs-lookup"><span data-stu-id="57edb-124">Add an endpoint using the <xref:System.ServiceModel.WebHttpBinding> and the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IImageServer), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. <span data-ttu-id="57edb-125">Hizmet konağını açın.</span><span class="sxs-lookup"><span data-stu-id="57edb-125">Open the service host.</span></span>  
  
    ```csharp  
    host.Open();  
    ```  
  
6. <span data-ttu-id="57edb-126">Hizmeti sonlandırmak için kullanıcının ENTER tuşuna basmasına kadar bekleyin.</span><span class="sxs-lookup"><span data-stu-id="57edb-126">Wait until the user presses ENTER to terminate the service.</span></span>  
  
    ```csharp
    Console.WriteLine("Service is running");  
    Console.Write("Press ENTER to close the host");  
    Console.ReadLine();  
    host.Close();  
    ```  
  
### <a name="to-call-the-raw-service-using-internet-explorer"></a><span data-ttu-id="57edb-127">Internet Explorer 'ı kullanarak ham hizmeti çağırmak için</span><span class="sxs-lookup"><span data-stu-id="57edb-127">To call the raw service using Internet Explorer</span></span>  
  
1. <span data-ttu-id="57edb-128">Hizmeti çalıştırın, hizmetten aşağıdaki çıktıyı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="57edb-128">Run the service, you should see the following output from the service.</span></span> `Service is running Press ENTER to close the host`  
  
2. <span data-ttu-id="57edb-129">Internet Explorer 'ı açın ve yazın, `http://localhost:8000/Service/GetImage?width=50&height=40` ortadaki mavi bir diyagonal çizgi ile sarı bir dikdörtgen görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="57edb-129">Open Internet Explorer and type in `http://localhost:8000/Service/GetImage?width=50&height=40` you should see a yellow rectangle with a blue diagonal line through the center.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57edb-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="57edb-130">Example</span></span>  

 <span data-ttu-id="57edb-131">Aşağıda, bu konunun kodun tamambir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="57edb-131">The following is a complete listing of the code for this topic.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="57edb-132">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="57edb-132">Compiling the Code</span></span>  
  
- <span data-ttu-id="57edb-133">Örnek kod başvurusunu derlerken System.ServiceModel.dll ve System.ServiceModel.Web.dll.</span><span class="sxs-lookup"><span data-stu-id="57edb-133">When compiling the sample code reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57edb-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57edb-134">See also</span></span>

- [<span data-ttu-id="57edb-135">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="57edb-135">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
