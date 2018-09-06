---
title: Koşullu etkinlik grubu
ms.date: 03/30/2017
ms.assetid: f76ef924-34ce-48ae-8c8d-48faf9697754
ms.openlocfilehash: 144a6c76ea6314c553e201fe4e2364890d869f34
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861211"
---
# <a name="conditioned-activity-group"></a>Koşullu etkinlik grubu
Örnek, bir seyahat kayıt uygulamasını gösterir. <xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) sahip iki kod etkinliği: bir araba etkinliği ve bir uçak etkinliği. İçinde `SimpleCAGWorkflow` Oluşturucu, bir "travelNeedType" ArrayList'i gerekli olan seyahat rezervasyonlarının türleri ile doldurulur. Birini veya her ikisini yorum tarafından `travelNeeds.Add` deyimleri CAG davranışı uygun şekilde değiştirin. Hem araç hem de Havayolu etkinliklerin kendi <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> koşul ile doldurulur bir <xref:System.Workflow.Activities.CodeCondition>. Yalnızca bir araba etkinliği yürütür `travelNeeds` gruplandırmasında bir `TravelNeeds.Car` girişi ve yalnızca bir etkinliği yürütür Havayolu `travelNeeds` gruplandırmasında bir `TravelNeeds.Airline` girişi.  
  
 Her etkinliğin yürütülmesine karşılık gelen bir giriş koleksiyondan kaldırır. Varsayılan <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> koşulu belirtir alt yürütülen veya yürütme için hazır CAG çıkılması gerekiyor (göre kendi <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> koşulları). Bu örnekte, bu CAG ne zaman çıkar anlamına gelir `travelNeeds` koleksiyonu boş.  
  
### <a name="to-build-the-sample"></a>Örneği oluşturmak için  
  
1.  Bir çözüm açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.  
  
3.  CTRL + F5 tuşlarına basarak hata ayıklama olmadan çözümü çalıştırın.  
  
### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
-   SDK komut istemi penceresinde, örnek için ana klasörü altında bulunan .exe dosyasını SimpleCAG\bin\debug klasöre (veya Visual Basic sürümünü SimpleCAG\bin klasörü) çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin için denetleyin:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\SimpleCAG`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Workflow.Activities.ConditionedActivityGroup>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>  
 <xref:System.Workflow.Activities.CodeCondition>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A>
