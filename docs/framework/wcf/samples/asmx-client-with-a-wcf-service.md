---
title: WCF Hizmeti ile ASMX İstemcisi
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 26fc56ae465c2792f895f08a8e55577d3b74b97d
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="asmx-client-with-a-wcf-service"></a>WCF Hizmeti ile ASMX İstemcisi
Bu örnek kullanarak bir hizmet oluşturmak nasıl gösterir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve ardından hizmet olmayan bir erişim[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASMX istemcisi gibi istemci.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Bu örnek, bir istemci konsol program (.exe) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı (.dll) oluşur. Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular. Anlaşma tarafından tanımlanan `ICalculator` matematik işlemleri kullanıma sunan arabirim (`Add`, `Subtract`, `Multiply`, ve `Divide`). ASMX istemcisi matematik işlemi ve hizmet yanıt sonucu ile eşzamanlı isteği yapar.  
  
 Hizmet uygulayan bir `ICalculator` aşağıdaki kodda tanımlanan sözleşme.  
  
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
  
 <xref:System.Runtime.Serialization.DataContractSerializer> Ve <xref:System.Xml.Serialization.XmlSerializer> bir XML temsili CLR Türleri eşleyin. <xref:System.Runtime.Serialization.DataContractSerializer> Bazı XML temsili XmlSerializer farklı yorumlar. Olmayan[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Wsdl.exe gibi proxy oluşturucuları XmlSerializer kullanıldığında daha kullanışlı bir arabirim oluşturur. <xref:System.ServiceModel.XmlSerializerFormatAttribute> Uygulanan `ICalculator` XmlSerializer CLR türlerini XML'e eşlemek için kullanıldığından emin olmak için arabirim. Hizmet uygulaması hesaplar ve uygun sonucunu döndürür.  
  
 Hizmet yapılandırma dosyasında (Web.config) kullanılarak tanımlanmış hizmet ile iletişim için tek bir uç noktasını kullanıma sunar. Uç nokta bir adresi, bağlama ve bir sözleşme oluşur. Hizmet Internet Information Services (IIS) ana bilgisayar tarafından sağlanan temel adresindeki uç noktasını kullanıma sunar. `binding` Özniteliği WS ile uyumlu SOAP 1.1 kullanarak HTTP iletişimi sağlayan basicHttpBinding ayarlanmış-ı BasicProfile aşağıdaki örnek yapılandırmada gösterildiği gibi 1.1.  
  
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
  
 ASMX istemcisi ile iletişim kurar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Hizmetleri Açıklama Dili (WSDL) yardımcı programı (Wsdl.exe) tarafından oluşturulan belirtilmiş bir proxy kullanarak hizmet. Yazılı proxy dosya generatedClient.cs içinde yer alır. WSDL yardımcı programı, belirtilen hizmet için meta verilerini alır ve iletişim kurmak için bir istemci tarafından kullanılmak üzere yazılmış bir proxy oluşturur. Varsayılan olarak, herhangi bir meta veri framework göstermiyor. Proxy oluşturmak için gereken meta verilerini kullanıma sunmak için eklemelisiniz bir [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) ve kendi `httpGetEnabled` özniteliğini `True` aşağıdaki yapılandırmada gösterildiği gibi.  
  
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
  
 Yazılı proxy oluşturmak için istemci dizininde bir komut isteminden aşağıdaki komutu çalıştırın.  
  
```console  
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl  
```  
  
 Oluşturulan yazılan proxy kullanarak, istemci uygun adresi yapılandırarak verilen hizmet uç noktası erişebilir. İstemci bir yapılandırma dosyasına (App.config) ile iletişim kurmak için uç nokta belirlemek için kullanır.  
  
```xml  
<appSettings>  
  <add key="CalculatorServiceAddress"   
       value="http://localhost/ServiceModelSamples/service.svc"/>  
</appSettings>  
```  
  
 İstemci uygulaması hizmetiyle iletişim kurulurken başlamak için yazılan proxy örneğini oluşturur.  
  
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
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Türleri ve karmaşık veri döndüren geçirme hakkında daha fazla bilgi için bkz: [bir Windows Forms istemcisinde veri bağlama](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [bir Windows Presentation Foundation istemcisinde veri bağlama](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md), ve [veri Bir ASP.NET istemcisinde bağlama](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`  
  
## <a name="see-also"></a>Ayrıca Bkz.
