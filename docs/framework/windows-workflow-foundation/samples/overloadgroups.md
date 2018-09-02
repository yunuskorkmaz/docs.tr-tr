---
title: OverloadGroups
ms.date: 03/30/2017
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
ms.openlocfilehash: 0773e76d36b25ad5485cc8912c7012815412de9f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43469875"
---
# <a name="overloadgroups"></a>OverloadGroups
Bu örnek bir etkinlik içerir (`CreateLocation`), iki ilginç özelliklere sahiptir:  
  
1.  Bazı bağımsız değişkenler ve bazı isteğe bağlı vm'lere zorunludur.  
  
2.  Bunu iki farklı kümesinden bağımsız değişken sağlamayı tercih izin verir.  
  
 Bu davranış, bu iki özelliği kullanılarak gerçekleştirilir:  
  
-   `[isRequired]` ata, belirli bir etkinliğe özelliğidir ve aksi durumda, bir özel durum oluşturur. doğrular.  
  
-   `[OverloadGroup]` Kullanıcı etkinliğinin bir küme veya başka bir kullanma arasında seçebilmeniz birlikte bir dizi bağımsız değişken geçirir. Kullanıcı, farklı gruplardan aşırı yükleme bağımsız değişkenleri aynı örneğinde kullanamaz.  
  
 Farklı iş akışlarını ayarladıktan sonra çağrı <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> döndüren bir <xref:System.Activities.Validation.ValidationResults> koleksiyonunu <xref:System.Activities.Validation.Constraint>. Yazdırma <xref:System.Activities.Validation.Constraint> konsola nesneleri.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Açık **OverloadGroups.sln** örnek çözümde [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Derleme ve çözümü çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`
