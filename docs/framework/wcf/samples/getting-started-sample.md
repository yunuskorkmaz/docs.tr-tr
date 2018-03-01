---
title: "Başlarken Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2f97ad418f3d5ed197e8c35edf9e897eb393ef18
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-sample"></a><span data-ttu-id="4ec58-102">Başlarken Örneği</span><span class="sxs-lookup"><span data-stu-id="4ec58-102">Getting Started Sample</span></span>
<span data-ttu-id="4ec58-103">Başlarken örneği tipik bir hizmet ve kullanarak tipik bir istemci uygulama gösterilmiştir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4ec58-103">The Getting Started sample demonstrates how to implement a typical service and a typical client using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="4ec58-104">Bu örnek diğer tüm temel teknoloji örnekleri temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4ec58-104">This sample is the basis for all other basic technology samples.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ec58-105">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="4ec58-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4ec58-106">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="4ec58-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4ec58-107">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4ec58-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4ec58-108">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="4ec58-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4ec58-109">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="4ec58-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\GettingStarted\GettingStarted`  
  
 <span data-ttu-id="4ec58-110">Hizmet meta veri genel olarak kullanıma sunan bir hizmet sözleşmesinde gerçekleştirdiği işlemleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="4ec58-110">The service describes the operations it performs in a service contract that it exposes publicly as metadata.</span></span> <span data-ttu-id="4ec58-111">Hizmet ayrıca işlemleri uygulamak için kod içerir.</span><span class="sxs-lookup"><span data-stu-id="4ec58-111">The service also contains the code to implement the operations.</span></span>  
  
 <span data-ttu-id="4ec58-112">İstemci, hizmet sözleşmesini ve hizmete erişim için bir proxy sınıf tanımını içerir.</span><span class="sxs-lookup"><span data-stu-id="4ec58-112">The client contains a definition of the service contract and a proxy class for accessing the service.</span></span> <span data-ttu-id="4ec58-113">Kullanarak hizmeti meta veri oluşturulan proxy kodda [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="4ec58-113">The proxy code is generated from the service metadata using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 <span data-ttu-id="4ec58-114">Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)], Windows Etkinleştirme Hizmeti (WAS) barındırılan hizmetin.</span><span class="sxs-lookup"><span data-stu-id="4ec58-114">On [!INCLUDE[wv](../../../../includes/wv-md.md)], the service is hosted in the Windows Activation Service (WAS).</span></span> <span data-ttu-id="4ec58-115">Üzerinde [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ve [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Internet Information Services (IIS) ve ASP.NET tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="4ec58-115">On [!INCLUDE[wxp](../../../../includes/wxp-md.md)] and [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], it is hosted by Internet Information Services (IIS) and ASP.NET.</span></span> <span data-ttu-id="4ec58-116">IIS ya da WAS hizmetinde barındırma ilk kez eriştiğinde, otomatik olarak etkinleştirilecek hizmeti sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ec58-116">Hosting a service in IIS or WAS allows the service to be activated automatically when it is accessed for the first time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ec58-117">IIS yerine bir konsol uygulamasında hizmet barındıran bir örnek kullanmaya başlamak tercih ederseniz, bkz: [kendini barındırma](../../../../docs/framework/wcf/samples/self-host.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="4ec58-117">If you would prefer to get started with a sample that hosts the service in a console application instead of IIS, see the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>  
  
 <span data-ttu-id="4ec58-118">Hizmet ve istemci erişim ayrıntılarını dağıtım zamanında esnekliği yapılandırma dosyası ayarları belirtin.</span><span class="sxs-lookup"><span data-stu-id="4ec58-118">The service and client specify access details in configuration file settings, which provide flexibility at the time of deployment.</span></span> <span data-ttu-id="4ec58-119">Bu, yalnızca bir adresi, bağlama ve sözleşme belirten bir uç nokta tanımı içerir.</span><span class="sxs-lookup"><span data-stu-id="4ec58-119">This includes an endpoint definition that specifies an address, binding, and contract.</span></span> <span data-ttu-id="4ec58-120">Bağlama nasıl erişilecek hizmetidir için taşıma ve güvenlik ayrıntılarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4ec58-120">The binding specifies transport and security details for how the service is to be accessed.</span></span>  
  
 <span data-ttu-id="4ec58-121">Hizmet meta verilerini yayımlamak için bir çalışma zamanı davranışını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="4ec58-121">The service configures a run-time behavior to publish its metadata.</span></span>  
  
 <span data-ttu-id="4ec58-122">Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="4ec58-122">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="4ec58-123">Anlaşma tarafından tanımlanan `ICalculator` matematik işlemleri kullanıma sunan arabirim (eklemek, çıkarma, çarpma ve bölme).</span><span class="sxs-lookup"><span data-stu-id="4ec58-123">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="4ec58-124">İstemci isteklerini belirli matematik işlemi ve sonuç ile hizmet yanıtları yapar.</span><span class="sxs-lookup"><span data-stu-id="4ec58-124">The client makes requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="4ec58-125">Hizmet uygulayan bir `ICalculator` aşağıdaki kodda tanımlanan sözleşme.</span><span class="sxs-lookup"><span data-stu-id="4ec58-125">The service implements an `ICalculator` contract that is defined in the following code.</span></span>  
  
```vb  
' Define a service contract.  
    <ServiceContract(Namespace:="http://Microsoft.Samples.GettingStarted")>  
     Public Interface ICalculator  
        <OperationContract()>  
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()>  
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()>  
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()>  
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double  
    End Interface  
```  
  
```csharp  
// Define a service contract.  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="4ec58-126">Hizmet uygulaması hesaplar ve aşağıdaki örnek kodda gösterildiği gibi uygun sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="4ec58-126">The service implementation calculates and returns the appropriate result, as shown in the following example code.</span></span>  
  
```vb  
' Service class which implements the service contract.  
Public Class CalculatorService  
Implements ICalculator  
Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add  
Return n1 + n2  
End Function  
  
Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract  
Return n1 - n2  
End Function  
  
Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply  
Return n1 * n2  
End Function  
  
Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide  
Return n1 / n2  
End Function  
End Class  
```  
  
```csharp  
// Service class that implements the service contract.  
public class CalculatorService : ICalculator  
{  
    public double Add(double n1, double n2)  
    {  
        return n1 + n2;  
    }  
    public double Subtract(double n1, double n2)  
    {  
        return n1 - n2;  
    }  
    public double Multiply(double n1, double n2)  
    {  
        return n1 * n2;  
    }  
    public double Divide(double n1, double n2)  
    {  
        return n1 / n2;  
    }  
}  
```  
  
 <span data-ttu-id="4ec58-127">Hizmet (Web.config) aşağıdaki gösterildiği gibi örnek bir yapılandırma bir yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim için bir uç noktasını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="4ec58-127">The service exposes an endpoint for communicating with the service, defined using a configuration file (Web.config), as shown in the following sample configuration.</span></span>  
  
```xaml  
<services>  
    <service   
        name="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- ICalculator is exposed at the base address provided by  
         host: http://localhost/servicemodelsamples/service.svc.  -->  
       <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
       ...  
    </service>  
</services>  
```  
  
 <span data-ttu-id="4ec58-128">Hizmet IIS ya da WAS ana bilgisayarı tarafından sağlanan temel adresindeki uç noktasını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="4ec58-128">The service exposes the endpoint at the base address provided by the IIS or WAS host.</span></span> <span data-ttu-id="4ec58-129">Bağlama ile standart bir yapılandırılmış <xref:System.ServiceModel.WSHttpBinding>, hangi HTTP iletişimi ve standart Web hizmeti protokolleri adresleme ve güvenlik için sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ec58-129">The binding is configured with a standard <xref:System.ServiceModel.WSHttpBinding>, which provides HTTP communication and standard Web service protocols for addressing and security.</span></span> <span data-ttu-id="4ec58-130">Sözleşme `ICalculator` hizmeti tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4ec58-130">The contract is the `ICalculator` implemented by the service.</span></span>  
  
 <span data-ttu-id="4ec58-131">Yapılandırıldığı şekilde hizmet http://localhost/servicemodelsamples/service.svc aynı bilgisayara bir istemci tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="4ec58-131">As configured, the service can be accessed at http://localhost/servicemodelsamples/service.svc by a client on the same computer.</span></span> <span data-ttu-id="4ec58-132">Uzak computersto erişim hizmet istemciler için localhost yerine bir tam etki alanı adı belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="4ec58-132">For clients on remote computersto access the service, a fully-qualified domain name must be specified instead of localhost.</span></span>  
  
 <span data-ttu-id="4ec58-133">Framework meta verileri varsayılan olarak kullanıma sunmuyor.</span><span class="sxs-lookup"><span data-stu-id="4ec58-133">The framework does not expose metadata by default.</span></span> <span data-ttu-id="4ec58-134">Bu nedenle, hizmetin açar <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ve http://localhost/servicemodelsamples/service.svc/mex konumunda bir meta veri değişimi (MEX) uç noktasını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="4ec58-134">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> and exposes a metadata exchange (MEX) endpoint at http://localhost/servicemodelsamples/service.svc/mex.</span></span> <span data-ttu-id="4ec58-135">Aşağıdaki yapılandırma bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ec58-135">The following configuration demonstrates this.</span></span>  
  
```xaml  
<system.serviceModel>  
  <services>  
    <service   
        name="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      ...  
      <!-- the mex endpoint is explosed at  
       http://localhost/servicemodelsamples/service.svc/mex -->  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange" />  
    </service>  
  </services>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults  
   attribute to true-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
        <serviceMetadata httpGetEnabled="True"/>  
        <serviceDebug includeExceptionDetailInFaults="False" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="4ec58-136">İstemci tarafından oluşturulan bir istemci sınıfını kullanarak verilen sözleşme türünü kullanarak iletişim kurar [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="4ec58-136">The client communicates using a given contract type by using a client class that is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="4ec58-137">Bu oluşturulan istemci dosya generatedClient.cs veya generatedClient.vb yer alır.</span><span class="sxs-lookup"><span data-stu-id="4ec58-137">This generated client is contained in the file generatedClient.cs or generatedClient.vb.</span></span> <span data-ttu-id="4ec58-138">Bu yardımcı program belirli bir hizmeti için meta verilerini alır ve belirli sözleşme türünü kullanarak iletişim kurmak için istemci uygulaması tarafından kullanım için bir istemci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4ec58-138">This utility retrieves metadata for a given service and generates a client for use by the client application to communicate using a given contract type.</span></span> <span data-ttu-id="4ec58-139">Hizmeti güncelleştirilmiş meta verilerini almak için kullanılır çünkü barındırılan hizmeti istemci kodunu oluşturmak kullanılabilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ec58-139">The hosted service must be available to generate the client code, because the service is used to retrieve the updated metadata.</span></span>  
  
 <span data-ttu-id="4ec58-140">Yazılı proxy oluşturmak için istemci dizinindeki SDK komut isteminden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="4ec58-140">Run the following command from the SDK command prompt in the client directory to generate the typed proxy:</span></span>  
  
```  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
```  
  
 <span data-ttu-id="4ec58-141">Visual Basic tür SDK komut isteminden aşağıdaki istemci oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="4ec58-141">To generate client in Visual Basic type the following from the SDK command prompt:</span></span>  
  
 `Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`  
  
 <span data-ttu-id="4ec58-142">Oluşturulan istemciyi kullanarak, istemci belirli hizmet uç noktası uygun adresi yapılandırma ve bağlama tarafından erişebilir.</span><span class="sxs-lookup"><span data-stu-id="4ec58-142">By using the generated client, the client can access a given service endpoint by configuring the appropriate address and binding.</span></span> <span data-ttu-id="4ec58-143">Gibi hizmet, istemci ile iletişim kurmak istediği uç noktası belirtmek için bir yapılandırma dosyasına (App.config) kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ec58-143">Like the service, the client uses a configuration file (App.config) to specify the endpoint with which it wants to communicate.</span></span> <span data-ttu-id="4ec58-144">Aşağıdaki örnekte gösterildiği gibi hizmet uç noktası, bağlama ve sözleşme için mutlak bir adres, istemci uç nokta yapılandırması oluşur.</span><span class="sxs-lookup"><span data-stu-id="4ec58-144">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract, as shown in the following example.</span></span>  
  
```xaml  
<client>  
     <endpoint  
         address="http://localhost/servicemodelsamples/service.svc"   
         binding="wsHttpBinding"   
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />  
</client>  
```  
  
 <span data-ttu-id="4ec58-145">İstemci uygulaması istemci başlatır ve aşağıdaki örnek kodda gösterildiği gibi hizmet ile iletişim başlamak için yazılan arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ec58-145">The client implementation instantiates the client and uses the typed interface to begin communicating with the service, as shown in the following example code.</span></span>  
  
```vb  
' Create a client  
Dim client As New CalculatorClient()  
  
' Call the Add service operation.  
            Dim value1 = 100.0R  
            Dim value2 = 15.99R  
            Dim result = client.Add(value1, value2)  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)  
  
' Call the Subtract service operation.  
value1 = 145.00R  
value2 = 76.54R  
result = client.Subtract(value1, value2)  
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)  
  
' Call the Multiply service operation.  
value1 = 9.00R  
value2 = 81.25R  
result = client.Multiply(value1, value2)  
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)  
  
' Call the Divide service operation.  
value1 = 22.00R  
value2 = 7.00R  
result = client.Divide(value1, value2)  
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)  
  
'Closing the client gracefully closes the connection and cleans up resources  
```  
  
```csharp  
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
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
  
//Closing the client releases all communication resources.  
client.Close();  
```  
  
 <span data-ttu-id="4ec58-146">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4ec58-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4ec58-147">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4ec58-147">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="4ec58-148">Başlarken örneği bir hizmet ve istemci oluşturmanın standart yolu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ec58-148">The Getting Started sample shows the standard way to create a service and client.</span></span> <span data-ttu-id="4ec58-149">Diğer [temel](../../../../docs/framework/wcf/samples/basic-sample.md) belirli ürün özellikleri göstermek için bu örneği derlemek.</span><span class="sxs-lookup"><span data-stu-id="4ec58-149">The other [Basic](../../../../docs/framework/wcf/samples/basic-sample.md) build on this sample to demonstrate specific product features.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4ec58-150">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="4ec58-150">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4ec58-151">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4ec58-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4ec58-152">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4ec58-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="4ec58-153">Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4ec58-153">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ec58-154">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4ec58-154">See Also</span></span>  
 [<span data-ttu-id="4ec58-155">Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="4ec58-155">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [<span data-ttu-id="4ec58-156">Nasıl yapılır: IIS'de WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="4ec58-156">How to: Host a WCF Service in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
