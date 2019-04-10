---
title: XmlSerializer Hataları
ms.date: 03/30/2017
ms.assetid: c6b80f14-64f4-4162-ae76-71664cf42fd3
ms.openlocfilehash: a64a28e7a0105f5133ba2b0cd3abf72d97d5a3e3
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298012"
---
# <a name="xmlserializer-faults"></a>XmlSerializer Hataları
<xref:System.Xml.Serialization.XmlSerializer> Hata sözleşme örnek gösterir kullanarak istemciye bir hizmetten hata bilgileri iletişim kurma <xref:System.Xml.Serialization.XmlSerializer>. Örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), bazı ek kod bir hata için iç özel durum dönüştürmek için hizmet eklenir. İstemci bir hata koşulu hizmette zorlamak için sıfır ile bölme gerçekleştirmeye çalışır.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 Hesaplayıcı sözleşme içerecek şekilde değiştirilmiş bir <xref:System.ServiceModel.FaultContractAttribute> aşağıdaki örnek kodda gösterildiği gibi. Ayrıca, <xref:System.ServiceModel.XmlSerializerFormatAttribute> serileştirme kullanarak etkinleştirmek için kullanılan <xref:System.Xml.Serialization.XmlSerializer>. <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A> Özelliği `true` Bu öznitelikte hangi bildirir kullanılacak serileştirici <xref:System.Xml.Serialization.XmlSerializer> hataları yazma ve okuma için.  
  
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
  
 Kod için istemci proxy oluşturulurken uygulamalısınız **/UseSerializerForFaults** bayrak [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\XmlSerializerFaults`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.XmlSerializerFormatAttribute>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A>
