---
title: Kurallarla Ifelse
ms.date: 03/30/2017
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
ms.openlocfilehash: 31906f04149a0ca7659201965ca565c7fa2af305
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500535"
---
# <a name="ifelse-with-rules"></a>Kurallarla Ifelse
Bu örnek, bir kural koşulu ile kullanımını gösterir. bir <xref:System.Workflow.Activities.IfElseActivity> etkinlik.  
  
 Örnek içinde geçen bir `OrderValue` konaktan parametresi. Parametresinin değeri ilk dalı bir kural koşulu kullanılır <xref:System.Workflow.Activities.IfElseActivity> etkinlik. Değer 10. 000'den az ise ilk dalı yürütür ve <xref:System.Workflow.Activities.CodeActivity> ilk dalı etkinliğinde yazdırır **yönetici onayı alma** konsola. Değeri, 10.000 büyükse <xref:System.Workflow.Activities.CodeActivity> ikinci daldaki etkinliği yürütür ve yazdırır **VP onay alma**.  
  
### <a name="to-build-the-sample"></a>Örneği oluşturmak için  
  
1.  Bir çözüm açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.  
  
3.  CTRL + F5 tuşlarına basarak hata ayıklama olmadan çözümü çalıştırın.  
  
### <a name="to-run-the-sample"></a>Örnek çalıştırmak için  
  
-   SDK komut istemi penceresinde, örnek için ana klasörü altında bulunan .exe dosyasını IfElseWithRules\bin\debug klasöre (veya Visual Basic sürümünü IfElseWithRules\bin klasörü) çalıştırın.  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin için denetleyin:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Workflow.Activities.Rules>  
 <xref:System.Workflow.Activities.IfElseActivity>  
 <xref:System.Workflow.Activities.CodeActivity>  
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>
