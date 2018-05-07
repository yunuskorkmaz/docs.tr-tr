---
title: Açılmamış İletiler
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: 163dc1a6d15ac5ec4c70a096f44a9bed9a2bc70f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="unwrapped-messages"></a>Açılmamış İletiler
Bu örnek açılmamış iletiler gösterir. Bir hizmet işlemi parametreleri kaydırılmış şekilde varsayılan olarak, ileti gövdesi olarak biçimlendirilir. Aşağıdaki örnekte gösterildiği bir `Add` İstek iletisini `ICalculator` Sarmalanan modda hizmet.  
  
```xml  
<s:Envelope   
    xmlns:s=http://www.w3.org/2003/05/soap-envelope  
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        …  
    </s:Header>  
    <s:Body>  
      <Add xmlns="http://Microsoft.ServiceModel.Samples">  
        <n1>100</n1>  
        <n2>15.99</n2>  
      </Add>  
    </s:Body>  
</s:Envelope>  
```  
  
 `<Add>` İleti gövdesi öğesinde sarmalar `n1` ve `n2` parametreleri. Buna karşılık, aşağıdaki örnek, sarmalanmamış modunda eşdeğer iletisi gösterir.  
  
```xml  
<s:Envelope   
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"   
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        ….  
    </s:Header>  
    <s:Body>  
      <n1 xmlns="http://Microsoft.ServiceModel.Samples">100</n1>  
      <n2 xmlns="http://Microsoft.ServiceModel.Samples">15.99</n2>  
    </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
 Sarmalanmamış iletiyi sarmalamak değil `n1` ve `n2` parametreleri içeren bir öğesinde oldukları soap gövdesi öğenin doğrudan alt öğeleri.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 Bu örnekte, sarmalanmamış bir ileti uygulanarak oluşturulan <xref:System.ServiceModel.MessageContractAttribute> hizmet işlemi parametresi türü ve aşağıdaki örnek kodda gösterildiği gibi dönüş değeri türü.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    ResponseMessage Add(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Subtract(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Multiply(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Divide(RequestMessage request);  
}  
  
//setting IsWrapped to false means the n1 and n2  
//members will be direct children of the soap body element  
[MessageContract(IsWrapped = false)]  
public class RequestMessage  
{  
    [MessageBodyMember]  
    private double n1;  
    [MessageBodyMember]  
    private double n2;  
    //…  
}  
  
//setting IsWrapped to false means the result  
//member will be a direct child of the soap body element  
[MessageContract(IsWrapped = false)]  
public class ResponseMessage  
{  
    [MessageBodyMember]  
    private double result;  
    //…  
}  
```  
  
 Gönderilen ve alınan iletileri görmenize olanak sağlamak için bu örnek izleme kullanır. Ayrıca, <xref:System.ServiceModel.WSHttpBinding> Bu günlükleri iletilerin sayısını azaltmak için güvenlik yapılandırıldı.  
  
 Sonuçta elde edilen izleme günlüğü (c:\logs\Message.log) kullanarak görüntülenebilir [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). İleti içeriğini görüntülemek için seçin **iletileri** sol ve sağ bölmeleri hizmet izleme Görüntüleyicisi aracı. Bu örnekte izleme günlükleri C:\LOGS klasörüne oluşturulacak şekilde yapılandırılır. Örneği çalıştırmadan önce bu klasörü oluşturun ve kullanıcının ağ hizmeti yazmasına bu dizin için izin verin.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Günlük iletileri için C:\LOGS dizin oluşturun. Ağ hizmeti yazma izinleri bu dizin için kullanıcı verin.  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
  
## <a name="see-also"></a>Ayrıca Bkz.
