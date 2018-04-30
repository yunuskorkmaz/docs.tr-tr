---
title: WCF İstemcisi Kullanarak Hizmetlere Erişme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
caps.latest.revision: 36
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 69352ba5c12267f5075ae38c5bdcc0665b3fe050
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="accessing-services-using-a-wcf-client"></a><span data-ttu-id="a10a7-102">WCF İstemcisi Kullanarak Hizmetlere Erişme</span><span class="sxs-lookup"><span data-stu-id="a10a7-102">Accessing Services Using a WCF Client</span></span>
<span data-ttu-id="a10a7-103">Bir hizmeti oluşturduktan sonra sonraki adıma oluşturmaktır bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci proxy.</span><span class="sxs-lookup"><span data-stu-id="a10a7-103">After you create a service, the next step is to create a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client proxy.</span></span> <span data-ttu-id="a10a7-104">Bir istemci uygulaması kullanan [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmetiyle iletişim kurmak için istemci proxy.</span><span class="sxs-lookup"><span data-stu-id="a10a7-104">A client application uses the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client proxy to communicate with the service.</span></span> <span data-ttu-id="a10a7-105">İstemci uygulamaları genellikle oluşturmak için bir hizmetin meta verileri içe aktarma [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmetini çağırmak için kullanılan istemci kodu.</span><span class="sxs-lookup"><span data-stu-id="a10a7-105">Client applications usually import a service's metadata to generate [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client code that can be used to invoke the service.</span></span>  
  
 <span data-ttu-id="a10a7-106">Oluşturmak için temel adımlar bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="a10a7-106">The basic steps for creating a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client include the following:</span></span>  
  
1.  <span data-ttu-id="a10a7-107">Hizmet koduna derleyin.</span><span class="sxs-lookup"><span data-stu-id="a10a7-107">Compile the service code.</span></span>  
  
2.  <span data-ttu-id="a10a7-108">Oluştur [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci proxy.</span><span class="sxs-lookup"><span data-stu-id="a10a7-108">Generate the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client proxy.</span></span>  
  
3.  <span data-ttu-id="a10a7-109">WCF istemci proxy örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a10a7-109">Instantiate the WCF client proxy.</span></span>  
  
 <span data-ttu-id="a10a7-110">WCF istemci proxy daha fazla bilgi için bkz: hizmet Model meta veri yardımcı Programracı (SvcUtil.exe) kullanarak el ile oluşturulabilir [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a10a7-110">The WCF client proxy can be generated manually by using the Service Model Metadata Utility Tool (SvcUtil.exe) for more information see, [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="a10a7-111">WCF istemci proxy ayrıca Visual Studio'da hizmet Başvurusu Ekle özelliği kullanılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="a10a7-111">The WCF client proxy can also be generated within Visual Studio using the Add Service Reference  feature.</span></span> <span data-ttu-id="a10a7-112">Hizmet yöntemlerden birini kullanarak WCF istemci proxy oluşturmak için çalıştırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a10a7-112">To generate the WCF client proxy using either method the service must be running.</span></span> <span data-ttu-id="a10a7-113">Hizmet kendiliğinden barındırılır varsa, ana bilgisayar çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a10a7-113">If the service is self-hosted you must run the host.</span></span> <span data-ttu-id="a10a7-114">Hizmet IIS'de barındırılıyorsa / olan başka bir şey yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a10a7-114">If the service is hosted in IIS/WAS you do not need to do anything else.</span></span>  
  
## <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="a10a7-115">ServiceModel meta veri yardımcı Programracı</span><span class="sxs-lookup"><span data-stu-id="a10a7-115">ServiceModel Metadata Utility Tool</span></span>  
 <span data-ttu-id="a10a7-116">[ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) meta verilerini kodu oluşturmak için bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="a10a7-116">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) is a command-line tool for generating code from metadata.</span></span> <span data-ttu-id="a10a7-117">Bir temel Svcutil.exe komutu örneği kullanılmasıdır.</span><span class="sxs-lookup"><span data-stu-id="a10a7-117">The following use is an example of a basic Svcutil.exe command.</span></span>  
  
```  
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
```  
  
 <span data-ttu-id="a10a7-118">Alternatif olarak, Web Hizmetleri Açıklama Dili (WSDL) ve XML Şeması Tanım Dili (XSD) dosyaları dosya sisteminde ile Svcutil.exe kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a10a7-118">Alternatively, you can use Svcutil.exe with Web Services Description Language (WSDL) and XML Schema definition language (XSD) files on the file system.</span></span>  
  
```  
Svcutil.exe <list of WSDL and XSD files on file system>  
```  
  
 <span data-ttu-id="a10a7-119">Sonuç içeren bir kod dosyasıdır [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci uygulamanın hizmetini çağırmak için kullanabileceği istemci kodu.</span><span class="sxs-lookup"><span data-stu-id="a10a7-119">The result is a code file that contains [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client code that the client application can use to invoke the service.</span></span>  
  
 <span data-ttu-id="a10a7-120">Aracı, yapılandırma dosyaları oluşturmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a10a7-120">You can also use the tool to generate configuration files.</span></span>  
  
```  
Svcutil.exe <file1 [,file2]>  
```  
  
 <span data-ttu-id="a10a7-121">Yalnızca bir dosya adı verilen, çıktı dosyası adını olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="a10a7-121">If only one file name is given, that is the name of the output file.</span></span> <span data-ttu-id="a10a7-122">İki dosya adları verilirse, ilk dosya içerikleri oluşturulan yapılandırmayla birleştirilmiş ve ikinci dosyaya yazılan bir giriş yapılandırma dosyası ise.</span><span class="sxs-lookup"><span data-stu-id="a10a7-122">If two file names are given, then the first file is an input configuration file whose contents are merged with the generated configuration and written out into the second file.</span></span> <span data-ttu-id="a10a7-123">Yapılandırma hakkında daha fazla bilgi için bkz: [hizmetler için bağlamaları yapılandırma](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a10a7-123">For more information about configuration, see [Configuring Bindings for Services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a10a7-124">Güvenli olmayan meta veri isteklerine yönelik bazı riskleri herhangi güvenli ağ isteği yapan aynı şekilde:, kurduğunuz endpoint kimin olduğu yazacaktır olduğundan emin değilseniz, aldığınız bilgiler kötü amaçlı bir hizmete meta verileri olabilir.</span><span class="sxs-lookup"><span data-stu-id="a10a7-124">Unsecured metadata requests pose certain risks in the same way that any unsecured network request does: If you are not certain that the endpoint you are communicating with is who it says it is, the information you retrieve might be metadata from a malicious service.</span></span>  
  
## <a name="add-service-reference-in-visual-studio"></a><span data-ttu-id="a10a7-125">Visual Studio'da hizmet Başvurusu Ekle</span><span class="sxs-lookup"><span data-stu-id="a10a7-125">Add Service Reference in Visual Studio</span></span>  
 <span data-ttu-id="a10a7-126">Hizmetin çalışmasını ile WCF istemci proxy içerir ve seçin projeye sağ tıklayın **hizmet Başvurusu Ekle**.</span><span class="sxs-lookup"><span data-stu-id="a10a7-126">With the service running, right click the project that will contain the WCF client proxy and select **Add Service Reference**.</span></span> <span data-ttu-id="a10a7-127">İçinde **hizmeti başvuru iletişim kutusu ekleme** çağrısı tıklatıp istediğiniz hizmeti URL'sini yazın **Git** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a10a7-127">In the **Add Service Reference Dialog** type in the URL to the service you want to call and click the **Go** button.</span></span> <span data-ttu-id="a10a7-128">İletişim kutusunda belirttiğiniz adresinde kullanılabilir hizmetlerin listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a10a7-128">The dialog will display a list of services available at the address you specify.</span></span> <span data-ttu-id="a10a7-129">Sözleşmeler ve kullanılabilir işlemleri görmek, üretilen kod için bir ad belirtin ve hizmeti çift tıklatın **Tamam** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="a10a7-129">Double click the service to see the contracts and operations available, specify a namespace for the generated code and click the **OK** button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a10a7-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="a10a7-130">Example</span></span>  
 <span data-ttu-id="a10a7-131">Aşağıdaki kod örneği bir hizmet için oluşturulan bir hizmet sözleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a10a7-131">The following code example shows a service contract created for a service.</span></span>  
  
```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    // Other methods are not shown here.
}
```
  
```vb
' Define a service contract.
<ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
Public Interface ICalculator
    <OperationContract()>  _
    Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
    ' Other methods are not shown here.
End Interface
```
  
 <span data-ttu-id="a10a7-132">Visual Studio'da hizmet Başvurusu Ekle ve ServiceModel meta veri yardımcı programı aracı oluşturur aşağıdaki [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a10a7-132">The ServiceModel Metadata utility tool and Add Service Reference in Visual Studio generates the following [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client class.</span></span> <span data-ttu-id="a10a7-133">Genel sınıf devralır <xref:System.ServiceModel.ClientBase%601> sınıfı ve uygulayan `ICalculator` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a10a7-133">The class inherits from the generic <xref:System.ServiceModel.ClientBase%601> class and implements the `ICalculator` interface.</span></span> <span data-ttu-id="a10a7-134">Araç ayrıca oluşturur `ICalculator` arabirimi (burada gösterilmiyor).</span><span class="sxs-lookup"><span data-stu-id="a10a7-134">The tool also generates the `ICalculator` interface (not shown here).</span></span>  
  
```csharp
public partial class CalculatorClient : System.ServiceModel.ClientBase<ICalculator>, ICalculator
{
    public CalculatorClient()
    {}

    public CalculatorClient(string endpointConfigurationName) :
            base(endpointConfigurationName)
    {}

    public CalculatorClient(string endpointConfigurationName, string remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(string endpointConfigurationName,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(System.ServiceModel.Channels.Binding binding,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(binding, remoteAddress)
    {}

    public double Add(double n1, double n2)
    {
        return base.Channel.Add(n1, n2);
    }
}
```  
  
```vb  
Partial Public Class CalculatorClient
    Inherits System.ServiceModel.ClientBase(Of ICalculator)
    Implements ICalculator

    Public Sub New()
        MyBase.New
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String)
        MyBase.New(endpointConfigurationName)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String, ByVal remoteAddress As String)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal binding As System.ServiceModel.Channels.Binding,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(binding, remoteAddress)
    End Sub

    Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        Implements ICalculator.Add
        Return MyBase.Channel.Add(n1, n2)
    End Function
End Class
```
  
## <a name="using-the-wcf-client"></a><span data-ttu-id="a10a7-135">WCF istemcisi kullanarak</span><span class="sxs-lookup"><span data-stu-id="a10a7-135">Using the WCF Client</span></span>  
 <span data-ttu-id="a10a7-136">Kullanılacak [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemcisi, bir örneğini oluşturmak [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci ve ardından aşağıdaki kodda gösterildiği gibi yöntemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="a10a7-136">To use the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client, create an instance of the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client, and then call its methods, as shown in the following code.</span></span>  
  
```csharp
// Create a client object with the given client endpoint configuration.
CalculatorClient calcClient = new CalculatorClient("CalculatorEndpoint"));
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = calcClient.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```
  
```vb
' Create a client object with the given client endpoint configuration.
Dim calcClient As CalculatorClient = _
New CalculatorClient("CalculatorEndpoint")

' Call the Add service operation.
Dim value1 As Double = 100.00D
Dim value2 As Double = 15.99D
Dim result As Double = calcClient.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)
```
  
## <a name="debugging-exceptions-thrown-by-a-client"></a><span data-ttu-id="a10a7-137">Bir istemci tarafından oluşturulan özel durumları hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="a10a7-137">Debugging Exceptions Thrown by a Client</span></span>  
 <span data-ttu-id="a10a7-138">Tarafından oluşturulan birçok özel durumlar bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci hizmeti bir özel durum neden.</span><span class="sxs-lookup"><span data-stu-id="a10a7-138">Many exceptions thrown by a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client are caused by an exception on the service.</span></span> <span data-ttu-id="a10a7-139">Bu, bazı örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a10a7-139">Some examples of this are:</span></span>  
  
-   <span data-ttu-id="a10a7-140"><xref:System.Net.Sockets.SocketException>: Varolan bir bağlantıyı zorla uzak ana bilgisayar tarafından kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="a10a7-140"><xref:System.Net.Sockets.SocketException>: An existing connection was forcibly closed by the remote host.</span></span>  
  
-   <span data-ttu-id="a10a7-141"><xref:System.ServiceModel.CommunicationException>: Arka plandaki bağlantı beklenmedik şekilde kesildi.</span><span class="sxs-lookup"><span data-stu-id="a10a7-141"><xref:System.ServiceModel.CommunicationException>: The underlying connection was closed unexpectedly.</span></span>  
  
-   <span data-ttu-id="a10a7-142"><xref:System.ServiceModel.CommunicationObjectAbortedException>: Yuva bağlantısı iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a10a7-142"><xref:System.ServiceModel.CommunicationObjectAbortedException>: The socket connection was aborted.</span></span> <span data-ttu-id="a10a7-143">Bu uzak ana bilgisayara veya bir arka plandaki ağ kaynağı sorunu aşılması alma zaman aşımı iletinizi işlenirken bir hata kaynaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="a10a7-143">This could be caused by an error processing your message, a receive time-out being exceeded by the remote host, or an underlying network resource issue.</span></span>  
  
 <span data-ttu-id="a10a7-144">Bu tür özel durumlar ortaya çıktığında, sorunu çözmek için en iyi hizmet tarafı izlemeyi etkinleştirmek ve hangi özel durumu var. oluştu belirlemek için yoludur.</span><span class="sxs-lookup"><span data-stu-id="a10a7-144">When these types of exceptions occur, the best way to solve the problem is to turn on tracing on the service side and determine what exception occurred there.</span></span> <span data-ttu-id="a10a7-145">İzleme hakkında daha fazla bilgi için bkz: [izleme](../../../docs/framework/wcf/diagnostics/tracing/index.md) ve [uygulamanız sorun giderme kullanarak izlemeyi](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="a10a7-145">For more information about tracing, see [Tracing](../../../docs/framework/wcf/diagnostics/tracing/index.md) and [Using Tracing to Troubleshoot Your Application](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a10a7-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a10a7-146">See Also</span></span>  
 [<span data-ttu-id="a10a7-147">Nasıl yapılır: İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a10a7-147">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="a10a7-148">Nasıl yapılır: Çift Yönlü Sözleşme ile Hizmetlere Erişme</span><span class="sxs-lookup"><span data-stu-id="a10a7-148">How to: Access Services with a Duplex Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [<span data-ttu-id="a10a7-149">Nasıl yapılır: Hizmet İşlemlerini Zaman Uyumsuz Olarak Çağırma</span><span class="sxs-lookup"><span data-stu-id="a10a7-149">How to: Call Service Operations Asynchronously</span></span>](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)  
 [<span data-ttu-id="a10a7-150">Nasıl yapılır: Tek Yönlü ve İstek-Yanıt Sözleşmeleriyle Hizmetlere Erişme</span><span class="sxs-lookup"><span data-stu-id="a10a7-150">How to: Access Services with One-Way and Request-Reply Contracts</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)  
 [<span data-ttu-id="a10a7-151">Nasıl yapılır: WSE 3.0 Hizmetine Erişme</span><span class="sxs-lookup"><span data-stu-id="a10a7-151">How to: Access a WSE 3.0 Service</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)  
 [<span data-ttu-id="a10a7-152">Oluşturulmuş İstemci Kodlarını Anlama</span><span class="sxs-lookup"><span data-stu-id="a10a7-152">Understanding Generated Client Code</span></span>](../../../docs/framework/wcf/feature-details/understanding-generated-client-code.md)  
 [<span data-ttu-id="a10a7-153">Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme</span><span class="sxs-lookup"><span data-stu-id="a10a7-153">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)  
 [<span data-ttu-id="a10a7-154">İstemci Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="a10a7-154">Specifying Client Run-Time Behavior</span></span>](../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [<span data-ttu-id="a10a7-155">İstemci Davranışlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a10a7-155">Configuring Client Behaviors</span></span>](../../../docs/framework/wcf/configuring-client-behaviors.md)
