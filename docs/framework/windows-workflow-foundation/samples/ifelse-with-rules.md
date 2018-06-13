---
title: Ifelse kurallarla
ms.date: 03/30/2017
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
ms.openlocfilehash: 179ec29f957894433fb527a14048460f5ff6ee5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515127"
---
# <a name="ifelse-with-rules"></a>Ifelse kurallarla
Bu örnek, bir kural koşulu ile kullanımını göstermektedir bir <xref:System.Workflow.Activities.IfElseActivity> etkinlik.  
  
 Örnek olarak geçirir bir `OrderValue` ana bilgisayardan parametresi. Bir kural koşulu ilk dalı parametresinin değeri kullanılıyor <xref:System.Workflow.Activities.IfElseActivity> etkinlik. Değer 10. 000'den az ise, ilk dal yürütür ve <xref:System.Workflow.Activities.CodeActivity> ilk şube etkinliğinde yazdırır **Yöneticisi Onayı alma** konsoluna. Değer, 10.000 büyük olduğunda <xref:System.Workflow.Activities.CodeActivity> etkinlik ikinci dal yürütür ve yazdırır **VP onay almak**.  
  
### <a name="to-build-the-sample"></a>Örneği oluşturmak için  
  
1.  Çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.  
  
3.  CTRL + F5'e basarak hata ayıklama olmadan çözümü çalıştırın.  
  
### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
-   Örnek için ana klasörü altında bulunan .exe dosyasını IfElseWithRules\bin\debug klasöründe (veya örnek Visual Basic sürümü için IfElseWithRules\bin klasör) SDK komut istemi penceresinde çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetle:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Workflow.Activities.Rules>  
 <xref:System.Workflow.Activities.IfElseActivity>  
 <xref:System.Workflow.Activities.CodeActivity>  
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>
