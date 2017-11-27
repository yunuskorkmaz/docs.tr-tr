---
title: "ASMX Web Hizmetleri ile Birlikte Çalışma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7c11f0a-9e68-4f03-a6b1-39cf478d1a89
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 635502ea186e188bf9906d45e7753eba72fbd5d1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="interoperating-with-asmx-web-services"></a><span data-ttu-id="397f8-102">ASMX Web Hizmetleri ile Birlikte Çalışma</span><span class="sxs-lookup"><span data-stu-id="397f8-102">Interoperating with ASMX Web Services</span></span>
<span data-ttu-id="397f8-103">Bu örnek nasıl tümleştirileceği gösteren bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] var olan bir ASMX Web hizmeti ile istemci uygulaması.</span><span class="sxs-lookup"><span data-stu-id="397f8-103">This sample demonstrates how to integrate a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client application with an existing ASMX Web service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="397f8-104">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="397f8-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="397f8-105">Bu örnek, bir istemci konsol program (.exe) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı (.dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="397f8-105">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="397f8-106">İstek-yanıt iletişim deseni tanımlayan bir sözleşme uygulayan bir ASMX Web hizmeti hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="397f8-106">The service is an ASMX Web Service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="397f8-107">Hizmet matematik işlemini kullanıma sunar (`Add`, `Subtract`, `Multiply`, ve `Divide`).</span><span class="sxs-lookup"><span data-stu-id="397f8-107">The service exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="397f8-108">İstemci eş zamanlı istekleri matematik işlemi ve sonuç ile hizmet yanıtları yapar.</span><span class="sxs-lookup"><span data-stu-id="397f8-108">The client makes synchronous requests to a math operation and the service replies with the result.</span></span> <span data-ttu-id="397f8-109">İstemci etkinliği konsol penceresinde görünür olur.</span><span class="sxs-lookup"><span data-stu-id="397f8-109">Client activity is visible in the console window.</span></span>  
  
 <span data-ttu-id="397f8-110">Aşağıdaki örnek kodda gösterildiği ASMX Web hizmeti uygulama hesaplar ve uygun sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="397f8-110">The ASMX Web service implementation shown in the following sample code calculates and returns the appropriate result.</span></span>  
  
```  
[WebService(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class CalculatorService : System.Web.Services.WebService  
    {  
        [WebMethod]  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
        [WebMethod]  
        public double Subtract(double n1, double n2)  
        {  
            return n1 - n2;  
        }  
        [WebMethod]  
        public double Multiply(double n1, double n2)  
        {  
            return n1 * n2;  
        }  
        [WebMethod]  
        public double Divide(double n1, double n2)  
        {  
            return n1 / n2;  
        }  
    }  
```  
  
 <span data-ttu-id="397f8-111">Yapılandırıldığı şekilde hizmet http://localhost/servicemodelsamples/service.asmx aynı makine üzerindeki bir istemci tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="397f8-111">As configured, the service can be accessed at http://localhost/servicemodelsamples/service.asmx by a client on the same machine.</span></span> <span data-ttu-id="397f8-112">Hizmete erişmek istemciler için uzak makinede, localhost yerine bir tam etki alanı adı belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="397f8-112">For clients on remote machines to access the service, a qualified domain name must be specified instead of localhost.</span></span>  
  
 <span data-ttu-id="397f8-113">Tarafından oluşturulan bir istemci aracılığıyla iletişim yapılır [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="397f8-113">Communication is done through a client generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="397f8-114">İstemci dosyası generatedClient.cs içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="397f8-114">The client is contained in the file generatedClient.cs.</span></span> <span data-ttu-id="397f8-115">Güncelleştirilmiş meta verilerini almak için kullanıldığından ASMX hizmeti proxy kodu oluşturmak kullanılabilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="397f8-115">The ASMX service must be available to generate the proxy code, because it is used to retrieve the updated metadata.</span></span> <span data-ttu-id="397f8-116">Yazılı proxy oluşturmak için istemci dizininde bir komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="397f8-116">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedClient.cs  
```  
  
 <span data-ttu-id="397f8-117">Oluşturulan istemciyi kullanarak hizmet uç noktası uygun adresi yapılandırma ve bağlama tarafından erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="397f8-117">By using the generated client, you can access a service endpoint by configuring the appropriate address and binding.</span></span> <span data-ttu-id="397f8-118">Gibi hizmet, istemci ile iletişim kurmak için uç nokta belirtmek için bir yapılandırma dosyasına (App.config) kullanır.</span><span class="sxs-lookup"><span data-stu-id="397f8-118">Like the service, the client uses a configuration file (App.config) to specify the endpoint to communicate with.</span></span> <span data-ttu-id="397f8-119">Aşağıdaki örnek yapılandırmada gösterildiği gibi hizmet uç noktası, bağlama ve sözleşme için mutlak bir adres, istemci uç nokta yapılandırması oluşur.</span><span class="sxs-lookup"><span data-stu-id="397f8-119">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract, as shown in the following sample configuration.</span></span>  
  
```xml  
<client>  
   <endpoint   
      address="http://localhost/ServiceModelSamples/service.asmx"   
      binding="basicHttpBinding"   
      contract="Microsoft.ServiceModel.Samples.CalculatorServiceSoap" />  
</client>  
```  
  
 <span data-ttu-id="397f8-120">İstemci uygulaması oluşturulan istemci örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="397f8-120">The client implementation constructs an instance of the generated client.</span></span> <span data-ttu-id="397f8-121">Oluşturulan istemci ardından hizmetiyle iletişim kurmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="397f8-121">The generated client can then be used to communicate with the service.</span></span>  
  
```  
// Create a client.  
CalculatorServiceSoapClient client = new CalculatorServiceSoapClient();  
  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
// Call the Subtract service operation.  
value1 = 145.00D;  
value2 = 76.54D;  
result = client.Subtract(value1, value2);  
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
// Call the Multiply service operation.  
value1 = 9.00D;  
value2 = 81.25D;  
result = client.Multiply(value1, value2);  
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
// Call the Divide service operation.  
value1 = 22.00D;  
value2 = 7.00D;  
result = client.Divide(value1, value2);  
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="397f8-122">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="397f8-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="397f8-123">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="397f8-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="397f8-124">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="397f8-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="397f8-125">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="397f8-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="397f8-126">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="397f8-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="397f8-127">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="397f8-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="397f8-128">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="397f8-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="397f8-129">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="397f8-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="397f8-130">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="397f8-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="397f8-131">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="397f8-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\Interop\ASMX`  
  
## <a name="see-also"></a><span data-ttu-id="397f8-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="397f8-132">See Also</span></span>
