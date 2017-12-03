---
title: "İptal işleyicisi Compensable etkinlik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afd98bee-eccf-47e9-99c9-27cea84ce5ce
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 89a5350d61600124e3e5073d6788e4f9042cd70f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="cancellation-handler-on-compensable-activity"></a>İptal işleyicisi Compensable etkinlik
Bu örnek üzerinde iptal işleyicisi kullanımını gösteren bir <xref:System.Activities.Statements.CompensableActivity>.  
  
 Bu örnek kullanımını gösteren iki senaryo içerir <xref:System.Activities.Statements.CompensableActivity> iptali. İlk senaryoda üç alt compensable etkinlikler içeren bir kök compensable etkinlik içerir. İki alt etkinlik kendi etkinlik gövdeleri başarıyla çalıştırmadan tamamlayın. Üçüncü alt etkinlik gövde çalıştığında, daha sonra Kök etkinlik iptaline tetiklenir üçüncü etkinlik işleme iptal ederek işlenmiş bir özel durum karşılaşır. Bu örnekte kök etkinlik mantık önceden tamamlanmış bir iki alt etkinlikler dengelemek sağlamaktır.  
  
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
  
 İkinci senaryo yürütme gösterir bir <xref:System.Activities.Statements.TryCatch> ile paralel bir <xref:System.Activities.Statements.Delay>, hangi bitmeden önce <xref:System.Activities.Statements.TryCatch> dal. Tamamlanma durumu kümesine `true` ilk şube tamamlandıktan sonra iptal başka bir şube neden.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CompensationCancellation.sln açın.  
  
2.  CTRL + SHIFT + B tuşuna basarak örneği oluşturmak veya "Yapı çözümü" yapı menüsünden seçin...  
  
3.  F5 tuşuna basarak örneği çalıştırmak veya hata ayıklama menüsünden "Hata ayıklamayı Başlat" ı seçin. Alternatif olarak Ctrl + F5 tuşuna basın veya "Hata ayıklama olmadan Başlat" hata ayıklama menüsünden seçin.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CompensationCancellation`