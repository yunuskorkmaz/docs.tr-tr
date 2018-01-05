---
title: "3.5 kural kümesi ile birlikte çalışma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 969f3295-d874-428c-a9c6-623e3d578e51
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 854aeac936d3f911f2613c6e315ab81347f64a25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="interop-with-35-rule-set"></a>3.5 kural kümesi ile birlikte çalışma
Bu örnek kullanımını gösteren <xref:System.Activities.Statements.Interop> özel bir etkinlikte ile tümleştirmek için etkinlik [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] kullanarak <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` ve kuralları. Özel Etkinlik verileri, bağlayarak geçirmeden [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] özel etkinlik tarafından kullanıma sunulan bağımlılık özellikleri değişkenleri.  
  
## <a name="requirements"></a>Gereksinimler  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
2.  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
3.  [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.Activities.Statements.Interop>etkinlik, <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` etkinliğinde [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] bağımlılık özellikleri  
  
## <a name="discussion"></a>Tartışma  
 Örnek ile tümleştirme için tümleştirme senaryolarına birini gösteren bir [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] etkinlik. Bu örnek içeren bir [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] çağıran Özel Etkinlik bir <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` etkinlik.  
  
## <a name="travelrulelibrary"></a>TravelRuleLibrary  
 Şu şekilde bir ilke etkinlik içeren özel bir sıralı etkinlik Tasarımcısı'nda TravelRuleSet.cs açma gösterir  
  
 ![Birlikte çalışma etkinlik](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")  
  
 Çift **DiscountPolicy** ilke etkinlik kuralları inceleyin. Kuralları göstermek için kuralları Düzenleyicisi görüntülenir.  
  
 ![Kural kümesi düzenleyici](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")  
  
 Sağ **DiscountPolicy** etkinliği ve seçin **görünümü kodu** seçeneği ile bu etkinliğine gittiği kod yanında C# kodu inceleyin. Bağımlılık özelliği ayarını gözlemlemek `DiscountLevel`. Bu eşdeğer olan bir <xref:System.Activities.Argument> içinde [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].  
  
```  
public static DependencyProperty DiscountLevelProperty = DependencyProperty.Register("DiscountLevel", typeof(int), typeof(TravelRuleSet));  
  
[DescriptionAttribute("DiscountLevel")]  
[CategoryAttribute("DiscountLevel Category")]  
[BrowsableAttribute(true)]  
[DesignerSerializationVisibilityAttribute(DesignerSerializationVisibility.Visible)]  
public int DiscountLevel  
{  
   get  
   {  
return ((int)base.GetValue(TravelRuleSet.DiscountLevelProperty)));  
   }  
   set  
   {  
base.SetValue(TravelRuleSet.DiscountLevelProperty, value);  
   }  
}  
```  
  
## <a name="interopwith35ruleset"></a>InteropWith35RuleSet  
 Bu bir [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] kullanan sıralı iş akışı projesinde <xref:System.Activities.Statements.Interop> özel kural TravelRuleLibrary projesinde oluşturulan kümesi ile tümleştirmek için etkinlik. Değişkenleri üst düzey üzerinde oluşturulan <xref:System.Activities.Statements.Sequence> gibi.  
  
 ![Değişkenleri](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")  
  
 ![Çözüm Gezgini](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")  
  
 Son olarak, <xref:System.Activities.Statements.Interop> etkinlik TravelRuleSet ile tümleştirmek için kullanılır. Daha önce üzerinde bildirilen değişkenlerin <xref:System.Activities.Statements.Sequence> bağımlılık özelliği bağlamak için kullanılır.  
  
 ![Etkinlik türü](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")  
  
 ![OK](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")  
  
 ![Özellikler](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`
