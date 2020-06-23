---
title: WCF İstemcisi Kullanarak Hizmetlere Erişme
description: WCF hizmetiniz için bir WCF istemci proxy 'si oluşturmayı öğrenin. İstemci uygulaması, hizmet ile iletişim kurmak için istemci proxy 'sini kullanır.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: 25446a89a0b5657d32d77e2d0d57f58f36bed71b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245550"
---
# <a name="accessing-services-using-a-wcf-client"></a><span data-ttu-id="19ad0-104">WCF İstemcisi Kullanarak Hizmetlere Erişme</span><span class="sxs-lookup"><span data-stu-id="19ad0-104">Accessing Services Using a WCF Client</span></span>

<span data-ttu-id="19ad0-105">Bir hizmet oluşturduktan sonra, bir sonraki adım bir WCF istemci proxy 'si oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="19ad0-105">After you create a service, the next step is to create a WCF client proxy.</span></span> <span data-ttu-id="19ad0-106">İstemci uygulaması, hizmet ile iletişim kurmak için WCF istemci proxy 'sini kullanır.</span><span class="sxs-lookup"><span data-stu-id="19ad0-106">A client application uses the WCF client proxy to communicate with the service.</span></span> <span data-ttu-id="19ad0-107">İstemci uygulamaları genellikle hizmeti çağırmak için kullanılabilecek WCF istemci kodu oluşturmak için bir hizmetin meta verilerini içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="19ad0-107">Client applications usually import a service's metadata to generate WCF client code that can be used to invoke the service.</span></span>

 <span data-ttu-id="19ad0-108">WCF istemcisi oluşturmaya yönelik temel adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="19ad0-108">The basic steps for creating a WCF client include the following:</span></span>

1. <span data-ttu-id="19ad0-109">Hizmet kodunu derleyin.</span><span class="sxs-lookup"><span data-stu-id="19ad0-109">Compile the service code.</span></span>

2. <span data-ttu-id="19ad0-110">WCF istemci ara sunucusunu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="19ad0-110">Generate the WCF client proxy.</span></span>

3. <span data-ttu-id="19ad0-111">WCF istemci ara sunucusunu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="19ad0-111">Instantiate the WCF client proxy.</span></span>

<span data-ttu-id="19ad0-112">WCF istemci proxy 'si, hizmet modeli meta verileri yardımcı programı Aracı (SvcUtil.exe) kullanılarak el ile oluşturulabilir. daha fazla bilgi için bkz. [ServiceModel Metadata Utility aracı (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="19ad0-112">The WCF client proxy can be generated manually by using the Service Model Metadata Utility Tool (SvcUtil.exe) for more information see, [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="19ad0-113">WCF istemci ara sunucusu, **hizmet başvurusu Ekle** özelliği kullanılarak Visual Studio içinde de oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="19ad0-113">The WCF client proxy can also be generated within Visual Studio using the **Add Service Reference**  feature.</span></span> <span data-ttu-id="19ad0-114">WCF istemci proxy 'sini her iki yöntemi kullanarak oluşturmak için hizmetin çalışıyor olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="19ad0-114">To generate the WCF client proxy using either method the service must be running.</span></span> <span data-ttu-id="19ad0-115">Hizmet şirket içinde barındırılıyorsa, Konağı çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="19ad0-115">If the service is self-hosted you must run the host.</span></span> <span data-ttu-id="19ad0-116">Hizmet IIS 'de barındırılıyorsa/ise başka bir şey yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="19ad0-116">If the service is hosted in IIS/WAS you do not need to do anything else.</span></span>

## <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="19ad0-117">ServiceModel meta veri yardımcı programı Aracı</span><span class="sxs-lookup"><span data-stu-id="19ad0-117">ServiceModel Metadata Utility Tool</span></span>
 <span data-ttu-id="19ad0-118">[ServiceModel meta veri yardımcı programı Aracı (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) , meta verilerden kod oluşturmaya yönelik bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="19ad0-118">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) is a command-line tool for generating code from metadata.</span></span> <span data-ttu-id="19ad0-119">Aşağıdaki kullanım, temel bir Svcutil.exe komutuna bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="19ad0-119">The following use is an example of a basic Svcutil.exe command.</span></span>

```console
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 <span data-ttu-id="19ad0-120">Alternatif olarak, dosya sisteminde Web Hizmetleri Açıklama Dili (WSDL) ve XML şeması tanım dili (XSD) dosyaları ile Svcutil.exe kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19ad0-120">Alternatively, you can use Svcutil.exe with Web Services Description Language (WSDL) and XML Schema definition language (XSD) files on the file system.</span></span>

```console
Svcutil.exe <list of WSDL and XSD files on file system>
```

 <span data-ttu-id="19ad0-121">Sonuç, istemci uygulamanın hizmeti çağırmak için kullanabileceği WCF istemci kodunu içeren bir kod dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="19ad0-121">The result is a code file that contains WCF client code that the client application can use to invoke the service.</span></span>

 <span data-ttu-id="19ad0-122">Ayrıca, yapılandırma dosyalarını oluşturmak için aracını da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19ad0-122">You can also use the tool to generate configuration files.</span></span>

```console
Svcutil.exe <file1 [,file2]>
```

 <span data-ttu-id="19ad0-123">Yalnızca bir dosya adı verilirse, bu çıkış dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="19ad0-123">If only one file name is given, that is the name of the output file.</span></span> <span data-ttu-id="19ad0-124">İki dosya adı verilirse, ilk dosya içerikleri oluşturulan yapılandırmayla birleştirilen ve ikinci dosyaya yazılan bir giriş yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="19ad0-124">If two file names are given, then the first file is an input configuration file whose contents are merged with the generated configuration and written out into the second file.</span></span> <span data-ttu-id="19ad0-125">Yapılandırma hakkında daha fazla bilgi için bkz. [Hizmetler Için bağlamaları yapılandırma](configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="19ad0-125">For more information about configuration, see [Configuring Bindings for Services](configuring-bindings-for-wcf-services.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="19ad0-126">Güvenli olmayan meta veri istekleri, güvenli olmayan herhangi bir ağ isteğiyle aynı şekilde bazı riskler ortaya çıkardığında: iletişim kurduğunuz uç noktanın kim olduğunu düşünmediği kesin değilse, aldığınız bilgiler kötü amaçlı bir hizmetten meta veriler olabilir.</span><span class="sxs-lookup"><span data-stu-id="19ad0-126">Unsecured metadata requests pose certain risks in the same way that any unsecured network request does: If you are not certain that the endpoint you are communicating with is who it says it is, the information you retrieve might be metadata from a malicious service.</span></span>

## <a name="add-service-reference-in-visual-studio"></a><span data-ttu-id="19ad0-127">Visual Studio 'da Hizmet Başvurusu Ekle</span><span class="sxs-lookup"><span data-stu-id="19ad0-127">Add Service Reference in Visual Studio</span></span>

 <span data-ttu-id="19ad0-128">Hizmet çalışırken, WCF istemci ara sunucusunu içerecek projeye sağ tıklayın ve **Add**  >  **hizmet başvurusu**Ekle ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="19ad0-128">With the service running, right click the project that will contain the WCF client proxy and select **Add** > **Service Reference**.</span></span> <span data-ttu-id="19ad0-129">**Hizmet başvurusu Ekle Iletişim kutusunda**, çağırmak istediğiniz hizmetin URL 'sini yazın ve **Git** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="19ad0-129">In the **Add Service Reference Dialog**, type in the URL to the service you want to call and click the **Go** button.</span></span> <span data-ttu-id="19ad0-130">İletişim kutusunda belirttiğiniz adreste bulunan hizmetlerin bir listesi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="19ad0-130">The dialog will display a list of services available at the address you specify.</span></span> <span data-ttu-id="19ad0-131">Kullanılabilir sözleşmeleri ve işlemleri görmek için hizmete çift tıklayın, oluşturulan kod için bir ad alanı belirtin ve **Tamam** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="19ad0-131">Double click the service to see the contracts and operations available, specify a namespace for the generated code, and click the **OK** button.</span></span>

## <a name="example"></a><span data-ttu-id="19ad0-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="19ad0-132">Example</span></span>
 <span data-ttu-id="19ad0-133">Aşağıdaki kod örneği, bir hizmet için oluşturulan bir hizmet sözleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="19ad0-133">The following code example shows a service contract created for a service.</span></span>

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

 <span data-ttu-id="19ad0-134">ServiceModel meta veri yardımcı programı aracı ve **hizmet başvurusu Ekle** Visual Studio 'DA aşağıdaki WCF istemci sınıfını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="19ad0-134">The ServiceModel Metadata utility tool and **Add Service Reference** in Visual Studio generates the following WCF client class.</span></span> <span data-ttu-id="19ad0-135">Sınıfı genel <xref:System.ServiceModel.ClientBase%601> sınıftan devralınır ve `ICalculator` arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="19ad0-135">The class inherits from the generic <xref:System.ServiceModel.ClientBase%601> class and implements the `ICalculator` interface.</span></span> <span data-ttu-id="19ad0-136">Araç ayrıca arabirimi de oluşturur `ICalculator` (burada gösterilmez).</span><span class="sxs-lookup"><span data-stu-id="19ad0-136">The tool also generates the `ICalculator` interface (not shown here).</span></span>

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

## <a name="using-the-wcf-client"></a><span data-ttu-id="19ad0-137">WCF Istemcisini kullanma</span><span class="sxs-lookup"><span data-stu-id="19ad0-137">Using the WCF Client</span></span>
 <span data-ttu-id="19ad0-138">WCF istemcisini kullanmak için, WCF istemcisinin bir örneğini oluşturun ve ardından aşağıdaki kodda gösterildiği gibi yöntemlerini çağırın.</span><span class="sxs-lookup"><span data-stu-id="19ad0-138">To use the WCF client, create an instance of the WCF client, and then call its methods, as shown in the following code.</span></span>

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

## <a name="debugging-exceptions-thrown-by-a-client"></a><span data-ttu-id="19ad0-139">Istemci tarafından oluşturulan özel durumların hatalarını ayıklama</span><span class="sxs-lookup"><span data-stu-id="19ad0-139">Debugging Exceptions Thrown by a Client</span></span>

<span data-ttu-id="19ad0-140">Bir WCF istemcisi tarafından oluşturulan birçok özel durum, hizmette bir özel durum nedeniyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="19ad0-140">Many exceptions thrown by a WCF client are caused by an exception on the service.</span></span> <span data-ttu-id="19ad0-141">Buna örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="19ad0-141">Some examples of this are:</span></span>

- <span data-ttu-id="19ad0-142"><xref:System.Net.Sockets.SocketException>: Mevcut bir bağlantı uzak ana bilgisayar tarafından zorla kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="19ad0-142"><xref:System.Net.Sockets.SocketException>: An existing connection was forcibly closed by the remote host.</span></span>

- <span data-ttu-id="19ad0-143"><xref:System.ServiceModel.CommunicationException>: Temeldeki bağlantı beklenmedik bir şekilde kapatıldı.</span><span class="sxs-lookup"><span data-stu-id="19ad0-143"><xref:System.ServiceModel.CommunicationException>: The underlying connection was closed unexpectedly.</span></span>

- <span data-ttu-id="19ad0-144"><xref:System.ServiceModel.CommunicationObjectAbortedException>: Yuva bağlantısı iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="19ad0-144"><xref:System.ServiceModel.CommunicationObjectAbortedException>: The socket connection was aborted.</span></span> <span data-ttu-id="19ad0-145">Bunun nedeni iletinizin işlendiği bir hata, uzak ana bilgisayar tarafından bir alma zaman aşımı veya temel alınan bir ağ kaynağı sorunu olabilir.</span><span class="sxs-lookup"><span data-stu-id="19ad0-145">This could be caused by an error processing your message, a receive time-out being exceeded by the remote host, or an underlying network resource issue.</span></span>

<span data-ttu-id="19ad0-146">Bu tür özel durumlar oluştuğunda, sorunu çözmenin en iyi yolu hizmet tarafında izlemeyi açmak ve ne özel durum oluştuğunu belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="19ad0-146">When these types of exceptions occur, the best way to solve the problem is to turn on tracing on the service side and determine what exception occurred there.</span></span> <span data-ttu-id="19ad0-147">İzleme hakkında daha fazla bilgi için, [bkz. izleme ve](./diagnostics/tracing/index.md) [kullanarak uygulamanızı sorun giderme](./diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="19ad0-147">For more information about tracing, see [Tracing](./diagnostics/tracing/index.md) and [Using Tracing to Troubleshoot Your Application](./diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="19ad0-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19ad0-148">See also</span></span>

- [<span data-ttu-id="19ad0-149">Nasıl yapılır: İstemci Oluşturma</span><span class="sxs-lookup"><span data-stu-id="19ad0-149">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [<span data-ttu-id="19ad0-150">Nasıl yapılır: Çift Yönlü Sözleşme ile Hizmetlere Erişme</span><span class="sxs-lookup"><span data-stu-id="19ad0-150">How to: Access Services with a Duplex Contract</span></span>](./feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="19ad0-151">Nasıl yapılır: Hizmet İşlemlerini Zaman Uyumsuz Olarak Çağırma</span><span class="sxs-lookup"><span data-stu-id="19ad0-151">How to: Call Service Operations Asynchronously</span></span>](./feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [<span data-ttu-id="19ad0-152">Nasıl yapılır: Tek Yönlü ve İstek-Yanıt Sözleşmeleriyle Hizmetlere Erişme</span><span class="sxs-lookup"><span data-stu-id="19ad0-152">How to: Access Services with One-Way and Request-Reply Contracts</span></span>](./feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [<span data-ttu-id="19ad0-153">Nasıl yapılır: WSE 3.0 Hizmetine Erişme</span><span class="sxs-lookup"><span data-stu-id="19ad0-153">How to: Access a WSE 3.0 Service</span></span>](./feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [<span data-ttu-id="19ad0-154">Oluşturulmuş İstemci Kodlarını Anlama</span><span class="sxs-lookup"><span data-stu-id="19ad0-154">Understanding Generated Client Code</span></span>](./feature-details/understanding-generated-client-code.md)
- [<span data-ttu-id="19ad0-155">Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme</span><span class="sxs-lookup"><span data-stu-id="19ad0-155">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>](./feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [<span data-ttu-id="19ad0-156">İstemci Çalışma Zamanı Davranışını Belirtme</span><span class="sxs-lookup"><span data-stu-id="19ad0-156">Specifying Client Run-Time Behavior</span></span>](specifying-client-run-time-behavior.md)
- [<span data-ttu-id="19ad0-157">İstemci Davranışlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="19ad0-157">Configuring Client Behaviors</span></span>](configuring-client-behaviors.md)
