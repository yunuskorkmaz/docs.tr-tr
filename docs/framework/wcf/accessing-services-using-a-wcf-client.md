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
# <a name="accessing-services-using-a-wcf-client"></a>WCF İstemcisi Kullanarak Hizmetlere Erişme

Bir hizmet oluşturduktan sonra, bir sonraki adım bir WCF istemci proxy 'si oluşturmaktır. İstemci uygulaması, hizmet ile iletişim kurmak için WCF istemci proxy 'sini kullanır. İstemci uygulamaları genellikle hizmeti çağırmak için kullanılabilecek WCF istemci kodu oluşturmak için bir hizmetin meta verilerini içeri aktarır.

 WCF istemcisi oluşturmaya yönelik temel adımlar şunlardır:

1. Hizmet kodunu derleyin.

2. WCF istemci ara sunucusunu oluşturun.

3. WCF istemci ara sunucusunu oluşturun.

WCF istemci proxy 'si, hizmet modeli meta verileri yardımcı programı Aracı (SvcUtil. exe) kullanılarak el ile oluşturulabilir. daha fazla bilgi için bkz. [ServiceModel Metadata Utility aracı (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md). WCF istemci ara sunucusu, **hizmet başvurusu Ekle** özelliği kullanılarak Visual Studio içinde de oluşturulabilir. WCF istemci proxy 'sini her iki yöntemi kullanarak oluşturmak için hizmetin çalışıyor olması gerekir. Hizmet şirket içinde barındırılıyorsa, Konağı çalıştırmanız gerekir. Hizmet IIS 'de barındırılıyorsa/ise başka bir şey yapmanız gerekmez.

## <a name="servicemodel-metadata-utility-tool"></a>ServiceModel meta veri yardımcı programı Aracı
 [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) meta verilerden kod oluşturmaya yönelik bir komut satırı aracıdır. Aşağıdaki kullanım, temel bir Svcutil. exe komutuna bir örnektir.

```console
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 Alternatif olarak, dosya sisteminde Web Hizmetleri Açıklama Dili (WSDL) ve XML şema tanımlama dili (XSD) dosyaları ile Svcutil. exe ' yi kullanabilirsiniz.

```console
Svcutil.exe <list of WSDL and XSD files on file system>
```

 Sonuç, istemci uygulamanın hizmeti çağırmak için kullanabileceği WCF istemci kodunu içeren bir kod dosyasıdır.

 Ayrıca, yapılandırma dosyalarını oluşturmak için aracını da kullanabilirsiniz.

```console
Svcutil.exe <file1 [,file2]>
```

 Yalnızca bir dosya adı verilirse, bu çıkış dosyasının adıdır. İki dosya adı verilirse, ilk dosya içerikleri oluşturulan yapılandırmayla birleştirilen ve ikinci dosyaya yazılan bir giriş yapılandırma dosyasıdır. Yapılandırma hakkında daha fazla bilgi için bkz. [Hizmetler Için bağlamaları yapılandırma](configuring-bindings-for-wcf-services.md).

> [!IMPORTANT]
> Güvenli olmayan meta veri istekleri, güvenli olmayan herhangi bir ağ isteğiyle aynı şekilde bazı riskler ortaya çıkardığında: iletişim kurduğunuz uç noktanın kim olduğunu düşünmediği kesin değilse, aldığınız bilgiler kötü amaçlı bir hizmetten meta veriler olabilir.

## <a name="add-service-reference-in-visual-studio"></a>Visual Studio'da Hizmet Başvurusu ekleyin

 Hizmet çalışırken, WCF istemci proxy 'sini içerecek projeye sağ tıklayın ve > **hizmet başvurusu** **Ekle** ' yi seçin. **Hizmet başvurusu Ekle Iletişim kutusunda**, çağırmak istediğiniz hizmetin URL 'sini yazın ve **Git** düğmesine tıklayın. İletişim kutusunda belirttiğiniz adreste bulunan hizmetlerin bir listesi görüntülenir. Kullanılabilir sözleşmeleri ve işlemleri görmek için hizmete çift tıklayın, oluşturulan kod için bir ad alanı belirtin ve **Tamam** düğmesine tıklayın.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, bir hizmet için oluşturulan bir hizmet sözleşmesini gösterir.

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

 ServiceModel meta veri yardımcı programı aracı ve **hizmet başvurusu Ekle** Visual Studio 'DA aşağıdaki WCF istemci sınıfını oluşturur. Sınıfı, genel <xref:System.ServiceModel.ClientBase%601> sınıfından devralır ve `ICalculator` arabirimini uygular. Araç ayrıca `ICalculator` arabirimini de oluşturur (burada gösterilmez).

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

## <a name="using-the-wcf-client"></a>WCF Istemcisini kullanma
 WCF istemcisini kullanmak için, WCF istemcisinin bir örneğini oluşturun ve ardından aşağıdaki kodda gösterildiği gibi yöntemlerini çağırın.

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

## <a name="debugging-exceptions-thrown-by-a-client"></a>Istemci tarafından oluşturulan özel durumların hatalarını ayıklama

Bir WCF istemcisi tarafından oluşturulan birçok özel durum, hizmette bir özel durum nedeniyle oluşur. Buna örnek olarak şunlar verilebilir:

- <xref:System.Net.Sockets.SocketException>: varolan bir bağlantı uzak konak tarafından zorla kapatıldı.

- <xref:System.ServiceModel.CommunicationException>: temeldeki bağlantı beklenmedik bir şekilde kapatıldı.

- <xref:System.ServiceModel.CommunicationObjectAbortedException>: yuva bağlantısı iptal edildi. Bunun nedeni iletinizin işlendiği bir hata, uzak ana bilgisayar tarafından bir alma zaman aşımı veya temel alınan bir ağ kaynağı sorunu olabilir.

Bu tür özel durumlar oluştuğunda, sorunu çözmenin en iyi yolu hizmet tarafında izlemeyi açmak ve ne özel durum oluştuğunu belirlemektir. İzleme hakkında daha fazla bilgi için, [bkz. izleme ve](./diagnostics/tracing/index.md) [kullanarak uygulamanızı sorun giderme](./diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: İstemci Oluşturma](how-to-create-a-wcf-client.md)
- [Nasıl yapılır: Çift Yönlü Sözleşme ile Hizmetlere Erişme](./feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Nasıl yapılır: Hizmet İşlemlerini Zaman Uyumsuz Olarak Çağırma](./feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [Nasıl yapılır: Tek Yönlü ve İstek-Yanıt Sözleşmeleriyle Hizmetlere Erişme](./feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [Nasıl yapılır: WSE 3.0 Hizmetine Erişme](./feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [Oluşturulmuş İstemci Kodlarını Anlama](./feature-details/understanding-generated-client-code.md)
- [Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme](./feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [İstemci Çalışma Zamanı Davranışını Belirtme](specifying-client-run-time-behavior.md)
- [İstemci Davranışlarını Yapılandırma](configuring-client-behaviors.md)
