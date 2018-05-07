---
title: Gövdeye göre Yönlendir
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: e9a0c947a1dd7ac2a6c7af74baaa072aae67358c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="route-by-body"></a>Gövdeye göre Yönlendir
Bu örnek, tüm SOAP eylemi ileti nesneleriyle kabul eden bir hizmet uygulaması gösterilmiştir. Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md) hesap makinesi hizmetinin uygular. Tek bir hizmet uygulayan `Calculate` kabul işlemi bir <xref:System.ServiceModel.Channels.Message> istek parametresi ve döndürür bir <xref:System.ServiceModel.Channels.Message> yanıt.  
  
 Bu örnekte, istemci bir konsol uygulaması (.exe) ve IIS'de barındırılan hizmetindeki.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Örnek ileti gönderme gövde içeriğine göre gösterir. Yerleşik Windows Communication Foundation (WCF) hizmet modeli ileti gönderme mekanizması Eylemler iletide temel alır. Ancak, tüm kullanıcıların işlemlerini eylemiyle tanımlamak birçok varolan Web hizmetleri vardır = "". İstek iletilerini eylem bilgi gönderme tutar WSDL temel bir hizmet oluşturmak mümkün değildir. Bu örnek WSDL (WSDL örneği ile dahil edilir Service.wsdl bulunur) dayalı bir hizmet sözleşmesini gösterir. Hizmet sözleşmesi hesaplayıcı kullanılanla benzer olduğunu [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md). Ancak `[OperationContract]` belirtir `Action=""` tüm işlemleri için.  
  
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
  
 Bir sözleşme göz önüne alındığında, bir hizmetin özel gönderme davranışı gerektirir `DispatchByBodyBehavior` işlemler arasında gönderilen iletilere izin vermek için. Bu dağıtım davranışı başlatır `DispatchByBodyElementOperationSelector` ilgili sarmalayıcı öğeleri QName tarafından Anahtarlanan işlem adları bir tablo ile özel işlem Seçici. `DispatchByBodyElementOperationSelector` Gövde ilk alt başlangıç etiketi arar ve daha önce bahsedilen tablo kullanarak işlemi seçer.  
  
 İstemci hizmetini kullanarak dışarı WSDL gelen otomatik üretilmiş bir proxy kullanır [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 Tüm işlemleri eylemlerini boş olgu istemci kodu otomatik olarak oluşturulan proxy eylem parametrelerinde dışında herhangi bir etkisi yoktur.  
  
 İstemci kodu birkaç hesaplama gerçekleştirir. Örneği çalıştırdığınızda, işlem isteklerini ve yanıtlarını istemci konsol penceresinde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
  
## <a name="see-also"></a>Ayrıca Bkz.
