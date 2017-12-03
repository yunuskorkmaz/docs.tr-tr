---
title: "Başlarken Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
caps.latest.revision: "60"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a5ff6af234fabf278c84a3487b9f65217d84f6e4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="getting-started-sample"></a>Başlarken Örneği
Başlarken örneği tipik bir hizmet ve kullanarak tipik bir istemci uygulama gösterilmiştir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Bu örnek diğer tüm temel teknoloji örnekleri temelini oluşturur.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\GettingStarted\GettingStarted`  
  
 Hizmet meta veri genel olarak kullanıma sunan bir hizmet sözleşmesinde gerçekleştirdiği işlemleri açıklanır. Hizmet ayrıca işlemleri uygulamak için kod içerir.  
  
 İstemci, hizmet sözleşmesini ve hizmete erişim için bir proxy sınıf tanımını içerir. Kullanarak hizmeti meta veri oluşturulan proxy kodda [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)], Windows Etkinleştirme Hizmeti (WAS) barındırılan hizmetin. Üzerinde [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ve [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Internet Information Services (IIS) ve ASP.NET tarafından barındırılır. IIS ya da WAS hizmetinde barındırma ilk kez eriştiğinde, otomatik olarak etkinleştirilecek hizmeti sağlar.  
  
> [!NOTE]
>  IIS yerine bir konsol uygulamasında hizmet barındıran bir örnek kullanmaya başlamak tercih ederseniz, bkz: [kendini barındırma](../../../../docs/framework/wcf/samples/self-host.md) örnek.  
  
 Hizmet ve istemci erişim ayrıntılarını dağıtım zamanında esnekliği yapılandırma dosyası ayarları belirtin. Bu, yalnızca bir adresi, bağlama ve sözleşme belirten bir uç nokta tanımı içerir. Bağlama nasıl erişilecek hizmetidir için taşıma ve güvenlik ayrıntılarını belirtir.  
  
 Hizmet meta verilerini yayımlamak için bir çalışma zamanı davranışını yapılandırır.  
  
 Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular. Anlaşma tarafından tanımlanan `ICalculator` matematik işlemleri kullanıma sunan arabirim (eklemek, çıkarma, çarpma ve bölme). İstemci isteklerini belirli matematik işlemi ve sonuç ile hizmet yanıtları yapar. Hizmet uygulayan bir `ICalculator` aşağıdaki kodda tanımlanan sözleşme.  
  
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
  
 Hizmet uygulaması hesaplar ve aşağıdaki örnek kodda gösterildiği gibi uygun sonucunu döndürür.  
  
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
  
 Hizmet (Web.config) aşağıdaki gösterildiği gibi örnek bir yapılandırma bir yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim için bir uç noktasını kullanıma sunar.  
  
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
  
 Hizmet IIS ya da WAS ana bilgisayarı tarafından sağlanan temel adresindeki uç noktasını kullanıma sunar. Bağlama ile standart bir yapılandırılmış <xref:System.ServiceModel.WSHttpBinding>, hangi HTTP iletişimi ve standart Web hizmeti protokolleri adresleme ve güvenlik için sağlar. Sözleşme `ICalculator` hizmeti tarafından uygulanır.  
  
 Yapılandırıldığı şekilde hizmet http://localhost/servicemodelsamples/service.svc aynı bilgisayara bir istemci tarafından erişilebilir. Uzak computersto erişim hizmet istemciler için localhost yerine bir tam etki alanı adı belirtilmelidir.  
  
 Framework meta verileri varsayılan olarak kullanıma sunmuyor. Bu nedenle, hizmetin açar <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ve http://localhost/servicemodelsamples/service.svc/mex konumunda bir meta veri değişimi (MEX) uç noktasını kullanıma sunar. Aşağıdaki yapılandırma bu gösterir.  
  
```xaml  
<system.serviceModel>  
  <services>  
    <service   
        name="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      ...  
      <!-- the mex endpoint is explosed at  
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
  
 İstemci tarafından oluşturulan bir istemci sınıfını kullanarak verilen sözleşme türünü kullanarak iletişim kurar [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Bu oluşturulan istemci dosya generatedClient.cs veya generatedClient.vb yer alır. Bu yardımcı program belirli bir hizmeti için meta verilerini alır ve belirli sözleşme türünü kullanarak iletişim kurmak için istemci uygulaması tarafından kullanım için bir istemci oluşturur. Hizmeti güncelleştirilmiş meta verilerini almak için kullanılır çünkü barındırılan hizmeti istemci kodunu oluşturmak kullanılabilir olması gerekir.  
  
 Yazılı proxy oluşturmak için istemci dizinindeki SDK komut isteminden aşağıdaki komutu çalıştırın:  
  
```  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
```  
  
 Visual Basic tür SDK komut isteminden aşağıdaki istemci oluşturmak için:  
  
 `Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`  
  
 Oluşturulan istemciyi kullanarak, istemci belirli hizmet uç noktası uygun adresi yapılandırma ve bağlama tarafından erişebilir. Gibi hizmet, istemci ile iletişim kurmak istediği uç noktası belirtmek için bir yapılandırma dosyasına (App.config) kullanır. Aşağıdaki örnekte gösterildiği gibi hizmet uç noktası, bağlama ve sözleşme için mutlak bir adres, istemci uç nokta yapılandırması oluşur.  
  
```xaml  
<client>  
     <endpoint  
         address="http://localhost/servicemodelsamples/service.svc"   
         binding="wsHttpBinding"   
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />  
</client>  
```  
  
 İstemci uygulaması istemci başlatır ve aşağıdaki örnek kodda gösterildiği gibi hizmet ile iletişim başlamak için yazılan arabirimini kullanır.  
  
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
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Başlarken örneği bir hizmet ve istemci oluşturmanın standart yolu gösterir. Diğer [temel](../../../../docs/framework/wcf/samples/basic-sample.md) belirli ürün özellikleri göstermek için bu örneği derlemek.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz bilgisayar yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: yönetilen bir uygulamada bir WCF Hizmeti barındırma](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [Nasıl yapılır: IIS'de WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
