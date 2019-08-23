---
title: XmlSerializer Hataları
ms.date: 03/30/2017
ms.assetid: c6b80f14-64f4-4162-ae76-71664cf42fd3
ms.openlocfilehash: c800b23ca5f3589ba3a99b88471afe5b4e5a62bf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959633"
---
# <a name="xmlserializer-faults"></a>XmlSerializer Hataları
Hata sözleşmesi örneği, <xref:System.Xml.Serialization.XmlSerializer>kullanarak bir hizmetten hata bilgilerini bir istemciye nasıl ileteceğinizi gösterir. <xref:System.Xml.Serialization.XmlSerializer> Örnek, bir iç özel durumu hataya dönüştürmek için hizmete eklenen bazı ek kodlar ile [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır. İstemci, hizmette bir hata koşulunu zorlamak için bölme işlemini sıfıra gerçekleştirmeye çalışır.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Hesap makinesi sözleşmesi, aşağıdaki örnek kodda gösterildiği <xref:System.ServiceModel.FaultContractAttribute> gibi öğesini içerecek şekilde değiştirilmiştir. Ayrıca, kullanılarak Serileştirmeyi etkinleştirmek için kullanılır. <xref:System.Xml.Serialization.XmlSerializer> <xref:System.ServiceModel.XmlSerializerFormatAttribute> Özelliği bu öznitelik üzerinde olarak `true` ayarlanır, bu da seri hale getirici 'in okuma ve yazma <xref:System.Xml.Serialization.XmlSerializer> hataları için kullanmasını söyler. <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A>  
  
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
  
 İstemci proxy 'si için kod oluştururken, bir [ServiceModel meta veri yardımcı programı aracına (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) **/UseSerializerForFaults** bayrağını uygulamanız gerekir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
>  Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\XmlSerializerFaults`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.XmlSerializerFormatAttribute>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A>
