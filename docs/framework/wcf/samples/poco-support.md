---
title: POCO Desteği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9c67b39c8d3c48281eb0ec9c360de7eaff1cfad6
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="poco-support"></a>POCO Desteği
Bu örnek işaretsiz türleri için seri hale getirme destek gösterir; diğer bir deyişle, kendisine serileştirme özniteliklerini uygulanmamış, türleri bazen başvurduğu düz eski CLR nesnesi (POCO) türleri olarak. <xref:System.Runtime.Serialization.DataContractSerializer> Veri sözleşmesi varsayılan bir oluşturucuya sahip tüm ortak işaretsiz türleri oluşturur. Veri sözleşmeleri için ve Hizmetleri'nden yapılandırılmış veri iletmek sağlar. İşaretsiz türleri hakkında daha fazla bilgi için bkz: [seri hale getirilebilir türler](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
 Bu örnek dayanır [Başlarken](../../../../docs/framework/wcf/samples/getting-started-sample.md), ancak yerine basit sayısal türler karmaşık numaralar kullanır. Ayrıca benzer [temel veri sözleşmesi](../../../../docs/framework/wcf/samples/basic-data-contract.md) , durumlar dışında örnek <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelikleri kullanılmaz.  
  
 Internet Information Services (IIS) tarafından barındırılan hizmetindeki ve istemcinin bir konsol uygulaması (.exe).  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 `ComplexNumber` Sınıfı kullanılıyor `ServiceContract`. `ComplexNumber` Türü yok <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> , aşağıdaki örnek kodda gösterildiği gibi öznitelikleri. Varsayılan olarak, tüm genel özellikleri ve alanları serileştirilir.  
  
```  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 [Seri Hale Getirilebilir Türler](../../../../docs/framework/wcf/feature-details/serializable-types.md)
