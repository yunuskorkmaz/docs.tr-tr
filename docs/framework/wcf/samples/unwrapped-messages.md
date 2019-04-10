---
title: Açılmamış İletiler
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: 161f38e474534d5a0e522817c4bd64925bb4cac6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310219"
---
# <a name="unwrapped-messages"></a>Açılmamış İletiler
Açılmamış iletiler bu örnek gösterir. Varsayılan olarak, ileti gövdesi, bir hizmet işlemi parametreleri sarmalanmış şekilde biçimlendirilir. Aşağıdaki örnekte gösterildiği bir `Add` istek iletisi `ICalculator` Sarmalanan modunda hizmet.  
  
```xml  
<s:Envelope   
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"  
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
  
 `<Add>` İleti gövdesinde öğesini sarmalar `n1` ve `n2` parametreleri. Buna karşılık, aşağıdaki örnek sarmalanmış halden modunda eşdeğer iletiyi gösterir.  
  
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
  
 Açılmış neden olan iletiyi değil sarmalamak `n1` ve `n2` parametreleri içeren bir öğesinde oldukları soap gövdesi öğesinin doğrudan alt öğeleri.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Bu örnekte, sarmalanmış halden iletisine uygulanarak oluşturulan <xref:System.ServiceModel.MessageContractAttribute> hizmet işlemi parametre türü ve aşağıdaki örnek kodda gösterildiği gibi dönüş değeri türü.  
  
```csharp
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
  
 Gönderilen ve alınan iletileri görmek, izin vermek için bu örnek izlemeyi kullanır. Ayrıca, <xref:System.ServiceModel.WSHttpBinding> kaydeder iletilerin sayısını azaltmak için daha fazla güvenlik yapılandırıldı.  
  
 Sonuçta elde edilen izleme günlüğü (c:\logs\Message.log) kullanılarak görüntülenebilir [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). İleti içeriği görüntülemek için seçin **iletileri** sol ve sağ bölmeleri hizmet izleme Görüntüleyicisi aracı. Bu örnekte izleme günlükleri C:\LOGS klasöre oluşturulacak yapılandırılır. Bu klasör örneği çalıştırmadan önce oluşturun ve ağ hizmeti yazma izinleri bu dizin için kullanıcı verin.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Günlük iletileri için bir C:\LOGS dizin oluşturun. Ağ hizmeti yazma izinleri bu dizin için kullanıcıya sağlayın.  
  
3. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
