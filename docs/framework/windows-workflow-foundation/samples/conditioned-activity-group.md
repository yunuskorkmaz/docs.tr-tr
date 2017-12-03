---
title: "Koşullu etkinlik grubu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f76ef924-34ce-48ae-8c8d-48faf9697754
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e0df4ddc6f2cc5404c8153b30df66cda41487691
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="conditioned-activity-group"></a>Koşullu etkinlik grubu
Örnek bir seyahat kayıt uygulaması gösterir. <xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) sahip iki kodunu aktivite: bir araba ve uçak etkinliğiyle. İçinde `SimpleCAGWorkflow` oluşturucusu, bir "travelNeedType" ArrayList nesnesi gerekli seyahat kayıtları türleri ile doldurulur. Birini veya her ikisini yorum tarafından `travelNeeds.Add` deyimleri CAG davranış buna göre değiştirin. Araba ve uçak etkinliklerin kendi <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> koşul doldurulmuş ile bir <xref:System.Workflow.Activities.CodeCondition>. Yalnızca araba etkinlik yürütür `travelNeeds` gruplandırmasında bir `TravelNeeds.Car` girişi ve etkinlik yürütür yalnızca uçak `travelNeeds` gruplandırmasında bir `TravelNeeds.Airline` girişi.  
  
 Her etkinlik yürütülmesini karşılık gelen bir giriş koleksiyondan kaldırır. Varsayılan <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> durumunu belirten alt öğesi yürütülmekte olduğunu veya yürütme için hazır olduğunda CAG çıkmalıdır (göre kendi <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> koşullar). Bu örnekte, bu CAG ne zaman çıkar anlamına gelir `travelNeeds` koleksiyonu boş.  
  
### <a name="to-build-the-sample"></a>Örneği oluşturmak için  
  
1.  Çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.  
  
3.  CTRL + F5'e basarak hata ayıklama olmadan çözümü çalıştırın.  
  
### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
-   Örnek için ana klasörü altında bulunan .exe dosyasını SimpleCAG\bin\debug klasöründe (veya örnek Visual Basic sürümü için SimpleCAG\bin klasör) SDK komut istemi penceresinde çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetle:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\SimpleCAG`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Workflow.Activities.ConditionedActivityGroup>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>  
 <xref:System.Workflow.Activities.CodeCondition>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A>
