---
title: Başlarken Örneği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
ms.openlocfilehash: b249137117f970a14284beb6439e501a3004eee1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298870"
---
# <a name="getting-started-sample"></a><span data-ttu-id="23513-102">Başlarken Örneği</span><span class="sxs-lookup"><span data-stu-id="23513-102">Getting Started Sample</span></span>

<span data-ttu-id="23513-103">Kullanmaya başlama örneği, tipik bir hizmet ve Windows Communication Foundation (WCF) kullanarak tipik bir istemci uygulama gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="23513-103">The Getting Started sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="23513-104">Bu örnek diğer tüm temel teknoloji örnekleri temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="23513-104">This sample is the basis for all other basic technology samples.</span></span>

> [!NOTE]
> <span data-ttu-id="23513-105">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="23513-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="23513-106">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="23513-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="23513-107">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="23513-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="23513-108">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="23513-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="23513-109">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="23513-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\GettingStarted\GettingStarted`

<span data-ttu-id="23513-110">Hizmet olarak meta veriler genel olarak kullanıma sunduğu bir hizmet sözleşmesinde gerçekleştirdiği işlemler açıklanır.</span><span class="sxs-lookup"><span data-stu-id="23513-110">The service describes the operations it performs in a service contract that it exposes publicly as metadata.</span></span> <span data-ttu-id="23513-111">Hizmet işlemleri uygulayan bir kod da içerir.</span><span class="sxs-lookup"><span data-stu-id="23513-111">The service also contains the code to implement the operations.</span></span>

<span data-ttu-id="23513-112">İstemci, hizmet sözleşmesi ve hizmete erişmek için bir proxy sınıfı bir tanım içeriyor.</span><span class="sxs-lookup"><span data-stu-id="23513-112">The client contains a definition of the service contract and a proxy class for accessing the service.</span></span> <span data-ttu-id="23513-113">Proxy kodu kullanarak hizmet meta verileri oluşturulan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="23513-113">The proxy code is generated from the service metadata using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

<span data-ttu-id="23513-114">Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)], hizmet Windows Etkinleştirme Hizmeti (WAS) barındırılır.</span><span class="sxs-lookup"><span data-stu-id="23513-114">On [!INCLUDE[wv](../../../../includes/wv-md.md)], the service is hosted in the Windows Activation Service (WAS).</span></span> <span data-ttu-id="23513-115">Üzerinde [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ve [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Internet Information Services (IIS) ve ASP.NET tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="23513-115">On [!INCLUDE[wxp](../../../../includes/wxp-md.md)] and [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], it is hosted by Internet Information Services (IIS) and ASP.NET.</span></span> <span data-ttu-id="23513-116">Bir IIS ya da WAS hizmetinde barındırma ilk kez eriştiğinde, otomatik olarak etkinleştirilecek hizmeti sağlar.</span><span class="sxs-lookup"><span data-stu-id="23513-116">Hosting a service in IIS or WAS allows the service to be activated automatically when it is accessed for the first time.</span></span>

> [!NOTE]
> <span data-ttu-id="23513-117">IIS yerine bir konsol uygulamasındaki hizmet barındıran bir örnek ile kullanmaya başlamak tercih ediyorsanız, bkz: [barındırma](../../../../docs/framework/wcf/samples/self-host.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="23513-117">If you would prefer to get started with a sample that hosts the service in a console application instead of IIS, see the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>

<span data-ttu-id="23513-118">İstemci ve hizmet dağıtım sırasında esneklik yapılandırma dosyası ayarlarının erişim ayrıntılarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="23513-118">The service and client specify access details in configuration file settings, which provide flexibility at the time of deployment.</span></span> <span data-ttu-id="23513-119">Bu, bir adresi, bağlama ve sözleşme belirten bir uç nokta tanımı içerir.</span><span class="sxs-lookup"><span data-stu-id="23513-119">This includes an endpoint definition that specifies an address, binding, and contract.</span></span> <span data-ttu-id="23513-120">Bağlama için nasıl erişilmesini hizmetidir aktarım veya güvenlik ayrıntılarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="23513-120">The binding specifies transport and security details for how the service is to be accessed.</span></span>

<span data-ttu-id="23513-121">Hizmet meta verilerini yayımlamak için bir çalışma zamanı davranışını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="23513-121">The service configures a run-time behavior to publish its metadata.</span></span>

<span data-ttu-id="23513-122">Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="23513-122">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="23513-123">Anlaşma tarafından tanımlanan `ICalculator` matematik işlemlerinden sunan arabirimi (ekleme, çıkarma, çarpma ve bölme).</span><span class="sxs-lookup"><span data-stu-id="23513-123">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="23513-124">İstemci isteklerini belirli matematik işlemi ve sonuç ile hizmet verilen yanıtları yapar.</span><span class="sxs-lookup"><span data-stu-id="23513-124">The client makes requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="23513-125">Hizmet uygulayan bir `ICalculator` aşağıdaki kod içinde tanımlanan sözleşme.</span><span class="sxs-lookup"><span data-stu-id="23513-125">The service implements an `ICalculator` contract that is defined in the following code.</span></span>

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

<span data-ttu-id="23513-126">Hizmet uygulaması, hesaplar ve aşağıdaki örnekte gösterildiği gibi uygun bir sonuç döndürür.</span><span class="sxs-lookup"><span data-stu-id="23513-126">The service implementation calculates and returns the appropriate result, as shown in the following example code.</span></span>

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

<span data-ttu-id="23513-127">Hizmet, örnek yapılandırma (Web.config), aşağıda gösterildiği gibi bir yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim kurmak için bir uç noktasını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="23513-127">The service exposes an endpoint for communicating with the service, defined using a configuration file (Web.config), as shown in the following sample configuration.</span></span>

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

<span data-ttu-id="23513-128">Hizmet, IIS veya WAS ana bilgisayar tarafından sağlanan taban adresinde uç noktasını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="23513-128">The service exposes the endpoint at the base address provided by the IIS or WAS host.</span></span> <span data-ttu-id="23513-129">Bir standart yapılandırılmış bağlama <xref:System.ServiceModel.WSHttpBinding>, sağlayan HTTP iletişimi ve standart Web hizmeti protokolleri adresleme ve güvenlik için.</span><span class="sxs-lookup"><span data-stu-id="23513-129">The binding is configured with a standard <xref:System.ServiceModel.WSHttpBinding>, which provides HTTP communication and standard Web service protocols for addressing and security.</span></span> <span data-ttu-id="23513-130">Sözleşme `ICalculator` hizmeti tarafından uygulanan.</span><span class="sxs-lookup"><span data-stu-id="23513-130">The contract is the `ICalculator` implemented by the service.</span></span>

<span data-ttu-id="23513-131">Adresinden yapılandırıldığı gibi hizmet erişilebilen `http://localhost/servicemodelsamples/service.svc` aynı bilgisayarda bir istemci tarafından.</span><span class="sxs-lookup"><span data-stu-id="23513-131">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="23513-132">Hizmete erişmek istemciler için uzak bilgisayarlarda, localhost yerine bir tam etki alanı adı belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="23513-132">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span>

<span data-ttu-id="23513-133">Framework meta verileri varsayılan olarak kullanıma sunmuyor.</span><span class="sxs-lookup"><span data-stu-id="23513-133">The framework does not expose metadata by default.</span></span> <span data-ttu-id="23513-134">Bu nedenle, hizmet açar <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ve bir meta veri değişimi (MEX) uç noktada ortaya çıkaran `http://localhost/servicemodelsamples/service.svc/mex`.</span><span class="sxs-lookup"><span data-stu-id="23513-134">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> and exposes a metadata exchange (MEX) endpoint at `http://localhost/servicemodelsamples/service.svc/mex`.</span></span> <span data-ttu-id="23513-135">Aşağıdaki yapılandırmayı bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="23513-135">The following configuration demonstrates this.</span></span>

```xaml
<system.serviceModel>
  <services>
    <service
        name="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
      ...
      <!-- the mex endpoint is exposed at
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

<span data-ttu-id="23513-136">İstemci tarafından oluşturulan istemci sınıfını kullanarak belirtilen anlaşma türü kullanarak iletişim kurar [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="23513-136">The client communicates using a given contract type by using a client class that is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="23513-137">Bu oluşturulan istemci dosyası generatedClient.cs veya generatedClient.vb yer alır.</span><span class="sxs-lookup"><span data-stu-id="23513-137">This generated client is contained in the file generatedClient.cs or generatedClient.vb.</span></span> <span data-ttu-id="23513-138">Bu yardımcı programı, verili bir hizmet için meta verileri alır ve kullanmak için bir istemci istemci uygulaması tarafından verilen anlaşma türü kullanarak iletişim kurmaya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="23513-138">This utility retrieves metadata for a given service and generates a client for use by the client application to communicate using a given contract type.</span></span> <span data-ttu-id="23513-139">Barındırılan hizmet, hizmet güncelleştirilmiş meta verilerini almak için kullanıldığından istemci kodu oluşturmak kullanılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="23513-139">The hosted service must be available to generate the client code, because the service is used to retrieve the updated metadata.</span></span>

 <span data-ttu-id="23513-140">Türü belirtilmiş bir proxy oluşturmak için istemci dizinindeki SDK komut isteminden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="23513-140">Run the following command from the SDK command prompt in the client directory to generate the typed proxy:</span></span>

```
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
```

<span data-ttu-id="23513-141">Visual Basic türü SDK komut isteminden aşağıdaki istemci oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="23513-141">To generate client in Visual Basic type the following from the SDK command prompt:</span></span>

`Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`

<span data-ttu-id="23513-142">Oluşturulan istemciyi kullanarak istemci belirli bir hizmet uç noktası uygun adresi yapılandırma ve bağlama tarafından erişebilir.</span><span class="sxs-lookup"><span data-stu-id="23513-142">By using the generated client, the client can access a given service endpoint by configuring the appropriate address and binding.</span></span> <span data-ttu-id="23513-143">Hizmet gibi istemci uç noktası ile iletişim kurmak istediği belirtmek için bir yapılandırma dosyası (App.config) kullanır.</span><span class="sxs-lookup"><span data-stu-id="23513-143">Like the service, the client uses a configuration file (App.config) to specify the endpoint with which it wants to communicate.</span></span> <span data-ttu-id="23513-144">Aşağıdaki örnekte gösterildiği gibi bir mutlak bir adres için hizmet uç noktası, bağlama ve Sözleşme, istemci uç nokta yapılandırması oluşur.</span><span class="sxs-lookup"><span data-stu-id="23513-144">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract, as shown in the following example.</span></span>

```xaml
<client>
     <endpoint
         address="http://localhost/servicemodelsamples/service.svc"
         binding="wsHttpBinding"
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />
</client>
```

<span data-ttu-id="23513-145">İstemci uygulaması, istemci başlatır ve aşağıdaki örnekte gösterildiği gibi hizmet ile iletişim başlatmak için belirlenmiş arabirimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="23513-145">The client implementation instantiates the client and uses the typed interface to begin communicating with the service, as shown in the following example code.</span></span>

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

<span data-ttu-id="23513-146">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="23513-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="23513-147">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="23513-147">Press ENTER in the client window to shut down the client.</span></span>

```
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

<span data-ttu-id="23513-148">Kullanmaya başlama örneği, hizmet ve istemci oluşturmak için standart bir yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="23513-148">The Getting Started sample shows the standard way to create a service and client.</span></span> <span data-ttu-id="23513-149">Diğer [temel](../../../../docs/framework/wcf/samples/basic-sample.md) belirli bir ürün özellikleri göstermek için bu örneği derlemek.</span><span class="sxs-lookup"><span data-stu-id="23513-149">The other [Basic](../../../../docs/framework/wcf/samples/basic-sample.md) build on this sample to demonstrate specific product features.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="23513-150">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="23513-150">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="23513-151">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="23513-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="23513-152">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="23513-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="23513-153">Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="23513-153">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="23513-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23513-154">See also</span></span>

- [<span data-ttu-id="23513-155">Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="23513-155">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="23513-156">Nasıl yapılır: IIS'de WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="23513-156">How to: Host a WCF Service in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
