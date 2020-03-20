---
title: ASMX Web Hizmetleri ile Birlikte Çalışma
ms.date: 03/30/2017
ms.assetid: a7c11f0a-9e68-4f03-a6b1-39cf478d1a89
ms.openlocfilehash: b5af8f15d38f730d2243c642d4623c0bc6e1343c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183582"
---
# <a name="interoperating-with-asmx-web-services"></a>ASMX Web Hizmetleri ile Birlikte Çalışma
Bu örnek, bir Windows Communication Foundation (WCF) istemci uygulamasının varolan bir ASMX Web hizmetiyle nasıl tümleştirilebildiğini göstermektedir.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Bu örnek, Internet Information Services (IIS) tarafından barındırılan bir istemci konsol programı (.exe) ve bir hizmet kitaplığından (.dll) oluşur. Hizmet, istek-yanıt iletişim iseni tanımlayan bir sözleşme uygulayan bir ASMX Web Hizmetidir. Hizmet matematik işlemlerini ortaya`Add` `Subtract`çıkarır `Multiply`( `Divide`, , , ve ). İstemci bir matematik işlemi için eşzamanlı isteklerde bulunmaz ve sonuç ile hizmet yanıtları. İstemci etkinliği konsol penceresinde görünür.  
  
 Aşağıdaki örnek kodda gösterilen ASMX Web hizmeti uygulaması, uygun sonucu hesaplar ve döndürür.  
  
```csharp  
[WebService(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class CalculatorService : System.Web.Services.WebService  
    {  
        [WebMethod]  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
        [WebMethod]  
        public double Subtract(double n1, double n2)  
        {  
            return n1 - n2;  
        }  
        [WebMethod]  
        public double Multiply(double n1, double n2)  
        {  
            return n1 * n2;  
        }  
        [WebMethod]  
        public double Divide(double n1, double n2)  
        {  
            return n1 / n2;  
        }  
    }  
```  
  
 Yapılandırıldıkça, hizmete aynı makinedeki bir istemci `http://localhost/servicemodelsamples/service.asmx` tarafından erişilebilir. Uzak makinelerdeki istemcilerin hizmete erişebilmek için localhost yerine nitelikli bir etki alanı adı belirtilmesi gerekir.  
  
 İletişim [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)tarafından oluşturulan bir istemci üzerinden yapılır. İstemci generatedClient.cs dosyada bulunur. Güncelleştirilmiş meta verileri almak için kullanıldığından, proxy kodunu oluşturmak için ASMX hizmetinin kullanılabilir olması gerekir. Yazılan proxy'yi oluşturmak için istemci dizinindeki bir komut isteminden aşağıdaki komutu çalıştırın.  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedClient.cs  
```  
  
 Oluşturulan istemciyi kullanarak, uygun adresi ve bağlamayı yapılandırarak bir hizmet bitiş noktasına erişebilirsiniz. Hizmet gibi istemci de iletişim kurmak için bitiş noktasını belirtmek için bir yapılandırma dosyası (App.config) kullanır. İstemci bitiş noktası yapılandırması, aşağıdaki örnek yapılandırmada gösterildiği gibi hizmet bitiş noktası, bağlama ve sözleşme için mutlak bir adresten oluşur.  
  
```xml  
<client>  
   <endpoint
      address="http://localhost/ServiceModelSamples/service.asmx"
      binding="basicHttpBinding"
      contract="Microsoft.ServiceModel.Samples.CalculatorServiceSoap" />  
</client>  
```  
  
 İstemci uygulaması oluşturulan istemcinin bir örneğini oluşturuyor. Oluşturulan istemci daha sonra hizmetle iletişim kurmak için kullanılabilir.  
  
```csharp  
// Create a client.  
CalculatorServiceSoapClient client = new CalculatorServiceSoapClient();  
  
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
  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\Interop\ASMX`  
