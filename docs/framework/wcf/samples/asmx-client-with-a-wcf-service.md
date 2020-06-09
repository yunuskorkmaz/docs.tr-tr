---
title: WCF Hizmeti ile ASMX İstemcisi
ms.date: 03/30/2017
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
ms.openlocfilehash: fd13d4907f1be09440387a36e14ecdc4926ba7e7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594783"
---
# <a name="asmx-client-with-a-wcf-service"></a><span data-ttu-id="a1768-102">WCF Hizmeti ile ASMX İstemcisi</span><span class="sxs-lookup"><span data-stu-id="a1768-102">ASMX Client with a WCF Service</span></span>

<span data-ttu-id="a1768-103">Bu örnek, Windows Communication Foundation (WCF) kullanarak bir hizmetin nasıl oluşturulacağını ve sonra hizmetten bir ASMX istemcisi gibi WCF olmayan bir istemciden nasıl erişebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a1768-103">This sample demonstrates how to create a service using Windows Communication Foundation (WCF) and then access the service from a non-WCF client, such as an ASMX client.</span></span>

> [!NOTE]
> <span data-ttu-id="a1768-104">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="a1768-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="a1768-105">Bu örnek, Internet Information Services (IIS) tarafından barındırılan bir istemci konsol programından (. exe) ve hizmet kitaplığından (. dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="a1768-105">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="a1768-106">Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="a1768-106">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="a1768-107">Sözleşme, `ICalculator` matematik işlemlerini ( `Add` ,, `Subtract` `Multiply` ve) sunan arabirim tarafından tanımlanır `Divide` .</span><span class="sxs-lookup"><span data-stu-id="a1768-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="a1768-108">ASMX istemcisi, bir matematik işlemine zaman uyumlu istek gönderir ve hizmet sonuçla yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="a1768-108">The ASMX client makes synchronous requests to a math operation and the service replies with the result.</span></span>

<span data-ttu-id="a1768-109">Hizmet, `ICalculator` aşağıdaki kodda tanımlandığı şekilde bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="a1768-109">The service implements an `ICalculator` contract as defined in the following code.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]
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

<span data-ttu-id="a1768-110"><xref:System.Runtime.Serialization.DataContractSerializer>Ve <xref:System.Xml.Serialization.XmlSerializer> clr TÜRLERINI bir XML temsili ile eşleyin.</span><span class="sxs-lookup"><span data-stu-id="a1768-110">The <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Xml.Serialization.XmlSerializer> map CLR types to an XML representation.</span></span> <span data-ttu-id="a1768-111">, <xref:System.Runtime.Serialization.DataContractSerializer> Bazı XML temsillerini XmlSerializer 'dan farklı yorumlar.</span><span class="sxs-lookup"><span data-stu-id="a1768-111">The <xref:System.Runtime.Serialization.DataContractSerializer> interprets some XML representations differently than XmlSerializer.</span></span> <span data-ttu-id="a1768-112">WSDL. exe gibi WCF olmayan proxy oluşturucuları, XmlSerializer kullanılırken daha kullanılabilir bir arabirim oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a1768-112">Non-WCF proxy generators, such as Wsdl.exe, generate a more usable interface when the XmlSerializer is being used.</span></span> <span data-ttu-id="a1768-113">, <xref:System.ServiceModel.XmlSerializerFormatAttribute> `ICalculator` XMLSERIALIZER 'ın CLR türlerini XML 'e eşlemek için kullanıldığından emin olmak için arabirimine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a1768-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> is applied to the `ICalculator` interface, to ensure that the XmlSerializer is used for mapping CLR types to XML.</span></span> <span data-ttu-id="a1768-114">Hizmet uygulama, uygun sonucu hesaplar ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="a1768-114">The service implementation calculates and returns the appropriate result.</span></span>

<span data-ttu-id="a1768-115">Hizmet, bir yapılandırma dosyası (Web. config) kullanılarak tanımlanan, hizmetle iletişim kurmak için tek bir uç nokta sunar.</span><span class="sxs-lookup"><span data-stu-id="a1768-115">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="a1768-116">Uç nokta bir adres, bağlama ve bir anlaşmada oluşur.</span><span class="sxs-lookup"><span data-stu-id="a1768-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="a1768-117">Hizmet, uç noktayı Internet Information Services (IIS) ana bilgisayarı tarafından belirtilen temel adreste kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="a1768-117">The service exposes the endpoint at the base address provided by the Internet Information Services (IIS) host.</span></span> <span data-ttu-id="a1768-118">`binding`Özniteliği, aşağıdaki örnek yapılandırmada gösterildiği gıbı WS-ı BasicProfile 1,1 ile uyumlu olan SOAP 1,1 kullanarak http iletişimleri sağlayan BasicHttpBinding olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a1768-118">The `binding` attribute is set to basicHttpBinding that provides HTTP communications using SOAP 1.1, which is compliant with WS-I BasicProfile 1.1 as shown in the following sample configuration.</span></span>

```xml
<services>
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc.  -->
    <endpoint address=""
              binding="basicHttpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </service>
</services>
```

<span data-ttu-id="a1768-119">ASMX istemcisi, Web Hizmetleri Açıklama Dili (WSDL) yardımcı programı (wsdl. exe) tarafından oluşturulan türü belirlenmiş bir ara sunucu kullanarak WCF hizmeti ile iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="a1768-119">The ASMX client communicates with the WCF service using a typed proxy that is generated by the Web Services Description Language (WSDL) utility (Wsdl.exe).</span></span> <span data-ttu-id="a1768-120">Yazılan ara sunucu generatedClient.cs dosyasında bulunur.</span><span class="sxs-lookup"><span data-stu-id="a1768-120">The typed proxy is contained in the file generatedClient.cs.</span></span> <span data-ttu-id="a1768-121">WSDL yardımcı programı, belirtilen hizmet için meta verileri alır ve bir istemci tarafından iletişim kurmak için kullanılan bir ara sunucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a1768-121">The WSDL utility retrieves metadata for the specified service and generates a typed proxy for use by a client to communicate.</span></span> <span data-ttu-id="a1768-122">Varsayılan olarak, çerçeve herhangi bir meta veri sunmaz.</span><span class="sxs-lookup"><span data-stu-id="a1768-122">By default, the framework does not expose any metadata.</span></span> <span data-ttu-id="a1768-123">Proxy 'yi oluşturmak için gereken meta verileri göstermek için, [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) `httpGetEnabled` `True` Aşağıdaki yapılandırmada gösterildiği gibi bir özniteliğini eklemeli ve öğesini olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1768-123">To expose the metadata required to generate the proxy, you must add a [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) and set its `httpGetEnabled` attribute to `True` as shown in the following configuration.</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <!-- Setting httpGetEnabled to True on the serviceMetadata
           behavior exposes the service's wsdl at <base address>?wsdl :
           http://localhost/servicemodelsamples/service.svc?wsdl -->
      <serviceMetadata httpGetEnabled="True"/>
      <serviceDebug includeExceptionDetailInFaults="False" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="a1768-124">Yazılan proxy 'yi oluşturmak için istemci dizinindeki bir komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a1768-124">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>

```console
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl
```

<span data-ttu-id="a1768-125">Oluşturulan tür ara sunucusunu kullanarak istemci, uygun adresi yapılandırarak belirli bir hizmet uç noktasına erişebilir.</span><span class="sxs-lookup"><span data-stu-id="a1768-125">By using the generated typed proxy, the client can access a given service endpoint by configuring the appropriate address.</span></span> <span data-ttu-id="a1768-126">İstemci, iletişim kuracak uç noktayı belirtmek için bir yapılandırma dosyası (App. config) kullanır.</span><span class="sxs-lookup"><span data-stu-id="a1768-126">The client uses a configuration file (App.config) to specify the endpoint to communicate with.</span></span>

```xml
<appSettings>
  <add key="CalculatorServiceAddress"
       value="http://localhost/ServiceModelSamples/service.svc"/>
</appSettings>
```

<span data-ttu-id="a1768-127">İstemci uygulama, hizmetle iletişim kurmaya başlamak için türü belirlenmiş proxy 'nin bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a1768-127">The client implementation constructs an instance of the typed proxy to begin communicating with the service.</span></span>

```csharp
// Create a client to the CalculatorService.
using (CalculatorService client = new CalculatorService())
{
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

}

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

<span data-ttu-id="a1768-128">Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a1768-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a1768-129">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a1768-129">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a1768-130">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a1768-130">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="a1768-131">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a1768-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="a1768-132">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a1768-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="a1768-133">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="a1768-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a1768-134">Karmaşık veri türlerini geçirme ve döndürme hakkında daha fazla bilgi için bkz. [Windows Forms Istemcisinde veri bağlama](data-binding-in-a-windows-forms-client.md), bir [Windows Presentation Foundation istemcisinde veri bağlama](data-binding-in-a-wpf-client.md)ve [bir ASP.net istemcisinde veri bağlama](data-binding-in-an-aspnet-client.md)</span><span class="sxs-lookup"><span data-stu-id="a1768-134">For more information about passing and returning complex data types see: [Data Binding in a Windows Forms Client](data-binding-in-a-windows-forms-client.md), [Data Binding in a Windows Presentation Foundation Client](data-binding-in-a-wpf-client.md), and [Data Binding in an ASP.NET Client](data-binding-in-an-aspnet-client.md)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a1768-135">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a1768-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a1768-136">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a1768-136">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="a1768-137">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a1768-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a1768-138">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a1768-138">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`
