---
title: WCF Hizmeti ile ASMX İstemcisi
ms.date: 03/30/2017
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
ms.openlocfilehash: a560650dba250d1ee4f0b959ead70a2915c9997f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716132"
---
# <a name="asmx-client-with-a-wcf-service"></a>WCF Hizmeti ile ASMX İstemcisi

Bu örnek, Windows Communication Foundation (WCF) kullanarak bir hizmetin nasıl oluşturulacağını ve sonra hizmetten bir ASMX istemcisi gibi WCF olmayan bir istemciden nasıl erişebileceğini gösterir.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Bu örnek, Internet Information Services (IIS) tarafından barındırılan bir istemci konsol programından (. exe) ve hizmet kitaplığından (. dll) oluşur. Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular. Sözleşme, matematik işlemlerini (`Add`, `Subtract`, `Multiply`ve `Divide`) sunan `ICalculator` arabirimi tarafından tanımlanır. ASMX istemcisi, bir matematik işlemine zaman uyumlu istek gönderir ve hizmet sonuçla yanıt verir.

Hizmet, aşağıdaki kodda tanımlandığı şekilde bir `ICalculator` sözleşmesi uygular.

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

<xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Xml.Serialization.XmlSerializer> CLR türlerini bir XML gösterimine eşleyin. <xref:System.Runtime.Serialization.DataContractSerializer>, bazı XML temsillerini XmlSerializer 'dan farklı yorumlar. WSDL. exe gibi WCF olmayan proxy oluşturucuları, XmlSerializer kullanılırken daha kullanılabilir bir arabirim oluşturur. <xref:System.ServiceModel.XmlSerializerFormatAttribute>, XmlSerializer 'ın CLR türlerini XML 'e eşlemek için kullanıldığından emin olmak için `ICalculator` arabirimine uygulanır. Hizmet uygulama, uygun sonucu hesaplar ve döndürür.

Hizmet, bir yapılandırma dosyası (Web. config) kullanılarak tanımlanan, hizmetle iletişim kurmak için tek bir uç nokta sunar. Uç nokta bir adres, bağlama ve bir anlaşmada oluşur. Hizmet, uç noktayı Internet Information Services (IIS) ana bilgisayarı tarafından belirtilen temel adreste kullanıma sunar. `binding` özniteliği, aşağıdaki örnek yapılandırmada gösterildiği gibi WS-ı BasicProfile 1,1 ile uyumlu olan SOAP 1,1 kullanılarak HTTP iletişimleri sağlayan basicHttpBinding olarak ayarlanır.

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

ASMX istemcisi, Web Hizmetleri Açıklama Dili (WSDL) yardımcı programı (wsdl. exe) tarafından oluşturulan türü belirlenmiş bir ara sunucu kullanarak WCF hizmeti ile iletişim kurar. Yazılan ara sunucu generatedClient.cs dosyasında bulunur. WSDL yardımcı programı, belirtilen hizmet için meta verileri alır ve bir istemci tarafından iletişim kurmak için kullanılan bir ara sunucu oluşturur. Varsayılan olarak, çerçeve herhangi bir meta veri sunmaz. Proxy oluşturmak için gereken meta verileri göstermek için, bir [\<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) eklemeli ve `httpGetEnabled` özniteliğini aşağıdaki yapılandırmada gösterildiği gibi `True` olarak ayarlamanız gerekir.

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

Yazılan proxy 'yi oluşturmak için istemci dizinindeki bir komut isteminden aşağıdaki komutu çalıştırın.

```console
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl
```

Oluşturulan tür ara sunucusunu kullanarak istemci, uygun adresi yapılandırarak belirli bir hizmet uç noktasına erişebilir. İstemci, iletişim kuracak uç noktayı belirtmek için bir yapılandırma dosyası (App. config) kullanır.

```xml
<appSettings>
  <add key="CalculatorServiceAddress"
       value="http://localhost/ServiceModelSamples/service.svc"/>
</appSettings>
```

İstemci uygulama, hizmetle iletişim kurmaya başlamak için türü belirlenmiş proxy 'nin bir örneğini oluşturur.

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

Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.

3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.

> [!NOTE]
> Karmaşık veri türlerini geçirme ve döndürme hakkında daha fazla bilgi için bkz. [Windows Forms Istemcisinde veri bağlama](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), bir [Windows Presentation Foundation istemcisinde veri bağlama](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md)ve [bir ASP.net istemcisinde veri bağlama](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`
