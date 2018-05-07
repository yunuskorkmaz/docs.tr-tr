---
title: .NET Framework 3.5 Ruleset ile değişkenlerini kullanma
ms.date: 03/30/2017
ms.assetid: 27b56249-22fe-4252-840f-74c0d6c7a6b3
ms.openlocfilehash: 9fa6eaf58aaddc4673f08ec9a9001647a494877d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-variables-with-a-net-framework-35-ruleset"></a>.NET Framework 3.5 Ruleset ile değişkenlerini kullanma
Bu örneği kullanan bir iş akışının nasıl oluşturulacağını gösterir <xref:System.Activities.Statements.Interop> yazılmış özel bir aktivite tümleştirmek için etkinlik [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] İlkesi ve kuralları kullanır. İş akışı değişkenleri özel etkinlik tarafından kullanıma sunulan bağımlılık özellikleri bağlayarak verileri özel etkinlik geçirir.  
  
## <a name="sample-walkthrough"></a>Örnek gözden geçirme  
  
#### <a name="to-examine-travelrulelibrary"></a>TravelRuleLibrary incelemek için  
  
1.  Visual Studio kullanarak InteropWith35RuleSet.sln çözüm dosyasını açın.  
  
2.  İş Akışı Tasarımcısı'nda TravelRuleSet.cs açın.  
  
     İçeren özel bir sıralı etkinlik bir <xref:System.Workflow.Activities.PolicyActivity> görüntülenir.  
  
3.  Kuralları incelemek için DiscountPolicy İlkesi etkinliği çift tıklatın.  
  
     Kuralları göstermek için kural Düzenleyicisi açılır.  
  
4.  Sağ tıklayın `DiscountPolicy` seçip **görünümü kodu** seçeneği C# kodu etkinliğin yanında kodu inceleyin.  
  
     Bağımlılık özelliği ayarını gözlemlemek `DiscountLevel`. Bu bağımsız değişkenler için eşdeğerdir [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]. Bağımsız değişkenleri hakkında daha fazla bilgi için bkz: [değişkenleri ve bağımsız değişkenler](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).  
  
## <a name="interopwith35ruleset"></a>InteropWith35RuleSet  
 Bu kullanan bir sıralı iş akışı projedir <xref:System.Activities.Statements.Interop> oluşturulan özel kural kümesi ile tümleştirmek için etkinlik `TravelRuleLibrary` projesi. Değişkenleri, en üst düzey oluşturulur <xref:System.Activities.Statements.Sequence> etkinlik. <xref:System.Activities.Statements.Interop> Etkinlik ile tümleştirmek için kullanılan `TravelRuleSet` etkinlik. Üzerinde bildirilen değişkenlerin <xref:System.Activities.Statements.Sequence> bağımlılık özelliği bağlamak için kullanılır.  
  
## <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], InteropWith35RuleSet.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`