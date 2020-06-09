---
title: XmlSerializer Hataları
ms.date: 03/30/2017
ms.assetid: c6b80f14-64f4-4162-ae76-71664cf42fd3
ms.openlocfilehash: ce5aa6d2c579d4776f9505ae694768203e48eecf
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584070"
---
# <a name="xmlserializer-faults"></a>XmlSerializer Hataları
Hata <xref:System.Xml.Serialization.XmlSerializer> sözleşmesi örneği, kullanarak bir hizmetten hata bilgilerini bir istemciye nasıl ileteceğinizi gösterir <xref:System.Xml.Serialization.XmlSerializer> . Örnek, bir iç özel durumu hataya dönüştürmek için hizmete eklenen bazı ek kodlar ile [Başlarken](getting-started-sample.md)' i temel alır. İstemci, hizmette bir hata koşulunu zorlamak için bölme işlemini sıfıra gerçekleştirmeye çalışır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Hesap makinesi sözleşmesi, <xref:System.ServiceModel.FaultContractAttribute> Aşağıdaki örnek kodda gösterildiği gibi öğesini içerecek şekilde değiştirilmiştir. Ayrıca, <xref:System.ServiceModel.XmlSerializerFormatAttribute> kullanılarak Serileştirmeyi etkinleştirmek için kullanılır <xref:System.Xml.Serialization.XmlSerializer> . <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A>Özelliği `true` Bu öznitelik üzerinde olarak ayarlanır, bu da seri hale getirici 'in <xref:System.Xml.Serialization.XmlSerializer> okuma ve yazma hataları için kullanmasını söyler.  
  
```csharp
[XmlSerializerFormat(SupportFaults=true)]  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
  
    [OperationContract]  
    int Subtract(int n1, int n2);  
  
    [OperationContract]  
    int Multiply(int n1, int n2);  
  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 İstemci proxy 'si için kod oluştururken, bir [ServiceModel meta veri yardımcı programı aracına (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) **/UseSerializerForFaults** bayrağını uygulamanız gerekir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\XmlSerializerFaults`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.XmlSerializerFormatAttribute>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A>
