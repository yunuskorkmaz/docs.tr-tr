---
title: Açılmamış İletiler
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: 81592910d8530cea2df5ec1fd8a8b1145350ef78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143739"
---
# <a name="unwrapped-messages"></a>Açılmamış İletiler
Bu örnek, paketlenmemiş iletileri gösterir. Varsayılan olarak, ileti gövdesi, bir hizmet işleminin parametreleri sarılmış olacak şekilde biçimlendirilir. Aşağıdaki örnek, `Add` paketleden `ICalculator` modunda hizmete bir istek iletisi gösterir.  
  
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
  
 İleti `<Add>` gövdesindeki öğe, `n1` parametreleri `n2` ve Buna karşılık, aşağıdaki örnek, paketlenmemiş modda eşdeğer iletiyi gösterir.  
  
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
  
 Unwrapped mesaj `n1` içeren bir `n2` öğe ve parametreleri sarmak değil, onlar sabun vücut elemanının doğrudan çocuklarıdır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Bu örnekte, aşağıdaki örnek kodda gösterildiği <xref:System.ServiceModel.MessageContractAttribute> gibi hizmet işlem parametresi türüne ve iade değeri türüne uygulanarak paketlenmemiş bir ileti oluşturulur.  
  
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
  
 Gönderilen ve alınan iletileri görmenizi sağlamak için bu örnek izleme kullanır. Buna ek <xref:System.ServiceModel.WSHttpBinding> olarak, günlükleri ileti sayısını azaltmak için, güvenlik olmadan yapılandırıldı.  
  
 Elde edilen izleme günlüğü (c:\logs\Message.log) [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)kullanılarak görüntülenebilir. İleti içeriğini görüntülemek için, Hizmet İzleme Görüntüleyici aracının hem sol hem de sağ bölmelerinde **İletileri** seçin. Bu örnekteki izleme günlükleri C:\LOGS klasöründe oluşturulacak şekilde yapılandırılır. Örneği çalıştırmadan önce bu klasörü oluşturun ve kullanıcıYa Bu dizini yazma izinleri verin.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. İletileri günlüğe kaydetmek için C:\LOGS dizini oluşturun. Kullanıcı Ağ Hizmeti'ne bu dizini yazma izinleri verin.  
  
3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
4. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
