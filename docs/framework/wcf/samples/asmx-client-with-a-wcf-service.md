---
title: WCF Hizmeti ile ASMX İstemcisi
ms.date: 03/30/2017
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
ms.openlocfilehash: 8b8ebebbcb2c95555605ebd1d8e164b8babb7e3e
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347844"
---
# <a name="asmx-client-with-a-wcf-service"></a>WCF Hizmeti ile ASMX İstemcisi
Bu örnek, Windows Communication Foundation (WCF) kullanan bir hizmet oluşturmak ve ardından ASMX istemcisi gibi bir WCF olmayan istemciden hizmete erişmek nasıl gösterir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Bu örnek, bir istemci konsol program (.exe) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı (.dll) oluşur. Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular. Anlaşma tarafından tanımlanan `ICalculator` matematik işlemlerinden sunan arabirimi (`Add`, `Subtract`, `Multiply`, ve `Divide`). ASMX istemcisi bir matematik işlemi ve hizmet yanıt sonucu zaman uyumlu istekleri yapar.  
  
 Hizmet uygulayan bir `ICalculator` aşağıdaki kodda tanımlanan sözleşme.  
  
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
  
 <xref:System.Runtime.Serialization.DataContractSerializer> Ve <xref:System.Xml.Serialization.XmlSerializer> CLR Türleri eşleştirmek için bir XML gösterimi. <xref:System.Runtime.Serialization.DataContractSerializer> Bazı XML gösterimleri XmlSerializer tarafından farklı olarak yorumlar. XmlSerializer kullanıldığında gibi Wsdl.exe, WCF olmayan proxy'si oluşturucuları daha kullanışlı bir arabirim oluşturur. <xref:System.ServiceModel.XmlSerializerFormatAttribute> Uygulanan `ICalculator` arabirim, XmlSerializer CLR türleri için XML eşleme için kullanıldığından emin olmak için. Hizmet uygulaması, hesaplar ve uygun sonucunu döndürür.  
  
 Hizmet yapılandırma dosyasında (Web.config) kullanılarak tanımlanmış hizmet ile iletişim kurmak için tek bir uç noktayı kullanıma sunar. Uç nokta, adres, bağlama ve bir sözleşme oluşur. Hizmet, Internet Information Services (IIS) ana bilgisayar tarafından sağlanan taban adresinde uç noktasını kullanıma sunar. `binding` Özniteliği WS ile uyumlu olan SOAP 1.1 kullanarak HTTP iletişimi sağlayan basicHttpBinding kümesine-ı BasicProfile aşağıdaki örnek yapılandırmada gösterildiği 1.1.  
  
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
  
 Web Hizmetleri Açıklama Dili (WSDL) yardımcı programı (Wsdl.exe) tarafından üretilen türü belirtilmiş bir proxy kullanarak WCF Hizmeti ile ASMX istemcisi iletişim kurar. Türü belirtilmiş bir proxy dosya generatedClient.cs içinde yer alır. WSDL yardımcı programı, belirtilen hizmet için meta verileri alır ve iletişim kurmak için bir istemci tarafından kullanım için türü belirtilmiş bir proxy oluşturur. Varsayılan olarak, framework meta verileri kullanıma sunmuyor. Proxy oluşturmak için gereken meta verileri kullanıma sunmak için eklemelisiniz bir [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) ve kendi `httpGetEnabled` özniteliğini `True` aşağıdaki yapılandırmayı gösterildiği gibi.  
  
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
  
 Türü belirtilmiş bir proxy oluşturmak için istemci dizininde bir komut isteminden aşağıdaki komutu çalıştırın.  
  
```console  
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl  
```  
  
 Üretilen türü belirtilmiş bir proxy kullanarak istemci uygun adresi yapılandırarak belirli hizmet uç noktası erişebilirsiniz. İstemci ile iletişim kurmak için uç nokta belirtmek için bir yapılandırma dosyası (App.config) kullanır.  
  
```xml  
<appSettings>  
  <add key="CalculatorServiceAddress"   
       value="http://localhost/ServiceModelSamples/service.svc"/>  
</appSettings>  
```  
  
 İstemci uygulama hizmeti ile iletişim başlatmak için türü belirtilmiş bir proxy örneği oluşturur.  
  
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
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
```console 
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Türleri ve karmaşık veri döndüren geçirme hakkında daha fazla bilgi için bkz: [bir Windows Forms istemcisinde veri bağlama](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [veri bağlama bir Windows Presentation Foundation istemcisi](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md), ve [veri Bir ASP.NET istemcisinde bağlama](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`  
  
## <a name="see-also"></a>Ayrıca Bkz.
