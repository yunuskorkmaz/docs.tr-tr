---
title: 'Nasıl yapılır: WCF REST Programlama Modeli Kullanarak Rastgele Verileri Kabul Eden Bir Hizmet Oluşturma'
ms.date: 03/30/2017
ms.assetid: e566c15a-b600-4e4a-be3a-4af43e767dae
ms.openlocfilehash: c03450c66cf8de14d6c638550a510a91593c45b6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144085"
---
# <a name="how-to-create-a-service-that-accepts-arbitrary-data-using-the-wcf-rest-programming-model"></a><span data-ttu-id="3f8e8-102">Nasıl yapılır: WCF REST Programlama Modeli Kullanarak Rastgele Verileri Kabul Eden Bir Hizmet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3f8e8-102">How to: Create a Service That Accepts Arbitrary Data using the WCF REST Programming Model</span></span>
<span data-ttu-id="3f8e8-103">Bazen geliştiriciler, veri hizmeti işleminden döndürülen nasıl tam denetimi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-103">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="3f8e8-104">Bir hizmet işlemi, verileri bir biçimde byWCF desteklenmiyor döndürmelidir olduğunda bu durum geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-104">This is the case when a service operation must return data in a format not supported byWCF.</span></span> <span data-ttu-id="3f8e8-105">Bu konuda, rastgele verileri alan bir hizmet oluşturmak için WCF REST programlama modeli kullanarak anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-105">This topic discusses using the WCF REST Programming Model to create a service that receives arbitrary data.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="3f8e8-106">Hizmet sözleşmesini uygulama</span><span class="sxs-lookup"><span data-stu-id="3f8e8-106">To implement the service contract</span></span>  
  
1.  <span data-ttu-id="3f8e8-107">Hizmet sözleşmesini tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-107">Define the service contract.</span></span> <span data-ttu-id="3f8e8-108">Rastgele veri aldığında işlem türünde bir parametresi olmalıdır <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-108">The operation that receives the arbitrary data must have a parameter of type <xref:System.IO.Stream>.</span></span> <span data-ttu-id="3f8e8-109">Ayrıca, bu parametre istek gövdesinde geçirilen tek parametresi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-109">In addition, this parameter must be the only parameter passed in the body of the request.</span></span> <span data-ttu-id="3f8e8-110">Bu örnekte açıklanan işlem, ayrıca bir filename parametresi alır.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-110">The operation described in this example also takes a filename parameter.</span></span> <span data-ttu-id="3f8e8-111">Bu parametre, istek URL'si içinde iletilir.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-111">This parameter is passed within the URL of the request.</span></span> <span data-ttu-id="3f8e8-112">Parametre URL'sini belirterek geçirilen belirtebileceğiniz bir <xref:System.UriTemplate> içinde <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-112">You can specify that a parameter is passed within the URL by specifying a <xref:System.UriTemplate> in the <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="3f8e8-113">URI çağırmak için kullanılan bu durumda bu yöntem, "UploadFile/bazı-dosya adı" sona erer.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-113">In this case the URI used to call this method ends in "UploadFile/Some-Filename".</span></span> <span data-ttu-id="3f8e8-114">URI şablonu "{filename}" kısmı, işlemi için dosya adı parametresi işlemi çağırmak için kullanılan URI içinde geçirildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-114">The "{filename}" portion of the URI template specifies that the filename parameter for the operation is passed within the URI used to call the operation.</span></span>  
  
    ```csharp  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2.  <span data-ttu-id="3f8e8-115">Hizmet sözleşmesini uygulama.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-115">Implement the service contract.</span></span> <span data-ttu-id="3f8e8-116">Sözleşme yalnızca bir yöntem olan `UploadFile` , rastgele veriler dosyası bir akışa alır.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-116">The contract has only one method, `UploadFile` that receives a file of arbitrary data in a stream.</span></span> <span data-ttu-id="3f8e8-117">İşlemin bayt sayısını sayma stream okuyun ve ardından dosya adı ve okunan bayt sayısını görüntüler okur.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-117">The operation reads the stream counting the number of bytes read and then displays the filename and the number of bytes read.</span></span>  
  
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
  
### <a name="to-host-the-service"></a><span data-ttu-id="3f8e8-118">Ana bilgisayar hizmeti</span><span class="sxs-lookup"><span data-stu-id="3f8e8-118">To host the service</span></span>  
  
1.  <span data-ttu-id="3f8e8-119">Hizmeti barındırmak için bir konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-119">Create a console application to host the service.</span></span>  
  
    ```csharp  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
    ```  
  
2.  <span data-ttu-id="3f8e8-120">İçinde hizmet için temel adresini tutacak bir değişken oluşturma `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-120">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```csharp  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3.  <span data-ttu-id="3f8e8-121">Oluşturma bir <xref:System.ServiceModel.ServiceHost> hizmet sınıfı ve taban adresini belirten bir hizmet örneği.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-121">Create a <xref:System.ServiceModel.ServiceHost> instance for the service that specifies the service class and the base address.</span></span>  
  
    ```csharp  
    ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
    ```  
  
4.  <span data-ttu-id="3f8e8-122">Sözleşme belirten bir uç nokta ekleyin <xref:System.ServiceModel.WebHttpBinding>, ve <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-122">Add an endpoint that specifies the contract, <xref:System.ServiceModel.WebHttpBinding>, and <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5.  <span data-ttu-id="3f8e8-123">Hizmet ana bilgisayarı açın.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-123">Open the service host.</span></span> <span data-ttu-id="3f8e8-124">Hizmet isteklerini almak artık hazırdır.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-124">The service is now ready to receive requests.</span></span>  
  
    ```csharp  
    host.Open();  
    Console.WriteLine("Host opened");  
    ```  
  
### <a name="to-call-the-service-programmatically"></a><span data-ttu-id="3f8e8-125">Program aracılığıyla hizmeti çağırmak için</span><span class="sxs-lookup"><span data-stu-id="3f8e8-125">To call the service programmatically</span></span>  
  
1.  <span data-ttu-id="3f8e8-126">Oluşturma bir <xref:System.Net.HttpWebRequest> hizmeti çağırmak için kullanılan URI ile.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-126">Create a <xref:System.Net.HttpWebRequest> with the URI used to call the service.</span></span> <span data-ttu-id="3f8e8-127">Bu kodda, temel adresi ile birleştirilir `"/UploadFile/Text"`.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-127">In this code, the base address is combined with `"/UploadFile/Text"`.</span></span> <span data-ttu-id="3f8e8-128">`"UploadFile"` URI kısmı aranacak işlem belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-128">The `"UploadFile"` portion of the URI specifies the operation to call.</span></span> <span data-ttu-id="3f8e8-129">`"Test.txt"` URI kısmı belirtir geçirilecek filename parametresi `UploadFile` işlemi.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-129">The `"Test.txt"` portion of the URI specifies the filename parameter to pass to the `UploadFile` operation.</span></span> <span data-ttu-id="3f8e8-130">Bu öğelerinin her ikisini de eşlemek <xref:System.UriTemplate> da işlem anlaşması için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-130">Both of these items map to the <xref:System.UriTemplate> applied to the operation contract.</span></span>  
  
    ```csharp  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
    ```  
  
2.  <span data-ttu-id="3f8e8-131">Ayarlama <xref:System.Net.HttpWebRequest.Method%2A> özelliği <xref:System.Net.HttpWebRequest> için `POST` ve <xref:System.Net.HttpWebRequest.ContentType%2A> özelliğini `"text/plain"`.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-131">Set the <xref:System.Net.HttpWebRequest.Method%2A> property of the <xref:System.Net.HttpWebRequest> to `POST` and the <xref:System.Net.HttpWebRequest.ContentType%2A> property to `"text/plain"`.</span></span> <span data-ttu-id="3f8e8-132">Bu kod, veri göndermek ve bu veriler düz metin olarak yapılır hizmet bildirir.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-132">This tells the service that the code is sending data and that data is in plain text.</span></span>  
  
    ```csharp  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3.  <span data-ttu-id="3f8e8-133">Çağrı <xref:System.Net.HttpWebRequest.GetRequestStream%2A> İstek akışını almak için veri göndermek, bu veri isteği akışa yazmak ve akış Kapat oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-133">Call <xref:System.Net.HttpWebRequest.GetRequestStream%2A> to get the request stream, create the data to send, write that data to the request stream, and close the stream.</span></span>  
  
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
  
4.  <span data-ttu-id="3f8e8-134">Çağırarak hizmetten yanıt alma <xref:System.Net.HttpWebRequest.GetResponse%2A> ve konsola yanıt verileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-134">Get the response from the service by calling <xref:System.Net.HttpWebRequest.GetResponse%2A> and display the response data to the console.</span></span>  
  
    ```csharp  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
    ```  
  
5.  <span data-ttu-id="3f8e8-135">Hizmet ana bilgisayarını kapatın.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-135">Close the service host.</span></span>  
  
    ```csharp  
    host.Close();  
    ```  
  
## <a name="example"></a><span data-ttu-id="3f8e8-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="3f8e8-136">Example</span></span>  
 <span data-ttu-id="3f8e8-137">Bu örnek için kod tam listesi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-137">The following is a complete listing of the code for this example.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="3f8e8-138">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="3f8e8-138">Compiling the Code</span></span>  
  
-   <span data-ttu-id="3f8e8-139">Kod başvurusu System.ServiceModel.dll ve System.ServiceModel.Web.dll derlenirken</span><span class="sxs-lookup"><span data-stu-id="3f8e8-139">When compiling the code reference System.ServiceModel.dll and System.ServiceModel.Web.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f8e8-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f8e8-140">See also</span></span>

- [<span data-ttu-id="3f8e8-141">UriTemplate ve UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="3f8e8-141">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)
- [<span data-ttu-id="3f8e8-142">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="3f8e8-142">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="3f8e8-143">WCF Web HTTP Programlama Modeli Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3f8e8-143">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
