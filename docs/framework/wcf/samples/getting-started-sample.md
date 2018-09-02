---
title: Başlarken Örneği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
ms.openlocfilehash: dda11511904d452a3a5101417f8ab8a33c00204f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43469914"
---
# <a name="getting-started-sample"></a>Başlarken Örneği
Kullanmaya başlama örneği, tipik bir hizmet ve Windows Communication Foundation (WCF) kullanarak tipik bir istemci uygulama gösterilmiştir. Bu örnek diğer tüm temel teknoloji örnekleri temelini oluşturur.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\GettingStarted\GettingStarted`  
  
 Hizmet olarak meta veriler genel olarak kullanıma sunduğu bir hizmet sözleşmesinde gerçekleştirdiği işlemler açıklanır. Hizmet işlemleri uygulayan bir kod da içerir.  
  
 İstemci, hizmet sözleşmesi ve hizmete erişmek için bir proxy sınıfı bir tanım içeriyor. Proxy kodu kullanarak hizmet meta verileri oluşturulan [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 Üzerinde [!INCLUDE[wv](../../../../includes/wv-md.md)], hizmet Windows Etkinleştirme Hizmeti (WAS) barındırılır. Üzerinde [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ve [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Internet Information Services (IIS) ve ASP.NET tarafından barındırılır. Bir IIS ya da WAS hizmetinde barındırma ilk kez eriştiğinde, otomatik olarak etkinleştirilecek hizmeti sağlar.  
  
> [!NOTE]
>  IIS yerine bir konsol uygulamasındaki hizmet barındıran bir örnek ile kullanmaya başlamak tercih ediyorsanız, bkz: [barındırma](../../../../docs/framework/wcf/samples/self-host.md) örnek.  
  
 İstemci ve hizmet dağıtım sırasında esneklik yapılandırma dosyası ayarlarının erişim ayrıntılarını belirtin. Bu, bir adresi, bağlama ve sözleşme belirten bir uç nokta tanımı içerir. Bağlama için nasıl erişilmesini hizmetidir aktarım veya güvenlik ayrıntılarını belirtir.  
  
 Hizmet meta verilerini yayımlamak için bir çalışma zamanı davranışını yapılandırır.  
  
 Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular. Anlaşma tarafından tanımlanan `ICalculator` matematik işlemlerinden sunan arabirimi (ekleme, çıkarma, çarpma ve bölme). İstemci isteklerini belirli matematik işlemi ve sonuç ile hizmet verilen yanıtları yapar. Hizmet uygulayan bir `ICalculator` aşağıdaki kod içinde tanımlanan sözleşme.  
  
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
  
 Hizmet uygulaması, hesaplar ve aşağıdaki örnekte gösterildiği gibi uygun bir sonuç döndürür.  
  
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
  
 Hizmet, örnek yapılandırma (Web.config), aşağıda gösterildiği gibi bir yapılandırma dosyası kullanılarak tanımlanmış hizmet ile iletişim kurmak için bir uç noktasını kullanıma sunar.  
  
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
  
 Hizmet, IIS veya WAS ana bilgisayar tarafından sağlanan taban adresinde uç noktasını kullanıma sunar. Bir standart yapılandırılmış bağlama <xref:System.ServiceModel.WSHttpBinding>, sağlayan HTTP iletişimi ve standart Web hizmeti protokolleri adresleme ve güvenlik için. Sözleşme `ICalculator` hizmeti tarafından uygulanan.  
  
 Adresinden yapılandırıldığı gibi hizmet erişilebilen http://localhost/servicemodelsamples/service.svc aynı bilgisayarda bir istemci tarafından. Uzak computersto erişimi hizmet istemciler için localhost yerine bir tam etki alanı adı belirtilmelidir.  
  
 Framework meta verileri varsayılan olarak kullanıma sunmuyor. Bu nedenle, hizmet açar <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ve bir meta veri değişimi (MEX) uç noktada ortaya çıkaran http://localhost/servicemodelsamples/service.svc/mex. Aşağıdaki yapılandırmayı bu gösterir.  
  
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
  
 İstemci tarafından oluşturulan istemci sınıfını kullanarak belirtilen anlaşma türü kullanarak iletişim kurar [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Bu oluşturulan istemci dosyası generatedClient.cs veya generatedClient.vb yer alır. Bu yardımcı programı, verili bir hizmet için meta verileri alır ve kullanmak için bir istemci istemci uygulaması tarafından verilen anlaşma türü kullanarak iletişim kurmaya oluşturur. Barındırılan hizmet, hizmet güncelleştirilmiş meta verilerini almak için kullanıldığından istemci kodu oluşturmak kullanılabilir olmalıdır.  
  
 Türü belirtilmiş bir proxy oluşturmak için istemci dizinindeki SDK komut isteminden aşağıdaki komutu çalıştırın:  
  
```  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
```  
  
 Visual Basic türü SDK komut isteminden aşağıdaki istemci oluşturmak için:  
  
 `Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`  
  
 Oluşturulan istemciyi kullanarak istemci belirli bir hizmet uç noktası uygun adresi yapılandırma ve bağlama tarafından erişebilir. Hizmet gibi istemci uç noktası ile iletişim kurmak istediği belirtmek için bir yapılandırma dosyası (App.config) kullanır. Aşağıdaki örnekte gösterildiği gibi bir mutlak bir adres için hizmet uç noktası, bağlama ve Sözleşme, istemci uç nokta yapılandırması oluşur.  
  
```xaml  
<client>  
     <endpoint  
         address="http://localhost/servicemodelsamples/service.svc"   
         binding="wsHttpBinding"   
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />  
</client>  
```  
  
 İstemci uygulaması, istemci başlatır ve aşağıdaki örnekte gösterildiği gibi hizmet ile iletişim başlatmak için belirlenmiş arabirimini kullanır.  
  
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
  
 Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 Kullanmaya başlama örneği, hizmet ve istemci oluşturmak için standart bir yolunu gösterir. Diğer [temel](../../../../docs/framework/wcf/samples/basic-sample.md) belirli bir ürün özellikleri göstermek için bu örneği derlemek.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Yönetilen Bir Uygulamada Bir WCF Hizmeti Barındırma](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [Nasıl yapılır: IIS'de WCF Hizmeti Barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
