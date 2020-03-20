---
title: XmlSerializer Hataları
ms.date: 03/30/2017
ms.assetid: c6b80f14-64f4-4162-ae76-71664cf42fd3
ms.openlocfilehash: adb14fdb45aa71bbaf4585cbfba55059df7cddf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183161"
---
# <a name="xmlserializer-faults"></a>XmlSerializer Hataları
Hata <xref:System.Xml.Serialization.XmlSerializer> sözleşmesi örneği, hata bilgilerinin bir hizmetten istemciye <xref:System.Xml.Serialization.XmlSerializer>nasıl iletilir, 'yi kullanarak. Örnek, bir iç özel durumu hataya dönüştürmek için hizmete eklenen bazı ek kodlarla [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanır. İstemci, hizmette hata koşulunu zorlamak için bölmeyi sıfıra kadar gerçekleştirmeye çalışır.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Hesap makinesi sözleşmesi, aşağıdaki <xref:System.ServiceModel.FaultContractAttribute> örnek kodda gösterildiği gibi bir sözleşme içerecek şekilde değiştirilmiştir. Ayrıca, <xref:System.ServiceModel.XmlSerializerFormatAttribute> serileştirmeyi etkinleştirmek için <xref:System.Xml.Serialization.XmlSerializer>kullanılır. Özellik, <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A> serileştiriciye hataları okuma ve yazma `true` <xref:System.Xml.Serialization.XmlSerializer> için kullanmasını emreden bu öznitelik üzerinde ayarlanır.  
  
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
  
 İstemci proxy için kod oluştururken, [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) **/UseSerializerForFaults** bayrağını uygulamanız gerekir.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\XmlSerializerFaults`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.XmlSerializerFormatAttribute>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A>
