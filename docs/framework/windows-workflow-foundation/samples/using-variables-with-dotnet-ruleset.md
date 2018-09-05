---
title: .NET Framework 3.5 kural kümesi ile değişkenleri kullanma
ms.date: 03/30/2017
ms.assetid: 27b56249-22fe-4252-840f-74c0d6c7a6b3
ms.openlocfilehash: 64d47564076e19e152e30b6ab0cb3900ce53cfa1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512860"
---
# <a name="using-variables-with-a-net-framework-35-ruleset"></a>.NET Framework 3.5 kural kümesi ile değişkenleri kullanma
Bu örnek kullanan bir iş akışının nasıl oluşturulacağını gösterir <xref:System.Activities.Statements.Interop> yazılan özel bir etkinlik tümleştirmek için etkinlik [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] ilke ve kurallara kullanır. İş akışı, özel bir etkinlik için özel etkinlik tarafından kullanıma sunulan bağımlılık özellikleri için değişkenleri bağlayarak verileri geçirir.  
  
## <a name="sample-walkthrough"></a>İzlenecek örnek yol  
  
#### <a name="to-examine-travelrulelibrary"></a>TravelRuleLibrary incelemek için  
  
1.  Visual Studio kullanarak, InteropWith35RuleSet.sln çözüm dosyasını açın.  
  
2.  TravelRuleSet.cs iş akışı Tasarımcısı'nda açın.  
  
     İçeren özel bir sıralı etkinlik bir <xref:System.Workflow.Activities.PolicyActivity> görüntülenir.  
  
3.  Kuralları incelemek için DiscountPolicy ilke etkinliği çift tıklatın.  
  
     Kuralları göstermek için kurallar düzenleyicisinde açılır.  
  
4.  Sağ tıklayın `DiscountPolicy` seçip **kodu görüntüle** seçeneği C# kodu etkinliğinin yanındaki kodu inceleyin.  
  
     Bağımlılık özelliği ayarı gözlemleyin `DiscountLevel`. Bu bağımsız değişken eşdeğer [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]. Bağımsız değişkenler hakkında daha fazla bilgi için bkz. [değişkenleri ve bağımsız değişkenler](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).  
  
## <a name="interopwith35ruleset"></a>InteropWith35RuleSet  
 Kullanan bir sıralı iş akışı projesi budur <xref:System.Activities.Statements.Interop> oluşturulan özel kural kümesi ile tümleştirmek için etkinlik `TravelRuleLibrary` proje. Değişkenleri, en üst düzey oluşturulur <xref:System.Activities.Statements.Sequence> etkinlik. <xref:System.Activities.Statements.Interop> Etkinlik ile tümleştirmek için kullanılan `TravelRuleSet` etkinlik. Üzerinde bildirilen değişkenlerin <xref:System.Activities.Statements.Sequence> bağımlılık özellikleri için bağlamak için kullanılır.  
  
## <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], InteropWith35RuleSet.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`