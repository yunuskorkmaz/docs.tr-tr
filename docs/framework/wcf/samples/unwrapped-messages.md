---
title: Açılmamış İletiler
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: 4d6525393bb65dd6361b8d195f3a71991102daa1
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716729"
---
# <a name="unwrapped-messages"></a>Açılmamış İletiler
Bu örnek sarmalanmamış iletileri gösterir. Varsayılan olarak, ileti gövdesi bir hizmet işlemine ait parametrelerin sarmalanması için biçimlendirilir. Aşağıdaki örnek, Sarmalanan modda `ICalculator` hizmetine bir `Add` isteği iletisi gösterir.  
  
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
  
 İleti gövdesindeki `<Add>` öğesi `n1` ve `n2` parametrelerini sarmalar. Buna karşılık aşağıdaki örnek, sarmalanmamış moddaki denk iletiyi gösterir.  
  
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
  
 Sarmalanmamış ileti, içerilen bir öğedeki `n1` ve `n2` parametrelerini sarmalamaz, bunlar soap body öğesinin doğrudan alt öğesidir.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Bu örnekte, hizmet işlemi parametre türüne <xref:System.ServiceModel.MessageContractAttribute> uygulanarak sarmalanmamış bir ileti oluşturulur ve aşağıdaki örnek kodda gösterildiği şekilde değer türü döndürülür.  
  
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
  
 Gönderilen ve alınan iletileri görmenizi sağlamak için bu örnek izleme kullanır. Ayrıca, <xref:System.ServiceModel.WSHttpBinding>, günlüğe kaydettiği ileti sayısını azaltmak için güvenlik olmadan yapılandırılmıştır.  
  
 Elde edilen izleme günlüğü (c:\logs\Message.log), [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)kullanılarak görüntülenebilir. İleti içeriğini görüntülemek için, hizmet Izleme Görüntüleyicisi aracının sol ve sağ bölmelerinde **iletiler** ' i seçin. Bu örnekteki izleme günlükleri C:\LOGS klasöründe oluşturulacak şekilde yapılandırılmıştır. Örneği çalıştırmadan önce bu klasörü oluşturun ve bu dizin için Kullanıcı ağ hizmetine yazma izinleri verin.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. İletileri günlüğe kaydetmek için bir C:\LOGS dizini oluşturun. Bu dizin için Kullanıcı ağ hizmetine yazma izinleri verin.  
  
3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
4. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
