---
title: Gövdeye göre Yönlendir
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: 146baf806f4922f5e3ddd92a762772786e61d443
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594601"
---
# <a name="route-by-body"></a>Gövdeye göre Yönlendir
Bu örnek, herhangi bir SOAP eylemiyle ileti nesnelerini kabul eden bir hizmetin nasıl uygulanacağını gösterir. Bu örnek, bir Hesaplayıcı hizmeti uygulayan [kullanmaya](getting-started-sample.md) Başlarken hizmetini temel alır. Hizmet, `Calculate` <xref:System.ServiceModel.Channels.Message> istek parametresini kabul eden ve bir yanıt döndüren tek bir işlem uygular <xref:System.ServiceModel.Channels.Message> .  
  
 Bu örnekte, istemci bir konsol uygulaması (. exe) ve hizmet IIS 'de barındırılır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Örnek, gövde içeriğine göre ileti gönderimi gösterir. Yerleşik Windows Communication Foundation (WCF) hizmet modeli ileti gönderme mekanizması ileti eylemlerini temel alır. Ancak, eylem = "" ile tüm işlemlerini tanımlayan birçok mevcut Web hizmeti vardır. Eylem bilgilerine göre istek iletilerinin dağıtımını tutan WSDL 'yi temel alan bir hizmet derlemek olanaksızdır. Bu örnek, WSDL 'yi temel alan bir hizmet sözleşmesini gösterir (WSDL, örnekle birlikte gelen Service. wsdl ' de bulunur). Hizmet sözleşmesinin, [Başlarken](getting-started-sample.md)' de kullanılan bir hesap hesaplayıcısı. Ancak, `[OperationContract]` `Action=""` tüm işlemleri belirtir.  
  
```csharp  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples"),
                 XmlSerializerFormat, DispatchByBodyBehavior]  
    public interface ICalculator  
    {  
        [OperationContract(Action="")]  
        double Add(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Subtract(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Multiply(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Divide(double n1, double n2);  
    }  
```  
  
 Bir sözleşme verildiğinde, bir hizmet, `DispatchByBodyBehavior` işlemler arasında iletilerin dağıtılması için özel dağıtım davranışı gerektirir. Bu dağıtım davranışı, `DispatchByBodyElementOperationSelector` özel işlem seçiciyi, ilgili sarmalayıcı öğelerinin QName tarafından anahtarlanan işlem adlarından oluşan bir tabloyla başlatır. `DispatchByBodyElementOperationSelector`, gövdenin ilk alt öğesinin başlangıç etiketine bakar ve daha önce bahsedilen tabloyu kullanarak işlemi seçer.  
  
 İstemci, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)kullanılarak hizmet tarafından DıŞARıYA aktarılmış WSDL 'den otomatik olarak oluşturulan bir proxy kullanır.  
  
```console  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 Tüm işlemlerin eylemlerinin boş olması, otomatik olarak oluşturulan ara sunucu 'daki eylem parametreleri dışında, istemci kodunda hiçbir etkiye sahip değildir.  
  
 İstemci kodu birkaç hesaplama gerçekleştirir. Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
