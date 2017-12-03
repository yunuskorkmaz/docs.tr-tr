---
title: "Koşullu etkinlik grubu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f76ef924-34ce-48ae-8c8d-48faf9697754
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e0df4ddc6f2cc5404c8153b30df66cda41487691
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="conditioned-activity-group"></a><span data-ttu-id="b7097-102">Koşullu etkinlik grubu</span><span class="sxs-lookup"><span data-stu-id="b7097-102">Conditioned Activity Group</span></span>
<span data-ttu-id="b7097-103">Örnek bir seyahat kayıt uygulaması gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7097-103">The sample demonstrates a travel booking application.</span></span> <span data-ttu-id="b7097-104"><xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) sahip iki kodunu aktivite: bir araba ve uçak etkinliğiyle.</span><span class="sxs-lookup"><span data-stu-id="b7097-104">The <xref:System.Workflow.Activities.ConditionedActivityGroup> (CAG) has two code activities: a Car activity and an Airline activity.</span></span> <span data-ttu-id="b7097-105">İçinde `SimpleCAGWorkflow` oluşturucusu, bir "travelNeedType" ArrayList nesnesi gerekli seyahat kayıtları türleri ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="b7097-105">In the `SimpleCAGWorkflow` constructor, a "travelNeedType" ArrayList object is populated with the types of travel bookings that are required.</span></span> <span data-ttu-id="b7097-106">Birini veya her ikisini yorum tarafından `travelNeeds.Add` deyimleri CAG davranış buna göre değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b7097-106">By commenting out one or both of the `travelNeeds.Add` statements, you modify the CAG behavior accordingly.</span></span> <span data-ttu-id="b7097-107">Araba ve uçak etkinliklerin kendi <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> koşul doldurulmuş ile bir <xref:System.Workflow.Activities.CodeCondition>.</span><span class="sxs-lookup"><span data-stu-id="b7097-107">Both the Car and Airline activities have their <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> condition populated with a <xref:System.Workflow.Activities.CodeCondition>.</span></span> <span data-ttu-id="b7097-108">Yalnızca araba etkinlik yürütür `travelNeeds` gruplandırmasında bir `TravelNeeds.Car` girişi ve etkinlik yürütür yalnızca uçak `travelNeeds` gruplandırmasında bir `TravelNeeds.Airline` girişi.</span><span class="sxs-lookup"><span data-stu-id="b7097-108">The Car activity executes only if the `travelNeeds` collection has a `TravelNeeds.Car` entry, and the Airline activity executes only if the `travelNeeds` collection has a `TravelNeeds.Airline` entry.</span></span>  
  
 <span data-ttu-id="b7097-109">Her etkinlik yürütülmesini karşılık gelen bir giriş koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b7097-109">The execution of each activity removes the corresponding entry from the collection.</span></span> <span data-ttu-id="b7097-110">Varsayılan <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> durumunu belirten alt öğesi yürütülmekte olduğunu veya yürütme için hazır olduğunda CAG çıkmalıdır (göre kendi <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> koşullar).</span><span class="sxs-lookup"><span data-stu-id="b7097-110">The default <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A> condition specifies that the CAG should exit when no children are executing or are ready for execution (based on their <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty> conditions).</span></span> <span data-ttu-id="b7097-111">Bu örnekte, bu CAG ne zaman çıkar anlamına gelir `travelNeeds` koleksiyonu boş.</span><span class="sxs-lookup"><span data-stu-id="b7097-111">In this sample, this means that the CAG exits when the `travelNeeds` collection is empty.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="b7097-112">Örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b7097-112">To build the sample</span></span>  
  
1.  <span data-ttu-id="b7097-113">Çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b7097-113">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="b7097-114">CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b7097-114">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="b7097-115">CTRL + F5'e basarak hata ayıklama olmadan çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b7097-115">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="b7097-116">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b7097-116">To run the sample</span></span>  
  
-   <span data-ttu-id="b7097-117">Örnek için ana klasörü altında bulunan .exe dosyasını SimpleCAG\bin\debug klasöründe (veya örnek Visual Basic sürümü için SimpleCAG\bin klasör) SDK komut istemi penceresinde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b7097-117">In the SDK Command Prompt window, run the .exe file in the SimpleCAG\bin\debug folder (or the SimpleCAG\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b7097-118">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="b7097-118">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b7097-119">Devam etmeden önce aşağıdaki (varsayılan) dizin denetle:</span><span class="sxs-lookup"><span data-stu-id="b7097-119">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b7097-120">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b7097-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b7097-121">Bu örnek aşağıdaki dizinde bulunur:</span><span class="sxs-lookup"><span data-stu-id="b7097-121">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\SimpleCAG`  
  
## <a name="see-also"></a><span data-ttu-id="b7097-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b7097-122">See Also</span></span>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.WhenConditionProperty>  
 <xref:System.Workflow.Activities.CodeCondition>  
 <xref:System.Workflow.Activities.ConditionedActivityGroup.UntilCondition%2A>
