---
title: POCO Desteği
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: e94f6d9576ed96613d975a66c1965820002f94ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183412"
---
# <a name="poco-support"></a>POCO Desteği
Bu örnek, işaretlenmemiş türler için serileştirme desteğini gösterir; diğer bir şey, serileştirme özniteliklerinin uygulanmadığı, bazen Düz Eski CLR Nesnesi (POCO) türleri olarak da adlandırılır. Parametresiz <xref:System.Runtime.Serialization.DataContractSerializer> bir oluşturucusu olan tüm genel işaretlenmemiş türler için bir veri sözleşmesi çıkar. Veri sözleşmeleri, yapılandırılmış verileri hizmetlere ve hizmetlerden aktarmanıza olanak sağlar. İşaretlenmemiş türler hakkında daha fazla bilgi için [Serializable Türleri'ne](../../../../docs/framework/wcf/feature-details/serializable-types.md)bakın.  
  
 Bu örnek [Başlarken'e](../../../../docs/framework/wcf/samples/getting-started-sample.md)dayanır, ancak ilkel sayısal türler yerine karmaşık sayılar kullanır. Ayrıca, özniteliklerin ve <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliklerin kullanılmaması [dışında, Temel Veri Sözleşmesi](../../../../docs/framework/wcf/samples/basic-data-contract.md) örneğine de benzer.  
  
 Hizmet Internet Information Services (IIS) tarafından barındırılan ve istemci bir konsol uygulamasıdır (.exe).  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
 Sınıf `ComplexNumber` ' da `ServiceContract`kullanılır. Tür, `ComplexNumber` aşağıdaki örnek <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> kodda gösterildiği gibi özniteliklere ve özniteliklere sahip değildir. Varsayılan olarak, tüm ortak özellikler ve alanlar seri hale getirilir.  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [Seri Hale Getirilebilir Türler](../../../../docs/framework/wcf/feature-details/serializable-types.md)
