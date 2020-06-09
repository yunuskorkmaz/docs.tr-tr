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
# <a name="how-to-create-a-service-that-accepts-arbitrary-data-using-the-wcf-rest-programming-model"></a><span data-ttu-id="ffd8c-102">Nasıl yapılır: WCF REST Programlama Modeli Kullanarak Rastgele Verileri Kabul Eden Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ffd8c-102">How to: Create a Service That Accepts Arbitrary Data using the WCF REST Programming Model</span></span>
<span data-ttu-id="ffd8c-103">Bazen geliştiricilerin, bir hizmet işleminden verilerin nasıl döndürüldüğünden tam denetime sahip olmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-103">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="ffd8c-104">Bu durum, bir hizmet işleminin verileri desteklenmeyen bir biçimde döndürmesi gereken bir biçimde (WCF), bu durumdur.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-104">This is the case when a service operation must return data in a format not supported byWCF.</span></span> <span data-ttu-id="ffd8c-105">Bu konuda, rastgele veri alan bir hizmet oluşturmak için WCF REST programlama modelinin kullanımı ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-105">This topic discusses using the WCF REST Programming Model to create a service that receives arbitrary data.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="ffd8c-106">Hizmet sözleşmesini uygulamak için</span><span class="sxs-lookup"><span data-stu-id="ffd8c-106">To implement the service contract</span></span>  
  
1. <span data-ttu-id="ffd8c-107">Hizmet sözleşmesini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-107">Define the service contract.</span></span> <span data-ttu-id="ffd8c-108">Rastgele verileri alan işlem türünde bir parametreye sahip olmalıdır <xref:System.IO.Stream> .</span><span class="sxs-lookup"><span data-stu-id="ffd8c-108">The operation that receives the arbitrary data must have a parameter of type <xref:System.IO.Stream>.</span></span> <span data-ttu-id="ffd8c-109">Ayrıca, bu parametre isteğin gövdesinde geçirilen tek parametre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-109">In addition, this parameter must be the only parameter passed in the body of the request.</span></span> <span data-ttu-id="ffd8c-110">Bu örnekte açıklanan işlem de bir filename parametresi alır.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-110">The operation described in this example also takes a filename parameter.</span></span> <span data-ttu-id="ffd8c-111">Bu parametre isteğin URL 'SI içinde geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-111">This parameter is passed within the URL of the request.</span></span> <span data-ttu-id="ffd8c-112">İçinde bir parametre belirterek parametrenin URL içinde geçtiğini belirtebilirsiniz <xref:System.UriTemplate> <xref:System.ServiceModel.Web.WebInvokeAttribute> .</span><span class="sxs-lookup"><span data-stu-id="ffd8c-112">You can specify that a parameter is passed within the URL by specifying a <xref:System.UriTemplate> in the <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="ffd8c-113">Bu durumda, bu yöntemi çağırmak için kullanılan URI "UploadFile/some-filename" içinde sona erer.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-113">In this case the URI used to call this method ends in "UploadFile/Some-Filename".</span></span> <span data-ttu-id="ffd8c-114">URI şablonunun "{filename}" kısmı, işlem için dosya adı parametresinin işlemi çağırmak için kullanılan URI içinde geçtiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-114">The "{filename}" portion of the URI template specifies that the filename parameter for the operation is passed within the URI used to call the operation.</span></span>  
  
    ```csharp  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2. <span data-ttu-id="ffd8c-115">Hizmet sözleşmesini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-115">Implement the service contract.</span></span> <span data-ttu-id="ffd8c-116">Sözleşmede bir `UploadFile` akışta rastgele veri dosyası alan yalnızca bir yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-116">The contract has only one method, `UploadFile` that receives a file of arbitrary data in a stream.</span></span> <span data-ttu-id="ffd8c-117">Bu işlem, okunan bayt sayısını sayarak akışı okur ve sonra dosya adını ve okunan bayt sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-117">The operation reads the stream counting the number of bytes read and then displays the filename and the number of bytes read.</span></span>  
  
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
  
### <a name="to-host-the-service"></a><span data-ttu-id="ffd8c-118">Hizmeti barındırmak için</span><span class="sxs-lookup"><span data-stu-id="ffd8c-118">To host the service</span></span>  
  
1. <span data-ttu-id="ffd8c-119">Hizmeti barındırmak için bir konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-119">Create a console application to host the service.</span></span>  
  
    ```csharp  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
    ```  
  
2. <span data-ttu-id="ffd8c-120">Yöntemi içindeki hizmetin temel adresini tutacak bir değişken oluşturun `Main` .</span><span class="sxs-lookup"><span data-stu-id="ffd8c-120">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```csharp  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. <span data-ttu-id="ffd8c-121">Hizmet <xref:System.ServiceModel.ServiceHost> sınıfı ve temel adresi belirten bir örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-121">Create a <xref:System.ServiceModel.ServiceHost> instance for the service that specifies the service class and the base address.</span></span>  
  
    ```csharp  
    ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
    ```  
  
4. <span data-ttu-id="ffd8c-122">, Ve sözleşmesini belirten bir uç nokta ekleyin <xref:System.ServiceModel.WebHttpBinding> <xref:System.ServiceModel.Description.WebHttpBehavior> .</span><span class="sxs-lookup"><span data-stu-id="ffd8c-122">Add an endpoint that specifies the contract, <xref:System.ServiceModel.WebHttpBinding>, and <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. <span data-ttu-id="ffd8c-123">Hizmet konağını açın.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-123">Open the service host.</span></span> <span data-ttu-id="ffd8c-124">Hizmet artık istekleri almaya hazırdır.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-124">The service is now ready to receive requests.</span></span>  
  
    ```csharp  
    host.Open();  
    Console.WriteLine("Host opened");  
    ```  
  
### <a name="to-call-the-service-programmatically"></a><span data-ttu-id="ffd8c-125">Hizmeti programlı olarak çağırmak için</span><span class="sxs-lookup"><span data-stu-id="ffd8c-125">To call the service programmatically</span></span>  
  
1. <span data-ttu-id="ffd8c-126"><xref:System.Net.HttpWebRequest>Hizmeti çağırmak için kullanılan URI ile bir oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-126">Create a <xref:System.Net.HttpWebRequest> with the URI used to call the service.</span></span> <span data-ttu-id="ffd8c-127">Bu kodda, temel adres ile birleştirilir `"/UploadFile/Text"` .</span><span class="sxs-lookup"><span data-stu-id="ffd8c-127">In this code, the base address is combined with `"/UploadFile/Text"`.</span></span> <span data-ttu-id="ffd8c-128">`"UploadFile"`URI 'nin bölümü çağrılacak işlemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-128">The `"UploadFile"` portion of the URI specifies the operation to call.</span></span> <span data-ttu-id="ffd8c-129">`"Test.txt"`URI 'nin bölümü, işleme geçirilecek filename parametresini belirtir `UploadFile` .</span><span class="sxs-lookup"><span data-stu-id="ffd8c-129">The `"Test.txt"` portion of the URI specifies the filename parameter to pass to the `UploadFile` operation.</span></span> <span data-ttu-id="ffd8c-130">Bu öğelerin her ikisi de <xref:System.UriTemplate> işlem sözleşmesine uygulanan ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-130">Both of these items map to the <xref:System.UriTemplate> applied to the operation contract.</span></span>  
  
    ```csharp  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
    ```  
  
2. <span data-ttu-id="ffd8c-131"><xref:System.Net.HttpWebRequest.Method%2A> <xref:System.Net.HttpWebRequest> `POST` Ve <xref:System.Net.HttpWebRequest.ContentType%2A> özelliğinin özelliğini olarak ayarlayın `"text/plain"` .</span><span class="sxs-lookup"><span data-stu-id="ffd8c-131">Set the <xref:System.Net.HttpWebRequest.Method%2A> property of the <xref:System.Net.HttpWebRequest> to `POST` and the <xref:System.Net.HttpWebRequest.ContentType%2A> property to `"text/plain"`.</span></span> <span data-ttu-id="ffd8c-132">Bu, hizmete kodun veri gönderdiğini ve verilerin düz metin olduğunu söyler.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-132">This tells the service that the code is sending data and that data is in plain text.</span></span>  
  
    ```csharp  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3. <span data-ttu-id="ffd8c-133"><xref:System.Net.HttpWebRequest.GetRequestStream%2A>İstek akışını almak için çağrısı yapın, gönderecek verileri oluşturun, bu verileri istek akışına yazın ve akışı kapatın.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-133">Call <xref:System.Net.HttpWebRequest.GetRequestStream%2A> to get the request stream, create the data to send, write that data to the request stream, and close the stream.</span></span>  
  
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
  
4. <span data-ttu-id="ffd8c-134"><xref:System.Net.HttpWebRequest.GetResponse%2A>Yanıt verilerini çağırarak ve konsola görüntüleyerek hizmetten gelen yanıtı alın.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-134">Get the response from the service by calling <xref:System.Net.HttpWebRequest.GetResponse%2A> and display the response data to the console.</span></span>  
  
    ```csharp  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
    ```  
  
5. <span data-ttu-id="ffd8c-135">Hizmet konağını kapatın.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-135">Close the service host.</span></span>  
  
    ```csharp  
    host.Close();  
    ```  
  
## <a name="example"></a><span data-ttu-id="ffd8c-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="ffd8c-136">Example</span></span>  
 <span data-ttu-id="ffd8c-137">Aşağıda bu örnek için kodun tamamen bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-137">The following is a complete listing of the code for this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="ffd8c-138">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ffd8c-138">Compiling the Code</span></span>  
  
- <span data-ttu-id="ffd8c-139">System. ServiceModel. dll ve System. ServiceModel. Web. dll kod başvurusunu derlerken</span><span class="sxs-lookup"><span data-stu-id="ffd8c-139">When compiling the code reference System.ServiceModel.dll and System.ServiceModel.Web.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffd8c-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ffd8c-140">See also</span></span>

- [<span data-ttu-id="ffd8c-141">UriTemplate ve UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="ffd8c-141">UriTemplate and UriTemplateTable</span></span>](uritemplate-and-uritemplatetable.md)
- [<span data-ttu-id="ffd8c-142">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="ffd8c-142">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="ffd8c-143">WCF Web HTTP Programlama Modeli Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ffd8c-143">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)
