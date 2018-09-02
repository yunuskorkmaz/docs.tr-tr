---
title: Compensable etkinliğinde iptal işleyicisi
ms.date: 03/30/2017
ms.assetid: afd98bee-eccf-47e9-99c9-27cea84ce5ce
ms.openlocfilehash: 2f32d10e22be7fdd1e84229a214409df06efa918
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43442713"
---
# <a name="cancellation-handler-on-compensable-activity"></a>Compensable etkinliğinde iptal işleyicisi
Bu örnek, üzerinde bir iptal işleyicisi kullanımını gösterir. bir <xref:System.Activities.Statements.CompensableActivity>.  
  
 Bu örnek kullanımını gösteren iki senaryo içerir <xref:System.Activities.Statements.CompensableActivity> iptali. İlk senaryoda üç alt compensable etkinlikler içeren bir kök compensable etkinliği içeriyor. İki alt etkinlik, etkinlik gövdeleri başarıyla çalıştığını tamamlayın. Üçüncü bir alt etkinlik gövdesi çalıştığında, sonra Kök etkinlik iptal tetiklenir üçüncü etkinlik işleme iptal tarafından işlenen özel durum karşılaşır. Bu örnekte kök etkinlik mantığı, daha önce tamamlanan bir iki alt etkinlikleri dengelemek sağlamaktır.  
  
```  
Try  
{  
    CA   
    {  
        CA1   
        {  
        }  
        CA2  
        {  
        }  
        CA3  
        {  
            //Exception here  
            // Then this will get cancelled  
        }  
  
       // Cancellation for the root activity automatically gets called, which, in turn, adds some logic to revert what was done (Or can decide to actually confirm CA1 & CA2 if the user so desires).  
    }  
}  
Catches {  
// Can do more stuff...  
}  
```  
  
 İkinci senaryoda yürütme gösterir bir <xref:System.Activities.Statements.TryCatch> ile paralel bir <xref:System.Activities.Statements.Delay>, önce tamamlanır <xref:System.Activities.Statements.TryCatch> dal. Tamamlama koşul kümesine `true` ilk dal tamamlandıktan sonra diğer dal iptal edilmesine neden.  
  
```  
Parallel   
{  
    Branch1   
    {  
        // Small Delay that times out (timeout1) before branch2.  
    }  
    Branch2   
    {  
        CA   
        {  
            CA1   
            {  
            }  
            CA2   
            {  
            }  
            CA3   
            {  
            }  
            If (timeout1)    
            {  
                call Cancel CA  
            }  
        }  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CompensationCancellation.sln açın.  
  
2.  CTRL + SHIFT + B tuşlarına basarak örneği oluşturmak veya derleme menüsünden "Çözümü Derle" seçin...  
  
3.  F5 tuşuna basarak örneği çalıştırın veya hata ayıklama menüsünden "Hata ayıklamaya Başla"'i seçin. Alternatif olarak, Ctrl + F5 tuşlarına basın veya hata ayıklama menüsünden "Hata ayıklama olmadan Başlat"'i seçin.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CompensationCancellation`