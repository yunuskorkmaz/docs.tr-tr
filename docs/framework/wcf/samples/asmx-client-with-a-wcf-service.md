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
# <a name="asmx-client-with-a-wcf-service"></a>WCF Hizmeti ile ASMX İstemcisi

Bu örnek, Windows Communication Foundation (WCF) kullanarak bir hizmetin nasıl oluşturulacağını ve sonra hizmetten bir ASMX istemcisi gibi WCF olmayan bir istemciden nasıl erişebileceğini gösterir.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

Bu örnek, Internet Information Services (IIS) tarafından barındırılan bir istemci konsol programından (. exe) ve hizmet kitaplığından (. dll) oluşur. Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular. Sözleşme, `ICalculator` matematik işlemlerini ( `Add` ,, `Subtract` `Multiply` ve) sunan arabirim tarafından tanımlanır `Divide` . ASMX istemcisi, bir matematik işlemine zaman uyumlu istek gönderir ve hizmet sonuçla yanıt verir.

Hizmet, `ICalculator` aşağıdaki kodda tanımlandığı şekilde bir sözleşme uygular.

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

<xref:System.Runtime.Serialization.DataContractSerializer>Ve <xref:System.Xml.Serialization.XmlSerializer> clr TÜRLERINI bir XML temsili ile eşleyin. , <xref:System.Runtime.Serialization.DataContractSerializer> Bazı XML temsillerini XmlSerializer 'dan farklı yorumlar. WSDL. exe gibi WCF olmayan proxy oluşturucuları, XmlSerializer kullanılırken daha kullanılabilir bir arabirim oluşturur. , <xref:System.ServiceModel.XmlSerializerFormatAttribute> `ICalculator` XMLSERIALIZER 'ın CLR türlerini XML 'e eşlemek için kullanıldığından emin olmak için arabirimine uygulanır. Hizmet uygulama, uygun sonucu hesaplar ve döndürür.

Hizmet, bir yapılandırma dosyası (Web. config) kullanılarak tanımlanan, hizmetle iletişim kurmak için tek bir uç nokta sunar. Uç nokta bir adres, bağlama ve bir anlaşmada oluşur. Hizmet, uç noktayı Internet Information Services (IIS) ana bilgisayarı tarafından belirtilen temel adreste kullanıma sunar. `binding`Özniteliği, aşağıdaki örnek yapılandırmada gösterildiği gıbı WS-ı BasicProfile 1,1 ile uyumlu olan SOAP 1,1 kullanarak http iletişimleri sağlayan BasicHttpBinding olarak ayarlanır.

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

ASMX istemcisi, Web Hizmetleri Açıklama Dili (WSDL) yardımcı programı (wsdl. exe) tarafından oluşturulan türü belirlenmiş bir ara sunucu kullanarak WCF hizmeti ile iletişim kurar. Yazılan ara sunucu generatedClient.cs dosyasında bulunur. WSDL yardımcı programı, belirtilen hizmet için meta verileri alır ve bir istemci tarafından iletişim kurmak için kullanılan bir ara sunucu oluşturur. Varsayılan olarak, çerçeve herhangi bir meta veri sunmaz. Proxy 'yi oluşturmak için gereken meta verileri göstermek için, [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) `httpGetEnabled` `True` Aşağıdaki yapılandırmada gösterildiği gibi bir özniteliğini eklemeli ve öğesini olarak ayarlamanız gerekir.

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

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.

3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.

> [!NOTE]
> Karmaşık veri türlerini geçirme ve döndürme hakkında daha fazla bilgi için bkz. [Windows Forms Istemcisinde veri bağlama](data-binding-in-a-windows-forms-client.md), bir [Windows Presentation Foundation istemcisinde veri bağlama](data-binding-in-a-wpf-client.md)ve [bir ASP.net istemcisinde veri bağlama](data-binding-in-an-aspnet-client.md)

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`
