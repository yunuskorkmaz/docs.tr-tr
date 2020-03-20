---
title: Gövdeye göre Yönlendir
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: c3f4b19e646a6a9716d2264a3969b339208c60a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144194"
---
# <a name="route-by-body"></a>Gövdeye göre Yönlendir
Bu örnek, herhangi bir SOAP eylemi ile ileti nesneleri kabul eden bir hizmetin nasıl uygulanacağını gösterir. Bu örnek, bir hesap makinesi hizmeti uygulayan [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md) dayanır. Hizmet, istek `Calculate` <xref:System.ServiceModel.Channels.Message> parametresini kabul eden ve yanıt <xref:System.ServiceModel.Channels.Message> döndüren tek bir işlem uygular.  
  
 Bu örnekte, istemci bir konsol uygulamasıdır (.exe) ve hizmet IIS'de barındırılır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Örnek, gövde içeriğine dayalı ileti göndermeyi gösterir. Yerleşik Windows Communication Foundation (WCF) hizmet modeli ileti gönderme mekanizması ileti Eylemleri'ni temel alır. Ancak, tüm işlemlerini Action="" ile tanımlayan birçok varolan Web hizmeti vardır. Eylem bilgilerine dayalı istek iletileri göndermeye devam eden WSDL tabanlı bir hizmet oluşturmak mümkün değildir. Bu örnek, WSDL'yi temel alan bir hizmet sözleşmesi gösterir (WSDL, örnekle birlikte service.wsdl'de bulunur). Hizmet sözleşmesi, [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)kullanılana benzer olan Hesap Makinesi'dir. Ancak `[OperationContract]` tüm işlemler `Action=""` için belirtir.  
  
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
  
 Bir sözleşme göz önüne alındığında, `DispatchByBodyBehavior` bir hizmet iletilerin işlemler arasında gönderilmesine izin vermek için özel gönderme davranışı gerektirir. Bu gönderme davranışı, `DispatchByBodyElementOperationSelector` ilgili sarıcı öğelerinin QName tarafından anahtarlanmış işlem adlarının bir tablosuyla özel işlem seçicisini devreye ait hale sağlar. `DispatchByBodyElementOperationSelector`Gövdenin ilk çocuğunun başlangıç etiketine bakar ve daha önce bahsedilen tabloyu kullanarak işlemi seçer.  
  
 İstemci [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)kullanarak hizmet tarafından dışa aktarılan WSDL'den otomatik olarak oluşturulan bir proxy kullanır.  
  
```console  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 Otomatik oluşturulan proxy'deki Eylem parametreleri dışında, tüm işlemlerin eylemlerinin boş olması istemci kodu üzerinde hiçbir etkiye sahip değildir.  
  
 İstemci kodu çeşitli hesaplamalar gerçekleştirir. Örneği çalıştırdığınızda, işlem istekleri ve yanıtları istemci konsol penceresinde görüntülenir. İstemciyi kapatmak için istemci penceresinde ENTER tuşuna basın.  
  
```console
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
