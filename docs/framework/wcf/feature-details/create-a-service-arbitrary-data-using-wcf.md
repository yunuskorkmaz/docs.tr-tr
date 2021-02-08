---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: WCF REST programlama modelini kullanarak rastgele verileri kabul eden bir hizmet oluşturma'
title: 'Nasıl yapılır: WCF REST Programlama Modeli Kullanarak Rastgele Verileri Kabul Eden Bir Hizmet Oluşturma'
ms.date: 03/30/2017
ms.assetid: e566c15a-b600-4e4a-be3a-4af43e767dae
ms.openlocfilehash: a08e611b51d92e070f18620d61a2b95de2cd6cfb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780329"
---
# <a name="how-to-create-a-service-that-accepts-arbitrary-data-using-the-wcf-rest-programming-model"></a><span data-ttu-id="49735-103">Nasıl yapılır: WCF REST Programlama Modeli Kullanarak Rastgele Verileri Kabul Eden Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="49735-103">How to: Create a Service That Accepts Arbitrary Data using the WCF REST Programming Model</span></span>

<span data-ttu-id="49735-104">Bazen geliştiricilerin, bir hizmet işleminden verilerin nasıl döndürüldüğünden tam denetime sahip olmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="49735-104">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="49735-105">Bu durum, bir hizmet işleminin verileri desteklenmeyen bir biçimde döndürmesi gereken bir biçimde (WCF), bu durumdur.</span><span class="sxs-lookup"><span data-stu-id="49735-105">This is the case when a service operation must return data in a format not supported byWCF.</span></span> <span data-ttu-id="49735-106">Bu konuda, rastgele veri alan bir hizmet oluşturmak için WCF REST programlama modelinin kullanımı ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="49735-106">This topic discusses using the WCF REST Programming Model to create a service that receives arbitrary data.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="49735-107">Hizmet sözleşmesini uygulamak için</span><span class="sxs-lookup"><span data-stu-id="49735-107">To implement the service contract</span></span>  
  
1. <span data-ttu-id="49735-108">Hizmet sözleşmesini tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="49735-108">Define the service contract.</span></span> <span data-ttu-id="49735-109">Rastgele verileri alan işlem türünde bir parametreye sahip olmalıdır <xref:System.IO.Stream> .</span><span class="sxs-lookup"><span data-stu-id="49735-109">The operation that receives the arbitrary data must have a parameter of type <xref:System.IO.Stream>.</span></span> <span data-ttu-id="49735-110">Ayrıca, bu parametre isteğin gövdesinde geçirilen tek parametre olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="49735-110">In addition, this parameter must be the only parameter passed in the body of the request.</span></span> <span data-ttu-id="49735-111">Bu örnekte açıklanan işlem de bir filename parametresi alır.</span><span class="sxs-lookup"><span data-stu-id="49735-111">The operation described in this example also takes a filename parameter.</span></span> <span data-ttu-id="49735-112">Bu parametre isteğin URL 'SI içinde geçirilir.</span><span class="sxs-lookup"><span data-stu-id="49735-112">This parameter is passed within the URL of the request.</span></span> <span data-ttu-id="49735-113">İçinde bir parametre belirterek parametrenin URL içinde geçtiğini belirtebilirsiniz <xref:System.UriTemplate> <xref:System.ServiceModel.Web.WebInvokeAttribute> .</span><span class="sxs-lookup"><span data-stu-id="49735-113">You can specify that a parameter is passed within the URL by specifying a <xref:System.UriTemplate> in the <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="49735-114">Bu durumda, bu yöntemi çağırmak için kullanılan URI "UploadFile/some-filename" içinde sona erer.</span><span class="sxs-lookup"><span data-stu-id="49735-114">In this case the URI used to call this method ends in "UploadFile/Some-Filename".</span></span> <span data-ttu-id="49735-115">URI şablonunun "{filename}" kısmı, işlem için dosya adı parametresinin işlemi çağırmak için kullanılan URI içinde geçtiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="49735-115">The "{filename}" portion of the URI template specifies that the filename parameter for the operation is passed within the URI used to call the operation.</span></span>  
  
    ```csharp  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2. <span data-ttu-id="49735-116">Hizmet sözleşmesini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="49735-116">Implement the service contract.</span></span> <span data-ttu-id="49735-117">Sözleşmede bir `UploadFile` akışta rastgele veri dosyası alan yalnızca bir yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="49735-117">The contract has only one method, `UploadFile` that receives a file of arbitrary data in a stream.</span></span> <span data-ttu-id="49735-118">Bu işlem, okunan bayt sayısını sayarak akışı okur ve sonra dosya adını ve okunan bayt sayısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="49735-118">The operation reads the stream counting the number of bytes read and then displays the filename and the number of bytes read.</span></span>  
  
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
  
### <a name="to-host-the-service"></a><span data-ttu-id="49735-119">Hizmeti barındırmak için</span><span class="sxs-lookup"><span data-stu-id="49735-119">To host the service</span></span>  
  
1. <span data-ttu-id="49735-120">Hizmeti barındırmak için bir konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="49735-120">Create a console application to host the service.</span></span>  
  
    ```csharp  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
    ```  
  
2. <span data-ttu-id="49735-121">Yöntemi içindeki hizmetin temel adresini tutacak bir değişken oluşturun `Main` .</span><span class="sxs-lookup"><span data-stu-id="49735-121">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```csharp  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3. <span data-ttu-id="49735-122">Hizmet <xref:System.ServiceModel.ServiceHost> sınıfı ve temel adresi belirten bir örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="49735-122">Create a <xref:System.ServiceModel.ServiceHost> instance for the service that specifies the service class and the base address.</span></span>  
  
    ```csharp  
    ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
    ```  
  
4. <span data-ttu-id="49735-123">, Ve sözleşmesini belirten bir uç nokta ekleyin <xref:System.ServiceModel.WebHttpBinding> <xref:System.ServiceModel.Description.WebHttpBehavior> .</span><span class="sxs-lookup"><span data-stu-id="49735-123">Add an endpoint that specifies the contract, <xref:System.ServiceModel.WebHttpBinding>, and <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5. <span data-ttu-id="49735-124">Hizmet konağını açın.</span><span class="sxs-lookup"><span data-stu-id="49735-124">Open the service host.</span></span> <span data-ttu-id="49735-125">Hizmet artık istekleri almaya hazırdır.</span><span class="sxs-lookup"><span data-stu-id="49735-125">The service is now ready to receive requests.</span></span>  
  
    ```csharp  
    host.Open();  
    Console.WriteLine("Host opened");  
    ```  
  
### <a name="to-call-the-service-programmatically"></a><span data-ttu-id="49735-126">Hizmeti programlı olarak çağırmak için</span><span class="sxs-lookup"><span data-stu-id="49735-126">To call the service programmatically</span></span>  
  
1. <span data-ttu-id="49735-127"><xref:System.Net.HttpWebRequest>Hizmeti çağırmak için kullanılan URI ile bir oluşturun.</span><span class="sxs-lookup"><span data-stu-id="49735-127">Create a <xref:System.Net.HttpWebRequest> with the URI used to call the service.</span></span> <span data-ttu-id="49735-128">Bu kodda, temel adres ile birleştirilir `"/UploadFile/Text"` .</span><span class="sxs-lookup"><span data-stu-id="49735-128">In this code, the base address is combined with `"/UploadFile/Text"`.</span></span> <span data-ttu-id="49735-129">`"UploadFile"`URI 'nin bölümü çağrılacak işlemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="49735-129">The `"UploadFile"` portion of the URI specifies the operation to call.</span></span> <span data-ttu-id="49735-130">`"Test.txt"`URI 'nin bölümü, işleme geçirilecek filename parametresini belirtir `UploadFile` .</span><span class="sxs-lookup"><span data-stu-id="49735-130">The `"Test.txt"` portion of the URI specifies the filename parameter to pass to the `UploadFile` operation.</span></span> <span data-ttu-id="49735-131">Bu öğelerin her ikisi de <xref:System.UriTemplate> işlem sözleşmesine uygulanan ile eşlenir.</span><span class="sxs-lookup"><span data-stu-id="49735-131">Both of these items map to the <xref:System.UriTemplate> applied to the operation contract.</span></span>  
  
    ```csharp  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
    ```  
  
2. <span data-ttu-id="49735-132"><xref:System.Net.HttpWebRequest.Method%2A> <xref:System.Net.HttpWebRequest> `POST` Ve <xref:System.Net.HttpWebRequest.ContentType%2A> özelliğinin özelliğini olarak ayarlayın `"text/plain"` .</span><span class="sxs-lookup"><span data-stu-id="49735-132">Set the <xref:System.Net.HttpWebRequest.Method%2A> property of the <xref:System.Net.HttpWebRequest> to `POST` and the <xref:System.Net.HttpWebRequest.ContentType%2A> property to `"text/plain"`.</span></span> <span data-ttu-id="49735-133">Bu, hizmete kodun veri gönderdiğini ve verilerin düz metin olduğunu söyler.</span><span class="sxs-lookup"><span data-stu-id="49735-133">This tells the service that the code is sending data and that data is in plain text.</span></span>  
  
    ```csharp  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3. <span data-ttu-id="49735-134"><xref:System.Net.HttpWebRequest.GetRequestStream%2A>İstek akışını almak için çağrısı yapın, gönderecek verileri oluşturun, bu verileri istek akışına yazın ve akışı kapatın.</span><span class="sxs-lookup"><span data-stu-id="49735-134">Call <xref:System.Net.HttpWebRequest.GetRequestStream%2A> to get the request stream, create the data to send, write that data to the request stream, and close the stream.</span></span>  
  
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
  
4. <span data-ttu-id="49735-135"><xref:System.Net.HttpWebRequest.GetResponse%2A>Yanıt verilerini çağırarak ve konsola görüntüleyerek hizmetten gelen yanıtı alın.</span><span class="sxs-lookup"><span data-stu-id="49735-135">Get the response from the service by calling <xref:System.Net.HttpWebRequest.GetResponse%2A> and display the response data to the console.</span></span>  
  
    ```csharp  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
    ```  
  
5. <span data-ttu-id="49735-136">Hizmet konağını kapatın.</span><span class="sxs-lookup"><span data-stu-id="49735-136">Close the service host.</span></span>  
  
    ```csharp  
    host.Close();  
    ```  
  
## <a name="example"></a><span data-ttu-id="49735-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="49735-137">Example</span></span>  

 <span data-ttu-id="49735-138">Aşağıda bu örnek için kodun tamamen bir listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="49735-138">The following is a complete listing of the code for this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="49735-139">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="49735-139">Compiling the Code</span></span>  
  
- <span data-ttu-id="49735-140">Kod başvurusunu derlerken System.ServiceModel.dll ve System.ServiceModel.Web.dll</span><span class="sxs-lookup"><span data-stu-id="49735-140">When compiling the code reference System.ServiceModel.dll and System.ServiceModel.Web.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49735-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49735-141">See also</span></span>

- [<span data-ttu-id="49735-142">UriTemplate ve UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="49735-142">UriTemplate and UriTemplateTable</span></span>](uritemplate-and-uritemplatetable.md)
- [<span data-ttu-id="49735-143">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="49735-143">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="49735-144">WCF Web HTTP Programlama Modeli Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="49735-144">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)
