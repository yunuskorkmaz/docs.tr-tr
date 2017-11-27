---
title: "Basit İlkesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a94c834-2e32-4bed-9f47-ae5845eef6ff
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0c704a9f3f27d63fb1a28db61f03cdc9b8de4370
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="simple-policy"></a>Basit İlkesi
Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Workflow.Activities.PolicyActivity> bir iş akışı etkinlik.  
  
 Bu örnekte sıralı iş akışı kullanılarak oluşturulan bir <xref:System.Workflow.Activities.PolicyActivity> etkinlik. İş akışını tanımlayan `orderValue`, `customerType`, ve `discount` bir ürün tanımlamak için kullanılan alanları indirim iş akışı. Kural dosyasında tanımlanan kurallar temel alır bir indirim değeri ayarlamak `orderValue` ve `customerType`. `orderValue` Ve `customerType` ayarlanır `SimplePolicyWorkflow` sınıf tanımının ve davranışı değiştirmek için değiştirilebilir. Sonuçta elde edilen indirim konsolda yazılır <xref:System.Workflow.Runtime.WorkflowRuntime.WorkflowCompleted> tanımlanan olay işleyicisi `SimplePolicyWorkflow` sınıfı.  
  
### <a name="to-build-the-sample"></a>Örneği oluşturmak için  
  
1.  Çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.  
  
3.  CTRL + F5'e basarak hata ayıklama olmadan çözümü çalıştırın.  
  
### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
-   Örnek için ana klasörü altında bulunan .exe dosyasını SimplePolicy\bin\debug klasöründe (veya örnek Visual Basic sürümü için SimplePolicy\bin klasör) SDK komut istemi penceresinde çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetle:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\SimplePolicy`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Workflow.Activities.Rules.RuleSet>  
 <xref:System.Workflow.Activities.PolicyActivity>  
 [Gelişmiş İlkesi](../../../../docs/framework/windows-workflow-foundation/samples/advanced-policy.md)
