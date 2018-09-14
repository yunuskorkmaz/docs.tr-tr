---
title: 3.5 kural kümesi ile birlikte çalışma
ms.date: 03/30/2017
ms.assetid: 969f3295-d874-428c-a9c6-623e3d578e51
ms.openlocfilehash: 5ea5454ef80bfd83611ed20392782d99cd8c0c25
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45510155"
---
# <a name="interop-with-35-rule-set"></a>3.5 kural kümesi ile birlikte çalışma
Bu örnek, kullanımını gösterir. <xref:System.Activities.Statements.Interop> özel etkinliği ile tümleştirmek için etkinlik [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] kullanarak <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` ve kuralları. Bağlayarak verileri için özel etkinlik geçirmeden [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] özel etkinlik tarafından kullanıma sunulan bağımlılık özellikleri için değişkenleri.  
  
## <a name="requirements"></a>Gereksinimler  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
2.  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
3.  [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.Activities.Statements.Interop> etkinlik, <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` etkinliğinde [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] bağımlılık özellikleri  
  
## <a name="discussion"></a>Tartışma  
 Örnek ile tümleştirmek için tümleştirme senaryoları biri gösterir bir [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] etkinlik. Bu örnek içeren bir [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] çağıran özel bir etkinlik bir <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` etkinlik.  
  
## <a name="travelrulelibrary"></a>TravelRuleLibrary  
 Şu şekilde bir ilke etkinlik içeren özel bir sıralı etkinlik Tasarımcısı'nda TravelRuleSet.cs açma gösterir  
  
 ![Interop etkinlik](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")  
  
 Çift **DiscountPolicy** kuralları incelemek için ilke etkinlik. Kuralları göstermek için kurallar düzenleyicisinde görünür.  
  
 ![Kural kümesi düzenleyici](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")  
  
 Sağ **DiscountPolicy** etkinliği ve seçin **kodu görüntüle** seçeneği bu etkinlikle giden kod yanında C# kodu inceleyin. Bağımlılık özelliği ayarı gözlemleyin `DiscountLevel`. Bunun eşdeğeri olan bir <xref:System.Activities.Argument> içinde [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].  
  
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
 Bu bir [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] kullanan sıralı iş akışı projesi <xref:System.Activities.Statements.Interop> TravelRuleLibrary projede oluşturulan özel kural tümleştirmek için etkinlik. Değişkenler en üst düzey üzerinde oluşturulan <xref:System.Activities.Statements.Sequence> gibi.  
  
 ![Değişkenleri](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")  
  
 ![Çözüm Gezgini](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")  
  
 Son olarak, <xref:System.Activities.Statements.Interop> etkinliği TravelRuleSet ile tümleştirmek için kullanılır. Daha önce bildirilen değişkenlerin <xref:System.Activities.Statements.Sequence> bağımlılık özellikleri için bağlamak için kullanılır.  
  
 ![Etkinlik türü](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")  
  
 ![OK](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")  
  
 ![Özellikleri](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`
