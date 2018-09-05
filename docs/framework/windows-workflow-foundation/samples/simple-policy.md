---
title: Basit ilke
ms.date: 03/30/2017
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
ms.openlocfilehash: 7f189e4d1811cb0b7dd9138b944bfd0552481690
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43561270"
---
# <a name="simple-policy"></a>Basit ilke
Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Workflow.Activities.PolicyActivity> bir iş akışında etkinlik.  
  
 Bu örnekte sıralı iş akışı kullanılarak oluşturulan bir <xref:System.Workflow.Activities.PolicyActivity> etkinlik. İş akışını tanımlayan `orderValue`, `customerType`, ve `discount` bir ürün tanımlamak için kullanılan alanlar, iş akışı indirim. Kuralları dosyasında tanımlanan kuralları temel alan bir indirim değeri ayarlamak `orderValue` ve `customerType`. `orderValue` Ve `customerType` ayarlanan `SimplePolicyWorkflow` sınıf tanımını ve davranışını değiştirmek için değiştirilebilir. Sonuçta elde edilen indirim konsolda yazılan <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> tanımlanan olay işleyicisi `SimplePolicyWorkflow` sınıfı.  
  
### <a name="to-build-the-sample"></a>Örneği oluşturmak için  
  
1.  Bir çözüm açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.  
  
3.  CTRL + F5 tuşlarına basarak hata ayıklama olmadan çözümü çalıştırın.  
  
### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
-   SDK komut istemi penceresinde, örnek için ana klasörü altında bulunan .exe dosyasını SimplePolicy\bin\debug klasöre (veya Visual Basic sürümünü SimplePolicy\bin klasörü) çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin için denetleyin:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [Gelişmiş İlke](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)
