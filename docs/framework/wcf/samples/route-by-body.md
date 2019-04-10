---
title: Gövdeye göre Yönlendir
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: b8a3f7785d7d59d8ad85d6dddde7fd6a04a12d63
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59320723"
---
# <a name="route-by-body"></a>Gövdeye göre Yönlendir
Bu örnek nasıl herhangi bir SOAP eylemi ileti nesneleri kabul eden bir hizmet uygulanacağı gösterir. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesaplayıcı hizmet uygulayan. Tek bir hizmeti uygulayan `Calculate` kabul eden bir işlem bir <xref:System.ServiceModel.Channels.Message> istek parametresi ve döndürür bir <xref:System.ServiceModel.Channels.Message> yanıt.  
  
 Bu örnekte, istemci bir konsol uygulaması (.exe) ve hizmet IIS'de barındırılan.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Örnek ileti gönderme gövdesi içeriğine göre gösterir. Yerleşik Windows Communication Foundation (WCF) hizmet modeli ileti gönderme mekanizması eylemleri iletide temel alır. Ancak, tüm eylem işlemlerini tanımlayan birçok mevcut Web hizmeti vardır = "". Eylem bilgi iletileri alan isteği gönderme tutar WSDL dayalı bir hizmet oluşturmak mümkün değildir. Bu örnek, WSDL (WSDL örnek ile birlikte sağlanan. Service.wsdl bulunur) temel alan bir hizmet sözleşmesini gösterir. Hizmet sözleşmesi hesaplayıcı kullanılanla benzer olan [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md). Ancak `[OperationContract]` belirtir `Action=""` tüm işlemler için.  
  
```  
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
  
 Bir sözleşme göz önünde bulundurulduğunda, bir hizmetin özel gönderme davranışı gerektirir `DispatchByBodyBehavior` işlemleri arasında dağıtılması iletilere izin verecek şekilde. Bu dağıtım davranışı başlatır `DispatchByBodyElementOperationSelector` işlem adları ilgili sarmalayıcı öğe bir QName tarafından Anahtarlanan bir tablo ile özel işlem Seçici. `DispatchByBodyElementOperationSelector` Gövde ilk alt öğenin başlangıç etiketi olarak görünür ve daha önce bahsedilen tabloyu kullanarak işlemi seçer.  
  
 İstemci hizmetini kullanarak dışarı WSDL gelen otomatik üretilmiş bir proxy kullanır [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 Tüm işlemlerin Eylemler boş olması, istemci kodu eylem parametrelerini otomatik olarak oluşturulan proxy'sinde dışında herhangi bir etkisi yoktur.  
  
 İstemci kodu birkaç hesaplamalar gerçekleştirir. Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
