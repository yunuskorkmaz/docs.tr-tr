---
title: POCO Desteği
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: 8d94d6a9700c38014aa53ee9910b53239fc28b0a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640037"
---
# <a name="poco-support"></a>POCO Desteği
Bu örnek, işaretsiz türleri için serileştirme destek gösterir; diğer bir deyişle, türleri, serileştirme öznitelikleri uygulanmadı, bazen ifade türleri olarak düz eski CLR nesnesi (POCO). <xref:System.Runtime.Serialization.DataContractSerializer> Varsayılan bir oluşturucuya sahip tüm genel işaretsiz türleri için bir veri anlaşması algılar. Veri sözleşmeleri, yapılandırılmış veriler için ve hizmetlerden geçmesine izin verin. İşaretsiz türleri hakkında daha fazla bilgi için bkz. [Serializable türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
 Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), ancak karmaşık sayılar yerine basit sayısal türler kullanır. Aynı zamanda benzeyen [temel veri anlaşması](../../../../docs/framework/wcf/samples/basic-data-contract.md) , hariç örnek <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelikleri kullanılmaz.  
  
 Hizmet, Internet Information Services (IIS) tarafından barındırılan ve istemcisinin bir konsol uygulaması (.exe).  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 `ComplexNumber` Sınıfı kullanılan `ServiceContract`. `ComplexNumber` Türü yok <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> , aşağıdaki örnek kodda gösterildiği gibi öznitelikleri. Varsayılan olarak, tüm ortak özellikler ve alanları serileştirilir.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [Seri Hale Getirilebilir Türler](../../../../docs/framework/wcf/feature-details/serializable-types.md)
