---
title: Başlarken Örneği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
ms.openlocfilehash: fc4a7e9acb15f77140732638b2982dd4a9dae9ce
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575192"
---
# <a name="getting-started-sample"></a><span data-ttu-id="844fd-102">Başlarken Örneği</span><span class="sxs-lookup"><span data-stu-id="844fd-102">Getting Started Sample</span></span>

<span data-ttu-id="844fd-103">Başlarken örneği, Windows Communication Foundation (WCF) kullanılarak tipik bir hizmetin ve tipik bir istemcinin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="844fd-103">The Getting Started sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="844fd-104">Bu örnek, diğer tüm temel teknoloji örnekleri için temeldir.</span><span class="sxs-lookup"><span data-stu-id="844fd-104">This sample is the basis for all other basic technology samples.</span></span>

> [!NOTE]
> <span data-ttu-id="844fd-105">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="844fd-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="844fd-106">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="844fd-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="844fd-107">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="844fd-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="844fd-108">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="844fd-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="844fd-109">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="844fd-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\GettingStarted\GettingStarted`

<span data-ttu-id="844fd-110">Hizmet, bir hizmet sözleşmesinde gerçekleştirdiği işlemleri, genel olarak meta veri olarak açığa çıkardığı şekilde açıklar.</span><span class="sxs-lookup"><span data-stu-id="844fd-110">The service describes the operations it performs in a service contract that it exposes publicly as metadata.</span></span> <span data-ttu-id="844fd-111">Hizmet ayrıca işlemleri uygulamak için kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="844fd-111">The service also contains the code to implement the operations.</span></span>

<span data-ttu-id="844fd-112">İstemci, hizmet sözleşmesinin bir tanımını ve hizmete erişmek için bir proxy sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="844fd-112">The client contains a definition of the service contract and a proxy class for accessing the service.</span></span> <span data-ttu-id="844fd-113">Proxy kodu, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)kullanılarak hizmet meta verilerinden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="844fd-113">The proxy code is generated from the service metadata using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

<span data-ttu-id="844fd-114">Windows Vista 'da, hizmet Windows etkinleştirme hizmeti 'nde (WAS) barındırılır.</span><span class="sxs-lookup"><span data-stu-id="844fd-114">On Windows Vista, the service is hosted in the Windows Activation Service (WAS).</span></span> <span data-ttu-id="844fd-115">Windows XP ve Windows Server 2003 ' de, Internet Information Services (IIS) ve ASP.NET tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="844fd-115">On Windows XP and Windows Server 2003, it is hosted by Internet Information Services (IIS) and ASP.NET.</span></span> <span data-ttu-id="844fd-116">Bir hizmetin IIS 'de barındırılması, ilk kez erişildiğinde hizmetin otomatik olarak etkinleştirilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="844fd-116">Hosting a service in IIS or WAS allows the service to be activated automatically when it is accessed for the first time.</span></span>

> [!NOTE]
> <span data-ttu-id="844fd-117">Hizmeti IIS yerine bir konsol uygulamasında barındıran bir örnekle çalışmaya başlamak isterseniz, [self-Host](self-host.md) örneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="844fd-117">If you would prefer to get started with a sample that hosts the service in a console application instead of IIS, see the [Self-Host](self-host.md) sample.</span></span>

<span data-ttu-id="844fd-118">Hizmet ve istemci, dağıtım sırasında esneklik sağlayan yapılandırma dosyası ayarları 'nda erişim ayrıntılarını belirler.</span><span class="sxs-lookup"><span data-stu-id="844fd-118">The service and client specify access details in configuration file settings, which provide flexibility at the time of deployment.</span></span> <span data-ttu-id="844fd-119">Bu, bir adresi, bağlamayı ve sözleşmeyi belirten bir uç nokta tanımı içerir.</span><span class="sxs-lookup"><span data-stu-id="844fd-119">This includes an endpoint definition that specifies an address, binding, and contract.</span></span> <span data-ttu-id="844fd-120">Bağlama, hizmetin nasıl erişileceğini gösteren taşıma ve güvenlik ayrıntılarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="844fd-120">The binding specifies transport and security details for how the service is to be accessed.</span></span>

<span data-ttu-id="844fd-121">Hizmet, meta verilerini yayımlamak için bir çalışma zamanı davranışı yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="844fd-121">The service configures a run-time behavior to publish its metadata.</span></span>

<span data-ttu-id="844fd-122">Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="844fd-122">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="844fd-123">Sözleşme, `ICalculator` matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) sunan arabirim tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="844fd-123">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="844fd-124">İstemci belirli bir matematik işlemine istek yapar ve hizmet sonuçla yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="844fd-124">The client makes requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="844fd-125">Hizmet, `ICalculator` aşağıdaki kodda tanımlı bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="844fd-125">The service implements an `ICalculator` contract that is defined in the following code.</span></span>

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

<span data-ttu-id="844fd-126">Hizmet uygulamasının aşağıdaki örnek kodda gösterildiği gibi, uygun sonucu hesaplar ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="844fd-126">The service implementation calculates and returns the appropriate result, as shown in the following example code.</span></span>

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

<span data-ttu-id="844fd-127">Hizmet, aşağıdaki örnek yapılandırmada gösterildiği gibi, bir yapılandırma dosyası (Web. config) kullanılarak tanımlanan hizmetle iletişim kurmak için bir uç nokta sunar.</span><span class="sxs-lookup"><span data-stu-id="844fd-127">The service exposes an endpoint for communicating with the service, defined using a configuration file (Web.config), as shown in the following sample configuration.</span></span>

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

<span data-ttu-id="844fd-128">Hizmet, uç noktayı IIS veya WAS ana bilgisayar tarafından belirtilen temel adreste kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="844fd-128">The service exposes the endpoint at the base address provided by the IIS or WAS host.</span></span> <span data-ttu-id="844fd-129">Bağlama, <xref:System.ServiceModel.WSHttpBinding> adresleme ve güvenlik IÇIN http iletişimi ve standart Web hizmeti protokolleri sağlayan bir standart ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="844fd-129">The binding is configured with a standard <xref:System.ServiceModel.WSHttpBinding>, which provides HTTP communication and standard Web service protocols for addressing and security.</span></span> <span data-ttu-id="844fd-130">Sözleşme, `ICalculator` hizmet tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="844fd-130">The contract is the `ICalculator` implemented by the service.</span></span>

<span data-ttu-id="844fd-131">Yapılandırıldığı gibi, hizmete `http://localhost/servicemodelsamples/service.svc` aynı bilgisayardaki bir istemci tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="844fd-131">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="844fd-132">Uzak bilgisayarlardaki istemcilerin hizmete erişmesi için localhost yerine tam etki alanı adı belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="844fd-132">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span>

<span data-ttu-id="844fd-133">Çerçeve varsayılan olarak meta verileri kullanıma sunmaz.</span><span class="sxs-lookup"><span data-stu-id="844fd-133">The framework does not expose metadata by default.</span></span> <span data-ttu-id="844fd-134">Bu nedenle hizmet, ve ' ı açar <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ve bir meta veri değişimi (MEX) uç noktasını kullanıma sunar `http://localhost/servicemodelsamples/service.svc/mex` .</span><span class="sxs-lookup"><span data-stu-id="844fd-134">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> and exposes a metadata exchange (MEX) endpoint at `http://localhost/servicemodelsamples/service.svc/mex`.</span></span> <span data-ttu-id="844fd-135">Aşağıdaki yapılandırma bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="844fd-135">The following configuration demonstrates this.</span></span>

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

<span data-ttu-id="844fd-136">İstemci, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)tarafından oluşturulan bir istemci sınıfını kullanarak belirli bir sözleşme türünü kullanarak iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="844fd-136">The client communicates using a given contract type by using a client class that is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="844fd-137">Bu oluşturulan istemci, generatedClient.cs veya generatedClient. vb dosyasında bulunur.</span><span class="sxs-lookup"><span data-stu-id="844fd-137">This generated client is contained in the file generatedClient.cs or generatedClient.vb.</span></span> <span data-ttu-id="844fd-138">Bu yardımcı program belirli bir hizmet için meta verileri alır ve belirli bir sözleşme türünü kullanarak iletişim kurmak için istemci uygulaması tarafından kullanılmak üzere bir istemci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="844fd-138">This utility retrieves metadata for a given service and generates a client for use by the client application to communicate using a given contract type.</span></span> <span data-ttu-id="844fd-139">Hizmet güncelleştirilmiş meta verileri almak için kullanıldığından, istemci kodunu oluşturmak için barındırılan hizmetin kullanılabilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="844fd-139">The hosted service must be available to generate the client code, because the service is used to retrieve the updated metadata.</span></span>

 <span data-ttu-id="844fd-140">Türü belirtilmiş proxy 'yi oluşturmak için istemci dizininde SDK komut isteminden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="844fd-140">Run the following command from the SDK command prompt in the client directory to generate the typed proxy:</span></span>

```console
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
```

<span data-ttu-id="844fd-141">Visual Basic ' de istemci oluşturmak için SDK komut isteminden aşağıdakini yazın:</span><span class="sxs-lookup"><span data-stu-id="844fd-141">To generate client in Visual Basic type the following from the SDK command prompt:</span></span>

`Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`

<span data-ttu-id="844fd-142">İstemci, oluşturulan istemciyi kullanarak, uygun adresi ve bağlamayı yapılandırarak belirli bir hizmet uç noktasına erişebilir.</span><span class="sxs-lookup"><span data-stu-id="844fd-142">By using the generated client, the client can access a given service endpoint by configuring the appropriate address and binding.</span></span> <span data-ttu-id="844fd-143">Hizmet gibi istemci, iletişim kurmak istediği uç noktayı belirtmek için bir yapılandırma dosyası (App. config) kullanır.</span><span class="sxs-lookup"><span data-stu-id="844fd-143">Like the service, the client uses a configuration file (App.config) to specify the endpoint with which it wants to communicate.</span></span> <span data-ttu-id="844fd-144">İstemci uç noktası yapılandırması, aşağıdaki örnekte gösterildiği gibi hizmet uç noktası, bağlama ve sözleşme için mutlak bir adresten oluşur.</span><span class="sxs-lookup"><span data-stu-id="844fd-144">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract, as shown in the following example.</span></span>

```xaml
<client>
     <endpoint
         address="http://localhost/servicemodelsamples/service.svc"
         binding="wsHttpBinding"
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />
</client>
```

<span data-ttu-id="844fd-145">İstemci uygulama, istemciyi başlatır ve aşağıdaki örnek kodda gösterildiği gibi hizmet ile iletişim kurmaya başlamak için türü belirlenmiş arabirimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="844fd-145">The client implementation instantiates the client and uses the typed interface to begin communicating with the service, as shown in the following example code.</span></span>

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

<span data-ttu-id="844fd-146">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="844fd-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="844fd-147">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="844fd-147">Press ENTER in the client window to shut down the client.</span></span>

```output
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

<span data-ttu-id="844fd-148">Başlarken örneği, bir hizmet ve istemci oluşturmanın standart yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="844fd-148">The Getting Started sample shows the standard way to create a service and client.</span></span> <span data-ttu-id="844fd-149">Belirli ürün özelliklerini göstermek için bu örnekteki diğer [temel](basic-sample.md) yapı.</span><span class="sxs-lookup"><span data-stu-id="844fd-149">The other [Basic](basic-sample.md) build on this sample to demonstrate specific product features.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="844fd-150">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="844fd-150">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="844fd-151">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="844fd-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="844fd-152">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="844fd-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="844fd-153">Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="844fd-153">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="844fd-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="844fd-154">See also</span></span>

- [<span data-ttu-id="844fd-155">Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="844fd-155">How to: Host a WCF Service in a Managed Application</span></span>](../how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="844fd-156">Nasıl yapılır: IIS'de WCF Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="844fd-156">How to: Host a WCF Service in IIS</span></span>](../feature-details/how-to-host-a-wcf-service-in-iis.md)
