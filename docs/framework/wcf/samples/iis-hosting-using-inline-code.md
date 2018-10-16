---
title: Satır İçi Kod Kullanarak IIS Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- Web hosted service
- IIS Hosting Using Inline Code Sample [Windows Communication Foundation]
ms.assetid: 56fe3687-a34b-4661-8e30-b33770f413fa
ms.openlocfilehash: ebaf524997ae4ed50b28aec53507f843f028bc31
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49348997"
---
# <a name="iis-hosting-using-inline-code"></a>Satır İçi Kod Kullanarak IIS Barındırma
Bu örnek, Internet Information Services (IIS) tarafından barındırılan bir hizmet ekleme işlemi gösterilmektedir hizmet kodu bulunduğu satır içi .svc dosyasında ve isteğe bağlı olarak derlenir. Hizmet kodu, uygulamanın \App_Code dizininde veya derlemesini \bin içinde dağıtılan derlenmiş doğrudan kaynak kodu dosyalarında de uygulanabilir. Bu örnek, bu teknikler göstermemiz gerekmez.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergeleri Bu konunun sonunda yer alır.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\InlineCode`  
  
 Örnek, bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygulayan normal bir hizmette gösterir. IIS'de barındırılan hizmet ve hizmet kod tamamen Service.svc dosyasında yer alır. Hizmet ana bilgisayarı-etkinleştirilir ve isteğe bağlı hizmetine gönderilen ilk ileti tarafından derlenmiş. Hiçbir ön derleme gerekli yoktur. Hizmet uygulayan bir `ICalculator` aşağıdaki kodda tanımlanan Sözleşme:  
  
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
  
 Hizmet uygulaması, hesaplar ve uygun sonucunu döndürür.  
  
```svc
<%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService" %>   
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
  
3.  Çözüm oluşturulduktan sonra ServiceModelSamples uygulamada ayarlamak için setup.bat çalıştırma [!INCLUDE[iisver](../../../../includes/iisver-md.md)]. ServiceModelSamples dizin artık olarak görünmesi gereken bir [!INCLUDE[iisver](../../../../includes/iisver-md.md)] uygulama.  
  
4.  Tek veya çoklu bilgisayar yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md). Bu hizmeti çağıran bir istemci uygulaması oluşturma hakkında bir örnek için bkz. [nasıl yapılır: istemci oluşturma](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AppFabric barındırma ve Kalıcılık örnekleri](https://go.microsoft.com/fwlink/?LinkId=193961)
