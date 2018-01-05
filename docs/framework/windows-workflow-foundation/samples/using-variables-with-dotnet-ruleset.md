---
title: ".NET Framework 3.5 Ruleset ile değişkenlerini kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27b56249-22fe-4252-840f-74c0d6c7a6b3
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2656cc5d8add0027d6bf038d5de735ebccd2d96d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-variables-with-a-net-framework-35-ruleset"></a><span data-ttu-id="68506-102">.NET Framework 3.5 Ruleset ile değişkenlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="68506-102">Using Variables with a .NET Framework 3.5 Ruleset</span></span>
<span data-ttu-id="68506-103">Bu örneği kullanan bir iş akışının nasıl oluşturulacağını gösterir <xref:System.Activities.Statements.Interop> yazılmış özel bir aktivite tümleştirmek için etkinlik [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] İlkesi ve kuralları kullanır.</span><span class="sxs-lookup"><span data-stu-id="68506-103">This sample demonstrates how to create a workflow that uses the <xref:System.Activities.Statements.Interop> activity to integrate a custom activity written in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] that uses policy and rules.</span></span> <span data-ttu-id="68506-104">İş akışı değişkenleri özel etkinlik tarafından kullanıma sunulan bağımlılık özellikleri bağlayarak verileri özel etkinlik geçirir.</span><span class="sxs-lookup"><span data-stu-id="68506-104">The workflow passes data to the custom activity by binding variables to the dependency properties exposed by the custom activity.</span></span>  
  
## <a name="sample-walkthrough"></a><span data-ttu-id="68506-105">Örnek gözden geçirme</span><span class="sxs-lookup"><span data-stu-id="68506-105">Sample walkthrough</span></span>  
  
#### <a name="to-examine-travelrulelibrary"></a><span data-ttu-id="68506-106">TravelRuleLibrary incelemek için</span><span class="sxs-lookup"><span data-stu-id="68506-106">To examine TravelRuleLibrary</span></span>  
  
1.  <span data-ttu-id="68506-107">Kullanarak [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], InteropWith35RuleSet.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="68506-107">Using [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], open the InteropWith35RuleSet.sln solution file.</span></span>  
  
2.  <span data-ttu-id="68506-108">İş Akışı Tasarımcısı'nda TravelRuleSet.cs açın.</span><span class="sxs-lookup"><span data-stu-id="68506-108">Open the TravelRuleSet.cs in the workflow designer.</span></span>  
  
     <span data-ttu-id="68506-109">İçeren özel bir sıralı etkinlik bir <xref:System.Workflow.Activities.PolicyActivity> görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="68506-109">A custom sequential activity that contains a <xref:System.Workflow.Activities.PolicyActivity> is displayed.</span></span>  
  
3.  <span data-ttu-id="68506-110">Kuralları incelemek için DiscountPolicy İlkesi etkinliği çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="68506-110">Double-click the DiscountPolicy policy activity to examine the rules.</span></span>  
  
     <span data-ttu-id="68506-111">Kuralları göstermek için kural Düzenleyicisi açılır.</span><span class="sxs-lookup"><span data-stu-id="68506-111">The Rules editor pops up to show the rules.</span></span>  
  
4.  <span data-ttu-id="68506-112">Sağ tıklayın `DiscountPolicy` seçip **görünümü kodu** seçeneği C# kodu etkinliğin yanında kodu inceleyin.</span><span class="sxs-lookup"><span data-stu-id="68506-112">Right click the `DiscountPolicy` and select the **View Code** option to examine the code beside C# code for the activity.</span></span>  
  
     <span data-ttu-id="68506-113">Bağımlılık özelliği ayarını gözlemlemek `DiscountLevel`.</span><span class="sxs-lookup"><span data-stu-id="68506-113">Observe the dependency property setting for `DiscountLevel`.</span></span> <span data-ttu-id="68506-114">Bu bağımsız değişkenler için eşdeğerdir [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="68506-114">This is equivalent to arguments in [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="68506-115">bağımsız değişkenleri, görmek [değişkenleri ve bağımsız değişkenler](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="68506-115"> arguments, see [Variables and Arguments](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).</span></span>  
  
## <a name="interopwith35ruleset"></a><span data-ttu-id="68506-116">InteropWith35RuleSet</span><span class="sxs-lookup"><span data-stu-id="68506-116">InteropWith35RuleSet</span></span>  
 <span data-ttu-id="68506-117">Bu kullanan bir sıralı iş akışı projedir <xref:System.Activities.Statements.Interop> oluşturulan özel kural kümesi ile tümleştirmek için etkinlik `TravelRuleLibrary` projesi.</span><span class="sxs-lookup"><span data-stu-id="68506-117">This is a sequential workflow project that uses the <xref:System.Activities.Statements.Interop> activity to integrate with the custom Rule set created in the `TravelRuleLibrary` project.</span></span> <span data-ttu-id="68506-118">Değişkenleri, en üst düzey oluşturulur <xref:System.Activities.Statements.Sequence> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="68506-118">Variables are created on the top level <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="68506-119"><xref:System.Activities.Statements.Interop> Etkinlik ile tümleştirmek için kullanılan `TravelRuleSet` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="68506-119">The <xref:System.Activities.Statements.Interop> activity is used to integrate with the `TravelRuleSet` activity.</span></span> <span data-ttu-id="68506-120">Üzerinde bildirilen değişkenlerin <xref:System.Activities.Statements.Sequence> bağımlılık özelliği bağlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="68506-120">The variables that are declared on the <xref:System.Activities.Statements.Sequence> are used to bind to the dependency properties.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="68506-121">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="68506-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="68506-122">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], InteropWith35RuleSet.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="68506-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InteropWith35RuleSet.sln solution file.</span></span>  
  
2.  <span data-ttu-id="68506-123">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="68506-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="68506-124">Çözümü çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="68506-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="68506-125">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="68506-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="68506-126">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="68506-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="68506-127">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="68506-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="68506-128">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="68506-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`