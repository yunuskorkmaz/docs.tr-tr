---
title: WCF Hizmeti ile ASMX İstemcisi
ms.date: 03/30/2017
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
ms.openlocfilehash: 3465954cc937e1611634c8cd13a9264173e71817
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507205"
---
# <a name="asmx-client-with-a-wcf-service"></a><span data-ttu-id="90514-102">WCF Hizmeti ile ASMX İstemcisi</span><span class="sxs-lookup"><span data-stu-id="90514-102">ASMX Client with a WCF Service</span></span>
<span data-ttu-id="90514-103">Bu örnek, Windows Communication Foundation (WCF) kullanan bir hizmet oluşturmak ve ardından ASMX istemcisi gibi bir WCF olmayan istemciden hizmete erişmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="90514-103">This sample demonstrates how to create a service using Windows Communication Foundation (WCF) and then access the service from a non-WCF client, such as an ASMX client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90514-104">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="90514-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="90514-105">Bu örnek, bir istemci konsol program (.exe) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı (.dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="90514-105">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="90514-106">Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="90514-106">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="90514-107">Anlaşma tarafından tanımlanan `ICalculator` matematik işlemlerinden sunan arabirimi (`Add`, `Subtract`, `Multiply`, ve `Divide`).</span><span class="sxs-lookup"><span data-stu-id="90514-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="90514-108">ASMX istemcisi bir matematik işlemi ve hizmet yanıt sonucu zaman uyumlu istekleri yapar.</span><span class="sxs-lookup"><span data-stu-id="90514-108">The ASMX client makes synchronous requests to a math operation and the service replies with the result.</span></span>  
  
 <span data-ttu-id="90514-109">Hizmet uygulayan bir `ICalculator` aşağıdaki kodda tanımlanan sözleşme.</span><span class="sxs-lookup"><span data-stu-id="90514-109">The service implements an `ICalculator` contract as defined in the following code.</span></span>  
  
```  
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
  
 <span data-ttu-id="90514-110"><xref:System.Runtime.Serialization.DataContractSerializer> Ve <xref:System.Xml.Serialization.XmlSerializer> CLR Türleri eşleştirmek için bir XML gösterimi.</span><span class="sxs-lookup"><span data-stu-id="90514-110">The <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Xml.Serialization.XmlSerializer> map CLR types to an XML representation.</span></span> <span data-ttu-id="90514-111"><xref:System.Runtime.Serialization.DataContractSerializer> Bazı XML gösterimleri XmlSerializer tarafından farklı olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="90514-111">The <xref:System.Runtime.Serialization.DataContractSerializer> interprets some XML representations differently than XmlSerializer.</span></span> <span data-ttu-id="90514-112">XmlSerializer kullanıldığında gibi Wsdl.exe, WCF olmayan proxy'si oluşturucuları daha kullanışlı bir arabirim oluşturur.</span><span class="sxs-lookup"><span data-stu-id="90514-112">Non-WCF proxy generators, such as Wsdl.exe, generate a more usable interface when the XmlSerializer is being used.</span></span> <span data-ttu-id="90514-113"><xref:System.ServiceModel.XmlSerializerFormatAttribute> Uygulanan `ICalculator` arabirim, XmlSerializer CLR türleri için XML eşleme için kullanıldığından emin olmak için.</span><span class="sxs-lookup"><span data-stu-id="90514-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> is applied to the `ICalculator` interface, to ensure that the XmlSerializer is used for mapping CLR types to XML.</span></span> <span data-ttu-id="90514-114">Hizmet uygulaması, hesaplar ve uygun sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="90514-114">The service implementation calculates and returns the appropriate result.</span></span>  
  
 <span data-ttu-id="90514-115">Hizmet yapılandırma dosyasında (Web.config) kullanılarak tanımlanmış hizmet ile iletişim kurmak için tek bir uç noktayı kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="90514-115">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="90514-116">Uç nokta, adres, bağlama ve bir sözleşme oluşur.</span><span class="sxs-lookup"><span data-stu-id="90514-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="90514-117">Hizmet, Internet Information Services (IIS) ana bilgisayar tarafından sağlanan taban adresinde uç noktasını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="90514-117">The service exposes the endpoint at the base address provided by the Internet Information Services (IIS) host.</span></span> <span data-ttu-id="90514-118">`binding` Özniteliği WS ile uyumlu olan SOAP 1.1 kullanarak HTTP iletişimi sağlayan basicHttpBinding kümesine-ı BasicProfile aşağıdaki örnek yapılandırmada gösterildiği 1.1.</span><span class="sxs-lookup"><span data-stu-id="90514-118">The `binding` attribute is set to basicHttpBinding that provides HTTP communications using SOAP 1.1, which is compliant with WS-I BasicProfile 1.1 as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="90514-119">Web Hizmetleri Açıklama Dili (WSDL) yardımcı programı (Wsdl.exe) tarafından üretilen türü belirtilmiş bir proxy kullanarak WCF Hizmeti ile ASMX istemcisi iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="90514-119">The ASMX client communicates with the WCF service using a typed proxy that is generated by the Web Services Description Language (WSDL) utility (Wsdl.exe).</span></span> <span data-ttu-id="90514-120">Türü belirtilmiş bir proxy dosya generatedClient.cs içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="90514-120">The typed proxy is contained in the file generatedClient.cs.</span></span> <span data-ttu-id="90514-121">WSDL yardımcı programı, belirtilen hizmet için meta verileri alır ve iletişim kurmak için bir istemci tarafından kullanım için türü belirtilmiş bir proxy oluşturur.</span><span class="sxs-lookup"><span data-stu-id="90514-121">The WSDL utility retrieves metadata for the specified service and generates a typed proxy for use by a client to communicate.</span></span> <span data-ttu-id="90514-122">Varsayılan olarak, framework meta verileri kullanıma sunmuyor.</span><span class="sxs-lookup"><span data-stu-id="90514-122">By default, the framework does not expose any metadata.</span></span> <span data-ttu-id="90514-123">Proxy oluşturmak için gereken meta verileri kullanıma sunmak için eklemelisiniz bir [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) ve kendi `httpGetEnabled` özniteliğini `True` aşağıdaki yapılandırmayı gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="90514-123">To expose the metadata required to generate the proxy, you must add a [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) and set its `httpGetEnabled` attribute to `True` as shown in the following configuration.</span></span>  
  
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
  
 <span data-ttu-id="90514-124">Türü belirtilmiş bir proxy oluşturmak için istemci dizininde bir komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="90514-124">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl  
```  
  
 <span data-ttu-id="90514-125">Üretilen türü belirtilmiş bir proxy kullanarak istemci uygun adresi yapılandırarak belirli hizmet uç noktası erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="90514-125">By using the generated typed proxy, the client can access a given service endpoint by configuring the appropriate address.</span></span> <span data-ttu-id="90514-126">İstemci ile iletişim kurmak için uç nokta belirtmek için bir yapılandırma dosyası (App.config) kullanır.</span><span class="sxs-lookup"><span data-stu-id="90514-126">The client uses a configuration file (App.config) to specify the endpoint to communicate with.</span></span>  
  
```xml  
<appSettings>  
  <add key="CalculatorServiceAddress"   
       value="http://localhost/ServiceModelSamples/service.svc"/>  
</appSettings>  
```  
  
 <span data-ttu-id="90514-127">İstemci uygulama hizmeti ile iletişim başlatmak için türü belirtilmiş bir proxy örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="90514-127">The client implementation constructs an instance of the typed proxy to begin communicating with the service.</span></span>  
  
```  
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
  
 <span data-ttu-id="90514-128">Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="90514-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="90514-129">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="90514-129">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="90514-130">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="90514-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="90514-131">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="90514-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="90514-132">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="90514-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="90514-133">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="90514-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90514-134">Türleri ve karmaşık veri döndüren geçirme hakkında daha fazla bilgi için bkz: [bir Windows Forms istemcisinde veri bağlama](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [veri bağlama bir Windows Presentation Foundation istemcisi](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md), ve [veri Bir ASP.NET istemcisinde bağlama](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)</span><span class="sxs-lookup"><span data-stu-id="90514-134">For more information about passing and returning complex data types see: [Data Binding in a Windows Forms Client](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [Data Binding in a Windows Presentation Foundation Client](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md), and [Data Binding in an ASP.NET Client](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="90514-135">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="90514-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="90514-136">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="90514-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="90514-137">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="90514-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="90514-138">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="90514-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`  
  
## <a name="see-also"></a><span data-ttu-id="90514-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="90514-139">See Also</span></span>
