---
title: Satır İçi Kod Kullanarak IIS Barındırma
ms.date: 03/30/2017
helpviewer_keywords:
- Web hosted service
- IIS Hosting Using Inline Code Sample [Windows Communication Foundation]
ms.assetid: 56fe3687-a34b-4661-8e30-b33770f413fa
ms.openlocfilehash: 41e19c318953d7e97eb5183c5a16a3780813f94c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559004"
---
# <a name="iis-hosting-using-inline-code"></a>Satır İçi Kod Kullanarak IIS Barındırma

Bu örnek Internet Information Services (IIS) tarafından barındırılan bir hizmetin nasıl uygulanacağını gösterir; burada hizmet kodu bir. svc dosyasında satır içinde bulunur ve isteğe bağlı olarak derlenir. Hizmet kodu Ayrıca, uygulamanın \ App_Code dizininde bulunan kaynak kodu dosyalarında doğrudan uygulanabilir veya \Bin. içinde dağıtılan derlemeye derlenmiş olabilir Bu örnek, bu teknikleri göstermez.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\InlineCode`

Örnek, istek-yanıt iletişim modelini tanımlayan bir sözleşmeyi uygulayan tipik bir hizmeti gösterir. Hizmet IIS 'de barındırılır ve hizmet kodu tamamen Service. svc dosyasında bulunur. Hizmet, ana bilgisayar etkinleştirilir ve hizmete gönderilen ilk ileti tarafından isteğe bağlı olarak derlenir. Ön derleme gerekli değildir. Hizmet `ICalculator` aşağıdaki kodda tanımlandığı şekilde bir sözleşme uygular:

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

Hizmet uygulama, uygun sonucu hesaplar ve döndürür.

`<%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService" %>`

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

3. Çözüm oluşturulduktan sonra, ServiceModelSamples uygulamasını IIS 7,0 ' de ayarlamak için setup.bat çalıştırın. ServiceModelSamples dizini artık bir IIS 7,0 uygulaması olarak görünmelidir.

4. Örneği tek veya bir çoklu bilgisayar yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin. Bu hizmeti çağırasağlayan bir istemci uygulaması oluşturma hakkında bir örnek için bkz. [nasıl yapılır: Istemci oluşturma](../how-to-create-a-wcf-client.md).

## <a name="see-also"></a>Ayrıca bkz.

- [AppFabric barındırma ve kalıcılık örnekleri](/previous-versions/appfabric/ff383418(v=azure.10))
