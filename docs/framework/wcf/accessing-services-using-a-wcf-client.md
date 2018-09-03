---
title: WCF İstemcisi Kullanarak Hizmetlere Erişme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: 0678300fca4442cf90dd15c5a4e011d80656eac6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43478162"
---
# <a name="accessing-services-using-a-wcf-client"></a>WCF İstemcisi Kullanarak Hizmetlere Erişme

Bir hizmet oluşturduktan sonra sonraki adım bir WCF istemci proxy oluşturmaktır. Bir istemci uygulaması, WCF istemci proxy hizmeti ile iletişim kurmak için kullanır. İstemci uygulamaları genellikle hizmetini çağırmak için kullanılan WCF istemci kodu oluşturmak üzere bir hizmet meta verileri içeri aktarın.

 Bir WCF istemcisi oluşturmak için temel adımlar şunlardır:

1.  Hizmet kodu derleyin.

2.  WCF istemci proxy oluşturur.

3.  WCF istemci proxy örneği oluşturur.

WCF istemci proxy daha fazla bilgi için bkz: hizmet Model meta veri yardımcı Programracı (SvcUtil.exe) kullanarak el ile oluşturulabilir [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). WCF istemci proxy, Visual Studio içinden oluşturulabilir kullanarak **hizmet Başvurusu Ekle** özelliği. Hizmet yöntemlerden birini kullanarak WCF istemci proxy oluşturmak için çalıştırılması gerekir. Şirket içinde barındırılan hizmet ise, ana bilgisayar çalıştırmanız gerekir. Hizmet IIS'de barındırılıyorsa / WAS'da başka bir şey yapmanız gerekmez.

## <a name="servicemodel-metadata-utility-tool"></a>ServiceModel meta veri yardımcı Programracı
 [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) meta verilerinden kod oluşturma için bir komut satırı aracıdır. Aşağıdaki kullanım, temel bir Svcutil.exe komut bir örnektir.

```
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 Alternatif olarak, Web Hizmetleri Açıklama Dili (WSDL) ve XML Şeması Tanım Dili (XSD) dosyaları dosya sistemindeki ile Svcutil.exe kullanabilirsiniz.

```
Svcutil.exe <list of WSDL and XSD files on file system>
```

 İstemci uygulaması hizmetini çağırmak için kullanabileceğiniz WCF istemci kodu içeren bir kod dosyası sonucudur.

 Aracı, yapılandırma dosyalarını oluşturmak için de kullanabilirsiniz.

```
Svcutil.exe <file1 [,file2]>
```

 Yalnızca bir dosya adı verilir, çıktı dosyası adını olmasıdır. İki dosya adları verilirse, ardından ilk dosyanın içerikleri ile oluşturulan yapılandırmayı birleştirilmiş ve ikinci dosyaya yazılan bir giriş yapılandırma dosyasıdır. Yapılandırma hakkında daha fazla bilgi için bkz. [hizmetler için bağlamaları yapılandırma](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).

> [!IMPORTANT]
> Güvenli olmayan meta veri isteği herhangi bir güvenli ağ isteği yapan aynı şekilde belirli riskler neden: sizin kurduğunuz uç noktası olan bu söylüyor olduğundan emin değilseniz, aldığınız bilgiler kötü amaçlı bir hizmet meta verileri olabilir.

## <a name="add-service-reference-in-visual-studio"></a>Visual Studio'da hizmet Başvurusu Ekle

 Hizmet çalıştırarak, seçin ve WCF istemci proxy içeren projeye sağ tıklayın **Ekle** > **hizmet başvurusu**. İçinde **hizmet Başvurusu Ekle iletişim kutusu**, arayın ve istediğiniz hizmeti URL'sini yazın **Git** düğmesi. İletişim kutusu, belirttiğiniz adrese kullanılabilir hizmetlerin listesini görüntüler. Hizmet sözleşmeleri ve kullanılabilen işlemleri görmek için üretilen kod için bir ad belirtin ve tıklayın çift tıklayarak **Tamam** düğmesi.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği bir hizmet için oluşturulan bir hizmet sözleşmesini gösterir.

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

 ServiceModel meta veri yardımcı programı Aracı'nı ve **hizmet Başvurusu Ekle** Visual Studio'da aşağıdaki WCF istemci sınıfı oluşturur. Genel sınıfından devralan <xref:System.ServiceModel.ClientBase%601> sınıf ve uyguladığı `ICalculator` arabirimi. Araç ayrıca oluşturur `ICalculator` arabirimi (burada gösterilmiyor).

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

## <a name="using-the-wcf-client"></a>WCF istemcisi kullanarak
 WCF istemcisini kullanmak için WCF istemci örneği oluşturun ve ardından aşağıdaki kodda gösterildiği gibi kendi yöntemlerini çağırın.

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

## <a name="debugging-exceptions-thrown-by-a-client"></a>Bir istemci tarafından oluşturulan özel durumları hata ayıklama

Birçok özel durumlar bir WCF istemcisi tarafından oluşturulan bir özel hizmet tarafından kaynaklanır. Bu bazı örnekleri şunlardır:

-   <xref:System.Net.Sockets.SocketException>: Varolan bir bağlantı uzak konak tarafından zorla kapatıldı.

-   <xref:System.ServiceModel.CommunicationException>: Temel alınan bağlantı beklenmedik biçimde kapatıldı.

-   <xref:System.ServiceModel.CommunicationObjectAbortedException>: Yuva bağlantısı iptal edildi. Bu ileti, uzak ana bilgisayarda veya bir alt ağ kaynağı sorunu aşılması alma zaman aşımı işlenirken bir hata tarafından kaynaklanabilir.

Bu tür özel durumlar oluştuğunda, sorunu çözmek için en iyi hizmet tarafında izlemeyi ve var. hangi özel durum oluştu belirlemek için yoludur. İzleme hakkında daha fazla bilgi için bkz: [izleme](../../../docs/framework/wcf/diagnostics/tracing/index.md) ve [uygulamanız sorun giderme için izleme kullanarak](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="see-also"></a>Ayrıca Bkz.

- [Nasıl yapılır: İstemci Oluşturma](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [Nasıl yapılır: Çift Yönlü Sözleşme ile Hizmetlere Erişme](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Nasıl yapılır: Hizmet İşlemlerini Zaman Uyumsuz Olarak Çağırma](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [Nasıl yapılır: Tek Yönlü ve İstek-Yanıt Sözleşmeleriyle Hizmetlere Erişme](../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [Nasıl yapılır: WSE 3.0 Hizmetine Erişme](../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [Oluşturulmuş İstemci Kodlarını Anlama](../../../docs/framework/wcf/feature-details/understanding-generated-client-code.md)
- [Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [İstemci Çalışma Zamanı Davranışını Belirtme](../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [İstemci Davranışlarını Yapılandırma](../../../docs/framework/wcf/configuring-client-behaviors.md)
