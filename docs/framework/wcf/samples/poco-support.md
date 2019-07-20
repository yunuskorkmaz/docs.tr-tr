---
title: POCO Desteği
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: 8f65f6d2131941d02c773f61f70084059293187c
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363097"
---
# <a name="poco-support"></a>POCO Desteği
Bu örnek, işaretsiz türler için serileştirme desteğini gösterir; diğer bir deyişle, bazı durumlarda düz eski CLR nesne (POCO) türleri olarak da adlandırılan serileştirme özniteliklerinin uygulanmadığı türler. , <xref:System.Runtime.Serialization.DataContractSerializer> Parametresiz oluşturucusu olan tüm genel işaretsiz türler için bir veri sözleşmesi olduğunu anlar. Veri sözleşmeleri, yapılandırılmış verileri hizmetlere ve hizmetlerden geçirmenize olanak sağlar. İşaretsiz türler hakkında daha fazla bilgi için bkz. [serileştirilebilir türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
 Bu örnek [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md)' i temel alır, ancak basit sayısal türler yerine karmaşık sayılar kullanır. Ayrıca, <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliklerinin kullanılmadığı durumlar dışında [temel veri sözleşmesi](../../../../docs/framework/wcf/samples/basic-data-contract.md) örneğine de benzer.  
  
 Hizmet Internet Information Services (IIS) tarafından barındırılır ve istemci bir konsol uygulaması (. exe).  
  
> [!NOTE]
>  Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Sınıfı ' de kullanılır. `ServiceContract` `ComplexNumber` Türü, aşağıdaki örnek kodda gösterildiği <xref:System.Runtime.Serialization.DataContractAttribute> gibi <xref:System.Runtime.Serialization.DataMemberAttribute> , ve özniteliklerine sahip değildir. `ComplexNumber` Varsayılan olarak, tüm ortak özellikler ve alanlar serileştirilir.  
  
```csharp
public class ComplexNumber  
{  
    public double Real;  
    public double Imaginary;  
    public ComplexNumber()  
    {  
        Real = double.MinValue;  
        Imaginary = double.MinValue;  
    }  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [Seri Hale Getirilebilir Türler](../../../../docs/framework/wcf/feature-details/serializable-types.md)
