---
title: 3.5 kural kümesi ile birlikte çalışma
ms.date: 03/30/2017
ms.assetid: 969f3295-d874-428c-a9c6-623e3d578e51
ms.openlocfilehash: 5ea5454ef80bfd83611ed20392782d99cd8c0c25
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43538558"
---
# <a name="interop-with-35-rule-set"></a><span data-ttu-id="635d7-102">3.5 kural kümesi ile birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="635d7-102">Interop with 3.5 Rule Set</span></span>
<span data-ttu-id="635d7-103">Bu örnek, kullanımını gösterir. <xref:System.Activities.Statements.Interop> özel etkinliği ile tümleştirmek için etkinlik [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] kullanarak <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` ve kuralları.</span><span class="sxs-lookup"><span data-stu-id="635d7-103">This sample demonstrates the use of the <xref:System.Activities.Statements.Interop> activity to integrate with a custom activity in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] using <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` and rules.</span></span> <span data-ttu-id="635d7-104">Bağlayarak verileri için özel etkinlik geçirmeden [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] özel etkinlik tarafından kullanıma sunulan bağımlılık özellikleri için değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="635d7-104">It passes data to the custom activity by binding [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] variables to the dependency properties exposed by the custom activity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="635d7-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="635d7-105">Requirements</span></span>  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
2.  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
3.  [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]  
  
## <a name="demonstrates"></a><span data-ttu-id="635d7-106">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="635d7-106">Demonstrates</span></span>  
 <span data-ttu-id="635d7-107"><xref:System.Activities.Statements.Interop> etkinlik, <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` etkinliğinde [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] bağımlılık özellikleri</span><span class="sxs-lookup"><span data-stu-id="635d7-107"><xref:System.Activities.Statements.Interop> activity, <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` activity in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] with dependency properties</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="635d7-108">Tartışma</span><span class="sxs-lookup"><span data-stu-id="635d7-108">Discussion</span></span>  
 <span data-ttu-id="635d7-109">Örnek ile tümleştirmek için tümleştirme senaryoları biri gösterir bir [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] etkinlik.</span><span class="sxs-lookup"><span data-stu-id="635d7-109">The sample demonstrates one of the integration scenarios for integrating with a [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] activity.</span></span> <span data-ttu-id="635d7-110">Bu örnek içeren bir [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] çağıran özel bir etkinlik bir <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="635d7-110">This sample includes a [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] custom activity that invokes a <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` activity.</span></span>  
  
## <a name="travelrulelibrary"></a><span data-ttu-id="635d7-111">TravelRuleLibrary</span><span class="sxs-lookup"><span data-stu-id="635d7-111">TravelRuleLibrary</span></span>  
 <span data-ttu-id="635d7-112">Şu şekilde bir ilke etkinlik içeren özel bir sıralı etkinlik Tasarımcısı'nda TravelRuleSet.cs açma gösterir</span><span class="sxs-lookup"><span data-stu-id="635d7-112">Opening TravelRuleSet.cs in the designer shows a custom sequential activity that contains a Policy activity as follows</span></span>  
  
 <span data-ttu-id="635d7-113">![Interop etkinlik](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")</span><span class="sxs-lookup"><span data-stu-id="635d7-113">![Interop Activity](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")</span></span>  
  
 <span data-ttu-id="635d7-114">Çift **DiscountPolicy** kuralları incelemek için ilke etkinlik.</span><span class="sxs-lookup"><span data-stu-id="635d7-114">Double-click the **DiscountPolicy** policy activity to examine the rules.</span></span> <span data-ttu-id="635d7-115">Kuralları göstermek için kurallar düzenleyicisinde görünür.</span><span class="sxs-lookup"><span data-stu-id="635d7-115">The Rules editor appears to show the rules.</span></span>  
  
 <span data-ttu-id="635d7-116">![Kural kümesi düzenleyici](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")</span><span class="sxs-lookup"><span data-stu-id="635d7-116">![Rule Set Editor](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")</span></span>  
  
 <span data-ttu-id="635d7-117">Sağ **DiscountPolicy** etkinliği ve seçin **kodu görüntüle** seçeneği bu etkinlikle giden kod yanında C# kodu inceleyin.</span><span class="sxs-lookup"><span data-stu-id="635d7-117">Right-click the **DiscountPolicy** activity and select the **View Code** option to examine the code-beside C# code that goes with this activity.</span></span> <span data-ttu-id="635d7-118">Bağımlılık özelliği ayarı gözlemleyin `DiscountLevel`.</span><span class="sxs-lookup"><span data-stu-id="635d7-118">Observe the dependency property setting for `DiscountLevel`.</span></span> <span data-ttu-id="635d7-119">Bunun eşdeğeri olan bir <xref:System.Activities.Argument> içinde [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="635d7-119">This is equivalent to an <xref:System.Activities.Argument> in [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span></span>  
  
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
  
## <a name="interopwith35ruleset"></a><span data-ttu-id="635d7-120">InteropWith35RuleSet</span><span class="sxs-lookup"><span data-stu-id="635d7-120">InteropWith35RuleSet</span></span>  
 <span data-ttu-id="635d7-121">Bu bir [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] kullanan sıralı iş akışı projesi <xref:System.Activities.Statements.Interop> TravelRuleLibrary projede oluşturulan özel kural tümleştirmek için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="635d7-121">This is a [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] sequential workflow project that uses the <xref:System.Activities.Statements.Interop> activity to integrate with the custom rule set created in the TravelRuleLibrary project.</span></span> <span data-ttu-id="635d7-122">Değişkenler en üst düzey üzerinde oluşturulan <xref:System.Activities.Statements.Sequence> gibi.</span><span class="sxs-lookup"><span data-stu-id="635d7-122">Variables are created on the top-level <xref:System.Activities.Statements.Sequence> as follows.</span></span>  
  
 <span data-ttu-id="635d7-123">![Değişkenleri](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")</span><span class="sxs-lookup"><span data-stu-id="635d7-123">![Variables](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")</span></span>  
  
 <span data-ttu-id="635d7-124">![Çözüm Gezgini](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")</span><span class="sxs-lookup"><span data-stu-id="635d7-124">![Solution Explorer](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")</span></span>  
  
 <span data-ttu-id="635d7-125">Son olarak, <xref:System.Activities.Statements.Interop> etkinliği TravelRuleSet ile tümleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="635d7-125">Lastly, the <xref:System.Activities.Statements.Interop> activity is used to integrate with the TravelRuleSet.</span></span> <span data-ttu-id="635d7-126">Daha önce bildirilen değişkenlerin <xref:System.Activities.Statements.Sequence> bağımlılık özellikleri için bağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="635d7-126">The variables that were declared earlier on the <xref:System.Activities.Statements.Sequence> are used to bind to the dependency properties.</span></span>  
  
 <span data-ttu-id="635d7-127">![Etkinlik türü](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")</span><span class="sxs-lookup"><span data-stu-id="635d7-127">![Activity Type](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")</span></span>  
  
 <span data-ttu-id="635d7-128">![OK](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")</span><span class="sxs-lookup"><span data-stu-id="635d7-128">![Arrow](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")</span></span>  
  
 <span data-ttu-id="635d7-129">![Özellikleri](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")</span><span class="sxs-lookup"><span data-stu-id="635d7-129">![Properties](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="635d7-130">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="635d7-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="635d7-131">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="635d7-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="635d7-132">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="635d7-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="635d7-133">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="635d7-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`
