---
title: WCF İstemcisi Kullanarak Hizmetlere Erişme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: 462d9a3923009f0124c2b90b6fa86dfa9869a3c5
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72316538"
---
# <a name="accessing-services-using-a-wcf-client"></a><span data-ttu-id="edc15-102">WCF İstemcisi Kullanarak Hizmetlere Erişme</span><span class="sxs-lookup"><span data-stu-id="edc15-102">Accessing Services Using a WCF Client</span></span>

<span data-ttu-id="edc15-103">Bir hizmet oluşturduktan sonra, bir sonraki adım bir WCF istemci proxy 'si oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="edc15-103">After you create a service, the next step is to create a WCF client proxy.</span></span> <span data-ttu-id="edc15-104">İstemci uygulaması, hizmet ile iletişim kurmak için WCF istemci proxy 'sini kullanır.</span><span class="sxs-lookup"><span data-stu-id="edc15-104">A client application uses the WCF client proxy to communicate with the service.</span></span> <span data-ttu-id="edc15-105">İstemci uygulamaları genellikle hizmeti çağırmak için kullanılabilecek WCF istemci kodu oluşturmak için bir hizmetin meta verilerini içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="edc15-105">Client applications usually import a service's metadata to generate WCF client code that can be used to invoke the service.</span></span>

 <span data-ttu-id="edc15-106">WCF istemcisi oluşturmaya yönelik temel adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="edc15-106">The basic steps for creating a WCF client include the following:</span></span>

1. <span data-ttu-id="edc15-107">Hizmet kodunu derleyin.</span><span class="sxs-lookup"><span data-stu-id="edc15-107">Compile the service code.</span></span>

2. <span data-ttu-id="edc15-108">WCF istemci ara sunucusunu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="edc15-108">Generate the WCF client proxy.</span></span>

3. <span data-ttu-id="edc15-109">WCF istemci ara sunucusunu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="edc15-109">Instantiate the WCF client proxy.</span></span>

<span data-ttu-id="edc15-110">WCF istemci proxy 'si, hizmet modeli meta verileri yardımcı programı Aracı (SvcUtil. exe) kullanılarak el ile oluşturulabilir. daha fazla bilgi için bkz. [ServiceModel Metadata Utility aracı (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="edc15-110">The WCF client proxy can be generated manually by using the Service Model Metadata Utility Tool (SvcUtil.exe) for more information see, [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="edc15-111">WCF istemci ara sunucusu, **hizmet başvurusu Ekle** özelliği kullanılarak Visual Studio içinde de oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="edc15-111">The WCF client proxy can also be generated within Visual Studio using the **Add Service Reference**  feature.</span></span> <span data-ttu-id="edc15-112">WCF istemci proxy 'sini her iki yöntemi kullanarak oluşturmak için hizmetin çalışıyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="edc15-112">To generate the WCF client proxy using either method the service must be running.</span></span> <span data-ttu-id="edc15-113">Hizmet şirket içinde barındırılıyorsa, Konağı çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="edc15-113">If the service is self-hosted you must run the host.</span></span> <span data-ttu-id="edc15-114">Hizmet IIS 'de barındırılıyorsa/ise başka bir şey yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="edc15-114">If the service is hosted in IIS/WAS you do not need to do anything else.</span></span>

## <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="edc15-115">ServiceModel meta veri yardımcı programı Aracı</span><span class="sxs-lookup"><span data-stu-id="edc15-115">ServiceModel Metadata Utility Tool</span></span>
 <span data-ttu-id="edc15-116">[ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) meta verilerden kod oluşturmaya yönelik bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="edc15-116">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) is a command-line tool for generating code from metadata.</span></span> <span data-ttu-id="edc15-117">Aşağıdaki kullanım, temel bir Svcutil. exe komutuna bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="edc15-117">The following use is an example of a basic Svcutil.exe command.</span></span>

```console
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 <span data-ttu-id="edc15-118">Alternatif olarak, dosya sisteminde Web Hizmetleri Açıklama Dili (WSDL) ve XML şema tanımlama dili (XSD) dosyaları ile Svcutil. exe ' yi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="edc15-118">Alternatively, you can use Svcutil.exe with Web Services Description Language (WSDL) and XML Schema definition language (XSD) files on the file system.</span></span>

```console
Svcutil.exe <list of WSDL and XSD files on file system>
```

 <span data-ttu-id="edc15-119">Sonuç, istemci uygulamanın hizmeti çağırmak için kullanabileceği WCF istemci kodunu içeren bir kod dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="edc15-119">The result is a code file that contains WCF client code that the client application can use to invoke the service.</span></span>

 <span data-ttu-id="edc15-120">Ayrıca, yapılandırma dosyalarını oluşturmak için aracını da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="edc15-120">You can also use the tool to generate configuration files.</span></span>

```console
Svcutil.exe <file1 [,file2]>
```

 <span data-ttu-id="edc15-121">Yalnızca bir dosya adı verilirse, bu çıkış dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="edc15-121">If only one file name is given, that is the name of the output file.</span></span> <span data-ttu-id="edc15-122">İki dosya adı verilirse, ilk dosya içerikleri oluşturulan yapılandırmayla birleştirilen ve ikinci dosyaya yazılan bir giriş yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="edc15-122">If two file names are given, then the first file is an input configuration file whose contents are merged with the generated configuration and written out into the second file.</span></span> <span data-ttu-id="edc15-123">Yapılandırma hakkında daha fazla bilgi için bkz. [Hizmetler Için bağlamaları yapılandırma](configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="edc15-123">For more information about configuration, see [Configuring Bindings for Services](configuring-bindings-for-wcf-services.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="edc15-124">Güvenli olmayan meta veri istekleri, güvenli olmayan herhangi bir ağ isteğiyle aynı şekilde bazı riskler ortaya çıkardığında: iletişim kurduğunuz uç noktanın kim olduğunu düşünmediği kesin değilse, aldığınız bilgiler kötü amaçlı bir hizmetten meta veriler olabilir.</span><span class="sxs-lookup"><span data-stu-id="edc15-124">Unsecured metadata requests pose certain risks in the same way that any unsecured network request does: If you are not certain that the endpoint you are communicating with is who it says it is, the information you retrieve might be metadata from a malicious service.</span></span>

## <a name="add-service-reference-in-visual-studio"></a><span data-ttu-id="edc15-125">Visual Studio'da Hizmet Başvurusu ekleyin</span><span class="sxs-lookup"><span data-stu-id="edc15-125">Add Service Reference in Visual Studio</span></span>

 <span data-ttu-id="edc15-126">Hizmet çalışırken, WCF istemci proxy 'sini içerecek projeye sağ tıklayın ve > **hizmet başvurusu** **Ekle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="edc15-126">With the service running, right click the project that will contain the WCF client proxy and select **Add** > **Service Reference**.</span></span> <span data-ttu-id="edc15-127">**Hizmet başvurusu Ekle Iletişim kutusunda**, çağırmak istediğiniz hizmetin URL 'sini yazın ve **Git** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="edc15-127">In the **Add Service Reference Dialog**, type in the URL to the service you want to call and click the **Go** button.</span></span> <span data-ttu-id="edc15-128">İletişim kutusunda belirttiğiniz adreste bulunan hizmetlerin bir listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="edc15-128">The dialog will display a list of services available at the address you specify.</span></span> <span data-ttu-id="edc15-129">Kullanılabilir sözleşmeleri ve işlemleri görmek için hizmete çift tıklayın, oluşturulan kod için bir ad alanı belirtin ve **Tamam** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="edc15-129">Double click the service to see the contracts and operations available, specify a namespace for the generated code, and click the **OK** button.</span></span>

## <a name="example"></a><span data-ttu-id="edc15-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="edc15-130">Example</span></span>
 <span data-ttu-id="edc15-131">Aşağıdaki kod örneği, bir hizmet için oluşturulan bir hizmet sözleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="edc15-131">The following code example shows a service contract created for a service.</span></span>

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

 <span data-ttu-id="edc15-132">ServiceModel meta veri yardımcı programı aracı ve **hizmet başvurusu Ekle** Visual Studio 'DA aşağıdaki WCF istemci sınıfını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="edc15-132">The ServiceModel Metadata utility tool and **Add Service Reference** in Visual Studio generates the following WCF client class.</span></span> <span data-ttu-id="edc15-133">Sınıfı, genel <xref:System.ServiceModel.ClientBase%601> sınıfından devralır ve `ICalculator` arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="edc15-133">The class inherits from the generic <xref:System.ServiceModel.ClientBase%601> class and implements the `ICalculator` interface.</span></span> <span data-ttu-id="edc15-134">Araç ayrıca `ICalculator` arabirimini de oluşturur (burada gösterilmez).</span><span class="sxs-lookup"><span data-stu-id="edc15-134">The tool also generates the `ICalculator` interface (not shown here).</span></span>

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

## <a name="using-the-wcf-client"></a><span data-ttu-id="edc15-135">WCF Istemcisini kullanma</span><span class="sxs-lookup"><span data-stu-id="edc15-135">Using the WCF Client</span></span>
 <span data-ttu-id="edc15-136">WCF istemcisini kullanmak için, WCF istemcisinin bir örneğini oluşturun ve ardından aşağıdaki kodda gösterildiği gibi yöntemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="edc15-136">To use the WCF client, create an instance of the WCF client, and then call its methods, as shown in the following code.</span></span>

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

## <a name="debugging-exceptions-thrown-by-a-client"></a><span data-ttu-id="edc15-137">Istemci tarafından oluşturulan özel durumların hatalarını ayıklama</span><span class="sxs-lookup"><span data-stu-id="edc15-137">Debugging Exceptions Thrown by a Client</span></span>

<span data-ttu-id="edc15-138">Bir WCF istemcisi tarafından oluşturulan birçok özel durum, hizmette bir özel durum nedeniyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="edc15-138">Many exceptions thrown by a WCF client are caused by an exception on the service.</span></span> <span data-ttu-id="edc15-139">Buna örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="edc15-139">Some examples of this are:</span></span>

- <span data-ttu-id="edc15-140"><xref:System.Net.Sockets.SocketException>: varolan bir bağlantı uzak konak tarafından zorla kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="edc15-140"><xref:System.Net.Sockets.SocketException>: An existing connection was forcibly closed by the remote host.</span></span>

- <span data-ttu-id="edc15-141"><xref:System.ServiceModel.CommunicationException>: temeldeki bağlantı beklenmedik bir şekilde kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="edc15-141"><xref:System.ServiceModel.CommunicationException>: The underlying connection was closed unexpectedly.</span></span>

- <span data-ttu-id="edc15-142"><xref:System.ServiceModel.CommunicationObjectAbortedException>: yuva bağlantısı iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="edc15-142"><xref:System.ServiceModel.CommunicationObjectAbortedException>: The socket connection was aborted.</span></span> <span data-ttu-id="edc15-143">Bunun nedeni iletinizin işlendiği bir hata, uzak ana bilgisayar tarafından bir alma zaman aşımı veya temel alınan bir ağ kaynağı sorunu olabilir.</span><span class="sxs-lookup"><span data-stu-id="edc15-143">This could be caused by an error processing your message, a receive time-out being exceeded by the remote host, or an underlying network resource issue.</span></span>

<span data-ttu-id="edc15-144">Bu tür özel durumlar oluştuğunda, sorunu çözmenin en iyi yolu hizmet tarafında izlemeyi açmak ve ne özel durum oluştuğunu belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="edc15-144">When these types of exceptions occur, the best way to solve the problem is to turn on tracing on the service side and determine what exception occurred there.</span></span> <span data-ttu-id="edc15-145">İzleme hakkında daha fazla bilgi için, [bkz. izleme ve](./diagnostics/tracing/index.md) [kullanarak uygulamanızı sorun giderme](./diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="edc15-145">For more information about tracing, see [Tracing](./diagnostics/tracing/index.md) and [Using Tracing to Troubleshoot Your Application](./diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="edc15-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edc15-146">See also</span></span>

- [<span data-ttu-id="edc15-147">Nasıl yapılır: İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="edc15-147">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [<span data-ttu-id="edc15-148">Nasıl yapılır: Çift Yönlü Sözleşme ile Hizmetlere Erişme</span><span class="sxs-lookup"><span data-stu-id="edc15-148">How to: Access Services with a Duplex Contract</span></span>](./feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="edc15-149">Nasıl yapılır: Hizmet İşlemlerini Zaman Uyumsuz Olarak Çağırma</span><span class="sxs-lookup"><span data-stu-id="edc15-149">How to: Call Service Operations Asynchronously</span></span>](./feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [<span data-ttu-id="edc15-150">Nasıl yapılır: Tek Yönlü ve İstek-Yanıt Sözleşmeleriyle Hizmetlere Erişme</span><span class="sxs-lookup"><span data-stu-id="edc15-150">How to: Access Services with One-Way and Request-Reply Contracts</span></span>](./feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [<span data-ttu-id="edc15-151">Nasıl yapılır: WSE 3.0 Hizmetine Erişme</span><span class="sxs-lookup"><span data-stu-id="edc15-151">How to: Access a WSE 3.0 Service</span></span>](./feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [<span data-ttu-id="edc15-152">Oluşturulmuş İstemci Kodlarını Anlama</span><span class="sxs-lookup"><span data-stu-id="edc15-152">Understanding Generated Client Code</span></span>](./feature-details/understanding-generated-client-code.md)
- [<span data-ttu-id="edc15-153">Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme</span><span class="sxs-lookup"><span data-stu-id="edc15-153">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>](./feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [<span data-ttu-id="edc15-154">İstemci Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="edc15-154">Specifying Client Run-Time Behavior</span></span>](specifying-client-run-time-behavior.md)
- [<span data-ttu-id="edc15-155">İstemci Davranışlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="edc15-155">Configuring Client Behaviors</span></span>](configuring-client-behaviors.md)
