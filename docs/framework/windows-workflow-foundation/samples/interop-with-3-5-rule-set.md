---
title: 3.5 kural kümesi ile birlikte çalışma
ms.date: 03/30/2017
ms.assetid: 969f3295-d874-428c-a9c6-623e3d578e51
ms.openlocfilehash: 9d42198d336e38c4ad9fc6c686a019814bd571bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517913"
---
# <a name="interop-with-35-rule-set"></a><span data-ttu-id="f8cc2-102">3.5 kural kümesi ile birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="f8cc2-102">Interop with 3.5 Rule Set</span></span>
<span data-ttu-id="f8cc2-103">Bu örnek kullanımını gösteren <xref:System.Activities.Statements.Interop> özel bir etkinlikte ile tümleştirmek için etkinlik [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] kullanarak <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` ve kuralları.</span><span class="sxs-lookup"><span data-stu-id="f8cc2-103">This sample demonstrates the use of the <xref:System.Activities.Statements.Interop> activity to integrate with a custom activity in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] using <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` and rules.</span></span> <span data-ttu-id="f8cc2-104">Özel Etkinlik verileri, bağlayarak geçirmeden [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] özel etkinlik tarafından kullanıma sunulan bağımlılık özellikleri değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="f8cc2-104">It passes data to the custom activity by binding [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] variables to the dependency properties exposed by the custom activity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8cc2-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f8cc2-105">Requirements</span></span>  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
2.  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
3.  [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]  
  
## <a name="demonstrates"></a><span data-ttu-id="f8cc2-106">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="f8cc2-106">Demonstrates</span></span>  
 <span data-ttu-id="f8cc2-107"><xref:System.Activities.Statements.Interop> etkinlik, <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` etkinliğinde [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] bağımlılık özellikleri</span><span class="sxs-lookup"><span data-stu-id="f8cc2-107"><xref:System.Activities.Statements.Interop> activity, <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` activity in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] with dependency properties</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="f8cc2-108">Tartışma</span><span class="sxs-lookup"><span data-stu-id="f8cc2-108">Discussion</span></span>  
 <span data-ttu-id="f8cc2-109">Örnek ile tümleştirme için tümleştirme senaryolarına birini gösteren bir [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] etkinlik.</span><span class="sxs-lookup"><span data-stu-id="f8cc2-109">The sample demonstrates one of the integration scenarios for integrating with a [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] activity.</span></span> <span data-ttu-id="f8cc2-110">Bu örnek içeren bir [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] çağıran Özel Etkinlik bir <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="f8cc2-110">This sample includes a [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] custom activity that invokes a <!--zz <xref:System.Workflow.Activities.Policy> --> `System.Workflow.Activities.Policy` activity.</span></span>  
  
## <a name="travelrulelibrary"></a><span data-ttu-id="f8cc2-111">TravelRuleLibrary</span><span class="sxs-lookup"><span data-stu-id="f8cc2-111">TravelRuleLibrary</span></span>  
 <span data-ttu-id="f8cc2-112">Şu şekilde bir ilke etkinlik içeren özel bir sıralı etkinlik Tasarımcısı'nda TravelRuleSet.cs açma gösterir</span><span class="sxs-lookup"><span data-stu-id="f8cc2-112">Opening TravelRuleSet.cs in the designer shows a custom sequential activity that contains a Policy activity as follows</span></span>  
  
 <span data-ttu-id="f8cc2-113">![Birlikte çalışma etkinlik](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")</span><span class="sxs-lookup"><span data-stu-id="f8cc2-113">![Interop Activity](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulespolicy.jpg "InteropRulesPolicy")</span></span>  
  
 <span data-ttu-id="f8cc2-114">Çift **DiscountPolicy** ilke etkinlik kuralları inceleyin.</span><span class="sxs-lookup"><span data-stu-id="f8cc2-114">Double-click the **DiscountPolicy** policy activity to examine the rules.</span></span> <span data-ttu-id="f8cc2-115">Kuralları göstermek için kuralları Düzenleyicisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f8cc2-115">The Rules editor appears to show the rules.</span></span>  
  
 <span data-ttu-id="f8cc2-116">![Kural kümesi düzenleyici](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")</span><span class="sxs-lookup"><span data-stu-id="f8cc2-116">![Rule Set Editor](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesruleseteditor.jpg "InteropRulesRuleSetEditor")</span></span>  
  
 <span data-ttu-id="f8cc2-117">Sağ **DiscountPolicy** etkinliği ve seçin **görünümü kodu** seçeneği ile bu etkinliğine gittiği kod yanında C# kodu inceleyin.</span><span class="sxs-lookup"><span data-stu-id="f8cc2-117">Right-click the **DiscountPolicy** activity and select the **View Code** option to examine the code-beside C# code that goes with this activity.</span></span> <span data-ttu-id="f8cc2-118">Bağımlılık özelliği ayarını gözlemlemek `DiscountLevel`.</span><span class="sxs-lookup"><span data-stu-id="f8cc2-118">Observe the dependency property setting for `DiscountLevel`.</span></span> <span data-ttu-id="f8cc2-119">Bu eşdeğer olan bir <xref:System.Activities.Argument> içinde [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f8cc2-119">This is equivalent to an <xref:System.Activities.Argument> in [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span></span>  
  
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
  
## <a name="interopwith35ruleset"></a><span data-ttu-id="f8cc2-120">InteropWith35RuleSet</span><span class="sxs-lookup"><span data-stu-id="f8cc2-120">InteropWith35RuleSet</span></span>  
 <span data-ttu-id="f8cc2-121">Bu bir [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] kullanan sıralı iş akışı projesinde <xref:System.Activities.Statements.Interop> özel kural TravelRuleLibrary projesinde oluşturulan kümesi ile tümleştirmek için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="f8cc2-121">This is a [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] sequential workflow project that uses the <xref:System.Activities.Statements.Interop> activity to integrate with the custom rule set created in the TravelRuleLibrary project.</span></span> <span data-ttu-id="f8cc2-122">Değişkenleri üst düzey üzerinde oluşturulan <xref:System.Activities.Statements.Sequence> gibi.</span><span class="sxs-lookup"><span data-stu-id="f8cc2-122">Variables are created on the top-level <xref:System.Activities.Statements.Sequence> as follows.</span></span>  
  
 <span data-ttu-id="f8cc2-123">![Değişkenleri](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")</span><span class="sxs-lookup"><span data-stu-id="f8cc2-123">![Variables](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesvariables.jpg "InteropRulesVariables")</span></span>  
  
 <span data-ttu-id="f8cc2-124">![Çözüm Gezgini](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")</span><span class="sxs-lookup"><span data-stu-id="f8cc2-124">![Solution Explorer](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulessolutionexplorer.jpg "InteropRulesSolutionExplorer")</span></span>  
  
 <span data-ttu-id="f8cc2-125">Son olarak, <xref:System.Activities.Statements.Interop> etkinlik TravelRuleSet ile tümleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f8cc2-125">Lastly, the <xref:System.Activities.Statements.Interop> activity is used to integrate with the TravelRuleSet.</span></span> <span data-ttu-id="f8cc2-126">Daha önce üzerinde bildirilen değişkenlerin <xref:System.Activities.Statements.Sequence> bağımlılık özelliği bağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f8cc2-126">The variables that were declared earlier on the <xref:System.Activities.Statements.Sequence> are used to bind to the dependency properties.</span></span>  
  
 <span data-ttu-id="f8cc2-127">![Etkinlik türü](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")</span><span class="sxs-lookup"><span data-stu-id="f8cc2-127">![Activity Type](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprules.jpg "InteropRules")</span></span>  
  
 <span data-ttu-id="f8cc2-128">![OK](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")</span><span class="sxs-lookup"><span data-stu-id="f8cc2-128">![Arrow](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesarrow.jpg "InteropRulesArrow")</span></span>  
  
 <span data-ttu-id="f8cc2-129">![Özellikler](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")</span><span class="sxs-lookup"><span data-stu-id="f8cc2-129">![Properties](../../../../docs/framework/windows-workflow-foundation/samples/media/interoprulesproperties.jpg "InteropRulesProperties")</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f8cc2-130">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="f8cc2-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f8cc2-131">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f8cc2-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f8cc2-132">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="f8cc2-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f8cc2-133">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f8cc2-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`
