---
title: Başlarken Örneği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
ms.openlocfilehash: 59f9edf67c03fb7d8670058eca8ea672a6f64c02
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837876"
---
# <a name="getting-started-sample"></a>Başlarken Örneği

Başlarken örneği, Windows Communication Foundation (WCF) kullanılarak tipik bir hizmetin ve tipik bir istemcinin nasıl uygulanacağını gösterir. Bu örnek, diğer tüm temel teknoloji örnekleri için temeldir.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\GettingStarted\GettingStarted`

Hizmet, bir hizmet sözleşmesinde gerçekleştirdiği işlemleri, genel olarak meta veri olarak açığa çıkardığı şekilde açıklar. Hizmet ayrıca işlemleri uygulamak için kodu içerir.

İstemci, hizmet sözleşmesinin bir tanımını ve hizmete erişmek için bir proxy sınıfı içerir. Proxy kodu, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)kullanılarak hizmet meta verilerinden oluşturulur.

Windows Vista 'da, hizmet Windows etkinleştirme hizmeti 'nde (WAS) barındırılır. [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ve [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Internet Information Services (IIS) ve ASP.NET tarafından barındırılır. Bir hizmetin IIS 'de barındırılması, ilk kez erişildiğinde hizmetin otomatik olarak etkinleştirilmesini sağlar.

> [!NOTE]
> Hizmeti IIS yerine bir konsol uygulamasında barındıran bir örnekle çalışmaya başlamak isterseniz, [self-Host](../../../../docs/framework/wcf/samples/self-host.md) örneğine bakın.

Hizmet ve istemci, dağıtım sırasında esneklik sağlayan yapılandırma dosyası ayarları 'nda erişim ayrıntılarını belirler. Bu, bir adresi, bağlamayı ve sözleşmeyi belirten bir uç nokta tanımı içerir. Bağlama, hizmetin nasıl erişileceğini gösteren taşıma ve güvenlik ayrıntılarını belirtir.

Hizmet, meta verilerini yayımlamak için bir çalışma zamanı davranışı yapılandırır.

Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular. Sözleşme, matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) sunan `ICalculator` arabirimi tarafından tanımlanır. İstemci belirli bir matematik işlemine istek yapar ve hizmet sonuçla yanıt verir. Hizmet aşağıdaki kodda tanımlanan bir `ICalculator` sözleşme uygular.

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

Hizmet uygulamasının aşağıdaki örnek kodda gösterildiği gibi, uygun sonucu hesaplar ve döndürür.

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

Hizmet, aşağıdaki örnek yapılandırmada gösterildiği gibi, bir yapılandırma dosyası (Web. config) kullanılarak tanımlanan hizmetle iletişim kurmak için bir uç nokta sunar.

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

Hizmet, uç noktayı IIS veya WAS ana bilgisayar tarafından belirtilen temel adreste kullanıma sunar. Bağlama, adresleme ve güvenlik için HTTP iletişimi ve standart Web hizmeti protokolleri sağlayan bir standart <xref:System.ServiceModel.WSHttpBinding>ile yapılandırılır. Sözleşme, hizmet tarafından uygulanan `ICalculator`.

Yapılandırıldığı gibi, hizmete aynı bilgisayardaki bir istemci tarafından `http://localhost/servicemodelsamples/service.svc` erişilebilir. Uzak bilgisayarlardaki istemcilerin hizmete erişmesi için localhost yerine tam etki alanı adı belirtilmelidir.

Çerçeve varsayılan olarak meta verileri kullanıma sunmaz. Bu nedenle hizmet, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> açar ve `http://localhost/servicemodelsamples/service.svc/mex`bir meta veri değişimi (MEX) uç noktasını kullanıma sunar. Aşağıdaki yapılandırma bunu gösterir.

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

İstemci, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)tarafından oluşturulan bir istemci sınıfını kullanarak belirli bir sözleşme türünü kullanarak iletişim kurar. Bu oluşturulan istemci, generatedClient.cs veya generatedClient. vb dosyasında bulunur. Bu yardımcı program belirli bir hizmet için meta verileri alır ve belirli bir sözleşme türünü kullanarak iletişim kurmak için istemci uygulaması tarafından kullanılmak üzere bir istemci oluşturur. Hizmet güncelleştirilmiş meta verileri almak için kullanıldığından, istemci kodunu oluşturmak için barındırılan hizmetin kullanılabilir olması gerekir.

 Türü belirtilmiş proxy 'yi oluşturmak için istemci dizininde SDK komut isteminden aşağıdaki komutu çalıştırın:

```console
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
```

Visual Basic ' de istemci oluşturmak için SDK komut isteminden aşağıdakini yazın:

`Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`

İstemci, oluşturulan istemciyi kullanarak, uygun adresi ve bağlamayı yapılandırarak belirli bir hizmet uç noktasına erişebilir. Hizmet gibi istemci, iletişim kurmak istediği uç noktayı belirtmek için bir yapılandırma dosyası (App. config) kullanır. İstemci uç noktası yapılandırması, aşağıdaki örnekte gösterildiği gibi hizmet uç noktası, bağlama ve sözleşme için mutlak bir adresten oluşur.

```xaml
<client>
     <endpoint
         address="http://localhost/servicemodelsamples/service.svc"
         binding="wsHttpBinding"
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />
</client>
```

İstemci uygulama, istemciyi başlatır ve aşağıdaki örnek kodda gösterildiği gibi hizmet ile iletişim kurmaya başlamak için türü belirlenmiş arabirimi kullanır.

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

Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.

```output
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

Başlarken örneği, bir hizmet ve istemci oluşturmanın standart yolunu gösterir. Belirli ürün özelliklerini göstermek için bu örnekteki diğer [temel](../../../../docs/framework/wcf/samples/basic-sample.md) yapı.

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.

3. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [Nasıl yapılır: IIS'de WCF Hizmeti Barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
